---
title: Cloudbeskyttelse og eksempelindsendelse på Microsoft Defender Antivirus
description: Få mere at vide om skybaseret beskyttelse og Microsoft Defender Antivirus
keywords: Microsoft Defender Antivirus, næste generations teknologier, indsendelse af antiviruseksemplet, næste generation af av, maskinel indlæring, antimalware, sikkerhed, defender, cloud, cloudbaseret beskyttelse
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 02/24/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 08f8e0c861bfd19f11c5b011d0a8db41ce3e73bc
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419940"
---
# <a name="cloud-protection-and-sample-submission-at-microsoft-defender-antivirus"></a>Cloudbeskyttelse og eksempelindsendelse på Microsoft Defender Antivirus

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

Microsoft Defender Antivirus bruger mange intelligente mekanismer til at opdage malware. En af de mest effektive funktioner er muligheden for at anvende styrken i skyen til at registrere malware og udføre hurtige analyser. Cloudbeskyttelse og automatisk indsendelse af eksempler arbejder sammen med Microsoft Defender Antivirus for at beskytte mod nye og nye trusler. 

Hvis der registreres en mistænkelig eller skadelig fil, sendes der et eksempel til cloudtjenesten til analyse, mens Microsoft Defender Antivirus blokerer filen. Så snart der er foretaget en bestemmelse, hvilket sker hurtigt, frigives filen enten eller blokeres af Microsoft Defender Antivirus. 

Denne artikel indeholder en oversigt over cloudbeskyttelse og automatisk indsendelse af eksempler på Microsoft Defender Antivirus. Du kan få mere at vide om cloudbeskyttelse under [Cloudbeskyttelse og Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md).

## <a name="how-cloud-protection-and-sample-submission-work-together"></a>Sådan arbejder cloudbeskyttelse og eksempelindsendelse sammen

For at forstå, hvordan cloudbeskyttelse fungerer sammen med eksempelindsendelse, kan det være nyttigt at forstå, hvordan Defender for Endpoint beskytter mod trusler. Microsoft Intelligent Security Graph overvåger trusselsdata fra et stort netværk af sensorer. Microsoft lager cloudbaserede modeller til maskinel indlæring, der kan vurdere filer baseret på signaler fra klienten og det enorme netværk af sensorer og data i Graph intelligent sikkerhed. Denne fremgangsmåde giver Defender for Endpoint mulighed for at blokere mange aldrig før sete trusler. 

På følgende billede vises flowet for cloudbeskyttelse og eksempelindsendelse med Microsoft Defender Antivirus:

:::image type="content" source="images/cloud-protection-flow.png" alt-text="Skybaseret beskyttelsesflow" lightbox="images/cloud-protection-flow.png":::

Microsoft Defender Antivirus og cloudbeskyttelse blokerer automatisk de fleste nye aldrig før sete trusler ved første øjekast ved hjælp af følgende metoder:

1. Letvægtsklientbaserede modeller til maskinel indlæring, der blokerer ny og ukendt malware.

2. Lokal adfærdsanalyse, der stopper filbaserede og filfri angreb.

3. Højpræcision antivirus, registrering af almindelig malware gennem generiske og heuristiske teknikker.

