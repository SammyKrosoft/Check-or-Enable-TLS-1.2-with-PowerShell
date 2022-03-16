# Check-or-Enable-TLS-1.2-with-PowerShell

## Pasting Docs Microsoft article extract for future reference (link at the end)

- As of April 2020, the PowerShell Gallery only supports connections using TLS 1.2 or later. For more information, see [PowerShell Gallery TLS Support](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/).

  To check your current settings in the Microsoft .NET Framework, run the following command in Windows PowerShell:

  ```powershell
  [Net.ServicePointManager]::SecurityProtocol
  ```

And to list the available protocols on your local workstation, and on your local Powershell profile you're using (*NOTE that you might have different results whether you launched your PowerShell session using elevated prompt*):

```powershell
[enum]::GetNames([System.Net.SecurityProtocolType])
```

  As described in the PowerShell Gallery TLS Support article, to *temporarily* change the security protocol to TLS 1.2 to install the PowerShellGet or ExchangeOnlineManagement modules, run the following command in Windows PowerShell *before* you install the module:

  ```powershell
  [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12 
  ```

  To *permanently* enable strong cryptography in the Microsoft .NET Framework version 4.x or later, run one of the following commands based on your Windows architecture:

  - x64:

    ```powershell
    Set-ItemProperty -Path 'HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319' -Name 'SchUseStrongCrypto' -Type DWord -Value '1'
    ```

  - x86

    ```powershell
    Set-ItemProperty -Path 'HKLM:\SOFTWARE\Microsoft\.NETFramework\v4.0.30319' -Name 'SchUseStrongCrypto' -Type DWord -Value '1'
    ```

  For more information, see [SchUseStrongCrypto](https://docs.microsoft.com/en-us/dotnet/framework/network-programming/tls#schusestrongcrypto).
  
  >Source: [About the Exchange Online PowerShell V2 module](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online-powershell-v2?view=exchange-ps#troubleshoot-installing-the-exo-v2-module)


## How-To - List all available security protocols from Powershell


