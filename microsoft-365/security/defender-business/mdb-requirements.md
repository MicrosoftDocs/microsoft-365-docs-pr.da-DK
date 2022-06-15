---
title: Krav til Microsoft Defender til virksomheder
description: krav til Microsoft Defender til virksomheder licens, hardware og software
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ab24e3898d897df6813338fd0d2131c3787f0a09
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089578"
---
# <a name="microsoft-defender-for-business-requirements"></a>krav til Microsoft Defender til virksomheder

I denne artikel beskrives kravene til Microsoft Defender til virksomheder.

## <a name="what-to-do"></a>Sådan gør du

1. [Gennemse kravene, og sørg for, at du opfylder dem](#review-the-requirements).
2. [Fortsæt til de næste trin](#next-steps).


## <a name="review-the-requirements"></a>Gennemse kravene

I følgende tabel vises de grundlæggende krav til konfiguration og brug af Microsoft Defender til virksomheder.

| Krav | Beskrivelse |
|:---|:---|
| Abonnement | Microsoft 365 Business Premium eller Microsoft Defender til virksomheder (separat). Se [Sådan får du Microsoft Defender til virksomheder](get-defender-business.md).<br/><br/>Bemærk, at hvis du har flere abonnementer, har det højeste abonnement forrang. Hvis du f.eks. har Microsoft Defender for Endpoint Plan 2 (købt eller prøveabonnement), og du får Microsoft Defender til virksomheder, har Defender for Endpoint Plan 2 forrang. I dette tilfælde kan du ikke se Defender for Business-oplevelsen.  |
| Datacenter | En af følgende datacenterplaceringer: <br/>- Den Europæiske Union <br/>- Det Forenede Kongerige <br/>- USA |
| Brugerkonti | – Brugerkonti oprettes i Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>- Microsoft Defender til virksomheder licenser tildeles i Microsoft 365 Administration<br/><br/>Hvis du vil have hjælp til denne opgave, skal du se [Tilføj brugere og tildel licenser](mdb-add-users.md). |
| Tilladelser  | Hvis du vil tilmelde dig Microsoft Defender til virksomheder, skal du være global Administration.<br/><br/>For at få adgang til Microsoft 365 Defender-portalen skal brugerne have en af følgende [roller i Azure AD](mdb-roles-permissions.md) tildelt: <br/>- Sikkerhedslæser<br/>- Sikkerheds Administration<br/>- Global Administration<br/><br/>Du kan få mere at vide [under Roller og tilladelser i Microsoft Defender til virksomheder](mdb-roles-permissions.md). |
| Krav til browser | Microsoft Edge eller Google Chrome |
| Operativsystem | Hvis du vil administrere enheder på Microsoft 365 Defender-portalen, skal dine enheder køre et af følgende operativsystemer: <br/>- Windows 10 Business eller nyere <br/>- Windows 10 Professional eller nyere <br/>- Windows 10 Enterprise eller nyere <br/>- macOS (de tre nyeste udgivelser understøttes)<br/><br/>Sørg for, at [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) er installeret på Windows enheder. <br/><br/>Hvis du allerede administrerer enheder i Microsoft Intune, kan du fortsætte med at bruge Microsoft Endpoint Manager Administration. |

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) bruges til at administrere brugertilladelser og enhedsgrupper. Azure AD er inkluderet i dit Defender for Business-abonnement. 
> - Hvis du ikke har et Microsoft 365 abonnement, før du starter din prøveversion, klargøres Azure AD for dig under aktiveringsprocessen. 
> - Hvis du har et andet Microsoft 365 abonnement, når du starter din Defender for Business-prøveversion, kan du bruge din eksisterende Azure AD-tjeneste. 
> - Hvis du bruger [Microsoft 365 Business Premium](../../business/index.yml), når du starter din Defender for Business-prøveversion, har du mulighed for at administrere dine enheder ved hjælp af Intune. 

## <a name="next-steps"></a>Næste trin

Fortsæt til [trin 2: Tildel roller og tilladelser i Microsoft Defender til virksomheder](mdb-roles-permissions.md).
 
