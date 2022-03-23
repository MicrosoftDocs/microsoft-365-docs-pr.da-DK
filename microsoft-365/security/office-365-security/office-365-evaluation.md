---
title: Evaluer Microsoft Defender for Office 365
description: Defender for Office 365 i evalueringstilstand opretter Defender for Office 365 og mailpolitikker, der logføres, f.eks. malware, men ikke reagerer på meddelelser.
keywords: evaluer Office 365, Microsoft Defender til Office 365, office 365-evaluering, kan du prøve Office 365, Microsoft Defender, Microsoft Defender til slutpunkt
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
ms.openlocfilehash: 7a00dc92383e71d105faf0975468e47bc38ed60e
ms.sourcegitcommit: dbce0b6e74ae2efec42fe2b3b82c8e8cabe0ddbe
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/15/2022
ms.locfileid: "63591509"
---
# <a name="evaluate-microsoft-defender-for-office-365"></a>Evaluer Microsoft Defender for Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!IMPORTANT]
> Microsoft Defender til Office 365 er i offentlig prøveversion. Denne prøveversion leveres uden en serviceaftale. Visse funktioner understøttes muligvis ikke, eller de har muligvis begrænsede egenskaber.

Udførelse af en grundig sikkerhedsproduktevaluering kan hjælpe dig med at give dig informerede beslutninger om opgraderinger og køb. Det hjælper at afprøve sikkerhedsproduktets muligheder for at vurdere, hvordan det kan hjælpe dit sikkerhedsteam i deres daglige opgaver.

Microsoft [Defender for](defender-for-office-365.md) Office 365-evalueringsoplevelsen er udviklet til at eliminere kompleksiteterne ved enheds- og miljøkonfiguration, så du kan fokusere på at evaluere funktionerne i Microsoft Defender til Office 365. Med evalueringstilstand kan alle meddelelser, der sendes Exchange Online postkasser, evalueres uden at pege MX-poster mod Microsoft. Funktionen gælder kun for mailbeskyttelse og ikke for Office klienter som Word, SharePoint eller Teams.

Hvis du ikke allerede har en licens, der understøtter Microsoft Defender til Office 365, kan du starte en [gratis 30-dages](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA) evaluering og teste funktionerne i Microsoft 365 Defender-portalen <https://security.microsoft.com>på . Du får glæde af den hurtige opsætning, og du kan nemt slå den fra, hvis det er nødvendigt.

> [!NOTE]
> Hvis du er på Microsoft 365 Defender-portalen <https://security.microsoft.com>på , kan du starte en Defender for Office 365-evaluering her: Mail **&** \> **samarbejdspolitikker & tilstanden Regler** \>  \> for trusselsevaluering i afsnittet Andre. Du kan også gå direkte til siden **Evalueringstilstand** ved hjælp af <https://security.microsoft.com/atpEvaluation>.

## <a name="how-the-evaluation-works"></a>Sådan fungerer evalueringen

Defender for Office 365 i evalueringstilstand opretter Defender for Office 365 og mailpolitikker, der logføres, f.eks. malware, men ikke reagerer på meddelelser. Det er ikke nødvendigt at ændre konfigurationen af din MX-post.

Med evalueringstilstand [er Pengeskab Vedhæftede](safe-attachments.md) [filer, Pengeskab Links](safe-links.md) og postkasseintelligens i [anti pishing-politikker](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) konfigureret på dine vegne. Alle Defender-Office 365-politikker oprettes i baggrunden i ikke-håndhævelsestilstand og er ikke synlige for dig.

Som en del af konfigurationen konfigurerer evalueringstilstand også [Udvidet filtrering for](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) forbindelser (også kaldet skip _listing_). Denne konfiguration forbedrer nøjagtigheden af filtrering ved at bevare IP-adresse og afsenderoplysninger, som ellers går tabt, når mails passerer gennem en mailsikkerhedsgateway (ESG) foran Defender Office 365. Forbedret filtrering for forbindelser forbedrer også filtreringsnøjagtigheden for dine eksisterende politikker for Exchange Online Protection (EOP) og antiphishing.

