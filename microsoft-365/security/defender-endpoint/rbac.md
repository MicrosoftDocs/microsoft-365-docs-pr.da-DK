---
title: Brug rollebaseret adgangskontrol til at give fuld adgang til Microsoft 365 Defender portal
description: Opret roller og grupper inden for dine sikkerhedshandlinger for at give adgang til portalen.
keywords: rbac, rolle, baseret, adgang, kontrolelement, grupper, kontrolelement, niveau, aad
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8c1ff743aa6c9c215c3894185a4096c9a35a16e0
ms.sourcegitcommit: 6b24f65c987e5ca06e6d5f4fc10804cdbe68b034
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/07/2021
ms.locfileid: "63591818"
---
# <a name="manage-portal-access-using-role-based-access-control"></a>Administrere portaladgang ved hjælp af rollebaseret adgangskontrol

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Azure Active Directory
- Office 365

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-rbac-abovefoldlink)

Med rollebaseret adgangskontrol (RBAC) kan du oprette roller og grupper i sikkerhedsteamet for at give relevant adgang til portalen. Baseret på de roller og grupper, du opretter, har du fuld kontrol over, hvad brugere med adgang til portalen kan se og gøre. 

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4bJ2a]

Store geo-distribuerede sikkerhedsteams indfører typisk en niveaubaseret model til at tildele og godkende adgang til sikkerhedsportaler. Typiske niveauer omfatter følgende tre niveauer:

Niveau|Beskrivelse|
:---|:---|
Niveau 1|**Lokalt sikkerhedsteam/it-team** <br> Dette team undersøger og undersøger sædvanligvis beskeder, der er indeholdt i deres geoplacering, og eskalerer til niveau 2 i tilfælde, hvor en aktiv afhjælpning er påkrævet.|
Niveau 2|**Regionalt sikkerhedsteam** <br> Dette team kan se alle enheder i deres område og udføre afhjælpningshandlinger.|
Niveau 3|**Global sikkerhedsteam** <br> Dette team består af sikkerhedseksperter og er autoriseret til at se og udføre alle handlinger fra portalen.|

> [!NOTE]
> Du kan finde flere oplysninger om niveau [0-aktiver Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-configure), hvor sikkerhedsadministratorer kan give mere detaljeret kontrol over Microsoft Defender til slutpunkt og Microsoft 365 Defender.  

Defender til Slutpunkt RBAC er designet til at understøtte dit valg af niveau eller rollebaseret model og giver dig detaljeret kontrol over, hvilke roller der kan ses, hvilke enheder de kan få adgang til, og handlinger, de kan udføre. RBAC-rammen er centreret omkring følgende kontrolelementer:

- **Bekontrolelement, hvem der kan gøre noget specifikt**
  - Opret brugerdefinerede roller, og styr, hvilke Defender-egenskaber for slutpunkter de kan få adgang til med granularitet.
- **Be kontrol, hvem der kan se oplysninger om en bestemt enhedsgruppe eller bestemte grupper**
  - [Opret enhedsgrupper](machine-groups.md) efter specifikke kriterier, f.eks. navne, mærker, domæner og andre, og giv derefter rolleadgang til dem ved hjælp af en bestemt Azure Active Directory (Azure AD) brugergruppe.

Hvis du vil implementere rollebaseret adgang, skal du definere administratorroller, tildele tilsvarende tilladelser og tildele Azure AD-brugergrupper, der er tildelt rollerne.

### <a name="before-you-begin"></a>Før du begynder

Før du bruger RBAC, er det vigtigt, at du forstår de roller, der kan give tilladelser, og konsekvenserne af at slå RBAC til.

> [!WARNING]
> Før du aktiverer funktionen, er det vigtigt, at du har en global administratorrolle eller sikkerhedsadministratorrolle i Azure AD, og at du har dine Azure AD-grupper klar til at reducere risikoen ved at blive låst ude af portalen. 

Når du logger på portalen Microsoft 365 Defender, får du enten fuld adgang eller skrivebeskyttet adgang. Fuld adgangsrettigheder gives til brugere med sikkerhedsadministratorroller eller globale administratorroller i Azure AD. Skrivebeskyttet adgang gives til brugere med en sikkerhedslæserrolle i Azure AD. 

En person med en Global Defender for Slutpunkt-rolle har ubegrænset adgang til alle enheder, uanset deres enhedsgruppegruppe og tildelinger i Azure AD-brugergrupper.

> [!WARNING]
> I første omgang er det kun personer med globale Azure AD- eller sikkerhedsadministratorrettigheder, der kan oprette og tildele roller i Microsoft 365 Defender-portalen, og det er derfor vigtigt at have de rigtige grupper klar i Azure AD.
>
> **Hvis du slår rollebaseret adgangskontrol til, mister brugere med skrivebeskyttede tilladelser (f.eks. brugere, der er tildelt rolle som Azure AD-sikkerhedslæser) adgang, indtil de er tildelt en rolle.** 
>
>Brugere med administratortilladelser tildeles automatisk den globale standardadministratorrolle for Defender til slutpunkt med de fulde tilladelser. Når du har tilslutt dig RBAC, kan du tildele flere brugere, der ikke er globale Azure AD- eller sikkerhedsadministratorer, til den globale administratorrolle Defender for Endpoint. 
>
> Når du logger på for at bruge RBAC, kan du ikke vende tilbage til de første roller, som da du først loggede på portalen.

## <a name="related-topic"></a>Relateret emne

- [RBAC-roller](../office-365-security/migrate-to-defender-for-office-365-onboard.md#rbac-roles)
- [Opret og administrer enhedsgrupper i Microsoft Defender til Slutpunkt](machine-groups.md)