4. Avanceret skybaseret beskyttelse leveres i tilfælde, hvor Microsoft Defender Antivirus, der kører på slutpunktet, har brug for mere intelligens for at bekræfte hensigten med en mistænkelig fil.

   1. Hvis Microsoft Defender Antivirus ikke kan foretage en klar bestemmelse, sendes filmetadata til cloudbeskyttelsestjenesten. Cloudbeskyttelsestjenesten kan ofte inden for millisekunder afgøre, om filen er skadelig eller ej, baseret på metadataene.  

      - Cloudforespørgslen for filmetadata kan være et resultat af funktionsmåde, webmærker eller andre egenskaber, hvor der ikke er fastlagt en klar dom.
      - Der sendes en lille metadatanyttedata med det formål at nå frem til en dom over malware eller ikke en trussel. Metadataene indeholder ikke personidentificerbare oplysninger. Oplysninger som f.eks. filnavne hashkodes.
      - Kan være synkron eller asynkron. Hvis filen er synkron, åbnes den først, når skyen har afsagt en dom. Hvis filen er asynkron, åbnes den, mens cloudbeskyttelse udfører analysen.
      - Metadata kan omfatte PE-attributter, statiske filattributter, dynamiske og kontekstafhængige attributter m.m. (se [Eksempler på metadata, der er sendt til cloudbeskyttelsestjenesten](#examples-of-metadata-sent-to-the-cloud-protection-service)).

   2. Hvis Microsoft Defender Antivirus cloudbeskyttelse efter undersøgelse af metadataene ikke kan nå frem til en afgørende dom, kan den anmode om en stikprøve af filen til yderligere inspektion. Denne anmodning imødekommer konfigurationen af indstillingerne for indsendelse af eksempel:

      1. **Send automatisk sikre eksempler** (standard)
         - Pengeskab eksempler er eksempler, der anses for ikke at indeholde pii-data som f.eks.: .bat, .scr, .dll .exe.
         - Hvis filen sandsynligvis indeholder pii, får brugeren en anmodning om at tillade indsendelse af fileksempel.
         - Denne indstilling er standard på Windows, macOS og Linux.

      2. **Spørg altid**
         - Hvis den er konfigureret, bliver brugeren altid bedt om samtykke, før filen indsendes
         - Denne indstilling er ikke tilgængelig i macOS cloudbeskyttelse

      3. **Send alle eksempler automatisk**
         - Hvis den er konfigureret, sendes alle eksempler automatisk
         - Hvis du vil medtage makroer, der er integreret i Word-dokumenter, skal du vælge "Send alle eksempler automatisk"
         - Denne indstilling er ikke tilgængelig i macOS cloudbeskyttelse

      4. **Send ikke**
         - Forhindrer "blok ved første øjekast" baseret på fileksempelanalyse
         - "Send ikke" svarer til indstillingen "Deaktiveret" i macOS politik
         - Metadata sendes til registreringer, selvom eksempelafsendelse er deaktiveret

   3. Når metadata og/eller filer er sendt til cloudbeskyttelse, kan du bruge **eksempler**, **detonation** eller modeller til maskinel indlæring **til analyse af big data** for at nå frem til en dom. Hvis du deaktiverer skybaseret beskyttelse, begrænses analysen til kun at være det, klienten kan levere via lokale modeller til maskinel indlæring og lignende funktioner.

> [!IMPORTANT]
> [BAFS (Block ved første øjekast)](configure-block-at-first-sight-microsoft-defender-antivirus.md) giver detonation og analyse til at afgøre, om en fil eller proces er sikker. BAFS kan udskyde åbningen af en fil midlertidigt, indtil en dom er nået. Hvis du deaktiverer eksempelindsendelse, deaktiveres BAFS også, og filanalyse er begrænset til kun metadata. Vi anbefaler, at eksempelindsendelse og BAFS er aktiveret. Du kan få mere at vide under [Hvad er "blok ved første øjekast"?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)

## <a name="cloud-protection-levels"></a>Skybeskyttelsesniveauer

Cloudbeskyttelse er som standard aktiveret ved Microsoft Defender Antivirus. Vi anbefaler, at du holder cloudbeskyttelse aktiveret, selvom du kan konfigurere beskyttelsesniveauet for din organisation. Se [Angiv det skybaserede beskyttelsesniveau for Microsoft Defender Antivirus](specify-cloud-protection-level-microsoft-defender-antivirus.md).

## <a name="sample-submission-settings"></a>Indstillinger for eksempelindsendelse

Ud over at konfigurere dit cloudbeskyttelsesniveau kan du konfigurere indstillingerne for indsendelse af eksempler. Du kan vælge mellem flere indstillinger:

- **Send automatisk sikre eksempler**  (standardfunktionsmåden)
- **Send alle eksempler automatisk**  
- **Send ikke eksempler**  

Du kan få oplysninger om konfigurationsindstillinger ved hjælp af Intune, Configuration Manager, GPO eller PowerShell under [Slå skybeskyttelse til på Microsoft Defender Antivirus](enable-cloud-protection-microsoft-defender-antivirus.md).

## <a name="examples-of-metadata-sent-to-the-cloud-protection-service"></a>Eksempler på metadata, der er sendt til cloudbeskyttelsestjenesten

:::image type="content" source="images/cloud-protection-metadata-sample.png" alt-text="Eksemplerne på metadata, der sendes til cloudbeskyttelse på Microsoft Defender Antivirus-portalen" lightbox="images/cloud-protection-metadata-sample.png":::

I følgende tabel vises eksempler på metadata, der er sendt til analyse af cloudbeskyttelse:

| Type | Attribut |
|:---|:---|
| Computerattributter | `OS version` <br/> `Processor` <br/> `Security settings` |
| Dynamiske og kontekstafhængige attributter | **Proces og installation** <br/> `ProcessName` <br/> `ParentProcess` <br/> `TriggeringSignature` <br/> `TriggeringFile` <br/> `Download IP and url` <br/> `HashedFullPath` <br/> `Vpath` <br/> `RealPath` <br/> `Parent/child relationships` <br/><br/>**Adfærdsmæssige** <br/> `Connection IPs` <br/> `System changes` <br/> `API calls` <br/> `Process injection` <br/><br/>**Landestandard** <br/> `Locale setting` <br/> `Geographical location` |
| Statiske filattributter | **Delvise og fulde hashværdier** <br/> `ClusterHash` <br/> `Crc16` <br/> `Ctph` <br/> `ExtendedKcrcs` <br/> `ImpHash` <br/> `Kcrc3n` <br/> `Lshash` <br/> `LsHashs` <br/> `PartialCrc1` <br/> `PartialCrc2` <br/> `PartialCrc3` <br/> `Sha1` <br/> `Sha256` <br/><br/>**Filegenskaber** <br/>`FileName` <br/> `FileSize` <br/><br/> **Underskriveroplysninger** <br/> `AuthentiCodeHash` <br/> `Issuer` <br/> `IssuerHash` <br/> `Publisher` <br/> `Signer` <br/> `SignerHash` |

## <a name="samples-are-treated-as-customer-data"></a>Eksempler behandles som kundedata

Hvis du undrer dig over, hvad der sker med eksempelindsendelser, behandler Defender for Endpoint alle fileksempler som kundedata. Microsoft hædr både de geografiske og dataopbevaringsvalg, som din organisation har valgt, når du onboarder til Defender for Endpoint. 

Derudover har Defender for Endpoint modtaget flere certificeringer af overholdelse af angivne standarder og demonstreret fortsat overholdelse af et avanceret sæt kontrolfunktioner til overholdelse af angivne standarder:

- ISO 27001
- ISO 27018
- SOC I, II, III
- PCI

Du kan få flere oplysninger i følgende ressourcer:

- [Azure Compliance-tilbud](/azure/storage/common/storage-compliance-offerings) 
- [Service Trust Portal](https://servicetrust.microsoft.com)
- [Microsoft Defender for Endpoint datalager og beskyttelse af personlige oplysninger](data-storage-privacy.md#data-storage-location)

## <a name="other-file-sample-submission-scenarios"></a>Andre scenarier for indsendelse af fileksempel

Der er to scenarier mere, hvor Defender for Endpoint kan anmode om et fileksempel, der ikke er relateret til cloudbeskyttelsen på Microsoft Defender Antivirus. Disse scenarier er beskrevet i følgende tabel:

| Scenario | Beskrivelse |
|:---|:---|
|Manuel fileksempelsamling på Microsoft 365 Defender-portalen | Når du onboarder enheder til Defender for Endpoint, kan du konfigurere indstillinger for [slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar)](overview-endpoint-detection-response.md). Der er f.eks. en indstilling til aktivering af eksempelsamlinger fra enheden, som nemt kan forveksles med de indstillinger for indsendelse af eksempel, der er beskrevet i denne artikel. <br/><br/>Indstillingen Slutpunktsregistrering og -svar styrer indsamling af fileksempler fra enheder, når der anmodes om det via Microsoft 365 Defender-portalen, og den er underlagt de roller og tilladelser, der allerede er oprettet. Denne indstilling kan tillade eller blokere filsamling fra slutpunktet for funktioner som dyb analyse på Microsoft 365 Defender-portalen. Hvis denne indstilling ikke er konfigureret, er standarden at aktivere eksempelsamling. <br/><br/>Få mere at vide om konfigurationsindstillinger for Defender for Endpoint under: [Onboarding-værktøjer og -metoder til Windows 10 enheder i Defender for Endpoint](configure-endpoints.md) |
| Automatiseret undersøgelse og analyse af svarindhold | Når [automatiserede undersøgelser](automated-investigations.md) kører på enheder (når de er konfigureret til at køre automatisk som svar på en besked eller manuelt kørsel), kan filer, der er identificeret som mistænkelige, indsamles fra slutpunkterne for yderligere inspektion. Hvis det er nødvendigt, kan funktionen til filindholdsanalyse for automatiserede undersøgelser deaktiveres på Microsoft 365 Defender-portalen. <br/><br/> Filtypenavnene kan også ændres for at tilføje eller fjerne filtypenavne for andre filtyper, der sendes automatisk under en automatisk undersøgelse. <br/><br/> Du kan få mere at vide under [Administrer automatiske filoverførsler](manage-automation-file-uploads.md). |

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, kan du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)

## <a name="see-also"></a>Se også

[Oversigt over næste generations beskyttelse](next-generation-protection.md)

[Konfigurer afhjælpning for Microsoft Defender Antivirus registreringer.](configure-remediation-microsoft-defender-antivirus.md)
