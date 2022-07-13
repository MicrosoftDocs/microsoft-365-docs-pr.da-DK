---
title: Forstå og bruge reduktion af angrebsoverfladen (ASR)
ms.reviewer: ''
description: Få mere at vide om funktionerne til reduktion af angrebsoverfladen i Microsoft Defender for Endpoint.
keywords: asr, reduktion af angrebsoverflade, regler for reduktion af angrebsoverfladen, Microsoft Defender for Endpoint, microsoft defender, antivirus, av, windows defender
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
ms.date: 05/16/2022
ms.openlocfilehash: 7c09db2138502ee8c1b491028308c56f23687a0d
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66748995"
---
# <a name="understand-and-use-attack-surface-reduction-capabilities"></a>Forstå og brug funktioner til reduktion af angrebsoverfladen

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Antivirus

**Platforme**
- Windows

> [!TIP]
> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Angrebsoverflader er alle de steder, hvor din organisation er sårbar over for cybertrusler og angreb. Defender for Endpoint indeholder flere funktioner, der kan hjælpe med at reducere dine angrebsoverflader. Se følgende video for at få mere at vide om reduktion af angrebsoverfladen.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4woug]

## <a name="configure-attack-surface-reduction-capabilities"></a>Konfigurer funktioner til reduktion af angrebsoverfladen

Hvis du vil konfigurere reduktion af angrebsoverfladen i dit miljø, skal du følge disse trin:

1. [Aktivér hardwarebaseret isolation for Microsoft Edge](/windows/security/threat-protection/microsoft-defender-application-guard/install-md-app-guard).

2. [Aktivér regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-deployment.md)

3. Aktivér programkontrol.

   1. Gennemse grundlæggende politikker i Windows. Se [eksempel på grundlæggende politikker](/windows/security/threat-protection/windows-defender-application-control/example-wdac-base-policies).
   2. Se [designvejledningen til Windows Defender application control](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-design-guide).
   3. Se [Installation Windows Defender WDAC-politikker (Application Control).](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control-deployment-guide)

4. [Aktivér kontrolleret mappeadgang](enable-controlled-folders.md).

5. [Flytbar lagringsbeskyttelse](device-control-removable-storage-protection.md)

6. [Slå Netværksbeskyttelse til](enable-network-protection.md).

7. Aktivér [oversigt over webbeskyttelse](web-protection-overview.md)

8. [Aktivér beskyttelse mod udnyttelse](enable-exploit-protection.md).

9. Konfigurer din netværksfirewall.

   1. Få et overblik over [Windows Defender Firewall med avanceret sikkerhed](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).
   2. Brug [Windows Defender Firewall designvejledning](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-design-guide) til at beslutte, hvordan du vil designe firewallpolitikker.
   3. Brug [installationsvejledningen til Windows Defender Firewall](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-deployment-guide) til at konfigurere organisationens firewall med avanceret sikkerhed.

> [!TIP]
> Når du konfigurerer funktioner til reduktion af angrebsoverfladen, kan du i de fleste tilfælde vælge mellem flere metoder:
>
> - Microsoft Endpoint Manager (som nu omfatter Microsoft Intune og Microsoft Endpoint Configuration Manager)
> - Gruppepolitik
> - PowerShell-cmdlet'er

## <a name="test-attack-surface-reduction-in-microsoft-defender-for-endpoint"></a>Reduktion af angrebsoverfladen i Microsoft Defender for Endpoint

Som en del af organisationens sikkerhedsteam kan du konfigurere funktioner til reduktion af angrebsoverfladen til at køre i overvågningstilstand for at se, hvordan de fungerer. Du kan aktivere følgende ASR-sikkerhedsfunktioner i overvågningstilstand:

- Regler for reduktion af angrebsoverflade
- Exploit Protection
- Netværksbeskyttelse
- Og kontrolleret mappeadgang

