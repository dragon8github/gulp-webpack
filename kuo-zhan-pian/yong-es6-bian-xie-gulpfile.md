据我所知，nodejs6.x的版本都已经支持部分 es6 了。但不支持import / export 模块导出导入语法。

虽然没什么卵用，但还是介绍一下吧。

---

1、首先gulpfile.js 改名为 gulpfile.babel.js

```js
import * as test from './test'
import gulp from 'gulp'

gulp.task('dev', function () {
    console.log(123);
})
```

2、下载核心插件

```
$ npm install babel-register babel-preset-env --save
```

3、新建.babelrc文件

```js
{
  "presets": ["env"]
}
```

4、运行一下

```
$ gulp dev
```



