---
title: Regler for testreduktion af angrebsoverflade
description: Indeholder en vejledning i, hvordan du tester installationen af asr-regler (attack surface reduction).
keywords: Installation af regler for reduktion af angrebsoverfladen, ASR-installation, aktivér asr-regler, konfigurer ASR, forebyggelsessystem for værtsindtrængen, beskyttelsesregler, regler for bekæmpelse af udnyttelse, anti-exploit, udnyttelsesregler, regler til forebyggelse af infektion, Microsoft Defender for Endpoint, konfigurer ASR-regler
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
ms.collection:
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 8bfe3e0d36a02831b5673b92217152ce87804d0a
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/01/2022
ms.locfileid: "66601284"
---
# <a name="test-attack-surface-reduction-asr-rules"></a>Regler for testreduktion af angrebsoverflade

Test af ASR-regler (Attack Surface Reduction) hjælper dig med at afgøre, om regler vil forhindre line of business-handlinger, før du aktiverer en regel. Ved at starte med en lille kontrolleret gruppe kan du begrænse potentielle arbejdsafbrydelser, når du udvider din udrulning på tværs af organisationen.

Begynd udrulningen af dine ASR-regler (Attack Surface Reduction) med ring 1.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-testing-steps.png" alt-text="Testtrinnene for ASR-regler" lightbox="images/asr-rules-testing-steps.png":::
  
## <a name="step-1-test-asr-rules-using-audit"></a>Trin 1: Test ASR-regler ved hjælp af Overvågning

Begynd testfasen ved at aktivere ASR-reglerne med de regler, der er angivet til Overvågning, startende med dine mesterbrugere eller enheder i ring 1. Anbefalingen er typisk, at du aktiverer alle reglerne (i Overvågning), så du kan afgøre, hvilke regler der udløses i testfasen. Bemærk, at regler, der er angivet til Overvågning, generelt ikke påvirker funktionaliteten af den eller de enheder, som reglen anvendes på, men genererer logførte hændelser til evalueringen. der ikke er nogen effekt på slutbrugerne.

### <a name="configure-asr-rules-using-mem"></a>Konfigurer ASR-regler ved hjælp af MEM

Du kan bruge Microsoft Endpoint Manager (MEM) Endpoint Security til at konfigurere brugerdefinerede ASR-regler.

