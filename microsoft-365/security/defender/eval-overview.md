---
title: Evaluer og Microsoft 365 Defender, en XDR-løsning
description: Hvad er XDR-sikkerhed? Hvordan kan du evaluere en Microsoft XDR i Microsoft 365 Defender? Brug denne blogserie til at planlægge dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø for at teste og prøve en sikkerhedsløsning, der er udviklet til at beskytte enheder, identitet, data og programmer. Start din XDR-cybersikkerhedsrejse her, og tag testen til produktion.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 06/25/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: f7830bb25f2572c43d665d059e0a36bc1fdaa172
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500777"
---
# <a name="evaluate-and-pilot-microsoft-365-defender"></a>Evaluer og Microsoft 365 Defender

**Gælder for:**

- Microsoft 365 Defender

## <a name="how-this-article-series-works"></a>Sådan fungerer denne artikelserie

Denne serie af artikler er udviklet til at hjælpe dig gennem hele processen med at konfigurere et *XDR-miljø* med prøveversioner, fra slutpunkt til slutpunkt, så du kan evaluere funktionerne og egenskaberne i Microsoft 365 Defender og endda fremme evalueringsmiljøet direkte til produktion, når og hvis du er klar.

Hvis du ikke har tænkt på XDR før, kan du scanne disse 7 artikler, der linkes til, for at få en fornemmelse for, hvor omfattende løsningen er.

- [Sådan oprettes miljøet](eval-create-eval-environment.md)
- Konfigurer eller få mere at vide om hver teknologi i denne Microsoft XDR
  - [Microsoft Defender for Identity](eval-defender-identity-overview.md)
  - [Microsoft Defender til Office](eval-defender-office-365-overview.md)
  - [Microsoft Defender for Endpoint](eval-defender-endpoint-overview.md)
  - [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)
- [Sådan undersøger og reagerer du ved hjælp af denne XDR](eval-defender-investigate-respond.md)
- [Yd prøveversionsmiljøet til produktion](eval-defender-promote-to-production.md)

## <a name="microsoft-365-defender-is-a-microsoft-xdr-cyber-security-solution"></a>Microsoft 365 Defender er en Microsoft XDR-cybersikkerhedsløsning

Microsoft 365 Defender er en **XDR-løsning (EXtended Detection and Response**), der automatisk indsamler, korrelerer og analyserer signal-, trussels- og advarselsdata fra hele Microsoft 365-miljøet, herunder *slutpunkter, mail, programmer og identiteter*. Den udnytter kunstig intelligens og automatisering til automatisk at stoppe angreb og  afhjælpe påvirkede aktiver i en sikker tilstand.

Tænk på XDR som det næste trin i sikkerhed, ens slutpunkt (slutpunktsregistrering og -svar eller Slutpunktsregistrering og -svar), mail-, app- og identitetssikkerhed på ét sted.

## <a name="microsoft-recommendations-for-evaluating-microsoft-365-defender"></a>Microsoft-anbefalinger til evaluering af Microsoft 365 Defender

Microsoft anbefaler, at du opretter din evaluering i et eksisterende produktionsabonnement på Office 365. På den måde får du indsigt i den virkelige verden med det samme, og du kan finjustere indstillingerne, så du kan arbejde mod aktuelle trusler i dit miljø. Når du har fået erfaring og er fortrolig med platformen, skal du blot promovere hver komponent, én ad gangen, til produktion.

## <a name="the-anatomy-of-a-cyber-security-attack"></a>En cybersikkerhedsangrebs enatomy

Microsoft 365 Defender er en skybaseret, samlet, forudbebudt og efter brud på enterprise-forsvarspakken. Det koordinerer *forebyggelse*, *registrering**, undersøgelse* og *svar* på tværs af slutpunkter, identiteter, apps, mail, samarbejdsprogrammer og alle deres data.

I denne illustration er et angreb i gang. Phishingmail ankommer til indbakken for en medarbejder i organisationen, som ukendt åbner den vedhæftede fil i en mail. Dette installerer malware, hvilket fører til en kæde af hændelser, der kan ende med tyveriet af følsomme data. Men i dette tilfælde er Defender for Office 365 i gang.

:::image type="content" source="../../media/defender/m365-defender-eval-threat-chain.png" alt-text="De forskellige angrebsforsøg" lightbox="../../media/defender/m365-defender-eval-threat-chain.png":::

I illustrationen:

- **Exchange Online Protection**, en del Microsoft Defender for Office 365, kan registrere phishing-mailen og bruge regler for mailflow til at sikre, at den aldrig ankommer i indbakken.
- **Defender for Office 365**, der er sikre, tester den vedhæftede fil og fastslår, at den er skadelig, så der kan ikke foretages handling i de mails, der modtages, eller politikker forhindrer, at mailen ankommer.
- **Defender til Slutpunkt administrerer** enheder, der opretter forbindelse til virksomhedens netværk og registrerer enheds- og netværksrisici, der ellers kunne udnyttes.
- **Defender for Identity** noterer sig pludselige kontoændringer som eskalering af rettigheder eller lateral bevægelse med høj risiko. Den rapporterer også om nemt udnyttede identitetsproblemer, f.eks. ikke-sammenkædede Kerberos-delegation, så sikkerhedsteamet kan rette det.
- **Microsoft Defender for Cloud Apps meddelelser** om unormal adfærd som umulig rejse, adgang til legitimationsoplysninger og usædvanlig download, fildeling eller videresendelse af mail og rapporterer disse til sikkerhedsteamet.

### <a name="microsoft-365-defender-components-secure-devices-identity-data-and-applications"></a>Microsoft 365 Defender komponenter gør enheder, identitet, data og programmer sikre

Microsoft 365 Defender består af disse sikkerhedsteknologier, som arbejder sammen. Du behøver ikke alle disse komponenter for at drage fordel af funktionerne i XDR og Microsoft 365 Defender. Du vil også opdage, at der vil komme en gevinst og effektivitet ved at bruge en eller to.

|Komponent|Beskrivelse|Referencemateriale|
|---|---|---|
|Microsoft Defender for Identity|Microsoft Defender for Identity bruger Active Directory-signaler til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og ondsindede Insider-handlinger rettet mod din organisation.|[Hvad er Microsoft Defender for Identity?](/defender-for-identity/what-is)|
|Exchange Online Protection|Exchange Online Protection er den oprindelige skybaserede SMTP relay- og filtreringstjeneste, der hjælper med at beskytte din organisation mod spam og malware.|[Exchange Online Protection (EOP) – Office 365](../office-365-security/overview.md)|
|Microsoft Defender for Office 365|Microsoft Defender for Office 365 beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer.|[Microsoft Defender for Office 365 – Office 365](../office-365-security/overview.md)|
|Microsoft Defender for Endpoint|Microsoft Defender for Endpoint er en samlet platform til enhedsbeskyttelse, registrering efter brud, automatisk undersøgelse og anbefalet svar.|[Microsoft Defender for Endpoint – Windows sikkerhed](../defender-endpoint/microsoft-defender-endpoint.md)|
|Microsoft Defender for Cloud Apps|Microsoft Defender for Cloud Apps er en omfattende løsning på tværs af SaaS, der giver stor synlighed, stærke datakontrolelementer og forbedret trusselsbeskyttelse til dine skyapps.|[Hvad er Defender til skyapps?](/cloud-app-security/what-is-cloud-app-security)|
|Azure AD Identity Protection|Azure AD Identity Protection evaluerer risikodata fra millioner af logonforsøg og bruger disse data til at evaluere risikoen for hvert logon til dit miljø. Disse data bruges af Azure AD til at tillade eller forhindre kontoadgang, afhængigt af hvordan politikkerne for Betinget adgang er konfigureret. Azure AD Identity Protection gives i licens separat Microsoft 365 Defender. Den er inkluderet i Azure Active Directory Premium P2.|[Hvad er identitetsbeskyttelse?](/azure/active-directory/identity-protection/overview-identity-protection)|
||||

## <a name="microsoft-365-defender-architecture"></a>Microsoft 365 Defender arkitektur

Nedenstående diagram illustrerer en arkitektur på højt niveau for Microsoft 365 Defender komponenter og integrationer. *I* denne serie af artikler gives detaljeret arkitektur for hver Defender-komponent og use-case-scenarier.

:::image type="content" source="../../media/defender/m365-defender-eval-architecture.png" alt-text="En arkitektur på højt niveau af Microsoft 365 Defender portalen" lightbox="../../media/defender/m365-defender-eval-architecture.png":::

I denne illustration:

- Microsoft 365 Defender kombinerer signaler fra alle Defender-komponenterne for at give udvidet registrering og respons (XDR) på tværs af domæner. Dette omfatter en samlet hændelseskøen, automatiseret svar til stop af angreb, selvbetjening (for kompromitterede enheder, brugeridentiteter og postkasser), krydstruslens jagt og trusselsanalyser.
- Microsoft Defender for Office 365 beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer. Den deler signaler, der følger af disse aktiviteter, Microsoft 365 Defender. Exchange Online Protection (EOP) er integreret, så der er en ende-til-ende-beskyttelse til indgående mails og vedhæftede filer.
- Microsoft Defender for Identity indsamler signaler fra servere, der kører AD FS (Active Directory Federated Services) og Active Directory i det lokale miljø Domain Services (AD DS). It uses these signals to protect your hybrid identity environment, including protect against hackers that use compromised accounts to move laterally across workstations in the on-premises environment.
- Microsoft Defender for Endpoint indsamler signaler fra og beskytter enheder, der bruges af din organisation.
- Microsoft Defender for Cloud Apps indsamler signaler fra din organisations brug af skyapps og beskytter data, der flyder mellem dit miljø og disse apps, herunder både målrettede og ikke-tilladte skyapps.
- Azure AD Identity Protection evaluerer risikodata fra millioner af logonforsøg og bruger disse data til at evaluere risikoen for hvert logon til dit miljø. Disse data bruges af Azure AD til at tillade eller forhindre kontoadgang, afhængigt af hvordan politikkerne for Betinget adgang er konfigureret. Azure AD Identity Protection gives i licens separat Microsoft 365 Defender. Den er inkluderet i Azure Active Directory Premium P2.

## <a name="microsoft-siem-and-soar-can-use-data-from-microsoft-365-defender"></a>Microsoft SIEM og SOAR kan bruge data fra Microsoft 365 Defender

Yderligere valgfri arkitekturkomponenter, der ikke er inkluderet i denne illustration:

- **Detaljerede signaldata fra alle Microsoft 365 Defender-komponenter kan integreres i Microsoft Sentinel** og kombineres med andre logføringskilder for at tilbyde fulde funktioner og indsigter i SIEM og SOAR.
- Du kan finde flere oplysninger om brug af **Microsoft Sentinel, et Azure SIEM med Microsoft 365 Defender** som XDR, i denne Oversigtsartikel samt [](/azure/sentinel/microsoft-365-defender-sentinel-integration) trinnene til Microsoft Sentinel og Microsoft 365 Defender [integration](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE).
- Du kan få mere at vide om SOAR i Microsoft Sentinel (herunder links til playbooks i Microsoft Sentinel GitHub Repository) ved at læse [denne artikel](/azure/sentinel/automate-responses-with-playbooks).

## <a name="the-evaluation-process-for-microsoft-365-defender-cyber-security"></a>Evalueringsprocessen for Microsoft 365 Defender cybersikkerhed

Microsoft anbefaler, at du aktiverer komponenterne i Microsoft 365 rækkefølge illustreret:

:::image type="content" source="../../media/defender/m365-defender-eval-process.png" alt-text="En evalueringsproces på højt niveau i Microsoft 365 Defender portal" lightbox="../../media/defender/m365-defender-eval-process.png":::

I følgende tabel beskrives denne illustration.

|  Serienummer   |Trin  |Beskrivelse  |
|------|---------|---------|
|1     | [Opret evalueringsmiljøet](eval-create-eval-environment.md)       |Dette trin sikrer, at du har prøveversionen af Microsoft 365 Defender.         |
|2     | [Aktivér Defender for Identity](eval-defender-identity-overview.md)        | Gennemgå arkitekturkravene, aktivér evalueringen, og gennemgå selvstudier til at identificere og afhjælpe forskellige angrebstyper.   |
|3     | [Aktivér Defender for Office 365 ](eval-defender-office-365-overview.md)       | Sørg for, at du opfylder arkitekturkravene, aktiverer evalueringen og opretter derefter pilotmiljøet. Denne komponent indeholder Exchange Online Protection så du rent faktisk *evaluerer begge* her.      |
|4     | [Aktivér Defender til Slutpunkt ](eval-defender-endpoint-overview.md)       | Sørg for, at du opfylder arkitekturkravene, aktiverer evalueringen og opretter derefter pilotmiljøet.         |
|5     | [Aktivér Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)        |  Sørg for, at du opfylder arkitekturkravene, aktiverer evalueringen og opretter derefter pilotmiljøet.        |
|6     | [Undersøg og svar på trusler](eval-defender-investigate-respond.md)        |   Simulere et angreb og begynde at bruge egenskaber for hændelsesrespons.      |
|7     | [Hæve prøveabonnementet til produktion](eval-defender-promote-to-production.md)        | Promote the Microsoft 365 components to production one-by-one.        |

Dette er en ofte anbefalet rækkefølge, der er udviklet til at udnytte værdien af egenskaberne hurtigt baseret på, hvor meget indsats der typisk kræves for at installere og konfigurere egenskaberne. Eksempelvis kan Defender for Office 365 konfigureres på kortere tid, end det tager at tilmelde enheder i Defender til slutpunkt. Du skal selvfølgelig prioritere komponenterne, så de opfylder virksomhedens behov, og du kan aktivere dem i en anden rækkefølge.

## <a name="go-to-the-next-step"></a>Gå til næste trin

[Få mere at vide om og/eller opret Microsoft 365 Defender Evaluation Environment](eval-create-eval-environment.md)
