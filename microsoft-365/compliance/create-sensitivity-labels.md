---
title: Opret og udgiv følsomhedsmærkater
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: 'Et krav til alle Microsoft Information Protection: Opret, konfigurer og udgiv følsomhedsmærkater for at klassificere og beskytte din organisations data.'
ms.openlocfilehash: b5bc61de14f54d65e4ce5eb6f7ae78303626c123
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587335"
---
# <a name="create-and-configure-sensitivity-labels-and-their-policies"></a>Opret og konfigurer følsomhedsmærkater og deres politikker

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Alle Microsoft Information Protection (nogle gange forkortet til MIP) implementeres ved hjælp af [følsomhedsmærkater](sensitivity-labels.md). Hvis du vil oprette og publicere disse etiketter, skal du gå <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">til Microsoft 365 Overholdelsescenter</a>.

Først skal du oprette og konfigurere de følsomhedsmærkater, du vil gøre tilgængelige for apps og andre tjenester. De etiketter, du vil have, at brugerne skal se og anvende fra Office apps.

Opret derefter en eller flere etiketpolitikker, der indeholder de etiketter og politikindstillinger, du konfigurerer. Det er etiketpolitikken, der publicerer etiketterne og indstillingerne for dine valgte brugere og placeringer.

## <a name="before-you-begin"></a>Før du begynder

Organisationens globale administrator har fuld tilladelse til at oprette og administrere alle aspekter af følsomhedsmærkater. Hvis du ikke logger på som global administrator, skal du se Tilladelser, der [kræves til at oprette og administrere følsomhedsmærkater](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels).

## <a name="create-and-configure-sensitivity-labels"></a>Opret og konfigurer følsomhedsmærkater

