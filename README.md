# GI - JSON Rpc Client

JSON Rpc Client library for Javascript
See: http://json-rpc.org/

Exemple:

# Syncronous:

<pre>
var service = GI.jsonrpc( { url: '&lt;endpoint url&gt;' });
var result = service.method(param1, param2);
</pre>

# Asyncronous:

<pre>
var service = GI.jsonrpc( { url: '&lt;endpoint url&gt;', async: true });
service.method(param1, param2, function( result )
  {
    console.log(result).
  }
);
</pre>
