# CSS Interview Questions


## Describe different ways to use styles on a web page

- inline : e.g. ```  <p style=”font-size: 12px;  color: #000000;”>Test </p> ```
- embeded : e.g. 
```  
<head>
<style type=”text/css”>
h2 {
   font-size: 16px;
   color: #2d2d2d;
   font-weight: 900;
}
</style>
</head>
```
- linked : e.g. ```  <link rel=”stylesheet” href=”custom/custom.css” type=”text/css” media=”screen, projection” /> ```
- imported : either in html or css files e.g. ``` @import url(‘/css/typography.css’); ```
