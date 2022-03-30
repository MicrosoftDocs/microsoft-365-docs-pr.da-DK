---
title: Få mere at vide om standardnavne og -politikker for Microsoft Information Protection
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
description: Få mere at vide om standardetiketter og politikker for Microsoft Information Protection (MIP) til klassificering og beskyttelse af følsomt indhold.
ms.openlocfilehash: a0634a8f67e28d84334cfadd4be7d9694084af6c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63598527"
---
# <a name="default-labels-and-policies-for-microsoft-information-protection"></a>Standardnavne og -politikker for Microsoft Information Protection

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Berettigede kunder kan aktivere standardetiketter og politikker for Microsoft Information Protection (MIP): 

- Følsomhedsmærkater og en følsomhedsmærkatpolitik
- Automatisk mærkning på klientsiden
- Automatisk mærkning på tjenestesiden
- Politikker til forebyggelse af datatab (DLP) for Teams enheder

Disse standardkonfigurationer hjælper dig med at komme hurtigt i gang med Microsoft Information Protection fra Microsoft 365 overholdelse af regler og standarder. Du kan bruge dem, som de er, foretage nogle få ændringer eller tilpasse dem fuldt ud, så de passer bedre til virksomhedens behov. 

Berettigelse omfatter kunder, der har [en gratis prøveversion til Microsoft 365 Overholdelse](compliance-easy-trials.md) af regler og standarder, og nogle kunder, der allerede har en Microsoft 365 E5-plan:

- **Nye kunder**: Hvis du har haft Microsoft 365 overholdelse af regler og standarder i mindre end 30 dage, kan din lejer aktivere alle de angivne standardkonfigurationer. Du kan altid deaktivere, fjerne eller redigere dem.

- **Eksisterende kunder**: Hvis du har haft Microsoft 365 Overholdelse i mere end 30 dage, kan du aktivere standardkonfigurationerne, hvis du endnu ikke har konfigureret en tilsvarende:

    | Standardkonfiguration| Tilsvarende |
    |:-----|:-----|
    |Følsomhedsmærkater og en følsomhedsmærkatpolitik | Publicerede følsomhedsmærkater |
    |Automatisk mærkning på klientsiden | En eller flere følsomhedsmærkater, der er konfigureret til automatisk at anvende (eller anbefale til brugere) Office apps|
    |Automatisk mærkning på tjenestesiden | Mindst én politik for automatisk mærkater, som er slået til|
    |DLP til Teams | Mindst én DLP-politik for Teams|
    |DLP til enheder | Mindst én DLP-politik til enheder|

## <a name="activate-the-default-labels-and-policies"></a>Aktivere standardnavnene og -politikkerne

Sådan får du disse forudkonfigurerede etiketter og politikker: 

