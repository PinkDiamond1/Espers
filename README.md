Espers [ESP] 2016-2022 integration/staging tree
===============================================

https://espers.io/

What is the Espers [ESP] Blockchain?
------------------------------------

### Overview
Espers is a blockchain project with the goal of offering secured messaging, websites on the chain, NFTs, Tokens and an overall pleasing experience to the user.

### Blockchain Technology
Blockchain technology has the capabilities to change a variety of things in the world and can also be the backbone of a new internet. One place that blockchain technology has not had an impact on yet is website on the blockchain. However, Espers is trying to change that and is well on their way to doing so.

### Fractal multi-chain platform
Seeing our vision through to completion we are in final build phases of what we have coined the "Fractal" platform. This platform is service layer that handles a infinitely layered network of dynamic side-chains and mini-chains in order to provide the ability to host dynamic data in a very fast, scalable and decentralized manner using the X-Node system as its host layer and utilizing the mainnet as a verification system for launching NFTs, Tokens or other hosted material. By doing this we avoid bloat, and mainnet net reliance beyond launch needs. Ultimately this platform can replace the need for servers, DNS hosting and much more while offering a much more robust solution than available today. I guess, you could call it Web3 or the "internet computer" as some have thrown the term around.

### Website on the Chain
Espers Blockchain will keep sites extremely safe and will make them virtually impenetrable, which is creating a new standard for website safety and security. In addition to the security improvements, Espers Blockchain will also ensure that your website is never taken down or removed, no matter what (PROVIDED THE CONTENT IS NOT ILLEGAL!!!). You will also have complete control of your data, and the sites will feature faster server times.

### NFT (Non-fungible Token)
Introducing altcoins to NFTs, as of v0.8.8.2 prototype now features NFT capabilities. This offers the ability to artists, musicians and animators alike a unified place to store, encrypt, protect, sell and share their artwork! Current compatible formats are JPG/JPEG, PNG, GIF (Animation), OGG VORBIS (Audio) in a square format for initial testing for pictures/animation and up to 5 minute sound files for OGG VORBIS audio. This is a soft limit done only for initial testing. These limits will soon be lifted for full release in future versions.

### Tokens (Like ETH)
Along with NFTs we have adapted the technology in the Fractal platform to launch and manage Tokens! No longer are there only the few giants that can do this, launch your own Token using Espers [ESP] as "GAS" and for no where near the fees!

### BVAC (Bits Visualized As Color)
BVAC is a unique system that we developed and created in house just for Espers [ESP] and associated projects. This offers us the ability to store ANY data as a PNG or JPG, similarly to a QR code, with only three files being required as apposed to three entire libraries that QR codes require and the data storage is denser. If you would like to learn more about this feature feel free to reach out to CryptoCoderz or SaltineChips. The current proof of concept implementation is the ability to store and read a public receiving address as a 16x16 BVAC image. Users can share their public keys this way by simply sending each other the BVAC image of the pubkey created from the wallet and then the receiving part is able to load the image using the wallet and decode it into the pubkey once again.

### Secured Messaging
Developing the usability features: The secured messaging system, masternodes (intuitive node launching and monitoring), smooth sync patch, shrinking blockchain, light clients and much much more.

### Custom Difficulty Retarget Algorithm “VRX”
VRX is designed from the ground up to integrate properly with the Velocity parameter enforcement system to ensure users no longer receive orphan blocks. In addition to this function it also dynamicaly adjusts for fluctuations in hashrate or staking whether it be great or small. Being a "Hybrid" blockchain, Espers [ESP] also utilizes VRX's advanced block shuffling and difficulty skewing proceedures in order to offer a truly equal mining/staking experience while further increasing the network's security and reliability. 

### Velocity Block Constraint System
Ensuring Espers stays as secure and robust as possible the CryptoCoderz team have implemented what's known as the Velocity block constraint system. This system acts as third and final check for both mined and peer-accepted blocks ensuring that all parameters are strictly enforced.

### HMQ1725 Algorithm
We use an custom internal algorithm known as HMQ1725 to sign blocks and conduct other functions, it takes its name from how it was designed: Highly-Modified-Quark 17-Algorithms 25-Scientific-Rounds

Specifications and General info
------------------
Espers uses:

		Boost1.74,
		OR Boost1.58+,
		OpenSSL1.02u,
		OR OpenSSL1.1x,
		Berkeley DB 6.2.32,
		Qt5.15.2 to compile

