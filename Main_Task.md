# 🔐 Vulnerability Assessment Report

**Tool Used**: Tenable Nessus Essentials  
**Scan Target**: 192.168.1.10 (Localhost)  
**Operating System**: Windows 11  
**Scan Duration**: 16 minutes  
**Date**: May 29, 2025

---

## 📊 Summary of Findings

| Severity      | Count |
|---------------|-------|
| 🟧 Medium      | 1     |
| 🟦 Info        | 29    |
| 🔴 High/Critical | 0     |

---

## 🚨 Most Critical Vulnerability

### SMB Signing Not Required
- **Severity**: Medium
- **CVSS Score**: 5.3
- **Description**:  
  This host allows SMB communication without signing, making it vulnerable to **man-in-the-middle (MITM)** attacks.
- **Remediation Steps**:
  1. Open `gpedit.msc`
  2. Navigate to:
     ```
     Computer Configuration → Windows Settings → Security Settings → Local Policies → Security Options
     ```
  3. Set the following to **Enabled**:
     - `Microsoft network client: Digitally sign communications (always)`
     - `Microsoft network server: Digitally sign communications (always)`

---

## 🧠 Informational Vulnerabilities (Selected)

| Vulnerability Name                     | Count | Category          |
|----------------------------------------|-------|-------------------|
| Netstat Portscanner (SSH)              | 42    | Port Scanners     |
| DCE Services Enumeration               | 8     | Windows           |
| SSL / TLS / HTTP (Multiple Issues)     | 10+   | Network Services  |
| Service Detection                      | 5     | General           |
| OS Fingerprints / Patch Report / CPE   | 1 each| General           |

> These do not pose an immediate threat but increase the visibility of the system and should be reviewed during hardening.

---

## 🛠 Suggested Fixes & Hardening Steps

- ✅ **Close unused ports** using `netstat -an` and your firewall.
- ✅ **Update Windows** and install all security patches.
- ✅ **Disable insecure services** like UPnP, NetBIOS, DCE RPC if not in use.
- ✅ **Enforce TLS 1.2 or 1.3** and disable deprecated SSL versions.
- ✅ **Restrict SMB access** to trusted IPs or subnets only.

---

## 📷 Scan Evidence

> Screenshots of Nessus Essentials results (May 29, 2025):

![Screenshot 2025-05-30 151808](https://github.com/user-attachments/assets/ce6bdfd3-408c-4a90-afc1-709c09121914)
  
*Overview with SMB Signing vulnerability*

![Screenshot 2025-05-30 151816](https://github.com/user-attachments/assets/40b0a6cb-9c42-45ce-8288-41e433ab63c1)

*List of informational vulnerabilities*

![Screenshot 2025-05-30 151823](https://github.com/user-attachments/assets/ced89d47-c5a2-4182-a2d0-8dacdcdf0c86)
  
*Additional informational vulnerabilities*

---

## ✅ Conclusion

While **no critical or high vulnerabilities** were found, **SMB Signing** should be enabled to prevent MITM attacks. All informational findings should be reviewed for service hardening and attack surface reduction.

---

> 📁 _Report by Dhruv Sabloak | Scan Date: May 29, 2025_
