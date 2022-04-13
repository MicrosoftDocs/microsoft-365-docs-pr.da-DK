---
title: Brug filplanen til at administrere opbevaringsmærkater i hele indholdslivscyklussen
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
description: Filplanen indeholder avancerede administrationsfunktioner til opbevaringsmærkater.
ms.custom: seo-marvel-may2020
ms.openlocfilehash: 40c395d609a9a02637b937cafae988578dc6e14f
ms.sourcegitcommit: 5eff41a350a01e18d9cdd572c9d8ff99d6c9563a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/13/2022
ms.locfileid: "64836166"
---
# <a name="use-file-plan-to-create-and-manage-retention-labels"></a>Brug filplanen til at oprette og administrere opbevaringsmærkater

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Selvom du kan oprette og administrere opbevaringsmærkater fra **Styring af oplysninger** i Microsoft 365 Overholdelsescenter, har filplanen fra **Datastyring** yderligere administrationsfunktioner:

- Du kan masseoprete opbevaringsmærkater ved at importere de relevante oplysninger fra et regneark.

- Du kan eksportere oplysningerne fra eksisterende opbevaringsmærkater til analyse og offlinesamarbejde.

- Der vises flere oplysninger om opbevaringsmærkater for at gøre det nemmere at se på og på tværs af indstillingerne for alle dine opbevaringsmærkater fra én visning.

- Filplanbeskrivelser understøtter yderligere og valgfrie oplysninger for hver mærkat.

Filplanen kan bruges til alle opbevaringsmærkater, selvom de ikke markerer indhold som en post.

Du kan finde oplysninger om, hvad opbevaringsmærkater er, og hvordan du bruger dem, under [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md).

## <a name="accessing-file-plan"></a>Adgang til filplan

Hvis du vil have adgang til filplanen, skal du have en af følgende administratorroller:
    
- Opbevaringsstyring

- Kun visningsstyring

I Microsoft 365 Overholdelsescenter skal du gå til **LøsningPostadministrationFilplan** >  > :

![Filplanside](../media/compliance-file-plan.png). 

Hvis **Datastyring** ikke vises i navigationsruden, skal du først rulle ned og vælge **Vis alle**.

## <a name="navigating-your-file-plan"></a>Navigering i filplanen

Hvis du allerede har oprettet opbevaringsmærkater fra **Styring af oplysninger** i Microsoft 365 Overholdelsescenter, vises disse mærkater automatisk i filplanen. 

Hvis du på samme måde nu opretter opbevaringsmærkater i filplanen, er de også tilgængelige fra **Styring af oplysninger** , hvis mærkaterne ikke er konfigureret til at markere indhold som en post.

På siden **Filplan** kan du se alle dine mærkater med deres status og indstillinger, valgfri filplanbeskrivelser, en eksportmulighed for at analysere eller aktivere offlinegennemsyn af dine mærkater og en importmulighed for at oprette opbevaringsmærkater. 

### <a name="label-settings-columns"></a>Kolonner med navneindstillinger

Alle kolonner undtagen navnet **kan** vises eller skjules ved at vælge indstillingen **Tilpas kolonner** . Men som standard viser de første par kolonner oplysninger om mærkatstatus og dens indstillinger: 

- **Status** identificerer, om mærkaten er inkluderet i en mærkatpolitik eller automatisk anvendelse af politik (**Aktiv**) eller ej (**Inactive**).

- **Baseret på** identificerer, hvordan eller hvornår opbevaringsperioden begynder. Gyldige værdier:
    - Hændelse
    - Når oprettet
    - Senest ændret
    - Når den er forsynet med mærkat

- **Angiver,** om elementet er markeret som en post, når etiketten anvendes. Gyldige værdier:
    - Nej
    - Ja
    - Ja (lovmæssigt)

- **Låses op som standard** – udrulles i øjeblikket – identificerer, om det element, der er markeret som en post, låses op, når mærkaten anvendes. Gyldige værdier:
    - Nej
    - Ja

