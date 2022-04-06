---
title: Anvend automatisk et opbevaringsnavn for at bevare eller slette indhold
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
description: Opret opbevaringspolitikker for automatisk mærkning, så du automatisk kan anvende etiketter for at bevare det, du har brug for, og slette det, du ikke har brug for
ms.openlocfilehash: 2d141ef349c456b9e8397ea1c96a4e450eaa73fc
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500432"
---
# <a name="automatically-apply-a-retention-label-to-retain-or-delete-content"></a>Anvend automatisk et opbevaringsnavn for at bevare eller slette indhold

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Dette scenarie understøttes [ikke for](records-management.md#records) lovgivningsposter eller standardetiketter til en organisationsstruktur som f.eks. et dokumentsæt eller et bibliotek i SharePoint eller en mappe i Exchange. Disse scenarier kræver en [publiceret opbevaringsetiketpolitik](create-apply-retention-labels.md).

En af de mest effektive funktioner i [opbevaringsmærkater](retention.md) er muligheden for at anvende dem automatisk på indhold, der opfylder de angivne betingelser. I dette tilfælde behøver personer i din organisation ikke at anvende opbevaringsmærkaterne. Microsoft 365 gør arbejdet for dem.
  
Automatisk anvendelse af opbevaringsmærkater er effektive, fordi:
  
- Du behøver ikke at oplære dine brugere i alle dine klassificeringer.
    
- Du behøver ikke at stole på, at brugerne klassificerer alt indhold korrekt.
    
- Brugere behøver ikke længere at kende til politikker for datastyring – de kan fokusere på deres arbejde.
    
Du kan anvende [opbevaringsmærkater](classifier-get-started-with.md) på indhold automatisk, når der ikke allerede er anvendt en opbevaringsetiket til indholdet, og det indeholder følsomme oplysninger, nøgleord eller søgbare egenskaber eller et match til trænbare klassificeringer. I forhåndsvisning kan du også automatisk anvende en opbevaringsetiket til vedhæftede skybaserede filer, der er gemt i SharePoint eller OneDrive.

> [!TIP]
> Brug søgbare egenskaber til at [identificere Teams mødeoptagelser og](#microsoft-teams-meeting-recordings) [elementer, hvor følsomhedsmærkatet er anvendt](#identify-files-and-emails-that-have-a-sensitivity-label).

Processerne til automatisk at anvende en opbevaringsetiket baseret på disse betingelser:

![Diagram over roller og opgaver til automatisk anvendelse af navne.](../media/32f2f2fd-18a8-43fd-839d-72ad7a43e069.png)

Brug følgende fremgangsmåde for de to administratortrin.

> [!NOTE]
> Autopolitikker anvender mærkning på tjenestesiden med betingelser til automatisk at anvende opbevaringsnavne på elementer. Du kan også automatisk anvende en opbevaringsetiket med en etiketpolitik, når du gør følgende: 
>
> - Anvend en opbevaringsetiket på en dokumentforståelsesmodel SharePoint Syntex
> - Anvend en standardopbevaringsetiket til SharePoint og Outlook
> - Anvend en opbevaringsetiket på mail ved hjælp Outlook regler
>
> For disse scenarier skal du se [Publicere opbevaringsnavne og anvende dem i apps](create-apply-retention-labels.md).

## <a name="before-you-begin"></a>Før du begynder

Den globale administrator i organisationen har fuld tilladelse til at oprette og redigere opbevaringsnavne og deres politikker. Hvis du ikke logger på som global administrator, kan du se tilladelsesoplysningerne [til](get-started-with-records-management.md#permissions) datastyring eller [informationsstyring](get-started-with-information-governance.md#permissions-for-retention-policies-and-retention-labels) afhængigt af den løsning, du bruger.

Sørg for, at du [har oprettet de opbevaringsnavne](file-plan-manager.md#create-retention-labels) , du vil anvende på elementer.

## <a name="how-to-create-an-auto-apply-retention-label-policy"></a>Sådan oprettes en automatisk opbevaringsetiketpolitik

Beslut før du opretter din politik for opbevaringsetiket, om **den vil være tilpasset** eller **statisk**. Få mere at vide under [Tilpasnings- eller statiske politikomfang for opbevaring](retention.md#adaptive-or-static-policy-scopes-for-retention). Hvis du beslutter dig for at bruge en tilpasset politik, skal du oprette et eller flere tilpassede områder, før du opretter din politik for opbevaringsetiket og derefter vælge dem under processen med at oprette opbevaringsetiketpolitik. Du kan finde en vejledning [i Konfigurationsoplysninger for adaptive områder](retention-settings.md#configuration-information-for-adaptive-scopes).

Når du opretter en automatisk anvendelsespolitik, vælger du en opbevaringsetiket, der automatisk skal anvendes på indhold, ud fra de betingelser, du angiver.

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com/) du gå til en af følgende placeringer:
    
    - Hvis du bruger datastyring:
        - **Løsninger** >  **Fanen > >** **datastyring under** fanen Etiketpolitikker > **anvende en etiket automatisk**
    
    - Hvis du bruger informationsstyring:
        - **Løsninger** >  **Styring af oplysninger** >  **Fanen Etiketpolitikker** > **automatisk anvendelse af en etiket**
    
    Kan du ikke umiddelbart se din løsning i navigationsruden? Vælg først **Vis alle**.

2. Angiv et navn og en beskrivelse til denne politik for automatisk mærkatering, og vælg derefter **Næste**.

3. Vælg **en af de tilgængelige betingelser under Vælg den type** indhold, du vil anvende denne etiket på. Du kan finde flere oplysninger om valgmulighederne i [afsnittet Konfigurer betingelser for automatisk anvendelse af opbevaringsetiketter](#configuring-conditions-for-auto-apply-retention-labels) på denne side.

4. For siden **Vælg den type opbevaringspolitik** , der skal oprettes skal du vælge **Tilpasset** eller **Statisk afhængigt** af det valg, du har foretaget fra vejledningen [Før du begynder](#before-you-begin) . Hvis du ikke allerede har oprettet tilpassede områder, kan du vælge Tilpasset, men  da der ikke vil være nogen tilpassede områder at vælge, kan du ikke afslutte guiden med denne indstilling.

5. Afhængigt af det valgte område:
    
    - Hvis du vælger **Tilpasset**: På siden Vælg  tilpassede politikomfang og -placeringer skal du vælge Tilføj områder  og vælge et eller flere tilpassede områder, der er blevet oprettet. Vælg derefter en eller flere placeringer. De placeringer, du kan vælge, afhænger af de tilføjede [omfangstyper](retention-settings.md#configuration-information-for-adaptive-scopes) . Hvis du f.eks. kun har tilføjet en omfangstype af **bruger, kan** du vælge Exchange **,** men ikke SharePoint **websteder**. 
    
    - Hvis du vælger **Statisk**: På **siden Vælg placeringer** skal du slå en placering til eller fra. For hver placering kan du lade den være som standard for at [anvende politikken](retention-settings.md#a-policy-that-applies-to-entire-locations) på hele placeringen, eller du [kan angive omfatter og udelader](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions)
    
    Du kan finde oplysninger om valgmulighederne for [placeringer under Placeringer](retention-settings.md#locations).

6. Følg instruktionerne i guiden for at vælge en opbevaringsetiket, og gennemse og indsend derefter dine konfigurationsvalg.

Hvis du vil redigere en eksisterende opbevaringsetiketpolitik (politiktypen er Anvend **automatisk), skal** du markere den  og derefter vælge indstillingen Rediger for at starte **konfigurationen Rediger opbevaringspolitik**.

Når indhold er navngivet ved hjælp af en automatisk anvendelse af etiketpolitik, kan den anvendte etiket ikke fjernes automatisk eller ændres ved at ændre indholdet eller politikken eller ved en ny automatisk anvendelse af etiketpolitik. Du kan finde flere oplysninger [under Kun én opbevaringsetiket ad gangen](retention.md#only-one-retention-label-at-a-time).

> [!NOTE]
> En politik for automatisk anvendelse af opbevaringsetiket vil aldrig erstatte en eksisterende opbevaringsmærkat, der anvendes på indhold. Hvis du vil ændre navn på indhold ved hjælp af de betingelser, du konfigurerer, skal du manuelt fjerne den aktuelle opbevaringsetiket fra eksisterende indhold.

### <a name="configuring-conditions-for-auto-apply-retention-labels"></a>Konfiguration af betingelser for automatisk anvendelse af opbevaringsnavne

Du kan anvende opbevaringsnavne på indhold automatisk, når indholdet indeholder:

- [Bestemte typer af følsomme oplysninger](#auto-apply-labels-to-content-with-specific-types-of-sensitive-information)

- [Specifikke nøgleord eller søgbare egenskaber, der svarer til en forespørgsel, du opretter](#auto-apply-labels-to-content-with-keywords-or-searchable-properties)

- [Et match til klassekammerater, der kan trænes](#auto-apply-labels-to-content-by-using-trainable-classifiers)

Eller du kan automatisk anvende opbevaringsmærkater på nyligt delte [skybaserede vedhæftede filer](#auto-apply-labels-to-cloud-attachments).

Når du konfigurerer opbevaringsnavne til automatisk anvendelse baseret på følsomme oplysninger, nøgleord eller søgbare egenskaber eller søgbare klassificeringer, kan du bruge følgende tabel til at identificere, hvornår opbevaringsmærkater kan anvendes automatisk.

Exchange:

|Betingelse|Varer under transport (sendt eller modtaget) |Eksisterende elementer (data i rest)|
|:-----|:-----|:-----|
|Følsomme oplysningstyper – indbygget| Ja | Nej |
|Typer af følsomme oplysninger – brugerdefineret| Ja | Nej |
|Specifikke nøgleord eller søgbare egenskaber| Ja |Ja |
|Trænbare klassificeringer| Ja | Ja (kun sidste seks måneder) |

SharePoint og OneDrive:

|Betingelse|Nye eller ændrede elementer |Eksisterende elementer |
|:-----|:-----|:-----|
|Følsomme oplysningstyper – indbygget| Ja | Ja |
|Typer af følsomme oplysninger – brugerdefineret| Ja | Nej |
|Specifikke nøgleord eller søgbare egenskaber| Ja |Ja |
|Trænbare klassificeringer| Ja | Ja (kun sidste seks måneder) |

Desuden understøttes SharePoint, der er i kladde, eller som aldrig er blevet publiceret, ikke i dette scenarie.

#### <a name="auto-apply-labels-to-content-with-specific-types-of-sensitive-information"></a>Anvend automatisk navne på indhold med bestemte typer af følsomme oplysninger

> [!IMPORTANT]
> For mails, du automatisk anvender ved at identificere følsomme oplysninger, medtages alle postkasser automatisk, hvilket omfatter postkasser fra Microsoft 365 grupper.
> 
> Selvom gruppepostkasser normalt ville være inkluderet ved at vælge **Microsoft 365-grupper-placeringen**, omfatter gruppeplaceringen kun de SharePoint, der er knyttet til en Microsoft 365 gruppe.

Når du opretter politikker for automatisk anvendelse af opbevaringsetiket til følsomme oplysninger, får du vist den samme liste over politikskabeloner, som når du opretter en politik til forebyggelse af datatab (DLP). Hver skabelon er forudkonfigureret til at søge efter bestemte typer af følsomme oplysninger. I følgende eksempel er typerne af følsomme oplysninger fra kategorien Beskyttelse  af personlige oplysninger og dataskabelonen USA Personidentificerbare oplysninger **(PII**):

![Politikskabeloner med typer af følsomme oplysninger.](../media/sensitive-info-configuration.png)

Du kan få mere at vide om typer af følsomhedsoplysninger under [Få mere at vide om typer af følsomme oplysninger](sensitive-information-type-learn-about.md#learn-about-sensitive-information-types). I øjeblikket [understøttes nøjagtige datamatchingsbaserede følsomme](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types) [oplysningstyper](document-fingerprinting.md) og dokument fingeraftryk ikke i dette scenarie.

Når du har valgt en politikskabelon, kan du tilføje eller fjerne typer af følsomme oplysninger, og du kan ændre tillidsniveauet og antallet af forekomster. I det forrige eksempelskærmbillede er disse indstillinger blevet ændret, så et opbevaringsnavn kun anvendes automatisk, når:
  
- Den type af følsomme oplysninger, der registreres, har en matchnøjagtighed (eller tillidsniveau [) på](sensitive-information-type-learn-about.md#more-on-confidence-levels) mindst Mellem **tillid til to** af de følsomme oplysningstyper og **Høj** tillid til én. Mange følsomme oplysningstyper defineres med flere mønstre, hvor et mønster med højere matchnøjagtighed kræver mere bevisførelse (f.eks. nøgleord, datoer eller adresser), mens et mønster med lavere matchnøjagtighed kræver mindre bevis. Jo lavere tillidsniveauet er, jo nemmere er det for indholdet at matche betingelsen, men med mulighederne for flere falske positive.

- Indholdet indeholder mellem 1 og 9 forekomster af disse tre følsomme oplysningstyper. Standardværdien for **til er** **Any**.

Du kan finde flere oplysninger om disse indstillinger i følgende vejledning fra reglerne for justering af DLP-dokumentation for at [gøre dem nemmere eller sværere at matche](data-loss-prevention-policies.md#tuning-rules-to-make-them-easier-or-harder-to-match).

> [!IMPORTANT]
> Typerne af følsomme oplysninger har to forskellige måder at definere parametrene for det maksimale antal entydige forekomster på. Du kan få mere at vide under [Forekomstantal understøttede værdier for SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

Overvej følgende, når du bruger typer af følsomme oplysninger til automatisk at anvende opbevaringsnavne:

- Hvis du bruger brugerdefinerede typer af følsomme oplysninger, kan disse ikke automatisk navnmærke eksisterende elementer i SharePoint og OneDrive.

- For mails kan du ikke vælge bestemte modtagere, der skal medtages eller udelades. kun **indstillingen Alle modtagere understøttes**, og i denne konfiguration er det kun postkasser fra Microsoft 365 grupper. 

#### <a name="auto-apply-labels-to-content-with-keywords-or-searchable-properties"></a>Anvend navne automatisk på indhold med nøgleord eller søgbare egenskaber

Du kan anvende navne automatisk på indhold ved hjælp af en forespørgsel, der indeholder bestemte ord, udtryk eller værdier i søgbare egenskaber. Du kan afgrænse forespørgslen ved hjælp af søgeoperatorer som OG, ELLER og IKKE.

![Forespørgselseditor.](../media/new-retention-query-editor.png)

Du kan finde flere oplysninger om den forespørgselssyntaksen, der bruger KQL (Keyword Query Language), i [Syntaksreference til Sprog til nøgleordsforespørgsel (KQL](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference)).

Forespørgselsbaserede politikker til automatisk anvendelse bruger det samme søgeindeks som eDiscovery-indholdssøgning til at identificere indhold. Du kan finde flere oplysninger om de søgbare egenskaber, du kan bruge, under [Nøgleordsforespørgsler og søgebetingelser for indholdssøgning](keyword-queries-and-search-conditions.md).

Her er nogle ting, du skal overveje, når du bruger nøgleord eller søgbare egenskaber til automatisk at anvende opbevaringsnavne:

- For SharePoint understøttes gennemsøgte egenskaber og brugerdefinerede egenskaber ikke for disse KQL-forespørgsler, og du må kun bruge foruddefinerede administrerede egenskaber til dokumenter. Du kan dog bruge tilknytninger på lejerniveau med de foruddefinerede administrerede egenskaber, der er aktiveret som afgrænsninger som standard (RefinableDate00-19, RefinableString00-99, RefinableInt00-49, RefinableDecimals00-09 og RefinableDouble00-09). Få mere at vide under Oversigt over gennemsøgte og administrerede egenskaber [i SharePoint Server](/SharePoint/technical-reference/crawled-and-managed-properties-overview), og du kan finde en vejledning i [Oprette en ny administreret egenskab](/sharepoint/manage-search-schema#create-a-new-managed-property).

- Hvis du tilknytter en brugerdefineret egenskab til en af afgrænsningens egenskaber, skal du vente 24 timer, før du bruger den i KQL-forespørgslen for en opbevaringsetiket.

- Selvom SharePoint administrerede egenskaber kan omdøbes ved hjælp af aliasser, skal du ikke bruge disse til KQL-forespørgsler i dine etiketter. Angiv altid det faktiske navn på den administrerede egenskab, f.eks. "RefinableString01".

- Hvis du vil søge efter værdier, der indeholder mellemrum eller specialtegn, skal du bruge dobbelte anførselstegn (`" "`) til at indeholde udtrykket, f.eks. `subject:"Financial Statements"`.

- Brug egenskaben *DocumentLink i* stedet for Sti *til at* matche et element baseret på dets URL-adresse. 

- Suffikssøgninger med jokertegn ( `*cat`f.eks. ) eller understrengssøgninger med jokertegn ( `*cat*`f.eks. ) understøttes ikke. Dog understøttes præfikssøgninger med jokertegn (f.eks `cat*`. ).

- Vær opmærksom på, at delvist indekserede elementer kan være ansvarlige for ikke at mærke elementer, som du forventer, eller at etiketelementer, som du forventer at blive udeladt af mærkningen, når du bruger operatoren NOT. Du kan finde flere oplysninger under [Delvist indekserede elementer i Indholdssøgning](partially-indexed-items-in-content-search.md).


Eksempler på forespørgsler:

| Arbejdsbelastning | Eksempel |
|:-----|:-----|
|Exchange   | `subject:"Financial Statements"` |
|Exchange   | `recipients:garthf@contoso.com` |
|SharePoint | `contenttype:document` |
|SharePoint | `site:https://contoso.sharepoint.com/sites/teams/procurement AND contenttype:document`|
|Exchange eller SharePoint | `"customer information" OR "private"`|

Mere komplekse eksempler:

Følgende forespørgsel til en SharePoint identificerer Word-dokumenter Excel regneark, når disse filer indeholder nøgleordene **adgangskode, adgangskoder** eller **pw**: 

```
(password OR passwords OR pw) AND (filetype:doc* OR filetype:xls*)
```

Følgende forespørgsel til en Exchange identificerer et Word-dokument eller en PDF-fil, der indeholder ordet **nda** eller udtrykket  aftale om hemmeligholdelse, når disse dokumenter er vedhæftet en mail:

```
(nda OR "non disclosure agreement") AND (attachmentnames:.doc* OR attachmentnames:.pdf)
```

Følgende forespørgsel til en SharePoint identificerer dokumenter, der indeholder et kreditkortnummer: 

```
sensitivetype:"credit card number"
```

Følgende forespørgsel indeholder nogle typiske nøgleord, der kan hjælpe med at identificere dokumenter eller mails, der indeholder juridisk indhold:

```
ACP OR (Attorney Client Privilege*) OR (AC Privilege)
```

Følgende forespørgsel indeholder typiske nøgleord, der hjælper med at identificere dokumenter eller mails til HR- ressourcer: 

```
(resume AND staff AND employee AND salary AND recruitment AND candidate)
```

Bemærk, at det sidste eksempel anvender den bedste fremgangsmåde, der altid omfatter operatorer mellem nøgleord. Et mellemrum mellem nøgleord (eller to egenskab:værdi-udtryk) er det samme som at bruge OG. Ved altid at tilføje operatorer er det nemmere at se, at denne eksempelforespørgsel kun identificerer indhold, der indeholder alle disse nøgleord, i stedet for indhold, der indeholder nogle af nøgleordene. Hvis du har i sinde at identificere indhold, der indeholder nogle af nøgleordene, skal du angive ELLER i stedet for OG. Som dette eksempel viser, er det nemmere at fortolke forespørgslen korrekt, når du altid angiver operatorerne. 

##### <a name="microsoft-teams-meeting-recordings"></a>Microsoft Teams mødeoptagelser

> [!NOTE]
> Muligheden for at bevare og Teams mødeoptagelser fungerer ikke, før optagelser gemmes på en OneDrive eller SharePoint. Få mere at vide under [Brug OneDrive for Business og SharePoint Online eller Stream til mødeoptagelser](/MicrosoftTeams/tmr-meeting-recording-change).

For at Microsoft Teams om mødeoptagelser, der er gemt på brugernes OneDrive konti eller i SharePoint, skal du angive følgende for **Editor til nøgleordsforespørgsel**:

```
ProgID:Media AND ProgID:Meeting
```

Som oftest gemmes mødeoptagelser i OneDrive. Men ved kanalmøder gemmes de i SharePoint.

##### <a name="identify-files-and-emails-that-have-a-sensitivity-label"></a>Identificer filer og mails, der har en følsomhedsmærkat

For at identificere filer i SharePoint eller OneDrive og Exchange, der har en bestemt følsomhedsmærkat anvendt, skal [](sensitivity-labels.md) du angive følgende for **Keyword-forespørgselseditoren**:

```
InformationProtectionLabelId:<GUID>
```

For at finde GUID'et skal [du bruge Get-Label-cmdlet'en](/powershell/module/exchange/get-label) [fra Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell):

````powershell
Get-Label | Format-Table -Property DisplayName, Name, Guid
````

#### <a name="auto-apply-labels-to-content-by-using-trainable-classifiers"></a>Anvend navne automatisk på indhold ved hjælp af trænbare klassificeringer

Når du vælger indstillingen for en trænbar klassificering, kan du vælge en eller flere af de færdigtrænede eller brugerdefinerede klassificeringer, der kan trænes:

![Vælg en klassificering, der kan trænes.](../media/retention-label-classifers.png)

> [!CAUTION]
> Vi fraråder den **præ-uddannede classifier** for stødende sprog, fordi den har produceret et stort antal falske positive. Brug ikke denne klassificering, og hvis du bruger den i øjeblikket, anbefaler vi, at du flytter dine forretningsprocesser væk fra den og i stedet bruger de målrettede **,** **profanity**- og trusselsbaserede klassificeringer.

For automatisk at anvende en etiket ved hjælp af denne indstilling skal SharePoint websteder og postkasser have mindst 10 MB data.

Du kan finde flere oplysninger om klassificeringer, der kan trænes, [i Få mere at vide om klassificerede klasser, der kan trænes](classifier-learn-about.md).

> [!TIP]
> Hvis du bruger klassificeringer, der kan trænes som Exchange, kan du se Sådan omskolinger du [en klassificering i indholdsstifinder](classifier-how-to-retrain-content-explorer.md).

Overvej dette, når du bruger klassificeringer, der kan trænes, til automatisk at anvende opbevaringsmærkater:

- Du kan ikke automatisk navnmærke elementer, SharePoint OneDrive, der er ældre end seks måneder.

#### <a name="auto-apply-labels-to-cloud-attachments"></a>Anvend automatisk navne på vedhæftede filer i skyen

> [!NOTE]
> Denne indstilling udrulles gradvist i eksempelvisning og kan ændres uden ændringer.

Du skal muligvis bruge denne indstilling, hvis du skal registrere og bevare alle kopier af filer i din lejer, som sendes via kommunikation af brugere. Du bruger denne indstilling sammen med opbevaringspolitikker til selve kommunikationstjenesterne, Exchange og Teams.

> [!IMPORTANT]
> Når du vælger en etiket, der skal bruges til automatisk anvendelse af opbevaringsmærkater til vedhæftede filer i skyen, skal du sikre dig, at indstillingen for opbevaring af etiketter **Start** opbevaringsperioden baseret på, er Hvornår elementer blev **mærket**.

Vedhæftede skyfiler, også kaldet moderne vedhæftede filer, er en delingsmekanisme, der bruger integrerede links til filer, der er gemt i skyen. De understøtter centraliseret lagring af delt indhold med samarbejdsfordele, f.eks. versionsstyring. Vedhæftede skybaserede filer er ikke vedhæftede kopier af en fil eller et URL-tekstlink til en fil. Det kan være nyttigt at se de visuelle tjeklister for understøttede vedhæftede skybaserede filer [i Outlook](/office365/troubleshoot/retention/cannot-retain-cloud-attachments#cloud-attachments-in-outlook) og [Teams](/office365/troubleshoot/retention/cannot-retain-cloud-attachments#cloud-attachments-in-teams).

Når du vælger at anvende en opbevaringsmærkat på vedhæftede filer i skyen, oprettes der en kopi af den pågældende fil på delings tidspunkt for overholdelse af regler og standarder. Din valgte opbevaringsmærkat anvendes derefter på den kopi, der derefter kan identificeres ved hjælp af eDiscovery. Brugere er ikke opmærksomme på den kopi, der er gemt i biblioteket til opbevaring af dokumenter. Opbevaringsnavnet anvendes ikke på selve meddelelsen eller på den oprindelige fil.

Hvis filen ændres og deles igen, gemmes en ny kopi af filen som en ny version i biblioteket til opbevaring af dokumenter. Du kan finde flere oplysninger, herunder hvorfor du **skal bruge indstillingen** Når elementer blev mærket etiket under Sådan fungerer opbevaring [med vedhæftede filer i skyen](retention-policies-sharepoint.md#how-retention-works-with-cloud-attachments).

De vedhæftede filer i skyen, der understøttes til denne indstilling, er filer som f.eks. dokumenter, videoer og billeder, der er gemt i SharePoint og OneDrive. For Teams understøttes vedhæftede filer fra skyen i chatmeddelelser samt standardkanaler og private kanaler. Vedhæftede skybaserede filer, der deles via mødeinvitationer og apps, Teams eller Outlook ikke understøttes. Vedhæftede filer i skyen skal deles af brugere. vedhæftede filer fra skyen, der sendes via botter, understøttes ikke.

Selvom det ikke er påkrævet for denne indstilling, anbefaler vi, at du sikrer, at versionsversioner er aktiveret for dine SharePoint-websteder og OneDrive-konti, så den delte version kan registreres korrekt. Hvis versionsversioner ikke er aktiveret, bevares den senest tilgængelige version. Dokumenter, der er i kladde, eller som aldrig er blevet publiceret, understøttes ikke.

Når du vælger en etiket, der skal bruges til automatisk anvendelse af opbevaringsmærkater til vedhæftede filer i skyen, skal du sørge for, at indstillingen for opbevaring af etiketter Starter opbevaringsperioden baseret på, er Hvornår elementer blev **mærket**. 

Når du konfigurerer placeringerne for denne indstilling, kan du vælge:

- **SharePoint websteder** til delte filer, der er gemt SharePoint kommunikationswebsteder, teamwebsteder, der ikke er forbundet Microsoft 365 grupper, og klassiske websteder. 
- **Microsoft 365-grupper** for delte filer, der er gemt på teamwebsteder, der er forbundet Microsoft 365 grupper.
- **OneDrive konti** for delte filer, der er gemt i OneDrive.

Du skal oprette separate opbevaringspolitikker, hvis du vil bevare eller slette de oprindelige filer, mails eller Teams meddelelser.

> [!NOTE]
> Hvis du vil bevare vedhæftede filer i skyen til at udløbe på samme tid som de meddelelser, der indeholdt dem, skal du konfigurere opbevaringsnavnet til at have den samme opbevaringsmærkat og derefter slette handlinger og tidsindstillinger som dine opbevaringspolitikker for Exchange og Teams.

Overvej dette, når du automatisk anvender opbevaringsnavne på vedhæftede skybaserede filer:

- Kun nyligt delte vedhæftede skybaserede filer bliver automatisk mærket til opbevaring.

- Vedhæftede skybaserede filer, der Teams og Outlook, understøttes ikke.

- Følgende elementer understøttes ikke som vedhæftede skybaserede filer, der kan bevares:
    - SharePoint websteder, sider, lister, formularer, mapper, dokumentsæt og OneNote sider.
    - Filer, der deles af brugere, der ikke har adgang til disse filer.
    - Filer, der er blevet slettet, før den vedhæftede sky er sendt. Dette kan ske, hvis en bruger kopierer og indsætter en tidligere delt vedhæftet fil fra en anden meddelelse, uden først at bekræfte, at filen stadig er tilgængelig. Eller en person videresender en gammel meddelelse, når filen nu er blevet slettet.
    - Filer, der deles af gæster eller brugere uden for organisationen.
    - Filer i kladdemails og meddelelser, der ikke sendes.
    - Tomme filer.

## <a name="how-long-it-takes-for-retention-labels-to-take-effect"></a>Hvor lang tid det tager, før opbevaringsetiketter træder i kraft

Når du automatisk anvender opbevaringsnavne baseret på følsomme oplysninger, nøgleord, søgbare egenskaber eller op til op til syv dage, før opbevaringsetiketterne er anvendt:
  
![Diagram over, hvornår automatisk anvendelse af navne træder i kraft.](../media/retention-labels-autoapply-timings.png)

Hvis de forventede etiketter ikke vises efter syv dage, skal du markere **Status** for automatisk anvendelse af politikken ved at vælge den på siden Etiketpolitikker  i Overholdelsescenter. Hvis du får vist statussen Fra **(fejl),** og i oplysningerne om placeringerne vises en meddelelse om, at det tager længere tid end forventet at implementere politikken (for SharePoint) eller prøve at implementere politikken igen (for OneDrive), kan du prøve at køre kommandoen [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell for at prøve politikdistributionen igen:

1. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Kør følgende kommando:
    
    ```PowerShell
    Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
    ```

## <a name="updating-retention-labels-and-their-policies"></a>Opdatering af opbevaringsnavne og deres politikker

I forbindelse med politikker for automatisk anvendelse af opbevaringsmærkater, der er konfigureret til følsomme oplysninger, nøgleord eller søgbare egenskaber eller et match for trænbare klassificeringer: Når der allerede er anvendt et opbevaringsnavn fra politikken på indhold, anvendes der automatisk en ændring i konfigurationen af den valgte etiket og politik på dette indhold ud over indhold, der er identificeret for nyligt.

I forbindelse med politikker for automatisk anvendelse af opbevaringsmærkater, der er konfigureret til vedhæftede filer i skyen: Da denne politik gælder for nyligt delte filer i stedet for eksisterende filer, vil en ændring i konfigurationen af den valgte etiket og politik kun automatisk blive anvendt på nyligt delt indhold.

Nogle indstillinger kan ikke ændres, efter etiketten eller politikken er oprettet og gemt, hvilket omfatter:
- Navne på opbevaringsnavne og deres politikker, omfangstypen (tilpasset eller statisk) og opbevaringsindstillingerne undtagen opbevaringsperioden. Du kan dog ikke ændre opbevaringsperioden, når en opbevaringsperiode er baseret på, hvornår elementerne blev mærket.
- Muligheden for at markere elementer som en post.

### <a name="deleting-retention-labels"></a>Sletning af opbevaringsnavne

Du kan slette opbevaringsnavne, der i øjeblikket ikke er medtaget i nogen opbevaringsetiketpolitikker, der ikke er konfigureret til hændelsesbaseret opbevaring, eller markere elementer som lovmæssige poster.

For opbevaringsetiketter, som du kan slette, hvis de er blevet anvendt på elementer, mislykkes sletningen, og du kan se et link til indholdsstifinder til at identificere de mærkede elementer.

Det kan dog tage op til to dage, før indholdsstifinder viser de elementer, der er mærket. I dette scenarie kan opbevaringsnavnet slettes uden at vise dig linket til indholdsstifinder.

## <a name="locking-the-policy-to-prevent-changes"></a>Låse politikken for at forhindre ændringer

Hvis du har brug for at sikre, at ingen kan deaktivere politikken, slette politikken eller gøre den mindre restriktiv, skal du se Brug Preservation Lock til at begrænse ændringer i opbevaringspolitikker og politikker for [opbevaringsmærkater](retention-preservation-lock.md).

## <a name="next-steps"></a>Næste trin

Sådan kan du holde styr på de etiketter, der anvendes fra politikkerne for automatisk mærkatning:

- [Overvågning af opbevaringsnavne](retention.md#monitoring-retention-labels)
- [Brug af indholdssøgning til at finde alt indhold med en bestemt opbevaringsmærkat](retention.md#using-content-search-to-find-all-content-with-a-specific-retention-label)
- [Overvågning af opbevaringshandlinger](retention.md#auditing-retention-actions)

Se Brug opbevaringsnavne til at administrere livscyklussen for dokumenter, der er gemt i [SharePoint](auto-apply-retention-labels-scenario.md) for et eksempelscenarie, der bruger en automatisk anvendelse af opbevaringsetiketpolitik med administrerede egenskaber i SharePoint og hændelsesbaseret opbevaring for at starte opbevaringsperioden.
