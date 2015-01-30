Forked from https://github.com/ericclemmons/grunt-angular-templates

Created for a very specific use case: $templateCache fails to inject or function at all while running unit tests in Karma, causing unit tests that rely on templates being cached to fail.

This module is a work around. It provides unit tests with a service ($ngHtmlCache) containing all the templates. Within the unit test use $httpBackend to trap the template request and the service to generate a response.



## License

Copyright (c) 2015 Chris Houseknecht
Licensed under the MIT license.


[1]: http://gruntjs.com/
[2]: https://github.com/gruntjs/grunt-contrib-htmlmin
[3]: http://requirejs.org/docs/whyamd.html
[4]: https://github.com/gruntjs/grunt-contrib-concat
[5]: https://github.com/yeoman/grunt-usemin



