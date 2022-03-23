---
title: Brug delte forespørgsler i Microsoft 365 Defender avanceret jagt
description: Start straks trusselssøgning med foruddefinerede og delte forespørgsler. Del dine forespørgsler til offentligheden eller til din organisation.
keywords: avanceret jagt, trusselssvining, cybertrusler, Microsoft 365 Defender, microsoft 365, m365, søgning, forespørgsel, telemetri, brugerdefinerede registreringer, skema, kusto, github repo, mine forespørgsler, delte forespørgsler
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 06952be112f4eb28867a4a0cd4bffbee0c664b5c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63592604"
---
# <a name="use-shared-queries-in-advanced-hunting"></a>Brug delte forespørgsler i avanceret jagt

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender
- Microsoft Defender til Slutpunkt



[Avancerede](advanced-hunting-overview.md) forespørgselsforespørgsler kan deles mellem brugere i samme organisation. Du kan også finde forespørgsler, der deles offentligt på GitHub. Disse forespørgsler gør det muligt for dig hurtigt at følge bestemte scenarier med trusselssøgning uden at skulle skrive forespørgsler fra bunden.

![Billede af delte forespørgsler.](../../media/shared-query-1.png)

## <a name="save-modify-and-share-a-query"></a>Gem, rediger og del en forespørgsel
Du kan gemme en ny eller eksisterende forespørgsel, så den kun er tilgængelig for dig eller delt med andre brugere i organisationen. 

1. Oprette eller redigere en forespørgsel. 

2. Klik på **rullemenuen** Gem forespørgsel, og vælg **Gem som**.
    
3. Angiv et navn til forespørgslen. 

   ![Billede af at gemme en forespørgsel.](../../media/shared-query-2.png)

4. Vælg den mappe, hvor du vil gemme forespørgslen.
    - **Delte forespørgsler –** delt med alle brugere i organisationen
    - **Mine forespørgsler – kun** tilgængelige for dig
    
5. Vælg **Gem**. 

## <a name="delete-or-rename-a-query"></a>Slette eller omdøbe en forespørgsel
1. Markér de tre prik til højre for en forespørgsel, du vil omdøbe eller slette.

    ![Billede af sletteforespørgsel.](../../media/shared-query-3.png)

2. Vælg **Slet,** og bekræft sletningen. Eller vælg **Omdøb** , og angiv et nyt navn til forespørgslen.

## <a name="create-a-direct-link-to-a-query"></a>Oprette et direkte link til en forespørgsel
For at oprette et link, der åbner din forespørgsel direkte i avanceret forespørgselseditor, skal du færdiggøre din forespørgsel og vælge **Del link**.

## <a name="access-queries-in-the-github-repository"></a>Access-forespørgsler i GitHub lager  
Microsoft-sikkerhedseksperter deler jævnligt avancerede forespørgselsforespørgsler [i et udpeget offentligt lager på GitHub](https://aka.ms/hunting-queries). Dette lager er åbent for bidrag. For at bidrage skal [du GitHub gratis](https://github.com/).

>[!tip]
>Microsofts sikkerhedseksperter tilbyder også avancerede forespørgselsforespørgsler, som du kan bruge til at finde aktiviteter og indikatorer, der er knyttet til kommende trusler. Disse forespørgsler leveres som en del af rapporterne [om trusselsanalyse](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) i Microsoft 365 Defender.


## <a name="related-topics"></a>Relaterede emner
- [Avanceret jagtoversigt](advanced-hunting-overview.md)
- [Lær forespørgselssproget](advanced-hunting-query-language.md)
- [Arbejd med forespørgselsresultater](advanced-hunting-query-results.md)
- [Lede på tværs af enheder, mails, apps og identiteter](advanced-hunting-query-emails-devices.md)
- [Forstå skemaet](advanced-hunting-schema-tables.md)
- [Anvend bedste fremgangsmåder for forespørgsler](advanced-hunting-best-practices.md)