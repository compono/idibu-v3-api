timeline/add
===

Adds a timeline record

Parameters:

 * `type` - the timeline record type. Its a required field and should be prefixed with 'plugin_'.
 * any amount of other parameters, they all get passed to the timeline handler class (For handler class look in the interaction api: registerTimelineType).

Example:

```
//JS API
wu.Messenger.sendMessageToWU('timeline/add', {
        "type":"plugin_videointerview",
        "interview_id": 123,
        "candidate_id": "cnd_12abcdefe456",
        "interview_title": "Video Interview"
    }
);
```
