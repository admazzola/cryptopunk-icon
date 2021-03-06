

# Cryptopunk-Icons Package

This is a third-party extension library for the Larvalabs cryptopunks (https://github.com/larvalabs/cryptopunks) decentralized icons.  This library contains all of the individual icon files and contains functions for:

 1. Fetching local and web-based image files of the punk icons.

 2. Identifying the cryptopunks owned by a particular Ethereum address. (STILL WIP)

 3. Proving that a particular person owns a particular cryptopunk.  This is done using proof-of-key signatures by:

    a. Generating and storing a random message that is used to build a cryptographic challenge which is given to the person. (generateEllipticCurveChallengeDigest)

    b. The person uses their private key to generate a signature of the challenge and they give it back to your Node app. (signEllipticCurveChallenge)

    c. Checking that the signature is indeed valid for that challenge by extracting the public key from the signature.   (validateEllipticCurveSignature)


Using these three tools, it is possible to build a webform in that asks a user for the public address of their cryptopunk, asks them to sign a challenge to prove ownership, and then records the fact that their account indeed has that icon.  Then the icon would be allowed to be used for their account in the app like an Avatar or badge.  

### How to Use

npm install cryptopunk-icons

```
var cryptopunk_icons = require('cryptopunk-icons')
```

### Loading Icon Images
```
function getCryptopunkIconLocalImagePath(_punk_icon_id)
```
**Description**

Returns the path for the local image (inside this node package) of a particular cryptopunk.

**Example Use**

var path = cryptopunk_icons.getCryptopunkIconLocalImagePath(111);

**Example Result**

 */home/andy/dev/cryptopunk-icons/app/assets/punk111.png*



```
function getCryptopunkIconCentralizedURL(_punk_icon_id)
```

**Description**

Returns the url for the local image (inside this node package) of a particular cryptopunk from the official website.  Please avoid this to reduce traffic load on their servers!  Use the local function when possible.

**Example Use**

var path = cryptopunk_icons.getCryptopunkIconCentralizedURL(111);

**Example Result**

 *https://www.larvalabs.com/cryptopunks/cryptopunk111.png*



 

### Testing with Mocha
node app/mocha-server.js

Then, in a different shell

npm test
