---
title: Aktiv bruger i Microsoft 365 brugsrapporter
ms.author: efrene
author: efrene
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 093a6d0d-890b-489e-9f46-b15687d3fe4f
description: Få mere at vide om en aktiv Microsoft 365 af Microsoft 365, aktivitetsrapporter og anvendelsesmålepunkter.
ms.openlocfilehash: 748bd08e08cc5e8243c3733c4b3f8448e15ab050
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63589300"
---
# <a name="active-user-in-microsoft-365-usage-reports"></a>Aktiv bruger i Microsoft 365 brugsrapporter

## <a name="active-user-in-usage-reports"></a>Aktiv bruger i forbrugsrapporter

En aktiv bruger af Microsoft 365 til [Microsoft 365 til forbrugsanalyse](usage-analytics.md) og aktivitetsrapporter i Administration defineres [](../activity-reports/activity-reports.md) således. 
  
|**Produkt**|**Definition af en aktiv bruger**|**Bemærkninger**|
|:-----|:-----|:-----|
|Exchange Online  <br/> |Alle brugere, der har udført en af følgende handlinger: Markér som læst, send meddelelser, opret aftaler, send mødeindkaldelser, acceptér (som foreløbig) eller afvis mødeindkaldelser, annuller møder.  <br/> |Der vises ingen kalenderoplysninger, dette tilføjes i en kommende opdatering.  <br/> |
|SharePoint Online  <br/> |Alle brugere, der har interageret med en fil ved at oprette, redigere, få vist, slette, dele internt eller eksternt, eller som har synkroniseret med klienter på et websted eller fået vist en side på et websted.  <br/> |Metrikværdierne for aktive brugere for SharePoint Online i skabelonappen til Microsoft 365-forbrugsanalyse afspejler kun brugere, der har brugt filaktivitet i forhold til et SharePoint-teamwebsted eller et gruppewebsted. Skabelonappen opdateres for at synkronisere definitionen til det samme som for forbrugsrapporter i Administration.  <br/> |
|OneDrive for Business  <br/> |Alle brugere, der har interageret med en fil ved at oprette, redigere, få vist, slette, dele internt eller eksternt, eller som har synkroniseret med klienter.  <br/> ||
|Yammer  <br/> |Alle brugere, der har læst, opslået eller syntes godt om en meddelelse Yammer.  <br/> ||
|Skype for Business  <br/> |Alle brugere, som har deltaget i en peer-to-peer-session (herunder chat, lyd- og videoopkald, programdeling og filoverførsler), eller som har organiseret eller deltaget i et møde.  <br/> ||
|Office  <br/> |Alle brugere, der har aktiveret deres Microsoft 365 Pro Plus-, Visio Pro- Project Pro-abonnement på mindst én enhed.  <br/> ||
|Microsoft 365 grupper  <br/> |Et gruppemedlem med postkasseaktivitet (hvis der er blevet sendt en meddelelse til gruppen)  <br/> |Denne definition forbedres med filaktivitet på gruppewebstedet og Yammer gruppeaktivitet (filaktivitet på gruppewebstedet og meddelelse skrevet i Yammer gruppe, der er knyttet til gruppen). Disse data er i øjeblikket ikke tilgængelige i Microsoft 365 for brugerstatistik-skabelonappen  <br/> |
|Microsoft Teams  <br/> |Alle brugere, der har deltaget i chatmeddelelser, private chatmeddelelser, opkald, møder eller anden aktivitet. Andre aktiviteter defineres som antallet af andre teamaktiviteter af brugeren, som omfatter og ikke er begrænset til: synes godt om meddelelser, apps, arbejde på filer, søgning, følger teams og kanaler og vælger dem som foretrukne.  <br/> ||
   
## <a name="adoption-metrics"></a>Målepunkter for anvendelse

[Microsoft 365 forbrugsanalyse indeholder](usage-analytics.md) flere målepunkter for anvendelse, der er relateret til aktive brugere, for at vise indføring af produkterne over tid. Disse målepunkter er gyldige for måned, år og produkt, der er valgt, og er defineret som følger. 
  
|**Metrisk**|**Beskrivelse**|
|:-----|:-----|
|EnabledUsers  <br/> |Antal brugere, der er aktiveret til at bruge produktet i måneden.  <br/> |
|ActiveUsers  <br/> |Antal brugere, der er aktive i måneden.  <br/> |
|MoMReturningUsers  <br/> |Antal aktive brugere i den måned, der også var aktive i den foregående måned.  <br/> |
|FirstTimeUsers  <br/> |Antal aktive brugere i måneden, der aldrig har brugt tjenesten før.  <br/> |
|CumulativeActiveUsers  <br/> |Antallet af brugere, der er aktive i måneden plus den foregående måned.  <br/> |
|ActiveUsers(%)  <br/> |Procent af brugere, afrundet til nærmeste tiendedel, aktiv i måneden sammenlignet med antallet af brugere aktiveret i den pågældende måned.  <br/> |
|MoMReturningUsers(%)  <br/> |Procent af brugere, afrundet til nærmeste tiendedel, aktiv i den måned, der også var aktiv i den foregående måned sammenlignet med antallet af aktive brugere.  <br/> |
   
MoMReturningUsers, FirstTimeUsers, &amp; CumulativeActiveUsers blev nulstillet fra 1. januar 2018 med medtagelse af Microsoft Teams.
  
