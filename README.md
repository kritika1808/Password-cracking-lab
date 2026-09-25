# Password Cracking Lab — Week 3 (Networkwalks)

Documentation of two lab exercises from the Networkwalks Cybersecurity & Ethical
Hacking course, **Week 3 – Password Cracking**. Both modules recover the
password of the same three encrypted PDF files (`My Locked PDF1.pdf`,
`My Locked PDF2.pdf`, `My Locked PDF3.pdf`) using a different toolset, and
each cracked PDF contains a CTF-style flag.

> ⚠️ **Scope note:** This lab uses files and hashes supplied by Networkwalks
> for training purposes. The techniques (hash extraction + dictionary attack)
> should only be used against files/systems you own or are explicitly
> authorized to test.

## Modules

| Module | Tools used | Doc |
|---|---|---|
| Module 1 | `pdf2john` (via OnlineHashCrack), **John the Ripper** + **Johnny** (GUI) | [docs/module1-jtr.md](docs/module1-jtr.md) |
| Module 2 | Networkwalks **Hash Calculator** + **Password Cracker** (browser-based, dictionary attack) | [docs/module2-networkwalks-tools.md](docs/module2-networkwalks-tools.md) |

## Results

| PDF | Cracked Password | Flag |
|---|---|---|
| My Locked PDF1.pdf | `good-luck` | `nw{cybersecurity_flag_captured_2608}` |
| My Locked PDF2.pdf | `password1` | `nw{networkwalks_persistence_jtr_270521}` |
| My Locked PDF3.pdf | `1qaz2wsx` | `nw{networkwalks_flag_260821_1}` |

Full write-up with evidence: [results/summary.md](results/summary.md)

## Repo structure

```
password-cracking-lab/
├── README.md
├── docs/
│   ├── module1-jtr.md                  # JTR John + Johnny walkthrough
│   └── module2-networkwalks-tools.md   # Networkwalks Hash Calculator + Password Cracker walkthrough
├── hashes/
│   ├── hash1.txt                       # PDF1 pdf2john hash
│   ├── hash2.txt                       # PDF2 pdf2john hash
│   └── hash3.txt                       # PDF3 pdf2john hash
├── results/
│   └── summary.md                      # Consolidated results table + flags
└── screenshots/
    ├── module1/                        # Evidence for Module 1 (26 screenshots)
    └── module2/                        # Evidence for Module 2 (11 screenshots)
```

## General method (both modules)

1. **Extract the hash** from the password-protected PDF using a `pdf2john`
   equivalent tool. This produces a crackable hash string starting with
   `$pdf$...` in the pdf2john/hashcat-compatible format.
2. **Save the hash** to a `.txt` file.
3. **Run a dictionary attack** against the hash — either locally with
   John the Ripper (via the Johnny GUI) or with the Networkwalks
   browser-based Password Cracker.
4. **Recover the plaintext password** once the tool finds a match in the
   wordlist.
5. **Open the PDF** with the recovered password and capture the flag
   printed inside.

## Tools reference

- [John the Ripper](https://www.openwall.com/john/) — password cracker (CLI)
- [Johnny](https://openwall.info/wiki/john/johnny) — GUI front-end for JTR
- [OnlineHashCrack PDF Hash Extractor](https://www.onlinehashcrack.com/tools-pdf-hash-extractor.php) — `pdf2john` as a web tool
- Networkwalks Hash Calculator — `https://networkwalks.com/hash-calculator/`
- Networkwalks Password Cracker — `https://networkwalks.com/password-cracker/`
