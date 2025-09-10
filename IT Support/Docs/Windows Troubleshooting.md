# Windows Troubleshooting

## Case 1: DNS Resolution Failure
**Problem:**  
The system could not access websites, and pinging hostnames such as `google.com` failed.
![DNS Failed](../Screenshots/Step2/Windows/Skenario1/nslookup_google_error.png)

**Solution:**  
- Checked IP configuration with `ipconfig /all`.  
- Flushed DNS cache using `ipconfig /flushdns`.  
- Reconfigured DNS server to Google DNS (8.8.8.8 / 8.8.4.4).  
- Verified connectivity with `ping google.com`.  

**Outcome:**  
Hostname resolution was restored and internet connection returned to normal.  

![DNS Fixed](../Screenshots/Step2/Windows/Skenario1/nslookup_google_success.png)

---

## Case 2: Network Adapter Disabled
**Problem:**  
The PC could not connect to the network, with the network icon showing "No Internet".
![No Internet](../Screenshots/Step2/Windows/Skenario2/no_internet_connection.png)

**Solution:**  
- Checked adapter status in Device Manager.  
- Re-enabled the network driver. 
![Enable Driver](../Screenshots/Step2/Windows/Skenario2/enable_driver.png) 
- If faulty, reinstalled the driver from vendor.  
- Verified connectivity with `ping google.com`.  

**Outcome:**  
Internet connection was restored after re-enabling the adapter.  
![Internet Fixed](../Screenshots/Step2/Windows/Skenario2/ping_success.png)


