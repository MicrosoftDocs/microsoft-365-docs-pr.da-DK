---
title: Indstillinger for overholdelse af angivne standarder for Microsoft 365 grupper, Teams og SharePoint samarbejde
ms.reviewer: ''
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-collaboration
- m365solution-collabgovernance
ms.custom:
- M365solutions
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om indstillinger for overholdelse af angivne standarder for Microsoft 365 grupper, Teams og SharePoint samarbejde.
ms.openlocfilehash: afbbc6e507d613e028f65dbc157ec2222414af8c
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939120"
---
# <a name="compliance-options-for-microsoft-365-groups-teams-and-sharepoint-collaboration"></a>Indstillinger for overholdelse af angivne standarder for Microsoft 365 grupper, Teams og SharePoint samarbejde

Microsoft 365 tilbyder en komplet pakke af værktøjer til at opretholde overholdelse af angivne standarder, i takt med at dine brugere samarbejder. Gennemse disse indstillinger, og overvej, hvordan de knyttes til dine forretningsbehov, følsomheden af dine data og omfanget af personer, som dine brugere skal samarbejde med.

Følgende tabel indeholder en hurtig reference til de kontrolelementer til overholdelse af angivne standarder, der er tilgængelige i Microsoft 365. Du kan finde flere oplysninger i følgende afsnit.

