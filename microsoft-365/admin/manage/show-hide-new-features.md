---
title: Administrer, Office funktioner vises i Nyheder
f1.keywords:
- NOCSH
ms.author: danbrown
author: DHB-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
description: Beslut, hvilke Office-funktioner der skal vises eller skjules, når en bruger vælger Hjælp > Nyheder i deres Office-app på Windows ved hjælp af funktionen "Nyheder i Office" i Microsoft 365 Administration.
ms.openlocfilehash: 53372a4075de6d6a4790d49dc23e79e0ca60d65d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590237"
---
# <a name="manage-which-office-features-appear-in-whats-new"></a>Administrer, Office funktioner vises i Nyheder

Når en vigtig Office-funktion frigives, får brugerne en meddelelse om det,  \> når de vælger Hjælp Nyheder i deres Office-app på Windows.

Du kan styre, hvilke af disse funktionsmeddelelser brugerne får vist, ved hjælp af funktionen **Nyheder i Office** i Microsoft 365 Administration. Hvis du beslutter dig for at skjule en funktionsmeddelelse for dine brugere, kan du altid vende tilbage senere og beslutte at vise den til dem.

> [!NOTE]
>
> - Når du skjuler en funktionsmeddelelse for dine brugere, deaktiveres funktionen ikke i Office-app.
> - Du skal være tildelt enten den globale administratorrolle eller Office-appadministratorrollen for at bruge funktionen **Nyheder Office** brugerfunktionen.

## <a name="show-or-hide-new-features"></a>Vis eller skjul nye funktioner

1. I Microsoft 365 Administration under **Indstillinger** skal du vælge **Org-indstillinger**, vælge fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Tjenester**</a> og derefter vælge Nyheder **i Office**.
1. Når du klikker på funktionsnavnet, vises et pop op-panel med følgende oplysninger:
     - En kort beskrivelse af funktionen.
     - Et link til en artikel for at få mere at vide om funktionen.
     - De Office programmer, som funktionen vises i.
     - Den første version (version), som funktionen er tilgængelig i for den pågældende kanal.
1. Vælg **Skjul for brugere**. Eller, hvis du tidligere har skjult funktionen, skal du vælge **Vis til brugere**.

Du kan også vælge flere funktioner på siden Administrer **, Office funktioner** vises på siden Nyheder, og derefter vælge enten **Skjul** eller **Vis**.

> [!NOTE]
>
> - Hvis en funktion er tilgængelig i flere Office-apps, og du angiver funktionen til Skjult, skjules funktionsmeddelelsen i alle disse Office apps.
> - Alle funktionsmeddelelser vises til brugerne som standard. Dette er standardstatus for alle funktioner, og status ændres kun, hvis du har valgt at skjule eller vise en funktionsmeddelelse.
> - Du kan også finde **funktionen Nyheder i Office** fra Microsoft 365 Apps Administration (<https://config.office.com>). Funktionen findes under **TilpasningHvad** >  **er den nye administration**.

## <a name="list-of-features"></a>Liste over funktioner

Du kan filtrere, hvilke funktioner der vises **på siden Administrer, Office funktioner vises på siden** Nyheder. Du kan filtrere efter kanal, program eller status eller efter en kombination af dem.

Nye funktioner vises på siden baseret på følgende tidsplan:

<br>

****

|Kanal|Dato|Gør noget|
|---|---|---|
|**Aktuel**|15. i måneden|1- 3 uger før den månedlige udgivelse|
|**Månedlig virksomhed**|Den første i måneden|To uger før den store udgivelse, der bringer nye funktioner|
|**Halvårlige Enterprise (forhåndsvisning)**|1. september og 1. marts| 2 uger før den store udgivelse, der giver nye funktioner|
|**Halvårlige Enterprise**|1. januar og 1. juli| 2 uger før den store udgivelse, der giver nye funktioner|
|

Du kan finde flere oplysninger om, hvornår der frigives nye versioner til hver opdateringskanal, under [Opdateringsoversigt for Microsoft 365 Apps (angivet efter dato)](/officeupdates/update-history-microsoft365-apps-by-date).

## <a name="add-the-whats-new-in-office-card-to-the-admin-center-home-page"></a>Føj kortet "Nyheder i Office" til startsiden i Administration

1. På Microsoft 365 Administration skal du **vælge Tilføj** kort øverst på siden
2. Find **Administrer, Office funktioner vises under Nyheder på** listen, og vælg den.
3. Når kortet er på din startside, kan du vælge Nyheder i  Office for at vise eller skjule [funktionerne](#show-or-hide-new-features) for organisationen.

## <a name="related-articles"></a>Relaterede artikler

[Office Administration af nyheder er nu generelt tilgængelig](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-what-s-new-management-is-now-generally-available/ba-p/1179954)
