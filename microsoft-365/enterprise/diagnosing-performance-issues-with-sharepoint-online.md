---
title: Diagnosticering af problemer med ydeevnen med SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: I denne artikel kan du se, hvordan du kan diagnosticere almindelige problemer med dit SharePoint Online-websted ved hjælp af Udviklerværktøjer i Internet Explorer.
ms.openlocfilehash: 041619991fdbdcb3e953fe2a06fd63dff0e9201f
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753798"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>Diagnosticering af problemer med ydeevnen med SharePoint Online

I denne artikel kan du se, hvordan du kan diagnosticere almindelige problemer med dit SharePoint Online-websted ved hjælp af Udviklerværktøjer i Internet Explorer.
  
Der er fire forskellige måder, du kan identificere, at en side på et SharePoint Online-websted har problemer med ydeevnen med tilpasningerne.

- Diagnosticering af websteds- og sideydeevne
  
- Netværksovervågning for F12-værktøjslinjen

- Sammenligning med en ikke-tilpasset oprindelig plan

- SharePoint målepunkter for onlinesvarheader

I dette emne beskrives det, hvordan du bruger hver af disse metoder til at diagnosticere problemer med ydeevnen. Når du har fundet årsagen til problemet, kan du arbejde mod en løsning ved hjælp af artiklerne om forbedring af SharePoint ydeevne, som du kan finde på https://aka.ms/tune.  

## <a name="use-the-site-and-page-performance-diagnostic-from-the-microsoft-365-admin-center"></a>Brug diagnosticering af websteds- og sideydeevne fra Microsoft 365 Administration Center

