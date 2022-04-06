---
title: Skybeskyttelse og indsendelse af eksempler på Microsoft Defender Antivirus
description: Få mere at vide om beskyttelse og beskyttelse i skyen Microsoft Defender Antivirus
keywords: Microsoft Defender Antivirus, næste generations teknologier, indsendelse af antiviruseksempel, næste generations av, maskinlæring, antimalware, sikkerhed, defender, skybaseret beskyttelse leveret i skyen
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
ms.openlocfilehash: a647617de3706481c2e12f4e1772f5bc609db6fc
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470675"
---
# <a name="cloud-protection-and-sample-submission-at-microsoft-defender-antivirus"></a>Skybeskyttelse og indsendelse af eksempler på Microsoft Defender Antivirus

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

Microsoft Defender Antivirus bruger mange intelligente mekanismer til at registrere malware. En af de mest effektive funktioner er muligheden for at anvende skyens styrke til at registrere malware og foretage hurtige analyser. Cloud protection and automatic sample submission work together with Microsoft Defender Antivirus to help protect against new and emerging threats. 

Hvis der registreres en mistænkelig eller skadelig fil, sendes en prøve til analyse i skytjenesten, Microsoft Defender Antivirus filer blokeres. Så snart der foretages en bestemmelse, som sker hurtigt, frigives eller blokeres filen enten af Microsoft Defender Antivirus. 

Denne artikel indeholder en oversigt over skybeskyttelse og automatisk indsendelse af eksempler på Microsoft Defender Antivirus. Du kan få mere at vide om [skybeskyttelse under Skybeskyttelse og Microsoft Defender Antivirus](cloud-protection-microsoft-defender-antivirus.md).

## <a name="how-cloud-protection-and-sample-submission-work-together"></a>Sådan fungerer skybeskyttelse og indsendelse af eksempler sammen

For at forstå, hvordan skybeskyttelse fungerer sammen med indsendelse af eksempler, kan det være nyttigt at forstå, hvordan Defender til Slutpunkt beskytter mod trusler. Microsoft Intelligent Security-Graph overvåger trusselsdata fra et enormt netværk af sensorer. Microsoft lag skybaserede maskinlæringsmodeller, der kan vurdere filer baseret på signaler fra klienten og det enorme netværk af sensorer og data i den intelligente sikkerhedsmodel Graph. Denne fremgangsmåde giver Defender til Slutpunkt mulighed for at blokere for mange aldrig før så trusler. 

Følgende billede afbilder strømmen af beskyttelse i skyen og eksempelindsendelse med Microsoft Defender Antivirus:

:::image type="content" source="images/cloud-protection-flow.png" alt-text="Cloud-leveret beskyttelse flow" lightbox="images/cloud-protection-flow.png":::

Microsoft Defender Antivirus og skybeskyttelse blokerer automatisk de fleste nye, aldrig før så store trusler ved første syn ved hjælp af følgende metoder:

1. Lette klientbaserede modeller til maskinel indlæring, der blokerer for ny og ukendt malware.

2. Lokal adfærdsanalyse, stopper filbaserede og filfri angreb.

3. Antivirus med høj præcision, registrering af almindelige malware ved hjælp af generiske og heuristiske teknikker.

