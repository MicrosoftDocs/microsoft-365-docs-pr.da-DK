---
title: Brug versionsversioner af poster til at opdatere poster, der er gemt i SharePoint eller OneDrive
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Få mere at vide om poster, der kan hjælpe dig med at implementere en løsning til datastyring Microsoft 365.
ms.openlocfilehash: 2aabfbf1b3e0aedd8ec7ba54d452cb01ad81776a
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63590309"
---
# <a name="use-record-versioning-to-update-records-stored-in-sharepoint-or-onedrive"></a>Brug versionsversioner af poster til at opdatere poster, der er gemt i SharePoint eller OneDrive

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

> [!NOTE]
> Da lovgivningsmæssige poster blokerer redigering, er versionsvisning af poster ikke tilgængelig for lovmæssige poster.
>
> Du kan også forhindre versionsstyring af poster for din lejer, også selvom du ikke bruger lovmæssige poster: Gå til noden Datastyring i Microsoft 365 Overholdelsescenter > **Indstillinger** >  for datastyringRetention-navneKonfigurer  >  versionsstyring af poster, og deaktiver derefter indstillingen Aktivér **postversionering**.

Muligheden for at markere et dokument [som en post](records-management.md#records) og begrænse handlinger, der kan udføres på posten, er et vigtigt mål for enhver datastyringsløsning. Samarbejde kan dog også være nødvendigt, for at folk kan oprette efterfølgende versioner.

Du kan f.eks. markere en salgskontrakt som en post, men derefter opdatere kontrakten med nye vilkår og markere den nyeste version som en ny post, mens du stadig bevarer den tidligere postversion. For disse typer scenarier understøtter SharePoint og OneDrive *registreringsversionering*. OneNote-notesbøger understøtter ikke versionsoperering af poster.

Hvis du vil bruge versionsversioner af poster, [skal du først navnmærke dokumentet og markere det som en post](declare-records.md). På dette tidspunkt vises en dokumentegenskab  med navnet Poststatus ud for opbevaringsetiketten, og den oprindelige poststatus er **Låst**.

Du kan nu gøre følgende:

- **Løbende redigere og bevare individuelle versioner af dokumentet som poster ved at låse poststatusegenskaben op.** Kun når egenskaben **Poststatus** er angivet til **Låst,** bevares en ny version af posten. Denne til/fra-knap for låst og ulåst reducerer risikoen for at bevare unødvendige versioner og kopier af dokumentet.

- **Få posterne gemt automatisk på et lokalt datalager, der er placeret i gruppen af websteder.** Hver gruppe af websteder i SharePoint og OneDrive bevarer indhold i dets bibliotek til opbevaring af dokumenter. Postversioner gemmes i mappen Poster i dette bibliotek.

- **Vedligeholde et stedsegrønt dokument, der indeholder alle versioner.** Som standard har hver SharePoint og OneDrive en versionshistorik tilgængelig i elementmenuen. I denne versionshistorik kan du nemt se, hvilke versioner der er poster, og få vist disse dokumenter.

> [!TIP]
> Når du bruger postversionering med en opbevaringsetiket, der har en slettehandling, kan du overveje at konfigurere opbevaringsindstillingen Start opbevaringsperioden baseret på **:** til at være Hvornår elementer blev **mærket**. Med denne etiketindstilling nulstilles starten af en opbevaringsperiode for hver ny postversion, hvilket sikrer, at ældre versioner slettes før nyere versioner.

Versionsversioner af poster bliver automatisk tilgængeligt for alle dokumenter, hvor der er anvendt en opbevaringsetiket, der markerer elementet som en post, og den pågældende etiket [publiceres på webstedet](create-apply-retention-labels.md). Når en bruger får vist dokumentegenskaberne ved hjælp af detaljeruden, kan brugeren slå **Poststatus** fra Låst **til** **Ulåst**. Denne handling opretter en post i mappen Poster i biblioteket Til opbevaring af dokumenter, hvor den er placeret i resten af dens opbevaringsperiode.

Mens dokumentet er låst op, kan alle brugere med standardredigeringstilladelser redigere filen. Brugerne kan dog ikke slette filen, fordi det stadig er en post. Når redigeringen er fuldført, kan en bruger derefter skifte poststatus fra Ulåst til **Låst, hvilket** forhindrer yderligere redigeringer, mens denne status er i gang. 
<br/><br/>

:::image type="content" alt-text="Egenskaben Poststatus på et dokument, der er mærket som en post." source="../media/recordversioning8.png" lightbox="../media/recordversioning8.png":::

## <a name="locking-and-unlocking-a-record"></a>Lås og lås op for en post

Når en opbevaringsetiket, der markerer indhold som en post, anvendes på et dokument, kan alle brugere med tilladelsen Bidrage eller et mere indsnævret tilladelsesniveau låse en post op eller låse en ulåst post.
<br/><br/>

:::image type="content" alt-text="Poststatus viser, at postdokumentet er ulåst." source="../media/recordversioning9.png" lightbox="../media/recordversioning9.png":::

Når en bruger låser en post op, udføres følgende handlinger:

1. Hvis den aktuelle gruppe af websteder ikke har et bibliotek til opbevaring af dokumenter, oprettes der et.

2. Hvis biblioteket til opbevaring af dokumenter ikke har mappen Poster, oprettes der en.

3. Handlingen **Kopiér** til kopierer den nyeste version af dokumentet til mappen Poster. Handlingen **Kopiér** til indeholder kun den nyeste version og ingen tidligere versioner. Det kopierede dokument betragtes nu som en postversion af dokumentet, og filnavnet har formatet: \[Titel-GUID-version\#\]

4. Den kopi, der er oprettet i mappen Poster, føjes til versionshistorikken for det oprindelige dokument, og denne version viser ordet **Post** i kommentarfeltet.

5. Det oprindelige dokument er en ny version, der kan redigeres, men ikke slettes. Kolonnen dokumentbibliotek Element **er en** post viser stadig Værdien **Ja** , fordi dokumentet stadig er en post, selvom det nu kan redigeres.

Når en bruger låser en post, kan det oprindelige dokument igen ikke redigeres. Men det er handlingen med at låse en post op, der kopierer en version til mappen Poster i biblioteket Til opbevaring af dokumenter.

## <a name="record-versions"></a>Optag versioner

Hver gang en bruger låser en post op, kopieres den nyeste version til biblioteket til opbevaring af dokumenter, og den version indeholder værdien af **Record** i feltet  Kommentarer i versionshistorikken.
<br/><br/>

:::image type="content" alt-text="Post vist i biblioteket til opbevaring af dokumenter." source="../media/recordversioning10.png" lightbox="../media/recordversioning10.png":::

For at få vist versionshistorikken skal du vælge et dokument i dokumentbiblioteket og derefter **klikke på Versionshistorik** i elementmenuen.

## <a name="where-records-are-stored"></a>Hvor poster gemmes

Poster gemmes i mappen Poster i biblioteket Preservation Hold på webstedet på øverste niveau i gruppen af websteder. I venstre navigationsrude på webstedet på øverste niveau skal du vælge Bibliotek **til** \> opbevaring af **webstedsindhold**.
<br/><br/>

![Preservation Hold library.](../media/recordversioning11.png)

<br/><br/>

![Mappen Poster i biblioteket Til opbevaring af dokumenter.](../media/recordversioning12.png)

Du kan finde flere oplysninger om, hvordan biblioteket til opbevaring af dokumenter fungerer, under [Sådan fungerer opbevaring for SharePoint og OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

## <a name="searching-the-audit-log-for-record-versioning-events"></a>Søgning i overvågningsloggen efter postversionshændelser

Handlingerne låsning og oplåsning af poster logføres i overvågningsloggen. Fra **Fil- og sideaktiviteter skal** du **vælge Ændret poststatus til låst og** **Ændret poststatus til ulåst**.

Hvis du vil have mere at vide om at søge efter disse hændelser, [skal du se Søge i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).

## <a name="next-steps"></a>Næste trin

For andre scenarier, der understøttes af datastyring, skal [du se Almindelige scenarier for datastyring](get-started-with-records-management.md#common-scenarios).
