传送门

> [https://github.com/twolfson/gulp.spritesmith](https://github.com/twolfson/gulp.spritesmith)

npm安装

> $ cnpm install gulp.spritesmith --save-dev

### ‍💻 Example

```js
var gulp = require('gulp');
var spritesmith = require('gulp.spritesmith');
var buffer = require('vinyl-buffer');
var csso = require('gulp-csso');
var imagemin = require('gulp-imagemin');
var merge = require('merge-stream');

gulp.task('sprite', function () {
  var spriteData = gulp.src('images/*.png').pipe(spritesmith({
    imgName: 'assets/images/sprite.png',
    cssName: 'assets/scss/sprite.scss',
    cssTemplate: 'sprite.handlebars',
    cssFormat: 'scss',
    padding: 8
  }));

  var imgStream = spriteData.img.pipe(buffer()).pipe(imagemin())
  var cssStream = spriteData.css.pipe(csso())

  return merge(imgStream, cssStream).pipe(gulp.dest('dist/'));
});
```

### 🍎 sprite.handlebars

```css
{{#sprites}}
.icon-{{name}}:before {
  display: block;
  background-image: url('{{image}}');
  background-position: {{px.offset_x}} {{px.offset_y}};
  width: {{px.width}};
  height: {{px.height}};
}
{{/sprites}}
```

### 🏆 Result

```bash
C:\Users\Lee\Desktop\123>gulp sprite
[20:57:06] Failed to load external module @babel/register
[20:57:06] Requiring external module babel-register
[20:57:07] Using gulpfile ~\Desktop\123\gulpfile.babel.js
[20:57:07] Starting 'sprite'...
[20:57:09] gulp-imagemin: Minified 1 image (saved 5.87 kB - 42.2%)
[20:57:09] Finished 'sprite' after 1.47 s
```

---

### Q&A

1、`sprite.handlebars` 中的变量，我如何获取和查看？

可以查看 github ，或者使用 cssVarMap 来查看和自定义

```js
 let spriteData = gulp.src(paths.src.sliceDir + `${slicePath}/*.png`).pipe(spritesmith({
      imgName: `${folder||'sprite'}.png`,
      cssName: `${folder||'sprite'}.scss`,
      cssFormat: 'scss',
      cssVarMap(sprite) {
        sprite.name = `${config.sprite.prefix}${folder ? '-' + folder : ''}-${sprite.name}`;
      },
      cssTemplate: 'templates/sprite.handlebars',
      algorithm: config.sprite.algorithm,
      padding: 8
  }));
```



