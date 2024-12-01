---
project: gulp-hb
stars: 148
description: A sane Gulp plugin to compile Handlebars templates. Useful as a static site generator.
url: https://github.com/shannonmoeller/gulp-hb
---

`gulp-hb`
=========

A sane static Handlebars Gulp plugin. Useful as a static site generator. Powered by `handlebars-wax`. Think Assemble, but with a lot less Jekyll baggage.

To precompile templates into JavaScript, see `gulp-handlebars`.

Install
-------

$ npm install --save-dev gulp-hb

Usage
-----

const gulp \= require('gulp');
const hb \= require('gulp-hb');

// Basic

function basic() {
    return gulp
        .src('./src/{,posts/}\*.html')
        .pipe(hb()
            .partials('./src/assets/partials/\*\*/\*.hbs')
            .helpers('./src/assets/helpers/\*.js')
            .data('./src/assets/data/\*\*/\*.{js,json}')
        )
        .pipe(gulp.dest('./web'));
}

gulp.task('basic', basic);

// Advanced

function advanced() {
    const hbStream \= hb({ debug: true })
        // Partials
        .partials('./partials/components/\*\*/\*.{hbs,js}')
        .partials('./partials/layouts/\*\*/\*.{hbs,js}')
        .partials({
            boo: '{{#each boo}}{{greet}}{{/each}}',
            far: '{{#each far}}{{length}}{{/each}}'
        })

        // Helpers
        .helpers(require('handlebars-layouts'))
        .helpers('./helpers/\*\*/\*.js')
        .helpers({
            foo: function () { ... },
            bar: function () { ... }
        })

        // Decorators
        .decorators('./decorators/\*\*/\*.js')
        .decorators({
            baz: function () { ... },
            qux: function () { ... }
        })

        // Data
        .data('./data/\*\*/\*.{js,json}')
        .data({
            lorem: 'dolor',
            ipsum: 'sit amet'
        });

    return gulp
        .src('./src/{,posts/}\*.html')
        .pipe(hbStream)
        .pipe(gulp.dest('./web'));
}

gulp.task('advanced', advanced);

### Template Context

The template context is a merge of pre-registered data and file-specific data. Pre-registered data is available to all templates and is set using the `.data()` method. File-specific data is available to the current template and is set via the `file.data` property.

#### `@` Data Variables

##### @root

The merged object of pre-registered data and file-specific data is available as the primary context of your templates. In cases where accessing this data would require the use of `../`, you may access the top-level context via `@root`:

{{ foo }}
{{ @root.foo }}

{{#each bar}}
    {{ ../foo }}
    {{ @root.foo }}
{{/each}}

##### @global

In cases where file-specific data keys collide with pre-registered data keys, you may access the pre-registered data via `@global`:

{{ @global.foo }}

##### @local

In cases where pre-registered data should be ignored, you may access the file-specific data via `@local`.

{{ @local.foo }}

##### @file

In cases where information about the template file itself is needed, you may access the file object via `@file`:

{{ @file.path }}

#### File-specific Data Sources

File-specific data is set via the `file.data` property using other plugins such as `gulp-data`, `gulp-data-json`, or `gulp-front-matter`.

const gulp \= require('gulp');
const data \= require('gulp-data');
const frontMatter \= require('gulp-front-matter');
const hb \= require('gulp-hb');

function inject() {
    return gulp
        .src('./src/\*.html')

        // Load an associated JSON file per post.
        .pipe(data((file) \=> {
            return require(file.path.replace('.html', '.json'));
        }))

        // Parse front matter from post file.
        .pipe(frontMatter({
            property: 'data.frontMatter'
        }))

        // Data for everyone.
        .pipe(hb().data('./data/\*\*/\*.js'))

        .pipe(gulp.dest('./web'));
}

gulp.task('inject', inject);

#### Multiple Data Sources

Multiple data sources can be used to render the same set of templates to different directories using `through2`.

const gulp \= require('gulp');
const hb \= require('gulp-hb');
const through \= require('through2');

function i18n() {
    return gulp
        .src('./i18n/\*.json')
        .pipe(through.obj((file, enc, cb) \=> {
            const locale \= file.stem;
            const data \= {
                locale: locale,
                i18n: JSON.parse(file.contents.toString())
            };

            gulp
                .src('./templates/\*\*/\*.html')
                .pipe(hb().data(data))
                .pipe(gulp.dest('./dist/' + locale))
                .on('error', cb)
                .on('end', cb);
        }));
}

gulp.task('i18n', i18n);

API
---

### `hb([options]): TransformStream`

-   `options` `{Object}` (optional) Passed directly to `handlebars-wax` so check there for more options.
    -   `bustCache` `{Boolean}` (default: `true`) Force reload data, partials, helpers, and decorators.
    -   `cwd` `{String}` (default: `process.cwd()`) Current working directory.
    -   `debug` `{Boolean|Number}` (default: `false` or `0`) Whether to log registered functions and data (`true` or `1`) and glob parsing (`2`).
    -   `handlebars` `{Handlebars}` (optional) A specific instance of Handlebars, if needed.
    -   `compileOptions` `{Object}` Options to use when compiling templates.
    -   `templateOptions` `{Object}` Options to use when rendering templates.
    -   `partials` `{String|Array.<String>|Object|Function(handlebars)}`
    -   `parsePartialName` `{Function(options, file): String}`
    -   `helpers` `{String|Array.<String>|Object|Function(handlebars)}`
    -   `parseHelperName` `{Function(options, file): String}`
    -   `decorators` `{String|Array.<String>|Object|Function(handlebars)}`
    -   `parseDecoratorName` `{Function(options, file): String}`
    -   `data` `{String|Array.<String>|Object}`
    -   `parseDataName` `{Function(options, file): String}`

Returns a Gulp-compatible transform stream that compiles Handlebars templates to static output.

### .partials(pattern \[, options\]): TransformStream

-   `pattern` `{String|Array<String>|Object|Function(handlebars)}`
-   `options` `{Object}` Same options as `hb()`.

Loads additional partials. See `handlebars-wax`.

### .helpers(pattern \[, options\]): TransformStream

-   `pattern` `{String|Array<String>|Object|Function(handlebars)}`
-   `options` `{Object}` Same options as `hb()`.

Loads additional helpers. See `handlebars-wax`.

### .decorators(pattern \[, options\]): TransformStream

-   `pattern` `{String|Array<String>|Object|Function(handlebars)}`
-   `options` `{Object}` Same options as `hb()`.

Loads additional decorators. See `handlebars-wax`.

### .data(pattern \[, options\]): TransformStream

-   `pattern` `{String|Array<String>|Object}`
-   `options` `{Object}` Same options as `hb()`.

Loads additional data. See `handlebars-wax`.

Contribute
----------

Standards for this project, including tests, code coverage, and semantics are enforced with a build tool. Pull requests must include passing tests with 100% code coverage and no linting errors.

### Test

$ npm test

* * *

MIT © Shannon Moeller
