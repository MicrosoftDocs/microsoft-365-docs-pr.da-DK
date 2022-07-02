---
title: Få vist og organiser køen Microsoft Defender for Endpoint beskeder
description: Få mere at vide om, hvordan Microsoft Defender for Endpoint beskeder fungerer, og hvordan du sorterer og filtrerer lister over beskeder.
keywords: beskeder, køer, beskedkø, sortering, rækkefølge, filter, administrere beskeder, ny, i gang, løst, nyeste, tid i kø, alvorsgrad, tidsperiode, microsoft threat experts alerts
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
ms.date: 03/27/2020
ms.technology: mde
ms.openlocfilehash: 13959666f0c44f83fcb938db010ed30d5e5056b4
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607520"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-alerts-queue"></a>Få vist og organiser køen Microsoft Defender for Endpoint beskeder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-alertsq-abovefoldlink)

**Køen Beskeder** viser en liste over beskeder, der er markeret fra enheder i netværket. Som standard viser køen beskeder, der er set inden for de sidste 30 dage i en grupperet visning. De seneste beskeder vises øverst på listen, så du kan se de nyeste beskeder først.

> [!NOTE]
> Beskederne reduceres betydeligt med automatiseret undersøgelse og afhjælpning, hvilket giver eksperter i sikkerhedsoperationer mulighed for at fokusere på mere avancerede trusler og andre initiativer af høj værdi. Når en besked indeholder et understøttet objekt til automatiseret undersøgelse (f.eks. en fil) på en enhed, der har et understøttet operativsystem til det, kan en automatiseret undersøgelse og afhjælpning starte. Du kan få flere oplysninger om automatiserede undersøgelser under [Oversigt over automatiserede undersøgelser](automated-investigations.md).

Der er flere indstillinger, du kan vælge imellem for at tilpasse visningen af beskeder.

På den øverste navigationslinje kan du:

- Tilpas kolonner for at tilføje eller fjerne kolonner
- Anvend filtre
- Vis beskeder for en bestemt varighed, f.eks. 1 dag, 3 dage, 1 uge, 30 dage og 6 måneder
- Eksportér listen over beskeder til Excel
- Administrer beskeder

:::image type="content" source="images/alerts-queue-list.png" alt-text="Siden Beskeder i kø" lightbox="images/alerts-queue-list.png":::

## <a name="sort-and-filter-alerts"></a>Sortér og filtrer beskeder 

Du kan anvende følgende filtre for at begrænse listen over beskeder og få en mere fokuseret visning af beskederne.

### <a name="severity"></a>Sværhedsgraden

Alvorsgrad af vigtig besked|Beskrivelse
---|---
Høj <br> ( Rød)|Beskeder, der ofte ses i forbindelse med avancerede vedvarende trusler (APT). Disse beskeder angiver en høj risiko på grund af alvorligheden af de skader, de kan påføre enheder. Nogle eksempler er: aktiviteter med legitimationsoplysninger tyveriværktøjer, ransomware-aktiviteter, der ikke er forbundet med nogen gruppe, manipulation med sikkerhedssensorer eller eventuelle ondsindede aktiviteter, der er tegn på en menneskelig modstander.
Medium <br> ( Orange)|Beskeder fra registrering af slutpunkter og svar efter sikkerhedsbrud, der kan være en del af en avanceret vedvarende trussel (APT). Disse funktionsmåder omfatter observerede funktionsmåder, der er typiske for angrebsfaser, unormal ændring af registreringsdatabasen, udførelse af mistænkelige filer osv. Selvom nogle kan være en del af intern sikkerhedstest, kræver det undersøgelse, da det også kan være en del af et avanceret angreb.
Lav <br> (Gul)|Beskeder om trusler, der er forbundet med almindelig kendt malware. For eksempel hack-værktøjer, ikke-malware hack værktøjer, såsom kørsel udforskning kommandoer, clearing logfiler, osv., der ofte ikke angiver en avanceret trussel rettet mod organisationen. Det kan også stamme fra en test af et isoleret sikkerhedsværktøj af en bruger i din organisation.
Informative <br> (Grå)|Beskeder, der muligvis ikke anses for at være skadelige for netværket, men som kan øge organisationens sikkerhedsbevidsthed om potentielle sikkerhedsproblemer.

#### <a name="understanding-alert-severity"></a>Om alvorsgrad af vigtige beskeder

Beskedafgrænsninger i Microsoft Defender Antivirus (Microsoft Defender AV) og Defender for Endpoint er forskellige, fordi de repræsenterer forskellige områder.