- **Opbevaringsvarighed** identificerer opbevaringsperioden. Gyldige værdier:
    - Dage
    - Måneder
    - År
    - Evigt
    - Ingen

- **Dispositionstype** identificerer, hvad der sker med indholdet i slutningen af opbevaringsperioden. Gyldige værdier:
    - Ingen handling
    - Slet automatisk
    - Korrektur er påkrævet

### <a name="file-plan-descriptors-columns"></a>Kolonner med beskrivelse af filplan

Filplanen giver dig mulighed for at inkludere flere oplysninger som en del af dine opbevaringsmærkater. Disse beskrivelser af filplan giver flere muligheder for at forbedre administrationen og organiseringen af det indhold, du skal navngive.

Fra og med **Reference-id** viser de næste par kolonner som standard disse valgfri filplanbeskrivelser, som du kan angive, når du opretter en opbevaringsmærkat eller redigerer en eksisterende etiket. 

For at komme i gang er der nogle indbyggede værdier for følgende filplanbeskrivelser: 
- Forretningsfunktion/afdeling
- Kategori
- Autoritetstype
- Klargøring/citat 

Eksempel på beskrivelse af filplan, når du opretter eller redigerer en opbevaringsmærkat:

![Filplanbeskrivelser, når du opretter eller redigerer en opbevaringsmærkat.](../media/file-plan-descriptors.png)

Når du vælger **Vælg** for hver af disse valgfri beskrivelse, kan du vælge en af de indbyggede værdier eller oprette din egen og derefter vælge den. Eksempel: 

![Opret en ny filplanbeskrivelse til klargøring/citat.](../media/file-plan-descriptors-create.png)

## <a name="create-retention-labels"></a>Opret opbevaringsmærkater

1. På siden **Filplan** skal du vælge **+ Opret en mærkatRetention-etiket** > 

