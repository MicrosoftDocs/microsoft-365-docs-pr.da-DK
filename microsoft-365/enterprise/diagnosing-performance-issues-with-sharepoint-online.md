---
title: Diagnosticering af problemer med ydeevnen for SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/19/2021
audience: Admin
ms.topic: troubleshooting
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
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: I denne artikel kan du se, hvordan du kan diagnosticere almindelige problemer med dit SharePoint Online-websted ved hjælp af Internet Explorer-udviklerværktøjer.
ms.openlocfilehash: a3ad33b147a20cd5b072f7f3ccc1b9272a58ef54
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63594230"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>Diagnosticering af problemer med ydeevnen for SharePoint Online

I denne artikel kan du se, hvordan du kan diagnosticere almindelige problemer med dit SharePoint Online-websted ved hjælp af Internet Explorer-udviklerværktøjer.
  
Der er fire forskellige måder, hvorpå du kan identificere, at en side på et SharePoint Online-websted har et ydelsesproblem med tilpasningerne.

- Diagnosticering af websteds- og sideydeevne
  
- Netværksovervågning med værktøjslinjen F12

- Sammenligning med en ikke-tilpasset grundlinje

- SharePoint online svarheadermålepunkter

I dette emne beskrives det, hvordan du kan bruge hver af disse metoder til at diagnosticere problemer med ydeevnen. Når du har fundet årsagen til problemet, kan du arbejde på en løsning ved hjælp af artiklerne om forbedring af ydeevnen SharePoint, som du kan finde på https://aka.ms/tune.  

## <a name="use-the-site-and-page-performance-diagnostic-from-the-microsoft-365-admin-center"></a>Brug ydeevnediagnosticering for websted og side fra Microsoft 365 Administration Center

