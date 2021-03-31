---
layout: single
title: "Rectangle"
categories: 
 - Data Structures
tags:
 - rectangle
 - class
 - operator overloading
 - C++
 - data structure
---

### *Rectangle_Class  Implementation & Operator Overloading*

#### Using C++



**rectangle.h [header file]**

```c++
#ifndef RECTANGLE_H
#define RECTANGLE_H
using namespace std;

class Rectangle {
public:
	Rectangle(int, int, int, int);  // constructor
	~Rectangle();                   // destructor
	void Print();
	int Area();
	bool LessThan(Rectangle&);
	bool Equal(Rectangle&);
	int GetHeight();
	int GetWidth();

	//operator overloading
	bool operator<(Rectangle&);
	bool operator==(Rectangle&);
	friend ostream& operator<<(ostream&, Rectangle&);

private:
	int xLow, yLow, height, width;
};

#endif
```



**rectangle.cpp [source file]**

```c++
#include <iostream>
#include "rectangle.h"
using namespace std;

Rectangle::Rectangle(int x = 0, int y = 0, int h = 0, int w = 0)
	: xLow(x), yLow(y), height(h), width(w) { }
Rectangle::~Rectangle(){ }

void Rectangle::Print()
{
	cout << "xLow: " << xLow << ", ";
	cout << "yLow: " << yLow << ", ";
	cout << "height: " << height << ", ";
	cout << "width: " << width << endl;
}

int Rectangle::Area()
{
	return width * height;
}

bool Rectangle::LessThan(Rectangle& s)
{
	if(Area() < s.Area()) return true;
	else return false;
}

bool Rectangle::Equal(Rectangle& s)
{
	if (this == &s) return true;
	return (xLow == s.xLow) && (yLow == s.yLow) && (height == s.height) && (width == s.width);
}

int Rectangle::GetHeight() 
{ 
	return height; 
}

int Rectangle::GetWidth() 
{ 
	return width; 
}

ostream& operator<<(ostream& os, Rectangle& s)
{
	// print the values of member variables of Rectangle s in accordance with the format
	os << "xLow: " << s.xLow << ", ";
	os << "yLow: " << s.yLow << ", ";
	os << "height: " << s.height << ", ";
	os << "width: " << s.width << endl;

	return os;
}
bool Rectangle::operator<(Rectangle& s)
{
	if (Area() < s.Area()) return true;
	else return false;
}
bool Rectangle::operator==(Rectangle& s)
{
	if (this == &s) return true;
	return (xLow == s.xLow) && (yLow == s.yLow) && (height == s.height) && (width == s.width);
}
```



**rectangle_main.cpp [source file]**

```c++
#include <iostream>
#include "rectangle.h"
using namespace std;

int main() {
	Rectangle r(2, 3, 4, 6), s(1, 2, 6, 6);

	cout << "<rectangle r> "; r.Print();
	cout << "<rectangle s> "; s.Print();
	if (r.LessThan(s))
		cout << "s is bigger";
	else if (r.Equal(s))
		cout << "Same Size";
	else cout << "r is bigger";
	cout << endl;

	if (r.Area() > s.Area())
		cout << "r has greater area";
	else if (r.Area() == s.Area())
		cout << "same area";
	else
		cout << "s has greater area";

	cout << endl;
	cout << endl;

	// using operator overloading code
	cout << "<rectangle r> " << r;
	cout << "<rectangle s> " << s;
	if (r < s)
		cout << "s is bigger";
	else if (r == s)
		cout << "Same Size";
	else cout << "r is bigger";
	cout << endl;

}
```

