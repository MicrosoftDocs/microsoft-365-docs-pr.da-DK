---
title: Fordeling af indhold
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkMAC
search.appverid:
- MOE150
- MET150
description: Overvåg og administrer bortskaffelsen af indhold, når du bruger en dispositionsgennemgang, eller elementer, der er markeret som poster, slettes automatisk i henhold til de indstillinger, du har konfigureret.
ms.openlocfilehash: 34ac1a9d3b62cd0806318582f7baef76947d7670
ms.sourcegitcommit: 37111bc0c5a6cc4690f7144a019bbff11d44858f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65463252"
---
# <a name="disposition-of-content"></a>Fordeling af indhold

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug siden **Disposition** fra **Datastyring** i Microsoft Purview-compliance-portal til at administrere dispositionsgennemgange og få vist metadataene for [poster](records-management.md#records), der automatisk er blevet slettet i slutningen af deres opbevaringsperiode.

## <a name="prerequisites-for-viewing-content-dispositions"></a>Forudsætninger for visning af indholdsdispositioner

Hvis du vil administrere dispositionsgennemgange og bekræfte, at poster er blevet slettet, skal du have de nødvendige tilladelser, og overvågning skal være aktiveret. Vær også opmærksom på eventuelle [begrænsninger](retention-limits.md#maximum-number-of-items-for-disposition) for fordeling.

### <a name="permissions-for-disposition"></a>Tilladelser til disposition

Brugerne skal have rollen **Dispositionsadministration** for at få adgang til fanen **Disposition** i Microsoft Purview-compliance-portal. Fra december 2020 er denne rolle nu inkluderet i standardrollegruppen **Datastyring** .

> [!NOTE]
> En global administrator tildeles som standard ikke rollen **Dispositionsstyring** . 

Hvis du kun vil give brugerne de tilladelser, de har brug for til dispositionsgennemgange, uden at tildele dem tilladelser til at få vist og konfigurere andre funktioner til opbevaring og datastyring, skal du oprette en brugerdefineret rollegruppe (f.eks. kaldet "Disposition Reviewers") og tildele denne gruppe rollen **Dispositionsstyring** .

Du kan finde oplysninger om, hvordan du føjer brugere til standardrollerne eller opretter dine egne rollegrupper, [under Tilladelser i Microsoft Purview-compliance-portal](microsoft-365-compliance-center-permissions.md).

Derudover:

- Hvis du vil have vist indholdet af elementer under fordelingsprocessen, skal du føje brugere til rollegruppen **Indholdsfremviser i Indholdsoversigt** . Hvis brugerne ikke har tilladelserne fra denne rollegruppe, kan de stadig vælge en dispositionsgennemsynshandling for at fuldføre dispositionsgennemgangen, men de skal gøre det uden at kunne få vist elementets indhold fra ruden med minivisning i Microsoft Purview-compliance-portal.

- Hver person, der får adgang til siden **Disposition** , kan som standard kun se elementer, de er tildelt til gennemsyn. For at en administrator af datastyring kan se alle elementer, der er tildelt alle brugere, og alle opbevaringsmærkater, der er konfigureret til gennemgang af disposition: Naviger til **indstillinger for** >  **datastyringFøj** for at vælge og derefter aktivere en mailaktiveret sikkerhedsgruppe, der indeholder administratorkontiene.
    
    Microsoft 365 grupper og sikkerhedsgrupper, der ikke er mailaktiverede, understøtter ikke denne funktion og vises ikke på listen for at vælge. Hvis du har brug for at oprette en ny mailaktiveret sikkerhedsgruppe, skal du bruge linket til <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> til at oprette den nye gruppe. 
    
    > [!IMPORTANT]
    > Når du har aktiveret gruppen, kan du ikke ændre den i Microsoft Purview-compliance-portal. I næste afsnit kan du se, hvordan du aktiverer en anden gruppe ved hjælp af PowerShell.

- Indstillingen **Indstillinger for datastyring** er kun synlig for administratorer af postadministration. 

#### <a name="enabling-another-security-group-for-disposition"></a>Aktivering af en anden sikkerhedsgruppe til fordeling

Når du har aktiveret en sikkerhedsgruppe til disposition fra indstillingerne for **datastyring** i Microsoft Purview-compliance-portal, kan du ikke deaktivere denne tilladelse for gruppen eller erstatte den valgte gruppe i Microsoft Purview-compliance-portal. Du kan dog aktivere en anden mailaktiveret sikkerhedsgruppe ved hjælp af cmdlet'en [Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) .

Eksempel: 

```PowerShell
Enable-ComplianceTagStorage -RecordsManagementSecurityGroupEmail dispositionreviewers@contosoi.com
````

### <a name="enable-auditing"></a>Aktivér overvågning

Sørg for, at overvågning er aktiveret mindst én dag før den første dispositionshandling. Du kan finde flere oplysninger under [Søg i overvågningsloggen i Microsoft Purview-compliance-portal](search-the-audit-log-in-security-and-compliance.md). 

## <a name="disposition-reviews"></a>Dispositionsgennemgange

Når indholdet når slutningen af opbevaringsperioden, er der flere grunde til, at du måske vil gennemse indholdet og bekræfte, om det kan slettes permanent ("bortskaffes"). I stedet for at slette indholdet skal du f.eks.:
  
- Suspender sletningen af relevant indhold i forbindelse med procesførelse eller revision.

- Tildel en anden opbevaringsperiode til indholdet, måske fordi de oprindelige opbevaringsindstillinger var en midlertidig eller midlertidig løsning.

- Flyt indholdet fra den eksisterende placering til en arkivplacering, f.eks. hvis indholdet har forskning eller historisk værdi.

Når en dispositionsgennemgang udløses i slutningen af opbevaringsperioden, modtager de korrekturlæsere, du vælger, en mail om, at de har indhold, der skal gennemses. Disse korrekturlæsere kan være individuelle brugere eller mailaktiverede sikkerhedsgrupper.

Du kan tilpasse den meddelelsesmail, som korrekturlæsere modtager, herunder instruktioner på forskellige sprog. Hvis du vil understøtte flere sprog, skal du selv angive oversættelserne, og denne brugerdefinerede tekst vises for alle korrekturlæsere, uanset deres landestandard.

Brugerne modtager en indledende mailmeddelelse pr. mærkat i slutningen af elementets opbevaringsperiode med en påmindelse pr. etiket én gang om ugen for alle dispositionsgennemgange, som de er tildelt. De kan klikke på linket i meddelelses- og påmindelsesmailene for at gå direkte til siden **DatastyringDisposition** >  i Microsoft Purview-compliance-portal for at gennemse indholdet og udføre en handling. Alternativt kan korrekturlæserne navigere til denne **dispositionsside** i Microsoft Purview-compliance-portal. Derefter:

- Korrekturlæsere kan kun se de dispositionsgennemgange, der er tildelt dem, hvorimod administratorer, der er føjet til den valgte sikkerhedsgruppe for datastyring, kan se alle dispositionsgennemgange.

- Korrekturlæsere kan føje nye brugere til den samme dispositionsgennemgang. Bemærk, at denne handling ikke automatisk giver de tilføjede brugere de [nødvendige tilladelser](#permissions-for-disposition).

- I forbindelse med processen til gennemgang af fordeling viser en minigennemsynsrude for hvert element et eksempel på indholdet, hvis de har tilladelse til at se det. Hvis de ikke har tilladelser, kan de vælge indholdslinket og anmode om tilladelser. Denne minigennemgangsrude indeholder også faner til yderligere oplysninger om indholdet:
   - **Oplysninger om** visning af indekserede egenskaber, hvor de er placeret, hvem der har oprettet dem, hvornår og hvem der senest har ændret dem, og hvornår.
   - **Historik** , der viser historikken for alle dispositionsgennemgangshandlinger til dato med kommentarer fra korrekturlæseren, hvis de er tilgængelige.

En dispositionsgennemgang kan omfatte indhold i Exchange postkasser, SharePoint websteder og OneDrive konti. Indhold, der afventer en dispositionsgennemsyn på disse placeringer, slettes kun permanent, når en validator for den sidste fase af dispositionen vælger at slette indholdet permanent.

> [!NOTE]
> En postkasse skal have mindst 10 MB data for at understøtte dispositionsgennemgange.

Administratorer kan se en oversigt over alle ventende dispositioner under fanen **Oversigt** . Korrekturlæsere kan kun se deres ventende elementer. Eksempel:

![Oversigt over ventende dispositioner i Datastyring.](../media/dispositions-overview.png)

Når du vælger **Vis alle ventende dispositioner**, føres du til siden **Disposition** . Eksempel:

![Siden Dispositioner i Microsoft Purview-compliance-portal.](../media/disposition-tab.png)


### <a name="workflow-for-a-disposition-review"></a>Arbejdsproces til gennemgang af fordeling

I følgende diagram vises den grundlæggende arbejdsproces for en dispositionsgennemgang (enkeltfase), når en opbevaringsmærkat udgives og derefter anvendes manuelt af en bruger. Alternativt kan en opbevaringsmærkat, der er konfigureret til en dispositionsgennemgang, anvendes automatisk på indhold.
  
![Diagram, der viser flowet for, hvordan fordeling fungerer.](../media/5fb3f33a-cb53-468c-becc-6dda0ec52778.png)

### <a name="how-to-configure-a-retention-label-for-disposition-review"></a>Sådan konfigurerer du en opbevaringsmærkat til gennemgang af fordeling

Udløsning af en gennemgang af fordeling i slutningen af opbevaringsperioden er en konfigurationsindstilling, der kun er tilgængelig med en opbevaringsmærkat. Dispositionsgennemgang er ikke tilgængelig for en opbevaringspolitik. Du kan finde flere oplysninger om disse to opbevaringsløsninger under [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md).

På siden **Vælg, hvad der sker efter opbevaringsperioden** for en opbevaringsmærkat:

![Opbevaringsindstillinger for en etiket.](../media/disposition-review-option.png)
 
Når du har valgt indstillingen **Start en dispositionsgennemsyn** , skal du vælge **+ Opret faser og tildele korrekturlæsere**. På den næste side i konfigurationen skal du angive, hvor mange på hinanden følgende dispositionsfaser du vil have, og hvilke dispositionsgennemgange der skal evalueres for hver fase:

![Angiver disponeringslæsere.](../media/disposition-reviewers.png) 

Vælg **+ Tilføj en fase**, og navngiv fasen med henblik på identifikation. Angiv derefter korrekturlæserne for den pågældende fase.

For korrekturlæserne skal du angive op til 10 individuelle brugere eller mailaktiverede sikkerhedsgrupper. Microsoft 365 grupper ([tidligere Office 365 grupper](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) understøttes ikke for denne indstilling.

Hvis du har brug for mere end én person til at gennemse et element i slutningen af opbevaringsperioden, skal du vælge **Tilføj en anden fase** og gentage konfigurationsprocessen for det antal faser, du har brug for, med højst fem faser. 

Inden for hver enkelt dispositionsfase er alle de brugere, du angiver for den pågældende fase, godkendt til at udføre den næste handling for elementet i slutningen af opbevaringsperioden. Disse brugere kan også føje andre brugere til fasen med gennemgang af disposition.

> [!NOTE]
> Hvis du har konfigureret opbevaringsmærkater, før gennemgang af flere faser var tilgængelig, kan du opgradere dine mærkater for at understøtte denne funktion: Rediger mærkaten, og vælg **Rediger faser og korrekturlæsere** på siden **Vælg, hvad der sker efter opbevaringsperioden** .

Under konfigurationsfasen kan du for hver angivet fase omdøbe den, omarrangere den eller fjerne den ved at vælge **Rediger faser og korrekturlæsere** , der nu vises for indstillingen **Start en dispositionsgennemsyn** . Derefter kan du for hver fase vælge indstillingen Fasehandlinger (**...**): 

![Fasehandlinger til dispositionsgennemgange.](../media/stage-actions-disposition-review.png)

Du kan dog ikke omarrangere eller fjerne en fase, når du har oprettet opbevaringsmærkaten. Du får kun vist indstillingerne **Tilføj en fase** og **Omdøb en fase** . Du kan stadig redigere korrekturlæserne.

Når du har angivet dine validatorer, skal du huske at give dem rollen **DispositionSstyring** . Du kan få flere oplysninger i afsnittet [Tilladelser til disposition](#permissions-for-disposition) på denne side.

### <a name="how-to-customize-email-messages-for-disposition-review"></a>Sådan tilpasser du mails til dispositionsgennemsyn

Eksempel på standardmeddelelse via mail, der er sendt til en korrekturlæser:

![Eksempel på mailmeddelelse med standardtekst, når et element er klar til dispositionsgennemsyn.](../media/disposition-review-email.png)

Du kan tilpasse de mails, der sendes til dispositionslæsere for den første meddelelse og derefter påmindelser.

Vælg **Indstillinger for datastyring** på en af siderne til datastyring i Microsoft Purview-compliance-portal:  

![Indstillinger for datastyring.](../media/record-management-settings.png)

Under fanen **Disposition** i afsnittet **Mailmeddelelser om dispositionsgennemgange** skal du vælge og angive, om du kun vil bruge standardmailmeddelelsen eller føje din egen tekst til standardmeddelelsen. Din brugerdefinerede tekst føjes til mailinstruktionerne efter oplysningerne om opbevaringsmærkaten og før de næste trins instruktioner.

Der kan tilføjes tekst til alle sprog, men formatering og billeder understøttes ikke. URL-adresser og mailadresser kan angives som tekst og, afhængigt af mailklienten, vises som links eller ikke-formateret tekst i den brugerdefinerede mail.

Eksempeltekst, der skal tilføjes:

```console
If you need additional information, visit the helpdesk website (https://support.contoso.com) or send them an email (helpdesk@contoso.com).
```

Vælg **Gem** for at gemme eventuelle ændringer.

### <a name="viewing-and-disposing-of-content"></a>Visning og bortskaffelse af indhold

Når en korrekturlæser får besked via mail om, at indholdet er klar til gennemsyn, kan vedkommende klikke på et link i mailen, der fører dem direkte til siden **Disposition** fra **Datastyring** i Microsoft Purview-compliance-portal. Der kan korrekturlæserne se, hvor mange elementer for hver opbevaringsmærkat der venter disposition med den **type,** der viser **Ventende disposition**. De vælger derefter en opbevaringsmærkat og **Åbner i et nyt vindue** for at få vist alt indhold med den pågældende etiket:

![Åbn i et nyt vindue til dispositionsgennemsyn.](../media/open-in-new-window.png)

Fra siden **Ventende dispositioner** kan de se alle ventende dispositioner for den pågældende etiket. Når et eller flere elementer er markeret, kan de bruge ruden med minieksemplet og fanen **Kilde**, **Detaljer** og **Oversigt** til at undersøge indholdet, før du foretager en handling på det:

![Dispositionsindstillinger.](../media/retention-disposition-options.png)

Hvis du bruger det vandrette rullepanel eller lukker ruden til min. gennemsyn, får du vist flere kolonner, der indeholder udløbsdatoen og navnet på fasen til gennemgang af dispositionen.

Som du kan se i det viste eksempel, er de understøttede handlinger: 
  
- **Godkend afsætning**:
    - Når denne handling er valgt til en midlertidig fase i dispositionsgennemgangen (du har konfigureret flere faser): Elementet flyttes til den næste dispositionsfase.
    - Når denne handling er valgt til den sidste fase i dispositionsgennemgangen, eller der kun er én dispositionsfase: Elementet er markeret som berettiget til permanent sletning, som et timerjob derefter udfører inden for 7 dage. Det nøjagtige tidspunkt for det element, der skal slettes permanent, afhænger af arbejdsbelastningen. Du kan få flere oplysninger under [Sådan fungerer opbevaring for SharePoint og OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive) og [Sådan fungerer opbevaring for Exchange](retention-policies-exchange.md#how-retention-works-for-exchange).

- **Relabel**:
    - Når denne handling er valgt, afslutter elementet processen til gennemgang af fordeling for den oprindelige etiket. Elementet er derefter underlagt opbevaringsindstillingerne for den nyligt valgte opbevaringsmærkat.

- **Udvid**:
    - Når denne handling er valgt, afbrydes gennemgangen af fordeling effektivt indtil slutningen af den forlængede periode, og derefter udløses dispositionsgennemgangen igen fra den første fase.

- **Tilføj korrekturlæsere**:
    - Når denne handling er valgt, bliver brugeren bedt om at angive og tilføje andre brugere til gennemsyn.
    > [!NOTE]
    > Denne handling tildeler ikke automatisk de [nødvendige tilladelser](#permissions-for-disposition) til de brugere, der er tilføjet. Hvis de ikke har disse tilladelser, kan de ikke deltage i dispositionsgennemgangen.

Hver handling, der udføres, har en tilsvarende overvågningshændelse i gruppen [Disposition review activities](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities) auditing activities.

Under en dispositionsgennemgang flyttes indholdet aldrig fra den oprindelige placering, og det markeres ikke til permanent sletning, før denne handling er valgt af en korrekturlæser til den endelige eller eneste dispositionsfase.

## <a name="disposition-of-records"></a>Fordeling af poster

På hovedsiden **Datastyring** > fanen **Disposition** kan du identificere:

- Elementer, der er slettet som følge af en dispositionsgennemgang.
- Elementer, der er markeret som en post eller lovmæssig post, som automatisk blev slettet ved slutningen af deres opbevaringsperiode.

Disse elementer viser **Poster, der er fjernet** i kolonnen **Type** . Eksempel:

![Elementer, der blev fjernet uden en dispositionsgennemgang.](../media/records-disposed2.png)

> [!NOTE]
> Denne funktionalitet bruger oplysninger fra den [samlede overvågningslog](search-the-audit-log-in-security-and-compliance.md) og kræver derfor, at overvågning [er aktiveret og kan søges i](turn-audit-log-search-on-or-off.md) , så de tilsvarende hændelser registreres.

Hvis du vil overvåge slettede elementer, der er markeret som poster eller lovmæssige poster, skal du søge efter **Slettet fil, der er markeret som en post** i kategorien **Fil- og sideaktiviteter** . Denne overvågningshændelse gælder for dokumenter og mails.

## <a name="filter-and-export-the-views"></a>Filtrer og eksportér visningerne

Når du vælger en opbevaringsmærkat på siden **Disposition** , kan du bruge fanen **Ventende fordeling** (hvis det er relevant) og fanen **Kasserede elementer** til at filtrere visningerne, så du nemmere kan finde elementer.

For ventende dispositioner er tidsintervallen baseret på udløbsdatoen. For fjernede varer er tidsintervallet baseret på datoen for sletning.
  
Du kan eksportere oplysninger om elementerne i begge visninger som en .csv fil, som du derefter kan sortere og administrere ved hjælp af Excel.
