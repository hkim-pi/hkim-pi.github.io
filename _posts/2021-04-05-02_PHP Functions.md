---
layout: single
title: "02_PHP Functions"
categories: 
 - Pop Quiz
tags:
 - web
 - PHP
 - function
 - class
 - inheritance
 - property
 - access
 - constructor
 - destructor
 - array
 - file
 - key
---

### *PHP Functions*



----------------------------------------------------------------------------------------------------------------------------------------------------------------

<br/>

<br/>

1. **If you operate the "phpinfo()" function, the screen as shown in the picture below is printed on the browser. Using the "phpinfo()" function, write a simple program that outputs the screen shown in the picture below.**

   ![](C:\Users\Hannah\Desktop\github_posts\Pop Quiz\phpinfo.JPG)

```php
<?php
 phpinfo();
?>
```

<br/>

2. **How many values can PHP function return?**

   ```
   One, but return of multiple values is possible 
   using arrays, reference, or global variables, etc.
   ```

   <br/>

3. **The following syntax defines a class' subclass. Fill in the blank.**

   ```
   class Subclass ________ Parentclass ...
   
   //-> extends
   ```

   <br/>

4. **What is "__construct" method, and how can you use it?**

   ```php
   /* When you create an object which is an instance of a 
   class using a new operator, it is automatically called 
   and creates an object defined in the constructor. 
   The name of the function is defined as __construct 
   and called after the object is created to initialize 
   the values of member variable. */
   
   function __construct() {}
   ```

   <br/>

5. **What is the output of the following program?**

   ```php
   <?php
    echo strrev(" .dlrow olleH"); echo ‘<br>’;
    echo str_repeat("Hip ", 2); echo ‘<br>’;
    echo strtoupper("hooray!"); 
   ?>
   
   //-> Hello world.
   //-> Hip Hip
   //-> HOORAY!
   ```

   <br/>

6. **Are the names of PHP functions case sensitive?**

   ```
   No, they are case insensitive.
   ```

   <br/>

7. **What is "ucfirst()" function?**

   ```
   Capitalizes the first letter of a string.
   ```

   <br/>

8. **The following program prints the result as follows. Fill in the blanks in the program.**

   ```php
   //-> William Henry Gates   // result
   
   // program
   <?php
    $names = fix_names("WILLIAM", "henry", "gatES");
    echo $names[0] . " " . $names[1] . " " . $names[2];
    function fix_names($n1, $n2, $n3)
    {
    $n1 = ___(1)____(_____(2)_____($n1));
    $n2 = ___(1)____(_____(2)_____($n2));
    $n3 = ___(1)____(_____(2)_____($n3));
    return array($n1, $n2, $n3);
    }
   ?>
   
   //-> 1) ucfirst, 2) strtolower
   ```

   <br/>

9. **What is the difference between "include_once " and "require_once"?**

   ```php
   include_once 
   //-> Run program even if the file containing php is not found.
   
   require_once
   //-> Include only once and return error 
   //-> if the file is not found.
   ```

   <br/>

10. **What is "print_r()" function?**

    ```
    A function that prints data in human-readable form, 
    which is originally recognized only by the system and 
    is difficult for humans to read, such as an object.
    ```

    <br/>

11. **Which of the following statements does the following program print?**

    ```php
    <?php
     $object = new User;
     print_r($object);
     class User
     {
     public $name = 'James', $password = 'passwd';
     	function save_user()
     	{
     		echo "Save User code goes here";
     	}
     }
    ?>
        
    /*1*/ // User Object ( [name] => James [password] => passwd )
    /*2*/ // User Object ( [name] => [password] => )
    /*3*/ // User Object  
    /*4*/ // User Object ( James, passwd )
    
    //-> 1
    ```

    <br/>
    
12. **What does the following program print?**

    ```php
    <?php
     $object1 = new User();
     $object1->name = "Alice";
     $object2 = $object1;
     $object2->name = "Amy";
     echo "object1 name = " . $object1->name . "<br>";
     echo "object2 name = " . $object2->name;
     class User
     { public $name;
     }
    ?>
        
    //-> object1 name = Amy
    //-> object2 name = Amy
    ```

    <br/>

13. **In question 12 above, the object pointed by the variable "$object2" created by the syntax "$object2 = $object1;" creates an object other than the previous "$object1", but the property values of these newly created objects are equal to those of "$object1". Is this right? Briefly explain this.**

    ```
    It's not made separately. $object2 refers to 
    the same two objects that $object1 points to.
    ```

    <br/>

