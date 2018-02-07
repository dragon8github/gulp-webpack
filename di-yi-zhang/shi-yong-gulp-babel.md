传送门

> [https://github.com/babel/gulp-babel](https://github.com/babel/gulp-babel)

npm安装

> $ cnpm install gulp-babel babel-core babel-preset-env babel-plugin-transform-runtime babel-preset-stage-2 --save-dev

Example

```js
const gulp         = require('gulp');
const babel        = require('gulp-babel');
const sourcemaps   = require('gulp-sourcemaps');

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

执行一下

```
$ gulp babel_env
```



