---
title: Firewall i Microsoft Defender for Business
description: Få mere at Windows Defender om Firewall i Microsoft Defender for Business, herunder konfigurationsindstillinger
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 92db1711fa5aefb8920c35a8665cf322b3f0f5ef
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63606801"
---
# <a name="firewall-in-microsoft-defender-for-business"></a>Firewall i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

Microsoft Defender for Business omfatter firewall-funktioner med [Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Firewallbeskyttelse hjælper med at sikre enheder med regler, der bestemmer, hvilken netværkstrafik der har tilladelse til at indtaste eller flyde fra enheder. 

Du kan bruge firewallbeskyttelse til at angive, om du vil tillade eller blokere forbindelser på enheder på forskellige steder. Dine firewallindstillinger kan f.eks. tillade indgående forbindelser på enheder, der har forbindelse til virksomhedens interne netværk, men forhindre disse forbindelser, når enheden er på et netværk med enheder, der ikke er tillid til.

**I denne artikel beskrives følgende**:

- [Standardindstillinger for firewall i Defender for Business](#default-firewall-settings-in-defender-for-business)

- [Firewall-indstillinger, du kan konfigurere i Defender for Business](#firewall-settings-you-can-configure-in-defender-for-business)

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="default-firewall-settings-in-defender-for-business"></a>Standardindstillinger for firewall i Defender for Business

Microsoft Defender for Business omfatter standardfirewall-politikker og -indstillinger for at beskytte din virksomheds enheder fra dag ét. Så snart din virksomheds enheder er onboardet til Microsoft Defender for Business, fungerer din standardpolitik for firewall som følger:

- Udgående forbindelser fra enheder er som standard tilladt, uanset placering.
- Når enheder har forbindelse til virksomhedens netværk, blokeres alle indgående forbindelser som standard.
- Når enheder har forbindelse til et offentligt netværk eller et privat netværk, blokeres alle indgående forbindelser som standard.

I Microsoft Defender for Business kan du definere undtagelser for at blokere eller tillade indgående forbindelser. Du definerer disse undtagelser ved at oprette brugerdefinerede regler. Se [Administrer brugerdefinerede regler for firewallpolitikker](mdb-custom-rules-firewall.md).

## <a name="firewall-settings-you-can-configure-in-defender-for-business"></a>Firewall-indstillinger, du kan konfigurere i Defender for Business

Microsoft Defender for Business omfatter firewallbeskyttelse via Windows Defender Firewall. I følgende tabel vises de indstillinger, der kan konfigureres til firewallbeskyttelse i Microsoft Defender for Business. <br/><br/>

| Indstilling | Beskrivelse |
|--|--|
| **Domænenetværk** | Domænenetværksprofilen gælder for din virksomheds netværk. Firewallindstillinger for dit domænenetværk gælder for indgående forbindelser, der er startet på andre enheder, der er på det samme netværk. Som standard er indgående forbindelser indstillet til **Bloker alle**.  |
| **Offentligt netværk** | Profilen for det offentlige netværk gælder for et netværk, som du kan bruge på et offentligt sted, f.eks. en café eller en lufthavn. Firewallindstillinger for offentlige netværk gælder for indgående forbindelser, der er startet på andre enheder, der er på det samme netværk. Da et offentligt netværk kan omfatte enheder, du ikke kender eller ikke har tillid til, er indgående forbindelser indstillet til **Bloker alle** som standard.  |
| **Privat netværk** | Den private netværksprofil gælder for et netværk på en privat placering, f.eks. dit hjem. Firewallindstillinger for private netværk gælder for indgående forbindelser, der er startet på andre enheder, der er på det samme netværk. Generelt på et privat netværk antages det, at alle andre enheder på samme netværk er pålidelige enheder. Som standard er indgående forbindelser dog indstillet til **Bloker alle**. |
| **Brugerdefinerede regler** | [Brugerdefinerede](mdb-custom-rules-firewall.md) regler giver dig mulighed for at blokere eller tillade bestemte forbindelser. Antag f.eks., at du vil blokere alle indgående forbindelser på enheder, der har forbindelse til et privat netværk, med undtagelse af forbindelser via en bestemt app på en enhed. I dette tilfælde skal du indstille Privat **netværk** til at blokere alle indgående forbindelser og derefter tilføje en brugerdefineret regel for at definere undtagelsen. <br/><br/>Du kan bruge brugerdefinerede regler til at definere undtagelser for bestemte filer eller apps, en IP-adresse (Internet Protocol) eller et område af IP-adresser. <br/><br/>Afhængigt af den type brugerdefinerede regel, du opretter, er her nogle eksempler på værdier, du kan bruge: <br/><br/>Programfilsti: `C:\Windows\System\Notepad.exe or %WINDIR%\Notepad.exe` <br/><br/>IP: En gyldig IPv4/IPv6-adresse, f.eks. `192.168.1.0` eller `192.168.1.0/24` <br/><br/>IP: Et gyldigt IPv4/IPv6-adresseområde, der er formateret `192.168.1.0-192.168.1.9` som (uden mellemrum) |

## <a name="next-steps"></a>Næste trin

- [Administrer indstillinger for firewall i Microsoft Defender for Business](mdb-custom-rules-firewall.md)

- [Få mere at vide om Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)

- [Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [Re besvare og afhjælpe trusler i Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [Gennemse afhjælpningshandlinger i Handlingscenter](mdb-review-remediation-actions.md)