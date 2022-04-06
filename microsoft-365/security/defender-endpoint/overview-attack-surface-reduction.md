---
title: Forstå og brug reduktion af angrebsoverfladen (ASR)
ms.reviewer: ''
description: Få mere at vide om muligheder for reduktion af angrebsoverfladen i Microsoft Defender til slutpunkt.
keywords: asr, reduktion af angrebsoverfladen, Microsoft Defender til Endpoint, microsoft defender, antivirus, av, windows defender
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: jweston-1
ms.author: v-jweston
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.custom: asr
ms.topic: conceptual
ms.technology: mde
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 9c489d28467582e0f95f3fde7440ff43022c44e1
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682036"
---
# <a name="understand-and-use-attack-surface-reduction-capabilities"></a>Forstå og brug reduktionsfunktioner til angrebsoverfladen

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Angrebsoverfladerne er alle de steder, hvor din organisation er sårbar over for cybertrusler og angreb. Defender til Slutpunkt indeholder adskillige funktioner, der kan hjælpe dig med at reducere dine angrebsoverflader. Se følgende video for at få mere at vide om reduktion af angrebsoverfladen.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4woug]

## <a name="configure-attack-surface-reduction-capabilities"></a>Konfigurer muligheder for reduktion af angrebsoverfladen

Hvis du vil konfigurere reduktion af angrebsoverfladen i dit miljø, skal du følge disse trin:

1. [Aktivér hardwarebaseret isolation for Microsoft Edge](/windows/security/threat-protection/microsoft-defender-application-guard/install-md-app-guard).

2. Aktivér programkontrolelement.

   1. Gennemse grundlæggende politikker i Windows. Se [Eksempel på grundlæggende politikker](/windows/security/threat-protection/windows-defender-application-control/example-wdac-base-policies).
   2. Se [designvejledningen Windows Defender programkontrolelement](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-design-guide).
   3. Se [WDAC-Windows Defender (Application Control).](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide)

3. [Aktivér styret mappeadgang](enable-controlled-folders.md).

4. [Slå Netværksbeskyttelse til](enable-network-protection.md).

5. [Aktivér udnyttelse af beskyttelse](enable-exploit-protection.md).

6. [Installér regler for reduktion af angrebsoverfladen](attack-surface-reduction-rules-deployment.md).

7. Konfigurer din netværksfirewall.

   1. Få et overblik over [Windows Defender Firewall med avanceret sikkerhed](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).
   2. Brug Windows Defender [Firewall-designvejledningen til](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-design-guide) at beslutte, hvordan du vil designe politikkerne for din firewall.
   3. Brug Windows Defender [Firewall-installationsvejledningen](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-deployment-guide) til at konfigurere din organisations firewall med avanceret sikkerhed.

> [!TIP]
> I de fleste tilfælde kan du, når du konfigurerer muligheder for reduktion af angrebsoverfladen, vælge mellem flere forskellige metoder:
>
> - Microsoft Endpoint Manager (som nu omfatter Microsoft Intune og Microsoft Endpoint Configuration Manager)
> - Gruppepolitik
> - PowerShell-cmdlet'er

## <a name="test-attack-surface-reduction-in-microsoft-defender-for-endpoint"></a>Reduktion af angrebsoverfladen i Microsoft Defender til slutpunkt

Som en del af din organisations sikkerhedsteam kan du konfigurere muligheder for reduktion af angrebsoverfladen til at køre i overvågningstilstand for at se, hvordan de fungerer. I overvågningstilstand kan du aktivere:

- Regler for reduktion af angrebsoverflade
- Exploit Protection
- Netværksbeskyttelse
- Og kontrolleret mappeadgang i overvågningstilstand

I overvågningstilstand kan du se en post med, *hvad der ville* være sket, hvis du havde aktiveret funktionen.

Du kan aktivere overvågningstilstand, når du tester, hvordan funktionerne fungerer. Aktivering af overvågningstilstand kun for test hjælper med at forhindre overvågningstilstand i at påvirke dine line of business-apps. Du kan også få en ide om, hvor mange mistænkelige filændringer, der forsøges i løbet af en bestemt tidsperiode.

Funktionerne blokerer eller forhindrer ikke, at apps, scripts eller filer ændres. Hændelsesloggen registrerer Windows, som om funktionerne var fuldt aktiveret. Med overvågningstilstand kan du gennemse hændelsesloggen for at se, hvilken indvirkning funktionen ville have haft, hvis den var aktiveret.

