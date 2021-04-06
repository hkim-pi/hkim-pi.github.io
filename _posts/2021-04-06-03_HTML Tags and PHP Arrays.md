---
layout: single
title: "03_HTML Tags and PHP Arrays"
categories: 
 - Pop Quiz
tags:
 - web
 - HTML
 - PHP
 - tag
 - input
 - form
 - array
 - property
---

### *HTML Tags and PHP Arrays*



----------------------------------------------------------------------------------------------------------------------------------------------------------------

<br/>

<br/>

**Watch the following program(upload.php) and answer the questions.**

```php
<?php // upload.php
 echo <<<_END
 	<html><head><title>PHP Form Upload</title></head><body>
 	<form method='post' action='upload.php' 
		          enctype='multipart/form-data'>
    	Select File: <input type='file' name='filename' size='10'>
 		<input type='submit' value='Upload'>
 	</form>
 _END;
 if ($_FILES)
 {
 	$name = $_FILES['filename']['name'];
	move_uploaded_file($_FILES['filename']['tmp_name'], $name);
	echo "Uploaded image '$name'<br><img src='$name'>";
 }
 echo "</body></html>";
?>
```

<br/>

1. **How many times are the above programs called?**

   ```
   Twice
   ```

   <br/>

2. **What does the above program do when it is first called? Write down exactly what you initially send to your web browser as a result of running "upload.php"(client) on the web server.**

   ```php
   //-> HTML resource containing form part, specifically:
   
   <html><head><title>PHP Form Upload</title></head><body> 
       <form method='post' action='upload.php' 
                        enctype='multipart/form-data'>
         Select File: <input type='file' name='filename' size='10'>
         <input type='submit' value='Upload'>
       </form>
   </body></html>
   ```

   <br/>

3. **When is the above program called back again?**

   ```
   When you click the Upload button after 
   specifying the file in the client, or browser.
   ```

   <br/>

4. **The program contains basic HTML document. A "form" tag does not show what is rendered specifically, but it specifies that a web browser should prepare a form such as the "input" type defined in the "form" tag. Among the attributes of this "form" tag, the method attribute must be specified, but the program above says only "method = 'post'". Briefly describe the meaning of this in relation to the HTTP protocol.**

   ```
   Send http requests in the "POST" method defined in the 
   HTTP protocol by storing them in the http request body 
   part without including information from data resources 
   in the URL.
   ```

   <br/>

5. **What is the attribute in the "form" tag that shows that the above program will be called back if the event mentioned in question 3 occurs?**

   ```html
   action='upload.php'
   ```

   <br/>

6. **In the "form" tag above, the "input" tag is used to indicate that a user can draw a form that can be entered in a web browser. However, the string "Select File:" can be found outside the inside of the "form" or "input" tag. Does this string appear drawn in a web browser?**

   ```
   Yes
   ```

   <br/>

7. **The "input" tag above specifies the type attribute. In other words, the "input" tag calls for creating a device that allows browser users to draw and receive data, and for us we have "type='file'" for allowing files to be entered. Can the value of the type attribute of the "input" tag be written arbitrarily? Or are certain values specified in the HTML5 standard?**

   ```
   In addition to file types, various types of input 
   are defined, such as text and buttons. (Not random)
   
   // refer to the page below.
   // https://www.w3schools.com/html/html_form_input_types.asp
   ```

   <br/>

8. **The "input" tag above shows an attribute called name. This attribute is an attribute that identifies the specific "input" to which this particular attribute belongs. This is the attribute used to name a particular "input". If you have two identical types of "input", how do you use name attribute to distinguish between these different "input"s?**
   
   ```
   Specify name differently.
   ```
   
<br/>
   
9. **"Form" or "input" should be prepared in the browser to perform "form" or "input" functions in addition to simply drawing from the browser. As such, "form" or "input" in HTML documents are implemented in a variety of (complex) properties and methods, in addition to simply being pictured. Thus, such HTML5 documents are models of HTML documents, which are called Document ___ Model. Write the appropriate term to underline.**

   ```
   Object
   ```

   <br/>

