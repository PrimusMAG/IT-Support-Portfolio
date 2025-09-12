# Defensive Phase (Blue Team - Defensive Security Framework)

## Stage 1: Preparation (Hardening)
**Objective: To proactively secure the system.**
- Deploy a Web Application Firewall (WAF):
- Install Nginx & ModSecurity (on the Ubuntu server):
- sudo apt update && sudo apt install nginx libmodsecurity3 modsecurity-crs -y
- Configure Nginx as a Reverse Proxy: Edit /etc/nginx/sites-available/default to forward traffic from port 80 to the app on port 4000 and enable ModSecurity.
- Enable Blocking Mode: In /etc/modsecurity/modsecurity.conf, change SecRuleEngine DetectionOnly to SecRuleEngine On.

## Stage 2 & 3: Detection & Analysis
**Objective: To monitor logs to detect and analyze attacks.**
- Implement Centralized Logging: Install an agent like Filebeat to ship Nginx and application logs to a SIEM platform.
- Analyze Logs: In the SIEM, the Blue Team would analyze logs for patterns:
- IDOR: Look for a single IP accessing many sequential /allocations/ IDs.
- Common Web Attacks: ModSecurity logs will show blocked NoSQL/XSS attempts.

## Stage 4: Containment
**Objective: To isolate the attacker.**
- Block Attacker IP: Upon detecting an attack, immediately block the malicious IP at the firewall.
- sudo ufw insert 1 deny from <KALI_IP>

## Stage 5: Eradication
**Objective: To fix the root cause of the vulnerabilities.**
- IDOR Code Fix: Developers must modify the /allocations/:id endpoint to check if the session's user_id matches the owner of the requested allocation id. If not, deny access.
- CSRF Code Fix: Implement the Synchronizer Token Pattern. Generate a unique, random anti-CSRF token per session, embed it in forms, and validate it on the server upon submission.
- Vulnerable Components Fix: Run npm audit fix and manually update remaining outdated libraries in package.json to the latest stable versions.

## Stage 6 & 7: Recovery & Lessons Learned
**Objective: To return to normal operations and improve security going forward.**
- Deploy Patched Code: Release the fixed version of the application.
- Re-test: The pentester must verify that all vulnerabilities have been closed.
- Lessons Learned: Document the incident. Update policies to mandate security code reviews and automated dependency scanning in the development pipeline.
