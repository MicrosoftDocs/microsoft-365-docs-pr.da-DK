---
title: Forøg trusselsbeskyttelse til Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: Konfigurer overholdelsesfunktioner for at forhindre datatab og hjælpe med at beskytte dine og dine kunders følsomme oplysninger.
ms.openlocfilehash: baac8bc1ad9a425ad7219a1e76949286858f60e0
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403704"
---
# <a name="set-up-compliance-features"></a>Konfigurer overholdelsesfunktioner

Dit Microsoft 365 Business Premium omfatter funktioner til overholdelse af regler og standarder og beskyttelse af personlige oplysninger. Disse funktioner er med til at beskytte din virksomheds data og for at hjælpe dig med at beskytte dine og dine kunders følsomme oplysninger. Denne artikel er beregnet til at hjælpe dig med at komme i gang med dine overholdelsesfunktioner.

## <a name="before-you-begin"></a>Før du begynder

Sørg for, at du har en af følgende roller tildelt Azure Active Directory:

- Global Administrator
- Overholdelsesadministrator

Du kan få mere at vide [under Introduktion til siden roller](../add-users/admin-roles-page.md).

## <a name="use-compliance-manager-to-get-started"></a>Brug Overholdelsesstyring til at komme i gang

:::image type="content" source="../../business-premium/media/m365bp-compliancemanager.png" alt-text="Skærmbillede af Overholdelsesstyring i Microsoft 365 Business Premium.":::

Microsoft 365 Business Premium inkluderer Overholdelsesstyring, som kan hjælpe dig i gang med at konfigurere dine overholdelsesfunktioner. Disse funktioner omfatter forebyggelse af datatab, informationsstyring og insider-risikostyring for blot at nævne nogle få. Overholdelsesstyring kan spare dig tid ved at fremhæve anbefalinger, et overholdelsesresultat og metoder til at forbedre dit resultat.

Sådan kommer du i gang:

1. Gå til [https://compliance.microsoft.com](https://compliance.microsoft.com) , og log på.

2. Vælg Styring af overholdelse i **navigationsruden**.

3. Gennemgå **oplysningerne** under fanen Oversigt. Vælg et element eller et link for at få vist flere oplysninger eller for at udføre handlinger, f.eks. konfigurere en politik til forebyggelse af datatab (DLP). Eksempelvis kan du i **sektionen Løsninger, der påvirker din score** vælge linket i **kolonnen Resterende** handlinger.

   :::image type="content" source="../../business-premium/media/m365bp-compliancesolutions.png" alt-text="Skærmbillede af løsninger, der påvirker ruden Score.":::

   Denne handling fører dig til fanen **Forbedringshandlinger** , der filtreres for det element, du har valgt. I dette eksempel kigger vi på DLP-politikker til konfiguration.

   :::image type="content" source="../../business-premium/media/m365bp-dlppoliciestoconfigure.png" alt-text="Skærmbillede af DLP-politikker til konfiguration.":::

4. Vælg et **element på** fanen Forbedringshandlinger. I vores eksempel har vi valgt Opret tilpassede **DLP-politikker eller personlige oplysninger**. En side indlæses, som indeholder flere oplysninger om den politik, der skal konfigureres.

   :::image type="content" source="../../business-premium/media/m365bp-dlppolicyinfo.png" alt-text="Skærmbillede af oplysninger om DLP-politik for kundeindhold.":::

   Følg oplysningerne på skærmen for at konfigurere din DLP-politik.

Du kan finde flere oplysninger om overholdelsesfunktioner Microsoft 365 til virksomheder i dokumentationen [Microsoft 365 overholdelse af regler og standarder](../../compliance/index.yml).

## <a name="use-sensitivity-labels"></a>Brug følsomhedsmærkater

Følsomhedsmærkater er tilgængelige Office apps (f.eks. Outlook, Word, Excel og PowerPoint). Eksempler på etiketter omfatter:

- Normal
- Personal
- Privat
- Fortroligt

Du kan dog også definere andre etiketter for virksomheden.

Brug følgende artikler til at komme i gang med følsomhedsmærkater:

1. [Hvad er følsomhedsmærkater?](../../compliance/sensitivity-labels.md)

2. [Kom i gang med at oprette dine følsomhedsmærkater](../../compliance/get-started-with-sensitivity-labels.md)

3. [Publicere følsomhedsmærkater og deres politikker](../../compliance/create-sensitivity-labels.md)

4. [Vis personer i din virksomhed, hvordan man bruger følsomhedsmærkater](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)