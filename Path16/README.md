### Notes on Wireshark

**Wireshark** is a widely-used network protocol analyzer that lets you capture and interactively browse the traffic running on a computer network. It is an essential tool for network administrators, security analysts, and penetration testers.

#### Key Features of Wireshark:
- **Live capture and offline analysis:** Capture network traffic in real-time or read previously captured traffic from a file.
- **Rich VoIP analysis:** Analyze voice-over-IP traffic.
- **Deep inspection of hundreds of protocols:** Support for a wide range of protocols.
- **Export:** Export data to XML, PostScript®, CSV, or plain text.

#### Installation:
- **Windows:** Download from [Wireshark's official website](https://www.wireshark.org/) and follow the installation wizard.
- **macOS:** Download from [Wireshark's official website](https://www.wireshark.org/) and drag the application to the Applications folder.
- **Linux:** Use the package manager of your distribution, e.g., `sudo apt-get install wireshark` for Debian-based systems.

#### Basic Usage:
1. **Start Capturing:**
   - Open Wireshark.
   - Select the network interface to capture from (usually Wi-Fi or Ethernet).
   - Click the shark fin icon to start capturing packets.

2. **Analyze Captured Data:**
   - Use filters to narrow down the data, e.g., `http` to see only HTTP traffic.
   - Inspect individual packets by selecting them in the top pane and viewing details in the bottom pane.

3. **Saving and Exporting:**
   - Save captures using `File > Save`.
   - Export specific packets or ranges using `File > Export Specified Packets`.

4. **Common Filters:**
   - `ip.src == 192.168.1.1` - Filter packets from a specific IP.
   - `tcp.port == 80` - Filter packets on a specific port.
   - `http` - Filter HTTP traffic.

### Notes on OWASP Top 10

The **OWASP Top 10** is a standard awareness document for developers and web application security. It represents a broad consensus about the most critical security risks to web applications.

#### OWASP Top 10 (2021 Edition):

1. **Broken Access Control:**
   - **Description:** Weaknesses that allow users to act outside of their intended permissions.
   - **Example:** Bypassing access controls to gain unauthorized access.

2. **Cryptographic Failures:**
   - **Description:** Issues related to cryptography that lead to sensitive data exposure.
   - **Example:** Using weak encryption algorithms.

3. **Injection:**
   - **Description:** Injection flaws, such as SQL, NoSQL, and LDAP injection, occur when untrusted data is sent to an interpreter.
   - **Example:** SQL injection allowing attackers to execute arbitrary SQL commands.

4. **Insecure Design:**
   - **Description:** Design flaws that cannot be mitigated by proper implementation.
   - **Example:** Lack of security controls in application design.

5. **Security Misconfiguration:**
   - **Description:** Incorrect or incomplete configuration of security settings.
   - **Example:** Default accounts and passwords still enabled and unchanged.

6. **Vulnerable and Outdated Components:**
   - **Description:** Using components with known vulnerabilities.
   - **Example:** Outdated libraries and frameworks.

7. **Identification and Authentication Failures:**
   - **Description:** Issues with authentication and session management.
   - **Example:** Weak password policies.

8. **Software and Data Integrity Failures:**
   - **Description:** Code and infrastructure are vulnerable to integrity violations.
   - **Example:** Applications that rely on libraries, plugins, or modules from untrusted sources.

9. **Security Logging and Monitoring Failures:**
   - **Description:** Inadequate logging and monitoring can lead to undetected breaches.
   - **Example:** Insufficient logging of critical activities.

10. **Server-Side Request Forgery (SSRF):**
    - **Description:** When a web application fetches a remote resource without validating the URL supplied by the user.
    - **Example:** An attacker forces the application to make requests to an unintended location.

#### Mitigation Strategies:
- **Access Control:** Implement strong access controls and regularly review permissions.
- **Cryptography:** Use strong, up-to-date cryptographic algorithms and properly manage keys.
- **Input Validation:** Validate all input from untrusted sources and use parameterized queries.
- **Secure Design:** Incorporate security principles into the design phase of development.
- **Configuration Management:** Regularly update and patch systems, and disable unnecessary features.
- **Component Management:** Monitor and update third-party components.
- **Authentication:** Implement multi-factor authentication and enforce strong password policies.
- **Integrity Checks:** Use checksums, digital signatures, and secure pipelines.
- **Logging and Monitoring:** Enable detailed logging and actively monitor for suspicious activities.
- **SSRF Prevention:** Validate and sanitize all user inputs that could be used to construct URLs.

By understanding and addressing the OWASP Top 10, organizations can significantly improve the security posture of their web applications.
