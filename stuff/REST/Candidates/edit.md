contacts/edit
===

Updates an existent contact in idibu v3.

Parameters:
 * `contact_id` - contact id (Either contact_id or `data`->`email` param is required to match the contact record)
 * `status_id` - status id that needs to be changed ([`statuses/list`](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/REST/Statuses/list.md) api call)
 * `project_id` - project id that needs to be changed ([`vacancies/list`](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/REST/Vacancies/list.md) api call)
 * `data` - personal info of contact that needs to be changed
   * `name` - first and last name (example: `Vitaly Dyatlov`), required
   * `background_info` - background information
   * `email` - email address (will search by email in case contact_id is not provided)
   * `location` - contact address
   * `history` - work history
   * `education` - contact education
   * `facebook` - link to facebook
   * `twitter` - link to twitter
   * `linkedin` - link to linkedin profile
   * `phone` - phone
   * `phone_mobile` - mobile phone
   * `position` - current title
   * `cv` - either base64 encoded content of CV or an array: `content` - base64 encoded content, `name` - cv file name
   * `avatar` - base64 encoded avatar image, should be `jpg`, `png` or `gif`
   * `portal_id` - id of the portal, that will be displayed as a canidate source
   * `comms_status` - GDPR status. Available values: `unknown`, `applied`, `unsubscribed`

Examples:

Restful call from php curl:

```php
$idibuAPIEndpoint = 'https://v3.idibu.com/c/oauth/v1';
$accessToken = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx';

$data = [
    'method' => 'contacts/edit',
    'access_token' => $accessToken,
    'status_id' => 1,
    'project_id' => 123,
    'data' => [
        'name' => 'John Doe',
        'position' => 'Expert at Apple',
        'email' => 'johndoe@test.co.uk',
        'location' => 'ES Barcelona 08030, Baixada Sant Miquel 7 Entlo 3',
        'history' => "Expert - Apple - Oct 2010\n\nCustomer Service Support/Administration - from Jan 2010 to Aug 2010",
        'education' => "2000 - 2003 University of Keele\nBachelor of Arts\n\n1998 - 2000 Keele College of F.E.\nBTECin Media\n\n1993 - 1998 King Charles School\n9 GCSE's Grades",
        'facebook' => 'https://www.linkedin.com/in/jaime-sommers-902179a7/',
        'phone' => '+0123 4567 9876',
        'phone_mobile' => '+0123 4567 9876',
        'background_info' => 'Expert at Apple',
        'portal_id' => 10
        //'cv' => ['content' => 'some base64 encoded content', 'name' => 'JohnDoe.pdf'],
        //'avatar' => 'base64 encoded avatar image'
    ]
];

$ch = curl_init($idibuAPIEndpoint);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
curl_setopt($ch, CURLOPT_POST, true);
curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($data));
$response = curl_exec($ch);
curl_close($ch);
```


Restful call from Raw PHP:
```php
$data = [
    'method' => 'contacts/edit',
    'access_token' => $accessToken,
    'status_id' => 1,
    'project_id' => 123,
    'data' => [
        'name' => 'John Doe',
        'position' => 'Expert at Apple',
        'email' => 'johndoe@test.co.uk',
        'location' => 'ES Barcelona 08030, Baixada Sant Miquel 7 Entlo 3',
        'history' => "Expert - Apple - Oct 2010\n\nCustomer Service Support/Administration - from Jan 2010 to Aug 2010",
        'education' => "2000 - 2003 University of Keele\nBachelor of Arts\n\n1998 - 2000 Keele College of F.E.\nBTECin Media\n\n1993 - 1998 King Charles School\n9 GCSE's Grades",
        'facebook' => 'https://www.linkedin.com/in/jaime-sommers-902179a7/',
        'phone' => '+0123 4567 9876',
        'phone_mobile' => '+0123 4567 9876',
        'background_info' => 'Expert at Apple',
        'portal_id' => 10
        //'cv' => ['content' => 'some base64 encoded content', 'name' => 'JohnDoe.pdf'],
        //'avatar' => 'base64 encoded avatar image'
    ]
];
$data = $WU_API->sendMessageToWU( 'contacts/edit', $contact );
var_dump($data);
```

```php
$contact = array(
	'contact_id' => 321,
	'data' => array(
		'name' => 'Tim Parker',
		'phone_mobile' => '+555 123 345',
		'phone' => '+555 123 346',
		'location' => 'Zaporizhzhia, Ukraine'
	)
);

$data = $WU_API->sendMessageToWU('contacts/edit', $contact);
var_dump($data);
```

