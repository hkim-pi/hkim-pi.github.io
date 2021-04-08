---
layout: single
title: "Basic_04_Data Type - How to Express Integers"
categories: 
 - Java
tags:
 - java
 - web
 - basic
 - programming
 - data type
 - int
 - long
 - short
 - byte
 - integer
---

### *Data Type - How to Express Integers*



<br/>

<br/>

#### **Variables and Memories**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- **Declaring a Variable Allocates as Much Memory as the Corresponding Data Type**

- **Variable Is a Name That Points to Allocated Memory**

- ```java
  int level = 10;
  
  // Four bytes of integer memory allocated 
  // under the name 'level'
  ```



<br/>

#### **Primitive Data Types**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- |        | Integer Type | Character Type | Real Type | Logical Type |
       | :----: | :----------: | :------------: | :-------: | :----------: |
  | 1 byte |     byte     |       -        |     -     |   boolean    |
  | 2 byte |    short     |      char      |     -     |      -       |
  | 4 byte |     int      |       -        |   float   |      -       |
  | 8 byte |     long     |       -        |  double   |      -       |



<br/>

#### **Types and Sizes of Integer Data Types**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- | Data Type | Byte | Range of Numbers |
  | :-------: | :--: | :--------------: |
  |   byte    |  1   |  -2^7 ~ 2^7 - 1  |
  |   short   |  2   | -2^15 ~ 2^15 - 1 |
  |    int    |  4   | -2^31 ~ 2^31 - 1 |
  |   long    |  8   | -2^63 ~ 2^63 - 1 |
  
- **Describing 10 with int**

  **0**(<- a bit for +/- sign) **0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 1 0 1 0** (32 bits)



<br/>

#### **byte and short**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- **byte:** 1-byte data type, used to process data in videos, music files, and executables
- **short:** 2-byte data type, used when compatible with C/C++ language



<br/>

#### **int**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- **Default Data Type for Integers Used in Java**
- **4-byte Data Type**
- **All Numbers (Literals) Used in Programs Are Stored as int**
- **Numbers Exceeding 32 Bits Must Be Handled as long Data Types**



<br/>

#### **long**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- **8-byte Data Type**
- **Write the Letter 'L' or 'l' After the Number to Indicate That It Is long**



<br/>

#### **Example**

----------------------------------------------------------------------------------------------------------------------------------------------------------------

- ```java
  package basic04;
  
  public class VariableTest {
  
  	public static void main(String[] args) {
  		
  		// byte bnum = 128; //-> error
  		byte bnum = 127;
  		System.out.println(bnum);
  		
  		// int num = 12345678900;   //-> error
  		// long lNum = 12345678900; //-> error
  		long lNum = 12345678900L;
  		System.out.println(lNum);
   
  	}
  
  }
  ```

  



