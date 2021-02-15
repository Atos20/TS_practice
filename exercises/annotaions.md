## Common TypeScript compiler snd tsconfig options
the complier will read the intructions frm this file
 If this tsconfig file doesn't exist the compiler will take the default instructions

//here are some of the compiler optons
/*
"target"" "es6"
this is the  version of ECMAScript you would like to complie your code to.
Common values : ES5, ES6/ES2015, ES2016, ES2017, ES2018, ES2019, ES2020, ESNext
The ESNext options targer the latest supported  ES proposed festures according to the "ts30/ proposal" document
https://github.com/tc39/proposals

If you are targeting very old browsers, you might want to choose "ES5". If you are going to
run your code ing Node 12.10, you can set your target to ES2019", because acording to the "https://node.gree" website 
ES2019 is sopported by this version of node

"L"
