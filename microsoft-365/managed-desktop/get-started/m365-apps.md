---
title: Microsoft 365 Apps for enterprise
description: Sådan installeres Microsoft 365 Apps, hvordan de opdateres, og hvordan indstillinger administreres
keywords: ændringsoversigt
ms.service: m365-md
ms.sitesec: library
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 82a0bbc4811b3f2be23403717b0a0ffb485d7c74
ms.sourcegitcommit: 584b4757f715a3eedf748858461c568f45137438
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/15/2022
ms.locfileid: "63589781"
---
# <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Apps for enterprise

## <a name="initial-deployment"></a>Indledende installation

Microsoft Managed Desktop sikrer, Microsoft 365 Apps for enterprise (64-bit) er installeret som en del af billedet på alle [programenheder](../service-description/device-list.md). Alle følgende programmer skal være til stede på enheden, når den leveres:

- Word
- Excel
- PowerPoint
- Outlook
- Publisher
- Access
- Skype for Business
- OneNote

Denne fremgangsmåde minimerer netværkspåvirkningen og sikrer, at brugerne kan være produktive, så snart de modtager deres enhed. Vi udruller derefter flere politikker på administrerede enheder for at konfigurere programmerne til brug.

> [!NOTE]
> Microsoft Teams installeres separat fra Microsoft 365 Apps for enterprise og medtages ikke i basisbilledet.

### <a name="available-deployment-to-users"></a>Tilgængelige udrulning for brugere

Hvis en bruger ikke har en Microsoft 365 Apps sin enhed af en eller anden grund, kan du bruge en pakke til at returnere enheden til den forventede tilstand. Føj brugeren til gruppen **moderne Office og Office365_Install** så bliver apps tilgængelige for dem i Firmaportal.

### <a name="microsoft-365-apps-for-enterprise-32-bit"></a>Microsoft 365 Apps for enterprise (32-bit)

Microsoft Managed Desktop understøtter ikke udrulning af 32-bit-versionen af Microsoft 365 Apps for enterprise.

## <a name="updates-to-microsoft-365-apps"></a>Opdateringer til Microsoft 365 Apps

