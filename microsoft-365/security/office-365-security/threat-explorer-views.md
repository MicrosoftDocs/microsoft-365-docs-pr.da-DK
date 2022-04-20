---
title: Visninger i Trusselsoversigt og registreringer i realtid
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 05/15/2020
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Få mere at vide om, hvordan du bruger Threat Explorer og rapporten med registreringer i realtid til at undersøge og reagere på trusler på portalen Microsoft 365 Defender.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ccc26bef5209dd297df0b3008b841edb56cdd160
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971148"
---
# <a name="views-in-threat-explorer-and-real-time-detections"></a>Visninger i Trusselsoversigt og registreringer i realtid

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

:::image type="content" source="../../media/explorer.png" alt-text="Siden Threat Explorer" lightbox="../../media/explorer.png":::

[Threat Explorer](threat-explorer.md) (og rapporten over registreringer i realtid) er et effektivt værktøj i nærheden af realtid, der hjælper sikkerhedsteams med at undersøge og reagere på trusler på Microsoft 365 Defender portalen. Explorer (og rapporten over registreringer i realtid) viser oplysninger om mistanke om malware og phish i mails og filer i Office 365 samt andre sikkerhedstrusler og risici for din organisation.

- Hvis du har [Microsoft Defender for Office 365](defender-for-office-365.md) Plan 2, så har du Explorer.
- Hvis du har Microsoft Defender for Office 365 Plan 1, har du registreringer i realtid.

Når du åbner Stifinder første gang (eller rapporten med registreringer i realtid), viser standardvisningen registreringer af malware i mails i løbet af de seneste 7 dage. Denne rapport kan også vise Microsoft Defender for Office 365 registreringer, f.eks. skadelige URL-adresser, der registreres af [Pengeskab Links](safe-links.md), og skadelige filer, der registreres af [Pengeskab vedhæftede filer](safe-attachments.md). Denne rapport kan ændres, så den viser data for de seneste 30 dage (med et betalt abonnement på Microsoft Defender for Office 365 P2). Prøveabonnementer omfatter kun data for de seneste syv dage.

|Abonnement|Nytte|Datadage|
|---|---|---|
|prøveversion af Microsoft Defender for Office 365 P1|Registreringer i realtid|7|
|betalt Microsoft Defender for Office 365 P1|Registreringer i realtid|30|
|betalt test Defender for Office 365 P2-prøveversion Microsoft Defender for Office 365 P1|Trusselsoversigt|7|
|prøveversion af Microsoft Defender for Office 365 P2|Trusselsoversigt|7|
|betalt Microsoft Defender for Office 365 P2|Trusselsoversigt|30|

> [!NOTE]
> Vi forlænger snart dataopbevarings- og søgegrænsen for prøveversionslejere (og registreringer i realtid) fra 7 til 30 dage. Denne ændring spores som en del af oversigtselement nr. 70544 og er i øjeblikket i en udrulningsfase.

Brug menuen **Vis** til at ændre, hvilke oplysninger der vises. Værktøjstip hjælper dig med at bestemme, hvilken visning der skal bruges.

:::image type="content" source="../../media/all-email.png" alt-text="Menuen Vis i Threat Explorer" lightbox="../../media/all-email.png":::

Når du har valgt en visning, kan du anvende filtre og konfigurere forespørgsler for at udføre yderligere analyser. Følgende afsnit indeholder en kort oversigt over de forskellige visninger, der er tilgængelige i Stifinder (eller registreringer i realtid).

## <a name="email--malware"></a>Mail > malware

Hvis du vil have vist denne rapport, skal du i Stifinder (eller registreringer i realtid) vælge **Vis** \> **mailmalware**\>. Denne visning viser oplysninger om mails, der blev identificeret som indeholdende malware.

:::image type="content" source="../../media/detection-technology.png" alt-text="Vis data om mail, der er identificeret som malware" lightbox="../../media/detection-technology.png":::

Klik på **Afsender** for at åbne listen over visningsindstillinger. Brug denne liste til at få vist data efter afsender, modtagere, afsenderdomæne, emne, registreringsteknologi, beskyttelsesstatus med mere.

Hvis du f.eks. vil se, hvilke handlinger der blev udført på registrerede mails, skal du vælge **Beskyttelsesstatus** på listen. Vælg en indstilling, og klik derefter på knappen Opdater for at anvende filteret på din rapport.

