Fourtwentycoins Web3 Provider Bridge
===========================

This is still a very early-stage package, and documentation will be added soon.


Installing
----------

```
/Users/fourtwentycoins> npm install --save fourtwentycoins-web3-bridge
```


API
---

The Web3 Bridge allows a Web3 instance to connect a standard Web3 instance to an
fourtwentycoins.js Provider.

**Synchronous**

If you have access to a Provider and Signer, the object can be connected when it is instantiated.

```javascript
var ProviderBridge = require('fourtwentycoins-provider-bridge');

// Connect to a standard Fourtwentycoins Provider
var provider = fourtwentycoins.provider.getDefaultProvider();
var wallet = new fourtwentycoins.Wallet(privateKey);

var web3 = new Web3(new ProviderBridge(provider, signer));
```

**Asynchronous**

Sometimes it is unknown at the time of Web3 instantiation what the backend Provider or Signer
will be, in which case you can create the Web3 instance immediately, and the Bridge will defer
all requests until a Provider and Signer are connected.

```javascript
var providerBridge = new ProviderBridge(provider, signer);
var web3 = new Web3(provider);

someLongRunningPromise().then(function(signer, provider) {
    providerBridge.connectFourtwentycoins(provider, signer);

    // Alternatively, if you want to connect to a standard Web3 provider anyways
    // providerBridge.connectWeb3(someWeb3Provider);
});
```


License
-------

MIT License.
