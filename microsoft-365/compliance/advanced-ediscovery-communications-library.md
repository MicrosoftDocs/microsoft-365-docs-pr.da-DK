---
title: Administrer skabeloner til tilsynsførende kommunikation i kommunikationsbiblioteket i eDiscovery (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Du kan tilføje skabeloner til tilsynsførende kommunikation (f.eks. en skabelon til meddelelse om venteposition) i eDiscovery (Premium), så de kan bruges i alle tilfælde i din organisation.
ms.openlocfilehash: faf4ea91ae6f160b2ba7388a7cfea8ad6cb9797b
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097266"
---
# <a name="manage-custodian-communications-templates-in-ediscovery-premium"></a>Administrer skabeloner til tilsynsførende kommunikation i eDiscovery (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du eller andre brugere opretter en meddelelse om bevarelse af venteposition eller andre typer af tilsynsførende kommunikation, skulle du oprette kommunikationsdokumentet fra bunden ved hjælp af kommunikationseditoren under fanen **Kommunikation** i en eDiscovery-sag (Premium). Nu har vi udgivet en ny funktion, hvor du kan oprette kommunikationsskabeloner, der under alle omstændigheder kan bruges til at oprette kommunikation i din organisation. Når der er oprettet kommunikationsskabeloner, kan de bruges i en sag. Det betyder, at paralegals eller andre brugere, der opretter tilsynsførende kommunikation, ikke behøver at starte fra bunden for at oprette en meddelelse. De kan i stedet vælge en skabelon for at oprette den meddelelse, der sendes til en tilsynsførende.

I denne artikel forklares det, hvordan du opretter kommunikationsskabeloner for hele organisationen og vælger dem, når du opretter en ny meddelelse om forældremyndigheden over en bestemt eDiscovery-sag (Premium).

## <a name="before-you-create-templates-in-the-communications-library"></a>Før du opretter skabeloner i kommunikationsbiblioteket

- Du skal være eDiscovery-administrator i din organisation for at tilføje eller fjerne skabeloner i kommunikationsbiblioteket i eDiscovery (Premium). Du kan finde flere oplysninger under [Tildel eDiscovery-tilladelser på Microsoft Purview-overholdelsesportalen](assign-ediscovery-permissions.md)  

- Din organisation kan maksimalt have 50 skabeloner i kommunikationsbiblioteket.

## <a name="create-a-communications-template"></a>Opret en kommunikationsskabelon

1. Gå til [eDiscovery (Premium)](https://go.microsoft.com/fwlink/p/?linkid=2173764) i portalen til overholdelse af angivne standarder, og klik derefter på **indstillinger for eDiscovery (Premium).**

   ![Vælg indstillinger for eDiscovery (Premium)](..\media\HistoricalVersions1.png)

2. Vælg fanen **Kommunikationsbibliotek** på siden **Indstillinger**.

3. Klik på **Opret** på siden **Kommunikationsbibliotek**.

4. Følg proceduren for at oprette en tilsynsførende kommunikation. Du kan finde en trinvis vejledning under [Opret en meddelelse om juridisk venteposition](create-hold-notification.md).

   > [!NOTE]
   > Trinnene til at oprette en kommunikationsskabelon er de samme som arbejdsprocessen til oprettelse af en meddelelse i en sag. Den eneste forskel er, at når du opretter en skabelon, angiver du ikke en udstedende officer, og du tildeler ikke tilsynsførende. Angivelse af en udstedende officer og tildeling af varetægtsfængslede sker, når du bruger en kommunikationsskabelon til at oprette en tilsynsførende meddelelse for en sag.

5. Når du har oprettet en skabelon, vises den på siden **Kommunikationsbibliotek** .

   ![Skabeloner, der vises i kommunikationsbiblioteket](..\media\AeDCommunicationsLibrary1.png)

Du eller andre eDiscovery-administratorer kan redigere en kommunikationsskabelon. De ændringer, du foretager i en skabelon, påvirker eller ændrer ikke meddelelser, der tidligere er oprettet ved hjælp af skabelonen. Disse ændringer gælder kun for nye meddelelser, der er oprettet ved hjælp af den opdaterede skabelon.

## <a name="use-a-communications-template-to-create-a-custodian-notification"></a>Brug en kommunikationsskabelon til at oprette en meddelelse fra en tilsynsførende

Når en eller flere kommunikationsskabeloner er oprettet i kommunikationsbiblioteket, kan disse skabeloner vælges for at oprette en underretning af en tilsynsførende i en sag.

Sådan vælger du en skabelon:

1. På overholdelsesportalen skal du gå til **eDiscovery > Avanceret** for at få vist listen over sager i din organisation.

2. Vælg en sag, klik på fanen **Kommunikation** , og klik derefter på **Ny kommunikation**.

3. På **siden Navngiv kommunikation** skal du bruge rullelisten **Vælg kommunikationsskabelon** til at vælge en kommunikationsskabelon, der skal bruges til at oprette meddelelsen om varetægtsfængslet.

   Listen over skabeloner i organisationens kommunikationsbibliotek vises på rullelisten.

   ![Skabeloner fra kommunikationsbiblioteket, der vises på rullelisten.](..\media\AeDCommunicationsTemplates1.png)
