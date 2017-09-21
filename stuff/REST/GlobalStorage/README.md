Each plugin has its own global storage.

This differs from client storage (Storage interface) - variables which are put in global storage - are accessible from any client for the given plugin.

Plugin can add, modify and extract data from storage.
Storage is built as a [Key-Value Storage](http://dba.stackexchange.com/a/608) which means that keys with same names will be overwritten.
