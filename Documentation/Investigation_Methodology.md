# Digital Forensic Investigation Methodology

**Case ID:** DFIR-001  
**Tool:** Autopsy 4.23.1  
**Evidence:** 1 GB VHD containing a controlled NTFS filesystem

## 1. Evidence Preparation

A virtual hard disk was created using Windows Disk Management and formatted as NTFS.

The fictional evidence consisted of public company information, confidential CSV documents, a budget document, and meeting notes.

Controlled activities included file creation, document modification, normal Windows deletion, and Shift + Delete.

## 2. Evidence Preservation

The virtual disk was detached before creating the preserved master and working copies.

SHA-256 hashes were calculated using PowerShell to compare all three VHD files.

The working copy was used for forensic examination, while the master was reserved for preservation.

## 3. Forensic Examination

The working VHD was imported into Autopsy as a disk-image data source.

The examination included filesystem browsing, file metadata inspection, text-content examination, deleted-file analysis, and investigation of Windows Recycle Bin artifacts.

## 4. Recycle Bin Analysis

Two recycled content files and their associated `$I` metadata files were identified.

The binary `$I` records were examined to identify the original file paths, file sizes, and Windows FILETIME deletion timestamps.

These observations were recorded separately from ordinary NTFS file timestamps.

## 5. Timeline Reconstruction

Relevant creation, modification, and metadata-change timestamps were documented.

The Recycle Bin deletion timestamps were also incorporated into the evidence timeline.

The reconstructed events were compared against the activity log maintained during evidence preparation.

## 6. Reporting

The final report documents findings E01–E06, supporting artifacts, evidence integrity, methods, interpretations, and limitations.

Conclusions were restricted to what the available forensic evidence could establish.