4. Avanceret skybaseret beskyttelse leveres til tilfælde, Microsoft Defender Antivirus brugere, der kører på slutpunktet, har brug for mere intelligens for at bekræfte formålet med en mistænkelig fil.

   1. I tilfælde af Microsoft Defender Antivirus der ikke kan træffe en klar bestemmelse, sendes der filmetadata til skybeskyttelsestjenesten. Ofte i millisekunder kan skybeskyttelsestjenesten afgøre ud fra metadataene, om filen er skadelig eller ej en trussel.  

      - Skyforespørgslen om filmetadata kan være et resultat af funktionsmåde, markering af internettet eller andre egenskaber, hvor der ikke bestemmes en tydelig vurdering.
      - Der sendes en lille nyttedata af metadata med det formål at nå en vurdering af malware eller ikke en trussel. Metadataene omfatter ikke personlige oplysninger (PII). Oplysninger som filnavne er blevet gemt.
      - Kan være synkron eller asynkron. Ved synkroniseret åbnes filen ikke, før skyen gengiver en konklusion. Ved asynkron åbning åbnes filen, mens skybeskyttelse udfører sin analyse.
      - Metadata kan omfatte PE-attributter, statiske filattributter, dynamiske og kontekstafhængige attributter og meget mere (se Eksempler på metadata, der [sendes til skybeskyttelsestjenesten](#examples-of-metadata-sent-to-the-cloud-protection-service)).

   2. Efter at have undersøgt metadataene kan Microsoft Defender Antivirus skybeskyttelse ikke nå frem til en konsonens konklusion, kan den anmode om en stikprøve af filen til yderligere undersøgelse. Denne anmodning imødekommer indstillingerne for eksempelindsendelse:

      1. **Send sikre eksempler automatisk** (standard)
         - Pengeskab eksempler betragtes som eksempler, der ikke ofte indeholder pii-data som f.eks.: .bat, .scr, .dll, .exe.
         - Hvis filen sandsynligvis indeholder PII, får brugeren en anmodning om at tillade indsendelse af fileksempel.
         - Denne indstilling er standardindstillingen på Windows, macOS og Linux.

      2. **Spørg altid**
         - Hvis konfigureret, vil brugeren altid blive bedt om samtykke før indsendelse af filen
         - Denne indstilling er ikke tilgængelig i macOS-skybeskyttelse

      3. **Send alle eksempler automatisk**
         - Hvis det er konfigureret, sendes alle eksempler automatisk
         - Hvis du vil have, at eksempelindsendelse omfatter makroer, der er integreret i Word-dokumenter, skal du vælge "Send alle eksempler automatisk"
         - Denne indstilling er ikke tilgængelig på macOS-skybeskyttelse

      4. **Send ikke**
         - Forhindrer "blok ved første syn" baseret på fileksempelanalyse
         - "Send ikke" svarer til indstillingen "Deaktiveret" i macOS-politik
         - Metadata sendes til registreringer, selv når eksempelindsendelse er deaktiveret

   3. Når metadata og/eller filer er blevet indsendt til skybeskyttelse, kan du bruge **eksempler,** **detonation** eller modeller til maskinlæring af store **dataanalyser** for at opnå en konklusion. Hvis du slår beskyttelse i skyen fra, begrænses analyser til kun det, klienten kan levere via lokale maskinlæringsmodeller og lignende funktioner.

> [!IMPORTANT]
> [Bloker ved første syn (BAFS) giver](configure-block-at-first-sight-microsoft-defender-antivirus.md) detonation og analyse til at afgøre, om en fil eller proces er sikker. BAFS kan forsinke åbning af en fil kortvarigt, indtil der opnås en konklusion. Hvis du deaktiverer eksempelindsendelse, deaktiveres BAFS også, og filanalyse er begrænset til kun metadata. Vi anbefaler, at du holder eksempelindsendelse og BAFS aktiveret. Du kan få mere at vide [under Hvad er "blok ved første syn"?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)

## <a name="cloud-protection-levels"></a>Skybeskyttelsesniveauer

Skybeskyttelse er som standard aktiveret Microsoft Defender Antivirus. Vi anbefaler, at du holder skybeskyttelse aktiveret, selvom du kan konfigurere beskyttelsesniveauet for din organisation. Se [Angive beskyttelsesniveauet, der leveres i skyen, for Microsoft Defender Antivirus](specify-cloud-protection-level-microsoft-defender-antivirus.md).

## <a name="sample-submission-settings"></a>Eksempel på indstillinger for indsendelse

Ud over at konfigurere dit skybeskyttelsesniveau kan du konfigurere dine eksempelindsendelsesindstillinger. Du kan vælge mellem flere forskellige muligheder:

- **Send sikre eksempler automatisk**  (standardfunktionsmåden)
- **Send alle eksempler automatisk**  
- **Send ikke eksempler**  

Du kan finde oplysninger om konfigurationsindstillinger ved Intune, Configuration Manager, gruppepolitikobjekt eller PowerShell under Aktiver [skybeskyttelse Microsoft Defender Antivirus](enable-cloud-protection-microsoft-defender-antivirus.md).

## <a name="examples-of-metadata-sent-to-the-cloud-protection-service"></a>Eksempler på metadata, der sendes til skybeskyttelsestjenesten

:::image type="content" source="images/cloud-protection-metadata-sample.png" alt-text="Eksempler på metadata, der sendes til skybeskyttelse i Microsoft Defender Antivirus-portalen" lightbox="images/cloud-protection-metadata-sample.png":::

I følgende tabel vises eksempler på metadata, der er sendt til analyse af skybeskyttelse:

| Type | Attribut |
|:---|:---|
| Computerattributter | `OS version` <br/> `Processor` <br/> `Security settings` |
| Dynamiske og kontekstafhængige attributter | **Proces og installation** <br/> `ProcessName` <br/> `ParentProcess` <br/> `TriggeringSignature` <br/> `TriggeringFile` <br/> `Download IP and url` <br/> `HashedFullPath` <br/> `Vpath` <br/> `RealPath` <br/> `Parent/child relationships` <br/><br/>**Funktionsmåde** <br/> `Connection IPs` <br/> `System changes` <br/> `API calls` <br/> `Process injection` <br/><br/>**Landepolitik** <br/> `Locale setting` <br/> `Geographical location` |
| Statiske filattributter | **Delvise og fulde hashes** <br/> `ClusterHash` <br/> `Crc16` <br/> `Ctph` <br/> `ExtendedKcrcs` <br/> `ImpHash` <br/> `Kcrc3n` <br/> `Lshash` <br/> `LsHashs` <br/> `PartialCrc1` <br/> `PartialCrc2` <br/> `PartialCrc3` <br/> `Sha1` <br/> `Sha256` <br/><br/>**Filegenskaber** <br/>`FileName` <br/> `FileSize` <br/><br/> **Oplysninger om underskriver** <br/> `AuthentiCodeHash` <br/> `Issuer` <br/> `IssuerHash` <br/> `Publisher` <br/> `Signer` <br/> `SignerHash` |

## <a name="samples-are-treated-as-customer-data"></a>Eksempler behandles som kundedata

Hvis du undrer dig over, hvad der sker med prøveindsendelser, behandler Defender til slutpunkt alle fileksempler som kundedata. Microsoft imødekommer både det geografiske valg og de valg, din organisation har valgt, når du onboarder til Defender til slutpunkt. 

Derudover har Defender til Endpoint modtaget flere kompatibilitetscertificeringer og viser fortsat overholdelse af et avanceret sæt kontrolfunktioner til overholdelse af regler og standarder:

- ISO 27001
- ISO 27018
- SOC I, II, III
- 1. 1

Du kan finde flere oplysninger i følgende ressourcer:

- [Azure Compliance Offerings](/azure/storage/common/storage-compliance-offerings) 
- [Service Trust Portal](https://servicetrust.microsoft.com)
- [Microsoft Defender for Endpoint datalagring og beskyttelse af personlige oplysninger](data-storage-privacy.md#data-storage-location)

## <a name="other-file-sample-submission-scenarios"></a>Andre scenarier for indsendelse af filekseler

Der er to scenarier mere, hvor Defender til Slutpunkt muligvis anmoder om en filprøve, der ikke er relateret til skybeskyttelsen Microsoft Defender Antivirus. Disse scenarier er beskrevet i følgende tabel:

| Scenarie | Beskrivelse |
|:---|:---|
|Manuel samling af filekse prøve i Microsoft 365 Defender portalen | Når onboardingenheder er på Defender til Slutpunkt, kan du konfigurere indstillingerne for [slutpunktsregistrering og -svar (Slutpunktsregistrering og -svar)](overview-endpoint-detection-response.md). Der er f.eks. en indstilling, der gør det muligt at aktivere eksempler på samlinger fra enheden, som nemt kan forveksles med de eksempelindstillinger for indsendelse, der er beskrevet i denne artikel. <br/><br/>Indstillingen Slutpunktsregistrering og -svar styrer indsamling af filer fra enheder, når der anmodes om det via Microsoft 365 Defender-portalen, og er underlagt de roller og tilladelser, der allerede er oprettet. Denne indstilling kan tillade eller blokere filsamling fra slutpunktet for funktioner som dybdegående analyse i Microsoft 365 Defender portal. Hvis denne indstilling ikke er konfigureret, er standardindstillingen at aktivere eksempelsamling. <br/><br/>Få mere at vide om konfigurationsindstillinger for Defender til Slutpunkt under: [Onboardingværktøjer og metoder til Windows 10 enheder i Defender til Slutpunkt](configure-endpoints.md) |
| Automatiseret undersøgelse og svarindholdsanalyse | Når [automatiserede](automated-investigations.md) undersøgelser kører på enheder (når de er konfigureret til at køre automatisk som svar på en besked eller køres manuelt), kan filer, der identificeres som mistænkelige, indsamles fra slutpunkterne til yderligere undersøgelse. Hvis det er nødvendigt, kan funktionen til analyse af filindhold til automatiserede undersøgelser deaktiveres i Microsoft 365 Defender portal. <br/><br/> Filtypenavnene kan også ændres for at tilføje eller fjerne filtypenavne for andre filtyper, der vil blive sendt automatisk under en automatisk undersøgelse. <br/><br/> Du kan få mere at vide [under Administrer automatiske filuploads](manage-automation-file-uploads.md). |

## <a name="see-also"></a>Se også

[Oversigt over næste generations beskyttelse](next-generation-protection.md)

[Konfigurer afhjælpning for Microsoft Defender Antivirus registreringer.](configure-remediation-microsoft-defender-antivirus.md)
