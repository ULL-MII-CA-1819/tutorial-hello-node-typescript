* [A crash course on TypeScript with Node.js](https://blog.sourcerer.io/a-crash-course-on-typescript-with-node-js-2c376285afe1)

```bash
$ npm init -y
$ npm install -g typescript
```

```bash
[~/javascript/learning/hello-typescript]$ tsc --help
Version 3.2.2
Syntax:   tsc [options] [file...]

Examples: tsc hello.ts
          tsc --outFile file.js file.ts
          tsc @args.txt
          tsc --build tsconfig.json

Options:
 -h, --help                                         Print this message.
 -w, --watch                                        Watch input files.
 --pretty                                           Stylize errors and messages using color and context (experimental).
 --all                                              Show all compiler options.
 -v, --version                                      Print the compiler's version.
 --init                                             Initializes a TypeScript project and creates a tsconfig.json file.
 -p FILE OR DIRECTORY, --project FILE OR DIRECTORY  Compile the project given the path to its configuration file, or to a folder with a 'tsconfig.json'.
 -b, --build                                        Build one or more projects and their dependencies, if out of date
 -t VERSION, --target VERSION                       Specify ECMAScript target version: 'ES3' (default), 'ES5', 'ES2015', 'ES2016', 'ES2017','ES2018' or 'ESNEXT'.
 -m KIND, --module KIND                             Specify module code generation: 'none', 'commonjs', 'amd', 'system', 'umd', 'es2015', or 'ESNext'.
 --lib                                              Specify library files to be included in the compilation.
                                                      'es5' 'es6' 'es2015' 'es7' 'es2016' 'es2017' 'es2018' 'esnext' 'dom' 'dom.iterable' 'webworker' 'webworker.importscripts' 'scripthost' 'es2015.core' 'es2015.collection' 'es2015.generator' 'es2015.iterable' 'es2015.promise' 'es2015.proxy' 'es2015.reflect' 'es2015.symbol' 'es2015.symbol.wellknown' 'es2016.array.include' 'es2017.object' 'es2017.sharedmemory' 'es2017.string' 'es2017.intl' 'es2017.typedarrays' 'es2018.intl' 'es2018.promise' 'es2018.regexp' 'esnext.array' 'esnext.symbol' 'esnext.asynciterable' 'esnext.intl' 'esnext.bigint' 
 --allowJs                                          Allow javascript files to be compiled.
 --jsx KIND                                         Specify JSX code generation: 'preserve', 'react-native', or 'react'.
 -d, --declaration                                  Generates corresponding '.d.ts' file.
 --declarationMap                                   Generates a sourcemap for each corresponding '.d.ts' file.
 --sourceMap                                        Generates corresponding '.map' file.
 --outFile FILE                                     Concatenate and emit output to single file.
 --outDir DIRECTORY                                 Redirect output structure to the directory.
 --removeComments                                   Do not emit comments to output.
 --noEmit                                           Do not emit outputs.
 --strict                                           Enable all strict type-checking options.
 --noImplicitAny                                    Raise error on expressions and declarations with an implied 'any' type.
 --strictNullChecks                                 Enable strict null checks.
 --strictFunctionTypes                              Enable strict checking of function types.
 --strictBindCallApply                              Enable strict 'bind', 'call', and 'apply' methods on functions.
 --strictPropertyInitialization                     Enable strict checking of property initialization in classes.
 --noImplicitThis                                   Raise error on 'this' expressions with an implied 'any' type.
 --alwaysStrict                                     Parse in strict mode and emit "use strict" for each source file.
 --noUnusedLocals                                   Report errors on unused locals.
 --noUnusedParameters                               Report errors on unused parameters.
 --noImplicitReturns                                Report error when not all code paths in function return a value.
 --noFallthroughCasesInSwitch                       Report errors for fallthrough cases in switch statement.
 --types                                            Type declaration files to be included in compilation.
 --esModuleInterop                                  Enables emit interoperability between CommonJS and ES Modules via creation of namespace objects for all imports. Implies 'allowSyntheticDefaultImports'.
 @<file>           
 ```

For the development environment we want to use a TypeScript execution environment for Node.js called ts-node. Installing it is as simple as installing TypeScript.

 ```bash
 npm install -g ts-node
 ```

 ```bash
 [~/javascript/learning/hello-typescript]$ ts-node --help

Usage: ts-node [options] [ -e script | script.ts ] [arguments]

Options:

  -e, --eval [code]              Evaluate code
  -p, --print [code]             Evaluate code and print result
  -r, --require [path]           Require a node module before execution

  -h, --help                     Print CLI usage
  -v, --version                  Print module version information

  -T, --transpile-only           Use TypeScript's faster `transpileModule`
  --cache-directory              Configure the output file cache directory
  -I, --ignore [pattern]         Override the path patterns to skip compilation
  -P, --project [path]           Path to TypeScript JSON project file
  -C, --compiler [name]          Specify a custom TypeScript compiler
  -D, --ignoreDiagnostics [code] Ignore TypeScript warnings by diagnostic code
  -O, --compilerOptions [opts]   JSON object to merge with compiler options

  --files                        Load files from `tsconfig.json` on startup
  --pretty                       Use pretty diagnostic formatter
  --no-cache                     Disable the local TypeScript Node cache
  --skip-project                 Skip reading `tsconfig.json`
  --skip-ignore                  Skip `--ignore` checks
  ```


  ```bash
  npm install --save express @types/express body-parser
  ```
* We’re installing express, 
* the express data types for TypeScript, 
* and of course body-parser. T

These types are what make TypeScript special. 
They’re part of DefinitelyTyped, the repository for high quality TypeScript type definitions. 

If you need some special types you just install them. 

This let’s the TypeScript compiler know what the special values in Express mean giving it the possibility to do pre-compile error checking correctly.

![](https://cdn-images-1.medium.com/max/1600/1*2XgsQZ-Oe8rYV7Z3r_s0ig.png)

I tend to use either Insomnia or Postman for testing routes, also called REST endpoints. Feel free to install whichever you like if you don’t already have one. They’re simple tools for sending HTTP requests. Here let me show you.

With the app running, open up Insomnia and send an HTTP GET request to http://localhost:4040/.

However, we’re still running the TypeScript files with ts-node. In production we want to compile everything to JavaScript and run it with the node command. But that’s a bit hard if we need to run the tsc command against one file at a time. Luckily, you can pass values to the command line interface and specify options that way, or just create a tsconfig.json file. It’s a special configuration file that specifies everything regarding the actual compilation process.

```bash
[~/javascript/learning/hello-typescript]$ tsc
[~/javascript/learning/hello-typescript]$ tree dist/
dist/
├── app.js
├── app.js.map
├── server.js
└── server.js.map

0 directories, 4 files
```

