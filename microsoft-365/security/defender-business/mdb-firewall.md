---
title: Firewall i Microsoft Defender til virksomheder
description: Få mere at vide om Windows Defender Firewall indstillinger i Defender for Business. Firewall kan hjælpe med at forhindre uønsket netværkstrafik, der flyder til virksomhedens enheder.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: ce3c3ec98d45341544d146f6e614c3df048b3d90
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/13/2022
ms.locfileid: "66772899"
---
# <a name="firewall-in-microsoft-defender-for-business"></a>Firewall i Microsoft Defender til virksomheder

Defender for Business indeholder firewallfunktioner via [Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security). Firewallbeskyttelse hjælper med at beskytte enheder ved at oprette regler, der bestemmer, hvilken netværkstrafik der må overføres til og fra enheder.

Du kan bruge firewallbeskyttelse til at angive, om du vil tillade eller blokere forbindelser på enheder på forskellige placeringer. Dine firewallindstillinger kan f.eks. tillade indgående forbindelser på enheder, der er tilsluttet virksomhedens interne netværk, men forhindre forbindelser, når enheden er på et netværk med enheder, der ikke er tillid til.

**I denne artikel beskrives**:

- [Standardindstillinger for firewall i Defender for Business](#default-firewall-settings-in-defender-for-business)
- [Firewallindstillinger, du kan konfigurere i Defender for Business](#firewall-settings-you-can-configure-in-defender-for-business)


## <a name="default-firewall-settings-in-defender-for-business"></a>Standardindstillinger for firewall i Defender for Business

Defender for Business indeholder standardfirewallpolitikker og -indstillinger, der hjælper med at beskytte virksomhedens enheder fra dag 1. Så snart din virksomheds enheder er onboardet til Defender for Business, fungerer din standardfirewallpolitik på følgende måde:

- Udgående forbindelser fra enheder er som standard tilladt, uanset placering.
- Når enheder er tilsluttet virksomhedens netværk, blokeres alle indgående forbindelser som standard.
- Når enheder er tilsluttet et offentligt netværk eller et privat netværk, blokeres alle indgående forbindelser som standard.

I Defender for Business kan du definere undtagelser for at blokere eller tillade indgående forbindelser. Du definerer disse undtagelser ved at oprette brugerdefinerede regler. Se [Administrer brugerdefinerede regler for firewallpolitikker](mdb-custom-rules-firewall.md).

## <a name="firewall-settings-you-can-configure-in-defender-for-business"></a>Firewallindstillinger, du kan konfigurere i Defender for Business

Defender for Business omfatter firewallbeskyttelse via Windows Defender Firewall. I følgende tabel vises de indstillinger, der kan konfigureres i Defender for Business.

| Indstilling | Beskrivelse |
|--|--|
| **Domænenetværk** | Domænenetværksprofilen gælder for virksomhedens netværk. Firewallindstillinger for dit domænenetværk gælder for indgående forbindelser, der startes på andre enheder på det samme netværk. Indgående forbindelser er som standard angivet til **Bloker alle**.  |
| **Offentligt netværk** | Den offentlige netværksprofil gælder for netværk, som du kan bruge på et offentligt sted, f.eks. en café eller lufthavn. Firewallindstillinger for offentlige netværk gælder for indgående forbindelser, der startes på andre enheder på det samme netværk. Da et offentligt netværk kan indeholde enheder, som du ikke kender eller ikke har tillid til, er indgående forbindelser som standard angivet til **Bloker alle** .  |
| **Privat netværk** | Den private netværksprofil gælder for netværk på en privat placering, f.eks. dit hjem. Firewallindstillinger for private netværk gælder for indgående forbindelser, der startes på andre enheder på det samme netværk. Generelt antages det på et privat netværk, at alle andre enheder på det samme netværk er pålidelige enheder. Indgående forbindelser er dog som standard angivet til **Bloker alle**. |
| **Brugerdefinerede regler** | [Med brugerdefinerede regler](mdb-custom-rules-firewall.md) kan du blokere eller tillade bestemte forbindelser. Lad os f.eks. antage, at du vil blokere alle indgående forbindelser på enheder, der er forbundet til et privat netværk med undtagelse af forbindelser via en bestemt app på en enhed. I dette tilfælde ville du angive **Privat netværk** til at blokere alle indgående forbindelser og derefter tilføje en brugerdefineret regel for at definere undtagelsen. <p>Du kan bruge brugerdefinerede regler til at definere undtagelser for bestemte filer eller apps, en IP-adresse (Internet Protocol) eller en række IP-adresser. Afhængigt af den type brugerdefineret regel, du opretter, er her nogle eksempler på værdier, du kan bruge:<ul><li>Sti til programfil: `C:\Windows\System\Notepad.exe or %WINDIR%\Notepad.exe`</li><li>IP: En gyldig IPv4/IPv6-adresse, f.eks `192.168.11.0` . eller `192.168.1.0/24`</li><li>IP: Et gyldigt IPv4/IPv6-adresseområde, formateret som `192.168.1.0-192.168.1.9` (uden mellemrum inkluderet)</li></ul> |

## <a name="next-steps"></a>Næste trin

- [Administrer firewallindstillinger i Defender for Business](mdb-custom-rules-firewall.md)
- [Få mere at vide om Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)
- [Få vist og administrer hændelser i Defender for Business](mdb-view-manage-incidents.md)
- [Reager på og afhjælp trusler i Defender for Business](mdb-respond-mitigate-threats.md)
- [Gennemse afhjælpningshandlinger i Løsningscenter](mdb-review-remediation-actions.md)