---
layout: page
title: Використання шаблонізаторів в Express
menu: guide
lang: uk
---

# Використання шаблонізаторів в Express

A _template engine_ enables you to use static template files in your application.   At runtime, the template engine replaces
variables in a template file with actual values, and transforms the template into an HTML file sent to the client.
This approach makes it easier to design an HTML page.

Some popular template engines that work with Express are [Pug](https://pugjs.org/api/getting-started.html),
[Mustache](https://www.npmjs.com/package/mustache), and [EJS](https://www.npmjs.com/package/ejs).
The [Express application generator](/expressjs.com/{{ page.lang }}/starter/generator.html) uses Pug as its default, but it also supports several others.

See [Template Engines (Express wiki)](https://github.com/expressjs/express/wiki#template-engines)
for a list of template engines you can use with Express.
See also [Comparing JavaScript Templating Engines: Jade, Mustache, Dust and More](https://strongloop.com/strongblog/compare-javascript-templates-jade-mustache-dust/).

To render template files, set the following [application setting properties](/expressjs.com/{{ page.lang }}/4x/api.html#app.set):

* `views`, the directory where the template files are located. Eg: `app.set('views', './views')`.
This defaults to the `views` directory in the application root directory.
* `view engine`, the template engine to use. For example, to use the Pug template engine: `app.set('view engine', 'pug')`.

Then install the corresponding template engine npm package; for example to install Pug:

<pre><code class="language-sh" translate="no">
$ npm install pug --save
</code></pre>

<div class="doc-box doc-notice" markdown="1">
Express-compliant template engines such as Pug export a function named `__express(filePath, options, callback)`,
which is called by the `res.render()` function to render the template code.

Some template engines do not follow this convention. The [Consolidate.js](https://www.npmjs.org/package/consolidate)
library follows this convention by mapping all of the popular Node.js template engines, and therefore works seamlessly within Express.
</div>

After the view engine is set, you don't have to specify the engine or load the template engine module in your app;
Express loads the module internally, as shown below (for the above example).

<pre><code class="language-javascript" translate="no">
app.set('view engine', 'pug');
</code></pre>

Create a Pug template file named `index.pug` in the `views` directory, with the following content:

<pre><code class="language-javascript" translate="no">
html
  head
    title= title
  body
    h1= message
</code></pre>

Then create a route to render the `index.pug` file. If the `view engine` property is not set,
you must specify the extension of the `view` file. Otherwise, you can omit it.

<pre><code class="language-javascript" translate="no">
app.get('/', function (req, res) {
  res.render('index', { title: 'Hey', message: 'Hello there!'});
});
</code></pre>

When you make a request to the home page, the `index.pug` file will be rendered as HTML.

To learn more about how template engines work in Express, see:
["Developing template engines for Express"](/expressjs.com/{{ page.lang }}/advanced/developing-template-engines.html).
