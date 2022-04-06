---
title: Opret indikatorer for filer
ms.reviewer: ''
description: Opret indikatorer for en filhash, der definerer registrering, forhindring og udelukkelse af enheder.
keywords: fil, hash, administrer, tilladt, blokeret, bloker, ren, skadelig, filhash, IP-adresse, URL-adresser, domæne
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
ms.openlocfilehash: 20e120385046a333f68f4959c395c2bbb520899b
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500909"
---
# <a name="create-indicators-for-files"></a>Opret indikatorer for filer

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Forebyg yderligere overførsel af et angreb i organisationen ved at udelukke potentielt skadelige filer eller mistanke om malware. Hvis du kender en potentielt skadelig eksekverbar eksekverbar fil (PE), kan du blokere den. Denne handling forhindrer den i at blive læst, skrevet eller udført på enheder i organisationen.

Der er tre måder, hvorpå du kan oprette indikatorer for filer:

- Ved at oprette en indikator via siden med indstillinger
- Ved at oprette en kontekstafhængig indikator ved hjælp af knappen Tilføj indikator fra siden med filoplysninger
- Ved at oprette en indikator via [indikator-API'en](ti-indicator.md)

## <a name="before-you-begin"></a>Før du begynder

Det er vigtigt at forstå følgende forudsætninger, før du opretter indikatorer for filer:

- Denne funktion er tilgængelig, hvis din organisation **Microsoft Defender Antivirus (i aktiv tilstand)** og **skybaseret beskyttelse er aktiveret**. Få mere at vide under [Administrer skybaseret beskyttelse](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).

- Versionen af Antimalware-klienten skal være 4.18.1901.x eller nyere. Se [Månedlig platform og programversioner](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)

- Understøttes på enheder med Windows 10, version 1703 eller nyere, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 og Windows Server 2022.
    
   >[!NOTE]
    >Windows Server 2016 og Windows Server 2012 R2 skal være onboardet ved hjælp af instruktionerne i [Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), for at denne funktion kan fungere. 

- Hvis du vil begynde at blokere filer, skal [du først aktivere funktionen "bloker eller tillad"](advanced-features.md) i Indstillinger.

Denne funktion er udviklet til at forhindre mulig malware (eller potentielt skadelige filer) i at blive hentet fra internettet. Det understøtter i øjeblikket portable eksekverbare filer (PE), herunder .exe og .dll filer. Dækningen udvides med tiden.

## <a name="create-an-indicator-for-files-from-the-settings-page"></a>Opret en indikator for filer fra siden med indstillinger

1. I **navigationsruden** skal du **vælge Indstillinger** \> **Slutpunktsindikatorer** \> (under **Regler**).

2. Vælg **fanen Filhashes** .

3. Vælg **Tilføj element**.

4. Angiv følgende oplysninger:
    - Indikator – Angiv enhedsdetaljerne, og definer udløb af indikatoren.
    - Handling – Angiv den handling, der skal gøres, og angiv en beskrivelse.
    - Omfang – Definer enhedsgruppens omfang.

5. Gennemgå oplysningerne under fanen Oversigt, og vælg derefter **Gem**.

## <a name="create-a-contextual-indicator-from-the-file-details-page"></a>Opret en kontekstafhængig indikator fra siden med filoplysninger

En af mulighederne, når du [tager svarhandlinger i en fil](respond-file-alerts.md) , er at tilføje en indikator for filen. Når du tilføjer en indikatorhash for en fil, kan du vælge at hæve en besked og blokere filen, når en enhed i organisationen forsøger at køre den.

Filer, der automatisk blokeres af en indikator, vises ikke i filens handlingscenter, men beskederne vil stadig være synlige i køen Vigtige beskeder.

## <a name="public-preview-alerting-on-file-blocking-actions"></a>Offentlig forhåndsvisning: Beskeder om filblokeringshandlinger

> [!IMPORTANT]
> Oplysningerne i dette afsnit (Offentlig prøveversion af automatiseret undersøgelse og **afhjælpningsprogram**) relaterer til det foreløbige produkt, som kan være væsentligt ændret, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

De aktuelle understøttede handlinger for fil-IOC er tilladte, overvåge og blokere og afhjælpe. Når du har valgt at blokere en fil, kan du vælge, om det er nødvendigt at udløse en besked. På denne måde kan du styre antallet af vigtige beskeder til dine sikkerhedsteams og sikre, at kun påkrævede beskeder hæves.

I Microsoft 365 Defender skal du gå **Indstillinger** >  EndpointsIndicatorsAdd >  >  **New File Hash**.

Vælg at blokere og afhjælpe filen.

Vælg, om der skal genereres en besked om filblokeringshændelsen, og definer indstillingerne for vigtige beskeder:

- Beskedens titel
- Alvorsgrad for beskeden
- Kategori
- Beskrivelse
- Anbefalede handlinger

:::image type="content" source="images/indicators-generate-alert.png" alt-text="Beskedindstillinger for filindikatorer" lightbox="images/indicators-generate-alert.png":::

> [!IMPORTANT]
>
> - Typisk gennemtvinges filblokke og fjernes inden for et par minutter, men det kan tage op til 30 minutter.
> - Hvis der er IoC-politikker med samme håndhævelsestype og destination, anvendes politikken for en mere sikker hash-fil. En IoC-politik for en SHA-256-filhash vinder over en IoC-politik for en SHA-1-filhash, som vinder over en IoC-politik for en MD5-filhash, hvis hash-typerne definerer den samme fil. Dette gælder altid, uanset enhedsgruppen.
> - I alle andre tilfælde gælder politikken i enhedsgruppen for en enhed, hvis der anvendes IoC-politikker med samme håndhævelsessmål for alle enheder og for enhedens gruppe. For en enhed gælder politikken i enhedsgruppen.
> - Hvis gruppepolitikken EnableFileHashComputation er deaktiveret, reduceres blokeringsnøjagtigheden af filens IoC. Aktivering kan dog påvirke `EnableFileHashComputation` enhedens ydeevne. Eksempelvis kan kopiering af store filer fra et netværksshare til din lokale enhed, især via en VPN-forbindelse, have en effekt på enhedens ydeevne.
>
> Du kan finde flere oplysninger om gruppepolitikken EnableFileHashComputation under [Defender CSP](/windows/client-management/mdm/defender-csp).

## <a name="public-preview-advanced-hunting-capabilities"></a>Offentlig prøveversion: Avancerede muligheder for at søge

> [!IMPORTANT]
> Oplysninger i dette afsnit (Offentlig prøveversion af automatiseret undersøgelse og **afhjælpningsprogram**) relaterer til det foreløbige produkt, som kan være væsentligt ændret, før det frigives kommercielt. Microsoft påser ingen garantier, udtrykkelige eller underforståede, med hensyn til de oplysninger, du har angivet her.

Du kan forespørge på svarhandlingsaktiviteten på forhånd at lede. Nedenfor er et eksempel på en avanceret forespørgsel:

```console
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
Timestamp > ago(30d)
| where AdditionalFields contains "EUS:Win32/CustomEnterpriseBlock!cl"
```

Du kan finde flere oplysninger om avanceret [jagt under Proaktivt lede efter trusler med avanceret jagt](advanced-hunting-overview.md).

Nedenfor finder du yderligere trådnavne, der kan bruges i eksempelforespørgslen ovenfor:

Filer:

- EUS:Win32/CustomEnterpriseBlock!cl
- EUS:Win32/CustomEnterpriseNoAlertBlock!cl

Certifikater:

- EUS:Win32/CustomCertEnterpriseBlock!cl

Svarhandlingsaktiviteten kan også ses på enhedens tidslinje.

## <a name="policy-conflict-handling"></a>Håndtering af konflikt mellem politikker

Cert- og File IoC-politikhåndteringskonflikt følger nedenstående rækkefølge:

- Hvis filen ikke er tilladt af Windows Defender Programkontrolelement og AppLocker-gennemtving tilstandspolitik/-politikker, skal du vælge **Bloker**
- Hvis filen ikke er tilladt i Microsoft Defender Antivirus, skal du vælge **Tillad**
- Ellers, hvis filen blokeres eller advares af en bloker eller advar fil IoC, så **Bloker/advar**
- Ellers hvis filen er tilladt af en IoC-politik for tillad fil, skal du **vælge Tillad**
- Ellers, hvis filen er blokeret af ASR-regler, CFA, AV, SmartScreen og derefter **Bloker**
- **Ellers** tillades (Windows Defender programkontrolelement & AppLocker-politik, ingen IoC-regler gælder for den)

>[!NOTE]
> I situationer, Microsoft Defender Antivirus er indstillet til **Bloker**, men Defender til Slutpunkt er indstillet til **Tillad**, vil politikken som standard være **Tillad**.

Hvis der er IoC-politikker med samme håndhævelsestype og destination, der er i konflikt med hinanden, anvendes politikken for den mere sikre (hvilket vil sige længere) hash. Eksempelvis vil en IoC-politik for en SHA-256-fil, vinde over en IoC-politik for en MD5-filhash, hvis begge hash-typer definerer den samme fil.

> [!WARNING]
> Håndtering af politikkonflikter for filer og certifikater adskiller sig fra håndtering af politikkonflikter for domæner/URL-adresser/IP-adresser.

Trussels- og håndtering af sikkerhedsrisici s blokerede følsomme programfunktioner bruger fil-IoCs til håndhævelse og følger rækkefølgen af ovenstående konflikthåndtering.

### <a name="examples"></a>Eksempler

<br>

****

|Komponent|Håndhævelse af komponent|Handling med filindikator|Resultat|
|---|---|---|---|
|Udelukkelse af reduktion af filsti til angrebsoverfladen|Tillad|Bloker|Bloker|
|Regel for reduktion af angrebsoverfladen|Bloker|Tillad|Tillad|
|Windows Defender programkontrolelement|Tillad|Bloker|Tillad|
|Windows Defender programkontrolelement|Bloker|Tillad|Bloker|
|Microsoft Defender Antivirus udeladelse|Tillad|Bloker|Tillad|
|

## <a name="see-also"></a>Se også

- [Opret indikatorer](manage-indicators.md)
- [Opret indikatorer for IP'er og URL-adresser/domæner](indicator-ip-domain.md)
- [Opret indikatorer baseret på certifikater](indicator-certificates.md)
- [Administrer indikatorer](indicator-manage.md)
