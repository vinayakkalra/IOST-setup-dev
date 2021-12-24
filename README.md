# IOST Setup Environment for Smart Contract Development

IOST Developer tutorials, setting up the environment guide for IOST smart contracts.

In the [previous section](https://github.com/vinayakkalra/IOST-getting-started) we covered the installations of the required softwares for IOST smart contract development. In this section we will cover building IOST on our environment along with installation of iWallet CLI. Please make sure you have all the softwares installed as mentioned in the previous section.

## Build IOST

Run the below commands to clone the go-iost repo from the official IOST github account.

> git clone https://github.com/iost-official/go-iost.git
> 
> cd go-iost
> 
> git lfs pull
> 
> make vmlib_install
> 
> make build install

## Installating iWallet Command Line Interface

Run the below command in the terminal

> go install github.com/iost-official/go-iost/v3/cmd/iwallet@latest

To check if the installation is successful, run the below command in the terminal:

> iwallet

It would give an output something like this:

```
An IOST RPC client

Usage:
  iwallet [command]

Available Commands:
  account     KeyPair manager
  balance     Check the information of a specified account
  block       Print block info
  call        Call the method in contracts
  compile     Generate contract abi
  help        Help about any command
  key         Create a key pair
  publish     Publish a contract
  receipt     Find receipt
  save        Save a transaction request with given actions to a file
  sign        Sign a tx and save the signature
  state       Get blockchain and node state
  system      Send system contract action to blockchain
  table       Fetch stored info of given contract
  transaction Find transactions
  transfer    Transfer IOST

Flags:
  -a, --account string                 which account to use
      --amount_limit string            amount limit for one transaction, eg iost:300.00|ram:2000 (default "*:unlimited")
      --chain_id uint32                chain id which distinguishes different network (default 1024)
      --check_result                   check publish/call status after sending to chain (default true)
      --check_result_delay float32     rpc checking will occur at [checkResultDelay] seconds after sending to chain. (default 3)
      --check_result_max_retry int32   max times to call grpc to check tx status (default 20)
      --config string                  configuration file (default $HOME/.iwallet.yaml)
  -e, --expiration int                 expiration time for a transaction in seconds (default 300)
  -l, --gas_limit float                gas limit for a transaction (default 1e+06)
  -p, --gas_ratio float                gas ratio for a transaction (default 1)
  -h, --help                           help for iwallet
  -s, --server string                  set server of this client (default "localhost:30002")
      --sign_algo string               sign algorithm (default "ed25519")
      --signers strings                additional signers
      --tx_time string                 use the special tx time instead of now, format: 2019-01-22T17:00:39+08:00
      --use_longest                    get info on longest chain
  -v, --verbose                        print verbose information (default true)

Use "iwallet [command] --help" for more information about a command.
```

## Launch IOST Server Locally

Run the following command in a terminal to launch the IOSt Server. Please make sure your terminal is set to the directory where you have placed go-iost folder cloned above in Build IOST section

> iserver -f ./config/iserver.yml

## Add an account in local server using iwallet

Run the following command to import an account in the local node.

> iwallet account import admin 2yquS3ySrGWPEKywCPzX4RTJugqRh7kJSo5aehsLYPEWkUxBWA39oMrZ7ZxuM4fgyXYs2cPwh5n8aNNpH5x2VyK1

After this command, the key store json file will written into ~/.iwallet/admin.json. Later 'iwallet --account admin' command will lookup account key store json inside ~/.iwallet folder and find the correct file.

To Know more commands on the iWallet CLI please refer to the [IOST Docs](https://developers.iost.io/docs/en/4-running-iost-node/iWallet.html)

