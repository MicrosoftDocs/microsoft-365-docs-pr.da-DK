---
title: Kapacitetsplanlægning og indlæsningstest i SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: I denne artikel beskrives det, hvordan du kan udrulle på SharePoint Online uden at udføre traditionel belastningstest, da det ikke er tilladt.
ms.openlocfilehash: 1d1714bbcdefdbc41ff3ac5d038c6b59a7043a26
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101089"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Kapacitetsplanlægning og indlæsningstest i SharePoint Online
I denne artikel beskrives det, hvordan du kan installere på SharePoint Online uden traditionel belastningstest, da belastningstest ikke er tilladt på SharePoint Online. SharePoint Online er en cloudtjeneste, og belastningsfunktionerne, tilstanden og den overordnede balance for belastningen i tjenesten administreres af Microsoft.
  
Den bedste tilgang til at sikre, at lanceringen af dit websted lykkes, er at følge de grundlæggende principper, fremgangsmåder og anbefalinger, der er fremhævet i [planen for udrulningen af portalen](planportallaunchroll-out.md).

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>Oversigt over, hvordan SharePoint Online udfører kapacitetsplanlægning 
En af de største fordele ved SharePoint Online i forbindelse med en udrulning i det lokale miljø er fleksibiliteten i cloudmiljøet og optimeringer for brugere i distribuerede områder. Vores store miljø er konfigureret til at betjene millioner af brugere dagligt, så det er vigtigt, at vi håndterer kapacitet effektivt ved at balancere og udvide farme.
  
Selvom væksten ofte er uforudsigelig for en hvilken som helst lejer i en farm, er den samlede sum af anmodninger forudsigelig over tid. Ved at identificere væksttendenserne i SharePoint Online kan vi planlægge en fremtidig udvidelse.
  
For effektivt at kunne bruge kapacitet og håndtere uventet vækst på alle farme har vi automatisering, der sporer og overvåger forskellige elementer i tjenesten. Der anvendes flere målepunkter, hvor en af de vigtigste er CPU-belastning, som bruges som et signal til skalering af frontendservere. Derudover anbefaler vi en [faseinddelt/bølgetilgang](planportallaunchroll-out.md), da SQL miljøer skaleres efter belastning og vækst over tid, og når faserne og bølgerne følges, giver det mulighed for korrekt fordeling af denne belastning og vækst. 

Kapacitet handler mere end blot om at tilføje mere hardware løbende, men det vedrører også administration og styring af kapaciteten for at sikre, at den servicerer gyldige belastningsanmodninger. Vi anbefaler, at kunderne følger den anbefalede vejledning for at sikre, at de får den bedste oplevelse. Det betyder også, at vi har begrænsninger for mønstre og kontroller på plads for at sikre, at vi ikke tillader "krænkende" adfærd i tjenesten. Selvom ikke al "dårlig" adfærd er bevidst, er vi nødt til at sikre, at vi begrænser effekten af denne funktionsmåde. Du kan finde flere oplysninger om begrænsning, og hvordan du undgår det, i artiklen Vejledning [til, hvordan du undgår begrænsning](/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) .

## <a name="why-you-cannot-load-test-sharepoint-online"></a>Derfor kan du ikke indlæse test SharePoint Online
I miljøer i det lokale miljø bruges belastningstest til at validere skaleringsantagelse og i sidste ende finde brudpunktet for en farm. ved at mætte den med belastning. 

Med SharePoint Online er vi nødt til at gøre tingene anderledes, fordi skalaen er relativt flydende og justerer, begrænser og styrer belastningen baseret på visse heuristik. Da vi er et så stort miljø med flere lejere, skal vi beskytte alle lejere i den samme farm, så vi begrænser automatisk alle belastningstest. Hvis du forsøger at indlæse test, vil du ud over at være begrænset få skuffende og potentielt vildledende resultater, fordi den farm, du har testet i dag, sandsynligvis vil have haft skaleringsændringer i løbet af testvinduet eller inden for få timer efter testen, da skala- og farmjusteringshandlinger udføres løbende.

I stedet for at forsøge at indlæse test SharePoint som en tjeneste, skal du i stedet fokusere på at følge de anbefalede fremgangsmåder og følge [vejledningen Til oprettelse, start og vedligeholdelse af en sund portal](/sharepoint/portal-health).