## Exercise 2: mongo Client JavaScript Interpreter

We can use javascript to create functions and loops.
```
function product(v1, v2) {
    return v1 * v2; // return the product of v1 and v2
}
v1 = 1;
v2 = 2;
product(v1, v2)
```
```
for (i = 0; i < 5; i++) {
     print(product(i, i + 1))
}
```
Open a editor of your choice and create a javascript file.
```
function addvals(v3, v4) {
    return v3 + v4;  // return the sum of v3 and v4
}
```
Save it as func.js and load the script in mongo the shell.
```
load("/path/to/func.js")
addvals(1,2)
```
