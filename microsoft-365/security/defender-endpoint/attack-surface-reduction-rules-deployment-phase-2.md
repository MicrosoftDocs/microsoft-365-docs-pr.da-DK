---
title: ASR-regler for installationsfase 2 - test
description: Giver vejledning til test af dine regler for reduktion af angrebsoverfladen.
keywords: Implementering af regler for reduktion af angrebsoverfladen, ASR-installation, aktivér asr-regler, konfigurer ASR, beskyttelsessystem til forebyggelse af indtrængen, beskyttelsesregler, anti exploit, udnyttelsesregler, regler for forebyggelse af indtrængen, Microsoft Defender til slutpunkt, konfigurer ASR-regler
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: m365solution-scenario
ms.date: 1/18/2022
ms.openlocfilehash: cbcdee33fe9bc66c12c1bd060c69506595202ed9
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/02/2022
ms.locfileid: "63594094"
---
# <a name="asr-rules-deployment-phase-2-test"></a>ASR-regler for installationsfase 2: test

Start udrulningen af ASR-reglerne med ring 1.

> [!div class="mx-imgBorder"]
> ![Trin til test af ASR-regler](images/asr-rules-testing-steps.png)

## <a name="step-1-test-asr-rules-using-audit"></a>Trin 1: Test ASR-regler ved hjælp af Overvågning

Start testfasen ved at slå ASR-reglerne til med reglerne angivet til Overvågning, hvor du starter med dine bedste brugere eller enheder i ring 1. Det anbefales typisk, at du aktiverer alle reglerne (i Overvågning), så du kan bestemme, hvilke regler der udløses i testfasen. Bemærk, at regler, der er angivet til Overvågning, generelt ikke påvirker funktionaliteten i den eller de enheder, som reglen anvendes på, men genererer logførte hændelser for evalueringen; har det ingen indflydelse på slutbrugerne.

### <a name="configure-asr-rules-using-mem"></a>Konfigurere ASR-regler ved hjælp af MEM

Du kan bruge MEM-slutpunktssikkerhed (Microsoft Endpoint Manager) til at konfigurere brugerdefinerede ASR-regler.

