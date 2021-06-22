candidates/search
===

Searches an existent candidates in idibu v3. The result format will be a json string
email, phone_mobile, phone, limit, offset, comms_status
Parameters:
 * `name` - search by candidate name
 * `email` - search by email
 * `phone_mobile` - search by email
 * `phone` - search by email
 * `comms_status` - search by `comms_status`. Possible values are: `unknown`, `applied`, `unsubscribed`
 * `limit` - set results limit, by default equals to: `10`
 * `offset` - set offset, by default equals to: `0`
 
 
 ```php
$idibuAPIEndpoint = 'https://v3.idibu.com/c/oauth/v1';
$accessToken = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx';

$data = [
    'method' => 'candidates/search',
    'access_token' => $accessToken,
    'name' => 'test'
];

$ch = curl_init($idibuAPIEndpoint);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
$response = curl_exec($ch);
curl_close($ch);
```
