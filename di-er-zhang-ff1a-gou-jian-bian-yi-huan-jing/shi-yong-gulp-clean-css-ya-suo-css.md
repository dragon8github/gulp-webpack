传送门

> [https://github.com/dlmanning/gulp-sass](https://github.com/peter-vilja/gulp-clean)

npm 安装列表

> $ [cnpm install --save-dev gulp-clean](https://github.com/scniro/gulp-clean-css)

gulpfile.js

```js
'use strict';
const gulp = require('gulp');
let cleanCSS = require('gulp-clean-css');

gulp.task('mincss', () => {
  return gulp.src('./dist/assets/css/*.css')
    .pipe(cleanCSS({compatibility: 'ie8'}))
    .pipe(gulp.dest('./dist/assets/css/'));
});

```

执行gulp任务

> $ gulp mincss



![](/assets/123123123123import.png)

