---
title: Grundlæggende mobilitet og sikkerhed
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
description: Grundlæggende mobilitet og sikkerhed kan hjælpe dig med at sikre og administrere dine mobilenheder.
ms.openlocfilehash: 04ee7e7dfbc4937d4add2e4c27e7f686b596fadb
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590421"
---
# <a name="capabilities-of-basic-mobility-and-security"></a>Grundlæggende mobilitet og sikkerhed

Grundlæggende mobilitet og sikkerhed kan hjælpe dig med at sikre og administrere mobilenheder som iPhones, iPads, Android-telefoner og Windows-telefoner, der bruges af licenserede Microsoft 365 brugere i organisationen. Du kan oprette politikker for administration af mobilenheder med indstillinger, der kan hjælpe med at kontrollere adgangen til din organisations Microsoft 365 og dokumenter for understøttede mobilenheder og apps. Hvis en enhed mistes eller bliver stjålet, kan du slette enheden eksternt for at fjerne følsomme virksomhedsoplysninger.

## <a name="supported-operating-systems"></a>Understøttede operativsystemer

Følg vejledningen Microsoft Intune for de understøttede minimumsoperativsystemer til enheder ved hjælp af Standardmobilitet og -sikkerhed. Du kan få mere at vide under [Understøttede operativsystemer i Intune](/mem/intune/fundamentals/supported-devices-browsers).

Du kan bruge Grundlæggende mobilitet og sikkerhed til at sikre og administrere følgende enheder.

- iOS
- Android (herunder Samsung Knox)<sup>1</sup>
- Windows <sup>2, 3</sup>

<sup>1</sup> Efter juni 2020 kan Android-versioner, der er nyere end 9, ikke administrere adgangskodeindstillinger med undtagelse af Samsung Knox-enheder.

<sup>2</sup> Adgangskontrol til Windows 8.1 RT-enheder er begrænset til Exchange ActiveSync.

<sup>3</sup> Adgangskontrol til Windows 10 kræver et abonnement, der Azure AD Premium, og enheden skal være forbundet til Azure Active Directory.

> [!NOTE]
> Enheder, der allerede er tilmeldt tidligere OS-versioner, fortsætter med at fungere, selvom egenskaberne kan ændres uden varsel.

Hvis personer i din organisation bruger mobilenheder, der ikke understøttes af Grundlæggende mobilitet og sikkerhed, kan det være en ide at blokere Exchange ActiveSync-appadgang til Microsoft 365-mail for disse enheder for at gøre din organisations data mere sikre. Se, hvordan du blokerer Exchange ActiveSync under [Administrer indstillinger for enhedsadgang i Grundlæggende mobilitet og sikkerhed](manage-device-access-settings.md).

## <a name="access-control-for-microsoft-365-email-and-documents"></a>Adgangskontrol til Microsoft 365 og dokumenter

De understøttede apps til de forskellige typer mobilenheder i følgende tabel beder brugerne om at tilmelde sig Grundlæggende mobilitet og sikkerhed, hvor der er en ny politik for administration af mobilenheder, der gælder for en brugers enhed, og brugeren ikke tidligere har tilmeldt enheden. Hvis en brugers enhed ikke overholder en politik, kan det være, at en bruger er blokeret fra at få adgang til Microsoft 365-ressourcer i disse apps, afhængigt af hvordan du konfigurerer politikken, eller at brugeren har adgang, men Microsoft 365 rapporterer om en overtrædelse af politikken.

|**Produkt**|**iOS**|**Android**|
|:-----|:-----|:-----|
|**Exchange** Exchange ActiveSync indbygget mail og tredjepartsapps, f.eks. TouchDown, der bruger Exchange ActiveSync version 14.1 eller nyere. |Mail |Mail |
| Office and  **OneDrive for Business** |Outlook </br>OneDrive </br>Word </br>Excel </br>PowerPoint|**På telefoner og tablets**:<br/>Outlook <br/> OneDrive <br/> Word <br/> Excel <br/> PowerPoint <br/> **Kun på telefoner:** <br/> Office Mobile |

> [!NOTE]
>
> - Understøttelse af iOS 10.0 og nyere versioner omfatter iPhone og iPad enheder.
> - Administration af BlackBerry OS-enheder understøttes ikke af Basic Security og Mobility. Brug BlackBerry Business Cloud Services (BBCS) fra BlackBerry til at administrere BlackBerry OS-enheder. Blackberry-enheder, der kører Android,er understøttet som almindelige Android-enheder
> - Brugere vil ikke blive bedt om at tilmelde sig og vil ikke blive blokeret eller rapporteret for overtrædelse af politikken, hvis de bruger mobilbrowseren til at få adgang til Microsoft 365 SharePoint-websteder, dokumenter i Office Online eller mail i Outlook Web App.

