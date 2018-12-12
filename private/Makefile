
THREADS ?= 0
MAXTRANSACTIONS ?= -1
GASLIMIT ?= 8000000

# binary of GETH
GETH = ../build/bin/geth

clean:
	rm -rf miner*

setup: clean
	mkdir miner1 miner2 miner3
	echo "password" > miner1/password.sec
	echo "password" > miner2/password.sec
	echo "password" > miner3/password.sec
	$(GETH) --datadir miner1 init genesis.json
	$(GETH) --datadir miner2 init genesis.json
	$(GETH) --datadir miner3 init genesis.json
	$(GETH) --datadir miner1 account new --password miner1/password.sec
	$(GETH) --datadir miner1 account new --password miner1/password.sec
	$(GETH) --datadir miner2 account new --password miner2/password.sec
	$(GETH) --datadir miner2 account new --password miner2/password.sec
	$(GETH) --datadir miner3 account new --password miner3/password.sec
	$(GETH) --datadir miner3 account new --password miner3/password.sec

start-1:
	$(GETH) --mine --identity "miner1" --networkid 101 --datadir miner1 --nodiscover --mine --rpc --rpcport "9001" --port "9101" --unlock 0 --password miner1/password.sec --ipcpath miner1/geth.ipc --miner.gaslimit $(GASLIMIT) --miner.threads $(THREADS) --miner.maxblocktransactions $(MAXTRANSACTIONS)

start-2:
	$(GETH) --mine --identity "miner2" --networkid 101 --datadir miner2 --nodiscover --mine --rpc --rpcport "9002" --port "9102" --unlock 0 --password miner2/password.sec --ipcpath miner2/geth.ipc --miner.gaslimit $(GASLIMIT) --miner.threads $(THREADS) --miner.maxblocktransactions $(MAXTRANSACTIONS)

start-3:
	$(GETH) --mine --identity "miner3" --networkid 101 --datadir miner3 --nodiscover --mine --rpc --rpcport "9003" --port "9103" --unlock 0 --password miner3/password.sec --ipcpath miner3/geth.ipc --miner.gaslimit $(GASLIMIT) --miner.threads $(THREADS) --miner.maxblocktransactions $(MAXTRANSACTIONS)

attach-1:
	$(GETH) attach miner1/geth.ipc

attach-2:
	$(GETH) attach miner2/geth.ipc

attach-3:
	$(GETH) attach miner3/geth.ipc

