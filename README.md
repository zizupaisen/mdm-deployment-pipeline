# MDM Deployment Pipeline

MDM project: Apply policies, compliance, push software, lock devices, automation scripts.

## Tools
- Microsoft Intune (recommended)
- PowerShell + Python

## Project Structure
- policies/compliance.json
- scripts/deploy-apps.ps1
- scripts/lock-device.py
- pipeline/deployment-pipeline.md

## Policies (policies/compliance.json)
```json
{
  "osVersion": "Windows 11 24H2",
  "encryption": true,
  "antivirus": true,
  "jailbreak": false
}

Scripts (scripts/deploy-apps.ps1)
PowerShell# Deploy apps via Intune
Connect-MgGraph
New-IntuneMobileApp -FilePath "app.pkg"
Write-Output "Apps pushed successfully"

Scripts (scripts/lock-device.py)
Pythonimport requests

def lock_device(device_id, token):
    url = f"https://api.intune.com/devices/{device_id}/lock"
    headers = {"Authorization": f"Bearer {token}"}
    requests.post(url, headers=headers)
    print("Device locked")

Deployment Pipeline

Create Microsoft Intune tenant
Import policies/compliance.json
Run deploy-apps.ps1 to push software
Apply compliance rules
Use lock-device.py for remote lock
Monitor & enforce

Setup

Clone this repo
Set up Intune
Run scripts as needed