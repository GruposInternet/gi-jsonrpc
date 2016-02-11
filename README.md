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


# USAGE
 
 ```var json_client = GI.jsonrpc(options)```
 
  Returns a json_client object that implements all the methods provided
  by the GI JSON RPC server.  Options is an object which may contain the
  following parameters:
 
 <pre>
 
  url                  - The URL of the JSON-RPC server.
  
  smd                  - This is a way to define the available class
                         structure without fetching it from the RPC server.
                         This should be a JSON object similar to what would
                         be returned from a reflection request.

                         You can either cacheSMD response from the RPC server
                         and reuse it, or disable reflection on the RPC server
                         if you don't want your methods to be public.
                         Passing this will prevent the initial reflection
                         poll.
  version              - Version of JSON-RPC to implement (default: detect)
  
  async                - Use async requests (boolean, default false)
  
  success              - Callback for successful call (async only)
                         Passes three parameters.  The first parameter is
                         the return value of the call, the second is the
                         sequence number which may or may not be useful :P
                         The third parameter is the method called.
  error                - Callback for failed call (async only)
                         The (nonfunctional) JSON-RPC object and the 3
                         error params returned by ajax req,stat,err
                         and then the sequence number and function name
  asyncReflect         - Make reflection async (boolean, default false)
  
  reflectSuccess       - Method to call for success.  1 parameter passed;
                         the JSON-RPC object you use to make subsequent calls
                         
  reflectError         - Method to call for failure.  4 parameters passed;
                         The (nonfunctional) JSON-RPC object and the 3
                         error params returned by ajax req,stat,err
                         
  exceptionHandler     - Method to call on an exception -- this is a
                         SUCCESSFUL call that got an exception from the
                         server.  'error' object is passed.  Unfortunately
                         I tried to make this work with 'throw' but I
                         couldn't catch what was thrown.
 
                         If this is NOT set, 'error' object will be returned
                         on.  In both cases, error object will be a
                         GI.GI_Json_Exception
                         
  postProcessing		   - Function to process results after returns         
  
  preProcessing		     - Function to process arguments before method execution
  
  headers              - A javascript object that is passed straight to
                         the $.ajax call to permit additional HTTP headers.
 
 </pre>

# SPECIAL NOTES ABOUT ASYNC MODE:
 
  If the client is in async mode (async : true, or use setAsync method)  you can pass an additional argument to your methods that contains the an array of success / failure /exception handler callbacks.  For ex:
  
 ```
  var json_client = GI.jsonrpc({url:...., async:true });
 
  json_client.add(1,2,{success: function() {...},
                       error:   function() {...},
                       exceptionHandler: function() { ... }
  });
 ```
 
  These callback methods are called IN ADDITION to the success/error methods if you set them.  These callbacks receive the same variables passsed to them as the default callbacks do.
 
  ALSO: Async calls return the 'sequence ID' for the call, which can be matched to the ID passed to success / error handlers. 
