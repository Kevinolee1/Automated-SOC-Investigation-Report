# Automated-SOC-Investigation-Report
Built a Python tool that automatically generates and saves a SOC investigation report containing IOC details, threat intelligence findings, risk level, analyst assessment, and recommended disposition.
![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/52afcc97886dee6a3ba145c1ff163f8514102983/Automated-SOC-Investigation-Report/Screenshot%202026-08-31%20152454.png)
Add "from datetime import datetime" import near the top of main.py

![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/e69e4e91c798fed454dd908a91f8048a8797fb5b/Automated-SOC-Investigation-Report/Screenshot%202026-08-31%20153023.png)
Add this function below above the section where you ask for the IOC

def generate_soc_report(
    ioc,
    ioc_type,
    vt_malicious,
    vt_suspicious,
    abuse_score,
    risk_level
):
    os.makedirs("reports", exist_ok=True)

    timestamp = datetime.now().strftime("%Y-%m-%d_%H-%M-%S")

    safe_ioc = ioc.replace(".", "_").replace(":", "_")

    filename = f"reports/SOC_Report_{safe_ioc}_{timestamp}.txt"

    if risk_level == "LOW":
        assessment = (
            "Threat intelligence results indicate a low-risk IOC. "
            "No significant malicious indicators were identified."
        )

    elif risk_level == "MEDIUM":
        assessment = (
            "Threat intelligence identified potentially suspicious activity. "
            "Additional investigation is recommended."
        )

    elif risk_level == "HIGH":
        assessment = (
            "Multiple threat intelligence indicators suggest malicious activity. "
            "Escalation and additional investigation are recommended."
        )

    else:
        assessment = (
            "Threat intelligence indicates a critical-risk IOC. "
            "Immediate escalation and incident response investigation are recommended."
        )

    report = f"""
SOC IOC INVESTIGATION REPORT
============================

Investigation Date: {datetime.now().strftime("%Y-%m-%d %H:%M:%S")}

IOC Information
---------------
IOC: {ioc}
IOC Type: {ioc_type}

VirusTotal Findings
-------------------
Malicious Detections: {vt_malicious}
Suspicious Detections: {vt_suspicious}

AbuseIPDB Findings
------------------
Abuse Confidence Score: {abuse_score}%

SOC Risk Assessment
-------------------
Risk Level: {risk_level}

Analyst Assessment
------------------
{assessment}

Disposition
-----------
Risk classification is based on project-defined automated scoring logic.
Results should be validated by a security analyst before taking response actions.
"""

    with open(filename, "w", encoding="utf-8") as file:
        file.write(report)

    print()
    print("SOC Investigation Report")
    print("------------------------")
    print(f"Report saved: {filename}")
![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/164c12a361a94ccb0d2973c55e06c0cfc8d64276/Automated-SOC-Investigation-Report/Screenshot%202026-08-31%20153501.png)

    Find this section 
    elif ioc_type == "IP Address":
    vt_malicious, vt_suspicious = investigate_ip(ioc)

    abuse_score = investigate_ip_abuseipdb(ioc)

    risk_level = calculate_risk(
        vt_malicious,
        vt_suspicious,
        abuse_score
    )

    print()
    print("SOC Risk Assessment")
    print("-------------------")
    print(f"Risk Level: {risk_level}")
![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/60511cfd30e06169a60b5b95334652ec1494e0cd/Automated-SOC-Investigation-Report/Screenshot%202026-08-31%20153614.png)
    Change it to this

    elif ioc_type == "IP Address":
    vt_malicious, vt_suspicious = investigate_ip(ioc)

    abuse_score = investigate_ip_abuseipdb(ioc)

    risk_level = calculate_risk(
        vt_malicious,
        vt_suspicious,
        abuse_score
    )

    print()
    print("SOC Risk Assessment")
    print("-------------------")
    print(f"Risk Level: {risk_level}")

    generate_soc_report(
        ioc,
        ioc_type,
        vt_malicious,
        vt_suspicious,
        abuse_score,
        risk_level
    )
![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/e56a6f30e77ec8de5a51cf675f95c22652691efc/Automated-SOC-Investigation-Report/Screenshot%202026-08-31%20153946.png)
![Image alt](https://github.com/Kevinolee1/Automated-SOC-Investigation-Report/blob/025cd38aa4245acc89adfc83b8a0eb5595849003/Automated-SOC-Investigation-Report/Screenshot%202026-08-31%20154012.png)

Go to Powershell to type python main.py and press enter
For enter IOC to investigate use 8.8.8.8
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
