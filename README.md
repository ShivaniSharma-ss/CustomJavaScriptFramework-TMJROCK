# CustomJavaScriptFramework-TMJROCK

Created a JavaScript framework, that reliefs programmers from client end programming, AJAX programming and form validation.This framework provides many useful UI Components like
Accordian, Modal, fillComboBox etc.

## Features:
1) User can create modal in very easy way.
2) User can create accordian pan in very simple way.
3) User can fill combobox by writing a very little code.
4) User able to do form validation by writing a some lines code.
5) Handle ajax GET and POST request.

## Steps to use this framework:-
1) Extract the zip File.
2) include this JS and CSS file:
````
<script src='js/framework.js'></script>
<link rel="stylesheet" href="css/framework_style.css">
````
3) Copy/cut web.xml to tomcat9/Webapps/"Project Name"/WEB-INF/.
4) Then start the tomcat server and go to any browser and type localhost:8080/ProjectName/resourceFileName
Example : localhost:8080/TMJRock/ModalExample.html

# POST Type Request Example

<body>
<h1>Post type request Example</h1> 
<label>First Name </label><br><input type='text' id='firstName'><br><br>
<label>Last Name </label><br><input type='text' id='lastName'><br><br>
<label>Age </label><br><input type='text' id='age'><br><br>
<button type='button' onclick='saveEnquiry()'>Save</button><br>
<br>
<div id='whatever'></div>
</body>





