# Evidence Integrity Verification — DFIR-001

## Case overview

- **Case:** Apex Data Theft Investigation (fictional training simulation)
- **Evidence format:** Windows Virtual Hard Disk (`.vhd`)
- **Hash algorithm:** SHA-256
- **Verification tool:** Windows PowerShell `Get-FileHash`
- **Examined application:** Autopsy 4.23.1

## Evidence copies

| Copy | Local file used during investigation | Purpose |
|---|---|---|
| Original | `Apex-Lab.vhd` | Simulated source disk, detached before copying |
| Master | `01_Evidence/Master/Master copy.vhd` | Preservation copy |
| Working | `01_Evidence/Working/Working copy.vhd` | Analysis in Autopsy |

> The `01_Evidence` directory and all VHD images are deliberately excluded from the public GitHub repository. Paths above describe the private investigation setup, not files available for download here.

## Initial SHA-256 verification

All three files were hashed individually using PowerShell. Each produced this value:

```text
34BF5F094CE7CC1977C69CF6C929F48978C4F27C19F7DFFA4EE769FD645AEFDC
```

**Result:** Matching hashes showed the three complete VHD files were byte-for-byte identical at the time of the initial check. This hash applies to each **whole VHD**, not to individual documents recovered from it.

## Subsequent master-copy recheck

After the forensic examination, the preserved **master** VHD was hashed again. The user-reported result was:

```text
34BF5F094CE7CC1977C69CF6C929F48978C4F27C19F7DFFA4EE769FD645AEFDC
```

**Result:** The master copy's hash matched the initial verification value. A subsequent hash of the working VHD was not established as part of this final recheck and is **not claimed** here.

## Reproducing verification (with access to private files)

Run in PowerShell and adjust the root folder if required:

```powershell
$root = "E:\DFIR-Projects\Apex-Investigation"
$paths = @(
    "$root\Apex-Lab.vhd",
    "$root\01_Evidence\Master\Master copy.vhd",
    "$root\01_Evidence\Working\Working copy.vhd"
)

foreach ($path in $paths) {
    Get-FileHash -Path $path -Algorithm SHA256
}
```

Do not mount or alter the preserved master image to verify its hash.

## Interpretation and limitations

- Matching cryptographic hashes support integrity and byte-for-byte equality at the points verified; they do not prove that the initial simulated data was authentic evidence from a real incident.
- The master was intended to remain unchanged, while the working image was supplied to Autopsy.
- Individual file hashes were not calculated for all recovered items; the whole-image hash is not a substitute for per-file hashes.
- Exact acquisition and recheck times were not captured in the published record; do not present them as known.

## Related documentation

- [Final forensic report](../reports/DFIR-001_Final_Investigation_Report.pdf)
- [Evidence timeline](../reports/Evidence_Timeline_Corrected.csv)

**Privacy:** This repository publishes documentation and selected redacted screenshots only. Forensic images and Autopsy case databases are retained outside the public repository.
