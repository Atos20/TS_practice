## Common TypeScript compiler snd tsconfig options

- The complier will read the intructions frm this file
 If this tsconfig file doesn't exist the compiler will take the default instructions.

- `tsconfig` options 

### "target"" "es6"
This is the  version of ECMAScript you would like to complie your code to.
Common values : ES5, ES6/ES2015, ES2016, ES2017, ES2018, ES2019, ES2020, ESNext
The ESNext options targer the latest supported  ES proposed festures according to the "ts30/ proposal" document
https://github.com/tc39/proposals

If you are targeting very old browsers, you might want to choose "ES5". If you are going to
run your code ing Node 12.10, you can set your target to ES2019", because acording to the "https://node.gree" website 
ES2019 is sopported by this version of node

### "lib": ["dom", "dom.iterable", "esnext"]

This is the list of library files you would like to include during the compilation. This library files tell the compiler  which features  you can use in your TS code. 

The "DOM" library tells the compiled hoe the DOm APi looks => so when use the DOM in our TS code `e.g. document.querySelector("a")`, the complier knows how to check it.

If we don't set this option, compiler will use a defaulr calue which is based on the target you've chose, `e.g for ES6thi is "DOM", ES6, DOM.iterable, ScriptHost`

Sometimes, you would want to tweak  this options, such that you can use some features in yout TS code.

### "strict : true

Enables all strict type schecking options, like noImplicityAny, noImplicitThis, alwaysStrict, strictFunctionTypes,
stricPropertyInitialization.
I suggest ti enable this option in order to improve type safety of your code.

### "module": "commonjs"

This optioon sets the module system that wil be used in the compiler  (.JS) files. YOu should choose the module system that is supported by the enviroment where yut code wi;; run.For example, `Node.js` uses `CommonJS`.


If you would like to compile your code for the browser, you'd have to combine the "module" option with the "outfile" option.
The OutFile option tells the compiler to bundle all your code into a single fil, which you can include into an HTML file using the `<script>` tag. The "outFile" option can be used only with AMD or SystemJS module systems. ** So if you use the "outFile" option you should set the "module" option to either `"amd"` or `"system"`**. And in order to use compile JS file in an HTML file, you should set up a corresponding module loader, like `https://require.org` or `https://github.com/systemjs/systemjs`


Instead of usinf the "outFile" option, I would recommendusing Typescript  together with webpack to bundle your code:
`https://webpack.js.org/guides/typescript`

And, for REAL projects, it would be even better if you use a framework,like `Create React App (https://create-react-app.dev/) or Next.js (https://nextjs.org)`
### "include": ["src/**/*"]
We use this option to list the files we'd like to be compiled. While the "files" options required relative or absolute paths to the files, the `"include"` option allows glob-like patters like.


`"**" =- any subdirectory`
`"*" - any file name`
`"?" - a character followed by the question mark become optional (e.g "src/*tsx?")`

### "exclude": ["node_modules","**/*/*.test.ts"]

This option excludes the file from the compilation. It accepts the ssame pattter as the `"include"` option. The `"exclude"` option doesn't affect the "files" option..

Usually, you'd like to exclude the `node_modules`, test files,  and the compilation output directory.

If you omit this option, the compiler  will exclude the folder specified unsing the "outDir" option

If you won't specify both options, "files" and "include", the compiler will compile all the TS files from the directory and any sibdirectory excluding the file specified using the "exclude" option.

### "esModuleInterop": true

This option allows us to import default from commonjs modules which don't have default export (modules which didin;t export the "default property"), like React, as if they have it. For example, in TypeScript, before, we use to import React like this:

```
import * as React from 'react'
```

Having this option enabled, we can import React like this:

```
import React from 'react';
```

### JS