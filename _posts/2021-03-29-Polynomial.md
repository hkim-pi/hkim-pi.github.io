---
layout: single
title: "Polynomial"
categories: 
 - Data Structures
 - C/C++
tags:
 - polynomial
 - C++
 - cpp
 - programming
 - data structure
---

### *Polynomial*

#### Using C++


<br/>
**polynomial.h [header file]**

```c++
#pragma once
#ifndef POLY_H
#define POLY_H
using namespace std;

class Polynomial; 
class Term {
	friend class Polynomial;
	friend ostream& operator<<(ostream&, Polynomial&);
	friend istream& operator>>(istream&, Polynomial&);
private:
	float coef;     // coefficient
	int exp;	    // exponent
};

class Polynomial {
public:
	Polynomial();                      // construct a polynomial p(x) = 0.
	Polynomial operator+(Polynomial&); // return sum of polynomial 
	void NewTerm(const float, const int);
	friend ostream& operator<<(ostream&, Polynomial&);
	friend istream& operator>>(istream&, Polynomial&);
private:
	Term* termArray;
	int capacity; // initialized to 1
	int terms;    // the number of saved terms, initialized to 0
};
#endif
```


<br/>
**polynomial.cpp [source file]**

```c++
#include <iostream>
#include "poly.h"
using namespace std;

istream& operator>> (istream& is, Polynomial& p) {
    // read in #terms and (coefficoent, exponent)'s pairs
    // suppose the terms are inputted in highest(higher) exponential order
    int noofterms; float coef; int exp;
    is >> noofterms;
    for (int i = 0; i < noofterms; i++) {
        is >> coef >> exp; // read in the pairs of coefficient and exponent
        p.NewTerm(coef, exp);
    }
    return is;
}

ostream& operator<<(ostream& os, Polynomial& p)
{
    for (int i = 0; i < p.terms; i++)
    {
        if (p.termArray[i].coef && p.termArray[i].coef != 1 && p.termArray[i].coef != -1)
            os << p.termArray[i].coef;
        if (p.termArray[i].exp != 0)
            os << "x^";
        if (p.termArray[i].exp && p.termArray[i].exp != 1)
            os << p.termArray[i].exp;
        if (i != p.terms - 1 && p.termArray[i + 1].coef >= 0)
            os << " +";
        else if (p.termArray[i + 1].coef == -1)
            os << " -";
        else if (p.termArray[i + 1].coef < -1)
            os << " ";
    }
    os << endl;
    return os;
}

Polynomial::Polynomial() :capacity(1), terms(0)
{
    termArray = new Term[capacity];
}

void Polynomial::NewTerm(const float theCoeff, const int theExp)
{   
    // add the new term at the end of termArray
    if (terms == capacity)
    {
        // expand the size of termArray twice
        capacity *= 2;
        Term* temp = new Term[capacity]; // new array
        copy(termArray, termArray + terms, temp);
        delete[]termArray; // return the previous memory
        termArray = temp;
    }
    termArray[terms].coef = theCoeff;
    termArray[terms++].exp = theExp;
}

Polynomial Polynomial::operator+(Polynomial& b)
{
    // return the sum of *this and b
    Polynomial c;
    int aPos = 0, bPos = 0;
    while ((aPos < terms) && (bPos < b.terms))
    {
        if (termArray[aPos].exp == b.termArray[bPos].exp)
        {
            float t = termArray[aPos].coef + b.termArray[bPos].coef;
            if (t)
                c.NewTerm(t, termArray[aPos].exp);
            aPos++;
            bPos++;
        }
        else if (termArray[aPos].exp < b.termArray[bPos].exp)
        {
            c.NewTerm(b.termArray[bPos].coef, b.termArray[bPos].exp);
            bPos++;
        }
        else
        {
            c.NewTerm(termArray[aPos].coef, termArray[aPos].exp);
            aPos++;
        }
    }
    // add the rest terms of *this
    for (; aPos < terms; aPos++)
        c.NewTerm(termArray[aPos].coef, termArray[aPos].exp);
    // add the rest terms of b(x)
    for (; bPos < b.terms; bPos++)
        c.NewTerm(b.termArray[bPos].coef, b.termArray[bPos].exp);
    return c;
}
```


<br/>
**polynomial_main.cpp [source file]**

```c++
#include <iostream>
using namespace std;
#include "poly.h"

int main() {
	Polynomial p1, p2;

	cin >> p1 >> p2; // read in two polynomial expressions
	Polynomial p3 = p1 + p2;
	cout << p1 << p2 << p3;
}
```

