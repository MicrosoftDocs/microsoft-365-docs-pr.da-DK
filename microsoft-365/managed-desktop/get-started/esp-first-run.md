---
title: Første kørselsoplevelse med Autopilot og Statussiden For tilmelding
description: Sådan installeres ESP-oplevelsen, de anvendte indstillinger og konfigurationsændringer
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: ff4e7dc306ea3a017cb94261673d1325bc7cf94e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590668"
---
# <a name="first-run-experience-with-autopilot-and-the-enrollment-status-page"></a>Første kørselsoplevelse med Autopilot og Statussiden For tilmelding

Microsoft Managed Desktop bruger [både Windows Autopilot](/windows/deployment/windows-autopilot/windows-autopilot) og Microsoft Intune s [Statusside (Enrollment Status Page)](/windows/deployment/windows-autopilot/enrollment-status) til at give dine brugere den bedst mulige første kørselsoplevelse.

## <a name="initial-deployment"></a>Indledende installation

For at kunne levere ESP-oplevelsen skal du registrere enheder i Microsoft Managed Desktop-tjenesten. Du kan finde flere oplysninger om registrering [i Manuel registrering](../get-started/manual-registration.md) eller [Partnerregistrering](../get-started/partner-registration.md).
Statussiden for tilmelding og Autopilot til klargjort installation er som standard aktiveret i Microsoft Managed Desktop.

## <a name="autopilot-profile-settings"></a>Profilindstillinger for AutoPilot

Microsoft Managed Desktop anvender disse indstillinger i AutoPilot-profilen, der bruges til dine brugeres enheder:

| Indstilling | Værdi |
| ----- | ----- |
| Installationstilstand | Brugerbaseret |
| Deltag i Azure AD som | Azure AD forbundet |
| Sprog (område) | Brugervælger |
| Konfigurer tastatur automatisk | Nej |
| Licensvilkår for Microsoft-software | Skjul |
| Indstillinger for beskyttelse af personlige oplysninger | Skjul |
| Skjule Skift kontoindstillinger | Vis |
| Brugerkontotype| Standard |
| Tillad hvid udrejsning af OOBE (Out of Box Experience) | Ja |
| Anvend skabelonen Enhedsnavn | Ja |
| Angiv et navn | `MMD-%RAND:11%` |

## <a name="enrollment-status-page-settings"></a>Indstillinger for statusside for registrering

Microsoft-administreret skrivebord bruger disse indstillinger til oplevelsen af siden Status for registrering:

| Indstilling | Værdi |
| ------ | ------ |
| Vis status for konfiguration af app og profil | Ja |
| Vis en fejl, når installationen tager længere tid end det angivne antal minutter | 60 |
| Vis brugerdefineret meddelelse, når der opstår fejl i tidsgrænse | Nej |
| Tillad brugere at indsamle logfiler om installationsfejl| Ja |
| Vis kun side til enheder, der er klargjort af OOBE (out of box-oplevelse) | Ja |
| Bloker enhedsbrug, indtil alle apps og profiler er installeret | Ja |
| Tillad brugere at nulstille enheden, hvis der opstår installationsfejl | Ja |
| Tillad brugere at bruge enheden, hvis der opstår installationsfejl | Ja |
| Bloker enhedsbrug, indtil disse påkrævede apps er installeret, hvis de er tildelt til brugeren/enheden <ul><li> Moderne arbejdsplads – tidsrettelse</li><li>Moderne arbejdsplads – klientbibliotek</li></ul> | Ja |

