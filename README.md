

# MS-Compliance-Search-Powershell

## Open Powershell console and start using these command one by one:

### Install ExchangeOnlineManagement module
```Install-Module -Name ExchangeOnlineManagement```

### Use ExchangeOnlineManagement module
```Import-Module ExchangeOnlineManagement```

### Connect to Sec & Compliance Powershell
```Connect-IPPSSession -CertificateFilePath "C:\cert.pfx" -CertificatePassword (Get-Credential).password -AppID "xxxxxxx-xxx-xxxx-xxxx-xxxxxxxxx" -Organization “something.com”```

This command will ask for username and password, but the username is not important, you can put anything. Password is the private key password to decrypt the certificate.

### Create compliance search
```New-ComplianceSearch -name "suspicious emails" -ExchangeLocation all -ContentMatchQuery 'subject:"suspicious"'```

Example:
```
New-ComplianceSearch -name "suspicious emails" -ExchangeLocation all -ContentMatchQuery 'subject:"suspicious"' 

Name              RunBy JobEndTime Status                                                                                                   ----              ----- ---------- ------                                                                                                   suspicious emails                  NotStarted
```

### Verify whether it is there
```Get-ComplianceSearch```

Example:
```
Get-ComplianceSearch

Name              RunBy JobEndTime           Status
----              ----- ----------           ------
example1          User1 6/12/2022 1:14:00 am Completed
test02                                       NotStarted
test002                                      NotStarted
**suspicious emails                            NotStarted**
```

### Disconnect the session
```Disconnect-ExchangeOnline -Confirm:$false -WarningAction:SilentlyContinue```

