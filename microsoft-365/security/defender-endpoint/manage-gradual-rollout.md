---
title: Administrer den gradvise udrulningsproces for Microsoft Defender-opdateringer
description: Få mere at vide om den gradvise opdateringsproces og kontrolelementer
keywords: opdater, opdateringsproces, kontrolelementer, version
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 177a7965d3e5a2d4ddd2e62bdde95fbc2762645b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599457"
---
# <a name="manage-the-gradual-rollout-process-for-microsoft-defender-updates"></a>Administrer den gradvise udrulningsproces for Microsoft Defender-opdateringer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Det er vigtigt at sikre, at klientkomponenter er opdaterede med henblik på at levere vigtige beskyttelsesfunktioner og forhindre angreb.

Funktioner leveres via flere komponenter:

- [Slutpunktsregistrering & svar](overview-endpoint-detection-response.md)
- [Næste generations beskyttelse med](microsoft-defender-antivirus-windows.md) [cloud-leveret beskyttelse](cloud-protection-microsoft-defender-antivirus.md)
- [Reduktion af angrebsoverfladen](overview-attack-surface-reduction.md)

Opdateringer udgives månedligt ved hjælp af en gradvis udgivelsesproces. Denne proces hjælper med at aktivere tidlig registrering af fejl for at fange påvirkningen, mens den opstår, og tager hånd om det hurtigt før en større udrulning.

> [!NOTE]
> Du kan finde flere oplysninger om, hvordan du styrer daglige sikkerhedsintelligensopdateringer under [Microsoft Defender Antivirus sikkerhedsopdateringer](manage-protection-update-schedule-microsoft-defender-antivirus.md). Opdateringer sikrer, at næste generations beskyttelse kan beskyttes mod nye trusler, selvom slutpunktet ikke har adgang til beskyttelse, der leveres i skyen.

## <a name="microsoft-gradual-rollout-model"></a>Microsoft gradvis udrulningsmodel

Den følgende gradvise implementeringsmodel følges for månedlige Defender-opdateringer:

1. Den første udgivelse går ud til abonnenter på betakanalen.
2. Efter validering, feedback og rettelser starter vi den gradvise udrulningsproces på en måde, der er blevet mindre, og til Se kanalabonn på forhånd.
3. Vi fortsætter derefter med at udgive opdateringen til resten af den globale befolkning ved at skalere fra 10-100 %.

Vores teknikere overvåger løbende effekten og eskalerer eventuelle problemer for at finde en løsning efter behov.

## <a name="how-to-customize-your-internal-deployment-process"></a>Sådan tilpasser du din interne installationsproces

Hvis dine computere modtager Defender-opdateringer fra Windows Update, kan den gradvise implementeringsproces medføre, at nogle af dine computere modtager Defender-opdateringer tidligere end andre. I det følgende afsnit beskrives det, hvordan du definerer en strategi, der gør det muligt for automatiske opdateringer at flyde forskelligt til bestemte grupper af enheder ved at udnytte konfigurationen af opdateringskanalen.

> [!NOTE]
> Når du planlægger din egen gradvise udgivelse, skal du sørge for altid at have et udvalg af enheder, der abonnerer på forhåndsvisningen og de faseerede kanaler. Dette giver din organisation samt Microsoft mulighed for at forebygge eller finde og løse problemer, der er specifikke for dit miljø.

For maskiner, der modtager opdateringer gennem f.eks. Windows Server Update Services (WSUS) eller Microsoft Endpoint Configuration Manager (MECM), er flere indstillinger tilgængelige for alle Windows-opdateringer, herunder indstillinger for Microsoft Defender til slutpunkt.

