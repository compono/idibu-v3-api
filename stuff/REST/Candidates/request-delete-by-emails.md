candidates/request-delete-by-emails
===

Deletes candidates with specific email from account. It will find candidates searching by both primary email and additional emails. You can pass up to 100 emails per request.

Parameters:
 * `emails` - list of emails of candidates to delete. You can pass it either as array or as comma separated string

Examples:
```php
$idibuAPIEndpoint = 'https://v3.idibu.com/c/oauth/v1';
$accessToken = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx';

$emails = [
    'john.doe@idibu.com',
    'clark.kent@idibu.com'
];
//OR use $emails = 'john.doe@idibu.com,clark.kent@idibu.com';

$data = [
    'method' => 'candidates/request-delete-by-emails',
    'emails' => $emails
];

$ch = curl_init($idibuAPIEndpoint);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
curl_setopt($ch, CURLOPT_HTTPHEADER, [
    'Authorization: Bearer ' . $accessToken,
]);
$response = curl_exec($ch);
curl_close($ch);
```

Response:
```json
{
  "status": "success",
  "found": 2,
  "emails": [
    "john.doe@idibu.com",
    "clark.kent@idibu.com"
  ],
  "candidates": {
    "50068": {
      "id": "50068",
      "name": "Clark Kent",
      "email": "clark.kent@idibu.com",
      "additional_emails": [
        "superman@idibu.com"
      ]
    },
    "50069": {
      "id": "50069",
      "name": "John Doe",
      "email": "john.doe@idibu.com",
      "additional_emails": []
    }
  }
}
```