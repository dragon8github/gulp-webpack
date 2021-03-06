传送门

> [https://github.com/VFK/gulp-html-replace](https://github.com/VFK/gulp-html-replace)

说明：该插件可能并没有你想象的强大或者复杂。他的作用仅仅是通过一定的规则。替换掉html页面中的资源引用而已。没有别的了。具体操作如下

---

## Example

index.html

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>

   <!-- build:fuckjs -->
   <script src="./src/js/a.js"></script>
   <script src="./src/js/b.js"></script>
   <script src="./src/js/c.js"></script>
   <!-- endbuild -->
</body>
</html>
```

gulpfile.js

```js
'use strict';
const gulp = require('gulp');
const htmlreplace = require('gulp-html-replace');

gulp.task('default', function() {
      gulp.src('./index.html')
        .pipe(htmlreplace({
            'css': './dist/assets/css/main.min.css',
            'fuckjs': './dist/assets/js/main.min.js'
        }))
        .pipe(gulp.dest('./dist/'));
});
```

Result:

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>

   <script src="./dist/assets/js/main.min.js"></script>
</body>
</html>
```

没错，就这么简单。它并没有合并a.js + b.js + c.js。仅仅是将Html中的内容替换了。实际上我们还要手动的将这些js合并并且保存到 ./dist/assets/js/main.min.js 中才有意义。

但这样做的意义还是有的，就是很好的区分开发和发布的资源情况（前提是你知道这个插件的作用。）

