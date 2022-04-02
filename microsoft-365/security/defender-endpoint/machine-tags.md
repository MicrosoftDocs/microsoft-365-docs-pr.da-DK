---
title: Opret og administrer enhedsmærker
description: Brug enhedsmærker til at gruppere enheder til at registrere kontekst og aktivere oprettelse af dynamisk liste som en del af en hændelse
keywords: mærker, enhedsmærker, enhedsgrupper, grupper, afhjælpning, niveau, regler, aad-gruppe, rolle, tildel, rang
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: b0b94e4905a780be9a608c8e91967b47a4db7160
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465745"
---
# <a name="create-and-manage-device-tags"></a>Opret og administrer enhedsmærker

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Tilføj mærker på enheder for at oprette en logisk gruppetilhørsforhold. Enhedsmærker understøtter korrekt tilknytning af netværket, så du kan vedhæfte forskellige mærker for at registrere kontekst og aktivere dynamisk oprettelse af lister som en del af en hændelse. Mærker kan bruges som et filter i visningen **Lager over enheder** eller til at gruppere enheder. Du kan finde flere oplysninger om enhedsgruppering i [Opret og administrer enhedsgrupper](machine-groups.md).

Du kan tilføje mærker på enheder på følgende måder:

- Brug af portalen
- Indstilling af en registreringsdatabasenøgleværdi

> [!NOTE]
> Der kan være en ventetid mellem det tidspunkt, hvor et mærke føjes til en enhed, og dens tilgængelighed på listen over enheder og på siden enhed.

Hvis du vil tilføje enhedsmærker ved hjælp af API, skal [du se Tilføj eller fjern enhedsmærkers API](add-or-remove-machine-tags.md).

## <a name="add-and-manage-device-tags-using-the-portal"></a>Tilføje og administrere enhedsmærker ved hjælp af portalen

1. Vælg den enhed, du vil administrere mærker for. Du kan vælge eller søge efter en enhed fra en af følgende visninger:

   - **Dashboard for sikkerhedshandlinger** – Vælg enhedsnavnet fra sektionen Bedste enheder med aktive beskeder.
   - **Kø til beskeder** – Vælg enhedsnavnet ud for enhedsikonet i køen med vigtige beskeder.
   - **Lager over** enheder – Vælg enhedsnavnet på listen over enheder.
   - **Søgefelt** – Vælg Enhed i rullemenuen, og angiv enhedsnavnet.

     Du kan også få adgang til påmindelsessiden gennem fil- og IP-visningerne.

2. Vælg **Administrer mærker** fra rækken af Svarhandlinger.

    :::image type="content" source="images/manage-tags-option.png" alt-text="Billede af knappen Administrer mærker" lightbox="images/manage-tags-option.png":::
    

3. Skriv for at finde eller oprette mærker

    :::image type="content" source="images/create-new-tag.png" alt-text="Tilføjelse af mærker på enhed1" lightbox="images/create-new-tag.png":::

Mærker føjes til enhedsvisningen og afspejles også i visningen **Lagerenheder** . Du kan derefter bruge **filteret Mærker** til at få vist den relevante liste over enheder.

> [!NOTE]
> Filtrering fungerer muligvis ikke på mærkenavne, der indeholder parenteser.
>
> Når du opretter et nyt mærke, vises der en liste over eksisterende mærker. Listen viser kun mærker, der er oprettet via portalen. Eksisterende mærker, der er oprettet fra klientenheder, vises ikke.

Du kan også slette mærker fra denne visning.

:::image type="content" source="images/new-tag-label-display.png" alt-text="Tilføjelse af mærker på enhed2" lightbox="images/new-tag-label-display.png":::

## <a name="add-device-tags-by-setting-a-registry-key-value"></a>Tilføj enhedsmærker ved at angive en registreringsdatabasenøgleværdi

> [!NOTE]
> Gælder kun på følgende enheder:
>
> - Windows 11
> - Windows 10, version 1709 eller nyere
> - Windows Server, version 1803 eller nyere
> - Windows Server 2016
> - Windows Server 2012 R2
> - Windows Server 2008 R2 SP1
> - Windows 8.1
> - Windows 7 SP1

> [!NOTE]
> Det maksimale antal tegn, der kan angives i et mærke, er 200.

Enheder med lignende mærker kan være praktiske, når du har brug for at anvende kontekstafhængig handling på en bestemt liste over enheder.

Brug følgende post i registreringsdatabasen til at tilføje et mærke på en enhed:

- Registreringsdatabasenøgle: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging\`
- Registreringsdatabasenøgleværdi (REG_SZ): `Group`
- Nøgledata i registreringsdatabasen: `Name of the tag you want to set`

> [!NOTE]
> Enhedskoden er en del af rapporten med enhedsoplysninger, der genereres en gang om dagen. Som alternativ kan du vælge at genstarte slutpunktet, der ville overføre en ny rapport med enhedsoplysninger.
>
> Hvis du vil fjerne et mærke, der blev tilføjet ved hjælp af den ovenstående registreringsdatabasenøgle, skal du fjerne indholdet af registreringsdatabasenøgledataene i stedet for at fjerne "Gruppe"-nøglen.
