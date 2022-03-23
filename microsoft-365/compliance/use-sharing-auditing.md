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
description: Administratoren kan se, hvordan man bruger overvågning af deling i Microsoft 365 til at identificere ressourcer, der er delt med brugere uden for organisationen.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ff05b655617608332b4b838e07a6af55e8b4d010
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588744"
---
# <a name="use-sharing-auditing-in-the-audit-log"></a>Brug overvågning af deling i overvågningsloggen

Deling er en vigtig aktivitet i SharePoint Online og OneDrive for Business og bruges meget i organisationer. Administratorer kan bruge overvågning af deling i overvågningsloggen til at bestemme, hvordan deling bruges i deres organisation. 
  
## <a name="the-sharepoint-sharing-schema"></a>Skemaet SharePoint deling

Delingshændelser (herunder ikke begivenheder, der vedrører politik for deling og delingslinks) er forskellige fra fil- og mapperelaterede begivenheder på en primær måde: En bruger udfører en handling, der har indvirkning på en anden bruger. Når en ressource f.eks. bruger A giver bruger B adgang til en fil. I dette eksempel er Bruger A den  *handlernde bruger*  , og bruger B er  *målbrugeren*. I SharePoint filskema påvirker den handlerens bruger kun selve filen. Når Bruger A åbner en fil, er den handlerens bruger de eneste oplysninger, der skal bruges i hændelsen **FileAccessed** . For at løse denne forskel er der et separat skema, kaldet *SharePoint delingsskema*, der registrerer flere oplysninger om delingshændelser. Dette sikrer, at administratorer har indsigt i, hvem der har delt en ressource, og den bruger, ressourcen blev delt med. 
  
Delingsskemaet indeholder to ekstra felter i en overvågningspost, der er relateret til delingshændelser: 
  
- **TargetUserOrGroupType:** Identificerer, om målbrugeren eller -gruppen er Medlem, Gæst, SharePointGroup, Sikkerhedsgruppe eller Partner.

- **TargetUserOrGroupName:** Gemmer UPN eller navnet på målbrugeren eller -gruppen, som en ressource blev delt med (Bruger B i det forrige eksempel). 

Disse to felter kan ud over andre egenskaber fra overvågningslogskemaet, f.eks. Bruger, Handling og Dato, se hele historien om, hvilken bruger der har delt  hvilken ressource med hvem og *hvornår*. 
  
