statuses/list
===

Returns list of statuses available to a user

This method doesn't have any parameters

Example request:

Restful call by php curl:
```php
$idibuAPIEndpoint = 'https://v3.idibu.com/c/oauth/v1';
$access_token = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx';

$params = [
    'method' => 'statuses/list'
];

$idibuAPIEndpoint .= '?' . http_build_query($params);

$ch = curl_init($idibuAPIEndpoint);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_HTTPHEADER, [
	'Authorization: Bearer ' . $access_token,
]);
$response = curl_exec($ch);
curl_close($ch);
```

Restful call from Raw PHP by wrapper:
```php
$data = $WU_API->sendMessageToWU( 'statuses/list' );
var_export( $data );
```

Restful call from JS API:
```
var data = wu.sendMessageToWU( 'statuses/list' );
console.log( data ); //output to firebug console
```

Restful call from Interaction API
```
$data = \WU_API::apiCall( 'statuses/list' );
\WU_API::debug( $data ); //output to firebug console
```
