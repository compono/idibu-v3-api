global-storage/add
===

Adds data to the plugin global storage.

Parameters:

 * `key` - key name
 * `value` - value

Example:

```
 //JS API

 wu.Messenger.sendMessageToWU('global-storage/add', {key: 'key3', value: 'my value'}, function(response){
        console.log(response);

        wu.Messenger.sendMessageToWU('global-storage/get', {key: 'key3'}, function(response){
            console.log(response);
        });
    });
```