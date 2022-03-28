---
title: Aktivér domæne sammenføjede Windows 10 enheder, så de administreres af Microsoft 365 til virksomheder
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
description: Lær, hvordan du Microsoft 365 til at beskytte lokale Active Directory-Windows 10-enheder med blot nogle få trin.
ms.openlocfilehash: b12acbfbc9ff6e25c846d512781d8b72edf3f2fe
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598054"
---
# <a name="enable-domain-joined-windows-10-devices-to-be-managed-by-microsoft-365-business-premium"></a>Aktivér domæne sammenføjede Windows 10 enheder, så de administreres af Microsoft 365 Business Premium

> [!NOTE]
> Microsoft Defender for Business udrulles til Microsoft 365 Business Premium fra 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md).

Hvis din organisation bruger Windows Server Active Directory lokalt, kan du konfigurere Microsoft 365 Business Premium til at beskytte dine Windows 10-enheder, mens du stadig bevarer adgangen til lokale ressourcer, der kræver lokal godkendelse.
Du kan konfigurere denne beskyttelse ved at implementere enheder, der **er forbundet med Hybrid Azure AD**. Disse enheder er forbundet til både dit lokale Active Directory og dit Azure Active Directory.

## <a name="watch-configure-hybrid-azure-active-directory-join"></a>Se: Konfigurer hybrid Azure Active Directory joinforbindelse

I denne video beskrives trinnene til, hvordan du konfigurerer dette til det mest almindelige scenarie, som også er beskrevet i de følgende trin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3C9hO]
  
## <a name="before-you-begin"></a>Før du begynder

- Synkroniser brugere til Azure AD med Azure AD Forbind.
- Fuldfør Azure AD Forbind Organisationsenhed -synkronisering (OU).
- Sørg for, at alle de domænebrugere, du synkroniserer, har licenser til Microsoft 365 Business Premium.

Se [trinnene i Synkroniser domænebrugere til Microsoft](manage-domain-users.md) .

## <a name="1-verify-mdm-authority-in-intune"></a>1. Bekræft MDM-myndighed i Intune

