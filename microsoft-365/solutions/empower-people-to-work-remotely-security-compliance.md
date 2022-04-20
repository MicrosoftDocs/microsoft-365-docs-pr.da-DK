---
title: 'Trin 3: Udrul sikkerhed og overholdelse af angivne standarder for hybride arbejdere'
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Brug Microsoft 365 tjenester til sikkerhed og overholdelse af angivne standarder til at beskytte dine apps, data og enheder til hybridarbejdere.
ms.openlocfilehash: 08771de0f9e833405da308fb645b5fb5c906c543
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937779"
---
# <a name="step-3-deploy-security-and-compliance-for-hybrid-workers"></a>Trin 3: Udrul sikkerhed og overholdelse af angivne standarder for hybride arbejdere

For hybride arbejdere, hvoraf nogle aldrig går ind på kontoret, eller som sjældent går, er sikkerhed og overholdelse af angivne standarder en vigtig del af den overordnede løsning. Al kommunikation sker via internettet i stedet for at være begrænset til et organisationsintranet.

Der er ting, du og dine medarbejdere kan gøre for at forblive produktive og samtidig reducere cybersikkerhedsrisikoen og opretholde overholdelse af dine interne politikker og dataregler.

Fjernarbejde har brug for disse elementer af sikkerhed og overholdelse af angivne standarder:

- Kontrolleret adgang til produktivitetsapps, som hybridarbejdere bruger, f.eks. Microsoft Teams
- Kontrolleret adgang til og beskyttelse af de data, som hybridarbejdere opretter og bruger, f.eks. chatsamtaler eller delte filer
- Beskyttelse af Windows 11 eller 10 enheder mod malware og andre typer cyberangreb
- Beskyttelse af mail, filer og websted med ensartet mærkning for følsomheds- og beskyttelsesniveauer
- Forebyggelse af lækkede oplysninger
- Overholdelse af regionale dataregler

Her er funktionerne i Microsoft 365, der leverer tjenester til sikkerhed og overholdelse af angivne standarder for hybridarbejdere.

:::image type="content" source="../media/empower-people-to-work-remotely/remote-workers-security-compliance-grid.png" alt-text="Brug disse Microsoft 365-tjenester til at forblive sikre og kompatible" lightbox="../media/empower-people-to-work-remotely/remote-workers-security-compliance-grid.png":::

## <a name="security"></a>Sikkerhed

Beskyt dine programmer og data med disse sikkerhedsfunktioner i Microsoft 365.

|Funktionalitet eller funktion|Hvorfor jeg har brug for det|Licensering|
|---|---|---|
|Microsoft Defender for Office 365|Beskyt dine Microsoft 365 apps og data – f.eks. mails, Office dokumenter og samarbejdsværktøjer – mod angreb. <p> Microsoft Defender for Office 365 indsamler og analyserer signaler fra dine apps til registrering, undersøgelse og afhjælpning af sikkerhedsrisici og beskytter din organisation mod skadelige trusler fra mails, links (URL-adresser) og samarbejdsværktøjer. Det giver også automatiseret lejerkonfigurationsvurdering og konfigurationsværktøjer til standard- og strenge sikkerhedsholdninger.|Microsoft 365 E3 eller E5|
|Beskyttelse mod skadelig software|Microsoft Defender Antivirus og Device Guard yder enhedsbaseret beskyttelse mod skadelig software. <p> SharePoint Online scanner automatisk filoverførsler for kendt malware. <p> Exchange Online Protection (EOP) sikrer cloudpostkasser.|Microsoft 365 E3 eller E5|
|Microsoft Defender for Endpoint|Beskyt din organisations enheder mod cybertrusler og brud på datasikkerheden, og registrer, undersøg og reager på avancerede trusler.|Microsoft 365 E5|
|Defender for Cloud Apps|Beskyt dine cloudbaserede tjenester – både Microsoft 365 og andre SaaS-apps – mod angreb.|Microsoft 365 E5 eller individuelle Defender for Cloud Apps-licenser|
|Azure AD Identity Protection|Automatiser registrering og afhjælpning af identitetsbaserede risici. <p>Opret risikobaserede politikker for betinget adgang for at kræve multifaktorgodkendelse for risikobetonede logons.|Microsoft 365 E5 eller E3 med Azure AD Premium P2-licenser|
||||

