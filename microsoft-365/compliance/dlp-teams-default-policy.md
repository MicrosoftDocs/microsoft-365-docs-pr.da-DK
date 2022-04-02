---
title: Få mere at vide om standardpolitikken til forebyggelse af datatab i Microsoft Teams (forhåndsvisning)
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Få mere at vide om standardpolitikken til forebyggelse af datatab i Microsoft Teams
ms.openlocfilehash: 61a1ea22362d9e75d605660d29116140f6708003
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63602998"
---
# <a name="learn-about-the-default-data-loss-prevention-policy-in-microsoft-teams-preview"></a>Få mere at vide om standardpolitikken til forebyggelse af datatab i Microsoft Teams (forhåndsvisning)

[Funktioner til forebyggelse af](dlp-learn-about-dlp.md) datatab er blevet udvidet til at omfatte Microsoft Teams chat- og kanalmeddelelser, herunder private kanalmeddelelser. Som en del af denne version har vi oprettet en DLP-standardpolitik for Microsoft Teams for første gang til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>.

## <a name="applies-to"></a>Gælder for

Enhver lejer, der har licens til en eller flere af nedenstående licenser og har aktive Teams brugere
 
- ME5, 
- MA5, 
- E5/A5-overholdelse, 
- IP+G, 
- OE5, 
- Avanceret overholdelse af O365 
- EMS E5


## <a name="what-does-the-default-policy-do"></a>Hvad gør standardpolitikken?

Standard-DLP-politikken for Teams registrerer alle de kreditkortnumre, der deles internt og eksternt i organisationen. Denne politik er som standard til for alle brugere af lejeren. Den genererer ikke politiktip til slutbrugere, men genererer en beskedhændelse og udløser også en mail med lav alvorsgrad til administratoren (tilføjet i politikken). Administratoren kan se aktiviteterne og redigere politikkerne ved at logge på Overholdelsescenter.

Administratorer kan få vist denne politik på siden [Politikker for](https://compliance.microsoft.com/compliancesettings) > til forebyggelse af datatab.


> [!div class="mx-imgBorder"]
> ![standardpolitik Teams DLP.](../media/default-teams-dlp-policy.png)

## <a name="edit-or-delete-the-default-policy"></a>Rediger eller slet standardpolitikken

Hvis [du vil redigere standardpolitikken for bedre ydeevne eller slette den, skal](create-test-tune-dlp-policy.md#tune-a-dlp-policy) du blot bruge en konto med **DLP-overholdelsesstyringstilladelser** . Du kan finde flere oplysninger [under Tilladelser](create-test-tune-dlp-policy.md#permissions).

