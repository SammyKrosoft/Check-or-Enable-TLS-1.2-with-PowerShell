---
title: About the Exchange Online PowerShell V2 module
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date:
ms.audience: Admin
audience: Admin
ms.topic: article
ms.service: exchange-powershell
ms.reviewer: navgupta
ms.localizationpriority: high
ms.collection: Strat_EX_Admin
ms.custom:
ms.assetid:
search.appverid: MET150
description: "Admins can learn about the installation, maintenance, and design of the Exchange Online PowerShell V2 module that they use to connect to all Exchange-related PowerShell environments in Microsoft 365."
---

# Check-or-Enable-TLS-1.2-with-PowerShell

## Pasting Docs Microsoft article extract for future reference

- As of April 2020, the PowerShell Gallery only supports connections using TLS 1.2 or later. For more information, see [PowerShell Gallery TLS Support](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/).

  To check your current settings in the Microsoft .NET Framework, run the following command in Windows PowerShell:

  ```powershell
  [Net.ServicePointManager]::SecurityProtocol
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

  For more information, see [SchUseStrongCrypto](/dotnet/framework/network-programming/tls#schusestrongcrypto).
  
  >Source: [About the Exchange Online PowerShell V2 module](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online-powershell-v2?view=exchange-ps#troubleshoot-installing-the-exo-v2-module)
