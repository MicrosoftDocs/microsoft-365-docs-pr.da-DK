---
title: Brug netværksbeskyttelse til at forhindre forbindelser til dårlige websteder
description: Beskyt dit netværk ved at forhindre brugere i at få adgang til kendte skadelige og mistænkelige netværksadresser
keywords: Netværksbeskyttelse, udnyttelse, skadeligt websted, ip, domæne, domæner
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: overview
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: ''
ms.openlocfilehash: 7b9443cac6543ac14f6d94bd2809b5263be0a860
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681826"
---
# <a name="protect-your-network"></a>Beskyt dit netværk

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>Oversigt over netværksbeskyttelse

Netværksbeskyttelse hjælper med at beskytte enheder mod internetbaserede hændelser. Netværksbeskyttelse er en reduktion af angrebsoverfladen. Det er med til at forhindre medarbejdere i at få adgang til skadelige domæner via programmer. Domæner, der hoster forsøg på phishing, udnyttelse og andet skadeligt indhold på internettet, betragtes som skadelige. Netværksbeskyttelse udvider omfanget af [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) til at blokere al udgående HTTP(s) trafik, der forsøger at oprette forbindelse til kilder med dårligt ry (baseret på domænet eller værtsnavnet).

Netværksbeskyttelse udvider beskyttelsen i [webbeskyttelse](web-protection-overview.md) til operativsystemniveau. Det giver funktionalitet til webbeskyttelse i Microsoft Edge til andre understøttede browsere og ikke-browserprogrammer. Derudover giver netværksbeskyttelse synlighed og blokering af indikatorer for kompromis (IOCs), når de bruges med [registrering og svar af slutpunkter](overview-endpoint-detection-response.md). Netværksbeskyttelse fungerer f.eks. med dine [brugerdefinerede](manage-indicators.md) indikatorer, som du kan bruge til at blokere bestemte domæner eller værtsnavne.

> [!TIP]
> Se webstedet microsoft Defender for Endpoint testground på demo.wd.microsoft.com [for](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) at se, hvordan netværksbeskyttelse fungerer.

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

## <a name="requirements-for-network-protection"></a>Krav til netværksbeskyttelse

Netværksbeskyttelse kræver Windows 10 Pro eller Enterprise og Microsoft Defender Antivirus beskyttelse i realtid.

<br>

****

|Windows version|Microsoft Defender Antivirus|
|---|---|
|Windows 10 version 1709 eller nyere <p> Windows 11 <p> Windows Server 1803 eller nyere|[Microsoft Defender Antivirus beskyttelse i realtid og](configure-real-time-protection-microsoft-defender-antivirus.md) [beskyttelse, der leveres i skyen](enable-cloud-protection-microsoft-defender-antivirus.md), skal være aktiveret|
|

Når du har aktiveret tjenesterne, skal du muligvis konfigurere dit netværk eller din firewall til at tillade forbindelser mellem tjenesterne og dine enheder (også kaldet slutpunkter).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="configuring-network-protection"></a>Konfiguration af netværksbeskyttelse

Du kan finde flere oplysninger om, hvordan du aktiverer netværksbeskyttelse, **[under Aktivér netværksbeskyttelse](enable-network-protection.md)**. Brug Gruppepolitik, PowerShell eller MDM-CSP'er til at aktivere og administrere netværksbeskyttelse i dit netværk.

## <a name="viewing-network-protection-events"></a>Visning af netværksbeskyttelseshændelser

Netværksbeskyttelse fungerer bedst med [Microsoft Defender til slutpunkt](microsoft-defender-endpoint.md), hvilket giver dig detaljeret rapportering om udnyttelse af beskyttelseshændelser og -blokke som en del af scenarier med [undersøgelse af beskeder](investigate-alerts.md).

Når netværksbeskyttelse blokerer en forbindelse, vises der en meddelelse fra Handlingscenter. Sikkerhedsteamet kan [tilpasse meddelelsen med](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) organisationens oplysninger og kontaktoplysninger. Desuden kan individuelle reduktionsregler for angrebsoverfladen aktiveres og tilpasses til visse teknikker til overvågning.

Du kan også bruge [overvågningstilstand til at](audit-windows-defender.md) evaluere, hvordan netværksbeskyttelse påvirker organisationen, hvis den er aktiveret.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>Gennemse hændelser for netværksbeskyttelse i Microsoft 365 Defender portalen

Microsoft Defender til Slutpunkt leverer detaljeret rapportering om hændelser og blokke som en del af scenarierne for [undersøgelsen af beskeder](investigate-alerts.md). Du kan få vist disse detaljer i Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i [beskedkøen eller](review-alerts.md) ved at bruge [avanceret jagt](advanced-hunting-overview.md). Hvis du bruger overvågningstilstand, [kan](audit-windows-defender.md) du bruge avanceret på jagt efter at se, hvordan indstillinger for netværksbeskyttelse vil påvirke dit miljø, hvis de blev aktiveret.

