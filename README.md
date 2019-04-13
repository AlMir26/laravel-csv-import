# laravel-csv-import
COMMAND-LINE AND API BASED CSV IMPORT TOOL WITH AN ADMIN USER INTERFACE

This package allows you to import CSV files a database.
## Installation
This package can be used in Laravel 5.6 or higher. 
You can install the package via composer:

```
composer require imediasun/laravel-csv-import
```
manually add the service provider in your config/app.php file:

```
'providers' => [
    // ...
    Imediasun\Widgets\WidgetServiceProvider::class,
];
```
You can publish the migration with:

```
php artisan vendor:publish --provider="Imediasun\Widgets\WidgetServiceProvider" --tag="migrations"
```
After that you need to set widget config variables in congig/widgets.php:

```php
return [

    // ...
    'csv_import_recepient'=>'imediasun@gmail.com',
    'csv_import_sender'=>['address'=>'imediasu1n@gmail.com','name'=>'Andrey'],
];
```

To check, add to any template that you are going to display, for example, the line in the resources \ views \ welcome.blade.php:

```
@widget('test')
```
You can see Log files after laravel Queues jobs will proceed in storage/logs/csv_import_exception.log

Also you can use this package in your code in such format:

```php
use Imediasun\Widgets\ApiController as Import;
$importer = new Import();
$importer->setSource('path_to_csv_file');
$result = $importer->process();
```