- Læs mere om, hvordan du bruger en løsning som WSUS, MECM til at administrere distribution og anvendelse af opdateringer på Administrer Microsoft Defender Antivirus-opdateringer og anvende [oprindelige planer – Windows sikkerhed](manage-updates-baselines-microsoft-defender-antivirus.md#product-updates).

## <a name="update-channels-for-monthly-updates"></a>Opdater kanaler for månedlige opdateringer

Du kan tildele en computer til en opdateringskanal for at definere den kadence, som en maskine modtager månedlige program- og platformopdateringer i.

Du kan finde flere oplysninger om, hvordan du konfigurerer opdateringer, [under Opret en brugerdefineret gradvis udrulningsproces til Microsoft Defender-opdateringer](configure-updates.md).

Følgende opdateringskanaler er tilgængelige:

<br>

****

|Kanalnavn|Beskrivelse|Program|
|---|---|---|
|Beta-kanal – Foreløbige versioner|Test opdateringer før andre|Enheder, der er indstillet til denne kanal, er de første til at modtage nye månedlige opdateringer. Vælg Beta-kanal for at deltage i identificering og rapportering af problemer med Microsoft. Enheder i Windows Insider Program abonneres på denne kanal som standard. Kun til brug i testmiljøer.|
|Aktuel kanal (forhåndsvisning)|Hent opdateringer til aktuel kanal **tidligere under** den gradvise udgivelse|Enheder, der er indstillet til denne kanal, vil blive tilbudt opdateringer tidligst i løbet af den gradvise udgivelsescyklus. Foreslået til præ-produktions-/valideringsmiljøer.|
|Aktuel kanal (faseret)|Få opdateringer til aktuel kanal senere i løbet af den gradvise udgivelse|Enheder vil blive tilbudt opdateringer senere i løbet af den gradvise udgivelsescyklus. Foreslået til at gælde for en lille, repræsentativ del af din enheds population (~10 %).|
|Aktuel kanal (bred)|Hent opdateringer ved slutningen af den gradvise udgivelse|Enheder tilbydes kun opdateringer, når den gradvise udgivelsescyklus er fuldført. Foreslået til at gælde for et bredt sæt enheder i produktionsbestanden (~10-100 %).|
|Kritisk: Tidsforsinkelse|Udsink Defender-opdateringer|Enheder tilbydes opdateringer med en 48-timers forsinkelse. Bedst til datacenter maskiner, der kun modtager begrænsede opdateringer. Kun foreslået til kritiske miljøer.|
|(standard)||Hvis du deaktiverer eller ikke konfigurerer denne politik, forbliver enheden i Aktuel kanal (standard): Hold dig opdateret automatisk under den gradvise udgivelsescyklus. Passer til de fleste enheder.|
|

### <a name="update-channels-for-daily-updates"></a>Opdater kanaler til daglige opdateringer

Du kan også tildele en maskine til en kanal for at definere den kadence, som den modtager daglige opdateringer i. Bemærk, at til forskel fra den månedlige proces er der ingen Beta-kanal, og denne gradvise udgivelsescyklus forekommer flere gange om dagen.

<br>

****

|Kanalnavn|Beskrivelse|Program|
|---|---|---|
|Aktuel kanal (faseret)|Få opdateringer til aktuel kanal senere i løbet af den gradvise udgivelse|Enheder vil blive tilbudt opdateringer senere i løbet af den gradvise udgivelsescyklus. Foreslået til at gælde for en lille, repræsentativ del af din enheds population (~10 %).|
|Aktuel kanal (bred)|Hent opdateringer ved slutningen af den gradvise udgivelse|Enheder tilbydes opdateringer efter den gradvise udgivelsescyklus. Bedst til datacenter maskiner, der kun modtager begrænsede opdateringer. Bemærk! Denne indstilling gælder for alle Defender-opdateringer.|
|(standard)||Hvis du deaktiverer eller ikke konfigurerer denne politik, forbliver enheden i Aktuel kanal (standard): Hold dig opdateret automatisk under den gradvise udgivelsescyklus. Passer til de fleste enheder|
|

> [!NOTE]
> Hvis du vil gennemtvinge en opdatering til den nyeste signatur i stedet for at udnytte tidsforsinkelsen, skal du fjerne denne politik først.

## <a name="update-guidance"></a>Opdater vejledning

I de fleste tilfælde er den anbefalede konfiguration ved brug af Windows Update at tillade slutpunkter at modtage og anvende månedlige Defender-opdateringer, når de modtages. Dette giver den bedste balance mellem beskyttelse og den mulige virkning, der er knyttet til de ændringer, de kan introducere.

I miljøer, hvor der er brug for en mere kontrolleret gradvis udrulning af automatiske Defender-opdateringer, bør du overveje en tilgang med installationsgrupper:

1. Deltag i programmet Windows Insider, eller tildel en gruppe enheder til Beta-kanalen.
2. Udpek en pilotgruppe, der tilmelder sig Preview-kanalen, typisk valideringsmiljøer, for at modtage nye opdateringer tidligt.
3. Angiv en gruppe af maskiner, der modtager opdateringer senere under den gradvise udrulning fra faseopdelagt kanal. Dette vil typisk være en repræsentativ ~10 % af populationen.
4. Angiv en gruppe af maskiner, der skal modtage opdateringer, når den gradvise udgivelsescyklus er fuldført. Disse er typisk vigtige produktionssystemer.

For resten af enheder er standardindstillingen at modtage nye opdateringer, når de modtages under Microsofts gradvise implementeringsproces, og der kræves ikke yderligere konfiguration.

Indføre denne model:

- Giver dig mulighed for at teste tidlige udgivelser, før de når et produktionsmiljø
- Sørg for, at produktionsmiljøet stadig modtager regelmæssige opdateringer og er beskyttet mod kritiske trusler.

## <a name="management-tools"></a>Administrationsværktøjer

Hvis du vil oprette din egen brugerdefinerede gradvise implementeringsproces for månedlige opdateringer, kan du bruge følgende værktøjer:

- Gruppepolitik
- Microsoft Endpoint Manager
- PowerShell

Hvis du vil have mere at vide om, hvordan du bruger disse værktøjer, [skal du se Opret en brugerdefineret gradvis udrulningsproces til Microsoft Defender-opdateringer](configure-updates.md).
