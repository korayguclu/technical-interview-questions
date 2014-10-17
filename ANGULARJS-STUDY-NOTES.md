
CONSTANT
== 

A constant is a value injectable anywhere
```
app.constant('jellyBean', 4.2)
```
Can not be intercepted by a decorator.High priority.

VALUE
== 
A simple injectable value.
```
app.value('name', 'Larry');
```
Can not be injected into configurations. Can be intercepted by decorators.

SERVICE
== 
Injectable constructor.
```
app.service('api', function (dep) {...});
```
A singleton. Good for cross app/controller communication.

Example

```
myApp.service('helloWorldFromService', function() {
    this.sayHello = function() {
        return "Hello, World!"
    };
});
```

FACTORY
== 
Injectable function for returning factory stuff.

```
app.factory('widget', function (dep) {... return ?;});
```
Question mark can be an object e.g. {} or a constructor function e.g. function(){}

A provider with only a $get method, essentially.

Example:
```
app.factory('helloWorldFromFactory', function() {
    return {
        sayHello: function() {
            return "Hello, World!"
        }
    };
});
```

DECORATOR
==
Modify or encapsulate other provisions.
```
app.config(function($provide) {
  $provide.decorate('name', function($delegate) {
    // Modifications to the 'name' provision.
    return $delegate + ' the Great';
  });
});
```
Useful for modifying upstream services.Stackable.

PROVIDER
== 
The low-level tool.

```
$provide.provider('foo', {$get: function(dep) {...}});
$provide.provider('foo', function(){
  this.$get = function(dep) {...}
});
```
You just need a $get method. More storage options. Can $inject other providers when instantiated.


SERVICE, FACTORY, VALUE
== 
They are derived from provider.

Service excepts a Class function do not require a return method.

Factory is factory design pattern returns an class which can be instantinated later. 
Or it can instantinate the class by itself and return a new object.

```
// service donot return a value. provider creates an instance of the object
provider.service = function(name, Class) {
  provider.provide(name, function() {
    this.$get = function($injector) {
      return $injector.instantiate(Class);
    };
  });
}

provider.factory = function(name, factory) {
  provider.provide(name, function() {
    this.$get = function($injector) {
      return $injector.invoke(factory);
    };
  });
}

provider.value = function(name, value) {
  provider.factory(name, function() {
    return value;
  });
};

```