2. Følg prompterne for konfigurationsprocessen. Vær forsigtig med, hvilket navn du vælger, da dette ikke kan ændres, når etiketten er gemt.
    
    Du kan få flere oplysninger om opbevaringsindstillingerne under [Indstillinger til at bevare og slette indhold](retention-settings.md#settings-for-retaining-and-deleting-content).
    
    Hvis du vil bruge opbevaringsmærkaten til at deklarere poster, skal du vælge **Markér elementer som poster** eller **Markér elementer som lovmæssige poster**. Du kan få flere oplysninger under [Konfiguration af opbevaringsmærkater til deklarering af poster](declare-records.md#configuring-retention-labels-to-declare-records).

3. Når du har oprettet etiketten, og du kan se indstillingerne for publicering af etiketten, skal du anvende etiketten automatisk eller blot gemme etiketten: Vælg **Gem blot etiketten nu**, og vælg derefter **Udført**.

4. Gentag disse trin for at oprette flere mærkater.

## <a name="edit-retention-labels"></a>Rediger opbevaringsmærkater

Hvis du vil redigere en eksisterende opbevaringsmærkat, skal du vælge den på siden **Filplan** og derefter vælge indstillingen **Rediger mærkat** for at starte processen til redigering af opbevaring, hvor du kan ændre beskrivelsen og eventuelle berettigede indstillinger.

Nogle indstillinger kan ikke ændres, når etiketten er oprettet og gemt, herunder:
- Navnet på opbevaringsmærkaten og opbevaringsindstillingerne undtagen opbevaringsperioden. Du kan dog ikke ændre opbevaringsperioden, når opbevaringsperioden er baseret på, hvornår elementer blev mærket.
- Indstillingen til at markere elementer som en post.

## <a name="delete-retention-labels"></a>Slet opbevaringsmærkater

Du kan slette opbevaringsmærkater, der i øjeblikket ikke er inkluderet i nogen [publicerede](create-apply-retention-labels.md) eller [automatisk gældende](apply-retention-labels-automatically.md) politikker for opbevaringsmærkater, som ikke er konfigureret til hændelsesbaseret opbevaring, eller markere elementer som lovmæssige poster.

For opbevaringsmærkater, som du kan slette, hvis de er blevet anvendt på elementer, mislykkes sletningen, og du får vist et link til indholdsoversigten for at identificere de navngivne elementer.

Det kan dog tage op til to dage, før indholdsoversigten viser de elementer, der er forsynet med mærkater. I dette scenarie kan opbevaringsmærkaten blive slettet uden at vise dig linket til Indholdsoversigt.

## <a name="export-all-retention-labels-to-analyze-or-enable-offline-reviews"></a>Eksportér alle opbevaringsmærkater for at analysere eller aktivere offlinegennemgange

Fra din filplan kan du eksportere oplysningerne om alle opbevaringsmærkater til en .csv fil for at hjælpe dig med at facilitere periodiske gennemgange af overholdelse af angivne standarder med interessenter i forbindelse med datastyring i din organisation.

Sådan eksporterer du alle opbevaringsmærkater: Klik på **Eksportér** på siden **Filplan**:

![Mulighed for at eksportere filplanen.](../media/compliance-file-plan-export-labels.png)

Der åbnes en *.csv fil, der indeholder alle eksisterende opbevaringsmærkater. Eksempel:

![CSV-fil, der viser alle opbevaringsmærkater.](../media/file-plan-csv-file.png)

## <a name="import-retention-labels-into-your-file-plan"></a>Importér opbevaringsmærkater til filplanen

I filplanen kan du masseimportér nye opbevaringsmærkater ved hjælp af en .csv fil med et bestemt format: 

1. Klik på **Importér** på siden **Filplan**: ![Mulighed for at importere filplan](../media/compliance-file-plan-import-labels.png)

2. I ruden **Udfyld og importér filplanen** skal du vælge **Download en tom skabelon**:

   ![Mulighed for at downloade en tom filplanskabelon](../media/file-plan-blank-template-option.png)

3. Når skabelonen er downloadet, skal du tilføje én række for hver etiket og gemme filen. I [næste afsnit kan du](#information-about-the-label-properties-for-import) finde oplysninger, der beskriver egenskaberne og de gyldige værdier for hver egenskab.
    
    Eksempel på en udfyldt skabelon:
    
    ![Filplanskabelon med udfyldte oplysninger.](../media/file-plan-filled-out-template.png)

4. Vælg **Upload en fil** for at uploade den udfyldte skabelon.
    
   Filplanen overfører filen og validerer posterne.

5. Afhængigt af valideringsresultaterne:
    
    - Hvis valideringen mislykkes: Bemærk det rækkenummer og kolonnenavn, der skal rettes i importfilen. Ret fejlene i filen, gem den, og gentag derefter trin 4.
    
    - Hvis valideringen gennemføres: Du kan se **, at du har importeret en filplan** , og posterne konverteres til opbevaringsmærkater. Vælg **Udført** for at lukke ruden og automatisk opdatere siden **Filplan** for at få vist dine nye navne.

Du kan nu publicere dine nye opbevaringsmærkater eller anvende dem automatisk. Du kan gøre begge dele under fanen **Label policies (Etiketpolitikker** ) ved at vælge **Publicer navne** eller **Anvende en etiket automatisk**.

### <a name="information-about-the-label-properties-for-import"></a>Oplysninger om mærkategenskaberne for import

Brug følgende oplysninger som en hjælp til at udfylde den downloadede skabelon for at importere nye opbevaringsmærkater. Nogle værdier har en maksimal længde for import:

- **LabelName**: Maksimumlængde på 64 tegn
- **Kommentar** og **noter**: Maksimumlængde på 1024 tegn
- Alle andre værdier: Ubegrænset længde
<br/>

|Ejendom|Type|Kræves|Gyldige værdier|
|:-----|:-----|:-----|:-----|
|Navn|String|Ja|Denne egenskab angiver navnet på opbevaringsmærkaten og skal være entydig i din lejer. Understøttede tegn til import: a-z, A-Z, 0-9, bindestreg (-) og mellemrumstegnet.|
|Kommenter|String|Nej|Brug denne egenskab til at tilføje en beskrivelse af opbevaringsmærkaten for administratorer. Denne beskrivelse vises kun for administratorer, der administrerer opbevaringsmærkaten i Overholdelsescenter.|
|Bemærkninger|String|Nej|Brug denne egenskab til at tilføje en beskrivelse af opbevaringsmærkaten for brugerne. Denne beskrivelse vises, når brugerne holder markøren over mærkaten i apps, f.eks. Outlook, SharePoint og OneDrive. Hvis du lader denne egenskab være tom, vises der en standardbeskrivelse, som forklarer indstillingerne for opbevaring af mærkaten. |
|IsRecordLabel|String|Nej, medmindre **lovgivningen** er **SAND**|Denne egenskab angiver, om etiketten markerer indholdet som en post. Gyldige værdier er: </br>**TRUE**: Etiketten markerer elementet som en post, og elementet kan derfor ikke slettes. </br>**FALSE**: Etiketten markerer ikke indholdet som en post. Dette er standardværdien. </br> </br> Gruppeafhængigheder: Når denne egenskab er angivet, skal RetentionAction, RetentionDuration og RetentionType også angives.|
|Opbevaringshandling|String|Nej, medmindre **RetentionDuration**, **RetentionType** eller **ReviewerEmail** er angivet|Denne egenskab angiver, hvilken handling der skal udføres, når den værdi, der er angivet af egenskaben RetentionDuration (hvis angivet), udløber. Gyldige værdier er: </br>**Slet**: Elementer, der er ældre end den værdi, der er angivet af egenskaben RetentionDuration, slettes.</br>**Bevar**: Bevar elementer i den varighed, der er angivet af egenskaben RetentionDuration, og gør derefter ingenting, når varighedsperioden udløber. </br>**KeepAndDelete**: Bevar elementer i den varighed, der er angivet i egenskaben RetentionDuration, og slet dem derefter, når varighedsperioden udløber. </br> </br> Gruppeafhængigheder: Når denne egenskab er angivet, skal RetentionDuration og RetentionType også angives. |
|Opbevaringsvarighed|String|Nej, medmindre **RetentionAction** eller **RetentionType** er angivet|Denne egenskab angiver det antal dage, indholdet skal bevares. Gyldige værdier er: </br>**Ubegrænset**: Elementer bevares på ubestemt tid. </br>**_n_*: Et positivt heltal i dage. for eksempel **365**. Det maksimale antal, der understøttes, er 24.855, hvilket er 68 år. Hvis du har brug for længere tid end denne maksimumværdi, skal du i stedet bruge Ubegrænset.</br> </br> Gruppeafhængigheder: Når denne egenskab er angivet, skal RetentionAction og RetentionType også angives.
|RetentionType|String|Nej, medmindre **RetentionAction** eller **RetentionDuration** er angivet|Denne egenskab angiver, om opbevaringsvarigheden (hvis det er angivet) beregnes ud fra datoen for oprettelse af indhold, hændelsesdatoen, hvornår der er angivet en dato eller datoen for seneste ændring. Gyldige værdier er: </br>**CreationAgeInDays**</br>**EventAgeInDays**</br>**TaggedAgeInDays**</br>**ModificationAgeInDays** </br> </br> Gruppeafhængigheder: Når denne egenskab er angivet, skal RetentionAction og RetentionDuraction også angives.|
|KorrekturlæserMail|SmtpAddress|Nej|Når denne egenskab er angivet, udløses der en dispositionsgennemgang, når opbevaringsvarigheden udløber. Denne egenskab angiver mailadressen på en korrekturlæser i din lejer for opbevaringshandlingen **KeepAndDelete** . </br> </br> Du kan inkludere mailadressen på individuelle brugere, distributionsgrupper eller sikkerhedsgrupper i din lejer. Angiv flere mailadresser ved at adskille dem med semikolon. </br> </br> Gruppeafhængigheder: Når denne egenskab er angivet, skal **RetentionAction** (skal være **KeepAndDelete**), **RetentionDuration** og **RetentionType** også være angivet.|
|ReferenceId|String|Nej|Denne egenskab angiver den værdi, der vises i filplanbeskrivelsen **Reference-id** , som du kan bruge som en entydig værdi for din organisation.| 
|Navn på afdeling|String|Nej|Denne egenskab angiver den værdi, der vises i beskrivelse af filplan for **funktion/afdeling** .|
|Kategori|String|Nej|Denne egenskab angiver den værdi, der vises i beskrivelse af filplanen **Kategori** .|
|Underkategori|String|Nej|Denne egenskab angiver den værdi, der vises i filplanbeskrivelsen **Underkategori** .|
|AuthorityType|String|Nej|Denne egenskab angiver den værdi, der vises i filtypens beskrivelse af **autoritetstype** .|
|Citatnavn|String|Nej|Denne egenskab angiver navnet på det citat, der vises i beskrivelsesbeskrivelsen **Til klargørings-/citatfilfil** . For eksempel "Sarbanes-Oxley Act of 2002". |
|Citaturl|String|Nej|Denne egenskab angiver den URL-adresse, der vises i beskrivelsesbeskrivelsen **for klargørings-/citatfilfilen** .|
|CitationJurisdiction|String|Nej|Denne egenskab angiver den jurisdiktion eller det agentur, der vises i beskrivelsesbeskrivelsen **Tilklarings-/citatfilfil** . For eksempel "Amerikanske værdipapirer og Exchange Commission (SEC)".|
|Lovgivningsmæssige|String|Nej|Denne egenskab angiver, om mærkaten markerer indholdet som en lovmæssig post, hvilket er [mere restriktivt](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked) end en post. Hvis du vil bruge denne mærkatkonfiguration, skal din lejer være konfigureret til at [vise indstillingen for at markere indhold som en lovmæssig post](declare-records.md#how-to-display-the-option-to-mark-content-as-a-regulatory-record), ellers mislykkes importvalideringen. Gyldige værdier er: </br>**TRUE**: Etiketten markerer elementet som en lovmæssig post. Du skal også angive egenskaben **IsRecordLabel** til TRUE.</br>**FALSE**: Mærkaten markerer ikke indholdet som en lovmæssig post. Dette er standardværdien.|
|EventType|String|Nej, medmindre **RetentionType** er **EventAgeInDays**|Denne egenskab angiver en hændelsestype, der bruges til [hændelsesbaseret opbevaring](event-driven-retention.md). Angiv en eksisterende hændelsestype, der vises i **Hændelsestyper** for **dataadministrationHændelser** >  > . Du kan også bruge [cmdlet'en Get-ComplianceRetentionEventType](/powershell/module/exchange/get-complianceretentioneventtype) til at få vist de tilgængelige hændelsestyper. Selvom der er nogle indbyggede hændelsestyper, f.eks **. medarbejderaktivitet** og **produktlevetid**, kan du også oprette dine egne hændelsestyper. </br> </br> Hvis du angiver din egen hændelsestype, skal den findes før importen, fordi navnet valideres som en del af importprocessen.|

Navneindstillinger understøttes ikke i øjeblikket for import:

- Gennemgang af fordeling i flere faser: Selvom du kan konfigurere indstillingerne for en enkelt fase for gennemgang af disposition, når du importerer opbevaringsmærkater med en skabelon, kan du ikke angive yderligere korrekturfaser. Konfigurer i stedet disse i Overholdelsescenter, når importen er fuldført.

- Lås denne post op som standard (udrulles i prøveversion): Denne indstilling er ikke tilgængelig i den skabelon, der skal importeres, og du kan ikke vælge denne indstilling i overholdelsescenter, når importen er fuldført.


## <a name="next-steps"></a>Næste trin

Nu, hvor du har oprettet opbevaringsmærkater, er de klar til at blive føjet til elementer ved at publicere mærkaterne eller automatisk anvende dem:
- [Publicer opbevaringsmærkater, og anvend dem i apps](create-apply-retention-labels.md)
- [Anvend automatisk en opbevaringsmærkat på indhold](apply-retention-labels-automatically.md)