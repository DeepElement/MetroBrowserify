<link href="http://fonts.googleapis.com/css?family=Lato:300,400,700" rel="stylesheet" type="text/css">

<img src="http://www.deepelement.com/img/logos/de/de_logo.ico" height="30"> Metro-Browserify 
================ 
Support NodeJs modules within the WinJS runtime in an instant. 

#Installation

1. Add [MetroBrowserify NuGet Package](https://www.nuget.org/packages/MetroBrowserify/) to WinJS project via [NuGet](https://www.nuget.org/)
2. Define your package.json in the project root:
```Javascript
{
	"name": "Winstore-Browserify",
	"version": "0.0.1",
	"description": "",
	"scripts": {},
	"dependencies": {
		"uniq": "*"
	},
	"author": "",
	"license": ""
}
```
3. Create a node module with the `*.node.js` extension:
```Javascript
var unique = require('uniq');
var data = [1, 2, 2, 3, 4, 5, 5, 5, 6];
console.log(unique(data));
```
4. Add reference to node module js file directly in your default.html:
```Javascript
<script src="/js/entry.node.js"></script>
```
__Extras__:

1. Clean-up unrequired files
	- Remove the 'npmPlaceholder.txt' (see [NPM NuGet](https://github.com/giggio/npm-nuget))
	- Exclude the ".bin" directory from project (see [NODE NuGet](https://www.nuget.org/packages/Node.js/))
2. Git Users
	- Add "*.cache" to .gitignore

#Samples & Explanation

See the [WinStore Sample](https://github.com/DeepElement/metro-browserify/tree/master/samples/standard)

The above sample shows that:

1. At build time, NPM, Node and Browserify will be installed relative to the project directory
2. Browserify compiles `*.node.js` files into `*.node.js.cache` variants
3. Cache versions of the node files are replaced in the Appx output

In result, the node module effectively runs like a champ in a running Metro app.


#Disclaimer
Not all Node Modules will run in Metro.
This is caused by the fact that some modules have C++ or Native implementations that are not available in RT.
Please test compiled functionality before production usage.

# Special Thanks
- [The Browserify Core Team](http://browserify.org/ "Browserify Project")
- [The Wondering Goat, Eugene Oregon](http://wanderinggoat.com/)

#License
The MIT License (MIT)

Copyright (c) 2014 Deep Element Software Services

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