Udvidet filtrering for forbindelser forbedrer filtreringsnøjagtigheden, men kan ændre leverancen for visse meddelelser, hvis du har en ESG foran Defender til Office 365 og i øjeblikket ikke tilsidesætter EOP-filtrering. Virkningen er begrænset til EOP-politikker. Defender for Office 365 politikker, der er konfigureret som en del af evalueringen, oprettes i ikke-håndhævelsestilstand. Hvis du vil minimere den potentielle produktionsbelastning, kan du tilsidesætte de fleste EOP-filtreringer ved at oprette en regel for mailflow (også kaldet en transportregel) for at angive tillidsniveauet for mails til -1. Se [Brug regler for mailflow til at indstille SCL (spam confidence level) i meddelelser i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) for at få mere at vide.

Når evalueringstilstanden er konfigureret, får du en daglig rapport med op til 90 dages data, der sætter tal på de meddelelser, der ville være blevet blokeret, hvis politikkerne blev implementeret (f.eks. slette, sende til uønsket post eller karantæne). Der genereres rapporter for alle Defender-, Office 365- og EOP-registreringer. Rapporter samles pr. registreringsteknologi (f.eks. efterligning) og kan filtreres efter tidsinterval. Desuden kan meddelelsesrapporter oprettes efter behov for at oprette brugerdefinerede pivoter eller for at dykke ned i meddelelser ved hjælp af Stifinder.

Med den forenklede opsætningsoplevelse kan du fokusere på:

- Kørsel af evalueringen
- Få en detaljeret rapport
- Analyse af rapporten for handlinger
- Præsentation af evalueringsresultatet

## <a name="before-you-begin"></a>Før du begynder

### <a name="licensing"></a>Licensering

For at få adgang til evalueringen skal du opfylde licenskravene. En af følgende licenser fungerer:

- Microsoft Defender til Office 365 Plan 1
- Microsoft Defender til Office 365 Plan 2
- Microsoft 365 E5. Microsoft 365 E5 Sikkerhed
- Office 365 E5

Hvis du ikke har en af disse licenser, skal du have en prøvelicens.

#### <a name="trial"></a>Prøveversion

Hvis du vil have en prøvelicens til Microsoft Defender for Office 365, skal du have **faktureringsadministratorrollen** eller **den globale administratorrolle**. Anmod om tilladelse fra en person, der har rollen som global administrator. [Få mere at vide om abonnementer og licenser](../../commerce/licenses/subscriptions-and-licenses.md)

Når du har den rette rolle, er den anbefalede vej at <https://admin.microsoft.com>  \> få en prøvelicens til Microsoft Defender til Office 365 (Plan 2) i Microsoft 365 Administration på og derefter gå til tjenester til køb af fakturering og derefter finde og vælge prøveversionen af Microsoft Defender til Office 365 (Plan 2). Eller hvis du vil gå direkte til prøvesiden, skal du <https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA)> bruge Prøveversionen omfatter en 30 dages gratis prøveversion på 25 licenser.

Du har et 30-dages vindue med evaluering til at overvåge og rapportere om avancerede trusler. Du har også mulighed for at købe et betalt abonnement, hvis du vil have den fulde Defender Office 365 funktioner.

### <a name="roles"></a>Roller

**Exchange Online roller er** nødvendige for at konfigurere Defender til Office 365 i evalueringstilstand. Tildeling af Microsoft 365 af regler og standarder eller sikkerhedsadministratorroller fungerer ikke.

- [Få mere at vide om tilladelser i Exchange Online](/exchange/permissions-exo/permissions-exo)
- [Få mere at vide om at tildele administratorroller](../../admin/add-users/assign-admin-roles.md)

Der skal bruges følgende roller:

