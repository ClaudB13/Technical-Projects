# Technical-Projects
# Project: UEFI BIOS Update & Storage Volume Manipulation 

## System Context 
* **Motherboard:** ASRock B860M-C
* **Current Task:** Flash UEFI BIOS to the latest firmware version.
* **Primary Constraint:** The motherboard's "Instant Flash" utility requires a FAT32 file system, but the available hardware was a 1TB USB 3.0 drive.

## The Challenge: FAT32 Volume Limitations 
Windows disk management and standard formatting on volumes larger than 32G.                                 
Attempting to format a 1TB drive natively would only offer NTFS or exFAT, neither of which are recognized by the ASRock BIOS flash tool. 

## The Solution: Manual partition scaling instead of sourcing a smaller drive, I utilized a "Silver Partition" strategy to bypass OS limitations: 

1. **Volume Deletion:** Opened 'diskmgnt.msc' and deleted all existing volumes on the 1TB USB drive to return it to "Unallocated" status.
2. **Targeted Pertitioning:** Created a **New Simple Volume** but manually restricted teh size to **2000MB (2GB)**.
3. **File System Selection:** Because the partition was under the 32GB threshold, the **FAT32** option became available. I formatted the 2GB partition and assigned a drive letter.
4. **Firmware Deployment:** Loaded the BIOS update file onto the 2GB partition. The motherboard successfully detected the drive and completed the flash.
5. **Recovery:** Post-update, I deleted the 2GB partition and restored the drive to its full 1TB capacity using **exFAT** for high-capacity storage.

## Key Technical Competencies
**Disk Management:** Proficiency in volume shrinking, deletion, and allocation. 
**File System Knowledge:** Understanding the compatibility differences between FAT32, exFAT and NTFS. 
**Legacy Support:** Solving modern hardware requirements using legacy file system constraints. 
