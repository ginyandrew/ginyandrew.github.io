---
title: Basic
layout: default
parent: Spring
nav_order: 1
---

# Spring - Basic 
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Basic


* ResponseEntity

Equal to @ResponseBody, it turns return value to JSON(default) or XML format.

---
* Difference Between CrudRepository and JPARepository 

CrudRepository and JPA repository both are the interface of the spring data repository library. 
**JPA repository extends** CrudRepository and PagingAndSorting repository. It inherits some finders from crud repository such as findOne, gets and removes an entity.

![](\assets\images\spring_001.png)

Choose CrudRepository for simple CRUD only. Choose JPARepository for paging/sorting/other JPA functionalities.



---
 reference 
www.tutorialspoint.com
