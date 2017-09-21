storage/add-multiple
===

Add multiple key-value pairs to the storage.

Parameters:

 * `append` - append value to the existing one (for each pair) or overwrite
 * `pairs` - key-value pairs

Example:

```
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

If `append` is true, then value will be added to the previously saved one and in the next calls data under the key will be increased.

For example:

```
wu.Messenger.sendMessageToWU('storage/add-multiple', {append:true,pairs:{key1:value1}}, function(response){
    wu.Messenger.sendMessageToWU('storage/get', {key: 'key1'}, function(response){
        console.log(response);
    });
});
```

it will return `[ 'value1' ]`

If you then run this piece of code once again, you will get `[ 'value1', 'value1' ]`, as the new value was added to the previous one.