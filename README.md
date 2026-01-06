Aetheris
=====================================

https://aetherischain.com

What is Aetheris?
----------------

Aetheris is a decentralised digital currency with near-instant transaction speeds and negligible transaction fees built upon Proof of Stake 3.0 (PoSV3, BPoS) as
introduced by the Aetheris development team.

For more information about Aetheris itself, see https://aetherischain.com.

What is Aetheris?
----------------

Aetheris is the name of open source software which enables the use of this currency. It takes Aetheris to the next level by building upon
Bitcoin Core 0.13.2 with some patches from newer Bitcoin Core versions to offer performance enhancements, wider compatibility with third party services and a more advanced base.

For more information, as well as an immediately useable, binary version of the Aetheris software, see https://aetherischain.com.

License
-------

Aetheris is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/licenses/MIT.

Development Process
-------------------

The `master` branch is regularly built and tested, but is not guaranteed to be
completely stable. [Tags](https://github.com/aetherischain/aetherischain/tags) are created
regularly to indicate new official, stable release versions of Aetheris.

Change log can be found in [CHANGELOG.md](CHANGELOG.md).

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md).


Testing
-------

Testing and code review might be the bottleneck for development. Please help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](/doc/unit-tests.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled in configure) with: `make check`

There are also [regression and integration tests](/qa) of the RPC interface, written
in Python, that are run automatically on the build server.
These tests can be run (if the [test dependencies](/qa) are installed) with: `qa/pull-tester/rpc-tests.py`

The Travis CI system makes sure that every pull request is built for Windows, Linux, and OS X, and that unit/sanity tests are run automatically.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.


Tutorial - Compile Linux wallet on Ubuntu Server 22.04
Compile a wallet for Ubuntu Linux on Ubuntu Server 22.04 with the following tutorial.

Update your Ubuntu server with the following command:

sudo apt-get update && sudo apt-get upgrade -y

Install the required dependencies with the following command:

sudo apt-get install make automake cmake curl g++-multilib libtool binutils-gold bsdmainutils pkg-config python3 patch bison -y

Create your source code directory with the following commands:

cd ~/
mkdir source_code
cd source_code

Download the source code of your coin with the following command:

git clone https://github.com/aetherischain/aetheris-source.git

Type the following command to extract the tar file:

tar -xzvf aetheris-source.tar.gz

Type the following command to download the update for Boost:

wget https://raw.githubusercontent.com/walletbuilders/source-patches/master/scrypt-pos/13.2.0/boost_fix_scrypt_pos_1320.diff

Type the following command to update Boost:

patch -p1 < boost_fix_scrypt_pos_1320.diff

64-bit

Build x86_64-pc-linux-gnu with the following commands:

PATH=$(echo "$PATH" | sed -e 's/:\/mnt.*//g')
cd depends
make HOST=x86_64-pc-linux-gnu
cd ..

Type the following commands to compile your wallet for Ubuntu Linux.

./autogen.sh
CONFIG_SITE=$PWD/depends/x86_64-pc-linux-gnu/share/config.site ./configure --prefix=/
make

Type the following command to clean your source code:

make clean

32-bit

Build i686-pc-linux-gnu with the following commands:

PATH=$(echo "$PATH" | sed -e 's/:\/mnt.*//g')
cd depends
make HOST=i686-pc-linux-gnu
cd ..

Type the following commands to compile your wallet for Ubuntu Linux.

./autogen.sh
CONFIG_SITE=$PWD/depends/i686-pc-linux-gnu/share/config.site ./configure --prefix=/
make

The compiled wallet for Ubuntu Linux is located in the directory src/qt, the tools are located in the directory src.


