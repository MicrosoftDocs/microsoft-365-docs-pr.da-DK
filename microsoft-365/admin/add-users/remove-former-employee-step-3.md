---
title: Trin 3 – Slet og bloker en tidligere medarbejders mobilenhed
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- m365solution-removeemployee
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
description: Brug Exchange Administration til at slette og blokere en tidligere medarbejders enhed, så alle organisationsdata fjernes, og der oprettes ikke længere forbindelse til Microsoft 365.
ms.openlocfilehash: 5ee94e9f9bfff2e4f257bf0ff3364806136e3f42
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436597"
---
# <a name="step-3---wipe-and-block-a-former-employees-mobile-device"></a>Trin 3 – Slet og bloker en tidligere medarbejders mobilenhed

Hvis din tidligere medarbejder havde en organisationstelefon, kan du bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> til at slette og blokere enheden, så alle organisationsdata fjernes fra enheden, og den kan ikke længere oprette forbindelse til Office 365. Hvis din organisation bruger Basic Mobility og Security til at administrere mobilenheder, kan du slette og blokere disse enheder ved hjælp af Basic Mobility og Security.

## <a name="wipe-mobile-device-using-the-exchange-admin-center"></a>Slet mobilenhed ved hjælp af Exchange Administration

1. Gå til Exchange Administration > <a href="https://go.microsoft.com/fwlink/?linkid=2183135" target="_blank">modtagerpostkasser</a>\>.
1. Vælg brugeren, og vælg **Få vist detaljer** under **Mobilenheder**.
1. På siden **Oplysninger om mobilenhed** under **Mobilenheder** skal du vælge mobilenheden, vælge **Slet dataWipe**![ Enhed](../../media/1c113a36-53cb-4974-884f-3ecd9535506e.png) og derefter vælge **Bloker**.
1. Vælg **Gem**.
   > [!TIP]
   > Sørg for at fjerne eller deaktivere brugeren fra din Blackberry Enterprise Service i det lokale miljø. Du bør også deaktivere enhver Blackberry-enheder for brugeren. Se Blackberry Business Cloud Services Administration Guide, hvis du har brug for specifikke trin til, hvordan du deaktiverer brugeren.

## <a name="related-content"></a>Relateret indhold

[Exchange Administration i Exchange Online](/exchange/exchange-admin-center)