I overvågningstilstand kan du se en post over, hvad der *ville* være sket, hvis du havde aktiveret funktionen.

Du kan aktivere overvågningstilstand, når du tester, hvordan funktionerne fungerer. Hvis du kun aktiverer overvågningstilstand til test, hjælper det med at forhindre, at overvågningstilstanden påvirker dine line of business-apps. Du kan også få en idé om, hvor mange mistænkelige filændringsforsøg der forekommer over en bestemt periode.

Funktionerne blokerer eller forhindrer ikke, at apps, scripts eller filer ændres. Windows-hændelsesloggen registrerer dog hændelser, som om funktionerne var fuldt aktiveret. Med overvågningstilstand kan du gennemse hændelsesloggen for at se, hvilken indvirkning funktionen ville have haft, hvis den var aktiveret.

Hvis du vil finde de overvågede poster, skal du gå til **Programmer og tjenester** \> **Microsoft** \> **Windows** \> **Windows Defender** \> **Operational**.

Brug Defender for Endpoint til at få flere oplysninger om hver enkelt hændelse. Disse oplysninger er især nyttige til undersøgelse af regler for reduktion af angrebsoverfladen. Ved hjælp af Defender for Endpoint-konsollen kan du [undersøge problemer som en del af tidslinjen for beskeder og undersøgelsesscenarier](investigate-alerts.md).

Du kan aktivere overvågningstilstand ved hjælp af Gruppepolitik, PowerShell og udbydere af konfigurationstjenester.

