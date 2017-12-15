传送门

> [https://github.com/sindresorhus/gulp-autoprefixer](https://github.com/sindresorhus/gulp-autoprefixer)

npm 安装列表

> $ npm install --save-dev gulp-autoprefixer

```js
'use strict';
const gulp = require('gulp');
const sass = require('gulp-sass');
const autoprefixer = require('gulp-autoprefixer');

gulp.task('sass', function () {
  return gulp.src('./src/sass/*.scss')
    .pipe(sass().on('error', sass.logError))
    .pipe(gulp.dest('./dist/assets/css'));
});


gulp.task('sass:watch', function () {
  gulp.watch('./src/sass/*.scss', ['sass']);
});


gulp.task('auto', function () {
    gulp.src('./dist/assets/css/*.css')
            .pipe(autoprefixer({
                browsers: ['last 2 version', 'safari 5', 'ie 8', 'ie 9', 'opera 12.1', 'ios 6', 'android 4'],
                cascade: false
            }))
            .pipe(gulp.dest('./dist/assets/css/'))
})
```

目前是学习阶段，当然是手动调用咯

> $ gulp sass
>
> $ gulp auto



![](/assets/1351231import.png)



