---
title: Opret en model på et lokalt SharePoint websted med Microsoft SharePoint Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Få mere at vide om, hvordan du opretter en lokal model på et lokalt SharePoint websted med SharePoint Syntex.
ms.openlocfilehash: bcd3f1f086af3982cb4a3ecc5fe754cf82f09a70
ms.sourcegitcommit: e624221597480295b799d56568c4f6f56d40b41d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/19/2022
ms.locfileid: "65535376"
---
# <a name="create-a-model-on-a-local-sharepoint-site-with-microsoft-sharepoint-syntex"></a>Opret en model på et lokalt SharePoint websted med Microsoft SharePoint Syntex

SharePoint Syntex giver nu mulighed for at oprette og oplære modeller lokalt på dit eget SharePoint websted. Disse modeller kan kun bruges på det websted, hvor de er oprettet. 

Ved at aktivere dokumentklassificering og -udtrækning på dit SharePoint websted kan du SharePoint Syntex klassificere filer i dokumentbiblioteker, udtrække oplysninger fra nye filer og automatisere aktiviteter baseret på udtrukne oplysninger.

Når du aktiverer oprettelse af lokale modeller, føjes følgende lister og biblioteker til dit websted:

- Dokumentbibliotek for modeller
- Dokumentbibliotek til oplæring af filer
- Liste over forklaringsskabeloner
- Liste over modelanvendelser

Denne funktion er kun tilgængelig til oprettelse af [modeller til dokumentforståelse](apply-a-model.md) og [færdigbyggede modeller](prebuilt-models.md). 

## <a name="create-a-model-on-a-local-site"></a>Opret en model på et lokalt websted

1. Vælg de filer, du vil analysere, i et SharePoint dokumentbibliotek, og vælg derefter **Klassificer og udtræk**.

    ![Skærmbillede af et SharePoint dokumentbibliotek med indstillingen Klassificer og udtræk fremhævet.](../media/content-understanding/local-model-classify-and-extract-option.png) 

2. Første gang du bruger denne funktion, aktiverer du SharePoint Syntex på dit websted. Du får vist følgende meddelelse.

    ![Skærmbillede af siden Aktivér dokumentklassificering og udtræksoplysninger.](../media/content-understanding/local-model-first-run-activate-message.png) 

    > [!NOTE]
    > Du skal have tilladelsen Administrer websted for at kunne udføre administrationsopgaver og administrere indhold for webstedet. Dette er webstedets ejer. Når funktionen er aktiveret, kan alle med tilladelsen Administrer lister oprette og administrere modeller.

3. Vælg **Aktivér** for at fortsætte. Du får vist følgende meddelelse.

    ![Skærmbillede af den aktiverede meddelelse om dokumentklassificering og -udtrækning med mulighed for at oprette en model.](../media/content-understanding/local-model-activated-message.png) 

4. Vælg **Opret en model**.

5. Skriv navnet på modellen i panelet **Opret en model** , vælg modeltypen, og vælg derefter **Opret**.

    ![Skærmbillede af panelet Opret en model.](../media/content-understanding/local-model-create-a-model.png) 

6. Fortsæt med at [oplære din model til forståelse af dokumentet](apply-a-model.md) eller [konfigurere den færdigbyggede model](prebuilt-models.md) ved hjælp af de filer, du har valgt.

7. Når du er færdig, åbnes panelet **Føj til bibliotek** .

    ![Skærmbillede af panelet Føj til bibliotek, der viser det anvendte websted og de anvendte biblioteker.](../media/content-understanding/local-model-add-to-library-panel.png) 

8. På panelet **Føj til bibliotek** kan du se navnet på dit SharePoint websted og det dokumentbibliotek, som modellen anvendes på. Hvis du vil anvende modellen på et andet bibliotek, skal du vælge **Tilbage til biblioteker** og vælge det bibliotek, du vil bruge. Vælg derefter **Tilføj**.

9. På modellens startside kan du i afsnittet **Hvor modellen anvendes på dette websted** se de biblioteker, hvor modellen er anvendt. Hvis du vil anvende modellen på andre biblioteker på webstedet, skal du vælge **Anvend model**. 

    ![Skærmbillede af modellens startside, der viser sektionen Hvor modellen anvendes på webstedet.](../media/content-understanding/local-model-home-page.png) 

