# go-bip39
[![CI](https://github.com/fbsobreira/go-bip39/actions/workflows/ci.yml/badge.svg)](https://github.com/fbsobreira/go-bip39/actions/workflows/ci.yml)
[![Go Reference](https://pkg.go.dev/badge/github.com/fbsobreira/go-bip39.svg)](https://pkg.go.dev/github.com/fbsobreira/go-bip39)
[![Go Report Card](https://goreportcard.com/badge/github.com/fbsobreira/go-bip39)](https://goreportcard.com/report/github.com/fbsobreira/go-bip39)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/fbsobreira/go-bip39/blob/master/LICENSE)


A golang implementation of the BIP0039 spec for mnemonic seeds

> **Note:** This is a preserved copy of the original `github.com/tyler-smith/go-bip39` repository, which is no longer available.

## Example

```go
package main

import (
  "github.com/fbsobreira/go-bip39"
  "github.com/fbsobreira/go-bip32"
  "fmt"
)

func main(){
  // Generate a mnemonic for memorization or user-friendly seeds
  entropy, _ := bip39.NewEntropy(256)
  mnemonic, _ := bip39.NewMnemonic(entropy)

  // Generate a Bip32 HD wallet for the mnemonic and a user supplied password
  seed := bip39.NewSeed(mnemonic, "Secret Passphrase")

  masterKey, _ := bip32.NewMasterKey(seed)
  publicKey := masterKey.PublicKey()

  // Display mnemonic and keys
  fmt.Println("Mnemonic: ", mnemonic)
  fmt.Println("Master private key: ", masterKey)
  fmt.Println("Master public key: ", publicKey)
}
```

## Credits

Wordlists are from the [bip39 spec](https://github.com/bitcoin/bips/tree/master/bip-0039).

Test vectors are from the standard Python BIP0039 implementation from the
Trezor team: [https://github.com/trezor/python-mnemonic](https://github.com/trezor/python-mnemonic)