> [!NOTE]
> Hvis du er administrator, og du har problemer med ydeevnen i SharePoint, skal du vælge Kør test nedenfor,  hvilket udfylder diagnosticeringen Websted og sideydeevne i Microsoft 365 Administration Center. Disse test kontrollerer din konfiguration og anbefaler hurtigt de næste trin for at forbedre SharePoint ydeevnen for din lejer.
>> [!div class="nextstepaction"]
>> [Kør test: Kontrollér SharePoint ydeevne](https://aka.ms/PillarSiteandPagePerf)

> [!NOTE] 
> Denne funktion er ikke tilgængelig for Microsoft 365 Government, Microsoft 365 drevet af 21Vianet eller Microsoft 365 Germany.
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>Brug af F12-værktøjslinjen til at diagnosticere ydeevnen SharePoint Online
<a name="F12ToolInfo"> </a>

I denne artikel bruger vi Internet Explorer 11. Versioner af F12-udviklerværktøjerne i andre browsere har lignende funktioner, men kan se lidt anderledes ud. Du kan finde oplysninger om F12-udviklingsværktøjerne i:
  
- [Nyheder i F12-værktøjer](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182632(v=vs.85))

- [Brug af F12-udviklerværktøjerne](/previous-versions/windows/internet-explorer/ie-developer/samples/bg182326(v=vs.85))

Tryk på **F12 for at få adgang til udviklerværktøjerne** , og klik derefter Wi-Fi ikonet:
  
![Skærmbillede af WiFi-ikon for F12-udviklerværktøjer.](../media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
På fanen **Netværk skal** du trykke på den grønne afspilningsknap for at indlæse en side. Værktøjet returnerer alle de filer, browseren anmoder om for at hente den side, du har bedt om. Følgende skærmbillede viser en sådan liste.
  
![Skærmbillede af listen over filer, der returneres med en sideanmodning.](../media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
Du kan også se downloadtider for filerne i højre side, som vist på dette skærmbillede.
  
![Diagram, der viser den tid, det tager at indlæse de anmodede sider SharePoint.](../media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
Her får du en visuel repræsentation af, hvor lang tid filen var om at blive indlæst. Den grønne linje angiver, hvornår siden er klar til at blive gengivet af browseren. Dette kan give dig en hurtig oversigt over de forskellige filer, der kan forårsage langsomme side indlæses på dit websted.
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>Konfiguration af en ikke-tilpasset grundlinje for SharePoint Online
<a name="F12ToolInfo"> </a>

Den bedste måde at fastslå de svage punkter i dit websteds ydeevne på er ved at konfigurere en helt out of the box-gruppe af websteder i SharePoint Online. På den måde kan du sammenligne alle de forskellige aspekter af dit websted med det, du ville få uden nogen tilpasning på siden. Startsiden OneDrive for Business et godt eksempel på en separat gruppe af websteder, der sandsynligvis ikke har nogle tilpasninger.
  
## <a name="viewing-sharepoint-response-header-information"></a>Vise SharePoint svarheaderoplysninger
<a name="F12ToolInfo"> </a>

I SharePoint Online kan du få adgang til de oplysninger, der sendes tilbage til browseren i svarheaderen for hver fil. Den mest nyttige værdi til diagnosticering af problemer med ydeevnen er **SPRequestDuration**, som viser, hvor lang tid det tog for anmodningen at blive behandlet på serveren. Dette kan hjælpe med at afgøre, om anmodningen er meget tung og ressourcekrævende. Dette giver det bedste indblik i, hvor meget serveren skal arbejde for at betjene siden.

### <a name="to-view-sharepoint-response-header-information"></a>Sådan får SharePoint vist svarheaderoplysninger
  
1. Sørg for, at du har F12-værktøjerne installeret. Du kan finde flere oplysninger om at downloade og installere disse [værktøjer under Nyheder i F12-værktøjer](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182632(v=vs.85)).

2. I F12-værktøjerne på **fanen Netværk skal** du trykke på den grønne afspilningsknap for at indlæse en side.

3. Klik på en af de .aspx-filer, der returneres af værktøjet, og klik derefter på **DETALJER**.

    ![Viser detaljer om svarheaderen.](../media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. Klik **på Svaroverskrifter**.

    ![Diagram, der viser URL-adressen til svarheaderen.](../media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>Hvad forårsager problemer med ydeevnen i SharePoint Online?
<a name="F12ToolInfo"> </a>

Artiklen Navigationsindstillinger [for SharePoint Online](navigation-options-for-sharepoint-online.md) viser et eksempel på brug af SPRequestDuration-værdien til at fastslå, at den komplicerede strukturelle navigation har forårsaget, at det tager lang tid at behandle siden på serveren. Ved at tage en værdi for et grundlinjewebsted (uden tilpasning) er det muligt at afgøre, om en given fil tager lang tid at indlæse. Det eksempel, der bruges [i Navigationsindstillinger for SharePoint Online](navigation-options-for-sharepoint-online.md), er den primære .aspx-fil. Filen indeholder det meste af den ASP.NET, der kører under indlæsningen af siden. Afhængigt af den webstedsskabelon, du bruger, kan dette være start.aspx, home.aspx, default.aspx eller et andet navn, hvis du tilpasser startsiden. Hvis dette tal er væsentligt højere end dit grundlinjewebsted, er det et godt tegn på, at der foregår noget komplekst på din side, der forårsager problemer med ydeevnen.
  
Når du har identificeret et problem, der er specifikt for dit websted, kan du med den anbefalede metode finde ud af, hvad der forårsager den forårne ydeevne, ved at udelukke alle de mulige årsager, f.eks. sidetilpasninger, og derefter føje dem til webstedet igen én efter én. Når du har fjernet tilstrækkeligt mange tilpasninger, som siden udfører uden problemer, kan du tilføje dem igen til specifikke tilpasninger én efter én.
  
Hvis du f.eks. har en meget kompleks navigation, kan du prøve at ændre navigationen til ikke at vise underordnede websteder, og derefter kontrollere udviklerværktøjerne for at se, om det gør en forskel. Eller hvis du har en stor mængde indholdspakke, kan du prøve at fjerne dem fra din side og se, om det forbedrer tingene. Hvis du eliminerer alle de mulige årsager og tilføjer dem igen én ad gangen, kan du nemt identificere, hvilke funktioner der er det største problem, og derefter arbejde dig hen mod en løsning.
