# JAVASCRIPT Interview Questions

## Describe  call() function

call() allows you to call a function defined in object1 in another function such as object2. For example person1 defines greet function. person2 object can call this function as its own function.

```
> var person1 = { name:"koray", greet: function(name){console.log( name +" says hello to " +this.name );} }
> person1.greet("jeck");
jeck says hello to koray 
> person1.greet.call(person2,"jeck");
jeck says hello to ahmet 
```

## Describe  apply() function

apply is the same as call() but apply expectes an array of parameters. call() expects alist of parameters. e.g. Function.apply(object1,[array of arguments]);
```
> person1.greet.call(person2,["jeck"]);
jeck says hello to ahmet 

```
It is also possible to improve performance by using apply in array operations e.g

```
var arr = [],arr1=[];
// arr has 1 million entries we want to copy them to arr1 
Array.prototype.push(arr1,arr);

```

## Describe javascript hoisting

javascript declarations are hoisted. in anotherwords they can be used before they are declared. but javascript initializations are not hoisted. 

functions declarations are hoisted at the top as well, that is to say they are accessable before they are defined. 

```
(function(){
   myFunction(); 
   function myFunction(){console.log("hello")};
	
})();
```

function expressions are not hoisted. the example below will not work.

```
(function(){
   myFunction(); 
   var myFunction = function (){console.log("hello")};
	
})();
``` 





# JAVASCRIPT Links 
- http://spencertipping.com/js-in-ten-minutes/js-in-ten-minutes.pdf
- http://ejohn.org/apps/learn/
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference
- http://www.toptal.com/javascript/interview-questions
- http://benalman.com/news/2010/11/immediately-invoked-function-expression
- http://blog.sourcing.io/interview-questions
- https://github.com/darcyclarke/Front-end-Developer-Interview-Questions