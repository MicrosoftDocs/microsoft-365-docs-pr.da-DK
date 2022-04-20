---
title: Brug overvågning af deling i overvågningsloggen
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MOE150
- BCS160
- MET150
ms.collection:
- M365-security-compliance
- SPO_Content
ms.assetid: 50bbf89f-7870-4c2a-ae14-42635e0cfc01
description: Administratoren kan få mere at vide om, hvordan du bruger deling af overvågning i Microsoft 365 overvågningslog til at identificere ressourcer, der deles med brugere uden for deres organisation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 7643dfae2e7e9fa871976cfe92bdf7028e756d3e
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64934483"
---
# <a name="use-sharing-auditing-in-the-audit-log"></a>Brug overvågning af deling i overvågningsloggen

Deling er en vigtig aktivitet i SharePoint Online og OneDrive for Business, og den bruges i vid udstrækning i organisationer. Administratorer kan bruge deling af overvågning i overvågningsloggen til at bestemme, hvordan deling bruges i deres organisation. 
  
## <a name="the-sharepoint-sharing-schema"></a>Skemaet SharePoint deling

Delingshændelser (ikke hændelser, der er relateret til delingspolitik og delingslinks) adskiller sig fra fil- og mapperelaterede hændelser på én primær måde: Én bruger udfører en handling, der har indflydelse på en anden bruger. Når en ressource f.eks. bruger A giver Bruger B adgang til en fil. I dette eksempel er Bruger A den  *fungerende bruger*  , og Bruger B er  *destinationsbrugeren*. I skemaet SharePoint fil påvirker den fungerende brugers handling kun selve filen. Når Bruger A åbner en fil, er den fungerende bruger de eneste oplysninger, der skal bruges i **hændelsen FileAccessed** . For at løse denne forskel er der et separat skema, der kaldes *SharePoint Delingsskema*, som henter flere oplysninger om delingshændelser. Dette sikrer, at administratorer har indblik i, hvem der delte en ressource, og den bruger, som ressourcen blev delt med. 
  
Delingsskemaet indeholder to ekstra felter i en overvågningspost, der er relateret til delingshændelser: 
  
- **TargetUserOrGroupType:** Identificerer, om målbrugeren eller -gruppen er medlem, gæst, SharePointGroup, sikkerhedsgruppe eller partner.

- **TargetUserOrGroupName:** Gemmer UPN eller navnet på den destinationsbruger eller gruppe, som en ressource blev delt med (Bruger B i det forrige eksempel). 

Disse to felter kan ud over andre egenskaber fra overvågningslogskemaet, f.eks. Bruger, Handling og Dato, fortælle hele historien om  *, hvilken*  bruger  *der*  har delt hvilken ressource med  *hvem*  og  *hvornår*. 
  
