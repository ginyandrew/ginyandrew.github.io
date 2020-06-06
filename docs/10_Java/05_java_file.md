---
title: File I/O
layout: default
parent: Java
nav_order: 2
---

# Java - File I/O
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## what is File I/O
example 

```java
public void upload(MultipartFile file) {
	file.getOriginalFilename();
	file.getSize();
		
	try {
		FileOutputStream fos = 
			new FileOutputStream("D:/02_mysite/workspace/NegobillBoot/src/main/resources/static/image/"+ file.getOriginalFilename());
		InputStream is = file.getInputStream();
			
		int readCount = 0;
		byte[] buffer = new byte[1024];
		while ((readCount = is.read(buffer)) != -1 ) {
			fos.write(buffer, 0, readCount);
		}
	} catch (Exception e) {
		throw new RuntimeException( e.getCause());
		// TODO: handle exception
	}
}
```
