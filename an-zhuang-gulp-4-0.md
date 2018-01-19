> Gulp 4.0 第三方介绍：
>
> [http://web.jobbole.com/82992/](http://web.jobbole.com/82992/)
>
> [http://zhangruojun.com/gulpshun-xu-zhi-xing-ren-wu/](http://zhangruojun.com/gulpshun-xu-zhi-xing-ren-wu/)
>
> 更新日志：
>
> [https://github.com/gulpjs/gulp/blob/4.0/CHANGELOG.md](https://github.com/gulpjs/gulp/blob/4.0/CHANGELOG.md)
>
> gulp 4.0 异常处理：
>
> [1、【Did you forget to signal async completion?](https://stackoverflow.com/questions/36897877/gulp-error-the-following-tasks-did-not-complete-did-you-forget-to-signal-async)】

### 🏡 安装gulp 4.0

想体验4.0只有通过github安装，执行以下两条命令即可在本地畅爽地使用gulp 4.0了。

```js
$ npm install gulpjs/gulp#4.0 -g

$ npm install gulpjs/gulp#4.0 --save-dev
```

### 🎲 Gulp 4.0 核心的变化：

* gulp.task 的变化；

* 增加了gulp.series（串行） 和 gulp.parallel（并行）

#### 1、gulp.task 的变化📭

#### 2、增加了gulp.series（串行） 和 gulp.parallel（并行）

首先要了解什么是串行，什么是并行：

* 串行：顺序执行，前面一个（异步）执行完了，后面一个才能执行。环环相扣，就像一个铁环链、责任链一般。
* 并行：同时执行，不分你我，没有顺序。就像起跑线上的运动员一样，不需要顾及其他人。

**比如当我们这样写的时候`（'clean', 'compass', [image', 'style', 'html']，'ftp'）`，我们期待圆括号里面串行执行，中括号里面并行执行。**

[**gulp 4.0**](https://github.com/gulpjs/gulp/issues/803) 也提供了新的API\(series、parallel\)来解决这个问题。**series**里的任务是顺序执行的，**parallel**里的任务是同时执行的。

```js
const gulp = require('gulp');

gulp.task('clean',   function(done) { console.log('clean');   done(); });
gulp.task('compass', function(done) { console.log('compass'); done(); });
gulp.task('image',   function(done) { console.log('image');   done(); });
gulp.task('style',   function(done) { console.log('style');   done(); });
gulp.task('html',    function(done) { console.log('html');    done(); });
gulp.task('ftp',     function(done) { console.log('ftp');     done(); });

gulp.task('prod', gulp.series('clean', 'compass', gulp.parallel('image', 'style', 'html'), 'ftp')); 
```

执行 `gulp prod`输出的任务执行情况：🏡

![](/assets/asd123dfsdfsdfimport.png)

