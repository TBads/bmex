bmex — BitMEX DTC Gateway
-------------------------------------------------------------------------------
%%VERSION%%

bmex is a gateway between the [DTC protocol](http://dtcprotocol.org) and the [BitMEX exchange](https://www.bitmex.com).

bmex is distributed under the ISC license.

Homepage: https://github.com/vbmithr/bmex

## Install

The instructions are for a debian-like distribution (tested on Debian, Ubuntu).

```bash
adduser dtc

# * Install OPAM >= 1.2.2
# For Debian:
# debian stable: See http://opam.ocaml.org/doc/Install.html
# debian >= testing: apt-get install opam
# For Ubuntu:
add-apt-repository ppa:avsm/ppa
apt update
apt install opam

# Will be required by bmex project later
apt install -qq -yy libffi-dev libgmp-dev libleveldb-dev libsnappy-dev libssl-dev libxen-dev uuid-dev zlib1g-dev
su dtc
opam init
opam switch 4.04.0
eval $(opam config env)
opam repo add janestreet git://github.com/janestreet/opam-repository

git clone https://github.com/vbmithr/bmex.git
cd bmex_dtc

# Install ocaml deps
./scripts/install_bmex.sh
# Build the project
make

# Run the daemon (yeah, an exe file on Linux)
./_build/default/src/bmex.exe -help
# Or,
./_build/default/src/bmex.exe -port 5567 -daemon -tls -testnet -loglevel 3
```

Sierra Chart expects bmex to run on port 5567 with TLS enabled.

## Upgrade

```bash
opam pin remove $(opam pin -s)
opam update
opam upgrade
```

Then continue from `Install ocaml deps` above.
