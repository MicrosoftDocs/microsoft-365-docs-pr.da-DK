---
title: Ofte stillede spørgsmål om enhedsregistrering
description: Få svar på ofte stillede spørgsmål om enhedsregistrering
keywords: enhedsregistrering, finde, passiv, proaktiv, netværk, synlighed, server, arbejdsstation, onboard, ikke-administrerede enheder
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 54a1b816f3d1322cab5558e5bd09d5d9b4285ae8
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665002"
---
# <a name="device-discovery-frequently-asked-questions"></a>Ofte stillede spørgsmål om enhedsregistrering

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- - [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

Få svar på ofte stillede spørgsmål om enhedsregistrering.

## <a name="what-is-basic-discovery-mode"></a>Hvad er grundlæggende registreringstilstand?

Denne tilstand gør det muligt for alle Microsoft Defender for Endpoint onboardede enheder at indsamle netværksdata og finde tilstødende enheder. Onboardede slutpunkter indsamler passivt hændelser på netværket og udtrækker enhedsoplysninger fra dem. Der startes ingen netværkstrafik. Onboardede slutpunkter udtrækker blot data fra hver netværkstrafik, der ses af en onboardet enhed. Disse data bruges til at vise ikke-administrerede enheder på netværket.

## <a name="can-i-disable-basic-discovery"></a>Kan jeg deaktivere grundlæggende registrering?

Du har mulighed for at slå enhedsregistrering fra på siden [Avancerede funktioner](advanced-features.md) . Du mister dog synligheden på ikke-administrerede enheder på netværket. Bemærk, at SenseNDR.exe stadig kører på de onboardede enheder, uanset om registrering er slået fra. 

## <a name="what-is-standard-discovery-mode"></a>Hvad er Standard-registreringstilstand?

I denne tilstand kan slutpunkter, der er onboardet til Microsoft Defender for Endpoint, aktivt undersøge observerede enheder i netværket for at forbedre indsamlede data (med ubetydelig mængde netværkstrafik). Kun enheder, der blev observeret af den grundlæggende registreringstilstand, undersøges aktivt i standardtilstand. Denne tilstand anbefales på det kraftigste til oprettelse af en pålidelig og sammenhængende enhedsoversigt. Hvis du vælger at deaktivere denne tilstand og vælger Grundlæggende registreringstilstand, vil du sandsynligvis kun få begrænset synlighed af ikke-administrerede slutpunkter på netværket.

 Standardtilstand bruger også almindelige registreringsprotokoller, der bruger multicast-forespørgsler i netværket, til at finde endnu flere enheder ud over dem, der blev observeret ved hjælp af den passive metode.

## <a name="can-i-control-which-devices-perform-standard-discovery"></a>Kan jeg styre, hvilke enheder der udfører standardregistrering?

Du kan tilpasse listen over enheder, der bruges til at udføre standardregistrering. Du kan enten aktivere Standard-registrering på alle onboardede enheder, der også understøtter denne funktion (i øjeblikket Windows 10 eller nyere og kun Windows Server 2019 eller nyere enheder), eller du kan vælge et undersæt eller undersæt af dine enheder ved at angive deres enhedskoder. I dette tilfælde konfigureres alle andre enheder til kun at køre Grundlæggende registrering. Konfigurationen er tilgængelig på siden med indstillinger for enhedsregistrering.

## <a name="can-i-exclude-unmanaged-devices-from-the-device-inventory-list"></a>Kan jeg udelade ikke-administrerede enheder fra enhedens lagerliste?

Ja, du kan anvende filtre for at udelade ikke-administrerede enheder fra enhedslagerlisten. Du kan også bruge kolonnen med onboardingstatus i API-forespørgsler til at filtrere ikke-administrerede enheder fra.

## <a name="which-onboarded-devices-can-perform-discovery"></a>Hvilke onboardede enheder kan udføre registrering?

Onboardede enheder, der kører på Windows 10 version 1809 eller nyere, Windows 11, Windows Server 2019 eller Windows Server 2022 kan udføre registrering.

## <a name="what-happens-if-my-onboarded-devices-is-connected-to-my-home-network-or-to-public-access-point"></a>Hvad sker der, hvis mine onboardede enheder har forbindelse til mit hjemmenetværk eller til et offentligt adgangspunkt?

Registreringsprogrammet skelner mellem netværkshændelser, der modtages i virksomhedens netværk i forhold til uden for virksomhedens netværk. Ved at korrelere netværks-id'er på tværs af alle lejerens klienter skelnes der mellem hændelser, der blev modtaget fra private netværk og virksomhedsnetværk. Hvis størstedelen af enhederne i organisationen f.eks. rapporterer, at de har forbindelse til det samme netværksnavn med den samme standardgateway og DHCP-serveradresse, kan det antages, at dette netværk sandsynligvis er et virksomhedsnetværk. Private netværksenheder vises ikke i oversigten og undersøges ikke aktivt.

## <a name="what-protocols-are-you-capturing-and-analyzing"></a>Hvilke protokoller opfanger og analyserer du?

Som standard kører alle onboardede enheder på Windows 10 version 1809 eller nyere, Windows 11, Windows Server 2019 eller Windows Server 2022 henter og analyserer følgende protokoller: ARP, CDP, DHCP, DHCPv6, IP (headers), LLDP, LLMNR, mDNS, MNDP, NBNS, SSDP, TCP (SYN-headere), UDP (headere), WSD

## <a name="which-protocols-do-you-use-for-active-probing-in-standard-discovery"></a>Hvilke protokoller bruger du til aktiv undersøgelse i Standard discovery?
Når en enhed er konfigureret til at køre Standard discovery, eksponerede tjenester undersøges ved hjælp af følgende protokoller: ARP, FTP, HTTP, HTTPS, ICMP, LLMNR, NBNS, RDP, SIP, SMTP, SNMP, SSH, Telnet, UPNP, WSD, SMB, NBSS, IPP, PJL, RPC, mDNS, DHCP, AFP, CrestonCIP, IphoneSync, WinRM, VNC, SLP, LDAP


## <a name="how-can-i-exclude-targets-from-being-probed-with-standard-discovery"></a>Hvordan kan jeg udelukke, at mål undersøges med Standard-registrering?

Hvis der er enheder på netværket, som ikke skal undersøges aktivt, kan du også definere en liste over undtagelser for at forhindre, at de scannes. Konfigurationen er tilgængelig på siden med indstillinger for enhedsregistrering.

> [!NOTE]
> Enheder kan stadig besvare multicast-registreringsforsøg i netværket. Disse enheder bliver fundet, men undersøges ikke aktivt. 

## <a name="can-i-exclude-devices-from-being-discovered"></a>Kan jeg udelukke enheder fra at blive fundet?

Da enhedsregistrering bruger passive metoder til at finde enheder i netværket, kan alle enheder, der kommunikerer med dine onboardede enheder i virksomhedens netværk, registreres og vises i oversigten. Du kan kun udelukke enheder fra aktiv undersøgelse.

## <a name="how-frequent-is-the-active-probing"></a>Hvor hyppigt er den aktive probing?

Enheder undersøges aktivt, når ændringer i enhedsegenskaber overholdes for at sikre, at de eksisterende oplysninger er opdateret (typisk undersøges enheder højst én gang i en tre ugers periode)

## <a name="my-security-tool-raised-alert-on-unicastscannerps1--psscript_guidps1-or-port-scanning-activity-initiated-by-it-what-should-i-do"></a>Mit sikkerhedsværktøj har givet besked om UnicastScanner.ps1/PSScript_{GUID}.ps1 eller portscanning, der er initieret af det. Hvad skal jeg gøre?

De aktive probingscripts er signeret af Microsoft og er sikre. Du kan føje følgende sti til listen over undtagelser: `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps1`

## <a name="what-is-the-amount-of-traffic-being-generated-by-the-standard-discovery-active-probe"></a>Hvad er den mængde trafik, der genereres af den aktive standardregistreringssonde?

Aktiv probing kan generere op til 50 KB trafik mellem den onboardede enhed og den probede enhed, hvert probingforsøg

## <a name="why-is-there-a-discrepancy-between-can-be-onboarded-devices-in-the-device-inventory-and-the-number-of-devices-to-onboard-in-the-dashboard-tile"></a>Hvorfor er der en uoverensstemmelse mellem "kan onboardes"-enheder i enhedslageret og antallet af "enheder, der skal onboardes" i dashboardfeltet?

Du vil muligvis bemærke forskelle mellem antallet af angivne enheder under "kan onboardes" i enhedslageret, sikkerhedsanbefalingerne "onboardes til Microsoft Defender for Endpoint" og "enheder, der skal onboardes" dashboardwidget.

 Sikkerhedsanbefalingerne og dashboardwidgetten er til enheder, der er stabile på netværket. undtagen flygtighedsenheder, gæsteenheder og andre. Ideen er at anbefale på faste enheder, der også indebærer den overordnede sikkerhedsscore for organisationen.

## <a name="can-i-onboard-unmanaged-devices-that-were-found"></a>Kan jeg onboarde ikke-administrerede enheder, der blev fundet?

Ja. Du kan onboarde ikke-administrerede enheder manuelt. Ikke-administrerede slutpunkter i dit netværk introducerer sikkerhedsrisici og risici for dit netværk. Onboarding af dem til tjenesten kan øge sikkerheden synlighed på dem.

## <a name="ive-noticed-that-unmanaged-device-health-state-is-always-active-why-is-that"></a>Jeg har bemærket, at ikke-administreret enhedstilstand altid er "Aktiv", hvorfor er det?

Midlertidigt vil ikke-administreret tilstandstilstand for enheden være "Aktiv" i enhedens standardopbevaringsperiode, uanset deres faktiske tilstand.

## <a name="does-standard-discovery-look-like-malicious-network-activity"></a>Ligner standardregistrering skadelig netværksaktivitet?

Når du overvejer Standard discovery, undrer du dig måske over konsekvenserne af at undersøge, og specifikt om sikkerhedsværktøjer kan have mistanke om sådan aktivitet som ondsindet. I følgende undersektion forklares det, hvorfor organisationer i næsten alle tilfælde ikke bør have nogen bekymringer omkring aktivering af Standard-registrering.  

### <a name="probing-is-distributed-across-all-windows-devices-on-the-network"></a>Probing distribueres på tværs af alle Windows enheder på netværket

I modsætning til ondsindet aktivitet, som typisk ville scanne hele netværket fra et lille antal kompromitterede enheder, initieres Microsoft Defender for Endpoint standardregistreringstest fra alle onboardede Windows enheder, hvilket gør aktiviteten godartet og ikke-unormal. Probing administreres centralt fra clouden for at balancere probingforsøget mellem alle understøttede onboardede enheder i netværket.  

### <a name="active-probing-generates-negligible-amount-of-extra-traffic"></a>Aktiv probing genererer ubetydelig mængde ekstra trafik

Ikke-administrerede enheder undersøges typisk ikke mere end én gang i en tre ugers periode og genererer mindre end 50 KB trafik. Ondsindet aktivitet omfatter normalt høje gentagne probingforsøg og i nogle tilfælde dataudfiltrering, der genererer en betydelig mængde netværkstrafik, der kan identificeres som en uregelmæssighed ved hjælp af værktøjer til netværksovervågning.

### <a name="your-windows-device-already-runs-active-discovery"></a>Din Windows enhed kører allerede aktiv registrering

Aktive registreringsfunktioner er altid blevet integreret i Windows operativsystem for at finde enheder i nærheden, slutpunkter og printere for at lette "plug and play"-oplevelser og fildeling mellem slutpunkter i netværket. Lignende funktionalitet implementeres i mobilenheder, netværksudstyr og lagerapplikationer blot for at nævne nogle få.  

Standardregistrering bruger de samme registreringsmetoder til at identificere enheder og til at have en samlet synlighed for alle enheder i dit netværk i Microsoft 365 Defender Enhedsoversigt. F.eks. – Standardregistrering identificerer slutpunkter i nærheden på netværket på samme måde Windows viser tilgængelige printere i netværket. 

Værktøjer til netværkssikkerhed og overvågning er ligeglade med sådanne aktiviteter, der udføres af enheder på netværket. 

### <a name="only-unmanaged-devices-are-being-probed"></a>Det er kun ikke-administrerede enheder, der undersøges

Enhedens registreringsfunktioner er udviklet til kun at finde og identificere ikke-administrerede enheder på netværket. Det betyder, at tidligere registrerede enheder, der allerede er onboardet med Microsoft Defender for Endpoint, ikke bliver undersøgt.

### <a name="you-can-exclude-network-lures-from-active-probing"></a>Du kan udelukke netværks-lokker fra aktiv sondering

Standardregistrering understøtter udeladelse af enheder eller områder (undernet) fra aktiv probing. Hvis du har installeret netværks-lokker, kan du bruge indstillingerne for Enhedsregistrering til at definere undtagelser baseret på IP-adresser eller undernet (en række IP-adresser). Hvis du definerer disse undtagelser, sikrer du, at disse enheder ikke undersøges aktivt og ikke bliver advaret. Disse enheder registreres kun ved hjælp af passive metoder (svarer til grundlæggende registreringstilstand).