:::image type="content" source="../../media/ThreatExplorerProtectionStatusOptions.png" alt-text="Indstillinger for trusselsbeskyttelsesstatus for Threat Explorer" lightbox="../../media/ThreatExplorerProtectionStatusOptions.png":::

Under diagrammet kan du se flere oplysninger om bestemte meddelelser. Når du vælger et element på listen, åbnes der en pop op-rude, hvor du kan få mere at vide om det element, du har valgt.

:::image type="content" source="../../media/ThreatExplorerMalwareItemSelectedFlyout.png" alt-text="Threat Explorer med pop op-vinduet åbnet" lightbox="../../media/ThreatExplorerMalwareItemSelectedFlyout.png":::

## <a name="email--phish"></a>Mail > phish

Hvis du vil have vist denne rapport, skal du i Stifinder (eller registreringer i realtid) vælge **Vis** \> **mail-phish**\>. I denne visning vises mails, der er identificeret som phishingforsøg.

:::image type="content" source="../../media/phish.png" alt-text="Vis data om mail, der er identificeret som phishingforsøg" lightbox="../../media/phish.png":::

Klik på **Afsender** for at åbne listen over visningsindstillinger. Brug denne liste til at få vist data efter afsender, modtagere, afsenderdomæne, afsender-IP, URL-domæne, klik på dom med mere.

Hvis du f.eks. vil se, hvilke handlinger der blev udført, da personer klikkede på URL-adresser, der blev identificeret som phishingforsøg, skal du vælge **Klik på dom** på listen, vælg en eller flere indstillinger, og klik derefter på knappen Opdater.

:::image type="content" source="../../media/click-verdict.png" alt-text="Indstillingerne for Klik på dom for Phish-rapporten" lightbox="../../media/click-verdict.png":::

Under diagrammet kan du se flere oplysninger om bestemte meddelelser, klik på URL-adresser, URL-adresser og mailindrindring.

:::image type="content" source="../../media/ThreatExplorerEmailPhishURLs.png" alt-text="De URL-adresser, der registreres som phish i mails" lightbox="../../media/ThreatExplorerEmailPhishURLs.png":::

Når du vælger et element på listen, f.eks. en URL-adresse, der blev registreret, åbnes der en pop op-rude, hvor du kan få mere at vide om det element, du har valgt.

:::image type="content" source="../../media/ThreatExplorerEmailPhishURLDetails.png" alt-text="Oplysninger om en registreret URL-adresse" lightbox="../../media/ThreatExplorerEmailPhishURLDetails.png":::

## <a name="email--submissions"></a>Mail > indsendelser

Hvis du vil have vist denne rapport, skal du vælge **Vis** \> **mailindsendelser** \> i Stifinder (eller registreringer i realtid). Denne visning viser mail, som brugerne har rapporteret som uønsket, ikke uønsket eller phishing-mail.

:::image type="content" source="../../media/ThreatExplorerEmailUserReportedViewOptions.png" alt-text="De mailmeddelelser, der er rapporteret af brugere" lightbox="../../media/ThreatExplorerEmailUserReportedViewOptions.png":::

Klik på **Afsender** for at åbne listen over visningsindstillinger. Brug denne liste til at få vist oplysninger efter afsender, modtagere, rapporttype (brugerens vurdering af, at mailen var uønsket, ikke uønsket eller phish) og meget mere.

Hvis du f.eks. vil have vist oplysninger om mails, der er rapporteret som phishingforsøg, skal du klikke på **Afsenderrapporttype**\>, vælge **Phish** og derefter klikke på knappen Opdater.

![Phish valgt til rapporttypefilter.](../../media/ThreatExplorerEmailUserReportedPhishSelected.png)

Under diagrammet kan du se flere oplysninger om bestemte mails, f.eks. emnelinjen, afsenderens IP-adresse, den bruger, der rapporterede meddelelsen som uønsket, ikke uønsket mail eller phish med mere.

:::image type="content" source="../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png" alt-text="De meddelelser, der blev rapporteret som phishingforsøg" lightbox="../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png":::

Vælg et element på listen for at få vist flere oplysninger.

## <a name="email--all-email"></a>Mail > alle mails

Hvis du vil have vist denne rapport, skal du vælge **Vis** \> **mail** \> **alle mails** i Stifinder. Denne visning viser en samlet visning af mailaktivitet, herunder mail, der er identificeret som skadelig på grund af phishing eller malware, samt alle ikke-skadelige mails (normal mail, spam og massemails).

