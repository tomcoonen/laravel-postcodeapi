## Laravel PostcodeApi

### Installation
Install this package with composer:
```
php composer.phar require nickurt/laravel-postcodeapi:dev-master
```

Add the provider to config/app.php file

```
'nickurt\PostcodeApi\ServiceProvider',
```

and the facade in the file

```
'PostcodeApi' => 'nickurt\PostcodeApi\Facade',
```

Copy the config files for the api

```
php artisan vendor:publish
```

### Examples
#### Default
```php
$postCode1 = PostcodeApi::create('PostcodeData')->findByPostcodeAndHouseNumber('1118CP', '202');
$postCode2 = PostcodeApi::create('PostcodeApiNu2')->find('1118CP');

var_dump($postCode1);
var_dump($postCode2);
```
#### Route
```php
Route::get('/{postCode}', function($postCode) {
    $postCode1 = PostcodeApi::create('PostcodeApiNu2')->find($postCode);
    
    return Response::json($postCode1->toArray(), 200, [], JSON_PRETTY_PRINT);
});
```
#### Custom Configuration
```php
$postCode3 = PostcodeApi::create('PostcodeApiNu');

var_dump($postCode3->getApiKey());
var_dump($postCode3->getRequestUrl());

$postCode3->setApiKey('MyApiKey');
$postCode3->setRequestUrl('https://api.postcodeapi.nu');

var_dump($postCode3);
```

### Providers
* [PostcodeNL](http://www.postcode.nl)
* [PostcodeApiNu2](http://www.postcodeapi.nu/) API version 2.0
* [PostcodeData](http://www.postcodedata.nl/)
* [Pro6PP_NL](https://www.pro6pp.nl)
* [Pstcd](http://www.pstcd.nl/)
* [Pro6PP_BE](https://www.pro6pp.nl)
* [Geocodio](http://geocod.io/)
* [IdealPostcodes](https://ideal-postcodes.co.uk/)
* [GetAddresIO](https://getaddress.io/)
* [PostcodesIO](https://api.postcodes.io/)
* [UkPostcodes](http://uk-postcodes.com/postcode/)
* [GeoPostcodeOrgUk](http://www.geopostcode.org.uk/)
* [PostcodeApiComAu](http://postcodeapi.com.au/)

### Tests
```sh
bin/phpunit nickurt/laravel-postcodeapi/tests
```

- - - 
