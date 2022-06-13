---
title: Anvend automatisk en opbevaringsmærkat
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
search.appverid:
- MOE150
- MET150
description: Opret politikker for opbevaring af automatisk mærkning, så du automatisk kan anvende mærkater for at bevare det, du har brug for, og slette det, du ikke har brug for
ms.openlocfilehash: 1b8871cba184772bd82e5e608c6e38113d4b0024
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012874"
---
# <a name="automatically-apply-a-retention-label-to-retain-or-delete-content"></a>Anvend automatisk en opbevaringsmærkat for at bevare eller slette indhold

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Dette scenarie understøttes ikke for [lovmæssige poster](records-management.md#records) eller standardnavne for en organiseringsstruktur, f.eks. et dokumentsæt eller et bibliotek i SharePoint eller en mappe i Exchange. Disse scenarier kræver en [publiceret politik for opbevaringsmærkat](create-apply-retention-labels.md).

En af de mest effektive funktioner i [opbevaringsmærkater](retention.md) er muligheden for automatisk at anvende dem på indhold, der opfylder de angivne betingelser. I dette tilfælde behøver personer i din organisation ikke at anvende opbevaringsmærkater. Microsoft 365 gør arbejdet for dem.
  
Automatisk anvendelse af opbevaringsmærkater er effektive, fordi:
  
- Du behøver ikke at oplære dine brugere i alle dine klassificeringer.
    
- Du behøver ikke at stole på, at brugerne klassificerer alt indhold korrekt.
    
- Brugerne behøver ikke længere at kende til politikker for datastyring – de kan fokusere på deres arbejde.
    
Du kan automatisk anvende opbevaringsmærkater på indhold, når der ikke allerede er anvendt en opbevaringsmærkat for dette indhold, og det indeholder følsomme oplysninger, nøgleord eller søgbare egenskaber eller et match for [klassificeringer, der kan oplæres](classifier-get-started-with.md). Nu som prøveversion kan du også automatisk anvende en opbevaringsmærkat på vedhæftede filer i skyen, der er gemt i SharePoint eller OneDrive.

> [!TIP]
> Brug søgbare egenskaber til at identificere [Teams mødeoptagelser](#microsoft-teams-meeting-recordings) og [elementer, hvor der er anvendt en følsomhedsmærkat](#identify-files-and-emails-that-have-a-sensitivity-label).

De processer, der automatisk anvender en opbevaringsmærkat baseret på disse betingelser:

![Diagram over roller og opgaver til automatisk anvendelse af navne.](../media/32f2f2fd-18a8-43fd-839d-72ad7a43e069.png)

Brug følgende instruktioner til de to administratortrin.

> [!NOTE]
> Automatiske politikker bruger mærkning på tjenestesiden med betingelser for automatisk at anvende opbevaringsmærkater på elementer. Du kan også automatisk anvende en opbevaringsmærkat med en mærkatpolitik, når du gør følgende: 
>
> - Anvend en opbevaringsmærkat på en model til dokumentforståelse i SharePoint Syntex
> - Anvend en standardopbevaringsmærkat for SharePoint og Outlook
> - Anvend en opbevaringsmærkat på mail ved hjælp af Outlook regler
>
> I disse scenarier skal du se [Publicer opbevaringsmærkater og anvende dem i apps](create-apply-retention-labels.md).

## <a name="before-you-begin"></a>Før du begynder

Den globale administrator for din organisation har fuld tilladelse til at oprette og redigere opbevaringsmærkater og deres politikker. Hvis du ikke logger på som global administrator, kan du se oplysninger om tilladelser til [dataadministration](get-started-with-records-management.md#permissions) eller administration af [datalivscyklus](get-started-with-data-lifecycle-management.md#permissions-for-retention-policies-and-retention-labels), afhængigt af den løsning du bruger.

Sørg for, at du har [oprettet de opbevaringsmærkater](file-plan-manager.md#create-retention-labels) , du vil anvende på elementer.

## <a name="how-to-create-an-auto-apply-retention-label-policy"></a>Sådan opretter du en politik for automatisk anvendelse af opbevaringsmærkat

Beslut, om politikken for opbevaringsmærkaten skal være **tilpasset** eller **statisk**, før du opretter den. Du kan finde flere oplysninger under [Tilpassede eller statiske politikområder for opbevaring](retention.md#adaptive-or-static-policy-scopes-for-retention). Hvis du beslutter at bruge en tilpasset politik, skal du oprette et eller flere tilpassede områder, før du opretter din politik for opbevaringsmærkat og derefter vælger dem under processen til oprettelse af opbevaringsmærkatpolitik. Du kan finde en vejledning under [Konfigurationsoplysninger for tilpassede områder](retention-settings.md#configuration-information-for-adaptive-scopes).

Når du opretter en politik, der automatisk skal anvendes, vælger du en opbevaringsmærkat, der automatisk skal anvendes på indhold baseret på de betingelser, du angiver.

1. Gå til en af følgende placeringer på [Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/):
    
    - Hvis du bruger datastyring:
        - **Løsninger** >  **Datastyring** > > fanen **Mærkatpolitikker** > **Anvend automatisk en etiket**
    
    - Hvis du bruger administration af datalivscyklus:
        - **Løsninger** >  Administration  >  **af datalivscyklus** Fanen **Etiketpolitikker** > **Anvend automatisk en etiket**
    
    Kan du ikke se din løsning i navigationsruden med det samme? Vælg først **Vis alle**.

2. Angiv et navn og en beskrivelse til denne politik for automatisk mærkning, og vælg derefter **Næste**.

3. Vælg en af de tilgængelige betingelser for **Vælg den type indhold, du vil anvende dette navn på**. Du kan finde flere oplysninger om valgmulighederne i afsnittet [Konfiguration af betingelser for automatisk anvendelse af opbevaringsmærkater](#configuring-conditions-for-auto-apply-retention-labels) på denne side.

4. På siden **Vælg den type opbevaringspolitik, der skal oprettes** skal du vælge **Adaptiv** eller **Statisk** afhængigt af det valg, du har foretaget i vejledningen [Før du starter](#before-you-begin) . Hvis du ikke allerede har oprettet tilpassede områder, kan du vælge **Adaptivt** , men fordi der ikke er nogen tilpassede områder at vælge, kan du ikke fuldføre guiden med denne indstilling.

5. Afhængigt af dit valgte område:
    
    - Hvis du vælger **Adaptiv**: På siden **Vælg tilpassede politikområder og -placeringer** skal du vælge **Tilføj områder** og vælge et eller flere tilpassede områder, der er blevet oprettet. Vælg derefter en eller flere placeringer. De placeringer, du kan vælge, afhænger af de [tilføjede områdetyper](retention-settings.md#configuration-information-for-adaptive-scopes) . Hvis du f.eks. kun har tilføjet områdetypen **Bruger**, kan du vælge **Exchange mail**, men ikke **SharePoint websteder**. 
    
    - Hvis du vælger **Statisk**: På siden **Vælg placeringer** skal du slå en af placeringerne til eller fra. For hver placering kan du lade den være som standard for at [anvende politikken på hele placeringen](retention-settings.md#a-policy-that-applies-to-entire-locations), eller du kan [angive medtag og ekskludering](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions)
    
    Du kan få oplysninger om valg af placering under [Placeringer](retention-settings.md#locations).

6. Følg prompterne i guiden for at vælge en opbevaringsmærkat, og gennemse og send derefter dine konfigurationsvalg.

Hvis du vil redigere en eksisterende politik for opbevaringsmærkater (politiktypen **Anvend automatisk**), skal du vælge den og derefter vælge indstillingen **Rediger** for at starte konfigurationen **Rediger opbevaringspolitik** .

Når indholdet er mærket ved hjælp af en politik for automatisk anvendelse af mærkater, kan den anvendte mærkat ikke fjernes eller ændres automatisk ved at ændre indholdet eller politikken eller af en ny politik for automatisk anvendelse af mærkater. Du kan få flere oplysninger under [Kun én opbevaringsmærkat ad gangen](retention.md#only-one-retention-label-at-a-time).

> [!NOTE]
> En politik for automatisk anvendelse af opbevaringsmærkat erstatter aldrig en eksisterende opbevaringsmærkat, der er anvendt på indhold. Hvis du vil genmærke indhold ved hjælp af de betingelser, du konfigurerer, skal du manuelt fjerne den aktuelle opbevaringsmærkat fra eksisterende indhold.

### <a name="configuring-conditions-for-auto-apply-retention-labels"></a>Konfiguration af betingelser for automatisk anvendelse af opbevaringsmærkater

Du kan automatisk anvende opbevaringsmærkater på indhold, når indholdet indeholder:

- [Specifikke typer følsomme oplysninger](#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)

- [Specifikke nøgleord eller egenskaber, der kan søges i, og som svarer til en forespørgsel, du opretter](#auto-apply-labels-to-content-with-keywords-or-searchable-properties)

- [Et match for klassificeringer, der kan oplæres](#auto-apply-labels-to-content-by-using-trainable-classifiers)

Eller du kan automatisk anvende opbevaringsmærkater på [nyligt delte vedhæftede filer i skyen](#auto-apply-labels-to-cloud-attachments).

Når du konfigurerer opbevaringsmærkater til automatisk anvendelse baseret på følsomme oplysninger, nøgleord eller søgbare egenskaber eller oplærbare klassificeringer, skal du bruge følgende tabel til at identificere, hvornår opbevaringsmærkater kan anvendes automatisk.

Exchange:

|Betingelse|Varer under forsendelse (sendt eller modtaget) |Eksisterende elementer (inaktive data)|
|:-----|:-----|:-----|
|Følsomme infotyper – indbygget| Ja | Nej |
|Følsomme infotyper – brugerdefineret| Ja | Nej |
|Specifikke nøgleord eller egenskaber, der kan søges efter| Ja |Ja |
|Trænbare klassificeringer| Ja | Ja (kun de seneste seks måneder) |

SharePoint og OneDrive:

|Betingelse|Nye eller ændrede elementer |Eksisterende elementer |
|:-----|:-----|:-----|
|Følsomme infotyper – indbygget| Ja | Ja |
|Følsomme infotyper – brugerdefineret| Ja | Nej |
|Specifikke nøgleord eller egenskaber, der kan søges efter| Ja |Ja |
|Trænbare klassificeringer| Ja | Ja (kun de seneste seks måneder) |

Derudover understøttes SharePoint elementer, der er kladder, eller som aldrig er blevet publiceret, ikke i dette scenarie.

#### <a name="auto-apply-labels-to-content-with-specific-types-of-sensitive-information"></a>Anvend automatisk mærkater på indhold med bestemte typer følsomme oplysninger

> [!IMPORTANT]
> For mails, som du automatisk anvender ved at identificere følsomme oplysninger, medtages alle postkasser automatisk, hvilket omfatter postkasser fra Microsoft 365 grupper.
> 
> Selvom gruppepostkasser normalt medtages ved at vælge den **Microsoft 365-grupper** placering, omfatter gruppeplaceringen kun SharePoint websteder, der er forbundet med en Microsoft 365 gruppe, for denne specifikke politikkonfiguration.

Når du opretter politikker for automatisk anvendelse af opbevaringsmærkater for følsomme oplysninger, får du vist den samme liste over politikskabeloner, som når du opretter en DLP-politik (Microsoft Purview Data Loss Prevention). Hver skabelon er forudkonfigureret til at søge efter bestemte typer følsomme oplysninger. I følgende eksempel er de følsomme oplysningstyper fra kategorien **Beskyttelse af personlige oplysninger** og dataskabelonen Personlige **oplysninger (PII** ):

![Politikskabeloner med typer af følsomme oplysninger.](../media/sensitive-info-configuration.png)

Du kan få mere at vide om typerne af følsomhedsoplysninger under [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types). I øjeblikket understøttes [præcise datamatchbaserede følsomme oplysningstyper](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) og [dokumentaftryk](document-fingerprinting.md) ikke i dette scenarie.

Når du har valgt en politikskabelon, kan du tilføje eller fjerne alle typer følsomme oplysninger, og du kan ændre tillidsniveauet og antallet af forekomster. På det forrige eksempelskærmbillede er disse indstillinger blevet ændret, så en opbevaringsmærkat kun anvendes automatisk, når:
  
- Den type følsomme oplysninger, der registreres, har en matchnøjagtighed (eller [et konfidensniveau](sensitive-information-type-learn-about.md#more-on-confidence-levels)) med mindst **medium genkendelsessikkerhed** for to af de følsomme oplysningstyper og **Høj genkendelsessikkerhed** for én. Mange følsomme oplysningstyper er defineret med flere mønstre, hvor et mønster med en højere matchnøjagtighed kræver, at der findes flere beviser (f.eks. nøgleord, datoer eller adresser), mens et mønster med en lavere matchnøjagtighed kræver mindre beviser. Jo lavere konfidensniveauet er, jo lettere er det for indhold at matche betingelsen, men med potentiale for flere falske positiver.

- Indholdet indeholder mellem 1 og 9 forekomster af disse tre følsomme infotyper. Standardværdien for **til-værdien** er **Enhver**.

Du kan finde flere oplysninger om disse indstillinger i følgende vejledning i DLP-dokumentationen [Justeringsregler for at gøre dem nemmere eller sværere at matche](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

> [!IMPORTANT]
> Følsomme informationstyper har to forskellige måder at definere de maksimale antal parametre for entydige forekomster på. Hvis du vil vide mere, skal du se [Antal understøttede værdier for SIT.](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit)

Sådan overvejer du, når du bruger følsomme oplysningstyper til automatisk at anvende opbevaringsmærkater:

- Hvis du bruger brugerdefinerede følsomme oplysningstyper, kan disse ikke automatisk navngive eksisterende elementer i SharePoint og OneDrive.

- I forbindelse med mails kan du ikke vælge bestemte modtagere, der skal inkluderes eller udelades. Kun indstillingen **Alle modtagere** understøttes, og for denne konfiguration omfatter den kun postkasser fra Microsoft 365 grupper. 

#### <a name="auto-apply-labels-to-content-with-keywords-or-searchable-properties"></a>Anvend automatisk mærkater på indhold med nøgleord eller søgbare egenskaber

Du kan anvende mærkater automatisk på indhold ved hjælp af en forespørgsel, der indeholder bestemte ord, udtryk eller værdier for søgbare egenskaber. Du kan tilpasse din forespørgsel ved hjælp af søgeoperatorer, f.eks. AND, OR og NOT.

![Forespørgselseditor.](../media/new-retention-query-editor.png)

Du kan få flere oplysninger om den forespørgselssyntaks, der bruger KQL (Keyword Query Language), under [Reference til KQL-syntaks (Keyword Query Language).](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)

Forespørgselsbaserede politikker til automatisk anvendelse bruger det samme søgeindeks som eDiscovery-indholdssøgning til at identificere indhold. Du kan finde flere oplysninger om de egenskaber, der kan søges i, under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).

Nogle ting, du skal overveje, når du bruger nøgleord eller egenskaber, der kan søges efter, til automatisk at anvende opbevaringsmærkater:

- I forbindelse med SharePoint understøttes gennemsøgte egenskaber og brugerdefinerede egenskaber ikke for disse KQL-forespørgsler, og du må kun bruge foruddefinerede administrerede egenskaber for dokumenter. Du kan dog bruge tilknytninger på lejerniveau med de foruddefinerede administrerede egenskaber, der som standard er aktiveret som afgrænsninger (RefinableDate00-19, RefinableString00-99, RefinableInt00-49, RefinableDecimals00-09 og RefinableDouble00-09). Du kan finde flere oplysninger [under Oversigt over gennemsøgte og administrerede egenskaber i SharePoint Server](/SharePoint/technical-reference/crawled-and-managed-properties-overview), og du kan finde instruktioner under [Opret en ny administreret egenskab](/sharepoint/manage-search-schema#create-a-new-managed-property).

- Hvis du knytter en brugerdefineret egenskab til en af afgrænsningsegenskaberne, skal du vente 24 timer, før du bruger den i din KQL-forespørgsel for en opbevaringsmærkat.

- Selvom SharePoint administrerede egenskaber kan omdøbes ved hjælp af aliasser, skal du ikke bruge disse til KQL-forespørgsler i dine navne. Angiv altid det faktiske navn på den administrerede egenskab, f.eks. "RefinableString01".

- Hvis du vil søge efter værdier, der indeholder mellemrum eller specialtegn, skal du bruge dobbelte anførselstegn (`" "`) til at indeholde udtrykket, `subject:"Financial Statements"`f.eks. .

- Brug egenskaben *DocumentLink* i stedet for *Path* til at matche et element baseret på dets URL-adresse. 

- Suffiks-jokertegnsøgninger (f.eks. `*cat`) eller jokertegnsøgninger med understrenge (f.eks. `*cat*`) understøttes ikke. Men præfiks-jokertegnsøgninger (f.eks. `cat*`) understøttes.

- Vær opmærksom på, at delvist indekserede elementer kan være ansvarlige for ikke at forsyne elementer, som du forventer, eller forsyne elementer, som du forventer at blive udelukket fra mærkning, når du bruger operatoren NOT. Du kan finde flere oplysninger under [Delvist indekserede elementer i indholdssøgning](partially-indexed-items-in-content-search.md).


Eksempler på forespørgsler:

| Arbejdsbyrde | Eksempel |
|:-----|:-----|
|Exchange   | `subject:"Financial Statements"` |
|Exchange   | `recipients:garthf@contoso.com` |
|SharePoint | `contenttype:document` |
|SharePoint | `site:https://contoso.sharepoint.com/sites/teams/procurement AND contenttype:document`|
|Exchange eller SharePoint | `"customer information" OR "private"`|

Mere komplekse eksempler:

Følgende forespørgsel om SharePoint identificerer Word-dokumenter eller Excel regneark, når disse filer indeholder **nøgleordsadgangskoden**, **adgangskoder** eller **pw**:

```
(password OR passwords OR pw) AND (filetype:doc* OR filetype:xls*)
```

Følgende forespørgsel om Exchange identificerer alle Word-dokumenter eller PDF-dokumenter, der indeholder ordet **nda** eller sætningen **fortrolighedsaftale**, når disse dokumenter er knyttet til en mail:

```
(nda OR "non disclosure agreement") AND (attachmentnames:.doc* OR attachmentnames:.pdf)
```

Følgende forespørgsel om SharePoint identificerer dokumenter, der indeholder et kreditkortnummer: 

```
sensitivetype:"credit card number"
```

Følgende forespørgsel indeholder nogle typiske nøgleord, der kan hjælpe med at identificere dokumenter eller mails, der indeholder juridisk indhold:

```
ACP OR (Attorney Client Privilege*) OR (AC Privilege)
```

Følgende forespørgsel indeholder typiske nøgleord, der kan hjælpe med at identificere dokumenter eller mails til HR: 

```
(resume AND staff AND employee AND salary AND recruitment AND candidate)
```

Bemærk, at i dette sidste eksempel bruges bedste praksis for altid at inkludere operatorer mellem nøgleord. Et mellemrum mellem nøgleord (eller to property:value-udtryk) er det samme som at bruge AND. Når du altid tilføjer operatorer, er det nemmere at se, at denne eksempelforespørgsel kun identificerer indhold, der indeholder alle disse nøgleord, i stedet for indhold, der indeholder nøgleordene. Hvis du har til hensigt at identificere indhold, der indeholder et af nøgleordene, skal du angive ELLER i stedet for AND. Som vist i dette eksempel er det nemmere at fortolke forespørgslen korrekt, når du altid angiver operatorerne. 

##### <a name="microsoft-teams-meeting-recordings"></a>Microsoft Teams mødeoptagelser

> [!NOTE]
> Muligheden for at bevare og slette Teams mødeoptagelser fungerer ikke, før optagelser gemmes på OneDrive eller SharePoint. Du kan få flere oplysninger under [Brug OneDrive for Business og SharePoint Online eller Stream til mødeoptagelser](/MicrosoftTeams/tmr-meeting-recording-change).

Hvis du vil identificere Microsoft Teams mødeoptagelser, der er gemt i brugernes OneDrive konti eller i SharePoint, skal du angive følgende for **forespørgselseditoren med nøgleord**:

```
ProgID:Media AND ProgID:Meeting
```

For det meste gemmes mødeoptagelser for at OneDrive. Men for kanalmøder gemmes de i SharePoint.

##### <a name="identify-files-and-emails-that-have-a-sensitivity-label"></a>Identificer filer og mails, der har en følsomhedsmærkat

Hvis du vil identificere filer i SharePoint eller OneDrive og Exchange mails, hvor der er anvendt en bestemt [følsomhedsmærkat](sensitivity-labels.md), skal du angive følgende for **forespørgselseditoren med nøgleord**:

```
InformationProtectionLabelId:<GUID>
```

Hvis du vil finde GUID'et, skal du bruge [Cmdlet'en Get-Label](/powershell/module/exchange/get-label) fra [Security & Compliance PowerShell](/powershell/exchange/scc-powershell):

```powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid
```

#### <a name="auto-apply-labels-to-content-by-using-trainable-classifiers"></a>Anvend automatisk mærkater på indhold ved hjælp af klassificeringer, der kan oplæres

Når du vælger indstillingen for en klassificering, der kan oplæres, kan du vælge en eller flere af de færdiguddannede eller brugerdefinerede klassificeringer, der kan oplæres:

![Vælg klassificering, der kan oplæres.](../media/retention-label-classifers.png)

> [!CAUTION]
> Vi udfaser den prækvalificerede klassificering af **stødende sprog** , fordi den har produceret et højt antal falske positiver. Brug ikke denne klassificering, og hvis du i øjeblikket bruger den, anbefaler vi, at du fjerner dine forretningsprocesser fra den og i stedet bruger de forududlærte klassificeringer **målrettet chikane**, **bandeord** og **trussel** .

Hvis du vil anvende en mærkat automatisk ved hjælp af denne indstilling, skal SharePoint websteder samt postkasser have mindst 10 MB data.

Du kan finde flere oplysninger om klassificeringer, der kan oplæres, under [Få mere at vide om klassificeringer, der kan oplæres](classifier-learn-about.md).

> [!TIP]
> Hvis du bruger klassificeringer, der kan oplæres til Exchange, skal du se [Sådan oplæres en klassificering igen i Indholdsoversigt](classifier-how-to-retrain-content-explorer.md).

Sådan overvejer du, når du bruger klassificeringer, der kan oplæres, til automatisk at anvende opbevaringsmærkater:

- Du kan ikke automatisk navngive SharePoint og OneDrive elementer, der er ældre end seks måneder.

#### <a name="auto-apply-labels-to-cloud-attachments"></a>Anvend automatisk mærkater på vedhæftede filer i skyen

> [!NOTE]
> Denne indstilling udrulles gradvist som prøveversion og kan ændres.

Du skal muligvis bruge denne indstilling, hvis du skal hente og bevare alle kopier af filer i din lejer, der sendes via kommunikation af brugere. Du kan bruge denne indstilling sammen med opbevaringspolitikker for selve kommunikationstjenesterne, Exchange og Teams.

> [!IMPORTANT]
> Når du vælger en etiket, der skal bruges til automatisk anvendelse af opbevaringsmærkater for vedhæftede filer i skyen, skal du sikre, at indstillingen for opbevaring af mærkater **Start opbevaringsperioden baseret på** **er Når elementer blev navngivet**.

Vedhæftede filer i cloudmiljøet, også kaldet moderne vedhæftede filer, er en delingsmekanisme, der bruger integrerede links til filer, der er gemt i cloudmiljøet. De understøtter centraliseret lagring af delt indhold med samarbejdsfordele, f.eks. versionsstyring. Vedhæftede filer i skyen vedhæftes ikke kopier af en fil eller et URL-tekstlink til en fil. Du kan finde det nyttigt at se de visuelle tjeklister for understøttede vedhæftede filer i skyen i [Outlook](/office365/troubleshoot/retention/cannot-retain-cloud-attachments#cloud-attachments-in-outlook) og [Teams](/office365/troubleshoot/retention/cannot-retain-cloud-attachments#cloud-attachments-in-teams).

Når du vælger muligheden for at anvende en opbevaringsmærkat på vedhæftede filer i skyen af hensyn til overholdelse af angivne standarder, oprettes der en kopi af filen på tidspunktet for delingen. Den valgte opbevaringsmærkat anvendes derefter på den kopi, der derefter kan [identificeres ved hjælp af eDiscovery](advanced-ediscovery-cloud-attachments.md). Brugerne kender ikke til den kopi, der er gemt i biblioteket til bevarelse af venteposition. Opbevaringsmærkaten anvendes ikke på selve meddelelsen eller den oprindelige fil.

Hvis filen ændres og deles igen, gemmes en ny kopi af filen som en ny version i biblioteket bevarelsesposition. Du kan få flere oplysninger, herunder hvorfor du skal bruge **mærkatindstillingen Når elementer blev mærket** , under [Sådan fungerer opbevaring med vedhæftede filer i skyen](retention-policies-sharepoint.md#how-retention-works-with-cloud-attachments).

De vedhæftede filer i skyen, der understøttes for denne indstilling, er filer som dokumenter, videoer og billeder, der er gemt i SharePoint og OneDrive. I forbindelse med Teams understøttes vedhæftede filer i skyen, der deles i chatbeskeder, samt standardkanaler og private kanaler. Vedhæftede filer i skyen, der deles via mødeindkaldelser, og andre apps end Teams eller Outlook understøttes ikke. Vedhæftede filer i skyen skal deles af brugerne. vedhæftede filer i skyen, der sendes via robotter, understøttes ikke.

Selvom det ikke kræves til denne indstilling, anbefaler vi, at du sikrer, at versionsstyring er aktiveret for dine SharePoint websteder og OneDrive konti, så den delte version kan registreres nøjagtigt. Hvis versionsstyring ikke er aktiveret, bevares den senest tilgængelige version. Dokumenter i kladden, eller som aldrig er blevet publiceret, understøttes ikke.

Når du vælger en etiket, der skal bruges til automatisk anvendelse af opbevaringsmærkater for vedhæftede filer i skyen, skal du sørge for, at indstillingen for opbevaring af mærkater **Start opbevaringsperioden baseret på** **er Når elementer blev mærket**. 

Når du konfigurerer placeringerne for denne indstilling, kan du vælge:

- **SharePoint websteder** til delte filer, der er gemt på SharePoint kommunikationswebsteder, teamwebsteder, der ikke er forbundet af Microsoft 365 grupper, og klassiske websteder. 
- **Microsoft 365-grupper** til delte filer, der er gemt på teamwebsteder, som Microsoft 365 grupper har oprettet forbindelse til.
- **OneDrive konti** for delte filer, der er gemt i brugernes OneDrive.

Du skal oprette separate opbevaringspolitikker, hvis du vil bevare eller slette de oprindelige filer, mails eller Teams meddelelser.

> [!NOTE]
> Hvis vedhæftede filer i skyen skal udløbe samtidig med de meddelelser, der indeholdt dem, skal du konfigurere opbevaringsmærkaten, så den har den samme bevarelse og derefter slette handlinger og tidsindstillinger som dine opbevaringspolitikker for Exchange og Teams.

Sådan overvejer du, hvornår opbevaringsmærkater automatisk anvendes på vedhæftede filer i skyen:

- Det er kun nyligt delte vedhæftede filer i skyen, der automatisk mærkes til opbevaring.

- Vedhæftede filer i skyen, der deles uden for Teams og Outlook, understøttes ikke.

- Følgende elementer understøttes ikke som vedhæftede filer i skyen, der kan bevares:
    - SharePoint websteder, sider, lister, formularer, mapper, dokumentsæt og OneNote sider.
    - Filer, der deles af brugere, som ikke har adgang til disse filer.
    - Filer, der slettes eller flyttes, før den vedhæftede fil i skyen sendes. En bruger kopierer og indsætter f.eks. en tidligere delt vedhæftet fil fra en anden meddelelse uden først at bekræfte, at filen stadig er tilgængelig. Eller nogen videresender en gammel meddelelse, når filen nu slettes.
    - Filer, der deles af gæster eller brugere uden for din organisation.
    - Filer i kladdemails og meddelelser, der ikke sendes.
    - Tomme filer.

## <a name="how-long-it-takes-for-retention-labels-to-take-effect"></a>Hvor lang tid det tager, før opbevaringsmærkater træder i kraft

Når du anvender opbevaringsmærkater automatisk på baggrund af følsomme oplysninger, nøgleord eller søgbare egenskaber eller klassificeringer, der kan oplæres, kan det tage op til syv dage, før opbevaringsmærkater anvendes:
  
![Diagram over, hvornår automatisk anvendelse af navne træder i kraft.](../media/retention-labels-autoapply-timings.png)

Hvis de forventede mærkater ikke vises efter syv dage, skal du kontrollere **status** for politikken for automatisk anvendelse ved at vælge den på siden **Mærkatpolitikker** på Microsoft Purview-overholdelsesportalen. Hvis du får vist status for **Fra (fejl),** og du i oplysningerne om placeringerne får vist en meddelelse om, at det tager længere tid end forventet at installere politikken (for SharePoint) eller at forsøge at geninstallere politikken (for OneDrive), kan du prøve at køre [PowerShell-kommandoen Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) for at forsøge at distribuere politikken igen:

1. [Forbind til PowerShell til sikkerhed & overholdelse af angivne standarder](/powershell/exchange/connect-to-scc-powershell).

2. Kør følgende kommando:
    
    ```PowerShell
    Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
    ```

## <a name="updating-retention-labels-and-their-policies"></a>Opdatering af opbevaringsmærkater og deres politikker

For politikker for automatisk anvendelse af opbevaringsmærkater, der er konfigureret til følsomme oplysninger, nøgleord eller søgbare egenskaber, eller et match for klassificeringer, der kan oplæres: Når der allerede anvendes en opbevaringsmærkat fra politikken på indhold, anvendes der automatisk en ændring i konfigurationen af den valgte mærkat og politik for dette indhold ud over det indhold, der netop er identificeret.

For politikker for automatisk anvendelse af opbevaringsmærkater, der er konfigureret for vedhæftede filer i skyen: Da denne politik gælder for nyligt delte filer i stedet for eksisterende filer, anvendes en ændring i konfigurationen af det valgte navn og den valgte politik kun for nyligt delt indhold.

Nogle indstillinger kan ikke ændres, når mærkaten eller politikken er oprettet og gemt, herunder:
- Navne på opbevaringsmærkater og deres politikker, omfangstypen (adaptiv eller statisk) og opbevaringsindstillingerne undtagen opbevaringsperioden. Du kan dog ikke ændre opbevaringsperioden, når opbevaringsperioden er baseret på, hvornår elementer blev mærket.
- Indstillingen til at markere elementer som en post.

### <a name="deleting-retention-labels"></a>Sletter opbevaringsmærkater

Du kan slette opbevaringsmærkater, der i øjeblikket ikke er inkluderet i nogen politikker for opbevaringsmærkater, som ikke er konfigureret til hændelsesbaseret opbevaring, eller markere elementer som lovmæssige poster.

For opbevaringsmærkater, som du kan slette, hvis de er blevet anvendt på elementer, mislykkes sletningen, og du får vist et link til indholdsoversigten for at identificere de navngivne elementer.

Det kan dog tage op til to dage, før indholdsoversigten viser de elementer, der er forsynet med mærkater. I dette scenarie kan opbevaringsmærkaten blive slettet uden at vise dig linket til Indholdsoversigt.

## <a name="locking-the-policy-to-prevent-changes"></a>Låsning af politikken for at forhindre ændringer

Hvis du har brug for at sikre, at ingen kan slå politikken fra, slette politikken eller gøre den mindre restriktiv, skal du se [Brug bevarelseslås til at begrænse ændringer af opbevaringspolitikker og politikker for opbevaringsmærkater](retention-preservation-lock.md).

## <a name="next-steps"></a>Næste trin

Som en hjælp til at spore de mærkater, der anvendes fra politikker for automatisk mærkning:

- [Overvågning af opbevaringsmærkater](retention.md#monitoring-retention-labels)
- [Brug af indholdssøgning til at finde alt indhold med en bestemt opbevaringsmærkat](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label)
- [Overvågningsopbevaringshandlinger](retention.md#auditing-retention-actions)

Se [Brug opbevaringsmærkater til at administrere livscyklussen for dokumenter, der er gemt i SharePoint](auto-apply-retention-labels-scenario.md) i et eksempelscenarie, hvor der bruges en politik for automatisk anvendelse af opbevaringsmærkat med administrerede egenskaber i SharePoint, og hændelsesbaseret opbevaring for at starte opbevaringsperioden.
