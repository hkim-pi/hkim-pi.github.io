---
layout: single
title: "Postfix Evaluation"
categories: 
 - Data Structures
 - Cpp
tags:
 - postfix evaluation
 - C++
 - cpp
 - programming
 - data structure
---

### *Postfix  Evaluation*
#### Using C++
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


<br/>
<br/>
**postfix.h [header file]**

```c++
#ifndef POST_H
#define POST_H
// token types for non one-char tokens
#define ID		257
#define NUM		258
#define EQ		259
#define NE		260
#define GE		261
#define LE		262
#define AND		263
#define OR		264
#define UMINUS	265
#define MAXLEN	80

struct Expression
{
    Expression(char* s) : str(s), pos(0)
    {
        for (len = 0; str[len] != '\0'; len++);
    }
    char* str;
    int pos;
    int len;
};

struct Token
{
    bool operator==(char);
    bool operator!=(char);
    Token();
    Token(char);                    // 1-char token: type equals the token itself              
    Token(char, char, int);     	// 2-char token(e.g. <=) & its type(e.g. LE)
    Token(char*, int, int);         // operand with its length & type(defaulted to ID)
    bool IsOperand();               // true if the token type is ID or NUM
    int type;	                    // ascii code for 1-char op; predefined for other tokens
    char* str;	                    // token value
    int len;	                    // length of str
    int ival;                       // used to store an integer for type NUM; init to 0 for ID
};

using namespace std;
ostream& operator<<(ostream& os, Token t);
Token NextToken(Expression&, bool); // 2nd arg=true for infix expression
#endif
```


<br/>
**postfix.cpp [source file]**

```c++
#include <iostream>
#include <stack>
#include "postfix.h"
using namespace std;

bool Token::operator==(char b) { return len == 1 && str[0] == b; }
bool Token::operator!=(char b) { return len != 1 || str[0] != b; }
Token::Token() {}
Token::Token(char c) : len(1), type(c)
{
    str = new char[1]; str[0] = c;
} // default type = c itself
Token::Token(char c, char c2, int ty) : len(2), type(ty)
{
    str = new char[2]; str[0] = c; str[1] = c2;
}
Token::Token(char* arr, int l, int ty = ID) : len(l), type(ty) {
    str = new char[len + 1];
    for (int i = 0; i < len; i++) str[i] = arr[i];
    str[len] = '\0';
    if (type == NUM) {
        ival = arr[0] - '0';
        for (int i = 1; i < len; i++) ival = ival * 10 + arr[i] - '0';
    }
    else if (type == ID) ival = 0;
    else throw "must be ID or NUM";
}
bool Token::IsOperand() { return type == ID || type == NUM; }
ostream& operator<<(ostream& os, Token t) {
    if (t.type == UMINUS) os << "-u";
    else if (t.type == NUM) os << t.ival;
    else for (int i = 0; i < t.len; i++) os << t.str[i];
    os << " ";
    return os;
}

bool GetID(Expression& e, Token& tok)
{
    char arr[MAXLEN]; int idlen = 0;
    char c = e.str[e.pos];
    if (!(c >= 'a' && c <= 'z' || c >= 'A' && c <= 'Z')) return false;
    arr[idlen++] = c;
    e.pos++;
    while ((c = e.str[e.pos]) >= 'a' && c <= 'z'
        || c >= 'A' && c <= 'Z'
        || c >= '0' && c <= '9')
    {
        arr[idlen++] = c; e.pos++;
    }
    arr[idlen] = '\0';
    tok = Token(arr, idlen, ID); // return an ID
    return true;
}

bool GetInt(Expression& e, Token& tok)
{
    char arr[MAXLEN]; int idlen = 0;
    char c = e.str[e.pos];
    if (!(c >= '0' && c <= '9')) return false;
    arr[idlen++] = c;
    e.pos++;
    while ((c = e.str[e.pos]) >= '0' && c <= '9')
    {
        arr[idlen++] = c; e.pos++;
    }
    arr[idlen] = '\0';
    tok = Token(arr, idlen, NUM);
    return true;
}


void SkipBlanks(Expression& e)
{
    char c;
    while (e.pos < e.len && ((c = e.str[e.pos]) == ' ' || c == '\t'))
        e.pos++;
}

bool TwoCharOp(Expression& e, Token& tok)
{  // seven 2-char tokens: // <= >= == != && || -u
    char c = e.str[e.pos]; char c2 = e.str[e.pos + 1];
    int op; // LE GE EQ NE AND OR UMINUS
    if (c == '<' && c2 == '=') op = LE;
    else if (c == '>' && c2 == '=') op = GE;
    else if (c == '=' && c2 == '=') op = EQ;
    else if (c == '!' && c2 == '=') op = NE;
    else if (c == '&' && c2 == '&') op = AND;
    else if (c == '|' && c2 == '|') op = OR;
    else if (c == '-' && c2 == 'u') op = UMINUS;
    else
        return false; // if it's not the right 2-char token, return false

    tok = Token(c, c2, op); e.pos += 2;
    return true;
}

bool OneCharOp(Expression& e, Token& tok)
{
    char c = e.str[e.pos];
    if (c == '-' || c == '!' || c == '*' || c == '/' || c == '%' ||
        c == '+' || c == '<' || c == '>' || c == '(' || c == ')' || c == '=')
    {
        tok = Token(c); e.pos++; return true;
    }
    return false;
}

Token NextToken(Expression& e, bool INFIX = true)
{
    static bool oprrFound = true; // suppose the operator has been found before end
    Token tok;
    SkipBlanks(e); // skip blanks if any
    if (e.pos == e.len) // no more token left in this expression
    {
        if (INFIX) oprrFound = true; return Token('#');
    }
    if (GetID(e, tok) || GetInt(e, tok))
    {
        if (INFIX) oprrFound = false; return tok;
    }
    if (TwoCharOp(e, tok) || OneCharOp(e, tok)) {
        if (tok.type == '-' && INFIX && oprrFound) // after operator '-' is found
            tok = Token('-', 'u', UMINUS); // change it to unary minus(-u)
        if (INFIX) oprrFound = true; return tok;
    }
    throw "Illegal Character Found";
}

int icp(Token& t) { // in-coming priority
    int ty = t.type;
    if (ty == '(') return 0;
    else if (ty == UMINUS || ty == '!') return 1;
    else if (ty == '*' || ty == '/' || ty == '%') return 2;
    else if (ty == '+' || ty == '-') return 3;
    else if (ty == '<' || ty == '>' || ty == LE || ty == GE) return 4;
    else if (ty == EQ || ty == NE) return 5;
    else if (ty == AND) return 6;
    else if (ty == OR) return 7;
    else if (ty == '=') return 8;
    else if (ty == '#') return 9;
}

int isp(Token& t) {
    // in-stack priority
    int ty = t.type;
    if (ty == '(') return 9;
    else if (ty == UMINUS || ty == '!') return 1;
    else if (ty == '*' || ty == '/' || ty == '%') return 2;
    else if (ty == '+' || ty == '-') return 3;
    else if (ty == '<' || ty == '>' || ty == LE || ty == GE) return 4;
    else if (ty == EQ || ty == NE) return 5;
    else if (ty == AND) return 6;
    else if (ty == OR) return 7;
    else if (ty == '=') return 8;
    else if (ty == '#') return 9;
}

void Postfix(Expression e) {
    stack<Token> stack;
    stack.push('#');
    for (Token x = NextToken(e); x != '#'; x = NextToken(e))
    {
        if (x.IsOperand()) cout << x;
        else if (x == ')')
        {
            for (; stack.top() != '('; stack.pop())
                cout << stack.top();
            stack.pop();
        }
        else
        {
            for (; isp(stack.top()) <= icp(x); stack.pop()) {
                if (x == '=' && stack.top() == '=') break;
                cout << stack.top();
            }
            stack.push(x);
        }
    }
    while (stack.top() != '#') { cout << stack.top(); stack.pop(); }
    cout << endl;
}
```