Her er en eksempelforespørgsel til avanceret jagt:

```kusto
DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Gennemse netværksbeskyttelseshændelser i Windows Event Viewer

Du kan gennemse hændelsesloggen Windows for at få vist hændelser, der oprettes, når netværksbeskyttelsesblokke (eller overvågninger) adgang til en ondsindet IP eller et ondsindet domæne:

1. [Kopiér XML direkte](event-views.md).

2. Vælg **OK**.

Denne procedure opretter en brugerdefineret visning, der filtrerer til kun at vise følgende hændelser relateret til netværksbeskyttelse:

<br>

****

|Hændelses-id|Beskrivelse|
|---|---|
|5007|Hændelse, når indstillingerne ændres|
|1125|Hændelse, når netværksbeskyttelse udløses i overvågningstilstand|
|1126|Hændelse, når netværksbeskyttelse udløses i bloktilstand|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>Netværksbeskyttelse og TCP trevejs-handshake

Med netværksbeskyttelse foretages bestemmelse af, om der skal tillades eller blokeres adgang til et websted efter fuldførelsen af [trevejs-handshake via TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip). Når et websted er blokeret af netværksbeskyttelse, `ConnectionSuccess` vises der derfor muligvis en handlingstype under i `NetworkConnectionEvents` Microsoft 365 Defender-portalen, selvom webstedet faktisk blev blokeret. `NetworkConnectionEvents` rapporteres fra TCP-laget og ikke fra netværksbeskyttelse. Når trevejs-handshake er udført, tillades eller blokeres adgang til webstedet af netværksbeskyttelse.

Her er et eksempel på, hvordan det fungerer:

1. Antag, at en bruger forsøger at få adgang til et websted på sin enhed. Webstedet hostes på et farligt domæne, og det bør være blokeret af netværksbeskyttelse.  

2. Trevejs-handshake via TCP/IP påbegyndes. Før den er fuldført, logføres `NetworkConnectionEvents` en handling, og den `ActionType` er angivet som `ConnectionSuccess`. Så snart trevejsprocessen er færdig, blokerer netværksbeskyttelse adgangen til webstedet. Alt dette sker meget hurtigt. En lignende proces sker med [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview). Det er her, trevejs-handshake fuldfører, at der foretages en bestemmelse, og at adgang til et websted enten er blokeret eller tilladt.

3. I Microsoft 365 Defender vises en besked i [beskedkøen](alerts-queue.md). Oplysningerne om beskeden omfatter både `NetworkConnectionEvents` og `AlertEvents`. Du kan se, at webstedet blev blokeret, selvom du også har et `NetworkConnectionEvents` element med ActionType af `ConnectionSuccess`.

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Overvejelser om Windows virtuelt skrivebord, der Windows 10 Enterprise en flersession

På grund af den mangebrugerbaserede Windows 10 Enterprise du huske på følgende punkter:

1. Netværksbeskyttelse er en funktion for hele enheden og kan ikke målrettes bestemte brugersessioner.

2. Politikker for filtrering af webindhold er også brede på enheder.

3. Hvis du har brug for at skelne mellem brugergrupper, kan du overveje at oprette separate Windows Virtual Desktop-værtsgrupper og tildelinger.

4. Test netværksbeskyttelse i overvågningstilstand for at vurdere dets funktionsmåde, før det rulles ud.

5. Overvej at ændre størrelsen på din installation, hvis du har et stort antal brugere eller et stort antal sessioner med flere brugere.

### <a name="alternative-option-for-network-protection"></a>Alternativ indstilling til netværksbeskyttelse

I Windows 10 Enterprise 1909 og frem, der bruges i Windows Virtual Desktop på Azure, kan netværksbeskyttelse af Microsoft Edge aktiveres ved hjælp af følgende metode:

1. Brug [Slå netværksbeskyttelse til,](enable-network-protection.md) og følg vejledningen for at anvende din politik.

2. Udfør følgende PowerShell-kommando: `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>Fejlfinding af netværksbeskyttelse

På grund af det miljø, hvor netværksbeskyttelse kører, kan Microsoft muligvis ikke registrere proxyindstillinger for operativsystemet. I nogle tilfælde kan netværkbeskyttelsesklienter ikke oprette forbindelse til skytjenesten. For at løse forbindelsesproblemet skal kunder med E5-licenser konfigurere en af følgende registreringsdatabasenøgler:

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="see-also"></a>Se også

- [Evaluer |](evaluate-network-protection.md) Påtager dig et hurtigt scenarie, der viser, hvordan funktionen fungerer, og hvilke hændelser der typisk vil blive oprettet.
- [Aktivér |](enable-network-protection.md) Brug Gruppepolitik, PowerShell eller MDM-CSP'er til at aktivere og administrere netværksbeskyttelse i dit netværk.
- [Konfiguration af reduktionsfunktioner til angrebsoverfladen i Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