Alvorsgraden af Microsoft Defender Antivirus-truslen repræsenterer den absolutte alvorsgrad af den registrerede trussel (malware) og tildeles baseret på den potentielle risiko for den enkelte enhed, hvis den er inficeret.

Besked alvorsgraden af Defender for Endpoint repræsenterer alvorsgraden af den registrerede funktionsmåde, den faktiske risiko for enheden, men endnu vigtigere den potentielle risiko for organisationen.

Det kan f.eks. være:

- Alvorsgraden af en besked fra Defender for Endpoint om en Microsoft Defender Antivirus registreret trussel, der blev forhindret, og som ikke smittede enheden, er kategoriseret som "Informational", fordi der ikke var nogen faktiske skader.
- En advarsel om en kommerciel malware blev registreret under udførelse, men blokeret og afhjælpes af Microsoft Defender AV, er kategoriseret som "Low", fordi det kan have forårsaget nogle skader på den enkelte enhed, men udgør ingen organisatorisk trussel.
- En advarsel om malware registreret under udførelse, som kan udgøre en trussel ikke kun for den enkelte enhed, men til organisationen, uanset om det til sidst blev blokeret, kan rangeres som "Medium" eller "High".
- Mistænkelige adfærdsbeskeder, der ikke blev blokeret eller afhjælpet, rangeres "Low", "Medium" eller "High" efter de samme organisatoriske trusselsovervejelser.

### <a name="status"></a>Status

Du kan vælge at filtrere listen over beskeder baseret på deres status.

> [!NOTE]
> Hvis du får vist beskedstatus for *ikke-understøttet beskedtype* , betyder det, at automatiserede undersøgelsesfunktioner ikke kan hente beskeden for at køre en automatisk undersøgelse. Du kan dog [undersøge disse beskeder manuelt](../defender/investigate-incidents.md#alerts).

### <a name="categories"></a>Kategorier

Vi har omdefineret beskedkategorierne, så de passer til [virksomhedens angrebstaktik](https://attack.mitre.org/tactics/enterprise/) i [MITRE ATT-&CK-matrixen](https://attack.mitre.org/). Nye kategorinavne gælder for alle nye beskeder. Eksisterende beskeder bevarer de forrige kategorinavne.

### <a name="service-sources"></a>Tjenestekilder

Microsoft-trusselseksperter deltagere i prøveversionen kan nu filtrere og se opdagelser fra den nye trusselsekspertadministrerede jagttjeneste.

Filtrer beskederne baseret på følgende tjenestekilder:

- Microsoft Defender for Identity
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Endpoint
- Microsoft 365 Defender
- Microsoft Defender for Office 365
- Appstyring
- AAD Identity Protection

> [!NOTE]
> Antivirusfilteret vises kun, hvis enheder bruger Microsoft Defender Antivirus som standardprodukt til beskyttelse modmalware i realtid.

### <a name="tags"></a>Tags

Du kan filtrere beskederne baseret på Mærker, der er tildelt til beskeder.

### <a name="policy"></a>Politik 

Du kan filtrere beskederne baseret på følgende politikker:

|Registreringskilde|API-værdi|
|---|---|
|Sensorer fra tredjepart|ThirdPartySensors|
|Antivirus|WindowsDefenderAv|
|Automatiseret undersøgelse|AutomatedInvestigation|
|Brugerdefineret registrering|Brugerdefineret registrering|
|Brugerdefineret TI|CustomerTI|
|EDR|WindowsDefenderAtp|
|Microsoft 365 Defender|MTP|
|Microsoft Defender for Office 365|OfficeATP|
|Microsoft Threat Experts|ThreatExperts|
|Smartscreen|WindowsDefenderSmartScreen|

### <a name="entities"></a>Enheder

Du kan filtrere beskederne baseret på enhedsnavn eller id. 

### <a name="automated-investigation-state"></a>Automatiseret undersøgelsestilstand

Du kan vælge at filtrere beskederne baseret på deres automatiserede undersøgelsestilstand.



## <a name="related-topics"></a>Relaterede emner

- [Administrer Microsoft Defender for Endpoint beskeder](manage-alerts.md)
- [Undersøg Microsoft Defender for Endpoint beskeder](investigate-alerts.md)
- [Undersøg en fil, der er knyttet til en Microsoft Defender for Endpoint besked](investigate-files.md)
- [Undersøg enheder på listen over Microsoft Defender for Endpoint enheder](investigate-machines.md)
- [Undersøg en IP-adresse, der er knyttet til en Microsoft Defender for Endpoint besked](investigate-ip.md)
- [Undersøg et domæne, der er knyttet til en Microsoft Defender for Endpoint besked](investigate-domain.md)
- [Undersøg en brugerkonto i Microsoft Defender for Endpoint](investigate-user.md)
