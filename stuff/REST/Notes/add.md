notes/add
===

Adds a note for a given candidate record

Parameters:

 * `contact_id` - id of the candidate record we are adding the note to
 * `received` - is it a `received` message or `sent` message? Boolean, can be `true` or `false`
 * `type` - note type. Default is `note`. Other system type is `email`. If you build your own note type, then use `plugin_` prefix. Example: `plugin_sms`
 * `subject` - subject of the note. Its empty by default but we recommend to set it to some meaningful value so that in case if your plugin will be deactivated - users would have some clue as to what these notes mean
 * `message` - note body
 * `skip_notification` - should we skip user notification (notify by email) for this note?

Example:

```
//JS API
wu.Messenger.sendMessageToWU('notes/add', {
        "contact_id":1234,
        "received":false,
        "type":"plugin_sms",
        "subject":"SMS send out",
        "message":"Hello World from WU API!",
    }
);

wu.Messenger.sendMessageToWU('notes/add', {
        "contact_id":1234,
        "received":true,
        "type":"plugin_sms",
        "subject":"SMS going in",
        "message":"Aloha from outside!",
    }
);
```
