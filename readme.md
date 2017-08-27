## gulp-query-postcss
Plugin for [gulp-query](https://github.com/gulp-query/gulp-query)

Uses [postcss](https://github.com/postcss/postcss)

This plugin provides postcss with plugins, automatic source maps, combine and rename.

```
npm install gulp-query gulp-query-postcss
```

### Example
Paste the code into your `gulpfile.js` and configure it
```javascript
let build = require('gulp-query')
  , postcss = require('gulp-query-postcss')
;
cocktail(function (query) {
    query.plugins([postcss])
      .postcss(['1.css','2.css'],'css/12.css',{
        name: 'onetwo',
        plugins: [
          autoprefixer({browsers: ['last 1 version']}),
          cssnano()
        ]
      })
      ;
});
```
And feel the freedom
```
gulp
gulp --production // For production
gulp watch // Watching change
gulp postcss // Only for postcss
gulp postcss:onetwo
gulp postcss watch
...
```

### Options
```javascript
.postcss({
    name: "task_name", // For gulp postcss:task_name 
    from: 'css_source/*.css', // ['1.css','2.css']
    to: "css/",
    source_map: true,
    source_map_type: 'inline',
    full: false, // if set true is without compress in prod
    plugins: [] // Plugins for Postcss
})
```