Der er en anden skemaegenskab, der er vigtig for delingshistorien. Når du eksporterer søgeresultater i overvågningsloggen, gemmes der oplysninger om deling af hændelser i kolonnen **AuditData** i den eksporterede CSV-fil. Når en bruger f.eks. deler et websted med en anden bruger, opnås dette ved at føje destinationsbrugeren til en SharePoint gruppe. Kolonnen **AuditData** henter disse oplysninger for at angive kontekst for administratorer. Se [Trin 2](#step-2-use-the-powerquery-editor-to-format-the-exported-audit-log) for at få oplysninger om, hvordan du fortolker oplysningerne i kolonnen **AuditData** .

## <a name="sharepoint-sharing-events"></a>SharePoint delingshændelser

Deling defineres ved, hvornår en bruger (den *fungerende* bruger) ønsker at dele en ressource med en anden bruger ( *målbrugeren* ). Overvåg poster, der er relateret til deling af en ressource med en ekstern bruger (en bruger uden for organisationen og ikke har en gæstekonto i organisationens Azure Active Directory) identificeres af følgende hændelser, som logføres i overvågningsloggen:

- **SharingInvitationCreated:** En bruger i organisationen forsøgte at dele en ressource (sandsynligvis et websted) med en ekstern bruger. Dette resulterer i en ekstern delingsinvitation, der sendes til destinationsbrugeren. Der gives ikke adgang til ressourcen på nuværende tidspunkt.

- **SharingInvitationAccepted:** Den eksterne bruger har accepteret invitationen til deling, der er sendt af den fungerende bruger, og har nu adgang til ressourcen.

- **AnonymousLinkCreated:** Der oprettes et anonymt link (også kaldet et link til alle) for en ressource. Da et anonymt link kan oprettes og derefter kopieres, er det rimeligt at antage, at alle dokumenter, der har et anonymt link, er blevet delt med en destinationsbruger.

- **AnonymousLinkUsed:** Som navnet antyder, logføres denne hændelse, når der bruges et anonymt link til at få adgang til en ressource. 

- **SecureLinkCreated:** En bruger har oprettet et "link til bestemte personer" for at dele en ressource med en bestemt person. Denne destinationsbruger kan være en person, der er ekstern i forhold til din organisation. Den person, som ressourcen er delt med, identificeres i overvågningsposten for hændelsen **AddedToSecureLink** . Tidsstemplerne for disse to hændelser er næsten identiske.

- **AddedToSecureLink:** En bruger blev føjet til et bestemt personlink. Brug feltet **TargetUserOrGroupName** i denne hændelse til at identificere den bruger, der er føjet til det tilsvarende link for bestemte personer. Denne destinationsbruger kan være en person, der er ekstern i forhold til din organisation.

## <a name="sharing-auditing-work-flow"></a>Deling af overvågningsarbejdsflow
  
Når en bruger (den fungerende bruger) ønsker at dele en ressource med en anden bruger (målbrugeren), kontrollerer SharePoint (eller OneDrive for Business) først, om målbrugerens mailadresse allerede er knyttet til en brugerkonto i organisationens mappe. Hvis målbrugeren er i mappen (og har en tilsvarende gæstebrugerkonto), gør SharePoint følgende:
  
-  Tildeler straks målbrugerens tilladelser til at få adgang til ressourcen ved at føje destinationsbrugeren til den relevante SharePoint gruppe og logfører en **AddedToGroup-hændelse**. 
    
- Sender en meddelelse om deling til destinationsbrugerens mailadresse.
    
- Logfører en **SharingSet-hændelse** . Denne hændelse har et brugervenligt navn på "Delt fil, mappe eller websted" under **Aktiviteter for delings- og adgangsanmodninger** i aktivitetsvælgeren i søgeværktøjet til overvågningsloggen. Se skærmbilledet i [trin 1](#step-1-search-for-sharing-events-and-export-the-results-to-a-csv-file). 
    
Hvis en brugerkonto for målbrugeren ikke findes i mappen, gør SharePoint følgende: 
    
   - Logfører en af følgende hændelser baseret på, hvordan ressourcen deles:
   
      - **Anonymt link blevoprettet**
   
      - **SecureLinkCreated**
   
      - **AddedToSecureLink** 

      - **SharingInvitationCreated** (denne hændelse logføres kun, når den delte ressource er et websted)
    
   - Når målbrugeren accepterer den invitation til deling, der sendes til vedkommende (ved at klikke på linket i invitationen), logfører SharePoint hændelsen **SharingInvitationAccepted** og tildeler destinationsbrugerens tilladelser til at få adgang til ressourcen. Hvis destinationsbrugeren får tilsendt et anonymt link, logføres hændelsen **AnonymousLinkUsed** , når destinationsbrugeren bruger linket til at få adgang til ressourcen. For sikre links logføres en **FileAccessed-hændelse** , når en ekstern bruger bruger linket til at få adgang til ressourcen.

Yderligere oplysninger om destinationsbrugeren logføres også, f.eks. identiteten på den bruger, invitationen er til, og den bruger, der accepterer invitationen. I nogle tilfælde kan disse brugere (eller mailadresser) være forskellige. 

## <a name="how-to-identify-resources-shared-with-external-users"></a>Sådan identificerer du ressourcer, der deles med eksterne brugere

Et almindeligt krav for administratorer er at oprette en liste over alle ressourcer, der er delt med brugere uden for organisationen. Ved hjælp af deling af overvågning i Office 365 kan administratorer oprette denne liste. Sådan gør du.
  
### <a name="step-1-search-for-sharing-events-and-export-the-results-to-a-csv-file"></a>Trin 1: Søg efter deling af hændelser, og eksportér resultaterne til en CSV-fil

Det første trin er at søge i overvågningsloggen efter delingshændelser. Du kan finde flere oplysninger (herunder de påkrævede tilladelser) om søgning i overvågningsloggen under [Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md).
  
1. Gå til <https://compliance.microsoft.com>.

2. Log på med din arbejds- eller skolekonto.

3. Klik på **Overvågning** i venstre rude på Microsoft Purview-overholdelsesportalen.

    Siden **Overvågning** vises.

4. Under **Aktiviteter** skal du klikke på **Delings- og adgangsanmodningsaktiviteter** for at søge efter delingsrelaterede hændelser. 

    ![Under Aktiviteter skal du vælge Delings- og adgangsanmodningsaktiviteter.](../media/46bb25b7-1eb2-4adf-903a-cc9ab58639f9.png)
  
5. Vælg et dato- og klokkeslætsinterval for at finde de delingshændelser, der fandt sted inden for den pågældende periode. 

6. Klik på **Søg** for at køre søgningen. 

7. Når søgningen er færdig med at køre, og resultaterne vises, skal du klikke på **Eksportér resultater** \> **Download alle resultater**.

    Når du har valgt eksportindstillingen, bliver du bedt om at åbne eller gemme CSV-filen nederst i vinduet.

8. Klik på **Gem** \> **som** , og gem CSV-filen i en mappe på din lokale computer. 

### <a name="step-2-use-the-powerquery-editor-to-format-the-exported-audit-log"></a>Trin 2: Brug PowerQuery-editor til at formatere den eksporterede overvågningslog

Det næste trin er at bruge JSON-transformationsfunktionen i Power Query-editor i Excel til at opdele hver egenskab i kolonnen **AuditData** (som består af et JSON-objekt med flere egenskaber) i sin egen kolonne. Dette giver dig mulighed for at filtrere kolonner for at få vist poster, der er relateret til deling

Du kan finde en trinvis vejledning under "Trin 2: Formatér den eksporterede overvågningslog ved hjælp af Power Query-editor" i [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).

### <a name="step-3-filter-the-csv-file-for-resources-shared-with-external-users"></a>Trin 3: Filtrer CSV-filen for ressourcer, der deles med eksterne brugere

Det næste trin er at filtrere CSV-filen for de forskellige delingsrelaterede hændelser, der tidligere blev beskrevet i afsnittet [SharePoint delingshændelser](#sharepoint-sharing-events). Du kan også filtrere kolonnen **TargetUserOrGroupType** for at få vist alle poster, hvor værdien af denne egenskab er **Guest**. 

Når du har fulgt instruktionerne i det forrige trin for at forberede CSV-filen ved hjælp af PowerQuery-editor, skal du gøre følgende:
    
1. Åbn den Excel fil, du oprettede i trin 2. 

2. Klik på **Sortér & Filter** under fanen **Hjem**, og klik derefter på **Filter**.
    
3. På rullelisten **Sortér & filter** i kolonnen **Handlinger** skal du rydde alle valg og derefter vælge en eller flere af følgende delingsrelaterede hændelser og derefter klikke på **OK**.
 
   - **SharingInvitationCreated**
   
   - **Anonymt link blevoprettet**
   
   - **SecureLinkCreated**
   
   - **AddedToSecureLink** 
    
    Excel viser rækkerne for de hændelser, du har valgt.
    
4. Gå til kolonnen med navnet **TargetUserOrGroupType** , og vælg den. 
    
5. På rullelisten **Sortér & Filter** skal du rydde alle valg og derefter vælge **TargetUserOrGroupType:Guest** og klikke på **OK**.
    
    Nu viser Excel rækkerne for deling af hændelser, OG hvor målbrugeren er uden for din organisation, fordi eksterne brugere identificeres af værdien **TargetUserOrGroupType:Guest**. 
  
> [!TIP]
> For de viste overvågningsposter identificerer kolonnen **ObjectId** den ressource, der blev delt med destinationsbrugeren. for eksempel  `ObjectId:https:\/\/contoso-my.sharepoint.com\/personal\/sarad_contoso_com\/Documents\/Southwater Proposal.docx`.
