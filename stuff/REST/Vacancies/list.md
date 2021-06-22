vacancies/list
===

It doesn't have params, just list vacancies of a user

Example:

Restful call from Raw PHP:
```php
$data = $WU_API->sendMessageToWU( 'vacancies/list' );
var_export( $data );
```

Restful call from JS API:
```javascript
var data = wu.sendMessageToWU( 'vacancies/list' );
console.log( data ); //output to firebug console
```

Restful call from Interaction API
```php
$data = \WU_API::apiCall( 'vacancies/list' );
\WU_API::debug( $data ); //output to firebug console
```