1. Åbn [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com/#home)
2. Gå til **Endpoint SecurityAttack** >  **surface-reduktion**.
3. Vælg **Opret politik**.
4. I **Platform** skal du **Windows 10 og nyere**, og i **Profil** skal du vælge Regler for reduktion **af angrebsoverfladen**.
  
    > [!div class="mx-imgBorder"]
    > ![Konfigurere profil for ASR-regler](images/asr-mem-create-profile.png)

5. Klik **på Opret**.
6. På fanen **Grundlæggende i** ruden **Opret profil** i Navn **skal du tilføje** et navn til din politik. I **Beskrivelse skal** du tilføje en beskrivelse af din politik for asr-regler.
7. På fanen **Konfigurationsindstillinger** under Regler for **reduktion af angrebsoverfladen** skal du angive alle regler **til overvågningstilstand**.

    > [!div class="mx-imgBorder"]
    > ![Angiv ASR-regler til overvågningstilstand](images/asr-mem-configuration-settings.png)

    >[!Note]
    >Der er variationer i nogle asr-regeltilstandslister. _Blokeret_ _og aktiveret_ giver samme funktionalitet.

8. [Valgfrit] I **ruden Områdemærker** kan du føje mærkeoplysninger til bestemte enheder. Du kan også bruge rollebaseret adgangskontrol og omfangsmærker for at sikre, at de rette administratorer har den rigtige adgang og synlighed til de rette Intune-objekter. Få mere at [vide: Brug rollebaseret adgangskontrol (RBAC) og omfangsmærker for distribueret IT i Intune](/mem/intune/fundamentals/scope-tags).
9. I **ruden Opgaver** kan du installere eller "tildele" profilen til dine bruger- eller enhedsgrupper. Få mere at vide: [Tildel enhedsprofiler Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)
10. Gennemse dine indstillinger i **ruden Gennemse + opret** . Klik **på Opret** for at anvende reglerne.

   > [!div class="mx-imgBorder"]
   > ![Aktivér POLITIK for ASR-regler](images/asr-mem-review-create.png)

Din nye politik for reduktion af angrebsoverfladen for ASR-regler er angivet **i | Reduktion af angrebsoverfladen**.

   > [!div class="mx-imgBorder"]
   > ![Liste over ASR-regelpolitik](images/asr-mem-my-asr-rules.png)

## <a name="step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Trin 2: Forstå rapporteringssiden for reduktionsregler for angrebsoverfladen i Microsoft 365 Defender portal

Rapporteringssiden for ASR-regler findes **i Microsoft 365 Defender** **portalReportsAttack** >  >  **surface-reduktionsregler**. Denne side har tre faner:

- Registreringer
- Konfiguration
- Tilføj udeladelse

### <a name="detections-tab"></a>Fanen Registreringer

Indeholder en 30-dages tidslinje for registreret overvågning og blokerede hændelser.

> [!div class="mx-imgBorder"]
> ![Fane til registrering af regler for reduktion af angrebsoverfladen](images/asr-defender365-01.png)

Ruden med reduktionsregler for angrebsoverfladen giver en oversigt over registrerede hændelser pr. regel.

>[!Note]
>Der er nogle variationer i ASR-regelrapporter. Microsoft er i gang med at opdatere funktionsmåden af ASR-regelrapporterne for at give en ensartet oplevelse.

> [!div class="mx-imgBorder"]
> ![Registrering af regler for reduktion af angrebsoverfladen](images/asr-defender365-01b.png)

Klik **på Vis registreringer** for at **åbne fanen Registreringer** .

> [!div class="mx-imgBorder"]
> ![Registrering af regler for reduktion af angrebsoverfladen](images/asr-defender365-reports-detections.png)

**Ruden GroupBy** **og** Filter indeholder følgende indstillinger:

**GroupBy returnerer** resultater, der er indstillet til følgende grupper:

- Ingen gruppering
- Registreret fil
- Overvågning eller blokering
- Regel
- Kildeapp
- Enhed
- Bruger
- Publisher

> [!div class="mx-imgBorder"]
> ![Registrering af regler for reduktion af angrebsoverfladen GroupBy-filter](images/asr-defender365-reports-detections.png)

**Filter** åbner siden **Filtrer på regler** , hvor du kun kan begrænse resultaterne til de valgte ASR-regler:

> [!div class="mx-imgBorder"]
> ![Registreringer af regler for reduktion af angrebsoverfladen filtrerer på regler](images/asr-defender365-filter.png)

>[!Note]
>Hvis du har en Microsoft Microsoft 365 Security E5- eller A5-, Windows E5- eller A5-licens, åbner følgende link fanen Microsoft Defender 365-rapporter > [Attack Surface](https://security.microsoft.com/asr?viewid=detections) > Detections.

### <a name="configuration-tab"></a>Fanen Konfiguration

Lister – på computerbasis – den aggregerede tilstand for ASR-regler: Fra, Overvågning, Bloker.

> [!div class="mx-imgBorder"]
> ![Regel for reduktion af angrebsoverfladen, fanen Konfiguration](images/asr-defender365-configurations.png)

På fanen Konfigurationer kan du på basis af enheder kontrollere, hvilke ASR-regler der er aktiveret, og i hvilken tilstand, ved at vælge den enhed, du vil gennemse ASR-regler for.

> [!div class="mx-imgBorder"]
> ![Regler for reduktion af angrebsoverfladen aktiveret og i tilstanden](images/asr-defender365-configurations.settings.png)

Linket **Introduktion åbner** Microsoft Endpoint Manager Administration, hvor du kan oprette eller redigere en politik for slutpunktsbeskyttelse af asr:

> [!div class="mx-imgBorder"]
> ![Regler for reduktion af angrebsoverfladen i MEM](images/asr-defender365-05b-mem1.png)

I sikkerhedsindstillinger for slutpunkter | Oversigt, vælg **Reduktion af angrebsoverfladen**:

> [!div class="mx-imgBorder"]
> ![Reduktion af angrebsoverfladen i MEM](images/asr-defender365-05b-mem2.png)

Sikkerhedsindstillinger for slutpunkter | Ruden til reduktion af angrebsoverfladen åbnes:

> [!div class="mx-imgBorder"]
> ![Ruden Slutpunktssikkerhed asr](images/asr-defender365-05b-mem3.png)

>[!Note]
>Hvis du har en Microsoft Defender 365 E5-licens (eller Windows E5?), åbner dette link fanen Microsoft Defender 365 Reports > Attack Surface > på fanen [Konfigurationer](https://security.microsoft.com/asr?viewid=configuration).

### <a name="add-exclusions"></a>Tilføj udeladelse

Denne fane indeholder en metode til at vælge registrerede enheder (f.eks. falske positive) til udeladelse. Når der tilføjes udeladelse, indeholder rapporten en oversigt over den forventede virkning.

>[!Note]
> Microsoft Defender Antivirus for av-udeladelser overholdes af ASR-regler.  Se [Konfigurer og valider udeladelse baseret på filtypenavn, navn eller placering](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

> [!div class="mx-imgBorder"]
> ![Asr-værktøj til slutpunktssikkerhed](Images/asr-defender365-06d.png)

> [!Note]
>Hvis du har en Microsoft Defender 365 E5-licens (eller Windows E5?), åbner dette link fanen Microsoft Defender 365 Reports > Attack > surface på fanen Udeladelser.[](https://security.microsoft.com/asr?viewid=exclusions)

### <a name="use-powershell-as-an-alternative-method-to-enable-asr-rules"></a>Brug PowerShell som en alternativ metode til at aktivere ASR-regler

Du kan bruge PowerShell – som et alternativ til MEM – til at aktivere ASR-regler i overvågningstilstand for at få vist en post med apps, der ville være blevet blokeret, hvis funktionen var fuldt aktiveret. Du kan også få en ide om, hvor ofte reglerne udløses under normal brug.

For at aktivere reglen til reduktion af angrebsoverfladen i overvågningstilstand skal du bruge følgende PowerShell-cmdlet:

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

Hvor `<rule ID>` er en [GUID-værdi af reglen for reduktion af angrebsoverfladen](attack-surface-reduction-rules-reference.md).

For at aktivere alle reglerne for reduktion af angrebsoverfladen i overvågningstilstand skal du bruge følgende PowerShell-cmdlet:

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> Hvis du fuldt ud vil overvåge, hvordan reduktionsregler for angrebsoverfladen fungerer i din organisation, skal du bruge et administrationsværktøj til at udrulle denne indstilling på enheder i dit netværk.

Du kan også bruge Gruppepolitik-, Intune- eller MDM-konfigurationstjenesteudbydere (CSM) til at konfigurere og installere indstillingen. Få mere at vide i artiklen [om reduktionsregler for angrebsoverfladen](attack-surface-reduction.md) .

## <a name="use-windows-event-viewer-review-as-an-alternative-to-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Brug Windows Event Viewer Review som et alternativ til rapporteringssiden for reduktion af angrebsoverfladen på Microsoft 365 Defender portal

Hvis du vil gennemse apps, der ville være blevet blokeret, skal du åbne Logbog og filtrere efter Hændelses-id 1121 i Microsoft-Windows-Windows Defender/Driftslog. I følgende tabel vises alle netværksbeskyttelseshændelser.

Hændelses-id | Beskrivelse
-|-
 5007 | Hændelse, når indstillingerne ændres
 1121 | Hændelse, når en regel for reduktion af angrebsoverfladen udløses i bloktilstand
 1122 | Hændelse, når en regel for reduktion af angrebsoverfladen udløses i overvågningstilstand

## <a name="additional-topics-in-this-deployment-collection"></a>Flere emner i denne installationssamling

[Oversigt over ASR-regler for installation](attack-surface-reduction-rules-deployment.md)

[Fase 1: Plan](attack-surface-reduction-rules-deployment-phase-1.md)

[Fase 3: Implementer](attack-surface-reduction-rules-deployment-phase-3.md)

[Fase 4: Drift](attack-surface-reduction-rules-deployment-phase-4.md)
