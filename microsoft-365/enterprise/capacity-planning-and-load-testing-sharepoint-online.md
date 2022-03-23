---
title: Kapacitetsplanlægning og indlæsningstest i SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: Denne artikel beskriver, hvordan du kan installere på SharePoint Online uden at udføre traditionelle belastningstests, da det ikke er tilladt.
ms.openlocfilehash: 8792c59ef96ef97cc36d0908100fd9ebb330857a
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63590587"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Kapacitetsplanlægning og indlæsningstest i SharePoint Online
Denne artikel beskriver, hvordan du kan installere på SharePoint Online uden traditionelle belastningstests, da belastningstests ikke er tilladt på SharePoint Online. SharePoint Online er en skybaseret tjeneste, og indlæsningsfunktionerne, tilstand og den overordnede balance mellem belastning af tjenesten administreres af Microsoft.
  
Den bedste fremgangsmåde til at sikre en vellykket lancering af dit websted er at følge de grundlæggende principper, fremgangsmåder og anbefalinger, der fremhæves i udrulningen af [portalens lancering](planportallaunchroll-out.md).

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>Oversigt over, hvordan SharePoint Online udfører Kapacitetsplanlægning 
En af de vigtigste fordele ved SharePoint Online over en lokal installation er elasticiteten af skyen og optimeringer for brugere i distribuerede områder. Vores omfattende miljø er konfigureret til at servicere millioner af brugere dagligt, så det er vigtigt, at vi håndterer kapacitet effektivt ved at balancere og udvide farme.
  
Væksten er ofte uforudsigelig for hver enkelt lejer i en hvilken som helst farm, men den aggregerede sum af anmodninger er forudsigelig over tid. Ved at identificere væksttendenserne i SharePoint Online kan vi planlægge fremtidig udvidelse.
  
For effektivt at bruge kapacitet og håndtere uventet vækst i en farm har vi automatisering, der registrerer og overvåger forskellige elementer i tjenesten. Der anvendes flere målepunkter, hvoraf en af de vigtigste er CPU-belastning, som bruges som et signal til opskalering af front end-servere. Desuden anbefaler vi en faseindfaset [/bølge-tilgang](planportallaunchroll-out.md), da SQL-miljøer skaleres efter belastning og vækst over tid, og hvis du følger faser og runder, kan du bruge den korrekte fordeling af den pågældende belastning og vækst. 

Kapacitet er mere end bare at tilføje mere hardware løbende, men det gælder også administration og kontrol af denne kapacitet for at sikre, at den servicerer gyldige anmodninger om belastning. Vi anbefaler, at kunder følger den anbefalede vejledning for at sikre, at de får den bedste oplevelse. Det betyder også, at vi har begrænsningsmønstre og -kontrolelementer på plads for at sikre, at vi ikke tillader "stødende" adfærd i tjenesten. Det er ikke alle "dårlige" funktionsmåder, der er tilsigtet, men vi er nødt til at sikre, at vi begrænser effekten af den pågældende funktionsmåde. Du kan finde flere oplysninger om begrænsning, og hvordan du undgår begrænsningen, i artiklen om, hvordan du [undgår at blive begrænsning af vejledningen](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) .

## <a name="why-you-cannot-load-test-sharepoint-online"></a>Derfor kan du ikke indlæse test SharePoint Online
I forbindelse med lokale miljøer bruges belastningstests til at validere skalaantagelser og i sidste ende finde en farms brudpunkt. ved at mætte den med indlæsning. 

Med SharePoint Online er vi nødt til at gøre tingene anderledes, fordi skalaen er relativt flydende og justerer, begrænser og styrer belastningen baseret på visse heuristics. Da der er så stort et miljø med flere lejere, skal vi beskytte alle lejere i samme farm, så vi begrænser automatisk eventuelle belastningtests. Hvis du imidlertid forsøger at belastningstests, men ikke bliver mindre, vil du få skuffende og potentielt misvisende resultater, fordi den farm, du har testet i dag, sandsynligvis vil have haft skaleringsændringer i løbet af testvinduet eller inden for få timer efter test, efterhånden som handlinger til justering af skala og farm udføres løbende.

I stedet for at forsøge at indlæse SharePoint som en tjeneste, bør du i stedet fokusere på at følge de anbefalede fremgangsmåder og følge vejledningen Oprette, starte og vedligeholde [en sund portal](/sharepoint/portal-health).