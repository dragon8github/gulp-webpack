传送门

> [https://github.com/sindresorhus/gulp-autoprefixer](https://github.com/sindresorhus/gulp-autoprefixer)

npm 安装列表

> $ npm install --save-dev gulp-autoprefixer

注意，这里是先进行autoprefixer，再进行sass编译。笔者之前弄反了导致编译的css出现了问题。通过网上其他学习才了解到正确的姿势。

---

### Example

gulpfile.js

```js
'use strict';
const gulp = require('gulp');
const sass = require('gulp-sass');
const autoprefixer = require('gulp-autoprefixer');

gulp.task('sass', function () {
  return gulp.src('./src/sass/*.scss')
    .pipe(autoprefixer({
                browsers: ['last 2 version', 'safari 5', 'ie 8', 'ie 9', 'opera 12.1', 'ios 6', 'android 4'],
                cascade: true,
                remove: true
    }))
    .pipe(sass().on('error', sass.logError))
    .pipe(gulp.dest('./dist/assets/css'))
});
```

执行任务：

> $ gulp sass

![](/assets/1351231import.png)

