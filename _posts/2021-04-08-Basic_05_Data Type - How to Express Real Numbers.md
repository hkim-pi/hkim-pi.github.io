---
layout: single
title: "Basic_05_Data Type - How to Express Real Numbers"
categories: 
 - Java
tags:
 - java
 - web
 - basic
 - programming
 - data type
 - float
 - double
 - floating point method
---

### *Data Type - How to Express Real Numbers*





<br/>

<br/>

#### **Floating Point Method**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- **Since Real Numbers Are More Precise Than Integers, They Should Be Expressed in a Different Way Than Integers**

- **Expression of Real Value '0.1' by Floating Point Method**

  ```
  1.0 * 10^-1
  
  1.0: fraction
  10: base -> 2, 10, 16 are commonly used for bases
  -1: exponent 
  ```

- **Expressed as Exponent and Fraction Parts**

- **Computers Use 2 as Bases**

-  **Normalization:** Where a fraction is represented as a fraction up to one digit less than the base

- **The Computer Has a Base of 2, So the First Digit of the Fraction Is Always 1 When Normalized.** (ex. 0.4 * 2^-1 expression of 0.2 -- normalized to --> 1.6 * 2^-3)



<br/>

#### **float and double**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- **float:** sign (1 bit) -- exponent part (8 bits) -- fraction part (23 bits)
- **double:** sign (1 bit) -- exponent part (11 bits) -- fraction part (52 bits)
- **In Java, the Default Type of Real Numbers Is double**



<br/>

#### **Example**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- ```java
  package basic05;
  
  public class DoubleTest {
  
  	public static void main(String[] args) {
  		
  		double dnum = 3.14;
  		// float fnum = 3.14; //-> error
  		float fnum = 3.14f;
  		
  		System.out.println(dnum);
  		System.out.println(fnum);
  	}
  
  }
  
  ```



<br/>

#### **Floating Point Method Error**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- **With Floating Point Method Represented by Exponent and Fraction, Some Errors May Occur Because the Exponent Part Cannot Represent Zero**.

  ```java
  public class DoubleTest2 {
  
  	public static void main(String[] args) {
  
  		double dnum = 1;
  		
  		for(int i = 0; i<10000; i++) {
  			dnum = dnum + 0.1;
  		}
  		System.out.println(dnum);
  	}
  }
  
  //-> 1001.000000000159
  ```

  

