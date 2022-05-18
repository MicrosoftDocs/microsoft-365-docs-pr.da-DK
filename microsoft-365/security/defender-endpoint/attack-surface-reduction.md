---
title: Brug regler for reduktion af angrebsoverfladen for at forhindre malware-infektion
description: Regler for reduktion af angrebsoverfladen kan forhindre udnyttelser i at bruge apps og scripts til at inficere enheder med malware.
keywords: Angreb overfladereduktion regler, asr, hofter, vært intrusion forebyggelse system, beskyttelsesregler, anti-exploit, anti-exploit, udnytte, infektion forebyggelse, Microsoft Defender for Endpoint
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
ms.custom:
- asr
- admindeeplinkDEFENDER
ms.technology: mde
ms.topic: article
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.openlocfilehash: a5ca2613028e892229da1888c6176cb729e0cf1b
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469574"
---
# <a name="attack-surface-reduction-rules-overview"></a>Oversigt over regler for reduktion af angrebsoverflade

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Microsoft Defender Antivirus

**Platforme**
- Windows

## <a name="why-attack-surface-reduction-rules-are-important"></a>Hvorfor regler for reduktion af angrebsoverfladen er vigtige

Din organisations angrebsoverflade indeholder alle de steder, hvor en hacker kan kompromittere organisationens enheder eller netværk. Reduktion af angrebsoverfladen betyder beskyttelse af organisationens enheder og netværk, hvilket efterlader hackere med færre måder at udføre angreb på. Konfiguration af regler for reduktion af angrebsoverfladen i Microsoft Defender for Endpoint kan hjælpe!

Regler for reduktion af angrebsoverfladen er målrettet bestemte softwarefunktioner, f.eks.:

- Start af eksekverbare filer og scripts, der forsøger at downloade eller køre filer
- Kørsel af slørede eller på anden måde mistænkelige scripts
- Udførelse af funktionsmåder, som apps normalt ikke initierer under normalt dag-til-dag-arbejde

Sådanne software adfærd er nogle gange set i legitime applikationer. Disse funktionsmåder betragtes dog ofte som risikable, fordi de ofte misbruges af hackere via malware. Regler for reduktion af angrebsoverfladen kan begrænse softwarebaserede risikable funktionsmåder og hjælpe med at beskytte din organisation.

Du kan få flere oplysninger om konfiguration af regler for reduktion af angrebsoverfladen under [Aktivér regler for reduktion af angrebsoverfladen](enable-attack-surface-reduction.md).

## <a name="assess-rule-impact-before-deployment"></a>Vurder regelvirkning før udrulning

