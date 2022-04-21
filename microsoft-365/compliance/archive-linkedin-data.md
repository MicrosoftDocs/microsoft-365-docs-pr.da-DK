---
title: Konfigurer en connector til arkivering af LinkedIn-data
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/06/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Få mere at vide om, hvordan administratorer kan konfigurere & bruge en oprindelig connector til at importere data fra en LinkedIn-firmaside for at Microsoft 365.
ms.openlocfilehash: f4def1c8946c8b09f1ba543762026572ceb229b6
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64998038"
---
# <a name="set-up-a-connector-to-archive-linkedin-data"></a>Konfigurer en connector til arkivering af LinkedIn-data

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en connector i Microsoft Purview-overholdelsesportalen til at importere og arkivere data fra LinkedIn-virksomhedssider. Når du har konfigureret en connector, oprettes der forbindelse til kontoen for den specifikke LinkedIn-firmaside én gang hver 24. time. Connectoren konverterer de meddelelser, der er sendt til siden Firma, til en mail og importerer derefter disse elementer til en postkasse i Microsoft 365.

Når siden LinkedIn-firmadata er gemt i en postkasse, kan du anvende Microsoft Purview-funktioner som f.eks. litigation hold, Content Search, In-Place Archiving, Auditing og Microsoft 365 retention policies på LinkedIn-data. Du kan f.eks. søge efter disse elementer ved hjælp af indholdssøgning eller knytte lagerpostkassen til en tilsynsførende i en Microsoft Purview eDiscovery-sag (Premium). Oprettelse af en connector til import og arkivering af LinkedIn-data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en connector

- Den bruger, der opretter en LinkedIn-firmasideconnector, skal tildeles rollen Administrator af dataconnector. Denne rolle er påkrævet for at tilføje forbindelser på siden **Dataconnectors på overholdelsesportalen** . Denne rolle føjes som standard til flere rollegrupper. Du kan se en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescentre" i [Tilladelser i Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). En administrator i din organisation kan også oprette en brugerdefineret rollegruppe, tildele rollen Administrator af dataconnector og derefter tilføje de relevante brugere som medlemmer. Du kan finde instruktioner i afsnittet "Opret en brugerdefineret rollegruppe" i [Tilladelser på Microsoft Purview-overholdelsesportalen](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Du skal have logonlegitimationsoplysninger (mailadresse eller telefonnummer og adgangskode) for en LinkedIn-brugerkonto, der er administrator for den LinkedIn-firmaside, du vil arkivere. Du kan bruge disse legitimationsoplysninger til at logge på LinkedIn, når du konfigurerer connectoren.

- LinkedIn-connectoren kan importere i alt 200.000 elementer på en enkelt dag. Hvis der er mere end 200.000 LinkedIn-elementer på én dag, importeres ingen af disse elementer til Microsoft 365.

## <a name="create-a-linkedin-connector"></a>Opret en LinkedIn-connector

1. Gå til <https://compliance.microsoft.com> , og klik derefter på **DataconnectorsLinkedIn** >  **Company-sider**.

2. Klik på **Tilføj connector** på produktsiden **LinkedIn-virksomhedssider**.

3. På siden **Vilkår for tjeneste** skal du vælge **Acceptér**.

4. Klik på **Log på med LinkedIn** på siden Log på **med LinkedIn**.

   LinkedIn-logonsiden vises.

   ![LinkedIn-logonside.](../media/LinkedInSigninPage.png)

5. På siden LinkedIn-logon skal du angive mailadressen (eller telefonnummeret) og adgangskoden for den LinkedIn-konto, der er knyttet til den firmaside, du vil arkivere, og derefter klikke på **Log på**.

   Der vises en guideside med en liste over alle LinkedIn-firmasider, der er knyttet til den konto, du loggede på. En connector kan kun konfigureres for én virksomhedsside. Hvis din organisation har flere LinkedIn-firmasider, skal du oprette en connector for hver enkelt.

   ![Der vises en side med en liste over LinkedIn-firmasider.](../media/LinkedInSelectCompanyPage.png)

6. Vælg den firmaside, du vil arkivere elementer fra, og klik derefter på **Næste**.

7. På siden **Vælg lagerplacering** skal du klikke i feltet, vælge mailadressen på en Microsoft 365 postkasse, som LinkedIn-elementerne skal importeres til, og derefter klikke på **Næste**. Elementer importeres til mappen Indbakke i denne postkasse.

8. Klik på **Næste** for at gennemse connectorindstillingerne, og klik derefter på **Udfør** for at fuldføre connectorkonfigurationen.

Når du har oprettet connectoren, kan du gå tilbage til siden **Dataconnectors** for at se status for importprocessen for den nye connector (vælg **Opdater** , hvis det er nødvendigt for at opdatere listen over forbindelser). Værdien i kolonnen **Status** **venter på at starte**. Det tager op til 24 timer, før den indledende importproces startes. Når connectoren kører og importerer LinkedIn-elementerne første gang, køres connectoren én gang hver 24. time og importerer eventuelle nye elementer, der er oprettet på LinkedIn-firmasiden inden for de forrige 24 timer.

Hvis du vil have vist flere oplysninger, skal du vælge connectoren på listen på siden **Dataconnectors** for at få vist pop op-siden. Under **Status** angiver det viste datointerval det aldersfilter, der blev valgt, da connectoren blev oprettet.

## <a name="more-information"></a>Flere oplysninger

LinkedIn-elementer importeres til LinkedIn-undermappen i indbakken i lagerpostkassen i Microsoft 365. De vises som mails.