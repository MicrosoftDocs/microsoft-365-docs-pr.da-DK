---
title: Tildel brugeradgang til Microsoft Defender Security Center
description: Tildel læse- og skrive- eller skrivebeskyttet adgang til Microsoft Defender for Endpoint-portalen.
keywords: tildel brugerroller, tildel læse- og skriveadgang, tildel skrivebeskyttet adgang, brugerroller, roller
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.date: 11/28/2018
ms.technology: mde
ms.openlocfilehash: fa0157a37cf25efcdcf1b578473b4dc2f6deb10d
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/24/2021
ms.locfileid: "63603032"
---
# <a name="assign-user-access-to-microsoft-defender-security-center"></a>Tildel brugeradgang til Microsoft Defender Security Center

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- Azure Active Directory
- Office 365
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Defender til Slutpunkt understøtter to måder at administrere tilladelser på:

- **Grundlæggende administration af tilladelser**: Angiv tilladelser til enten fuld adgang eller skrivebeskyttet.
- **Rollebaseret adgangskontrol :** Angiv detaljerede tilladelser ved at definere roller, tildele Azure AD-brugergrupper til rollerne og give brugergrupperne adgang til enhedsgrupper. Du kan finde flere oplysninger om RBAC i [Administrere portaladgang ved hjælp af rollebaseret adgangskontrol](rbac.md).

> [!NOTE]
> Hvis du allerede har tildelt grundlæggende tilladelser, kan du når som helst skifte til RBAC. Overvej følgende, før du skifter:
>
> - Brugere med fuld adgang (brugere, der er tildelt katalogrollen Global administrator eller Sikkerhedsadministrator i Azure AD) tildeles automatisk standardadministratorrollen Defender til slutpunktsadministrator, som også har fuld adgang. Yderligere Azure AD-brugergrupper kan tildeles rollen som Defender for Endpoint-administrator, efter du har skiftet til RBAC. Kun brugere, der er tildelt rollen som Defender for Endpoint-administrator, kan administrere tilladelser ved hjælp af RBAC. 
> - Brugere, der har skrivebeskyttet adgang (sikkerhedslæsere), mister adgang til portalen, indtil de får tildelt en rolle. Bemærk, at det kun er Azure AD-brugergrupper, der kan tildeles en rolle under RBAC.
> - Når du har skiftet til RBAC, kan du ikke skifte tilbage til at bruge grundlæggende administration af tilladelser.

## <a name="related-topics"></a>Relaterede emner

- [Brug grundlæggende tilladelser til at få adgang til portalen](basic-permissions.md)
- [Administrer portaladgang ved hjælp af RBAC](rbac.md)
