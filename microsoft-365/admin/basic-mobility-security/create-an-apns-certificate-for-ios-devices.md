---
title: Opret et APNs-certifikat til iOS-enheder
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
description: Hvis du vil administrere iOS-enheder, f.eks. iPads og iPhones i Basic Mobility and Security, skal du starte med at oprette et APN-certifikat.
ms.openlocfilehash: 10d2e8412cfecf3627c7520123592b371bf01fdb
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863516"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>Opret et APNs-certifikat til iOS-enheder

Hvis du vil administrere iOS-enheder, f.eks. iPads og iPhones i Basic Mobility og Security, skal du oprette et APN-certifikat.

1. Log på for at Microsoft 365 med din globale administratorkonto.

1. Gå til [Microsoft 365 Administration](https://portal.office.com/adminportal/home?#/MifoDevices), og vælg **APN-certifikat til iOS**.

1. Vælg **Næste** på siden Certifikat til Apple Push-meddelelse Indstillinger.

1. Vælg Download din CSR-fil, og gem anmodningen om certifikatsignering et sted på din computer, som du vil huske. Vælg **Næste**.

1. På siden Opret et APN-certifikat:

    1. Vælg Apple APNS-portalen for at åbne Portal til Apple Push-certifikater.

    2. Log på med et Apple-id.

       > [!IMPORTANT]
       > Brug et Apple-firma-id, der er knyttet til en mailkonto, som forbliver hos din organisation, selvom den bruger, der administrerer kontoen, forlader kontoen. Gem dette id, fordi du skal bruge det samme id, når det er tid til at forny certifikatet.

    3. Vælg **Opret et certifikat** , og acceptér Vilkår for anvendelse.

    4. Gå til den anmodning om signering af certifikat, du har downloadet til din computer fra Microsoft 365, og vælg **Upload**.

       Download det APN-certifikat, der er oprettet af Apple Push-certifikatportalen, til din computer.

       > [!TIP]
       > Hvis du har problemer med at downloade certifikatet, skal du opdatere din browser.

1. Gå tilbage til Microsoft 365, og vælg **Næste** for at gå til siden **med Upload APNS-certifikat**.

1. Gå til det APN-certifikat, du har downloadet fra Portal til Apple Push-certifikater.

1. Vælg **Udfør**.

Hvis du vil fuldføre installationen, skal du gå tilbage til Security & Compliance Center \> **Sikkerhedspolitikker** \> **Administration af enheder** \> **Administrationsindstillinger**.
