---
title: Indstillinger for overholdelse Microsoft 365 grupper, Teams og SharePoint samarbejde
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
description: Få mere at vide om indstillinger for Microsoft 365 for grupper, Teams og SharePoint samarbejde.
ms.openlocfilehash: ab840ea5652a13087ecc8d505391bac152ca1052
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/17/2021
ms.locfileid: "63591549"
---
# <a name="compliance-options-for-microsoft-365-groups-teams-and-sharepoint-collaboration"></a>Indstillinger for overholdelse Microsoft 365 grupper, Teams og SharePoint samarbejde

Microsoft 365 tilbyder en komplet pakke med værktøjer til at opretholde overholdelse af regler og standarder, efterhånden som brugerne samarbejder. Gennemgå disse muligheder, og overvej, hvordan de kortlægger dine forretningsmæssige behov, følsomheden af dine data og omfanget af personer, som dine brugere skal samarbejde med.

Den følgende tabel giver en hurtig reference til de kontrolelementer til overholdelse af regler og standarder, der er tilgængelige Microsoft 365. Yderligere oplysninger findes i de følgende afsnit.

|Kategori|Beskrivelse|Reference|
|:-------|:----------|:--------|
|Opbevaring af oplysninger|||
||Bevare grupper, mail og SharePoint indhold|[Få mere at vide om opbevaringspolitikker for SharePoint og OneDrive](../compliance/retention-policies-sharepoint.md)|
||Behold chat og meddelelser|[Få mere at vide om opbevaringspolitikker for Microsoft Teams](../compliance/retention-policies-teams.md)|
|Klassificering af oplysninger|||
||Klassificer grupper og teams|[Brug følsomhedsetiketter til at beskytte indhold Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md)|
||Klassificer automatisk følsomt indhold|[Anvend en følsomhedsmærkat på indhold automatisk](../compliance/apply-sensitivity-label-automatically.md)|
||Kryptér følsomt indhold|[Begræns adgangen til indhold ved at bruge følsomhedsmærkater til at anvende kryptering](../compliance/encryption-sensitivity-labels.md)|
|Beskyttelse af oplysninger|||
||Undgå tab af følsomme oplysninger|[Få mere at vide om forebyggelse af datatab](../compliance/dlp-learn-about-dlp.md)|
||Beskyt følsomme oplysninger i chat.|[Forebyggelse af datatab og Microsoft Teams](../compliance/dlp-microsoft-teams.md)|
||Definere organisationens følsomme oplysninger|[Brugerdefinerede typer af følsomme oplysninger](../compliance/sensitive-information-type-learn-about.md)|
|Brugersegmentering|||
||Begræns kommunikationen mellem brugersegmenter|[Informationsbarrierer](../compliance/information-barriers.md)|
|Dataopbevaring|||
||Store data i bestemte geoplaceringer|[Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)|

## <a name="information-retention"></a>Opbevaring af oplysninger

Opbevaringspolitikker er tilgængelige til at bevare eller slette elementer, der bruges til samarbejde i grupper og teams, herunder filer, meddelelser og mail. Politikker kan indstilles til at bevare og slette, kun at bevare eller slette. Oplysninger, der er dækket af en opbevaringspolitik, er beskyttet, hvis gruppen eller teamet udløber eller på anden måde slettes.

Konfiguration af en opbevaringspolitik for Microsoft 365 grupper dækker gruppepostkassen og de tilknyttede SharePoint websted og filer.

- [Få mere at vide om opbevaringspolitikker for SharePoint og OneDrive](../compliance/retention-policies-sharepoint.md)

Opbevaringspolitikker for at Teams bevare chat- og kanalmeddelelser. Mens chat- og kanalmeddelelser er gemt i Exchange postkasser, påvirkes de ikke Exchange opbevaringspolitikker. Du skal angive dine opbevaringspolitikker for at gælde for Teams chats og Teams kanalmeddelelser. 

Brugerchatsamtaler bevares på ubestemt tid, selvom en brugerkonto slettes. Hvis du ikke vil bevare disse data på ubestemt tid, kan du overveje at bruge en opbevaringspolitik til at slette brugerchats efter et bestemt tidsrum eller medtage denne sletning i din brugers sletningsproces.

- [Få mere at vide om opbevaringspolitikker for Microsoft Teams](../compliance/retention-policies-teams.md)

