# Automated-SOC-Investigation-Report
Built a Python automation tool that generates a SOC investigation report containing IOC details, VirusTotal and AbuseIPDB findings, automated risk scoring, analyst assessment, and recommended disposition.
![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/52afcc97886dee6a3ba145c1ff163f8514102983/Automated-SOC-Investigation-Report/Screenshot%202026-08-31%20152454.png)
Add "from datetime import datetime" import near the top of main.py

![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/e69e4e91c798fed454dd908a91f8048a8797fb5b/Automated-SOC-Investigation-Report/Screenshot%202026-08-31%20153023.png)
Add the following function above the section where the script asks for the IOC.
![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/e7319085f83e9dcad9863415a4582b10385771aa/Screenshot%202026-08-31%20170123.png)



![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/164c12a361a94ccb0d2973c55e06c0cfc8d64276/Automated-SOC-Investigation-Report/Screenshot%202026-08-31%20153501.png)

Locate the following IP Address section in main.py:
![image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/c1540657dc38ccc97275e6f0e222dfedb49a661e/Screenshot%202026-08-31%20170524.png)

![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/60511cfd30e06169a60b5b95334652ec1494e0cd/Automated-SOC-Investigation-Report/Screenshot%202026-08-31%20153614.png)
    
Change it to this below

![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/9dbff1c29d1c5978b51ec572801a3534dc612265/Screenshot%202026-08-31%20170737.png)
    
![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/e56a6f30e77ec8de5a51cf675f95c22652691efc/Automated-SOC-Investigation-Report/Screenshot%202026-08-31%20153946.png)
![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/025cd38aa4245acc89adfc83b8a0eb5595849003/Automated-SOC-Investigation-Report/Screenshot%202026-08-31%20154012.png)

Open PowerShell and run:python main.py

When prompted, enter the test IOC: 8.8.8.8

The output should be similar to

    
SOC IOC Investigation Tool
--------------------------
IOC:  8.8.8.8
Type: IP Address

VirusTotal IP Results
---------------------
Malicious:  0
Suspicious: 0
Harmless:   53
Undetected: 38

IP Information
--------------
Country: US
Network: 8.8.8.0/24
ASN: 15169
Owner: Google LLC

AbuseIPDB Results
------------------
Abuse Confidence Score: 0%
Total Reports: 195
Country: US
ISP: Google LLC
Domain: google.com
Usage Type: Content Delivery Network

SOC Risk Assessment
-------------------
Risk Level: LOW

SOC Investigation Report
------------------------
Report saved: reports/SOC_Report_8_8_8_8_2026-08-31_15-39-04.txt

Skills Demonstrated: Python • SOC Automation • VirusTotal API • AbuseIPDB API • Threat Intelligence • IOC Analysis • Risk Assessment • SOC Reporting
