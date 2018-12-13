Private Blockchain
==================

This directory was created thanks to [this
documentation](https://chainskills.com/2017/03/10/part-3-setup-the-private-chain-miners/).
Please refer to this article to learn more.

This directory is designed to help run a private blockchain with three miners
(`miner1`, `miner2`, and `miner3`).

### Setup

To setup your environment, run...

```sh
make setup
```

This will create three directories for each miner, as well as initialize them
and create two accounts per miner. The password for each account is
"password".

### Start

To start a miner, run...

```sh
make start-1
```

Exchange the "1" with another number of a miner (ie "2" or "3"). This will
start the service and run it in the foreground.

If you want to start the miner with different values for gas limit
(`GASLIMIT`), max
transactions per block (`MAXTRANSACTIONS`), or number of threads (`THREADS`),
use those environment variables.

For example...

```sh
GASLIMIT=4000000 THREADS=2 MAXTRANSACTIONS=4 start-1
```

### Attach

To attach to a miner to run commands, run...

```sh
make attach-1
```

Exchange the "1" with another number of a miner (ie "2" or "3").
