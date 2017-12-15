传送门

> https://github.com/dlmanning/gulp-sass

npm 安装列表

> $ cnpm install gulp --save-dev
>
> $ cnpm install gulp-sass --save-dev

gulpfile.js

```js
'use strict';
var gulp = require('gulp');
var sass = require('gulp-sass');

gulp.task('sass', function () {
  return gulp.src('./src/sass/*.scss')
    .pipe(sass().on('error', sass.logError))
    .pipe(gulp.dest('./dist/assets/css'));
});

gulp.task('sass:watch', function () {
  gulp.watch('./src/sass/*.scss', ['sass']);
});
```

执行gulp任务

> $ gulp sass

![](/assets/12312import.png)

执行gulp 监听任务

> $ gulp sass:watch

当我们修改/src/sass/\*.scss时，会实时编译为/assets/css/\[name\].css

![](/assets/123123import.png)