1. Åbn [Microsoft Endpoint Manager Administration](https://endpoint.microsoft.com/#home).
2. Gå til **slutpunktets overfladereduktion****af sikkerhedsangreb** > .
3. Vælg **Opret politik**.
4. Vælg **Windows 10 og nyere** i **Platform**, og vælg **Regler for reduktion af angrebsoverflade** under **Profil**.
  
    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/asr-mem-create-profile.png" alt-text="Siden til oprettelse af profil for ASR-regler" lightbox="images/asr-mem-create-profile.png":::

5. Klik på **Opret**.
6. Under fanen **Grundlæggende** i ruden **Opret profil** under **Navn** skal du tilføje et navn til din politik. I **Beskrivelse** skal du tilføje en beskrivelse af politikken for ASR-regler.
7. Under fanen **Konfigurationsindstillinger** under **Regler for reduktion af angrebsoverflade** skal du angive alle regler til **Overvågningstilstand**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/asr-mem-configuration-settings.png" alt-text="Konfigurationen af ASR-regler til overvågningstilstand" lightbox="images/asr-mem-configuration-settings.png":::

    >[!Note]
    >Der er variationer i nogle lister over ASR-regler. _Blokeret_ og _aktiveret_ giver den samme funktionalitet.

8. [Valgfri] I ruden **Områdekoder** kan du føje mærkeoplysninger til bestemte enheder. Du kan også bruge rollebaseret adgangskontrol og områdekoder til at sikre, at de rette administratorer har den rette adgang og synlighed til de rette Intune objekter. Få mere at vide: [Brug rollebaseret adgangskontrol (RBAC) og områdekoder til distribueret it i Intune](/mem/intune/fundamentals/scope-tags).
9. I ruden **Tildelinger** kan du installere eller "tildele" profilen til dine bruger- eller enhedsgrupper. Få mere at vide: [Tildel enhedsprofiler i Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)
10. Gennemse dine indstillinger i ruden **Gennemse + opret** . Klik på **Opret** for at anvende reglerne.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/asr-mem-review-create.png" alt-text="Siden Opret profil" lightbox="images/asr-mem-review-create.png":::

Din nye politik for reduktion af angrebsoverfladen for ASR-regler er angivet i **Endpoint Security | Reduktion af angrebsoverflade**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="images/asr-mem-my-asr-rules.png" alt-text=" Siden Til reduktion af angrebsoverfladen" lightbox="images/asr-mem-my-asr-rules.png":::

## <a name="step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Trin 2: Forstå rapporteringssiden for regler for reduktion af angrebsoverfladen på portalen Microsoft 365 Defender

Rapporteringssiden for ASR-regler findes i **Microsoft 365 Defender portalrapporter** >  > **regler for reduktion af angrebsoverfladen**. Denne side har tre faner:

- Opdagelser
- Konfiguration
- Tilføj udeladelser

### <a name="detections-tab"></a>Fanen Registreringer

Indeholder en 30-dages tidslinje over registrerede overvågnings- og blokerede hændelser.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-01.png" alt-text="Fanen Opdagelser af regler for reduktion af angrebsoverfladen" lightbox="images/asr-defender365-01.png":::

Ruden Regler for reduktion af Angrebsoverflade indeholder en oversigt over registrerede hændelser pr. regel.

>[!Note]
>Der er nogle variationer i rapporter over ASR-regler. Microsoft er i gang med at opdatere funktionsmåden for ASR-regelrapporterne for at give en ensartet oplevelse.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-01b.png" alt-text="Siden Regler for reduktion af angrebsoverfladen" lightbox="images/asr-defender365-01b.png"::: 

Klik på **Vis registreringer** for at åbne fanen **Registreringer** .

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-reports-detections.png" alt-text="Registreringer af regler for reduktion af angrebsoverfladen" lightbox="images/asr-defender365-reports-detections.png":::

Ruden **GroupBy** og **Filter** indeholder følgende indstillinger:

**GroupBy** returnerer resultater, der er angivet til følgende grupper:

- Ingen gruppering
- Registreret fil
- Overvåg eller bloker
- Regel
- Kildeapp
- Enhed
- Bruger
- Publisher

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-reports-detections.png" alt-text="Reglerne for reduktion af angrebsoverfladen registrerer GroupBy-filteret" lightbox="images/asr-defender365-reports-detections.png":::

**Filter** åbner siden **Filtrer efter regler** , hvilket giver dig mulighed for kun at afgrænse resultaterne til de valgte ASR-regler:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-filter.png" alt-text="Reglerne for reduktion af angrebsoverfladen filtrerer efter regler" lightbox="images/asr-defender365-filter.png":::

>[!Note]
>Hvis du har en Microsoft 365 Security E5- eller A5-, Windows E5- eller A5-licens, åbner følgende link Microsoft Defender 365 Reports > [Attack surface reductions](https://security.microsoft.com/asr?viewid=detections) > fanen Detections.

### <a name="configuration-tab"></a>Fanen Konfiguration

Lister – pr. computer – den samlede tilstand af ASR-regler: Fra, Overvågning, Bloker.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-configurations.png" alt-text="Fanen Konfiguration af regler for reduktion af angrebsoverfladen og en post på siden" lightbox="images/asr-defender365-configurations.png":::

Under fanen Konfigurationer kan du – pr. enhed – kontrollere, hvilke ASR-regler der er aktiveret, og i hvilken tilstand, ved at vælge den enhed, du vil gennemse ASR-regler for.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-configurations.settings.png" alt-text="Regler for reduktion af angrebsoverfladen aktiveret og tilstand" lightbox="images/asr-defender365-configurations.settings.png":::

Linket **Introduktion** åbner Microsoft Endpoint Manager Administration, hvor du kan oprette eller redigere en politik for beskyttelse af slutpunkter for ASR:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem1.png" alt-text="*Menupunktet Sikkerhed for slutpunkt på siden Oversigt" lightbox="images/asr-defender365-05b-mem1.png":::

I | for slutpunktssikkerhed Oversigt, vælg **Reduktion af angrebsoverflade**:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem2.png" alt-text="Reduktion af angrebsoverfladen i MEM" lightbox="images/asr-defender365-05b-mem2.png":::

Endpoint Security-| Ruden Reduktion af angrebsoverfladen åbnes:

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-defender365-05b-mem3.png" alt-text="Ruden Reduktion af overfladereduktion af slutpunktssikkerhedsangreb" lightbox="images/asr-defender365-05b-mem3.png":::

>[!Note]
>Hvis du har en Licens til Microsoft Defender 365 E5 (eller Windows E5?), åbnes Microsoft Defender 365 Reports > Reduktioner af angrebsoverfladen > fanen [Konfigurationer](https://security.microsoft.com/asr?viewid=configuration) .

### <a name="add-exclusions"></a>Tilføj udeladelser

Denne fane indeholder en metode til at vælge registrerede objekter (f.eks. falske positiver) til udeladelse. Når der tilføjes undtagelser, indeholder rapporten en oversigt over den forventede virkning.

>[!Note]
> Microsoft Defender Antivirus AV-undtagelser er omfattet af ASR-regler.  Se [Konfigurer og valider udeladelser baseret på filtypenavn, navn eller placering](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

> [!div class="mx-imgBorder"]
> :::image type="content" source="Images/asr-defender365-06d.png" alt-text="Ruden til udeladelse af den registrerede fil" lightbox="Images/asr-defender365-06d.png":::

> [!Note]
>Hvis du har en Microsoft Defender 365 E5- (eller Windows E5?)-licens, åbnes Microsoft Defender 365 Reports > Surface Reductions > fanen [Exclusions](https://security.microsoft.com/asr?viewid=exclusions) .

### <a name="use-powershell-as-an-alternative-method-to-enable-asr-rules"></a>Brug PowerShell som en alternativ metode til at aktivere ASR-regler

Du kan bruge PowerShell – som et alternativ til MEM – til at aktivere ASR-regler i overvågningstilstand for at få vist en post over apps, der ville være blevet blokeret, hvis funktionen var fuldt aktiveret. Du kan også få en idé om, hvor ofte reglerne vil blive anvendt under normal brug.

Hvis du vil aktivere en regel for reduktion af angrebsoverfladen i overvågningstilstand, skal du bruge følgende PowerShell-cmdlet:

```PowerShell
Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
```

Hvor `<rule ID>` er en [GUID-værdi for reglen for reduktion af angrebsoverfladen](attack-surface-reduction-rules-reference.md).

Hvis du vil aktivere alle de tilføjede regler for reduktion af angrebsoverfladen i overvågningstilstand, skal du bruge følgende PowerShell-cmdlet:

```PowerShell
(Get-MpPreference).AttackSurfaceReductionRules_Ids | Foreach {Add-MpPreference -AttackSurfaceReductionRules_Ids $_ -AttackSurfaceReductionRules_Actions AuditMode}
```

> [!TIP]
> Hvis du vil overvåge fuldt ud, hvordan regler for reduktion af angrebsoverfladen fungerer i din organisation, skal du bruge et administrationsværktøj til at installere denne indstilling på enheder på dine netværk.

Du kan også bruge Gruppepolitik, Intune eller MDM-udbydere (Mobile Device Management) til at konfigurere og installere indstillingen. Få mere at vide i artiklen om [reduktion af angrebsoverfladen](attack-surface-reduction.md) .

## <a name="use-windows-event-viewer-review-as-an-alternative-to-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Brug Windows Logbog review som et alternativ til rapporteringssiden for regler for reduktion af angreb på Microsoft 365 Defender-portalen

Hvis du vil gennemse apps, der ville være blevet blokeret, skal du åbne Logbog og filtrere efter Event ID 1121 i Microsoft-Windows-Windows Defender/Operational log. I følgende tabel vises alle netværksbeskyttelseshændelser.

Hændelses-id | Beskrivelse
-|-
 5007 | Hændelse, når indstillingerne ændres
 1121 | Hændelse, når en regel for reduktion af angrebsoverfladen udløses i bloktilstand
 1122 | Hændelse, når en regel for reduktion af angrebsoverfladen udløses i overvågningstilstand

## <a name="additional-topics-in-this-deployment-collection"></a>Yderligere emner i denne installationssamling

[Udrulningsoversigt til reduktion af angrebsoverflade (ASR)](attack-surface-reduction-rules-deployment.md)

[Planlæg udrulning af reduktion af angrebsoverflade (ASR)](attack-surface-reduction-rules-deployment-plan.md)

[Aktiver regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-implement.md)

[Operationaliser regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-operationalize.md)

[Henvisning til regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-reference.md)
