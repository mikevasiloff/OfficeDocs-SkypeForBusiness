---
title: "Integration between Skype for Business Online and Exchange server"
ms.reviewer: cbland
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 09/06/2024
audience: ITPro
ms.topic: quickstart
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.custom:
  - has-azure-ad-ps-ref, azure-ad-ref-level-one-done
ms.collection: IT_Skype16
ms.assetid: ffe4c3ba-7bab-49f1-b229-5142a87f94e6
description: "Configuring OAuth authentication between Exchange on premises and Skype for Business Online enables the Skype for Business and Exchange Integration features described in Feature support."
---

# Configure Integration and OAuth between Skype for Business Online and Exchange Server 

Configuring integration between Exchange server and Skype for Business Online enables the Skype for Business and Exchange Integration features described in [Feature support](../../plan-your-deployment/integrate-with-exchange/integrate-with-exchange.md#feature_support).

This topic applies to integration with Exchange Server 2013 through 2019. Check the [Exchange Server Supportability Matrix](/exchange/plan-and-deploy/supportability-matrix#supported-versions-and-builds) to find out which versions of Exchange Server are in a supported state.

## What do you need to know before you begin?

- Estimated time to complete this task: 15 minutes

- You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the [Exchange and Shell infrastructure permissions](/exchange/exchange-and-shell-infrastructure-permissions-exchange-2013-help) topic.

- For information about keyboard shortcuts that may apply to the procedures in this topic, see [Keyboard shortcuts in the Exchange admin center]( https://go.microsoft.com/fwlink/p/?LinkId=746512).

- For information about compatibility, see [Skype for Business compatibility with Office apps](../../plan-your-deployment/clients-and-devices/compatibility-with-office.md).

## Configure integration between Exchange Server and O365

### Step 1: Configure OAuth authentication between Exchange Server and O365

Perform the steps in the following article:

[Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help)

### Step 2: Create a new Mail User account for the Skype for Business Online Partner Application

This step is done on the Exchange server. It creates a mail user and assign it the appropriate management role rights. This account is then be used in the next step.

Specify a verified domain for your Exchange organization. This domain should be the same domain used as the primary Simple Mail Transfer Protocol (SMTP) domain used for the on-premises Exchange accounts. This domain is referred as `<your Verified Domain>` in the following procedure. Also, the `<DomainControllerFQDN>` should be the fully qualified domain name (FQDN) of a domain controller.

```powershell
$user = New-MailUser -Name SfBOnline-ApplicationAccount -ExternalEmailAddress SfBOnline-ApplicationAccount@<your Verified Domain> -DomainController <DomainControllerFQDN>
```

This command hides the new mail user from address lists.

```powershell
Set-MailUser -Identity $user.Identity -HiddenFromAddressListsEnabled $True -DomainController <DomainControllerFQDN>
```
Create a new role based on UserApplication role
```powershell
New-ManagementRole -Name "TeamsApp" -Parent "UserApplication" -DomainController <DomainControllerFQDN>
```
 
Remove all cmdlets from the new role except [GetDelegate](/exchange/client-developer/web-service-reference/getdelegate), as this is the only command required by the scheduling (delegation) service.  

```powershell
Get-ManagementRoleEntry "TeamsApp\*" -DomainController <DomainControllerFQDN> | Where-Object { $_.Name -ne "GetDelegate" } | Remove-ManagementRoleEntry -DomainController <DomainControllerFQDN>
```
 
Assign TeamsApp role to this new account
```powershell
New-ManagementRoleAssignment -Role TeamsApp -User $user.Identity -DomainController <DomainControllerFQDN>
```

### Step 3: Create and enable a Partner Application for Skype for Business Online 

Create a new partner application and use the account you created. Run the following command in the Exchange PowerShell in your on-premises Exchange organization.

```powershell
New-PartnerApplication -Name SfBOnline -ApplicationIdentifier 00000004-0000-0ff1-ce00-000000000000 -Enabled $True -LinkedAccount $user.Identity
```

### Step 4: Export the on-premises authorization certificate

Run a PowerShell script to export the on-premises authorization certificate, which you will import to your Skype for Business Online organization in the next step.

Save the following text to a PowerShell script file named, for example, `ExportAuthCert.ps1`.

```powershell
$thumbprint = (Get-AuthConfig).CurrentCertificateThumbprint
if((Test-Path $env:SYSTEMDRIVE\OAuthConfig) -eq $false)
{
   New-Item -Path $env:SYSTEMDRIVE\OAuthConfig -Type Directory
}
Set-Location -Path $env:SYSTEMDRIVE\OAuthConfig
$oAuthCert = (dir Cert:\LocalMachine\My) | Where-Object {$_.Thumbprint -match $thumbprint}
$certType = [System.Security.Cryptography.X509Certificates.X509ContentType]::Cert
$certBytes = $oAuthCert.Export($certType)
$CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
[System.IO.File]::WriteAllBytes($CertFile, $certBytes)
```

In Exchange PowerShell in your on-premises Exchange organization, run the PowerShell script that you created. For example: `.\ExportAuthCert.ps1`

<a name='step-5-upload-the-on-premises-authorization-certificate-to-azure-active-directory-acs'></a>

### Step 5: Upload the on-premises authorization certificate to Microsoft Entra ACS

Next, use the Microsoft Graph PowerShell to upload the on-premises authorization certificate that you exported in the previous step to Microsoft Entra Access Control Services (ACS). If you don't have the module installed, open a Windows PowerShell window as an administrator and run the following command:

```powershell
Install-Module -Name Microsoft.Graph.Applications
```

1. Open a Windows PowerShell workspace that has the Microsoft Graph cmdlets installed. All commands in this step must run using the Windows PowerShell connected to Microsoft Graph console.

2. Save the following text to a PowerShell script file named, for example,  `UploadAuthCert.ps1`.

   ```powershell
   Connect-MgGraph -Scopes Application.ReadWrite.All

   $CertFile = "$env:SYSTEMDRIVE\OAuthConfig\OAuthCert.cer"
   $objFSO = New-Object -ComObject Scripting.FileSystemObject
   $CertFile = $objFSO.GetAbsolutePathName($CertFile)
   $cer = [System.Security.Cryptography.X509Certificates.X509Certificate2]::new($CertFile)
   $binCert = $cer.GetRawCertData()
   $credValue = [System.Convert]::ToBase64String($binCert)
   $ServiceName = "00000004-0000-0ff1-ce00-000000000000"
   Write-Host "[+] Trying to query the service principals for service: $ServiceName" -ForegroundColor Cyan
   $p = Get-MgServicePrincipal -Filter "AppId eq '$ServiceName'"
   Write-Host "[+] Trying to query the keyCredentials for service: $ServiceName" -ForegroundColor Cyan
   $servicePrincipalKeyInformation = Get-MgServicePrincipal -Filter "AppId eq '$ServiceName'" -Select "keyCredentials"

   $keyCredentialsLength = $servicePrincipalKeyInformation.KeyCredentials.Length
   if ($keyCredentialsLength -gt 0) {
      Write-Host "[+] $keyCredentialsLength existing key(s) found - we keep them if they have not expired" -ForegroundColor Cyan

   $newCertAlreadyExists = $false
      $servicePrincipalObj = New-Object -TypeName Microsoft.Graph.PowerShell.Models.MicrosoftGraphServicePrincipal
      $keyCredentialsArray = @()

   foreach ($cred in $servicePrincipalKeyInformation.KeyCredentials) {
         $thumbprint = [System.Convert]::ToBase64String($cred.CustomKeyIdentifier)

   Write-Host "[+] Processing existing key: $($cred.DisplayName) thumbprint: $thumbprint" -ForegroundColor Cyan

   if ($newCertAlreadyExists -ne $true) {
            $newCertAlreadyExists = ($cer.Thumbprint).Equals($thumbprint, [System.StringComparison]::OrdinalIgnoreCase)
         }

   if ($cred.EndDateTime -lt (Get-Date)) {
            Write-Host "[+] This key has expired on $($cred.EndDateTime) and will not be retained" -ForegroundColor Yellow
            continue
         }

   $keyCredential = New-Object -TypeName Microsoft.Graph.PowerShell.Models.MicrosoftGraphKeyCredential
         $keyCredential.Type = "AsymmetricX509Cert"
         $keyCredential.Usage = "Verify"
         $keyCredential.Key = $cred.Key

   $keyCredentialsArray += $keyCredential
      }

   if ($newCertAlreadyExists -eq $false) {
         Write-Host "[+] New key: $($cer.Subject) thumbprint: $($cer.Thumbprint) will be added" -ForegroundColor Cyan
         $keyCredential = New-Object -TypeName Microsoft.Graph.PowerShell.Models.MicrosoftGraphKeyCredential
         $keyCredential.Type = "AsymmetricX509Cert"
         $keyCredential.Usage = "Verify"
         $keyCredential.Key = [System.Text.Encoding]::ASCII.GetBytes($credValue)

   $keyCredentialsArray += $keyCredential

   $servicePrincipalObj.KeyCredentials = $keyCredentialsArray
         Update-MgServicePrincipal -ServicePrincipalId $p.Id -BodyParameter $servicePrincipalObj
      } else {
         Write-Host "[+] New key: $($cer.Subject) thumbprint: $($cer.Thumbprint) already exists and will not be uploaded again" -ForegroundColor Yellow
      }
   } else {
      $params = @{
         type = "AsymmetricX509Cert"
         usage = "Verify"
         key = [System.Text.Encoding]::ASCII.GetBytes($credValue)
      }

   Write-Host "[+] This is the first key which will be added to this service principal" -ForegroundColor Cyan
      Update-MgServicePrincipal -ServicePrincipalId $p.Id -KeyCredentials $params
   }
   ```

3. Run the PowerShell script that you created in the previous step. For example:  `.\UploadAuthCert.ps1`

4. After you start the script, a credentials dialog box is displayed. Enter the credentials for the tenant administrator account in your Microsoft Online Microsoft Entra organization. After running the script, leave the Windows PowerShell connected to Microsoft Graph session open. You will use the session to run a PowerShell script in the next step.

### Step 6: Verify that the Certificate was uploaded to the Skype for Business Service Principal
1. In the PowerShell connected to Microsoft Graph session, run the following

   ```powershell
   Get-MgServicePrincipal -Filter "AppId eq '00000004-0000-0ff1-ce00-000000000000'" -Select "keyCredentials" | Format-List *
   ```

2. Confirm you see a key listed with start date and end data that matches your Exchange OAuth certificate start and end dates

### Verify your success

Verify that the configuration is correct by verifying some of the features are working successfully. 

1. Confirm that Skype for Business users with Cloud Voicemail service, in an organization with a Hybrid Exchange Server configuration, can successfully change their voicemail greetings.

2. Confirm conversation history for mobile clients is visible in the Outlook Conversation History folder.

3. Confirm that archived chat messages are deposited in the user's on-premises mailbox in the Purges folder using [EWSEditor](/archive/blogs/webdav_101/where-to-get-ewseditor).

Alternately, look at your traffic. The traffic in an OAuth handshake is distinctive (and doesn't look like Basic authentication), particularly around realms, where you begin to see issuer traffic that looks like this: `00000004-0000-0ff1-ce00-000000000000@` (sometimes with a `/` before the `@` sign), in the tokens that are being passed. There isn't a username or password, which is the point of OAuth. But you will see  the `Office` issuer – in this case `4` is `Skype for Business – and the realm of your subscription`.

If you want to be sure you’re successfully using OAuth, make certain you know what to expect and know what the traffic should look like. So [here's what to expect](https://tools.ietf.org/html/draft-ietf-oauth-v2-23#page-34).

Here's an [example of setting one up](/archive/blogs/kaevans/updated-fiddler-oauth-inspector), but you can use any network tracing tool you like to undertake this process.

## Related topics

[Configure OAuth authentication between Exchange and Exchange Online organizations](/exchange/configure-oauth-authentication-between-exchange-and-exchange-online-organizations-exchange-2013-help)
