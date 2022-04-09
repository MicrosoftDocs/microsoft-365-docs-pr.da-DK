---
title: Evaluer Microsoft Defender for Office 365
description: Defender for Office 365 i evalueringstilstand opretter Defender for Office 365 mailpolitikker, der logfører domme, f.eks. malware, men ikke reagerer på meddelelser.
keywords: evaluer Office 365, Microsoft Defender for Office 365, office 365-evaluering, prøv office 365, Microsoft Defender Microsoft Defender for Endpoint
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0f5d82e9baaca7209f8a91a7f1984aa38e3102e6
ms.sourcegitcommit: 74518b920b4166adccc10ea1581a62c44bb14edb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/09/2022
ms.locfileid: "64738746"
---
# <a name="evaluate-microsoft-defender-for-office-365"></a>Evaluer Microsoft Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Microsoft Defender for Office 365 evaluering er en offentlig prøveversion. Denne prøveversion leveres uden en serviceniveauaftale. Visse funktioner understøttes muligvis ikke, eller de kan have begrænsede funktioner.

En grundig evaluering af sikkerhedsproduktet kan hjælpe dig med at træffe velunderbyggede beslutninger om opgraderinger og køb. Det hjælper med at afprøve sikkerhedsproduktets funktioner for at vurdere, hvordan det kan hjælpe dit sikkerhedsteam med at udføre deres daglige opgaver.

Den [Microsoft Defender for Office 365](defender-for-office-365.md) evalueringsoplevelse er designet til at fjerne kompleksiteten af enheds- og miljøkonfigurationen, så du kan fokusere på at evaluere funktionerne i Microsoft Defender for Office 365. I evalueringstilstand kan alle meddelelser, der sendes til Exchange Online postkasser, evalueres uden at pege MX-poster på Microsoft. Funktionen gælder kun for mailbeskyttelse og ikke for Office klienter, f.eks. Word, SharePoint eller Teams.

Hvis du ikke allerede har en licens, der understøtter Microsoft Defender for Office 365, kan du starte en [gratis 30-dages evaluering](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA) og teste funktionerne på Microsoft 365 Defender-portalen på <https://security.microsoft.com>. Du vil nyde den hurtige konfiguration, og du kan nemt slå den fra, hvis det er nødvendigt.

> [!NOTE]
> Hvis du er på Microsoft 365 Defender-portalen på <https://security.microsoft.com>, kan du starte en Defender for Office 365 evaluering her: **Mail & Samarbejdspolitikker** \> **& tilstanden Regler** \> **Trusselspolitikker** \> **Evalueringstilstand** i afsnittet **Andre**. Du kan også gå direkte til siden **Evalueringstilstand** ved at bruge <https://security.microsoft.com/atpEvaluation>.

## <a name="how-the-evaluation-works"></a>Sådan fungerer evalueringen

Defender for Office 365 i evalueringstilstand opretter Defender for Office 365 mailpolitikker, der logfører domme, f.eks. malware, men ikke reagerer på meddelelser. Du behøver ikke at ændre konfigurationen af din MX-post.

Med evalueringstilstand konfigureres [Pengeskab Attachments](safe-attachments.md), [Pengeskab Links](safe-links.md) og [mailbox intelligence i anti-pishing-politikker](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) på dine vegne. Alle Defender for Office 365 politikker oprettes i ikke-gennemtvingende tilstand i baggrunden og er ikke synlige for dig.

Som en del af konfigurationen konfigurerer evalueringstilstanden også [udvidet filtrering for forbindelser](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) (også kendt som _skip listing_). Denne konfiguration forbedrer filtreringsnøjagtigheden ved at bevare IP-adresse og afsenderoplysninger, som ellers går tabt, når mail passerer en ESG (Email Security Gateway) foran Defender for Office 365. Forbedret filtrering for forbindelser forbedrer også filtreringsnøjagtigheden for dine eksisterende EOP-politikker (Exchange Online Protection) og anti-phishing.

Forbedret filtrering for forbindelser forbedrer filtreringsnøjagtigheden, men kan ændre leveringsdygtigheden for visse meddelelser, hvis du har en ESG foran Defender for Office 365 og i øjeblikket ikke tilsidesætter EOP-filtrering. Indvirkningen er begrænset til EOP-politikker; Defender for Office 365 politikker, der er konfigureret som en del af evalueringen, oprettes i ikke-håndhævelsestilstand. Hvis du vil minimere den potentielle produktionspåvirkning, kan du omgå de fleste EOP-filtreringer ved at oprette en regel for mailflow (også kendt som en transportregel) for at angive niveauet for afsendersikkerhed for spam (SCL) for meddelelser til -1. Se [Brug regler for mailflow til at angive niveauet for spamsikkerhed i meddelelser i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) for at få flere oplysninger.

