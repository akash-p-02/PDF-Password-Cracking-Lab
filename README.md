<<<<<<< HEAD
# PDF Password Cracking Lab

A hands-on cybersecurity practical documenting PDF password-hash extraction and dictionary-based password recovery using Kali Linux, John the Ripper, and NetworkWalks lab tools.

> **Lab scope:** This repository documents work performed on two password-protected PDF files supplied for the NetworkWalks exercise. The techniques are intended for authorized security testing and learning only.

## Objectives

- Extract a crackable password hash from an encrypted PDF.
- Understand the PDF hash format used by password-recovery tools.
- Test password candidates using a wordlist.
- Recover passwords with John the Ripper and the NetworkWalks Password Cracker.
- Verify recovered passwords by opening the corresponding PDFs.

## Tools and Environment

| Tool | Purpose |
|---|---|
| Kali Linux | Lab operating system |
| Firefox | Accessing the NetworkWalks lab tools |
| NetworkWalks Hash Calculator | Extracting the PDF-compatible hash |
| NetworkWalks Password Cracker | Testing the second hash against its built-in list |
| John the Ripper | Dictionary-based recovery for the first PDF |
| PDF viewer | Verifying the recovered passwords and flags |

## Lab Workflow

### 1. Extract the PDF hash

I used the PDF option in the NetworkWalks Hash Calculator and selected `My Locked PDF2.pdf`. The tool identified the file as encrypted and returned a PDF hash compatible with the formats described on the page (pdf2john / hashcat). I saved the extracted value in `Hash2.txt`.

See: [`Screenshots/pdf-hash-extraction.png`](Screenshots/pdf-hash-extraction.png)

### 2. Recover the first PDF password with John the Ripper

The first hash was saved in `Hash1.txt`. I ran John the Ripper in Kali Linux:

```bash
john Hash1.txt
```

To display the recovered result:

```bash
john --show Hash1.txt
```

The terminal reported one password hash cracked.

See: [`Screenshots/john-the-ripper-output.png`](Screenshots/john-the-ripper-output.png)

### 3. Recover the second PDF password

I pasted the second PDF hash into the NetworkWalks Password Cracker and selected its built-in list of 100 passwords. The page showed 91 of 100 candidates tested before reporting a match.

See: [`Screenshots/password-cracker-match.png`](Screenshots/password-cracker-match.png)

### 4. Verify both results

I entered each recovered password into its corresponding PDF and confirmed that both documents opened successfully.

- First PDF: [`Screenshots/pdf1-flag-verification.png`](Screenshots/pdf1-flag-verification.png)
- Second PDF: [`Screenshots/pdf2-flag-verification.png`](Screenshots/pdf2-flag-verification.png)

## Results

| File | Recovery method | Result |
|---|---|---|
| `My Locked PDF1.pdf` (`Hash1.txt`) | John the Ripper | Password recovered; PDF opened |
| `My Locked PDF2.pdf` (`Hash2.txt`) | NetworkWalks Password Cracker, built-in 100-word list | Password recovered; PDF opened |

The recovered passwords and lab flags are documented in the practical report in the `Report/` directory.

## Repository Structure

```text
PDF-Password-Cracking-Lab/
├── README.md
├── LICENSE
├── .gitignore
├── Report/
│   ├── PDF-Password-Cracking-Report.pdf
│   └── PDF-Password-Cracking-Report.docx
└── Screenshots/
    ├── hash-extraction evidence
    ├── password-cracker evidence
    ├── John the Ripper output
    └── PDF verification evidence
```

## Key Learnings

- Encrypted PDFs can expose structured password hashes that can be tested offline.
- Password-recovery tools require hashes in a compatible format.
- Wordlist attacks test candidate passwords and depend on the candidates available.
- A tool's success message should be followed by verification using the original file.
- Weak or commonly used passwords are more vulnerable to dictionary-based guessing.

## Responsible Use

Only perform password-recovery testing on files you own or have explicit permission to assess. Do not use these techniques to access documents or systems without authorization.

## Report

The detailed practical report, including the methodology, terminal output, recovered results, flags, and screenshot evidence, is available here:

- [PDF Report](Report/PDF-Password-Cracking-Report.pdf)
- [Editable Word Report](Report/PDF-Password-Cracking-Report.docx)
=======
# PDF-Password-Cracking-Lab
>>>>>>> 7bb67ae8fc41c2bf57b9077328d303defcf3c63d
