---
title: Brug netværksbeskyttelse til at forhindre forbindelser til forkerte websteder
description: Beskyt dit netværk ved at forhindre brugerne i at få adgang til kendte skadelige og mistænkelige netværksadresser
keywords: Netværksbeskyttelse, udnyttelser, skadeligt websted, ip, domæne, domæner
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
ms.openlocfilehash: f58c7afe9c6f532f7f6420d58bcd681778483680
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789332"
---
# <a name="protect-your-network"></a>Beskyt dit netværk

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platforme**
- Windows

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="overview-of-network-protection"></a>Oversigt over netværksbeskyttelse

Netværksbeskyttelse hjælper med at beskytte enheder mod internetbaserede hændelser. Netværksbeskyttelse er en funktionalitet til reduktion af angrebsoverfladen. Det hjælper med at forhindre medarbejdere i at få adgang til farlige domæner via programmer. Domæner, der hoster phishing-svindel, udnyttelser og andet skadeligt indhold på internettet, betragtes som farlige. Netværksbeskyttelse udvider omfanget af [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) for at blokere al udgående HTTP(er)-trafik, der forsøger at oprette forbindelse til kilder med lavt omdømme (baseret på domænet eller værtsnavnet).

Netværksbeskyttelse udvider beskyttelsen i [webbeskyttelse](web-protection-overview.md) til operativsystemets niveau. Den leverer webbeskyttelsesfunktioner i Edge til andre understøttede browsere og programmer, der ikke er browsere. Desuden giver netværksbeskyttelse synlighed og blokering af indikatorer for kompromitterende (IOCs), når de bruges sammen med [registrering og svar af slutpunkter](overview-endpoint-detection-response.md). Netværksbeskyttelse fungerer f.eks. med dine [brugerdefinerede indikatorer](manage-indicators.md) , som du kan bruge til at blokere bestemte domæner eller værtsnavne.

> [!TIP]
> Se Microsoft Defender for Endpoint testground site på [demo.wd.microsoft.com](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) for at se, hvordan netværksbeskyttelse fungerer.

> [!NOTE]
> Demowebstedet Defender for Endpoint på demo.wd.microsoft.com frarådes og fjernes fremover.

## <a name="requirements-for-network-protection"></a>Krav til netværksbeskyttelse

Netværksbeskyttelse kræver Windows 10 Pro eller Enterprise og Microsoft Defender Antivirus beskyttelse i realtid.

<br>

****

|Windows version|Microsoft Defender Antivirus|
|---|---|
|Windows 10 version 1709 eller nyere <p> Windows 11 <p> Windows Server 1803 eller nyere|[Microsoft Defender Antivirus beskyttelse i realtid](configure-real-time-protection-microsoft-defender-antivirus.md) og [skybaseret beskyttelse](enable-cloud-protection-microsoft-defender-antivirus.md) skal aktiveres|
|

Når du har aktiveret tjenesterne, skal du muligvis konfigurere netværket eller firewallen for at tillade forbindelser mellem tjenesterne og dine enheder (også kaldet slutpunkter).

- `.smartscreen.microsoft.com`
- `.smartscreen-prod.microsoft.com`

## <a name="configuring-network-protection"></a>Konfiguration af netværksbeskyttelse

Du kan få mere at vide om, hvordan du aktiverer netværksbeskyttelse, under **[Aktivér netværksbeskyttelse](enable-network-protection.md)**. Brug Gruppepolitik, PowerShell eller MDM-CSP'er til at aktivere og administrere netværksbeskyttelse på dit netværk.

## <a name="viewing-network-protection-events"></a>Visning af netværksbeskyttelseshændelser

Netværksbeskyttelse fungerer bedst sammen med [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md), hvilket giver dig detaljeret rapportering om hændelser og blokke for udnyttelse af beskyttelse som en del af [scenarier med undersøgelse af beskeder](investigate-alerts.md).

Når netværksbeskyttelse blokerer en forbindelse, vises der en meddelelse fra Løsningscenter. Dit team af sikkerhedshandlinger kan [tilpasse meddelelsen](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) med din organisations oplysninger og kontaktoplysninger. Derudover kan individuelle regler for reduktion af angrebsoverfladen aktiveres og tilpasses, så de passer til visse teknikker, der skal overvåges.

Du kan også bruge [overvågningstilstand](audit-windows-defender.md) til at evaluere, hvordan netværksbeskyttelse vil påvirke din organisation, hvis den er aktiveret.

## <a name="review-network-protection-events-in-the-microsoft-365-defender-portal"></a>Gennemse netværksbeskyttelseshændelser på Microsoft 365 Defender-portalen

Microsoft Defender for Endpoint giver detaljeret rapportering om hændelser og blokke som en del af [scenarierne til undersøgelse af advarsler](investigate-alerts.md). Du kan få vist disse oplysninger på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) i [beskedkøen](review-alerts.md) eller ved hjælp af [avanceret jagt](advanced-hunting-overview.md). Hvis du bruger [overvågningstilstand](audit-windows-defender.md), kan du bruge avanceret jagt til at se, hvordan indstillinger for netværksbeskyttelse vil påvirke dit miljø, hvis de er aktiveret.

Her er et eksempel på en forespørgsel om avanceret jagt:

```kusto
DeviceNetworkEvents
|where ActionType in ('ExploitGuardNetworkProtectionAudited','ExploitGuardNetworkProtectionBlocked', 'ConnectionSuccess')
```

## <a name="review-network-protection-events-in-windows-event-viewer"></a>Gennemse netværksbeskyttelseshændelser i Windows Logbog

