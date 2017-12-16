传送门

> [https://github.com/dlmanning/gulp-sass](https://github.com/peter-vilja/gulp-clean)

npm 安装列表

> $ cnpm install --save-dev gulp-clean

gulpfile.js

```js
'use strict';
const gulp = require('gulp');
var clean = require('gulp-clean');

gulp.task('clean', function () {
    return gulp.src('./dist/**', {read: false})
        .pipe(clean());
});

```

执行gulp任务

> $ gulp clean

执行之后，dist文件夹就被清空并删除了

![](/assets/123123123import.png)

