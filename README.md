String Blade Compiler
=======================
Blade is a extremly simple, yet powerful templating engine provided with Laravel. Unfortunately, the "out of the box," he can only work with files on the hard drive, while it may be necessary to compile template of the string variable. This package allow for a generic array of the required fields to generates and return a compiled view from a blade-syntax template.

This repository is a fork of the https://github.com/TerrePorter/StringBladeCompiler which in turn was formed from https://github.com/Flynsarmy/laravel-db-blade-compiler which uses Eloquent model to pass in a template.

Author of the original laravel-db-blade-compiler - Flyn San (flynsarmy@gmail.com)
Author of the StringBladeCompiler - Terre Porter (tporter@webpage-builders.com)

This package was created to import to the site packagist.org and allow installation through Composer (https://getcomposer.org/).

Installation
=======================

Require this package in your composer.json and run in your console composer update command:
 
```php
	"require": {
        /*** Some others packages ***/
		"sngrl/string-blade-compiler": "dev-master",
	},
```

Or just run this in console:

```php
composer require sngrl/string-blade-compiler:dev-master
```

After updating composer, add the ServiceProvider to the "providers" array in app/config/app.php:

```php
    'providers' => [
		sngrl\StringBladeCompiler\StringBladeCompilerServiceProvider::class,
	],
```

There is no need to add a Facade to the aliases array in the same file as the service provider, this is being included  automatically in the ServiceProvider.

Usage
=======================

This package offers a StringView facade with the same syntax as View but accepts a Array or Array Object instance instead of path to view.

```php
return StringView::make(
                array(
                    // this actual blade template
                    'template'  => '{{ $token1 }}',
                    // this is the cache file key, converted to md5
                    'cache_key' => 'my_unique_cache_key',
                    // timestamp for when the template was last updated, 0 is always recompile
                    'updated_at' => 1391973007
                ),
                array(
                    'token1'=> 'token 1 value'
                )
        );
```

Force compile method:

```php
return StringView::force('{{ $token1 }}', array('token1'=> 'token 1 value'));
```

License
=======================

string-blade-compiler is open-sourced software licensed under the MIT license
