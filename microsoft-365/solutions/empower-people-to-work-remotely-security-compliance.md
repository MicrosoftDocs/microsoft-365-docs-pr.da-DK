---
title: 'Trin 3: Installere sikkerhed og overholdelse for hybridmedarbejdere'
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
description: Brug Microsoft 365 og overholdelsestjenester til at beskytte dine apps, data og enheder for hybridmedarbejdere.
ms.openlocfilehash: 5ae369ffa41444e0cd2d3c6d28be470ede170b01
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63588240"
---
# <a name="step-3-deploy-security-and-compliance-for-hybrid-workers"></a>Trin 3: Installere sikkerhed og overholdelse for hybridmedarbejdere

For hybridmedarbejdere, som aldrig kommer til kontoret, eller som sjældent kommer ind, er sikkerhed og overholdelse en vigtig del af den overordnede løsning. Al deres kommunikation foregår via internettet i stedet for at være begrænset til et organisatorisk intranet.

Der er ting, du og dine medarbejdere kan gøre for at forblive produktive og samtidig reducere risikoen for cybersikkerhed og opretholde overholdelse af dine interne politikker og databestemmelser.

Fjernarbejde har brug for disse elementer af sikkerhed og overholdelse:

- Kontrolleret adgang til produktivitetsapps, som hybridmedarbejdere bruger, f.eks Microsoft Teams
- Kontrolleret adgang til og beskyttelse af data, som hybridmedarbejdere opretter og bruger, f.eks. chatsamtaler eller delte filer
- Beskyttelse af Windows 11 eller 10 enheder mod malware og andre typer cyberangreb
- Beskyttelse af mail, filer og websted med ensartet mærkning for følsomheds- og beskyttelsesniveauer
- Forebyggelse af lækerede oplysninger
- Overholdelse af regionale dataregler

Her er funktionerne i Microsoft 365, der leverer sikkerheds- og overholdelsestjenester for hybridmedarbejdere.

:::image type="content" source="../media/empower-people-to-work-remotely/remote-workers-security-compliance-grid.png" alt-text="Brug disse Microsoft 365-tjenester for at være sikre og kompatible" lightbox="../media/empower-people-to-work-remotely/remote-workers-security-compliance-grid.png":::

## <a name="security"></a>Sikkerhed

Beskyt dine programmer og data med disse sikkerhedsfunktioner i Microsoft 365.