10. **When we study PHP classes, each class instance is called an object, and a new object is assigned to a variable so that different variables point to different objects. Look at the program above and briefly describe how to distinguish objects, which are the components that make up HTML documents, from each other.**

    ```
    The program above utilizes name attribute.
    ```

    <br/>

11. **The component of HTML is one of the objects defined as standard in HTML without exception. HTML documents are descriptive of HTML objects, and different types of objects are required to have attributes to define each object. In the program above, the "input" object is distinguished by specifying a proper value in the name object, so is there only a name attribute in the attribute that distinguishes each object, and can other attributes be used to identify the object?**

    ```
    You can also use attributes such as "id". Alternatively, 
    if CSS is applied to an object, the object can be 
    identified through the css selector.
    ```

    <br/>

12. **Is there an attribute specified to refer to the second "input" object in the program above?**

    ```
    There is no separate attribute, but it can be 
    identified by the <input> tag.
    ```

    <br/>

13. **What are the values specified in the type of the second "input" object above and what function does the "input" given these values perform?**

    ```
    A submit type is specified.It submits saved input data 
    from the browser through input fields in the form tag 
    to the web server and requests programs specified as 
    the value of the action attribute of the form tag 
    to run on the web server.
    ```

    <br/>

14. **The program that performs the same functions as question 13 above is not implemented in our PHP program. Where are these implemented to run?**

    ```
    On the web browser program itself.
    ```

    <br/>

15. **When "upload.php" program is called again, unlike when it was called for the first time, somebody said that heredoc "echo<<< ... _END;" does not practice. Is it right or wrong?**

    ```
    Wrong
    ```

    <br/>

16. **When the "upload.php" program is first called, the "if ($FILES)" syntax is executed, but the body of the "if ($FILES)" syntax is not executed. That is, the value of "$FILES" is not evaluated to TRUE when first called. Why?**

    ```
    "$_FILES" does not have a specified value 
    because no file attachment occurred.
    ```

    <br/>

17. **What's the so-called variable for "$FILES" in question 16 above?**

    ```php
    superglobals
    ```

    <br/>

18. **The second time "upload.php" program is executed, the body of the "if ($FILES)" syntax is executed, because of course the value of the "$FILES" variable is evaluated to TRUE. Specifically explain why the value of the "$FILES" variable is evaluated to TRUE when called the second time.**

    ```
    Uploading a file through a browser resulted in 
    specified data (files) in "$_FILES".
    ```

    <br/>

19. **The "upload.php" program is a program that uploads files in the computer that browser operates to a web server that is equipped with the "upload.php" program. In our case, which directory on the web server is it stored in?**

    ```
    Apache web server www directory
    ```

    <br/>

20. **Can you tell from the following syntax what dimension array is the "$FILES" variable?**

    ```php
    $name = $_FILES['filename']['name']; 
    
    //-> Two dimension array
    ```
    
    <br/>
    
21. **The first index of "$FILES" "['filename']" shows that it is an associative array. Write down where the "['filename']" used for the upload.php program, which was also used as an associative index.**

    ```php
    $name = $_FILES['myname']['name'];
    move_uploaded_file($_FILES['filename']['tmp_name'], $name);
    ```

    <br/>

22. **If the "upload.php" program used the value "myname" instead of the value "filename", considering the above issue of question 21 how should the following syntax be fixed to work properly?**

    ```php
    $_FILES['filename']['name']
        
    //-> 
    $_FILES['myname']['name']
    ```

    <br/>

23. **What we have seen so far is that the first index of "$FILES" array is that we can designate the appropriate string at our convenience. However, since the second index is an array with an object pointing to the file that "$FILES" array received from the browser, it cannot use any value because the particular properties of the file it receives must be separated into a second index. Which of the following is invalid "$FILES" elements, including undefined indexes?**

    ```php
    /*1*/ $_FILES['file']['name']
    /*2*/ $_FILES['file']['type']
    /*3*/ $_FILES['file']['tmp_name']
    /*4*/ $_FILES['file']['size']
    /*5*/ $_FILES['file']['owner']
     
    //-> 5
    ```

    <br/>
