---
title: Brug opbevaringsnavne til at administrere livscyklussen for dokumenter, der er gemt i SharePoint
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom:
- admindeeplinkCOMPLIANCE
- admindeeplinkSPO
search.appverid:
- MOE150
- MET150
description: Sådan kan du bruge opbevaringsmærkater til at administrere livscyklussen for dokumenter i SharePoint ved hjælp af metadata til at klassificere indholdet, anvende etiketterne automatisk og bruge hændelsesbaseret opbevaring til at starte en opbevaringsperiode.
ms.openlocfilehash: 35c43a96e07fe52d9e5e0cc0a72195353b6f5da6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587329"
---
# <a name="use-retention-labels-to-manage-the-lifecycle-of-documents-stored-in-sharepoint"></a>Brug opbevaringsnavne til at administrere livscyklussen for dokumenter, der er gemt i SharePoint

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

I denne artikel beskrives det, hvordan du kan administrere livscyklussen for dokumenter, der er gemt i SharePoint, ved hjælp af automatisk anvendte opbevaringsmærkater og hændelsesbaseret opbevaring.

Funktionen til automatisk anvendelse anvender SharePoint til dokumentklassificering. Eksemplet i denne artikel er til produktrelaterede dokumenter, men de samme begreber kan bruges i andre scenarier. I olie- og brændstofbranchen kan du f.eks. bruge den til at administrere livscyklussen for dokumenter om fysiske aktiver som f.eks. olieplatforme, logfiler eller produktionslicenser. Inden for den finansielle sektor kan du administrere dokumenter vedrørende bankkonto, realkredit eller forsikring. I den offentlige sektor kan du administrere byggetilladelser eller skatteformularer.

I denne artikel ser vi nærmere på informationsarkitekturen og definitionen af opbevaringsnavnene. Derefter klassificerer vi dokumenter ved automatisk at anvende etiketterne. Og endelig genererer vi de hændelser, der starter en opbevaringsperiode.

## <a name="information-architecture"></a>Informationsarkitektur

Vores scenarie er en produktionsvirksomhed, der SharePoint til at gemme alle dokumenter om de produkter, som virksomheden udvikler. Disse dokumenter omfatter produktspecifikationer, aftaler med leverandører og brugermanualer. Når disse dokumenter er gemt i SharePoint i Enterprise Content Management-politikker, defineres dokumentmetadata, som bruges til at klassificere dem. Hvert dokument har følgende metadataegenskaber:

- **Dokumenttype** (f.eks. produktspecifikation, aftale eller brugermanual)

- **Produktnavn**

- **Status** (kladde eller endelig)

Disse metadata danner en grundlæggende indholdstype kaldet *Produktionsdokument* for alle dokumenterne.

![Tabel over metadata for produktdokumentation.](../media/SPRetention1.png)

> [!NOTE]
> **Egenskaberne Dokumenttype** **og Status** bruges af opbevaringspolitikker senere i dette scenarie til at klassificere og anvende opbevaringsetiketter automatisk.

Vi kan have flere indholdstyper, der repræsenterer forskellige typer dokumenter, men lad os fokusere på produktdokumentationen.

I dette scenarie bruger vi tjenesten Administrerede metadata og ordtypen Store til at oprette et ordsæt for *Dokumenttype* og et andet for *Produktnavn*. For hvert ordsæt opretter vi et ord for hver værdi. Det ville se sådan ud i ord Store for din SharePoint organisation:

![Eksempel på et ordsæt til produktdokumentation i Store.](../media/SPRetention2.png)

