statuses/list
===

Returns list of statuses available to a user

This method doesn't have any parameters

Example:

Restful call from Raw PHP:
```
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
