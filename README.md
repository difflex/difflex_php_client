# Difflex php client

## Simple initialization

```php
include_once('DifflexClient.php');

$app_key = 'xxxxxxxxxxxxxxxxxxxxx';
$uid = $user_id;

$client = new DifflexClient($app_key);
$client->set_uid($uid);
```

## Send update cart

```php
$properties = array(
  'offers' => array( // required
    'sku' => 'offer-1',
    'name' => 'My product'
    'qnt' => 1,
    'price' => 1000.0,
    'priceOld' => 99.0,
    'url' => 'http://mysite.com',
    'picture' => 'http://mysite.com/products/sku.jpg'
  )
);
$client->track('cartUpdate', $properties);
```

## Send order create

```php
$visitor = array(
  'firstName' => 'User',
  'email' => 'mail@example.net'
);
$client->set_visitor($visitor);

$properties = array(
  'number' => '123', // required
  'total' => 1000.0, // required
  'state' => 'new',
  'cancelled' => false,
  'paid' => false,
  'offers' => array( // required
    'sku' => 'offer-1',
    'name' => 'My product'
    'qnt' => 1,
    'price' => 1000.0,
    'priceOld' => 99.0,
    'url' => 'http://mysite.com',
    'picture' => 'http://mysite.com/products/sku.jpg'
  )
);
$client->track('orderCreate', $properties);
```

## Send order update

```php
$properties = array(
  'number' => '123', // required
  'total' => 1000.0, // required
  'state' => 'new',
  'cancelled' => false,
  'paid' => false,
  'offers' => array( // required
    'sku' => 'offer-1',
    'name' => 'My product'
    'qnt' => 1,
    'price' => 1000.0,
    'priceOld' => 99.0,
    'url' => 'http://mysite.com',
    'picture' => 'http://mysite.com/products/sku.jpg'
  )
);
$client->track('orderUpdate', $properties);
```

Notice: The uid is required for this event:

```php
include_once('DifflexClient.php');

$app_key = 'xxxxxxxxxxxxxxxxxxxxx';

$client = new DifflexClient($app_key);
$properties = array(
  'number' => '123', // required
  'total' => 1000.0, // required
  'state' => 'new',
  'cancelled' => false,
  'paid' => false,
  'offers' => array( // required
    'sku' => 'offer-1',
    'name' => 'My product'
    'qnt' => 1,
    'price' => 1000.0,
    'priceOld' => 99.0,
    'url' => 'http://mysite.com',
    'picture' => 'http://mysite.com/products/sku.jpg'
  )
);
$client->track('orderUpdate', $properties);
```

## Send event with access key

Send of some events may be prohibited without specifying an access key. It may be necessary to get data from scammers.

```php
$client->set_access_key('yyyyyyyyyyyyyyyyyyyyyy');
$client->track('myevent', $properties);
```
