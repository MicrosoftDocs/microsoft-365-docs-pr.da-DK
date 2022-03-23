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
description: Administrer iOS-enheder i Grundlæggende mobilitet og sikkerhed.
ms.openlocfilehash: f2539ac1c27bd63c13766e197fc12fafc3906f07
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590404"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>Opret et APNs-certifikat til iOS-enheder

For at administrere iOS-enheder som iPads og iPhones i Basic Mobility and Security skal du oprette et APNS-certifikat.

1. Log på Microsoft 365 med din globale administratorkonto.

2. Skriv i din browser <https://protection.office.com/>.

3. Vælg  **Data loss**  **preventionDevice** > management, og vælg **APNs Certificate for iOS devices**.

4. På siden Apple Push Notification Certificate Indstillinger du  **vælgeNext**.

5. Vælg Download din CSR-fil, og gem anmodningen om certifikatunder signering et sted på din computer, som du kan huske.   **VælgNæste**.

6. På siden Opret et APNs-certifikat:

    1. Vælg Apple APNS Portal for at åbne Apple Push Certificates Portal.

    2. Log på med et Apple-id.

       > [!IMPORTANT]
       > Brug virksomhedens Apple-id, der er knyttet til en mailkonto, som forbliver hos din organisation, også selvom den bruger, der administrerer kontoen, forlader virksomheden. Gem dette id, da du skal bruge det samme id, når certifikatet skal fornys.

    3.   **VælgOprette et certifikat**  og acceptere Vilkår for anvendelse.

    4. Gå til den anmodning om signering af certifikat, du har downloadet til computeren fra Microsoft 365, og **vælg Upload**.

       Download det APNs-certifikat, der er oprettet af Apple Push Certificate Portal, til computeren.

       > [!TIP]
       > Hvis du har problemer med at downloade certifikatet, skal du opdatere din browser.

7. Gå tilbage til Microsoft 365, og vælg **Næste**  for at få   **Upload APNS-certifikatsiden** .

8. Gå til det APN-certifikat, du har downloadet fra Apple Push Certificates Portal.

9.   **VælgFind**.

For at fuldføre konfigurationen skal du gå tilbage til Security & Compliance Center > **SikkerhedspolitikkerAdministration** >  **af** >  **administration Af administrere indstillinger**.
