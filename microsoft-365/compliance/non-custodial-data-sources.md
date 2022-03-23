---
title: Føj ikke-registrerede datakilder til en Advanced eDiscovery sag
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
description: Du kan føje ikke-registrerede datakilder til en Advanced eDiscovery og placere en venteposition på datakilden. Ikke-registerede datakilder bliver genindført, så alt indhold, der blev markeret som delvist indekseret, behandles igen, så det bliver fuldt og hurtigt søgbart.
ms.openlocfilehash: a4702ebdfbd41b2541c51380a1d44dd133d506c9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588653"
---
# <a name="add-non-custodial-data-sources-to-an-advanced-ediscovery-case"></a>Føj ikke-registrerede datakilder til en Advanced eDiscovery sag

I Advanced eDiscovery tilfælde opfylder det ikke altid dine behov for at knytte Microsoft 365 datakilde til en medarbejdermedarbejder i sagen. Men det kan stadig være nødvendigt at knytte disse data til en sag, så du kan søge i dem, føje dem til et korrektursæt og analysere og gennemse dem. Funktionen i Advanced eDiscovery kaldes *ikke-registrerede* datakilder og gør det muligt at føje data til en sag uden at skulle knytte dem til en medarbejder. Den anvender også den samme Advanced eDiscovery-funktionalitet på data, der ikke er til rådighed for data, der er knyttet til øverlige oplysninger. To af de mest nyttige ting, du kan anvende på data, der ikke skal opbevares, er at sætte dem i venteposition og behandle dem ved hjælp [af Avanceret indeksering](indexing-custodian-data.md).

## <a name="add-a-non-custodial-data-source"></a>Tilføje en datakilde, der ikke er til information

Følg disse trin for at tilføje og administrere datakilder, der ikke er tillid til, Advanced eDiscovery en sag.

1. På **Advanced eDiscovery skal** du klikke på den sag, du vil føje dataene til.

2. Klik på **fanen Datakilder**, og klik **derefter på Tilføj datakilderF** >  **tilføjet dataplaceringer**.

3. På pop **op-siden Nye ikke-registrerede dataplaceringer** skal du vælge de datakilder, du vil føje til sagen. Du kan tilføje flere postkasser og websteder ved at udvide **SharePoint** eller **Exchange** og derefter klikke på **Rediger**.

   ![Tilføj SharePoint og Exchange postkasser som ikke-følsomme datakilder.](../media/NonCustodialDataSources1.png)

   - **SharePoint –** Klik på **Rediger for** at tilføje websteder. Vælg et websted på listen, eller du kan søge efter et websted ved at skrive URL-adressen til webstedet i søgelinjen. Vælg de websteder, du vil tilføje som ikke-registrerede datakilder, og klik på **Tilføj**.

   - **Exchange** – Klik på **Rediger for** at tilføje postkasser. Skriv et navn eller alias (mindst tre tegn) i søgefeltet for postkasser eller distributionsgrupper. Markér de postkasser, du vil tilføje som datakilder, der ikke er til hjælp, og klik på **Tilføj**.

   > [!NOTE]
   > Du kan bruge sektionerne **SharePoint** **og Exchange** til at tilføje websteder og postkasser, der er knyttet til en team- eller Yammer-gruppe, som ikke-selvbeholdende datakilder. Du skal tilføje postkassen og webstedet, der er knyttet til en team- eller Yammer gruppe, separat.<br/><br/> Tilføjelse af en rodwebsteds URL-adresse (f.eks `https://contoso-my.sharepoint.com/personal/` `https://contoso-my.sharepoint.com/`. eller ) som SharePoint datakilde understøttes heller ikke. Du skal tilføje bestemte websteder.

4. Når du tilføjer ikke-registrerede datakilder, har du mulighed for at placere disse placeringer i venteposition eller ej. Markér eller fjern markeringen i **afkrydsningsfeltet Sæt** i venteposition ud for datakilden for at placere det i venteposition.

5. Klik **på** Tilføj nederst på pop **op-siden Nye ikke-registrerede dataplaceringer** for at føje datakilderne til sagen.

   Alle datakilder, som ikke er registrerede, og som du har tilføjet, er angivet **på siden** Datakilder. Datakilder, der ikke er tillid til, identificeres af **værdien for** Dataplacering **i kolonnen Kildetype** .

   ![Ikke-ressourcers datakilder under fanen Datakilder.](../media/NonCustodialDataSources2.png)

Når du har føjet ikke-registrerede datakilder til sagen, oprettes og vises der et job med navnet Genbevaring af data, der ikke er til opbevaring, og det vises på fanen **Jobs** i sagen. Når jobbet er oprettet, startes processen Avanceret indeksering, og datakilderne indekseres igen.

## <a name="manage-the-hold-for-non-custodial-data-sources"></a>Administrere ventepositionen for ikke-registrerede datakilder

Når du placerer en venteposition på en datakilde, der ikke er til opbevaring, oprettes der automatisk en politik for venteposition, der indeholder de ikke-begrærlige datakilder for sagen. Når du placerer andre ikke-registrerede datakilder i venteposition, føjes de til denne ventepositionspolitik.

1. Åbn dialogboksen Advanced eDiscovery store og små bogstaver, og vælg **fanen Venteposition**.

2. Klik **på NCDSHold-\<GUID\>**, hvor GUID-værdien er entydig for sagen.

   Pop op-siden viser oplysninger og statistikker om de ikke-registrerede datakilder, der er i venteposition.

   ![Pop op-siden for ikke-registrerede datakilder viser statistik.](../media/NonCustodialDataSourcesHoldFlyout.png)

3. Klik **på Rediger venteposition** for at få vist de ikke-følsomme datakilder, der er sat i venteposition, og udføre følgende administrationsopgaver:

   - På siden **Placeringer kan** du slippe en datakilde, der ikke er til opbevaring, ved at fjerne den fra ventepositionen. Frigivelse af en datakilde fjerner ikke den ikke-registrerede datakilde fra sagen. Det fjerner kun den venteposition, der blev sat på datakilden.

   - På siden **Forespørgsel** kan du redigere ventepositionen for at oprette en forespørgselsbaseret venteposition, der anvendes til alle ikke-beskårede datakilder i sagen.
