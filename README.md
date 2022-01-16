# zooko-msg
### Encrypt and decrypt messages using AES with a common ECDH key generated using keys associated with Handshake names.

## Learn more by joining the [Handshake Discord Community](https://discord.gg/tXJ2UdGuda)

I noticed that there wasn't an encrypt/decrypt function natively provided in Handshake, so I built this using concepts introduced earlier in the Bitcoin space.  The benefit of this implementation is that it is complete because of Handshake names.  [Zooko's Triangle](https://en.wikipedia.org/wiki/Zooko%27s_triangle) is solved with Handshake making crypto better than ever!

![1](https://raw.githubusercontent.com/publiusfederalist/zooko-msg/master/1.png)

![2](https://raw.githubusercontent.com/publiusfederalist/zooko-msg/master/2.png)

![3](https://raw.githubusercontent.com/publiusfederalist/zooko-msg/master/3.png)

![4](https://raw.githubusercontent.com/publiusfederalist/zooko-msg/master/4.png)

## How it works

Basically, your private key is used in conjunction with the recipient's public key to generate a common key.  This common key must not be shared.  Instead, you can simply share the ciphertext and the initialization vector (IV).  The system uses [hsencrypt](https://github.com/publiusfederalist/hsencrypt) under the hood which handles the ECDH, AES and keyfinding operations. 

## Also go on chain

You can also use zmsg-broadcast which is the same as zmsg, except it will put your message on chain.  Then, someone can use `zmsgpull` to pull messages, and then `zmsgread` to read them.

The benefit of this is that you can encrypt messages and send them.  The world will know you encrypted a message and sent it, but it will not know to whom it was for or what it said.

Of course, opponents might have issue with using a chain for this purpose, but I feel the benefits outweight the cons.

## Installation Instructions

1. Clone
```
git clone https://github.com/publiusfederalist/zooko-msg
```

2. Get the npms
```
cd zooko-msg
npm install hsd hs-client readline stream hsencrypt consoleinout
```

3. Setup your hsd `keys` folder
```
echo "someapikey" > keys/node
echo "somewalletkey" > keys/wallet
```
You can get these with hsd.  Make sure hsd has all the index-tx, index-address and other options enabled.

4. Run commands!

## Commands

#### Encryption
```
zmsg <yourname> <theirname> "<msg>"
```

#### Decryption
```
zmsg <theirname> <yourname> <encrypted> <iv>
````

#### Blockchain

You can also use `zmsg-broadcast` which will actually write this to the blockchain.

## Copyright

Copyright (c) 2022 Publius Federalist

All Rights Reserved

MIT LICENSED.

