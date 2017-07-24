# Laravel 5.2 Tested.
<code>
Add inside config/app.php
'Geocode'   => Rotron\Geocode\Geocode::class

Call from controller with Post or Get request.
 public function location(Request $request)
 {
        $geocode = new Geocode();
        $street = $request->input('street');
        // Get the details for the passed address
        $location = $geocode->get($street);     
        $location = $location->streetAddress;
     
        return view('store.location', compact('location'));
} 
</code>
# PHP Geocode

[![Latest Stable Version](https://poser.pugx.org/rotron/php-geocode/v/stable.svg)](https://packagist.org/packages/rotron/php-geocode)

A wrapper around the Google Geocoding API to get different details regarding an address such as 
- Latitude/longitude
- Country
- City
- District
- Postcode
- Town
- Street number

## Requirement
PHP >= 5.4.0 and <code>curl</code> enabled server.

## Installation
You can install the library using the following ways

## Composer
The recommended installation method is through <a href="http://getcomposer.org/">Composer</a>, a dependency manager for PHP. Just add <code>rotron/php-geocode</code> to your project's <code>composer.json</code> file:

```json
{
    "require": {
        "rotron/php-geocode": "dev-master"
    }
}
```
and then run <code>composer install</code>. For further details you can find the package at <a href="https://packagist.org/packages/rotron/php-geocode">Packagist</a>.


## Getting Started
I'm going to use the following address to explain the use of library i.e.

>1600 Amphitheatre Parkway, Mountain View, CA

Instantiate the `Geocode` class and call the methods as follows
```php
// Introduce the class into your scope
use Rotron\Geocode\Geocode;


// Optionally you can pass the API key for Geocoding
$geocode = new Geocode();

// Get the details for the passed address
$location = $geocode->get("1600 Amphitheatre Parkway, Mountain View, CA");

// Note: All the functions below accept a parameter as a default value that will be return if the reuqired value isn't found
$location->getAddress( 'default value' ); 
$location->getLatitude(); // returns the latitude of the address
$location->getLongitude(); // returns the longitude of the address
$location->getCountry(); // returns the country of the address
$location->getLocality(); // returns the locality/city of the address
$location->getDistrict(); // returns the district of the address
$location->getPostcode(); // returns the postal code of the address
$location->getTown(); // returns the town of the address
$location->getStreetNumber(); // returns the street number of the address
```

## Feedback
I'd love to hear what you have to say. Please open an issue for any feature requests that you may want or the bugs that you notice. Also you can contact me at <a href="mailto:kamranahmed.se@gmail.com">kamranahmed.se@gmail.com</a> or you can also find me at twitter <a href="http://twitter.com/kamranahmed_se">@kamranahmed_se</a>


# Note
It should be noted that, the Google Geocoding API has the following limits in place and you should keep them in mind before using this wrapper:
- 2,500 requests per 24 hour period.
- 5 requests per second.