Statussiden for registrering forekommer i tre faser. Du kan finde flere [oplysninger under Registreringsstatus for sidesporing](/mem/intune/enrollment/windows-enrollment-status#enrollment-status-page-tracking-information).

Oplevelsen fortsætter som følger:

1. Autopilot-oplevelsen starter, og brugeren angiver sine legitimationsoplysninger.
2. Enheden åbner statussiden for tilmelding og fortsætter gennem Forberedelse af enhed og Enhedsopstillingsfaser. Det tredje trin (Kontoopsætning) ignoreres *i øjeblikket i* konfigurationen af Microsoft Managed Desktop, fordi User ESP er deaktiveret. Enheden genstartes.
3. Efter genstart åbner enheden logonsiden Windows anden **bruger**.
4. Brugerne angiver deres legitimationsoplysninger igen, og skrivebordet åbnes.

> [!NOTE]
> Win32-apps installeres kun under ESP, hvis Windows 10 versionen er 1903 eller nyere.

![Startside for Autopilot-konfiguration, der viser "klargøring af enhed" og "enhedskonfiguration"-faser.](../../media/mmd-autopilot-screenshot.png)

## <a name="additional-prerequisites-for-autopilot-for-pre-provisioned-deployment"></a>Yderligere forudsætninger for Autopilot til klargjort udrulning

- Enheden skal have en kablet netværksforbindelse.
- Hvis du har enheder, der blev registreret via Microsoft Managed Desktop-portalen før august 2020, skal du framelde og registrere enhederne igen.
- Enheder skal have et fabriksbillede, der omfatter den kumulative opdatering fra november 2020 [19H1/19H2 2020.11C](https://support.microsoft.com/topic/november-19-2020-kb4586819-os-builds-18362-1237-and-18363-1237-preview-25cbb849-74af-b8b8-29b8-68aa925e8cc3) eller [20H1 2020.11C](https://support.microsoft.com/topic/november-30-2020-kb4586853-os-builds-19041-662-and-19042-662-preview-8fb07fb8-a7dd-ea62-d65e-3305da09f92e) , eller skal animeres med det seneste Microsoft Managed Desktop-billede.
- Fysiske enheder skal understøtte TPM 2.0 og enhedens udrunding. Virtuelle maskiner understøttes ikke. Før klargøringsprocessen bruges Windows autopilot-selvudrulningsfunktioner, så TPM 2.0 er påkrævet. TPM-bekræftelsesprocessen kræver også adgang til et sæt HTTPS-URL-adresser, der er entydige for hver TPM-udbyder. Du kan finde flere oplysninger i posten for Selvudrullende AutoPilot-tilstand og Automatisk klargøring i [Windows AutoPilot-netværk.](/mem/autopilot/networking-requirements#tpm)

## <a name="sequence-of-events-in-autopilot-for-pre-provisioned-deployment"></a>Sekvens af hændelser i Autopilot for klargjort udrulning

1. It-administratoren animerer eller nulstiller enheden, hvis det er nødvendigt.
2. It-administratoren starter enheden op, når frem til out of box-oplevelsen og trykker Windows-tasten fem gange.
3. It-administratoren vælger Windows Autopilot-klargøring og vælger derefter **Fortsæt**. På Windows Autopilot-konfiguration vises der oplysninger om enheden.
4. It-administratoren **vælger Klargøring** for at starte klargøringsprocessen.
5. Enheden starter ESP og gennemgår forberedelses- og konfigurationsfaser for enheder. Under fasen til konfiguration af enheden får du vist **Appinstallation x af x** (afhængigt af den nøjagtige konfiguration af ESP-profilen).
6. Trinnet til kontoopsætning er i øjeblikket sprunget over i konfigurationen af Microsoft Managed Desktop, da vi deaktiverer User ESP.
7. Enheden genstartes.

Efter genstart viser enheden den grønne statusskærm med en **Genseal-knap** .

> [!IMPORTANT]
> Kendte problemer:
>
> - ESP kører ikke igen efter Autopilot for en klargjort installations-reseal-funktion.
> - Enheden omdøbes ikke af Autopilot til klargøring. Enheden omdøbes kun, når du har gennemgåt brugerflowet i ESP.

## <a name="change-to-autopilot-and-enrollment-status-page-settings"></a>Skift til indstillinger for Autopilot og Statusside for tilmelding

Hvis konfigurationen, der bruges af Microsoft Managed Desktop, ikke helt opfylder dine behov, kan du indsende en supportanmodning via [administrationsportalen](https://portal.azure.com/). Her er nogle eksempler på de konfigurationstyper, du kan få brug for:

### <a name="autopilot-settings-change"></a>Autopilot-indstillinger ændres

Det kan være en god ide at anmode om en anden enhedsnavnskabelon. Du kan dog ikke ændre installationstilstand, deltage i Azure AD As, beskyttelse Indstillinger eller brugerkontotype.

### <a name="enrollment-status-page-settings-change"></a>Indstillinger for statussiden for registrering ændres

- Et længere antal minutter for indstillingen "Vis en fejl, når installationen tager længere tid end angivet antal minutter".
- Fejlmeddelelsen vises.
- Tilføjelse eller fjernelse af programmer i indstillingen "Bloker enhedsbrug, indtil disse nødvendige apps er installeret, hvis de er tildelt brugeren/enheden".

## <a name="required-applications"></a>Påkrævede programmer

- Du skal målrette programmer i enhedsgrupperne for *den moderne arbejdsplads* Test, Første, Hurtig og Bred. Programmer skal installeres i "System"-konteksten. Sørg for at udføre test med ESP i gruppen Test, før du tildeler dem til alle grupper.
- Ingen programmer bør kræve, at enheden genstarter. Vi anbefaler, at programmer indstilles til "Gør intet", når du opretter programpakken, hvis enheden kræver en genstart.
- Begræns påkrævede programmer til kun de kerneprogrammer, en bruger skal bruge, straks når de logger på enheden.
- Bevar den samlede størrelse af alle programmer samlet under 1 GB for at undgå timeouts i programinstallationsfasen.
- Ideelt set bør apps ikke have afhængigheder. Hvis du har apps, der *skal* have afhængigheder, skal du sørge for at konfigurere, teste og validere dem som en del af din ESP-evaluering.
- Microsoft Teams ikke medtages i ESP.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Trin til at komme i gang med Microsoft-administreret skrivebord

1. Få adgang [til administrationsportalen](access-admin-portal.md).
1. [Tilføj og bekræft administratorkontakter i administrationsportalen](add-admin-contacts.md).
1. [Juster indstillinger efter tilmelding](conditional-access.md).
1. Installér og [tildel Intune-firmaportal](company-portal.md).
1. [Tildel licenser](assign-licenses.md).
1. [Installér apps](deploy-apps.md).
1. [Klargør enheder](prepare-devices.md).
1. Konfigurer første kørselsoplevelse med Autopilot og Statussiden For tilmelding (denne artikel).
1. [Aktivér brugersupportfunktioner](enable-support.md).
1. [Gør dine brugere klar til at bruge enheder](get-started-devices.md).
1. [Kom i gang med appstyring](get-started-app-control.md).
