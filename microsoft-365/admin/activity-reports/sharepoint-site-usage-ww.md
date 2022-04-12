---
title: Microsoft 365 Administration SharePoint rapporter over webstedsforbrug
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
description: Få rapporten over SharePoint webstedsforbrug for at finde ud af, hvor mange filer brugerne gemmer på SharePoint websteder, hvor mange der aktivt bruges, og hvor meget lagerplads der bruges i alt.
ms.openlocfilehash: afcaa6cd087948c635604dbadeb9d56c6d48c1a9
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64781495"
---
# <a name="microsoft-365-reports-in-the-admin-center---sharepoint-site-usage"></a>Microsoft 365 Rapporter i Administration – SharePoint brug af websted

Som Microsoft 365 administrator viser dashboardet Rapporter aktivitetsoversigten på tværs af forskellige produkter i din organisation. Det giver dig mulighed for at foretage detailudledning for at få mere detaljeret indsigt i de aktiviteter, der er specifikke for hvert produkt. Du kan f.eks. få en overordnet visning af den værdi, du får fra SharePoint med hensyn til det samlede antal filer, som brugerne gemmer på SharePoint websteder, hvor mange filer der aktivt bruges, og det lager, der forbruges på alle disse websteder. Derefter kan du analysere rapporten over SharePoint webstedsforbrug for at forstå tendenser og oplysninger på webstedsniveau for alle websteder. 

## <a name="how-to-get-to-the-sharepoint-site-usage-report"></a>Sådan får du vist rapporten over brug af SharePoint websted

1. I Administration skal du gå til siden **Rapportanvendelse**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank"></a> 
2. På startsiden for dashboardet skal du klikke på knappen **Vis mere** på kortet SharePoint.

## <a name="show-user-details-in-the-reports"></a>Vis brugeroplysninger i rapporterne

Rapporter indeholder oplysninger om din organisations forbrugsdata. Rapporter viser som standard oplysninger med identificerbare navne for brugere, grupper og websteder. Fra og med den 1. september 2021 skjuler vi brugeroplysninger som standard for alle rapporter som en del af vores løbende forpligtelse til at hjælpe virksomheder med at understøtte deres lokale love om beskyttelse af personlige oplysninger.
  
Brugerlisten vil se sådan ud:
  
![Rapporter – anonymiseret brugerliste.](../../media/2ed99bce-4978-4ee3-9ea2-4a8db26eef02.png)
  
Globale administratorer kan gendanne denne ændring for deres lejer og vise identificerbare brugeroplysninger, hvis organisationens praksis for beskyttelse af personlige oplysninger tillader det. Det kan opnås i Microsoft 365 Administration ved at følge disse trin:
  
1. I Administration skal du gå til siden **Indstillinger** \> **Org Indstillinger** \> **Services**.

2. Vælg **Rapporter**. 
  
3. Fjern markeringen af sætningen **Vis de identificerede navne for brugere, grupper og websteder i alle rapporter,** og gem derefter dine ændringer. 
  
## <a name="interpret-the-sharepoint-site-usage-report"></a>Fortolkning af rapporten over anvendelse af SharePoint websted

Du kan få vist brugen af webstedet i SharePoint rapport ved at vælge fanen **Webstedsforbrug**.

:::image type="content" alt-text="Microsoft 365 rapporter – Microsoft SharePoint rapport over webstedsforbrug." source="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png" lightbox="../../media/d1cb6200-e81c-460b-9d05-53f4bd7cf5ee.png":::

Vælg **Vælg kolonner** for at tilføje eller fjerne kolonner fra rapporten.

:::image type="content" alt-text="SharePoint rapport over brug af websted – vælg kolonner." source="../../media/71ac3195-c494-40c1-9346-a858125ef6df.png":::

Du kan også eksportere rapportdataene til en Excel .csv fil ved at vælge linket **Eksportér**. Dette eksporterer data for alle brugere og giver dig mulighed for at foretage enkel sortering og filtrering for yderligere analyse. Hvis du har mindre end 2.000 brugere, kan du sortere og filtrere i tabellen i selve rapporten. Hvis du har mere end 2.000 brugere, skal du eksportere dataene for at kunne filtrere og sortere dem. 

Den **SharePoint webstedsforbrugsrapport** kan ses for tendenser for de seneste 7 dage, 30 dage, 90 dage eller 180 dage. Men hvis du vælger en bestemt dag i rapporten, viser tabellen data for op til 28 dage fra dags dato (ikke den dato, hvor rapporten blev genereret).
  
|Metriske|Beskrivelse|
|:-----|:-----|
|URL-adresse til websted  |Webstedets fulde URL-adresse. |
|Slettet  |Webstedets status for sletning. Det tager mindst 7 dage, før websteder markeres som slettede.  |
|Webstedsejer  |Brugernavnet for den primære ejer af webstedet.   |
|Webstedets ejers hovednavn  |Mailadressen på ejeren af webstedet. |
|Seneste aktivitetsdato (UTC)  | Datoen for sidste gang, filaktiviteten blev registreret, eller en side blev vist på webstedet.  |
|Id for følsomhedsmærkat for websted  | Følsomhedsmærkaten på webstedet.  |
|Ekstern deling  | Indstillingerne for ekstern delbart på webstedet.  |
|Politik for ikke-administreret enhed  | Politikken for webstedsadgang for ikke-administrerede enheder.  |
|Geografisk placering  | Webstedets Geo-placering.  |
|Filer  |Antallet af filer på webstedet. |
|Aktive filer  | Antallet af aktive filer på webstedet. En fil anses for at være aktiv, hvis den er blevet gemt, synkroniseret, ændret eller delt inden for den angivne tidsperiode.<br/> BEMÆRK! Hvis filer blev fjernet i den angivne tidsperiode for rapporten, kan antallet af aktive filer, der vises i rapporten, være større end det aktuelle antal filer på webstedet.  |
|Storage brugt (MB)  |Den mængde lagerplads, der i øjeblikket bruges på webstedet.  |
|Storage allokeret (MB)  |Den maksimale lagermængde, der er allokeret til webstedet.  |
|Sidevisninger  |Antallet af gange, sider blev vist på webstedet.  |
|Besøgte sider  |Antallet af entydige sider, der blev besøgt på webstedet.  |
|Antal anonyme links  |Det antal gange, dokumenter eller mapper deles ved hjælp af "Alle med linket" på webstedet.  |
|Antal virksomhedslinks  |Det antal gange, dokumenter eller mapper deles ved hjælp af "Personer i organisationen med linket" på webstedet.  |
|Sikkert link til antal gæster  |Det antal gange, dokumenter eller mapper deles ved hjælp af "bestemte personer" på webstedet.  |
|Sikkert link til medlemsantal  |Det antal gange, dokumenter eller mapper deles ved hjælp af "bestemte personer" på webstedet.  |
|Rodwebstedsskabelon  |Den skabelon, der bruges til at oprette webstedet.  <br/> BEMÆRK! Hvis du vil filtrere dataene efter forskellige webstedstyper, skal du eksportere dataene og bruge kolonnen Rodwebskabelon. |

