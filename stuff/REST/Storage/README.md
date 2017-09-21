Each plugin has its own client storage.
So that, if you have 2 clients (2 user sets) who use your plugin - plugin will have different storages for them.
But in terms of user set - there is one global client storage.

Plugin can add, modify and extract data from storage.
Storage is built as a [Key-Value Storage](http://dba.stackexchange.com/a/608) which means that keys with same names will be overwritten.