|Kategori|Beskrivelse|Reference|
|:-------|:----------|:--------|
|Opbevaring af oplysninger|||
||Bevar gruppers mail og SharePoint indhold|[Få mere at vide om opbevaringspolitikker for SharePoint og OneDrive](../compliance/retention-policies-sharepoint.md)|
||Bevar chat og meddelelser|[Få mere at vide om opbevaringspolitikker for Microsoft Teams](../compliance/retention-policies-teams.md)|
|Informationsklassificering|||
||Klassificer grupper og teams|[Brug følsomhedsmærkater til at beskytte indhold på Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Klassificer automatisk følsomt indhold|[Anvend automatisk en følsomhedsmærkat på indhold](../compliance/apply-sensitivity-label-automatically.md)|
||Kryptér følsomt indhold|[Begræns adgangen til indhold ved at bruge følsomhedsmærkater til at anvende kryptering](../compliance/encryption-sensitivity-labels.md)|
|Beskyttelse af oplysninger|||
||Undgå tab af følsomme oplysninger|[Få mere at vide om Forebyggelse af datatab i Microsoft Purview](../compliance/dlp-learn-about-dlp.md)|
||Beskyt følsomme oplysninger i chat.|[Microsoft Purview Forebyggelse og Microsoft Teams af datatab](../compliance/dlp-microsoft-teams.md)|
||Definer organisationens følsomme oplysninger|[Brugerdefinerede typer følsomme oplysninger](../compliance/sensitive-information-type-learn-about.md)|
|Brugersegmentering|||
||Begræns kommunikationen mellem brugersegmenter|[Informationsbarrierer](../compliance/information-barriers.md)|
|Dataopbevaring|||
||Store data på bestemte geografiske placeringer|[Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)|

## <a name="information-retention"></a>Opbevaring af oplysninger

Opbevaringspolitikker er tilgængelige til at gemme eller slette elementer, der bruges til samarbejde i grupper og teams, herunder filer, meddelelser og mail. Politikker kan angives til at bevare og slette, kun at bevare eller slette. Oplysninger, der er omfattet af en opbevaringspolitik, er beskyttet, hvis gruppen eller teamet udløber eller på anden måde slettes.

Konfiguration af en opbevaringspolitik for Microsoft 365-grupper dækker gruppepostkassen og de tilknyttede SharePoint websted og filer.

- [Få mere at vide om opbevaringspolitikker for SharePoint og OneDrive](../compliance/retention-policies-sharepoint.md)

Opbevaringspolitikker for Teams bevare chat- og kanalmeddelelser. Selvom chat- og kanalmeddelelser gemmes i Exchange postkasser, påvirkes de ikke af Exchange opbevaringspolitikker. Du skal angive, at dine opbevaringspolitikker skal gælde for Teams chats og Teams kanalmeddelelser. 

Brugerchat gemmes på ubestemt tid, selvom en brugerkonto slettes. Hvis du ikke vil bevare disse data på ubestemt tid, kan du overveje at bruge en opbevaringspolitik til at slette brugerchats efter et angivet tidspunkt eller medtage denne sletning i din brugers sletningsproces.

- [Få mere at vide om opbevaringspolitikker for Microsoft Teams](../compliance/retention-policies-teams.md)

- [Opbevaringspolitikker i Microsoft Teams](/microsoftteams/retention-policies)

En enkelt opbevaringspolitik kan indstilles til at gælde for Teams chat og Teams kanalmeddelelser. 

Flere ressourcer:

- [Få mere at vide om opbevaringspolitikker](../compliance/retention.md)

- [Opbevaringskoder og opbevaringspolitikker](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) i Exchange

## <a name="information-classification"></a>Informationsklassificering

Du kan bruge følsomhedsmærkater til at styre gæsteadgang, gruppe- og teambeskyttelse og adgang for ikke-administrerede enheder for grupper og teams. Ved at anvende mærkaten konfigureres disse indstillinger automatisk som angivet i etiketindstillingerne.

- [Brug følsomhedsmærkater til at beskytte indhold på Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md)

Du kan konfigurere Microsoft 365 til automatisk at anvende følsomhedsmærkater på filer og mails baseret på de kriterier, du angiver, herunder registrering af følsomme informationstyper eller mønster, der matcher med klassificeringer, der kan oplæres.

- [Anvend automatisk en følsomhedsmærkat på indhold](../compliance/apply-sensitivity-label-automatically.md)

Du kan bruge følsomhedsmærkater til at kryptere filer, så det kun er dem, der har tilladelse til at dekryptere og læse dem.

- [Begræns adgangen til indhold ved at bruge følsomhedsmærkater til at anvende kryptering](../compliance/encryption-sensitivity-labels.md)

- [Konfigurer et team med sikkerhedsisolering](./secure-teams-security-isolation.md)

Flere ressourcer:

- [Få mere at vide om følsomhedsmærkater](../compliance/sensitivity-labels.md)


## <a name="information-protection"></a>Beskyttelse af oplysninger

DLP-politikker kan forhindre utilsigtet deling af følsomme oplysninger på tværs af SharePoint, Exchange og Teams. Du kan oprette politikker, der angiver handlinger, der skal udføres (f.eks. blokering af adgang), baseret på et sæt regler.

- [Få mere at vide om forebyggelse af datatab](../compliance/dlp-learn-about-dlp.md)

DLP i Teams kan hjælpe med at beskytte følsomme oplysninger i Teams chat- og kanalmeddelelser ved at slette meddelelser, der indeholder følsomme oplysninger.

- [Forebyggelse og Microsoft Teams af datatab](../compliance/dlp-microsoft-teams.md)

Hvis du har følsomme oplysninger, der er entydige for din organisation, f.eks. projektkodenavne, kan du oprette dine egne følsomme oplysningstyper og anvende dem på DLP-politikker for at beskytte indhold i grupper, teams og SharePoint.

- [Brugerdefinerede typer følsomme oplysninger](../compliance/sensitive-information-type-learn-about.md)

## <a name="user-segmentation"></a>Brugersegmentering

Med informationsbarrierer kan du segmentere dine data og brugere for at begrænse uønsket kommunikation og samarbejde mellem grupper og undgå interessekonflikter i din organisation. Med informationsbarrierer kan du oprette politikker, der tillader eller forhindrer filsamarbejde, chat, opkald eller mødeinvitationer mellem grupper af personer i din organisation.

- [Informationsbarrierer](../compliance/information-barriers.md)

- [Informationsbarrierer i Microsoft Teams](/microsoftteams/information-barriers-in-teams)

- [Brug informationsbarrierer med SharePoint](/sharepoint/information-barriers)

## <a name="data-residency"></a>Dataopbevaring

Med Microsoft 365 Multi-Geo kan du klargøre og gemme inaktive data på de geografiske placeringer, du har valgt at opfylde kravene til dataopbevaring. I et Multi-Geo-miljø består din Microsoft 365 lejer af en central placering (hvor dit Microsoft 365 abonnement oprindeligt blev klargjort) og en eller flere satellitplaceringer, hvor du kan gemme data.

- [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)

- [Plan for Microsoft 365 Multi-Geo](/microsoft-365/enterprise/plan-for-multi-geo)

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Sikkerhed og overholdelse af angivne standarder for Exchange Online](/exchange/security-and-compliance/security-and-compliance)

[Beskyt oplysninger](../compliance/information-protection.md)
