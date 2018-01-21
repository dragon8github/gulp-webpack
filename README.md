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

---

## 为什么使用gulp？

> 根本目的是搭建一套前端自动化流程。

但没有经历前端工程化和自动化的同学很可能一时手足无措，不知从何下手。事实上这是很正常的。

哪怕是熟练每个gulp插件的开发者，在构建自己的开发环境和生产编译环境时也需要反复斟酌、反复思考、谨慎搭配、匠心搭建。

毕竟每个人的开发场景都不一样，想要配置出一套一通百通的gulp环境几乎是不可能的。

但总有一些是我们期待的共识，我们是可以投入生产的。

通过将这些通用的套路结合在一起，保存并且作为基础架构。然后根据不同的项目类型和工作场景，在基础架构的基础上再一次进行构建、迭代优化、个性化配置。这就是gulp的最佳实践。

这也是组件化的思路。方便我们不断的迭代和升级我们的架构。是一个非常好的开发习惯。适应任何的架构和开发。

