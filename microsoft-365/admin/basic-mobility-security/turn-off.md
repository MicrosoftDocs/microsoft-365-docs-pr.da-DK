---
title: Slå Basic Mobility og Security fra
f1.keywords: NOCSH
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
ms.custom: AdminSurgePortfolio
description: Fjern grupper eller politikker for at deaktivere Grundlæggende mobilitet og sikkerhed.
ms.openlocfilehash: c3c82c040e688977a68e06639e87c8f733bc8c38
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780759"
---
# <a name="turn-off-basic-mobility-and-security"></a>Slå Basic Mobility og Security fra

Hvis du vil slå Grundlæggende mobilitet og sikkerhed fra effektivt, skal du fjerne grupper af personer, der er defineret af sikkerhedsgrupper, fra politikkerne for enhedshåndtering eller fjerne selve politikkerne.

- Fjern grupper af brugere ved at fjerne brugersikkerhedsgrupper fra de enhedspolitikker, du har oprettet.

- Deaktiver Grundlæggende mobilitet og sikkerhed for alle ved at fjerne alle politikker for grundlæggende mobilitet og sikkerhedsenheder.

Disse indstillinger fjerner Basic Mobility og Security-håndhævelse for enheder i din organisation. Du kan desværre ikke blot "annullere klargøringen" Basic Mobility og Security, når du har konfigureret den.

> [!IMPORTANT]
> Vær opmærksom på indvirkningen på brugernes enheder, når du fjerner brugersikkerhedsgrupper fra politikker eller fjerner selve politikkerne. Mailprofiler og cachelagrede mails kan f.eks. blive fjernet, afhængigt af enheden. Du kan finde flere oplysninger under [Hvad sker der, når du sletter en politik eller fjerner en bruger fra politikken?](../../admin/basic-mobility-security/create-device-security-policies.md)

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>Fjern brugersikkerhedsgrupper fra politikker for grundlæggende mobilitet og sikkerhedsenheder

1. I din browser skal du skrive: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. Vælg en enhedspolitik, og vælg **Rediger politik**.

3. Vælg **Fjern** på siden **Installation**.

4. Under **Grupper** skal du vælge en sikkerhedsgruppe.

5. Vælg **Fjern**, og vælg **Gem**.

## <a name="remove-basic-mobility-and-security-device-policies"></a>Fjern enhedspolitikker for grundlæggende mobilitet og sikkerhed

1. I din browser skal du skrive: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. Vælg en enhedspolitik, og vælg derefter **Slet politik**.

3. Vælg **Ja** i dialogboksen Advarsel.

> [!NOTE]
> Du kan finde flere trin til at fjerne blokeringen af enheder, hvis dine organisationsenheder stadig er i blokeret tilstand, i blogindlægget [Fjernelse af Access Control fra Mobilenhedshåndtering til Office 365](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934).