- [Opbevaringspolitikker i Microsoft Teams](/microsoftteams/retention-policies)

En enkelt opbevaringspolitik kan indstilles til at gælde for Teams chat og Teams kanalmeddelelser. 

Flere ressourcer:

- [Få mere at vide om opbevaringspolitikker](../compliance/retention.md)

- [Opbevaringsmærker og opbevaringspolitikker](/exchange/security-and-compliance/messaging-records-management/retention-tags-and-policies) i Exchange

## <a name="information-classification"></a>Klassificering af oplysninger

Du kan bruge følsomhedsmærkater til at styre gæsteadgang, gruppe- og teamsikkerhed og adgang for ikke-administrerede enheder for grupper og teams. Når etiketten anvendes, konfigureres disse indstillinger automatisk efter de angivne navneindstillinger.

- [Brug følsomhedsetiketter til at beskytte indhold Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md)

Du kan konfigurere Microsoft 365 til automatisk at anvende følsomhedsmærkater på filer og mails baseret på de kriterier, du angiver, herunder registrering af følsomme oplysningstyper eller mønstre, der matcher med trænbare klassificeringer.

- [Anvend en følsomhedsmærkat på indhold automatisk](../compliance/apply-sensitivity-label-automatically.md)

Du kan bruge følsomhedsmærkater til at kryptere filer, så kun personer med tilladelse til at dekryptere og læse dem.

- [Begræns adgangen til indhold ved at bruge følsomhedsmærkater til at anvende kryptering](../compliance/encryption-sensitivity-labels.md)

- [Konfigurere et team med sikkerhedsisolation](./secure-teams-security-isolation.md)

Flere ressourcer:

- [Få mere at vide om følsomhedsmærkater](../compliance/sensitivity-labels.md)


## <a name="information-protection"></a>Beskyttelse af oplysninger

DLP-politikker kan forhindre utilsigtet deling af følsomme oplysninger på tværs SharePoint, Exchange og Teams. Du kan oprette politikker, der angiver handlinger, der skal udføre (f.eks. blokere adgang), baseret på et sæt regler.

- [Få mere at vide om forebyggelse af datatab](../compliance/dlp-learn-about-dlp.md)

DLP i Teams kan hjælpe med at beskytte følsomme oplysninger i Teams chat og kanalmeddelelser ved at slette meddelelser, der indeholder følsomme oplysninger.

- [Forebyggelse af datatab og Microsoft Teams](../compliance/dlp-microsoft-teams.md)

Hvis du har følsomme oplysninger, der er unikke for din organisation, f.eks. projektkodenavne, kan du oprette dine egne typer af følsomme oplysninger og anvende dem på DLP-politikker for at beskytte indhold i grupper, teams og SharePoint.

- [Brugerdefinerede typer af følsomme oplysninger](../compliance/sensitive-information-type-learn-about.md)

## <a name="user-segmentation"></a>Brugersegmentering

Med informationsbarrierer kan du segmentere dine data og brugere for at begrænse uønsket kommunikation og samarbejde mellem grupper og undgå interessekonflikter i organisationen. Informationsbarrierer gør det muligt at oprette politikker, der tillader eller forhindrer filsamarbejde, chat, opkald eller mødeinvitationer mellem grupper af personer i organisationen.

- [Informationsbarrierer](../compliance/information-barriers.md)

- [Informationsbarrierer i Microsoft Teams](/microsoftteams/information-barriers-in-teams)

- [Brug informationsbarrierer med SharePoint](/sharepoint/information-barriers)

## <a name="data-residency"></a>Dataopbevaring

Med Microsoft 365 multi-geo kan du klargøre og gemme in restdata på de geoplaceringer, du har valgt at opfylde krav til dataopbevaring. I et Multi-Geo-miljø består din Microsoft 365-lejer af en central placering (hvor dit Microsoft 365-abonnement oprindeligt blev klargjort), og en eller flere satellitplaceringer, hvor du kan gemme data.

- [Microsoft 365 Multi-Geo](/microsoft-365/enterprise/microsoft-365-multi-geo)

- [Plan for Microsoft 365 multi-geo](/microsoft-365/enterprise/plan-for-multi-geo)

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Sikkerhed og overholdelse af regler og Exchange Online](/exchange/security-and-compliance/security-and-compliance)

[Beskyt oplysninger](../compliance/information-protection.md)
