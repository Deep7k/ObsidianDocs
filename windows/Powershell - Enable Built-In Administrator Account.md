---
Author: Deepak N A
Date: 2024-06-23
---
## Introduction

This document provides step-by-step instructions on how to enable the built-in Administrator account on Windows using PowerShell. The Administrator account is typically disabled by default for security reasons.

## Prerequisites

- Access to a Windows machine with administrative privileges.
- Basic familiarity with PowerShell commands.
## Steps

### 1. Open PowerShell as Administrator

- Right-click on the **Start** menu and select **Windows PowerShell (Admin)**.
### 2. Check Current Status (Optional)

- Before enabling, you can check if the Administrator account is already enabled or disabled:
```powershell
Get-LocalUser -Name "Administrator"
```
If the account is enabled, the output will show `Enabled True`.
### 3. Enable the Administrator Account

   - To enable the Administrator account, use the following PowerShell command:
```powershell
Enable-LocalUser -Name "Administrator"
```
### 4. Verify the Status

- Verify that the Administrator account is now enabled by running:
```powershell
Get-LocalUser -Name "Administrator"
```
The output should show `Enabled True`.
### 5. Set a Password

- If the Administrator account does not have a password set (which is common if it was disabled), you can set one using:
```powershell
Set-LocalUser -Name "Administrator" -Password (ConvertTo-SecureString -AsPlainText "YourNewPassword" -Force)
```
Replace `"YourNewPassword"` with the desired password.

## Conclusion

You have successfully enabled the Administrator account on your Windows machine using PowerShell. Ensure to use this account responsibly, as it has elevated privileges.

## References

- [Microsoft Docs: Enable-LocalUser](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.localaccounts/enable-localuser)
- [Microsoft Docs: Set-LocalUser](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.localaccounts/set-localuser)

