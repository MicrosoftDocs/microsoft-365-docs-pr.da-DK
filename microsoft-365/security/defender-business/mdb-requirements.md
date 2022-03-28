---
title: Krav til Microsoft Defender for Business
description: Licens, hardware og softwarekrav for Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 17954ec9c01a053f847a7d8a74188edf2f4e4091
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63596969"
---
# <a name="microsoft-defender-for-business-requirements"></a>Krav til Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

I denne artikel beskrives kravene til Microsoft Defender for Business.

## <a name="what-to-do"></a>Hvad kan du gøre?

1. [Gennemse kravene, og sørg for, at du opfylder dem](#review-the-requirements).

2. [Fortsæt til de næste trin](#next-steps).

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="review-the-requirements"></a>Gennemse kravene

I følgende tabel vises de grundlæggende krav til konfiguration og brug af Microsoft Defender for Business. <br/><br/>

| Krav | Beskrivelse |
|:---|:---|
| Abonnement | Microsoft 365 Business Premium <br/>--- eller ---<br/>Microsoft Defender for Business (separat, i øjeblikket i forhåndsvisning). <br/><br/> Se [Sådan får du Microsoft Defender for Business](get-defender-business.md).<br/><br/>Bemærk, at hvis du har flere abonnementer, har det højeste abonnement forrang. Hvis du f.eks. har Microsoft Defender for Endpoint Plan 2 (købt eller prøveabonnement), og du får Microsoft Defender for Business, har Defender for Endpoint Plan 2 forrang. I dette tilfælde kan du ikke se Defender for Business-oplevelsen.  |
| Datacenter | En af følgende datacenterplaceringer: <br/>- EU <br/>- Storbritannien <br/>- USA |
| Brugerkonti | Brugerkonti oprettes i Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>Microsoft Defender for Business-licenser tildeles i Microsoft 365 Administration<br/><br/>Hvis du vil have hjælp til denne opgave, skal [du se Tilføj brugere, og tildel licenser](../../admin/add-users/add-users.md). |
| Tilladelser  | Hvis du vil tilmelde dig Microsoft Defender for Business, skal du være global administrator.<br/><br/>For at få adgang Microsoft 365 Defender-portalen skal brugere have en af følgende [roller i Azure AD](mdb-roles-permissions.md) tildelt: <br/>- Sikkerhedslæser<br/>- Sikkerhedsadministrator<br/>- Global administrator<br/><br/>Du kan få mere at [vide under Roller og tilladelser i Microsoft Defender for Business](mdb-roles-permissions.md). |
| Browserkrav | Microsoft Edge eller Google Chrome |
| Operativsystem | Hvis du vil administrere enheder i Microsoft Defender for Business, skal dine enheder køre et af følgende operativsystemer: <br/>- Windows 10 Business eller nyere <br/>- Windows 10 Professional eller nyere <br/>- Windows 10 Enterprise eller nyere <br/><br/>Sørg for, [at KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) er installeret. <br/><br/>Hvis du allerede administrerer enheder i Microsoft Intune (eller Microsoft Endpoint Manager), kan du onboarde disse enheder til Defender for Business. |
| Integration med Microsoft Endpoint Manager  | Hvis du planlægger at onboarde enheder [ved hjælp af sikkerhedskonfigurationen af Microsoft Defender for Business](mdb-onboard-devices.md#microsoft-defender-for-business-security-configuration), skal følgende krav være opfyldt:<br/><br/>Forudsætningerne skal være opfyldt for [Sikkerhedsadministration til Microsoft Defender til slutpunkt](/mem/intune/protect/mde-security-integration).<br/>- Azure AD skal konfigureres sådan, at tillid oprettes mellem virksomhedens enheder og Azure AD. <br/>- Defender for Business skal have aktiveret sikkerhedsadministration Microsoft Endpoint Manager.<br/><br/>Enheder skal kunne oprette forbindelse til følgende URL-adresser:<br/>- `enterpriseregistration.windows.net` (til registrering i Azure AD)<br/>- `login.microsoftonline.com` (til registrering i Azure AD)<br/>- `*.dm.microsoft.com` Jokertegnet (*) understøtter slutpunkter i skytjenesten, der bruges til registrering, indtjekning og rapportering, og som kan ændres, når tjenesten skaleres. |

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) bruges til at administrere brugertilladelser og enhedsgrupper. Azure AD er inkluderet i dit abonnement på Defender for Business. 
> - Hvis du ikke har et Microsoft 365 inden du starter din prøveversion, bliver Azure AD klargjort til dig under aktiveringsprocessen. 
> - Hvis du har et andet Microsoft 365, når du starter din prøveversion af Defender for Business, kan du bruge din eksisterende Azure AD-tjeneste. 
> - Hvis du [bruger Microsoft 365 Business Premium,](../../business/index.yml) når du starter din prøveversion af Defender for Business, har du mulighed for at administrere enheder Microsoft Intune. 

## <a name="next-steps"></a>Næste trin

Fortsæt til:

- [Trin 2: Tildel roller og tilladelser i Microsoft Defender for Business](mdb-roles-permissions.md) 
 