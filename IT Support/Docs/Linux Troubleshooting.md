# Linux Troubleshooting (Ubuntu Server)

## Case 1: File Permission Denied
**Problem:**  
A user could not access a file, showing "Permission denied".
![Permission Denied](../Screenshots/Step2/Ubuntu/Skenario1/permission_denied.png)

**Solution:**  
- Checked file permissions using `ls -l`.
  ![File Permission](../Screenshots/Step2/Ubuntu/Skenario1/file_permission.png)
- Modified permissions with `chmod 644 <filename>`.  
- Verified access using `cat <filename>`.  

**Outcome:**  
The file became accessible again with proper permissions.  

![Permission Fixed](../Screenshots/Step2/Ubuntu/Skenario1/permission_fixed.png)

---

## Case 2: Web Service Down (Apache)
**Problem:**  
The hosted website was not accessible because the Apache service was stopped.

**Solution:**  
- Checked service status with `systemctl status apache2`.  
![Service Status](../Screenshots/Step2/Ubuntu/Skenario2/service_status.png)
- Inspected logs using `journalctl -u apache2`.  
![Inspect Logs](../Screenshots/Step2/Ubuntu/Skenario2/inspect_logs.png)
- Restarted service with `systemctl start apache2`.  
![Start Service](../Screenshots/Step2/Ubuntu/Skenario2/start_service.png)
- Verified configuration with `apache2ctl configtest`.  

**Outcome:**  
Apache service was restored, and the website became accessible.  

![Status Active](../Screenshots/Step2/Ubuntu/Skenario2/status_active.png)
