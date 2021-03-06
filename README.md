##generator-webapp with gulp-uncss##

The aim of this repository is to test the integration of the [Yeoman webapp generator](https://github.com/yeoman/generator-webapp) with gulp-uncss. This is **not** a generator; this is code **generated** by Yeoman and then modified to handle an additional plugin. I intend to create a custom generator once my organization has determined which modifications (to Gulp functionality, to project dependencies, or to the file structure, for example) would be beneficial.

A Grunt-centered version of this actually already [exists](https://github.com/addyosmani/generator-webapp-uncss). Despite being more familiar with Grunt (and being partial to pre-built solutions), I decided not to make use of it because it is not actively maintained, and because because I encountered serious issues with mocha and other dependencies.

To test, you must have the necessary tools installed and then carry out the steps outlined below:

##Requirements##

* [Node](https://nodejs.org/en/)
* [npm](https://www.npmjs.com/)
* [generator-webapp](https://github.com/yeoman/generator-webapp) -- the steps listed here will also have you install Yeoman, gulp-cli, and Bower.

My personal machine is a 2013 iMac running Yosemite (10.10.5), Node v5.8.0, npm v3.7.3, Yeoman v.1.7.0, Gulp v3.9.1- (CLI version 3.9.0), and Bower v1.7.7.

My work machine is a 2015 ASUS PC running Windows 10 Home, Node v4.2.3, npm v3.5.3, Yeoman v.1.7.0, Gulp v3.9.1 (CLI version 1.2.1), and Bower v1.7.7.

##Steps##

1. clone this repo
2. run `npm install`
3. run `bower install`
4. run `gulp serve` to preview and watch for changes
5. run `gulp` to build your webapp for production (*note: this is when the uncss task takes place*)
6. run `gulp serve:dist` to preview the production build

##Confirm that uncss is working as expected##

Within `app/styles/main.scss` you will find a bit of *unused* css. In other words, there is no HTML that instantiates these classes:

```scss
.no-way-jose {
  color: red;
  .blacklivesmatter {
    background-color: #666;
  }
}
```

By default, the uncss plugin will strip these rules from the outputted CSS file (main.css); run `gulp` and then inspect dist/styles/main.css. This file should be small and the above rules should be nowhere to be found.

However, if one of these classes is added to the markup, and the `gulp` command is run again (re-populating the dist directory with updated code), you should be able to see that class when you inspect main.css (or when you run `gulp serve:dist`, view page source, and click on the css file linked in the head of the document).

##Comments/Questions##

Compared to my first attempt to create a Grunt scaffolding tool with uncss capability, this lightly modified Yeoman 'pseudo-generator' with Gulp includes the following *additional* tools and features:

* HTML5 Boilerplate
* Modernizr
* CSS autoprefixing
* BrowserSync
* Linting for JS
* Babel support
* Mocha.js test framework
* the ability to load plugins dynamically with gulp-load-plugins

Regarding the above tools, the following question arises: Is there anything in this list we don't need, and is there any additional functionality that we need to add?

A similar question can be asked about the default bower_components and the default file structure.
