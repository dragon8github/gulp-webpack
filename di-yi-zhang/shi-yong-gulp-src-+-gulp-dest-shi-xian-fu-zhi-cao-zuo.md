官方API

```
https://www.gulpjs.com.cn/docs/api/
```

#### ⚽️ gulp.src 的使用 与 options.base 参数

请想像一下在一个路径为 client/js/somedir 的目录中，有一个文件叫 somefile.js ：

```js
gulp.src('client/js/**/*.js') // 匹配 'client/js/somedir/somefile.js' 并且将 `base` 解析为 `client/js/`
  .pipe(minify())
  .pipe(gulp.dest('build'));  // 写入 'build/somedir/somefile.js'

gulp.src('client/js/**/*.js', { base: 'client' })
  .pipe(minify())
  .pipe(gulp.dest('build'));  // 写入 'build/js/somedir/somefile.js'
```

默认编译输出的路径是匹配到标识符（正则表达式）。但使用 options.base 参数就可以指定自己要的相对路径了。

