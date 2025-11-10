# Memory Forensics Investigation using Volatility 3 & FTK Imager

**Author:** Babar Omkar Sukhdev  
**College:** Modern College, Nanded  
**Type:** Academic Project  
**Domain:** Cybersecurity & Digital Forensics  

---

## 🎯 Objective
To acquire, analyze, and interpret volatile memory (RAM) data in order to detect evidence of compromise, running processes, network connections, and malicious activities that may not be visible on disk.

---

## 🧰 Tools Used
| Category | Tool | Purpose |
|-----------|------|----------|
| Memory Acquisition | **FTK Imager** | Captured system RAM as `.mem` file |
| Memory Analysis | **Volatility 3 (Python)** | Analyzed running processes, connections, and injections |
| Hash Verification | **certutil / sha256sum** | Verified memory dump integrity |
| Virtualization | **VirtualBox / VMware** | Isolated lab environment |
| OS Platforms | **Windows (Target)**, **Kali Linux (Analysis)** | For acquisition & analysis respectively |

---

## ⚙️ Project Workflow

### **Step 1 — Memory Acquisition**
- Used *FTK Imager* to capture the RAM of a running Windows VM.  
- Saved the dump as `memdump.mem` and recorded the destination path.

### **Step 2 — Hash Verification**
- Verified dump integrity using:
  ```bash
  certutil -hashfile memdump.mem SHA256

### **Step 3 — Transfer to Analysis Machine**

Moved .mem file to Kali Linux via shared folder or USB.

Verified the SHA256 hash again using: sha256sum memdump.mem

### **Step 4 - Memory Analysis (Volatility 3)**

Executed the following plugins:**
Command	Purpose
```bash
windows.info       	Identify OS details from the dump
windows.pstree	    List running processes in a tree view
windows.cmdline    	Show command-line arguments for each process
windows.netscan   	Enumerate open network connections
windows.malfind	    Detect hidden or injected malicious code
```
### **Projects Outputs**
```bash
ol_outputs/
├── 02_pstree.txt     # Process tree
├── 03_cmdline.txt    # Command lines
├── 05_netscan.txt    # Network connections
└── 04_malfind.txt    # Memory injection analysis

Report/
└── Memory_Forensics_Report_Template_BabarOmkar.docx
```
### **Findings**
->No suspicious processes or rogue network connections were found.
->All running executables belonged to legitimate Windows services.
->malfind plugin reported no injected or RWX memory regions.
✅ The analyzed system snapshot appeared clean and uncompromised.


### **Key Learnings**
->Performed full memory acquisition and verified forensic integrity.\
->Understood how to extract live system artifacts from volatile memory.
->Gained experience with Volatility 3, a widely used forensic framework.
->Learned to detect and analyze in-memory malware or anomalies.

### **Conclusion**
This project demonstrates a complete end-to-end memory forensic investigation, from acquisition to analysis and reporting.
It highlights the importance of volatile data in cybersecurity incident response and how forensic analysts can uncover live malware or traces of attacker activity using tools like Volatility 3.
