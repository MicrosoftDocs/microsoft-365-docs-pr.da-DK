---
title: Beskyt bruger- og enhedsadgang
f1.keywords:
- NOCSH
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 4/17/2018
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a6ef28a4-2447-4b43-aae2-f5af6d53c68e
description: Få mere at vide om, hvordan du beskytter bruger- og enhedsadgang Microsoft 365 data og tjenester og beskytter dig mod datatab.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 121c5b8f1168e9986693fea128aa66626b3e31fe
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63587731"
---
# <a name="protect-user-and-device-access"></a>Beskyt bruger- og enhedsadgang

Beskyttelse af adgang til dine Microsoft 365 data og tjenester er afgørende for at beskytte dig mod cyberangreb og beskytte mod datatab. De samme beskyttelser kan anvendes på andre SaaS-programmer i dit miljø og endda på programmer i det lokale miljø, der er udgivet med Azure Active Directory-programproxy.
  
## <a name="step-1-review-recommendations"></a>Trin 1: Gennemse anbefalinger

Anbefalede funktioner til beskyttelse af identiteter og enheder, der har adgang til Office 365, andre SaaS-tjenester og programmer i det lokale miljø, der er udgivet med Azure AD-programproxy.
  
[PDF](https://go.microsoft.com/fwlink/p/?linkid=841656) |  [](https://go.microsoft.com/fwlink/p/?linkid=841657) |  Visio [Sprog mere](https://www.microsoft.com/download/details.aspx?id=55032)
  
## <a name="step-2-protect-administrator-accounts-and-access"></a>Trin 2: Beskyt administratorkonti og adgang
De administrative konti, du bruger til at administrere Microsoft 365 dit miljø, omfatter administratorrettigheder. Disse er værdifulde mål for hackere og cyberangreb. 

Start med kun at bruge administratorkonti til administration. Administratorer skal have en separat brugerkonto til almindelig, ikke-administrativ brug og kun bruge deres administrative konto, når det er nødvendigt for at udføre en opgave, der er knyttet til deres jobfunktion.

Beskyt dine administratorkonti med multifaktorgodkendelse og betinget adgang. Få mere at vide under [Beskyttelse af administratorkonti](../security/office-365-security/identity-access-prerequisites.md#protecting-administrator-accounts). 

Dernæst skal du konfigurere administration af adgang med rettigheder i Office 365. Med administration af adgang med rettigheder kan du opnå detaljeret adgangskontrol over administratoropgaver med Office 365. Det kan hjælpe med at beskytte din organisation mod brud, der kan bruge eksisterende privilegerede administratorkonti med stående adgang til følsomme data eller adgang til vigtige konfigurationsindstillinger.

- [Oversigt over administration af adgangspriviligerede](privileged-access-management-overview.md)
- [Konfigurere adgangsstyring med rettigheder](privileged-access-management-configuration.md)

En anden top anbefaling er at bruge arbejdsstationer, der er særligt konfigureret til administrativt arbejde. Disse er dedikerede enheder, der kun bruges til administrative opgaver. Se [Sikring af privilegeret adgang](/windows-server/identity/securing-privileged-access/securing-privileged-access).

Endelig kan du afhjælpe effekten af utilsigtet manglende administrativ adgang ved at oprette to eller flere konti til hurtig adgang i din lejer. Se [Administrere konti til nødadgang i Azure AD](/azure/active-directory/users-groups-roles/directory-emergency-access). 

## <a name="step-3-configure-recommended-identity-and-device-access-policies"></a>Trin 3: Konfigurer anbefalede politikker for identitet og enhedsadgang
Multifaktorgodkendelse (MFA) og politikker for betinget adgang er effektive værktøjer til at mindske kompromitterede konti og uautoriseret adgang. Vi anbefaler implementering af et sæt politikker, der er blevet testet sammen. Du kan finde flere oplysninger, herunder installationstrin, under [Konfigurationer for identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md).

 Disse politikker implementerer følgende funktioner:
- Multifaktorgodkendelse
- Betinget adgang
- Intune-appbeskyttelse (app og databeskyttelse til enheder)
- Overholdelse af intune-enhed
- Azure AD Identity Protection

Implementering af Intune-enhedsoverholdelse kræver tilmelding af enheder. Administration af enheder giver dig mulighed for at sikre, at de er sunde og kompatible, før du giver dem adgang til ressourcer i dit miljø. Se [Tilmeld enheder til administration i Intune](/mem/intune/user-help/enroll-windows-10-device)

## <a name="step-4-configure-sharepoint-device-access-policies"></a>Trin 4: Konfigurere SharePoint politikker for enhedsadgang

Microsoft anbefaler, at du beskytter indhold på SharePoint med følsomt og meget regulerede indhold med adgangskontrolelementer for enheder. Du kan finde flere oplysninger [i Politikanbefalinger til sikring SharePoint websteder og filer](../security/office-365-security/sharepoint-file-access-policies.md).



