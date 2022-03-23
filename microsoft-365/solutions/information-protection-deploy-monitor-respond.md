---
title: Overvåg og svar på hændelser i forbindelse med beskyttelse af personlige oplysninger i din organisation
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 01/04/2021
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
ms.custom: ''
description: Brug overvågning og påmindelsespolitikker og anmodninger fra den registrerede til at overvåge og reagere på personlige datahændelser.
ms.openlocfilehash: 74efff60bb8e0ad6f170b57c86e384d3b689eee1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590898"
---
# <a name="monitor-and-respond-to-data-privacy-incidents-in-your-organization"></a>Overvåg og svar på hændelser i forbindelse med beskyttelse af personlige oplysninger i din organisation

Microsoft 365 tilgængelige funktioner, der kan hjælpe dig med at overvåge, undersøge og reagere på hændelser i forbindelse med beskyttelse af personlige oplysninger i organisationen, når du driftsiserer relaterede funktioner. Det kan også være vigtigt at have processer, procedurer og anden dokumentation til hver af disse for at demonstrere overholdelse af lovbestemmelser.

Disse omfatter: 

- Overvågning og beskedpolitikker
- Anmodninger fra den registrerede (herunder indholdssøgning og eDiscovery)
- Yderligere nyttige værktøjer og rapportering

## <a name="data-privacy-regulations-impacting-the-use-of-monitoring-and-response-tools"></a>Regler for beskyttelse af personlige oplysninger for data, der påvirker brugen af overvågnings- og svarværktøjer

Her er et eksempel på en liste over bestemmelser om beskyttelse af personlige oplysninger, der kan være relateret til styring af oplysninger:

- LGPD artikel 46
- LGPD-artikel 48
- GDPR-artikel (5)(1)(f)
- GDPR-artikel (15)(1)(e)
- HIPAA-HITECH (45 C.F.R. 164.308(a)(1)(ii)(D))
- HIPAA-HITECH (45 C.F.R. 164.308(a)(6)(ii)
- HIPAA-HITECH (45 C.F.R. 164.312(b))
- CCPA (1798.105(c))

Få mere at vide under [Vurder risici i forbindelse med beskyttelse af data og identificer følsomme oplysninger](information-protection-deploy-assess.md).

Reglerne for beskyttelse af personlige oplysninger for data kræver generelt følgende for overvågning og svar:

- Overvågning, påmindelse og rapportering for aktiviteter vedrørende lagring, deling og behandling af personlige data
- Muligheden for at besvare en anmodning fra den registrerede (DSR) og i nogle tilfælde udføre handlinger, der kræver handling, og andre administrative foranstaltninger for at overholde sådanne anmodninger.

Din organisation kan også ønske at udføre overvågnings- og svaraktiviteter til andre formål, f.eks. andre overholdelsesbehov eller af forretningsmæssige årsager. Når du etablerer overvågnings- og svarskemaet for beskyttelse af data, skal det gøres som en del af den overordnede planlægning af overvågning og svar, implementering og administration.

For at hjælpe dig med at komme i gang med et overvågnings- og svarskema i Microsoft 365 for regler om beskyttelse af personlige oplysninger for data viser denne artikel nyttige funktioner i Microsoft 365 til at besvare spørgsmål som f.eks.: 

- Hvilken slags daglig overvågning, overvågning og rapporteringsteknikker er tilgængelige for de forskellige datatyper og -kilder?
- Hvilke mekanismer er nødvendige for at håndtere anmodninger fra registrerede og eventuelle afhjælpende handlinger, f.eks anonymisering, redaction og sletning.

## <a name="auditing-and-alert-policies-in-the-security-and-compliance-center"></a>Overvågning og beskedpolitikker i Security and Compliance Center

Se disse artikler for at konfigurere overvågning, avanceret overvågning og beskedpolitikker:

- [Samlet overvågning](../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Overvågning af postkasse](../compliance/enable-mailbox-auditing.md)
- [Avanceret overvågning](../compliance/advanced-audit.md)
- [Beskedpolitikker](../compliance/alert-policies.md)

## <a name="data-subject-requests-for-the-gdpr-and-ccpa"></a>Anmodninger fra den registrerede om GDPR og CCPA

Se [Anmodninger fra den registrerede om GDPR og CCPA](/compliance/regulatory/gdpr-dsr-Office365) for at få oplysninger om besvarelse af en DSR Microsoft 365.

## <a name="manage-deleted-users-in-microsoft-stream"></a>Administrer slettede brugere i Microsoft Stream

Når en bruger i Microsoft Stream slettes fra Azure Active Directory (Azure AD), forbliver brugerens mailadresse knyttet til videoen, hvis brugerens navn er knyttet til en stream-video, der er udgivet før dette tidspunkt. Se [Administrer slettede brugere fra Microsoft Stream for](/stream/managing-deleted-users) at fjerne den.

## <a name="insider-risk-management-as-an-investigative-tool"></a>Insider-risikostyring som et værktøj til at tilsnive risici

[Insider-risikostyring i Microsoft 365](../compliance/insider-risk-management.md) er en funktion i Microsoft Compliance Admin center, som kan hjælpe dig med at minimere den interne risiko ved at gøre det muligt for dig at registrere, undersøge og handle på risikabelt arbejde i din organisation.