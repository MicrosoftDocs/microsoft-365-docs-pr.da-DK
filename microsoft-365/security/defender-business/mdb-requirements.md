---
title: Krav til Microsoft Defender til virksomheder
description: Microsoft Defender til virksomheder licens-, hardware- og softwarekrav
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 9fd082160640c239424ec75ff58c695a0175d630
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634927"
---
# <a name="microsoft-defender-for-business-requirements"></a>Microsoft Defender til virksomheder krav

> [!IMPORTANT]
> Microsoft Defender til virksomheder udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) fra 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

I denne artikel beskrives kravene til Microsoft Defender til virksomheder.

## <a name="what-to-do"></a>Hvad kan du gøre?

1. [Gennemse kravene, og sørg for, at du opfylder dem](#review-the-requirements).

2. [Fortsæt til de næste trin](#next-steps).

>
> **Har du et minut?**
> Tag vores <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">korte undersøgelse om Microsoft Defender til virksomheder</a>. Vi vil meget gerne høre fra dig!
>

## <a name="review-the-requirements"></a>Gennemse kravene

I følgende tabel vises de grundlæggende krav til konfiguration og brug Microsoft Defender til virksomheder. <br/><br/>

| Krav | Beskrivelse |
|:---|:---|
| Abonnement | Microsoft 365 Business Premium <br/>--- eller ---<br/>Microsoft Defender til virksomheder (separat, i øjeblikket i forhåndsvisning). <br/><br/> Se [Sådan får du Microsoft Defender til virksomheder](get-defender-business.md).<br/><br/>Bemærk, at hvis du har flere abonnementer, har det højeste abonnement forrang. Hvis du f.eks. har Microsoft Defender for Endpoint Plan 2 (købt eller prøveabonnement), og du får Microsoft Defender til virksomheder, tilsidesætter Defender for Endpoint Plan 2. I dette tilfælde kan du ikke se Defender for Business-oplevelsen.  |
| Datacenter | En af følgende datacenterplaceringer: <br/>- EU <br/>- Storbritannien <br/>- USA |
| Brugerkonti | Brugerkonti oprettes i Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>Microsoft Defender til virksomheder licenser tildeles i Microsoft 365 Administration<br/><br/>Hvis du vil have hjælp til denne opgave, skal [du se Tilføj brugere, og tildel licenser](../../admin/add-users/add-users.md). |
| Tilladelser  | Hvis du vil tilmelde Microsoft Defender til virksomheder, skal du være global administrator.<br/><br/>For at få adgang Microsoft 365 Defender-portalen skal brugere have en af følgende [roller i Azure AD](mdb-roles-permissions.md) tildelt: <br/>- Sikkerhedslæser<br/>- Sikkerhedsadministrator<br/>- Global administrator<br/><br/>Du kan få mere at [vide under Roller og tilladelser i Microsoft Defender til virksomheder](mdb-roles-permissions.md). |
| Browserkrav | Microsoft Edge eller Google Chrome |
| Operativsystem | Hvis du vil administrere Microsoft Defender til virksomheder, skal dine enheder køre et af følgende operativsystemer: <br/>- Windows 10 Business eller nyere <br/>- Windows 10 Professional eller nyere <br/>- Windows 10 Enterprise eller nyere <br/><br/>Sørg for, [at KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) er installeret. <br/><br/>Hvis du allerede administrerer enheder i Microsoft Intune (eller Microsoft Endpoint Manager), kan du onboarde disse enheder til Defender for Business. |

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) bruges til at administrere brugertilladelser og enhedsgrupper. Azure AD er inkluderet i dit abonnement på Defender for Business. 
> - Hvis du ikke har et Microsoft 365 inden du starter din prøveversion, bliver Azure AD klargjort til dig under aktiveringsprocessen. 
> - Hvis du har et andet Microsoft 365, når du starter din prøveversion af Defender for Business, kan du bruge din eksisterende Azure AD-tjeneste. 
> - Hvis du [bruger Microsoft 365 Business Premium,](../../business/index.yml) når du starter din prøveversion af Defender for Business, har du mulighed for at administrere enheder Microsoft Intune. 

## <a name="next-steps"></a>Næste trin

Fortsæt til:

- [Trin 2: Tildel roller og tilladelser i Microsoft Defender til virksomheder](mdb-roles-permissions.md) 
 