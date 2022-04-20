---
title: Funktioner i Basic Mobility og Security
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Basic Mobility and Security kan hjælpe dig med at sikre og administrere dine mobilenheder.
ms.openlocfilehash: b0e303af27d731cf3dba3af13019b3b993e52bfe
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937757"
---
# <a name="capabilities-of-basic-mobility-and-security"></a>Funktioner i Basic Mobility og Security

Basic Mobility and Security kan hjælpe dig med at sikre og administrere mobilenheder, f.eks. iPhones, iPads, Androids og Windows telefoner, der bruges af licenserede Microsoft 365 brugere i din organisation. Du kan oprette politikker for administration af mobilenheder med indstillinger, der kan hjælpe med at styre adgangen til organisationens Microsoft 365 mail og dokumenter for understøttede mobilenheder og apps. Hvis en enhed mistes eller bliver stjålet, kan du slette enheden eksternt for at fjerne følsomme organisationsoplysninger.

## <a name="supported-operating-systems"></a>Understøttede operativsystemer

Følg vejledningen til Microsoft Intune operativsystemer for at få oplysninger om minimum understøttede operativsystemer til enheder fra Basic Mobility and Security. Du kan finde flere oplysninger [under Intune understøttede operativsystemer](/mem/intune/fundamentals/supported-devices-browsers).

Du kan bruge Basic Mobility og Security til at sikre og administrere følgende enheder.

- Ios
- Android (herunder Samsung Knox)<sup>1</sup>
- Windows <sup>2, 3</sup>

<sup>1</sup> Efter juni 2020 kan Android-versioner, der er nyere end 9, ikke administrere adgangskodeindstillinger undtagen på Samsung Knox-enheder.

<sup>2</sup> Adgangskontrol for Windows 8.1 RT-enheder er begrænset til Exchange ActiveSync.

<sup>3</sup> Adgangskontrol for Windows 10 kræver et abonnement, der indeholder Azure AD Premium, og enheden skal være tilsluttet Azure Active Directory.

> [!NOTE]
> Enheder, der allerede er tilmeldt tidligere operativsystemversioner, fungerer fortsat, selvom funktionerne kan ændres uden varsel.

Hvis personer i din organisation bruger mobilenheder, der ikke understøttes af Basic Mobility og Security, kan det være en god idé at blokere Exchange ActiveSync appadgang til Microsoft 365 mail for disse enheder for at gøre organisationens data mere sikre. Du kan finde trin til at blokere Exchange ActiveSync [under Administrer indstillinger for enhedsadgang i Grundlæggende mobilitet og sikkerhed](manage-device-access-settings.md).

## <a name="access-control-for-microsoft-365-email-and-documents"></a>Adgangskontrol for Microsoft 365 mail og dokumenter

De understøttede apps til de forskellige typer mobilenheder i følgende tabel beder brugerne om at tilmelde sig Basic Mobility og Security, hvor der er en ny politik for administration af mobilenheder, som gælder for en brugers enhed, og brugeren ikke tidligere har tilmeldt enheden. Hvis en brugers enhed ikke overholder en politik, afhængigt af hvordan du konfigurerer politikken, kan en bruger blive blokeret fra at få adgang til Microsoft 365 ressourcer i disse apps, eller vedkommende har muligvis adgang, men Microsoft 365 rapporterer en politikovertrædelse.

|Produkt|Ios|Android|
|---|---|---|
|**Exchange** Exchange ActiveSync omfatter indbyggede mailapps og tredjepartsapps, f.eks. TouchDown, der bruger Exchange ActiveSync version 14.1 eller nyere.|Mail|E-mail|
|**Office** og **OneDrive for Business**|Outlook </br>OneDrive </br>Word </br>Excel </br>PowerPoint|**På telefoner og tablets**:<br/>Outlook <br/> OneDrive <br/> Word <br/> Excel <br/> PowerPoint <br/> **Kun til telefoner:** <br/> Office Mobil|

> [!NOTE]
>
> - Understøttelse af iOS 10.0 og nyere versioner omfatter iPhone og iPad enheder.
> - Administration af BlackBerry OS-enheder understøttes ikke af Grundlæggende sikkerhed og mobilitet. Brug BlackBerry Business Cloud Services (BBCS) fra BlackBerry til at administrere BlackBerry OS-enheder. Blackberry-enheder, der kører Android OS, understøttes som android-standardenheder
> - Brugerne bliver ikke bedt om at tilmelde sig og vil ikke blive blokeret eller rapporteret for politikovertrædelse, hvis de bruger mobilbrowseren til at få adgang til Microsoft 365 SharePoint websteder, dokumenter i Office Online eller mail i Outlook Web App.

I følgende diagram kan du se, hvad der sker, når en bruger med en ny enhed logger på en app, der understøtter adgangskontrol med Basic Mobility og Security. Brugeren er blokeret fra at få adgang til Microsoft 365 ressourcer i appen, indtil vedkommende tilmelder sin enhed.

