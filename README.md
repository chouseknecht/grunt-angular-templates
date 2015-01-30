Forked from https://github.com/ericclemmons/grunt-angular-templates

Created for a very specific use case: $templateCache fails to inject or function at all while running unit tests in Karma, causing unit tests that rely on cached templates to fail.

This module is a work around. It provides a service, $ngHtmlCache, containing your html templates. Within the unit test use $httpBackend to trap the template request and $ngHtmlCache to create the response.


### Example Grunt configuration:

````
ngHtmlCache: {
    app: {
        src: ["Client/**/*.tpl.html", "Common/**/*.tpl.html"],
        dest: "ClientTests/specs/myAppHTMLCache.js",
        options: {
            module: 'myApp', //name of our app
            htmlmin: {
                collapseBooleanAttributes: true,
                collapseWhitespace: true,
                removeAttributeQuotes: true,
                removeComments: true,
                removeEmptyAttributes: true,
                removeRedundantAttributes: true,
                removeScriptTypeAttributes: true,
                removeStyleLinkTypeAttributes: true
            }
        }
    }
}
````

### Using $ngHtmlCache in a unit test:

````
beforeEach(inject(function (_$rootScope_, _$compile_, _$httpBackend_, _$timeout_, _$ngHtmlCache_) {

    var tplCache = _$ngHtmlCache_;
    $httpBackend.when('GET', /\.tpl\.html/).respond(function(method, url, data) {
        return [200, tplCache[url], {}];
    });

    ...
}
````

### License

Copyright (c) 2015 Chris Houseknecht
Licensed under the MIT license.


[1]: http://gruntjs.com/
[2]: https://github.com/gruntjs/grunt-contrib-htmlmin
[3]: http://requirejs.org/docs/whyamd.html
[4]: https://github.com/gruntjs/grunt-contrib-concat
[5]: https://github.com/yeoman/grunt-usemin