*Indholdstype* kan oprettes og publiceres ved hjælp af [Hub til indholdstype](https://support.office.com/article/manage-content-type-publishing-06f39ac0-5576-4b68-abbc-82b68334889b). Du kan også oprette og publicere en indholdstype ved hjælp af værktøjer til klargøring af websteder, f.eks [. PnP-klargøringsrammen](/sharepoint/dev/solution-guidance/pnp-provisioning-framework) eller [JSON-skemaet for webstedsdesign](/sharepoint/dev/declarative-customization/site-design-json-schema#define-a-new-content-type).

Hvert produkt har en dedikeret SharePoint, der indeholder ét dokumentbibliotek, der har de rigtige indholdstyper aktiveret. Alle dokumenter gemmes i dette dokumentbibliotek.

[![Dokumentbibliotek til produktdokumentation.](../media/SPRetention3.png) ](../media/SPRetention3.png#lightbox)

> [!NOTE]
> I stedet for at have et SharePoint-websted pr. produkt kunne produktionsfirmaet i dette scenarie bruge et Microsoft Team pr. produkt til at understøtte samarbejde mellem medlemmer af teamet, f.eks. via fast chat, og bruge fanen Filer i Teams til dokumentstyring. I denne artikel fokuserer vi kun på dokumenter, så vi bruger kun et websted.

Her er en visning af dokumentbiblioteket for produktet til den roterende widget:

[![Roterende widget-dokumentbibliotek.](../media/SPRetention4.png) ](../media/SPRetention4.png#lightbox)

Nu hvor vi har den grundlæggende informationsarkitektur på plads til dokumentstyring, så lad os se på opbevarings- og afhændelsesstrategi for de dokumenter, der bruger metadataene, og hvordan vi klassificerer disse dokumenter.

## <a name="retention-and-disposition"></a>Opbevaring og disposition

Produktionsselskabets politikker for overholdelse af regler og standarder og datastyring bestemmer, hvordan data bevares og afhændes. Produktrelaterede dokumenter skal opbevares, så længe produktet er fremstillet og i en bestemt ekstra periode. Den ekstra periode er forskellig for produktspecifikationer, aftaler og brugermanualer. Følgende tabel angiver kravene til opbevaring og fordeling:

|   Dokumenttype            |   Opbevaring                            |   Disposition                                |
| -------------------------- | -------------------------------------- | -------------------------------------------- |
| Produktspecifikationer      | 5 år efter produktionsstop  | Slet                                       |
| Produktaftaler          | 10 år efter produktionsstop | Gennemse                                       |
| Brugermanualer                | 5 år efter produktionsstop  | Slet                                       |
| Alle andre typer dokumenter | Behold ikke aktivt  | Slet, når dokumentet er ældre end 3 år <br /><br /> Et dokument betragtes som ældre end 3 år, hvis det ikke er blevet ændret inden for de seneste 3 år. |
|||

Vi bruger Microsoft 365 Overholdelsescenter til at oprette følgende [opbevaringsnavne](retention.md#retention-labels):

  - Produktspecifikation

  - Produktaftale

  - Brugermanual

I denne artikel viser vi kun, hvordan du opretter og automatisk anvender opbevaringsmærkaten for produktspecifikationen. For at implementere det komplette scenarie skal du også oprette og automatisk anvende opbevaringsmærkater for de to andre dokumenttyper.

### <a name="settings-for-the-product-specification-retention-label"></a>Indstillinger for opbevaringsmærkaten for produktspecifikationen

Her er filplanen [for opbevaringsmærkatet](file-plan-manager.md) for produktspecifikationen:

- **Navn:** Produktspecifikation

- **Beskrivelse af brugere:** Behold i 5 år efter produktionsstop.

- **Beskrivelse af administratorer:** Bevar i 5 år efter produktionsstop, automatisk sletning, begivenhedsbaseret opbevaring, hændelsestype er *Produktbevarelse*.

- **Opbevaringshandling:** Behold og slet.

- **Opbevaringsvarighed:** 5 år (1.825 dage).

- **Postetiket**: Konfigurer opbevaringsetiketten til at markere elementer som en [post, hvilket](records-management.md#records) betyder, at de mærkede dokumenter ikke kan ændres eller slettes af brugerne.

- **Beskrivelse af filplan:** For at forenkle scenariet findes der ingen valgfri filbeskrivelser.

Følgende skærmbillede viser indstillingerne, når du opretter opbevaringsmærkatet for Produktspecifikation i Microsoft 365 Overholdelsescenter. Du kan oprette *begivenhedstypen Produktarrangement* , når du opretter opbevaringsmærkaten. Se fremgangsmåden i det følgende afsnit.

![Opbevaringsindstillinger for produktspecifikationsmærkaten.](../media/SPRetention5.png)

> [!NOTE]
> Du kan undgå at vente 5 år på dokumentsletning ved at angive opbevaringsvarigheden til ***1*** dag, hvis du genskaber dette scenarie i et testmiljø.

### <a name="create-an-event-type-when-you-create-a-retention-label"></a>Oprette en begivenhedstype, når du opretter en opbevaringsetiket

1. På siden **Definer opbevaringsindstillinger** i guiden Opret opbevaringsnavn skal du efter **Start opbevaringsperioden** baseret på **vælge Opret ny hændelsestype**:

    ![Opret en ny hændelsestype for dialogboksen Etiket for produktspecifikation.](../media/SPRetention6.png)

3. På siden **Navngiv din begivenhedstype** skal du angive **Produktoplysninger** og en valgfri beskrivelse. Vælg derefter **Næste**, **Send** og **Udført**.

4. Tilbage på siden **Definer opbevaringsindstillinger** skal du for **Start** opbevaringsperioden baseret på bruge rullelisten til at vælge den produktbevarelseshændelsestype, du har oprettet.

    Sådan ser indstillingerne ud for opbevaringsmærkatet for Produktspecifikation:

   ![Indstillinger til den nye produktspecifikationsmærkat.](../media/SPRetention7.png)

6. Vælg **Opret etiket**, og når du på næste side ser mulighederne **for** at publicere navnet, anvende etiketten automatisk eller blot gemme navnet: Vælg Gem blot etiketten indtil videre, og vælg derefter **Udført**.

    > [!TIP]
    > Hvis du vil have en mere detaljeret vejledning, [skal du se Opret en etiket, hvis opbevaringsperiode er baseret på en begivenhed](event-driven-retention.md#step-1-create-a-label-whose-retention-period-is-based-on-an-event).

Lad os nu se på, hvordan vi automatisk anvender opbevaringsmærkaten på indhold med produktspecifikationer.

## <a name="auto-apply-retention-labels-to-documents"></a>Anvend automatisk opbevaringsmærkater på dokumenter

Vi vil bruge KQL (Keyword Query Language) til automatisk at anvende de [opbevaringsetiketter](apply-retention-labels-automatically.md) , vi har oprettet. KQL er det sprog, der bruges til at opbygge søgeforespørgsler. I KQL kan du søge ved hjælp af nøgleord eller administrerede egenskaber. Du kan finde flere oplysninger i Reference til syntaks [for Sprog til nøgleordsforespørgsel (KQL](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)).

Grundlæggende vil vi bede Microsoft 365 "anvende opbevaringsmærkaten for produktspecifikationen på alle dokumenter, der har status som endelig  og en  dokumenttype for  **produktspecifikationen**". Husk, **at Status** og **Dokumenttype er** de webstedskolonner, vi har defineret for indholdstypen Produktdokumentation i [sektionen Informationsarkitektur](#information-architecture) . For at gøre dette skal vi konfigurere søgeskemaet.

Når SharePoint indekserer indhold, genererer det automatisk gennemsøgte egenskaber for hver webstedskolonne. I dette scenarie er vi interesseret i **egenskaberne Dokumenttype** **og Status** . Vi har brug for dokumenter i det bibliotek, der er den rigtige indholdstype, og har webstedskolonnerne udfyldt til søgning for at oprette de gennemsøgte egenskaber.

Åbn <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">søgekonfigurationen SharePoint</a> Administration, og vælg Administrer søgeskema for at få  vist og konfigurere de gennemsøgte egenskaber.

![Gennemsøgte egenskaber i søgeskemaet.](../media/SPRetention8.png)

Hvis vi skriver ***status** _ i feltet _ *Crawled Properties**, og vælger den grønne pil, får vi vist et resultat som dette:

![Den ows_Status gennemsøgte egenskab.](../media/SPRetention9.png)

Egenskaben **owsStatus\_\_** (bemærk dobbelt understregningstegn) er den, der interesserer os. Det er en tilknytning til **egenskaben Status** for indholdstypen Produktionsdokument.

Hvis vi nu skriver ***owsdoc\_ og*** vælger den grønne pil, får vi vist noget i retning af dette:

![Den ows_Doc_Type gennemsøgte egenskab.](../media/SPRetention10.png)

Egenskaben **owsDocx0020Type\_\_\_ er** den anden egenskab, der interesserer os. Den knyttes til **egenskaben Dokumenttype** for indholdstypen Produktionsdokument.

> [!TIP]
> For at identificere navnet på en gennemsøgt egenskab for dette scenarie skal du gå til det dokumentbibliotek, der indeholder produktionsdokumenterne. Gå derefter til biblioteksindstillingerne. Ud **for Kolonner** skal du vælge navnet på kolonnen (f.eks. **Status** eller **Dokumenttype**) for at åbne webstedskolonnesiden. *Feltparameteren* i URL-adressen for den pågældende side indeholder navnet på feltet. Dette feltnavn, der har præfikset "ows_", er navnet på den gennemsøgte egenskab. Eksempelvis svarer URL-adressen `https://tenantname.sharepoint.com/sites/SpinningWidget/_layouts/15/FldEdit.aspx?List=%7BC38C2F45-3BD6-4C3B-AA3B-EF5DF6B3D172%7D&Field=_Status` til den *gennemsøgte egenskab owsStatus\_\_*.

Hvis de gennemsøgte egenskaber, du leder efter, ikke vises i sektionen Administrer søgeskema SharePoint Administration:

- Måske er dokumenterne ikke blevet indekseret. Du kan gennemtvinge et nyt bibliotek ved at gå til Indstillinger **for dokumentbibliotekAdvanceret** >  **Indstillinger**.

- Hvis dokumentbiblioteket er på et moderne websted, skal du sikre dig, at SharePoint er administrator for gruppen af websteder.

Du kan finde flere oplysninger om gennemsøgte og administrerede egenskaber [under Automatisk oprettede administrerede egenskaber SharePoint Server](/sharepoint/technical-reference/automatically-created-managed-properties-in-sharepoint).

### <a name="map-crawled-properties-to-pre-defined-managed-properties"></a>Knytte gennemsøgte egenskaber til foruddefinerede administrerede egenskaber

KQL kan ikke bruge gennemsøgte egenskaber i søgeforespørgsler. Den skal bruge en administreret egenskab. I et typisk søgescenarie opretter vi en administreret egenskab og tilknytter den til den gennemsøgte egenskab, vi har brug for. Men for automatisk anvendelse af opbevaringsetiketter kan du kun angive foruddefinerede administrerede egenskaber i KQL og ikke brugerdefinerede administrerede egenskaber. Der er et sæt foruddefinerede administrerede egenskaber i systemet for *strengRefinableString00* til *RefinableString199* , som du kan bruge. Du kan finde en komplet liste under Standard [ubrugte administrerede egenskaber](/sharepoint/manage-search-schema#default-unused-managed-properties). Disse standard administrerede egenskaber bruges typisk til at definere søge afgrænsning.

Hvis KQL-forespørgslen automatisk skal anvende den korrekte opbevaringsetiket på produktdokumentindhold, tilknytter vi de gennemsøgte egenskaber **owsDocx0020Type\_\_\_* og *owsStatus\_\_** til to refinerbare administrerede egenskaber. I vores testmiljø til dette **scenarie bruges RefinableString00** og **RefinableString01** ikke. Det har vi besluttet ved at **se på Administrerede** **egenskaber i Administrer** <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a>.

[![Administrerede egenskaber i søgeskemaet.](../media/SPRetention12.png) ](../media/SPRetention12.png#lightbox)

Bemærk, at **kolonnen Tilknyttede gennemsøgte** egenskaber i det forrige skærmbillede er tom.

Hvis du vil tilknytte **egenskaben owsDocx0020Type\_\_\_, der** gennemsøges, skal du følge disse trin:

1. I **filterfeltet Administreret** egenskab skal du **_skrive RefinableString00_** og vælge den grønne pil.

2. Vælg linket **RefinableString00** på resultatlisten, og rul derefter ned til sektionen **Tilknytninger til gennemsøgte** egenskaber.

3. Vælg **Tilføj en** tilknytning, og skriv **_derefter owsDocx0020Type\_\_\__*_* i feltet _Search for a crawled property name** i vinduet **for** gennemsøgte egenskaber. Vælg **Søg**.

4. På resultatlisten skal du vælge **owsDocx0020Type\_\_\_** og derefter vælge **OK**.

   I sektionen **Tilknyttede gennemsøgte egenskaber** bør du få vist noget, der ligner dette skærmbillede:

   [![Vælg Tilføj en tilknytning i sektionen Tilknyttede gennemsøgte egenskaber.](../media/SPRetention13.png) ](../media/SPRetention13.png#lightbox)


5. Rul til bunden af siden, og vælg **OK** for at gemme tilknytningen.

Gentag disse trin for at **tilknytte RefinableString01** **og owsStatus\_\_**.

Nu bør du have to administrerede egenskaber tilknyttet de to gennemsøgte egenskaber:

[![Administrerede egenskaber vist tilknyttet gennemsøgte egenskaber.](../media/SPRetention14.png) ](../media/SPRetention14.png#lightbox)

Lad os kontrollere, at vores konfiguration er korrekt, ved at køre en virksomhedssøgning. Gå til https://*\<your_tenant>.sharepoint.com/search i en browser*. Skriv ***RefinableString00:"Produktspecifikation"_ i** søgefeltet, og tryk på Enter. Denne søgning bør returnere alle dokumenter, der har en _ *produktspecifikation** af **_dokumenttype_**.

Nu skal du i søgefeltet skrive **RefinableString00:"Produktspecifikation" OG RefinableString01:Final** og trykke på Enter. Dette bør returnere alle dokumenter, der har **produktspecifikationen** **_for Doc Type_*_ og en _* Status** for **_Endelig_**.

### <a name="create-auto-apply-label-policies"></a>Opret politikker for automatisk anvendelse af navne

Nu hvor vi har bekræftet, at KQL-forespørgslen fungerer, så lad os oprette en automatisk anvendelse af etiketpolitik, der bruger en KQL-forespørgsel til automatisk at anvende produktspecifikationens opbevaringsetiket på de relevante dokumenter.

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter skal</a> du gå til **Records managementLabel** >  **policiesAuto-apply** >  a label.

   [![Vælg "Anvend automatisk en etiket" på siden Etiketter](../media/SPRetention16.png) ](../media/SPRetention16.png#lightbox)

2. I guiden Opret politik for automatisk mærkater på siden Navngive  din politik for automatisk mærkater skal du angive et navn, f.eks. Anvend automatisk etiketten for produktspecifikationen og en valgfri beskrivelse. Vælg derefter **Næste**.

3. På siden **Vælg den type** indhold, du vil anvende denne etiket på skal du vælge Anvend etiket på indhold, der indeholder bestemte ord eller udtryk eller **egenskaber, og** vælg derefter **Næste**.

   [![Vælg Anvend etiket på indhold, der indeholder bestemte ord eller udtryk eller egenskaber.](../media/SPRetention17.png) ](../media/SPRetention17.png#lightbox)

   Med denne indstilling kan vi levere den samme KQL-søgeforespørgsel, som vi testede i forrige afsnit. Forespørgslen returnerer alle produktspecifikationsdokumenter, der har statussen *Endelig*. Når vi bruger den samme forespørgsel i automatisk anvendelse af etiketpolitikken, anvendes opbevaringsmærkaten for produktspecifikationen automatisk på alle dokumenter, der passer til den.

4. På siden **Anvend etiket** på indhold, der matcher denne forespørgsel skal du skrive **RefinableString00:"Produktspecifikation" AND RefinableString01:Final** og derefter vælge **Næste**.

   ![Angiv forespørgslen i feltet Nøgleordsforespørgselseditor.](../media/SPRetention19.png)

5. På siden **Vælg placeringer for at anvende politikken** skal du vælge de indholdsplaceringer, du vil anvende politikken på. I dette scenarie anvender vi kun politikken på SharePoint, fordi alle produktionsdokumenter gemmes i SharePoint dokumentbiblioteker. Slå status for mail **, Exchange** konti **OneDrive konti og** grupper **Microsoft 365 fra****.** Sørg for, at status for SharePoint er indstillet til **Til**, før du vælger **Næste**:

    ![Vælg bestemte websteder for automatisk at anvende navne på.](../media/SPRetentionSPlocations.png)

   > [!TIP]
   > I stedet for at anvende politikken på SharePoint websteder kan du vælge **Vælg** websted og tilføje URL-adresserne for bestemte SharePoint websteder.

6. På siden **Vælg en etiket til automatisk anvendelse skal** du vælge **Tilføj etiket**.

7. Vælg Produktspecifikation på listen over **opbevaringsnavne**. Vælg derefter **Tilføj** og **Næste**.

8. Gennemse dine indstillinger:

    ![Indstillinger at anvende etiketten automatisk.](../media/SPRetention18.png)

9. Vælg **Send** for at oprette automatisk anvendelse af etiketpolitik.

   > [!NOTE]
   > Det tager op til 7 dage at anvende produktspecifikationens etiket automatisk på alle dokumenter, der svarer til KQL-søgeforespørgslen.

### <a name="verify-that-the-retention-label-was-automatically-applied"></a>Kontrollér, at opbevaringsmærkaten blev anvendt automatisk

Efter syv dage kan du bruge [](data-classification-activity-explorer.md) Aktivitetsstifinder i Overholdelsescenter til at bekræfte, at den automatiske anvendelse af etiketpolitikken, vi har oprettet, automatisk anvender opbevaringsmærkaterne på produktdokumenterne.

Se også på egenskaberne for dokumenterne i dokumentbiblioteket. I informationspanelet kan du se, at opbevaringsmærkaten anvendes på et markeret dokument.

[![Kontrollér, at navnet er blevet anvendt, ved at se på dokumentegenskaberne i dokumentbiblioteket.](../media/SPRetention21.png) ](../media/SPRetention21.png#lightbox)

Da opbevaringsetiketterne er blevet anvendt automatisk på dokumenter, er disse dokumenter beskyttet mod sletning, fordi opbevaringsetiketten er konfigureret til at erklære dokumenterne som *poster*. Som et eksempel på denne beskyttelse får vi vist følgende fejlmeddelelse, når vi forsøger at slette et af disse dokumenter:

[![En fejlmeddelelse viser, at dokumenter ikke kan slettes, fordi etiketten erklærer, at dokumenterne er poster.](../media/SPRetention22.png) ](../media/SPRetention22.png#lightbox)

## <a name="generate-the-event-that-triggers-the-retention-period"></a>Generere den hændelse, der udløser opbevaringsperioden

Nu, hvor opbevaringsetiketterne er anvendt, fokuserer vi på den begivenhed, der angiver slutdatoen for produktion for et bestemt produkt. Denne hændelse udløser starten af den opbevaringsperiode, der er defineret i opbevaringsnavnene. For produktspecifikationsdokumenter starter opbevaringsperioden på fem år, når "slut på produktion"-hændelsen udløses.

Du kan manuelt oprette begivenheden i Microsoft 365 Overholdelsescenter ved at gå til **Records ManagementsEvents** > . Du skal vælge hændelsestypen, angive de korrekte aktiv-i-oplysninger og angive en dato for begivenheden. Få mere at vide under [Start opbevaring, når en hændelse indtræffer](event-driven-retention.md).

Men i dette scenarie genererer vi automatisk begivenheden ud fra et eksternt produktionssystem. Systemet er en simpel liste SharePoint der angiver, om et produkt er i produktion. Et [Power Automate](/power-automate/getting-started) flow, der er knyttet til listen, udløser hændelsen. I et virkelige scenarie kan du bruge forskellige systemer til at generere begivenheden, f.eks. et HR- eller CRM-system. Power Automate indeholder mange brugerklare interaktioner og byggesten til Microsoft 365-arbejdsbelastninger, f.eks. Microsoft Exchange, SharePoint, Teams og Dynamics 365 samt tredjepartsapps som Twitter, Box, Salesforce og Arbejdsdage. Denne funktion gør det nemt at integrere Power Automate med forskellige systemer. Få mere at vide under [Automatiser begivenhedsbaseret opbevaring](./event-driven-retention.md#automate-events-by-using-a-rest-api).

Følgende skærmbillede viser den SharePoint liste, der skal bruges til at udløse hændelsen:

[![Den liste, der udløser opbevaringshændelsen.](../media/SPRetention23.png) ](../media/SPRetention23.png#lightbox)

Der er i øjeblikket to produkter i produktion, som angivet af ***Ja** _ i kolonnen _ *I* produktion*. Når værdien i denne kolonne er angivet til **_Nej_** for et produkt, vil det flow, der er knyttet til listen, automatisk generere hændelsen. Hændelsen starter starten af opbevaringsperioden for den opbevaringsetiket, der blev anvendt automatisk på de tilsvarende produktdokumenter.

I dette scenarie bruger vi følgende flow til at udløse hændelsen:

[![Konfiguration af det flow, der udløser hændelsen.](../media/SPRetention24.png) ](../media/SPRetention24.png#lightbox)

Hvis du vil oprette dette flow, skal du starte fra SharePoint forbindelse og vælge **udløseren Når et element oprettes eller ændres**. Angiv webstedets adresse og listenavn. Tilføj derefter en betingelse baseret på, hvornår  værdien i listen I produktion er angivet til **_Nej_* _ (eller lig _false* på betingelseskortet). Tilføj derefter en handling, der er baseret på den indbyggede HTTP-skabelon. Brug værdierne i følgende afsnit til at konfigurere HTTP-handlingen. Du kan kopiere værdierne for **URI'en og** **egenskaberne** for Brødtekst fra følgende afsnit og indsætte dem i skabelonen.

- **Metode**: POST
- **URI**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **Overskrifter**: Nøgle = Content-Type, Value = application/atom+xml
- **Brødtekst**:

    ```xml
    <?xml version='1.0' encoding='utf-8' standalone='yes'>
    <entry xmlns:d='http://schemas.microsoft.com/ado/2007/08/dataservices' xmlns:m='http://schemas.microsoft.com/ado/2007/08/dataservices/metadata' xmlns='https://www.w3.org/2005/Atom'>
    <category scheme='http://schemas.microsoft.com/ado/2007/08/dataservices/scheme' term='Exchange.ComplianceRetentionEvent'>
    <updated>9/9/2017 10:50:00 PM</updated>
    <content type='application/xml'>
    <m:properties>
    <d:Name>Cessation Production @{triggerBody()?['Product_x0020_Name']?['Value']}</d:Name>
    <d:EventType>Product Cessation&lt;</d:EventType>
    <d:SharePointAssetIdQuery>ProductName:&quot;@{triggerBody()?['Product_x0020_Name']?['Value']}<d:SharePointAssetIdQuery>
    <d:EventDateTime>@{formatDateTime(utcNow(),'yyyy-MM-dd')}</d:EventDateTime>
    </m:properties>
    </content&gt>
    </entry>
    ```

Denne liste beskriver parametrene i egenskaben **Brødtekst** for den handling, der skal konfigureres til dette scenarie:

- **Navn**: Denne parameter angiver navnet på den hændelse, der oprettes i Microsoft 365 Overholdelsescenter. I dette scenarie er navnet "Kantproduktion *xxx*", hvor *xxx* er værdien af den **Administrerede ProductName-egenskab** , som vi oprettede tidligere.
- **EventType**: Værdien for denne parameter svarer til den hændelsestype, som den oprettede hændelse gælder for. Denne hændelsestype blev defineret, da du oprettede opbevaringsnavnet. I dette scenarie er hændelsestypen "Produktbegivenhed".
- **SharePointAssetIdQuery**: Denne parameter definerer aktiv-id'et for hændelsen. Hændelsesbaseret opbevaring skal have entydig identifier for dokumentet. Vi kan bruge aktiv-id'er til at identificere de dokumenter, som en bestemt hændelse gælder for, eller, som i dette scenarie, **metadatakolonnen Produktnavn**. For at gøre dette skal vi oprette en ny **ProductName-administreret** egenskab, der kan bruges i KQL-forespørgslen. (Alternativt kan vi bruge **RefinableString00 i stedet** for at oprette en ny administreret egenskab). Vi skal også knytte denne nye administrerede egenskab til den **ows_Product_x0020_Name** gennemsøgte egenskab. Her er et skærmbillede af denne administrerede egenskab.

    [![Leje administreret egenskab.](../media/SPRetention25.png) ](../media/SPRetention25.png#lightbox)

- **EventDateTime**: Denne parameter definerer den dato, hvor hændelsen forekommer. Brug det aktuelle datoformat:<br/><br/>*formatDateTime(utcNow(),'yyyy-MM-dd'*)

### <a name="putting-it-all-together"></a>Samle det hele

Nu oprettes og anvendes opbevaringsmærkaten automatisk, og flowet konfigureres og oprettes. Når værdien i kolonnen I  produktion for produktet roterende widget på listen Produkter ændres fra **_Ja_*_ til _*_No_ _, udløses flowet for at *oprette begivenheden. Hvis du vil se denne hændelse i overholdelsescenteret, skal du gå til _* Records** **managementEvents** > .

[![Den hændelse, der blev udløst af flowet, vises på siden Hændelser i overholdelsescenteret.](../media/SPRetention28.png) ](../media/SPRetention28.png#lightbox)

Vælg begivenheden for at få vist detaljerne på pop op-siden. Bemærk, at selvom begivenheden oprettes, viser begivenhedsstatussen, at SharePoint websteder eller dokumenter er blevet behandlet.

![Oplysninger om begivenhed.](../media/SPRetention29.png)

Men efter en forsinkelse viser hændelsesstatussen, at SharePoint websted og et SharePoint dokument er blevet behandlet.

![Oplysninger om begivenhed viser, at dokumenterne er blevet behandlet.](../media/SPRetention31.png)

Dette viser, at opbevaringsperioden for den etiket, der anvendes på produktdokumentet til roterende widget, er blevet startet baseret på datoen for begivenheden for den tvede produktionswidget, der *drejes* . Hvis du har implementeret scenariet i dit testmiljø ved at konfigurere en opbevaringsperiode på én dag, kan du gå til dokumentbiblioteket for dine produktdokumenter et par dage efter, at begivenheden blev oprettet, og bekræfte, at dokumentet er blevet slettet (efter sletningsjobbet i SharePoint er kørt).

### <a name="more-about-asset-ids"></a>Mere om aktiv-id'er

Som det [forklares i](event-driven-retention.md) artiklen Start opbevaring, når en hændelse indtræffer, er det vigtigt at forstå relationen mellem hændelsestyper, opbevaringsmærkater, begivenheder og aktiv-it'er. Aktiv-id'et er blot en dokumentegenskab i SharePoint og OneDrive. Det hjælper dig med at identificere de dokumenter, hvis opbevaringsperiode udløses af begivenheden. Har som standard SharePoint **aktiv-id,** som du kan bruge til hændelsesbaseret opbevaring:

![Egenskaben Aktiv-id vises på detaljesiden for dokumentegenskaber.](../media/SPRetention26.png)

Som det fremgår af følgende skærmbillede, kaldes den administrerede egenskab for **aktiv-id'et ComplianceAssetId**.

[![Administreret egenskab for ComplianceAssetId.](../media/SPRetention27.png) ](../media/SPRetention27.png#lightbox)

I stedet for at bruge **standardegenskaben** Aktiv-id, som vi gør i dette scenarie, kan du bruge en hvilken som helst anden egenskab. Men det er vigtigt at forstå, at hvis du ikke angiver et aktiv-id eller nøgleord for en begivenhed, vil alt det indhold, der har en etiket af den pågældende hændelsestype, få sin opbevaringsperiode udløst af begivenheden.

### <a name="using-advanced-search-in-sharepoint"></a>Brug af avanceret søgning i SharePoint

I det forrige skærmbillede kan du se, at der er en anden administreret egenskab relateret til opbevaringsetiketter kaldet **Overholdelsestag** , der er knyttet til en gennemsøgt egenskab. Den **administrerede egenskab ComplianceAssetId** er også knyttet til en gennemsøgt egenskab. Det betyder, at du kan bruge disse administrerede egenskaber i avanceret søgning til at hente alle dokumenter, der er mærket med en opbevaringsetiket.