Det første trin bør være at få mere at vide om og bruge [Microsoft Secure Score](/microsoft-365/security/defender/microsoft-secure-score).

Se [Top 12-opgaver, som sikkerhedsteams kan understøtte, når de arbejder hjemmefra](../security/top-security-tasks-for-remote-work.md) , for at få flere oplysninger.

Du kan få flere oplysninger om sikkerhed på tværs af Microsoft 365 [i Microsoft 365 sikkerhedsdokumentation](/microsoft-365/security).

## <a name="compliance"></a>Overholdelse af angivne standarder

Overhold interne politikker eller lovmæssige krav med disse funktioner til overholdelse af angivne standarder i Microsoft 365.

|Funktionalitet eller funktion|Hvorfor jeg har brug for det|Licensering|
|---|---|---|
|Følsomhedsmærkater|Klassificer og beskyt din organisations data uden at hindre brugernes produktivitet og deres mulighed for at samarbejde ved at placere mærkater med forskellige beskyttelsesniveauer på mail, filer eller websteder.|Microsoft 365 E3 eller E5|
|DLP (Data Loss Protection)|Registrer, advar og bloker risikable, utilsigtede eller upassende deling, f.eks. deling af data, der indeholder personlige oplysninger, både internt og eksternt.|Microsoft 365 E3 eller E5|
|Appkontrol med betinget adgang|Undgå, at følsomme data downloades til brugernes personlige enheder.|Microsoft 365 E3 eller E5|
|Dataopbevaringsmærkater og -politikker|Implementer styringskontroller for oplysninger, f.eks. hvor længe data og krav om opbevaring af personlige data om kunder skal bevares, for at overholde organisationens politikker eller dataregler.|Microsoft 365 E3 eller E5|
|Microsoft Purview-meddelelsekryptering|Send og modtag krypterede mails mellem personer i og uden for din organisation, der indeholder regulerede data, f.eks. personlige data om kunder.|Microsoft 365 E3 eller E5|
|Overholdelsesstyring|Administrer aktiviteter for lovmæssig overholdelse af angivne standarder, der er relateret til Microsofts cloudtjenester, med dette arbejdsprocesbaserede risikovurderingsværktøj på Microsoft Service Trust Portal.|Microsoft 365 E3 eller E5|
|Overholdelsesstyring|Se en samlet score for din aktuelle konfiguration af overholdelse af angivne standarder og anbefalinger til forbedring af den på Microsoft Purview-overholdelsesportalen.|Microsoft 365 E3 eller E5|
|Kommunikation med overholdelse af angivne standarder|Registrer, hent og udfør afhjælpningshandlinger for upassende meddelelser i din organisation.|Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelserne Overholdelse eller Insider Risk Management|
|Styring af insiderrisiko|Registrer, undersøg og håndter skadelige og utilsigtede risici i din organisation. Microsoft 365 kan registrere disse typer risici, selv når en arbejder bruger en ikke-administreret enhed.|Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelserne Overholdelse eller Insider Risk Management|
||||

Se [Hurtige opgaver for at komme i gang med Microsoft Purview](../compliance/compliance-quick-tasks.md) for at få flere oplysninger.

## <a name="results-of-step-3"></a>Resultater af trin 3

For dine hybridarbejdere har du implementeret:

- Sikkerhed
  - Kontrolleret adgang til apps og data, som hybridarbejdere bruger til at kommunikere og samarbejde
  - Beskyttelse mod skadelig software til cloudtjenestedata, mail og Windows 11 eller 10 enheder
- Overholdelse af angivne standarder
  - Ensartet mærkning af følsomheds- og beskyttelsesniveauer
  - Politikker til forebyggelse af informationsfejl
  - Overholdelse af regionale dataregler

## <a name="next-step"></a>Næste trin

[![Trin 4: Administrer dine enheder, pc'er og andre slutpunkter.](../media/empower-people-to-work-remotely/remote-workers-step-grid-4.png)](empower-people-to-work-remotely-manage-endpoints.md)

Fortsæt med [Trin 4](empower-people-to-work-remotely-manage-endpoints.md) for at administrere dine enheder, pc'er og andre slutpunkter.
