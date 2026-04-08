# Section 3: Hash Comparison and Hashcat Analysis

## Research Question: Cryptographic Hashes
Cryptographic hash functions are one-way processes that ensure data integrity. "Hash functions are fundamental tools in cryptography, used for digital signatures and secure password storage" (DigiCert, 2024). They are designed to be fast to compute but computationally expensive to reverse.

## Hashcat Experimental Results
The following table compares two common attack scenarios executed with Hashcat to test the resistance of different entropy levels:

| PARAMETERS | CASE 1: LOW ENTROPY | CASE 2: MEDIUM ENTROPY |
| :--- | :--- | :--- |
| **PASSWORD** | 12345678 | Uide2026* |
| **ATTACK METHOD** | Dictionary (rockyou.txt) | Brute Force (?a?a?a?a?a?a?a?a Mask) |
| **RUNNING TIME** | 0 seconds (instantaneous) | 9 days, 17 hours (estimated) |
| **FINAL STATUS** | Successful (Cracked) | Unfeasible (Exhausted) |

## Analysis
The experiment demonstrates that the "rockyou.txt" dictionary attack is extremely efficient against common passwords like `12345678`. In contrast, the medium entropy password `Uide2026*` significantly increases the complexity, making a full brute-force mask attack unfeasible for standard hardware within a reasonable timeframe.
