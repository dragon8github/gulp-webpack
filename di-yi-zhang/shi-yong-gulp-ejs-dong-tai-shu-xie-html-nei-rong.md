传送门

> [https://github.com/babel/gulp-babel](https://github.com/rogeriopvl/gulp-ejs)

npm安装

> $ npm install --save-dev gulp-ejs

### Example

gulpfile.js

```js
const ejs          = require("gulp-ejs")

function compile () {
    const files = fs.readdirSync('./components')
    let components = [];
    files.forEach(function (item, index) {
        var stat = fs.lstatSync("./components/" + item);
        if (stat.isDirectory() === true) components.push(item)
    })
    return gulp.src('./index.html')
               .pipe(ejs({
                   components: components
               }))
               .pipe(gulp.dest('./components'))
}

// 编译ejs
gulp.task(compile)
```

index.html

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <ul>
        <% components.forEach(function(name){ %>
        <li><a href="./<%= name %>"><%= name %></a></li>
        <% }); %>
    </ul>
</body>
</html>
```



