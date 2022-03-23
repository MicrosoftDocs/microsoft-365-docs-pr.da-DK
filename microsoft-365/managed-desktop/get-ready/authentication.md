---
title: Forbered lokale ressourcers adgang til Microsoft Managed Desktop
description: Vigtige trin for at sikre, at et Azure AD kan kommunikere med lokalt AD for at levere godkendelse
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 3db3d469f7b417035e6ae11507c54c6bad871a89
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63587675"
---
# <a name="prepare-on-premises-resources-access-for-microsoft-managed-desktop"></a>Forbered lokale ressourcers adgang til Microsoft Managed Desktop

I Microsoft-administreret skrivebord bliver enheder automatisk forbundet til Azure Active Directory (Azure AD). Hvis du bruger et lokalt Active Directory, skal du derfor sikre dig, at enheder, der er forbundet til Azure AD, kan kommunikere med dit lokale Active Directory.

> [!NOTE]  
> *Hybrid* Azure AD-joinforbindelse understøttes ikke af Microsoft Managed Desktop.

Azure Active Directory gør det muligt for brugerne at benytte enkeltstående Sign-On enkeltstående bruger (SSO). Enkelt logon betyder, at de typisk ikke behøver at angive legitimationsoplysninger, hver gang de bruger ressourcer.

