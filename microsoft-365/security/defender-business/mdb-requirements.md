---
title: Krav til Microsoft Defender til virksomheder
description: krav til Microsoft Defender til virksomheder licens, hardware og software
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/20/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 75c3df32bb3103ad818524da0972567d3fd11cc8
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "65000680"
---
# <a name="microsoft-defender-for-business-requirements"></a>krav til Microsoft Defender til virksomheder

> [!NOTE]
> Microsoft Defender til virksomheder er nu inkluderet i [Microsoft 365 Business Premium](../../business-premium/index.md). 

I denne artikel beskrives kravene til Microsoft Defender til virksomheder.

## <a name="what-to-do"></a>Sådan gør du

1. [Gennemse kravene, og sørg for, at du opfylder dem](#review-the-requirements).

2. [Fortsæt til de næste trin](#next-steps).

>
> **Har du et øjeblik?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om sikkerhed</a>. Vi vil meget gerne høre fra dig!
>

## <a name="review-the-requirements"></a>Gennemse kravene

I følgende tabel vises de grundlæggende krav til konfiguration og brug af Microsoft Defender til virksomheder.

| Krav | Beskrivelse |
|:---|:---|
| Abonnement | Microsoft 365 Business Premium <br/>--- eller ---<br/>Microsoft Defender til virksomheder (separat, som i øjeblikket er en prøveversion). <br/><br/> Se [Sådan får du Microsoft Defender til virksomheder](get-defender-business.md).<br/><br/>Bemærk, at hvis du har flere abonnementer, har det højeste abonnement forrang. Hvis du f.eks. har Microsoft Defender for Endpoint Plan 2 (købt eller prøveabonnement), og du får Microsoft Defender til virksomheder, har Defender for Endpoint Plan 2 forrang. I dette tilfælde kan du ikke se Defender for Business-oplevelsen.  |
| Datacenter | En af følgende datacenterplaceringer: <br/>- Den Europæiske Union <br/>- Det Forenede Kongerige <br/>- USA |
| Brugerkonti | Brugerkonti oprettes i Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>Microsoft Defender til virksomheder licenser tildeles i Microsoft 365 Administration<br/><br/>Hvis du vil have hjælp til denne opgave, skal du se [Tilføj brugere og tildel licenser](mdb-add-users.md). |
| Tilladelser  | Hvis du vil tilmelde dig Microsoft Defender til virksomheder, skal du være global administrator.<br/><br/>Brugerne skal have tildelt en af følgende [roller i Azure AD](mdb-roles-permissions.md) for at få adgang til Microsoft 365 Defender-portalen: <br/>- Sikkerhedslæser<br/>– Sikkerhedsadministrator<br/>- Global administrator<br/><br/>Du kan få mere at vide [under Roller og tilladelser i Microsoft Defender til virksomheder](mdb-roles-permissions.md). |
| Krav til browser | Microsoft Edge eller Google Chrome |
| Operativsystem | Hvis du vil administrere enheder i Microsoft Defender til virksomheder, skal dine enheder køre et af følgende operativsystemer: <br/>- Windows 10 Business eller nyere <br/>- Windows 10 Professional eller nyere <br/>- Windows 10 Enterprise eller nyere <br/>- macOS (de tre nyeste versioner understøttes)<br/><br/>Kontrollér, at [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) er installeret. <br/><br/>Hvis du allerede administrerer enheder i Microsoft Intune (eller Microsoft Endpoint Manager), kan du onboarde disse enheder til Defender for Business. |

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) bruges til at administrere brugertilladelser og enhedsgrupper. Azure AD er inkluderet i dit Defender for Business-abonnement. 
> - Hvis du ikke har et Microsoft 365 abonnement, før du starter din prøveversion, klargøres Azure AD for dig under aktiveringsprocessen. 
> - Hvis du har et andet Microsoft 365 abonnement, når du starter din Defender for Business-prøveversion, kan du bruge din eksisterende Azure AD-tjeneste. 
> - Hvis du bruger [Microsoft 365 Business Premium](../../business/index.yml), når du starter din Defender for Business-prøveversion, har du mulighed for at administrere enheder i Microsoft Intune. 

## <a name="next-steps"></a>Næste trin

Fortsæt til [trin 2: Tildel roller og tilladelser i Microsoft Defender til virksomheder](mdb-roles-permissions.md).
 