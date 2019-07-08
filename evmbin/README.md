
## evmbin

EVM implementation for Parity.

### Build
```
  cargo build
```

### Usage

```
parity-evm --help
EVM implementation for Parity.
  Copyright 2015-2019 Parity Technologies (UK) Ltd.

Usage:
    parity-evm state-test <file> [--json --std-json --std-dump-json --only NAME --chain CHAIN --std-out-only --std-err-only]
    parity-evm stats [options]
    parity-evm stats-jsontests-vm <file>
    parity-evm [options]
    parity-evm [-h | --help]

Commands:
    state-test         Run a state test from a json file.
    stats              Execute EVM runtime code and return the statistics.
    stats-jsontests-vm Execute standard json-tests format VMTests and return
                       timing statistics in tsv format.

Transaction options:
    --code CODE        Contract code as hex (without 0x).
    --to ADDRESS       Recipient address (without 0x).
    --from ADDRESS     Sender address (without 0x).
    --input DATA       Input data as hex (without 0x).
    --gas GAS          Supplied gas as hex (without 0x).
    --gas-price WEI    Supplied gas price as hex (without 0x).

State test options:
    --only NAME        Runs only a single test matching the name.
    --chain CHAIN      Run only tests from specific chain.

General options:
    --json             Display verbose results in JSON.
    --std-json         Display results in standardized JSON format.
    --std-err-only     With --std-json redirect to err output only.
    --std-out-only     With --std-json redirect to out output only.
    --std-dump-json    Display results in standardized JSON format
                       with additional state dump.
Display result state dump in standardized JSON format.
    --chain CHAIN      Chain spec file path.
    -h, --help         Display this message and exit.
```

## Example

Let's change the text 'hello' (0x68656c6c6f) with the new opcode uppercase (0x24)
```
$ parity-evm  --code 6468656c6c6f2400 --std-json

{"pc":0,"op":100,"opName":"PUSH5","gas":"0xffffffffffffffff","stack":[],"storage":{},"depth":1}
{"pc":6,"op":36,"opName":"UPPER","gas":"0xfffffffffffffffc","stack":["0x68656c6c6f"],"storage":{},"depth":1}
{"pc":7,"op":0,"opName":"STOP","gas":"0xfffffffffffffff9","stack":["0x48454c4c4f"],"storage":{},"depth":1}
{"stateRoot":"0x0000000000000000000000000000000000000000000000000000000000000000"}
{"output":"0x","gasUsed":"0x6","time":8884}

```


## Parity Ethereum toolchain
_This project is a part of the Parity Ethereum toolchain._

- [evmbin](https://github.com/paritytech/parity-ethereum/blob/master/evmbin/) - EVM implementation for Parity Ethereum.
- [ethabi](https://github.com/paritytech/ethabi) - Parity Ethereum function calls encoding.
- [ethstore](https://github.com/paritytech/parity-ethereum/blob/master/accounts/ethstore) - Parity Ethereum key management.
- [ethkey](https://github.com/paritytech/parity-ethereum/blob/master/accounts/ethkey) - Parity Ethereum keys generator.
- [whisper](https://github.com/paritytech/parity-ethereum/blob/master/whisper/) - Implementation of Whisper-v2 PoC.
