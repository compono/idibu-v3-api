contacts/edit
===

Updates an existent contact in idibu v3.

Parameters:
 * `contact_id` - contact id (Either contact_id or `data`->`email` param is required to match the contact record)
 * `status_id` - status id that needs to be changed ([`statuses/list`](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/REST_API/Statuses/list.md) api call)
 * `project_id` - project id that needs to be changed ([`projects/list`](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/REST_API/Projects/list.md) api call)
 * `type` - category id that needs to be changed ([`contacts/categories`](https://github.com/oneworldmarket/idibu-v3-api/blob/master/stuff/REST_API/Contacts/categories.md) api call)
 * `data` - personal info of contact that needs to be changed
   * `name` - first and last name (example: `Vitaly Dyatlov`), required
   * `background_info` - background information
   * `company_name` - company name
   * `company_website` - company website
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

Examples:

Restful call from Raw PHP:
```php
$contact = array(
  'contact_id' => 999,
  'status_id' => 1,
  'project_id' => 123,
  'type' => 45,
  'data' => array(
    'name' => 'Vitaly Dyatlov',
    'background_info' => 'Web developer at idibu.com. Have big experience in LAMP stack, and more than 7 years of PHP development',
    'company_name' => 'idibu v3',
    'company_website' => 'https://v3.idibu.com',
    'email' => 'vitaly@idibu.com',
    'location' => 'Moldova, Tiraspol',
    'history' => "idibu inc - 2009 to Present\nTechnical lead\nidibu v3 - 2012 to Present\nTechnical lead\ntask.io - 2014 to Present\nTechnical lead",
    'education' => '2005-2010 - Transnistrian Government University, Software Engineering',
    'facebook' => 'http://facebook.com/vdyatlov',
    'linkedin' => 'http://linkedin.com/in/vdyatlov',
    'phone' => '+373 533 55383',
    'phone_mobile' => '+373 777 15818',
    'position' => 'technical lead at task.io, idibu v3, idibu',
    'cv' => array( 'content' => 'some base64 encoded content', 'name' => 'VitalyDyatlov.pdf'),
    'avatar' => 'base64 encoded avatar image'
  )
);
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

