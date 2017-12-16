第三方教程

> [http://blog.csdn.net/lensgcx/article/details/71420058](http://blog.csdn.net/lensgcx/article/details/71420058)
>
> [https://segmentfault.com/a/1190000002580846\#articleHeader5](https://segmentfault.com/a/1190000002580846#articleHeader5)

官方插件

> [https://gulpjs.com/plugins/](https://gulpjs.com/plugins/)

官方api文档

> [https://github.com/gulpjs/gulp/blob/master/docs/API.md](https://github.com/gulpjs/gulp/blob/master/docs/API.md)

---

## gulp命令 {#articleHeader3}

你仅仅需要知道的5个`gulp`命令

```js
gulp.task(name[, deps], fn) 定义任务  name：任务名称 deps：依赖任务名称 fn：回调函数

gulp.run(tasks...)：尽可能多的并行运行多个task

gulp.watch(glob, fn)：当glob内容发生改变时，执行fn

gulp.src(glob)：置需要处理的文件的路径，可以是多个文件以数组的形式，也可以是正则

gulp.dest(path[, options])：设置生成文件的路径
```



