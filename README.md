# gulp-loco-export v0.0.1

> Use urllib to call api to Loco.


## Install

```
npm install --save-dev https://github.com/byseob/gulp-loco-export.git
```


## Example

### import test.pot to loco in gulpfile.js  

```js
/**
 * Created by matthew on 2017. 3. 23..
 */

'use strict';

var assert = require('assert');
var gulp = require('gulp');
var file = require('gulp-file');
var loco_api_export = require('../index');

var options = {
  'key': '--YOUR--LOCO--API--KEY--',
  'ext': 'po',
  'tmp_zip': './temp/all.zip',
  'po_temp_path': './temp/i18n',
  'po_root_path': './app/i18n'
}

describe('gulp-loco-export', function() {

  it('should export call successfully', function(done) {

    this.timeout(60000);

    gulp.task('test', function() {
      return file(options.tmp_zip, '', { src: true })
        .pipe(loco_api_export(options))
        .on('end', function(data){
          // console.log(data);
          //assert.equal(content, destFile.toString());
          done();
        });
    });

    gulp.start('test');

  });
});

```

## options
Option     | Type                             | Description
---------- | -------------------------------- | --------------
key        | ((string))(_required_)           | Loco API Key
ext        | ((string))                       | pot, json, po ... reference from localize.biz

## License

MIT
# gulp-loco-export
