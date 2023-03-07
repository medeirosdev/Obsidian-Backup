## [#](https://handlebarsjs.com/guide/#installation)Installation

The fastest way to test Handlebars is to load it from a _CDN_ and embed it in an HTML file.

```
<!-- Include Handlebars from a CDN -->
<script src="https://cdn.jsdelivr.net/npm/handlebars@latest/dist/handlebars.js"></script>
<script>
  // compile the template
  var template = Handlebars.compile("Handlebars <b>{{doesWhat}}</b>");
  // execute the compiled template and print the output to the console
  console.log(template({ doesWhat: "rocks!" }));
</script>
```

WARNING

This method can be used for small pages and for testing. There are several other ways to use Handlebars, when you target real production systems.

[Learn more: Installation](https://handlebarsjs.com/installation/)

There are a variety of ways to install Handlebars, depending on the programming language and environment you are using.

## [#](https://handlebarsjs.com/installation/#npm-or-yarn-recommended)npm or yarn (recommended)

The reference implementation of Handlebars is written in JavaScript. It is most commonly installed using `npm` or `yarn`:

```
npm install handlebars
# or
yarn add handlebars
```

You can then use Handlebars using `require`

```
const Handlebars = require("handlebars");
const template = Handlebars.compile("Name: {{name}}");
console.log(template({ name: "Nils" }));
```

TIP

Using npm or yarn is the recommended way of using Handlebars. If you want to use Handlebars templates in the web-browser, we recommend that you use a build-engine such as Webpack, Browserify or Parcel.

The [integrations](https://handlebarsjs.com/installation/integrations.html) page contains a list of plugins for those loaders that allow you to automatically precompile templates or use Handlebars otherwise.

[Learn more: Integrations](https://handlebarsjs.com/installation/integrations.html)

### [#](https://handlebarsjs.com/installation/#browser-builds-in-the-npm-package)Browser builds in the npm-package

The browser builds are located in the `node_modules/handlebars/dist/` directory. Making these accessible to the browser will depend on what build system you are using but this may be as simple as copying the files to an accessible place.

This is the preferred method of installation when using the precompiler as it ensures that your precompiled templates always run against the same version of the runtime.

## [#](https://handlebarsjs.com/installation/#downloading-handlebars)Downloading Handlebars

The following downloads are provided as a convenience to the community. They are not meant for production use, but they can give you a quick-start without having to set up a build-engine.

### [#](https://handlebarsjs.com/installation/#latest-release-version-handlebarsversions-latest)Latest release (version 4.7.7)

[Handlebars 4.7.7 (compiler + runtime)](https://s3.amazonaws.com/builds.handlebarsjs.com/handlebars-v4.7.7.js "Download Handlebars 4.7.7 (compiler + runtime)") [minified](https://s3.amazonaws.com/builds.handlebarsjs.com/handlebars.min-v4.7.7.js "Download minified Handlebars 4.7.7 (compiler + runtime)") 

Use this version as a quick start, if you want to compile your templates in the browser.

[Handlebars 4.7.7 (runtime only)](https://s3.amazonaws.com/builds.handlebarsjs.com/handlebars.runtime-v4.7.7.js "Download Handlebars 4.7.7 (runtime only)") [minified](https://s3.amazonaws.com/builds.handlebarsjs.com/handlebars.runtime.min-v4.7.7.js "Download minified Handlebars 4.7.7 (runtime only)") 

Use this version when you are using [precompiled templates](https://handlebarsjs.com/installation/precompilation.html) in the browser. This version does not include the compiler.

### [#](https://handlebarsjs.com/installation/#non-release-builds)Non-release builds

All of Handlebars' released versions and CI builds are available for download on S3 in our [builds page (opens new window)](https://com.s3.amazonaws.com/builds.handlebarsjs/bucket-listing.html?sort=lastmod&sortdir=desc).

The latest passing master build is named `handlebars-latest.js` and each passing SHA on master will create a `handlebars-gitSHA.js` file. While these all pass the CI, it's preferable to use one of the tagged releases.

**Note**: The builds page is provided as a convenience for the community, but you should not use it for hosting Handlebars in production.

## [#](https://handlebarsjs.com/installation/#cdns)CDNs

Handlebars is hosted on a number of free CDNs as well.

-   [cdnjs(opens new window)](https://cdnjs.com/libraries/handlebars.js)
-   [jsDelivr (opens new window)](http://www.jsdelivr.com/#!handlebarsjs). Advanced usage, such as [version aliasing & concocting (opens new window)](https://github.com/jsdelivr/jsdelivr#usage), is available.

## [#](https://handlebarsjs.com/installation/#rubygems)RubyGems

The official Handlebars build is available on https://rubygems.org/gems/handlebars-source

## [#](https://handlebarsjs.com/installation/#bower-component-composer-jspm)Bower, Component, Composer, jspm

Handlebars can be enabled by using other package-managers as well, like

-   Bower (deprecated)
-   Component
-   Composer
-   jspm

see https://github.com/components/handlebars.js for details

## [#](https://handlebarsjs.com/installation/#usage)Usage

You can deliver a template to the browser by including it in a `<script>` tag.

```
<script id="entry-template" type="text/x-handlebars-template">
  <div class="entry">
    <h1>{{title}}</h1>
    <div class="body">
      {{body}}
    </div>
  </div>
</script>
```

Always use a script-tag for your template

If you use this method, you have to wrap your template with a script-tag. Otherwise the browser may remove or modify parts of your template if you don't. Have a look at ["Unexpected markup in tables" (opens new window)](https://html.spec.whatwg.org/multipage/parsing.html#unexpected-markup-in-tables)for an example.

Compile a template in JavaScript by using Handlebars.compile

```
var source = document.getElementById("entry-template").innerHTML;
var template = Handlebars.compile(source);
```

Get the HTML result of evaluating a Handlebars template by executing the template with a context.

```
var context = { title: "My New Post", body: "This is my first post!" };
var html = template(context);
```

results in

```
<div class="entry">
  <h1>My New Post</h1>
  <div class="body">
    This is my first post!
  </div>
</div>
```

### [#](https://handlebarsjs.com/installation/#precompiling-templates)Precompiling Templates

In the previous example, we have loaded the compiler-and-runtime version of Handlebars. It is much more efficient, to compile your templates beforehand and include the precompiled version in your website. You can include the smaller runtime and the browser does not have to compile the templates before running them.

[Learn More: Precompilation](https://handlebarsjs.com/installation/precompilation.html)