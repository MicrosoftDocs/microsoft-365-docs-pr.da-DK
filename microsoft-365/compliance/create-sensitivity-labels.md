---
title: Opret og publicer følsomhedsmærkater
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
description: 'Et krav til alle Microsoft Purview-Information Protection-løsninger: Opret, konfigurer og publicer følsomhedsmærkater for at klassificere og beskytte din organisations data.'
ms.openlocfilehash: e35d6e317abc3fb32bb11a6bdf937f303212fc23
ms.sourcegitcommit: 4cd8be7c22d29100478dce225dce3bcdce52644d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/10/2022
ms.locfileid: "65302348"
---
# <a name="create-and-configure-sensitivity-labels-and-their-policies"></a>Opret og konfigurer følsomhedsmærkater og deres politikker

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Alle Microsoft Purview-Information Protection-løsninger implementeres ved hjælp af [følsomhedsmærkater](sensitivity-labels.md). Hvis du vil oprette og publicere disse mærkater, skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-overholdelsesportalen</a>.

Først skal du oprette og konfigurere de følsomhedsmærkater, du vil gøre tilgængelige for apps og andre tjenester. De mærkater, du vil have, at brugerne skal se og anvende fra Office apps.

Opret derefter en eller flere mærkatpolitikker, der indeholder de mærkater og politikindstillinger, du konfigurerer. Det er mærkatpolitikken, der publicerer mærkaterne og indstillingerne for de valgte brugere og placeringer.

## <a name="before-you-begin"></a>Før du begynder

