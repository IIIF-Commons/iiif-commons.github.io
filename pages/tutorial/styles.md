---
title: Custom Styles and Images
sidebar: tutorial_sidebar
permalink: tutorial_styles.html
folder: tutorial
---

## Create custom styles with LESS

Since I know that I'm going to want to have some custom CSS and icons for my component, the next thing I do is create the following two directories in the `src` directory: `css` and `img` . I create a simple `styles.less` file in `css` and add a `.paper` class to style our canvas like so:

```css
@img-path: "../img/"

.svg-draw-component{
    /* someplace to put component-specific css */
    .paper{
        width:800px; height:600px;
        margin:20px 60px;
        border:1px solid blue;
        background-color: rgba\(158, 167, 184, 0.2\);}
}
```

We can leave the `img` directory blank for now.

## Configure gulp to compile LESS styles on build

In order for the less file to be compiled into css, we need to add a npm module called `gulp-less` and we also need to add gulp tasks to ensure the compiled css files are copied into the appropriate location in `examples` when our build runs. To add the gulp-less npm module to the package.json devDependencies, type the following npm command:

`npm install gulp-less --save-dev`

Now, we will create our gulp tasks. I add the following lines to the `tasks/copy.js`:

```js
gulp.task('copy:css', function() {
 return gulp.src([path.join(config.dist, config.cssOut)]).pipe(gulp.dest(config.examplesCssDir));
});

gulp.task('copy:img',other function() {
 return gulp.src(config.imgSrc).pipe(gulp.dest(config.examplesImgDir));
});
```

We also need to add a file called less.js to the `tasks` directory. It looks like this:

```js
var c = require('../gulpfile.config');
var config = new c();
var gulp = require('gulp');
var less = require('gulp-less');
var path = require('path');
var rename = require('gulp-rename');

gulp.task('less', function () {
 return gulp.src(config.cssSrc)
     .pipe(less({
         paths: [ path.join(__dirname, 'less', 'includes') ]
     }))
     .pipe(rename(config.cssOut))
     .pipe(gulp.dest(config.dist));
});
```

Finally, we add these tasks to the `gulpfile.js` . Add 'less' to the default runSequence here:

```js
runSequence('clean:dist', 'build', 'browserify', 'less', 'minify', ...
```

And add our `copy:css` and `copy:img` tasks to the 'sync' task:

```js
gulp.task('sync', ['copy:bundle', 'copy:css', 'copy:img', 'copy:typings']);
```
