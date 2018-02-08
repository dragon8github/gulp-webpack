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