Du kan finde de reviderede poster ved at gå til **Programmer og tjenester,** \> **som Microsoft** \> **Windows** \> **Windows Defender** \> **Drift.**

Brug Defender til Slutpunkt for at få flere detaljer for hver begivenhed. Disse detaljer er især nyttige ved undersøgelse af regler for reduktion af angrebsoverfladen. Med Defender til slutpunktskonsollen kan du [undersøge problemer som en del af tidslinjen og undersøgelsesscenarierne](investigate-alerts.md).

Du kan aktivere overvågningstilstand ved Gruppepolitik, PowerShell og konfigurationstjenesteudbydere.

> [!TIP]
> Du kan også besøge webstedet Windows Defender Testground på [demo.wd.microsoft.com for at](https://demo.wd.microsoft.com?ocid=cx-wddocs-testground) bekræfte, at funktionerne virker, og se, hvordan de fungerer.

> [!NOTE]
> Defender for Endpoint-demowebstedet demo.wd.microsoft.com forældet og fjernes fremover.

| Overvågningsindstillinger | Sådan aktiveres overvågningstilstand | Sådan får du vist begivenheder |
|---|---|---|
| Overvågning gælder for alle hændelser | [Aktivér styret mappeadgang](enable-controlled-folders.md) | [Kontrollerede mappeadgangshændelser](evaluate-controlled-folder-access.md#review-controlled-folder-access-events-in-windows-event-viewer) |
| Overvågning gælder for individuelle regler | [Trin 1: Test ASR-regler ved hjælp af Overvågning](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit) | [Trin 2: Forstå rapporteringssiden for reduktionsregler for angrebsoverfladen](attack-surface-reduction-rules-deployment-test.md#step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal) |
| Overvågning gælder for alle hændelser | [Aktivér netværksbeskyttelse](enable-network-protection.md) | [Netværksbeskyttelseshændelser](evaluate-network-protection.md#review-network-protection-events-in-windows-event-viewer) |
| Overvågning gælder for enkelt afhjælpninger | [Aktivér udnyttelse af beskyttelse](enable-exploit-protection.md) | [Exploit protection-hændelser](exploit-protection.md#review-exploit-protection-events-in-windows-event-viewer) |

## <a name="view-attack-surface-reduction-events"></a>Få vist hændelser til reduktion af angrebsoverfladen

Gennemse hændelser til reduktion af angrebsoverfladen i Logvisning for at overvåge, hvilke regler eller indstillinger der fungerer. Du kan også afgøre, om nogen af indstillingerne er for "støjende" eller påvirker den daglige arbejdsproces.

Det er praktisk at gennemgå begivenheder, når du skal evaluere funktionerne. Du kan aktivere overvågningstilstand for funktioner eller indstillinger og derefter se, hvad der ville være sket, hvis de var fuldt aktiveret.

I dette afsnit beskrives alle hændelserne, deres tilknyttede funktion eller indstilling, og det beskrives, hvordan du kan oprette brugerdefinerede visninger til filtrering efter bestemte hændelser.

Få detaljeret rapportering om begivenheder, blokke og advarsler som en del Windows Sikkerhed hvis du har et E5-abonnement og bruger [Microsoft Defender til slutpunkt](microsoft-defender-endpoint.md).

### <a name="use-custom-views-to-review-attack-surface-reduction-capabilities"></a>Brug brugerdefinerede visninger til at gennemse muligheder for reduktion af angrebsoverfladen

Opret brugerdefinerede visninger i Windows for kun at se hændelser for bestemte funktioner og indstillinger. Den nemmeste måde er at importere en brugerdefineret visning som en XML-fil. Du kan kopiere XML direkte fra denne side.

Du kan også manuelt navigere til det hændelsesområde, der svarer til funktionen.

#### <a name="import-an-existing-xml-custom-view"></a>Importere en eksisterende brugerdefineret XML-visning

1. Opret en tom .txt, og kopiér XML'en for den brugerdefinerede visning, du vil bruge, .txt filen. Gør dette for hver af de brugerdefinerede visninger, du vil bruge. Omdøb filerne på følgende måde (sørg for at ændre typen .txt til .xml):
    - Kontrolleret mappeadgangshændelser for *brugerdefineret visning:cfa-events.xml*
    - Brugerdefineret visning af Exploit Protection-hændelser: *ep-events.xml*
    - Brugerdefineret visning af reduktionshændelser for *angrebsoverfladen:asr-events.xml*
    - Brugerdefineret visning af netværks-/ *beskyttelseshændelser:np-events.xml*

2. Skriv **begivenhedsvisning** i menuen Start og åbn **Log på**.

3. Vælg **Brugerdefineret** \> **visning af handlingsimport...**

   > [!div class="mx-imgBorder"]
   > ![Animation, der fremhæver Importér brugerdefineret visning til venstre for vinduet Lige fremviser.](images/events-import.gif)

4. Gå til det sted, hvor du udpakkede XML-filen til den ønskede brugerdefinerede visning, og vælg den.

5. Vælg **Åbn**.

6. Den opretter en brugerdefineret visning, der filtrerer for kun at vise de hændelser, der er relateret til den pågældende funktion.

#### <a name="copy-the-xml-directly"></a>Kopiere XML direkte

1. Skriv **log på i** menuen Start, og åbn Windows **Log på**.

2. I venstre panel under Handlinger **skal du** vælge **Opret brugerdefineret visning...**

   > [!div class="mx-imgBorder"]
   > ![Animation, der fremhæver indstillingen Opret brugerdefineret visning i vinduet Logvisning.](images/events-create.gif)

3. Gå til fanen XML, og vælg **Rediger forespørgsel manuelt**. Der vises en advarsel om, at du ikke kan redigere forespørgslen ved hjælp af **fanen Filter** , hvis du bruger indstillingen XML. Vælg **Ja**.

4. Indsæt XML-koden for den funktion, du vil filtrere hændelser fra, i XML-sektionen.

5. Vælg **OK**. Angiv et navn til filteret. Dette opretter en brugerdefineret visning, der filtreres for kun at vise de hændelser, der er relateret til den pågældende funktion.

#### <a name="xml-for-attack-surface-reduction-rule-events"></a>XML til reduktion af angrebsoverfladen ved hændelser i forbindelse med reglen

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-controlled-folder-access-events"></a>XML til styret mappeadgangshændelser

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1123 or EventID=1124 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-exploit-protection-events"></a>XML til udnyttelse af beskyttelseshændelser

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Security-Mitigations/KernelMode">
   <Select Path="Microsoft-Windows-Security-Mitigations/KernelMode">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Concurrency">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Contention">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Messages">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Operational">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Power">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Render">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/Tracing">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Win32k/UIPI">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="System">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
   <Select Path="Microsoft-Windows-Security-Mitigations/UserMode">*[System[Provider[@Name='Microsoft-Windows-Security-Mitigations' or @Name='Microsoft-Windows-WER-Diag' or @Name='Microsoft-Windows-Win32k' or @Name='Win32k'] and ( (EventID &gt;= 1 and EventID &lt;= 24)  or EventID=5 or EventID=260)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-network-protection-events"></a>XML til netværksbeskyttelseshændelser

```xml
<QueryList>
 <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
  <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
  <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1125 or EventID=1126 or EventID=5007)]]</Select>
 </Query>
</QueryList>
```

### <a name="list-of-attack-surface-reduction-events"></a>Liste over hændelser til reduktion af angrebsoverfladen

Alle hændelser til reduktion af angrebsoverfladen er placeret under Programmer og tjenester **> Microsoft > Windows** og derefter mappen eller udbyderen som angivet i følgende tabel.

Du kan få adgang til disse Windows i Logrevisning:

1. Åbn menuen **Start** , og skriv **log over** begivenheder, og vælg derefter Resultatet **fra Logvisning** .
2. **Udvid Logfiler for programmer og tjenester > Microsoft > Windows** og gå derefter til den mappe, der er angivet under **Udbyder/** kilde i tabellen nedenfor.
3. Dobbeltklik på det underordnede element for at få vist begivenheder. Rul gennem begivenhederne for at finde den, du leder efter.

   ![Animation, der viser ved hjælp af Logvisning.](images/event-viewer.gif)

<br>

****

|Funktion|Udbyder/kilde|Hændelses-id|Beskrivelse|
|---|---|:---:|---|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|1|ACG-overvågning|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|2|ACG gennemtving|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|3|Tillad ikke overvågning af underordnede processer|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|4|Tillad ikke blokering af underordnede processer|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|5|Bloker overvågning af billeder med lav integritet|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|6|Bloker billeder med lav integritet|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|7|Bloker overvågning af eksterne billeder|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|8|Bloker fjernbilleder|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|9|Deaktiver overvågning af win32k-systemopkald|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|10|Deaktiver blokering af win32k-systemopkald|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|11|Overvågning af kodeintegritetsbeskyttelse|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|12|Blok for kodeintegritetsbeskyttelse|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|13|EAF-overvågning|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|14|EAF gennemtving|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|15|EAF+-overvågning|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|16|EAF+ gennemtving|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|17|IAF-overvågning|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|18|IAF gennemtving|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|19|ROP-stakpivot-overvågning|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|20|GENNEMTving ROP-stakpivot|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|21|ROP CallerCheck-overvågning|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|22|ROP CallerCheck gennemtving|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|23|ROP SimExec-overvågning|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|24|ROP SimExec gennemtving|
|Exploit Protection|WER-Diagnostics|5|CFG-blok|
|Exploit Protection|Win32K (drift)|260|Skrifttype, der ikke er tillid til|
|Netværksbeskyttelse|Windows Defender (drift)|5007|Hændelse, når indstillingerne ændres|
|Netværksbeskyttelse|Windows Defender (drift)|1125|Hændelse, når netværksbeskyttelse udløses i overvågningstilstand|
|Netværksbeskyttelse|Windows Defender (drift)|1126|Hændelse, når netværksbeskyttelse udløses i bloktilstand|
|Styret mappeadgang|Windows Defender (drift)|5007|Hændelse, når indstillingerne ændres|
|Styret mappeadgang|Windows Defender (drift)|1124|Overvåget styret mappeadgangshændelse|
|Styret mappeadgang|Windows Defender (drift)|1123|Hændelse med blokeret styret mappeadgang|
|Styret mappeadgang|Windows Defender (drift)|1127|Blokeret styret mappeadgang til skriveblokeringshændelse|
|Styret mappeadgang|Windows Defender (drift)|1128|Overvåget kontrolleret mappeadgangshændelse af skriveblok|
|Reduktion af angrebsoverfladen|Windows Defender (drift)|5007|Hændelse, når indstillingerne ændres|
|Reduktion af angrebsoverfladen|Windows Defender (drift)|1122|Hændelse, når reglen udløses i overvågningstilstand|
|Reduktion af angrebsoverfladen|Windows Defender (drift)|1121|Hændelse, når reglen udløses i bloktilstand|

>[!NOTE]
> For brugerens perspektiv sendes meddelelser om ASR-advarselstilstand som en del Windows toastbesked for regler for reduktion af angrebsoverfladen.
>
> I ASR giver Netværksbeskyttelse kun overvågnings- og blokeringstilstande.

## <a name="resources-to-learn-more-about-attack-surface-reduction"></a>Ressourcer til at lære mere om reduktion af angrebsoverfladen

Som nævnt i videoen indeholder Defender til Slutpunkt flere muligheder for reduktion af angrebsoverfladen. Brug følgende ressourcer til at få mere at vide:

| Artikel | Beskrivelse |
|:---|:---|
| [Hardwarebaseret isolation](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview) | Beskyt og vedligehold integriteten af et system, når det starter, og mens det kører. Valider systemintegritet via lokal og fjernvalidering. Brug objektbeholderisolation til Microsoft Edge at beskytte dig mod skadelige websteder. |
| [Programkontrolelement](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) | Brug programkontrol, så dine programmer skal have tillid til sig for at køre. |
| [Styret mappeadgang](controlled-folders.md) | Forhindre skadelige eller mistænkelige apps (herunder filkryptering af ransomware malware) i at foretage ændringer i filer i dine vigtigste systemmapper (kræver, at Microsoft Defender Antivirus) |
| [Netværksbeskyttelse](network-protection.md) | Udvid beskyttelse til din netværkstrafik og forbindelse på organisationens enheder. (Kræver Microsoft Defender Antivirus) |
| [Exploit Protection](exploit-protection.md) | Beskyt de operativsystemer og apps, din organisation bruger, mod at blive udnyttet. Exploit Protection fungerer også sammen med antivirusløsninger fra tredjeparter. |
| [Regler for reduktion af angrebsoverflade](attack-surface-reduction.md) | Reducer sårbarheder (angrebsoverfladerne) i dine programmer med intelligente regler, der hjælper med at stoppe malware. (Kræver Microsoft Defender Antivirus). |
| [Enhedsstyring](device-control-report.md) | Beskytter mod datatab ved at overvåge og kontrollere medier, der bruges på enheder, f.eks. flytbart lager og USB-drev, i din organisation. |
