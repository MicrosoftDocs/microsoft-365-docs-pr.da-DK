---
title: Aktivér regler for reduktion af angrebsoverfladen
description: Aktivér ASR-regler (Attack Surface Reduction) for at beskytte dine enheder mod angreb, der bruger makroer, scripts og almindelige indlægningsteknikker.
keywords: Reduktion af angrebsoverfladen, hips, vær vært for forebyggelse af indtrængen, beskyttelsesregler, antiexploit, udnyttelse, forebyggelse af virus, aktivér, aktivér
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
ms.openlocfilehash: 929ecd109d110c9a4578b39fbc69ed65c0b7d116
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682609"
---
# <a name="enable-attack-surface-reduction-rules"></a>Aktivér regler for reduktion af angrebsoverfladen

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Regler for reduktion af angrebsoverfladen](attack-surface-reduction.md) (ASR-regler) hjælper med at forhindre handlinger, som malware ofte misbruger for at kompromittere enheder og netværk.

## <a name="requirements"></a>Krav

Reduktionsfunktioner til angrebsoverfladen på tværs Windows versioner

Du kan angive reduktionsregler for angrebsoverfladen for enheder, der kører en af følgende versioner og versioner af Windows:

- Windows 10 Pro, [version 1709](/windows/whats-new/whats-new-windows-10-version-1709) eller nyere
- Windows 10 Enterprise, [version 1709](/windows/whats-new/whats-new-windows-10-version-1709) eller nyere
- Windows Server, [version 1803 (halvårlige kanal)](/windows-server/get-started/whats-new-in-windows-server-1803) eller senere
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/windows/win32/srvnodes/what-s-new-for-windows-server-2012-r2)
- Windows Server 2022

Hvis du vil bruge hele funktionssættet af reduktionsregler for angrebsoverfladen, skal du bruge:

- Windows Defender Antivirus som primær AV (beskyttelse i realtid er til)
- [Beskyttelse mod skylevering på](/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) (visse regler kræver dette)
- Windows 10 Enterprise E5- eller E3-licens

Selvom regler for reduktion af angrebsoverfladen ikke kræver en [Windows E5-licens](/windows/deployment/deploy-enterprise-licenses) med en Windows E5-licens, får du avancerede administrationsfunktioner, herunder overvågning, analyse og arbejdsprocesser, der er tilgængelige i Defender til slutpunkt samt rapporterings- og konfigurationsfunktioner i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>. Disse avancerede funktioner er ikke tilgængelige med en E3-licens, men du kan stadig bruge Event Viewer til at gennemse hændelser til reduktion af angrebsoverfladen.

Hver ASR-regel indeholder én af fire indstillinger:

- **Ikke konfigureret** |  **Deaktiveret**: Deaktivere ASR-reglen
- **Bloker**: Aktivér ASR-reglen
- **Overvågning**: Evaluer, hvordan ASR-reglen påvirker organisationen, hvis den er aktiveret
- **Advarsel**: Aktivér ASR-reglen, men tillad slutbrugeren at tilsidesætte blokken