Følgende diagram viser, hvad der sker, når en bruger med en ny enhed logger på en app, der understøtter adgangskontrol med Grundlæggende mobilitet og Sikkerhed. Brugeren er blokeret fra at Microsoft 365 adgang til ressourcer i appen, indtil brugeren tilmelder sin enhed.

:::image type="content" source="../../media/basic-mobility-security/bms-1-access-control.png" alt-text="Adgangskontrol for grundlæggende mobilitet og sikkerhed.":::

> [!NOTE]
> Politikker og adgangsregler, der er oprettet i Grundlæggende mobilitet og sikkerhed for Microsoft 365 Business Standard, tilsidesætter Exchange ActiveSync politikker for mobilenhedspostkasse og regler for enhedsadgang, der er oprettet i Exchange Administration. Når en enhed er tilmeldt Basic Mobility and Security for Microsoft 365 Business Standard, ignoreres enhver Exchange ActiveSync-postkassepolitik eller adgangsregel for enheder, der anvendes på enheden. Du kan få mere at vide Exchange ActiveSync under  [Exchange ActiveSync i Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="policy-settings-for-mobile-devices"></a>Politikindstillinger for mobilenheder

Hvis du opretter en politik om at blokere adgang med bestemte indstillinger slået til, blokeres brugere fra at få adgang til Microsoft 365-ressourcer, når de bruger en understøttet app, der er angivet i [Access-kontrol for Microsoft 365-mail](capabilities.md) og -dokumenter.

De indstillinger, der kan blokere brugeres adgang Microsoft 365 ressourcer, findes i disse sektioner:

- Sikkerhed

- Kryptering

- Jail broken

- Administreret mailprofil

Følgende diagram viser f.eks., hvad sker der, når en bruger med en registreret enhed ikke er kompatibel med en sikkerhedsindstilling i en politik for administration af mobilenheder, der gælder for brugerens enhed. Brugeren logger på en app, der understøtter adgangskontrol med Grundlæggende mobilitet og Sikkerhed. De er blokeret fra Microsoft 365 adgang til ressourcer i appen, indtil deres enhed overholder sikkerhedsindstillingen.

:::image type="content" source="../../media/basic-mobility-security/bms-2-device-not-compliant.png" alt-text="Meddelelse om overholdelse af grundlæggende mobilitet og sikkerhed.":::

De følgende afsnit viser de politikindstillinger, du kan bruge til at sikre og administrere mobilenheder, der opretter forbindelse til Microsoft 365 i organisationen.

## <a name="security-settings"></a>Sikkerhedsindstillinger

|**Navn på indstilling**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Kræve en adgangskode|Ja|Ja|Ja|
|Undgå enkel adgangskode|Ja|Nej|Nej|
|Kræve en alfanumerisk adgangskode|Ja|Nej|Nej|
|Minimum adgangskodelængde |Ja|Ja|Ja|
|Antal logonfejl, før enheden slettes |Ja|Ja|Ja|
|Minutters inaktivitet, før enheden er låst |Ja|Ja|Ja|
|Udløb af adgangskode (dage) |Ja|Ja|Ja|
|Husk adgangskodehistorikken, og forbyd genbrug |Ja|Ja|Ja|

## <a name="encryption-settings"></a>Krypteringsindstillinger

|**Navn på indstilling**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Kræv datakryptering på <sup>enheder1</sup> |Nej|Ja|Ja|

<sup>1</sup> Med Samsung Knox kan du også kræve kryptering på lagerkort.

## <a name="jail-broken-setting"></a>Indstilling for jail broken

|**Navn på indstilling**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Enheden må ikke være jail broken eller rooted |Ja|Ja|Ja|

## <a name="managed-email-profile-option"></a>Indstillingen Administreret mailprofil

Følgende indstilling kan blokere brugere i at få adgang til deres Microsoft 365 mail, hvis de bruger en manuelt oprettet mailprofil. Brugere på iOS-enheder skal slette deres manuelt oprettede mailprofil, før de kan få adgang til deres mail. Når profilen er blevet slettet, oprettes der automatisk en ny profil på enheden. Du kan finde en vejledning til, hvordan slutbrugere kan overholde reglerne, [under Der blev fundet en eksisterende mailkonto](/intune-user-help/existing-company-email-account-found).

|**Navn på indstilling**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Mailprofil administreres |Ja|Nej|Nej|

## <a name="cloud-settings"></a>Skyindstillinger

|**Navn på indstilling**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Kræv krypteret sikkerhedskopiering |Ja|Nej|Nej|
|Bloker sikkerhedskopiering i skyen |Ja|Nej|Nej|
|Bloker dokumentsynkronisering |Ja|Nej|Nej|
|Bloker fotosynkronisering  |Ja|Nej|Nej|
|Tillad sikkerhedskopiering af Google  |I/T|Nej|Ja|
|Tillad automatisk synkronisering af Google-konto  |I/T|Nej|Ja|

## <a name="system-settings"></a>Systemindstillinger

|**Navn på indstilling**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Bloker skærmklip |Ja|Nej|Ja|
|Bloker afsendelse af diagnostiske data fra enhed |Ja|Nej|Ja|

## <a name="application-settings"></a>Programindstillinger

|**Navn på indstilling**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Bloker videomøder på enhed |Ja|Nej|Nej|
|Bloker adgang til programlager |Ja|Nej|Ja|
|Kræv adgangskode, når du åbner programlageret |Nej|Ja|Ja|

## <a name="device-capabilities-settings"></a>Indstillinger for enhedsegenskaber

|**Navn på indstilling**|**iOS** |**Android**|**Samsung Knox**|
|:-----|:-----|:-----|:-----|
|Bloker forbindelse med flytbart lager |Ja|Ja|Nej|
|Blokere Bluetooth forbindelse |Ja|Ja|Nej|

## <a name="additional-settings"></a>Yderligere indstillinger

Du kan angive følgende yderligere politikindstillinger ved hjælp af Security & Compliance Center PowerShell-cmdlet'er. Du kan finde flere oplysninger  [underSecurity & Compliance Center PowerShell](/powershell/exchange/scc-powershell).

|**Navn på indstilling**|**iOS** |**Android**|
|:-----|:-----|:-----|
|CameraEnabled|Ja|Ja|
|OmrådeRatings|Ja|Nej|
|MoviesRatings|Ja|Nej|
|TVShowsRating |Ja|Nej|
|AppsRatings |Ja|Nej|
|AllowVoiceDialing |Ja|Nej|
|AllowVoiceAssistant |Ja|Nej|
|AllowAssistantWhileLocked  |Ja|Nej|
|AllowPassbookWhileLocked |Ja|Nej|
|MaxPasswordGracePeriod |Ja|Nej|
|PasswordQuality |Nej|Ja|
|SystemSecurityTLS  |Ja|Nej|
|WLANEnabled  |Nej|Nej|

## <a name="settings-supported-by-windows"></a>Indstillinger understøttes af Windows

Du kan administrere Windows 10 enheder ved at tilmelde dem som mobilenheder. Når en gældende politik er implementeret, skal brugere med Windows 10-enheder tilmelde sig Grundlæggende mobilitet og sikkerhed, første gang de bruger den indbyggede mailapp til at få adgang til deres Microsoft 365-mail (kræver Azure AD Premium-abonnement).

Følgende indstillinger understøttes for Windows 10 enheder, der er tilmeldt som mobilenheder. Denne indstilling blokerer ikke brugere fra at få adgang Microsoft 365 ressourcer.

### <a name="security-settings"></a>Sikkerhedsindstillinger

- Kræve en alfanumerisk adgangskode

- Minimum adgangskodelængde

- Antal logonfejl, før enheden slettes

- Minutters inaktivitet, før enheden er låst

- Udløb af adgangskode (dage)

- Husk adgangskodehistorikken, og forbyd genbrug

> [!NOTE]
> Følgende indstillinger, der kontrollerer adgangskoder, styrer kun lokale Windows konti. Windows konti, der leveres via joinforbindelse til et domæne eller Azure Active Directory, påvirkes ikke af disse indstillinger.

### <a name="system-settings"></a>Systemindstillinger

Bloker afsendelse af diagnostiske data fra enheden.

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

Hvis en enhed mistes eller bliver stjålet, kan du fjerne følsomme organisationsdata og hjælpe med at forhindre adgang til dine Microsoft 365-organisationsressourcer ved at udføre en sletning fra Security & Compliance Center > **Forebyggelse** >  af datatabAdministration **af datatab**. Du kan udføre en selektiv sletning for kun at fjerne organisationsdata eller en komplet sletning for at slette alle oplysninger fra en enhed og gendanne den til fabriksindstillingerne.

Du kan få mere at vide  [underWipe a mobile device in Basic Mobility and Security](wipe-mobile-device.md).

## <a name="related-content"></a>Relateret indhold

[Oversigt over Grundlæggende mobilitet og sikkerhed for Microsoft 365](overview.md) (artikel)\
[Opret sikkerhedspolitikker for enheder i Grundlæggende mobilitet og sikkerhed](create-device-security-policies.md) (artikel)
