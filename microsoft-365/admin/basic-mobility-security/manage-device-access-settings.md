---
title: Administrer indstillinger for enhedsadgang i Grundlæggende mobilitet og sikkerhed
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
ms.custom:
- AdminSurgePortfolio
search.appverid:
- MET150
description: Grundlæggende mobilitet og sikkerhed kan hjælpe dig med at sikre og administrere mobilenheder.
ms.openlocfilehash: ef74aba7398867ad97748feba45647e7cf4aa609
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591439"
---
# <a name="manage-device-access-settings-in-basic-mobility-and-security"></a>Administrer indstillinger for enhedsadgang i Grundlæggende mobilitet og sikkerhed

Hvis du bruger Grundlæggende mobilitet og sikkerhed, kan der være enheder, som du ikke kan administrere med Grundlæggende mobilitet og Sikkerhed. Hvis det er ja, bør du blokere Exchange ActiveSync appadgang til mails Microsoft 365 til mobilenheder, der ikke understøttes af Grundlæggende mobilitet og sikkerhed. Dette er med til at sikre dine organisationsoplysninger på tværs af flere enheder.

Benyt følgende fremgangsmåde:

1. Log på Microsoft 365 med din globale administratorkonto.

2. Skriv følgende i din browser: [https://protection.office.com](https://protection.office.com/)

    > [!IMPORTANT]
    > Hvis det er første gang, du bruger Basic Mobility and Security til Microsoft 365 Business Standard, skal du aktivere det her: [Aktivér Grundlæggende sikkerhed og mobilitet](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). Når du har aktiveret det, skal du administrere dine enheder med [Office 365 Security & Compliance](https://protection.office.com/).

3. Gå til Beskyttelse mod datatab > **politikker for** > enhedshåndtering **, og** vælg Administration af adgangsindstillinger for  **hele organisationen**.

4.  **VælgBlock**.

    :::image type="content" source="../../media/basic-mobility-security/bms-5-block-access.png" alt-text="Afkrydsningsfeltet Adgangsblokering for grundlæggende mobilitet og sikkerhed.":::

5.  **VælgSave**.

Hvis du vil vide, hvilke enheder Basic Mobility og Security understøtter, skal du  [seCapabilities of Basic Mobility and Security](capabilities.md).
