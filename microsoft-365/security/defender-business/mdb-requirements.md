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
- m365solution-mdb-setup
ms.openlocfilehash: 1cb133a11bf0c59bcff117721badddc87e44a96c
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/22/2022
ms.locfileid: "66970072"
---
# <a name="microsoft-defender-for-business-requirements"></a>krav til Microsoft Defender til virksomheder

I denne artikel beskrives kravene til Defender for Business.

## <a name="what-to-do"></a>Sådan gør du

1. [Gennemse kravene, og sørg for, at du opfylder dem](#review-the-requirements).
2. [Fortsæt til de næste trin](#next-steps).


## <a name="review-the-requirements"></a>Gennemse kravene

I følgende tabel vises de grundlæggende krav, du skal bruge for at konfigurere og bruge Defender for Business.

| Krav | Beskrivelse |
|:---|:---|
| Abonnement | Microsoft 365 Business Premium eller Defender for Business (separat). Se [Sådan får du Defender for Business](get-defender-business.md).<p>Bemærk, at hvis du har flere abonnementer, har det højeste abonnement forrang. Hvis du f.eks. har Microsoft Defender for Endpoint Plan 2 (købt eller prøveabonnement), og du får Defender for Business, har Defender for Endpoint Plan 2 forrang. I dette tilfælde kan du ikke se Defender for Business-oplevelsen. Se [Hvad sker der, hvis jeg har en blanding af Microsoft 365 Defender abonnementer](mdb-faq.yml#what-happens-if-i-have-a-mix-of-microsoft-endpoint-security-subscriptions)?  |
| Datacenter | En af følgende datacenterplaceringer: <ul><li>Eu</li><li>Storbritannien</li><li>USA</li></ul> |
| Brugerkonti |<ul><li>Brugerkonti oprettes i Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com)).</li><li>Licenser til Defender for Business (eller Microsoft 365 Business Premium) tildeles i Microsoft 365 Administration.</li></ul>Hvis du vil have hjælp til denne opgave, skal du se [Tilføj brugere og tildel licenser](mdb-add-users.md). |
| Tilladelser  | Hvis du vil tilmelde dig Defender for Business, skal du være global Administration.<p>For at få adgang til Microsoft 365 Defender-portalen skal brugerne have en af følgende [roller i Azure AD](mdb-roles-permissions.md) tildelt:<ul><li>Sikkerhedslæser</li><li>Sikkerheds Administration</li><li>Globale Administration</li></ul>Du kan få mere at vide under [Roller og tilladelser i Defender for Business](mdb-roles-permissions.md). |
| Krav til browser | Microsoft Edge eller Google Chrome |
| Klientenhedsoperativsystem | Hvis du vil administrere enheder på Microsoft 365 Defender-portalen, skal dine enheder køre et af følgende operativsystemer: <ul><li>Windows 10 eller 11 erhverv</li><li>Windows 10 eller 11 Professional</li><li>Windows 10 eller 11 Enterprise</li><li>Mac (de tre nyeste versioner understøttes)</li></ul><p>Sørg for, at [KB5006738](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) er installeret på Windows-enhederne. <p>Hvis du allerede administrerer enheder i Microsoft Intune, kan du fortsætte med at bruge Microsoft Endpoint Manager Administration. I så fald understøttes følgende andre operativsystemer: <ul><li>iOS og iPadOS</li><li>Android OS</li></ul> |
| Serverkrav | Hvis du planlægger at onboarde en forekomst af Windows Server eller Linux Server, skal du opfylde følgende krav: <ul><li>Indstillingen **Prøveversionsfunktioner** er slået til. På Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) skal du gå til **Indstillinger** > **Slutpunkter** > **Prøveversionsfunktioner til generelle** > **avancerede funktioner** > .</li><li>Håndhævelsesområdet for Windows Server er slået til. I Microsoft 365 Defender-portalen skal du gå til **Indstillinger** > **Slutpunkter** > **Administration af konfiguration** > **Håndhævelsesomfang**. Vælg **Brug MDE til at gennemtvinge sikkerhedskonfigurationsindstillinger fra MEM**, vælg  **Windows Server**, og vælg derefter **Gem**.</li><li>Linux Server-slutpunkter opfylder [forudsætningerne for Microsoft Defender for Endpoint på Linux](../defender-endpoint/microsoft-defender-endpoint-linux.md#prerequisites).</li></ul> |

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) bruges til at administrere brugertilladelser og enhedsgrupper. Azure AD er inkluderet i dit Defender for Business-abonnement. 
> - Hvis du ikke har et Microsoft 365-abonnement, før du starter din prøveversion, klargøres Azure AD for dig under aktiveringsprocessen. 
> - Hvis du har et andet Microsoft 365-abonnement, når du starter din Defender for Business-prøveversion, kan du bruge din eksisterende Azure AD tjeneste. 
> - Hvis du bruger [Microsoft 365 Business Premium](../../business/index.yml), når du starter din Defender for Business-prøveversion, har du mulighed for at administrere dine enheder ved hjælp af Intune.

## <a name="next-steps"></a>Næste trin

Gå til [trin 2: Tildel roller og tilladelser i Defender for Business](mdb-roles-permissions.md).
 
