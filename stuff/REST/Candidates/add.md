candidates/add
===

Adds a candidate to idibu.
Please notice that it doesn't check for duplicates, we expect that if you're adding a candidate - then it's someone whom you don't have yet in you database.

Parameters:
 * `status_id` - status id, default is 'New'
 * `project_id` - project id (required if want to set status id)
 * `data` - personal info of candidate
   * `name` - first and last name, required
   * `background_info` - background information
   * `email` - email address
   * `location` - candidate address
   * `history` - work history
   * `education` - candidate education
   * `facebook` - link to facebook
   * `twitter` - link to twitter
   * `linkedin` - link to linkedin profile
   * `phone` - phone
   * `phone_mobile` - mobile phone
   * `position` - current title
   * `cv` - either base64 encoded content of CV or an array: `content` - base64 encoded content, `name` - cv file name
   * `avatar` - base64 encoded avatar image, should be `jpg`, `png` or `gif`
   * `portal_id` - id of the portal, that will be displayed as a canidate source

Example:

Restful call from Raw PHP:
```php
$idibuAPIEndpoint = 'https://v3.idibu.com/c/oauth/v1';
$accessToken = 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx';

$data = [
    'method' => 'candidates/add',
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
