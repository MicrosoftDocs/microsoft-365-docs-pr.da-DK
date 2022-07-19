---
title: Aktivér domænetilsluttede Windows 10 enheder, der skal administreres af Microsoft 365 til virksomheder
f1.keywords:
- CSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
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
description: Få mere at vide om, hvordan du gør det muligt for Microsoft 365 at beskytte lokale Active Directory-joinforbundne Windows 10 enheder med nogle få trin.
ms.openlocfilehash: 3d3c4cbe30481a2c74783f943ac0cedbe4004dc5
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858807"
---
# <a name="manage-windows-devices-with-microsoft-365-business-premium"></a>Administrer Windows-enheder med Microsoft 365 Business Premium

Hvis din organisation bruger Windows Server Active Directory i det lokale miljø, kan du konfigurere Microsoft 365 Business Premium til at beskytte dine Windows-enheder, samtidig med at du bevarer adgang til ressourcer i det lokale miljø, der kræver lokal godkendelse.

Hvis du vil konfigurere dette, skal du implementere **Hybrid Azure AD tilsluttede enheder**. Disse enheder er forbundet til både dit Active Directory i det lokale miljø og dit Azure Active Directory.

> [!NOTE]
> Microsoft Defender til virksomheder udrulles til Microsoft 365 Business Premium kunder fra den 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../security/defender-business/mdb-overview.md).

## <a name="watch-configure-hybrid-azure-active-directory-join"></a>Se: Konfigurer Hybrid Azure Active Directory-joinforbindelse

I denne video beskrives trinnene til, hvordan du konfigurerer dette til det mest almindelige scenarie, hvilket også beskrives i de efterfølgende trin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE3C9hO]
  
## <a name="before-you-begin"></a>Før du begynder

- Synkroniser brugere for at Azure AD med Azure AD Opret forbindelse.
- Fuldfør synkronisering af Azure AD Opret forbindelse til organisationsenhed.
- Sørg for, at alle de domænebrugere, du synkroniserer, har licenser til Microsoft 365 Business Premium.

Se [Synkroniser domænebrugere til Microsoft 365 for at](../admin/setup/manage-domain-users.md) få flere oplysninger.

## <a name="possible-device-actions-and-statuses"></a>Mulige enhedshandlinger og -statusser
  
![På listen Enhedshandlinger kan du se enhedernes tilstande.](./../media/a621c47e-45d9-4e1a-beb9-c03254d40c1d.png)

Enheder og deres tilknyttede handlinger kan have følgende tilstande:
  
|**Status**|**Beskrivelse**|
|:-----|:-----|
|Administreret af Intune  |Administreret af Microsoft 365 Business Premium.  |
|Afventer tilbagetrækning  |Microsoft 365 Business Premium er ved at gøre klar til at fjerne firmadata fra enheden.  |
|Udgå i gang  |Microsoft 365 Business Premium fjerner i øjeblikket firmadata fra enheden.  |
|Tilbagetrækning mislykkedes  | Det lykkedes ikke at fjerne firmadatahandlingen.  |
|Tilbagetrækning annulleret  |Tilbagetrækningshandlingen blev annulleret.  |
|Afventer sletning  |Venter på, at fabriksnulstillingen starter.  |
|Sletning er i gang  |Fabriksnulstilling er udstedt.  |
|Sletning mislykkedes  |Fabriksnulstillingen kunne ikke udføres.  |
|Sletning annulleret  |Fabrikssletning blev annulleret.  |
|Usunde  |En handling venter (eller er i gang), men enheden har ikke tjekket ind i mere end 30 dage.  |
|Slet ventende  |Sletningshandlingen afventer.  |
|Opdaget  |Microsoft 365 Business Premium har registreret enheden.  |

## <a name="1-verify-mdm-authority-in-intune"></a>1. Kontrollér MDM-autoriteten i Intune

