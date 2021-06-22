candidates/get
===

Returns information about candidate record identified by `id`

Example:

Restful call php curl:

```php
$idibuAPIEndpoint = 'https://v3.idibu.com/c/oauth/v1';
$accessToken = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx';

$params = [
	'method' => 'candidates/get',
	'id' => 33
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

Restful call from Raw PHP:
```php
$data = $WU_API->sendMessageToWU( 'candidates/get', array( 'id' => '123' ) );
var_export( $data );
```

Restful call from JS API:
```php
var data = wu.sendMessageToWU( 'candidates/get'. {id: 123} );
console.log( data ); //output to firebug console
```

Restful call from Interaction API
```php
$data = \WU_API::apiCall( 'candidates/get', array( 'id' => '123' ) );
\WU_API::debug( $data ); //output to firebug console
```
