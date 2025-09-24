# Reviewing-Unallocated-Space-Extracting-Data-with-Tools-Digital-Investigation-Processes
## AIM:
To review unallocated space in a disk image, extract data using forensic tools, and understand the digital investigation process.
## REQUIREMENTS
- Autopsy or FTK Imager
- Sleuth Kit (TSK)
- Hex Editor (e.g., HxD)
- Operating System: Windows 10/11 or Linux (Kali preferred)
## ARCHITECTURE DIAGRAM
```mermaid
flowchart TD
    A[Disk Image / Physical Drive] --> B[Load into Autopsy or Sleuth Kit]
    B --> C[Identify Unallocated Space]
    C --> D[Scan for Data Signatures]
    D --> E[Carve and Recover Files]
    E --> F[Analyze Recovered Data]
    F --> G[Document Findings in Report]
```
## DESIGN STEPS:
### Step 1 (Acquire Evidence Image):
- Obtain the disk image in ```.dd``` or ```.E01``` format from a trusted forensic acquisition process.
- Verify hash values (MD5/SHA256) to maintain integrity.

### Step 2(Load Image into Forensic Tool):
- Open Autopsy or FTK Imager.
- Create a new case and add the evidence image.

### Step 3(Locate Unallocated Space):
- Navigate to the partition structure view.
- Identify sectors not assigned to any partition (unallocated).
### Step 4(Analyze & Carve Data):
- Use built-in data carving tools to search for file signatures (JPEG, DOCX, PDF, etc.).
- Preview carved files for relevance.
  
## PROGRAM:
| Step | Action                     | Tool Used                   | Output                       |
| ---- | -------------------------- | --------------------------- | ---------------------------- |
| 1    | Load disk image            | Autopsy / FTK Imager        | Partition & unallocated view |
| 2    | Identify unallocated space | Autopsy File System View    | Sector ranges                |
| 3    | Data carving               | Autopsy Data Carving Module | Recovered files              |
| 4    | Export evidence            | Autopsy Export Option       | File copies for analysis     |


## OUTPUT:

```
lsblk
```

<img width="864" height="301" alt="image" src="https://github.com/user-attachments/assets/b51ca3e7-5126-4db3-b6ba-4e5cd00fe184" />

```
sudo dd if=/dev/sda of=/home/kali/disk.img bs=512
```

<img width="946" height="254" alt="image" src="https://github.com/user-attachments/assets/7a473851-8323-48ae-a8af-e98ad91cbece" />

```
mmls ~/disk.img
```

<img width="1096" height="310" alt="image" src="https://github.com/user-attachments/assets/c8c20128-949f-46ac-bdd5-19a69e84b04b" />

```
sudo ls -lh disk.img
```

<img width="879" height="216" alt="image" src="https://github.com/user-attachments/assets/c5e59f73-84d6-4d6b-8d4f-a5e40db7d3c9" />


```
strings disk.img | less
```
<img width="1390" height="797" alt="image" src="https://github.com/user-attachments/assets/95226f66-52a7-4fd3-9bd9-43ff08b3c72d" />


## RESULT:
The unallocated space was successfully analyzed, data was extracted, and the digital investigation process was followed effectively.

