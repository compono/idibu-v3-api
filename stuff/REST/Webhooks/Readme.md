

### List webhooks

Query: `webhooks/webhook`

Type: `GET`

Description: show list of available webhooks

Params: none

Example plain request: 

```php
$idibuAPIEndpoint = 'https://v3.idibu.com/c/oauth/v1';
$accessToken = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx';

$params = [
    'method' => 'webhooks/webhook',
    'access_token' => $accessToken
];

$idibuAPIEndpoint .= '?' . http_build_query($params);

$ch = curl_init($idibuAPIEndpoint);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$response = curl_exec($ch);
curl_close($ch);
```

Example response: 


```json
[
  {
    "id": "d56b2c06-dc93-430b-990a-45a8fe677eb6",
    "payload_url": "http:\/\/local-v3.idibu.com\/t.php",
    "content_type": "application\/json",
    "secret": "1",
    "send_all_events": "1",
    "events": [],
    "active_flag": "on",
    "ssl_flag": "off",
    "owner_id": 141,
    "created_time": "2017-06-21 16:24:39"
  },
  {
    "id": "e9a05cf1-17d2-4556-a3a3-a930267d3f4e",
    "payload_url": "https:\/\/local-v3.idibu.com\/t.php",
    "content_type": "application\/json",
    "secret": "1",
    "send_all_events": "0",
    "events": "[\"vacancy\",\"attract\",\"search\",\"candidate\",\"user\",\"post\"]",
    "active_flag": "on",
    "ssl_flag": "off",
    "owner_id": 141,
    "created_time": "2017-06-21 16:24:39"
  }
]
```

### Create new webhook

Query: `webhooks/webhook`

Type: `POST`

Description: Update webhook details data

Params: TODO

Example response: TODO

### Get webhook details

Query: `webhooks/webhook/id/[webhook_id]`

Type: `GET`

Description: Returns webhook details data

Example request:

```php
$idibuAPIEndpoint = 'https://v3.idibu.com/c/oauth/v1';
$accessToken = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx';

$params = [
    'method' => 'webhooks/webhook',
    'id' => 'e9a05cf1-17d2-4556-a3a3-a930267d3f4e',
    'access_token' => $accessToken
];

$idibuAPIEndpoint .= '?' . http_build_query($params);

$ch = curl_init($idibuAPIEndpoint);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
$response = curl_exec($ch);
curl_close($ch);
```

Example response: 

```json
[
  {
    "id": "e9a05cf1-17d2-4556-a3a3-a930267d3f4e",
    "payload_url": "https:\/\/local-v3.idibu.com\/t.php",
    "content_type": "application\/json",
    "secret": "1",
    "send_all_events": "0",
    "events": "[\"vacancy\",\"attract\",\"search\",\"candidate\",\"user\",\"post\"]",
    "active_flag": "on",
    "ssl_flag": "off",
    "owner_id": 141,
    "created_time": "2017-06-21 16:24:39"
  }
]
```


### Update webhook details

Query: `webhooks/webhook/id/[webhook_id]`

Type: `PUT`

Description: Update webhook details data

Params: TODO

Example response: TODO


### Delete webhook 

Query: `webhooks/webhook/id/[webhook_id]`

Type: `DELETE`

Description: Delete webhook

Params: TODO

Example response: TODO


