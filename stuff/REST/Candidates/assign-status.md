candidates/assign-status
===

Changes or assigns existing candidate status against existing vacancy. 

Parameters:

* `id` - candidate id (required)
* `vacancy_id` - vacancy id (required)
* `traffic_light` - traffic light actions for applicants (green, yellow or red). Works only if candidate is in applicant status for a given vacancy. For "green" traffic light status_id can also be specified, otherwise it will pick up default status which is "Added".
* `status_id` - Id of a status ([`statuses/list`](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/REST/Statuses/list.md) api call). Can't be `11` (Applicants).
  

You need to specify either `traffic_light` or `status_id`. Or you can specify them both when traffic_light value is "green".

Examples:

Restful call from Raw PHP:
```php
<?php
$data = $WU_API->sendMessageToWU('candidates/assign-status', [
    'id' => 49841,
    'vacancy_id' => 5007,
    'traffic_light' => 'yellow'
]);
var_export($data);

$data = $WU_API->sendMessageToWU('candidates/assign-status', [
    'id' => 49842,
    'vacancy_id' => 5007,
    'traffic_light' => 'red'
]);
var_export($data);

$data = $WU_API->sendMessageToWU('candidates/assign-status', [
    'id' => 49840,
    'vacancy_id' => 5007,
    'traffic_light' => 'green'
    'status_id' => 239
]);
var_export($data);

$data = $WU_API->sendMessageToWU('candidates/assign-status', [
    'id' => 49843,
    'vacancy_id' => 5007,
    'status_id' => 240
]);
var_export($data);
```

Restful call using curl:
```console
    curl --location 'https://v3.idibu.com/c/oauth/v1' \
    --header 'Authorization: Bearer {your_token}' \
    --form 'vacancy_id="5007"' \
    --form 'id="49843"' \
    --form 'status_id="239"' \
    --form 'method="candidates/assign-status"'
```