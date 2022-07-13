---
title: Evaluer og pilot Microsoft 365 Defender, en XDR-løsning
description: Hvad er XDR-sikkerhed? Hvordan kan du evaluere en Microsoft XDR i Microsoft 365 Defender? Brug denne blogserie til at planlægge dit Microsoft 365 Defender prøvelaboratorium eller et pilotmiljø for at teste og styre en sikkerhedsløsning, der er udviklet til at beskytte enheder, identitet, data og programmer. Start din XDR-cybersikkerhedsrejse her, og tag denne test til produktion.
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
- zerotrust-solution
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 5256a578abb515f7d8d2d6e73b5a01fe71404dd0
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750072"
---
# <a name="evaluate-and-pilot-microsoft-365-defender"></a>Evaluer og test Microsoft 365 Defender

**Gælder for:**

- Microsoft 365 Defender

## <a name="how-this-article-series-works"></a>Sådan fungerer denne artikelserie

Denne serie af artikler er designet til at hjælpe dig gennem hele processen med at konfigurere et XDR-prøveversionsmiljø fra *slutpunkt til slutpunkt*, så du kan evaluere funktionerne og egenskaberne i Microsoft 365 Defender og endda fremme evalueringsmiljøet direkte til produktion, når og hvis du er klar.

Hvis du ikke har tænkt på XDR, kan du scanne disse syv sammenkædede artikler for at få en fornemmelse af, hvor omfattende løsningen er.

- [Sådan opretter du miljøet](eval-create-eval-environment.md)
- Konfigurer eller få mere at vide om hver teknologi i denne Microsoft XDR
  - [Microsoft Defender for Identity](eval-defender-identity-overview.md)
  - [Microsoft Defender til Office](eval-defender-office-365-overview.md)
  - [Microsoft Defender for Endpoint](eval-defender-endpoint-overview.md)
  - [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)
- [Sådan undersøges og reageres der ved hjælp af denne XDR](eval-defender-investigate-respond.md)
- [Hæv prøvemiljøet til produktion](eval-defender-promote-to-production.md)

## <a name="microsoft-365-defender-is-a-microsoft-xdr-cyber-security-solution"></a>Microsoft 365 Defender er en Microsoft XDR-løsning til cybersikkerhed

Microsoft 365 Defender er en **XDR-løsning (eXtended detection and response),** der automatisk indsamler, korrelerer og analyserer signal-, trussels- og beskeddata fra *hele* dit Microsoft 365-miljø, herunder *slutpunkt, mail, programmer og identiteter*. Den udnytter kunstig intelligens og automatisering til *automatisk* at stoppe angreb og afhjælpe berørte aktiver i en sikker tilstand.

Tænk på XDR som det næste trin i sikkerhed, samlende slutpunkt (registrering af slutpunkt og svar eller EDR), mail, app og identitetssikkerhed på ét sted.

## <a name="microsoft-recommendations-for-evaluating-microsoft-365-defender"></a>Microsofts anbefalinger til evaluering af Microsoft 365 Defender

Microsoft anbefaler, at du opretter din evaluering i et eksisterende produktionsabonnement på Office 365. På denne måde får du øjeblikkelig indsigt i den virkelige verden og kan indstille indstillingerne for at arbejde mod aktuelle trusler i dit miljø. Når du har fået erfaring og er fortrolig med platformen, skal du blot hæve hver komponent, én ad gangen, til produktion.

## <a name="the-anatomy-of-a-cyber-security-attack"></a>Anatomien i et cybersikkerhedsangreb

Microsoft 365 Defender er en cloudbaseret, samlet, før- og efter sikkerhedsbrud virksomhedsforsvarspakke. Den koordinerer *forebyggelse*, *registrering*, *undersøgelse* og *svar* på tværs af slutpunkter, identiteter, apps, mail, samarbejdsprogrammer og alle deres data.

I denne illustration er et angreb i gang. Phishing-mail modtages i indbakken for en medarbejder i din organisation, som ubevidst åbner den vedhæftede fil. Dette installerer malware, hvilket fører til en kæde af hændelser, der kan ende med tyveri af følsomme data. Men i dette tilfælde er Defender for Office 365 i funktion.

:::image type="content" source="../../media/defender/m365-defender-eval-threat-chain.png" alt-text="De forskellige angrebsforsøg" lightbox="../../media/defender/m365-defender-eval-threat-chain.png":::

I illustrationen:

