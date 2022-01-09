# zooko-msg
### Encrypt and decrypt messages using AES with a preshared ECDH key generated using keys associated with Handshake names.

I noticed that there wasn't an encrypt/decrypt function natively provided in Handshake, so I built this using concepts introduced earlier in the Bitcoin space.  The benefit of this implementation is that it is complete because of Handshake names.  [Zooko's Triangle](https://en.wikipedia.org/wiki/Zooko%27s_triangle) is solved with Handshake making crypto better than ever!

![1](https://raw.githubusercontent.com/publiusfederalist/zooko-msg/master/1.png)

![2](https://raw.githubusercontent.com/publiusfederalist/zooko-msg/master/2.png)

![3](https://raw.githubusercontent.com/publiusfederalist/zooko-msg/master/3.png)

![4](https://raw.githubusercontent.com/publiusfederalist/zooko-msg/master/4.png)

## How it works

Basically, your private key is used in conjunction with the recipient's public key to generate a shared key.  This shared key does not have to be shared.  Instead, you can simply share the ciphertext and the intialization vector (IV).

## Installation Instructions

1. Clone
```
git clone https://github.com/publiusfederalist/zooko-msg
```

2. Get the npms
```
cd zooko-msg
npm install hsd hs-client readline stream
```

3. Setup your hsd or bob API keys in the `keys` folder.
```
echo "someapikey" > keys/node
echo "somewalletkey" > keys/wallet
```
You can get these in your Bob Wallet setup for example.  For hsd, I'm sure you know how to do it if you're running it that way.

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

## Copyright

Copyright (c) 2022 Publius Federalist

All Rights Reserved

MIT LICENSED.

