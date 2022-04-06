---
title: Aktivér regler for reduktion af angrebsoverflade
description: Aktivér ASR-regler (Attack Surface Reduction) for at beskytte dine enheder mod angreb, der bruger makroer, scripts og almindelige injektionsteknikker.
keywords: Reduktion af angrebsoverflade, hofter, host intrusion forebyggelse system, beskyttelsesregler, anti-exploit, anti-exploit, udnytte, infektion forebyggelse, aktivere, tænde
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.date: 1/18/2022
ms.openlocfilehash: f8f6865bc65662cbbfd5a9276d95abc405f5a64b
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664232"
---
# <a name="enable-attack-surface-reduction-rules"></a>Aktivér regler for reduktion af angrebsoverflade

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vil du gerne opleve Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Regler for reduktion af angrebsoverflader](attack-surface-reduction.md) (ASR-regler) hjælper med at forhindre handlinger, som malware ofte misbruger for at kompromittere enheder og netværk.

## <a name="requirements"></a>Krav

Reduktion af angrebsoverfladen på tværs af Windows versioner

Du kan angive regler for reduktion af angrebsoverfladen for enheder, der kører en af følgende versioner af Windows:

- Windows 10 Pro[, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) eller nyere
- Windows 10 Enterprise, [version 1709](/windows/whats-new/whats-new-windows-10-version-1709) eller nyere
- Windows Server, [version 1803 (halvårlig kanal)](/windows-server/get-started/whats-new-in-windows-server-1803) eller nyere
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/windows/win32/srvnodes/what-s-new-for-windows-server-2012-r2)
- Windows Server 2022

Hvis du vil bruge hele funktionssættet med regler for reduktion af angrebsoverfladen, skal du bruge:

- Windows Defender Antivirus som primær AV (beskyttelse i realtid er slået til)
- [Cloud-Delivery Protection](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) på (nogle regler kræver det)
- Windows 10 Enterprise E5- eller E3-licens

Selvom regler for reduktion af angrebsoverfladen ikke kræver en [Windows E5-licens](/windows/deployment/deploy-enterprise-licenses) med en Windows E5-licens, får du avancerede administrationsfunktioner, herunder overvågning, analyse og arbejdsprocesser, der er tilgængelige i Defender for Endpoint samt rapporterings- og konfigurationsfunktioner i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalen</a>. Disse avancerede funktioner er ikke tilgængelige med en E3-licens, men du kan stadig bruge Logbog til at gennemse hændelser for regler for reduktion af angrebsoverfladen.

Hver ASR-regel indeholder en af fire indstillinger:

- **Ikke konfigureret** |  **Deaktiveret**: Deaktiver ASR-reglen
- **Blok**: Aktivér ASR-reglen
- **Overvågning**: Evaluer, hvordan ASR-reglen vil påvirke din organisation, hvis den er aktiveret
- **Advarsel**! Aktivér ASR-reglen, men tillad, at slutbrugeren tilsidesætter blokken