- **Exchange Online Protection**, som er en del af Microsoft Defender for Office 365, kan registrere phishingmailen og bruge regler for mailflow til at sikre, at den aldrig modtages i indbakken.
- **Defender for Office 365** sikre vedhæftede filer tester den vedhæftede fil og fastslår, at den er skadelig, så den mail, der modtages, enten ikke kan handles af brugeren, eller politikker forhindrer, at mailen ankommer til alle.
- **Defender for Endpoint** administrerer enheder, der opretter forbindelse til virksomhedens netværk, og registrerer sikkerhedsrisici for enheder og netværk, der ellers kan udnyttes.
- **Defender for Identity** noterer sig pludselige ændringer som rettighedseskalering eller højrisiko tværgående bevægelse. Den rapporterer også om letudnyttede identitetsproblemer, f.eks. begrænset Kerberos-delegering, til rettelse af sikkerhedsteamet.
- **Microsoft Defender for Cloud Apps** bemærker unormal adfærd som f.eks. umulig rejse, adgang til legitimationsoplysninger og usædvanlig download, fildeling eller videresendelse af mail og rapporterer disse til sikkerhedsteamet.

### <a name="microsoft-365-defender-components-secure-devices-identity-data-and-applications"></a>Microsoft 365 Defender komponenter sikre enheder, identitet, data og programmer

Microsoft 365 Defender består af disse sikkerhedsteknologier, der fungerer parallelt. Du behøver ikke alle disse komponenter for at drage fordel af funktionerne i XDR og Microsoft 365 Defender. Du vil realisere gevinster og effektivitet ved hjælp af en eller to samt.

|Komponent|Beskrivelse|Referencemateriale|
|---|---|---|
|Microsoft Defender for Identity|Microsoft Defender for Identity bruger Active Directory-signaler til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og skadelige insiderhandlinger, der er rettet mod din organisation.|[Hvad er Microsoft Defender for Identity?](/defender-for-identity/what-is)|
|Exchange Online Protection|Exchange Online Protection er det oprindelige skybaserede SMTP-relæ og den oprindelige filtreringstjeneste, der hjælper med at beskytte din organisation mod spam og malware.|[oversigt over Exchange Online Protection (EOP) – Office 365](../office-365-security/overview.md)|
|Microsoft Defender for Office 365|Microsoft Defender for Office 365 beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer.|[Microsoft Defender for Office 365 - Office 365](../office-365-security/overview.md)|
|Microsoft Defender for Endpoint|Microsoft Defender for Endpoint er en samlet platform til enhedsbeskyttelse, registrering efter sikkerhedsbrud, automatiseret undersøgelse og anbefalet svar.|[Microsoft Defender for Endpoint – Windows-sikkerhed](../defender-endpoint/microsoft-defender-endpoint.md)|
|Microsoft Defender for Cloud Apps|Microsoft Defender for Cloud Apps er en omfattende saaS-løsning, der giver dig dyb synlighed, stærke datakontroller og forbedret trusselsbeskyttelse af dine cloudapps.|[Hvad er Defender for Cloud Apps?](/cloud-app-security/what-is-cloud-app-security)|
|Azure AD Identity Protection|Azure AD Identity Protection evaluerer risikodata fra milliarder af logonforsøg og bruger disse data til at evaluere risikoen for hvert logon til dit miljø. Disse data bruges af Azure AD til at tillade eller forhindre kontoadgang, afhængigt af hvordan politikker for betinget adgang er konfigureret. Azure AD Identity Protection gives i licens separat fra Microsoft 365 Defender. Det er inkluderet i Azure Active Directory Premium P2.|[Hvad er identitetsbeskyttelse?](/azure/active-directory/identity-protection/overview-identity-protection)|
||||

## <a name="microsoft-365-defender-architecture"></a>Microsoft 365 Defender arkitektur

Nedenstående diagram illustrerer arkitektur på højt niveau for vigtige Microsoft 365 Defender komponenter og integrationer. Der er angivet *en detaljeret* arkitektur for hver Defender-komponent og use case-scenarier i hele denne artikelserie.

:::image type="content" source="../../media/defender/m365-defender-eval-architecture.png" alt-text="En arkitektur på højt niveau i Microsoft 365 Defender-portalen" lightbox="../../media/defender/m365-defender-eval-architecture.png":::

I denne illustration:

- Microsoft 365 Defender kombinerer signalerne fra alle Defender-komponenterne for at levere udvidet registrering og svar (XDR) på tværs af domæner. Dette omfatter en samlet hændelseskø, automatiseret svar på stopangreb, selvreparerende (for kompromitterede enheder, brugeridentiteter og postkasser), jagt på tværs af trusler og trusselsanalyser.
- Microsoft Defender for Office 365 beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer. Den deler signaler fra disse aktiviteter med Microsoft 365 Defender. Exchange Online Protection (EOP) er integreret for at give end-to-end-beskyttelse af indgående mails og vedhæftede filer.
- Microsoft Defender for Identity indsamler signaler fra servere, der kører AD FS (Active Directory Federated Services) og AD DS (Active Directory i det lokale miljø Domain Services). Den bruger disse signaler til at beskytte dit hybride identitetsmiljø, herunder beskyttelse mod hackere, der bruger kompromitterede konti til at flytte tværgående på tværs af arbejdsstationer i det lokale miljø.
- Microsoft Defender for Endpoint indsamler signaler fra og beskytter enheder, der bruges af din organisation.
- Microsoft Defender for Cloud Apps indsamler signaler fra din organisations brug af cloudapps og beskytter data, der flyder mellem dit miljø og disse apps, herunder både godkendte og ikke-godkendte cloudapps.
- Azure AD Identity Protection evaluerer risikodata fra milliarder af logonforsøg og bruger disse data til at evaluere risikoen for hvert logon til dit miljø. Disse data bruges af Azure AD til at tillade eller forhindre kontoadgang, afhængigt af hvordan politikker for betinget adgang er konfigureret. Azure AD Identity Protection gives i licens separat fra Microsoft 365 Defender. Det er inkluderet i Azure Active Directory Premium P2.

