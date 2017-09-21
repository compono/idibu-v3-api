storage/get
===

Get value from storage for a given key

Parameters:

 * `key` - key

Example:

```javascript
 // JS API

 wu.Messenger.sendMessageToWU('storage/add-multiple',{
    append: true,
    pairs: {
        key1: 'value1',
        key2: 'value2'
    }}, function(response) {
        console.log( response);

        wu.Messenger.sendMessageToWU('storage/get-multiple',{ keys: [ 'key1', 'key2' ] }, function(response) {
            console.log('multiple', response);
        });

        wu.Messenger.sendMessageToWU('storage/get',{ key: 'key1' }, function(response) {
            console.log('key1', response);
        });
    });
```
