# Front End Developers Website

This repository contains all the files for the Front End Developers website.

## Getting Started

### Dependencies

Make sure these are installed first.

* [Node.js](http://nodejs.org)
* [Gulp](http://gulpjs.com) `sudo npm install -g gulp`

### Quick Start

1. In bash/terminal/command line, `cd` into your project directory.
2. Run `npm install` to install required files.
3. When it's done installing, run one of the task runners to get going:
  * `gulp` automatically watch for changes and compile files, lints JavaScript and server and synchronise changes to the browser via [Browsersync](https://www.browsersync.io/) accordingly; 
  * `gulp build` will manually compile files and lint JavaScript without serving the files to the browser.
  
## File Structure

Add your files to the appropriate `src` subdirectories. Gulp will process and and compile them into `dist`.

* Content in subdirectories under the `js` directory will be concatenated;
* Image files (including svg files) placed in the `img` directory will be optimised and copied into the `dist/assets/img` directory;
* SVG files placed in the `src/sprite` directory will be optimized and compiled into the `dist/assets/img` directory as a `sprite.svg` file.

```
gulp-boilerplate/
|—— dist/
|   |—— assets/
|   |   |—— css/
|   |   |   |—— critical.min.css
|   |   |   |—— main.min.css
|   |   |—— fonts/
|   |   |   |—— # font files
|   |   |—— img/
|   |   |   |—— # image files
|   |   |—— js/
|   |   |   |—— scripts.min.js
|   |—— favicon.icon
|   |—— humans.txt
|   |—— index.html
|   |—— manifest.json
|   |—— robots.txt
|   |—— service-worker.js
|   |—— # static assets
|—— src/
|   |—— img/
|   |   |—— # image files
|   |   |—— touch/
|   |   |   |—— apple-touch-icon.png
|   |   |   |—— chrome-touch-icon-192x192.png
|   |   |   |—— icon.png
|   |   |   |—— ms-touch-icon-144x144-precomposed.png
|   |—— js/
|   |   |—— # script files
|   |—— scss/
|   |—— sprite/
|—— .babelrc
|—— .editorconfig
|—— .eslintrc
|—— .gitignore
|—— gulpfile.babel.js
|—— LICENSE
|—— package.json
|—— readme.md
```

## Working with the Source Files

### Sass

This project uses the ITCSS structure and makes use of imports to allow for a critical stylesheet to be generated alongside you main stylesheet. 

Sass files are located in `src` > `sass`. Gulp generates minified and unminified CSS files. It also includes [autoprefixer](https://github.com/postcss/autoprefixer), which adds vendor prefixes for you if required by the last two versions of a browser.

### JavaScript

JavaScript files are located in the `src/js` directory.

All script files placed in this directory will be concatinated and minified into a single `scripts.min.js` file compiled directly into the `dist/assets/js` directory.

### Images

Image files placed in the `src/img` directory will be optimised and copied into the `dist/assets/img` directory. The `src/touch` directory contains some placeholder images various touch devices. These are compiled into the subdirectory `dist/assets/img/touch` and referenced, if required, in the head of `dist/index.html`.

*Note:* Although the `images` task has image optimisation enable through the [imagemin](https://www.npmjs.com/package/gulp-imagemin) plugin images can sometimes be further optimise with [ImageOptim](https://imageoptim.com/) and [b64.io](http://b64.io/).

### SVG sprite

SVG files placed in the `src/svg` directory will be compiled into a single SVG sprite named `sprite.svg` and compiled to the `dist/assets/img` directory. This can then be loaded into the page with ajax via a snippet which resides in the `<head>` of `dist/index.html`.

## Options and Settings

### Updating Project Details

Open up `package.json` to change the name, version, URL and other data about the project. The following values are used in the banner which is inserted in the top of the compiled files.

* Name;
* Title;
* URL;
* Author;
* Version;
* License.

### Changing the Directory Structure

Inside `gulpfile.babel.js` you'll see group of constants in the `Directory Templates` section. Adjust the paths to suit your workflow.

```
const project = {
  src: 'src',
  dist: 'dist'
};

const scssPath = {
  src: `${project.src}/scss/**/*.scss`,
  dest: `${project.dist}/assets/css/`
};

const jsPath = {
  src: [
    `${project.src}/js/plugins/*.js`,
    `${project.src}/js/*.js`
  ],
  dest: `${project.dist}/assets/js`
};

const imagePath = {
  src: `${project.src}/img/{,*/}*.{jpg,jpeg,png,gif,svg}`,
  dest: `${project.dist}/assets/img`
};

const spritePath = {
  src: `${project.src}/sprite/{,*/}*.svg`,
  dest: `${project.dist}/assets/img`
}
```

## TODO

- Build website [ O ]
- Integrate with slack [ O ]