Microsoft 365 Apps er indstillet til at opdatere på den [månedlige virksomhedskanal](/deployoffice/overview-update-channels#monthly-enterprise-channel-overview). Denne fremgangsmåde giver brugerne nye Office-funktioner hver måned, men de modtager kun én opdatering pr. måned efter en forudsigelig tidsplan for udgivelse. Opdateringerne frigives den anden tirsdag i måneden; disse opdateringer kan omfatte funktions-, sikkerheds- og kvalitetsopdateringer. Disse opdateringer sker automatisk og trækkes direkte fra Office CDN for den pågældende kanal.

Microsoft Managed Desktop forskudte hver version for at identificere potentielle problemer i dit miljø. Vi fuldfører udrulningen fra Microsoft 365 App-produktgruppen. Microsoft Managed Desktop planlægger udgivelser af opdateringer til forskellige grupper, så der er tid til validering og test, som følger:

- Test: nul dage
- Første: nul dage
- Hurtig: tre dage
- Bred: syv dage

Microsoft Managed Desktop angiver en deadline for en opdatering [på syv dage](/deployoffice/configure-update-settings-microsoft-365-apps) for enheder. Når opdateringen er tilgængelig, skal den installeres inden for syv dage. Brugerne får [besked](/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) om, at der kræves opdateringer flere steder: programmet, på proceslinjen 12 timer før deadline, og de modtager en 15-minutters advarsel før deadline. Alle Microsoft 365 Apps være lukket, for at opdateringen kan fuldføres.

### <a name="pausing-or-rolling-back-an-update"></a>Pause eller tilbagerulning af en opdatering

Hvis du af en eller anden grund har brug for at afbryde eller Microsoft 365 en appopdatering på pause eller vende tilbage, kan du arkivere en [anmodning om administratorsupport](../working-with-managed-desktop/admin-support.md) via microsoft-portalen til administreret skrivebord.

I løbet af en udgivelse overvåger Microsoft Managed Desktop fejlhastighederne for alle Microsoft 365 Apps. Hvis vi ser en betydelig forskel i kvaliteten mellem den nye version og den forrige version, kan vi kontakte dig via Microsoft Managed Desktop Admin-portalen.

Afhængigt af alvorsgraderne gør vi begge følgende:

- Spørg, om du vil afbryde udgivelsen midlertidigt, eller
- Informer dig om, at vi har taget skridt til at afhjælpe et problem.

### <a name="delivery-optimization"></a>Leveringsoptimering

Leveringsoptimering er en peer-to-peer-distributionsteknologi, der er tilgængelig i Windows 10. Det giver enheder mulighed for at dele indhold, f.eks. opdateringer, som de enheder, der er downloadet fra Microsoft via internettet. Us Delivery Optimization kan hjælpe med at reducere netværkets båndbredde, fordi en enhed kan hente dele af opdateringen fra en anden enhed på dens lokale netværk i stedet for at hente opdateringen helt fra Microsoft.

[Leveringsoptimering](/deployoffice/delivery-optimization) er som standard aktiveret på enheder, der kører Windows 10 Enterprise eller Windows 10 Education versioner.

## <a name="settings-managed-by-microsoft-managed-desktop"></a>Indstillinger administreret af Microsoft Managed Desktop

Microsoft administrerer nogle indstillinger som en del af tjenesten. Microsoft Managed Desktop administrerer ikke en oprindelig plan Office Sikkerhed. Du kan dog selv angive en ved at følge vejledningen i Indstillinger [du administrerer](#settings-you-manage).

### <a name="update-settings"></a>Opdateringsindstillinger

Microsoft Managed Desktop vedligeholder alle [opdateringsindstillinger](/deployoffice/configure-update-settings-microsoft-365-apps) for administrerede enheder, og du bør ændre disse indstillinger.

| Indstilling | Standardværdi | Beskrivelse |
| ------ | ------ | ------ |
| Indstil opdateringer til at ske automatisk | Aktiveret | Denne politik er konfigureret for at sikre, at Office enheder kan holdes opdateret fra skyen. |
| Angiv en deadline, når opdateringer skal anvendes | Syv dage | Politikken **UpdateDeadline** bruges til at konfigurere den udvidede periode, som brugerne har, før en opdatering håndhæves på enheden. Denne deadlinepolitik udløser også [beskeder til](/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) brugeren om de ændringer, der kræves på enheden. |
| Udskyde opdateringer på en enhed i et stykke tid | Se beskrivelse | Denne politik er konfigureret forskelligt for hver gruppe af enheder til opdateringsstyring. Det er påkrævet, at Microsoft Managed Desktop opfylder sine opdateringsmål: <ul> <li> Test: nul dage </li> <li>Første: nul dage</li><li>Hurtig syv dage</li><li>Bred: 21 dage</li></ul> |
| Opdateringsindstillinger for meddelelser | Falsk | Indstillingen "Skjul meddelelser om opdateringer" er indstillet til **Falsk** på Microsoft-administrerede skrivebordsenheder for at give den bedste opdateringsoplevelse for brugerne ved at give dem besked, når der kræves opdateringer.[](/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps)|
| Angiv en placering til at søge efter opdateringer | Månedlig virksomhedskanal | En kombination af **politikkerne UpdatePath** **og UpdateChannel** bruges efter behov for at opnå opdateringsplanen. Disse politikker er indstillet til at sikre, at Office-enheder modtager opdateringer direkte fra CDN til den månedlige virksomhedskanal.|
| Angiv målversionen af Microsoft 365 Apps | Se beskrivelse | Politikken Destinationsversion bruges nogle gange af Microsoft Managed Desktop til at rulle en bestemt version af Office.|
| Skjul indstillingen for at aktivere eller deaktivere Office automatiske opdateringer | Aktiveret | Denne indstilling er påkrævet, for at Microsoft Managed Desktop kan opfylde sine opdateringsmål for Microsoft 365-programmer. |
| Indstillinger for første kørsel | Se beskrivelse | Der er flere indstillinger, der påvirker funktionsmåden første gang, Office køres. |
| Acceptér licensvilkårene på vegne af slutbrugeren | Deaktiveret | Første gang en bruger åbner en Microsoft 365-app, bliver brugeren bedt om at acceptere licensvilkårene. Hvis du vil acceptere licensvilkårene på vegne af dine brugere, skal du arkivere en supportanmodning hos Microsoft Managed Desktop Operations-teamet og bede om, at denne indstilling aktiveres. |
| Skjule Outlook afkrydsningsfeltet mobil | Deaktiveret | Første gang en bruger åbner Outlook, bliver brugeren bedt om at installere Outlook Mobile. Hvis du ikke vil have dine brugere til at se dette afkrydsningsfelt, skal du arkivere en supportanmodning hos Microsoft Managed Desktop Operations-teamet og bede om, at denne indstilling er aktiveret for dine enheder. |

## <a name="other-settings"></a>Andre indstillinger

Der er andre Microsoft 365 appindstillinger, som Microsoft Managed Desktop eventuelt kan konfigurere på dine vegne.

| Indstilling | Standardværdi | Beskrivelse |
| ------ | ------ | ------ |
| Deaktiver personlige OneDrive | Deaktiveret | Nogle organisationer er bekymrede for, at brugere har adgang til både virksomhedsfiler og personlige filer på deres enheder. Du kan arkivere en supportanmodning med Microsoft Managed Desktop Operations-teamet og bede om, at denne indstilling aktiveres. |

## <a name="settings-you-manage"></a>Indstillinger du administrerer

Der er mange andre politikker, som Microsoft Managed Desktop endnu ikke har angivet som en del af vores tjeneste. Du kan konfigurere disse politikker ved hjælp Microsoft Intune, som bruger [Office Skypolitik](/DeployOffice/overview-office-cloud-policy-service#how-the-policy-configuration-is-applied). Hvis du vil angive disse politikker, skal du følge disse trin:

1. Log på Microsoft Endpoint Manager Administration.
1. Vælg **Apps**.
1. Vælg **Politikker for at Office apps**, og vælg derefter **Opret**.
1. Gør følgende **på** siden Opret politikkonfiguration:
    - Angiv et navn.
    - Angiv en valgfri beskrivelse.
    - Under **tildelinger skal** du vælge, om denne politik gælder for alle brugere af Microsoft 365 Apps for enterprise eller blot for brugere, der har anonym adgang til dokumenter ved hjælp Office på internettet.
    - Vælg den **AAD sikkerhedsgruppe, der** er tildelt til politikkonfigurationen. Hver politikkonfiguration kan kun tildeles til én gruppe. Hver gruppe kan kun tildeles én politikkonfiguration.
    - Konfigurer de politikindstillinger, der skal medtages i politikkonfigurationen. Du kan søge efter navnet på politikindstillingen for at finde den politikindstilling, du vil konfigurere. Du kan også filtrere, hvis politikken er en anbefalet grundlinje for sikkerhed, og hvis politikken er blevet konfigureret. Kolonnen Platform angiver, om politikken er anvendt på Microsoft 365 Apps for enterprise til Windows enheder, Office på internettet eller alle.
1. Når du har foretaget dine valg, skal du vælge **Opret**.

> [!NOTE]
> Office konfigurationspolitikker understøtter kun brugerbaseret installation
