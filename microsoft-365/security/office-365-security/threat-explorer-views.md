---
title: Visninger i Trusselsstifinder og registreringer i realtid
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
description: Få mere at vide om, hvordan du bruger Threat Explorer og registreringer i realtid til at undersøge og reagere på trusler Microsoft 365 Defender portalen.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 959d3d676f07a7816b622d5db53252c846340d2a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589563"
---
# <a name="views-in-threat-explorer-and-real-time-detections"></a>Visninger i Trusselsstifinder og registreringer i realtid

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


![Threat Explorer.](../../media/explorer.png)

[Threat Explorer](threat-explorer.md) (og registreringerne i realtid) er et effektivt værktøj i næsten realtid, der kan hjælpe sikkerhedsteams med at undersøge og reagere på trusler Microsoft 365 Defender portalen. Stifinder (og rapporten om registreringer i realtid) viser oplysninger om mistænkelig malware og phish i mails og filer i Office 365 samt andre sikkerhedstrusler og risici for din organisation.

- Hvis du har [Microsoft Defender til Office 365](defender-for-office-365.md) Plan 2, har du Stifinder.
- Hvis du har Microsoft Defender Office 365 Plan 1, har du registreringer i realtid.

Når du åbner Stifinder (eller rapporten over registreringer i realtid), viser standardvisningen registreringer af malware i mails for de seneste 7 dage. Denne rapport kan også vise Microsoft Defender til Office 365 registreringer, f.eks ondsindede URL-adresser, der registreres af [Pengeskab Links](safe-links.md), og skadelige filer, der [registreres af Pengeskab vedhæftede filer](safe-attachments.md). Denne rapport kan ændres til at vise data for de seneste 30 dage (med et Microsoft Defender for Office 365 P2-betalt abonnement). Prøveabonnementer indeholder kun data for de seneste syv dage.

****

|Abonnement|Hjælpeprogram|Dage med data|
|---|---|---|
|Microsoft Defender for Office 365 P1-prøveversion|Registreringer i realtid|7|
|Microsoft Defender for Office 365 P1 betalt|Registreringer i realtid|30|
|Microsoft Defender for Office 365 P1 betalte test af Defender for Office 365 P2-prøveversion|Threat Explorer|7|
|Microsoft Defender for Office 365 P2-prøveversion|Threat Explorer|7|
|Microsoft Defender for Office 365 P2 betalt|Threat Explorer|30|
|

> [!NOTE]
> Vi vil snart udvide grænsen for dataopbevaring og søgning i Stifinder (og realtid) for lejere til prøveversioner fra 7 til 30 dage. Denne ændring registreres som en del af oversigtselement nr. 70544 og er i øjeblikket i en udrulningsfase.

Brug menuen **Vis** til at ændre, hvilke oplysninger der vises. Værktøjstip hjælper dig med at afgøre, hvilken visning du skal bruge.

![Menuen Visningen Trusselsstifinder.](../../media/all-email.png)

Når du har valgt en visning, kan du anvende filtre og konfigurere forespørgsler til yderligere analyse. De følgende afsnit indeholder en kort oversigt over de forskellige visninger, der er tilgængelige i Stifinder (eller registreringer i realtid).

## <a name="email--malware"></a>Malware > mail

Hvis du vil have vist denne rapport i Stifinder (eller registreringer i realtid), skal du **vælge Vis** **mailmalware** \> \>. Denne visning viser oplysninger om mails, der er identificeret som indeholdende malware.

![Få vist data om mails, der er identificeret som malware.](../../media/detection-technology.png)

Klik **på Afsender** for at åbne listen over visningsindstillinger. Brug denne liste til at få vist data efter afsender, modtagere, afsenderdomæne, emne, registreringsteknologi, beskyttelsesstatus og meget mere.