General Info:


		Block Spacing: 5 Minutes
		Stake Minimum Age: 90 Confirmations (PoS-v3) | 2 Hours (PoS-v2)
		Port: 22448
		RPC Port: 22442

Compiling Espers daemon on Ubunutu 18.04 / 20.04 LTS Bionic
---------------------------
### Note: guide should be compatible with other Ubuntu versions from 14.04+

### Become poweruser
```
sudo -i
```

### Dependencies install
```
cd ~; apt-get install ntp git build-essential libssl-dev libdb-dev libdb++-dev libboost-all-dev libqrencode-dev libcurl4-openssl-dev curl libzip-dev; apt-get update; apt-get upgrade; apt-get install git make automake build-essential libboost-all-dev; apt-get install yasm binutils libcurl4-openssl-dev openssl libssl-dev; sudo apt-get install libgmp-dev;
```

### Dependencies build and link
```
cd ~; wget http://download.oracle.com/berkeley-db/db-6.2.32.NC.tar.gz; tar zxf db-6.2.32.NC.tar.gz; cd db-6.2.32.NC/build_unix; ../dist/configure --enable-cxx; make; make install; ln -s /usr/local/BerkeleyDB.6.2/lib/libdb-6.2.so /usr/lib/libdb-6.2.so;ln -s /usr/local/BerkeleyDB.6.2/lib/libdb_cxx-6.2.so /usr/lib/libdb_cxx-6.2.so; export BDB_INCLUDE_PATH="/usr/local/BerkeleyDB.6.2/include"; export BDB_LIB_PATH="/usr/local/BerkeleyDB.6.2/lib"; cd ~;
```

### Personal upload EXAMPLE
```
cd ~; cp -r /home/ftpuser/ftp/files/ESP-clean/. ~/Espers
```

### GitHub pull RECOMMENDED
```
cd ~; git clone https://github.com/CryptoCoderz/Espers
```

### Build Espers daemon
```
cd ~; cd ~/Espers/src; chmod a+x obj; chmod a+x leveldb/build_detect_platform; chmod a+x leveldb; chmod a+x ~/Espers/src; chmod a+x ~/Espers; make -f ~/Espers/src/makefile/makefile.unix USE_UPNP=-; cd ~; cp ~/Espers/src/Espersd /usr/local/bin;
```

### Create config file for daemon
```
cd ~; sudo ufw allow 22448/tcp; sudo ufw allow 22442/tcp; sudo mkdir ~/.ESP; cat << "CONFIG" >> ~/.ESP/Espers.conf
listen=1
server=1
daemon=1
deminodes=1
demimaxdepth=200
testnet=0
rpcuser=espersuser
rpcpassword=SomeCrazyVeryVerySecurePasswordHere
rpcport=22442
port=22448
rpcconnect=127.0.0.1
rpcallowip=127.0.0.1
addnode=198.50.180.207
addnode=85.255.7.52
addnode=195.181.211.221
addnode=176.31.205.41
addnode=116.14.167.86
addnode=167.99.171.227
addnode=174.107.102.219
addnode=176.9.156.236
addnode=198.50.180.193
addnode=94.130.64.143
addnode=145.239.65.6
addnode=108.61.175.156
addnode=46.4.27.201
addnode=149.56.154.75
addnode=50.46.99.238
addnode=159.89.114.40

CONFIG
chmod 700 ~/.ESP/Espers.conf; chmod 700 ~/.ESP; ls -la ~/.ESP
```

### Run Espers daemon
```
cd ~; Espersd; Espersd getinfo
```

### Troubleshooting
### for basic troubleshooting run the following commands when compiling:
### this is for minupnpc errors compiling
```
make clean -f makefile.unix USE_UPNP=-
make -f makefile.unix USE_UPNP=-
```

License
-------

Espers [ESP] is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.

Development Process
-------------------

The `master` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags](https://github.com/CryptoCoderz/Espers/tags) are created
regularly to indicate new official, stable release versions of Espers [ESP].

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md).

The developer [mailing list](https://lists.linuxfoundation.org/mailman/listinfo/bitcoin-dev)
should be used to discuss complicated or controversial changes before working
on a patch set.

Developer Discord can be found at https://discord.gg/cn3AfPS .

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](/doc/unit-tests.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`

There are also [regression and integration tests](/qa) of the RPC interface, written
in Python, that are run automatically on the build server.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.