> [!IMPORTANT]
> Tilstanden Advarsel understøttes i øjeblikket ikke for tre ASR-regler, når du konfigurerer ASR-regler i Microsoft Endpoint Manager (MEM). Du kan få mere at vide under [Tilfælde, hvor advarselstilstand ikke understøttes](attack-surface-reduction.md#cases-where-warn-mode-is-not-supported).

Vi anbefaler, at du bruger ASR-regler med en Windows E5-licens (eller lignende licenserings-SKU) for at drage fordel af de avancerede overvågnings- og rapporteringsfunktioner, der er tilgængelige i [Microsoft Defender til slutpunkt](microsoft-defender-endpoint.md) (Defender til slutpunkt). Men hvis du har en anden licens, f.eks. Windows Professional eller Windows E3, som ikke omfatter avancerede overvågnings- og rapporteringsfunktioner, kan du udvikle dine egne overvågnings- og rapporteringsværktøjer ud over de hændelser, der genereres på hvert slutpunkt, når der udløses ASR-regler (f.eks. Hændelses videresendelse).

> [!TIP]
> Du kan få mere at Windows om licenser i [Windows 10 licensering](https://www.microsoft.com/licensing/product-licensing/windows10?activetab=windows10-pivot:primaryr5), og få [vejledningen volumenlicens til Windows 10](https://download.microsoft.com/download/2/D/1/2D14FE17-66C2-4D4C-AF73-E122930B60F6/Windows-10-Volume-Licensing-Guide.pdf).

Du kan aktivere regler for reduktion af angrebsoverfladen ved hjælp af en af disse metoder:

- [Microsoft Intune](#intune)
- [Administration af mobilenheder (MDM)](#mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Gruppepolitik](#group-policy)
- [PowerShell](#powershell)

Virksomhedsstyring som f.eks. Intune eller Microsoft Endpoint Manager anbefales. Enterprise-level management vil overskrive eventuelle modstridende Gruppepolitik eller PowerShell-indstillinger ved opstart.

## <a name="exclude-files-and-folders-from-asr-rules"></a>Udelad filer og mapper fra ASR-regler

Du kan udelukke filer og mapper fra at blive evalueret af de fleste regler for reduktion af angrebsoverfladen. Det betyder, at selvom en ASR-regel bestemmer, at filen eller mappen indeholder skadelig funktionsmåde, blokeres filen ikke, så den ikke kan køre. Dette kan potentielt tillade, at usikre filer kan køre og inficere dine enheder.

Du kan også udelukke ASR-regler fra at udløse baseret på certifikat- og filhashes ved at tillade den angivne Defender for Endpoint-fil og certifikatindikatorer. (Se [Administrer](manage-indicators.md) indikatorer).

> [!IMPORTANT]
> Udelukkelse af filer eller mapper kan reducere beskyttelsen i henhold til ASR-regler alvorligt. Ekskluderede filer får tilladelse til at køre, og der optages ingen rapport eller hændelse.
> Hvis ASR-regler registrerer filer, som du mener ikke bør detekteres, skal du først bruge [overvågningstilstand til at teste reglen](evaluate-attack-surface-reduction.md).

Du kan angive individuelle filer eller mapper (ved hjælp af mappestier eller fuldt kvalificerede ressourcenavne), men du kan ikke angive, hvilke regler udeladelseerne skal gælde for. En udeladelse anvendes kun, når det ekskluderede program eller den ekskluderede tjeneste starter. Hvis du f.eks. tilføjer en udeladelse for en opdateringstjeneste, der allerede kører, fortsætter opdateringstjenesten med at udløse hændelser, indtil tjenesten stoppes og genstartes.

ASR-regler understøtter miljøvariabler og jokertegn. Du kan finde oplysninger om brug af jokertegn i [Brug jokertegn i filnavnet og mappestien eller udeladelseslister for filtypenavnet](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).

## <a name="policy-conflict"></a>Politikkonflikt

1. Hvis der anvendes en modstridende politik via MDM og GP, har den indstilling, der anvendes fra MDM, forrang.

2. Regler for reduktion af angrebsoverfladen for MEM-administrerede enheder understøtter nu adfærd i forbindelse med fusion af indstillinger fra forskellige politikker for at oprette et supersæt af politikker for hver enhed. Kun de indstillinger, der ikke er modstridende, flettes, mens de indstillinger, der er i konflikt, ikke føjes til oversættet af regler. Tidligere, hvis to politikker indeholdt konflikter for en enkelt indstilling, blev begge politikker markeret som værende i konflikt, og der blev ikke installeret nogen indstillinger fra nogen af profilerne. Funktionsmåden for reduktion af antallet af angrebsoverfladen ved fletning af regler er som følger:
   - Regler for reduktion af angrebsoverfladen fra følgende profiler evalueres for hver enhed, som reglerne gælder for:
     - Enheder > konfigurationspolitik > profil til slutpunktsbeskyttelse > **Microsoft Defender Exploit Guard** >  [Attack Surface-reduktion](/mem/intune/protect/endpoint-protection-windows-10#attack-surface-reduction-rules).
     - Sikkerhedspolitik for slutpunkter > **reduktion af angrebsoverfladenRegler** >  [for reduktion afackoverfladen](/mem/intune/protect/endpoint-security-asr-policy#devices-managed-by-intune).
     - Slutpunktssikkerhed > grundlinjer for sikkerhed > **Microsoft Defender ATP BaselineAttack** >  [Surface-reduktionsregler](/mem/intune/protect/security-baseline-settings-defender-atp#attack-surface-reduction-rules).
   - Indstillinger der ikke har konflikter, føjes til et oversæt af politikker for enheden.
   - Når to eller flere politikker har modstridende indstillinger, føjes de modstridende indstillinger ikke til den kombinerede politik, mens de indstillinger, der ikke er i konflikt, føjes til supersætpolitikken, der gælder for en enhed.
   - Det er kun konfigurationerne for modstridende indstillinger, der holdes tilbage.

## <a name="configuration-methods"></a>Konfigurationsmetoder

Dette afsnit indeholder konfigurationsoplysninger om følgende konfigurationsmetoder:

- [Intune](#intune)
- [MEM](#mem)
- [MDM](#mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Gruppepolitik](#group-policy)
- [PowerShell](#powershell)

Følgende procedurer for aktivering af ASR-regler omfatter instruktioner til at udelukke filer og mapper.

### <a name="intune"></a>Intune

#### <a name="device-configuration-profiles"></a>Enhedskonfigurationsprofiler

1. Vælg **Enhedskonfigurationsprofiler**\>. Vælg en eksisterende profil til slutpunktsbeskyttelse, eller opret en ny. Hvis du vil oprette en ny, skal **du vælge Opret** profil og angive oplysninger for denne profil. Under **Profiltype skal** du vælge **Slutpunktsbeskyttelse**. Hvis du har valgt en eksisterende profil, skal du **vælge Egenskaber** og derefter vælge **Indstillinger**.

2. I **ruden Endpoint protection** skal du vælge **Windows Defender Exploit Guard** og derefter vælge **Reduktion af angrebsoverfladen**. Vælg den ønskede indstilling for hver ASR-regel.

3. Under **Undtagelser til reduktion af angrebsoverfladen** skal du angive individuelle filer og mapper. Du kan også vælge **Importér for** at importere en CSV-fil, der indeholder filer og mapper, som skal udelukkes fra ASR-regler. Hver linje i CSV-filen skal formateres således:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Vælg **OK** i de tre konfigurationsruder. Vælg derefter **Opret** , hvis du opretter en ny slutpunktsbeskyttelsesfil eller **Gem** , hvis du redigerer en eksisterende.

#### <a name="endpoint-security-policy"></a>Slutpunktssikkerhedspolitik**

1. Vælg **Endpoint Security Attack** \> **Surface-reduktion**. Vælg en eksisterende ASR-regel, eller opret en ny. Hvis du vil oprette en ny, skal **du vælge Opret** politik og angive oplysninger for denne profil. For **Profiltype skal** du vælge **Regler for reduktion af angrebsoverfladen**. Hvis du har valgt en eksisterende profil, skal du **vælge Egenskaber** og derefter vælge **Indstillinger**.

2. I **ruden Konfigurationsindstillinger** skal du vælge **Reduktion af angrebsoverfladen** og derefter vælge den ønskede indstilling for hver ASR-regel.

3. Angiv **individuelle filer** og mapper under Liste over yderligere mapper, der skal være beskyttet, Liste over **apps**, der har adgang til beskyttede mapper og Udelad filer og stier fra reduktionsregler for angrebsoverfladen. Du kan også vælge **Importér for** at importere en CSV-fil, der indeholder filer og mapper, som skal udelukkes fra ASR-regler. Hver linje i CSV-filen skal formateres således:

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Vælg **Næste** på de tre konfigurationsruder, og vælg  derefter Opret, hvis du opretter en ny politik,  eller Gem, hvis du redigerer en eksisterende politik.

### <a name="mem"></a>MEM

Du kan bruge Microsoft Endpoint Manager (MEM) OMA-URI til at konfigurere brugerdefinerede ASR-regler. I følgende procedure bruges reglen [Bloker misbrug af udnyttet sårbar signerede drivere](attack-surface-reduction-rules-reference.md#block-abuse-of-exploited-vulnerable-signed-drivers) i eksemplet.

1. Åbn Microsoft Endpoint Manager Administration (MEM). I menuen **Hjem skal** du klikke  **på Enheder**, vælge **Konfigurationsprofiler** og derefter klikke på **Opret profil**.

   > [!div class="mx-imgBorder"]
   > ![MEM Opret profil.](images/mem01-create-profile.png)

2. Vælg **følgende i** Opret en profil på følgende to rullelister:

   - I **Platform** skal du **vælge Windows 10 og nyere**
   - I **Profiltype skal** du vælge **Skabeloner**
   - Hvis DER allerede er angivet ASR-regler via slutpunktssikkerhed, skal du **i Profiltype** **vælge Indstillinger Katalog**.

   Vælg **Brugerdefineret**, og vælg derefter **Opret**.

   > [!div class="mx-imgBorder"]
   > ![Profilattributter for MEM-regel.](images/mem02-profile-attributes.png)

3. Værktøjet Brugerdefineret skabelon åbnes til trin **1 Grundlæggende.** I **1 Grundlæggende skal** du i **Navn** skrive et navn til skabelonen, og i **Beskrivelse** kan du skrive en beskrivelse (valgfrit).

   > [!div class="mx-imgBorder"]
   > ![GRUNDLÆGGENDE MEM-attributter.](images/mem03-1-basics.png)

4. Klik på **Næste**. Trin **2 Konfigurationsindstillinger** åbnes. For OMA-URI-Indstillinger du klikke på **Tilføj**. Der vises nu to muligheder: **Tilføj** og **Eksportér**.

   > [!div class="mx-imgBorder"]
   > ![Mem-konfigurationsindstillinger.](images/mem04-2-configuration-settings.png)

5. Klik **på Tilføj** igen. **Tilføjelsesrækken OMA-URI Indstillinger** åbnes. Gør **følgende** i Tilføj række:

   - Skriv **et** navn til reglen under Navn.
   - Skriv **en** kort beskrivelse under Beskrivelse.
   - I **OMA-URI skal** du skrive eller indsætte den specifikke OMA-URI-kæde for den regel, du tilføjer. Se afsnittet MDM i denne artikel, hvis OMA-URI'en skal bruges i denne eksempelregel. Du kan finde oplysninger om reduktion af angrebsoverfladens regel GUIDS i [beskrivelserne](attack-surface-reduction-rules-reference.md#per-rule-descriptions) af de forskellige regler i dette emne: Regler for reduktion af angrebsoverfladen.
   - Vælg **Streng i Datatype**.
   - I **Værdi** skal du skrive eller indsætte GUID-værdien, \= fortegnet og værdien Stat uden mellemrum (_GUID=StateValue_). Hvor:

     - 0: Deaktiver (deaktiver ASR-reglen)
     - 1: Bloker (Aktivér ASR-reglen)
     - 2: Overvågning (Evaluer, hvordan ASR-reglen påvirker din organisation, hvis den er aktiveret)
     - 6: Advar (Aktivér ASR-reglen, men tillad slutbrugeren at tilsidesætte blokeringen)

   > [!div class="mx-imgBorder"]
   > ![MEM OMA-URI-konfiguration.](images/mem05-add-row-oma-uri.png)

6. Vælg **Gem**. **Tilføj række** lukkes. I **Brugerdefineret** skal du vælge **Næste**. I trin **3 Omfangsmærker** er omfangsmærker valgfrie. Gør et af følgende:

   - Vælg **Vælg omfangsmærker**, vælg områdemærket (valgfrit), og vælg derefter **Næste**.
   - Eller vælg **Næste**

7. På trin **4 Opgaver i** **Inkluderede grupper** for de grupper, denne regel skal anvendes for, skal du vælge mellem følgende indstillinger:

   - **Tilføj grupper**
   - **Tilføj alle brugere**
   - **Tilføj alle enheder**

   > [!div class="mx-imgBorder"]
   > ![MEM-opgaver.](images/mem06-4-assignments.png)

8. I **grupperne Udeladt** skal du vælge de grupper, som du vil udelukke fra denne regel, og derefter vælge **Næste**.

9. I trin **5 Regler for anvendelse** af følgende indstillinger skal du gøre følgende:

   - I **Regel skal** du vælge **enten Tildel profil**, hvis **eller Tildel ikke profil, hvis**
   - I **Egenskab** skal du vælge den egenskab, som reglen skal anvendes på
   - I **Værdi skal** du angive den relevante værdi eller værdiområdet

   > [!div class="mx-imgBorder"]
   > ![MEM-anvendelsesregler.](images/mem07-5-applicability-rules.png)

10. Vælg **Næste**. I trin **6 Gennemgå + opret** skal du gennemgå de indstillinger og oplysninger, du har valgt og angivet, og derefter vælge **Opret**.

    > [!div class="mx-imgBorder"]
    > ![Gennemse og opret i MEM.](images/mem08-6-review-create.png)

    > [!NOTE]
    > Regler er aktive og live inden for få minutter.

> [!NOTE]
> Håndtering af konflikter:
>
> Hvis du tildeler en enhed to forskellige asr-politikker, er måden, som konflikt håndteres på, regler, der er tildelt forskellige tilstande, der ikke er nogen konfliktstyring på plads, og resultatet er en fejl.
>
> Regler, der ikke er i konflikt, medfører ikke en fejl, og reglen anvendes korrekt. Resultatet er, at den første regel anvendes, og efterfølgende regler, der ikke er i konflikt, flettes ind i politikken.

### <a name="mdm"></a>MDM

Brug [konfigurationen ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductionrules) serviceudbyder til individuelt at aktivere og angive tilstanden for hver regel.

Følgende er en referenceprøve, der bruger GUID-værdier for reference [til reduktionsregler for angrebsoverfladen](attack-surface-reduction-rules-reference.md).

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules`

`Value: 75668c1f-73b5-4cf0-bb93-3ecf5cb7cc84=2|3b576869-a4ec-4529-8536-b80a7769e899=1|d4f940ab-401b-4efc-aadc-ad5f3c50688a=2|d3e037e1-3eb8-44c8-a917-57927947596d=1|5beb7efe-fd9a-4556-801d-275e5ffc04cc=0|be9ba2d9-53ea-4cdc-84e5-9b1eeee46550=1`

Værdierne, der skal aktiveres (Bloker), deaktivere, advare eller aktivere i overvågningstilstand er:

- 0: Deaktiver (deaktiver ASR-reglen)
- 1: Bloker (Aktivér ASR-reglen)
- 2: Overvågning (Evaluer, hvordan ASR-reglen påvirker din organisation, hvis den er aktiveret)
- 6: Advar (Aktivér ASR-reglen, men tillad slutbrugeren at tilsidesætte blokken). Advarselstilstand er tilgængelig for de fleste asr-regler.

Brug [konfigurationen ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) serviceudbyder (CSP) til at tilføje udeladelser.

Eksempel:

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions`

`Value: c:\path|e:\path|c:\Exclusions.exe`

> [!NOTE]
> Sørg for at angive OMA-URI-værdier uden mellemrum.

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. I Microsoft Endpoint Configuration Manager skal du gå **til Assets and Compliance Endpoint Protection** \>  \> **Windows Defender Exploit Guard**.

2. Vælg **Home** \> **Create Exploit Guard-politik**.

3. Angiv et navn og en beskrivelse, vælg **Reduktion af angrebsoverfladen**, og vælg **Næste**.

4. Vælg, hvilke regler der skal blokere eller overvåge handlinger, og vælg **Næste**.

5. Gennemse indstillingerne, og vælg **Næste for** at oprette politikken.

6. Når politikken er oprettet, skal du vælge **Luk**.

### <a name="group-policy"></a>Gruppepolitik

> [!WARNING]
> Hvis du administrerer dine computere og enheder med Intune, Konfigurationsstyring eller andre virksomhedsadministrationsplatform, overskriver administrationssoftwaren eventuelle modstridende Gruppepolitik indstillingerne ved opstart.

1. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik Administrationskonsol](https://technet.microsoft.com/library/cc731212.aspx), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og vælge **Rediger**.

2. I **administrationseditoren Gruppepolitik** skal du gå til **Computerkonfiguration** og vælge **Administrative skabeloner**.

3. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** \> **Microsoft Defender Exploit Guard reduktion af** \> **angrebsoverfladen**.

4. Vælg **Konfigurer regler for reduktion af angrebsoverfladen,** og vælg **Aktiveret**. Du kan derefter angive den individuelle tilstand for hver regel i sektionen med indstillinger. Vælg **Vis...,** og angiv regel-id'et **i kolonnen Værdinavn** og den valgte tilstand i **kolonnen** Værdi på følgende måde:

   - 0: Deaktiver (deaktiver ASR-reglen)
   - 1: Bloker (Aktivér ASR-reglen)
   - 2: Overvågning (Evaluer, hvordan ASR-reglen påvirker din organisation, hvis den er aktiveret)
   - 6: Advar (Aktivér ASR-reglen, men tillad slutbrugeren at tilsidesætte blokeringen)

   :::image type="content" source="images/asr-rules-gp.png" alt-text="ASR-regler i Gruppepolitik.":::

5. Hvis du vil udelade filer og mapper fra ASR-regler, skal du vælge indstillingen Udeluk filer og stier fra reduktionsregler for **angrebsoverfladen** og angive indstillingen til **Aktiveret**. Vælg **Vis** , og angiv hver enkelt fil eller mappe i **kolonnen Værdinavn** . Angiv **0** i **kolonnen Værdi** for hvert element.

   > [!WARNING]
   > Brug ikke anførselstegn, da de ikke understøttes **hverken i kolonnen** Værdinavn eller **kolonnen** Værdi.

### <a name="powershell"></a>PowerShell

> [!WARNING]
> Hvis du administrerer dine computere og enheder med Intune, Konfigurationsstyring eller en anden administrationsplatform på virksomhedsniveau, overskriver administrationssoftwaren eventuelle modstridende PowerShell-indstillinger ved opstart. For at give brugerne mulighed for at definere værdien ved hjælp af PowerShell skal du bruge indstillingen "Brugerdefineret" for reglen på administrationsplatformen.
> "Brugerdefineret" gør det muligt for en lokal administratorbruger at konfigurere reglen.
> Indstillingsindstillingen Brugerdefineret vises i følgende figur.

> [!div class="mx-imgBorder"]
> ![ASR aktiverer "Brugerdefineret"](images/asr-user-defined.png)

1. Skriv **powershell** i menuen Start, **højreklik på Windows PowerShell** og vælg **Kør som administrator**.

2. Skriv en af følgende cmdlet'er. Se Reference til regler [for reduktion af angrebsoverfladen](attack-surface-reduction-rules-reference.md) for at få flere oplysninger, f.eks. regel-id.)

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

    For at aktivere ASR Blokere misbrug af udnyttet sårbar signerede drivere skal du bruge følgende cmdlet:

   ```PowerShell
   Add-MpPreference -AttackSurfaceReductionRules_Ids 56a863a9-875e-4185-98a7-b882c64b5ce5 -AttackSurfaceReductionRules_Actions Enabled
   ```

    Hvis du vil deaktivere ASR-regler, skal du bruge følgende cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Disabled
    ```

    > [!IMPORTANT]
    > Du skal angive tilstanden enkeltvis for hver regel, men du kan kombinere regler og tilstande i en kommasepareret liste.
    >
    > I følgende eksempel aktiveres de to første regler, den tredje regel deaktiveres, og den fjerde regel aktiveres i overvågningstilstand:
    >
    > ```PowerShell
    > Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID 1>,<rule ID 2>,<rule ID 3>,<rule ID 4> -AttackSurfaceReductionRules_Actions Enabled, Enabled, Disabled, AuditMode
    > ```

    Du kan også bruge PowerShell-verbet `Add-MpPreference` til at føje nye regler til den eksisterende liste.

    > [!WARNING]
    > `Set-MpPreference` overskriver altid de eksisterende regler. Hvis du vil føje til det eksisterende sæt, skal du bruge det i `Add-MpPreference` stedet for.
    > Du kan få en liste over regler og deres aktuelle tilstand ved hjælp af `Get-MpPreference`.

3. Hvis du vil udelukke filer og mapper fra ASR-regler, skal du bruge følgende cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Fortsæt med at `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` bruge til at føje flere filer og mapper til listen.

    > [!IMPORTANT]
    > Bruges `Add-MpPreference` til at tilføje eller føje apps til listen. Hvis du `Set-MpPreference` bruger cmdlet'en, overskrives den eksisterende liste.

## <a name="related-articles"></a>Relaterede artikler

- [Reference til begrænsningsregler for angrebsoverfladen](attack-surface-reduction-rules-reference.md)
- [Evaluer reduktion af angrebsoverfladen](evaluate-attack-surface-reduction.md)
- [Ofte stillede spørgsmål om reduktion af angrebsoverfladen](attack-surface-reduction.md)
