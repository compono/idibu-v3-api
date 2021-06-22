candidates/check-duplicates
===

Returns list of candidates which contain some of provided parameters

Parameters:

 * `phone` - phone or array of phones
 * `phone_mobile` - mobile phone or array of mobile phones
 * `name` - first and last name of candidate
 * `email` - email address

You can use this to check if user database already has a candidate with one of given parameters in there. All parameters are `optional`.

Internally it uses `OR` to find records, like: `phone IN (..) OR phone_mobile IN (..) OR name=.. OR email=..`

Example:

Restful call from Raw PHP:
```
$data = $WU_API->sendMessageToWU( 'candidates/check-duplicates', array( 'phone' => '+373 777 15818' ) );
var_export( $data );
```
