---
title: Brug opbevaringsmærkater til at administrere Livscyklus for SharePoint-dokument
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
description: Sådan kan du bruge opbevaringsmærkater til at administrere livscyklussen for dokumenter i SharePoint ved hjælp af metadata til at klassificere indholdet, anvende mærkaterne automatisk og bruge hændelsesbaseret opbevaring til at starte opbevaringsperioden.
ms.openlocfilehash: ed054995943fc5366539fb6bc524757a6a6f820e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632965"
---
# <a name="use-retention-labels-to-manage-the-lifecycle-of-documents-stored-in-sharepoint"></a>Brug opbevaringsmærkater til at administrere livscyklussen for dokumenter, der er gemt i SharePoint

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

I denne artikel beskrives det, hvordan du kan administrere livscyklussen for dokumenter, der er gemt i SharePoint, ved hjælp af automatisk anvendte opbevaringsmærkater og hændelsesbaseret opbevaring.

Funktionen anvend automatisk bruger SharePoint-metadata til dokumentklassificering. Eksemplet i denne artikel er til produktrelaterede dokumenter, men de samme begreber kan bruges til andre scenarier. I olie- og gasbranchen kan du f.eks. bruge den til at administrere livscyklussen for dokumenter om fysiske aktiver, f.eks. olieplatforme, well logs eller produktionslicenser. I sektoren for finansielle tjenesteydelser kan du administrere dokumenter om bankkonto, realkreditlån eller forsikringskontrakter. I den offentlige sektor kan du administrere byggetilladelser eller skatteformularer.

I denne artikel kigger vi på informationsarkitekturen og definitionen af opbevaringsmærkater. Derefter klassificerer vi dokumenter ved automatisk at anvende mærkaterne. Og endelig genererer vi de hændelser, der starter opbevaringsperioden.

## <a name="information-architecture"></a>Informationsarkitektur

Vores scenarie er en produktionsvirksomhed, der bruger SharePoint til at gemme alle dokumenter om de produkter, som virksomheden udvikler. Disse dokumenter omfatter produktspecifikationer, aftaler med leverandører og brugervejledninger. Når disse dokumenter gemmes i SharePoint via politikker for administration af virksomhedsindhold, defineres dokumentmetadata, som bruges til at klassificere dem. Hvert dokument har følgende metadataegenskaber:

- **Dokumenttype** (f.eks. produktspecifikation, aftale eller brugervejledning)

- **Produktnavn**

- **Status** (kladde eller endelig)

Disse metadata udgør en grundlæggende indholdstype med navnet *Produktionsdokument* for alle dokumenterne.

![Tabel over metadata for produktdokumentation.](../media/SPRetention1.png)

> [!NOTE]
> Egenskaberne **Dokumenttype** og **Status** bruges af opbevaringspolitikker senere i dette scenarie til at klassificere og anvende opbevaringsmærkater automatisk.

Vi kan have flere indholdstyper, der repræsenterer forskellige typer dokumenter, men lad os fokusere på produktdokumentationen.

I dette scenarie bruger vi tjenesten Administrerede metadata og Ordbank til at oprette et ordsæt for *dokumenttype* og et andet for *Produktnavn*. For hvert ordsæt opretter vi et ord for hver værdi. Det vil se sådan ud i Ordbank for din SharePoint-organisation:

![Eksempelordsæt til produktdokumentation i Ordbank.](../media/SPRetention2.png)