1. Fra [Microsoft 365 Overholdelsescenter vælge](https://compliance.microsoft.com/) **SolutionsInformation** >  **Protection**
    
    Hvis du ikke umiddelbart kan se denne indstilling, skal du først **vælge Vis alle** i navigationsruden. 
    
2. Hvis du er berettiget til Microsoft Information Protection standardnavne og -politikker, får du vist følgende oplysninger, hvor du kan aktivere standardnavnene og -politikkerne. Eksempel:
    
    :::image type="content" alt-text="Microsoft Information Protection aktivering af forudkonfigurerede etiketter og politikker." source="../media/mip-preconfigured.png" lightbox="../media/mip-preconfigured.png":::
    
    Hvis disse oplysninger ikke vises sammen med aktiveringsindstillingen, er du i øjeblikket ikke berettiget til automatisk oprettelse af følsomhedsmærkater og -politikker. Du kan prøve at vende tilbage senere for at se, om denne status er ændret, eller du kan bruge de følgende indstillinger til manuelt at oprette de samme etiketter og politikker.

3. Aktivér nu følsomhedsetiketter for SharePoint og OneDrive. Dette trin er en forudsætning for at kunne bruge følsomhedsmærkater Office på internettet politikker for automatisk mærkater til SharePoint og OneDrive.
   
    Brug følgende banner øverst på fanen Oversigt over beskyttelse **af oplysninger** , og vælg **Aktivér nu**. Hvis du ikke kan se dette banner, er følsomhedsmærkaterne for SharePoint og OneDrive allerede aktiveret for din lejer.
    
    ![Aktivér følsomhedsmærkater SharePoint et OneDrive banner.](../media/turn-on-mip-labels.png)
    
    Du kan finde flere oplysninger om denne funktionalitet under [Aktivér følsomhedsmærkater for Office filer i SharePoint og OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="default-sensitivity-labels"></a>Standardmærkater for følsomhed

Når du ikke har offentliggjort følsomhedsmærkater, opretter vi følgende mærkater til dig:


|Navn på etiket|Etiketbeskrivelse for brugere|Indstillinger|
|-------------------------------|---------------------------|-----------------|
|Personal|Ikke-virksomhedsdata, kun til personlig brug.|**Omfang**: Fil, Mail <br /><br />**Indholdsmærkning**: Nej<br /><br />**Automatisk mærkat:** Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkat for databasekolonner**: Ingen|
|Offentlig|Virksomhedsdata, der er specifikt forberedt og godkendt til offentligt forbrug.|**Omfang**: Fil, Mail <br /><br />**Indholdsmærkning**: Nej<br /><br />**Automatisk mærkat:** Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkat for databasekolonner**: Ingen|
|Generel|Virksomhedsdata, der ikke er beregnet til offentligt forbrug. Dette kan dog deles med eksterne partnere efter behov. Eksempler omfatter virksomhedens interne telefonbog, organisationsdiagrammer, interne standarder og de fleste interne kommunikation.|**Omfang**: Fil, Mail <br /><br />**Indholdsmærkning**: Nej<br /><br />**Automatisk mærkat:** Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkat for databasekolonner**: Ingen|
|Generel <br /> \ Alle (ubegrænset)|Organisationsdata, der ikke er beregnet til offentligt forbrug, men som kan deles med eksterne partnere, hvis det er relevant. Eksempler omfatter kundesamtaler, der ikke omfatter følsomme oplysninger eller udgivet marketingmateriale.|**Omfang**: Fil, Mail <br /><br />**Indholdsmærkning**: Nej<br /><br />**Automatisk mærkat:** Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkat for databasekolonner**: Ingen|
|Generel <br /> \ Alle medarbejdere (ubegrænset)|Organisationsdata, der ikke er beregnet til offentligt forbrug. Hvis du vil dele dette indhold med eksterne partnere, skal du bekræfte med andre dataejere, at det er OK at dele, og derefter ændre navnet til Generelt \ Alle (ubegrænset). Eksempler omfatter virksomhedens interne telefonbog, organisationsdiagrammer, interne standarder og de fleste interne kommunikation.|**Omfang**: Fil, Mail <br /><br />**Indholdsmærkning**: Nej<br /><br />**Automatisk mærkat:** Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkat for databasekolonner**: Ingen|
|Fortroligt|Følsomme forretningsdata, der kan skade virksomheden, hvis de deles med uautoriserede personer. Eksempler kan være kontrakter, sikkerhedsrapporter, prognoseoversigter og salgskontodata.|**Omfang**: Fil, Mail <br /><br />**Indholdsmærkning**: Nej<br /><br />**Automatisk mærkat:** Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkat for databasekolonner**: Ingen|
|Fortroligt <br /> \ Alle (ubegrænset)|Fortrolige data, der ikke behøver at være krypteret. Brug denne indstilling med pleje og passende forretningsberettigelse.|Denne etiket er valgt [til automatisk mærkatning på](#client-side-auto-labeling) klientsiden [og automatisk mærkning på tjenestesiden](#service-side-auto-labeling).<br /><br /> **Omfang**: Fil, Mail <br /><br />**Indholdsmærkning**: Sidefod: Klassificeret som fortrolig<br /><br />**Automatisk mærkning: Anbefal**, at brugerne anvender etiketten <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkat for databasekolonner**: Ingen|
|Fortroligt <br /> \ Alle medarbejdere|Fortrolige data, der kræver beskyttelse, som giver alle medarbejdere fuld tilladelse. Dataejere kan spore og tilbagekalde indhold.|Denne etiket er valgt [til automatisk mærkatning på](#client-side-auto-labeling) klientsiden [og automatisk mærkning på tjenestesiden](#service-side-auto-labeling).<br /><br /> **Omfang**: Fil, Mail <br /><br />**Kryptering**: Alle brugere og grupper i organisationen: Co-Author<br /><br />**Indholdsmærkning**: Sidefod: Klassificeret som fortrolig<br /><br />**Automatisk mærkning: Anbefal**, at brugerne anvender etiketten <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkat for databasekolonner**: Ingen |
|Fortroligt <br /> \ Personer, der er tillid til|Fortrolige data, der kan deles med personer, der er tillid til, i og uden for organisationen. Disse personer kan også dele dataene igen efter behov.|**Omfang**: Fil, Mail <br /><br />**Kryptering**: Lad brugere tildele tilladelser: <br /> - Encrypt-Only til Outlook <br />- Spørg brugerne i Word, PowerPoint og Excel<br /><br />**Indholdsmærkning**: Sidefod: Klassificeret som fortrolig<br /><br />**Automatisk mærkat:** Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkat for databasekolonner**: Ingen|
|Meget fortrolig|Meget følsomme forretningsdata, der ville skade virksomheden, hvis de blev delt med uautoriserede personer. Eksempler er medarbejder- og kundeoplysninger, adgangskoder, kildekode og på forhånd annoncerede økonomiske rapporter.|**Omfang**: Fil, Mail <br /><br />**Indholdsmærkning**: Vandmærke: MEGET FORTROLIGT<br /><br />**Automatisk mærkat:** Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkat for databasekolonner**: Ingen|
|Meget fortrolig <br /> \ Alle medarbejdere|Meget fortrolige data, der giver alle medarbejdere mulighed for at få vist, redigere og svare på dette indhold. Dataejere kan spore og tilbagekalde indhold.|**Omfang**: Fil, Mail <br /><br />**Kryptering**: Alle brugere og grupper i organisationen: Co-Author<br /><br />**Indholdsmærkning**: Sidefod: Klassificeret som meget fortrolig<br /><br />**Automatisk mærkat:** Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkat for databasekolonner**: Ingen|
|Meget fortrolig <br /> \ Bestemte personer |Meget fortrolige data, der kræver beskyttelse, og som kun kan ses af personer, du angiver, og med det tilladelsesniveau, du vælger.|**Omfang**: Fil, Mail <br /><br />**Kryptering**: Lad brugere tildele tilladelser: <br />- Videresendes ikke for Outlook <br />- Spørg brugerne i Word, PowerPoint og Excel<br /><br />**Indholdsmærkning**: Sidefod: Klassificeret som meget fortrolig<br /><br />**Automatisk mærkat:** Nej <br /><br />**Gruppeindstillinger**: Nej<br /><br />**Indstillinger for websted**: Nej <br /><br />**Automatisk mærkat for databasekolonner**: Ingen|

> [!NOTE]
> Navne og beskrivelser er automatisk tilgængelige for følgende lande/ lande: amerikansk engelsk, forenklet kinesisk og traditionelt, fransk, tysk, italiensk, japansk, koreansk, portugisisk (Brasilien) og russisk.
> 
> Hvis du har brug for flere sprog, kan du angive dine oversættelser [ved hjælp af PowerShell](create-sensitivity-labels.md#example-configuration-to-configure-a-sensitivity-label-for-different-languages).

Du kan finde flere oplysninger om disse konfigurationsindstillinger, og hvad følsomhedsmærkater kan, under [Hvad følsomhedsmærkater kan gøre](sensitivity-labels.md#what-sensitivity-labels-can-do).

Hvis du vil redigere disse standardmærkater for følsomhed, skal du [se Opret og konfigurer følsomhedsmærkater](create-sensitivity-labels.md#create-and-configure-sensitivity-labels).

## <a name="default-sensitivity-label-policy"></a>Standardpolitik for følsomhedsmærkater

Standardpolitikken for følsomhedsmærkater gør mærkaterne tilgængelige, så brugerne kan begynde at navnmærke deres dokumenter og mails med følsomhedsmærkater. Den har følgende konfiguration:

- Udgive standardetiketterne til alle brugere i din lejer
- **Standardetiket for GeneralAlle** \  **medarbejdere (ubegrænset)** for dokumenter og mails uden navn
- Brugerne skal angive en begrundelse for at fjerne en etiket eller sænke dens klassificering

Du kan finde flere oplysninger om disse politikindstillinger og andre politikindstillinger, der er tilgængelige, under [Hvilke etiketpolitikker kan gøre](sensitivity-labels.md#what-label-policies-can-do).

Hvis du vil redigere disse standardpolitikindstillinger, skal du se [Publicere følsomhedsmærkater ved at oprette en etiketpolitik](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

Når du bruger disse etiketter i Office-apps på Windows, macOS, iOS og Android, får brugerne vist nye navne inden for fire timer og inden for en time for Word, Excel og PowerPoint på internettet, når du opdaterer browseren. Det kan dog være nødvendigt at tillade, at ændringer replikeres til alle apps og tjenester i op til 24 timer.

## <a name="client-side-auto-labeling"></a>Automatisk mærkning på klientsiden

Standardkonfigurationen af automatisk mærkning på klientsiden anbefaler automatisk, at brugerne anvender et følsomhedsmærkat, når vi registrerer kreditkortnumre i dokumenter eller mails, de arbejder med. Som en anbefaling i stedet for automatisk anvendelse fungerer denne konfiguration som et godt første trin til at fremhæve fremhævet indhold og introducerer brugerne til etiketning af deres dokumenter og mails.

Automatisk mærkning på klientsiden fungerer kun for dokumenter og mails, der bruges af Office-appsene Word, Excel, PowerPoint og Outlook. 

Automatisk mærkater på klientsiden har følgende konfiguration: 

- Hvis der findes 1-9 forekomster af kreditkortnumre i et dokument eller en mail, anbefaler vi, at brugeren anvender følsomhedsetiketten **ConfidentialAnyone**  \  (ubegrænset) 

- Hvis der er fundet 10 eller flere forekomster af kreditkortnumre i et dokument eller en mail, anbefaler vi, at brugeren anvender følsomhedsmærkatet **FortroligeAlle medarbejdere**  \  

> [!NOTE]
> Hvis vi har opdaget, at du har publiceret dine egne følsomhedsmærkater, beder vi dig om at vælge en af dine egne etiketter til automatisk mærkning og konfigurere den for dig.

Hvis du vil redigere konfigurationen af automatisk mærkning på klientsiden, skal du se Sådan konfigureres [automatisk mærkater til Office apps](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-for-office-apps).

## <a name="service-side-auto-labeling"></a>Automatisk mærkning på tjenestesiden 

Automatisk mærkning på tjenestesiden hjælper med at mærke følsomme dokumenter, når de er indeværende, og mails, der er under overførsel. Standardpolitikken for automatisk mærkning på tjenestesiden opretter en politik i simuleringstilstand for dokumenter, der er gemt på alle SharePoint- eller OneDrive-websteder, og alle mails, der sendes via Exchange Online. I simuleringstilstand navnmærkes elementer faktisk ikke, før du slår politikken til. Simuleringstilstand giver dig mulighed for at se, hvilke elementer der ville blive mærket, når politikken er slået til, så du har tillid til etiketfunktionen, før du installerer politikken for den faktiske mærkning til din lejer. 

Automatisk mærkning på tjenestesiden har følgende konfiguration: 

- Hvis der findes 1-9 forekomster af kreditkortnumre i et dokument, skal du anvende følsomhedsetiketten **ConfidentialAnyone** \  **(uden begrænsninger)**

- Hvis der er fundet 10 eller flere forekomster af kreditkortnumre i et dokument eller en mail, anbefaler vi, at brugeren anvender følsomhedsmærkatet **FortroligeAlle medarbejdere**  \  

> [!NOTE]
> Hvis vi har opdaget, at du har publiceret dine egne følsomhedsmærkater, beder vi dig om at vælge en af dine egne etiketter til din automatiske mærkningspolitik.

Når simulering er fuldført, skal du gennemse resultaterne, og hvis du er tilfreds med dem, skal du aktivere politikken.

Du kan finde flere oplysninger om simuleringstilstand i [Få mere at vide om simuleringstilstand](apply-sensitivity-label-automatically.md#learn-about-simulation-mode).

Hvis du vil redigere politikken for automatisk mærkning af tjenester, skal du se Sådan konfigureres politikker for automatisk mærkater [for SharePoint, OneDrive og Exchange](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange).

## <a name="dlp-for-teams"></a>DLP til Teams

Standard-DLP-politikken for Teams registrerer tilstedeværelsen af kreditkortnumre i alle chatsamtaler Teams kanalmeddelelser. Når disse følsomme oplysninger registreres, får administratorer besked om lav alvorsgrad.

Denne politik er ikke-diskret for brugere uden synlig politiktip og ingen meddelelser blokeret, men administratorer vil have poster for de følsomme oplysninger, der deles i disse meddelelser. Hvis det er nødvendigt, kan du redigere indstillingerne for at ændre denne standardkonfiguration.

Hvis du vil se resultaterne af denne politik, skal du [bruge DLP-aktivitetsoversigt](dlp-learn-about-dlp.md#dlp-activity-explorer).

Hvis du vil redigere DLP-politikken, skal du [se Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md).

## <a name="dlp-for-devices"></a>DLP til enheder

DLP-standardpolitikken for enheder registrerer tilstedeværelsen af kreditkortnumre på enheder, Windows 10 er blevet onboardet i Microsoft 365 overholdelse af regler og standarder. Derefter overvåges (blokeres ikke) følgende handlinger: 

- Upload til skytjenestedomæner eller adgang fra ikke-tilladte browsere

- Kopiér til Udklipsholder, USB eller netværksshare 

- Adgang fra ikke-tilladte apps 

- Udskriv 

- Kopiér eller flyt ved hjælp af Bluetooth-app 

- Fjernskrivebord-tjenester 

Hvis indhold indeholder 10 eller flere forekomster af kreditkort, og en eller flere af de angivne aktiviteter registreres, sendes der en besked om beskeden med mellemstor alvorsgrad til administratorer.

Denne politik er ikke-diskret for brugere uden synlig politiktip og ingen handlinger blokeret, men administratorer vil have poster for alle mistænkelige aktiviteter. Hvis det er nødvendigt, kan du redigere disse indstillinger for at ændre denne standardkonfiguration.

Hvis du vil se resultaterne af denne politik, skal du [bruge DLP-aktivitetsoversigt](dlp-learn-about-dlp.md#dlp-activity-explorer).

Hvis du vil redigere DLP-politikken, skal du [se Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md).

## <a name="additional-resources"></a>Yderligere ressourcer

Du kan få mere at vide om følsomhedsmærkater, forebyggelse af datatab og alle de tilgængelige Microsoft Information Protection ved at se følgende ressourcer:

- [Få mere at vide om følsomhedsmærkater](sensitivity-labels.md)
- [Få mere at vide om forebyggelse af datatab](dlp-learn-about-dlp.md)
- [Microsoft Information Protection i Microsoft 365](information-protection.md)
