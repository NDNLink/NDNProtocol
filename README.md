# NDN Protocol
NDN Protocol Is the Decentralized Storage Integration Protocol And Oracle
NDN Protocol  chain based on polkadot Substrate  Implementation

# NDN Protocol

Implementation of a https://ndn.link node in Rust based on the Substrate framework.


[substrate-repo]: https://github.com/paritytech/substrate

This repo contains runtimes for the NDNProtocol networks. The README provides
information about installing the `NDNProtocol` binary and developing on the codebase. For more
specific guides, like how to be a validator, see the


## Installation

If you just wish to run a NDNProtocol node without compiling it yourself, you may
either run the latest binary from our

Installation from the debian or rpm repositories will create a `systemd`
service that can be used to run a NDN node. This is disabled by default,
and can be started by running `systemctl start NDNProtocol` on demand (use
`systemctl enable NDNProtocol` to make it auto-start after reboot). By default, it
will run as the `NDNProtocol` user.  Command-line flags passed to the binary can
be customised by editing `/etc/default/NDNProtocol`. This file will not be
overwritten on updating NDN Protocol. You may also just run the node directly from
the command-line.

### Debian-based (Debian, Ubuntu)

Currently supports Debian 10 (Buster) and Ubuntu 20.04 (Focal), and
derivatives. Run the following commands as the `root` user.

```
# Import the security@parity.io GPG key
gpg --recv-keys --keyserver hkps://keys.mailvelope.com 9D4B2B6EB8F97156D19669A9FF0812D491B96798
gpg --export 9D4B2B6EB8F97156D19669A9FF0812D491B96798 > /usr/share/keyrings/parity.gpg
# Add the Parity repository and update the package index
echo 'deb [signed-by=/usr/share/keyrings/NDNProtocol.gpg] https://releases.parity.io/deb release main' > /etc/apt/sources.list.d/NDNProtocol.list
apt update
# Install NDNProtocol
apt install NDNProtocol

```

### RPM-based (Fedora, CentOS)

Currently supports Fedora 32 and CentOS 8, and derivatives.

```
# Install dnf-plugins-core (This might already be installed)
dnf install dnf-plugins-core
# Add the repository and enable it
dnf config-manager --add-repo https://releases.NDNProtocol.io/rpm/NDNProtocol.repo
dnf config-manager --set-enabled NDN
# Install NDNProtocol (You may have to confirm the import of the GPG key, which
# should have the following fingerprint: 9D4B2B6EB8F97156D19669A9FF0812D491B96798)
dnf install NDNProtocol
```

## Building

### Install via Cargo

If you want to install NDNProtocol in your PATH, you can do so with with:

```bash
cargo install --git https://github.com/NDNLink/NDNProtocol --tag <version> NDNProtocol --locked
```

### Build from Source

If you'd like to build from source, first install Rust. You may need to add Cargo's bin directory
to your PATH environment variable. Restarting your computer will do this for you automatically.

```bash
curl https://sh.rustup.rs -sSf | sh
```

If you already have Rust installed, make sure you're using the latest version by running:

```bash
rustup update
```

Once done, finish installing the support software:

```bash
sudo apt install build-essential git clang libclang-dev pkg-config libssl-dev
```

Build the client by cloning this repository and running the following commands from the root
directory of the repo:

```bash
git checkout <latest tagged release>
./scripts/init.sh
cargo build --release
```

Note that compilation is a memory intensive process. We recommend having 4 GiB of phyiscal RAM or swap available (keep in mind that if a build hits swap it tends to be very slow).

## Networks

This repo supports runtimes for NDN Protocol , Kusama, and Westend.

### Connect to NDNProtocol Mainnet

Connect to the global NDN Protocol Mainnet network by running:

```bash
./target/release/NDN --chain=NDNProtocol
```





### Obtaining DOTs

If you want to do anything on NDNProtocol, then you'll need to get an account and
some NDN respectively. See the
i.NDN.network/docs/en/learn-DOT#getting-westies) on the Wiki.

## Hacking on NDNProtocol

If you'd actually like hack on NDNProtocol, you can grab the source code and build it. Ensure you have
Rust and the support software installed. This script will install or update Rust and install the
required dependencies (this may take up to 30 minutes on Mac machines):
