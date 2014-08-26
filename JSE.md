# JSE Interview Questions

## Difference between final, finally, finalize

final is to mark a variable or method unchangeable, finally is used in a try/catch statement to execute code "always", finalize is called when an object is garbage collected. You rarely need to override it.(ref. http://bit.ly/1mJ6fRU)


## Difference between StringBuffer, StringBuilder

StringBuffer is threadsafe, but they can be slow. 
Use StringBuilder whenever possible because it is faster than StringBuffer. But, if thread safety is necessary then use StringBuffer objects.

## Difference between List and Set

List: Duplicates are allowed,Insertion order preserved.	

Set: Duplicates are not allowed,Insertion order not preserved.

# Describe new features in JDK7

simple readable generics(dimand opeator): only one side must have generics e.g List<Integer> i  =new  LinkedList<>(); 

sourcode number formating ex. _ or new 0bx0101_0000 for ninary format 

try-with-resources 
e.g. to use this stream must implement autocloseble interface

```
 try(InputStream is = new FileInputStream("i.txt");OutputStream os=new FileOutputstram("o.txt")){
   // do your work.
};
```

multicatch 
try{} catch (NamingException|IOException|SQLExcepton ex) { log(ex);}

switch with strings (enums are better for such kind of things because of type safety):
```
swich(month) {
    case "januar":
   case "marz":
   return 31;//...
}
```

NIO.2: new programming interface to simplify file resource access . 

new package is 
java.nio.file instead of File there is Path now (with symbolic links) java.nio.file.Path is platform dependent you donot need to use seperators etc.. 
e.g. 
```
Path source = Paths.get("path","to","source");
Path target  = Paths.get("path","to","target");
Files.copy(source,target);
Files.move(source,target);
```

new utillity class Files and Paths to read, copy files etc...
filesystemprovider for jar and zip files.
 
java.util.concurrent(java5) has been extended in java7 again.

Fork/Join Framework for multi-core cpus.
TransferQueue
 
swing, garbage collector (g1 mehere processon), schnelere sortier algorithmen for arrays are double faster
ref: http://openjdk.java.net/projects/jdk7/features/


## Describe new features in JDK8

Lambda-Ausdrücke sind eine kompakte Schreibweise zur Formulierung einer anonymen Klasse mit einer Methode
Similar interfaces Runnable, EventHandler which runs later.
Consumer <String> c= (String text)->System.out.println (text);
http://openjdk.java.net/projects/jdk8/features


## Describe Unbounded, UpperBounded, LowerBounded Wildcards in java generics

Unbounded : It is specified with wildcard (?) character. It is type of unknow e.g. ```List<?>``` means list of unknow type. Any object can be added to the list.

UpperBounded :  ```List<? extends Number>``` all subclass of Number can be added to the list.

LowerBounded : ```List<? super Integer>``` all supertype of Integer can be added to the list.


## Describe heap polution

This situation can happen when a a variable of a parameterized type such as ```List<String>``` refers to an object that is not of that parameterized type such as ```ArrayList<Number>()```. 

Example (of heap pollution): 
 
```
List ln = new ArrayList<Number>(); 
List<String> ls =ln;  // unchecked warning 
String s = ls.get(0); // ClassCastException 
```

After the assignment of the reference variable  ln to the reference variable ls , the  ```List<String>``` variable will point to a  ```List<Number>``` object. Such a situation is called  heap pollution and is usually indicated by an unchecked warning.  A polluted heap is likely to lead to an unexpected  ClassCastException at runtime.  In the example above, it will lead to a  ClassCastException , when a object is retrieved from the  ```List<String>``` and assigned to a  String variable, because the object is a  Number , not a  String .

ref. http://bit.ly/1tDldOj
