# Analysis-of-the-Disk-Structure-using-Sleuth-Kit
## AIM:
To analyze the disk structure of a given disk image using Sleuth Kit tools in Kali Linux.

## REQUIREMENTS
- **Operating System**: Windows 10/11 or Kali Linux
- **Tools**:  
  - [The Sleuth Kit for Windows](https://sleuthkit.org/)  
  - Optional GUI: [Autopsy Forensic Browser](https://www.autopsy.com/)
- **Test Data**: Disk image file (`disk.dd`, `disk.img`, `.E01`)

## ARCHITECTURE DIAGRAM
```mermaid
flowchart TD
    A[Disk Image / Physical Disk] --> B[mmls - Partition Analysis]
    B --> C[fsstat - File System Metadata]
    C --> D[fls - File Listing]
    D --> E[icat - File Recovery]
    E --> F[Recovered Data / Metadata Report]
```
## DESIGN STEPS:
### Step 1:
- Obtain or create a disk image file (e.g., disk.dd) to analyze.
- Open the terminal in Kali Linux.

### Step 2:
Use Sleuth Kit tools like:
 - mmls → Examine the partition layout.
 - fsstat → View file system details.
 - fls → Get file listing.
 - icat → Recover files using inode numbers.
### Step 3:
Interpret the output to understand:
 - Partition table layout
 - File system metadata (block size, creation time, etc.)
 - Deleted and allocated files
 - Inode-based file recovery

## PROGRAM:
Sleuth Kit Disk Analysis Commands
### Partition Analysis
```bash
mmls disk.dd
```
### File System Metadata
```bash
fsstat -o 2048 disk.dd
```
### File Listing
```bash
fls -o 2048 disk.dd
```
### File Recovery
```bash
icat -o 2048 disk.dd 4 > recovered_file.txt
```
- Recovers the file associated with inode 4.
## SAMPLE WORKFLOW (Windows)
```bash
# Step 1: View partitions
mmls disk.dd

# Step 2: View file system details
fsstat -f fat disk.dd

# Step 3: List files
fls -f fat disk.dd

# Step 4: Recover a file
istat -f fat -o 0 disk.dd 4
```
## OUTPUT:

### Creating a disk file

<img width="906" height="669" alt="VirtualBox_KaliLinux2024_17_08_2025_09_06_01" src="https://github.com/user-attachments/assets/3edd04cd-bbfc-4167-a50f-9d7f4a47e3be" />

### View partitions

<img width="328" height="63" alt="2-copy" src="https://github.com/user-attachments/assets/c94b344a-be58-4d59-8550-7f850b133d45" />

### View file system details

<img width="1920" height="757" alt="2" src="https://github.com/user-attachments/assets/20775dea-89ac-4c28-8521-c818708fb287" />

### List files

<img width="1920" height="663" alt="3" src="https://github.com/user-attachments/assets/3132416a-4ff0-4fc1-9ccd-7d38294dab61" />

### Recover a file

<img width="476" height="303" alt="4" src="https://github.com/user-attachments/assets/daeacd4c-6425-4f1f-924a-78b6530d7985" />


## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.
