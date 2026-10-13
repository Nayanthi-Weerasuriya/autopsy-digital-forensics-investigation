# Digital Forensics Investigation with Autopsy

### DFIR-001 | Simulated Corporate Data Investigation

A hands-on digital forensics project examining a simulated corporate data-handling incident using **Autopsy 4.23.1**, NTFS filesystem analysis, evidence integrity verification, deleted-file recovery, and Windows Recycle Bin forensics.

## Project Overview

This project simulates an internal investigation at Apex Financial Solutions, a fictional financial services organization.

A 1 GB Windows virtual hard disk was prepared with fictional company documents and controlled file activities. A forensic examination was then conducted to identify active and deleted files, recover digital artifacts, and reconstruct relevant filesystem events.

**This is an educational simulation, not an investigation of an actual data breach or crime.**

## Tools and Technologies

- Autopsy 4.23.1
- Windows 11
- NTFS filesystem
- Windows Virtual Hard Disk (VHD)
- PowerShell and SHA-256
- Windows Recycle Bin artifact analysis
- Excel / CSV for timeline documentation

## Investigation Methodology

1. Created a controlled NTFS virtual disk containing fictional business documents.
2. Simulated document modification and two deletion methods.
3. Preserved original, master, and working evidence copies.
4. Verified evidence integrity using SHA-256 hashing.
5. Examined the working image using Autopsy.
6. Recovered deleted-file content and investigated Recycle Bin artifacts.
7. Reconstructed filesystem activity and compared findings with the simulation log.
8. Prepared an evidence-based forensic investigation report.

## Key Findings

| Evidence | Description | Result |
|---|---|---|
| E01 | Deleted confidential budget document | Textual content recovered |
| E02 | Client list CSV | Active file identified and readable |
| E03 | Quarterly revenue CSV | Active file identified and readable |
| E04 | Modified meeting notes | Content and modification metadata examined |
| E05 | Recycled client-list document | Original path and Recycle Bin deletion time decoded |
| E06 | Recycled revenue document | Original path and Recycle Bin deletion time decoded |

The investigation demonstrated that both normal deletion and Shift + Delete may leave recoverable forensic artifacts.

## Evidence Integrity

The original VHD and the preserved master and working copies produced matching SHA-256 hashes at initial verification.

The master image was subsequently checked again, with its recorded hash remaining unchanged.

The full forensic disk images are intentionally excluded from this public repository.

## Findings and Documentation

- [Final Forensic Investigation Report](reports/DFIR-001_Final_Investigation_Report.pdf)
- [Evidence Timeline](reports/Evidence_Timeline_Corrected.csv)
- [Detailed Investigation Findings](reports/Investigation_Findings_Final.txt)
- [Investigation Methodology](documentation/Investigation_Methodology.md)

## Limitations

This project uses deliberately constructed fictional evidence. Filesystem timestamps and recovered documents do not independently establish the identity or intentions of a person or demonstrate an actual data theft.

## Skills Demonstrated

Digital Forensics · DFIR · NTFS Analysis · Evidence Preservation · SHA-256 Verification · Deleted File Recovery · Windows Recycle Bin Analysis · Timeline Reconstruction · Technical Reporting

## Disclaimer

All documents and financial information in this project are fictional and were created solely for educational purposes.
