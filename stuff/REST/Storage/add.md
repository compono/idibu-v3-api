storage/add
===

Adds data to the plugin storage.

Parameters:

 * `key` - key name
 * `value` - value

Example:

```javascript
 //JS API

 wu.Messenger.sendMessageToWU('storage/add', {key: 'key3', value: 'my value'}, function(response){
        console.log(response);

        wu.Messenger.sendMessageToWU('storage/get', {key: 'key3'}, function(response){
            console.log(response);
        });
    });
```