<br/>
**posteval.cpp [source file]**

```c++
#include <iostream>
#include <stack>
#include "postfix.h"
using namespace std;

int GetVal(Token& opnd)
{
    if (opnd.type == NUM) return opnd.ival;
    return 0; // if it's ID, return 0
}

Token UnaryOp(int op, Token& x)
{ // only for the cases with UMINUS or ‘!’
    if (!x.IsOperand()) throw "Operand Only for Unary Operator";
    Token tmp; tmp.type = NUM;
    if (op == UMINUS) tmp.ival = -GetVal(x);
    else if (op == '!') tmp.ival = !GetVal(x);
    else throw "Invalid unary operator";
    return tmp;
}

Token BinaryOp(int op, Token& left, Token& right)
{
    if (!left.IsOperand() || !right.IsOperand())
        throw "Two Operands required for Binary Operation";
    Token tmp; tmp.type = NUM;
    int val1 = GetVal(left), val2 = GetVal(right);
    if (op == '+') tmp.ival = val1 + val2;
    else if (op == '-') tmp.ival = val1 - val2; 
    else if (op == '*') tmp.ival = val1 * val2; 
    else if (op == '/') tmp.ival = val1 / val2; 
    else if (op == '%') tmp.ival = val1 % val2; 
    else if (op == '<') tmp.ival = val1 < val2;
    else if (op == '>') tmp.ival = val1 > val2;
    else if (op == GE) tmp.ival = val1 >= val2;
    else if (op == LE) tmp.ival = val1 <= val2; 
    else if (op == EQ) tmp.ival = val1 == val2;
    else if (op == NE) tmp.ival = val1 != val2;  
    else if (op == AND) tmp.ival = val1 == val2; 
    else if (op == OR) tmp.ival = val1 || val2;  

    else if (op == '=') throw "Assignment Not Yet Implemented";

    else throw "No such binary operator";
    return tmp;
}

Token DeleteFromStack(stack<Token>& stack)
{ // get the top of the stack and return
    if (stack.empty()) throw "Trying to pop from an empty stack";
    Token tmp = stack.top();
    stack.pop();
    return tmp;
}

void Eval(Expression e)
{ // accept a postfix expression as an input and calculate the value
    stack<Token> stack;
    Token opnd1, opnd2;
    for (Token x = NextToken(e, false); x != '#'; x = NextToken(e, false)) 
        if (x.IsOperand()) stack.push(x);
        else { // x is an operator
            if (x.type == UMINUS || x.type == '!') { // unary operator
                opnd1 = DeleteFromStack(stack);
                stack.push(UnaryOp(x.type, opnd1));
            }
            else { // binary operator
                opnd2 = DeleteFromStack(stack);   
                opnd1 = DeleteFromStack(stack);   
                stack.push(BinaryOp(x.type, opnd1, opnd2));   
            }
        }
    cout << DeleteFromStack(stack) << endl; // print the final calculation result
}
```


<br/>
**posteval_main.cpp [source file]**

```c++
#include <iostream>
#include "postfix.h"
using namespace std;
void Eval(Expression);

int main(void)
{
    char line[MAXLEN];
    while (cin.getline(line, MAXLEN))
    {
        Expression e(line); // assume postfix notation
        try
        {
            Eval(e);
        }
        catch (char const* msg)
        {
            cerr << "Exception: " << msg << endl;
        }
    }
}
```

