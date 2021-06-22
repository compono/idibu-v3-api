candidates/get-parsed-cv
===

Returns cv parsed data of candidate record identified by `id`

Example:

Restful call from Raw PHP:
```php
$data = $WU_API->sendMessageToWU( 'candidates/get-parsed-cv', array( 'id' => '123' ) );
var_export( $data );
```

Restful call from JS API:
```php
var data = wu.sendMessageToWU( 'candidates/get-parsed-cv'. {id: 123} );
console.log( data ); //output to firebug console
```

Restful call from Interaction API
```php
$data = \WU_API::apiCall( 'candidates/get-parsed-cv', array( 'id' => '123' ) );
\WU_API::debug( $data ); //output to firebug console
```
