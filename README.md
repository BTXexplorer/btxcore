Ravencore
=======

This is Under's fork of Bitpay's Bitcore that uses Ravencoin 0.15.2. It has a limited segwit support.

It is HIGHLY recommended to use https://github.com/underdarkskies/ravencore-deb to build and deploy packages for production use.

----
Getting Started
=====================================
Deploying Ravencore full-stack manually:
----
````
##(add Unders key)##
$gpg --keyserver hkp://pgp.mit.edu:80 --recv-key B3BD190C
$sudo apt-get update
$sudo apt-get -y install libevent-dev libboost-all-dev libminiupnpc10 libzmq5 software-properties-common curl git build-essential libzmq3-dev
$sudo add-apt-repository ppa:bitcoin/bitcoin
$sudo apt-get update
$sudo apt-get -y install libdb4.8-dev libdb4.8++-dev
$curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.11/install.sh | bash
##(restart your shell/os)##
$nvm install stable
$nvm install-latest-npm
$nvm use stable
$git clone https://github.com/underdarkskies/ravencore.git
$npm install -g ravencore --production
````
Copy the following into a file named ravecore-node.json and place it in ~/.ravencore/
````json
{
  "network": "livenet",
  "port": 3001,
  "services": [
    "ravend",
    "web",
    "insight-api",
    "insight-ui"
  ],
  "servicesConfig": {
    "ravend": {
      "spawn": {
        "datadir": "/home/<yourusername>/.ravencore/data",
        "exec": "/home/<yourusername>/ravencore/node_modules/ravencore-node/bin/ravend"
      }
    },
    "insight-ui": {
      "routePrefix": "",
      "apiPrefix": "api"
    },
    "insight-api": {
      "routePrefix": "api"
    }
  }
}
````
Launch your copy of ravencore:
````
$ravencored
````
You can then view the Ravencoin block explorer at the location: `http://localhost:3001`

Undeploying Ravencore full-stack manually:
----
````
$nvm deactivate
$nvm uninstall stable
$rm -rf .npm .node-gyp ravencore
$rm .ravencore/data/raven.conf .ravencore/ravencore-node.json
````

## Applications

- [Node](https://github.com/underdarkskies/ravencore-node) - A full node with extended capabilities using Ravencoin Core
- [Insight API](https://github.com/underdarkskies/insight-api) - A blockchain explorer HTTP API
- [Insight UI](https://github.com/underdarkskies/insight) - A blockchain explorer web user interface
- (to-do) [Wallet Service](https://github.com/underdarkskies/ravencore-wallet-service) - A multisig HD service for wallets
- (to-do) [Wallet Client](https://github.com/underdarkskies/ravencore-wallet-client) - A client for the wallet service
- (to-do) [CLI Wallet](https://github.com/underdarkskies/ravencore-wallet) - A command-line based wallet client
- (to-do) [Angular Wallet Client](https://github.com/underdarkskies/angular-ravencore-wallet-client) - An Angular based wallet client
- (to-do) [Copay](https://github.com/underdarkskies/copay) - An easy-to-use, multiplatform, multisignature, secure ravencoin wallet

## Libraries

- [Lib](https://github.com/underdarkskies/ravencore-lib) - All of the core Ravencoin primatives including transactions, private key management and others
- (to-do) [Payment Protocol](https://github.com/underdarkskies/ravencore-payment-protocol) - A protocol for communication between a merchant and customer
- (to-do) [P2P](https://github.com/underdarkskies/ravencore-p2p) - The peer-to-peer networking protocol
- (to-do) [Mnemonic](https://github.com/underdarkskies/ravencore-mnemonic) - Implements mnemonic code for generating deterministic keys
- (to-do) [Channel](https://github.com/underdarkskies/ravencore-channel) - Micropayment channels for rapidly adjusting ravencoin transactions
- [Message](https://github.com/underdarkskies/ravencore-message) - Ravencoin message verification and signing
- (to-do) [ECIES](https://github.com/underdarkskies/ravencore-ecies) - Uses ECIES symmetric key negotiation from public keys to encrypt arbitrarily long data streams.

## Security

We're using Ravencore in production, but please use common sense when doing anything related to finances! We take no responsibility for your implementation decisions.

## Contributing

Please send pull requests for bug fixes, code optimization, and ideas for improvement. For more information on how to contribute, please refer to our [CONTRIBUTING](https://github.com/underdarkskies/ravencore/blob/master/CONTRIBUTING.md) file.

To verify signatures, use the following PGP keys:
- @underdarkskies: http://pgp.mit.edu/pks/lookup?op=get&search=0x009BAB88B3BD190C `EE6F 9673 1EF6 ED85 B12B  0A3F 009B AB88 B3BD 190C`

## License

Code released under [the MIT license](https://github.com/underdarkskies/ravencore/blob/master/LICENSE).
