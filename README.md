# Notes

<b>JAVASCRIPT NOTES :</b>
<b>Disadvantages of Javascript:</b>
1. Security: Javascirpt runs on client machine. So malacious user may use javascirpt to do a variety of things like tracking your browser history,stealing passwords etc. therfore many disable javascript.
2. Browser compatibility: Not all browser treat the javascript code in the same manner.therfore cross browser testing is required. however with javascript libraries like jquery browser compatibility is no longer an issue. innerText property works in IE & chrome but not in firefox. therefore need to replace with textContent.

<b>Closures:</b> Nested functions are called closures which have access all properties methods of parent functions.

catches unhandled exceptions:
window.onerror=function(msg,url,line){}
errors are catched in try , catch block..if not catched in try ..catch will be handled in onerror event of window object.

Events in Javascirpt:An event is a signal from the browser that something has happened. ex: click, mouseover, mouseout, onblur, onkeyup, onkeydown etc.
we can execute javascript code or functions in response to those events, that functions are called event handler.

serveral ways to associate event handler to events are :
1. using attributes of html tags : <button onclick='fun1()' id='btn"/>
2. using DOM object property : document.getElementById('btn').onClick=fun1();
3. using special methods: ,detachEvent.
 addEventListener/removeEventListener: executes multiple event handlers but order is not specified.
 btn.addEventListener("Onclick",func1,false); false: indicates events bubbles from inner towards outside. true: indicates bubbles from outside towards inside.
 btn.addEventListener("Onclick",func2,false);
 btn.removeEventListener("Onclick",func2);
  
 attachEvent/detachEvent: Works only in IE <=8 version.
 
 Event Object : contains properties like type,clientX,clientY,target.type,target.tagName etc.
 
 Event bubbles from inner object event to outer object event in DOM hierarchy. To stop event bubbling use event.StopPropogation();
 To Prevent browser default action use 
 event=event|| window.event;
 event.PreventDefault(); or event.returnValue=false;
 
 event.button or event.which property : display which mouse button is clicked.  
  
attribute event handlers are overriden by dom object event handler. If multiple event handlers are associated with one control then latest eventhandler will be executed.i.e overrides the previous event handlers.
  
When page is loaded, the browser creates a document object model.
window=>document=>html=>head & body


timing events:
setInterval(func,delay) :execute repeatedly javascript function 
setTimeout(func,delay): execute once javascript function after some dealy time in seconds.
clearInterval():
var intervalId=setInterval(func,delay);
clearInterval(intervalId);

Javascript minification is the process of reducing the file size by removing comments,extra white spcaes and new line characters that are not needed for executing javascript code.it may reduce the size by 30 to 90%. The minification process will not change its original functionality.

Benefits: Javascript files needs to be downloaded to the client machine before the browser can execute javascirpt code. Minification reduces the file size and have following benefits.
1. Reduce download time.
2. Less bandwidth consumption of your website
3. Reduced javascript execution time as all comments,extra white spaces and new line charaters are removed from minified version.
4. Multiple javacript files can be merged into one single minified file.This means there are now reduced number of HTTP requests to your server.which in turn reduces the load on server and allows more users to access your website

Disadvantages: Readability is lost and debugging can be difficult

Javascript is OOP langauge: Has 4 pillars: Inheritance,Encapsulation,Abstraction,Polymorphism.
Objects in javscript can be classified as Standard build in objects and Custom objects (string,array,date,RegExp...)

Two ways to create custom objects: Constructor function and literal notation(they are singleton object).

Constructor function :create multiple instances of the object. will not have any impact of value change on other object.
function Employee(firstName,lastName){
this.firstName=firstName;
this.secondName=secondName;
this.getFullName=function(){
    return this.firstName + this.secondName;
  }
}
var emp=new Employee("savi',"math");
document.write(@"{0}{1}{2}",emp.firstName,emp.secondName,emp.getFullName());

Literal notation:Singleton object, will always contain latest value modified.
var employee={
firstName:"savi",
secondName""math",
getFullName:function(){
return this.firstName+this.secondName;
}
}

var newEmployee=employee;
newEmployee.firstName="contain latest changed value in both objects"

With the literal notation we have already created an object, so to access firstname value we need to use by employee.firstname. With the constructor function first we need to create an instance and then get the property of an instance.

Window is the global object. there is no ovloading functionality in javascipt. therefore the order in which js files are called in .html files may overrwrite the objects having same name. To avoid polluting global scope use NameSpaces

var team=team || {};
var team.teamA=teamA || {};
team.teamA.customer=function(firstName,lastName){};
team.teamB.customer=function(firstNamelastName,middleName){}
alert(window.team.teamA.customer("a","b") +window.team.teamB.customer("A","B","C"));