:::image type="content" source="../../media/basic-mobility-security/bms-1-access-control.png" alt-text="Basic Mobility- og Security-adgangskontrol.":::

> [!NOTE]
> Politikker og adgangsregler, der er oprettet i Basic Mobility and Security for Microsoft 365 Business Standard, tilsidesætter Exchange ActiveSync politikker for postkasser på mobilenheder og regler for enhedsadgang, der er oprettet i Exchange Administration. Når en enhed er tilmeldt Basic Mobility and Security for Microsoft 365 Business Standard, ignoreres alle Exchange ActiveSync politik for postkasser på mobilenheder eller regler for enhedsadgang, der er anvendt på enheden. Du kan få mere at vide om Exchange ActiveSync [under Exchange ActiveSync i Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="policy-settings-for-mobile-devices"></a>Politikindstillinger for mobilenheder

Hvis du opretter en politik for at blokere adgang med visse indstillinger slået til, blokeres brugerne fra at få adgang til Microsoft 365 ressourcer, når de bruger en understøttet app, der er angivet i [Adgangskontrol for Microsoft 365 mail og dokumenter](capabilities.md).

De indstillinger, der kan forhindre brugerne i at få adgang til Microsoft 365 ressourcer, findes i disse afsnit:

- Sikkerhed

- Kryptering

- Fængsel er brudt

- Administreret mailprofil

I følgende diagram kan du f.eks. se, hvad der sker, når en bruger med en tilmeldt enhed ikke overholder en sikkerhedsindstilling i en politik for administration af mobilenheder, der gælder for brugerens enhed. Brugeren logger på en app, der understøtter adgangskontrol med Basic Mobility og Security. De er blokeret fra at få adgang til Microsoft 365 ressourcer i appen, indtil deres enhed overholder sikkerhedsindstillingen.

:::image type="content" source="../../media/basic-mobility-security/bms-2-device-not-compliant.png" alt-text="Meddelelse om overholdelse af grundlæggende standarder for mobilitet og sikkerhed.":::

I følgende afsnit vises de politikindstillinger, du kan bruge til at beskytte og administrere mobilenheder, der opretter forbindelse til dine Microsoft 365 organisationsressourcer.

## <a name="security-settings"></a>Sikkerhedsindstillinger

|Indstillingsnavn|Ios|Android|Samsung Knox|
|---|---|---|---|
|Kræv en adgangskode|Ja|Ja|Ja|
|Undgå simpel adgangskode|Ja|Nej|Nej|
|Kræv en alfanumerisk adgangskode|Ja|Nej|Nej|
|Minimumlængde for adgangskode|Ja|Ja|Ja|
|Antal logonfejl, før enheden slettes|Ja|Ja|Ja|
|Minutter med inaktivitet, før enheden låses|Ja|Ja|Ja|
|Udløb af adgangskode (dage)|Ja|Ja|Ja|
|Husk adgangskoder, og undgå genbrug|Ja|Ja|Ja|

## <a name="encryption-settings"></a>Krypteringsindstillinger

|Indstillingsnavn|Ios|Android|Samsung Knox|
|---|---|---|---|
|Kræv datakryptering på <sup>enheder1</sup>|Nej|Ja|Ja|

<sup>1</sup> Med Samsung Knox kan du også kræve kryptering på lagerkort.

## <a name="jail-broken-setting"></a>Indstilling for fængselsbrud

|Indstillingsnavn|Ios|Android|Samsung Knox|
|---|---|---|---|
|Enheden kan ikke være beskadiget eller rodfæstet i fængsel|Ja|Ja|Ja|

## <a name="managed-email-profile-option"></a>Indstillingen Administreret mailprofil

Følgende indstilling kan forhindre brugerne i at få adgang til deres Microsoft 365 mail, hvis de bruger en manuelt oprettet mailprofil. Brugere på iOS-enheder skal slette deres manuelt oprettede mailprofil, før de kan få adgang til deres mail. Når profilen er blevet slettet, oprettes der automatisk en ny profil på enheden. Du kan finde oplysninger om, hvordan slutbrugerne kan blive kompatible, under [Der blev fundet en eksisterende mailkonto](/intune-user-help/existing-company-email-account-found).

|Indstillingsnavn|Ios|Android|Samsung Knox|
|---|---|---|---|
|Mailprofilen administreres|Ja|Nej|Nej|

## <a name="cloud-settings"></a>Cloudindstillinger

|Indstillingsnavn|Ios|Android|Samsung Knox|
|---|---|---|---|
|Kræv krypteret sikkerhedskopiering|Ja|Nej|Nej|
|Bloker cloudsikkerhedskopiering|Ja|Nej|Nej|
|Bloker dokumentsynkronisering|Ja|Nej|Nej|
|Bloker fotosynkronisering|Ja|Nej|Nej|
|Tillad Google-sikkerhedskopiering|NIELSEN|Nej|Ja|
|Tillad automatisk synkronisering af Google-konto|NIELSEN|Nej|Ja|

## <a name="system-settings"></a>Systemindstillinger

|Indstillingsnavn|Ios|Android|Samsung Knox|
|---|---|---|---|
|Bloker hentning af skærmbillede|Ja|Nej|Ja|
|Bloker afsendelse af diagnosticeringsdata fra enhed|Ja|Nej|Ja|

## <a name="application-settings"></a>Programindstillinger

|Indstillingsnavn|Ios|Android|Samsung Knox|
|---|---|---|---|
|Bloker videokonferencer på enheden|Ja|Nej|Nej|
|Bloker adgang til programlager|Ja|Nej|Ja|
|Kræv adgangskode ved adgang til programlageret|Nej|Ja|Ja|

## <a name="device-capabilities-settings"></a>Indstillinger for enhedsegenskaber

|Indstillingsnavn|Ios|Android|Samsung Knox|
|---|---|---|---|
|Bloker forbindelse med flytbart lager|Ja|Ja|Nej|
|Bloker Bluetooth forbindelse|Ja|Ja|Nej|

## <a name="additional-settings"></a>Yderligere indstillinger

Du kan angive følgende yderligere politikindstillinger ved hjælp af PowerShell-cmdlet'er & Security & Compliance Center. Du kan få flere oplysninger under [Security & Compliance Center PowerShell](/powershell/exchange/scc-powershell).

|Indstillingsnavn|Ios|Android|
|---|---|---|
|CameraEnabled|Ja|Ja|
|Områdeudskiftninger|Ja|Nej|
|Filmudskiftninger|Ja|Nej|
|TVShowsRating|Ja|Nej|
|AppsRatings|Ja|Nej|
|AllowVoiceDialing|Ja|Nej|
|AllowVoiceAssistant|Ja|Nej|
|AllowAssistantWhileLocked|Ja|Nej|
|AllowPassbookWhileLocked|Ja|Nej|
|MaxPasswordGracePeriod|Ja|Nej|
|PasswordQuality|Nej|Ja|
|SystemSecurityTLS|Ja|Nej|
|WLANEnabled|Nej|Nej|

## <a name="settings-supported-by-windows"></a>Indstillinger understøttes af Windows

Du kan administrere Windows 10 enheder ved at tilmelde dem som mobilenheder. Når en relevant politik er udrullet, skal brugere med Windows 10 enheder tilmelde sig Basic Mobility and Security, første gang de bruger den indbyggede mailapp til at få adgang til deres Microsoft 365 mail (kræver Azure AD Premium-abonnement).

Følgende indstillinger understøttes for Windows 10 enheder, der er tilmeldt som mobilenheder. Disse indstillinger forhindrer ikke brugere i at få adgang til Microsoft 365 ressourcer.

### <a name="security-settings"></a>Sikkerhedsindstillinger

- Kræv en alfanumerisk adgangskode

- Minimumlængde for adgangskode

- Antal logonfejl, før enheden slettes

- Minutter med inaktivitet, før enheden låses

- Udløb af adgangskode (dage)

- Husk adgangskoder, og undgå genbrug

> [!NOTE]
> Følgende indstillinger, der regulerer adgangskoder, styrer kun lokale Windows konti. Windows konti, der leveres via Joinforbind et domæne eller Azure Active Directory, påvirkes ikke af disse indstillinger.

### <a name="system-settings"></a>Systemindstillinger

Bloker afsendelse af diagnosticeringsdata fra enhed.

### <a name="additional-settings"></a>Yderligere indstillinger

Du kan angive disse yderligere politikindstillinger ved hjælp af PowerShell-cmdlet'er:

- AllowConvenienceLogon

- UserAccountControlStatus

- FirewallStatus

- AutoUpdateStatus

- AntiVirusStatus

- AntiVirusSignatureStatus

- SmartScreenEnabled

- WorkFoldersSyncUrl

## <a name="remotely-wipe-a-mobile-device"></a>Fjernsletning af en mobilenhed

Hvis en enhed mistes eller bliver stjålet, kan du fjerne følsomme organisationsdata og forhindre adgang til dine Microsoft 365 organisationsressourcer ved at udføre en sletning fra **Microsoft Purview-overholdelsesportalEn portal** >  **til forebyggelse af** >  **datatabAdministration af datatab**. Du kan udføre en selektiv sletning for kun at fjerne organisationsdata eller en fuld sletning for at slette alle oplysninger fra en enhed og gendanne dem til fabriksindstillingerne.

Du kan få flere oplysninger under [Slet en mobilenhed i Grundlæggende mobilitet og sikkerhed](wipe-mobile-device.md).

## <a name="related-content"></a>Relateret indhold

[Oversigt over grundlæggende mobilitet og sikkerhed for Microsoft 365](overview.md) (artikel)\
[Opret politikker for enhedssikkerhed i Grundlæggende mobilitet og sikkerhed](create-device-security-policies.md) (artikel)