Du kan vurdere, hvordan en regel for reduktion af angrebsoverfladen kan påvirke dit netværk ved at åbne sikkerhedsanbefalingerne for den pågældende regel i [Håndtering af trusler og sikkerhedsrisici](/windows/security/threat-protection/#tvm).

:::image type="content" source="images/asrrecommendation.png" alt-text="ASR-anbefalingen" lightbox="images/asrrecommendation.png":::

I ruden med anbefalingsoplysninger skal du kontrollere, om brugeren har indflydelse, for at bestemme, hvilken procentdel af dine enheder der kan acceptere en ny politik, der aktiverer reglen i blokeringstilstand, uden at det påvirker produktiviteten negativt.

Se [Krav](enable-attack-surface-reduction.md#requirements) i artiklen "Aktivér regler for reduktion af angrebsoverfladen" for at få oplysninger om understøttede operativsystemer og yderligere kravoplysninger.

## <a name="audit-mode-for-evaluation"></a>Overvågningstilstand til evaluering

Brug [overvågningstilstand](audit-windows-defender.md) til at evaluere, hvordan regler for reduktion af angrebsoverfladen ville påvirke din organisation, hvis den er aktiveret. Kør først alle regler i overvågningstilstand, så du kan forstå, hvordan de påvirker dine line of business-programmer. Mange line-of-business-programmer skrives med begrænsede sikkerhedsproblemer, og de kan udføre opgaver på måder, der synes at ligne malware. Ved at overvåge overvågningsdata og [tilføje udeladelser](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) for nødvendige programmer kan du udrulle regler for reduktion af angrebsoverfladen uden at reducere produktiviteten.

## <a name="warn-mode-for-users"></a>Advarselstilstand for brugere

(**NY**!) Før du advarer om tilstandsfunktioner, kan regler for reduktion af angrebsoverfladen, der er aktiveret, indstilles til enten overvågningstilstand eller bloktilstand. Med den nye advarselstilstand kan brugerne se en dialogboks, der angiver, at indholdet er blokeret, når indhold er blokeret af en regel for reduktion af angrebsoverfladen. Dialogboksen giver også brugeren mulighed for at fjerne blokeringen af indholdet. Brugeren kan derefter prøve at udføre handlingen igen, så fuldføres handlingen. Når en bruger fjerner blokeringen af indhold, fjernes blokeringen af indholdet i 24 timer, og blokeringen af genoptages derefter.

Advarselstilstand hjælper din organisation med at have regler for reduktion af angrebsoverfladen på plads uden at forhindre brugerne i at få adgang til det indhold, de har brug for til at udføre deres opgaver.

### <a name="requirements-for-warn-mode-to-work"></a>Krav til advarselstilstand for at fungere

Advarselstilstand understøttes på enheder, der kører følgende versioner af Windows:

- [Windows 10, version 1809](/windows/whats-new/whats-new-windows-10-version-1809) eller nyere
- Windows 11
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809) eller nyere

Microsoft Defender Antivirus skal køre med beskyttelse i realtid i [aktiv tilstand](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state).

Sørg også for, at [Microsoft Defender Antivirus og antimalwareopdateringer](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions) er installeret.

- Minimumkrav til udgivelse af platform: `4.18.2008.9`
- Minimumkrav til udgivelse af motor: `1.1.17400.5`

Du kan få flere oplysninger og hente dine opdateringer under [Opdater til Microsoft Defender-platformen til antimalware](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform).

### <a name="cases-where-warn-mode-is-not-supported"></a>Tilfælde, hvor advarselstilstand ikke understøttes

Advarselstilstand understøttes ikke for tre regler for reduktion af angrebsoverfladen, når du konfigurerer dem i Microsoft Endpoint Manager. (Hvis du bruger Gruppepolitik til at konfigurere dine regler for reduktion af angrebsoverfladen, understøttes advarselstilstand). De tre regler, der ikke understøtter advarselstilstand, når du konfigurerer dem i Microsoft Endpoint Manager, er som følger:

- [Bloker JavaScript eller VBScript fra start af downloadet eksekverbart indhold](attack-surface-reduction-rules-reference.md#block-javascript-or-vbscript-from-launching-downloaded-executable-content) (GUID `d3e037e1-3eb8-44c8-a917-57927947596d`)
- [Bloker vedholdenhed via WMI-hændelsesabonnement](attack-surface-reduction-rules-reference.md#block-persistence-through-wmi-event-subscription) (GUID `e6db77e5-3df2-4cf1-b95a-636979351e5b`)
- [Brug avanceret beskyttelse mod ransomware](attack-surface-reduction-rules-reference.md#use-advanced-protection-against-ransomware) (GUID `c1db55ab-c21a-4637-bb3f-a12568109d35`)

Advarselstilstand understøttes heller ikke på enheder, der kører ældre versioner af Windows. I disse tilfælde vil regler for reduktion af angrebsoverfladen, der er konfigureret til at køre i advarselstilstand, køre i blokeringstilstand.

## <a name="notifications-and-alerts"></a>Meddelelser og beskeder

Når en regel for reduktion af angrebsoverfladen udløses, vises der en meddelelse på enheden. Du kan [tilpasse meddelelsen](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) med dine firmaoplysninger og kontaktoplysninger.

Når visse regler for reduktion af angrebsoverfladen udløses, genereres der også beskeder.

Meddelelser og eventuelle beskeder, der genereres, kan ses på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>.

Du kan finde specifikke oplysninger om funktionalitet for meddelelser og beskeder under: [Oplysninger om regelbeskeder og meddelelser](attack-surface-reduction-rules-reference.md#per-rule-alert-and-notification-details) i artiklen **Reference til regler for reduktion af angrebsoverflade**.

## <a name="advanced-hunting-and-attack-surface-reduction-events"></a>Avancerede hændelser for reduktion af jagt- og angrebsoverfladen

Du kan bruge avanceret jagt til at få vist hændelser for reduktion af angrebsoverfladen. For at strømline mængden af indgående data er det kun unikke processer for hver time, der kan ses med avanceret jagt. Tidspunktet for en hændelse til reduktion af angrebsoverfladen er første gang, at hændelsen ses inden for en time.

Antag f.eks., at der forekommer en hændelse til reduktion af angrebsoverfladen på 10 enheder i løbet af 14:00-timen. Lad os antage, at den første hændelse fandt sted kl. 2:15 og den sidste kl. 2:45. Ved avanceret jagt kan du se én forekomst af hændelsen (selvom den rent faktisk fandt sted på 10 enheder), og tidsstemplet er 14:15.

Du kan finde flere oplysninger om avanceret jagt under [Proaktiv jagt efter trusler med avanceret jagt](advanced-hunting-overview.md).

## <a name="attack-surface-reduction-features-across-windows-versions"></a>Reduktion af angrebsoverfladen på tværs af Windows versioner

Du kan angive regler for reduktion af angrebsoverfladen for enheder, der kører en af følgende versioner af Windows:

- Windows 10 Pro[, version 1709](/windows/whats-new/whats-new-windows-10-version-1709) eller nyere
- Windows 10 Enterprise, [version 1709](/windows/whats-new/whats-new-windows-10-version-1709) eller nyere
- Windows Server, [version 1803 (halvårlig kanal)](/windows-server/get-started/whats-new-in-windows-server-1803) eller nyere
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/hh801901(v=ws.11))

  >[!NOTE]
  >Windows Server 2016 og Windows Server 2012 R2 skal onboardes ved hjælp af vejledningen i [Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), for at denne funktion kan fungere.

Selvom regler for reduktion af angrebsoverfladen ikke kræver en [Windows E5-licens](/windows/deployment/deploy-enterprise-licenses), får du avancerede administrationsfunktioner, hvis du har Windows E5. De avancerede funktioner – kun tilgængelige i Windows E5 – omfatter:

- Overvågning, analyse og arbejdsprocesser, der er tilgængelige i [Defender for Endpoint](microsoft-defender-endpoint.md)
- Funktionerne til rapportering og konfiguration i [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

Disse avancerede funktioner er ikke tilgængelige med en Windows Professional- eller Windows E3-licens. Men hvis du har disse licenser, kan du bruge Logbog og Microsoft Defender Antivirus logge til at gennemse hændelserne for reglen for reduktion af angrebsoverfladen.

## <a name="review-attack-surface-reduction-events-in-the-microsoft-365-defender-portal"></a>Gennemse hændelser for reduktion af angrebsoverfladen på Microsoft 365 Defender-portalen

Defender for Endpoint giver detaljeret rapportering for hændelser og blokke som en del af scenarier med undersøgelse af beskeder.

Du kan forespørge Defender om slutpunktsdata i [Microsoft 365 Defender](microsoft-defender-endpoint.md) ved hjælp af [avanceret jagt](/microsoft-365/security/defender/advanced-hunting-query-language). 

Her er et eksempel på en forespørgsel:

```kusto
DeviceEvents
| where ActionType startswith 'Asr'
```

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>Gennemse hændelser for reduktion af angrebsoverfladen i Windows Logbog

Du kan gennemse Windows hændelsesloggen for at få vist hændelser, der er genereret af regler for reduktion af angrebsoverfladen:

1. Download [evalueringspakken](https://aka.ms/mp7z2w) , og udtræk filen *cfa-events.xml* til en placering, der er let tilgængelig på enheden.

2. Indtast ordene *Logbog* i menuen Start for at åbne Windows Logbog.

3. Under **Handlinger** skal du vælge **Importér brugerdefineret visning...**.

4. Vælg filen *cfa-events.xml* , hvor den blev udpakket fra. Du kan også [kopiere XML-koden direkte](event-views.md).

5. Vælg **OK**.

Du kan oprette en brugerdefineret visning, der filtrerer hændelser, så de kun viser følgende hændelser, som alle er relateret til kontrolleret mappeadgang:

|Hændelses-id|Beskrivelse|
|---|---|
|5007|Hændelse, når indstillingerne ændres|
|1121|Hændelse, når reglen udløses i bloktilstand|
|1122|Hændelse, når reglen udløses i overvågningstilstand|

Den "programversion", der er angivet for hændelser for reduktion af angrebsoverfladen i hændelsesloggen, genereres af Defender for Endpoint og ikke af operativsystemet. Defender for Endpoint er integreret med Windows 10 og Windows 11, så denne funktion fungerer på alle enheder, hvor Windows 10 eller Windows 11 er installeret.

> [!TIP]
> Hvis du leder efter antivirusrelaterede oplysninger til andre platforme, skal du se:
> - [Angiv indstillinger for Microsoft Defender for Endpoint på macOS-](mac-preferences.md)
> - [Microsoft Defender for Endpoint på Mac](microsoft-defender-endpoint-mac.md)
> - [Politikindstillinger for macOS Antivirus for Microsoft Defender Antivirus for Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Angiv indstillinger for Microsoft Defender for Endpoint på Linux](linux-preferences.md)
> - [Microsoft Defender for Endpoint på Linux](microsoft-defender-endpoint-linux.md)
> - [Konfigurer Defender for Endpoint på Android-funktioner](android-configure.md)
> - [Konfigurer Microsoft Defender for Endpoint på iOS-funktioner](ios-configure-features.md)
