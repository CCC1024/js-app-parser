## web-pkg-parser

* Base on https://github.com/mljsgto222/js-app-parser.git, and modify the plist parser. *

### Features

* Getting apk meta info.
* Getting ipa meta info.


### Dependency

* [jszip](https://stuk.github.io/jszip/)
* [pako](http://nodeca.github.io/pako/)
* [js-crc32](https://github.com/SheetJS/js-crc32)
* [text-encoding](https://github.com/inexorabletash/text-encoding)
* [plist](https://github.com/TooTallNate/plist.js)


### Install

```npm
npm install --save web-pkg-parser
```

### Usage

#### Node

```js
const appParser = require('web-pkg-parser');
const fs = require('fs');

const buffer = fs.readFileSync('your apk or ipa file path').buffer;
appParser.Application.loadAsync(buffer).then(application => {
    // get application meta info
}).catch(error => {
    // do when error
});
```

#### Browser

```html
<input id="fileInput" type="file" onchange="onFileSelect()" />
```

```js
function onFileSelect() {
    const fileInput = document.getElementById('fileInput');
    appParser.Application.loadAsync(fileInput.files[0]).then(application => {
         // get application meta info
    });
}
```

### Application Class

```js
    class Application {
        versionCode: string; // application version code
        versionName: string; // application version name
        package: string; // android app id or ios build identifier
        icon?: string; // application icon path
        iconSteam?: Uint8Array; // application icon file buffer
        name: string; // application name
        platform: string; // platform 'android' or 'ios'
    }
```
