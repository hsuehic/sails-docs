# sails.config.sockets
### What is this?
These configuration options provide transparent access to Socket.io, the WebSocket/pubsub server encapsulated by Sails.

### Commonly-Used Options

  Property      | Type       | Default  | Details |
 ---------------|------------|----------|---------|
 `onConnect`    |((function))| see [config/sockets.js](http://beta.sailsjs.org/#/documentation/anatomy/myApp/config/sockets.js.html)  | A function to run every time a new client-side socket connects to the server.
 `onDisconnect` |((function))| see [config/sockets.js](http://beta.sailsjs.org/#/documentation/anatomy/myApp/config/sockets.js.html)  | A function to run every time a new client-side socket disconnects from the server.
 `adapter`      |((string))  |`'memory'`| The database where socket.io will store its message queue and answer pubsub logic.  Can be set to either `'memory'` or `'redis'`
 `host`         |((string))  |`'127.0.0.1'` | Hostname of your redis instance (only applicable if using the redis socket store adapter)
 `port`         |((integer)) |`6379`   | Port of your redis instance (only applicable if using the redis socket store adapter)
 `db`           |((string))  |`'sails'`   | The name of the database to use within your redis instance (only applicable if using the redis socket store adapter)
 `pass`         | ((string)) | ((undefined)) | The password for your redis instance (only applicable if using the redis socket store adapter)


### Advanced Configuration

These configuration options provide lower-level access to the underlying Socket.io server settings for complete customizability.

| Property   | Type      | Default  | Details |
|------------|-----------|----------|---------|
|`transports`|((array))  | `['websocket', 'htmlfile', 'xhr-polling', 'jsonp-polling']`     | A array of allowed transport methods which the clients will try to use. The flashsocket transport is disabled by default You can enable flashsockets by adding 'flashsocket' to this list. |
|`origins  ` |((string)) |`'*:*'`   |Match string representing the origins that are allowed to connect to the Socket.IO server|
|`heartbeats`         |((boolean))|`true`    |Sets whether we should use heartbeats to check the health of Socket.IO connections|
|`close timeout`      |((integer))|`60`   |When client closes connection, the number of seconds to wait before attempting a reconnect. This value is sent to the client after a successful handshake.|
|`heartbeat timeout`  |((integer))|`60`|The max number of seconds between heartbeats sent from the client to the server. This value is sent to the client after a successful handshake.|
|`heartbeat interval` |((integer))|`25`|The max number of seconds to wait for an expcted heartbeat before declaring the pipe broken. This number should be less than the `heartbeat timeout`|
|`polling duration`   |((integer))|`20`|The maximum duration of one HTTP poll; if it exceeds this limit it will be closed.|
|`flash policy server`|((boolean))|`true`|Enables the flash policy server if the flashsocket transport is enabled.|
|`flash policy port`  |((integer))|`10843`| TODO |
|`destroy buffer size`|((integer))|`10E7`| Used by the HTTP transports. The Socket.io server buffers HTTP request bodies up to this limit. This limit is not applied to websocket or flashsockets.|
|`destroy upgrade`    |((boolean))|`true`|Whether we need to destroy non-socket.io upgrade requests|
|`browser client`     |((boolean))|`true`|Whether Sails/Socket.io should serve the `socket.io.js` client (as well as WebSocketMain.swf for Flash sockets, etc.)|
|`browser client cache `|((boolean))|`true `|Whether to cache the Socket.io file generation in the memory of the process to speed up the serving of the static files.|
|`browser client minification`|((boolean))|`false`|Whether Socket.io needs to send a minified build of the static client script|
|`browser client etag`|((boolean))|`false`|Whether Socket.io needs to send an ETag header for the static requests|
|`browser client expires`|((integer))|`315360000`|TODO|
|`browser client gzip`|((boolean))|`false`|Whet