Du kan gennemse Windows hændelseslog for at se hændelser, der oprettes, når netværksbeskyttelse blokerer (eller overvåger) adgang til en skadelig IP-adresse eller et skadeligt domæne:

1. [Kopiér XML-koden direkte](event-views.md).

2. Vælg **OK**.

Denne procedure opretter en brugerdefineret visning, der filtrerer for kun at vise følgende hændelser, der er relateret til netværksbeskyttelse:

<br>

****

|Hændelses-id|Beskrivelse|
|---|---|
|5007|Hændelse, når indstillingerne ændres|
|1125|Hændelse, når netværksbeskyttelse udløses i overvågningstilstand|
|1126|Hændelse, når netværksbeskyttelse udløses i bloktilstand|
|

## <a name="network-protection-and-the-tcp-three-way-handshake"></a>Netværksbeskyttelse og TCP-trevejs-håndtryk

Med netværksbeskyttelse afgøres det, om der skal tillades eller blokeres adgang til et websted, efter at [det trevejshåndtryk er fuldført via TCP/IP](/troubleshoot/windows-server/networking/three-way-handshake-via-tcpip). Når et websted er blokeret af netværksbeskyttelse, kan du derfor se en handlingstype `ConnectionSuccess` under `NetworkConnectionEvents` i Microsoft 365 Defender portalen, selvom webstedet faktisk er blokeret. `NetworkConnectionEvents` rapporteres fra TCP-laget og ikke fra netværksbeskyttelse. Når det trevejs-håndtryk er fuldført, er adgang til webstedet tilladt eller blokeret af netværksbeskyttelse.

Her er et eksempel på, hvordan det fungerer:

1. Lad os antage, at en bruger forsøger at få adgang til et websted på sin enhed. Webstedet hostes tilfældigvis på et farligt domæne, og det bør blokeres af netværksbeskyttelse.  

2. Det trevejs-håndtryk via TCP/IP begynder. Før den fuldføres, logføres en `NetworkConnectionEvents` handling, og den `ActionType` er angivet som `ConnectionSuccess`. Men så snart den trevejshandtryksproces er fuldført, blokerer netværksbeskyttelse adgangen til webstedet. Alt dette sker meget hurtigt. En lignende proces forekommer med [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview). Det er, når det trevejshåndtryk fuldføres, at der foretages en bestemmelse, og adgangen til et websted er enten blokeret eller tilladt.

3. I Microsoft 365 Defender-portalen vises en besked i [beskedkøen](alerts-queue.md). Oplysningerne om denne besked omfatter både `NetworkConnectionEvents` og `AlertEvents`. Du kan se, at webstedet er blokeret, selvom du også har et `NetworkConnectionEvents` element med ActionType for `ConnectionSuccess`.

## <a name="considerations-for-windows-virtual-desktop-running-windows-10-enterprise-multi-session"></a>Overvejelser i forbindelse med Windows virtuelt skrivebord, der kører Windows 10 Enterprise multisession

På grund af typen af flere brugere i Windows 10 Enterprise skal du være opmærksom på følgende punkter:

1. Netværksbeskyttelse er en funktion i hele enheden og kan ikke målrettes til bestemte brugersessioner.

2. Politikker til filtrering af webindhold er også enhedsdækkende.

3. Hvis du har brug for at skelne mellem brugergrupper, kan du overveje at oprette separate Windows Virtual Desktop-værtspuljer og -tildelinger.

4. Test netværksbeskyttelse i overvågningstilstand for at vurdere dens funktionsmåde, før den udrulles.

5. Overvej at ændre størrelsen på udrulningen, hvis du har et stort antal brugere eller et stort antal sessioner med flere brugere.

### <a name="alternative-option-for-network-protection"></a>Alternativ mulighed for netværksbeskyttelse

I forbindelse med Windows 10 Enterprise multisession 1909 og op, der bruges i Windows Virtual Desktop på Azure, kan netværksbeskyttelse af Microsoft Edge aktiveres ved hjælp af følgende metode:

1. Brug [Slå netværksbeskyttelse](enable-network-protection.md) til, og følg vejledningen for at anvende din politik.

2. Udfør følgende PowerShell-kommandoer:
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

## <a name="network-protection-troubleshooting"></a>Fejlfinding af netværksbeskyttelse

På grund af det miljø, hvor netværksbeskyttelse kører, kan Microsoft muligvis ikke registrere operativsystemets proxyindstillinger. I nogle tilfælde kan klienter til netværksbeskyttelse ikke oprette forbindelse til Cloud Service. For at løse forbindelsesproblemet skal kunder med E5-licenser konfigurere en af følgende registreringsdatabasenøgler:

```console
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyServer /d "<proxy IP address: Port>" /f
reg add "HKLM\Software\Microsoft\Windows Defender" /v ProxyPacUrl /d "<Proxy PAC url>" /f

```

## <a name="see-also"></a>Se også

- [Evaluer | netværksbeskyttelse](evaluate-network-protection.md) Tag et hurtigt scenarie, der viser, hvordan funktionen fungerer, og hvilke hændelser der typisk oprettes.
- [Aktivér netværksbeskyttelse](enable-network-protection.md) | Brug Gruppepolitik, PowerShell eller MDM-CSP'er til at aktivere og administrere netværksbeskyttelse på dit netværk.
- [Konfiguration af funktioner til reduktion af angrebsoverfladen i Microsoft Intune](/mem/intune/protect/endpoint-security-asr-policy)
