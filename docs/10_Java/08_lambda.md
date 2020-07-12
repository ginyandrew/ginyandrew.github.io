---
title: Lambda
layout: default
parent: Java
nav_order: 8
---

# Java - Lambda
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---
## Lambda 
what is Lambda? - an anonymous function with no name.

in this example, Lambda's target type is 'Adder'. all anonymouse function with no name have interace type.

```java
//Lambda's target interface should have only one method. 
//@FunctionalInterface enforces it.
@FuntionalInterface 
interface Adder {
  int add(int n);
}
```
```java
class Calculator {
 public static void main(String[] args) {
  
  int n = 2;
	
  //before Lambda expression
  Adder ad = new Adder(){
   @Override // initiating with overriding at the same time
   int add(int n){  return n+ 1;} // Lambda's param ('n' in this case) is considered as 'final', can't change it.
  }
 
  //Lambda 1
  Adder ad = (int n) -> {return n + 1;};
  //Lambda 2
  Adder ad = (n) -> {return n + 1;}; //it knows param type so we can skip it
  //Lambda 3
  Adder ad = n -> n + 1; // if logic is one line, can skip bracket. 

  System.out.println(ad.add(n)); // 3
}
```

There are many registered Lambda interfaces (provided name/param/return types) so we can resue them.
```java
// example - IntBinaryOperator (get two int, return bigger value)
// before Lambda expression
IntBinaryOperator op = (int x, int y) -> {
  if(x > y) return x;
  return y;
};

// Lambda 1
IntBinaryOperator op1 = (int x, int y) -> {return Math.max(x, y);};
// Lambda 2
IntBinaryOperator op2 = (x, y) -> Math.max(x, y);
// Lambda 3
IntBinaryOperator op = Math::max; // this Lambda refers existing interface (with Math.max) so can skip those params (x,y)

System.out.println(op.applyAsInt(3, 7)); // 7
```
