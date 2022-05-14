---
title: Administrer den gradvise udrulningsproces for Microsoft Defender-opdateringer
description: Få mere at vide om processen og kontrolelementerne for gradvis opdatering
keywords: opdatering, opdateringsproces, kontrolelementer, udgivelse
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
ms.openlocfilehash: 8f1f2add8196afef6e8bd738586957d7fea15c84
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416326"
---
# <a name="manage-the-gradual-rollout-process-for-microsoft-defender-updates"></a>Administrer den gradvise udrulningsproces for Microsoft Defender-opdateringer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Det er vigtigt at sikre, at klientkomponenter er opdaterede til at levere vigtige beskyttelsesfunktioner og forhindre angreb.

Funktioner leveres via flere komponenter:

- [Slutpunktsregistrering & svar](overview-endpoint-detection-response.md)
- [Næste generations beskyttelse](microsoft-defender-antivirus-windows.md) med [cloudbaseret beskyttelse](cloud-protection-microsoft-defender-antivirus.md)
- [Reduktion af angrebsoverflade](overview-attack-surface-reduction.md)

Opdateringer udgives månedligt ved hjælp af en gradvis udgivelsesproces. Denne proces hjælper med at gøre det muligt at registrere tidlige fejl for at registrere indvirkningen, efterhånden som den opstår, og håndtere den hurtigt før en større udrulning.

> [!NOTE]
> Du kan få flere oplysninger om, hvordan du styrer daglige opdateringer af sikkerhedsintelligens, under [Planlæg Microsoft Defender Antivirus beskyttelsesopdateringer](manage-protection-update-schedule-microsoft-defender-antivirus.md). Opdateringer sikrer, at næste generations beskyttelse kan forsvare sig mod nye trusler, selvom cloudbaseret beskyttelse ikke er tilgængelig for slutpunktet.

## <a name="microsoft-gradual-rollout-model"></a>Microsofts gradvise udrulningsmodel

Følgende gradvise udrulningsmodel følges for månedlige Defender-opdateringer:

1. Den første version går ud til betakanalabonnenter.
2. Efter validering, feedback og rettelser starter vi den gradvise udrulningsproces på en begrænset måde og først for at få vist kanalabonnenter.
3. Derefter udgiver vi opdateringen til resten af den globale befolkning med udskalering fra 10-100 %.

Vores teknikere overvåger løbende indvirkningen og eskalerer eventuelle problemer for at oprette en løsning efter behov.

## <a name="how-to-customize-your-internal-deployment-process"></a>Sådan tilpasser du din interne installationsproces

Hvis dine maskiner modtager Defender-opdateringer fra Windows Update, kan den gradvise udrulningsproces medføre, at nogle af dine maskiner modtager Defender-opdateringer hurtigere end andre. I følgende afsnit forklares det, hvordan du definerer en strategi, der gør det muligt for automatiske opdateringer at flyde anderledes til bestemte grupper af enheder ved at udnytte konfigurationen af opdateringskanalen.

> [!NOTE]
> Når du planlægger din egen gradvise udgivelse, skal du sørge for altid at have et udvalg af enheder, der abonnerer på prøveversions- og fasekanaler. Dette giver din organisation samt Microsoft mulighed for at forhindre eller finde og løse problemer, der er specifikke for dit miljø.

For maskiner, der modtager opdateringer via f.eks. Windows Server Update Services (WSUS) eller Microsoft Endpoint Configuration Manager (MECM), er der flere muligheder tilgængelige for alle Windows opdateringer, herunder muligheder for Microsoft Defender for Endpoint.

