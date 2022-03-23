---
title: Administrere brugersamtykke til apps i Microsoft 365
f1.keywords:
- CSH
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
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 7e453a40-66df-44ab-92a1-96786cb7fb34
description: Få mere at vide om brugersamtykke til apps, og hvordan du aktiverer dem for at tillade tredjepartsapps at få adgang til Microsoft 365 oplysninger.
ms.openlocfilehash: d9a07eb333b0abdb3cb6a890ac2de3d19ad3685b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590698"
---
# <a name="managing-user-consent-to-apps-in-microsoft-365"></a>Administrere brugersamtykke til apps i Microsoft 365

Denne indstilling styrer, om brugerne kan give samtykke til apps, der bruger OpenID-Forbind og OAuth 2.0 til logon og anmodninger om at få adgang til data. En app kan oprettes fra din egen organisation, eller den kan komme fra Office 365 en anden organisation eller en tredjepart.

Hvis du slår denne indstilling til, vil disse apps bede brugerne om tilladelse til at få adgang til din organisations data, og brugerne kan vælge, om de vil tillade det. Hvis du slår denne indstilling fra, skal administratorer acceptere disse apps, før brugerne kan bruge dem. I dette tilfælde skal du overveje at konfigurere en arbejdsproces for administratorsamtykke i Azure-portalen, så brugere kan sende en anmodning om administratorgodkendelse for at bruge enhver blokeret app.

En bruger kan kun give adgang til apps, som brugeren ejer, og som har adgang Office 365 oplysninger. De kan ikke give en app adgang til andre brugeres oplysninger.

## <a name="turning-user-consent-on-or-off"></a>Slå brugersamtykke til eller fra

Her kan du se, hvordan du kan slå Brugersamtykke til apps til eller fra.

1. I Administration skal du gå til siden **Indstillinger** \> **Org** [settingsServices](https://go.microsoft.com/fwlink/p/?linkid=2053743) >  og derefter vælge **Brugersamtykke til apps**.

2. På siden **Brugersamtykke til apps** skal du vælge indstillingen for at slå brugersamtykke til eller fra.

## <a name="related-content"></a>Relateret indhold 

[Konfigurer arbejdsprocessen for administratorsamtykke](/azure/active-directory/manage-apps/configure-admin-consent-workflow) (artikel)\
[Administrere samtykke til programmer og vurdere anmodninger om samtykke](/azure/active-directory/manage-apps/manage-consent-requests) (artikel)