Der er et andet skemaegenskab, som er vigtig for delingshistorien. Når du eksporterer søgeresultaterne fra overvågningsloggen, gemmer kolonnen **AuditData** i den eksporterede CSV-fil oplysninger om delingshændelser. Når en bruger f.eks. deler et websted med en anden bruger, opnås dette ved at føje målbrugeren til en SharePoint gruppe. Kolonnen **AuditData** registrerer disse oplysninger for at give kontekst til administratorer. Se [Trin 2](#step-2-use-the-powerquery-editor-to-format-the-exported-audit-log) for at få en vejledning i, hvordan du fortolker oplysningerne i **kolonnen AuditData** .

## <a name="sharepoint-sharing-events"></a>SharePoint delingshændelser

Deling defineres af, når en bruger *(den handler* bruger) vil dele en ressource med en anden bruger ( *målbrugeren* ). De poster, der er relateret til deling af en ressource med en ekstern bruger (en bruger, som er uden for organisationen og ikke har en gæstekonto i organisationens Azure Active Directory), identificeres af følgende hændelser, som er logført i overvågningsloggen:

- **SharingInvitationCreated:** En bruger i organisationen har forsøgt at dele en ressource (sandsynligvis et websted) med en ekstern bruger. Dette resulterer i en invitation til ekstern deling, der sendes til målbrugeren. Der gives ingen adgang til ressourcen på nuværende tidspunkt.

- **SharingInvitationAccepted:** Den eksterne bruger har accepteret den invitation til deling, som er sendt af den handlernde bruger, og har nu adgang til ressourcen.

- **AnonymtLinkOprettet:** Der oprettes et anonymt link (også kaldet et "Alle"-link) for en ressource. Da et anonymt link kan oprettes og derefter kopieres, er det fornuftigt at antage, at alle dokumenter med et anonymt link er blevet delt med en målbruger.

- **AnonymtLinkBrugt:** Som navnet antyder, logføres denne hændelse, når der bruges et anonymt link til at få adgang til en ressource. 

- **SecureLinkCreated:** En bruger har oprettet et "bestemte personer-link" for at dele en ressource med en bestemt person. Denne målbruger kan være en person, der er ekstern i forhold til din organisation. Den person, ressourcen deles med, identificeres i overvågningsposten for **hændelsen AddedToSecureLink** . Tidsstemplerne for disse to begivenheder er næsten identiske.

- **AddedToSecureLink:** En bruger blev føjet til et link til bestemte personer. Brug **feltet TargetUserOrGroupName i** denne hændelse til at identificere den bruger, der er føjet til det tilsvarende bestemte personer-link. Denne målbruger kan være en person, der er ekstern i forhold til din organisation.

## <a name="sharing-auditing-work-flow"></a>Arbejdsflow i forbindelse med deling af overvågning
  
Når en bruger (den handlernde bruger) vil dele en ressource med en anden bruger (målbrugeren), kontrollerer SharePoint (eller OneDrive for Business) først, om målbrugerens mailadresse allerede er knyttet til en brugerkonto i organisationens adressekartotek. Hvis målbrugeren er i kataloget (og har en tilsvarende gæstebrugerkonto), SharePoint gøre følgende:
  
-  Tildeler straks målbrugeren tilladelser til at få adgang til ressourcen ved at føje målbrugeren til den relevante SharePoint-gruppe og logføres en **AddedToGroup-hændelse**. 
    
- Sender en delingsmeddelelse til målbrugereens mailadresse.
    
- Logføres en **SharingSet-begivenhed** . Denne hændelse har det fulde navn "Delt fil, mappe eller websted **" under Aktiviteter** for anmodning om deling og adgang i søgeværktøjets aktivitetsvælger. Se skærmbilledet i [trin 1](#step-1-search-for-sharing-events-and-export-the-results-to-a-csv-file). 
    
Hvis en brugerkonto for målbrugeren ikke er i mappen, skal SharePoint gøre følgende: 
    
   - Logføres en af følgende hændelser baseret på, hvordan ressourcen deles:
   
      - **AnonymtLinkOprettet**
   
      - **SecureLinkCreated**
   
      - **AddedToSecureLink** 

      - **SharingInvitationCreated** (denne hændelse logføres kun, når den delte ressource er et websted)
    
   - Når målbrugeren accepterer invitationen om deling, der er sendt til dem (ved at klikke på linket i invitationen), logger SharePoint en **SharingInvitationAccepted-hændelse** og tildeler målbrugeren tilladelser til at få adgang til ressourcen. Hvis målbrugeren sendes et anonymt link, logføres hændelsen **AnonymtLinkBrugt** , når målbrugeren bruger linket til at få adgang til ressourcen. For sikre links **logføres en FileAccessed-hændelse** , når en ekstern bruger bruger linket til at få adgang til ressourcen.

Der logføres også yderligere oplysninger om målbrugeren, f.eks. identiteten på den bruger, invitationen er til, og den bruger, der accepterer invitationen. I nogle tilfælde kan disse brugere (eller mailadresser) være forskellige. 

## <a name="how-to-identify-resources-shared-with-external-users"></a>Sådan identificeres ressourcer, der er delt med eksterne brugere

Et almindeligt krav til administratorer er at oprette en liste over alle de ressourcer, der er delt med brugere uden for organisationen. Ved hjælp af overvågning af deling i Office 365 kan administratorer generere denne liste. Sådan gør du.
  
### <a name="step-1-search-for-sharing-events-and-export-the-results-to-a-csv-file"></a>Trin 1: Søg efter delingshændelser, og eksportér resultaterne til en CSV-fil

Det første trin er at søge efter delingshændelser i overvågningsloggen. Du kan finde flere oplysninger (herunder de nødvendige tilladelser) om søgning i overvågningsloggen [i Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md).
  
1. Gå til <https://compliance.microsoft.com>.

2. Log på med din arbejds- eller skolekonto.

3. Klik på Overvågning i venstre rude Microsoft 365 Overholdelsescenter **navigationsruden**.

    **Siden Overvågning** vises.

4. Under **Aktiviteter skal** du klikke **på Anmodning om deling og anmodning om** adgang for at søge efter delingsrelaterede begivenheder. 

    ![Under Aktiviteter skal du vælge Aktiviteter for anmodning om deling og adgang.](../media/46bb25b7-1eb2-4adf-903a-cc9ab58639f9.png)
  
5. Vælg en dato og et tidsinterval for at finde de delingshændelser, der er opstået inden for den pågældende periode. 

6. Klik **på** Søg for at køre søgningen. 

7. Når søgningen er færdig med at køre, og resultaterne vises, skal du klikke på **Eksportér resultater** \> **Hent alle resultater**.

    Når du har valgt eksportindstillingen, bliver du bedt om at åbne eller gemme CSV-filen i en meddelelse nederst i vinduet.

8. Klik **på** \> **Gem Gem som** , og gem CSV-filen i en mappe på din lokale computer. 

### <a name="step-2-use-the-powerquery-editor-to-format-the-exported-audit-log"></a>Trin 2: Brug PowerQuery-editoren til at formatere den eksporterede overvågningslog

Næste trin er at bruge JSON-transformeringsfunktionen i Power Query Editor i Excel til at opdele hver egenskab i kolonnen **AuditData** (som består af et JSON-objekt med flere egenskaber) i sin egen kolonne. Dette giver dig mulighed for at filtrere kolonner for at få vist poster, der er relateret til deling

Du kan finde en trinvis vejledning under "Trin 2: Formatere den eksporterede overvågningslog ved hjælp af Power-forespørgselseditoren" i Eksportér, konfigurere og få vist [overvågningslogposter](export-view-audit-log-records.md#step-2-format-the-exported-audit-log-using-the-power-query-editor).

### <a name="step-3-filter-the-csv-file-for-resources-shared-with-external-users"></a>Trin 3: Filtrer CSV-filen for ressourcer, der er delt med eksterne brugere

Det næste trin er at filtrere CSV'en for de forskellige delingsrelaterede hændelser, der tidligere er blevet beskrevet [i SharePoint om delingshændelser](#sharepoint-sharing-events). Alternativt kan du filtrere kolonnen **TargetUserOrGroupType** for at få vist alle poster, hvor værdien af denne egenskab er **Gæst**. 

Når du har fulgt vejledningen i det forrige trin for at forberede CSV-filen ved hjælp af PowerQuery-editoren, skal du gøre følgende:
    
1. Åbn den Excel fil, du oprettede i trin 2. 

2. Klik på **Sortér** og **filtrer & under** fanen Hjem, og klik derefter på **Filtrer**.
    
3. På **rullelisten & Sortér** filter i kolonnen Handlinger skal du fjerne  alle valg og derefter vælge en eller flere af følgende delingsrelaterede hændelser og derefter klikke på **OK**.
 
   - **SharingInvitationCreated**
   
   - **AnonymtLinkOprettet**
   
   - **SecureLinkCreated**
   
   - **AddedToSecureLink** 
    
    Excel viser rækkerne for de hændelser, du har valgt.
    
4. Gå til kolonnen **TargetUserOrGroupType,** og vælg den. 
    
5. På **rullelisten Sortér & Filter** skal du rydde alle valg og derefter **vælge TargetUserOrGroupType:Guest** og klikke på **OK**.
    
    Nu Excel rækkerne for delingshændelser, OG hvor målbrugeren er uden for organisationen, fordi eksterne brugere er identificeret af værdien **TargetUserOrGroupType:Guest**. 
  
> [!TIP]
> For de overvågningsposter, der vises, identificerer **kolonnen ObjectId** den ressource, der blev delt med målbrugeren. for eksempel  `ObjectId:https:\/\/contoso-my.sharepoint.com\/personal\/sarad_contoso_com\/Documents\/Southwater Proposal.docx`.
