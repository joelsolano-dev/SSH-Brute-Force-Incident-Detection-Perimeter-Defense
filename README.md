# SSH-Brute-Force-Incident-Detection-Perimeter-Defense

A SOC incident response study analyzing a common enterprise SSH brute-force vector: detecting unauthorized access attempts via system logs and executing immediate perimeter block via UFW firewall rules.

---

### 1. Incident Detection
A high volume of failed SSH authentication attempts was detected from an unauthorized IP address (`192.168.1.150`).

* **Description:** Monitored system and journal logs to isolate unauthorized access vectors targeting port 22[cite: 3].
* **Evidence:**
<img width="931" height="659" alt="Captura de pantalla 2026-10-30 194121" src="https://github.com/user-attachments/assets/7d1c5427-195e-48cc-9c6c-815efc2781ca" />

---

### 2. Containment & Remediation (Action)
To neutralize the threat and protect the system against automated credential-stuffing scripts, the perimeter firewall was configured and enabled.

* **Commands Executed:**
  ```bash
  sudo ufw enable
  sudo ufw deny from 192.168.1.150 to any
  sudo ufw limit 22/tcp
  ---
* **Evidence:**
<img width="1720" height="954" alt="image" src="https://github.com/user-attachments/assets/e799f7ba-f2e8-446c-885c-6f17470f54c9" />

### 3. Verification & Result
Validated the firewall rules to confirm that incoming traffic from the offending host is successfully dropped.

* **Commands Used for Verification:**
  ```bash
  sudo ufw status verbose
* **Evidence:**