> [!IMPORTANT]
> Advarselstilstand understøttes i øjeblikket ikke for tre ASR-regler, når du konfigurerer ASR-regler i Microsoft Endpoint Manager (MEM). Du kan få mere at vide under [Sager, hvor advarselstilstand ikke understøttes](attack-surface-reduction.md#cases-where-warn-mode-is-not-supported).

Vi anbefaler, at du bruger ASR-regler med en Windows E5-licens (eller lignende licens-SKU) for at drage fordel af de avancerede overvågnings- og rapporteringsfunktioner, der er tilgængelige i [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md) (Defender for Endpoint). Men hvis du har en anden licens, f.eks. Windows Professional eller Windows E3, der ikke indeholder avancerede overvågnings- og rapporteringsfunktioner, kan du udvikle dine egne overvågnings- og rapporteringsværktøjer oven på de hændelser, der genereres på hvert slutpunkt, når ASR-regler udløses (f.eks. Videresending af hændelse).

> [!TIP]
> Hvis du vil vide mere om Windows licenser, [skal du se Windows 10 Licenser](https://www.microsoft.com/licensing/product-licensing/windows10?activetab=windows10-pivot:primaryr5) og få [vejledningen til volumenlicensering for at få Windows 10](https://download.microsoft.com/download/2/D/1/2D14FE17-66C2-4D4C-AF73-E122930B60F6/Windows-10-Volume-Licensing-Guide.pdf).

Du kan aktivere regler for reduktion af angrebsoverfladen ved hjælp af en af disse metoder:

- [Microsoft Intune](#intune)
- [Mobil Enhedshåndtering (MDM)](#mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Gruppepolitik](#group-policy)
- [PowerShell](#powershell)

Administration på virksomhedsniveau, f.eks. Intune eller Microsoft Endpoint Manager, anbefales. Administration på virksomhedsniveau overskriver eventuelle modstridende Gruppepolitik eller PowerShell-indstillinger ved start.

## <a name="exclude-files-and-folders-from-asr-rules"></a>Udelad filer og mapper fra ASR-regler

Du kan udelukke filer og mapper fra at blive evalueret af de fleste regler for reduktion af angrebsoverfladen. Det betyder, at selvom en ASR-regel bestemmer, at filen eller mappen indeholder skadelig funktionsmåde, blokerer den ikke for, at filen kører. Dette kan potentielt tillade, at usikre filer kører og inficerer dine enheder.

Du kan også udelade ASR-regler fra udløsere baseret på certifikat- og filhashes ved at tillade den angivne Defender for Endpoint-fil- og certifikatindikatorer. (Se [Administrer indikatorer](manage-indicators.md)).

> [!IMPORTANT]
> Hvis du udelader filer eller mapper, kan det reducere beskyttelsen af ASR-regler alvorligt. Udeladte filer får tilladelse til at køre, og der registreres ingen rapport eller hændelse.
> Hvis ASR-regler registrerer filer, som du mener ikke bør registreres, skal du [først bruge overvågningstilstanden til at teste reglen](evaluate-attack-surface-reduction.md).

Du kan angive individuelle filer eller mapper (ved hjælp af mappestier eller fuldt kvalificerede ressourcenavne), men du kan ikke angive, hvilke regler undtagelserne skal gælde for. En udeladelse anvendes kun, når det udeladte program eller den udeladte tjeneste starter. Hvis du f.eks. tilføjer en udeladelse for en opdateringstjeneste, der allerede kører, vil opdateringstjenesten fortsat udløse hændelser, indtil tjenesten stoppes og genstartes.

ASR-regler understøtter miljøvariabler og jokertegn. Du kan få oplysninger om, hvordan du bruger jokertegn, [under Brug jokertegn i filnavnet og mappestien eller på listen over filtypenavne](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).

## <a name="policy-conflict"></a>Politikkonflikt

1. Hvis der anvendes en modstridende politik via MDM og GP, har den indstilling, der anvendes fra MDM, forrang.

2. Regler for reduktion af angrebsoverfladen for MEM-administrerede enheder understøtter nu funktionsmåde for sammenlægning af indstillinger fra forskellige politikker for at oprette en overordnet politik for hver enhed. Det er kun de indstillinger, der ikke er i konflikt, der flettes, mens de indstillinger, der er i konflikt, ikke føjes til undersættet af regler. Tidligere hvis to politikker indeholdt konflikter for en enkelt indstilling, var begge politikker markeret som værende i konflikt, og ingen indstillinger fra nogen af profilerne ville blive installeret. Funktionsmåden for fletning af regler for reduktion af angrebsoverfladen er som følger:
   - Regler for reduktion af angrebsoverfladen fra følgende profiler evalueres for hver enhed, som reglerne gælder for:
     - Enheder > konfigurationspolitik > profil til beskyttelse af slutpunkter > **Microsoft Defender Exploit Guard** >  [Nedskæring af surface](/mem/intune/protect/endpoint-protection-windows-10#attack-surface-reduction-rules).
     - Slutpunktsikkerhed > Politik  >  for **reduktion af angrebsoverfladenRegler** for [reduktion af angrebsoverflade](/mem/intune/protect/endpoint-security-asr-policy#devices-managed-by-intune).
     - Slutpunktssikkerhed > Sikkerhedsgrundlinjer > **Microsoft Defender ATP BaselineAttack** >  [Surface Reduction Rules](/mem/intune/protect/security-baseline-settings-defender-atp#attack-surface-reduction-rules).
   - Indstillinger, der ikke har konflikter, føjes til en delmængde af politikken for enheden.
   - Når to eller flere politikker har modstridende indstillinger, føjes de modstridende indstillinger ikke til den kombinerede politik, mens indstillinger, der ikke er i konflikt, føjes til den politik for supersæt, der gælder for en enhed.
   - Det er kun konfigurationerne for modstridende indstillinger, der holdes tilbage.

## <a name="configuration-methods"></a>Konfigurationsmetoder

Dette afsnit indeholder konfigurationsoplysninger om følgende konfigurationsmetoder:

- [Intune](#intune)
- [MEM](#mem)
- [MDM](#mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Gruppepolitik](#group-policy)
- [PowerShell](#powershell)

Følgende procedurer for aktivering af ASR-regler omfatter instruktioner til, hvordan filer og mapper udelades.

### <a name="intune"></a>Intune

#### <a name="device-configuration-profiles"></a>Profiler til enhedskonfiguration

1. Vælg **Profiler for enhedskonfiguration**\>. Vælg en eksisterende beskyttelsesprofil for slutpunkter, eller opret en ny. Hvis du vil oprette en ny, skal du vælge **Opret profil** og angive oplysninger for denne profil. Vælg **Slutpunktsbeskyttelse** som **Profiltype**. Hvis du har valgt en eksisterende profil, skal du vælge **Egenskaber** og derefter vælge **Indstillinger**.

2. I ruden **Endpoint Protection** skal du vælge **Windows Defender Exploit Guard** og derefter vælge **Reduktion af angrebsoverflade**. Vælg den ønskede indstilling for hver ASR-regel.

3. Under **Undtagelser for Reduktion af angrebsoverflade** skal du angive individuelle filer og mapper. Du kan også vælge **Importér** for at importere en CSV-fil, der indeholder filer og mapper, for at udelade fra ASR-regler. Hver linje i CSV-filen skal formateres på følgende måde:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Vælg **OK** i de tre konfigurationsruder. Vælg derefter **Opret** , hvis du opretter en ny fil til beskyttelse af slutpunkter eller **Gem** , hvis du redigerer en eksisterende fil.

#### <a name="endpoint-security-policy"></a>Sikkerhedspolitik for slutpunkt**

1. Vælg **Overfladereduktion af** **slutpunktssikkerhedsangreb**\>. Vælg en eksisterende ASR-regel, eller opret en ny. Hvis du vil oprette en ny, skal du vælge **Opret politik** og angive oplysninger for denne profil. Som **Profiltype** skal du vælge **Regler for reduktion af angrebsoverflade**. Hvis du har valgt en eksisterende profil, skal du vælge **Egenskaber** og derefter vælge **Indstillinger**.

2. I ruden **Konfigurationsindstillinger** skal du vælge **Reduktion af angrebsoverflade** og derefter vælge den ønskede indstilling for hver ASR-regel.

3. Angiv individuelle filer og mapper under **Liste over yderligere mapper, der skal beskyttes**, **liste over apps, der har adgang til beskyttede mapper** og **Udelad filer og stier fra regler for reduktion af angrebsoverfladen**. Du kan også vælge **Importér** for at importere en CSV-fil, der indeholder filer og mapper, for at udelade fra ASR-regler. Hver linje i CSV-filen skal formateres på følgende måde:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Vælg **Næste** i de tre konfigurationsruder, og vælg derefter **Opret** , hvis du opretter en ny politik, eller **Gem** , hvis du redigerer en eksisterende politik.

### <a name="mem"></a>MEM

Du kan bruge MICROSOFT ENDPOINT MANAGER (MEM) OMA-URI til at konfigurere brugerdefinerede ASR-regler. I følgende procedure bruges reglen [Bloker misbrug af udnyttede sårbare signerede drivere](attack-surface-reduction-rules-reference.md#block-abuse-of-exploited-vulnerable-signed-drivers) i eksemplet.

1. Åbn MEM Administration (Microsoft Endpoint Manager). Klik på **Enheder** i menuen **Start**, vælg **Konfigurationsprofiler**, og klik derefter på **Opret profil**.

   > [!div class="mx-imgBorder"]
   >  :::image type="content" source="images/mem01-create-profile.png" alt-text="Siden Opret profil på Microsoft Endpoint Manager Administrationsportal" lightbox="images/mem01-create-profile.png":::

2. Vælg følgende på følgende to rullelister under **Opret en profil**:

   - Vælg **Windows 10 og nyere** i **Platform**
   - Vælg **Skabeloner** i **Profiltype**
   - Hvis ASR-regler allerede er angivet via Slutpunktssikkerhed, skal du i **Profiltype** vælge **Indstillinger Katalog**.

   Vælg **Brugerdefineret**, og vælg derefter **Opret**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem02-profile-attributes.png" alt-text="Attributterne for regelprofilen på Microsoft Endpoint Manager Administrationsportal" lightbox="images/mem02-profile-attributes.png":::

3. Værktøjet Brugerdefineret skabelon åbnes i trin **1 Grundlæggende**. Skriv et navn til skabelonen i **Navn** i **1 Grundlæggende**, og i **Beskrivelse** kan du skrive en beskrivelse (valgfrit).

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem03-1-basics.png" alt-text="De grundlæggende attributter i Microsoft Endpoint Manager Administrationsportal" lightbox="images/mem03-1-basics.png":::

4. Klik på **Næste**. Trin **2 Konfigurationsindstillinger** åbnes. Klik på **Tilføj** for OMA-URI-Indstillinger. Der vises nu to indstillinger: **Tilføj** og **eksportér**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem04-2-configuration-settings.png" alt-text="Konfigurationsindstillingerne på Microsoft Endpoint Manager Administrationsportal" lightbox="images/mem04-2-configuration-settings.png":::

5. Klik på **Tilføj** igen. Indstillinger **Add Row OMA-URI** åbnes. Gør følgende i **Tilføj række**:

   - Skriv et navn til reglen i **Navn**.
   - Angiv en kort beskrivelse i **Beskrivelse**.
   - I **OMA-URI** skal du skrive eller indsætte det specifikke OMA-URI-link for den regel, du tilføjer. Se AFSNITTET MDM i denne artikel for at få den OMA-URI, der skal bruges til denne eksempelregel. Hvis du vil have mere at vide om GUIDS for regler for reduktion af angrebsoverfladen, skal du se [Beskrivelser af regler for hver regel](attack-surface-reduction-rules-reference.md#per-rule-descriptions) i emnet: Regler for reduktion af angrebsoverfladen.
   - I **Datatype** skal du vælge **Streng**.
   - I **Værdi** skal du skrive eller indsætte GUID-værdien, \= fortegnet og værdien State uden mellemrum (_GUID=StateValue_). Hvor:

     - 0: Deaktiver (deaktiver ASR-reglen)
     - 1 : Blok (aktivér ASR-reglen)
     - 2: Overvågning (evaluer, hvordan ASR-reglen vil påvirke din organisation, hvis den er aktiveret)
     - 6: Advar (aktivér ASR-reglen, men tillad, at slutbrugeren springer blokken over)

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem05-add-row-oma-uri.png" alt-text="OMA URI-konfigurationen på Microsoft Endpoint Manager Administrationsportal" lightbox="images/mem05-add-row-oma-uri.png":::

6. Vælg **Gem**. **Tilføj rækkelukninger** . Vælg **Næste** i **Brugerdefineret**. I trin **3 Områdekoder** er områdekoder valgfrie. Gør et af følgende:

   - **Vælg Vælg områdekoder**, vælg områdekoden (valgfrit), og vælg derefter **Næste**.
   - Eller vælg **Næste**

7. I trin **4 Tildelinger** i **Inkluderede grupper** skal du vælge mellem følgende indstillinger for de grupper, som reglen skal gælde for:

   - **Tilføj grupper**
   - **Tilføj alle brugere**
   - **Tilføj alle enheder**

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem06-4-assignments.png" alt-text="Tildelingerne på portalen Microsoft Endpoint Manager Administration" lightbox="images/mem06-4-assignments.png":::

8. I **Udeladte grupper** skal du vælge de grupper, du vil udelade fra denne regel, og derefter vælge **Næste**.

9. I trin **5 skal du** gøre følgende for anvendelsesregler for følgende indstillinger:

   - I **Regel** skal du enten vælge **Tildel profil, hvis** eller **Tildel ikke profil, hvis**
   - Under **Egenskab** skal du vælge den egenskab, som reglen skal gælde for
   - Angiv den relevante værdi eller det relevante værdiinterval i **Værdi**

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/mem07-5-applicability-rules.png" alt-text="Anvendelighedsreglerne på portalen Microsoft Endpoint Manager Administration" lightbox="images/mem07-5-applicability-rules.png":::

10. Vælg **Næste**. Gennemse **+ opret** i trin 6, gennemse de indstillinger og oplysninger, du har valgt og angivet, og vælg derefter **Opret**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/mem08-6-review-create.png" alt-text="Indstillingen Gennemse og opret på Microsoft Endpoint Manager Administrationsportal" lightbox="images/mem08-6-review-create.png":::

    > [!NOTE]
    > Reglerne er aktive og live inden for få minutter.

> [!NOTE]
> Konflikthåndtering:
>
> Hvis du tildeler en enhed to forskellige ASR-politikker, er den måde, konflikten håndteres på, regler, der er tildelt forskellige tilstande, der er ingen konfliktstyring på plads, og resultatet er en fejl.
>
> Ikke-modstridende regler medfører ikke en fejl, og reglen anvendes korrekt. Resultatet er, at den første regel anvendes, og efterfølgende ikke-modstridende regler flettes ind i politikken.

### <a name="mdm"></a>MDM

Brug [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductionrules) CSP (Configuration Service Provider) til individuelt at aktivere og angive tilstanden for hver regel.

Følgende er et eksempel på en reference, der bruger GUID-værdier for [referencen til regler for reduktion af angrebsoverfladen](attack-surface-reduction-rules-reference.md).

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules`

`Value: 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84=2|3b576869-a4ec-4529-8536-b80a7769e899=1|d4f940ab-401b-4efc-aadc-ad5f3c50688a=2|d3e037e1-3eb8-44c8-a917-57927947596d=1|5beb7efe-fd9a-4556-801d-275e5ffc04cc=0|be9ba2d9-53ea-4cdc-84e5-9b1eeee46550=1`

De værdier, der skal aktiveres (Bloker), deaktiveres, advares eller aktiveres i overvågningstilstand, er:

- 0: Deaktiver (deaktiver ASR-reglen)
- 1 : Blok (aktivér ASR-reglen)
- 2: Overvågning (evaluer, hvordan ASR-reglen vil påvirke din organisation, hvis den er aktiveret)
- 6: Advar (aktivér ASR-reglen, men tillad, at slutbrugeren tilsidesætter blokken). Advarselstilstand er tilgængelig for de fleste ASR-regler.

Brug [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) CSP (Configuration Service Provider) til at tilføje udeladelser.

Eksempel:

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions`

`Value: c:\path|e:\path|c:\Exclusions.exe`

> [!NOTE]
> Sørg for at angive OMA-URI-værdier uden mellemrum.

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. I Microsoft Endpoint Configuration Manager skal du gå til **Assets and Compliance** \> **Endpoint Protection** \> **Windows Defender Exploit Guard**.

2. Vælg **Start** \> **Opret Exploit Guard-politik**.

3. Angiv et navn og en beskrivelse, vælg **Reduktion af angrebsoverflade**, og vælg **Næste**.

4. Vælg, hvilke regler der skal blokere eller overvåge handlinger, og vælg **Næste**.

5. Gennemse indstillingerne, og vælg **Næste** for at oprette politikken.

6. Når politikken er oprettet, skal du vælge **Luk**.

### <a name="group-policy"></a>Gruppepolitik

> [!WARNING]
> Hvis du administrerer dine computere og enheder med Intune, Configuration Manager eller en anden platform til administration på virksomhedsniveau, overskriver administrationssoftwaren eventuelle modstridende Gruppepolitik indstillinger ved start.

1. Åbn [administrationskonsollen Gruppepolitik](https://technet.microsoft.com/library/cc731212.aspx) Gruppepolitik, højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg **Rediger**.

2. I **editoren til Gruppepolitik administration** skal du gå til **Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **Microsoft Defender Exploit Guard** \> **reduktion af angrebsoverfladen**.

4. Vælg **Konfigurer regler for reduktion af angrebsoverfladen** , og vælg **Aktiveret**. Du kan derefter angive den individuelle tilstand for hver regel i indstillingsafsnittet. Vælg **Vis...** og angiv regel-id'et i kolonnen **Værdinavn** og din valgte tilstand i kolonnen **Værdi** på følgende måde:

   - 0: Deaktiver (deaktiver ASR-reglen)
   - 1 : Blok (aktivér ASR-reglen)
   - 2: Overvågning (evaluer, hvordan ASR-reglen vil påvirke din organisation, hvis den er aktiveret)
   - 6: Advar (aktivér ASR-reglen, men tillad, at slutbrugeren springer blokken over)

   :::image type="content" source="images/asr-rules-gp.png" alt-text="ASR-regler i Gruppepolitik" lightbox="images/asr-rules-gp.png":::

5. Hvis du vil udelade filer og mapper fra ASR-regler, skal du vælge indstillingen **Udelad filer og stier fra regler for reduktion af angrebsoverfladen** og angive indstillingen til **Aktiveret**. Vælg **Vis** , og angiv hver fil eller mappe i kolonnen **Værdinavn** . Angiv **0** i kolonnen **Værdi** for hvert element.

   > [!WARNING]
   > Brug ikke anførselstegn, da de ikke understøttes for hverken kolonnen **Value name** eller kolonnen **Value** .

### <a name="powershell"></a>PowerShell

> [!WARNING]
> Hvis du administrerer dine computere og enheder med Intune, Configuration Manager eller en anden platform til administration på virksomhedsniveau, overskriver administrationssoftwaren alle modstridende PowerShell-indstillinger ved start. Hvis du vil give brugerne tilladelse til at definere værdien ved hjælp af PowerShell, skal du bruge indstillingen "Brugerdefineret" for reglen i administrationsplatformen.
> "Brugerdefineret" gør det muligt for en lokal administrator at konfigurere reglen.
> Indstillingen Brugerdefineret vises i følgende figur.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-user-defined.png" alt-text="Indstillingen Aktivér for sikkerhed med legitimationsoplysninger" lightbox="images/asr-user-defined.png":::

1. Skriv **powershell** i menuen Start, højreklik **Windows PowerShell**, og vælg **Kør som administrator**.

2. Skriv en af følgende cmdlet'er. (Se [Reference til regler for reduktion af angrebsoverfladen](attack-surface-reduction-rules-reference.md) for at få flere oplysninger, f.eks. regel-id).

    ```PowerShell
    Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Enabled
    ```

    Hvis du vil aktivere ASR-regler i overvågningstilstand, skal du bruge følgende cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
    ```

    Hvis du vil aktivere ASR-regler i advarselstilstand, skal du bruge følgende cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Warn
    ```

    Hvis du vil aktivere ASR Bloker misbrug af udnyttede sårbare signerede drivere, skal du bruge følgende cmdlet:

   ```PowerShell
   Add-MpPreference -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Enabled
   ```

    Hvis du vil slå ASR-regler fra, skal du bruge følgende cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Disabled
    ```

    > [!IMPORTANT]
    > Du skal angive tilstanden enkeltvist for hver regel, men du kan kombinere regler og tilstande på en kommasepareret liste.
    >
    > I følgende eksempel aktiveres de første to regler, den tredje regel deaktiveres, og den fjerde regel aktiveres i overvågningstilstand:
    >
    > ```PowerShell
    > Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID 1>,<rule ID 2>,<rule ID 3>,<rule ID 4> -AttackSurfaceReductionRules_Actions Enabled, Enabled, Disabled, AuditMode
    > ```

    Du kan også bruge `Add-MpPreference` PowerShell-verbet til at føje nye regler til den eksisterende liste.

    > [!WARNING]
    > `Set-MpPreference` overskriver altid det eksisterende sæt regler. Hvis du vil føje til det eksisterende sæt, skal du i stedet bruge `Add-MpPreference` .
    > Du kan få en liste over regler og deres aktuelle tilstand ved hjælp `Get-MpPreference`af .

3. Hvis du vil udelade filer og mapper fra ASR-regler, skal du bruge følgende cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Fortsæt med at bruge `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` til at føje flere filer og mapper til listen.

    > [!IMPORTANT]
    > Bruges `Add-MpPreference` til at tilføje eller føje apps til listen. Hvis du bruger cmdlet'en `Set-MpPreference` , overskrives den eksisterende liste.

## <a name="related-articles"></a>Relaterede artikler

- [Reference til regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-reference.md)
- [Evaluer reduktion af angrebsoverflade](evaluate-attack-surface-reduction.md)
- [Ofte stillede spørgsmål om reduktion af angrebsoverflade](attack-surface-reduction.md)
