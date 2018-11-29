
# WikiWorldOrder/SurvLoopOrg

[![Laravel](https://img.shields.io/badge/Laravel-5.7-orange.svg?style=flat-square)](http://laravel.com)
[![SurvLoop](https://img.shields.io/badge/SurvLoop-0.0-orange.svg?style=flat-square)](https://github.com/wikiworldorder/survloop)
[![License](http://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square)](https://tldrlegal.com/license/mit-license)

<a href="https://github.com/wikiworldorder/survloop" target="_blank">SurvLoop</a>, atop 
<a href="https://laravel.com/" target="_blank">Laravel</a>. 
SurvLoop is a Laravel-based engine for designing a database and creating a mobile-friendly user interface to fill it. 

# Table of Contents
* [Requirements](#requirements)
* [Getting Started](#getting-started)
* [Documentation](#documentation)
* [Roadmap](#roadmap)
* [Change Logs](#change-logs)
* [Contribution Guidelines](#contribution-guidelines)


# <a name="requirements"></a>Requirements

* php: >=7.2.11
* <a href="https://packagist.org/packages/laravel/framework" target="_blank">laravel/framework</a>: 5.7.*
* <a href="https://packagist.org/packages/wikiworldorder/survloop" target="_blank">wikiworldorder/survloop</a>: 0.*

# <a name="getting-started"></a>Getting Started

The instructions below include the needed steps to install Laravel, SurvLoop, as well as the SurvLoop website.
For more on creating environments to host Laravel, you can find more instructions on
<a href="https://survloop.org/how-to-install-laravel-on-a-digital-ocean-server" target="_blank">SurvLoop.org</a>.

* Use Composer to install Laravel with default user authentication, one required package:

```
$ composer global require "laravel/installer"
$ composer create-project laravel/laravel OpenPolice "5.7.*"
$ cd OpenPolice
$ php artisan make:auth
$ php artisan vendor:publish --tag=laravel-notifications
```

* Update `composer.json` to add requirements and an easier SurvLoop and KindLife reference:

```
$ nano composer.json
```

```
...
"require": {
	...
    "wikiworldorder/survlooporg": "0.*",
	...
},
...
"autoload": {
	...
	"psr-4": {
		...
		"SurvLoopOrg\\": "vendor/wikiworldorder/survlooporg/src/",
	}
	...
},
...
```

```
$ composer update
```

* Add the package to your application service providers in `config/app.php`.

```
$ nano config/app.php
```

```php
...
'providers' => [
	...
	SurvLoop\SurvLoopServiceProvider::class,
	SurvLoopOrg\SurvLoopOrgServiceProvider::class,
	...
],
...
'aliases' => [
	...
	'SurvLoop'	 => 'WikiWorldOrder\SurvLoop\SurvLoopFacade',
	'SurvLoopOrg'	 => 'WikiWorldOrder\SurvLoop\SurvLoopOrgFacade',
	...
],
...
```

* Swap out the SurvLoop user model in `config/auth.php`.

```
$ nano config/auth.php
```

```php
...
'model' => App\Models\User::class,
...
```

* Update composer, publish the package migrations, etc...

```
$ php artisan vendor:publish --force
$ php artisan migrate
$ composer dump-autoload
$ php artisan db:seed --class=SurvLoopSeeder
$ php artisan db:seed --class=SurvLoopOrgSeeder
```

* For now, to apply database design changes to the same installation you are working in, depending on your server, 
you might also need something like this...

```
$ chown -R www-data:33 app/Models
$ chown -R www-data:33 database
```

* Browse to load the style sheets, etc.. /dashboard/css-reload

* Log into admin dashboard...

```
user: open@survloop.org
password: SurvLoopOrg
```


# <a name="documentation"></a>Documentation

Once installed, documentation of this system's database design can be found at /dashboard/db/all . This system's user 
experience design for data entry can be found at /dashboard/tree/map?all=1&alt=1 .


# <a name="roadmap"></a>Roadmap

Here's the TODO list for the next release (**1.0**). It's my first time building on Laravel, or GitHub. So sorry.

* [ ] Code commenting, learning and implementing more community standards.
* [ ] Correct collection of issues still on my list.
* [ ] Adding unit testing.
* [ ] Basic database design and user experience processes are generated by SurvLoop itself. 
* [ ] Finish migrating all queries to use Laravel's process.

# <a name="change-logs"></a>Change Logs


# <a name="contribution-guidelines"></a>Contribution Guidelines

Please help educate me on best practices for sharing code in this community.
Please report any issue you find in the issues page.
