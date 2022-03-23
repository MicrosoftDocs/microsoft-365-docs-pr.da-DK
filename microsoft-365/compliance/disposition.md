---
title: Disposition af indhold
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
description: Overvåge og administrere afhændelse af indhold, når du bruger en dispositionsgennemgang, eller elementer, der er markeret som poster, slettes automatisk i overensstemmelse med de indstillinger, du har konfigureret.
ms.openlocfilehash: 2d078eb00ffa6d2dd8279c7e5eb65a8fcfb6fa53
ms.sourcegitcommit: 40f89c46032ea33de25417106f39cbeebef5a049
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/10/2022
ms.locfileid: "63590045"
---
# <a name="disposition-of-content"></a>Disposition af indhold

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Brug siden **Disposition** fra **Datastyring** i Microsoft 365 Overholdelsescenter til at administrere dispositionsvurderinger og få vist metadataene for poster [](records-management.md#records), der er blevet slettet automatisk i slutningen af deres opbevaringsperiode.

## <a name="prerequisites-for-viewing-content-dispositions"></a>Forudsætninger for visning af indholdsdispositioner

Hvis du vil administrere dispositionsvurderinger og bekræfte, at poster er blevet slettet, skal du have tilstrækkelige tilladelser, og overvågning skal være aktiveret. Vær også opmærksom på eventuelle [begrænsninger](retention-limits.md#maximum-number-of-items-for-disposition) for disposition.

### <a name="permissions-for-disposition"></a>Tilladelser til disposition

For at få adgang **til fanen Disposition** i Microsoft 365 Overholdelsescenter skal brugere have rollen **Dispositionsstyring**. Fra december 2020 er denne rolle nu inkluderet i **standardrollegruppen** Datastyring.

> [!NOTE]
> Som standard tildeles en global administrator ikke rollen **dispositionsstyring** . 

Hvis du kun vil give brugerne de tilladelser, de skal bruge til gennemgang af dispositioner, uden at give dem tilladelse til at få vist og konfigurere andre funktioner til opbevaring og datastyring, skal du oprette en brugerdefineret rollegruppe (f.eks. kaldet "Dispositions reviewere") og tildele denne gruppe rollen **Dispositionsstyring** .

Du kan finde en vejledning til at føje brugere til standardrollerne eller oprette dine egne [rollegrupper under Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md).

Derudover:

- Hvis du vil have vist indholdet af elementer under dispositionsprocessen, skal du føje brugere til **rollegruppen Indholdsvisning i Indholdsoversigt** . Hvis brugerne ikke har tilladelser fra denne rollegruppe, kan de stadig vælge en handling til dispositionsgennemsyn for at fuldføre dispositionsgennemsynet, men de skal gøre det uden at kunne se elementets indhold fra minivisningsruden i overholdelsescenteret.

- Som standard får hver person, der får adgang til **siden Disposition** , kun vist elementer, som de er tildelt til at gennemgå. For at en datastyringsadministrator kan se alle elementer, der er tildelt til alle brugere, og alle opbevaringsnavne, der er konfigureret til dispositionsgennemsyn:  >  Gå til Indstillinger for datastyringDisposition for at vælge og derefter aktivere en mailaktiveret sikkerhedsgruppe, der indeholder administratorkontiene.
    
    Microsoft 365 grupper og sikkerhedsgrupper, der ikke er mailaktiverede, understøtter ikke denne funktion og vises ikke på listen for at vælge den. Hvis du vil oprette en ny mailaktiveret sikkerhedsgruppe, skal du bruge linket til <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration til at</a> oprette den nye gruppe. 
    
    > [!IMPORTANT]
    > Når du har aktiveret gruppen, kan du ikke ændre den i Overholdelsescenter. Se næste afsnit for at finde ud af, hvordan du aktiverer en anden gruppe ved hjælp af PowerShell.

- Indstillingen **Indstillinger for datastyring** er kun synlig for administratorer af datastyring. 

#### <a name="enabling-another-security-group-for-disposition"></a>Aktivering af en anden sikkerhedsgruppe til disposition

Når du har aktiveret en sikkerhedsgruppe til disposition fra  indstillingerne for datastyring i Microsoft 365 Overholdelsescenter, kan du ikke deaktivere denne tilladelse for gruppen eller erstatte den valgte gruppe i overholdelsescenteret. Du kan dog aktivere en anden mailaktiveret sikkerhedsgruppe ved hjælp [af cmdlet'en Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) .

Eksempel: 

```PowerShell
Enable-ComplianceTagStorage -RecordsManagementSecurityGroupEmail dispositionreviewers@contosoi.com
````

### <a name="enable-auditing"></a>Aktivér overvågning

Sørg for, at overvågning er aktiveret mindst én dag før den første dispositionshandling. Få mere at vide under [Søg i overvågningsloggen i overholdelsescenteret](search-the-audit-log-in-security-and-compliance.md). 

## <a name="disposition-reviews"></a>Dispositionsvurderinger

Når indholdet når slutningen af dets opbevaringsperiode, kan der være flere grunde til, at du bør gennemse indholdet og bekræfte, om det kan slettes permanent ("bortkastet"). I stedet for at slette indholdet kan det f.eks. være nødvendigt at:
  
- Suspender sletning af relevant indhold til procesførelse eller en overvågning.

- Tildel indholdet en anden opbevaringsperiode, måske fordi de oprindelige opbevaringsindstillinger var en midlertidig eller midlertidig løsning.

- Flyt indholdet fra dens eksisterende placering til en arkivplacering, f.eks. hvis indholdet har forskning eller historisk værdi.

Når en gennemgang af disposition udløses i slutningen af opbevaringsperioden, modtager de korrekturlæsere, du vælger, en mail om, at de har indhold, der skal gennemgås. Disse korrekturlæsere kan være individuelle brugere eller mailaktiverede sikkerhedsgrupper.

Du kan tilpasse den mail om meddelelser, som korrekturlæsere modtager, herunder instruktioner på forskellige sprog. For understøttelse af flere sprog skal du selv angive oversættelserne, og denne brugerdefinerede tekst vises for alle korrekturlæsere uanset deres landesprog.

Brugere modtager en indledende mailbesked pr. etiket ved slutningen af elementets opbevaringsperiode med en påmindelse pr. etiket én gang om ugen af alle dispositionsvurderinger, de er tildelt. De kan klikke på linket i notifikations- og påmindelsesmailene for at gå direkte til siden Datastyringsdisposition  >  i Microsoft 365 Overholdelsescenter for at gennemse indholdet og gøre noget. Ellers kan korrekturlæserne navigere til siden **Disposition** i overholdelsescenteret. Gør derefter følgende:

- Korrekturlæsere kan kun se de dispositionsvurderinger, der er tildelt til dem, hvorimod administratorer, der er føjet til den valgte sikkerhedsgruppe for datastyring, kan se alle dispositionsvurderinger.

- Korrekturlæsere kan tilføje nye brugere til den samme gennemgang af dispositionen. Bemærk, at denne handling ikke automatisk giver de tilføjede brugere [de nødvendige tilladelser](#permissions-for-disposition).

- I forbindelse med processen til gennemgang af fordeling viser en minigennemsynsrude for hvert element et eksempel på indholdet, hvis de har tilladelse til at se det. Hvis de ikke har tilladelser, kan de vælge linket til indhold og anmode om tilladelser. Denne minigennemsynsrude indeholder også faner til yderligere oplysninger om indholdet:
   - **Detaljer** for at få vist indekserede egenskaber, hvor den er placeret, hvem der har oprettet den, hvornår, hvem der senest har ændret den og hvornår.
   - **Oversigt** , der viser historikken for alle handlinger til gennemgang af fordeling til dato med korrekturlæserens kommentarer, hvis de er tilgængelige.

En gennemgang af dispositionen kan omfatte indhold Exchange postkasser, SharePoint websteder og OneDrive konti. Indhold, der afventer en gennemgang af dispositionen på disse placeringer, slettes først permanent, når en korrekturlæser for det sidste trin i dispositionen vælger at slette indholdet permanent.

> [!NOTE]
> En postkasse skal have mindst 10 MB data for at understøtte dispositionsvurderinger.

Administratorer kan se en oversigt over alle ventende dispositioner på **fanen** Oversigt. Korrekturlæsere kan kun se deres elementer, der afventer disposition. Eksempel:

![Ventende dispositioner i Oversigt over datastyring.](../media/dispositions-overview.png)

Når du vælger **Vis alle ventende dispositioner**, kommer du til **siden Disposition** . Eksempel:

![Siden Dispositioner i Microsoft 365 Overholdelsescenter.](../media/disposition-tab.png)


### <a name="workflow-for-a-disposition-review"></a>Arbejdsproces for en gennemgang af dispositionen

Følgende diagram viser den grundlæggende arbejdsproces for en dispositionsgennemgang (enkelt trin), når en opbevaringsetiket publiceres og derefter anvendes manuelt af en bruger. Alternativt kan et opbevaringsmærkat, der er konfigureret til en dispositionsgennemsyn, automatisk anvendes på indhold.
  
![Diagram, der viser, hvordan disposition fungerer.](../media/5fb3f33a-cb53-468c-becc-6dda0ec52778.png)

### <a name="how-to-configure-a-retention-label-for-disposition-review"></a>Sådan konfigureres en opbevaringsetiket til gennemgang af disposition

Udløsning af en dispositionsvurdering i slutningen af en opbevaringsperiode er en konfigurationsindstilling, der kun er tilgængelig med en opbevaringsmærkat. Gennemgang af disposition er ikke tilgængelig for en opbevaringspolitik. Du kan finde flere oplysninger om disse to opbevaringsløsninger under [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md).

Fra siden **Definer opbevaringsindstillinger** for en opbevaringsetiket:

![Opbevaringsindstillinger for en etiket.](../media/disposition-review-option.png)
 
Når du har valgt  denne indstilling Udløs en dispositionsgennemsynsindstilling, skal du på næste side i konfigurationen angive, hvor mange efterfølgende trin i dispositionen, du ønsker, samt korrekturlæserne for dispositionen for hver fase:

![Angivelse af korrekturlæsere for fordeling.](../media/disposition-reviewers.png) 

Vælg **Tilføj en fase**, og navngive din fase for at identificere den. Angiv derefter korrekturlæserne for det pågældende trin.

Til korrekturlæserne skal du angive en bruger eller en mailaktiveret sikkerhedsgruppe. Microsoft 365 ([tidligere Office 365 grupper](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)) understøttes ikke til denne indstilling.

Hvis du har brug for mere end én person til at gennemgå et element i slutningen af dets opbevaringsperiode, skal du vælge Tilføj en fase igen og gentage konfigurationsprocessen for antallet af trin, du har brug for, med maksimalt fem trin. 

Inden for hver enkelt dispositionsfase er alle de brugere, du angiver for det pågældende trin, autoriseret til at tage den næste handling for elementet i slutningen af dets opbevaringsperiode. Disse brugere kan også føje andre brugere til deres gennemgangsfase for disposition.

> [!NOTE]
> Hvis du har konfigureret opbevaringsnavne, før gennemgang af flere faser var tilgængelig, kan du opgradere dine etiketter for at understøtte denne funktion: I guiden til etiketter skal du vælge Tilføj en fase eller redigere de eksisterende korrekturlæsere eller tilføje nye korrekturlæsere.

I konfigurationsfasen kan du for hver angivet fase omdøbe den, ændre rækkefølgen eller fjerne den ved at vælge indstillingen Fasehandlinger (**...**): 

![Trinhandlinger for gennemgang af fordeling.](../media/stage-actions-disposition-review.png)

Du kan dog ikke ændre rækkefølgen eller fjerne en fase, når du har oprettet opbevaringsnavnet.

Når du har angivet dine korrekturlæsere, skal du huske at give dem tilladelse **til rollen Dispositionsstyring** . Du kan finde flere oplysninger i [afsnittet Tilladelser til disposition](#permissions-for-disposition) på denne side.

### <a name="how-to-customize-email-messages-for-disposition-review"></a>Sådan tilpasser du mails til dispositionsgennemsyn

Eksempel på standardmailmeddelelse sendt til en korrekturlæser:

![Eksempel på mailbesked med standardtekst, når et element er klar til gennemgang af disposition.](../media/disposition-review-email.png)

Du kan tilpasse de mails, der sendes til korrekturlæsere af dispositionen for den første meddelelse og derefter påmindelser.

Fra alle siderne til datastyring i overholdelsescenteret skal du vælge **Indstillinger for datastyring**:  

![Indstillinger for datastyring.](../media/record-management-settings.png)

Vælg **og angiv** , om du kun vil bruge standardmailmeddelelsen, eller tilføj din egen tekst til standardmeddelelsen i sektionen Mailbeskeder **om dispositionsvurderinger** under fanen Disposition. Din brugerdefinerede tekst føjes til mailinstruktionerne efter oplysningerne om opbevaringsmærkaten og før de næste trins instruktioner.

Tekst til alle sprog kan tilføjes, men formatering og billeder understøttes ikke. URL-adresser og mailadresser kan indtastes som tekst, og afhængigt af mailklienten kan du få vist som links eller uformateret tekst i den brugerdefinerede mail.

Eksempeltekst, der skal tilføjes:

```console
If you need additional information, visit the helpdesk website (https://support.contoso.com) or send them an email (helpdesk@contoso.com).
```

Vælg **Gem** for at gemme ændringerne.

### <a name="viewing-and-disposing-of-content"></a>Visning og afvisning af indhold

Når en korrekturlæser får besked via mail om, at indholdet er klar til at blive gennemset, kan vedkommende klikke på et link i mailen, der  fører vedkommende direkte til siden **Disposition** fra Datastyring i Microsoft 365 Overholdelsescenter. Her kan korrekturlæserne se, hvor mange elementer for hver opbevaringsetiket, der venter på disposition, med den **Type** , der viser **Afventer disposition**. De vælger derefter en opbevaringsetiket og **Åbn i nyt vindue for** at få vist alt indhold med den pågældende etiket:

![Åbn i nyt vindue for gennemgang af disposition.](../media/open-in-new-window.png)

På siden **Ventende dispositioner** kan de se alle ventende dispositioner for den pågældende etiket. Når et eller flere elementer er markeret, kan de bruge minivisningsruden og fanen **Kilde, Detaljer** og Oversigt til  at undersøge **indholdet, før** der sker noget på det:

![Dispositionsindstillinger.](../media/retention-disposition-options.png)

Hvis du bruger det vandrette rullepanel eller lukker min.gennemsynsruden, kan du se flere kolonner, der indeholder udløbsdatoen og navnet på dispositionsgennemsynsfasen.

Som du kan se i det viste eksempel, er de understøttede handlinger: 
  
- **Godkend afhændelse**:
    - Når denne handling er valgt for en midlertidig dispositionsgennemgang (du har konfigureret flere faser): Elementet flyttes til den næste dispositionsfase.
    - Når denne handling er valgt til den sidste fase af gennemgangen af dispositionen, eller der kun er én dispositionsfase: Elementet markeres som berettiget til permanent sletning, hvilket derefter sker inden for 7 dage.
- **Relabel**:
    - Når denne handling er valgt, afslutter elementet gennemgangen af dispositionen for den oprindelige etiket. Elementet er derefter underlagt opbevaringsindstillingerne for den nyligt valgte opbevaringsmærkat.
- **Udvid**:
    - Når denne handling er valgt, suspenderes dispositionsgennemsyn effektivt indtil slutningen af den udvidede periode, og derefter udløses dispositionsgennemsyn igen fra første fase.
- **Tilføj korrekturlæsere**:
    - Når denne handling er markeret, bliver brugeren bedt om at angive og tilføje andre brugere til gennemsyn.
    
    > [!NOTE]
    > Denne handling giver ikke automatisk de nødvendige [tilladelser til de](#permissions-for-disposition) brugere, der er tilføjet. Hvis de ikke har disse tilladelser, kan de ikke deltage i gennemgangen af dispositionen.

Hver handling, der er foretaget, har en tilsvarende overvågningshændelse i gruppen [Aktiviteter til overvågning](search-the-audit-log-in-security-and-compliance.md#disposition-review-activities) af dispositionsgennemsyn.

Under en gennemgang af dispositionen flyttes indholdet aldrig fra dets oprindelige placering, og det markeres ikke til permanent sletning, før denne handling er valgt af en korrekturlæser for den endelige fase eller kun dispositionsfasen.

## <a name="disposition-of-records"></a>Disposition af poster

Fra **hovedsiden til** administration af poster > **fanen Disposition** kan du identificere:

- Elementer, der er blevet slettet som et resultat af en gennemgang af dispositionen.
- Elementer, der er markeret som en post eller en lovgivningsmæssig post, som blev slettet automatisk ved afslutningen af deres opbevaringsperiode.

Disse elementer viser **Poster, der er** afhændet **i kolonnen Type** . Eksempel:

![Elementer, der blev afhændet uden en gennemgang af dispositionen.](../media/records-disposed2.png)

> [!NOTE]
> Denne funktion bruger oplysninger [fra den samlede](search-the-audit-log-in-security-and-compliance.md) overvågningslog og kræver derfor overvågning for at være aktiveret og søgbar, så de tilhørende hændelser registreres.[](turn-audit-log-search-on-or-off.md)

Hvis du vil overvåge slettede elementer, der er markeret som poster eller lovgivningsposter,  skal du søge efter Slettet fil, der er markeret som en post i kategorien Filer og **sideaktiviteter**. Denne overvågningshændelse gælder for dokumenter og mails.

## <a name="filter-and-export-the-views"></a>Filtrer og eksportér visningerne

Når du vælger et opbevaringsnavn på siden **Disposition**, kan du under fanen Afventer **disposition** (hvis det  er relevant) og fanen Kassér elementer filtrere visningerne, så du nemmere kan finde elementer.

For ventende dispositioner er tidsintervallet baseret på udløbsdatoen. For afhændede varer er tidsintervallet baseret på datoen for sletningen.
  
Du kan eksportere oplysninger om elementerne i begge visning som en .csv, som du derefter kan sortere og administrere ved hjælp af Excel.