Hvis du f.eks. vil se, hvilke handlinger der er foretaget på registrerede mails, skal **du vælge Beskyttelsesstatus** på listen. Vælg en indstilling, og klik derefter på knappen Opdater for at anvende filteret på rapporten.

![Statusindstillinger for Trusselsbeskyttelse for Threat Explorer.](../../media/ThreatExplorerProtectionStatusOptions.png)

Få vist flere oplysninger om bestemte meddelelser under diagrammet. Når du vælger et element på listen, åbnes en pop op-rude, hvor du kan få mere at vide om det element, du har valgt.

![Trusselsstifinder med pop op-vinduet åbnet.](../../media/ThreatExplorerMalwareItemSelectedFlyout.png)

## <a name="email--phish"></a>Mail > Phish

For at få vist denne rapport i Stifinder (eller registreringer i realtid) skal du **vælge Vis** \> **phish-mail**\>. Denne visning viser mails, der identificeres som forsøg på phishing.

![Få vist data om mails, der identificeres som forsøg på phishing.](../../media/phish.png)

Klik **på Afsender** for at åbne listen over visningsindstillinger. Brug denne liste til at få vist data efter afsender, modtagere, afsenderdomæne, afsender-IP, URL-domæne, klik på konklusion og meget mere.

Hvis du f.eks. vil se, hvilke handlinger der blev foretaget, når der blev klikket på URL-adresser, der blev identificeret som phishingforsøg, skal du vælge Klik på konklusion på listen, vælge en eller flere indstillinger og derefter klikke på knappen Opdater.

![Klik på indstillinger for konklusion for Phish-rapporten.](../../media/click-verdict.png)

Under diagrammet kan du få vist flere oplysninger om bestemte meddelelser, URL-klik, URL-adresser og mailens oprindelse.

![URL-adresser registreret som phish i mails.](../../media/ThreatExplorerEmailPhishURLs.png)

Når du vælger et element på listen, f.eks. en URL-adresse, der blev registreret, åbnes en pop op-rude, hvor du kan få mere at vide om det element, du har valgt.

![Oplysninger om en registreret URL-adresse.](../../media/ThreatExplorerEmailPhishURLDetails.png)

## <a name="email--submissions"></a>Mail > indsendelser

Hvis du vil have vist denne rapport i Stifinder (eller registreringer i realtid), skal du **vælge Vis** \> **mailindsendelser**\>. Denne visning viser mails, som brugere har rapporteret som uønsket mail, ikke uønsket mail eller phishingmail.

![Mails rapporteret af brugere.](../../media/ThreatExplorerEmailUserReportedViewOptions.png)

Klik **på Afsender** for at åbne listen over visningsindstillinger. Brug denne liste til at få vist oplysninger efter afsender, modtagere, rapporttype (brugerens bestemmelse om, at mailen var uønsket, ikke uønsket eller phish) og meget mere.

Hvis du f.eks. vil have vist oplysninger om mails, der er rapporteret som phishingforsøg, skal du klikke på **Afsenderrapporttype** \> **, vælge** **Phish** og derefter klikke på knappen Opdater.

![Phish valgt for filteret Rapporttype.](../../media/ThreatExplorerEmailUserReportedPhishSelected.png)

Under diagrammet kan du få vist flere oplysninger om bestemte mails, f.eks. emnelinjen, afsenderens IP-adresse, den bruger, der rapporterede meddelelsen som uønsket, ikke uønsket, eller phish og meget mere.

![Meddelelser, der blev rapporteret som forsøg på phishing.](../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png)

Vælg et element på listen for at få vist flere detaljer.

## <a name="email--all-email"></a>Mail > Alle mails

For at få vist denne rapport skal du i Stifinder **vælge Vis** \> **mail** \> **alle mails**. Disse visninger viser en samlet oversigt over mailaktivitet, herunder mails, der er identificeret som skadelige på grund af phishing eller malware, samt alle ikke-skadelige mails (normal mail, spam og massemails).

