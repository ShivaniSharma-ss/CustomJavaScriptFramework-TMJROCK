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


###  POST type request Example :

````
<script>
function saveEnquiry()
{
var firstName=$$$("firstName").value();
var lastName=$$$("lastName").value();
var age=$$$("age").value();
var customer={
"firstName" : firstName,
"lastName" :  lastName,
"age" : age
};
var whatever=$$$("whatever");
whatever.html("");
$$$.ajax({
"methodType":"POST",
"url":"servletThree",
"data":customer,
"sendJSON":true,
"success":function(responseData){
var customer=JSON.parse(responseData);
var a="First Name: "+customer.firstName+"<br>";
a=a+"Last Name: "+customer.lastName+"<br>";
a=a+"Age: "+customer.age;
whatever.html(a);
},
"failure":function(){
alert("Some problem");
}
});
}
</script>
````

````
<body>
<h1>Post type request Example</h1> 
<label>First Name </label><br><input type='text' id='firstName'><br><br>
<label>Last Name </label><br><input type='text' id='lastName'><br><br>
<label>Age </label><br><input type='text' id='age'><br><br>
<button type='button' onclick='saveEnquiry()'>Save</button><br>
<br>
<div id='whatever'></div>
</body>
````

### Output : 

![Screenshot (627)](https://user-images.githubusercontent.com/69362478/124371134-7e7c0d00-dc9c-11eb-82d5-1f7c7558c4dd.png)

### Get Type Request Example : 

````
<script>
function getDesignation()
{
let titleSpan=$$$("title");
titleSpan.html("");
let code=$$$("code").value();
$$$.ajax({
"url":"servletTwo",
"data":{
"code":code
},
"methodType":"GET",
"success":function(responseData){
// code 
},
"failure":function(){
//code
}
});
}
</script>
````

````
<h1>GET Type request with data Example</h1>
Enter code <input type='text' id='code'>
<button type='button' onclick='getDesignation()'>Get Designation</button><br>
<br>
Title <span id='title'></span>
<br>
<a href='index.html'>Home</a>
````
### Output : 

![Screenshot (626)](https://user-images.githubusercontent.com/69362478/124371218-27c30300-dc9d-11eb-81cf-e0f9896380d0.png)

### Form validation:
````
<script>
// TMJRock user script starts here
function doSomething()
{
return $$$("someForm").isValid({
"nm":{
"required":true,
"maxLength":20,
"errorPane":"nmErrorSection",
"errors":{
"required":"Name required",
"maxLength":"Name cannot exceed 20 characters"
}
},
"ad":{
"required":true,
"errorPane":"adErrorSection",
"errors":{
"required":"Address required"
}
},
"ct":{
"invalid":-1,
"errorPane":"ctErrorSection",
"errors":{
"invalid":"Select city"
}
},
"gender":{
"required":true,
"errorPane":"genderErrorSection",
"errors":{
"required":"select gender"
}
},
"agree":{
"requiredState":true,
"displayAlert":true,
"errors":{
"requiredState":"Select I agree checkbox"
}
}
});
}
</script>
````

````
<body>
<h1>Form validation example</h1>
<form id='someForm' onsubmit='return doSomething()'>
<label>Name</label> <br><input type='text' name='nm' id='nm'> <span id='nmErrorSection'></span><br><br>
<label>Address</label> <br><textarea id='ad' name='ad'></textarea> <span id='adErrorSection'></span><br><br>
<label>Select city</label><br>
<select id='ct' name='ct'>
<option value='-1'>select city</option>
<option value='1'>Ujjain</option>
<option value='2'>Dewas</option>
<option value='3'>Indore</option>
</select>
 <span id='ctErrorSection'></span><br>
<br><br>
<label>Gender &nbsp;&nbsp;&nbsp;</label><br>
Male <input type='radio' name='gender' id='ml' value='M'>&nbsp;&nbsp;&nbsp;
Female <input type='radio' name='gender' id='fe' value='F'>&nbsp;&nbsp;&nbsp;
 <span id='genderErrorSection'></span>
<br><br>
<input type='checkbox' name='agree' id='ag' value='y'> I agree?
<br><br>
<button type='submit'>Registor</button>
</form>
</body>
````
### Output : 

![Screenshot (623)](https://user-images.githubusercontent.com/69362478/124371238-69ec4480-dc9d-11eb-98fc-80e7d1b335dc.png)

![Screenshot (632)](https://user-images.githubusercontent.com/69362478/124382708-75179280-dce6-11eb-97c3-6c27938cdd78.png)




### Fill combobox:
````
<script>
function populateDesignations()
{
$$$.ajax({
"url": "servletOne",
"methodType": "GET",
"success": function(responseData){
var designations=JSON.parse(responseData);
$$$("designationCode").fillComboBox({
"dataSource": designations,
"text" : "title",
"value": "code",
"firstOption" : {
"text": "<select designation>",
"value" : "-1"
}
});
},
"failure": function(){
alert("Some problem");
}
});
}
window.addEventListener('load',populateDesignations);
</script>
````

````
<body>
<h1>Fill ComboBox Example</h1>
<select id='designationCode'>
</select>
</body>
````

### Creating accordian panel:
 code to write in between <body> tag
 
 ````
 <h1>Accordian Pan Example</h1>
<div accordian="true">
<h3 accordianHeadrerBackgroundColor="#b97a56">Heading 1</h3>
<div accordianBackgroundColor="#ffe3ec">
1 whatever whatever
2 whatever whatever
3 whatever whatever<br>
4 whatever whatever
5 whatever whatever
6 whatever whatever<br>
7 whatever whatever
8 whatever whatever
9 whatever whatever<br>
</div><br>
<h3 accordianHeadrerBackgroundColor="#b97a56">Heading 2</h3>
<div accordianBackgroundColor="#ffe3ec">
11 whatever whatever
22 whatever whatever
33 whatever whatever
44 whatever whatever
55 whatever whatever
66 whatever whatever
77 whatever whatever
</div><br>
<h3 accordianHeadrerBackgroundColor="#b97a56">Heading 3</h3>
<div accordianBackgroundColor="#ffe3ec">
111 whatever whatever
222 whatever whatever
333 whatever whatever
444 whatever whatever
555 whatever whatever
666 whatever whatever
777 whatever whatever
</div>
</div>
<br><br>


<div accordian='true'>
<h3>Heading 1000</h3>
<div>
1 whatever whatever
2 whatever whatever
3 whatever whatever
4 whatever whatever
5 whatever whatever
6 whatever whatever
7 whatever whatever
</div><br>
<h3>Heading 2000</h3>
<div>
11 whatever whatever
22 whatever whatever
33 whatever whatever
44 whatever whatever
55 whatever whatever
66 whatever whatever
77 whatever whatever
</div><br>
<h3>Heading 3000</h3>
<div>
111 whatever whatever
222 whatever whatever
333 whatever whatever
444 whatever whatever
555 whatever whatever
666 whatever whatever
777 whatever whatever
</div><br>
</div>
 ````
 
 ### Creating accordian panel:
 code to write in between <body> tag
 
 ````
 <h1>Accordian Pan Example</h1>
<div accordian="true">
<h3 accordianHeadrerBackgroundColor="#b97a56">Heading 1</h3>
<div accordianBackgroundColor="#ffe3ec">
1 whatever whatever
2 whatever whatever
3 whatever whatever<br>
4 whatever whatever
5 whatever whatever
6 whatever whatever<br>
7 whatever whatever
8 whatever whatever
9 whatever whatever<br>
</div><br>
<h3 accordianHeadrerBackgroundColor="#b97a56">Heading 2</h3>
<div accordianBackgroundColor="#ffe3ec">
11 whatever whatever
22 whatever whatever
33 whatever whatever
44 whatever whatever
55 whatever whatever
66 whatever whatever
77 whatever whatever
</div><br>
<h3 accordianHeadrerBackgroundColor="#b97a56">Heading 3</h3>
<div accordianBackgroundColor="#ffe3ec">
111 whatever whatever
222 whatever whatever
333 whatever whatever
444 whatever whatever
555 whatever whatever
666 whatever whatever
777 whatever whatever
</div>
</div>
<br><br>


<div accordian='true'>
<h3>Heading 1000</h3>
<div>
1 whatever whatever
2 whatever whatever
3 whatever whatever
4 whatever whatever
5 whatever whatever
6 whatever whatever
7 whatever whatever
</div><br>
<h3>Heading 2000</h3>
<div>
11 whatever whatever
22 whatever whatever
33 whatever whatever
44 whatever whatever
55 whatever whatever
66 whatever whatever
77 whatever whatever
</div><br>
<h3>Heading 3000</h3>
<div>
111 whatever whatever
222 whatever whatever
333 whatever whatever
444 whatever whatever
555 whatever whatever
666 whatever whatever
777 whatever whatever
</div><br>
</div>
 ````
 
 
 ![Screenshot (629)](https://user-images.githubusercontent.com/69362478/124382725-911b3400-dce6-11eb-8c9a-0e85291d5dff.png)

 
 
 
 
 















