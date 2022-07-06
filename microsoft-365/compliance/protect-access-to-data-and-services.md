---
title: Beskyt bruger- og enhedsadgang
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 4/17/2018
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a6ef28a4-2447-4b43-aae2-f5af6d53c68e
description: Få mere at vide om, hvordan du beskytter bruger- og enhedsadgang til Microsoft 365-data og -tjenester og forsvarer dig mod tab af data.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f8b6b266d037e8bbc185643e530bf7a2f6919038
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623694"
---
# <a name="protect-user-and-device-access"></a>Beskyt bruger- og enhedsadgang

Beskyttelse af adgangen til dine Microsoft 365-data og -tjenester er afgørende for at forsvare sig mod cyberangreb og beskytte mod datatab. Den samme beskyttelse kan anvendes på andre SaaS-programmer i dit miljø og endda på programmer i det lokale miljø, der publiceres med Azure Active Directory Programproxy.
  
## <a name="step-1-review-recommendations"></a>Trin 1: Gennemse anbefalinger

Anbefalede funktioner til beskyttelse af identiteter og enheder, der har adgang til Office 365, andre SaaS-tjenester og programmer i det lokale miljø, der er publiceret med Azure AD Programproxy.
  
[PDF](https://go.microsoft.com/fwlink/p/?linkid=841656) |  [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657) |  [Flere sprog](https://www.microsoft.com/download/details.aspx?id=55032)
  
## <a name="step-2-protect-administrator-accounts-and-access"></a>Trin 2: Beskyt administratorkonti og adgang

De administrative konti, du bruger til at administrere dit Microsoft 365-miljø, omfatter administratorrettigheder. Disse er værdifulde mål for hackere og cyberattackers.

Begynd med kun at bruge administratorkonti til administration. Administratorer skal have en separat brugerkonto til regelmæssig, ikke-administrativ brug og kun bruge deres administrative konto, når det er nødvendigt, for at fuldføre en opgave, der er knyttet til deres jobfunktion.

Beskyt dine administratorkonti med multifaktorgodkendelse og betinget adgang. Du kan få flere oplysninger under [Beskyttelse af administratorkonti](../security/office-365-security/identity-access-prerequisites.md#protecting-administrator-accounts). 

Konfigurer derefter Administration af privilegeret adgang til Microsoft Purview. Privilegeret adgangsstyring giver detaljeret adgangskontrol over privilegerede administratoropgaver i Office 365. Det kan hjælpe med at beskytte din organisation mod brud, der kan bruge eksisterende privilegerede administratorkonti med stående adgang til følsomme data eller adgang til vigtige konfigurationsindstillinger.

- [Oversigt over privilegeret adgangsstyring](privileged-access-management.md)
- [Konfigurer privilegeret adgangsstyring](privileged-access-management-configuration.md)

En anden topanbefaling er at bruge arbejdsstationer, der er specielt konfigureret til administrativt arbejde. Disse er dedikerede enheder, der kun bruges til administrative opgaver. Se [Sikring af privilegeret adgang](/windows-server/identity/securing-privileged-access/securing-privileged-access).

Endelig kan du afhjælpe virkningen af utilsigtet mangel på administrativ adgang ved at oprette to eller flere akutadgangskonti i din lejer. Se [Administrer akutadgangskonti i Azure AD](/azure/active-directory/users-groups-roles/directory-emergency-access). 

## <a name="step-3-configure-recommended-identity-and-device-access-policies"></a>Trin 3: Konfigurer anbefalede politikker for identitet og enhedsadgang

Multifaktorgodkendelse (MFA) og politikker for betinget adgang er effektive værktøjer til at afhjælpe mod kompromitterede konti og uautoriseret adgang. Vi anbefaler, at du implementerer et sæt politikker, der er blevet testet sammen. Du kan finde flere oplysninger, herunder installationstrin, under [Konfigurationer af identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md).

 Disse politikker implementerer følgende funktioner:

- Multifaktorgodkendelse
- Betinget adgang
- Intune appbeskyttelse (app- og databeskyttelse for enheder)
- Intune enhedens overholdelse af angivne standarder
- Azure AD Identity Protection

Implementering af Intune enhedsoverholdelse kræver tilmelding af enheden. Administration af enheder giver dig mulighed for at sikre, at de er sunde og kompatible, før du giver dem adgang til ressourcer i dit miljø. Se [Tilmeld enheder til administration i Intune](/mem/intune/user-help/enroll-windows-10-device)

## <a name="step-4-configure-sharepoint-device-access-policies"></a>Trin 4: Konfigurer politikker for enhedsadgang til SharePoint

Microsoft anbefaler, at du beskytter indhold på SharePoint-websteder med følsomt og stærkt reguleret indhold med kontrolelementer for enhedsadgang. Du kan finde flere oplysninger under [Politikanbefalinger til sikring af SharePoint-websteder og -filer](../security/office-365-security/sharepoint-file-access-policies.md).
