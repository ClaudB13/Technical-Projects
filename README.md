# Technical-Projects
# Project: UEFI BIOS Update & Storage Volume Manipulation 

## System Context 
* **Motherboard:** ASRock B860M-C
* **Current Task:** Flash UEFI BIOS to the latest firmware version.
* **Primary Constraint:** The motherboard's "Instant Flash" utility requires a FAT32 file system, but the avalable hardware was a 1TB USB 3.0 drive.

## The Challenge: FAT32 Volume Limitations 
Windows disk management and standard formatting on volumes larger than 32G.                                 
Attempting to format a 1TB drive natively would only offer NTFS or exFAT, neither of which are recognized by the ASRock BIOS flash tool. 

## The Solution: Manual partition scaling instead of sourcing a smaller drive, I utilized a "Silver Pertition" strategy to bypass OS limitations: 

1. **Volume Deletion:** Opened 'diskmgnt.msc' and deleted all existing volumes on the 1TB USB drive to return it to "Unallocated" status.
2. **Targeted Pertitioning:** Created a **New Simple Volume** but manually restricted 
