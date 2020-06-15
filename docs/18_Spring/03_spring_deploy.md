---
title: Deploy Boot+Vue
layout: default
parent: Spring
nav_order: 3
---

# How to deploy Spring Boot + Vue project with external Tomcat 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Prepare physical server - Respberry PI 4 
Once decided to use Raspberry PI, (chose it solely for 'no extra cost')  need to know how to deploy it by using an external Tomcat...

* Rasberry PI parts to purchase - 
	* **RAS PI RASPBERRY PI 4 - 8GB**  
	* RAS PI 15W **POWER SUPPLY** WH
	* MICROCONN MICROCONN PI 4 ALM **CASE**
	* KING** 64GB MicroSD W/ADP CL10 (will become a main storage space for O/S...)

Raspberry PI turns on when it's plugged in automatically. 
Burn the OS installation image on the microSD card, and assemble the parts and plug it in the power.
It has already wifi -

## Install Tomcat 
My java project uses the java ver. 11. so choose [Tomcat version 9 ](https://tomcat.apache.org/download-90.cgi)or above.
already had 1.8 installed but it caused some error, so removed 1.8...

* **Eclipse setting** 
	* Properties -> Java Compiler -> compliance level  ( set to **11**)
	* Properties -> Java Build Path -> **JavaSE-11**

## Set up & Build Spring Boot project  

* **pom.xml**

```xml
...
<parent>
...
</parent>
<!--SpringBoot should be built as a .jar.. -->
<packaging>jar</packaging>
...
<properties>
	<java.version>1.11</java.version>
</properties>
<dependencies>
	...
	<!-- these 2 dependencies cover JPA/Hibernate. Remove 'hibernate-core' and 'hibernate-entitymanager' to avoid conflict. -->
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-data-jpa</artifactId>
		<scope>provided</scope>
	</dependency>
	<dependency>
		<groupId>org.springframework.data</groupId>
		<artifactId>spring-data-jpa</artifactId>
	</dependency>
	<!--got some error since javax- was missing. added it as well -->	
	<dependency>
		<groupId>javax.servlet</groupId>
		<artifactId>jstl</artifactId>
		<scope>provided</scope> 
	</dependency>
	...
</dependencies>
<build>
	<plugins>
		<plugin>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-maven-plugin</artifactId>
			<!-- To set the java version for compiler -->
			<configuration>
				<source>1.11</source>
				<target>1.11</target>
			</configuration>
			...
```


* **MyApplication.java**

```java
@SpringBootApplication
public class MyApplication extends SpringBootServletInitializer{ // extends SpringBootServletInitializer for external deployment 
	...
	@Override
	protected SpringApplicationBuilder configure(SpringApplicationBuilder builder) {
		return builder.sources(MyApplication.class);
	}
	...
}
```

* **..Repository.java**

```java
@Repository // make sure Repository classes have the annotation 'repository'
public interface CareRepository extends JpaRepository<CareVO, Integer>{ ...
```

<br/>
In Eclipse, _Project -> Run as -> Run Configuration_, empty _Profiles_ and put 'package' in _Goals_

![](/assets/images/spring_002.JPG )

Once the configuration is created, it can build jar in _projectRoot/target_ folder.

![](/assets/images/spring_003.JPG)

![](/assets/images/spring_004.JPG)

copy the jar file into _Tomcat/webapps_  folder.

![](/assets/images/spring_005.JPG)


run Tomcat by using command line.
```shell
... apache-tomcat-9.0.35\webapps>java -jar NegobillBoot1-1.jar # jar file name in webapps.
```
![](/assets/images/spring_006.JPG)

## Set up & Build Vue project
* **webpack.config.js**

```js
module.exports = {
  entry: './src/main.js',
  output: {
    path: path.resolve(__dirname, './dist'),
    publicPath: './dist/',  // tomcat will look for build.js file in the child folder 'dist' of the folder index.html located.
	filename: 'build.js'
  },
	...
```

run the CL below to build .js files in /dist folder.

```powershell
npm run build # it builds files in 'dist' folder.
```

<br/>
main.html, index.html and /dist are static files that will be deployed by Tomcat.
![](/assets/images/vue_003.JPG)

copy the static files into Tomcat folder. (inside webapps/projectName)
![](/assets/images/vue_004.JPG)

by using CommandLind, move to _apache-tomcat-9.0.35\bin_ and run tomcat.

```shell
startup.bat # it starts tomcat 
shutdown.bat # it shutdown tomcat.
```

<br/>
To run both services, added one more port into server.xml of Tomcat. _(add one more service tag and change service name/ connector port/redirectPort/ and appBase.)_

```xml
<?xml version="1.0" encoding="UTF-8"?>
<Server port="8005" shutdown="SHUTDOWN">
		...
	<!--first service for Spring boot-->
	<Service name="Catalina">
		<Connector port="8080" protocol="HTTP/1.1" connectionTimeout="20000" redirectPort="8442" />...
		<Host name="localhost"  appBase="webapps" unpackWARs="true" autoDeploy="true">...
	</Service>
	<!--first service for Vue -->
	<Service name="Catalina2">
		<!--appBase should have full path of Tomcat's webapps folder -->
		<Connector port="9000" protocol="HTTP/1.1" connectionTimeout="20000" redirectPort="8443" />...
		<Host name="localhost"  appBase="D:/...skip.../apache-tomcat-9.0.35/webapps/negobill" unpackWARs="true" autoDeploy="true">...
	</Service>
</Server>		
```

can access to the app at : _localhost:9000/negobill(folder name in Tomcat webapps folder)/index.html_

![](/assets/images/vue_005.JPG)
