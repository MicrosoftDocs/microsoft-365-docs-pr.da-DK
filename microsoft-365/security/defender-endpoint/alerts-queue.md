---
title: Få vist og organiser Microsoft Defender for Endpoint i køen vigtige beskeder
description: Få mere at vide Microsoft Defender for Endpoint, hvordan beskederne i kø fungerer, og hvordan du sorterer og filtrerer lister over beskeder.
keywords: beskeder, køer, kø med beskeder, sortering, rækkefølge, filtrer, administrer beskeder, nye, igangværende, løst, nyeste, tid i kø, alvorsgrad, tidsperiode, beskeder fra Microsoft-trusselseksperter
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
ms.openlocfilehash: 0d6b012d2e3dbe6778c8d9c70552cf24427f8a3d
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472039"
---
# <a name="view-and-organize-the-microsoft-defender-for-endpoint-alerts-queue"></a>Få vist og organiser Microsoft Defender for Endpoint i køen vigtige beskeder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-alertsq-abovefoldlink)

**Køen Vigtige beskeder** viser en liste over beskeder, der er markeret med flag fra enheder i dit netværk. Som standard viser køen beskeder, der er set i de seneste 30 dage i en grupperet visning. De nyeste beskeder vises øverst på listen, hvilket hjælper dig med at få vist de nyeste beskeder først.

> [!NOTE]
> Beskederne reduceres markant med automatiseret undersøgelse og afhjælpning, så sikkerhedseksperter kan fokusere på mere avancerede trusler og andre initiativer med høj værdi. Når en besked indeholder en understøttet enhed til automatisk undersøgelse (f.eks. en fil) på en enhed, der har et understøttet operativsystem til det, kan en automatisk undersøgelse og afhjælpning starte. Få mere at vide om automatiserede undersøgelser under [Oversigt over automatiserede undersøgelser](automated-investigations.md).

Der er flere muligheder, du kan vælge mellem for at tilpasse visningen af vigtige beskeder.

På den øverste navigationslinje kan du:

- Tilpasse kolonner for at tilføje eller fjerne kolonner
- Anvend filtre
- Få vist beskederne for en bestemt varighed, f.eks. 1 dag, 3 dage, 1 uge, 30 dage og 6 måneder
- Eksportér listen med vigtige beskeder til Excel
- Administrer beskeder

:::image type="content" source="images/alerts-queue-list.png" alt-text="Siden med køen Beskeder" lightbox="images/alerts-queue-list.png":::

## <a name="sort-and-filter-alerts"></a>Sorterings- og filtreringsbeskeder 

Du kan anvende følgende filtre til at begrænse listen over beskeder og få en mere fokuseret visning af beskederne.

### <a name="severity"></a>Alvorsgrad

Besked om alvorsgrad|Beskrivelse
---|---
Høj <br> (Rød)|Beskeder, der ofte ses i forbindelse med avancerede permanente trusler (APT). Disse beskeder angiver en høj risiko på grund af den alvorlige skade, de kan påtige på enheder. Nogle eksempler er: aktiviteter med værktøj til tyveri af legitimationsoplysninger, ransomware-aktiviteter, der ikke er knyttet til en gruppe, ændring af sikkerhedssensorer eller ondsindede aktiviteter, der spredes af en menneskelig adversær.
Mellem <br> (Orange)|Beskeder fra slutpunktsregistrering og -svar, der kan være en del af en avanceret vedvarende trussel (APT) efter brud. Disse funktionsmåder omfatter observerede funktionsmåder, der er typiske for angrebsfaser, unormale ændringer i registreringsdatabasen, udførelse af mistænkelige filer osv. Selvom nogle kan være en del af den interne sikkerhedstest, kræver det undersøgelse, da det kan også være en del af et avanceret angreb.
Lav <br> (Gul)|Beskeder om trusler, der er knyttet til meget almindeligt malware. Eksempelvis hackværktøjer, ikke-malware-hackede værktøjer, f.eks. kørsel af undersøgelseskommandoer, rydning af logfiler osv., der ofte ikke indikerer en avanceret trusselsmålretning mod organisationen. Det kan også komme fra en isoleret sikkerhedsværktøjstest af en bruger i organisationen.
Information <br> (Grå)|Beskeder, der muligvis ikke anses for at være skadelige for netværket, men som kan skabe opmærksomhed omkring organisationens sikkerhed vedrørende potentielle sikkerhedsproblemer.

#### <a name="understanding-alert-severity"></a>Forstå alvorsgrad for beskeder

Microsoft Defender Antivirus (Microsoft Defender AV) og Defender for endpoint-beskedens alvorlighed er anderledes, fordi de repræsenterer forskellige områder.

