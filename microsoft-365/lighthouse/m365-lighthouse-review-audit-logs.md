---
title: Gennemse overvågningslogge i Microsoft 365 Fyrtårn
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: vivkuma
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Få mere at vide om, hvordan du gennemser overvågningslogge for udbydere af administrerede tjenester ved hjælp af Microsoft 365 Lighthouse.
ms.openlocfilehash: a357d6d4383fb967b09d1ce3dc1be68d7fd2ca4f
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017504"
---
# <a name="review-audit-logs-in-microsoft-365-lighthouse"></a>Gennemse overvågningslogge i Microsoft 365 Fyrtårn

Microsoft 365 Lighthouse-overvågningslogge registrerer handlinger, der genererer en ændring i Lighthouse eller andre Microsoft 365 tjenester. Opret, rediger, slet, tildel og fjernhandlinger alle opret overvågningshændelser, som du kan gennemse. Overvågning er som standard aktiveret for alle kunder. Den kan ikke deaktiveres.

## <a name="before-you-begin"></a>Før du begynder

Hvis du vil have vist overvågningslogge, skal du have en af følgende tilladelser:

- Azure Active Directory rolle (Azure AD) – Global administrator af partnerlejer

- Rolle i Microsoft Partnercenter – Administratoragent

## <a name="review-audit-logs"></a>Gennemse overvågningslogfiler

1. Vælg **Overvågningslogge** i venstre navigationsrude i Lighthouse.

    > [!NOTE]
    > Det kan tage op til 1 time at se nye logge. Gå til den respektive tjeneste for at se de seneste ændringer.

2. Filtrer loggene efter behov ved hjælp af følgende indstillinger:

    - **Datointerval** – forrige måned, uge eller dag.
    - **Lejere** – lejerkoder eller kundelejernavne.
    - **Activity** – Microsoft 365 aktivitetstype, der svarer til den udførte handling. Du kan få flere oplysninger i tabellen [Aktiviteter](#activities) .
    - **Initieret af** – Who startede handlingen.

3. Vælg en log på listen for at få vist alle detaljer, herunder brødteksten i **anmodningen** .

    Hvis du vil eksportere logdata til en fil med kommaseparerede værdier (.csv), skal du vælge **Eksportér**.

## <a name="activities"></a>Aktiviteter

I følgende tabel vises de aktiviteter, der registreres i overvågningslogge for fyrtårnet. Listen kan ændres, når der oprettes nye handlinger. Du kan bruge den aktivitet, der er angivet i overvågningsloggen, til at se, hvilken handling der blev startet.<br><br>

| Aktivitetsnavn | Område i fyrtårn | Handling startet | Tjenesten er påvirket |
|--|--|--|--|
| **anvend** eller **udrul** | Lejere | Anvend en udrulningsplan | Azure AD, Microsoft Endpoint Manager (MEM) |
| **assignTag** | Lejere | Anvend et mærke fra en kunde | Fyrtårn |
| **changeDeploymentStatus** eller **assign** | Lejere | Opdater status for handlingsplan for udrulningsplan | Fyrtårn |
| **managedTenantOperations** | Lejere | Få vist oplysninger om en udrulningsplan | Azure AD |
| **offboardTenant** | Lejere | Deaktiver en kunde | Fyrtårn |
| **resetTenantOnboardingStatus** | Lejere | Reaktiv en kunde | Fyrtårn |
| **tenantTags** | Lejere | Opret eller slet et mærke | Fyrtårn |
| **tenantCustomizedInformation** | Lejere | Opret, opdater eller slet et kundewebsted eller kontaktoplysninger | Fyrtårn |
| **unassignTag** | Lejere | Fjern et mærke fra en kunde | Fyrtårn |
| **Validere** | Lejere | Test en udrulningsplan | Azure AD |
| **blockUserSignin** | Brugere | Bloker logon | Azure AD |
| **confirmUsersCompromised** | Brugere | Bekræft, at en bruger er kompromitteret | Azure AD |
| **dismissUsersRisk** | Brugere | Afvis brugerrisiko | Azure AD |
| **resetUserPassword** | Brugere | Nulstil adgangskode | Azure AD |
| **getConditionalAccessPolicies** | Brugere | Vis ca-politikker, der kræver MFA | Azure AD |
| **getTenantIDToTenantNameMap** | Brugere | Søg efter id'er | Azure AD |
| **getUsers** | Brugere | Søg efter brugere | Azure AD |
| **getUsersWithoutMfa** | Brugere | Vis brugere, der ikke er registreret til MFA | Azure AD |
| **getSsprEnabledButNotRegisteredUsers** | Brugere | Vis brugere, der ikke er registreret til SSPR | Azure AD |
| **setCustomerSecurityDefaultsEnabledStatus** | Brugere | Aktivér multifaktorgodkendelse (MFA) med sikkerhedsstandarder | Azure AD |
|**getCompliancePolicyInfo** | Enheder | Få vist en politik | MEM
|**getDeviceCompliancePolicyStates** | Enheder | Vis politiktilstande | MEM
|**getDeviceCompliancePolicySettingStates** | Enheder | Vis indstillinger, der ikke overholder angivne standarder | MEM
|**getDeviceCompliancePolicySettingStateSummaries** | Enheder | Vis enheder, der ikke overholder angivne standarder | MEM
|**getTenantsDeviceCompliancePolicies** | Enheder | Sammenlign politikker | MEM
| **restartDevice** | Enheder | Genstarte | MEM |
| **syncDevice** | Enheder | Sync | MEM |
| **rebootNow** | Trusselsstyring | Genstarte | MEM |
| **klargøring igen** | Windows 365 | Prøv at klargøre igen | Windows 365 |
| **getDeviceUserInfo** | Trusselsstyring | Få vist brugeroplysninger for administreret enhed  | MEM |
| **getManagedDevice**, **remoteActionAudits** eller **deviceActionResults** | Trusselsstyring | Få vist oplysninger om administreret enhed  | MEM |
| **windowsDefenderScanFull** | Trusselsstyring | Fuld scanning | MEM |
| **windowsDefenderScan** | Trusselsstyring | Hurtig scanning | MEM |
| **windowsDefenderUpdateSignatures** | Trusselsstyring | Opdater antivirus | MEM |

## <a name="next-steps"></a>Næste trin

Brug Microsoft Graph API til at få adgang til flere overvågningshændelser, hvis det er nødvendigt. Du kan få flere oplysninger under [Oversigt over administration af flere lejere ved hjælp af api'en til Microsoft 365 Lighthouse](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>Relateret indhold

[Microsoft 365 Ofte stillede spørgsmål om Fyrtårn](m365-lighthouse-faq.yml) (artikel)\
[Få vist dine Azure Active Directory roller i Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (artikel)