14. **What is "constructor" method?**

    ```
    A function that is automatically called and 
    creates objects defined in the constructor 
    when you create an object which is an instance 
    of a class using new operator.
    ```

    <br/>

15. **It is a construction method of a class. Fill in the blanks in the program.**

    ```php
    <?php
     class User
     {
     	function _____________($param1, $param2)
     	{
    	 // Constructor statements go here
     	public $username = "Guest";
     	}
     }
    ?>
    
    //-> __constructor
    ```

    <br/>

16. **What is "destructor" method?**

    ```
    Destructor, returning memory allocated 
    to the object
    ```

    <br/>

17. **What is the name of destructor method in PHP?**

    ```php
    __destructor
    ```

    <br/>

18. **Fill in the blanks in the following program.**

    ```php
    <?php
     $object = new User;
     $object->password = "secret";
     echo $object->get_password();
     
     class User
     {
     	public $name, $password;
    	 function get_password()
     	{
     		return _____password;
     	}	
     }
    ?>
        
    //-> this->
    ```

    <br/>

19. **The following are the methods for defining a class' property. After the comment mark "//", mark the underlined part as valid if the definition method is correct or invalid if it is incorrect.**

    ```php
    <?php
    class Test
    {
    	public $name = "Paul Smith"; // valid
    	public $age = 42; // valid
    	public $time = time(); // invalid
    	public $score = $level * 2; // invalid
     }
    ?>
    ```

    <br/>

20. **What is "static" method?**

    ```
    A function that calls objects of class 
    without creating it.
    ```

    <br/>

21. **Fill in the blanks in the following program.**

    ```php
    <?php
    Translate::lookup();
    class Translate
    {
    	const ENGLISH = 0;
    	const SPANISH = 1;
    	const FRENCH = 2;
    	const GERMAN = 3;
    	// ...
     	______ function lookup()
    	{
    		 echo self::SPANISH;
    	}
    }
    ?>
    
    //-> static
    ```

    <br/>

22. **What is the difference between the syntax "$object2 = $object1;" and "$object2 = clone $object1;"?**

    ```php
    $object2 = $object1;
    //-> One object is referenced by two pointers.
    
    $object2 = clone $object1;
    //-> Each cloned object is referenced by each pointer.
    ```

    <br/>

23. **There are three scopes of PHP class' property. List and briefly write down the extent of each scope.**

    ```php
    public
    //-> Accessible from anywhere
    
    protected
    //-> Accessible from subclass class 
    //-> and its own class only
    
    private
    //-> Accessible from its own class only
    ```

    <br/>

24. **When can it be typically convenient if using static properties?**

    ```
    The program starts and tries to save 
    which/how many function has been called so far.
    ```

    <br/>

25. **What is "inheritance"?**

    ```
    When creating a child class that inherits 
    the properties and methods of the parent class, 
    it creates a subclass.
    ```

    <br/>

26. **Which keyword refers directly to the parent class?**

    ```php
    parent
    ```

    <br/>

27. **What does it mean when you create final methods using the keyword "final"?**

    ```
    It means that you use final keyword before name 
    when creating a method that does not allow 
    subclasses to modify that method.
    ```

    <br/>

28. **Write down the four array designations in one line.**

    ```php
    $paper[] = "Copier";
    $paper[] = "Inkjet";
    $paper[] = "Laser";
    $paper[] = "Photo";
    
    //-> $paper = array("Copier", "Inkjet", "Laser", "Photo");
    ```

    <br/>

29. **Are the four statements in question 28 above the same as the following statements? Why?**

    ```php
    $paper[0] = "Copier";
    $paper[2] = "Inkjet";
    $paper[1] = "Laser";
    $paper[3] = "Photo";
    
    //-> Not the same. The index in question 
    //-> is not equal because it is 0, 1, 2, 3, 
    //-> not 0, 1, 2, 3.
    ```

    <br/>

30. **The sociological array is a very convenient function. Why is it convenient?**

    ```
    If it is indexed numerically, it is difficult 
    for programmers to remember which elements of 
    the array contain which data.
    (The disadvantage of it is that it takes 
    longer to find the element.)
    ```

    <br/>

31. **What is the output of the following program?**

    ```php
    <?php
     $paper[] = "Copier";
     $paper[] = "Inkjet";
     $paper[] = "Laser";
     $paper[] = "Photo";
     print_r($paper);
    ?>
    
    //-> Array ( [0] => Copier [1] => Inkjet [2] => Laser [3] => Photo )
    ```

    <br/>

