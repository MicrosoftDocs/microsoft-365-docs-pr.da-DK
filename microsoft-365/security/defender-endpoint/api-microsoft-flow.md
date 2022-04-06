---
title: Sådan bruger du Power Automate forbindelse til at konfigurere en Flow til begivenheder
ms.reviewer: ''
description: Brug Microsoft Defender for Endpoint Flow forbindelseskomponent til at oprette et flow, der udløses, når der sker en ny hændelse på din lejer.
keywords: flow, understøttede API'er, api, Microsoft-flow, forespørgsel, automatisering, power automate
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: how-to
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 63626978311b679d0f8b520e4b041d92942bd1fd
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467989"
---
# <a name="how-to-use-power-automate-connector-to-set-up-a-flow-for-events"></a>Sådan bruger du Power Automate forbindelse til at konfigurere en Flow til begivenheder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Automatisering af sikkerhedsprocedurer er et standardkrav for alle moderne SOC (Security Operations Center). For at SOC-teams kan fungere på den mest effektive måde, er automatisering et must. Brug Microsoft Power Automate som en hjælp til at oprette automatiserede arbejdsprocesser og opbygge en end-to-end-procedure automatisering inden for et par minutter. Microsoft Power Automate understøtter forskellige forbindelser, der er bygget nøjagtigt til det.  

Brug denne artikel som vejledning i at oprette automatiseringer, der udløses af en hændelse, f.eks. når der oprettes en ny besked i din lejer. Microsoft Defender API har en officiel Power Automate Connector med mange funktioner. 

:::image type="content" source="images/api-flow-0.png" alt-text="Siden Handlinger i Microsoft Defender 365-portalen" lightbox="images/api-flow-0.png" :::

> [!NOTE]
> Du kan finde flere oplysninger om forudsætninger for premium-forbindelseslicenser [i Licenser til premium-forbindelser](/power-automate/triggers-introduction#licensing-for-premium-connectors).

## <a name="usage-example"></a>Brugseksememem

Følgende eksempel viser, hvordan du opretter et Flow, der udløses, når der opstår en ny besked på din lejer. Du bliver vejledt i at definere, hvilken begivenhed der starter flowet, og hvilken næste handling der skal foretages, når den pågældende udløser forekommer.  

1. Log på [Microsoft Power Automate](https://flow.microsoft.com).

2. Gå til **Mine flow** \> **Ny** \> **automatiseret fra tom**.

    :::image type="content" source="images/api-flow-1.png" alt-text="Ruden Ny flow under Menupunktet Mine flow i Microsoft Defender 365-portalen" lightbox="images/api-flow-1.png":::

3. Vælg et navn til din Flow, søg efter "Microsoft Defender ATP Triggers" som udløser, og vælg derefter den nye udløser til vigtige beskeder.

    :::image type="content" source="images/api-flow-2.png" alt-text=" Udløsersektionen Vælg dit flow i Microsoft Defender 365-portalen" lightbox="images/api-flow-2.png" :::

Nu har du et Flow, der udløses, hver gang der opstår en ny besked.

:::image type="content" source="images/api-flow-3.png" alt-text="Beskrivelse af udløser" lightbox="images/api-flow-3.png":::

Det eneste, du skal gøre nu, er at vælge de næste trin.
Du kan f.eks. isolere enheden, hvis beskedens alvorsgrad er høj, og sende en mail om den.
Udløseren Besked indeholder kun besked-id'et og computer-id'et. Du kan bruge forbindelsen til at udvide disse enheder.

### <a name="get-the-alert-entity-using-the-connector"></a>Hent enheden Alert ved hjælp af forbindelsen

1. Vælg **Microsoft Defender ATP** for det nye trin.

2. Vælg **Beskeder – Få API'en med enkelt besked**.

3. Indstil **besked-id'et** fra det sidste trin som **Input**.

    :::image type="content" source="images/api-flow-4.png" alt-text="Ruden Vigtige beskeder"  lightbox="images/api-flow-4.png":::

### <a name="isolate-the-device-if-the-alerts-severity-is-high"></a>Isoler enheden, hvis beskedens alvorsgrad er høj

1. Tilføj **betingelse** som et nyt trin.

2. Kontrollér, om alvorsgrad for **besked er lig med** Høj.

   Hvis ja, skal du tilføje **handlingen Microsoft Defender ATP – Isolate machine** med computer-id'et og en kommentar.

    :::image type="content" source="images/api-flow-5.png" alt-text="Ruden Handlinger"  lightbox="images/api-flow-5.png":::

3. Tilføj et nyt trin til mail om påmindelsen og isolationen. Der er flere mailforbindelser, der er meget nemme at bruge, f.eks. Outlook eller Gmail.

4. Gem dit flow.

Du kan også oprette et **planlagt flow** , der kører Avanceret ræveforespørgsler og meget mere!

## <a name="related-topic"></a>Relateret emne
- [Microsoft Defender for Endpoint API'er](apis-intro.md)
