---
title: Opret indikatorer for filer
ms.reviewer: ''
description: Opret indikatorer for en filhash, der definerer registrering, forebyggelse og udeladelse af objekter.
keywords: fil, hash, administrere, tilladt, blokeret, blokere, ren, skadelig, filhash, IP-adresse, URL-adresser, domæne
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
ms.technology: mde
ms.openlocfilehash: 0414f85c9d461a2f676f9bc248a1ce065f7547d7
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/21/2022
ms.locfileid: "66949497"
---
# <a name="create-indicators-for-files"></a>Opret indikatorer for filer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender for Endpoint Plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Business](../defender-business/mdb-overview.md)

> [!TIP]
> Vil du opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Undgå yderligere overførsel af et angreb i din organisation ved at forbyde potentielt skadelige filer eller mistanke om malware. Hvis du kender en potentielt skadelig PE-fil (Portable Executable), kan du blokere den. Denne handling forhindrer, at den læses, skrives eller udføres på enheder i din organisation.

Du kan oprette indikatorer for filer på tre måder:

- Ved at oprette en indikator via indstillingssiden
- Ved at oprette en kontekstafhængig indikator ved hjælp af knappen Tilføj indikator fra siden med filoplysninger
- Ved at oprette en indikator via [indikator-API'en](ti-indicator.md)

## <a name="before-you-begin"></a>Før du begynder

Det er vigtigt at forstå følgende forudsætninger, før du opretter indikatorer for filer:

- Denne funktion er tilgængelig, hvis din organisation bruger **Microsoft Defender Antivirus (i aktiv tilstand),** og **cloudbaseret beskyttelse er aktiveret**. Du kan få flere oplysninger under [Administrer skybaseret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).

- Antimalware-klientversionen skal være 4.18.1901.x eller nyere. Se [Månedlige platform- og programversioner](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)

- Understøttes på enheder med Windows 10, version 1703 eller nyere, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 og Windows Server 2022.
    
   > [!NOTE]
   > Windows Server 2016 og Windows Server 2012 R2 skal onboardes ved hjælp af vejledningen i [Indbyggede Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) , for at denne funktion fungerer. Brugerdefinerede filindikatorer med handlingerne Allow, Block og Remediate er nu også tilgængelige i den [offentlige prøveversion for de forbedrede funktioner i antimalwareprogrammet til macOS og Linux](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/enhanced-antimalware-engine-capabilities-for-linux-and-macos/ba-p/3292003).

- Hvis du vil starte blokering af filer, skal du først [aktivere funktionen "bloker eller tillad"](advanced-features.md) i Indstillinger.

Denne funktion er designet til at forhindre, at formodet malware (eller potentielt skadelige filer) downloades fra internettet. Den understøtter i øjeblikket bærbare eksekverbare filer (PE), herunder .exe og .dll filer. Dækningen vil blive forlænget over tid.

> [!IMPORTANT]
> I Defender for Endpoint Plan 1 og Defender for Business kan du oprette en indikator for at blokere eller tillade en fil. I Defender for Business anvendes indikatoren på tværs af dit miljø og kan ikke begrænses til bestemte enheder.

## <a name="create-an-indicator-for-files-from-the-settings-page"></a>Opret en indikator for filer fra indstillingssiden

1. Vælg **Indstillinger** \> **Slutpunktsindikatorer** \> (under **Regler**) i navigationsruden.

2. Vælg fanen **Filerhashes** .

3. Vælg **Tilføj element**.

4. Angiv følgende oplysninger:
    - Indikator – Angiv enhedsoplysningerne, og definer indikatorens udløb.
    - Handling – Angiv den handling, der skal udføres, og angiv en beskrivelse.
    - Scope – Definer omfanget af enhedsgruppen (området er ikke tilgængeligt i [Defender for Business](../defender-business/mdb-overview.md)).

5. Gennemse oplysningerne under fanen Oversigt, og vælg derefter **Gem**.

## <a name="create-a-contextual-indicator-from-the-file-details-page"></a>Opret en kontekstafhængig indikator fra siden med filoplysninger

En af indstillingerne, når du foretager [svarhandlinger på en fil](respond-file-alerts.md) , er at tilføje en indikator for filen. Når du tilføjer en indikatorhash for en fil, kan du vælge at udløse en besked og blokere filen, når en enhed i organisationen forsøger at køre den.

Filer, der automatisk blokeres af en indikator, vises ikke i filens Løsningscenter, men beskederne vil stadig være synlige i beskedkøen.

## <a name="public-preview-alerting-on-file-blocking-actions"></a>Offentlig prøveversion: Besked om handlinger til filblokering

> [!IMPORTANT]
> Oplysningerne i dette afsnit (**Offentlig prøveversion til automatiseret undersøgelse og afhjælpningsprogram**) er relateret til et produkt, der er udgivet på forhånd, og som kan ændres væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

De aktuelt understøttede handlinger for fil-IOC tillader, overvåger og blokerer og afhjælper. Når du har valgt at blokere en fil, kan du vælge, om det er nødvendigt at udløse en besked. På denne måde kan du styre antallet af beskeder, der sendes til dine sikkerhedsteams, og sørge for, at der kun sendes påkrævede beskeder.

I Microsoft 365 Defender skal du gå til **Indstillinger** > **Slutpunkter** > **Indikatorer** > **Tilføj ny filhash**.

Vælg at blokere og afhjælpe filen.

Vælg, om der skal oprettes en besked for filblokeringshændelsen, og definer beskedindstillingerne:

- Beskedens titel
- Alvorsgraden af beskeden
- Kategori
- Beskrivelse
- Anbefalede handlinger

:::image type="content" source="images/indicators-generate-alert.png" alt-text="Beskedindstillingerne for filindikatorer" lightbox="images/indicators-generate-alert.png":::

> [!IMPORTANT]
>
> - Filblokke gennemtvinges og fjernes typisk inden for et par minutter, men kan tage op til 30 minutter.
> - Hvis der er modstridende IoC-politikker med samme håndhævelsestype og mål, anvendes politikken for den mere sikre hash. En SHA-256-filhash IoC-politik vinder over en SHA-1-filhash IoC-politik, som vil vinde over en MD5-filhash IoC-politik, hvis hashtyperne definerer den samme fil. Dette er altid tilfældet, uanset enhedsgruppen.
> - Hvis IoC-politikker med samme håndhævelsesmål anvendes på alle enheder og på enhedens gruppe, vil politikken i enhedsgruppen i alle andre tilfælde vinde, hvis der anvendes modstridende IoC-politikker på alle enheder og på enhedens gruppe.
> - Hvis gruppepolitikken EnableFileHashComputation er deaktiveret, reduceres blokeringsnøjagtigheden af filen IoC. Aktivering kan dog `EnableFileHashComputation` påvirke enhedens ydeevne. Kopiering af store filer fra et netværksshare til din lokale enhed, især via en VPN-forbindelse, kan f.eks. have indflydelse på enhedens ydeevne.
>
> Du kan få flere oplysninger om gruppepolitikken EnableFileHashComputation under [Defender CSP](/windows/client-management/mdm/defender-csp).
>
> Du kan finde flere oplysninger om konfiguration af denne funktion på Defender for Endpoint på Linux og macOS under [Konfigurer funktionen til beregning af filhash på Linux](linux-preferences.md#configure-file-hash-computation-feature) og [funktionen Konfigurer filhashberegning på macOS](mac-preferences.md#configure-file-hash-computation-feature).

## <a name="public-preview-advanced-hunting-capabilities"></a>Offentlig prøveversion: Avancerede jagtegenskaber

> [!IMPORTANT]
> Oplysningerne i dette afsnit (**Offentlig prøveversion til automatiseret undersøgelse og afhjælpningsprogram**) er relateret til et produkt, der er udgivet på forhånd, og som kan ændres væsentligt, før det udgives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller stiltiende, med hensyn til de oplysninger, der er angivet her.

Du kan forespørge om svarhandlingsaktiviteten på forhånd på jagt. Nedenfor er et eksempel på en forespørgsel om avanceret jagt:

```console
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
Timestamp > ago(30d)
| where AdditionalFields contains "EUS:Win32/CustomEnterpriseBlock!cl"
```

Du kan finde flere oplysninger om avanceret jagt under [Proaktiv jagt efter trusler med avanceret jagt](advanced-hunting-overview.md).

Nedenfor er yderligere trådnavne, som kan bruges i eksempelforespørgslen ovenfor:

Filer:

- EUS:Win32/CustomEnterpriseBlock!cl
- EUS:Win32/CustomEnterpriseNoAlertBlock!cl

Certifikater:

- EUS:Win32/CustomCertEnterpriseBlock!cl

Aktiviteten for svarhandlingen kan også ses på enhedens tidslinje.

## <a name="policy-conflict-handling"></a>Politikkonflikthåndtering

Konflikt i håndtering af certifikat- og fil-IoC-politik følger nedenstående rækkefølge:

- Hvis filen ikke er tilladt af Windows Defender Programkontrolelement og AppLocker gennemtvinge tilstandspolitik/-politikker, skal du **blokere**
- Ellers, hvis filen er tilladt af Microsoft Defender Antivirus-udeladelse, så **Tillad**
- Ellers, hvis filen er blokeret eller advaret af en blok eller advar fil IoC, og derefter **Bloker/Advar**
- Ellers, hvis filen er tilladt af en IoC-politik for tillad fil **, skal du**
- Ellers, hvis filen er blokeret af ASR-regler, CFA, AV, SmartScreen og derefter **Bloker**
- Else **Allow** (overfører Windows Defender Application Control & AppLocker-politik, der gælder ingen IoC-regler for den)

>[!NOTE]
> I situationer, hvor Microsoft Defender Antivirus er angivet til **Bloker**, men Defender for Endpoint er angivet til **Tillad**, vil politikken som standard **være Tillad**.

Hvis der er modstridende IoC-politikker med samme håndhævelsestype og mål, anvendes politikken for den mere sikre hashværdi (dvs. længere). En SHA-256-filhash IoC-politik vinder f.eks. over en IoC-politik for MD5-filhash, hvis begge hashtyper definerer den samme fil.

> [!WARNING]
> Politikkonflikthåndtering for filer og certifikater adskiller sig fra politikkonflikthåndtering for domæner/URL-adresser/IP-adresser.

Trussels- og sårbarhedsstyringens bloker sårbare programfunktioner bruger fil-IOC'erne til håndhævelse og følger ovenstående rækkefølge for konflikthåndtering.

### <a name="examples"></a>Eksempler

<br>

****

|Komponent|Gennemtvingelse af komponent|Filindikatorhandling|Resultat|
|---|---|---|---|
|Udeladelse af filsti til reduktion af angrebsoverflade|Tillad|Bloker|Bloker|
|Regel for reduktion af angrebsoverflade|Bloker|Tillad|Tillad|
|Windows Defender programkontrolelement|Tillad|Bloker|Tillad|
|Windows Defender programkontrolelement|Bloker|Tillad|Bloker|
|Microsoft Defender Antivirus-udeladelse|Tillad|Bloker|Tillad|
|

## <a name="see-also"></a>Se også

- [Opret indikatorer](manage-indicators.md)
- [Opret indikatorer for IP'er og URL-adresser/domæner](indicator-ip-domain.md)
- [Opret indikatorer baseret på certifikater](indicator-certificates.md)
- [Administrer indikatorer](indicator-manage.md)
