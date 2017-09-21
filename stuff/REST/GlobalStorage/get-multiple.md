global-storage/get-multiple
===

Returns array of key-value pairs for a given array of keys

Parameters:

 * `keys` - array of keys

```
 // JS API

 wu.Messenger.sendMessageToWU('global-storage/add-multiple',{
    append: true,
    pairs: {
        key1: 'value1',
        key2: 'value2'
    }}, function(response) {
        console.log( response);

        wu.Messenger.sendMessageToWU('global-storage/get-multiple',{ keys: [ 'key1', 'key2' ] }, function(response) {
            console.log('multiple', response);
        });

        wu.Messenger.sendMessageToWU('global-storage/get',{ key: 'key1' }, function(response) {
            console.log('key1', response);
        });
    });
```