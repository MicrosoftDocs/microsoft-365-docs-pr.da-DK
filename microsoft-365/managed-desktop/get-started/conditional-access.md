---
title: Juster indstillinger efter tilmelding
description: Sådan udelader du visse Microsoft-konti
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: a5ff8a9a662eb442b7a18726463f14e914d4a133
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587546"
---
# <a name="adjust-settings-after-enrollment"></a>Juster indstillinger efter tilmelding

Når du har fuldført tilmeldingen til Microsoft Managed Desktop, skal nogle administrationsindstillinger muligvis justeres. Hvis du vil kontrollere og justere, om det er nødvendigt, skal du følge disse trin:

1. Gennemgå de Microsoft Intune og Azure Active Directory, der er beskrevet i næste afsnit.
2. Hvis nogen af elementerne gælder for dit miljø, skal du foretage justeringerne som beskrevet.
3. Hvis du vil dobbelttjekke, at alle indstillinger er korrekte, kan du køre værktøjet til [](https://aka.ms/mmdart) vurdering af parathed igen for at sikre, at der ikke er nogen konflikter med Microsoft Managed Desktop.

> [!NOTE]
> Når dine handlinger fortsætter i de efterfølgende måneder, og du foretager ændringer efter tilmelding til politikker i Microsoft Intune, Azure Active Directory eller Microsoft 365, der påvirker Microsoft Managed Desktop, er det muligt, at Microsoft Managed Desktop kan stoppe med at fungere korrekt. For at undgå problemer med tjenesten skal du kontrollere de specifikke indstillinger, [](../get-ready/readiness-assessment-fix.md) der er beskrevet i Løs problemer, der blev fundet af værktøjet til vurdering af parathed, før du ændrer de politikker, der er angivet der. Du kan også når som helst køre værktøjet til vurdering af parathed igen.

## <a name="microsoft-intune-settings"></a>Microsoft Intune indstillinger

| Indstilling | Beskrivelse |
| ------ | ------ |
| Autopilot-udrulningsprofil | Hvis du bruger autopilotpolitikker, skal du opdatere hver enkelt for at udelukke **enheder med moderne arbejdsplads – hele** Azure AD-gruppen. <br><br> **Sådan opdaterer du Autopilot-politikkerne:** <br><br> Under **Opgaver skal du** **i grupperne** Udeladt vælge gruppen Enheder til moderne arbejdsplads **-** alle Azure AD-enheder, der blev oprettet under tilmelding til Microsoft-administreret skrivebord. <br><br> Microsoft Managed Desktop vil også have oprettet en Autopilot-profil, som har "Moderne arbejdsplads" i navnet ( **Den moderne Workplace Autopilot-profil**). Når du opdaterer dine egne Autopilot-profiler, skal du  sikre, at du ikke udelader gruppen Moderne arbejdsenheder **-** Alle Azure AD fra den **Moderne Workplace Autopilot-profil**, der er oprettet af Microsoft Managed Desktop. |
| Politikker for betinget adgang | Hvis du opretter nye politikker for betinget adgang i forbindelse med Azure AD, Microsoft Intune eller Microsoft 365 Defender til slutpunkt efter microsoft-administreret skrivebordsregistrering, skal du udelade Microsoft **Modern Workplace Service Accounts** Azure AD-gruppen fra dem. Få mere at vide under [Betinget adgang: Brugere og grupper](/azure/active-directory/conditional-access/concept-conditional-access-users-groups). Microsoft Managed Desktop vedligeholder separate politikker for betinget adgang for at begrænse adgangen til disse konti. <br><br> **Sådan gennemgås Microsoft Managed Desktop-politikken for betinget adgang (Moderne arbejdsplads – Sikker arbejdsstation):** <br><br> Gå til Microsoft Endpoint Manager og gå til **Betinget adgang** i **Slutpunktssikkerhed**. Rediger ikke nogen politikker for betinget adgang i Azure AD, der er oprettet af Microsoft Managed Desktop, og som har "Moderne arbejdsplads" i navnet. |
| Multifaktorgodkendelse | Hvis du opretter nye krav til multifaktorgodkendelse i politikker for betinget adgang til Azure AD, Intune eller Microsoft 365 Defender til slutpunkt efter microsoft-administreret skrivebordsregistrering, skal du udelade Azure AD-gruppen  konti for moderne arbejdsplads-konti fra dem. Få mere at vide under [Betinget adgang: Brugere og grupper](/azure/active-directory/conditional-access/concept-conditional-access-users-groups). Microsoft Managed Desktop vedligeholder separate politikker for betinget adgang for at begrænse adgangen for medlemmer af denne gruppe. <br><br> **Sådan gennemgås Microsoft Managed Desktop-politikken for betinget adgang (Moderne arbejdsplads -):** <br><br> Gå til Microsoft Endpoint Manager og gå til **Betinget adgang** i **Slutpunktssikkerhed**.
| Windows 10 opdateringsring | For alle Windows 10 politikker for opdateringsring, du har oprettet, skal du udelade gruppen Moderne enheder på arbejdspladsen **– alle** Azure AD-grupper fra hver politik. Få mere at vide under [Opret og tildel opdateringsringe](/mem/intune/protect/windows-10-update-rings#create-and-assign-update-rings). <br><br> Microsoft Managed Desktop vil også have oprettet nogle politikker for opdateringsring, som alle har "Moderne arbejdsplads" i navnet. Eksempel: <ul><li>Opdateringspolitik for den moderne arbejdsplads [Bred]</li><li>Opdateringspolitik for den moderne arbejdsplads [Fast]</li><li>Politik for opdatering af den moderne arbejdsplads [Første]</li><li>Opdateringspolitik for den moderne arbejdsplads [Test]</li></ul> <br>Når du opdaterer dine egne politikker, skal du sikre  dig, at du ikke udelader gruppen Enheder på den moderne arbejdsplads **–** alle Azure AD fra dem, der blev oprettet af Microsoft Managed Desktop. |

## <a name="azure-active-directory-settings"></a>Azure Active Directory indstillinger

Nulstilling af adgangskode via selvbetjening: Hvis du bruger selvbetjening til nulstilling af adgangskode for alle brugere, skal du justere tildelingen, så microsoft Managed Desktop Service-konti udelades.

**Sådan tilpasses denne opgave:**

1. Opret en dynamisk Azure AD-gruppe til alle brugere undtagen *Microsoft* Managed Desktop-tjenestekonti
1. Brug denne gruppe til tildeling i stedet for "alle brugere".

For at hjælpe dig med at finde og udelade tjenestekontiene er her et eksempel på en dynamisk forespørgsel, du kan bruge:

```Console
(user.objectID -ne null) and (user.userPrincipalName -ne "MSADMIN@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSADMININT@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_SOC_RO@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_WDGSOC@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSTEST@TENANT.onmicrosoft.com")
```

I denne forespørgsel skal du erstatte `@TENANT` med dit lejerdomænenavn.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Trin til at komme i gang med Microsoft-administreret skrivebord

1. Få adgang [til administrationsportalen](access-admin-portal.md).
1. [Tilføj og bekræft administratorkontakter i administrationsportalen](add-admin-contacts.md).
1. Juster indstillinger efter tilmelding (denne artikel).
1. Installér og [tildel Intune-firmaportal](company-portal.md).
1. [Tildel licenser](assign-licenses.md).
1. [Installér apps](deploy-apps.md).
1. [Klargør enheder](prepare-devices.md).
1. Konfigurer første [kørselsoplevelse med Autopilot og Statussiden For tilmelding](esp-first-run.md).
1. [Aktivér brugersupportfunktioner](enable-support.md).
1. [Gør dine brugere klar til at bruge enheder](get-started-devices.md).
1. [Kom i gang med appstyring](get-started-app-control.md).
