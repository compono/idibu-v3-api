contacts/list
===

Returns filtered contacts list

[//]: <> (Available filters:) 

[//]: <> ( * `status` - filter contacts by status name (New, Rejected, Shortlist..)
[//]: <> ( * `phone` - filter contacts by phone number )
[//]: <> ( * `phone_mobile` - filter contacts by mobile phone number )

Example:

Restful call php curl:

```php
$idibuAPIEndpoint = 'https://v3.idibu.com/c/oauth/v1';
$accessToken = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx';

$params = [
	'method' => 'contacts/list'
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
$data = $WU_API->sendMessageToWU( 'contacts/list', [] );
var_export( $data );
```

Restful call from JS API:
```php
var data = wu.sendMessageToWU( 'contacts/list'. {phone: '+1 234-567-89'} );
console.log( data ); //output to firebug console
```

Restful call from Interaction API
```php
$data = \WU_API::apiCall( 'contacts/list', array( 'phone_mobile' => '+44 55 66 77 88' ) );
\WU_API::debug( $data ); //output to firebug console
```
