---
title: Administrer snægtsiske kommunikationsskabeloner i kommunikationsbiblioteket i Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Du kan tilføje kommunikationsskabeloner, der skal anvendes, f.eks. en skabelon til meddelelse om venteposition Advanced eDiscovery så de kan bruges i alle tilfælde i din organisation.
ms.openlocfilehash: 1b5be4a4a923050b43943e81ac64265e16749899
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704855"
---
# <a name="manage-custodian-communications-templates-in-advanced-ediscovery"></a>Administrer håndterede kommunikationsskabeloner i Advanced eDiscovery

Når du eller andre brugere opretter en meddelelse om venteposition eller andre typer af kommunikation, der skal anvendes, skulle du oprette kommunikationsdokumentet fra bunden ved hjælp af kommunikationseditoren på fanen Kommunikation i en Advanced eDiscovery sag. Nu har vi udgivet en ny funktion, der gør det muligt at oprette kommunikationsskabeloner, der kan bruges til at oprette kommunikation i alle tilfælde i din organisation. Når kommunikationsskabeloner er oprettet, er de tilgængelige til brug i en sag. Det betyder, at advokatsekretærer eller andre brugere, der opretter kommunikationsmedarbejdere, ikke behøver at starte fra bunden for at opbygge en meddelelse. De kan i stedet vælge en skabelon for at opbygge den meddelelse, der sendes til en vagtleder.

I denne artikel forklares det, hvordan du kan oprette kommunikationsskabeloner for hele organisationen og vælge dem, når du opretter en ny meddelelse om, at der er tale om en Advanced eDiscovery sag.

## <a name="before-you-create-templates-in-the-communications-library"></a>Før du opretter skabeloner i kommunikationsbiblioteket

- Du skal være eDiscovery-administrator i din organisation for at tilføje eller fjerne skabeloner i kommunikationsbiblioteket i Advanced eDiscovery. Få mere at vide under [Tildel eDiscovery-tilladelser i Microsoft 365 Overholdelsescenter](assign-ediscovery-permissions.md)  

- Din organisation kan maksimalt have 50 skabeloner i kommunikationsbiblioteket.

## <a name="create-a-communications-template"></a>Opret en kommunikationsskabelon

1. I Microsoft 365 Overholdelsescenter skal du gå til [Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?linkid=2173764) og derefter klikke på **Advanced eDiscovery indstillinger**.

   ![Vælg Advanced eDiscovery indstillinger](..\media\HistoricalVersions1.png)

2. På siden **Indstillinger** skal du vælge **fanen Kommunikationsbibliotek**.

3. Klik på **Opret på** siden **kommunikationsbibliotek**.

4. Følg fremgangsmåden for at oprette en kommunikation, der skal følges. Du kan finde en trinvis vejledning under Oprette en meddelelse om [retslig venteposition](create-hold-notification.md).

   > [!NOTE]
   > Trinnene til at oprette en kommunikationsskabelon er de samme som arbejdsprocessen til at oprette en meddelelse i en sag. Den eneste forskel er, at når du opretter en skabelon, angiver du ikke en udstederofficer, og du tildeler ikke ydsofficer. Når du angiver en udstederofficer og tildeler assistenter, udføres det, når du bruger en kommunikationsskabelon til at oprette en meddelelse om, at den eriansk, til en sag.

5. Når du har oprettet en skabelon, vises den på siden **i biblioteket** Kommunikation.

   ![Skabeloner vist i kommunikationsbiblioteket](..\media\AeDCommunicationsLibrary1.png)

Du eller andre eDiscovery-administratorer kan redigere en kommunikationsskabelon. De ændringer, du foretager i en skabelon, påvirker eller ændrer ikke eventuelle meddelelser, der tidligere er oprettet ved hjælp af den pågældende skabelon. Disse ændringer gælder kun for nye meddelelser, der er oprettet ved hjælp af den opdaterede skabelon.

## <a name="use-a-communications-template-to-create-a-custodian-notification"></a>Brug en kommunikationsskabelon til at oprette en meddelelse om beskyttelse af forældre

Når der er oprettet en eller flere kommunikationsskabeloner i kommunikationsbiblioteket, kan disse skabeloner vælges for at oprette en meddelelse om, at der er tale om eniansk meddelelse, i en sag.

Sådan vælger du en skabelon:

1. I Microsoft 365 Overholdelsescenter skal du gå **til eDiscovery > Avanceret** for at få vist listen over sager i din organisation.

2. Vælg en sag, klik på **fanen Kommunikation** , og klik derefter på **Ny kommunikation**.

3. På siden **Name communication** skal du bruge **rullelisten Vælg** kommunikationsskabelon til at vælge en kommunikationsskabelon, der skal bruges til at oprette meddelelsen om kontaktpersoner.

   Listen over skabeloner i organisationens Kommunikationsbibliotek vises på rullelisten.

   ![Skabeloner fra kommunikationsbiblioteket vises på rullelisten.](..\media\AeDCommunicationsTemplates1.png)
