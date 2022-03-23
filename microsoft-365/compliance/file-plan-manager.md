---
title: Brug filplan til at administrere opbevaringsnavne i hele indholdslivscyklussen
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
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: af398293-c69d-465e-a249-d74561552d30
description: Filplan giver avancerede administrationsfunktioner til opbevaringsnavne.
ms.custom: seo-marvel-may2020
ms.openlocfilehash: 2e028bae676b949c662a86178bac5e8ccdc557bf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587498"
---
# <a name="use-file-plan-to-create-and-manage-retention-labels"></a>Brug filplan til at oprette og administrere opbevaringsnavne

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Selvom du kan oprette og administrere opbevaringsnavne **fra Styring** af oplysninger i Microsoft 365 Overholdelsescenter, har **filplanen fra** Datastyring yderligere administrationsfunktioner:

- Du kan masseopret opbevaringsetiketter ved at importere de relevante oplysninger fra et regneark.

- Du kan eksportere oplysningerne fra eksisterende opbevaringsnavne til analyse og offlinesamarbejde.

- Der vises flere oplysninger om opbevaringsnavnene for at gøre det nemmere at se og på tværs af indstillingerne for alle dine opbevaringsnavne fra én visning.

- Filplanbeskrivelser understøtter yderligere og valgfrie oplysninger for hver etiket.

Filplanen kan bruges til alle opbevaringsnavne, også selvom de ikke markerer indhold som en post.

Du kan finde oplysninger om, hvad opbevaringsnavne er, og hvordan du bruger dem, under [Få mere at vide om opbevaringspolitikker og opbevaringsnavne](retention.md).

## <a name="accessing-file-plan"></a>Adgang til filplan

For at få adgang til filplanen skal du have en af følgende administratorroller:
    
- Opbevaringsstyring

- Kun visningsopbevaringsstyring

I Microsoft 365 Overholdelsescenter skal du **gå til** **SolutionsRecords** >  **managementFile-plan** > :

![Siden Filplan](../media/compliance-file-plan.png). 

Hvis **datastyring** ikke vises i navigationsruden, skal du først rulle ned og vælge **Vis alle**.

## <a name="navigating-your-file-plan"></a>Navigering i din filplan

Hvis du allerede har oprettet opbevaringsnavne **ud fra** Styring af oplysninger i Microsoft 365 Overholdelsescenter, vises disse etiketter automatisk i din filplan. 

Hvis du nu opretter opbevaringsnavne i filplanen, er de også tilgængelige fra Styring  af oplysninger, hvis etiketterne ikke er konfigureret til at markere indhold som en post.

På **siden** Filplan kan du se alle dine etiketter med deres status og indstillinger, valgfrie filplanbeskrivelser, en eksportindstilling for at analysere eller aktivere offlinegennemsyn af dine etiketter og en importindstilling for at oprette opbevaringsnavne. 

### <a name="label-settings-columns"></a>Kolonner med navneindstillinger

Alle kolonner undtagen navnet **Navn** kan vises eller skjules ved at vælge **indstillingen Tilpas** kolonner. Men som standard viser de første kolonner oplysninger om etiketstatus og dens indstillinger: 

- **Status** identificerer, om navnet er medtaget i en etiketpolitik eller automatisk anvendelsespolitik **(Aktiv**) eller ej (**Inaktiv**).

- **Baseret på** identificerer, hvordan eller hvornår en opbevaringsperiode begynder. Gyldige værdier:
    - Hændelse
    - Da den blev oprettet
    - Senest ændret
    - Ved mærkat

- **Er post** identificerer, om elementet er markeret som en post, når navnet anvendes. Gyldige værdier:
    - Nej
    - Ja
    - Ja(lovgivning)

- **Opbevaringsvarigheden** identificerer opbevaringsperioden. Gyldige værdier:
    - Dage
    - Måneder
    - År
    - Uendelig lang tid
    - Ingen

- **Dispositionstype** identificerer, hvad der sker med indholdet i slutningen af en opbevaringsperiode. Gyldige værdier:
    - Ingen handling
    - Slet automatisk
    - Gennemsyn påkrævet

### <a name="file-plan-descriptors-columns"></a>Kolonner med beskrivelse af filplan

Med filplanen kan du medtage flere oplysninger som en del af dine opbevaringsnavne. Disse filplanbeskrivelser giver flere muligheder for at forbedre administrationen og organiseringen af det indhold, du skal navnmærke.

Fra og med **Reference-id** viser de næste par kolonner som standard disse valgfrie filplanbeskrivelser, som du kan angive, når du opretter en opbevaringsetiket eller redigerer en eksisterende etiket. 

For at komme i gang er der nogle standardværdier for følgende filplanbeskrivelser: 
- Funktionen Business/afdeling
- Kategori
- Nøglecentertype
- Klargøring/citat 

