gulp-rename 插件简直就是解决路径问题的神器。特别适合解决相对路径问题。

```
$ cnpm i gulp-rename
```

稍后整理

gulpfile.js

```js
const rename       = require('gulp-rename');
const babel        = require('gulp-babel');

function babel_env () {
    return gulp.src('./components/**/src/*.js')
               .pipe(sourcemaps.init())
               .pipe(babel({
                  presets: [
                      [
                        "env",
                        {
                          "targets": {
                            "browsers": ["last 5 versions", "ie >= 8"]
                          }
                        }
                      ],
                      "babel-preset-stage-2"
                  ],
                  plugins: [
                      'transform-runtime'
                  ]
               }))
               .pipe(sourcemaps.write('.')) 
               .pipe(rename(function (path) {
                   path.dirname = path.dirname.replace('src', 'dist')
               }))
               .pipe(gulp.dest('./components'))

}

// 编译babel
gulp.task(babel_env)
```

通常还需要结合src.base参数

```js
const gulp         = require('gulp')
const sass         = require('gulp-sass')
const autoprefixer = require('gulp-autoprefixer')
const rename       = require('gulp-rename')


function scss () {
    return gulp.src(['./src/pages/**/*.scss', './src/components/**/*.scss'], {base: './src'})
               .pipe(autoprefixer({
                   browsers: ['last 2 version', 'safari 5', 'ie 8', 'ie 9', 'opera 12.1', 'ios 6', 'android 4'],
                   cascade: true,
                   remove: true
               }))
               .pipe(sass().on('error', sass.logError))
               .pipe(rename(function (path) {
                  console.log(path);
                  path.extname = '.wxss';
               }))
               .pipe(gulp.dest('./src'))
}

// 编译sass
gulp.task(scss)


// 静态服务器
gulp.task('serve', function() {
    gulp.watch(['./src/pages/**/*.scss', './src/components/**/*.scss'], scss)
})

// 开始
gulp.task('default', gulp.series('scss', 'serve'))
```