Du kan finde oplysninger om Azure Active Directory i Sådan gør du[: Planlæg din implementering af Azure AD-joinforbindelse](/azure/active-directory/devices/azureadjoin-plan). Du kan finde baggrundsoplysninger om enkeltstående Sign-On (SSO) på enheder, der er forbundet til Azure AD, under Sådan fungerer [SSO til lokale ressourcer på enheder, der er forbundet til Azure AD](/azure/active-directory/devices/azuread-join-sso#how-it-works).

I denne artikel forklares de ting, du skal kontrollere for at sikre, at apps og andre ressourcer, der afhænger af den lokale Active Directory-forbindelse, fungerer problemfrit med Microsoft Managed Desktop.

## <a name="single-sign-on-for-on-premises-resources"></a>Enkelt Sign-On for lokale ressourcer

Enkeltlogo (SSO – Single Sign-On) ved hjælp af UPN og adgangskode er som standard aktiveret på Microsoft-administrerede stationære enheder. Men brugerne kan også bruge Windows Hello for Business, hvilket kræver nogle ekstra konfigurationstrin.

### <a name="single-sign-on-by-using-upn-and-password"></a>Enkelt Sign-On ved hjælp af UPN og adgangskode

I de fleste organisationer vil brugerne kunne bruge SSO til at godkende med UPN og adgangskode på Microsoft-administrerede stationære enheder. For at sikre at denne funktion fungerer, skal du dobbelttjekke følgende:

- Bekræft, at Azure AD Forbind er konfigureret. Den skal bruge en lokal Active Directory-server, der Windows Server 2008 R2 eller nyere.
- Bekræft, at Azure AD Forbind kører en understøttet version. Den skal være indstillet til at synkronisere disse tre attributter med Azure AD:
    - DNS-domænenavn for det lokale Active Directory (hvor brugerne er placeret).
    - Net BIOS for dit lokale Active Directory (hvor brugerne er placeret).
    - BRUGERENS SAM-kontonavn.

### <a name="single-sign-on-by-using-windows-hello-for-business"></a>Enkelt Sign-On ved hjælp af Windows Hello for Business

Microsoft-administrerede skrivebordsenheder giver også brugerne en hurtig og adgangskodefri oplevelse ved at anvende Windows Hello for Business. For at sikre at Windows Hello for Business fungerer, uden at dine brugere skal angive deres respektive UPN og adgangskode, skal du gå til Konfigurer [Azure AD-enheder til lokale Single-Sign On using Windows Hello for Business for](/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso-base) at kontrollere kravene og derefter følge de angivne trin der.

## <a name="apps-and-resources-that-use-authentication"></a>Apps og ressourcer, der bruger godkendelse

Se Forstå [overvejelser for programmer og ressourcer](/azure/active-directory/devices/azureadjoin-plan#understand-considerations-for-applications-and-resources) i Azure-indholdssættet for at få fuld vejledning i at konfigurere apps til at arbejde med Azure Active Directory. Oversigt:

| App eller tjeneste | Opgave |
| ------ | ------ |
| Skybaserede apps | Hvis du bruger **skybaserede apps**, f.eks. dem, der er føjet til Azure AD-appgalleriet, kræver de fleste ikke yderligere forberedelse for at fungere med Microsoft Managed Desktop. Win32-apps, der ikke bruger Web Account Manager (WAM), kan dog stadig bede brugerne om godkendelse. |
| Apps, der hostes lokalt | For apps, der **hostes lokalt, skal** du sørge for at føje disse apps til listen over pålidelige websteder i dine browsere. Dette trin gør det muligt Windows at arbejde problemfrit, uden at brugerne bliver bedt om legitimationsoplysninger. Hvis du vil tilføje apps, skal du [se Websteder, der er](../working-with-managed-desktop/config-setting-ref.md#trusted-sites) tillid til [i referencen Konfigurerbare indstillinger](../working-with-managed-desktop/config-setting-ref.md). |
| Active Directory Federated Services | Hvis du bruger Active Directory Federated Services, skal du kontrollere, at SSO er aktiveret ved hjælp af trinnene i Bekræft og administrer enkelt logon med [AD FS](/previous-versions/azure/azure-services/jj151809(v=azure.100)). |
| Lokale apps, der bruger ældre protokoller | For apps **, der er** i det lokale miljø og bruger ældre protokoller, kræves der ingen ekstra konfiguration, så længe enhederne har adgang til en lokal domænecontroller for at godkende. Du skal dog installere Azure AD-programproxy for at give sikker adgang til disse programmer. Du kan få mere [at vide under Fjernadgang til programmer i det lokale miljø Azure Active Directory din brugers programproxy](/azure/active-directory/manage-apps/application-proxy). |
| Lokale apps med godkendelse på en computer | Apps, der **kører lokalt og er afhængige** af computergodkendelse, understøttes ikke, så du bør overveje at erstatte dem med nyere versioner. |

### <a name="network-shares-that-use-authentication"></a>Netværkshares, der bruger godkendelse

Ingen ekstra konfiguration er påkrævet, for at brugere kan få adgang til netværksshares, så længe enhederne har adgang til en lokal domænecontroller ved hjælp af en UNC-sti.

### <a name="printers"></a>Printere

Microsoft-administrerede skrivebordsenheder kan ikke oprette forbindelse til printere, der er publiceret på Active Directory i det lokale miljø, medmindre du har konfigureret [hybridskyudskrift](/windows-server/administration/hybrid-cloud-print/hybrid-cloud-print-deploy).

Selvom printere ikke automatisk kan findes i et miljø, der kun findes i skyen, kan brugerne bruge lokale printere ved hjælp af printerstien eller printerkøstien, så længe enhederne har adgang til en lokal domænecontroller.

<!--add fuller material on printers when available-->
## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Trin til at blive klar til Microsoft Managed Desktop

1. Gennemgå [forudsætninger for Microsoft Managed Desktop](prerequisites.md).
1. Kør værktøjer [til vurdering af parathed](readiness-assessment-tool.md).
1. Køb [Firmaportal](../get-started/company-portal.md).
1. Gennemgå [forudsætningerne for gæstekonti](guest-accounts.md).
1. Kontrollér [netværkskonfigurationen](network.md).
1. [Forberede certifikater og netværksprofiler](certs-wifi-lan.md).
1. Forberede brugeradgang til data (denne artikel).
1. [Forbered apps](apps.md).
1. [Forbered tilknyttede drev](mapped-drives.md).
1. [Forberede udskrivningsressourcer](printing.md).
1. Navne [på adresseenhed](address-device-names.md).
