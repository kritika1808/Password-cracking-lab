# Results Summary

Both modules were run against the same three encrypted PDFs and produced
identical passwords and flags, confirming the `$pdf$...` hash extracted from
each PDF is consistent across tools (OnlineHashCrack / Networkwalks Hash
Calculator) and crackers (John the Ripper via Johnny / Networkwalks Password
Cracker).

| PDF | Hash file | Cracked Password | Flag | Cracked via (Module 1 / JTR) | Cracked via (Module 2 / NW Tools) |
|---|---|---|---|---|---|
| My Locked PDF1.pdf | [hash1.txt](../hashes/hash1.txt) | `good-luck` | `nw{cybersecurity_flag_captured_2608}` | ✅ | ✅ |
| My Locked PDF2.pdf | [hash2.txt](../hashes/hash2.txt) | `password1` | `nw{networkwalks_persistence_jtr_270521}` | ✅ | ✅ |
| My Locked PDF3.pdf | [hash3.txt](../hashes/hash3.txt) | `1qaz2wsx` | `nw{networkwalks_flag_260821_1}` | ✅ | ✅ |

## Raw hashes

```
# hash1.txt
$pdf$4*4*128*-1028*1*16*ca7f72f11459cba469f1005a8765ed51*32*f32d8fa1bfbe2648226dffc39f7909ea0021446990b9e4114071a4d9104984c1*32*9322f50c29569712067a775264635e4954ccb1b99e209d664984054ffad30a6a

# hash2.txt
$pdf$4*4*128*-1028*1*16*0853f2cde0ef15b1c0f93ed229d3b1ad*32*8f13ce5aa39ad974364d36a057da76790021446990b9e4114071a4d9104984c1*32*ceecdac74b19b5a62688d3b3524e1374c955cbb9cc3c45316494d9446ef81af1

# hash3.txt
$pdf$4*4*128*-1028*1*16*34eb542eff4e1b0b32d25ce15a9a7281*32*b77872bfc9a24fb2f845066283a8fc1b0021446990b9e4114071a4d9104984c1*32*e7572256e4b552cd57988f5134214b91920d94d7a6bf550ea94a2995c7f2ab02
```

## Takeaways

- All three passwords are weak, dictionary-guessable strings (`good-luck`,
  `password1`, `1qaz2wsx`) — the lab's intended lesson that short or
  common passwords fall quickly to a dictionary attack, while a longer,
  random, mixed-character password would resist both wordlist attacks used
  here.
- The PDF encryption in all three files was revision 4, 128-bit RC4
  (`$pdf$4*4*128*...`), and cracking speed was on the order of single-digit
  to low-double-digit attempts per second on the Networkwalks Password
  Cracker (browser JS implementation), so real-world offline GPU cracking
  (hashcat) would be dramatically faster against the same hash.
