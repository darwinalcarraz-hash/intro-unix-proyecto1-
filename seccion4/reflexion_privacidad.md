# Section 4: Cryptography and Privacy Research

## 1. Asymmetric Encryption and GPG
Asymmetric encryption is a cryptographic method that uses a pair of distinct keys: a **public key** to encrypt and a **private key** to decrypt. This system eliminates the need to share a secret password, allowing the public key to be freely distributed while the private key remains under the exclusive custody of the owner (Badman & Kosinski, n.d.).

**In GPG, it works through:**
* **Storage and Keyring:** GPG stores keys in the `.gnupg` folder. The `pubring.kbx` file acts as the keyring where personal and imported keys are organized (Parrales, 2021).
* **Key Structure:** The system creates a primary public key (`pub`) for signing and a subkey (`sub`) for encryption and decryption (Parrales, 2021).
* **Encryption and Authentication:** Digital signatures are created by encrypting the file's hash with the sender's private key, ensuring authenticity and integrity (Badman & Kosinski, n.d.).

---

## 2. Comparison of Email Providers

| Feature | Proton Mail | Gmail | Outlook |
| :--- | :--- | :--- | :--- |
| **Encryption at Rest** | Zero-access (AES-256) | Standard server-side (AES) | BitLocker encryption |
| **Encryption in Transit** | TLS | Standard TLS | Standard TLS |
| **E2EE** | Native via PGP (automatic) | Requires Enterprise | Requires manual S/MIME |
| **Data Policies** | No IP logging; Swiss privacy | Data for ads/personalization | Data for diagnostics |
| **Legal Jurisdiction** | Switzerland | United States (CLOUD Act) | United States (CLOUD Act) |

*Note: Based on technical privacy documentation (Proton, 2024; Google Privacy, 2024; Microsoft Privacy, 2024).*

---

## 3. PKI Model vs. Web of Trust (WoT)
The **PKI model** based on Certification Authorities (CA) is a hierarchical framework where a trusted third party validates identities through digital certificates (IBM, n.d.).

* **Advantages of PKI:** (1) **Massive Scalability:** Users trust millions of entities by trusting a few root CAs. (2) **Efficient Revocation:** Uses CRLs to immediately invalidate compromised certificates (Axelspire, 2025).
* **Disadvantages of PKI:** (1) **Single Point of Failure:** Security depends entirely on the CA's integrity. (2) **Centralized Control:** Trust is dictated by large organizations, reducing individual control (Cryptology ePrint Archive, 2013).

---

## 4. GDPR (EU) and LOPDP (Ecuador) Comparison
The GDPR and LOPDP establish legal frameworks for personal information control. The Ecuadorian law is significantly inspired by the European model (Roldán, 2024).

| Aspect | GDPR (European Union) | LOPDP (Ecuador) |
| :--- | :--- | :--- |
| **Email Control** | Explicit opt-in consent | Prior consent (Art. 8, p. 15) |
| **Digital Surveillance** | Right against profiling | Informational self-determination |
| **Data Access** | Right to obtain copies | Origin/destination info (Art. 13) |
| **Right to be Forgotten** | Right to erasure | Demand data deletion (Art. 15) |
| **Automated Decisions** | Right to human review | Prohibition without consent (Art. 20) |

---

## 5. Email Metadata and Privacy
**Metadata** includes technical data like IP addresses, subject lines, and timestamps (InboxAlly, 2025). 

**Why encryption doesn't protect it:** Intermediate servers must read the metadata (the "envelope") to route the message. If it were hidden, delivery would fail (Bodekaer, 2025).
**Implications:** It allows **traffic analysis**, creating detailed behavioral profiles without reading the message content (Universidad Europea, 2025).

## Final Reflection
After
completing this project with these encryption models, we learned that digital
privacy requires a balance between technology and legislation. While GPG
guarantees confidentiality, metadata exposure remains a critical vulnerability
that content encryption cannot address. We must understand that relying on
centralized PKI models offers scalability but creates a single point of
failure. 
In
conclusion, protecting digital identity depends on choosing secure tools and
understanding data protection laws like GDPR (The General Data Protection
Regulation) and LOPDP.(Organic Law on the Protection of
Personal Data).
## References
* Asamblea Nacional del Ecuador. (2021). *Ley Orgánica de Protección de Datos Personales*.
* Axelspire. (2025). *Foundations of Trust Models: PKI vs Web of Trust*.
* Badman, A. & Kosinski, M. (n.d.). *What is asymmetric encryption?*. IBM.
* Bodekaer, M. (2025). *Email metadata and privacy*.
* Cryptology ePrint Archive. (2013). *Trust Views for the Web PKI*.
* Parrales, D. (2021). *Cifrado asimétrico con gpg y openssl*.
* Roldán, J. (2024). *La protección de datos personales en Ecuador*.
