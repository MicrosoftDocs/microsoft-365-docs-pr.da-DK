---
title: Slå Grundlæggende mobilitet og sikkerhed fra
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
ms.openlocfilehash: ff3fe72e1ca3a6445aa29ac18404aae139a70f8a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63594307"
---
# <a name="turn-off-basic-mobility-and-security"></a>Slå Grundlæggende mobilitet og sikkerhed fra

Hvis du effektivt vil deaktivere Standardmobilitet og sikkerhed, skal du fjerne grupper af personer, der er defineret af sikkerhedsgrupper, fra politikkerne for enhedsadministration eller fjerne selve politikkerne.

- Fjern grupper af brugere ved at fjerne brugersikkerhedsgrupper fra de enhedspolitikker, du har oprettet.

- Deaktiver Grundlæggende mobilitet og sikkerhed for alle ved at fjerne alle politikker for standardmobilitet og sikkerhedsenhed.

Disse indstillinger fjerner håndhævelsen af Grundlæggende mobilitet og sikkerhed for enheder i organisationen. Desværre kan du ikke bare fjerne "unprovision" Basic Mobility and Security, når du har konfigureret den.

> [!IMPORTANT]
> Vær opmærksom på virkningen på brugernes enheder, når du fjerner brugersikkerhedsgrupper fra politikker eller fjerner selve politikkerne. Eksempelvis kan mailprofiler og cachelagrede mails blive fjernet afhængigt af enheden. Du kan få mere at vide   [underHvad sker der, når du sletter en politik eller fjerner en bruger fra politikken?](../../admin/basic-mobility-security/create-device-security-policies.md)

## <a name="remove-user-security-groups-from-basic-mobility-and-security-device-policies"></a>Fjern brugersikkerhedsgrupper fra politikkerne Standardmobilitet og Sikkerhedsenhed

1. I din browsertype: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. Vælg en enhedspolitik, og vælg **Rediger politik**.

3. På  **installationssiden**  skal du vælge **Fjern**.

4. Vælg   **en sikkerhedsgruppe** under Grupper.

5. Vælg  **Fjern**, og vælg **Gem**.

## <a name="remove-basic-mobility-and-security-device-policies"></a>Fjern politikkerne for standardmobilitet og -sikkerhed

1. I din browsertype: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. Vælg en enhedspolitik, og vælg derefter  **Slet politik**.

3. I dialogboksen Advarsel skal du vælge **Ja**.

> [!NOTE]
> Du kan finde flere trin til at fjerne blokeringen af enheder, hvis organisationens enheder stadig er i blokeret tilstand, i blogindlægget [Fjerne adgangskontrol fra Mobilenhedshåndtering til Office 365](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Removing-Access-Control-from-Mobile-Device-Management-for-Office/ba-p/279934).
