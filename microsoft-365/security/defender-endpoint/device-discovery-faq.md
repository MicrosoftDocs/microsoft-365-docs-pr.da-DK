---
title: Ofte stillede spørgsmål om Enhedsregistrering
description: Find svar på ofte stillede spørgsmål om enhedsregistrering
keywords: enhedsregistrering, find, passiv, proaktiv, netværk, synlighed, server, arbejdsstation, onboard, ikke-administrerede enheder
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
ms.openlocfilehash: 530846d4a7c18900f0697806bb656aa653b71947
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592170"
---
# <a name="device-discovery-frequently-asked-questions"></a>Ofte stillede spørgsmål om Enhedsregistrering

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- - [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

Find svar på ofte stillede spørgsmål om enhedsregistrering.

## <a name="what-is-basic-discovery-mode"></a>Hvad er Grundlæggende registreringstilstand?

Denne tilstand gør det muligt for alle onboardede Microsoft Defender for Endpoint-enheder at indsamle netværksdata og finde tilstødende enheder. Onboarded slutpunkter indsamler passivt hændelser i netværket og udtrækker enhedsoplysninger fra dem. Der startes ingen netværkstrafik. Onboarded slutpunkter vil ganske enkelt udtrække data fra hver enkelt netværkstrafik, der ses af en onboarded enhed. Disse data bruges til at vise ikke-administrerede enheder i dit netværk.

## <a name="can-i-disable-basic-discovery"></a>Kan jeg deaktivere Grundlæggende opdagelse?

Du har mulighed for at deaktivere registrering af enheder via siden [Avancerede](advanced-features.md) funktioner. Du mister dog synligheden på enheder, der ikke er administrerede i dit netværk. Bemærk, SenseNDR.exe stadig kører på onboardede enheder, uanset om Discovery er slået fra. 

## <a name="what-is-standard-discovery-mode"></a>Hvad er Standardregistreringstilstand?

I denne tilstand kan slutpunkter, der er onboardet til Microsoft Defender til Slutpunkt, aktivt søge efter observerede enheder i netværket for at forbedre indsamlede data (med den maksimale mængde netværkstrafik). Kun enheder, der er blevet observeret af den grundlæggende registreringstilstand, vil aktivt skifte i standardtilstand. Denne tilstand anbefales kraftigt til at opbygge et pålideligt og sammenhængende lager over enheder. Hvis du vælger at deaktivere denne tilstand og vælger Grundlæggende registreringstilstand, vil du sandsynligvis kun få begrænset synlighed for ikke-administrerede slutpunkter i dit netværk.

 Standardtilstand udnytter også almindelige discovery-protokoller, der bruger multicast-forespørgsler på netværket til at finde endnu flere enheder ud over dem, der er observeret ved hjælp af den passive metode.

## <a name="can-i-control-which-devices-perform-standard-discovery"></a>Kan jeg styre, hvilke enheder der udfører Standard discovery?

Du kan tilpasse listen over enheder, der bruges til at udføre Standard Discovery. Du kan enten aktivere Standardregistrering på alle onboardede enheder, der også understøtter denne funktion (aktuelt kun Windows 10 eller nyere og Windows Server 2019 eller nyere enheder), eller du kan vælge et undersæt eller undersæt af dine enheder ved at angive deres enhedsmærker. I dette tilfælde konfigureres alle andre enheder til kun at køre Grundlæggende opdagelse. Konfigurationen er tilgængelig på siden med indstillinger for enhedsregistrering.

## <a name="can-i-exclude-unmanaged-devices-from-the-device-inventory-list"></a>Kan jeg udelade enheder, der ikke er administrerede, fra listen over enheders lager?

Ja, du kan anvende filtre for at udelukke enheder, der ikke er administrerede, fra listen over enheders lager. Du kan også bruge kolonnen onboardingstatus på API-forespørgsler til at frafiltrere enheder, der ikke er administrerede.

## <a name="which-onboarded-devices-can-perform-discovery"></a>Hvilke onboardede enheder kan blive fundet?

Onboardede enheder, der kører på Windows 10 version 1809 eller nyere, Windows 11, Windows Server 2019 eller Windows Server 2022, kan opdage det.

## <a name="what-happens-if-my-onboarded-devices-is-connected-to-my-home-network-or-to-public-access-point"></a>Hvad sker der, hvis mine onboardede enheder er forbundet til mit hjemmenetværk eller til et offentligt adgangspunkt?

Discovery-programmet skelner mellem netværkshændelser, der modtages i virksomhedens netværk kontra uden for virksomhedens netværk. Ved at korrelere netværksidentifikatorer på tværs af alle lejers klienter skelnes begivenheder mellem dem, der er modtaget fra private netværk og virksomhedsnetværk. Hvis størstedelen af enhederne i organisationen rapporterer, at de har forbindelse til det samme netværksnavn med samme standardgateway og DHCP-serveradresse, kan det antages, at dette netværk sandsynligvis er et virksomhedsnetværk. Private netværksenheder vises ikke på listen i lageret og kan ikke aktivt skiftes.

## <a name="what-protocols-are-you-capturing-and-analyzing"></a>Hvilke protokoller registreres og analyseres i protokoller?

Som standard kører alle onboardede enheder på Windows 10 version 1809 eller nyere, Windows 11, Windows Server 2019 eller Windows Server 2022 er ved at hente og analysere følgende protokoller: ARP, CDP, DHCP, DHCPv6, IP (overskrifter), LLDP, LLMNR, mDNS, MNDP, NBNS, SSDP, TCP (SYN-overskrifter), UDP (overskrifter), WSDD

## <a name="which-protocols-do-you-use-for-active-probing-in-standard-discovery"></a>Hvilke protokoller bruger du til aktiv søgning i Standard Discovery?
Når en enhed er konfigureret til at køre Standard discovery, eksponerede tjenester afprøves ved hjælp af følgende protokoller: ARP, FTP, HTTP, HTTPS, ICMP, LLMNR, NBNS, RDP, SIP, SMTP, SNMP, SSH, Telnet, UPNP, WSD, SMB, NBSS, IPP, PJL, RPC, mDNS, DHCP, AFP, CrestonCIP, IphoneSync, WinRM, VNC, SLP, LDAP


## <a name="how-can-i-exclude-targets-from-being-probed-with-standard-discovery"></a>Hvordan kan jeg udelukke mål fra at blive afprøvet med Standard Discovery?

Hvis der er enheder på dit netværk, som ikke aktivt bør søges i, kan du også definere en liste over undtagelser for at forhindre dem i at blive scannet. Konfigurationen er tilgængelig på siden med indstillinger for enhedsregistrering.

> [!NOTE]
> Enheder kan stadig svare på forsøg på opdagelse med multicasts i netværket. Disse enheder bliver fundet, men vil ikke aktivt blive udsondret. 

## <a name="can-i-exclude-devices-from-being-discovered"></a>Kan jeg udelukke enheder fra at blive fundet?

Efterhånden som enhedsregistrering bruger passive metoder til at finde enheder i netværket, kan alle enheder, der kommunikerer med dine onboardede enheder på virksomhedens netværk, findes og vises på lageret. Du kan kun udelukke enheder fra aktiv sondering.

## <a name="how-frequent-is-the-active-probing"></a>Hvor hyppigt er den aktive sonde?

Enhederne vil aktivt blive afprøvet, når ændringer i enhedskarakteristika observeres for at sikre, at de eksisterende oplysninger er opdaterede (normalt har enhederne ikke skiftes mere end én gang inden for en periode på tre uger)

## <a name="my-security-tool-raised-alert-on-unicastscannerps1--psscript_guidps1-or-port-scanning-activity-initiated-by-it-what-should-i-do"></a>Min sikkerhedsværktøj hævet besked på UnicastScanner.ps1/PSScript_{GUID}.ps1 eller portscanning aktivitet startet af den, hvad skal jeg gøre?

De aktive prøvescripts er signeret af Microsoft og er sikre. Du kan føje følgende sti til udeladelseslisten: `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps1`

## <a name="what-is-the-amount-of-traffic-being-generated-by-the-standard-discovery-active-probe"></a>Hvor meget trafik genereres af den aktive probe Standard Discovery?

Aktive forsøg kan generere op til 50Kb trafik mellem onboardingenheden og den efterseende enhed, hvert forsøg på at

## <a name="why-is-there-a-discrepancy-between-can-be-onboarded-devices-in-the-device-inventory-and-the-number-of-devices-to-onboard-in-the-dashboard-tile"></a>Hvorfor er der en forskel mellem "kan være onboarding"-enheder i lagerlageret for enheder og antallet af "enheder, der skal onboardes" i dashboard-feltet?

Du kan måske se forskelle mellem antallet af angivne enheder under "kan onboardes" på enhedens lager, "onboard to Microsoft Defender for Endpoint"-sikkerhedsdete samt "enheder til onboard"-dashboardwidget.

 Sikkerhedsanbefalingen og dashboardwidgeten er til enheder, der er stabile i netværket; undtagen kortvarige enheder, gæsteenheder og andre. Idéen er at anbefale på permanente enheder, hvilket også indikerer organisationens overordnede sikkerhedsresultat.

## <a name="can-i-onboard-unmanaged-devices-that-were-found"></a>Kan jeg onboarde ikke-administrerede enheder, der blev fundet?

Ja. Du kan onboarde ikke-administrerede enheder manuelt. Ikke-administrerede slutpunkter i dit netværk introducerer sårbarheder og risici i dit netværk. Onboarding af dem til tjenesten kan øge synligheden af dem.

## <a name="ive-noticed-that-unmanaged-device-health-state-is-always-active-why-is-that"></a>Jeg har bemærket, at ikke-administrerede tilstand for enheder altid er "Aktiv", hvorfor er det?

Midlertidigt ikke-administreret enhedstilstand vil være "Aktiv" i standardopbevaringsperioden for enhedens lager, uanset den faktiske tilstand.

## <a name="does-standard-discovery-look-like-malicious-network-activity"></a>Ligner standardregistrering skadelig netværksaktivitet?

Når du overvejer Standardregistrering, undrer du dig måske over konsekvenserne af mulige handlinger og specifikt, om der kan være mistanke om sikkerhedsværktøjer, såsom ondsindet aktivitet. Følgende underafsnit forklarer, hvorfor organisationer i næsten alle tilfælde ikke bør bekymre sig om at aktivere Standard discovery.  

### <a name="probing-is-distributed-across-all-windows-devices-on-the-network"></a>Skiftene fordeles på tværs af Windows enheder på netværket

I modsætning til ondsindet aktivitet, som typisk scanner hele netværket fra et lille antal kompromitterede enheder, startes Microsoft Defender for Endpoints Standard Discovery-undersøgelse fra alle onboardede Windows-enheder, hvilket gør aktiviteten god og ikke-unormal. Sonden administreres centralt fra skyen for at balancere forsøg på at skifte mellem alle understøttede onboardede enheder i netværket.  

### <a name="active-probing-generates-negligible-amount-of-extra-traffic"></a>Aktiv sonde genererer mængden af ekstra trafik

Enheder, der ikke er administrerede, vil typisk blive vist højst én gang i en periode på tre uger og generere mindre end 50KB trafik. Ondsindet aktivitet omfatter som regel store gentagne forsøg og i nogle tilfælde dataudfyldning, der genererer en betydelig mængde netværkstrafik, som kan identificeres som en anomali ved hjælp af netværkovervågningsværktøjer.

### <a name="your-windows-device-already-runs-active-discovery"></a>Din Windows kører allerede aktiv opdagelse

Aktive registreringsfunktioner er altid integreret i Windows-operativsystemet for at finde enheder, slutpunkter og printere i nærheden, så det er nemmere at bruge plug and play-oplevelser og fildeling mellem slutpunkter på netværket. Tilsvarende funktionalitet er implementeret i mobilenheder, netværksudstyr og lagerprogrammer blot for blot at nævne nogle få.  

Standardregistrering bruger de samme registreringsmetoder til at identificere enheder og til at få en samlet synlighed for alle enheder i dit netværk på Microsoft 365 Defender Device Inventory. Eksempel – Standardregistrering identificerer slutpunkter i nærheden på netværket på samme måde, som Windows viser tilgængelige printere i netværket. 

Netværkssikkerhed og overvågningsværktøjer er ligegyldige for sådanne aktiviteter, der udføres af enheder på netværket. 

### <a name="only-unmanaged-devices-are-being-probed"></a>Der skiftes kun enheder, som ikke er administrerede

Funktionerne til registrering af enheder er blevet udviklet til kun at opdage og identificere enheder, der ikke er administrerede på dit netværk. Det betyder, at der ikke kan skiftes til enheder, der tidligere er blevet fundet, og som allerede er onboardet med Microsoft Defender til slutpunkt.

### <a name="you-can-exclude-network-lures-from-active-probing"></a>Du kan udelukke netværker fra aktive søgninger

Standardregistrering understøtter udelukkelse af enheder eller områder (undernet) fra aktiv søgning. Hvis du har netværksdrivere installeret på stedet, kan du bruge indstillingerne for Enhedsregistrering til at definere udeladelse baseret på IP-adresser eller undernet (et interval af IP-adresser). Definition af disse udeladelser sikrer, at enhederne ikke aktivt skiftes og ikke får besked. Disse enheder vil kun blive fundet ved hjælp af passive metoder (svarende til tilstanden Grundlæggende registrering).
