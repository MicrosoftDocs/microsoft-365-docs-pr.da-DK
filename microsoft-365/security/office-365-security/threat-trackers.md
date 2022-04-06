---
title: Threat Trackers – ny og bemærkelsesværdig
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: a097f5ca-eac0-44a4-bbce-365f35b79ed1
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Få mere at vide om Threat Trackers, herunder nye Bemærkelsesværdige Trackers, for at hjælpe din organisation med at holde styr på sikkerhedsproblemer.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ba038f94e711470242995a8ea0f082cd6d82dcda
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663242"
---
# <a name="threat-trackers---new-and-noteworthy"></a>Threat Trackers – ny og bemærkelsesværdig

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[funktionerne Office 365 Threat Investigation og Response](office-365-ti.md) gør det muligt for organisationens sikkerhedsteam at opdage og gribe ind over for cybersikkerhedstrusler. Office 365 Threat Investigation- og Response-funktioner omfatter Threat Tracker-funktioner, herunder Bemærkelsesværdige trackere. Læs denne artikel for at få en oversigt over disse nye funktioner og de næste trin.

> [!IMPORTANT]
> Office 365 Threat Intelligence er nu Microsoft Defender for Office 365 Plan 2 sammen med yderligere trusselsbeskyttelsesfunktioner. Du kan få mere at vide [under Microsoft Defender for Office 365 planer og priser](https://products.office.com/exchange/advance-threat-protection) og beskrivelsen [af Microsoft Defender for Office 365-tjenesten](/office365/servicedescriptions/office-365-advanced-threat-protection-service-description).

## <a name="what-are-threat-trackers"></a>Hvad er Threat Trackers?

Threat Trackers er informative widgets og visninger, der giver dig intelligens på forskellige cybersikkerhedsproblemer, der kan påvirke din virksomhed. Du kan f.eks. få vist oplysninger om populære malwarekampagner ved hjælp af Threat Trackers.

:::image type="content" source="../../media/a883b5ac-8e2b-469a-90e0-f8ad39bb63b7.png" alt-text="Eksemplet på Threat Tracker, der viser malwarekampagner" lightbox="../../media/a883b5ac-8e2b-469a-90e0-f8ad39bb63b7.png":::

De fleste trackersider omfatter populære tal, der opdateres jævnligt, widgets, der hjælper dig med at forstå, hvilke problemer der er størst eller er vokset mest, og et hurtigt link i kolonnen **Handlinger** , der fører dig til Stifinder, hvor du kan få vist mere detaljerede oplysninger.

:::image type="content" source="../../media/e426f220-fdcb-4dd9-99a2-db97dbcf71d5.png" alt-text="Eksemplet på kampagneoplysninger i Stifinder" lightbox="../../media/e426f220-fdcb-4dd9-99a2-db97dbcf71d5.png":::

Trackers er blot nogle af de mange fantastiske funktioner, du får med [Microsoft Defender for Office 365 Plan 2](office-365-ti.md). Threat Trackers omfatter [bemærkelsesværdige sporingsmaskiner](#noteworthy-trackers), [trendingsporingsforespørgsler](#trending-trackers), [sporede forespørgsler](#tracked-queries) og [gemte forespørgsler](#saved-queries).

Hvis du vil have vist og bruge dine Threat Trackers for din organisation, skal du åbne Microsoft 365 Defender-portalen på <https://security.microsoft.com>og gå til **Mail & collaboration** \> **Threat Tracker**. Hvis du vil gå direkte til siden **Trusselssporing** , skal du bruge <https://security.microsoft.com/threattrackerv2>.

> [!NOTE]
> Hvis du vil bruge Threat Trackers, skal du være global administrator, sikkerhedsadministrator eller sikkerhedslæser. Se [Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

### <a name="noteworthy-trackers"></a>Bemærkelsesværdige trackere

Bemærkelsesværdige trackere er der, hvor du kan finde store og mindre trusler og risici, som vi mener, du bør kende til. Bemærkelsesværdige trackere hjælper dig med at finde ud af, om disse problemer findes i dit Microsoft 365 miljø, plus et link til artikler (som denne), der giver dig flere oplysninger om, hvad der sker, og hvordan de påvirker din organisations brug af Office 365. Uanset om det er en stor ny trussel (f.eks. Wannacry, Petya) eller en eksisterende trussel, der kan skabe nogle nye udfordringer (som vores andet indledende bemærkelsesværdige element - Nemucod), er det her, du finder vigtige nye ting, som du og dit sikkerhedsteam skal gennemgå og undersøge med jævne mellemrum.

Bemærkelsesværdige trackere slås op i blot et par uger, når vi identificerer nye trusler og mener, at du muligvis har brug for den ekstra synlighed, som denne funktion giver. Når den største risiko for en trussel er overstået, fjerner vi det bemærkelsesværdige element. På denne måde kan vi holde listen opdateret med andre relevante nye elementer.

### <a name="trending-trackers"></a>Mest populære trackere

Populære trackere (tidligere kaldet kampagner) fremhæver nye trusler, der er modtaget i din organisations mail i den seneste uge. Visningen Trending Trackers indeholder dynamiske vurderinger af mailtrusler, der påvirker organisationens Office 365 miljø. Denne visning viser malwaretendenser på lejerniveau, identificerer malwarefamilier, der stiger, er flade eller faldende, hvilket giver administratorer større indsigt i, hvilke trusler der kræver yderligere opmærksomhed.

:::image type="content" source="../../media/d2ccc1a0-2a1d-4e36-99b5-6766c207772f.png" alt-text="Eksemplet på widgetten trending malwarekampagner" lightbox="../../media/d2ccc1a0-2a1d-4e36-99b5-6766c207772f.png":::

Trending trackers giver dig en idé om nye trusler, du bør gennemgå for at sikre, at dit bredere virksomhedsmiljø er forberedt mod angreb.

### <a name="tracked-queries"></a>Sporede forespørgsler

Sporede forespørgsler udnytter dine gemte forespørgsler til jævnligt at vurdere Microsoft 365 aktivitet i din organisation. Dette giver dig begivenhedstendens med mere at komme i de kommende måneder. Sporede forespørgsler kører automatisk, hvilket giver dig opdaterede oplysninger uden at skulle huske at køre dine forespørgsler igen.

:::image type="content" source="../../media/0c556174-06eb-4ae5-b32a-5ff76b9e4f13.png" alt-text="Eksemplet på sporede forespørgsler med én valgt" lightbox="../../media/0c556174-06eb-4ae5-b32a-5ff76b9e4f13.png":::

### <a name="saved-queries"></a>Gemte forespørgsler

Gemte forespørgsler findes også i afsnittet Trackers. Du kan bruge Gemte forespørgsler til at gemme de almindelige Stifinder-søgninger, som du vil vende tilbage til hurtigere og gentagne gange, uden at du skal genoprette søgningen hver gang.

:::image type="content" source="../../media/188cf3ff-58f1-41ea-81aa-76158d8f40c3.png" alt-text="Listen over sporede forespørgsler med én valgt" lightbox="../../media/188cf3ff-58f1-41ea-81aa-76158d8f40c3.png":::

Du kan altid gemme en Bemærkelsesværdig tracker-forespørgsel eller en af dine egne Explorer-forespørgsler ved hjælp af knappen **Gem forespørgsel** øverst på siden Stifinder. Alt, der er gemt der, vises på listen **Gemte forespørgsler** på siden Tracker.

## <a name="trackers-and-explorer"></a>Trackers og Explorer

Uanset om du gennemgår mail, indhold eller Office aktiviteter (kommer snart), arbejder Explorer og Trackers sammen for at hjælpe dig med at undersøge og spore sikkerhedsrisici og trusler. Alt i alt giver Trackers dig oplysninger, der beskytter dine brugere ved at fremhæve nye, bemærkelsesværdige og ofte søgte problemer – så du sikrer, at din virksomhed er bedre beskyttet, når den flyttes til cloudmiljøet.

Og husk, at du altid kan give os feedback om dette eller andre Microsoft 365 sikkerhedsfunktioner ved at klikke på knappen **Feedback** i nederste højre hjørne.

:::image type="content" source="../../media/microsoft-365-defender-portal.png" alt-text="Portalen Microsoft 365 Defender" lightbox="../../media/microsoft-365-defender-portal.png":::

## <a name="trackers-and-microsoft-defender-for-office-365"></a>Sporings- og Microsoft Defender for Office 365

Med vores første bemærkelsesværdige trussel fremhæver vi avancerede malwaretrusler, der er registreret af [Pengeskab Attachments](safe-attachments.md). Hvis du er Office 365 Enterprise E5-kunde, og du ikke bruger [Microsoft Defender for Office 365](defender-for-office-365.md), skal du være – den er inkluderet i dit abonnement. Defender for Office 365 giver værdi, selvom du har andre sikkerhedsværktøjer, der filtrerer mailflow med dine Office 365 tjenester. Funktionerne anti-spam og [Pengeskab Links](safe-links.md) fungerer dog bedst, når din primære sikkerhedsløsning til mail er via Office 365.

:::image type="content" source="../../media/policies.png" alt-text="Microsoft Defender for Office 365 på Microsoft 365 Defender-portalen" lightbox="../../media/policies.png":::

I dagens trussel-riddled verden, kører kun traditionelle anti-malware scanninger betyder, at du ikke er beskyttet godt nok mod angreb. Nutidens mere avancerede angribere bruger almindeligt tilgængelige værktøjer til at oprette nye, slørede eller forsinkede angreb, der ikke genkendes af traditionelle signaturbaserede antimalwareprogrammer. Funktionen Pengeskab vedhæftede filer tager vedhæftede filer i mails og detonerer dem i et virtuelt miljø for at afgøre, om de er sikre eller skadelige. Denne detonationsproces åbner hver fil i et virtuelt computermiljø og ser derefter, hvad der sker, når filen åbnes. Uanset om det er en PDF-fil og en komprimeret fil eller et Office dokument, kan skadelig kode skjules i en fil og aktiveres kun, når offeret åbner det på deres computer. Ved at detonere og analysere filen i mailflowet finder Defender for Office 365 funktioner disse trusler baseret på adfærd, filomdømme og en række heuristiske regler.

Det nye Bemærkelsesværdige trusselsfilter fremhæver elementer, der for nylig blev registreret via Pengeskab Vedhæftede filer. Disse registreringer repræsenterer elementer, der er nye skadelige filer, som ikke tidligere blev fundet af Microsoft 365 i enten dit mailflow eller andre kunders mail. Vær opmærksom på elementerne i Bemærkelsesværdige Threat Tracker, se, hvem der blev målrettet af dem, og gennemse de oplysninger om detonation, der vises under fanen Avanceret analyse (findes ved at klikke på emnet i mailen i Stifinder). Bemærk, at du kun finder denne fane i mails, der er registreret af funktionen Pengeskab Attachments – denne bemærkelsesværdige tracker indeholder dette filter, men du kan også bruge dette filter til andre søgninger i Stifinder.

## <a name="next-steps"></a>Næste trin

- Hvis din organisation ikke allerede har disse funktioner til Office 365 Threat Investigation og Response, skal [du se Hvordan får vi Office 365 Threat Investigation- og Response-funktioner?](office-365-ti.md).

- Sørg for, at sikkerhedsteamet har de korrekte roller og tilladelser tildelt. Du skal være global administrator eller have tildelt rollen Sikkerhedsadministrator eller Søg og Fjern på Microsoft 365 Defender-portalen. Se [Tilladelser på Microsoft 365 Defender-portalen](permissions-microsoft-365-security-center.md).

- Hold øje med, at de nye trackere vises i dit Microsoft 365 miljø. Når det er muligt, kan du finde dine Trackers på siden **Threat tracker** på portalen Microsoft 365 Defender på <https://security.microsoft.com/threattracker>.

- Hvis du ikke allerede har gjort det, kan du få mere at vide om og konfigurere [Microsoft Defender for Office 365](defender-for-office-365.md) for din organisation, herunder [Pengeskab links](safe-links.md) og [Pengeskab Vedhæftede filer](safe-attachments.md).
