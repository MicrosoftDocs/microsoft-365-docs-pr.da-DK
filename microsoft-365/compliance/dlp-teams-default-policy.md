---
title: Få mere at vide om DLP-standardpolitikken i Microsoft Teams (prøveversion)
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
ms.openlocfilehash: 5c3a5a116da90a41abcc459808e83176dc750fe1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624217"
---
# <a name="learn-about-the-default-data-loss-prevention-policy-in-microsoft-teams-preview"></a>Få mere at vide om standardpolitikken for forebyggelse af datatab i Microsoft Teams (prøveversion)

[Microsoft Purview Forebyggelse af datatab](dlp-learn-about-dlp.md) funktioner er blevet udvidet til at omfatte Microsoft Teams-chat- og kanalmeddelelser, herunder private kanalmeddelelser. Som en del af denne version har vi oprettet en DLP-standardpolitik for Microsoft Teams for førstegangskunder til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview-compliance-portal</a>.

## <a name="licensing"></a>Licensering

Du kan få komplette licensoplysninger om DLP i Microsoft Teams under [Information Protection: Forebyggelse af datatab i Teams](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-teams).

## <a name="what-does-the-default-policy-do"></a>Hvad gør standardpolitikken?

Standard-DLP-politikken for Teams sporer alle de kreditkortnumre, der deles internt og eksternt med organisationen. Denne politik er som standard slået til for alle brugere af lejeren. Den genererer ikke nogen politiktip til slutbrugere, men genererer en beskedhændelse og udløser også en mail med lav alvorsgrad til administratoren (tilføjet i politikken). Administratoren kan få vist aktiviteterne og redigere oplysningerne om politikker ved at logge på Overholdelsescenter.

Administratorer kan få vist denne politik på siden [Microsoft Purview-compliance-portal](https://compliance.microsoft.com/compliancesettings) > politikker til forebyggelse af datatab.


> [!div class="mx-imgBorder"]
> ![standardpolitik for Teams DLP.](../media/default-teams-dlp-policy.png)

## <a name="edit-or-delete-the-default-policy"></a>Rediger eller slet standardpolitikken

Hvis du vil [redigere standardpolitikken for at opnå en bedre ydeevne eller slette den](create-test-tune-dlp-policy.md#tune-a-dlp-policy), skal du blot bruge en konto med tilladelser til **administration af DLP-overholdelse** . Du kan få flere oplysninger under [Tilladelser](create-test-tune-dlp-policy.md#permissions).

