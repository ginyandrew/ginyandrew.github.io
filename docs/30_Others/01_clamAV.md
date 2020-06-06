---
title: ClamAV
layout: default
parent: Others
nav_order: 1
---

# ClamAV 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## What is ClamAV ?
 an open source antivirus engine  (free!) by Cisco. can detect malware/ virus.
 
## How to Implement ClamAV in Java ?
 
 1. [download ClamAV](https://www.clamav.net/downloads) and install. (C:\program files\clamAV)
 2. Open Powershell as an administrator (in \clamAV) and run the CLs below. 
```powershell
cd "c:\program files\clamav"
copy .\conf_examples\freshclam.conf.sample .\freshclam.conf
copy .\conf_examples\clamd.conf.sample .\clamd.conf 
write.exe .\freshclam.conf  # change  "Example" to #"Example" and change config if you need
write.exe .\clamd.conf # change "Example" to #"Example" and change config if you need
.\freshclam.exe   # it downloads database (database/ .cvd )
```
3. Open a command line as an administrator (in \clamAV) and run the CL below.
```shell
clamd.exe install   # it starts ClamAV service in your machine. (probably 127.0.0.1 / port no. is in clamd.conf)
```
4. Download the jars of required libraries below and add to /lib in your project (or add Maven dependency to pom.xml)
* [org.apache.commons.logging](https://mvnrepository.com/artifact/commons-logging/commons-logging/1.2)
* [commons-io ](https://mvnrepository.com/artifact/commons-io/commons-io/2.6)
* [ClamAV Client in maven (clamav-client-1.0.0.jar)](https://mvnrepository.com/artifact/fi.solita.clamav/clamav-client/1.0.0)
5. implement the java code
```java
File initialFile = new File("resource/sample.txt");
InputStream fis = new FileInputStream(initialFile)
ClamAVClient clamAVClient = new ClamAVClient("127.0.0.1", 3310, 200); // "ClamAV host url", ClamAV port number, socket time out max 
byte[] bts = clamAVClient.scan (fis ); // byte[] scan(InputStream is)
// scanResult:  true - no virus/ false - virus detected
boolean scanResult = ClamAVClient.iscleanReply(bts); // static boolean isCleanReply(byte[] reply)
```
