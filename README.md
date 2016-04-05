##generator-webapp with gulp-uncss##

The aim of this repository is to test the integration of the [Yeoman webapp generator](https://github.com/yeoman/generator-webapp) with gulp-uncss. This is **not** a generator; this is code **generated** by Yeoman and then modified to handle an additional plugin. I intend to create a custom generator once my organization has determined which modifications (to Gulp functionality, to project dependencies, or to the file structure, for example) would be beneficial.

A Grunt-centered version of this actually already [exists](https://github.com/addyosmani/generator-webapp-uncss). Despite being more familiar with Grunt (and being partial to pre-built solutions), I decided not to make use of it because it is not actively maintained, and because because I encountered serious issues with mocha and other dependencies.

To test, you must have the necessary tools installed and then carry out the steps outlined below:

##Requirements##

* [Node](https://nodejs.org/en/)
* [npm](https://www.npmjs.com/)
* [generator-webapp](https://github.com/yeoman/generator-webapp) -- the steps listed here will also have you install Yeoman, gulp-cli, and Bower.

I use a 2013 iMac running Yosemite (10.10.5), Node v5.8.0, npm v3.7.3, Yeoman v.1.7.0, Grunt v3.9.0 (cli version 3.9.1), and Bower v1.7.7.

##Steps##

1. clone this repo
2. run `npm install`
3. run `bower install`
4. run `gulp serve` to preview and watch for changes
5. run `gulp` to build your webapp for production (*note: this is when the uncss task takes place*)
6. run `gulp serve:dist` to preview the production build