Gå til Microsoft Endpoint Manager Administration ([https://endpoint.microsoft.com](https://endpoint.microsoft.com/#blade/Microsoft_Intune_Enrollment/EnrollmentMenu/overview)), vælg **Enhedsregistrering**, og sørg derefter for, at **MDM-autoriteten** er **Intune** på siden **Oversigt**.

- Hvis **MDM-autoritet** er **None (Ingen**), skal du klikke på **MDM-autoriteten** for at angive den til **Intune**.
- Hvis **MDM-autoritet** er **Microsoft Office 365**, skal du gå til **Enheder** > **Tilmelde enheder** og bruge dialogboksen **Tilføj MDM-autoritet** til højre for at tilføje **Intune MDM-autoritet** (dialogboksen **Tilføj MDM-autoritet** er kun tilgængelig, hvis **MDM-autoriteten** er angivet til Microsoft Office 365).

## <a name="2-verify-azure-ad-is-enabled-for-joining-computers"></a>2. Kontrollér, at Azure AD er aktiveret til tilslutning af computere

1. Gå til Microsoft 365 Administration på , <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> og vælg **Azure Active Directory** (vælg Vis alle, hvis Azure Active Directory ikke er synligt) på listen **Administration centre**. 

2. I **Azure Active Directory Administration** skal du gå til **Azure Active Directory** , vælge **Enheder** og derefter **Enhedsindstillinger**.

3. Kontrollér **, at brugere kan tilmelde sig enheder til Azure AD** er aktiveret 

    1. Hvis du vil aktivere alle brugere, skal du angive til **Alle**.

    2. Hvis du vil aktivere bestemte brugere, skal du angive Til **Valgt** for at aktivere en bestemt gruppe af brugere.

        - Føj de ønskede domænebrugere, der er synkroniseret i Azure AD, til en [sikkerhedsgruppe](../admin/create-groups/create-groups.md).

        - Vælg **Vælg grupper** for at aktivere MDM-brugerområde for den pågældende sikkerhedsgruppe.

## <a name="3-verify-azure-ad-is-enabled-for-mdm"></a>3. Kontrollér, at Azure AD er aktiveret for MDM

1. Gå til Microsoft 365 Administration på , <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> og vælg **Administration af slutpunkt** (vælg **Vis alle**, hvis **Endpoint Manager** ikke er synlig)

2. I **Microsoft Endpoint Manager Administration** skal du gå til **Enheder** > **Windows-tilmelding** > **automatisk tilmelding** til **Windows** > .

3. Kontrollér, at MDM-brugerområdet er aktiveret.

    1. Hvis du vil tilmelde alle computere, skal du indstille til **Alle** for automatisk at tilmelde alle de brugercomputere, der er tilsluttet Azure AD og nye computere, når brugerne føjer en arbejdskonto til Windows.
  
    2. Angiv til **Nogle** for at tilmelde computerne for en bestemt gruppe af brugere.
  
        -  Føj de ønskede domænebrugere, der er synkroniseret i Azure AD, til en [sikkerhedsgruppe](/admin/create-groups/create-groups.md).
  
       -  Vælg **Vælg grupper** for at aktivere MDM-brugerområde for den pågældende sikkerhedsgruppe.

## <a name="4-create-the-required-resources"></a>4. Opret de nødvendige ressourcer 

Udførelse af de påkrævede opgaver for at [konfigurere hybrid Azure AD joinforbindelse](/azure/active-directory/devices/hybrid-azuread-join-managed-domains#configure-hybrid-azure-ad-join) er blevet forenklet ved hjælp af cmdlet'en [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md), der findes i [SecMgmt](https://www.powershellgallery.com/packages/SecMgmt) PowerShell-modulet. Når du aktiverer denne cmdlet, oprettes og konfigureres det påkrævede tjenesteforbindelsespunkt og gruppepolitik.

Du kan installere dette modul ved at aktivere følgende fra en forekomst af PowerShell:

```powershell
Install-Module SecMgmt
```

> [!IMPORTANT]
> Installér dette modul på den Windows Server, der kører Azure AD Opret forbindelse.

Hvis du vil oprette det nødvendige tjenesteforbindelsespunkt og den nødvendige gruppepolitik, skal du aktivere cmdlet'en  [Initialize-SecMgmtHybirdDeviceEnrollment](https://github.com/microsoft/secmgmt-open-powershell/blob/master/docs/help/Initialize-SecMgmtHybirdDeviceEnrollment.md) . Du skal bruge dine Microsoft 365 Business Premium globale administratorlegitimationsoplysninger, når du udfører denne opgave. Når du er klar til at oprette ressourcerne, skal du aktivere følgende:

```powershell
PS C:\> Connect-SecMgmtAccount
PS C:\> Initialize-SecMgmtHybirdDeviceEnrollment -GroupPolicyDisplayName 'Device Management'
```

Den første kommando opretter forbindelse til Microsoft-cloudmiljøet, og når du bliver bedt om det, skal du angive dine Microsoft 365 Business Premium globale administratorlegitimationsoplysninger.

## <a name="5-link-the-group-policy"></a>5. Sammenkobling af gruppepolitik

1. Højreklik på den placering, hvor du vil sammenkæde politikken, i GPMC (Gruppepolitik Management Console), og vælg *Sammenkæd et eksisterende gruppepolitikobjekt...* i genvejsmenuen.

2. Vælg den politik, der er oprettet i trinnet ovenfor, og klik derefter på **OK**.

## <a name="get-the-latest-administrative-templates"></a>Hent de nyeste administrative skabeloner

Hvis du ikke kan se politikken **Aktivér automatisk MDM-tilmelding ved hjælp af standardlegitimationsoplysninger for Azure AD**, kan det skyldes, at ADMX ikke er installeret til Windows 10, version 1803 eller nyere. Du kan løse problemet ved at følge disse trin (Bemærk! Den nyeste MDM.admx er bagudkompatibel):

1. Download: [Administrative skabeloner (.admx) til Windows 10 oktober 2020-opdatering (20H2)](https://www.microsoft.com/download/102157).

2. Installér pakken på en domænecontroller.

3. Naviger, afhængigt af versionen af Administrative skabeloner til mappen: **C:\Program Files (x86)\Microsoft Gruppepolitik\Windows 10 oktober 2020 Update (20H2)**.

4. Omdøb mappen **Politikdefinitioner** i ovenstående sti til **PolicyDefinitions**.

5. Kopiér mappen **PolicyDefinitions** til sysvol-sharet, der som standard er placeret på `C:\Windows\SYSVOL\domain\Policies`.

   Hvis du planlægger at bruge et centralt politiklager for hele domænet, skal du tilføje indholdet af PolicyDefinitions der.

6. Hvis du har flere domænecontrollere, skal du vente på, at SYSVOL replikeres, før politikkerne er tilgængelige. Denne procedure fungerer også for alle fremtidige versioner af de administrative skabeloner.

På dette tidspunkt bør du kunne se politikken **Aktivér automatisk MDM-tilmelding ved hjælp af standard Azure AD tilgængelige legitimationsoplysninger**.

## <a name="related-content"></a>Relateret indhold

- [Synkroniser domænebrugere til Microsoft 365](../admin/setup/manage-domain-users.md)

- [Opret en gruppe i Administration](../admin/create-groups/create-groups.md)

- [Selvstudium: Konfigurer hybridforbindelse til Azure Active Directory for administrerede domæner](/azure/active-directory/devices/hybrid-azuread-join-managed-domains)

- [Konfigurer selvbetjeningsadgangskoder](../admin/add-users/let-users-reset-passwords.md)

- [Konfigurer selvbetjent gruppeadministration](/azure/active-directory/enterprise-users/groups-self-service-management)

- [Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>Næste mål

[Klargør til installation af Office-klient](m365bp-prepare-for-office-client-deployment.md)