> [!NOTE]
> Hvis du får vist en fejl, der læser **for mange data til at blive vist, skal** du tilføje et filter og om nødvendigt indsnævre det datointerval, du får vist.

Hvis du vil anvende et filter, skal du vælge **Afsender**, vælge et element på listen og derefter klikke på knappen Opdater. I vores eksempel brugte vi **registreringsteknologi** som et filter (der er flere tilgængelige indstillinger). Få vist oplysninger efter afsender, afsenderens domæne, modtagere, emne, navn på vedhæftet fil, malwarefamilie, beskyttelsesstatus (handlinger, der udføres af dine trusselsbeskyttelsesfunktioner og -politikker i Office 365), registreringsteknologi (hvordan malwaren blev registreret) og meget mere.

:::image type="content" source="../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png" alt-text="Teknologi til visning af data om registreret mail ved registrering" lightbox="../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png":::

Under diagrammet kan du se flere oplysninger om bestemte mails, f.eks. emnelinje, modtager, afsender, status osv.

## <a name="content--malware"></a>Indhold > malware

Hvis du vil have vist denne rapport, skal du vælge **Vis** \> **indholdsmalware** \> i Stifinder (eller registreringer i realtid). Denne visning viser filer, der er identificeret som skadelige af [Microsoft Defender for Office 365 i SharePoint Online, OneDrive for Business og Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Få vist oplysninger efter malwarefamilie, registreringsteknologi (hvordan malwaren blev registreret) og arbejdsbelastning (OneDrive, SharePoint eller Teams).

:::image type="content" source="../../media/malware-family.png" alt-text="Vis data om registreret malware" lightbox="../../media/malware-family.png":::

Under diagrammet kan du se flere oplysninger om bestemte filer, f.eks. navn på vedhæftet fil, arbejdsbelastning, filstørrelse, hvem der senest har ændret filen med mere.

## <a name="click-to-filter-capabilities"></a>Klik og filtrer-funktioner

Med Stifinder (og registreringer i realtid) kan du anvende et filter med et klik. Klik på et element i forklaringen, så bliver elementet et filter for rapporten. Lad os f.eks. antage, at vi ser på visningen Malware i Explorer:

:::image type="content" source="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png" alt-text="Siden Stifinder på portalen sikkerhed & overholdelse" lightbox="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png":::

Hvis du klikker på **ATP-detonation** i dette diagram, resulterer det i en visning som denne:

:::image type="content" source="../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png" alt-text="Stifinder filtreret, så der kun vises Defender for Office 365 detonationsresultater" lightbox="../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png":::

I denne visning kigger vi nu på data for filer, der blev detoneret af [Pengeskab Attachments](safe-attachments.md). Under diagrammet kan vi se detaljer om bestemte mails, der indeholdt vedhæftede filer, som blev registreret af Pengeskab Vedhæftede filer.

:::image type="content" source="../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png" alt-text="De specifikke oplysninger om mails med registrerede vedhæftede filer" lightbox="../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png":::

Hvis du vælger et eller flere elementer, aktiveres menuen **Handlinger** , som indeholder flere valgmuligheder, som du kan vælge mellem for det eller de valgte elementer.

:::image type="content" source="../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png" alt-text="Processen med at vælge et element, der aktiverer menuen Handlinger" lightbox="../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png":::

Muligheden for at filtrere med et klik og navigere til bestemte detaljer kan spare dig meget tid til at undersøge trusler.

## <a name="queries-and-filters"></a>Forespørgsler og filtre

Explorer (samt rapporten over registreringer i realtid) har flere effektive filtre og forespørgselsfunktioner, der giver dig mulighed for at analysere detaljer, f.eks. de mest målrettede brugere, de mest populære malwarefamilier, registreringsteknologi og meget mere. Hver type rapport giver dig en række forskellige måder at få vist og udforske data på.

> [!IMPORTANT]
> Brug ikke jokertegn, f.eks. en stjerne eller et spørgsmålstegn, på forespørgselslinjen til Stifinder (eller registreringer i realtid). Når du søger i **emnefeltet** efter mails, vil Stifinder (eller registreringer i realtid) udføre delvis matchning og give resultater, der svarer til en søgning med jokertegn.