Gå til [Endpoint Manager](https://endpoint.microsoft.com/#blade/Microsoft_Intune_Enrollment/EnrollmentMenu/overview), og vælg Microsoft Intune tilmelding af enhed på siden Oversigt **, og** kontrollér derefter, at **MDM-autoriteten** er **Intune**.

- Hvis **MDM-myndighed er** **Ingen**, skal du klikke på **MDM-myndigheden** for at angive **den til Intune**.
- Hvis **MDM-myndighed** er **Microsoft Office 365**, skal du gå til **DevicesEnroll-enheder**  >  og bruge dialogboksen Tilføj **MDM-myndighed** til højre for at tilføje **Intune MDM-myndighed** (dialogboksen **Tilføj MDM-myndighed** er kun tilgængelig, hvis **MDM-myndighed** er indstillet til Microsoft Office 365).

## <a name="2-verify-azure-ad-is-enabled-for-joining-computers"></a>2. Bekræft, at Azure AD er aktiveret til at deltage i computere

- Gå til Administration på , <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> og vælg **Azure Active Directory** (vælg Vis alle, Azure Active Directory ikke er synligt) på **listen Administration**. 
- I Azure Active Directory **Administration skal du** gå **til Azure Active Directory ,** vælge **Enheder og** derefter **Enhedsindstillinger**.
- **VerifyUsers may join devices to Azure AD** is enabled 
    1. Hvis du vil aktivere alle brugere, skal du angive til **Alle**.
    2. Hvis du vil aktivere bestemte brugere, skal du **angive til Valgt** for at aktivere en bestemt gruppe af brugere.
        - Føj de ønskede domænebrugere, der er synkroniseret i Azure AD, til [en sikkerhedsgruppe](../../admin/create-groups/create-groups.md).
        - Vælg **Vælg grupper for** at aktivere MDM-brugerområdet for den pågældende sikkerhedsgruppe.

## <a name="3-verify-azure-ad-is-enabled-for-mdm"></a>3. Bekræft, at Azure AD er aktiveret for MDM

- Gå til Administration på , og <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> vælg **Slutpunktsadministration (** vælg **Vis** alle, hvis **Endpoint Manager** ikke er synlig)
- I Microsoft Endpoint Manager **Administration skal** du gå **til Enheder** >  **Windows** >  **Windows EnrollmentAutomatic-registrering** > .
- Kontrollér, at MDM-brugerområdet er aktiveret.

    1. Hvis du vil tilmelde alle computere, skal  du angive til Alle for automatisk at tilmelde alle brugercomputere, der er forbundet til Azure AD, og nye computere, når brugerne føjer en arbejdskonto til Windows.
    2. Indstillet **til** Nogle for at tilmelde computere for en bestemt gruppe af brugere.
        -  Føj de ønskede domænebrugere, der er synkroniseret i Azure AD, til [en sikkerhedsgruppe](../create-groups/create-groups.md).
        -  Vælg **Vælg grupper for** at aktivere MDM-brugerområdet for den pågældende sikkerhedsgruppe.

## <a name="4-create-the-required-resources"></a>4. Opret de nødvendige ressourcer 

Udførelse af de nødvendige opgaver til konfiguration af [hybrid Azure AD-joinforbindelse](/azure/active-directory/devices/hybrid-azuread-join-managed-domains#configure-hybrid-azure-ad-join) er blevet forenklet ved hjælp af [Initialize-SecMgmtHybirdDeviceEnrollment-cmdlet'en](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) , der findes i [SecMgmt](https://www.powershellgallery.com/packages/SecMgmt) PowerShell-modulet. Når du aktiverer denne cmdlet, opretter og konfigurerer den nødvendige tjenesteforbindelsespunkt og gruppepolitik.

Du kan installere dette modul ved at gøre følgende fra en forekomst af PowerShell:

```powershell
Install-Module SecMgmt
```

> [!IMPORTANT]
> Det anbefales, at du installerer dette modul på den Windows Server, der kører Azure AD Forbind.

Hvis du vil oprette det påkrævede tjenesteforbindelsespunkt og gruppepolitik, skal du aktivere  [cmdlet'en Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) . Du skal bruge dine Microsoft 365 Business Premium legitimationsoplysninger som global administrator, når du udfører denne opgave. Når du er klar til at oprette ressourcerne, skal du aktivere følgende:

```powershell
PS C:\> Connect-SecMgmtAccount
PS C:\> Initialize-SecMgmtHybirdDeviceEnrollment -GroupPolicyDisplayName 'Device Management'
```

Den første kommando opretter en forbindelse til Microsoft Cloud, og når du bliver bedt om det, skal du angive Microsoft 365 Business Premium globale administratoroplysninger.

## <a name="5-link-the-group-policy"></a>5. Sammenkæd Gruppepolitik

1. I Gruppepolitik Management Console (GPMC) skal du højreklikke på den placering, hvor du vil sammenkæde politikken, og vælge Sammenkæd et eksisterende gruppepolitikobjekt *...* i genvejsmenuen.
2. Vælg den politik, der er oprettet i ovenstående trin, og klik derefter på **OK**.

## <a name="get-the-latest-administrative-templates"></a>Få de nyeste administrative skabeloner

Hvis du ikke kan se politikken Aktivér automatisk MDM-registrering ved hjælp af **standardoplysninger til Azure AD**, kan det skyldes, at du ikke har ADMX installeret til Windows 10, version 1803 eller nyere. Du kan løse problemet ved at følge disse trin (Bemærk: den nyeste MDM.admx er bagudkompatibel):

1. Download: [Administrative skabeloner (.admx) til Windows 10 opdatering fra oktober 2020 (20H2)](https://www.microsoft.com/download/102157).
2. Installér pakken på en domænecontroller.
3. Naviger, afhængigt af den administrative skabelonversion til mappen: **C:\Program Files (x86)\Microsoft Gruppepolitik\Windows 10 October 2020 Update (20H2)**.
4. **Omdøb mappen Politikdefinitioner** på stien ovenfor til **PolicyDefinitions**.
5. Kopiér **mappen PolicyDefinitions** til din SYSVOL-deling, der som standard er placeret på **C:\Windows\SYSVOL\domain\Policies**.
   - Hvis du planlægger at bruge et centralt politiklager for hele domænet, skal du tilføje indholdet af PolicyDefinitions der.
6. Hvis du har flere domænecontrollere, skal du vente på, at SYSVOL replikerer for, at politikkerne er tilgængelige. Denne fremgangsmåde fungerer også for alle fremtidige versioner af de administrative skabeloner.

På dette tidspunkt bør du kunne se politikken Aktivér automatisk **MDM-registrering ved hjælp af standard tilgængelige Azure AD-legitimationsoplysninger** .

## <a name="related-content"></a>Relateret indhold

[Synkroniser domænebrugere Microsoft 365](manage-domain-users.md) (artikel)\
[Opret en gruppe i Administration](../create-groups/create-groups.md) (artikel)\
[Selvstudium: Konfigurer Azure Active Directory for administrerede](/azure/active-directory/devices/hybrid-azuread-join-managed-domains) domæner (artikel) [De 10 bedste måder at sikre Microsoft 365 for business-planer](../security-and-compliance/secure-your-business-data.md)
