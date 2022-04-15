---
title: Firewall i Microsoft Defender til virksomheder
description: Få mere at vide om Windows Defender Firewall i Microsoft Defender til virksomheder, herunder konfigurationsindstillinger
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 77c2042ace89a133b9be8995ef817c1fe3766a07
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861394"
---
# <a name="firewall-in-microsoft-defender-for-business"></a>Firewall i Microsoft Defender til virksomheder

> [!NOTE]
> Microsoft Defender til virksomheder er nu inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md). 

Microsoft Defender til virksomheder indeholder firewallfunktioner med [Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Firewallbeskyttelse hjælper med at sikre enheder med regler, der bestemmer, hvilken netværkstrafik der må komme ind eller flyde fra enheder. 

Du kan bruge firewallbeskyttelse til at angive, om du vil tillade eller blokere forbindelser på enheder på forskellige placeringer. Dine firewallindstillinger kan f.eks. tillade indgående forbindelser på enheder, der er tilsluttet virksomhedens interne netværk, men forhindre disse forbindelser, når enheden er på et netværk med enheder, der ikke er tillid til.

**I denne artikel beskrives**:

- [Standardindstillinger for firewall i Defender for Business](#default-firewall-settings-in-defender-for-business)
- [Firewallindstillinger, du kan konfigurere i Defender for Business](#firewall-settings-you-can-configure-in-defender-for-business)

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

## <a name="default-firewall-settings-in-defender-for-business"></a>Standardindstillinger for firewall i Defender for Business

Microsoft Defender til virksomheder indeholder standardfirewallpolitikker og -indstillinger, der hjælper med at beskytte virksomhedens enheder fra dag 1. Så snart din virksomheds enheder er onboardet til Microsoft Defender til virksomheder, fungerer din standardfirewallpolitik på følgende måde:

- Udgående forbindelser fra enheder er som standard tilladt, uanset placering.
- Når enheder er tilsluttet virksomhedens netværk, blokeres alle indgående forbindelser som standard.
- Når enheder er tilsluttet et offentligt netværk eller et privat netværk, blokeres alle indgående forbindelser som standard.

I Microsoft Defender til virksomheder kan du definere undtagelser for at blokere eller tillade indgående forbindelser. Du definerer disse undtagelser ved at oprette brugerdefinerede regler. Se [Administrer brugerdefinerede regler for firewallpolitikker](mdb-custom-rules-firewall.md).

## <a name="firewall-settings-you-can-configure-in-defender-for-business"></a>Firewallindstillinger, du kan konfigurere i Defender for Business

Microsoft Defender til virksomheder omfatter firewallbeskyttelse via Windows Defender Firewall. I følgende tabel vises de indstillinger, der kan konfigureres til firewallbeskyttelse i Microsoft Defender til virksomheder.

| Indstilling | Beskrivelse |
|--|--|
| **Domænenetværk** | Domænenetværksprofilen gælder for virksomhedens netværk. Firewallindstillinger for dit domænenetværk gælder for indgående forbindelser, der startes på andre enheder, der er på det samme netværk. Indgående forbindelser er som standard angivet til **Bloker alle**.  |
| **Offentligt netværk** | Den offentlige netværksprofil gælder for et netværk, som du kan bruge på et offentligt sted, f.eks. en café eller en lufthavn. Firewallindstillinger for offentlige netværk gælder for indgående forbindelser, der startes på andre enheder, der er på det samme netværk. Da et offentligt netværk kan omfatte enheder, som du ikke kender eller ikke har tillid til, er indgående forbindelser som standard angivet til **Bloker alle** .  |
| **Privat netværk** | Profilen for det private netværk gælder for et netværk på en privat placering, f.eks. dit hjem. Firewallindstillinger for private netværk gælder for indgående forbindelser, der startes på andre enheder, der er på det samme netværk. Generelt antages det på et privat netværk, at alle andre enheder på det samme netværk er pålidelige enheder. Indgående forbindelser er dog som standard angivet til **Bloker alle**. |
| **Brugerdefinerede regler** | [Med brugerdefinerede regler](mdb-custom-rules-firewall.md) kan du blokere eller tillade bestemte forbindelser. Lad os f.eks. antage, at du vil blokere alle indgående forbindelser på enheder, der er forbundet til et privat netværk, undtagen forbindelser via en bestemt app på en enhed. I dette tilfælde skal du angive **Privat netværk** til at blokere alle indgående forbindelser og derefter tilføje en brugerdefineret regel for at definere undtagelsen. <br/><br/>Du kan bruge brugerdefinerede regler til at definere undtagelser for bestemte filer eller apps, en IP-adresse (Internet Protocol) eller en række IP-adresser. <br/><br/>Afhængigt af den type brugerdefineret regel, du opretter, er her nogle eksempelværdier, du kan bruge: <br/><br/>Sti til programfil: `C:\Windows\System\Notepad.exe or %WINDIR%\Notepad.exe` <br/><br/>IP: En gyldig IPv4/IPv6-adresse, f.eks `192.168.11.0` . eller `192.168.1.0/24` <br/><br/>IP: Et gyldigt IPv4/IPv6-adresseområde, formateret som `192.168.1.0-192.168.1.9` (uden mellemrum inkluderet) |

## <a name="next-steps"></a>Næste trin

- [Administrer firewallindstillinger i Microsoft Defender til virksomheder](mdb-custom-rules-firewall.md)
- [Mer informasjon om Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)
- [Få vist og administrer hændelser i Microsoft Defender til virksomheder](mdb-view-manage-incidents.md)
- [Reagere på og afhjælpe trusler i Microsoft Defender til virksomheder](mdb-respond-mitigate-threats.md)
- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)