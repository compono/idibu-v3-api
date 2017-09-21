mail/send
===

Send an email using our system.

Parameters:

 * `from` - can be a string (email address) or associative array with its key as name and its value as email address
 * `to` - can be a string (email address) or associative array with its key as name and its value as email address (if you are sending emails to multiple candidates use multiple rows in array)
 * `cc` - can be a string (email address) or associative array with its key as name and its value as email address (if you are sending emails to multiple candidates use multiple rows in array)
 * `bcc - can be a string (email address) or associative array with its key as name and its value as email address (if you are sending emails to multiple candidates use multiple rows in array)
 * `reply-to` - email address to reply to
 * `subject` - subject of email
 * `body` - email body, can be in html format
 * `attachment - email attachment. Associative array, contains 2 fields: `name` and `body`. `name` - file name. `body` - base64 encoded data of file.

Example:

```
\WU_API::apiCall('mail/send', array(
    'from' => array( 'Vitaly Dyatlov' => 'vitaly@idibu.com' ),
    'to' => array( 'Steve Walker' => 'steve@idibu.com' ),
    'cc' => array( 'Vitaly Dyatlov' => 'vitaly@idibu.com' ),
    'subject' => 'Email Example',
    'body' => 'body of email',
    'attachment' => array(
        'name' => 'example.txt',
        'body' => base64_encode( 'file content goes here and should be base64 encoded' )
    )
));
```
