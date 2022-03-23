---
title: Aktivere SharePoint Multi-Geo din satellits geoplacering
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.collection:
- Strat_SP_gtc
- SPO_Content
ms.localizationpriority: medium
description: Denne artikel indeholder oplysninger til globale eller SharePoint administratorer om aktivering af SharePoint Multi-Geo i satellit-geoplaceringer.
ms.openlocfilehash: b542c1ee77c7b4ca7a6179bac5ce5eaa1090606a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589762"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a>Aktivere SharePoint Multi-Geo din satellits geoplacering

Denne artikel er til globale administratorer eller SharePoint-administratorer, der har oprettet en satellitplacering med flere geografiske placeringer, **før** SharePoint Multi-Geo-funktionaliteterne blev alment tilgængelige d. 27. marts 2019, og som ikke har aktiveret SharePoint Multi-Geo i deres satellit geoplaceringer. 

>[!Note]
>Hvis du har tilføjet en ny geoplacering efter **d. 27. marts 2019**, behøver du ikke at udføre disse instruktioner, da din nye geoplacering allerede er aktiveret til OneDrive og SharePoint Multi-Geo.

Denne vejledning gør det muligt at aktivere SharePoint i din satellitplacering, så dine multi-geo-satellitbrugere kan drage fordel af både OneDrive og SharePoint Multi-Geo i O365. 

>[!IMPORTANT]
>Bemærk, at dette er en envejsaktivering. Når du har angivet SPO-tilstand, vil du ikke kunne vende tilbage til din lejer OneDrive kun Multi-Geo-tilstand uden en eskalering med support. 

## <a name="to-set-a-geo-location-into-spo-mode"></a>Sådan angives en geoplacering i SPO-tilstand

Hvis du vil angive en geoplacering i SPO-tilstand, skal du oprette forbindelse til den geoplacering, du vil angive i SPO-tilstand:

1.    Åbn din SharePoint Online Management Shell 
2.    Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential
3.    Set-SPOMultiGeoExperience</br></br>
![Set-SPOMultiGeoExperience.](../media/Set-SPO-MultiGeo.jpg)
4.    Denne handling tager som regel ca. en time, mens vi udfører forskellige tilbagegiv-handlinger i tjenesten og genstempler din lejer. Efter mindst 1 time skal du udføre en Get-SPOMultiGeoExperience.  Dette viser dig, om denne geoplacering er i SPO-tilstand.</br></br>
![Set-SPOMultiGeoExperience.](../media/Get-SPO-MultiGeo.jpg)

 
 
 
>[!Note]
>Visse cacher i tjenesteopdateringen hver 24. time, så det er muligt, at din satellit-geo i en periode på op til 24 timer periodisk fungerer, som om den stadig var i ODB-tilstand. Dette forårsager ingen tekniske problemer. 
 
Yderligere oplysninger om SharePoint Multi-Geo findes i [aka.ms/sharepointmultigeo](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)