1. Fra [Microsoft 365 Overholdelsescenter vælge](https://compliance.microsoft.com/) **SolutionsInformation** >  **Protection**
    
    Hvis du ikke umiddelbart kan se denne indstilling, skal du først vælge **Vis alle**.

2. På siden **Etiketter skal** du vælge **+ Opret en etiket for** at starte konfigurationen af Ny følsomhedsetiket. 

    Fra Microsoft 365 Overholdelsescenter:

    ![Opret et følsomhedsmærkat.](../media/create-sensitivity-label-full.png)

    > [!NOTE]
    > Som standard har lejere ikke nogen etiketter, og du skal oprette dem. Etiketterne i eksempelbilledet viser standardetiketter, der [er overført fra Azure Information Protection](/azure/information-protection/configure-policy-migrate-labels).

3. På siden **Definer omfanget for** denne etiket bestemmer de valgte indstillinger navnets omfang for de indstillinger, du kan konfigurere, og hvor de bliver synlige, når de publiceres:

    ![Omfang for følsomhedsmærkater.](../media/sensitivity-labels-scopes.png)

    - Hvis **filer & er** markeret, kan du konfigurere de indstillinger, der gælder for apps, der understøtter følsomhedsmærkater, f.eks. Office Word og Outlook. Hvis denne indstilling ikke vælges, får du vist den første side i disse indstillinger, men du kan ikke konfigurere dem, og etiketterne vil ikke være tilgængelige for brugere til at vælge i disse apps.

    - Hvis **Grupper & websteder** er markeret, kan du konfigurere de indstillinger, der gælder for Microsoft 365 grupper og websteder for Teams og SharePoint. Hvis denne indstilling ikke vælges, får du vist den første side i disse indstillinger, men du kan ikke konfigurere dem, og brugerne kan ikke vælge etiketterne til grupper og websteder.

    Du kan finde oplysninger **om området Skemalagte dataaktiver** under [Navn giv dit indhold en automatisk mærkat i Azure-visning](/azure/purview/create-sensitivity-label).

4. Følg konfigurationsprompterne for etiketindstillingerne.

    Du kan finde flere oplysninger om etiketindstillingerne under [](sensitivity-labels.md#what-sensitivity-labels-can-do) Hvad følsomhedsetiketter kan gøre fra oversigtsoplysningerne og bruge hjælpen i brugergrænsefladen til individuelle indstillinger.

5. Gentag disse trin for at oprette flere etiketter. Men hvis du vil oprette et undernavn, skal du først markere det overordnede navn og vælge **...** **for at** få flere handlinger og derefter **vælge Tilføj underetiket**.

6. Når du har oprettet alle de etiketter, du skal bruge, kan du gennemse deres rækkefølge og om nødvendigt flytte dem op eller ned. Hvis du vil ændre rækkefølgen af en etiket, skal **du vælge ...** for **flere** handlinger og derefter **vælge Flyt op** **eller Flyt ned**. Du kan finde flere oplysninger [under Etiketprioritet (rækkefølge vigtig)](sensitivity-labels.md#label-priority-order-matters) fra oversigtsoplysningerne.

Hvis du vil redigere en eksisterende etiket, skal du markere den og derefter **vælge knappen Rediger** etiket:

![Knappen Rediger etiket for at redigere et følsomhedsmærkat.](../media/edit-sensitivity-label-full.png)

Denne knap starter **konfigurationen af Rediger følsomhedsmærkat** , som giver dig mulighed for at ændre alle navneindstillingerne i trin 4.

Slet ikke en etiket, medmindre du forstår påvirkningen for brugerne. Du kan finde flere oplysninger i [afsnittet Fjerne og slette](#removing-and-deleting-labels) navne. 

> [!NOTE]
> Hvis du redigerer en etiket, der allerede er udgivet ved hjælp af en etiketpolitik, er der ikke behov for ekstra trin, når du er færdig med konfigurationen. Du behøver f.eks. ikke at føje den til en ny etiketpolitik, for at ændringerne bliver tilgængelige for de samme brugere. Der kan dog gå op til 24 timer, før ændringerne replikeres til alle apps og tjenester.

Før du publicerer dine etiketter, vil de ikke kunne vælges i apps eller til tjenester. Hvis etiketterne skal udgives, skal de [føjes til en etiketpolitik](#publish-sensitivity-labels-by-creating-a-label-policy).

> [!IMPORTANT]
> På denne **fane Etiketter** skal du ikke vælge fanen  Udgiv navne (eller knappen  Udgiv etiket, når du redigerer en etiket), medmindre du har brug for at oprette en ny etiketpolitik. Du skal kun bruge flere etiketpolitikker, hvis brugerne har brug for forskellige navne eller forskellige politikindstillinger. Formål at have så få etiketpolitikker som muligt – det er ikke ualmindeligt, at du kun har én etiketpolitik for organisationen.

### <a name="additional-label-settings-with-security--compliance-center-powershell"></a>Yderligere etiketindstillinger med Security & Compliance Center PowerShell

Yderligere etiketindstillinger er tilgængelige med [Set-Label-cmdlet'en](/powershell/module/exchange/set-label) [fra Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell).

Eksempel:

- Brug *parameteren LocaleSettings* for multinationale installationer, så brugerne kan se navnet og værktøjstip på deres lokale sprog. Følgende [afsnit indeholder](#example-configuration-to-configure-a-sensitivity-label-for-different-languages) en eksempelkonfiguration, der angiver etiketnavnet og værktøjstipteksten for fransk, italiensk og tysk.

- Den samlede Azure Information Protection-etiketklient understøtter en omfattende liste [](/azure/information-protection/rms-client/clientv2-admin-guide-customizations) over avancerede indstillinger, som omfatter indstilling af en etiketfarve og anvendelse af en brugerdefineret egenskab, når der anvendes en etiket. Du kan se den komplette liste [under Tilgængelige avancerede indstillinger for navne](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-labels) fra denne klients administratorvejledning.

#### <a name="example-configuration-to-configure-a-sensitivity-label-for-different-languages"></a>Eksempelkonfiguration til konfiguration af følsomhedsmærkat for forskellige sprog

Følgende eksempel viser PowerShell-konfigurationen for en etiket med navnet "Offentlig" med pladsholdertekst for værktøjstippet. I dette eksempel er navnet og værktøjstipteksten konfigureret til fransk, italiensk og tysk.

Som et resultat af denne konfiguration kan brugere, der har Office, der bruger disse visningssprog, se deres navne og værktøjstip på det samme sprog. På samme måde kan brugere, der har disse sprogversioner af Windows se deres navnenavne og værktøjstip på deres lokale sprog, når de bruger højreklikshandlingerne til mærkning, hvis du har en samlet Azure Information Protection-klient.

For de sprog, du skal understøtte, skal du bruge Office-sprogidentifikatorer (også kaldet sprogmærker), og angive din egen oversættelse for etiketnavnet og [værktøjstip](/deployoffice/office2016/language-identifiers-and-optionstate-id-values-in-office-2016#language-identifiers).

Før du kører kommandoerne i PowerShell, skal du først [oprette forbindelse til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

```powershell
$Languages = @("fr-fr","it-it","de-de")
$DisplayNames=@("Publique","Publico","Oeffentlich")
$Tooltips = @("Texte Français","Testo italiano","Deutscher text")
$label = "Public"
$DisplayNameLocaleSettings = [PSCustomObject]@{LocaleKey='DisplayName';
Settings=@(
@{key=$Languages[0];Value=$DisplayNames[0];}
@{key=$Languages[1];Value=$DisplayNames[1];}
@{key=$Languages[2];Value=$DisplayNames[2];})}
$TooltipLocaleSettings = [PSCustomObject]@{LocaleKey='Tooltip';
Settings=@(
@{key=$Languages[0];Value=$Tooltips[0];}
@{key=$Languages[1];Value=$Tooltips[1];}
@{key=$Languages[2];Value=$Tooltips[2];})}
Set-Label -Identity $Label -LocaleSettings (ConvertTo-Json $DisplayNameLocaleSettings -Depth 3 -Compress),(ConvertTo-Json $TooltipLocaleSettings -Depth 3 -Compress)
```

## <a name="publish-sensitivity-labels-by-creating-a-label-policy"></a>Publicere følsomhedsmærkater ved at oprette en etiketpolitik

1. Fra [Microsoft 365 Overholdelsescenter vælge](https://compliance.microsoft.com/) **SolutionsInformation** >  **Protection**
    
    Hvis du ikke umiddelbart kan se denne indstilling, skal du først vælge **Vis alle**.

2. Vælg fanen **Etiketpolitikker** og derefter Publicer etiket **for at** starte **konfigurationen af Opret** politik:

    Fra Microsoft 365 Overholdelsescenter:

    ![Publicere etiketter.](../media/publish-sensitivity-labels-full.png)

    > [!NOTE]
    > Som standard har lejere ikke nogen etiketpolitikker, og du skal oprette dem. 

3. På siden **Vælg følsomhedsmærkater til publicering** skal du vælge **linket Vælg følsomhedsmærkater for at publicere** . Markér de etiketter, du vil gøre tilgængelige i apps og tjenester, og vælg derefter **Tilføj**.

    > [!IMPORTANT]
    > Hvis du vælger et undernavn, skal du sørge for også at markere det overordnede navn.

4. Gennemse de markerede navne, og hvis du vil foretage ændringer, skal du vælge **Rediger**. Ellers skal du **vælge Næste**.

5. Følg instruktionerne for at konfigurere politikindstillingerne.

    De politikindstillinger, du ser, svarer til omfanget af de etiketter, du har valgt. Hvis du f.eks. har markeret navne, der kun har området Filer **& mails**, kan du ikke se politikindstillingerne Anvend dette navn  som standard på grupper og websteder og Kræv, at brugerne anvender et navn på deres grupper og **websteder.**

    Du kan finde flere oplysninger om disse indstillinger [under Hvilken etiketpolitik](sensitivity-labels.md#what-label-policies-can-do) kan du bruge i oversigtsoplysningerne og bruge hjælpen i brugergrænsefladen til individuelle indstillinger.

    For etiketter, der er **konfigureret til Azure-visningsaktiver (forhåndsvisning)**: Disse etiketter har ikke nogen tilknyttede politikindstillinger.

6. Gentag disse trin, hvis du har brug for forskellige politikindstillinger for forskellige brugere eller områder. Du vil f.eks. have flere etiketter til en gruppe af brugere eller en anden standardetiket til et undersæt af brugere. Eller, hvis du har konfigureret etiketter til at have forskellige områder.

7. Hvis du opretter mere end én etiketpolitik, der kan medføre en konflikt for en bruger, skal du gennemse politikrækkefølgen og om nødvendigt flytte dem op eller ned. Hvis du vil ændre rækkefølgen af en etiketpolitik, skal du **vælge ...** for **at få flere** handlinger og derefter **vælge Flyt op** **eller Flyt ned**. Få mere at vide under [Prioritet af etiketpolitik (rækkefølge vigtig)](sensitivity-labels.md#label-policy-priority-order-matters) i oversigtsoplysningerne.

Når du **gennemfører konfigurationen** Opret politik, udgives etiketpolitikken automatisk. Hvis du vil foretage ændringer i en publiceret politik, skal du blot redigere den. Du kan ikke vælge en bestemt handling for udgiv eller genpublicer.

Hvis du vil redigere en eksisterende etiketpolitik, skal du markere den og derefter **vælge knappen Rediger** politik: 

![Rediger et følsomhedsmærkat.](../media/edit-sensitivity-label-policy-full.png)

Denne knap starter konfigurationen **Opret politik** , som gør det muligt at redigere, hvilke etiketter der er inkluderet samt navneindstillingerne. Når du har fuldført konfigurationen, replikeres eventuelle ændringer automatisk til de valgte brugere og tjenester.

Når du bruger indbygget mærkning til Office-apps på Windows, macOS, iOS og Android, får brugerne vist nye etiketter inden for fire timer og inden for en time for Word, Excel og PowerPoint på internettet, når du opdaterer browseren. Der kan dog gå op til 24 timer, før ændringer replikeres til alle apps og tjenester.

Andre apps og tjenester, der understøtter følsomhedsmærkater, kan blive opdateret oftere end 24 timer med deres egne opdateringsplaner og udløsere til politikopdateringer. Se deres dokumentation for at få flere oplysninger. For eksempel kan du for den samlede Azure Information Protection-etiketklient se opdateringsrækken for Politikker i de detaljerede sammenligninger [for tabellen Azure Information Protection-klienter](/azure/information-protection/rms-client/use-client#detailed-comparisons-for-the-azure-information-protection-clients).

> [!TIP]
> Husk at faktor i tidsafhængigheder, der nogle gange kan forsinke følsomhedsmærkater og etiketpolitikker i at fungere som forventet. Hvis du f.eks. udfylder ændringer af en ny gruppe og gruppemedlemskab, begrænsninger for netværksreplikering og båndbredde samt cachelagring af gruppemedlemskaber fra [Azure Information Protection-tjenesten](/azure/information-protection/prepare#group-membership-caching-by-azure-information-protection) for etiketter, der anvender kryptering.
> 
> Med mange eksterne afhængigheder, som hver har deres egen tidscyklus, er det en god ide at vente 24 timer, før du bruger tid på fejlfinding af etiketter og etiketpolitikker for de seneste ændringer.

### <a name="additional-label-policy-settings-with-security--compliance-center-powershell"></a>Yderligere indstillinger for etiketpolitik med Security & Compliance Center PowerShell

Yderligere indstillinger for etiketpolitik er tilgængelige med [Set-LabelPolicy-cmdlet'en](/powershell/module/exchange/set-labelpolicy) [fra Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell).

Den samlede Azure Information Protection-etiketklient understøtter [](/azure/information-protection/rms-client/clientv2-admin-guide-customizations) mange avancerede indstillinger, der omfatter overførsel fra andre mærkningsløsninger, og pop op-meddelelser i Outlook, der advarer, justerer eller blokerer mails, der sendes. Du kan finde en komplet liste [under Tilgængelige avancerede indstillinger for etiketpolitikker](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-label-policies) fra denne klients administratorvejledning.

## <a name="use-powershell-for-sensitivity-labels-and-their-policies"></a>Brug PowerShell til følsomhedsmærkater og deres politikker

Du kan nu bruge [Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell) til at oprette og konfigurere alle de indstillinger, du ser i din etiketadministration. Det betyder, at ud over at bruge PowerShell til indstillinger, der ikke er tilgængelige i navneadministrationen, kan du nu fuldt ud scripte oprettelse og vedligeholdelse af følsomhedsetiketter og politikker for følsomhedsmærkater. 

Se følgende dokumentation for understøttede parametre og værdier:

- [Ny etiket](/powershell/module/exchange/new-label)
- [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy)
- [Set-Label](/powershell/module/exchange/set-label)
- [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy)

Du kan også bruge [Remove-Label](/powershell/module/exchange/remove-label) og [Remove-LabelPolicy](/powershell/module/exchange/remove-labelpolicy) , hvis du har brug for at scripte sletning af følsomhedsetiketter eller politikker for følsomhedsetiketter. Før du sletter følsomhedsmærkater, skal du imidlertid sørge for at læse følgende afsnit.

## <a name="removing-and-deleting-labels"></a>Fjerne og slette navne

I et produktionsmiljø er det usandsynligt, at du skal fjerne følsomhedsmærkater fra en etiketpolitik eller slette følsomhedsmærkater. Det er mere sandsynligt, at du skal udføre en eller en af disse handlinger i løbet af en indledende testfase. Sørg for, at du forstår, hvad der sker, når du gør en af disse handlinger.

Det er mindre risikabelt at fjerne en etiket fra en etiketpolitik end at slette den, og du kan altid føje den tilbage til en etiketpolitik senere, hvis det er nødvendigt:

- Når du fjerner en etiket fra en etiketpolitik, så navnet ikke længere udgives til de oprindeligt angivne brugere, vil brugerne ikke længere kunne se den etiket, de skal vælge, næste gang etiketpolitikken opdateres, i deres Office-app. Men hvis etiketten er blevet anvendt på dokumenter eller mails, fjernes etiketten ikke fra indholdet. Enhver kryptering, der blev anvendt af etiketten, forbliver, og den underliggende beskyttelsesskabelon forbliver publiceret. 

- For navne, der er fjernet, men tidligere har været anvendt på indhold, kan brugere, der bruger indbygget mærkning til Word, Excel og PowerPoint, stadig se det anvendte etiketnavn på statuslinjen. På samme måde vises navne, der er blevet fjernet, SharePoint på websteder, stadig navnet på mærkaten i **kolonnen** Følsomhed.

Til sammenligning sletter du en etiket:

- Hvis etiketten anvendes kryptering, arkiveres den underliggende beskyttelsesskabelon, så tidligere beskyttet indhold stadig kan åbnes. På grund af denne arkiverede skabelon til beskyttelse kan du ikke oprette en ny etiket med det samme navn. Selvom det er muligt at slette en skabelon til beskyttelse ved hjælp af [PowerShell](/powershell/module/aipservice/remove-aipservicetemplate), skal du ikke gøre dette, medmindre du er sikker på, at du ikke behøver at åbne indhold, der er krypteret med den arkiverede skabelon.

- For skrivebordsapps: Etiketoplysningerne i metadataene forbliver, men fordi et navne-id til navnetilknytning ikke længere er muligt, kan brugerne ikke se det anvendte etiketnavn vist (f.eks. på statuslinjen), så brugerne antager, at indholdet ikke er mærket. Hvis navnet anvendes kryptering, forbliver krypteringen, og når indholdet åbnes, kan brugerne stadig se navnet og beskrivelsen af den nu arkiverede beskyttelsesskabelon.

- For Office på internettet: Brugerne kan ikke se navnet på navnet på statuslinjen **eller i kolonnen** Følsomhed. Etiketoplysningerne i metadataene forbliver kun, hvis etiketten ikke anvender kryptering. Hvis etiketten anvendte kryptering, og du har aktiveret følsomhedsmærkater [for SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md), fjernes etiketoplysningerne i metadataene, og krypteringen fjernes. 

Når du fjerner et følsomhedsmærkat fra en etiketpolitik eller sletter en følsomhedsmærkat, kan det tage op til 24 timer, før disse ændringer replikeres til alle brugere og tjenester.

## <a name="next-steps"></a>Næste trin

Hvis du vil konfigurere og bruge dine følsomhedsmærkater til bestemte scenarier, skal du bruge følgende artikler:

- [Begræns adgangen til indhold ved hjælp af kryptering i følsomhedsmærkater](encryption-sensitivity-labels.md)

- [Anvend en følsomhedsmærkat på indhold automatisk](apply-sensitivity-label-automatically.md)

- [Brug følsomhedsmærkater med teams, grupper og websteder](sensitivity-labels-teams-groups-sites.md)

- [Aktivér følsomhedsetiketter Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)

Hvis du vil overvåge, hvordan etiketterne bruges, skal du [se Introduktion til dataklassificering](data-classification-overview.md).
