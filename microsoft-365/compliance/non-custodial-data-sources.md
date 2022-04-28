---
title: Føj datakilder uden frihedsberøvelse til en eDiscovery-sag (Premium)
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
description: Du kan føje datakilder uden frihedsberøvelse til en eDiscovery-sag (Premium) og placere en venteposition på datakilden. Datakilder, der ikke er frihedsberøvende, genbehandles, så alt indhold, der er markeret som delvist indekseret, behandles igen for at gøre det fuldt ud og hurtigt søgbart.
ms.openlocfilehash: 86011a0f19dcb8f46041f4c0aa7c91d89e4e2198
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097970"
---
# <a name="add-non-custodial-data-sources-to-an-ediscovery-premium-case"></a>Føj datakilder uden frihedsberøvelse til en eDiscovery-sag (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

I Premium-sager (Microsoft Purview eDiscovery) opfylder det ikke altid dine behov at knytte en Microsoft 365 datakilde til en tilsynsførende i tilfælde af dette. Men du skal muligvis stadig knytte disse data til en sag, så du kan søge i dem, føje dem til et korrektursæt og analysere og gennemse dem. Funktionen i eDiscovery (Premium) kaldes *ikke-frihedsberøvende datakilder* og giver dig mulighed for at føje data til en sag uden at skulle knytte dem til en tilsynsførende. Den anvender også den samme eDiscovery-funktionalitet (Premium) på ikke-frihedsberøvende data, der er tilgængelige for data, der er knyttet til tilsynsførende. To af de mest nyttige ting, du kan anvende på ikke-frihedsberøvende data, er at sætte dem i venteposition og behandle dem ved hjælp af [avanceret indeksering](indexing-custodian-data.md).

## <a name="add-a-non-custodial-data-source"></a>Tilføj en datakilde, der ikke er frihedsberøvende

Følg disse trin for at tilføje og administrere datakilder, der ikke er frihedsberøvende, i en eDiscovery-sag (Premium).

1. Klik på den sag, du vil føje dataene til, på startsiden **for eDiscovery (Premium**).

2. Klik på fanen **Datakilder,** og klik derefter på **Tilføj datakildeTilføj** >  **dataplaceringer**.

3. På pop **op-siden Nye ikke-frihedsberøvende dataplaceringer** skal du vælge de datakilder, du vil føje til sagen. Du kan tilføje flere postkasser og websteder ved at udvide sektionerne **SharePoint** eller **Exchange** og derefter klikke på **Rediger**.

   ![Tilføj SharePoint websteder og Exchange postkasser som datakilder uden frihedsberøvelse.](../media/NonCustodialDataSources1.png)

   - **SharePoint** – Klik på **Rediger** for at tilføje websteder. Vælg et websted på listen, eller du kan søge efter et websted ved at skrive URL-adressen til webstedet i søgelinjen. Vælg de websteder, du vil tilføje som datakilder uden tilsynsførende, og klik på **Tilføj**.

   - **Exchange** – Klik på **Rediger** for at tilføje postkasser. Skriv et navn eller et alias (mindst tre tegn) i søgefeltet for postkasser eller distributionsgrupper. Vælg de postkasser, du vil tilføje som datakilder uden frihedsberøvelse, og klik på **Tilføj**.

   > [!NOTE]
   > Du kan bruge afsnittene **SharePoint** og **Exchange** til at tilføje websteder og postkasser, der er knyttet til et team eller Yammer gruppe, som datakilder uden frihedsberøvelse. Du skal tilføje den postkasse og det websted, der er knyttet til en gruppe eller Yammer gruppe.<br/><br/> Tilføjelse af en URL-adresse til rodwebstedet (f.eks. `https://contoso-my.sharepoint.com/personal/` eller `https://contoso-my.sharepoint.com/`) som en SharePoint datakilde understøttes heller ikke. Du skal tilføje bestemte websteder.

4. Når du har tilføjet datakilder, der ikke er frihedsberøvende, har du mulighed for at placere disse placeringer i venteposition eller ej. Markér eller fjern markeringen i afkrydsningsfeltet **Venteposition** ud for datakilden for at placere den i venteposition.

5. Klik på **Tilføj** nederst på siden **Nye ikke-frihedsberøvende dataplaceringer** for at føje datakilderne til sagen.

   Hver datakilde, du ikke har tilføjet, vises på siden **Datakilder** . Datakilder, der ikke er frihedsberøvende, identificeres af værdien **For dataplacering** i kolonnen **Kildetype** .

   ![Datakilder uden frihedsberøvelse på fanen Datakilder.](../media/NonCustodialDataSources2.png)

Når du føjer datakilder, der ikke er frihedsberøvende, til sagen, oprettes der et job med navnet *Omdexering af ikke-frihedsberøvende data* , som vises under fanen **Job** i sagen. Når jobbet er oprettet, startes den avancerede indekseringsproces i , og datakilderne indekseres igen.

## <a name="manage-the-hold-for-non-custodial-data-sources"></a>Administrer ventepositionen for datakilder uden frihedsberøvelse

Når du har sat en venteposition på en datakilde, der ikke er frihedsberøvende, oprettes der automatisk en politik for bevarelse, der indeholder de datakilder, der ikke er frihedsberøvende for sagen. Når du placerer andre datakilder, der ikke er frihedsberøvende, i venteposition, føjes de til denne politik for bevarelse.

1. Åbn sagen eDiscovery (Premium), og vælg fanen **Venteposition**.

2. Klik på **NCDSHold-, hvor GUID-værdien\<GUID\>** er entydig for sagen.

   På pop op-siden vises oplysninger og statistikker om de datakilder, der ikke er i venteposition.

   ![På pop op-siden for datakilder, der ikke er frihedsberøvende, vises statistik.](../media/NonCustodialDataSourcesHoldFlyout.png)

3. Klik på **Rediger venteposition** for at få vist de datakilder, der ikke er frihedsberøvende, og udføre følgende administrationsopgaver:

   - På siden **Placeringer** kan du frigive en datakilde, der ikke er varetægtsfængslet, ved at fjerne den fra ventepositionen. Når du frigiver en datakilde, fjernes den datakilde, der ikke er varetægtsfængslet, ikke fra sagen. Den fjerner kun den venteposition, der er placeret på datakilden.

   - På siden **Forespørgsel** kan du redigere ventepositionen for at oprette en forespørgselsbaseret venteposition, der anvendes på alle de datakilder, der ikke er frihedsberøvende.
