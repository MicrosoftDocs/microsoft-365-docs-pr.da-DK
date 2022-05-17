---
title: Brug af domæne Forbind
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: ec6f4bd8-5996-4505-ba68-afaf8a141fb9
description: Få mere at vide om, hvordan du arbejder med domæne Forbind aktiverede registratorer og føjer dit domæne til Microsoft 365.
ms.openlocfilehash: e20588181a5e9ca55d11844e2f31c3504a2bbfa0
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437607"
---
# <a name="using-domain-connect-to-add-your-domain-to-microsoft-365"></a>Brug af Domæne Forbind til at føje dit domæne til Microsoft 365

 **[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml)** , hvis du ikke kan finde det, du leder efter.

[Med domæne Forbind](https://www.domainconnect.org/) aktiverede registratorer kan du føje dit domæne til Microsoft 365 i en proces med tre trin, der tager minutter.

I guiden bekræfter vi blot, at du ejer domænet, og derefter konfigurerer vi automatisk dine domæneposter, så mail kommer til Microsoft 365 og andre Microsoft 365 tjenester, f.eks. Teams, arbejder med dit domæne.

> [!NOTE]
> Sørg for at deaktivere pop op-blokeringer i browseren, før du starter installationsguiden.

## <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Domæne Forbind registratorer, der integreres med Microsoft 365

- [11&amp; IONOS](https://www.1and1.com/)
- [123Reg](https://www.123-reg.co.uk/)
- [Godaddy](https://www.godaddy.com/)
- [Wordpress](https://wordpress.com/)
- [Plesk](https://www.plesk.com/)
- [Medietemple](https://mediatemple.net/)
- SecureServer eller WildWestDomains (GoDaddy-forhandlere, der bruger SecureServer DNS-hosting)
  - [MadDog-webhosting](https://maddogwebhosting.com/domains/)
  - [CheapNames](https://www.cheapnames.com)

## <a name="what-happens-to-my-email-and-website"></a>Hvad sker der med min mail og mit websted?

Når du er færdig med at konfigurere, opdateres MX-posten for dit domæne, så den peger på Microsoft 365, og alle mails for dit domæne begynder at komme til Microsoft 365. Sørg for, at du har tilføjet brugere, og konfigurer postkasser i Microsoft 365 for alle, der modtager mail på dit domæne!

Hvis du har et websted, som du bruger sammen med din virksomhed, fortsætter det med at fungere, hvor det er. Trinnene til konfiguration af domæne Forbind påvirker ikke dit websted.