| Overvågningsindstillinger | Sådan aktiverer du overvågningstilstand | Sådan får du vist hændelser |
|---|---|---|
| Overvågning gælder for alle hændelser | [Aktivér styret mappeadgang](enable-controlled-folders.md) | [Hændelser for adgang til styrede mapper](evaluate-controlled-folder-access.md#review-controlled-folder-access-events-in-windows-event-viewer) |
| Overvågning gælder for individuelle regler | [Trin 1: Test ASR-regler ved hjælp af overvågningstilstand](attack-surface-reduction-rules-deployment-test.md#step-1-test-asr-rules-using-audit) | [Trin 2: Forstå rapporteringssiden for regler for reduktion af angrebsoverfladen](attack-surface-reduction-rules-deployment-test.md#step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal) |
| Overvågning gælder for alle hændelser | [Aktivér netværksbeskyttelse](enable-network-protection.md) | [Netværksbeskyttelseshændelser](evaluate-network-protection.md#review-network-protection-events-in-windows-event-viewer) |
| Overvågning gælder for individuelle afhjælpninger | [Aktivér Exploit Protection](enable-exploit-protection.md) | [Udnyt beskyttelseshændelser](exploit-protection.md#review-exploit-protection-events-in-windows-event-viewer) |

### <a name="attack-surface-reduction-asr-rules"></a>Regler for reduktion af angrebsoverflade

ASR-regler (Attack Surface Reduction) er foruddefinerede for at hærde almindelige kendte angrebsoverflader. Der er flere metoder, du kan bruge til at implementere regler for reduktion af angrebsoverfladen. Den foretrukne metode er dokumenteret i følgende emner om installation af asr-regler (attack surface reduction):

- [Udrulningsoversigt til reduktion af angrebsoverflade (ASR)](attack-surface-reduction-rules-deployment.md)
- [Planlæg udrulning af reduktion af angrebsoverflade (ASR)](attack-surface-reduction-rules-deployment-plan.md)
- [Regler for testreduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-test.md)
- [Aktiver regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-implement.md)
- [Operationaliser regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-operationalize.md)

## <a name="view-attack-surface-reduction-events"></a>Få vist hændelser for reduktion af angrebsoverfladen

Gennemse hændelser for reduktion af angrebsoverfladen i Logbog for at overvåge, hvilke regler eller indstillinger der fungerer. Du kan også afgøre, om nogen indstillinger er for "støjende" eller påvirker din daglige arbejdsproces.

Det er praktisk at gennemgå hændelser, når du evaluerer funktionerne. Du kan aktivere overvågningstilstand for funktioner eller indstillinger og derefter gennemse, hvad der ville være sket, hvis de var fuldt aktiveret.

I dette afsnit vises alle hændelserne, deres tilknyttede funktion eller indstilling, og det beskrives, hvordan du opretter brugerdefinerede visninger for at filtrere efter bestemte hændelser.

Få detaljeret rapportering om hændelser, blokke og advarsler som en del af Windows Sikkerhed hvis du har et E5-abonnement og bruger [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md).

### <a name="use-custom-views-to-review-attack-surface-reduction-capabilities"></a>Brug brugerdefinerede visninger til at gennemse funktioner til reduktion af angrebsoverfladen

Opret brugerdefinerede visninger i Windows Logbog for kun at se hændelser for bestemte egenskaber og indstillinger. Den nemmeste måde er at importere en brugerdefineret visning som en XML-fil. Du kan kopiere XML-koden direkte fra denne side.

Du kan også navigere til det hændelsesområde, der svarer til funktionen, manuelt.

#### <a name="import-an-existing-xml-custom-view"></a>Importér en eksisterende brugerdefineret XML-visning

1. Opret en tom .txt fil, og kopiér XML-filen for den brugerdefinerede visning, du vil bruge, til den .txt fil. Gør dette for hver af de brugerdefinerede visninger, du vil bruge. Omdøb filerne på følgende måde (sørg for at ændre typen fra .txt til .xml):
    - Brugerdefineret visning af hændelser for adgang til styrede mapper: *cfa-events.xml*
    - Brugerdefineret visning af hændelser for udnyttelse af beskyttelse: *ep-events.xml*
    - Brugerdefineret visning af hændelser for reduktion af angrebsoverfladen: *asr-events.xml*
    - Brugerdefineret visning af netværks-/beskyttelseshændelser: *np-events.xml*

2. Skriv **Logbog** i menuen Start, og åbn **Logbog**.

3. Vælg **importér brugerdefineret visning af** **handling**\>...

   > [!div class="mx-imgBorder"]
   > ![Fremhævning af animation Importér brugerdefineret visning til venstre i vinduet Lige fremviser.](images/events-import.gif)

4. Gå til den placering, hvor du har udtrukket XML-filen til den ønskede brugerdefinerede visning, og vælg den.

5. Vælg **Åbn**.

6. Den opretter en brugerdefineret visning, der filtrerer, så den kun viser de hændelser, der er relateret til den pågældende funktion.

#### <a name="copy-the-xml-directly"></a>Kopiér XML-koden direkte

1. Skriv **Logbog** i menuen Start, og åbn Windows **Logbog**.

2. Vælg **Opret brugerdefineret visning** under **Handlinger** i panelet til venstre...

   > [!div class="mx-imgBorder"]
   > ![Animation, der fremhæver indstillingen Opret brugerdefineret visning i vinduet Logbog.](images/events-create.gif)

3. Gå til fanen XML, og vælg **Rediger forespørgsel manuelt**. Du får vist en advarsel om, at du ikke kan redigere forespørgslen ved hjælp af fanen **Filter** , hvis du bruger indstillingen XML. Vælg **Ja**.

4. Indsæt XML-koden for den funktion, du vil filtrere hændelser fra, i AFSNITTET XML.

5. Vælg **OK**. Angiv et navn til filteret. Dette opretter en brugerdefineret visning, der filtrerer, så den kun viser de hændelser, der er relateret til den pågældende funktion.

#### <a name="xml-for-attack-surface-reduction-rule-events"></a>XML til regelhændelser for reduktion af angrebsoverflade

```xml
<QueryList>
  <Query Id="0" Path="Microsoft-Windows-Windows Defender/Operational">
   <Select Path="Microsoft-Windows-Windows Defender/Operational">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
   <Select Path="Microsoft-Windows-Windows Defender/WHC">*[System[(EventID=1121 or EventID=1122 or EventID=5007)]]</Select>
  </Query>
</QueryList>
```

#### <a name="xml-for-controlled-folder-access-events"></a>XML til hændelser for adgang til styrede mapper

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

### <a name="list-of-attack-surface-reduction-events"></a>Liste over hændelser for reduktion af angrebsoverfladen

Alle hændelser for reduktion af angrebsoverfladen er placeret under **Program- og tjenestelogfiler > Microsoft > Windows** og derefter mappen eller udbyderen som angivet i følgende tabel.

Du kan få adgang til disse hændelser i Windows Logbog:

1. Åbn menuen **Start,** skriv **Logbog**, og vælg derefter **Logbog** resultat.
2. Udvid **Logfiler for programmer og tjenester > Microsoft > Windows** , og gå derefter til den mappe, der er angivet under **Provider/source** i tabellen nedenfor.
3. Dobbeltklik på underelementet for at se hændelser. Rul gennem hændelserne for at finde den, du leder efter.

   ![Animation, der viser ved hjælp af Logbog.](images/event-viewer.gif)

<br>

****

|Funktion|Provider/kilde|Hændelses-id|Beskrivelse|
|---|---|:---:|---|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|1|ACG-overvågning|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|2|ACG-gennemtving|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|3|Tillad ikke overvågning af underordnede processer|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|4|Tillad ikke blok for underordnede processer|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|5|Bloker overvågning af billeder med lav integritet|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|6|Bloker blok for billeder med lav integritet|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|7|Bloker overvågning af fjernbilleder|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|8|Bloker fjernbilleder|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|9|Deaktiver overvågning af win32k-systemkald|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|10|Deaktiver blokering af win32k-systemkald|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|11|Overvågning af kodeintegritetsvagt|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|12|Blok for kodeintegritetsbeskyttelse|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|13|EAF-revision|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|14|Gennemtving EAF|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|15|EAF+ audit|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|16|Gennemtving EAF+|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|17|IAF-revision|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|18|Gennemtving IAF|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|19|ROP StackPivot-overvågning|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|20|ROP StackPivot gennemtving|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|21|ROP CallerCheck audit|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|22|ROP CallerCheck gennemtving|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|23|ROP SimExec-overvågning|
|Exploit Protection|Security-Mitigations (kernetilstand/brugertilstand)|24|ROP SimExec gennemtvinge|
|Exploit Protection|WER-Diagnostics|5|CFG-blok|
|Exploit Protection|Win32K (driftsklar)|260|Der er ikke tillid til skrifttype|
|Netværksbeskyttelse|Windows Defender (driftsklar)|5007|Hændelse, når indstillingerne ændres|
|Netværksbeskyttelse|Windows Defender (driftsklar)|1125|Hændelse, når netværksbeskyttelse udløses i overvågningstilstand|
|Netværksbeskyttelse|Windows Defender (driftsklar)|1126|Hændelse, når netværksbeskyttelse udløses i bloktilstand|
|Styret mappeadgang|Windows Defender (driftsklar)|5007|Hændelse, når indstillingerne ændres|
|Styret mappeadgang|Windows Defender (driftsklar)|1124|Overvåget adgangshændelse for kontrolleret mappe|
|Styret mappeadgang|Windows Defender (driftsklar)|1123|Adgangshændelse for blokeret kontrolleret mappe|
|Styret mappeadgang|Windows Defender (driftsklar)|1127|Hændelse for blokeret sektor med adgang til kontrolleret mappe|
|Styret mappeadgang|Windows Defender (driftsklar)|1128|Hændelse for skriveblokering for overvåget kontrolleret mappeadgangssektor|
|Reduktion af angrebsoverfladen|Windows Defender (driftsklar)|5007|Hændelse, når indstillingerne ændres|
|Reduktion af angrebsoverfladen|Windows Defender (driftsklar)|1122|Hændelse, når reglen udløses i overvågningstilstand|
|Reduktion af angrebsoverfladen|Windows Defender (driftsklar)|1121|Hændelse, når reglen udløses i bloktilstand|

>[!NOTE]
> Fra brugerens perspektiv sendes meddelelser om ASR-advarselstilstand som en Windows Toast-meddelelse for regler for reduktion af angrebsoverfladen.
>
> I ASR leverer Network Protection kun overvågnings- og bloktilstande.

## <a name="resources-to-learn-more-about-attack-surface-reduction"></a>Ressourcer til at få mere at vide om reduktion af angrebsoverfladen

Som nævnt i videoen indeholder Defender for Endpoint flere funktioner til reduktion af angrebsoverfladen. Brug følgende ressourcer til at få mere at vide:

| Artikel | Beskrivelse |
|:---|:---|
| [Hardwarebaseret isolation](/windows/security/threat-protection/microsoft-defender-application-guard/md-app-guard-overview) | Beskyt og bevar integriteten af et system, efterhånden som det starter, og mens det kører. Valider systemintegritet via lokal og ekstern attestation. Brug objektbeholderisolation til Microsoft Edge som en hjælp til at beskytte mod skadelige websteder. |
| [Programkontrolelement](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control) | Brug programkontrolelementet, så dine programmer skal have tillid til at kunne køre. |
| [Styret mappeadgang](controlled-folders.md) | Hjælp med at forhindre skadelige eller mistænkelige apps (herunder filkryptering af ransomware-malware) i at foretage ændringer af filer i dine centrale systemmapper (kræver Microsoft Defender Antivirus). |
| [Netværksbeskyttelse](network-protection.md) | Udvid beskyttelsen til netværkstrafik og -forbindelse på organisationens enheder. (Kræver Microsoft Defender Antivirus). |
| [Exploit Protection](exploit-protection.md) | Hjælp med at beskytte de operativsystemer og apps, din organisation bruger, så de ikke kan udnyttes. Udnyttelse af beskyttelse fungerer også med antivirusløsninger fra tredjepart. |
| [Enhedsstyring](device-control-report.md) | Beskytter mod tab af data ved at overvåge og styre medier, der bruges på enheder, f.eks. flytbart lager og USB-drev, i din organisation. |
| [Udrulningsvejledning til reduktion af angrebsoverflade (ASR)](attack-surface-reduction-rules-deployment.md) | Præsenterer oversigtsoplysninger og forudsætninger for installation af regler for reduktion af angrebsoverfladen efterfulgt af en trinvis vejledning i test, aktivering og overvågning. |
| [Planlæg udrulning af reduktion af angrebsoverflade (ASR)](attack-surface-reduction-rules-deployment-plan.md) | Viser de anbefalede trin til installation af regler for reduktion af angrebsoverfladen. |
| [Regler for testreduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-test.md) | Indeholder trin til at bruge overvågningstilstand til at teste regler for reduktion af angrebsoverfladen. |
| [Aktiver regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-implement.md) | Viser trinnene til overgang af regler for reduktion af angrebsoverfladen fra testtilstand (overvågning) til aktiv, aktiveret tilstand (bloktilstand). |
| [Operationaliser regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-deployment-operationalize.md) | Indeholder oplysninger om daglige gennemgangs- og vedligeholdelsesaktiviteter. |
| [Henvisning til regler for reduktion af angrebsoverflade](attack-surface-reduction-rules-reference.md) | Indeholder oplysninger om hver regel for reduktion af angrebsoverfladen. |
| [Regler for reduktion af angrebsoverflade](attack-surface-reduction.md) | Reducer sikkerhedsrisici (angrebsoverflader) i dine programmer med intelligente regler, der hjælper med at stoppe malware. (Kræver Microsoft Defender Antivirus). |
