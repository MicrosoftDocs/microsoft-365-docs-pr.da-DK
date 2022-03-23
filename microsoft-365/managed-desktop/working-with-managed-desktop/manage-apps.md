---
title: Administrer apps i Microsoft-administreret skrivebord
description: Oplysninger om, hvordan du opdaterer line of business-apps, der er installeret på Microsoft-administrerede computerenheder
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.date: 01/18/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: a51be2521924164a8c90a51fcf99328ecf511877
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63587865"
---
# <a name="manage-line-of-business-apps-in-microsoft-managed-desktop"></a>Administrer line of business-apps i Microsoft Managed Desktop

<!--Application management -->

Der er et par måder, hvorpå du kan administrere app-opdateringer og installere opdateringerne til dine Microsoft Managed Desktop-enheder. Du kan foretage appopdateringer i Microsoft Managed Desktop-portalen eller Intune.

<span id="update-app-mmd" />

## <a name="update-line-of-business-apps-in-microsoft-managed-desktop"></a>Opdater line of business-apps i Microsoft Managed Desktop

**Sådan opdaterer du dine line of business-apps i Microsoft Managed Desktop-portalen:**

1. Log på [administrationsportalen for Microsoft-administreret skrivebord](https://aka.ms/mmdportal).
1. Under **Lager skal** du vælge **Apps**.  
1. Vælg den app, du vil opdatere, og vælg derefter **Rediger**.
1. Under **Administrer skal** du vælge **Egenskaber**.
1. Vælg **App-pakkefil**, og søg derefter efter at uploade en ny app-pakkefil.
1. Vælg **App-pakkefil**.
1. Vælg mappeikonet, og gå til placeringen af din opdaterede appfil. Vælg **Åbn**. Appoplysningerne opdateres med pakkeoplysningerne.
1. Kontrollér, **at appversionen** afspejler den opdaterede app-pakke.

Den opdaterede app installeres på din brugers enheder.

<span id="update-app-intune" />

## <a name="update-line-of-business-apps-in-intune"></a>Opdater line of business-apps i Intune

**Sådan opdaterer du dine line of business-apps i Intune:**

1. Log på [Azure-portalen](https://portal.azure.com).
2. Vælg **Alle** **tjenesterIntune** > . Intune findes i **sektionen Overvågning +** Administration.
3. Vælg **Klientapps > apps**.
4. Find og vælg din app på listen over apps.
5. I sektionen **Oversigt** skal du vælge **Egenskaber**.
6. Vælg **App-pakkefil**.
7. Vælg mappeikonet, og gå til placeringen af din opdaterede appfil. Vælg **Åbn**. Appoplysningerne opdateres med pakkeoplysningerne.
8. Kontrollér, **at appversionen** afspejler den opdaterede app-pakke.

<span id="roll-back-app-mmd" />

## <a name="roll-back-an-app-to-a-previous-version"></a>Rulle en app tilbage til en tidligere version

Når en ny version af en app er installeret, og der findes en fejl, kan du vende tilbage til en tidligere version. Processen, der er beskrevet nedenfor, er til apps, hvor typen er angivet **som Windows MSI line of business-app** **eller Windows-app (Win 32) – forhåndsvisning**

**Sådan tilbagerulles en line of business-app til en tidligere version:**

1. Log på [administrationsportalen for Microsoft-administreret skrivebord](https://aka.ms/mmdportal).
2. Under **Lager skal** du vælge **Apps**.  
3. Vælg den app, du vil tilbagerulle, og vælg derefter **Rediger**.
4. Under **Administrer skal** du vælge **Egenskaber**.
    - Du **Windows appapps med MSI-line of business** ved at vælge **Appoplysninger** og derefter vælge **Ja** under **Ignorer appversion**.
    - For **Windows appen (Win 32) –** eksempelapps skal du vælge **Appoplysninger**, vælge **Registreringsregler** og derefter vælge **Tilføj**.
    Hvis der er en MSI-regel, skal du kontrollere, at **kontrol af MSI-produktversion** er indstillet til **Nej**.
5. [Upload en tidligere version af appkildefilen til](../get-started/deploy-apps.md) Microsoft Managed Desktop Admin-portalen.  
