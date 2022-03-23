---
title: Gennemse overvågningslogfiler
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
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
description: For administrerede tjenesteudbydere, der bruger Microsoft 365 Lighthouse, kan du få mere at vide om, hvordan du gennemser overvågningslogfiler.
ms.openlocfilehash: e16f6eb83d1fdc9f5aea2fdc6463959cc07e5650
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63593684"
---
# <a name="review-audit-logs"></a>Gennemse overvågningslogfiler

Microsoft 365 fyrtårnsrevision registrerer handlinger, der genererer en ændring i Fyrtårn eller andre Microsoft 365 tjenester. Opret, rediger, slet, tildel og fjernhandlinger opret alle overvågningshændelser, som du kan gennemse. Som standard er overvågning aktiveret for alle kunder. Den kan ikke deaktiveres.

## <a name="before-you-begin"></a>Før du begynder

Hvis du vil have vist overvågningslogfiler, skal du have en af følgende tilladelser:

- Azure Active Directory (Azure AD) – global administrator for partnerlejeren

- Microsoft Partnercenter-rolle – administratoragent

## <a name="review-audit-logs"></a>Gennemse overvågningslogfiler

1. I venstre navigationsrude i Fyrtårn skal du **vælge Overvågningslogger**.

    > [!NOTE]
    > Det kan tage op til 1 time at se nye logfiler. Gå til den pågældende tjeneste for at se de seneste ændringer.

2. Filtrer logfilerne efter behov ved at bruge følgende indstillinger:

    - **Datointerval** – Forrige måned, uge eller dag.
    - **Lejere** – Lejermærker eller kundelejernavne.
    - **Aktivitet** – Microsoft 365 aktivitetstype, der svarer til den handling, der er foretaget. Du kan finde flere oplysninger i [tabellen](#activities) Aktiviteter.
    - **Startet af** – Who startet handlingen.

3. Vælg en log på listen for at få vist alle oplysninger, herunder **brødteksten i anmodningen** .

    Hvis du vil eksportere logdata til en fil med kommaseparerede værdier (.csv), skal du vælge **Eksportér**.

## <a name="activities"></a>Aktiviteter

Følgende tabel viser aktiviteter registreret i Fyrtårns overvågningslogfiler. Listen kan blive ændret, efterhånden som der oprettes nye handlinger. Du kan bruge aktiviteten, der er angivet i overvågningsloggen, til at se, hvilken handling der blev startet.<br><br>

| Aktivitetens navn | Område i Fyrtårn | Handling startet | Påvirket tjeneste |
|--|--|--|--|
| **anvende** eller **installere** | Lejere | Anvend en udrulningsplan | Azure AD, Microsoft Endpoint Manager (MEM) |
| **assignTag** | Lejere | Anvend et mærke fra en kunde | Fyrtårn |
| **changeDeploymentStatus** eller **tildel** | Lejere | Opdater status for handlingsplan for installationsplan | Fyrtårn |
| **managedTenantOperations** | Lejere | Få vist oplysninger om en installationsplan | Azure AD |
| **offboardTenant** | Lejere | Deaktiver en kunde | Fyrtårn |
| **resetTenantOnboardingStatus** | Lejere | Reactive a customer | Fyrtårn |
| **lejerTags** | Lejere | Opret eller slet et mærke | Fyrtårn |
| **tenantCustomizedInformation** | Lejere | Oprette, opdatere eller slette et kundewebsted eller kontaktoplysninger | Fyrtårn |
| **fjerne tildelingsmærke** | Lejere | Fjern et mærke fra en kunde | Fyrtårn |
| **valider** | Lejere | Test en installationsplan | Azure AD |
| **blockUserSignin** | Brugere | Bloker logon | Azure AD |
| **confirmUsersCompromised** | Brugere | Bekræft, at en bruger er blevet kompromitteret | Azure AD |
| **dismissUsersRisk** | Brugere | Afvis brugerrisici | Azure AD |
| **resetUserPassword** | Brugere | Nulstil adgangskode | Azure AD |
| **getConditionalAccessPolicies** | Brugere | Vis nøglecenterpolitikker, der kræver MFA | Azure AD |
| **getTenantIDToTenantNameMap** | Brugere | Søg efter ID'er | Azure AD |
| **getUsers** | Brugere | Søg efter brugere | Azure AD |
| **getUsersWithoutMfa** | Brugere | Få vist brugere, der ikke er registreret til MFA | Azure AD |
| **getSsprEnabledNotRegisteredUsers** | Brugere | Få vist brugere, der ikke er registreret for SSPR | Azure AD |
| **setCustomerSecurityDefaultsEnabledStatus** | Brugere | Aktivér multifaktorgodkendelse (MFA) med sikkerhedsstandard | Azure AD |
|**getCompliancePolicyInfo** | Enheder | Få vist en politik | MEM
|**getDeviceCompliancePolicyStates** | Enheder | Vis politik tilstande | MEM
|**getDeviceCompliancePolicySettingStates** | Enheder | Få vist ikke-kompatible indstillinger | MEM
|**getDeviceCompliancePolicySettingStateSummaries** | Enheder | Få vist ikke-kompatible enheder | MEM
|**getTenantsDeviceCompliancePolicies** | Enheder | Sammenlign politikker | MEM
| **restartDevice** | Enheder | Genstart | MEM |
| **syncDevice** | Enheder | Synkroniser | MEM |
| **genstartNow** | Administration af trusler | Genstart | MEM |
| **genopdeling** | Windows 365 | Prøv klargøring igen | Windows 365 |
| **getDeviceUserInfo** | Administration af trusler | Få vist brugeroplysninger for administreret enhed  | MEM |
| **getManagedDevice**, **remoteActionAudits** eller **deviceActionResults** | Administration af trusler | Få vist oplysninger om administreret enhed  | MEM |
| **windowsDefenderScanFull** | Administration af trusler | Fuld scanning | MEM |
| **windowsDefenderScan** | Administration af trusler | Hurtig scanning | MEM |
| **windowsDefenderUpdateSignatures** | Administration af trusler | Opdater antivirus | MEM |

## <a name="next-steps"></a>Næste trin

Hvis du har brug for flere oplysninger, kan du bruge Microsoft Graph API til at få adgang til flere overvågningshændelser. Få mere at vide under [Oversigt over administration af flere lejere ved hjælp Microsoft 365 Lighthouse API](/graph/managedtenants-concept-overview).

## <a name="related-content"></a>Relateret indhold

[Microsoft 365 ofte stillede spørgsmål om fyrtårn](m365-lighthouse-faq.yml) (artikel)
