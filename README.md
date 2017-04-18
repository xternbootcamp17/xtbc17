# XTBC17 Source

This is the source for [xternbootcamp17.github.io](http://xternbootcamp17.github.io). Build and deploy the site with [Hugo](https://gohugo.io/).

For development, run each of the following commands in separate terminals:

```bash
hugo serve
```

```bash
npm start
```

The first command starts Hugo's development server (on port 1313 by default) and features hot-reloading.

Hugo does not include support for CSS or JavaScript preprocessors, so we've added `package.json` with appropriate scripts for compiling stylesheets. It's configured for [Stylus](http://stylus-lang.com/), which is very similar to SASS/SCSS. Unlike SASS, it is compiled with JavaScript and doesn't require Ruby. You can also mix SCSS style (with semicolons and curly braces) and SASS style (with significant whitespace) within the same file. Stylus has its own syntax for variables, mixins, etc.

Stylus files are located in `static-src/css-src`, and the compiled CSS will be placed in `/static/css`, where Hugo expects to find stylesheets. The npm script will watch for changes in the `.styl` files, and Hugo will pick up the resulting changes in the `.css` files and hot-reload.

We've also added [autoprefixer](https://github.com/postcss/autoprefixer), which adds vendor prefixes to CSS rules using values from [Can I Use](http://caniuse.com/).
