传送门

> [https://github.com/dlmanning/gulp-sass](https://github.com/dlmanning/gulp-sass)
>
> [https://github.com/floridoo/gulp-sourcemaps](https://github.com/floridoo/gulp-sourcemaps)

npm安装

> $ cnpm install gulp-sourcemaps --save-dev

```js
'use strict';
const gulp = require('gulp');
const sass = require('gulp-sass');
const autoprefixer = require('gulp-autoprefixer');
var sourcemaps = require('gulp-sourcemaps');

gulp.task('sass', function () {
  return gulp.src('./src/sass/*.scss')
        .pipe(sourcemaps.init())
        .pipe(autoprefixer({
             browsers: ['last 2 version', 'safari 5', 'ie 8', 'ie 9', 'opera 12.1', 'ios 6', 'android 4'],
             cascade: true,
             remove: true
        }))
        .pipe(sass().on('error', sass.logError))
        .pipe(sourcemaps.write('./maps'))
        .pipe(gulp.dest('./dist/assets/css'))
});
```

执行任务

> $ gulp sass

![](/assets/161import.png)

![](/assets/24324import.png)

