---
title: Brug postversionsstyring i SharePoint eller OneDrive
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
description: Få mere at vide om poster, der kan hjælpe dig med at implementere en løsning til datastyring i Microsoft 365.
ms.openlocfilehash: 9515622af6a6ddb5abe28d6fb920eed72f487f41
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285056"
---
# <a name="use-record-versioning-to-update-records-stored-in-sharepoint-or-onedrive"></a>Brug postversionsstyring til at opdatere poster, der er gemt i SharePoint eller OneDrive

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Da lovmæssige poster blokerer redigering, er versionering af poster ikke tilgængelig for lovmæssige poster.
>
> Du kan også forhindre postversionsstyring for din lejer, selvom du ikke bruger lovmæssige poster: Gå til **Dataadministration** på Microsoft Purview-overholdelsesportalen > **indstillinger for administration af posterIndstillinger** >  for  >  administration af **posterKonfigurer postversionsstyring**, og slå derefter indstillingen for **Aktivér postversionsstyring** fra.

Muligheden for at markere et dokument som en [post](records-management.md#records) og begrænse handlinger, der kan udføres på posten, er et vigtigt mål for enhver løsning til datastyring. Der kan dog også være behov for samarbejde, for at personer kan oprette efterfølgende versioner.

Du kan f.eks. markere en salgsaftale som en post, men derefter skal opdatere kontrakten med nye vilkår og markere den nyeste version som en ny post, mens du stadig bevarer den tidligere postversion. I forbindelse med disse typer scenarier understøtter SharePoint og OneDrive *postversioner*. OneNote notesbogmapper understøtter ikke postversionsstyring.

Hvis du vil bruge postversionsstyring, skal du først forsyne dokumentet med en [opbevaringsmærkat, der er konfigureret til at markere elementer som en post](declare-records.md). På dette tidspunkt vises en dokumentegenskab med navnet *Poststatus* ud for opbevaringsmærkaten. Afhængigt af om etiketten er konfigureret til at låse posten op som standard (udrulles i øjeblikket), er den indledende poststatus enten **Låst** eller **Ulåst**.

Du kan nu gøre følgende:

- **Rediger og bevar løbende individuelle versioner af dokumentet som poster ved at låse egenskaben Poststatus op og låsning.** Det er kun, når egenskaben **Poststatus** er angivet til **Låst,** at en ny version af posten bevares. Denne til/fra-knap for låst og ulåst reducerer risikoen for at bevare unødvendige versioner og kopier af dokumentet.
    
    > [!NOTE]
    > Hvis mærkaten som standard er konfigureret til at låse posten op, men versionsstyring ikke er aktiveret af administratoren eller forhindret af indstillingen for datastyring, kan brugerne ikke låse dokumentet op, når de har låst det.

- **Få posterne automatisk gemt i et lager med poster på stedet, der er placeret på webstedet.** Hvert websted i SharePoint og OneDrive bevarer indhold i biblioteket til bevarelse af venteposition. Postversioner gemmes i mappen Poster i dette bibliotek. Du kan få flere oplysninger om, hvordan biblioteket bevarelsesposition fungerer, under [Sådan fungerer opbevaring for SharePoint og OneDrive](retention-policies-sharepoint.md#how-retention-works-for-sharepoint-and-onedrive).

- **Vedligehold et stedsegrønt dokument, der indeholder alle versioner.** Hvert SharePoint og OneDrive dokument har som standard en versionshistorik tilgængelig i elementmenuen. I denne versionshistorik kan du nemt se, hvilke versioner der er poster, og få vist disse dokumenter.

> [!TIP]
> Når du bruger versionering af poster med en opbevaringsmærkat, der har en sletningshandling, bør du overveje at konfigurere opbevaringsindstillingen **Start opbevaringsperioden baseret på:** til at være **Når elementer blev mærket**. Med denne mærkatindstilling nulstilles starten af opbevaringsperioden for hver nye postversion, hvilket sikrer, at ældre versioner slettes før nyere versioner.

Postversionsstyring er som standard automatisk tilgængelig for alle dokumenter, hvor der anvendes en opbevaringsmærkat, der markerer elementet som en post, og det pågældende navn [publiceres på webstedet](create-apply-retention-labels.md). Når en bruger får vist dokumentegenskaberne ved hjælp af detaljeruden, kan vedkommende skifte **status for Post** mellem **Låst** og **Ulåst**.

Mens dokumentet er ulåst, kan alle brugere med standardredigeringstilladelser redigere filen. Brugerne kan dog ikke slette filen, fordi det stadig er en post. Når redigeringen er fuldført, kan en bruger derefter slå **poststatus** fra **Låst op** til **Låst**, hvilket forhindrer yderligere redigeringer i denne status.
<br/><br/>

:::image type="content" alt-text="Egenskaben Poststatus for et dokument, der er mærket som en post." source="../media/recordversioning8.png" lightbox="../media/recordversioning8.png":::

Du kan få flere oplysninger om, hvilke brugerhandlinger der er tilladt, når en post er låst eller låst op, under [Sammenlign begrænsninger for, hvilke handlinger der er tilladt eller blokeret](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked).

## <a name="locking-and-unlocking-a-record"></a>Låsning og låsning af en post

Når en opbevaringsmærkat, der markerer indhold som en post, anvendes på et dokument, kan alle brugere med tilladelsen Bidrag eller et smallere tilladelsesniveau låse en post op eller låse en ulåst post.
<br/><br/>

:::image type="content" alt-text="Poststatus viser, at postdokumentet ikke er låst op." source="../media/recordversioning9.png" lightbox="../media/recordversioning9.png":::

Når en post låses op, sker følgende handlinger:

1. Hvis det aktuelle websted ikke har et bibliotek til bevarelse af venteposition, oprettes der et.

2. Hvis biblioteket til bevarelse af venteposition ikke har en postmappe, oprettes der en.

3. Handlingen **Kopiér til** kopierer den nyeste version af dokumentet til mappen Poster. Handlingen **Kopiér til** indeholder kun den nyeste version og ingen tidligere versioner. Dette kopierede dokument betragtes nu som en postversion af dokumentet, og filnavnet har formatet: \[Titel-GUID-version\#\]

4. Den kopi, der oprettes i mappen Poster, føjes til versionshistorikken for det oprindelige dokument, og denne version viser ordet **Post** i kommentarfeltet.

5. Det oprindelige dokument er en ny version, der kan redigeres, men ikke slettes. Kolonnen Element i dokumentbiblioteket **er en post** , der stadig viser værdien **Ja** , fordi dokumentet stadig er en post, selvom det nu kan redigeres.

Når en bruger låser en post, kan det oprindelige dokument ikke redigeres igen. Men det er den handling, der består i at låse en post op, der kopierer en version til mappen Poster i biblioteket Bevarelsesposition.

## <a name="record-versions"></a>Postversioner

Hver gang en post låses op, kopieres den seneste version til biblioteket bevarelsesposition, og den version indeholder **værdien post i** feltet **Kommentarer** i versionshistorikken.
<br/><br/>

:::image type="content" alt-text="Post, der vises i biblioteket bevarelses venteposition." source="../media/recordversioning10.png" lightbox="../media/recordversioning10.png":::

Hvis du vil have vist versionshistorikken, skal du vælge et dokument i dokumentbiblioteket og derefter klikke på **Versionshistorik** i elementmenuen.

## <a name="searching-the-audit-log-for-record-versioning-events"></a>Søger i overvågningsloggen efter hændelser for postversioner

Handlingerne til låsning og låsning af poster logføres i overvågningsloggen. Fra **Fil- og sideaktiviteter** skal du vælge **Ændret poststatus til låst** og **Ændret poststatus til ulåst**.

Du kan finde flere oplysninger om, hvordan du søger efter disse hændelser, [i Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md#file-and-page-activities).

## <a name="next-steps"></a>Næste trin

I forbindelse med andre scenarier, der understøttes af datastyring, skal du se [Almindelige scenarier til datastyring](get-started-with-records-management.md#common-scenarios).
