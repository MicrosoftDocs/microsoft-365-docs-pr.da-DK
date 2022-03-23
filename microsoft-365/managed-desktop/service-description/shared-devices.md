---
title: Delte enheder
description: Hvordan og hvornår skal du bruge delt enhedstilstand?
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
ms.openlocfilehash: 5ed7373bdcf9a8f2c8eda53c0bd249c6ba825992
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63594040"
---
# <a name="shared-devices"></a>Delte enheder

Microsoft Managed Desktop giver dig mulighed for at registrere enheder i "delt enhedstilstand" på samme måde som tilstanden for delte enheder, som [tilbydes Microsoft Intune](/mem/intune/configuration/shared-user-device-settings).

Enheder i denne tilstand er optimeret til situationer, hvor brugere ikke er bundet til et enkelt skrivebord og ofte skifter enhed. Frontlinemedarbejdere som f.eks. banklæsere eller personale, der er til at tage sig af. Du kan anvende en hvilken som helst af De [Microsoft-administrerede skrivebordsprofiler](profiles.md) på enheder i denne tilstand. Enheder, der er registreret i denne tilstand, har nogle vigtige forskelle:

- [Enhedslager](#device-storage) er optimeret til delte brugere.
- [Inaktive](#deletion-of-inactive-accounts) konti slettes.
- [Gæstekonti](#guest-accounts) understøttes ikke som standard.
- [Microsoft 365 til virksomhedslicens](#microsoft-365-apps-for-enterprise) er optimeret til delte enheder.

Da du vælger at bruge delt enhedstilstand, når du registrerer dig i Microsoft Managed Desktop, skal du, hvis du vil skifte fra denne tilstand på et senere tidspunkt, afmelde den og registrere den igen.

## <a name="when-to-use-shared-device-mode"></a>Hvornår skal jeg bruge delt enhedstilstand?

Enhver situation, hvor brugerne ofte skifter enhed.

Det kan f.eks. være, at banklæsere administrerer indskud på ét sted, men flytter til et back office for at hjælpe kunder med et realkreditlån. På hver af disse placeringer kører enheden forskellige programmer og er optimeret til disse opgaver, selvom de bruges af flere personer.

Personalet flytter typisk mellem lokaler og kontorer, når de interagerer med patienter. De kan logge på en arbejdsstation på et kontor, men oprette forbindelse til deres fjernskrivebord og tage noter, og gentage denne proces i et andet lokale med en anden patient.

## <a name="when-not-to-use-shared-device-mode"></a>Hvornår skal jeg ikke bruge delt enhedstilstand?

Tilstanden Delt enhed er ikke et godt valg i disse situationer:

- Når en brugers filer skal gemmes lokalt i stedet for i skyen
- Hvis brugeroplevelsen skal være anderledes for forskellige brugere på enheden
- Hvis det sæt programmer, som hver bruger har brug for, er væsentligt anderledes

## <a name="enroll-new-devices-in-shared-device-mode"></a>Tilmeld nye enheder i delt enhedstilstand

Uanset om du eller en partner håndterer registrering, kan du vælge at bruge delt enhedstilstand.

Hvis du selv tilmelder enheder, skal du følge trinnene i Manuel registrering og [](../get-started/manual-registration.md)derefter føje dem til gruppen Moderne enheder på arbejdspladsen **– delt enhedstilstand**.

> [!WARNING]
> Forsøg ikke at konvertere eksisterende Microsoft-administrerede skrivebordsenheder til delt enhedstilstand ved blot at føje dem til denne gruppe. De politikker, der anvendes, kan potentielt medføre OneDrive filer går permanent tabt.

Hvis du har en partnertilmeldingsenheder, skal du følge trinnene i [Partnerregistrering](../get-started/partner-registration.md), men føj **-** Delt til gruppemærket, som vist i følgende tabel:

| Enhedsprofil | Autopilot-gruppemærke (standardtilstand) | Gruppemærke (delt enhedstilstand) |
| ----- | ----- | ----- |
| Følsomme data | Microsoft365Managed_SensitiveData |  Microsoft365Managed_SensitiveData-Shared |
| Superbruger | Microsoft365Managed_PowerUser | Understøttes ikke |
| Standard  | Microsoft365Managed_Standard | Microsoft365Managed_Standard-Shared |

## <a name="consequences-of-shared-device-mode"></a>Konsekvenser af delt enhedstilstand

### <a name="device-storage"></a>Lager på enhed

Brugere af delte enheder skal have deres data sikkerhedskopieret i skyen, så de kan følge dem til andre enheder. Når du har registreret enheder i tilstanden delt enhed, skal du sørge for at aktivere OneDrive Filer [efter](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e#:~:text=%20Turn%20on%20Files%20On-Demand%20%201%20Make,files%20as%20you%20use%20them%20box.%20More%20) behov og kendte [mappeomdirigeringsfunktioner](/onedrive/redirect-known-folders). Denne fremgangsmåde minimerer den effekt, som hver brugerprofil har på enhedens lager. Enheder i delt enhedstilstand sletter automatisk brugerprofiler, hvis den ledige diskplads falder til under 25 %. Denne aktivitet er planlagt til midnat på enhedens lokale tid, medmindre lagerpladsen bliver kritisk begrænset.

Microsoft Managed Desktop bruger [SharedPC](/mem/intune/configuration/shared-user-device-settings-windows) CSP til at udføre disse handlinger, så sørg for, at du ikke selv bruger disse csp'er.

> [!IMPORTANT]
> Træn dine brugere om, at de, når de har downloadet en stor fil, skal bekræfte, at de kan se det grønne kontrolikon på filen, før de logger af. Hvis deres konto slettes som en del af oprydningshandlingerne, og filen ikke er helt overført i OneDrive, går filen permanent tabt.

### <a name="deletion-of-inactive-accounts"></a>Sletning af inaktive konti

Tilstanden Delt enhed fjerner alle konti, der ikke har været logget på i mere end 30 dage.

### <a name="guest-accounts"></a>Gæstekonti

Enheder i delt enhedstilstand tillader kun konti, der er forbundet til et domæne. Hvis du har brug for gæstekonti på en enhed, kan du arkivere en [ændringsanmodning](../working-with-managed-desktop/admin-support.md) for at anmode om, at de bliver aktiveret.

### <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Apps for enterprise

[Microsoft 365 Apps for enterprise](/microsoft-365/managed-desktop/get-started/m365-apps) gør det typisk muligt for en given bruger at installere disse apps på kun fem enheder ad gangen. I tilstanden delt enhed tæller appsene ikke med i grænsen, så de kan bruge dem under roaming mellem enheder. Installation og opdateringer af Microsoft 365 Apps for enterprise fungere som normalt.

### <a name="device-profiles"></a>Enhedsprofiler

I delt enhedstilstand kan du kun have én [enhedsprofil](profiles.md) på en given enhed. Desuden understøttes Enhedsprofilen for Power-bruger ikke i øjeblikket i delt enhedstilstand.

### <a name="apps-and-policies-assigned-to-users"></a>Apps og politikker, der er tildelt til brugere

På delte enheder skal du tildele apps eller politikker, som du administrerer selv, til *enhedsgrupper* og ikke brugergrupper. Tildeling til enhedsgrupper sikrer, at hver enkelt bruger har en mere ensartet oplevelse. Undtagelsen er [Firmaportal](#deploying-apps-with-company-portal).

## <a name="limitations-of-shared-device-mode"></a>Begrænsninger for delt enhedstilstand

### <a name="windows-hello"></a>Windows Hello

Windows Hello bruger chipkort-emulering til sikker [cache](/windows/security/identity-protection/hello-for-business/hello-faq) af bruger-pinkoder, så det minimerer det antal gange, brugerne skal godkendes. Dog tillader Windows kun 10 chipkort ad gangen på en given enhed. Når en 11. bruger logger på første gang, mister en af de eksisterende konti sit chipkort. De kan logge på, men deres pinkode cachelagres ikke.

### <a name="universal-print"></a>Universaludskrift

Når universel udskrivning installerer en printer til en enkelt bruger på en delt enhed, bliver printeren tilgængelig for alle brugere af den pågældende enhed. Det er ikke muligt at isolere printere mellem brugere på delte enheder.

## <a name="limitations-of-shared-device-mode-in-the-public-preview-release"></a>Begrænsninger for delt enhedstilstand i den offentlige prøveversion

### <a name="primary-user"></a>Primær bruger

Hver Microsoft Intune enhed har en primær bruger, som tildeles, når enheden er konfigureret af Autopilot. Men når enhederne deles, kræver Intune, at den primære bruger fjernes.

> [!IMPORTANT]
> Mens tilstanden delt enhed er i offentlig forhåndsvisning, skal du sørge for at fjerne den primære bruger ved at følge disse trin: Log på Microsoft Endpoint Manager Administration, vælg **EnhederAlle**> **enheder, vælg** en enhed, vælg derefter **PropertiesRemove**> primær bruger, og slet den bruger, der er angivet der.

### <a name="deploying-apps-with-company-portal"></a>Installation af apps med Firmaportal

Nogle apps behøver sandsynligvis ikke at være til stede på alle enheder, så det kan være, at du foretrækker, at brugerne kun installerer disse apps, når de skal bruge dem [fra Firmaportal](/mem/intune/user-help/install-apps-cpapp-windows).

Microsoft Managed Desktop deaktiverer Firmaportal som standard for enheder i delt enhedstilstand. Hvis du ønsker, at Firmaportal aktiveret, kan du arkivere en [ændringsanmodning](../working-with-managed-desktop/admin-support.md). Du skal dog være opmærksom på nogle begrænsninger i denne funktion i denne offentlige prøveversion:

- Hvis du vil gøre en app tilgængelig for brugere i [Firmaportal, skal](/mem/intune/apps/apps-deploy) du tildele en brugergruppe til den pågældende app i Intune og derefter føje hver enkelt bruger til den pågældende brugergruppe.
- Enheder kan ikke have en [primær bruger](#primary-user).
- Hvis du vil fjerne en app, som en bruger har Firmaportal, skal du fjerne appen fra alle brugere på enheden.

> [!CAUTION]
> Firmaportal understøtter ikke programmer, der er tildelt enhedsgrupper, som tilgængelige.

### <a name="redeployment-of-microsoft-365-apps-for-enterprise"></a>Ominstallation af Microsoft 365 Apps til Enterprise

Under den offentlige prøveversion, Microsoft 365 Apps skal geninstalleres, skal brugerne kontakte deres lokale supportmedarbejdere for at anmode om at få en agent til at hæve og geninstallere Microsoft 365 Apps for enterprise på enheden.

### <a name="microsoft-teams"></a>Microsoft Teams

Når en bruger Teams første gang, bliver brugeren bedt om at opdatere appen, før han eller hun kan bruge den. Når de tillader opdateringen, Teams automatisk automatisk opdateret i baggrunden.
