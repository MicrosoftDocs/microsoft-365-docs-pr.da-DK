---
title: Implementer reduktion af angrebsoverfladen (ASR)-regler for implementering
description: Giver vejledning til implementering af dine implementeringsregler for reduktion af angrebsoverfladen.
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
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 2ca83735eab465e3a5ec6b25156143fde1719c0a
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63683115"
---
# <a name="step-3-implement-asr-rules"></a>Trin 3: Implementer ASR-regler

Implementering af ASR-regler (Attack Surface Reduction) flytter den første testring til en aktiveret, funktionel tilstand.

> [!div class="mx-imgBorder"]
> ![Trin til implementering af ASR-regler](images/asr-rules-implementation-steps.png)

## <a name="step-1-transition-asr-rules-from-audit-to-block"></a>Trin 1: Overgå ASR-regler fra Overvågning til Bloker

1. Når alle undtagelser er fastlagt, mens du er i overvågningstilstand, skal du begynde at indstille visse asrregler til at "blokere" tilstand startende med den regel, der har færrest udløste hændelser. Se" [Aktivér regler for reduktion af angrebsoverfladen](enable-attack-surface-reduction.md).
2. Gennemse rapporteringssiden på Microsoft 365 Defender. Se [Trusselsbeskyttelsesrapport i Microsoft Defender til slutpunkt](threat-protection-reports.md). Gennemgå også feedback fra ASR-vindere.
3. Tilpas udeladelse, eller opret nye udeladelsesforanstaltninger efter behov.
4. Skift problematiske regler tilbage til Overvågning.

  >[!Note]
  >For problematiske regler (regler, der skaber for meget støj) er det bedre at oprette udeladelse end at deaktivere eller skifte tilbage til Overvågning. Du er nødt til at bestemme, hvad der er bedst for dit miljø.

  >[!Tip]
  >Hvis de er tilgængelige, kan du benytte indstillingen Advar i regler for at begrænse afbrydelser. Hvis du aktiverer ASR-regler i tilstanden Advar, kan du registrere udløste hændelser og få vist deres potentielle afbrydelser uden rent faktisk at blokere slutbrugeradgang. Få mere at vide: [Advarselstilstand for brugere](attack-surface-reduction.md#warn-mode-for-users).

### <a name="how-does-warn-mode-work"></a>Hvordan fungerer advarselstilstanden?

Advarselstilstand er i praksis en Bloker-instruktion, men med indstillingen for brugeren til at "fjerne blokeringen" af efterfølgende udførelser af det angivne flow eller den angivne app. Advar tilstand fjerner blokeringen på en pr. enhed, bruger, fil og proceskombination. Oplysningerne om advarselstilstanden gemmes lokalt og varer 24 timer.

### <a name="step-2-expand-deployment-to-ring-n--1"></a>Trin 2: Udvid udrulningen til at ringe på n + 1

Når du er sikker på, at du har konfigureret reglerne for AA korrekt for ring 1, kan du udvide omfanget af din installation til den næste ring (ring n + 1).

Installationsprocessen, trin 1-3, er i bund og grund den samme for hver efterfølgende ring:

1. Testregler i Overvågning
2. Gennemse ASR-udløste overvågningshændelser i Microsoft 365 Defender-portalen
3. Opret udeladelse
4. Gennemse: finjustere, tilføje eller fjerne udeladelse efter behov
5. Angiv regler til "bloker"
6. Gennemse rapporteringssiden i Microsoft 365 Defender portalen.
7. Opret udeladelse.
8. Deaktiver problematiske regler, eller skift dem tilbage til Overvågning.

#### <a name="customize-attack-surface-reduction-rules"></a>Tilpas regler for reduktion af angrebsoverfladen

Efterhånden som du fortsætter med at udvide dine regler for reduktion af angrebsoverfladen, kan det være nødvendigt eller nyttigt at tilpasse de reduktionsregler for angrebsoverfladen, som du har aktiveret.

##### <a name="exclude-files-and-folders"></a>Udelad filer og mapper

Du kan vælge at udelukke filer og mapper fra at blive evalueret af regler for reduktion af angrebsoverfladen. Når filen udelades, blokeres den ikke fra at køre, selvom en regel for reduktion af angrebsoverfladen registrerer, at filen indeholder skadelig opførsel.

Overvej f.eks. ransomware-reglen:

Ransomware-reglen er udviklet til at hjælpe virksomhedskunder med at reducere risikoen for ransomware-angreb og samtidig sikre forretningskontinuitet. Som standard fejl med ransomware-reglen på grund af forsigtighed og beskyttelse mod filer, der endnu ikke har fået tilstrækkelig renommé og tillid. For at understrege det er ransomware-reglen kun udløser filer, der ikke har fået nok positivt ry og gode resultater baseret på brugsmålepunkter for millioner af vores kunder. Som regel er blokkene selv løst, fordi hver fils værdier med "ry og tillid" gradvist opgraderes, efterhånden som ikke-problematisk brug øges.

I tilfælde, hvor blokke ikke løses uden problemer i tide, kan kunderne på eget ansvar gøre brug af enten selvbetjeningsmekanismen eller en IOC-baseret "tilladelsesliste" til _at_ fjerne blokeringen af selve filerne.

> [!WARNING]
> Hvis du udelukker eller fjerner blokeringen af filer eller mapper, kan det potentielt tillade, at usikre filer kan køre og inficere dine enheder. Hvis du udelader filer eller mapper, kan det i alvorlig grad reducere den beskyttelse, der leveres af regler for reduktion af angrebsoverfladen. Filer, der er blevet blokeret af en regel, har tilladelse til at køre, og der bliver ikke registreret nogen rapport eller hændelse.

En udeladelse gælder for alle regler, der tillader udeladelser. Du kan angive en individuel fil, mappesti eller det fulde domænenavn for en ressource. Du kan dog ikke begrænse en udeladelse til en bestemt regel.

En udeladelse anvendes kun, når det ekskluderede program eller den ekskluderede tjeneste starter. Hvis du f.eks. tilføjer en udeladelse for en opdateringstjeneste, der allerede kører, fortsætter opdateringstjenesten med at udløse hændelser, indtil tjenesten stoppes og genstartes.

Reduktion af angrebsoverfladen understøtter miljøvariabler og jokertegn. Du kan finde oplysninger om brug af jokertegn [i Brug jokertegn i filnavnet og mappestien eller udeladelseslister for filtypenavnet](configure-extension-file-exclusions-microsoft-defender-antivirus.md#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists).
Hvis du støder på problemer med regler, der registrerer filer, som du mener ikke bør registreres, skal du bruge [overvågningstilstand til at teste reglen](evaluate-attack-surface-reduction.md).

Se [referenceemnet om reduktionsregler](attack-surface-reduction-rules-reference.md) for angrebsoverfladen for at få mere at vide om hver regel.

##### <a name="use-group-policy-to-exclude-files-and-folders"></a>Brug Gruppepolitik til at udelade filer og mapper

1. På Gruppepolitik administrationscomputer skal du åbne [Gruppepolitik Administrationskonsol](https://technet.microsoft.com/library/cc731212.aspx), højreklikke på det Gruppepolitik objekt, du vil konfigurere, og vælge **Rediger**.

2. I **administrationseditoren Gruppepolitik skal** du gå til **Computerkonfiguration og** klikke på **Administrative skabeloner**.

3. Udvid træet for **at Windows komponenter** \> **Microsoft Defender Antivirus** \> **Microsoft Defender Exploit Guard reduktion af** \> **angrebsoverfladen**.

4. Dobbeltklik på indstillingen **Ekskluder filer og stier fra reduktionsregler for angrebsoverfladen** , og angiv indstillingen til **Aktiveret**. Vælg **Vis** , og angiv hver enkelt fil eller mappe i **kolonnen Værdinavn** . Angiv **0** i **kolonnen Værdi** for hvert element.

> [!WARNING]
> Brug ikke anførselstegn, da de ikke understøttes **hverken i kolonnen** Værdinavn eller **kolonnen** Værdi.

##### <a name="use-powershell-to-exclude-files-and-folders"></a>Brug PowerShell til at udelukke filer og mapper

1. Skriv **powershell** i menuen Start, **højreklik på Windows PowerShell** og vælg **Kør som administrator**.

2. Angiv følgende cmdlet:

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Fortsæt med at `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` bruge til at føje flere mapper til listen.

    > [!IMPORTANT]
    > Bruges `Add-MpPreference` til at tilføje eller føje apps til listen. Hvis du `Set-MpPreference` bruger cmdlet'en, overskrives den eksisterende liste.

##### <a name="use-mdm-csps-to-exclude-files-and-folders"></a>Brug AFDM-CSP'er til at udelukke filer og mapper

Brug [konfigurationen ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) serviceudbyder (CSP) til at tilføje udeladelser.

##### <a name="customize-the-notification"></a>Tilpasse meddelelsen

Du kan tilpasse beskeden, så en regel udløses, og blokere en app eller fil. Se [Windows Sikkerhed](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center#customize-notifications-from-the-windows-defender-security-center) artikel.

## <a name="additional-topics-in-this-deployment-collection"></a>Flere emner i denne installationssamling

[Forudsætninger for implementering af ASR-regler](attack-surface-reduction-rules-deployment.md)

[Trin 1: Planlægge udrulning af ASR-regler](attack-surface-reduction-rules-deployment-plan.md)

[Trin 2: Test ASR-regler](attack-surface-reduction-rules-deployment-test.md)

[Trin 4: At drifte ASR-regler](attack-surface-reduction-rules-deployment-operationalize.md)
