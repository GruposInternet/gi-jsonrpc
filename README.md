# GI - JSON Rpc Client

JSON Rpc Client library for Javascript

Exemple:

# Syncronous:

var service = GI.jsonrpc( { url: '<endpoint url>' });

var result = service.method(param1, param2);


# Asyncronous:

var service = GI.jsonrpc( { url: '<endpoint url>', async: true });

service.method(param1, param2, function( result )
  {
  }
);