- Læs mere om, hvordan du bruger en løsning som WSUS, MECM til at administrere distributionen og anvendelsen af opdateringer på [Administrer Microsoft Defender Antivirus opdateringer og anvende grundlinjer – Windows sikkerhed](manage-updates-baselines-microsoft-defender-antivirus.md#product-updates).

## <a name="update-channels-for-monthly-updates"></a>Opdater kanaler for månedlige opdateringer

Du kan tildele en maskine til en opdateringskanal for at definere den kadence, som en maskine modtager månedlige program- og platformopdateringer i.

Du kan få flere oplysninger om, hvordan du konfigurerer opdateringer, under [Opret en brugerdefineret gradvis udrulningsproces for Microsoft Defender-opdateringer](configure-updates.md).

Følgende opdateringskanaler er tilgængelige:

<br>

****

|Kanalnavn|Beskrivelse|Program|
|---|---|---|
|Betakanal – forhåndsudgivelse|Test opdateringer før andre|Enheder, der er angivet til denne kanal, er de første til at modtage nye månedlige opdateringer. Vælg Beta Channel for at deltage i identificering og rapportering af problemer til Microsoft. Enheder i Windows Insider Program abonneres som standard på denne kanal. Kun til brug i testmiljøer.|
|Aktuel kanal (prøveversion)|Hent aktuelle kanalopdateringer **tidligere** under gradvis frigivelse|Enheder, der er angivet til denne kanal, tilbydes opdateringer tidligst under den gradvise udgivelsescyklus. Foreslået til præproduktions-/valideringsmiljøer.|
|Aktuel kanal (faset)|Hent aktuelle kanalopdateringer senere under gradvis frigivelse|Enheder tilbydes opdateringer senere under den gradvise udgivelsescyklus. Foreslået at anvende på en lille, repræsentativ del af enhedens population (~10 %).|
|Aktuel kanal (bred)|Hent opdateringer i slutningen af gradvis frigivelse|Enheder tilbydes kun opdateringer, når den gradvise udgivelsescyklus er fuldført. Foreslået at anvende på et bredt sæt enheder i din produktionspopulation (~10-100%).|
|Kritisk: Tidsforsinkelse|Forsinkelse af defender-opdateringer|Enheder tilbydes opdateringer med en 48-timers forsinkelse. Bedst til datacentermaskiner, der kun modtager begrænsede opdateringer. Kun foreslået til kritiske miljøer.|
|(standard)||Hvis du deaktiverer eller ikke konfigurerer denne politik, forbliver enheden i aktuel kanal (standard): Hold dig automatisk opdateret under den gradvise udgivelsescyklus. Egnet til de fleste enheder.|
|

### <a name="update-channels-for-daily-updates"></a>Opdater kanaler for daglige opdateringer

Du kan også tildele en maskine til en kanal for at definere den kadence, som den modtager daglige opdateringer i. Bemærk, at i modsætning til den månedlige proces er der ingen Beta-kanal, og denne gradvise udgivelsescyklus forekommer flere gange om dagen.

<br>

****

|Kanalnavn|Beskrivelse|Program|
|---|---|---|
|Aktuel kanal (faset)|Hent aktuelle kanalopdateringer senere under gradvis frigivelse|Enheder tilbydes opdateringer senere under den gradvise udgivelsescyklus. Foreslået at anvende på en lille, repræsentativ del af enhedens population (~10 %).|
|Aktuel kanal (bred)|Hent opdateringer i slutningen af gradvis frigivelse|Enheder tilbydes opdateringer efter den gradvise udgivelsescyklus. Bedst til datacentermaskiner, der kun modtager begrænsede opdateringer. Bemærk! Denne indstilling gælder for alle Defender-opdateringer.|
|(standard)||Hvis du deaktiverer eller ikke konfigurerer denne politik, forbliver enheden i aktuel kanal (standard): Hold dig automatisk opdateret under den gradvise udgivelsescyklus. Egnet til de fleste enheder|
|

> [!NOTE]
> Hvis du vil gennemtvinge en opdatering til den nyeste signatur i stedet for at udnytte tidsforsinkelsen, skal du først fjerne denne politik.

## <a name="update-guidance"></a>Vejledning til opdatering

I de fleste tilfælde er den anbefalede konfiguration, når du bruger Windows Update, at tillade slutpunkter at modtage og anvende månedlige Defender-opdateringer, når de ankommer. Dette giver den bedste balance mellem beskyttelse og mulig indvirkning, der er forbundet med de ændringer, de kan medføre.

I de miljøer, hvor der er behov for en mere kontrolleret gradvis udrulning af automatiske Defender-opdateringer, bør du overveje en tilgang med udrulningsgrupper:

1. Deltag i Windows Insider-programmet, eller tildel en gruppe enheder til betakanalen.
2. Angiv en pilotgruppe, der tilmelder sig eksempelkanalen, typisk valideringsmiljøer, for at modtage nye opdateringer tidligt.
3. Angiv en gruppe computere, der modtager opdateringer senere under den gradvise udrulning fra kanalen Staged. Dette vil typisk være en repræsentativ ~10 % af befolkningen.
4. Angiv en gruppe computere, der modtager opdateringer, når den gradvise udgivelsescyklus er fuldført. Disse er typisk vigtige produktionssystemer.

For resten af enhederne er standardindstillingen at modtage nye opdateringer, når de modtages under Microsofts gradvise udrulningsproces, og der kræves ingen yderligere konfiguration.

Brug af denne model:

- Giver dig mulighed for at teste tidlige udgivelser, før de når et produktionsmiljø
- Sørg for, at produktionsmiljøet stadig modtager regelmæssige opdateringer, og sørg for beskyttelse mod kritiske trusler.

## <a name="management-tools"></a>Administrationsværktøjer

Hvis du vil oprette din egen brugerdefinerede gradvise udrulningsproces for månedlige opdateringer, kan du bruge følgende værktøjer:

- Gruppepolitik
- Microsoft Endpoint Manager
- PowerShell

Du kan finde oplysninger om, hvordan du bruger disse værktøjer, under [Opret en brugerdefineret gradvis udrulningsproces for Microsoft Defender-opdateringer](configure-updates.md).

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)