---
title: Test dit Intune program på testbasen
description: Sådan tester du dit intune-program
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 04/11/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: Tinacyt
f1.keywords: NOCSH
ms.openlocfilehash: e2e56b931dd7ae26fa5881036f4cf208b66922d6
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "66858383"
---
# <a name="test-your-intune-application-on-test-base"></a>Test dit Intune program på testbasen 
  > [!Note] 
  > Denne vejledning hjælper dig med at uploade din intunewinformatpakke til testbasen. Du kan finde generelle instruktioner til overførsel af testbasepakker i dette [dokument](https://microsoft.sharepoint.com/:w:/t/AzureSUVPCoreTeam/EeHQIT3qA0FKqBDWI5TzmzgBiH2Syz39o5VbY2kdugMn4A?e=Rk1KD9).

## <a name="intunewin-upload-flow"></a>Intunewin Upload Flow
For yderligere at muliggøre kommerciel udnyttelse begyndte Test Base at understøtte intunewin-format for it-teknikere, der administrerer apps til deres apps i Intune som standard onboardingpakkeformat. Intunewin-uploadflowet giver it-teknikere mulighed for at genbruge deres intunewin-formatpakker, som indeholder de apps, de har installeret på deres enheder via MEM/Intune til hurtigt at onboarde deres apps og teste konfigurationer til testbasen. 

**Forudsætninger**
  - I øjeblikket understøtter Test Base synkronisering via det samme abonnement mellem Intune-konto og Test Base-konto (du behøver ikke at have en Intune konto for at uploade din intunewin-pakke, men hvis du vil synkronisere Intune konfiguration for intunewin-filens tilsvarende apps fra Intune, skal du sikre dig, at din Intune  -kontoen oprettes under det samme abonnement som din Test Base-konto).
  - Intunewin-pakker, der skal uploades. 

**Overførselsflow for Intunwin-fil (synkroniseret med Intune-konto)** <br/>
Som Intune kunde, der har en Intune pakke, som allerede er onboardet på Intune portal. Kunden kan onboarde intunewin-pakken (der indeholder en app med/uden afhængigheder af forudinstallerede apps, der administreres i Intune) til Test Base-tjenesten. (via Intune konto, som har den korrekte tilladelse til at synkronisere oplysningerne om Intune app).

**Forberedelsestrin**
1. Log på med din Test Base-konto.
2. Forbered din intunewin-pakke.
3. Begynd at uploade ved at klikke på linket "Opret pakke med Intune app" som nedenfor.
    
    > [!div class="mx-imgBorder"] 
    > ![Begynd at bygge en pakke med Intune app](Media/testintuneapplication01.png) 


**Trin 1: Definer indhold**
1. Upload den intunewin-pakke, du vælger.
2. Tildel token ved at klikke på nedenstående link "Tildel token, og vælg app".
3. Når du har synkroniseret automatisk med din Intune konto, vises du med appen dine programmer under din Intune konto. Vælg den app, der svarer til din uploadede intunewin-pakke, og klik derefter på "Vælg".
    
    > [!div class="mx-imgBorder"] 
    > ![Upload intune-pakken](Media/testintuneapplication02.png) 


5. På siden Trin 1 kan du se afhængigheder, der er angivet under afsnittet Afhængighed, og du kan enten vælge at uploade afhængighedens installationsfil eller fjerne den fra dette trin (hvis du planlægger at administrere afhængigheden i trin 3 alene, skal du angive de relaterede binære filer). Valgte afhængigheder i dette afsnit forudinstalleres på samme måde, som de installeres via Intune.
    
    > [!div class="mx-imgBorder"] 
    > ![Overfør afhængighedspakke](Media/testintuneapplication03.png) 


**Trin 2: Konfigurer test**
1. Vælg powershell.
2. Vælg Fra og med.


**Trin 3: Rediger pakke**
1. Kontrollér, at de scripts, der genereres automatisk, er mærket korrekt.
2. Hvis du har synkroniseret konfigurationen fra Intune, kan du se, at installations-/fjernelseskommandoerne for testappen er blevet tilføjet i installations-/fjernelsesscripts, og kommandoerne for den afhængighed **, der er blevet overført**, bør også indsættes i package explorer-træet til gennemsyn.
3. Kontrollér, at de binære testapps er flyttet under **mappen Bin** .
4. Kontrollér de binære afhængigheder **, der er overført** under **guid-mappen** .
5. Du kan redigere scripts efter behov og gemme dem.
    > [!Note] 
    > Hvis afhængighedspakken ikke er blevet overført, genererer Test Base ikke installations-/fjernelseskommandoer til den.


**Trin 4: Test matrix**
1. Kontrollér de standardvalg, der findes på os-listen, for de tilsvarende testtyper.
    - Testbasen understøtter valg af flere kumulative Windows-opdateringer **fra Windows 10 1909 undtagen Windows 10 2004**, men Intune Win-app tildeles en version fra versioner, der er lig med eller højere end **Windows 10 1607**.
    - Os-listen vil som standard indeholde alle de OSes, der understøttes af testbasen, som er højere end det minimumsystem, der er angivet for Intune Win-appen.
2. Brugerne har tilladelse til at ændre operativsystemets valg efter behov.


**Trin 5: Gennemse + Publicer** <br/>
Gennemse den konfiguration, hvorefter pakken kan publiceres.<br/><br/>


**Overførselsflow for Intunwin-fil (der kan ikke synkroniseres med Intune konto)** <br/>
Som testbasekunde, der har en separat intunewin-pakke. Kunden kan onboarde intunewin-pakken (der indeholder en app med/uden afhængigheder af forudinstallerede apps, der administreres i Intune) uden at skulle have tilladelse til Intune konto for at afslutte onboardingprocessen.

**Forberedelsestrin**
1. Log på med din Test Base-konto.
2. Forbered din intunewin-pakke.
3. Begynd at uploade ved at klikke på linket "Opret pakke med Intune app" som nedenfor.
    
    > [!div class="mx-imgBorder"] 
    > ![Opret pakke med Intune app](Media/testintuneapplication04.png) 


**Trin 1: Definer indhold**
1. Upload intunewin-pakken.
2. Angiv alle oplysninger i henhold til dine indstillinger.


**Trin 2: Konfigurer test**
1. Vælg powershell.
2. Vælg Fra og med.


**Trin 3: Rediger pakke**
1. Kontrollér, at scripts er mærket korrekt.
2. Da ingen installations-/fjernelseskommandoer synkroniseres fra den tilsvarende Intune konto, skal du selv angive alle scripts (install/uninstall/launch/close).
3. Kontrollér, at de binære testapps er flyttet under mappen Bin.
4. Du kan redigere scripts efter behov og gemme dem.


**Trin 4: Test matrix**
1. Der er ikke valgt nogen standardversion af operativsystemet.
2. Brugerne har tilladelse til at foretage deres egne valg på de OSes, der skal planlægges.


**Trin 5: Gennemse + Publicer** <br/>
Gennemse den konfiguration, hvorefter pakken kan publiceres.




