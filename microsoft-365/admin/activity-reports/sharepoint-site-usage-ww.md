---
title: Microsoft 365 Administration SharePoint rapporter over brug af websted
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
- Adm_NonTOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
description: Få rapporten SharePoint webstedsbrug for at vide, hvor mange filer brugerne gemmer på SharePoint, hvor mange der bruges aktivt og den samlede forbrugte lagerplads.
ms.openlocfilehash: ae25562924f569431b3a6d7eda3099f69cd912b1
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754223"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-site-usage"></a>Microsoft 365 Rapporter i Administration – SharePoint brug af websted

Som administrator Microsoft 365, viser dashboardet Rapporter aktivitetsoversigten på tværs af forskellige produkter i organisationen. Det gør det muligt for dig at få mere detaljeret indsigt i aktiviteterne, der er specifikke for hvert produkt. Du kan f.eks. få en visning på højt niveau af den værdi, du får fra SharePoint med hensyn til det samlede antal filer, som brugere gemmer på SharePoint-websteder, hvor mange filer der bruges aktivt, og hvor meget lagerplads der forbruges på tværs af alle disse websteder. Derefter kan du analysere rapporten over SharePoint for at forstå tendenserne og niveaudetaljerne pr. websted for alle websteder. 

## <a name="how-to-get-to-the-sharepoint-site-usage-report"></a>Sådan kommer du til rapporten SharePoint webstedsbrug

1. I Administration skal du gå til **siden Rapporter** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">over</a> brug. 
2. Fra dashboardets startside skal du klikke på **knappen Vis** mere på SharePoint visitkort.

## <a name="show-user-details-in-the-reports"></a>Vis brugeroplysninger i rapporterne

Rapporter indeholder oplysninger om organisationens brugsdata. Rapporter viser som standard oplysninger med identificerbare navne for brugere, grupper og websteder. Pr. 1. september 2021 skjuler vi som standard brugeroplysninger for alle rapporter som en del af vores løbende bestræbelser på at hjælpe virksomheder med at understøtte den lokale lovgivning om beskyttelse af personlige oplysninger.
  
Din brugerliste vil se sådan ud:
  
![Rapporter – anonymiseret brugerliste.](../../media/2ed99bce-4978-4ee3-9ea2-4a8db26eef02.png)
  
Globale administratorer kan vende tilbage til denne ændring for deres lejer og vise identificerbare brugeroplysninger, hvis organisationens praksis for beskyttelse af personlige oplysninger tillader det. Det kan opnås i Microsoft 365 Administration ved at følge disse trin:
  
1. I Administration skal du gå til siden **Indstillinger** \> **Org Indstillinger** \> **Services**.

2. Vælg **Rapporter**. 
  
3. Fjern markeringen i **sætningen Vis ikke-identificerede navne for brugere,** grupper og websteder i alle rapporter, og gem derefter ændringerne. 
  
## <a name="interpret-the-sharepoint-site-usage-report"></a>Fortolk rapporten SharePoint webstedsbrug

Du kan få vist webstedsforbruget i SharePoint ved at vælge **fanen Webstedsforbrug**.

:::image type="content" alt-text="Microsoft 365 - Microsoft SharePoint rapport over brug af websteder." source="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png" lightbox="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png":::

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.

:::image type="content" alt-text="SharePoint anvendelsesrapport for websted – vælg kolonner." source="../../media/71ac3195-c494-40c1-9346-a858125ef6df.png":::

Du kan også eksportere dataene i rapporten til Excel .csv fil ved at vælge **linket Eksportér**. Dette eksporterer data for alle brugere, så du kan foretage simpel sortering og filtrering til yderligere analyse. Hvis der er mindre end 2000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2000 brugere, skal du eksportere dataene, før du kan filtrere og sortere. 

I **SharePoint for webstedsbrug** kan du se tendenser i løbet af de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, vises der i tabellen data for op til 28 dage fra den aktuelle dato (ikke den dato rapporten blev oprettet).
  
|Metrisk|Beskrivelse|
|:-----|:-----|
|URL-adresse til websted  |Webstedets fulde URL-adresse. |
|Slettet  |Webstedets sletningsstatus. Det tager mindst 7 dage, før websteder markeres som slettet.  |
|Webstedsejer  |Brugernavnet på den primære ejer af webstedet.   |
|Ejer af webstedets hovednavn  |Mailadressen på ejeren af webstedet. |
|Dato for seneste aktivitet (UTC)  | Datoen for sidste gang, filaktiviteten blev registreret, eller en side blev vist på webstedet.  |
|Webstedets følsomhedsmærkat-id  | Følsomhedsmærkatet på webstedet.  |
|Ekstern deling  | Indstillinger for eksterne skygger på webstedet.  |
|Ikke-administreret enhedspolitik  | Politikken for webstedsadgang for enheder, der ikke er administrerede.  |
|Geoplacering  | Webstedets geografiske placering.  |
|Filer  |Antallet af filer på webstedet. |
|Aktive filer  | Antallet af aktive filer på webstedet. En fil betragtes som aktiv, hvis den er blevet gemt, synkroniseret, ændret eller delt inden for den angivne periode.<br/> BEMÆRK! Hvis filerne er blevet fjernet i løbet af den angivne periode for rapporten, kan antallet af aktive filer, der vises i rapporten, være større end det aktuelle antal filer på webstedet.  |
|Storage anvendt (MB)  |Mængden af lagerplads, der aktuelt bruges på webstedet.  |
|Storage allokeret (MB)  |Den maksimale mængde lagerplads, der er allokeret til webstedet.  |
|Sidevisninger  |Det antal gange, siderne blev vist på webstedet.  |
|Sider besøgt  |Antallet af unikke sider, der blev besøgt på webstedet.  |
|Antal anonyme links  |Antallet af gange, dokumenter eller mapper deles ved hjælp af "Alle med linket" på webstedet.  |
|Antal firmalinks  |Antallet af gange, dokumenter eller mapper deles ved hjælp af "Personer i organisation med linket" på webstedet.  |
|Sikkert link til antal gæster  |Antallet af gange, dokumenter eller mapper deles ved hjælp af "bestemte personer" på webstedet.  |
|Sikkert link til medlemsantal  |Antallet af gange, dokumenter eller mapper deles ved hjælp af "bestemte personer" på webstedet.  |
|Rodwebskabelon  |Den skabelon, der bruges til at oprette webstedet.  <br/> BEMÆRK! Hvis du vil filtrere dataene efter forskellige webstedstyper, skal du eksportere dataene og bruge kolonnen Rodwebskabelon. |

