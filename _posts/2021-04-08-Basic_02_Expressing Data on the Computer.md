---
layout: single
title: "Basic_02_Expressing Data on the Computer"
categories: 
 - Java
tags:
 - java
 - web
 - basic
 - programming
 - data
 - bynary
 - bit
 - byte
 - decimal
 - octal
 - hexadecimal
---

### *Expressing Data on the Computer*



<br/>

<br/>

#### **Binary Expression**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- **Stores data only with 0 and 1**
- **Bit (1 Bit):** Minimum unit of data expressed by the computer, the amount of memory that can store a binary value
- **Byte:** 1 byte = 8 bits



<br/>

#### **Binary and Decimal**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- | Decimal    | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    | 9    | 10   |
  | ---------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
  | **Binary** | 0    | 1    | 10   | 11   | 100  | 101  | 110  | 111  | 1000 | 1001 | 1010 |



<br/>

#### **Binary, Octal, and Hexadecimal**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- | Decimal         | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    |
  | :-------------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| **Binary**      | 0000 | 0001 | 0010 | 0011 | 0100 | 0101 | 0110 | 0111 | 1000 |
  | **Octal**       | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 10   |
| **Hexadecimal** | 0    | 1    | 2    | 3    | 4    | 5    | 6    | 7    | 8    |
  
- | Decimal         | 9    | 10   | 11   | 12   | 13   | 14   | 15   | 16    |
  | --------------- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ----- |
  | **Binary**      | 1001 | 1010 | 1011 | 1100 | 1101 | 1110 | 1111 | 10000 |
  | **Octal**       | 11   | 12   | 13   | 14   | 15   | 16   | 17   | 20    |
  | **Hexadecimal** | 9    | A    | B    | C    | D    | E    | F    | 10    |



<br/>

#### **If You Describe 5 with 8 Bits...**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- **0** (<- MSB: representing +/- sign)  **0  0  0  0  1  0  1**



<br/>

#### **What Is the Range of Numbers That You Can Describe with Bits?**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- **Numbers by 1 Bit:** 0, 1 (2 numbers)
- **Numbers by 2 Bits:** 00, 01, 10, 11 (4 numbers)
- **Numbers by 3 Bits:** 000, 001, 010, 011, 100, 101, 110, 111 (8 numbers)



<br/>

#### **Example**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- ```java
  package basic02;
  
  public class BinaryTest {
  
  	public static void main(String[] args) {
  		int num = 10;       // Decimal
  		int bNum = 0B1010;  // 0b - Binary
  		int oNum = 012;     // 0 - Octal
  		int xNum = 0XA;     // 0x - Hexadecimal
  		
  		System.out.println(num);
  		System.out.println(bNum);
  		System.out.println(oNum);
  		System.out.println(xNum);
  	}
  
  }
  ```

  