> [!NOTE]
> Hvis du får en fejlmeddelelse, hvor der står **for mange data** at vise, skal du tilføje et filter og, hvis det er nødvendigt, begrænse det datointerval, du får vist.

Hvis du vil anvende et filter, **skal** du vælge Afsender, vælge et element på listen og derefter klikke på knappen Opdater. I vores eksempel brugte vi **registreringsteknologi som** et filter (der er flere tilgængelige muligheder). Få vist oplysninger efter afsender, afsenderens domæne, modtagere, emne, vedhæftede filnavn, malwarefamilie, beskyttelsesstatus (handlinger, der er foretaget af dine funktioner til trusselsbeskyttelse og politikker i Office 365), registreringsteknologi (hvordan malwaren blev registreret) og meget mere.

![Få vist data om registrerede mails ved hjælp af registreringsteknologi.](../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png)

Få vist flere oplysninger om bestemte mails under diagrammet, f.eks. emnelinje, modtager, afsender, status osv.

## <a name="content--malware"></a>Malware > indhold

Hvis du vil have vist denne rapport i Stifinder (eller registreringer i realtid), skal du **vælge Vis malware** \> **om** \> **indhold**. Denne visning viser filer, der blev identificeret som skadelige [af Microsoft Defender Office 365 i SharePoint Online, OneDrive for Business og Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Få vist oplysninger efter malwarefamilie, registreringsteknologi (hvordan malwaren blev registreret) og arbejdsbelastning (OneDrive, SharePoint eller Teams).

![Få vist data om registreret malware.](../../media/malware-family.png)

Under diagrammet kan du få vist flere oplysninger om bestemte filer, f.eks. vedhæftede filers filnavn, arbejdsbelastning, filstørrelse, hvem der senest har ændret filen og meget mere.

## <a name="click-to-filter-capabilities"></a>Klik og filtrer-funktioner

Med Stifinder (og registreringer i realtid) kan du anvende et filter med et klik. Klik på et element i forklaringen, så bliver det pågældende element til et filter for rapporten. Lad os f.eks. antage, at vi kigger på visningen malware i Stifinder:

![Gå til Threat Management \> Explorer.](../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)

Når du **klikker på ATP-detonation** i dette diagram, resulterer det i en visning som denne:

![Explorer filtreret til kun at vise Defender for Office 365 detonationsresultaterne.](../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png)

I denne visning kigger vi nu på data for filer, der blev detoneret af Pengeskab [vedhæftede filer](safe-attachments.md). Under diagrammet kan vi se detaljer om bestemte mails, der havde vedhæftede filer, der blev registreret af Pengeskab vedhæftede filer.

![Specifikke detaljer om mails med registrerede vedhæftede filer.](../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png)

Hvis du vælger et eller flere elementer, aktiveres **menuen** Handlinger, som indeholder flere valgmuligheder, du kan vælge mellem for det eller de markerede elementer.

![Når du vælger et element, aktiveres menuen Handlinger.](../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png)

Muligheden for at filtrere med et klik og navigere til bestemte detaljer kan spare dig en masse tid ved undersøgelse af trusler.

## <a name="queries-and-filters"></a>Forespørgsler og filtre

Stifinder (samt rapporten over registreringer i realtid) har flere effektive filtre og forespørgselsfunktioner, der gør det muligt at analysere detaljer, f.eks. mest populære brugere, de bedste malwarefamilier, registreringsteknologi og meget mere. Hver type rapport tilbyder en række forskellige måder at få vist og udforske data på.

> [!IMPORTANT]
> Brug ikke jokertegn, f.eks. en stjerne eller et spørgsmålstegn, i forespørgselslinjen til Stifinder (eller registreringer i realtid). Når du søger i feltet **Emne efter mails** , udfører Stifinder (eller registreringer i realtid) delvis matchende og giver resultater, der svarer til en søgning med jokertegn.