|Funktionalitet eller funktion|Derfor skal jeg bruge det|Licensering|
|---|---|---|
|Microsoft Defender til Office 365|Beskyt dine Microsoft 365 apps og data – f.eks. mails, Office dokumenter og samarbejdsværktøjer – mod angreb. <p> Microsoft Defender for Office 365 indsamler og analyserer signaler fra dine apps til registrering, undersøgelse og afhjælpning af sikkerhedsrisici og beskytter din organisation mod skadelige trusler fra mails, links (URL'er) og samarbejdsværktøjer. Det giver også automatiseret lejerkonfigurationsvurdering og konfigurationsværktøj til standard- og streng sikkerhedsstillinger.|Microsoft 365 E3 eller E5|
|Beskyttelse mod malware|Microsoft Defender Antivirus Device Guard giver enhedsbaseret malwarebeskyttelse. <p> SharePoint Online scanner automatisk filuploads for kendt malware. <p> Exchange Online Protection (EOP) sikrer postkasser i skyen.|Microsoft 365 E3 eller E5|
|Microsoft Defender til Slutpunkt|Beskyt din organisations enheder mod cybertrusler og databribrider og registrer, undersøg og svar på avancerede trusler.|Microsoft 365 E5|
|Defender til skyapps|Beskyt dine skybaserede tjenester – både Microsoft 365 og andre SaaS-apps – mod angreb.|Microsoft 365 E5 eller individuelle Defender for Cloud Apps-licenser|
|Azure AD Identity Protection|Automatiser registrering og afhjælpning af identitetsbaserede risici. <p>Opret risikobaserede betingede Access-politikker, der kræver multifaktorgodkendelse (MFA) for risikabelt logon.|Microsoft 365 E5 eller E3 med Azure AD Premium P2-licenser|
||||

Det første trin skal være at lære om og bruge [Microsoft Secure Score](/microsoft-365/security/defender/microsoft-secure-score).

Se [Top 12-opgaver for sikkerhedsteams til at understøtte arbejde hjemmefra for at](../security/top-security-tasks-for-remote-work.md) få flere oplysninger.

Du kan finde oplysninger om sikkerhed på Microsoft 365 i [Microsoft 365 og sikkerhedsdokumentation](/microsoft-365/security).

## <a name="compliance"></a>Overholdelse af regler og standarder

Overser interne politikker eller lovmæssige krav med disse overholdelsesfunktioner i Microsoft 365.

|Funktionalitet eller funktion|Derfor skal jeg bruge det|Licensering|
|---|---|---|
|Følsomhedsmærkater|Klassificer og beskyt din organisations data uden at forhindre brugernes produktivitet og deres mulighed for at samarbejde ved at placere etiketter med forskellige beskyttelsesniveauer for mail, filer eller websteder.|Microsoft 365 E3 eller E5|
|DLP (Data Loss Protection)|Registrer, advar og bloker risikabelt, utilsigtet eller upassende deling, f.eks. deling af data, der indeholder personlige oplysninger, både internt og eksternt.|Microsoft 365 E3 eller E5|
|Betinget adgang til appkontrol|Undgå, at følsomme data overføres til brugernes personlige enheder.|Microsoft 365 E3 eller E5|
|Dataopbevaringsmærkater og -politikker|Implementer kontrolelementer til informationsstyring, f.eks. hvor lang tid data og krav vedrørende lagring af personlige data på kunder skal opbevares, så de overholder organisationens politikker eller databestemmelser.|Microsoft 365 E3 eller E5|
|Office (OME)|Send og modtag krypterede mails mellem personer i og uden for organisationen, der indeholder regulerede data, f.eks. personlige data for kunder.|Microsoft 365 E3 eller E5|
|Overholdelsesstyring|Administrer lovgivningsmæssige overholdelsesaktiviteter relateret til Microsofts skytjenester med dette værktøj til arbejdsprocesbaseret risikovurdering i Microsoft Service Trust Portal.|Microsoft 365 E3 eller E5|
|Overholdelsesstyring|Se et overordnet resultat for din aktuelle konfiguration af overholdelse og anbefalinger til forbedring af den Microsoft 365 Overholdelsescenter.|Microsoft 365 E3 eller E5|
|Kommunikationsoverholdelse|Registrer, registrer og tag afhjælpningshandlinger i forbindelse med upassende meddelelser i organisationen.|Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelses- eller Insider Risk Management-tilføjelses-|
|Insider Risk Management|Find, undersøg og handle på ondsindede og utilsigtede risici i organisationen. Microsoft 365 kan registrere disse typer af risici, selv når en medarbejder bruger en ikke-administreret enhed.|Microsoft 365 E5 eller Microsoft 365 E3 med tilføjelses- eller Insider Risk Management-tilføjelses-|
||||

Se [Hurtige opgaver for at komme i gang med Microsoft 365 overholdelse af regler](../compliance/compliance-quick-tasks.md) og standarder for at få flere oplysninger.

## <a name="results-of-step-3"></a>Resultater af trin 3

For dine hybridmedarbejdere har du implementeret:

- Sikkerhed
  - Kontrolleret adgang til apps og data, som hybridmedarbejdere bruger til at kommunikere og samarbejde
  - Malwarebeskyttelse til skytjenestedata, mail og Windows 11 eller 10 enheder
- Overholdelse af regler og standarder
  - Ensartet mærkning for følsomheds- og beskyttelsesniveauer
  - Politikker til at forhindre lækage af oplysninger
  - Overholdelse af regionale dataregler

## <a name="next-step"></a>Næste trin

[![Trin 4: Administrer dine enheder, pc'er og andre slutpunkter.](../media/empower-people-to-work-remotely/remote-workers-step-grid-4.png)](empower-people-to-work-remotely-manage-endpoints.md)

Fortsæt med [Trin 4](empower-people-to-work-remotely-manage-endpoints.md) for at administrere dine enheder, pc'er og andre slutpunkter.
