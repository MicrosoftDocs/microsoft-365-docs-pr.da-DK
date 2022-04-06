---
title: Implementer installation af ASR-regler (Attack Surface Reduction)
description: Indeholder en vejledning i, hvordan du implementerer udrulningen af regler for reduktion af angrebsoverfladen.
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
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 675d881c3737b67cfdc0207be85285f71455d65c
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666960"
---
# <a name="step-3-implement-asr-rules"></a>Trin 3: Implementer ASR-regler

Implementering af ASR-regler (Attack Surface Reduction) flytter den første testring til en aktiveret, funktionel tilstand.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-implementation-steps.png" alt-text="Proceduren for implementering af ASR-regler" lightbox="images/asr-rules-implementation-steps.png":::
  

## <a name="step-1-transition-asr-rules-from-audit-to-block"></a>Trin 1: Overgå ASR-regler fra Overvågning til Bloker

1. Når alle udeladelser er bestemt i overvågningstilstand, skal du begynde at angive nogle ASR-regler til "bloker"-tilstand, startende med den regel, der har færrest udløste hændelser. Se" [Aktivér regler for reduktion af angrebsoverfladen](enable-attack-surface-reduction.md).
2. Gennemse rapportsiden på portalen Microsoft 365 Defender. Se [Rapporten om trusselsbeskyttelse i Microsoft Defender for Endpoint](threat-protection-reports.md). Gennemse også feedback fra dine ASR-mestre.
3. Afgræns udeladelser, eller opret nye undtagelser efter behov.
4. Skift problematiske regler tilbage til Overvågning.

  >[!Note]
  >I forbindelse med problematiske regler (regler, der skaber for meget støj), er det bedre at oprette undtagelser end at slå regler fra eller skifte tilbage til Overvågning. Du skal afgøre, hvad der er bedst for dit miljø.

  >[!Tip]
  >Når den er tilgængelig, kan du drage fordel af indstillingen Advar-tilstand i regler for at begrænse afbrydelser. Aktivering af ASR-regler i Warn-tilstand giver dig mulighed for at registrere udløste hændelser og få vist deres potentielle afbrydelser uden faktisk at blokere slutbrugeradgang. Få mere at vide: [Advarselstilstand for brugere](attack-surface-reduction.md#warn-mode-for-users).

### <a name="how-does-warn-mode-work"></a>Hvordan fungerer Warn-tilstand?

Advarselstilstand er i praksis en blokinstruktion, men med mulighed for brugeren at "fjerne blokeringen" af efterfølgende udførelser af det angivne flow eller den givne app. Fjern blokeringer i advarselstilstand på en kombination af enhed, bruger, fil og proces. Oplysningerne om advarselstilstand gemmes lokalt og har en varighed på 24 timer.

### <a name="step-2-expand-deployment-to-ring-n--1"></a>Trin 2: Udvid udrulningen for at ringe til n + 1

Når du er sikker på, at du har konfigureret ASR-reglerne for ring 1 korrekt, kan du udvide omfanget af udrulningen til næste ring (ring n + 1).

Udrulningsprocessen, trin 1-3, er stort set den samme for hver efterfølgende ring:

1. Test regler i Overvågning
2. Gennemse ASR-udløste overvågningshændelser på Microsoft 365 Defender-portalen
3. Opret udeladelser
4. Gennemse: Afgræns, tilføj eller fjern udeladelser efter behov
5. Angiv regler til "blok"
6. Gennemse rapportsiden på portalen Microsoft 365 Defender.
7. Opret udeladelser.
8. Deaktiver problematiske regler, eller skift dem tilbage til Overvågning.

#### <a name="customize-attack-surface-reduction-rules"></a>Tilpas regler for reduktion af angrebsoverflade

Efterhånden som du fortsætter med at udvide installationen af regler for reduktion af angrebsoverfladen, kan det være nødvendigt eller nyttigt at tilpasse de regler for reduktion af angrebsoverfladen, som du har aktiveret.

##### <a name="exclude-files-and-folders"></a>Udelad filer og mapper

Du kan vælge at udelukke filer og mapper fra at blive evalueret af regler for reduktion af angrebsoverfladen. Når den udelades, blokeres filen ikke fra at køre, selvom en regel for reduktion af angrebsoverfladen registrerer, at filen indeholder skadelig funktionsmåde.

Overvej for eksempel ransomware-reglen:

Ransomware-reglen er designet til at hjælpe virksomhedskunder med at reducere risikoen for ransomware-angreb og samtidig sikre forretningskontinuitet. Som standard, ransomware regel fejl på den side af forsigtighed og beskytte mod filer, der endnu ikke har opnået tilstrækkeligt omdømme og tillid. For at understrege det igen, udløser ransomware-reglen kun filer, der ikke har fået nok positivt omdømme og prævalens, baseret på forbrugsdata for millioner af vores kunder. Normalt løses blokkene selv, fordi værdierne for hver fils "omdømme og tillid" opgraderes trinvist, efterhånden som ikke-problematisk brug øges.

I de tilfælde, hvor blokke ikke løses rettidigt, kan kunderne – _på egen risiko_ – gøre brug af enten selvbetjeningsmekanismen eller en IOC-baseret egenskab (Indicator of Compromise) for at fjerne blokeringen af filerne selv.

> [!WARNING]
> Hvis du udelader eller fjerner blokeringen af filer eller mapper, kan det potentielt tillade usikre filer at køre og inficere dine enheder. Hvis du udelader filer eller mapper, kan det i alvorlig grad reducere den beskyttelse, der leveres af regler for reduktion af angrebsoverfladen. Filer, der ville være blevet blokeret af en regel, får tilladelse til at køre, og der registreres ingen rapport eller hændelse.

En udeladelse gælder for alle regler, der tillader udeladelser. Du kan angive en enkelt fil, mappesti eller det fuldt kvalificerede domænenavn for en ressource. Du kan dog ikke begrænse en udeladelse til en bestemt regel.

En udeladelse anvendes kun, når det udeladte program eller den udeladte tjeneste starter. Hvis du f.eks. tilføjer en udeladelse for en opdateringstjeneste, der allerede kører, vil opdateringstjenesten fortsat udløse hændelser, indtil tjenesten stoppes og genstartes.

Reduktion af angrebsoverfladen understøtter miljøvariabler og jokertegn. Du kan få oplysninger om, hvordan du bruger jokertegn, [under Brug jokertegn i filnavnet og mappestien eller udvidelsesudeladelseslisterne](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).
Hvis du støder på problemer med regler, der registrerer filer, som du mener ikke skal registreres, skal du [bruge overvågningstilstand til at teste reglen](evaluate-attack-surface-reduction.md).

Se emnet [reference til regler for reduktion af angrebsoverfladen](attack-surface-reduction-rules-reference.md) for at få oplysninger om hver enkelt regel.

##### <a name="use-group-policy-to-exclude-files-and-folders"></a>Brug Gruppepolitik til at udelade filer og mapper

1. Åbn [administrationskonsollen Gruppepolitik](https://technet.microsoft.com/library/cc731212.aspx) Gruppepolitik, højreklik på det Gruppepolitik objekt, du vil konfigurere, og vælg **Rediger**.

2. I **Gruppepolitik Management Editor** skal du gå til **Computerkonfiguration** og klikke på **Administrative skabeloner**.

3. Udvid træet for at **Windows komponenter** \> **Microsoft Defender Antivirus** \> **Microsoft Defender Exploit Guard** \> **reduktion af angrebsoverfladen**.

4. Dobbeltklik på indstillingen **Udelad filer og stier fra regler for reduktion af angrebsoverfladen** , og angiv indstillingen til **Aktiveret**. Vælg **Vis** , og angiv hver fil eller mappe i kolonnen **Værdinavn** . Angiv **0** i kolonnen **Værdi** for hvert element.

> [!WARNING]
> Brug ikke anførselstegn, da de ikke understøttes for hverken kolonnen **Value name** eller kolonnen **Value** .

##### <a name="use-powershell-to-exclude-files-and-folders"></a>Brug PowerShell til at udelade filer og mapper

1. Skriv **powershell** i menuen Start, højreklik **Windows PowerShell**, og vælg **Kør som administrator**.

2. Angiv følgende cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Fortsæt med at bruge `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` til at føje flere mapper til listen.

    > [!IMPORTANT]
    > Bruges `Add-MpPreference` til at tilføje eller føje apps til listen. Hvis du bruger cmdlet'en `Set-MpPreference` , overskrives den eksisterende liste.

##### <a name="use-mdm-csps-to-exclude-files-and-folders"></a>Brug MDM CSP'er til at udelade filer og mapper

Brug [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) CSP (Configuration Service Provider) til at tilføje udeladelser.

##### <a name="customize-the-notification"></a>Tilpas meddelelsen

Du kan tilpasse meddelelsen, når en regel udløses, og blokerer en app eller fil. Se artiklen [om Windows Sikkerhed](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center#customize-notifications-from-the-windows-defender-security-center).

## <a name="additional-topics-in-this-deployment-collection"></a>Yderligere emner i denne installationssamling

[Forudsætninger for udrulning af ASR-regler](attack-surface-reduction-rules-deployment.md)

[Trin 1: Planlæg udrulning af ASR-regler](attack-surface-reduction-rules-deployment-plan.md)

[Trin 2: Test ASR-regler](attack-surface-reduction-rules-deployment-test.md)

[Trin 4: Operationaliser ASR-regler](attack-surface-reduction-rules-deployment-operationalize.md)