32. **What is the output of the following program?**

    ```php
    <?php
     $paper['copier'] = "Copier & Multipurpose";
     $paper['inkjet'] = "Inkjet Printer";
     $paper['laser'] = "Laser Printer";
     $paper['photo'] = "Photographic Paper";
     print_r($paper);
    ?>
    
    //-> Array ( [copier] => Copier & Multipurpose [inkjet] => Inkjet Printer [laser] => Laser 
    //-> Printer [photo] => Photographic Paper )
    ```

    <br/>

33. **The following program specifies elements of an array using associative keys. Fill in the blanks using "copier", "inkjet", "laser", and "photo" as each key, respectively.**

    ```php
    <?php
     $p2 = array(
        ___________ "Copier & Multipurpose",
     	___________ "Inkjet Printer",
     	___________ "Laser Printer",
     	___________ "Photographic Paper");
    ?>
        
    //-> 'copier' => 
    //-> 'inkjet' => 
    //-> 'laser' => 
    //-> 'photo' =>
    ```

    <br/>

34. **Fill in the blanks in the following program.**

    ```php
    $paper = array("Copier", "Inkjet", "Laser", "Photo");
    $j = 0;
    foreach(_________________)
    {
     echo "$item<br>";
     ++$j;
    }
    
    //-> $paper as $item
    ```

    <br/>

35. **Fill in the blanks in the following program.**

    ```php
    $paper = array(
        'copier' => "Copier & Multipurpose",
    	'inkjet' => "Inkjet Printer",
    	'laser' => "Laser Printer",
    	'photo' => "Photographic Paper");
    foreach(echo _________________________ )
    
    //-> "$paper: $description<br>";
    ```

    <br/>

36. **Fill in the blanks in the following program.**

    ```php
    echo (is_array($fred)) _(1)_ "Is an array"
                           _(2)_ "Is not an array";
    
    //-> 1) ?
    //-> 2) :
    ```

    <br/>

37. **The following program prints the result as follows. Fill in the blanks in the program.**

    ```php
    //-> Array ( [0] => This [1] => is [2] => a [3] => 
    //-> sentence [4] => with [5] => seven [6] 
    //-> => words )              // result
    
    <?php
     $temp = _______(' ', "This is a sentence with seven words");
     print_r($temp);
    ?>
    
    //-> explode
    ```

    <br/>

38. **The following program prints the result as follows. Fill in the blanks in the program.**

    ```php
    //-> Array ( [0] => A [1] => sentence [2] 
    //->       => with [3] => asterisks )
    // result
    
    <?php
     $temp = __(1)__( _(2)_, "A***sentence***with***asterisks");
     print_r($temp);
    ?>
    
    //-> 1) explode
    //-> 2) '***'
    ```

    <br/>

39. **What is the PHP function that returns the last element of an array?**

    ```php
    end()
    ```

    <br/>

40. **Fill in the blanks in the following program that outputs the current time.**

    ```php
    echo __(1)__("l F jS, Y - g:ia", __(2)__);
    
    //-> 1) date
    //-> 2) time()
    ```

    <br/>

    **Watch the following program and answer questions 41 to 44.**

    ```php
    <?php
    $fh = fopen("testfile.txt", 'w') 
            or die("Failed to create file");
    $text = <<<_END
    Line 1
    Line 2
    Line 3
    _END;
    fwrite($fh, $text) 
             or die("Could not write to file");
    fclose($fh);
     
    $fh = fopen("testfile.txt", 'r') 
             or die("Failed to open file");
    $file_content= fread($fh, filesize("testfile.txt")) 
                              or die("Failed to read");
    fclose($fh);
    echo $file_content; 
    ?>
    ```

    <br/>

41. **What doew 'w' mean in "fopen("testfile.txt", 'w')"?**

    ```
    Mode: write only
    Pointer location: beginning of file
    
    If file exists: delete its contents 
    If file doesn't exist: create a new file
    ```

    <br/>

42. **What doew 'r' mean in "fopen("testfile.txt", 'r')"?**

    ```
    Mode: read only
    Pointer location: beginning of file
    
    If file exists/doesn't exist: 
                  preserve its contents
    ```

    <br/>

43. **What is the fucntion "filesize("testfile.txt")"? What does it return?**

    ```
    It returns the byte size of the file 
    to an integer value.
    ```

    <br/>

44. **Write down what the program above prints out.**

    ```
    Line 1 Line 2 Line 3
    ```

    <br/>