<br>

****

|Opgave|Rolle (i Exchange Online)|
|---|---|
|Få en gratis prøveversion, eller køb Microsoft Defender for Office 365 (Plan 2)|Faktureringsadministratorrolle ELLER global administratorrolle|
|Opret en evalueringspolitik|Rolle for fjerndomæner og accepterede domæner. Sikkerhedsadministratorrolle|
|Rediger evalueringspolitik|Rolle for fjerndomæner og accepterede domæner. Sikkerhedsadministratorrolle|
|Slet evalueringspolitik|Rolle for fjerndomæner og accepterede domæner. Sikkerhedsadministratorrolle |
|Vis evalueringsrapport|Sikkerhedsadministratorrolle ELLER Sikkerhedslæser-rolle|
|

### <a name="enhanced-filtering-for-connectors"></a>Forbedret filtrering for forbindelser

Dine Exchange Online Protection politikker, f.eks masse- og spambeskyttelse, forbliver de samme. Evalueringen slår dog Enhanced Filtering for Connectors til, hvilket kan påvirke dit mailflow og dine Exchange Online Protection, medmindre den tilsidesættes.

Udvidet filtrering for forbindelser giver lejere mulighed for at bruge beskyttelse mod spoofing. Antispoofing understøttes ikke, hvis du bruger en mailsikkerhedsgateway (ESG) uden at have aktiveret udvidet filtrering for forbindelser.

### <a name="urls"></a>URL-adresser

URL-adresser detoneres under mailflow. Hvis du ikke ønsker, at bestemte URL-adresser skal detoneres, skal du administrere din liste over tilladte URL-adresser korrekt. Se [Administrer lejerens tilladelses-/blokeringsliste](tenant-allow-block-list.md) for at få flere oplysninger.

URL-links i mailens tekst ombrydes ikke, så det påvirker kunderne mindre.

### <a name="email-routing"></a>Mailrouting

Forbered de tilsvarende oplysninger, du skal bruge for at konfigurere, hvordan din mail aktuelt distribueres, herunder navnet på den indgående forbindelse, der dirigerer din mail. Hvis du kun bruger Exchange Online Protection, har du ikke en forbindelse. [Få mere at vide om mailflow og mailrouting](/office365/servicedescriptions/exchange-online-service-description/mail-flow)

Understøttede scenarier for mailrouting omfatter:

- **Tredjepartspartner og/** eller lokal serviceudbyder: Den indgående forbindelse, som du vil evaluere, bruger en tredjepartsudbyder, og/eller du bruger en løsning til mailsikkerhed lokalt.
- **Microsoft Exchange Online beskyttelse**: Den lejer, du vil evaluere, bruger Office 365 til mailsikkerhed, og MX-posten (Mail Exchange) peger på Microsoft.

### <a name="email-security-gateway"></a>Mailsikkerhedsgateway

Hvis du bruger en mailsikkerhedsgateway fra en tredjepart (ESG), skal du kende udbyderens navn. Hvis du bruger en lokal ESG eller ikke-understøttede leverandører, skal du kende den offentlige IP-adresse(er) til enhederne.

Understøttede tredjepartspartnere omfatter:

- Barracuda
- IronPort
- Mimecast
- Korrekturpunkt
- Sofone
- Ikke-for-store
- Tendens micro

### <a name="scoping"></a>Angivelse af oplysninger

Du kan begrænse evalueringen til en indgående forbindelse. Hvis der ikke er konfigureret nogen forbindelse, giver evalueringsomfanget administratorer mulighed for at indsamle data fra alle brugere i din lejer for at evaluere Defender for Office 365.

## <a name="get-started-with-the-evaluation"></a>Introduktion til evalueringen

Find microsoft Defender for Office 365-evalueringssætkortet i Microsoft 365 Defender-portalen fra følgende adgangspunkter:

- **Slutpunkter** \> **Administration af sikkerhedsrisiko** \> **Dashboard** (<https://security.microsoft.com/tvm_dashboard>)
- **Mail & samarbejde** \> **Politikker & regler** \> **Trusselspolitikker** (<https://security.microsoft.com/threatpolicy>)
- **Rapporter** \> **Mail & samarbejde** \> **Rapporter & mailsamarbejde (**<https://security.microsoft.com/emailandcollabreport>)

## <a name="setting-up-the-evaluation"></a>Konfiguration af evalueringen

Når du starter opsætningsflowet for din evaluering, får du to routingindstillinger. Afhængigt af din organisations behov for konfiguration og evaluering af mail kan du vælge, om du bruger en tredjepart og/eller et lokalt serviceudbyder eller kun Microsoft Exchange Online.

- Hvis du bruger en tredjepartspartner og/eller en lokal serviceudbyder, skal du vælge navnet på leverandøren i rullemenuen. Angiv de andre forbindelsesrelaterede oplysninger.

- Vælg **Microsoft Exchange Online,** hvis MX-posten peger på Microsoft, og du har en Exchange Online postkasse.

Gennemse dine indstillinger, og rediger dem, hvis det er nødvendigt. Vælg derefter **Opret evaluering**. Du bør få en bekræftelsesmeddelelse, der angiver, at opsætningen er fuldført.

Din Microsoft Defender for Office 365-evalueringsrapport genereres én gang om dagen. Det kan tage op til 24 timer, før dataene udfyldes.

### <a name="exchange-mail-flow-rules-optional"></a>Exchange regler for mailflow (valgfrit)

Hvis du har en eksisterende gateway, aktiverer aktivering af evalueringstilstand udvidet filtrering for forbindelser. Denne funktion forbedrer filtreringsnøjagtigheden ved at ændre IP-adressen for den indgående afsender. Denne funktion kan ændre filterets konklusion, og hvis du ikke tilsidesætter Exchange Online Protection, kan dette ændre leverancen for visse meddelelser. I dette tilfælde kan det være en ide midlertidigt at tilsidesætte filtrering for at analysere påvirkningen. Hvis du vil tilsidesætte filtrering, skal du oprette en regel for mailflow (også kaldet en transportregel) i Exchange Administration (EAC), <https://admin.exchange.microsoft.com/#/transportrules> der angiver SCL for meddelelser til -1 (hvis du ikke allerede har en). Du kan finde en vejledning [i Brug regler for mailflow til at indstille spamtillidsniveauet (SCL) i meddelelser Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

## <a name="evaluate-capabilities"></a>Evaluer funktioner

Når evalueringsrapporten er blevet oprettet, kan du se, hvor mange avancerede trusselslinks, avancerede vedhæftede trusler og potentielle efterligninger, der er blevet identificeret i mails og samarbejdsarbejdsområder i organisationen.

Når prøveperioden er udløbet, kan du fortsætte med at få adgang til rapporten i 90 dage. Der indsamles dog ikke flere oplysninger. Hvis du vil fortsætte med at bruge Microsoft Defender til Office 365, når prøveperioden er udløbet, skal du sørge for at købe et betalt abonnement på [Microsoft Defender Office 365 (Plan 2)](https://admin.microsoft.com/AdminPortal/Home#/catalog/offer-details/microsoft-defender-for-office-365-plan-2-/223860DC-15D6-42D9-A861-AE05473069FA).

Du kan til enhver **tid Indstillinger** at opdatere din routing eller deaktivere din evaluering. Du skal dog gennemgå den samme opsætningsproces igen, hvis du beslutter dig for at fortsætte evalueringen efter at have slået den fra.

## <a name="provide-feedback"></a>Giv feedback

Din feedback hjælper os med at blive bedre til at beskytte dit miljø mod avancerede angreb. Del din oplevelse og dine indtryk af produktegenskaber og evalueringsresultater.

Vælg **Giv feedback for** at fortælle os, hvad du synes.