*Indholdstypen* kan oprettes og publiceres ved hjælp af [indholdstypehubben](https://support.office.com/article/manage-content-type-publishing-06f39ac0-5576-4b68-abbc-82b68334889b). Du kan også oprette og publicere en indholdstype ved hjælp af værktøjer til klargøring af websteder, f.eks [. PnP-klargøringsstrukturen](/sharepoint/dev/solution-guidance/pnp-provisioning-framework) eller [JSON-skemaet til webstedsdesign](/sharepoint/dev/declarative-customization/site-design-json-schema#define-a-new-content-type).

Hvert produkt har et dedikeret SharePoint-websted, der indeholder ét dokumentbibliotek, hvor de rigtige indholdstyper er aktiveret. Alle dokumenter gemmes i dette dokumentbibliotek.

[![Dokumentbibliotek til produktdokumentation.](../media/SPRetention3.png) ](../media/SPRetention3.png#lightbox)

> [!NOTE]
> I stedet for at have et SharePoint-websted pr. produkt kan produktionsvirksomheden i dette scenarie bruge et Microsoft-team pr. produkt til at understøtte samarbejde mellem medlemmer af teamet, f.eks. gennem vedvarende chat, og bruge fanen **Filer** i Teams til dokumentstyring. I denne artikel fokuserer vi kun på dokumenter, så vi bruger kun et websted.

Her er en visning af dokumentbiblioteket for produktet Spinning Widget:

[![Spinning Widget-dokumentbibliotek.](../media/SPRetention4.png) ](../media/SPRetention4.png#lightbox)

Nu, hvor vi har den grundlæggende informationsarkitektur på plads til dokumentstyring, kan vi se på opbevarings- og bortskaffelsesstrategien for de dokumenter, der bruger metadataene, og hvordan vi klassificerer disse dokumenter.

## <a name="retention-and-disposition"></a>Opbevaring og fordeling

Produktionsvirksomhedens politikker for overholdelse af angivne standarder og datastyring dikterer, hvordan data bevares og bortskaffes. Produktrelaterede dokumenter skal opbevares, så længe produktet er fremstillet, og i en bestemt yderligere periode. Den ekstra periode varierer for produktspecifikationer, aftaler og brugervejledninger. Følgende tabel angiver opbevarings- og fordelingskravene:

|   Dokumenttype            |   Fastholdelse                            |   Fordeling                                |
| -------------------------- | -------------------------------------- | -------------------------------------------- |
| Produktspecifikationer      | 5 år efter produktionsstop  | Slette                                       |
| Produktaftaler          | 10 år efter produktionsstop | Vurder                                       |
| Brugermanualer                | 5 år efter produktionsstop  | Slette                                       |
| Alle andre dokumenttyper | Bevar ikke aktivt  | Slet, når dokumentet er ældre end tre år <br /><br /> Et dokument anses for at være ældre end 3 år, hvis det ikke er blevet ændret inden for de sidste tre år. |
|||

Vi bruger Microsoft Purview-compliance-portal til at oprette følgende [opbevaringsmærkater](retention.md#retention-labels):

  - Varespecifikationen

  - Produktaftale

  - Brugervejledning

I denne artikel viser vi kun, hvordan du opretter og anvender opbevaringsmærkaten for produktspecifikationen automatisk. Hvis du vil implementere hele scenariet, skal du også oprette og automatisk anvende opbevaringsmærkater for de to andre dokumenttyper.

### <a name="settings-for-the-product-specification-retention-label"></a>Indstillinger for opbevaringsmærkat for produktspecifikation

Her er [filplanen](file-plan-manager.md) for opbevaringsmærkaten for produktspecifikationen:

- **Navn:** Varespecifikationen

- **Beskrivelse af brugere:** Bevar i 5 år, efter produktionen er ophørt.

- **Beskrivelse af administratorer:** Bevar i 5 år, efter produktionen stopper, automatisk sletning, hændelsesbaseret opbevaring, hændelsestypen er *Produktophør*.

- **Opbevaringshandling:** Bevar og slet.

- **Opbevaringsvarighed:** 5 år (1.825 dage).

- **Postetiket**: Konfigurer opbevaringsmærkaten for at markere elementer som en [post](records-management.md#records), hvilket betyder, at de navngivne dokumenter derefter ikke kan ændres eller slettes af brugerne.

- **Beskrivelse af filplan:** Der er ikke angivet nogen valgfri filbeskrivelser for at forenkle scenariet.

På følgende skærmbillede vises indstillingerne, når du opretter opbevaringsmærkaten Produktspecifikation i Microsoft Purview-compliance-portal. Du kan oprette hændelsestypen *Produktophør* , når du opretter opbevaringsmærkaten. Se proceduren i følgende afsnit.

![Opbevaringsindstillinger for mærkaten Produktspecifikation.](../media/SPRetention5.png)

> [!NOTE]
> Hvis du vil undgå en 5-års ventetid for dokumentsletning, skal du angive opbevaringsvarigheden til ***1 dag*** , hvis du opretter dette scenarie igen i et testmiljø.

### <a name="create-an-event-type-when-you-create-a-retention-label"></a>Opret en hændelsestype, når du opretter en opbevaringsmærkat

1. På siden **Definer opbevaringsindstillinger** i guiden Opret opbevaringsmærkat skal du efter **Start opbevaringsperioden baseret på** vælge **Opret ny hændelsestype**:

    ![Opret en ny hændelsestype for dialogboksen Produktspecifikationsmærkat.](../media/SPRetention6.png)

3. På siden **Navngiv din hændelsestype** skal du angive **Produktophør** og en valgfri beskrivelse. Vælg derefter **Næste**, **Indsend** og **Udført**.

4. Tilbage på siden **Definer opbevaringsindstillinger** for **Start den opbevaringsperiode**, der er baseret på, skal du bruge rullelisten til at vælge hændelsestypen **Produktophør** , som du har oprettet.

    Sådan ser indstillingerne ud for opbevaringsmærkaten for produktspecifikationen:

   ![Indstillinger for det nye navn til produktspecifikationen.](../media/SPRetention7.png)

6. Vælg **Opret etiket**, og på næste side, når du ser indstillingerne for udgivelse af etiketten, skal du anvende etiketten automatisk eller blot gemme etiketten: Vælg **Gem blot etiketten for nu**, og vælg derefter **Udført**.

    > [!TIP]
    > Du kan finde flere detaljerede trin under [Opret en mærkat, hvis opbevaringsperiode er baseret på en hændelse](event-driven-retention.md#step-1-create-a-label-whose-retention-period-is-based-on-an-event).

Lad os nu se på, hvordan vi automatisk anvender opbevaringsmærkaten på indholdet i produktspecifikationen.

## <a name="auto-apply-retention-labels-to-documents"></a>Anvend automatisk opbevaringsmærkater på dokumenter

Vi bruger KQL (Keyword Query Language) til [automatisk at anvende](apply-retention-labels-automatically.md) de opbevaringsmærkater, vi har oprettet. KQL er det sprog, der bruges til at oprette søgeforespørgsler. I KQL kan du søge ved hjælp af nøgleord eller administrerede egenskaber. Du kan få flere oplysninger under [Reference til KQL-syntaks (Keyword Query Language).](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

Grundlæggende vil vi gerne bede Microsoft 365 om at "anvende opbevaringsmærkaten **for produktspecifikationen** på alle dokumenter, der har **statussen** **Final** og **Doc Type** of **Product Specification**". Husk, at **Status** og **Dokumenttype** er de webstedskolonner, vi har defineret for indholdstypen Produktdokumentation i afsnittet [Informationsarkitektur](#information-architecture) . Det gør vi ved at konfigurere søgeskemaet.

Når SharePoint indekserer indhold, genereres gennemsøgte egenskaber automatisk for hver webstedskolonne. I dette scenarie er vi interesseret i egenskaberne **Dokumenttype** og **Status** . Vi skal bruge dokumenter i biblioteket, der er den rigtige indholdstype, og webstedskolonnerne skal udfyldes til søgning for at oprette de gennemsøgte egenskaber.

Åbn søgekonfigurationen i <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a>, og vælg **Administrer søgeskema** for at få vist og konfigurere de gennemsøgte egenskaber.

![Gennemsøgte egenskaber i søgeskemaet.](../media/SPRetention8.png)

Hvis vi skriver ***status** _ i feltet _ *Gennemsøgte egenskaber** og vælger den grønne pil, får vi vist et resultat som dette:

![Den ows_Status gennemsøgte egenskab.](../media/SPRetention9.png)

Egenskaben **ows\_\_Status** (bemærk det dobbelte understregningstegn) er den, der interesserer os. Den knyttes til egenskaben **Status** for indholdstypen Produktionsdokument.

Hvis vi skriver ***ows\_doc*** og vælger den grønne pil, kan vi se noget i stil med dette:

![Den ows_Doc_Type gennemsøgte egenskab.](../media/SPRetention10.png)

Egenskaben **ows\_Doc\_x0020\_Type** er den anden egenskab, der interesserer os. Den knyttes til egenskaben **Doc Type** for indholdstypen Produktionsdokument.

> [!TIP]
> Hvis du vil identificere navnet på en gennemsøgt egenskab for dette scenarie, skal du gå til det dokumentbibliotek, der indeholder produktionsdokumenterne. Gå derefter til biblioteksindstillingerne. For **Kolonner** skal du vælge navnet på kolonnen (f.eks **. Status** eller **Dokumenttype**) for at åbne webstedskolonnesiden. *Feltparameteren* i URL-adressen for den pågældende side indeholder navnet på feltet. Dette feltnavn med præfikset "ows_" er navnet på den gennemsøgte egenskab. URL-adressen `https://tenantname.sharepoint.com/sites/SpinningWidget/_layouts/15/FldEdit.aspx?List=%7BC38C2F45-3BD6-4C3B-AA3B-EF5DF6B3D172%7D&Field=_Status` svarer f.eks. til den gennemsøgte egenskab *ows\_\_Status* .

Hvis de gennemsøgte egenskaber, du leder efter, ikke vises i afsnittet Administrer søgeskema i SharePoint Administration:

- Måske er dokumenterne ikke indekseret. Du kan gennemtvinge en omdex af biblioteket ved at gå til **Indstillinger for** >  dokumentbibliotek **Avancerede indstillinger**.

- Hvis dokumentbiblioteket findes på et moderne websted, skal du sørge for, at SharePoint-administratoren også er administrator af gruppen af websteder.

Du kan finde flere oplysninger om gennemsøgte og administrerede egenskaber under [Automatisk oprettede administrerede egenskaber i SharePoint Server](/sharepoint/technical-reference/automatically-created-managed-properties-in-sharepoint).

### <a name="map-crawled-properties-to-pre-defined-managed-properties"></a>Knyt gennemsøgte egenskaber til foruddefinerede administrerede egenskaber

KQL kan ikke bruge gennemsøgte egenskaber i søgeforespørgsler. Den skal bruge en administreret egenskab. I et typisk søgescenarie opretter vi en administreret egenskab og knytter den til den gennemsøgte egenskab, vi har brug for. Men for automatisk anvendelse af opbevaringsmærkater kan du kun angive foruddefinerede administrerede egenskaber i KQL og ikke brugerdefinerede administrerede egenskaber. Der er et sæt foruddefinerede administrerede egenskaber i systemet for strengen *RefinableString00* til *RefinableString199* , som du kan bruge. Du kan se en komplet liste under [Standard for ubrugte administrerede egenskaber](/sharepoint/manage-search-schema#default-unused-managed-properties). Disse administrerede standardegenskaber bruges typisk til at definere søgeindskrænkninger.

Hvis KQL-forespørgslen automatisk skal anvende den korrekte opbevaringsmærkat på produktdokumentindhold, knytter vi de gennemsøgte egenskaber **\_til Doc\_x0020\_Type* og ows Status til to administrerede egenskaber, der kan *afgrænses\_\_**. I vores testmiljø til dette scenarie bruges **RefinableString00** og **RefinableString01** ikke. Vi har bestemt dette ved **at se på Administrerede egenskaber** i **Administrer søgeskema** i <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint Administration</a>.

[![Administrerede egenskaber i søgeskema.](../media/SPRetention12.png) ](../media/SPRetention12.png#lightbox)

Bemærk, at kolonnen **Tilknyttede gennemsøgte egenskaber** på det forrige skærmbillede er tom.

Hvis du vil tilknytte den gennemsøgte egenskab **ows\_Doc\_x0020\_Type** , skal du følge disse trin:

1. I feltet **Filter for administreret egenskab** skal du skrive **_RefinableString00_** og vælge den grønne pil.

2. På listen over resultater skal du vælge linket **RefinableString00** og derefter rulle ned til afsnittet **Tilknytninger til gennemsøgte egenskaber** .

3. Vælg **Tilføj en tilknytning**, og skriv derefter **_ows\_Doc\_x0020\_Type_*_ i feltet _* Søg efter et navn på en gennemsøgt egenskab** i **vinduet Valg af gennemsøgt egenskab** . Vælg **Find**.

4. Vælg **ows\_Doc\_x0020\_Type** på listen over resultater, og vælg derefter **OK**.

   I afsnittet **Tilknyttede gennemsøgte egenskaber** kan du se noget, der ligner dette skærmbillede:

   [![Vælg Tilføj en tilknytning i afsnittet Tilknyttede gennemsøgte egenskaber.](../media/SPRetention13.png) ](../media/SPRetention13.png#lightbox)


5. Rul ned til bunden af siden, og vælg **OK** for at gemme tilknytningen.

Gentag disse trin for at tilknytte **RefinableString01** og **ows\_\_Status**.

Nu skal du have knyttet to administrerede egenskaber til de to gennemsøgte egenskaber:

[![De administrerede egenskaber, der vises knyttet til gennemsøgte egenskaber.](../media/SPRetention14.png) ](../media/SPRetention14.png#lightbox)

Lad os kontrollere, at vores konfiguration er korrekt, ved at køre en virksomhedssøgning. Gå til *https://\<your_tenant>.sharepoint.com/search* i en browser. Skriv ***RefinableString00:"Product Specification"** _ i søgefeltet, og tryk på Enter. Denne søgning skal returnere alle dokumenter, der har en _ *Product Specification** af **_dokumenttypen_**.

Skriv **RefinableString00:"Product Specification" AND RefinableString01:Final** i søgefeltet, og tryk på Enter. Dette skal returnere alle dokumenter, der har **produktspecifikationen** **_for Doc Type_*_ og en _* Status** of **_Final_**.

### <a name="create-auto-apply-label-policies"></a>Opret mærkatpolitikker for automatisk anvendelse

Nu, hvor vi har bekræftet, at KQL-forespørgslen fungerer, kan vi oprette en politik for automatisk anvendelse af mærkater, der bruger en KQL-forespørgsel til automatisk at anvende opbevaringsmærkaten for produktspecifikationen på de relevante dokumenter.

1. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a> skal du gå til **Mærkatpolitikker** >  for **administration af** >  data **automatisk anvende en mærkat**.

   [![Vælg "Anvend automatisk en etiket" på siden](../media/SPRetention16.png) Navne ](../media/SPRetention16.png#lightbox)

2. I guiden Opret politik til automatisk mærkning skal du angive et navn, f.eks **. Anvend mærkat til produktspecifikation automatisk**, og en valgfri beskrivelse på siden **Navngiv politik for automatisk mærkning**. Vælg derefter **Næste**.

3. På siden **Vælg den type indhold, du vil anvende denne etiket** på, skal du vælge **Anvend mærkat på indhold, der indeholder bestemte ord eller udtryk eller egenskaber**, og derefter vælge **Næste**.

   [![Vælg Anvend mærkat på indhold, der indeholder bestemte ord, udtryk eller egenskaber.](../media/SPRetention17.png) ](../media/SPRetention17.png#lightbox)

   Denne indstilling giver os mulighed for at angive den samme KQL-søgeforespørgsel, som vi testede i det forrige afsnit. Forespørgslen returnerer alle dokumenter med produktspecifikationen, der har statussen *Endelig*. Når vi bruger den samme forespørgsel i politikken for automatisk anvendelse af mærkat, anvendes opbevaringsmærkaten for produktspecifikationen automatisk for alle dokumenter, der stemmer overens med den.

4. På siden **Anvend mærkat på indhold, der stemmer overens med denne forespørgselsside** , skal du skrive **RefinableString00:"Product Specification" AND RefinableString01:Final** og derefter vælge **Næste**.

   ![Angiv forespørgslen i feltet Forespørgselseditor med nøgleord.](../media/SPRetention19.png)

5. På siden **Vælg placeringer, hvor politikken skal anvendes** skal du vælge de indholdsplaceringer, du vil anvende politikken på. I dette scenarie anvender vi kun politikken på SharePoint-placeringer, fordi alle produktionsdokumenterne gemmes i SharePoint-dokumentbiblioteker. Slå status for **Exchange-mail**, **OneDrive-konti** og **Microsoft 365-grupper** til **Fra**. Sørg for, at status for SharePoint-websteder er angivet til **Til** , før du vælger **Næste**:

    ![Vælg bestemte websteder, der automatisk skal anvendes mærkater på.](../media/SPRetentionSPlocations.png)

   > [!TIP]
   > I stedet for at anvende politikken på alle SharePoint-websteder kan du vælge **Vælg websted** og tilføje URL-adresserne for bestemte SharePoint-websteder.

6. På siden **Vælg en etiket, der skal anvendes automatisk** skal du vælge **Tilføj etiket**.

7. Vælg **Produktspecifikation** på listen over opbevaringsmærkater. Vælg derefter **Tilføj** og **Næste**.

8. Gennemse dine indstillinger:

    ![Indstillinger for automatisk anvendelse af etiketten.](../media/SPRetention18.png)

9. Vælg **Send** for at oprette mærkatpolitikken for automatisk anvendelse.

   > [!NOTE]
   > Det tager op til 7 dage at anvende mærkaten for produktspecifikationen automatisk på alle dokumenter, der svarer til KQL-søgeforespørgslen.

### <a name="verify-that-the-retention-label-was-automatically-applied"></a>Kontrollér, at opbevaringsmærkaten blev anvendt automatisk

Efter 7 dage kan du bruge [aktivitetsoversigten](data-classification-activity-explorer.md) i Microsoft Purview-compliance-portal til at bekræfte, at politikken for automatisk anvendelse af mærkater, som vi har oprettet, automatisk har anvendt opbevaringsmærkater på produktdokumenterne.

Se også egenskaberne for dokumenterne i dokumentbiblioteket. I informationspanelet kan du se, at opbevaringsmærkaten anvendes på et valgt dokument.

[![Kontrollér, at mærkaten blev anvendt, ved at se på dokumentegenskaberne i dokumentbiblioteket.](../media/SPRetention21.png) ](../media/SPRetention21.png#lightbox)

Da opbevaringsmærkater automatisk blev anvendt på dokumenter, er disse dokumenter beskyttet mod sletning, fordi opbevaringsmærkaten er konfigureret til at deklarere dokumenterne som *poster*. Som et eksempel på denne beskyttelse får vi vist følgende fejlmeddelelse, når vi forsøger at slette et af disse dokumenter:

[![En fejlmeddelelse viser, at dokumenter ikke kan slettes, fordi etiketten angiver, at dokumenterne er poster.](../media/SPRetention22.png) ](../media/SPRetention22.png#lightbox)

## <a name="generate-the-event-that-triggers-the-retention-period"></a>Generér den hændelse, der udløser opbevaringsperioden

Nu, hvor opbevaringsmærkater anvendes, skal vi fokusere på den hændelse, der angiver afslutningen af produktionen for et bestemt produkt. Denne hændelse udløser starten af den opbevaringsperiode, der er defineret i opbevaringsmærkater. For dokumenter med produktspecifikation begynder opbevaringsperioden på 5 år f.eks., når hændelsen "ophør af produktion" udløses.

Du kan oprette hændelsen manuelt i Microsoft Purview-compliance-portal ved at gå til **Hændelser** for **datastyring** > . Du skal vælge hændelsestypen, angive de korrekte aktiv-id'er og angive en dato for hændelsen. Du kan få flere oplysninger under [Start opbevaring, når der opstår en hændelse](event-driven-retention.md).

Men i dette scenarie genererer vi automatisk hændelsen fra et eksternt produktionssystem. Systemet er en simpel SharePoint-liste, der angiver, om et produkt er i produktion. Et [Power Automate-flow](/power-automate/getting-started) , der er knyttet til listen, udløser hændelsen. I et realistisk scenarie kan du bruge forskellige systemer til at generere hændelsen, f.eks. et HR- eller CRM-system. Power Automate indeholder mange brugsklare interaktioner og byggesten til Microsoft 365-arbejdsbelastninger, f.eks. Microsoft Exchange, SharePoint, Teams og Dynamics 365 samt tredjepartsapps som Twitter, Box, Salesforce og arbejdsdage. Denne funktion gør det nemt at integrere Power Automate med forskellige systemer. Du kan få flere oplysninger under [Automatiser hændelsesdrevet opbevaring](./event-driven-retention.md#automate-events-by-using-a-rest-api).

På følgende skærmbillede kan du se SharePoint-listen, der skal bruges som udløser for hændelsen:

[![Den liste, der udløser opbevaringshændelsen.](../media/SPRetention23.png) ](../media/SPRetention23.png#lightbox)

Der er i øjeblikket to produkter i produktion, som angivet med ***Ja** _ i kolonnen _ *I produktion**. Når værdien i denne kolonne er angivet til **_Nej_** for et produkt, genererer det flow, der er knyttet til listen, automatisk hændelsen. Hændelsen udløser starten på opbevaringsperioden for den opbevaringsmærkat, der automatisk blev anvendt på de tilsvarende produktdokumenter.

I dette scenarie bruger vi følgende flow til at udløse hændelsen:

[![Konfiguration af det flow, der udløser hændelsen.](../media/SPRetention24.png) ](../media/SPRetention24.png#lightbox)

Hvis du vil oprette dette flow, skal du starte fra en SharePoint-connector og vælge udløseren **Når et element oprettes eller ændres** . Angiv webstedsadressen og listenavnet. Tilføj derefter en betingelse, der er baseret på, hvornår kolonneværdien på listen **In Production** er angivet til **_No_* _ (eller lig med _false* på betingelseskortet). Tilføj derefter en handling baseret på den indbyggede HTTP-skabelon. Brug værdierne i følgende afsnit til at konfigurere HTTP-handlingen. Du kan kopiere værdierne for **egenskaberne URI** og **Brødtekst** fra følgende afsnit og indsætte dem i skabelonen.

- **Metode**: POST
- **URI**: `https://ps.compliance.protection.outlook.com/psws/service.svc/ComplianceRetentionEvent`
- **Headere**: Key = Content-Type, Value = application/atom+xml
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

På denne liste beskrives parametrene i egenskaben **Body** for den handling, der skal konfigureres for dette scenarie:

- **Navn**: Denne parameter angiver navnet på den hændelse, der oprettes i Microsoft Purview-compliance-portal. I dette scenarie er navnet "Ophørsproduktion *xxx*", hvor *xxx* er værdien af den **administrerede egenskab ProductName** , som vi oprettede tidligere.
- **EventType**: Værdien for denne parameter svarer til den hændelsestype, som den oprettede hændelse gælder for. Denne hændelsestype blev defineret, da du oprettede opbevaringsmærkaten. I dette scenarie er hændelsestypen "Produktophør".
- **SharePointAssetIdQuery**: Denne parameter definerer aktiv-id'et for hændelsen. Hændelsesbaseret opbevaring skal bruge et entydigt id for dokumentet. Vi kan bruge aktiv-id'er til at identificere de dokumenter, som en bestemt hændelse gælder for, eller som i dette scenarie kolonnen **Product Name** for metadata. For at gøre dette skal vi oprette en ny **productName-administreret** egenskab, der kan bruges i KQL-forespørgslen. (Alternativt kan vi bruge **RefinableString00** i stedet for at oprette en ny administreret egenskab). Vi skal også knytte denne nye administrerede egenskab til den **ows_Product_x0020_Name** gennemsøgte egenskab. Her er et skærmbillede af denne administrerede egenskab.

    [![Leje administreret ejendom.](../media/SPRetention25.png) ](../media/SPRetention25.png#lightbox)

- **EventDateTime**: Denne parameter definerer den dato, hvor hændelsen forekommer. Brug det aktuelle datoformat:<br/><br/>*formatDateTime(utcNow(),'yyyy-MM-dd'*)

### <a name="putting-it-all-together"></a>Sætte det hele sammen

Nu oprettes og anvendes opbevaringsmærkaten automatisk, og flowet konfigureres og oprettes. Når værdien i kolonnen **I produktion** for produktet Spinning Widget på listen Produkter ændres fra **_Ja_*_ til _*_No_*_, udløses flowet for at oprette hændelsen. Hvis du vil se denne hændelse i Microsoft Purview-compliance-portal, skal du gå til _*****Datastyringshændelser** > .

[![Den hændelse, der blev udløst af flowet, vises på siden Hændelser i Microsoft Purview-compliance-portal.](../media/SPRetention28.png) ](../media/SPRetention28.png#lightbox)

Vælg hændelsen for at få vist detaljerne på pop op-siden. Bemærk, at selvom hændelsen oprettes, viser hændelsesstatussen, at ingen SharePoint-websteder eller -dokumenter er blevet behandlet.

![Hændelsesoplysninger.](../media/SPRetention29.png)

Men efter en forsinkelse viser hændelsesstatussen, at et SharePoint-websted og et SharePoint-dokument er blevet behandlet.

![Hændelsesdetaljer viser, at dokumenter blev behandlet.](../media/SPRetention31.png)

Dette viser, at opbevaringsperioden for det mærkat, der anvendes på produktdokumentet Spinning Widget, er blevet startet baseret på hændelsesdatoen for hændelsen *Ophørsproduktion Spinning Widget* . Hvis du implementerede scenariet i testmiljøet ved at konfigurere en opbevaringsperiode på én dag, kan du gå til dokumentbiblioteket for produktdokumenterne et par dage efter, at hændelsen blev oprettet, og kontrollere, at dokumentet er blevet slettet (efter at sletningsjobbet i SharePoint er kørt).

### <a name="more-about-asset-ids"></a>Mere om aktiv-id'er

Som det forklares i artiklen [Start opbevaring, når en hændelse indtræffer](event-driven-retention.md) , er det vigtigt at forstå relationen mellem hændelsestyper, opbevaringsmærkater, hændelser og aktiv-id'er. Aktiv-id'et er blot en dokumentegenskab i SharePoint og OneDrive. Det hjælper dig med at identificere de dokumenter, hvis opbevaringsperiode udløses af hændelsen. SharePoint har som standard egenskaben **Asset Id** , som du kan bruge til hændelsesbaseret opbevaring:

![Egenskaben Aktiv-id vises på en side med dokumentegenskaber.](../media/SPRetention26.png)

Som vist på følgende skærmbillede kaldes den administrerede egenskab for **aktiv-id'et ComplianceAssetId**.

[![ComplianceAssetId administreret egenskab.](../media/SPRetention27.png) ](../media/SPRetention27.png#lightbox)

I stedet for at bruge standardegenskaben **Aktiv-id** , som vi gør i dette scenarie, kan du bruge en hvilken som helst anden egenskab. Men det er vigtigt at forstå, at hvis du ikke angiver et aktiv-id eller nøgleord for en hændelse, får alt det indhold, der har en mærkat af den pågældende hændelsestype, sin opbevaringsperiode udløst af hændelsen.

### <a name="using-advanced-search-in-sharepoint"></a>Brug af avanceret søgning i SharePoint

På det forrige skærmbillede kan du se, at der er en anden administreret egenskab, der er relateret til opbevaringsmærkater kaldet **ComplianceTag** , som er knyttet til en gennemsøgt egenskab. Den administrerede egenskab **ComplianceAssetId** knyttes også til en gennemsøgt egenskab. Det betyder, at du kan bruge disse administrerede egenskaber i avanceret søgning til at hente alle dokumenter, der er mærket med en opbevaringsmærkat.
