# pseudo-inverse
Left or right pseudo inverse.

## Dependencies

There are 2 dependencies 'matrix-computations' and 'singular-value-decomposition'.

```bash
https://github.com/PeterTadich/matrix-computations
https://github.com/PeterTadich/singular-value-decomposition
```

## Installation

### Node.js

```bash
npm install https://github.com/PeterTadich/pseudo-inverse
```

### Google Chrome Web browser

No installation required for the Google Chrome Web browser.

## How to use

### Node.js

```js
import * as pinv from 'pseudo-inverse';
```

### Google Chrome Web browser

```js
import * as pinv from './pinv.mjs';
```

## Examples

### Node.js (server side)

Copy the following code to index.mjs

```js
import * as pinv from 'pseudo-inverse';

var a = [
    [1,2],
    [3,4],
    [5,6],
    [7,8]
];
var b = pinv.pinv(a);
console.log(b);
```

Then run:

```bash
npm init -y
npm install https://github.com/PeterTadich/pseudo-inverse
node index.mjs
```

If the above does not work, modify the package.json file as follows:
Helpful ref: [https://stackoverflow.com/questions/45854169/how-can-i-use-an-es6-import-in-node-js](https://stackoverflow.com/questions/45854169/how-can-i-use-an-es6-import-in-node-js)

```js
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node --experimental-modules index.mjs"
  },
"type": "module",
```

Now try:

```bash
npm start
```

Returns:

```js
[
  [ -1.0000,  0.8500 ],
  [ -0.5000,  0.4500 ],
  [  0.0000,  0.0500 ],
  [  0.5000, -0.3500 ]
]
```

### Google Chrome Web browser (client side)

Copy the following code to index.mjs

```js
import * as pinv from './pinv.mjs';

var a = [
    [1,2],
    [3,4],
    [5,6],
    [7,8]
];
var b = pinv.pinv(a);
console.log(b);
```

Copy the following code to index.html

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <script type="module" src="index.mjs"></script>
    </head>
</html>
```

Download the modules:

```bash
curl -O https://raw.githubusercontent.com/PeterTadich/singular-value-decomposition/main/svdcmp.mjs
curl -O https://raw.githubusercontent.com/PeterTadich/matrix-computations/main/hlao.mjs
curl -O https://raw.githubusercontent.com/PeterTadich/pseudo-inverse/main/pinv.mjs
```

Open pinv.mjs and modify form:

```js
import * as svdcmp from 'singular-value-decomposition';
import * as hlao from 'matrix-computations';
```

to:

```js
import * as svdcmp from './svdcmp.mjs';
import * as hlao from './hlao.mjs';
```

Start the server, open index.html with Google Chrome and inspect with the console.

Returns:

```js
[
  [ -1.0000,  0.8500 ],
  [ -0.5000,  0.4500 ],
  [  0.0000,  0.0500 ],
  [  0.5000, -0.3500 ]
]
```

Server '*.conf' files may require modification.

mime.types file include:

```conf
text/javascript mjs js
```

httpd.conf file include:

```conf
AddType text/javascript .mjs
```

Alternatively change the file extension from *.mjs to *.js

## License

[MIT](LICENSE)