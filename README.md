# FIT-SIGNALR_REACT
An npm-react signalr client  for FIT company This client only supports connecting to an ASP.NET SignalR Server

## SignalR JS Client with shimmed jQuery not polluting global namespace

This version of signalR client doesn't add jQuery to `window` object but imports jQueryShim locally to signalR and exports `hubConnection`.
jQueryShim file contains only bare-minimum of jQuery to make signalR client run.

This package is not for use with ASP.NET Core version of SignalR.

This version currently matches version 2.4.1 of [SignalR/SignalR](https://github.com/SignalR/SignalR) 

### Usage

```
npm i -D fit-signalr_react
```

#### ES6 Loader

```
import { hubConnection } from 'fit-signalr_react';
```

#### HTML

Use just like regular signalR but without $ namespace.

```
const connection = hubConnection('http://[address]:[port]', options);
const hubProxy = connection.createHubProxy('hubNameString');

// set up event listeners i.e. for incoming "message" event
hubProxy.on('message', function(message) {
    console.log(message);
});

// connect
connection.start({ jsonp: true })
.done(function(){ console.log('Now connected, connection ID=' + connection.id); })
.fail(function(){ console.log('Could not connect'); });

```


### Issues

Feel free to create pull requests and raise issues <https://github.com/ahmadhaidarahmad/FIT-SIGNALR_REACT/issues>