Den globale administrator for din organisation har fuld tilladelse til at oprette og administrere alle aspekter af følsomhedsmærkater. Hvis du ikke logger på som global administrator, skal du se [Tilladelser, der kræves for at oprette og administrere følsomhedsmærkater](get-started-with-sensitivity-labels.md#permissions-required-to-create-and-manage-sensitivity-labels).

## <a name="create-and-configure-sensitivity-labels"></a>Opret og konfigurer følsomhedsmærkater

1. Vælg **LøsningerInformationsbeskyttelse**  >  på [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/)
    
    Hvis du ikke kan se denne indstilling med det samme, skal du først vælge **Vis alle**.

2. På siden **Etiketter** skal du vælge **+ Opret en mærkat** for at starte den nye konfiguration af følsomhedsmærkat: 
    
    ![Opret en følsomhedsmærkat.](../media/create-sensitivity-label-full.png)

    > [!NOTE]
    > Lejere har som standard ingen mærkater, og du skal oprette dem. Etiketterne i eksempelbilledet viser de standardmærkater, der er [overført fra Azure Information Protection](/azure/information-protection/configure-policy-migrate-labels).

3. På siden **Definer området for denne etiket** bestemmer de valgte indstillinger etikettens omfang for de indstillinger, du kan konfigurere, og hvor de vil være synlige, når de udgives:

    ![Områder for følsomhedsmærkater.](../media/sensitivity-labels-scopes.png)

    - Hvis **Filer & mails** er valgt, kan du konfigurere indstillinger, der gælder for apps, der understøtter følsomhedsmærkater, f.eks. Office Word og Outlook. Hvis denne indstilling ikke er valgt, kan du se den første side med disse indstillinger, men du kan ikke konfigurere dem, og mærkaterne vil ikke være tilgængelige for brugerne at vælge i disse apps.

    - Hvis **Grupper & websteder** er valgt, kan du konfigurere indstillinger, der gælder for Microsoft 365 grupper, og websteder for Teams og SharePoint. Hvis denne indstilling ikke er valgt, får du vist den første side med disse indstillinger, men du kan ikke konfigurere dem, og mærkaterne vil ikke være tilgængelige for brugerne at vælge for grupper og webstedet.

    Du kan få oplysninger om området **Skematiserede dataaktiver** under [Mærk automatisk dit indhold i Microsoft Purview-dataoversigt](/azure/purview/create-sensitivity-label).

4. Følg konfigurationsprompterne for mærkatindstillingerne.

    Du kan finde flere oplysninger om mærkatindstillingerne under [Hvad følsomhedsmærkater kan gøre](sensitivity-labels.md#what-sensitivity-labels-can-do) ud fra oversigtsoplysningerne og bruge hjælpen i brugergrænsefladen til individuelle indstillinger.

5. Gentag disse trin for at oprette flere mærkater. Men hvis du vil oprette en undermærkat, skal du først vælge den overordnede etiket og vælge **...** for **Flere handlinger** og derefter vælge **Tilføj undernavn**.

6. Når du har oprettet alle de mærkater, du har brug for, kan du gennemse deres rækkefølge og om nødvendigt flytte dem op eller ned. Hvis du vil ændre rækkefølgen af en etiket, skal du vælge **...** for **Flere handlinger** og derefter vælge **Flyt op** eller **Flyt ned**. Du kan få flere oplysninger under [Mærkatprioritet (ordrespørgsmål)](sensitivity-labels.md#label-priority-order-matters) i oversigtsoplysningerne.

Hvis du vil redigere en eksisterende etiket, skal du markere den og derefter vælge knappen **Rediger etiket** :

![Knappen Rediger mærkat for at redigere en følsomhedsmærkat.](../media/edit-sensitivity-label-full.png)

Denne knap starter konfigurationen **Rediger følsomhedsmærkat** , hvor du kan ændre alle mærkatindstillingerne i trin 4.

Slet ikke en mærkat, medmindre du forstår virkningen for brugerne. Du kan få flere oplysninger i afsnittet [Fjernelse og sletning af mærkater](#removing-and-deleting-labels) . 

> [!NOTE]
> Hvis du redigerer en etiket, der allerede er publiceret ved hjælp af en mærkatpolitik, er der ikke behov for ekstra trin, når du er færdig med konfigurationen. Du behøver f.eks. ikke at føje den til en ny mærkatpolitik, før ændringerne bliver tilgængelige for de samme brugere. Det kan dog tage op til 24 timer, før ændringerne replikeres til alle apps og tjenester.

Før du publicerer dine mærkater, vil de ikke være tilgængelige til valg i apps eller til tjenester. Hvis du vil publicere etiketterne, skal de [føjes til en mærkatpolitik](#publish-sensitivity-labels-by-creating-a-label-policy).

> [!IMPORTANT]
> Under denne fane **Etiketter** skal du ikke vælge fanen **Publicer navne** (eller knappen **Publicer navn** , når du redigerer en etiket), medmindre du har brug for at oprette en ny etiketpolitik. Du skal kun bruge flere mærkatpolitikker, hvis brugerne har brug for forskellige mærkater eller forskellige politikindstillinger. Målet er at have så få mærkatpolitikker som muligt – det er ikke ualmindeligt kun at have én mærkatpolitik for organisationen.

### <a name="additional-label-settings-with-security--compliance-center-powershell"></a>Yderligere mærkatindstillinger med Security & Compliance Center PowerShell

Der er flere mærkatindstillinger tilgængelige med [Set-Label-cmdlet'en](/powershell/module/exchange/set-label) fra [Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell).

Eksempel:

- Brug parameteren *LocaleSettings* til multinationale installationer, så brugerne kan se navnet og værktøjstippet på deres lokale sprog. [I følgende afsnit](#example-configuration-to-configure-a-sensitivity-label-for-different-languages) er der et eksempel på en konfiguration, der angiver navnet og værktøjstippet for fransk, italiensk og tysk.

- Azure Information Protection Unified Labeling-klienten understøtter en omfattende liste over [avancerede indstillinger](/azure/information-protection/rms-client/clientv2-admin-guide-customizations), der omfatter angivelse af en navnefarve og anvendelse af en brugerdefineret egenskab, når der anvendes en mærkat. Du kan se den komplette liste under [Tilgængelige avancerede indstillinger for mærkater](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-labels) i denne klients administratorvejledning.

#### <a name="example-configuration-to-configure-a-sensitivity-label-for-different-languages"></a>Eksempelkonfiguration til konfiguration af en følsomhedsmærkat for forskellige sprog

I følgende eksempel vises PowerShell-konfigurationen for en etiket med navnet "Offentlig" med pladsholdertekst for værktøjstippet. I dette eksempel er navnet og teksten i værktøjstippet konfigureret til fransk, italiensk og tysk.

Som et resultat af denne konfiguration kan brugere, der har Office apps, der bruger disse visningssprog, se deres navne og værktøjstip på det samme sprog. Hvis du på samme måde har Azure Information Protection Unified-mærkatklient installeret til mærkatfiler fra Stifinder, kan brugere, der har disse sprogversioner af Windows se deres navne og værktøjstip på deres lokale sprog, når de bruger højreklikshandlinger til mærkning.

For de sprog, du skal understøtte, skal du bruge Office [sprog-id'er](/deployoffice/office2016/language-identifiers-and-optionstate-id-values-in-office-2016#language-identifiers) (også kendt som sprogkoder) og angive din egen oversættelse for navnet og værktøjstippet.

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

## <a name="publish-sensitivity-labels-by-creating-a-label-policy"></a>Publicer følsomhedsmærkater ved at oprette en mærkatpolitik

1. Vælg **LøsningerInformationsbeskyttelse**  >  på [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/)
    
    Hvis du ikke kan se denne indstilling med det samme, skal du først vælge **Vis alle**.

2. Vælg fanen **Mærkatpolitikker** , og **vælg derefter Publicer etiket** for at starte konfigurationen **af politikken Opret** :
    
    ![Publicer navne.](../media/publish-sensitivity-labels-full.png)
    
    > [!NOTE]
    > Lejere har som standard ingen mærkatpolitikker, og du skal oprette dem. 

3. På siden **Vælg følsomhedsmærkater, der skal publiceres** skal du vælge linket **Vælg følsomhedsmærkater, der skal udgives** . Vælg de mærkater, du vil gøre tilgængelige i apps og tjenester, og vælg derefter **Tilføj**.

    > [!IMPORTANT]
    > Hvis du vælger en undernavn, skal du sørge for også at vælge dens overordnede etiket.

4. Gennemse de markerede navne, og vælg **Rediger** for at foretage ændringer. Ellers skal du vælge **Næste**.

5. Følg prompterne for at konfigurere politikindstillingerne.

    De politikindstillinger, du får vist, svarer til omfanget af de valgte mærkater. Hvis du f.eks. har valgt navne, der kun har området **Filer & mails** , kan du ikke se politikindstillingerne **Anvend denne mærkat som standard på grupper og websteder og** **Kræv, at brugerne anvender en mærkat på deres grupper og websteder**.

    Du kan finde flere oplysninger om disse indstillinger under [Hvad mærkatpolitikker kan gøre](sensitivity-labels.md#what-label-policies-can-do) ud fra oversigtsoplysningerne og bruge hjælpen i brugergrænsefladen til individuelle indstillinger.

    For mærkater, der er konfigureret til **Microsoft Purview Data Map-aktiver (prøveversion)**: Disse mærkater har ingen tilknyttede politikindstillinger.

6. Gentag disse trin, hvis du har brug for forskellige politikindstillinger for forskellige brugere eller områder. Du vil f.eks. have flere mærkater for en gruppe brugere eller et andet standardnavn for et undersæt af brugere. Eller hvis du har konfigureret mærkater til at have forskellige områder.

7. Hvis du opretter mere end én mærkatpolitik, der kan resultere i en konflikt for en bruger, skal du gennemse politikrækkefølgen og om nødvendigt flytte dem op eller ned. Hvis du vil ændre rækkefølgen af en mærkatpolitik, skal du vælge **...** for **Flere handlinger** og derefter vælge **Flyt op** eller **Flyt ned**. Du kan få flere oplysninger under [Mærkatpolitikprioritet (ordrespørgsmål)](sensitivity-labels.md#label-policy-priority-order-matters) i oversigtsoplysningerne.

Når konfigurationen **af Opret politik** fuldføres, publiceres mærkatpolitikken automatisk. Hvis du vil foretage ændringer af en publiceret politik, skal du blot redigere den. Der er ingen specifik publicerings- eller genudgivelseshandling, som du kan vælge.

Hvis du vil redigere en eksisterende mærkatpolitik, skal du vælge den og derefter vælge knappen **Rediger politik** : 

![Rediger en følsomhedsmærkat.](../media/edit-sensitivity-label-policy-full.png)

Denne knap starter konfigurationen **af politikken Opret** , hvor du kan redigere, hvilke mærkater der er inkluderet, og etiketindstillingerne. Når du har fuldført konfigurationen, replikeres eventuelle ændringer automatisk til de valgte brugere og tjenester.

### <a name="additional-label-policy-settings-with-security--compliance-center-powershell"></a>Yderligere indstillinger for mærkatpolitik med Security & Compliance Center PowerShell

Yderligere indstillinger for mærkatpolitik er tilgængelige med [Set-LabelPolicy-cmdlet'en](/powershell/module/exchange/set-labelpolicy) fra [Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell).

Azure Information Protection Unified Labeling-klienten understøtter mange [avancerede indstillinger](/azure/information-protection/rms-client/clientv2-admin-guide-customizations), der omfatter overførsel fra andre mærkatløsninger, og pop op-meddelelser i Outlook, der advarer, begrunder eller blokerer mails, der sendes. Du kan se den komplette liste under [Tilgængelige avancerede indstillinger for mærkatpolitikker](/azure/information-protection/rms-client/clientv2-admin-guide-customizations#available-advanced-settings-for-label-policies) i denne klients administratorvejledning.

## <a name="when-to-expect-new-labels-and-changes-to-take-effect"></a>Hvornår kan du forvente, at nye mærkater og ændringer træder i kraft?

I forbindelse med indstillinger for mærkater og mærkatpolitik kan ændringerne overføres gennem tjenesterne i 24 timer. Der er mange eksterne afhængigheder, der hver især har deres egne tidscyklusser, så det er en god idé at vente denne 24-timers tidsperiode, før du bruger tid på fejlfinding af mærkater og mærkatpolitikker for de seneste ændringer.

Der er dog nogle scenarier, hvor ændringer af mærkater og mærkater kan træde i kraft meget hurtigere eller være længere end 24 timer. For nye og slettede følsomhedsmærkater for Word, Excel og PowerPoint på internettet kan du f.eks. se opdateringer replikeret inden for en time. Men for konfigurationer, der afhænger af, at en ny gruppe og gruppemedlemskab ændres, eller at netværksreplikeringsventetid og båndbreddebegrænsninger er begrænset, kan disse ændringer tage 24-48 timer.

## <a name="use-powershell-for-sensitivity-labels-and-their-policies"></a>Brug PowerShell til følsomhedsmærkater og deres politikker

Du kan nu bruge [Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell) til at oprette og konfigurere alle de indstillinger, du kan se i dit administrationscenter for mærkater. Det betyder, at du ud over at bruge PowerShell til indstillinger, der ikke er tilgængelige i administrationscentre for mærkater, nu fuldt ud kan scripte oprettelsen og vedligeholdelsen af følsomhedsmærkater og politikker for følsomhedsmærkater. 

Se følgende dokumentation for understøttede parametre og værdier:

- [Nyt navn](/powershell/module/exchange/new-label)
- [New-LabelPolicy](/powershell/module/exchange/new-labelpolicy)
- [Angiv navn](/powershell/module/exchange/set-label)
- [Set-LabelPolicy](/powershell/module/exchange/set-labelpolicy)

Du kan også bruge [Remove-Label](/powershell/module/exchange/remove-label) og [Remove-LabelPolicy](/powershell/module/exchange/remove-labelpolicy) , hvis du har brug for at scripte sletning af følsomhedsmærkater eller politikker for følsomhedsmærkater. Før du sletter følsomhedsmærkater, skal du dog sørge for at læse følgende afsnit.

## <a name="removing-and-deleting-labels"></a>Fjerner og sletter navne

I et produktionsmiljø er det usandsynligt, at du skal fjerne følsomhedsmærkater fra en mærkatpolitik eller slette følsomhedsmærkater. Det er mere sandsynligt, at du skal udføre en eller en af disse handlinger i en indledende testfase. Sørg for at forstå, hvad der sker, når du udfører en af disse handlinger.

Det er mindre risikabelt at fjerne en mærkat fra en mærkatpolitik end at slette den, og den kan altid tilføjes igen senere, hvis det er nødvendigt. Du kan ikke slette en etiket, hvis den stadig er i en mærkatpolitik.

Når du fjerner en mærkat fra en mærkatpolitik, så mærkaten ikke længere publiceres til de oprindeligt angivne brugere, kan brugerne ikke længere se den mærkat, der skal vælges i deres Office apps, næste gang mærkatpolitikken opdateres. Hvis denne etiket allerede er anvendt, fjernes navnet ikke fra indholdet eller objektbeholderen. Brugere, der bruger indbygget mærkat i skrivebordsapps til Word, Excel og PowerPoint, kan f.eks. stadig se navnet på det anvendte navn på statuslinjen. En anvendt objektbeholderetiket fortsætter med at beskytte det Teams eller SharePoint websted.

Når du til sammenligning sletter en etiket:

- Hvis mærkaten anvendte kryptering, arkiveres den underliggende beskyttelsesskabelon, så tidligere beskyttet indhold stadig kan åbnes. På grund af denne arkiverede beskyttelsesskabelon kan du ikke oprette en ny mærkat med det samme navn. Selvom det er muligt at slette en beskyttelsesskabelon ved hjælp af [PowerShell](/powershell/module/aipservice/remove-aipservicetemplate), skal du ikke gøre dette, medmindre du er sikker på, at du ikke behøver at åbne indhold, der er krypteret med den arkiverede skabelon.

- For dokumenter, der er gemt i SharePoint eller OneDrive, og du har [aktiveret følsomhedsmærkater for Office filer](sensitivity-labels-sharepoint-onedrive-files.md): Når du åbner dokumentet i Office på internettet, kan du ikke se den mærkat, der er anvendt i appen, og navnet vises ikke længere i kolonnen **Følsomhed** i SharePoint. Hvis den slettede mærkat anvendte kryptering, og tjenesterne kan behandle det krypterede indhold, fjernes krypteringen. Egress handlinger fra disse tjenester resulterer i det samme resultat. Download, kopiér til, flyt til og åbn f.eks. med en Office desktop- eller mobilapp. Selvom mærkatoplysningerne forbliver i filens metadata, kan apps ikke længere knytte mærkat-id'et til et vist navn, så brugerne antager, at en fil ikke er mærket.

- For dokumenter, der er gemt uden for SharePoint og OneDrive, eller du ikke har aktiveret følsomhedsmærkater for Office filer og for mails: Når du åbner indholdet, forbliver mærkatoplysningerne i metadataene, men uden navnetilknytningen for mærkat-id'et kan brugerne ikke se det anvendte mærkatnavn vist (f.eks. på statuslinjen for skrivebordsapps). Hvis den slettede mærkat anvendte kryptering, forbliver krypteringen, og brugerne kan stadig se navnet på og beskrivelsen af den nu arkiverede beskyttelsesskabelon.

- For objektbeholdere, f.eks. websteder i SharePoint og Teams: Etiketten fjernes, og de indstillinger, der er konfigureret med den pågældende mærkat, gennemtvinges ikke længere. Denne handling tager typisk mellem 48-72 timer for SharePoint websteder og kan være hurtigere i Teams og Microsoft 365-grupper.

Som med alle mærkatændringer tager det tid at replikere til alle brugere og tjenester, hvis du fjerner en følsomhedsmærkat fra en mærkatpolitik eller sletter en følsomhedsmærkat.

## <a name="next-steps"></a>Næste trin

Hvis du vil konfigurere og bruge dine følsomhedsmærkater til bestemte scenarier, skal du bruge følgende artikler:

- [Begræns adgangen til indhold ved hjælp af kryptering i følsomhedsmærkater](encryption-sensitivity-labels.md)

- [Anvend automatisk en følsomhedsmærkat på indhold](apply-sensitivity-label-automatically.md)

- [Brug følsomhedsmærkater med teams, grupper og websteder](sensitivity-labels-teams-groups-sites.md)

- [Aktivér følsomhedsmærkater for Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md)

Hvis du vil overvåge, hvordan dine mærkater bruges, skal du se [Kom i gang med dataklassificering](data-classification-overview.md).