Når evalueringstilstanden er konfigureret, har du en daglig rapport med op til 90 dages data, der kvantificerer de meddelelser, der ville være blevet blokeret, hvis politikkerne blev implementeret (f.eks. slet, send til uønsket post, karantæne). Der genereres rapporter for alle Defender for Office 365- og EOP-registreringer. Rapporter er aggregeret pr. registreringsteknologi (f.eks. repræsentation) og kan filtreres efter tidsinterval. Derudover kan der oprettes meddelelsesrapporter efter behov for at oprette brugerdefinerede pivots eller til detaljerede gennemgangsmeddelelser ved hjælp af Stifinder.

Med den forenklede konfiguration kan du fokusere på:

- Kører evalueringen
- Sådan får du en detaljeret rapport
- Analyse af rapporten til handling
- Præsentation af evalueringsresultatet

## <a name="before-you-begin"></a>Før du begynder

### <a name="licensing"></a>Licensering

Hvis du vil have adgang til evalueringen, skal du opfylde licenskravene. En af følgende licenser fungerer:

- Microsoft Defender for Office 365 Plan 1
- Microsoft Defender for Office 365 plan 2
- Microsoft 365 E5, Microsoft 365 E5 Sikkerhed
- Office 365 E5

Hvis du ikke har en af disse licenser, skal du have en prøvelicens.

#### <a name="trial"></a>Retssag

Hvis du vil have en prøvelicens til Microsoft Defender for Office 365, skal du have **rollen Faktureringsadministrator** eller **Global administrator**. Anmod om tilladelse fra en person, der har rollen Global administrator. [Få mere at vide om abonnementer og licenser](../../commerce/licenses/subscriptions-and-licenses.md)

Når du har den korrekte rolle, anbefales det, at du får en prøvelicens til Microsoft Defender for Office 365 (Plan 2) i Microsoft 365 Administration på <https://admin.microsoft.com> og derefter går til **Fakturering** \> **Køb tjenester** og derefter finder og vælger prøveversion af Microsoft Defender for Office 365 (Plan 2). Eller hvis du vil gå direkte til prøveversionssiden, skal du bruge <https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA)> Prøveversionen indeholder en 30-dages gratis prøveversion til 25 licenser.

Du har et 30-dages vindue med evalueringen til at overvåge og rapportere om avancerede trusler. Du har også mulighed for at købe et betalt abonnement, hvis du vil have de fulde Defender for Office 365 funktioner.

### <a name="roles"></a>Roller

**Exchange Online roller** kræves for at konfigurere Defender for Office 365 i evalueringstilstand. Tildeling af en Microsoft 365 overholdelses- eller sikkerhedsadministratorrolle fungerer ikke.

- [Få mere at vide om tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Få mere at vide om tildeling af administratorroller](../../admin/add-users/assign-admin-roles.md)

Følgende roller er nødvendige:

|Opgave|Rolle (i Exchange Online)|
|---|---|
|Få en gratis prøveversion, eller køb Microsoft Defender for Office 365 (Plan 2)|Rollen faktureringsadministrator eller rollen global administrator|
|Opret evalueringspolitik|Rollen Fjerndomæner og Accepterede domæner. Sikkerhedsadministratorrolle|
|Rediger evalueringspolitik|Rollen Fjerndomæner og Accepterede domæner. Sikkerhedsadministratorrolle|
|Slet evalueringspolitik|Rollen Fjerndomæner og Accepterede domæner. Sikkerhedsadministratorrolle |
|Vis evalueringsrapport|Sikkerhedsadministratorrolle ELLER Rollen Sikkerhedslæser|

### <a name="enhanced-filtering-for-connectors"></a>Forbedret filtrering for forbindelser

Dine Exchange Online Protection politikker, f.eks. masse- og spambeskyttelse, forbliver de samme. Evalueringen aktiverer dog udvidet filtrering for forbindelser, hvilket kan påvirke dit mailflow og Exchange Online Protection politikker, medmindre de tilsidesættes.

Forbedret filtrering for forbindelser gør det muligt for lejere at bruge beskyttelse mod spoofing. Anti-spoofing understøttes ikke, hvis du bruger en mailsikkerhedsgateway (ESG) uden at have slået Udvidet filtrering til for connectors.

### <a name="urls"></a>Webadresser

URL-adresser detoneres under mailflow. Hvis du ikke vil have bestemte URL-adresser detoneret, skal du administrere din liste over tilladte URL-adresser korrekt. Se [Administrer listen over tilladte/blokerede lejere](tenant-allow-block-list.md) for at få flere oplysninger.

URL-links i mailens meddelelsestekster ombrydes ikke for at mindske kundernes indvirkning.

### <a name="email-routing"></a>Maildistribution

Forbered de tilsvarende oplysninger, som du skal bruge for at konfigurere, hvordan din mail i øjeblikket distribueres, herunder navnet på den indgående connector, der distribuerer din mail. Hvis du kun bruger Exchange Online Protection, har du ikke en connector. [Få mere at vide om mailflow og maildistribution](/office365/servicedescriptions/exchange-online-service-description/mail-flow)

Understøttede maildistributionsscenarier omfatter:

- **Tredjepartspartner og/eller tjenesteudbyder** i det lokale miljø: Den indgående connector, du vil evaluere, bruger en tredjepartsudbyder, og/eller du bruger en løsning til mailsikkerhed i det lokale miljø.
- **kun Microsoft Exchange Online Beskyttelse**: Den lejer, du vil evaluere, bruger Office 365 til mailsikkerhed, og posten Mail Exchange (MX) peger på Microsoft.