## <a name="microsoft-siem-and-soar-can-use-data-from-microsoft-365-defender"></a>Microsoft SIEM og SOAR kan bruge data fra Microsoft 365 Defender

Yderligere valgfrie arkitekturkomponenter, der ikke er inkluderet i denne illustration:

- **Detaljerede signaldata fra alle Microsoft 365 Defender komponenter kan integreres i Microsoft Sentinel** og kombineres med andre logføringskilder for at tilbyde fuld SIEM- og SOAR-funktioner og -indsigt.
- Hvis du vil **have mere at vide om, hvordan du bruger Microsoft Sentinel, en Azure SIEM med Microsoft 365 Defender** som XDR, kan du se denne [oversigtsartikel](/azure/sentinel/microsoft-365-defender-sentinel-integration) og [trinnene til integration](/azure/sentinel/connect-microsoft-365-defender?tabs=MDE) af Microsoft Sentinel og Microsoft 365 Defender.
- Du kan få mere at vide om SOAR i Microsoft Sentinel (herunder links til playbooks i Microsoft Sentinel GitHub Repository) ved at læse [denne artikel](/azure/sentinel/automate-responses-with-playbooks).

## <a name="the-evaluation-process-for-microsoft-365-defender-cyber-security"></a>Evalueringsprocessen for Microsoft 365 Defender cybersikkerhed

Microsoft anbefaler, at du aktiverer komponenterne i Microsoft 365 i den illustrerede rækkefølge:

:::image type="content" source="../../media/defender/m365-defender-eval-process.png" alt-text="En evalueringsproces på højt niveau på Microsoft 365 Defender-portalen" lightbox="../../media/defender/m365-defender-eval-process.png":::

I følgende tabel beskrives denne illustration.

|  Serienummer   |Trin  |Beskrivelse  |
|------|---------|---------|
|1     | [Opret evalueringsmiljøet](eval-create-eval-environment.md)       |Dette trin sikrer, at du har prøvelicensen til Microsoft 365 Defender.         |
|2     | [Aktivér Defender for Identity](eval-defender-identity-overview.md)        | Gennemse arkitekturkravene, aktivér evalueringen, og gennemgå selvstudier til identifikation og afhjælpning af forskellige angrebstyper.   |
|3     | [Aktivér Defender for Office 365 ](eval-defender-office-365-overview.md)       | Sørg for, at du opfylder arkitekturkravene, aktivér evalueringen, og opret derefter pilotmiljøet. Denne komponent indeholder Exchange Online Protection, så du skal faktisk evaluere *begge* her.      |
|4     | [Aktivér Defender for Slutpunkt ](eval-defender-endpoint-overview.md)       | Sørg for, at du opfylder arkitekturkravene, aktivér evalueringen, og opret derefter pilotmiljøet.         |
|5     | [Aktivér Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)        |  Sørg for, at du opfylder arkitekturkravene, aktivér evalueringen, og opret derefter pilotmiljøet.        |
|6     | [Undersøg og reager på trusler](eval-defender-investigate-respond.md)        |   Simuler et angreb, og begynd at bruge funktioner til svar på hændelser.      |
|7     | [Hæv prøveversionen til produktion](eval-defender-promote-to-production.md)        | Hæv Microsoft 365-komponenterne til produktion én for én.        |

Dette er en almindeligt anbefalet rækkefølge, der er designet til hurtigt at udnytte værdien af egenskaberne baseret på, hvor meget indsats der typisk kræves for at udrulle og konfigurere egenskaberne. Defender for Office 365 kan f.eks. konfigureres på mindre tid, end det tager at tilmelde enheder til Defender for Endpoint. Du skal selvfølgelig prioritere komponenterne, så de opfylder dine forretningsbehov, og du kan aktivere dem i en anden rækkefølge.

## <a name="go-to-the-next-step"></a>Gå til næste trin

[Få mere at vide om og/eller opret det Microsoft 365 Defender evalueringsmiljø](eval-create-eval-environment.md)
