# Section 2: Password Entropy and Strength Analysis

## Research Question: Entropy and Security
Password entropy measures the unpredictability of a password. According to NIST, "the strength of a password is determined by its entropy, calculated based on the character set and the length of the string" (NIST, 2024). High entropy is critical to resist brute-force attacks.

## Manual Calculations
Based on the group's analysis for the LUKS encryption passphrase, the following calculations were performed to determine the time required to crack the password:

### 1. Total Combinations
$C = 208,827,064,576$ combinations.

### 2. Attack Time Calculation ($T$)
Assuming a processing speed of $1,000,000,000$ attempts per second ($1 \text{ GHz}$):

$$T = \frac{208,827,064,576 \text{ combinations}}{1,000,000,000 \text{ attempts/sec}}$$

**Result:**
$$T = 208.82 \text{ seconds}$$

## Conclusion
A cracking time of approximately 208 seconds (less than 4 minutes) indicates a very low entropy for this specific test case. For the final Debian installation, a passphrase with at least 100 bits of entropy was used to ensure long-term security.

---
## Bibliography
NIST. (2024). *Digital Identity Guidelines: Password Strength and Entropy*. https://pages.nist.gov/800-63-3/