### <a name="email-security-gateway"></a>Mailsikkerhedsgateway

Hvis du bruger en ESG (third-party email security gateway), skal du kende udbyderens navn. Hvis du bruger en ESG eller ikke-understøttet leverandør i det lokale miljø, skal du kende den eller de offentlige IP-adresser for enhederne.

Understøttede tredjepartspartnere omfatter:

- Barracuda
- IronPort
- Mimecast
- Korrekturpunkt
- Sophos
- Symantec
- Trend Micro

### <a name="scoping"></a>Områdeafgrænsning

Du kan tilpasse evalueringen til en indgående connector. Hvis der ikke er konfigureret en connector, giver evalueringsområdet administratorer mulighed for at indsamle data fra alle brugere i din lejer for at evaluere Defender for Office 365.

## <a name="get-started-with-the-evaluation"></a>Kom i gang med evalueringen

Find kortet til konfiguration af Microsoft Defender for Office 365 evaluering på portalen Microsoft 365 Defender fra følgende adgangspunkter:

- **Slutpunkter** \> **Administration af** \> sårbarheder **Dashboard** (<https://security.microsoft.com/tvm_dashboard>)
- **Mail & samarbejde** \> **Politikker & regler** \> **Trusselspolitikker** (<https://security.microsoft.com/threatpolicy>)
- **Rapporter** \> **Mail & samarbejde** \> **Mail & samarbejdsrapporter** (<https://security.microsoft.com/emailandcollabreport>)

## <a name="setting-up-the-evaluation"></a>Konfiguration af evalueringen

Når du starter opsætningsflowet til din evaluering, får du to routingindstillinger. Afhængigt af organisationens behov for konfiguration og evaluering af maildistribution kan du vælge, om du bruger en tredjepartsudbyder og/eller en tjenesteudbyder i det lokale miljø eller kun Microsoft Exchange Online.

- Hvis du bruger en tredjepartspartner og/eller en tjenesteudbyder i det lokale miljø, skal du vælge navnet på leverandøren i rullemenuen. Angiv de andre connectorrelaterede oplysninger.

- Vælg **Microsoft Exchange Online**, hvis MX-posten peger på Microsoft, og du har en Exchange Online postkasse.

Gennemse dine indstillinger, og rediger dem, hvis det er nødvendigt. Vælg derefter **Opret evaluering**. Du bør få en bekræftelsesmeddelelse for at angive, at din konfiguration er fuldført.

Din Microsoft Defender for Office 365 evalueringsrapport genereres én gang om dagen. Det kan tage op til 24 timer, før dataene er udfyldt.

### <a name="exchange-mail-flow-rules-optional"></a>Exchange regler for mailflow (valgfrit)

Hvis du har en eksisterende gateway, aktiverer aktivering af evalueringstilstand udvidet filtrering for forbindelser. Denne funktion forbedrer filtreringsnøjagtigheden ved at ændre ip-adressen for den indgående afsender. Denne funktion kan ændre filterafsigelserne, og hvis du ikke tilsidesætter Exchange Online Protection, kan dette ændre leveringsdygtigheden for visse meddelelser. I dette tilfælde kan det være en god idé midlertidigt at tilsidesætte filtrering for at analysere indvirkningen. Hvis du vil tilsidesætte filtrering, skal du oprette en regel for mailflowet (også kendt som en transportregel) i Exchange Administration (EAC) på <https://admin.exchange.microsoft.com/#/transportrules> den måde, der angiver SCL for meddelelser til -1 (hvis du ikke allerede har en). Du kan finde en vejledning under [Brug regler for mailflow til at angive niveauet for spamsikkerhed i meddelelser i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

## <a name="evaluate-capabilities"></a>Evaluer funktioner

Når evalueringsrapporten er genereret, kan du se, hvor mange avancerede trusselslinks, vedhæftede filer med avancerede trusler og potentielle repræsentationer, der blev identificeret i mail- og samarbejdsarbejdsområder i din organisation.

Når prøveversionen er udløbet, kan du fortsætte med at få adgang til rapporten i 90 dage. Den indsamler dog ikke flere oplysninger. Hvis du vil fortsætte med at bruge Microsoft Defender for Office 365, når din prøveversion er udløbet, skal du sørge for at [købe et betalt abonnement på Microsoft Defender for Office 365 (Plan 2)](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA).

Du kan når som helst gå til **Indstillinger** for at opdatere distributionen eller deaktivere evalueringen. Du skal dog gennemgå den samme konfigurationsproces igen, hvis du beslutter dig for at fortsætte din evaluering efter at have slået den fra.

## <a name="provide-feedback"></a>Giv feedback

Din feedback hjælper os med at blive bedre til at beskytte dit miljø mod avancerede angreb. Del dine erfaringer og visninger af produktegenskaber og evalueringsresultater.

Vælg **Giv feedback** for at fortælle os, hvad du synes.