Eksempel på beskrivelse af filplan, når du opretter eller redigerer et opbevaringsnavn:

![Filplanbeskrivelser, når du opretter eller redigerer et opbevaringsnavn.](../media/file-plan-descriptors.png)

Når du **vælger Vælg** for hver af disse valgfrie beskrivelsesindstillinger, kan du vælge en af de out of box-værdier eller oprette din egen og derefter vælge den. Eksempel: 

![Opret en beskrivelse af en ny filplan til klargøring/citat.](../media/file-plan-descriptors-create.png)

## <a name="create-retention-labels"></a>Opret opbevaringsnavne

1. På siden **Filplan** skal du **vælge + Opret en** **etiketRetention-etiket** > 

2. Følg instruktionerne for konfigurationsprocessen. Vær forsigtig med det navn, du vælger, da dette ikke kan ændres, når etiketten er gemt.
    
    Du kan finde flere oplysninger om opbevaringsindstillingerne [under Indstillinger opbevaring og sletning af indhold](retention-settings.md#settings-for-retaining-and-deleting-content).
    
    Hvis du vil bruge opbevaringsnavnet til at erklære poster, **skal du vælge** Markér elementer som poster **eller Markér elementer som lovmæssige poster**. Du kan få mere at vide under [Konfiguration af opbevaringsnavne til erklæring af poster](declare-records.md#configuring-retention-labels-to-declare-records).

3. Når du har oprettet navnet, og du får vist mulighederne for at publicere navnet, skal du anvende den automatisk eller blot gemme navnet: Vælg Gem blot etiketten **indtil** videre, og vælg derefter **Udført**.

4. Gentag disse trin for at oprette flere etiketter.

## <a name="edit-retention-labels"></a>Rediger opbevaringsnavne

Hvis du vil redigere et eksisterende opbevaringsnavn, skal  du vælge det på siden Filplan og  derefter vælge indstillingen Rediger etiket for at starte opbevaringsprocessen til redigering, hvor du kan ændre beskrivelsen af navnet og alle berettigede indstillinger.

Nogle indstillinger kan ikke ændres, efter etiketten er oprettet og gemt, hvilket omfatter:
- Opbevaringsnavnet og opbevaringsindstillingerne undtagen opbevaringsperioden. Du kan dog ikke ændre opbevaringsperioden, når en opbevaringsperiode er baseret på, hvornår elementerne blev mærket.
- Muligheden for at markere elementer som en post.

## <a name="delete-retention-labels"></a>Slet opbevaringsnavne

Du kan slette opbevaringsnavne, der i øjeblikket ikke er medtaget i [](apply-retention-labels-automatically.md) eventuelle publicerede politikker eller politikker for automatisk anvendelse af opbevaringsetiketter, der ikke er konfigureret til hændelsesbaseret opbevaring, eller markere elementer som lovmæssige poster.[](create-apply-retention-labels.md)

For opbevaringsetiketter, som du kan slette, hvis de er blevet anvendt på elementer, mislykkes sletningen, og du kan se et link til indholdsstifinder til at identificere de mærkede elementer.

Det kan dog tage op til to dage, før indholdsstifinder viser de elementer, der er mærket. I dette scenarie kan opbevaringsnavnet slettes uden at vise dig linket til indholdsstifinder.

## <a name="export-all-retention-labels-to-analyze-or-enable-offline-reviews"></a>Eksportér alle opbevaringsetiketter for at analysere eller aktivere offlinegennemsyn

Fra din filplan kan du eksportere detaljerne for alle opbevaringsnavne til en .csv-fil for at hjælpe dig med at lette periodiske gennemgange af overholdelse med interessenter inden for datastyring i organisationen.

Hvis du vil eksportere alle opbevaringsnavne: På **siden Filplan skal** du klikke på **Eksportér**:

![Mulighed for at eksportere filplan.](../media/compliance-file-plan-export-labels.png)

En *.csv fil, der indeholder alle eksisterende opbevaringsnavne, åbnes. Eksempel:

![CSV-fil, der viser alle opbevaringsnavne.](../media/file-plan-csv-file.png)

## <a name="import-retention-labels-into-your-file-plan"></a>Importér opbevaringsnavne i din filplan

I filplanen kan du masseimportér nye opbevaringsnavne ved hjælp af en .csv fil med et bestemt format: 

1. På siden **Filplan skal** du klikke på **Importér**: ![Indstilling for import af filplan](../media/compliance-file-plan-import-labels.png)

2. I **ruden Udfyld og importér din filplan** skal du **vælge Download en tom skabelon**:

   ![Mulighed for at downloade en tom filplanskabelon](../media/file-plan-blank-template-option.png)

3. Når skabelonen er hentet, skal du tilføje én række for hver etiket og gemme filen. Se næste [afsnit](#information-about-the-label-properties-for-import) for at få oplysninger, der beskriver egenskaberne og de gyldige værdier for hver egenskab.
    
    Eksempel på en udfyldt skabelon:
    
    ![Skabelon til filplan med udfyldte oplysninger.](../media/file-plan-filled-out-template.png)

4. Vælg **Upload en fil for** at overføre skabelonen udfyldt.
    
   Filplanen uploader filen og validerer posterne.

5. Afhængigt af valideringsresultaterne:
    
    - Hvis valideringen mislykkes: Bemærk rækkenummeret og kolonnenavnet, der skal rettes i importfilen. Ret fejlene i filen, gem den, og gentag derefter trin 4.
    
    - Hvis valideringen lykkes: Du **kan se** , at du har importeret en filplan, og posterne er konverteret til opbevaringsetiketter. Vælg **Udført** for at lukke ruden og automatisk opdatere **siden Filplan** for at få vist de nye etiketter.

Du kan nu publicere dine nye opbevaringsnavne eller anvende dem automatisk. Du kan gøre begge dele fra **fanen Etiketpolitikker** ved at vælge **Publicer navne** eller **Anvend automatisk en etiket automatisk**.

### <a name="information-about-the-label-properties-for-import"></a>Oplysninger om egenskaberne for etiketter til import

Brug følgende oplysninger som hjælp til at udfylde den downloadede skabelon for at importere nye opbevaringsnavne. Nogle værdier har en maksimal længde for import:

- **LabelName**: Maksimal længde på 64 tegn
- **Kommentar** og **noter**: Maksimal længde på 1024 tegn
- Alle andre værdier: Ubegrænset længde
<br/>

|Egenskab|Type|Påkrævet|Gyldige værdier|
|:-----|:-----|:-----|:-----|
|Etiketnavn|String|Ja|Denne egenskab angiver navnet på opbevaringsmærkaten og skal være entydigt i din lejer. Understøttede tegn til import: a-z, A-Z, 0-9, bindestreg (-) og mellemrumstegnet.|
|Kommenter|String|Nej|Brug denne egenskab til at tilføje en beskrivelse af opbevaringsnavnet for administratorer. Denne beskrivelse vises kun for administratorer, der administrerer opbevaringsmærkaten i Overholdelsescenter.|
|Bemærkninger|String|Nej|Brug denne egenskab til at tilføje en beskrivelse af opbevaringsmærkaten for brugere. Denne beskrivelse vises, når brugerne holder markøren over navnet i apps som Outlook, SharePoint og OneDrive. Hvis du lader denne egenskab være tom, vises der en standardbeskrivelse, som forklarer etikettens opbevaringsindstillinger. |
|IsRecordLabel|String|Nej, medmindre **lovgivning** er **SAND**|Denne egenskab angiver, om navnet markerer indholdet som en post. Gyldige værdier er: </br>**SAND**: Navnet markerer elementet som en post, og elementet kan derfor ikke slettes. </br>**FALSK**: Etiketten markerer ikke indholdet som en post. Dette er standardværdien. </br> </br> Gruppeafhængigheder: Når denne egenskab er angivet, skal Opbevaringshandling, Opbevaringsforbevaring og Opbevaringstype også angives.|
|RetentionAction|String|Nej, medmindre **Opbevaringsduration**, **Opbevaringstype** eller **KorrekturlæserMail** er angivet|Denne egenskab angiver, hvilken handling der skal sker, efter den værdi, der er angivet af egenskaben Opbevaringsvarighed (hvis angivet) udløber. Gyldige værdier er: </br>**Slet**: Elementer, der er ældre end den værdi, der er angivet af egenskaben Opbevaringsvarighed slettes.</br>**Behold**: Bevar elementer i den varighed, der er angivet af egenskaben Opbevaringsvarighed, og gør derefter intet, når varigheden udløber. </br>**BeholdOgSlette**: Bevar elementer i den varighed, der er angivet af egenskaben Opbevaringsduration, og slet dem derefter, når varigheden udløber. </br> </br> Gruppeafhængigheder: Når denne egenskab er angivet, skal Opbevarings- og Opbevaringstype også angives. |
|Opbevaringsduration|String|Nej, medmindre **RetentionAction eller** **RetentionType** er angivet|Denne egenskab angiver antallet af dage, indholdet skal bevares. Gyldige værdier er: </br>**Ubegrænset**: Varer bevares på ubestemt tid. </br>**_n_*: Et positivt heltal i dage; f.eks **. 365**. Det maksimale antal understøttede er 24.855, hvilket er 68 år. Hvis du har brug for længere end denne maksimumgrænse, skal du bruge Ubegrænset i stedet.</br> </br> Gruppeafhængigheder: Når denne egenskab er angivet, skal Opbevaringshandling og Opbevaringstype også angives.
|RetentionType|String|Nej, medmindre **Opbevaringshandling** eller **Opbevaringsduration** er angivet|Denne egenskab angiver, om opbevaringsvarigheden (hvis angivet) beregnes ud fra oprettelsesdatoen for indholdet, begivenhedsdatoen, datoen for mærkaten eller datoen for seneste ændring. Gyldige værdier er: </br>**CreationAgeInDays**</br>**EventAgeInDays**</br>**TaggedAgeInDays**</br>**ModificationAgeInDays** </br> </br> Gruppeafhængigheder: Når denne egenskab er angivet, skal Opbevaringshandling og Opbevaringshandling også angives.|
|ReviewerEmail|SmtpAddress|Nej|Når denne egenskab er angivet, udløses en dispositionsgennemgang, når opbevaringsvarigheden udløber. Denne egenskab angiver mailadressen på en korrekturlæser i din lejer for **opbevaringshandlingen BeholdOgSlette** . </br> </br> Du kan medtage mailadressen på individuelle brugere, distributionsgrupper eller sikkerhedsgrupper i din lejer. Angiv flere mailadresser ved at adskille dem med semikolon. </br> </br> Gruppeafhængigheder: Når denne egenskab er angivet, skal **Opbevaringshandling** (skal **være KeepAndDelete**), **Opbevaringsduration** og **Opbevaringstype** også angives.|
|ReferenceId|String|Nej|Denne egenskab angiver den værdi, der vises i planbeskrivelsen for  reference-id-filen, som du kan bruge som en entydig værdi for organisationen.| 
|Afdelingsnavn|String|Nej|Denne egenskab angiver den værdi, der vises i funktions **-/** afdelingsfilplanbeskrivelsen.|
|Kategori|String|Nej|Denne egenskab angiver den værdi, der vises i **beskrivelsesbeskrivelsen** for kategorifilplanen.|
|Underkategori|String|Nej|Denne egenskab angiver den værdi, der vises i **beskrivelsesbeskrivelsen for** underkategorifilen.|
|AuthorityType|String|Nej|Denne egenskab angiver den værdi, der vises i beskrivelsesbeskrivelsen **for** filtypen Authority-filtype.|
|Citatnavn|String|Nej|Denne egenskab angiver navnet på citatet, der vises i beskrivelsesbeskrivelsen for **klargørings-/** citatfilplanen. For eksempel "Sarbanes-Oxley Act of 2002". |
|CitationUrl|String|Nej|Denne egenskab angiver URL-adressen, der vises i **beskrivelsesbeskrivelsen for klargørings-/** citatfilplanen.|
|CitationJurisdiction|String|Nej|Denne egenskab angiver jurisdiktionen eller det agentur, der vises i beskrivelsesbeskrivelsen for filen **Provision/citation** . For eksempel "US Securities and Exchange Commission (SEC)".|
|Lovgivning|String|Nej|Denne egenskab angiver, om etiketten markerer indholdet som en lovgivningsmæssig post, hvilket er [mere restriktivt](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked) end en post. Hvis du vil bruge denne etiketkonfiguration, skal din lejer være konfigureret til at vise indstillingen til at markere indhold som en lovgivningsmæssig [post,](declare-records.md#how-to-display-the-option-to-mark-content-as-a-regulatory-record) ellers mislykkes importvalideringen. Gyldige værdier er: </br>**SAND**: Etiketten markerer elementet som en lovgivningspost. Du skal også angive **egenskaben IsRecordLabel** til SAND.</br>**FALSK**: Etiketten markerer ikke indholdet som en lovgivningspost. Dette er standardværdien.|
|EventType|String|Nej, medmindre **RetentionType** er **EventAgeInDays**|Denne egenskab angiver en hændelsestype, der bruges [til hændelsesbaseret opbevaring](event-driven-retention.md). Angiv en eksisterende hændelsestype, der vises i **Records** **managementEventsManage-hændelsestyper** >  > . Alternativt kan du bruge [Get-ComplianceRetentionEventType-cmdlet'en](/powershell/module/exchange/get-complianceretentioneventtype) til at få vist de tilgængelige hændelsestyper. Selvom der er nogle indbyggede begivenhedstyper, f.eks. **Medarbejderaktivitet** og **Produktlevetid**, kan du også oprette dine egne begivenhedstyper. </br> </br> Hvis du angiver din egen hændelsestype, skal den findes før importen, fordi navnet valideres som en del af importprocessen.|
|||

## <a name="next-steps"></a>Næste trin

Nu har du oprettet opbevaringsmærkater, de er klar til at blive føjet til elementer ved at publicere etiketterne eller automatisk anvende dem:
- [Udgive opbevaringsmærkater og anvende dem i apps](create-apply-retention-labels.md)
- [Anvende en opbevaringsetiket på indhold automatisk](apply-retention-labels-automatically.md)