Trusselens Microsoft Defender Antivirus repræsenterer den absolutte alvorlighed af den registrerede trussel (malware) og tildeles baseret på den potentielle risiko for den enkelte enhed, hvis den er inficeret.

Alvoren af Defender for Endpoint-beskeden repræsenterer alvoren af den registrerede funktionsmåde, den faktiske risiko for enheden, men mere vigtigt den potentielle risiko for organisationen.

Det kunne f.eks. være:

- Alvoren af en Defender for Endpoint-advarsel om en Microsoft Defender Antivirus registreret trussel, der blev forhindret og ikke inficerede enheden, kategoriseres som "Informational", fordi der ikke var nogen egentlig skade.
- Der blev registreret en besked om kommerciel malware under udførelse, men blokeret og afhjælpes af Microsoft Defender AV, kategoriseres som "Lav", fordi det kan have beskadiget den enkelte enhed, men udgør ingen organisatoriske trusler.
- En advarsel om malware registreret under udførelse, som kan udgøre en trussel ikke kun for den enkelte enhed, men for organisationen, uanset om den blev blokeret med tiden, kan rangeres som "Mellem" eller "Høj".
- Mistænkelige adfærdsmæssige beskeder, som ikke blev blokeret eller afhjulpet, bliver rangeret som "Lav", "Mellem" eller "Høj" efter de samme overvejelser om organisatoriske trusler.

### <a name="status"></a>Status

Du kan vælge at filtrere listen over beskeder ud fra deres Status.

### <a name="categories"></a>Kategorier

Vi har omdefineret kategorierne for påmindelser, så de passer til virksomhedsangrebenes [taktikker](https://attack.mitre.org/tactics/enterprise/) [i MITRE ATT&CK-matrixen](https://attack.mitre.org/). Nye kategorinavne gælder for alle nye beskeder. Eksisterende beskeder beholder de forrige kategorinavne.

### <a name="service-sources"></a>Tjenestekilder

Microsoft-trusselseksperter-eksempeldeltagerne kan nu filtrere og se registreringer fra den nye trusselseksperter-administrerede jagttjeneste.

Filtrer beskederne baseret på følgende tjenestekilder:

- Microsoft Defender for Identity
- Microsoft Defender for Cloud Apps
- Microsoft Defender for Endpoint
- Microsoft 365 Defender
- Microsoft Defender for Office 365
- Appstyring
- AAD-identitetsbeskyttelse

> [!NOTE]
> Antivirusfilteret vises kun, hvis enheder Microsoft Defender Antivirus som standard antimalwareprodukt til beskyttelse i realtid.

### <a name="tags"></a>Mærker

Du kan filtrere beskederne baseret på Mærker, der er tildelt vigtige beskeder.

### <a name="policy"></a>Politik 

Du kan filtrere beskederne ud fra følgende politikker:

|Registreringskilde|API-værdi|
|---|---|
|Tredjepartssensorer|ThirdPartySensors|
|Antivirus|WindowsDefenderAv|
|Automatiseret undersøgelse|Automatiseretinvestering|
|Brugerdefineret registrering|CustomDetection|
|Brugerdefineret TI|CustomerTI|
|Slutpunktsregistrering og -svar|WindowsDefenderAtp|
|Microsoft 365 Defender|MTP|
|Microsoft Defender for Office 365|OfficeATP|
|Microsoft-trusselseksperter|ThreatExperts|
|SmartScreen|WindowsDefenderSmartScreen|

### <a name="entities"></a>Enheder

Du kan filtrere beskederne baseret på Enhedsnavn eller -id. 

### <a name="automated-investigation-state"></a>Automatiseret undersøgelsestilstand

Du kan vælge at filtrere beskederne baseret på deres automatiske undersøgelsestilstand.



## <a name="related-topics"></a>Relaterede emner

- [Administrer Microsoft Defender for Endpoint vigtige beskeder](manage-alerts.md)
- [Undersøg Microsoft Defender for Endpoint vigtige beskeder](investigate-alerts.md)
- [Undersøg en fil, der er knyttet Microsoft Defender for Endpoint besked](investigate-files.md)
- [Undersøg enhederne Microsoft Defender for Endpoint listen Over enheder](investigate-machines.md)
- [Undersøg en IP-adresse, der er knyttet Microsoft Defender for Endpoint besked](investigate-ip.md)
- [Undersøg et domæne, der er knyttet Microsoft Defender for Endpoint besked](investigate-domain.md)
- [Undersøg en brugerkonto i Microsoft Defender for Endpoint](investigate-user.md)
