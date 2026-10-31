# SSH-Brute-Force-Incident-Detection-Perimeter-Defense

A SOC incident response study analyzing a common enterprise SSH brute-force vector: detecting unauthorized access attempts via system logs and executing immediate perimeter block via UFW firewall rules.

---

### 1. Incident Detection
A high volume of failed SSH authentication attempts was detected from an unauthorized IP address (`192.168.1.150`).

* **Description:** Monitored system and journal logs to isolate unauthorized access vectors targeting port 22.
* **Evidence:**
<img width="926" height="444" alt="image" src="https://github.com/user-attachments/assets/31c9da1a-0459-4846-9319-19fce70f951e" />
---

### 2. Containment & Remediation (Action)
To neutralize the threat and protect the system against automated credential-stuffing scripts, the perimeter firewall was configured and enabled.

* **Commands Executed:**
  ```bash
  sudo ufw enable
  sudo ufw deny from 192.168.1.150 to any
  sudo ufw limit 22/tcp
Evidence:
<img width="928" height="736" alt="image" src="https://github.com/user-attachments/assets/36eb76a4-8d25-4b51-be5b-9f650f202aa2" />

3. Verification & Result
Validated the firewall rules and performed a local socket audit to confirm that incoming traffic from the offending host is successfully dropped and the SSH service remains properly bound and secured.

Security Audit Command:

Bash
sudo ss -tunlp | grep ssh
Outcome: The malicious IP address is permanently blocked at the perimeter layer, and the local socket audit verifies that the SSH daemon is operating securely under the new network constraints.

Evidence:
<img width="923" height="733" alt="image" src="https://github.com/user-attachments/assets/9c8b7659-bfa7-4144-922f-030165b47335" />