> [!NOTE]
> Hvis du er administrator, og du har problemer med ydeevnen i SharePoint, skal du vælge **Kør test** nedenfor, hvor diagnosticering af websted og sideydeevne udfyldes i Microsoft 365 Administration Center. Disse test kontrollerer din konfiguration og anbefaler hurtigt næste trin for at forbedre SharePoint ydeevne for din lejer.
>> [!div class="nextstepaction"]
>> [Kør test: Kontrollér ydeevnen SharePoint](https://aka.ms/PillarSiteandPagePerf)

> [!NOTE] 
> Denne funktion er ikke tilgængelig for Microsoft 365 offentlige myndigheder, Microsoft 365 drevet af 21Vianet eller Microsoft 365 Tyskland.
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>Brug af værktøjslinjen F12 til at diagnosticere ydeevnen i SharePoint Online
<a name="F12ToolInfo"> </a>

I denne artikel bruger vi Internet Explorer 11. Versioner af F12-udviklerværktøjer i andre browsere har lignende funktioner, selvom de kan se lidt anderledes ud. Du kan få oplysninger om F12-udviklerværktøjerne under:
  
- [Nyheder i F12-værktøjer](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182632(v=vs.85))

- [Brug af F12-udviklerværktøjer](/previous-versions/windows/internet-explorer/ie-developer/samples/bg182326(v=vs.85))

Tryk på **F12** for at få vist udviklerværktøjerne, og klik derefter på ikonet Wi-Fi:
  
![Skærmbillede af F12 udviklerværktøjer wi-fi-ikon.](../media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
Tryk på den grønne afspilningsknap under fanen **Netværk** for at indlæse en side. Værktøjet returnerer alle de filer, som browseren anmoder om, for at få den side, du bad om. På følgende skærmbillede kan du se en sådan liste.
  
![Skærmbillede af listen over filer, der er returneret med en sideanmodning.](../media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
Du kan også se downloadtiderne for filerne i højre side som vist på dette skærmbillede.
  
![Diagram, der viser den tid, det tager at indlæse de ønskede sider fra SharePoint.](../media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
Det giver dig en visuel gengivelse af, hvor lang tid det tog at indlæse filen. Den grønne linje angiver, hvornår siden er klar til at blive gengivet i browseren. Dette kan give dig et hurtigt overblik over de forskellige filer, der kan medføre langsomme sidebelastninger på dit websted.
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>Konfiguration af en ikke-tilpasset oprindelig plan til SharePoint Online
<a name="F12ToolInfo"> </a>

Den bedste måde at bestemme dit websteds ydeevne på er ved at konfigurere en helt klar gruppe af websteder i SharePoint Online. På denne måde kan du sammenligne alle de forskellige aspekter af dit websted med det, du ville få uden tilpasning på siden. Den OneDrive for Business startside er et godt eksempel på en separat gruppe af websteder, hvor det er usandsynligt, at der foretages tilpasninger.
  
## <a name="viewing-sharepoint-response-header-information"></a>Visning SharePoint oplysninger i svarheaderen
<a name="F12ToolInfo"> </a>

I SharePoint Online kan du få adgang til de oplysninger, der sendes tilbage til browseren i svarheaderen for hver fil. Den mest nyttige værdi til diagnosticering af problemer med ydeevnen er **SPRequestDuration**, som viser den mængde tid, som anmodningen tog på den server, der skulle behandles. Dette kan hjælpe med at afgøre, om anmodningen er tung og ressourcekrævende. Dette er den bedste indsigt, du har i, hvor meget arbejde serveren gør for at tjene siden.

### <a name="to-view-sharepoint-response-header-information"></a>Sådan får du vist SharePoint oplysninger i svarheaderen
  
1. Sørg for, at F12-værktøjerne er installeret. Du kan finde flere oplysninger om, hvordan du downloader og installerer disse værktøjer, [under Nyheder i F12-værktøjer](/previous-versions/windows/internet-explorer/ie-developer/dev-guides/bg182632(v=vs.85)).

2. Tryk på den grønne afspilningsknap under fanen **Netværk** i F12-værktøjerne for at indlæse en side.

3. Klik på en af de .aspx-filer, der returneres af værktøjet, og klik derefter på **DETALJER**.

    ![Viser detaljer om svarheaderen.](../media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. Klik på **Svarheadere**.

    ![Diagram, der viser URL-adressen til svarheaderen.](../media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>Hvad forårsager problemer med ydeevnen i SharePoint Online?
<a name="F12ToolInfo"> </a>

I artiklen [Navigationsindstillinger for SharePoint Online](navigation-options-for-sharepoint-online.md) vises et eksempel på brug af værdien SPRequestDuration til at fastslå, at den komplicerede strukturelle navigation medførte, at siden tog lang tid at behandle på serveren. Ved at tage en værdi for et grundlæggende websted (uden tilpasning) er det muligt at afgøre, om en given fil tager lang tid at indlæse. Det eksempel, der bruges i [navigationsindstillinger for SharePoint Online](navigation-options-for-sharepoint-online.md), er den primære .aspx-fil. Filen indeholder de fleste af de ASP.NET kode, der kører for sideindlæsningen. Afhængigt af den webstedsskabelon, du bruger, kan det være start.aspx, home.aspx, default.aspx eller et andet navn, hvis du tilpasser startsiden. Hvis dette tal er betydeligt højere end dit oprindelige websted, er det en god indikation af, at der er noget komplekst på din side, der forårsager problemer med ydeevnen.
  
Når du har identificeret et problem, der er specifikt for dit websted, anbefales det, at du finder ud af, hvad der forårsager dårlig ydeevne, ved at fjerne alle mulige årsager, f.eks. sidetilpasninger, og derefter føje dem tilbage til webstedet én efter én. Når du har fjernet nok tilpasninger, som siden klarer sig godt, kan du tilføje specifikke tilpasninger én efter én igen.
  
Hvis du f.eks. har en kompleks navigation, kan du prøve at ændre navigationen, så den ikke viser underordnede websteder, og derefter kontrollere udviklerværktøjerne for at se, om det gør en forskel. Eller hvis du har en stor mængde indholdsopløftninger, kan du prøve at fjerne dem fra din side og se, om det forbedrer noget. Hvis du fjerner alle de mulige årsager og tilføjer dem i ét ad gangen, kan du nemt identificere, hvilke funktioner der er det største problem, og derefter arbejde hen imod en løsning.
