---
title: Overvåg og besvar hændelser om beskyttelse af personlige oplysninger i din organisation
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
description: Brug politikker for overvågning og beskeder og anmodninger fra den registrerede til at overvåge og besvare personlige datahændelser.
ms.openlocfilehash: 730eb42fdf6aed66f5beac69621981848ffa6510
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953321"
---
# <a name="monitor-and-respond-to-data-privacy-incidents-in-your-organization"></a>Overvåg og besvar hændelser om beskyttelse af personlige oplysninger i din organisation

Microsoft 365 funktioner er tilgængelige, som kan hjælpe dig med at overvåge, undersøge og reagere på hændelser om beskyttelse af personlige oplysninger i din organisation, når du anvender relaterede funktioner. Det kan også være vigtigt at have processer, procedurer og anden dokumentation til hver af disse for at vise overholdelse over for tilsynsorganer.

Disse omfatter: 

- Politikker for overvågning og beskeder
- Anmodninger fra fysiske personer (herunder indholdssøgning og eDiscovery)
- Yderligere undersøgelsesværktøjer og rapportering

## <a name="data-privacy-regulations-impacting-the-use-of-monitoring-and-response-tools"></a>Bestemmelser om beskyttelse af personlige oplysninger, der påvirker brugen af overvågnings- og svarværktøjer

Her er et eksempel på en liste over bestemmelser om beskyttelse af personlige oplysninger, der kan relatere til kontrolelementer for styring af oplysninger:

- LGPD-artikel 46
- LGPD-artikel 48
- GDPR-artikel (5)(1)(f)
- GDPR-artikel (15)(1)(e)
- HIPAA-HITECH (45 C.F.R. 164.308(a)(1)(ii)(D))
- HIPAA-HITECH (45 C.F.R. 164.308(a)(6)(ii)
- HIPAA-HITECH (45 C.F.R. 164.312(b))
- CCPA (1798.105(c))

Du kan finde flere oplysninger under [Vurder risici for beskyttelse af personlige oplysninger og identificer følsomme oplysninger](information-protection-deploy-assess.md).

Reglerne om beskyttelse af personlige oplysninger kræver generelt følgende for overvågning og svar:

- Overvågning, advarsler og rapportering for aktiviteter, der er relateret til lagring, deling og behandling af personlige data
- Muligheden for at besvare en DSR-anmodning (Data Subject Request) og i nogle tilfælde udføre undersøgelser og andre administrative foranstaltninger for at overholde sådanne anmodninger.

Din organisation ønsker måske også at udføre overvågnings- og svaraktiviteter til andre formål, f.eks. andre behov for overholdelse af angivne standarder eller af forretningsmæssige årsager. Oprettelse af din overvågnings- og svarordning for beskyttelse af personlige oplysninger skal udføres som en del af den overordnede planlægning, implementering og administration af overvågning og svar.

For at hjælpe dig med at komme i gang med et overvågnings- og svarskema i Microsoft 365 til bestemmelser om beskyttelse af personlige oplysninger indeholder denne artikel en liste over nyttige funktioner i Microsoft 365 til at besvare spørgsmål som f.eks.: 

- Hvilken slags daglige overvågnings-, undersøgelses- og rapporteringsteknikker er tilgængelige for de forskellige datatyper og kilder?
- Hvilke mekanismer skal der bruges til at håndtere DSR-anmodninger (data subject requests) og eventuelle afhjælpende handlinger, f.eks. anonymisering, redaction og sletning.

## <a name="auditing-and-alert-policies-in-the-security-and-compliance-center"></a>Politikker for overvågning og beskeder i Security and Compliance Center

Se disse artikler om konfiguration af overvågning, avanceret overvågning og beskedpolitikker:

- [Samlet overvågning](../compliance/search-the-audit-log-in-security-and-compliance.md)
- [Postkasseovervågning](../compliance/enable-mailbox-auditing.md)
- [Overvågning (Premium)](../compliance/advanced-audit.md)
- [Underretningspolitikker](../compliance/alert-policies.md)

## <a name="data-subject-requests-for-the-gdpr-and-ccpa"></a>Anmodninger fra fysiske personer for GDPR og CCPA

Se [Anmodninger fra fysiske personer for GDPR og CCPA for](/compliance/regulatory/gdpr-dsr-Office365) at få oplysninger om besvarelse af en DSR i Microsoft 365.

## <a name="manage-deleted-users-in-microsoft-stream"></a>Administrer slettede brugere i Microsoft Stream

For Microsoft Stream, når en bruger slettes fra Azure Active Directory (Azure AD), hvis vedkommendes navn var knyttet til en postet Stream-video før dette tidspunkt, forbliver vedkommendes mailadresse knyttet til videoen. Se [Administrer slettede brugere fra Microsoft Stream](/stream/managing-deleted-users) for at fjerne den.

## <a name="insider-risk-management-as-an-investigative-tool"></a>Insiderrisikostyring som undersøgelsesværktøj

[Styring af insiderrisiko](../compliance/insider-risk-management.md) er en funktion i Microsoft Purview-overholdelsesportalen, der hjælper dig med at minimere den interne risiko ved at gøre det muligt for dig at registrere, undersøge og reagere på risikable aktiviteter i din organisation.