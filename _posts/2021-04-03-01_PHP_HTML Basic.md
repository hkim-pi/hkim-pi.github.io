---
layout: single
title: "01_PHP/HTML Basic"
categories: 
 - Pop Quiz
tags:
 - web
 - quiz
 - PHP
 - HTML
 - array
 - syntax
 - grammar

---

### *PHP/HTML Basic*



----------------------------------------------------------------------------------------------------------------------------------------------------------------

<br/>

<br/>

1. **<<<_END..._END; is the heredoc syntax. Can it be replaced by another letter instead of END?**

   ```
   Yes
   ```


 <br/>

2. **Are the names used in PHP case sensitive?**

   ```
   Yes
   ```

   <br/>

3. **Write a PHP program to print "Hello, World."**

   ```php
   <?php
    echo "Hello, World.";
   ?>
   ```

   <br/>

4. **Write a code in PHP which assigns an array to a variable named "myarray" and values "one", "two", and "three" to that array.**

   ```php
   $myarray = array("one", "two", "three"); 
   ```

   <br/>

5. **What is the output value of the following syntax following question number 4 above?**

   ```php
   echo $myarray[1]
       
   //-> two
   ```

<br/>

6. **What is the assigned value of the following variable?**

   ```php
   $result = 6/4;
   
   //-> 1.5
   ```

   <br/>

7. **What is printed as a result of the following syntax?**

   ```php
   echo "This is line " . __LINE__ . " of file " . __FILE__;
   
   //-> This is line <number(indicating the line of the php file)>
   //-> of file <path to the php file>
   ```

   <br/>

8. **What is printed as a result of the following syntax?**

   ```php
   <?php echo 2+3; echo '<br>'; echo '2+3'; ?>
       
   //-> 5
   //-> 2+3
   ```

   <br/>

9. **What are the two ways to display comments in PHP program?**

   ```php
   //
   /* */
   ```

   <br/>

10. **What is the difference between the operators "==" and "==="?**

    ```php
    ==
    //-> compares the values while...
    
    === 
    //-> compares the values and the types(objects).
    ```

    <br/>

11. **Why does the PHP syntax not allow variable names that contain "-" sign such as $var-name?**

    ```
    To avoid confusion with the "-" operator
    ```

    <br/>

12. **Can PHP store a string value in a variable after storing an integer value?**

    ```
    Yes
    ```

    <br/>

13. **Which keyword is used to point within a function to a variable defined outside the function?**

    ```php
    global
    ```

    <br/>

14. **Within a function, a variable is defined as follows. What additional effects does the "static $count" variable have?**

    ```php
    static $count = 0;
    
    //-> It is first initialized and does not disappear 
    //-> until the end of the program.
    ```

    <br/>

15. **What is the "superglobal" variable?**

    ```
    It's the variable that can be used anywhere/anytime in the program.
    ```

    <br/>

16. **Create an html document that prints "Hello, World. Again."**

    ```html
    <html>
     <head></head>
     <body>
     Hello, World. Again
     </body>
    </html>
    ```

    <br/>

17. **Which of the following statements is incorrect?**

    ```php
    /*1*/ $team = array(‘Kim’, ‘Lee’, ‘Choi’, ‘Park’);
    /*2*/ $friend = $team[2];
    /*3*/ $team = array(“Kim”, “Lee”);
    /*4*/ $team = array(array(‘a’), array(‘c’), array(‘e’));
    /*5*/ No answer(All correct)
    
    //-> 5
    ```

    <br/>

18. **What is the output value of the following program?**

    ```php
    <?php
     $var1 = 10;
     echo $var1 += $var1%9; 
    ?> 
    
    //-> 11
    ```

    <br/>

19. **What is the difference between the following two syntax?**

    ```php
    $info = 'Preface variables with a $ like this: $variable';
    $info = “Preface variables with a $ like this: $variable”;
    
    //-> In case of '', it outputs the value of $variable by evaluating it.
    ```

    <br/>

20. **The following syntax is invalid. Why doesn't it work?**

    ```php
    $text = 'My spelling's atroshus';    // wrong syntax
    
    //-> If you want to write ' in a string, you have to use \'.
    ```

    <br/>

21. **Modify the syntax of the above problem so that the string "My spelling's atroshus" can be assigned to the variable "$text".**

    ```php
    $text = 'My spelling\'s atroshus';
    ```

    <br/>

22. **What does the following program print?**

    ```php
    <?php
     $text = 'This is a text';
     echo substr($text, 3, 3);
    ?>
        
    //-> s i
    ```

<br/>

23. **What is the difference between "$s++" and ""++$s" ?**

    ```php
    $s++     
    //-> Postfix operator,
    //-> increasing last after the expression operates.
        
    ++$s
    //-> Prefix operator,
    //-> Increasing before the expression operates.
    ```

    <br/>

24. **What If you combine(add) string and number?**

    ```php
    string
    ```

    <br/>

25. **What does the following program print?**

    ```php
    <?php  
     echo "a: [" . TRUE . "]<br>";
     echo "b: [" . FALSE . "]<br>";
    ?>
    
    //-> a: [1]
    //-> b: []
    ```

    <br/>

26. **What does the following program print?**

    ```php
    <?php
     $myname = "Brian";
     $myage = 37;
     echo "a: " . 73 . "<br>"; 
     echo "b: " . "Hello" . "<br>"; 
     echo "c: " . FALSE . "<br>"; 
     echo "d: " . $myname . "<br>"; 
     print "e: " . $myage . "<br>"; 
    ?>
    
    //-> a: 73
    //-> b: Hello
    //-> c: 
    //-> d: Brian
    //-> e: 37
    ```

    <br/>

27. **What is the three keywords that make conditional statements?**

    ```php
    if
    switch
    ? :
    ```

    <br/>

28. **What does the following program print?**

    ```php
    <?php
     $a = "1000";
     $b = "+1000";
     if ($a == $b) echo "1";
     if ($a === $b) echo "2";
    ?>
        
    //-> 1
    ```

    <br/>

29. **What does the following syntax mean?**

    ```php
    break 2;
    
    //-> It means to escape 
    //-> the two-step(level) of 
    //-> condition statement/loop statement.
    ```

    <br/>

