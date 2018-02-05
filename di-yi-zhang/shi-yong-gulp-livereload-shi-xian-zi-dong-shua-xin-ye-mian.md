传送门：

> [https://www.browsersync.io/docs/gulp/](https://www.browsersync.io/docs/gulp/)
>
> [https://browsersync.io/](https://browsersync.io/)

npm安装

> $ cnpm install browser-sync gulp --save-dev

请注意一定要使用npm来安装，如果是cnpm安装完之后似乎还缺少几个模块。附上package.json吧

```js
  "devDependencies": {
    "browser-sync": "^2.18.13",
    "gulp": "^3.9.1",
    "gulp-autoprefixer": "^4.0.0",
    "gulp-html-replace": "^1.6.2",
    "gulp-sass": "^3.1.0",
    "is-number-like": "^1.0.8",
    "lodash.isfinite": "^3.3.2"
  }
```

---

### Example

gulpfile.js

```js
'use strict';
const gulp = require('gulp');
const sass = require('gulp-sass');
const autoprefixer = require('gulp-autoprefixer');
var sourcemaps = require('gulp-sourcemaps');

var browserSync = require('browser-sync').create();
var reload      = browserSync.reload;

gulp.task('sass', function() {
    return gulp.src(['./src/**/*.scss', './src/**/**/*.scss'])
        .pipe(sourcemaps.init())
        .pipe(autoprefixer({
            browsers: ['last 2 version', 'safari 5', 'ie 8', 'ie 9', 'opera 12.1', 'ios 6', 'android 4'],
            cascade: true,
            remove: true
        }))
        .pipe(sass().on('error', sass.logError))
        .pipe(sourcemaps.write('./'))
        .pipe(gulp.dest('./dist/'))
});

// 静态服务器
gulp.task('serve', ['sass'], function() {
    browserSync.init({
        server: {
            baseDir: "./"
        }
    });
    gulp.watch("./src/sass/*.scss", ['sass']);
    gulp.watch("./index.html").on('change', reload);
});
```

运行

> $ gulp serve



