# Java Thick Client VAPT Example

This document outlines a practical approach to performing Vulnerability Assessment and Penetration Testing (VAPT) on a **Java-based thick client** application.

---

## Target Overview

**Application:** `AppClient.jar`  
**Platform:** Java SE Desktop  
**Functionality:** Login, data management, and file transfer  
**Communication:** HTTP(S) with backend APIs

---

## Testing Steps

### 1. Information Gathering

- **Identify technologies:**
  file AppClient.jar
  Output: `Zip archive data (JAR file)`

* **List JAR contents:**
  unzip -l AppClient.jar

---

### 2. Static Analysis (Decompilation)

* **Decompile using CFR:**
  java -jar cfr.jar AppClient.jar --outputdir src/

* **Look for:**
  * Hardcoded credentials
  * API keys or secrets
  * Backend URLs
  * Encryption routines
  * Authentication logic

* **Example Finding:**
  String apiKey = "12345-ABCDE";
  String apiUrl = "https://api.internal.company.com/v1";
  
---

### 3. Traffic Interception

* **Configure system to route traffic through Burp Suite or Fiddler.**

* **Bypass SSL validation (if applicable):**

  * Patch Java code to trust all certs
  * Or import Burp's CA certificate into the JVM:

    keytool -import -trustcacerts -keystore cacerts \
      -storepass changeit -noprompt -alias burp \
      -file burp.der
   
* **Intercept and analyze:**

  * Check if login, session, file transfer use HTTPS
  * Look for insecure tokens, IDs, parameters

---

### 4. Authentication Testing

* **Test for:**

  * Token replay or reuse
  * Session fixation/hijacking
  * Authorization bypass (e.g., user ID tampering)

* **Example:**
  Modify `userId=123` → `userId=124` and check response access to other users' data.

---

### 5. Local Storage Inspection

* **Search user/system directories for sensitive files:**

  * `%AppData%`, `~/.appname/`, local install folder

* **Look for:**

  * `.config`, `.ini`, `.log`, `.xml`, `.sqlite` files

* **Example Finding:**

  ```xml
  <db_username>admin</db_username>
  <db_password>password123</db_password>
  ```

---

### 6. Dynamic Analysis

* **Run with Java debugger:**
 jdb -jar AppClient.jar
 
* **Use tools:**

  * `JVisualVM`, `JConsole`, or `Process Explorer`

* **Modify logic or observe behavior:**

  * Patch `.class` files
  * Hook or override Java methods
  * Inject logging for key functionality

---

### 7. Exploit Development (Optional)

* **Proof of Concepts:**

  * Modify logic to bypass login
  * Auto-authenticate using static token
  * Exfiltrate sensitive files or requests

---

## Sample Findings

| ID  | Title                  | Severity | Description                                         |
| --- | ---------------------- | -------- | --------------------------------------------------- |
| 001 | Hardcoded API Key      | High     | API key found in `.class` files after decompilation |
| 002 | Insecure Local Storage | Medium   | Plaintext credentials found in `config.xml`         |
| 003 | No SSL Pinning         | Medium   | Allowed traffic interception via MITM               |

---

##  Tools Used

| Category             | Tools                          |
| -------------------- | ------------------------------ |
| Decompilers          | CFR, JD-GUI, Fernflower        |
| Traffic Interception | Burp Suite, Fiddler, Wireshark |
| Debugging            | JDB, JVisualVM, JConsole       |
| Static Analysis      | Ghidra, jadx                   |
| Local Inspection     | ProcMon, grep, strings         |

---

## Disclaimer

This document is for **authorized security testing and educational purposes only**. Do not use the described techniques on systems without explicit permission.

---
