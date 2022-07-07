---
title: Få mere at vide om standardmærkater og -politikker til beskyttelse af dine data
f1.keywords:
- CSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
description: Få mere at vide om standardmærkater og -politikker for Microsoft Purview Information Protection til at klassificere og beskytte følsomt indhold.
ms.openlocfilehash: 4afa6cfa281fa260c71f10f34c06ab1cbc14457f
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66663080"
---
# <a name="default-labels-and-policies-to-protect-your-data"></a>Standardmærkater og -politikker til beskyttelse af dine data

>*[Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Berettigede kunder kan aktivere standardmærkater og -politikker for Microsoft Purview Information Protection: 

- Følsomhedsmærkater og en politik for følsomhedsmærkater
- Automatisk mærkning på klientsiden
- Automærkater på tjenestesiden
- DLP-politikker (forebyggelse af datatab) for Teams og enheder

Disse standardkonfigurationer hjælper dig med hurtigt at komme i gang med Microsoft Purview Information Protection til Microsoft 365. Du kan bruge dem, som de er, foretage nogle få ændringer eller tilpasse dem fuldt ud, så de passer bedre til dine forretningsbehov. 

Berettigelse omfatter kunder, der har en [gratis prøveversion til Microsoft Purview](compliance-easy-trials.md), og nogle kunder, der allerede har en Microsoft 365 E5 plan:

- **Nye kunder**: Hvis du har haft Microsoft Purview i mindre end 30 dage, kan din lejer aktivere alle de angivne standardkonfigurationer. Du kan altid deaktivere, fjerne eller redigere dem.

- **Eksisterende kunder**: Hvis du har haft Microsoft Purview i mere end 30 dage, kan du aktivere standardkonfigurationerne, hvis du endnu ikke har konfigureret en tilsvarende:

    | Standardkonfiguration| Svarer |
    |:-----|:-----|
    |Følsomhedsmærkater og en politik for følsomhedsmærkater | Publicerede følsomhedsmærkater |
    |Automatisk mærkning på klientsiden | En eller flere følsomhedsmærkater, der er konfigureret til automatisk at anvende (eller anbefale til brugere) i Office-apps|
    |Automærkater på tjenestesiden | Mindst én politik for automatisk mærkning, der er slået til|
    |DLP til Teams | Mindst én DLP-politik for Teams|
    |DLP til enheder | Mindst én DLP-politik for enheder|

## <a name="activate-the-default-labels-and-policies"></a>Aktivér standardnavne og -politikker

Sådan henter du disse forudkonfigurerede mærkater og politikker: 

1. Vælg **Beskyttelse af løsningsoplysninger** >  [i Microsoft Purview-compliance-portal](https://compliance.microsoft.com/)
    
    Hvis du ikke kan se denne indstilling med det samme, skal du først vælge **Vis alle** i navigationsruden. 
    
2. Hvis du er berettiget til Microsoft Purview Information Protection standardmærkater og -politikker, får du vist følgende oplysninger, hvor du kan aktivere standardmærkater og -politikker. Eksempel:
    
    :::image type="content" alt-text="Microsoft Purview Information Protection aktivering af forudkonfigurerede mærkater og politikker." source="../media/mip-preconfigured.png" lightbox="../media/mip-preconfigured.png":::
    
    Hvis du ikke kan se disse oplysninger, der vises med aktiveringsindstillingen, er du i øjeblikket ikke berettiget til automatisk oprettelse af følsomhedsmærkater og politikker. Du kan prøve at vende tilbage senere for at se, om denne status er ændret, eller du kan bruge de efterfølgende indstillingsoplysninger til manuelt at oprette de samme mærkater og politikker.

3. Aktivér nu følsomhedsmærkater for SharePoint og OneDrive. Dette trin er en forudsætning for at bruge følsomhedsmærkater i Office på internettet og politikker for automatisk mærkning for SharePoint og OneDrive.
   
    Brug følgende banner øverst på fanen Information Protection **Oversigt**, og vælg **Slå til nu**. Hvis du ikke kan se dette banner, er følsomhedsmærkater for SharePoint og OneDrive allerede aktiveret for din lejer.
    
    ![Aktivér følsomhedsmærkater for banneret SharePoint og OneDrive.](../media/turn-on-mip-labels.png)
    
    Du kan finde flere oplysninger om denne funktion under [Aktivér følsomhedsmærkater for Office-filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="default-sensitivity-labels"></a>Standardfølsomhedsmærkater

Når du ikke har følsomhedsmærkater, der er publiceret, opretter vi følgende mærkater for dig:


|Navn|Beskrivelse af mærkat for brugere|Indstillinger|
|-------------------------------|---------------------------|-----------------|
|Personal|Ikke-forretningsrelaterede data, kun til personlig brug.|**Område**: Elementer (fil, mail) <br /><br />**Indholdsmarkering**: Nej<br /><br />**Automatisk mærkning**: Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkning af databasekolonner**: Ingen|
|Offentlige|Forretningsdata, der er specifikt forberedt og godkendt til offentligt forbrug.|**Område**: Elementer (fil, mail) <br /><br />**Indholdsmarkering**: Nej<br /><br />**Automatisk mærkning**: Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkning af databasekolonner**: Ingen|
|Generel|Forretningsdata, der ikke er beregnet til offentligt forbrug. Dette kan dog deles med eksterne partnere efter behov. Eksempler omfatter virksomhedens interne telefonliste, organisationsdiagrammer, interne standarder og de fleste interne kommunikationer.|**Område**: Elementer (fil, mail) <br /><br />**Indholdsmarkering**: Nej<br /><br />**Automatisk mærkning**: Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkning af databasekolonner**: Ingen|
|Generel <br /> \ Alle (ubegrænset)|Organisationsdata, der ikke er beregnet til offentligt forbrug, men som kan deles med eksterne partnere, hvis det er relevant. Eksempler omfatter kundesamtaler, der ikke indeholder følsomme oplysninger eller udgivet marketingmateriale.|**Område**: Elementer (fil, mail) <br /><br />**Indholdsmarkering**: Nej<br /><br />**Automatisk mærkning**: Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkning af databasekolonner**: Ingen|
|Generel <br /> \ Alle medarbejdere (ubegrænset)|Organisationsdata, der ikke er beregnet til offentligt forbrug. Hvis du har brug for at dele dette indhold med eksterne partnere, skal du bekræfte med andre dataejere, at det er OK at dele og derefter ændre etiketten til Generelt \ Alle (ubegrænset) . Eksempler omfatter virksomhedens interne telefonliste, organisationsdiagrammer, interne standarder og de fleste interne kommunikationer.|**Område**: Elementer (fil, mail) <br /><br />**Indholdsmarkering**: Nej<br /><br />**Automatisk mærkning**: Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkning af databasekolonner**: Ingen|
|Fortrolige|Følsomme forretningsdata, der kan beskadige virksomheden, hvis de deles med uautoriserede personer. Eksempler omfatter kontrakter, sikkerhedsrapporter, prognoseoversigter og salgskontodata.|**Område**: Elementer (fil, mail) <br /><br />**Indholdsmarkering**: Nej<br /><br />**Automatisk mærkning**: Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkning af databasekolonner**: Ingen|
|Fortrolige <br /> \ Alle (ubegrænset)|Fortrolige data, der ikke behøver at blive krypteret. Brug denne indstilling med omhyggelig og passende forretningsberettigelse.|Denne etiket er valgt til [automatisk mærkning på klientsiden](#client-side-auto-labeling) og [automatisk mærkning på servicesiden](#service-side-auto-labeling).<br /><br /> **Område**: Elementer (fil, mail) <br /><br />**Indholdsmarkering**: Sidefod: Klassificeret som fortroligt<br /><br />**Automatisk mærkning**: Anbefal, at brugerne anvender mærkaten <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkning af databasekolonner**: Ingen|
|Fortrolige <br /> \ Alle medarbejdere|Fortrolige data, der kræver beskyttelse, hvilket giver alle medarbejdere fulde tilladelser. Dataejere kan spore og tilbagekalde indhold.|Denne etiket er valgt til [automatisk mærkning på klientsiden](#client-side-auto-labeling) og [automatisk mærkning på servicesiden](#service-side-auto-labeling).<br /><br /> **Område**: Elementer (fil, mail) <br /><br />**Kryptering**: Alle brugere og grupper i organisationen: Co-Author<br /><br />**Indholdsmarkering**: Sidefod: Klassificeret som fortroligt<br /><br />**Automatisk mærkning**: Anbefal, at brugerne anvender mærkaten <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkning af databasekolonner**: Ingen |
|Fortrolige <br /> \ Personer, der er tillid til|Fortrolige data, der kan deles med personer, der er tillid til, i og uden for din organisation. Disse personer kan også dele dataene igen efter behov.|**Område**: Elementer (fil, mail) <br /><br />**Kryptering**: Lad brugerne tildele tilladelser: <br /> - Encrypt-Only til Outlook <br />– Spørg brugere i Word, PowerPoint og Excel<br /><br />**Indholdsmarkering**: Sidefod: Klassificeret som fortroligt<br /><br />**Automatisk mærkning**: Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkning af databasekolonner**: Ingen|
|Meget fortroligt|Meget følsomme forretningsdata, der kan beskadige virksomheden, hvis de deles med uautoriserede personer. Eksempler omfatter medarbejder- og kundeoplysninger, adgangskoder, kildekode og forhånds annoncerede regnskaber.|**Område**: Elementer (fil, mail) <br /><br />**Indholdsmarkering**: Vandmærke: MEGET FORTROLIGT<br /><br />**Automatisk mærkning**: Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkning af databasekolonner**: Ingen|
|Meget fortroligt <br /> \ Alle medarbejdere|Meget fortrolige data, der giver alle medarbejdere tilladelse til at få vist, redigere og svare på dette indhold. Dataejere kan spore og tilbagekalde indhold.|**Område**: Elementer (fil, mail) <br /><br />**Kryptering**: Alle brugere og grupper i organisationen: Co-Author<br /><br />**Indholdsmarkering**: Sidefod: Klassificeret som meget fortroligt<br /><br />**Automatisk mærkning**: Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkning af databasekolonner**: Ingen|
|Meget fortroligt <br /> \ Bestemte personer |Meget fortrolige data, der kræver beskyttelse og kun kan ses af de personer, du angiver, og med det tilladelsesniveau, du vælger.|**Område**: Elementer (fil, mail) <br /><br />**Kryptering**: Lad brugerne tildele tilladelser: <br />- Videresend ikke til Outlook <br />– Spørg brugere i Word, PowerPoint og Excel<br /><br />**Indholdsmarkering**: Sidefod: Klassificeret som meget fortroligt<br /><br />**Automatisk mærkning**: Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkning af databasekolonner**: Ingen|

> [!NOTE]
> Navne og beskrivelser er automatisk tilgængelige for følgende landestandarder: amerikansk engelsk, kinesisk (forenklet) og traditionelt, fransk, tysk, italiensk, japansk, koreansk, portugisisk (Brasilien), russisk og spansk.
> 
> Hvis du har brug for flere sprog, kan du angive dine oversættelser [ved hjælp af PowerShell](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages).

Du kan få flere oplysninger om disse konfigurationsindstillinger, og hvad følsomhedsmærkater kan gøre, under [Hvad følsomhedsmærkater kan gøre](sensitivity-labels.md#what-sensitivity-labels-can-do).

Hvis du har brug for at redigere disse standardfølsomhedsmærkater, skal du se [Opret og konfigurer følsomhedsmærkater](create-sensitivity-labels.md#create-and-configure-sensitivity-labels).

## <a name="default-sensitivity-label-policy"></a>Standardpolitik for følsomhedsmærkat

Standardpolitikken for følsomhedsmærkat gør mærkaterne tilgængelige, så brugerne kan begynde at forsyne deres dokumenter og mails med følsomhedsmærkater. Den har følgende konfiguration:

- Publicer standardnavnene til alle brugere i din lejer
- Standardmærkat for **General** \ **All Employees (ubegrænset)** for dokumenter og mails, der ikke er forsynet med mærkater
- Brugerne skal angive en begrundelse for at fjerne en mærkat eller sænke klassificeringen

Du kan få flere oplysninger om disse politikindstillinger og andre politikindstillinger, der er tilgængelige, under [Hvad mærkatpolitikker kan gøre](sensitivity-labels.md#what-label-policies-can-do).

Hvis du har brug for at redigere disse standardpolitikindstillinger, skal du se [Publicer følsomhedsmærkater ved at oprette en mærkatpolitik](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

Når du bruger disse mærkater i Office-apps på Windows, macOS, iOS og Android, kan brugerne se nye mærkater inden for fire timer og inden for én time for Word, Excel og PowerPoint på internettet, når du opdaterer browseren. Det kan dog være nødvendigt at tillade op til 24 timer, før ændringer replikeres til alle apps og tjenester.

## <a name="client-side-auto-labeling"></a>Automatisk mærkning på klientsiden

Standardkonfigurationen for automatisk mærkning på klientsiden anbefaler automatisk, at brugerne anvender en følsomhedsmærkat, når vi registrerer kreditkortnumre i dokumenter eller mails, de arbejder med. Som en anbefaling i stedet for automatisk anvendelse fungerer denne konfiguration som et godt første skridt til fremhævning af indhold og introducerer brugerne til praksis med at forsyne deres dokumenter og mails med mærkater.

Automatisk mærkning på klientsiden fungerer kun for dokumenter og mails, der bruges af Office-apps Word, Excel, PowerPoint og Outlook. 

Standardindstillingen for automatisk mærkning på klientsiden har følgende konfiguration: 

- Hvis der findes 1-9 forekomster af kreditkortnumre i et dokument eller en mail, anbefaler vi, at brugeren anvender følsomhedsmærkaten **Fortroligt** \ **alle (ubegrænset)** 

- Hvis der findes 10 eller flere forekomster af kreditkortnumre i et dokument eller en mail, anbefaler vi, at brugeren anvender følsomhedsmærkaten **Fortroligt** \ **alle medarbejdere** 

> [!NOTE]
> Hvis vi har registreret, at du har publiceret dine egne følsomhedsmærkater, beder vi dig om at vælge en af dine egne mærkater til automatisk mærkning og konfigurere den for dig.

Hvis du vil redigere konfigurationen af automatisk mærkat på klientsiden, skal du se [Sådan konfigurerer du automatisk mærkning for Office-apps](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps).

## <a name="service-side-auto-labeling"></a>Automærkater på tjenestesiden 

Automatisk mærkning på tjenestesiden hjælper med at mærke inaktive følsomme dokumenter og mails under overførsel. Standardpolitikken for automatisk mærkning på tjenestesiden opretter politikker, der kører i simuleringstilstand for dokumenter, der er gemt på alle SharePoint- eller OneDrive-websteder, og alle mails, der sendes via Exchange Online. 

I simuleringstilstand mærkes elementer ikke, før politikken er slået til. Du kan slå politikken til manuelt, eller medmindre du ændrer standardindstillingen, aktiveres politikken automatisk for dig, hvis der ikke er nogen ændringer af politikken inden for et angivet antal dage, fra simuleringen er fuldført.

> [!NOTE]
> Automatisk aktivering af politikker for automatisk mærkning er ny og udrulles gradvist for nye politikker for automatisk mærkning. Du kan muligvis ikke se denne konfiguration med det samme eller for alle politikker.

I de fleste tilfælde er antallet af dage, før en uredigeret politik automatisk aktiveres, 7. Men specifikt for nye kunder fra den 23. juni 2022 er det indledende antal dage 25 og derefter 7, når politikken er redigeret.

I simuleringstilstand kan du se, hvilke elementer der skal mærkes, når politikken er slået til, så du har tillid til mærkatfunktionen, før du udruller politikken til din lejer til faktisk mærkning. 

Standardpolitikkerne for automatisk mærkning på tjenestesiden har følgende konfiguration: 

For alle kunder:

- Hvis der findes 1-9 forekomster af kreditkortnumre i et dokument eller en mail, skal du anvende følsomhedsmærkaten **Fortroligt** \ **alle (ubegrænset)**
    
- Hvis der findes 10 eller flere forekomster af kreditkortnumre i et dokument eller en mail, skal du anvende følsomhedsmærkaten **Fortroligt** \ **alle medarbejdere** 

> [!NOTE]
> Hvis vi har registreret, at du har publiceret dine egne følsomhedsmærkater, beder vi dig om at vælge et af dine egne mærkater til din politik for automatisk mærkning.

For nye kunder fra den 23. juni 2022 og Microsoft 365-lejeren er i området USA:

- Hvis der findes 1-9 forekomster af amerikanske personlige data og fulde navne i et dokument eller en mail, skal du anvende følsomhedsmærkaten **Fortroligt** \ **alle (ubegrænset)**

- Hvis der findes 10 eller flere forekomster af amerikanske personlige data og fulde navne i et dokument eller en mail, skal du anvende følsomhedsmærkaten **Fortroligt** \ **alle medarbejdere** 

Nye kunder fra den 23. juni 2022 har to politikker for automatisk mærkning for hver indstilling. Én politik er for Exchange-placeringen og den anden for SharePoint- og OneDrive-placeringerne. Selvom politikkerne oprettes på samme tid, er simulering ikke slået til med det samme for SharePoint og OneDrive:
- Exchange-placering: Politikken for automatisk mærkning oprettes og starter straks simulering.
- Placeringer for SharePoint og OneDrive: Politikken for automatisk mærkning oprettes, men venter 25 dage, før simulering startes automatisk. Denne forsinkelse giver dig tid til at oprette og gemme filer på disse placeringer. 

Når simuleringen er fuldført, skal du gennemse resultaterne, og hvis du er tilfreds med dem, skal du aktivere politikkerne. Politikkerne udrulles langsomt fra den 23. juni 2022 som standard, hvis de ikke redigeres inden for den angivne tidsperiode (25 dage i første omgang for nye kunder, ellers 7 dage).

Du kan finde flere oplysninger om simuleringstilstand under [Få mere at vide om simuleringstilstand](apply-sensitivity-label-automatically.md#learn-about-simulation-mode).

Hvis du vil redigere politikken for automatisk mærkning på tjenestesiden, skal du se [Sådan konfigurerer du politikker for automatisk mærkning for SharePoint, OneDrive og Exchange](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

## <a name="dlp-for-teams"></a>DLP til Teams

Standard-DLP-politikken for Teams registrerer tilstedeværelsen af kreditkortnumre i alle Teams-chats og kanalmeddelelser. Når disse følsomme oplysninger registreres, får administratorer besked om lav alvorsgrad.

Denne politik er diskret for brugere uden synlige politiktip og ingen blokerede meddelelser, men administratorer vil have poster over de følsomme oplysninger, der deles i disse meddelelser. Hvis det er nødvendigt, kan du redigere indstillingerne for at ændre denne standardkonfiguration.

Hvis du vil se resultaterne af denne politik, skal du bruge [DLP-aktivitetsoversigt.](dlp-learn-about-dlp.md#dlp-activity-explorer)

Hvis du vil redigere DLP-politikken, skal du se [Opret, test og juster en DLP-politik](create-test-tune-dlp-policy.md).

## <a name="dlp-for-devices"></a>DLP til enheder

Standard-DLP-politikken for enheder registrerer tilstedeværelsen af kreditkortnumre på Windows 10 enheder, der er blevet onboardet i Microsoft Purview. Derefter overvåges (blokerer ikke) følgende handlinger: 

- Upload til cloudtjenestedomæner eller adgang af ikke-tilladte browsere

- Kopiér til Udklipsholder, USB eller netværksshare 

- Adgang fra ikke-tilladte apps 

- Udskrive 

- Kopiér eller flyt ved hjælp af en Bluetooth-app, der ikke er tilladt 

- Fjernskrivebord-tjenester 

Hvis indholdet indeholder 10 eller flere forekomster af kreditkort, og en eller flere af de viste aktiviteter registreres, sendes der en besked med mellem alvorsgrad til administratorer.

Denne politik er diskret for brugere uden synlige politiktips og ingen handlinger blokeret, men administratorer vil have poster over alle mistænkelige aktiviteter. Hvis det er nødvendigt, kan du redigere disse indstillinger for at ændre denne standardkonfiguration.

Hvis du vil se resultaterne af denne politik, skal du bruge [DLP-aktivitetsoversigt.](dlp-learn-about-dlp.md#dlp-activity-explorer)

Hvis du vil redigere DLP-politikken, skal du se [Opret, test og juster en DLP-politik](create-test-tune-dlp-policy.md).

## <a name="additional-resources"></a>Yderligere ressourcer

Du kan få mere at vide om følsomhedsmærkater, forebyggelse af datatab og alle de funktioner, der er tilgængelige med Microsoft Purview Information Protection, i følgende ressourcer:

- [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Beskyt dine data med Microsoft Purview](information-protection.md)
