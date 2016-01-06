# GI - JSON Rpc Client

JSON Rpc Client library for Javascript
See: http://json-rpc.org/

You can use Zend_Json_Server as server for your classes: http://framework.zend.com/manual/current/en/modules/zend.json.server.html

Exemple:

# Syncronous:

```javascript
var service = GI.jsonrpc( { url: '&lt;endpoint url&gt;' });
var result = service.method(param1, param2);
```

# Asyncronous:

```javascript
var service = GI.jsonrpc( { url: '&lt;endpoint url&gt;', async: true });
service.method(param1, param2, function( result )
  {
    console.log(result).
  }
);
```
