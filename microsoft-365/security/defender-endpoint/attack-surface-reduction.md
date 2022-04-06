---
title: Brug regler for reduktion af angrebsoverfladen til at forhindre malware inficeret
description: Regler for reduktion af angrebsoverfladen kan hjælpe med at forhindre udnyttelse i at bruge apps og scripts til at inficere enheder med malware.
keywords: Regler for reduktion af angrebsoverfladen, asr, hips, forebyggelse af indtrængen, beskyttelsesregler, antieksploit, udnyttelse, forebyggelse af indtrængen, Microsoft Defender til slutpunkt
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
ms.date: 1/18/2022
ms.openlocfilehash: 53f338ec713038841ab5cc089c12cebf7fe46131
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680615"
---
# <a name="attack-surface-reduction-rules-overview"></a>Oversigt over regler for reduktion af angrebsoverfladen

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="why-attack-surface-reduction-rules-are-important"></a>Derfor er begrænsningsregler for angrebsoverfladen vigtige

Din organisations angrebsoverflade omfatter alle de steder, hvor en hacker kan kompromittere din organisations enheder eller netværk. At reducere din angrebsoverflade betyder, at du beskytter din organisations enheder og netværk, hvilket efterlader hackere med færre måder at udføre angreb på. Konfiguration af regler for reduktion af angrebsoverfladen i Microsoft Defender til slutpunkt kan hjælpe!

Regler for reduktion af angrebsoverfladen målretter visse softwarefunktionsmåder, f.eks.:

- Åbne eksekverbare filer og scripts, der forsøger at hente eller køre filer
- Kører obskøne eller på anden måde mistænkelige scripts
- Udføre funktionsmåder, som apps normalt ikke starter ved normalt arbejde fra dag til dag

Sådanne softwarefunktionsmåder ses nogle gange i legitime programmer. Disse handlinger anses dog ofte for risikabelt, fordi de ofte misbruges af hackere via malware. Regler for reduktion af angrebsoverfladen kan begrænse softwarebaseret risikabel adfærd og hjælpe med at beskytte din organisation.

Du kan finde flere oplysninger om konfiguration af regler for reduktion af angrebsoverfladen [i Aktivér regler for reduktion af angrebsoverfladen](enable-attack-surface-reduction.md).

## <a name="assess-rule-impact-before-deployment"></a>Vurder regelpåvirkning før installation

Du kan vurdere, hvordan en reduktionsregel for angrebsoverfladen kan påvirke dit netværk ved at åbne sikkerhedsanbefalingen for den [pågældende regel Håndtering af trusler og sikkerhedsrisici](/windows/security/threat-protection/#tvm).

:::image type="content" source="images/asrrecommendation.png" alt-text="Sikkerheds-reco for begrænsningsregel for angrebsoverfladen.":::

I detaljeruden på anbefalingen skal du kontrollere, om der er brugerpåvirkning for at afgøre, hvilken procentdel af dine enheder, der kan acceptere en ny politik, som aktiverer reglen i blokeringstilstand uden at påvirke produktiviteten negativt.

Se [kravene](enable-attack-surface-reduction.md#requirements) i artiklen "Aktivér regler for reduktion af angrebsoverfladen", hvis du vil have mere at vide om understøttede operativsystemer og yderligere kravoplysninger.

## <a name="audit-mode-for-evaluation"></a>Overvågningstilstand til evaluering

Brug [overvågningstilstand til at](audit-windows-defender.md) evaluere, hvordan reduktionsregler for angrebsoverfladen vil påvirke din organisation, hvis den er aktiveret. Kør alle regler i overvågningstilstand først, så du kan forstå, hvordan de påvirker dine line of business-programmer. Mange line of business-programmer er skrevet med begrænsede sikkerhedsproblemer, og de kan udføre opgaver på måder, der ligner malware. Ved at overvåge overvågningsdata og [tilføje undtagelser](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) for nødvendige programmer kan du implementere regler for reduktion af angrebsoverfladen uden at reducere produktiviteten.

## <a name="warn-mode-for-users"></a>Advarselstilstand for brugere

(**NY**!) Før du advarer om funktioner til advarselstilstand, kan regler for reduktion af angrebsoverfladen, der er aktiveret, indstilles til enten overvågningstilstand eller blokeringstilstand. Med den nye advarselstilstand, når indhold blokeres af en regel for reduktion af angrebsoverfladen, kan brugerne se en dialogboks, der angiver, at indholdet er blokeret. Dialogboksen giver også brugeren mulighed for at fjerne blokeringen af indholdet. Brugeren kan derefter prøve at udføre handlingen igen, og handlingen fuldføres. Når en bruger fjerner blokeringen af indhold, forbliver blokeringen af indholdet blokeret i 24 timer og blokerer derefter cv'er.

Tilstanden Advar hjælper din organisation med at få regler for reduktion af angrebsoverfladen på plads uden at forhindre brugere i at få adgang til det indhold, de skal bruge for at udføre deres opgaver.

### <a name="requirements-for-warn-mode-to-work"></a>Krav til, at advarselstilstand fungerer

Advarselstilstand understøttes på enheder, der kører følgende versioner af Windows:

- [Windows 10, version 1809](/windows/whats-new/whats-new-windows-10-version-1809) eller nyere
- Windows 11
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809) eller nyere

Microsoft Defender Antivirus skal køre med beskyttelse i realtid i [aktiv tilstand](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state).

Sørg også for, [Microsoft Defender Antivirus og antimalwareopdateringer](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions) er installeret.

- Minimumskrav til udgivelse til platform: `4.18.2008.9`
- Minimumskrav til programudgivelse: `1.1.17400.5`

Du kan finde flere oplysninger om og få dine opdateringer [under Opdatering til Microsoft Defender-antimalwareplatform](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform).

### <a name="cases-where-warn-mode-is-not-supported"></a>Tilfælde, hvor advarselstilstand ikke understøttes

Advarselstilstand understøttes ikke for tre regler for reduktion af angrebsoverfladen, når du konfigurerer dem Microsoft Endpoint Manager. (Hvis du bruger en Gruppepolitik konfigurere dine regler for reduktion af angrebsoverfladen, understøttes advarselstilstand). De tre regler, der ikke understøtter advarselstilstand, når du konfigurerer dem i Microsoft Endpoint Manager er som følger:

- [Bloker JavaScript eller VBScript fra at starte hentet eksekverbart indhold](attack-surface-reduction-rules-reference.md#block-javascript-or-vbscript-from-launching-downloaded-executable-content) (GUID `d3e037e1-3eb8-44c8-a917-57927947596d`)
- [Bloker vedholdenhed gennem WMI-hændelsesabonnement](attack-surface-reduction-rules-reference.md#block-persistence-through-wmi-event-subscription) (GUID `e6db77e5-3df2-4cf1-b95a-636979351e5b`)
- [Brug avanceret beskyttelse mod ransomware](attack-surface-reduction-rules-reference.md#use-advanced-protection-against-ransomware) (GUID `c1db55ab-c21a-4637-bb3f-a12568109d35`)

Tilstanden Advar understøttes heller ikke på enheder, der kører ældre versioner Windows. I disse tilfælde kører reduktionsregler for angrebsoverfladen, der er konfigureret til at køre i advarselstilstand, i blokeringstilstand.

## <a name="notifications-and-alerts"></a>Meddelelser og beskeder

Når der udløses en regel for reduktion af angrebsoverfladen, vises der en meddelelse på enheden. Du kan [tilpasse meddelelsen med](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) dine firmaoplysninger og kontaktoplysninger.

Når visse reduktionsregler for angrebsoverfladen udløses, genereres der også beskeder.

Meddelelser og eventuelle beskeder, der genereres, kan ses på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>.

Du kan finde specifikke oplysninger om meddelelses- og beskedfunktionalitet [i: Oplysninger](attack-surface-reduction-rules-reference.md#per-rule-alert-and-notification-details) om beskeder og meddelelser for hver regel i artiklen **Referenceoplysninger om reduktionsregler for angrebsoverfladen**.

## <a name="advanced-hunting-and-attack-surface-reduction-events"></a>Avanceret reduktion af jagt- og angrebsoverfladen

Du kan bruge avanceret jagt til at få vist hændelser til reduktion af angrebsoverfladen. For at strømline mængden af indgående data er det kun unikke processer for hver time, der kan vises med avanceret jagt. Tidspunktet for en reduktion af angrebsoverfladen er første gang, begivenheden ses inden for timen.

Antag f.eks., at en hændelse med reduktion af angrebsoverfladen forekommer på 10 enheder i løbet af 14:00-timen. Antag, at den første hændelse forekom kl. 2:15 og den sidste kl. 2:45. Med avanceret jagt kan du se en forekomst af den pågældende begivenhed (også selvom den faktisk fandt sted på 10 enheder), og dens tidsstempel er 14:15.

Du kan finde flere oplysninger om avanceret [jagt under Proaktivt lede efter trusler med avanceret jagt](advanced-hunting-overview.md).

## <a name="attack-surface-reduction-features-across-windows-versions"></a>Reduktionsfunktioner til angrebsoverfladen på tværs Windows versioner

Du kan angive reduktionsregler for angrebsoverfladen for enheder, der kører en af følgende versioner og versioner af Windows:

- Windows 10 Pro, [version 1709](/windows/whats-new/whats-new-windows-10-version-1709) eller nyere
- Windows 10 Enterprise, [version 1709](/windows/whats-new/whats-new-windows-10-version-1709) eller nyere
- Windows Server, [version 1803 (halvårlige kanal)](/windows-server/get-started/whats-new-in-windows-server-1803) eller senere
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/win32/srvnodes/what-s-new-for-windows-server-2012-r2)

  >[!NOTE]
  >Windows Server 2016 og Windows Server 2012 R2 skal være onboardet ved hjælp af instruktionerne i [Onboard Windows-servere](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016), for at denne funktion kan fungere.

Selvom regler for reduktion af angrebsoverfladen ikke kræver [en Windows E5-licens](/windows/deployment/deploy-enterprise-licenses), får du avancerede administrationsfunktioner, hvis Windows E5. De avancerede funktioner – som kun er tilgængelige i Windows E5 – omfatter:

- Overvågning, analyse og arbejdsprocesser, der er tilgængelige i [Defender til Slutpunkt](microsoft-defender-endpoint.md)
- Rapporterings- og konfigurationsfunktionerne [i Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

Disse avancerede funktioner er ikke tilgængelige med en Windows Professional eller Windows E3-licens. Men hvis du har disse licenser, kan du bruge Logbog og Microsoft Defender Antivirus til at gennemse dine reduktionshændelser for angrebsoverfladen.

## <a name="review-attack-surface-reduction-events-in-the-microsoft-365-defender-portal"></a>Gennemse hændelser til reduktion af angrebsoverfladen i Microsoft 365 Defender-portalen

Defender til Slutpunkt giver detaljeret rapportering om hændelser og blokke som en del af scenarier med undersøgelse af beskeder.

Du kan forespørge på Defender til slutpunktsdata [i Microsoft 365 Defender ved](microsoft-defender-endpoint.md) hjælp af [avanceret jagt](/microsoft-365/security/defender/advanced-hunting-query-language). 

Her er en eksempelforespørgsel:

```kusto
DeviceEvents
| where ActionType startswith 'Asr'
```

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>Gennemse hændelser til reduktion af angrebsoverfladen i Windows Event Viewer

Du kan gennemse hændelsesloggen Windows for at få vist hændelser, der genereres af regler for reduktion af angrebsoverfladen:

1. Download [evalueringspakken](https://aka.ms/mp7z2w) , og udtræk *filencfa-events.xml* en lettilgængelig placering på enheden.

2. Skriv ordene, *Logvisning, i* menuen Start for at åbne Windows Log på.

3. Under **Handlinger skal** du vælge **Importér brugerdefineret visning...**.

4. Vælg den fil *cfa-events.xmlfra* det sted, hvor den blev hentet fra. Alternativt kan du [kopiere XML direkte](event-views.md).

5. Vælg **OK**.

Du kan oprette en brugerdefineret visning, der filtrerer hændelser til kun at vise følgende hændelser, som alle er relateret til styret mappeadgang:

|Hændelses-id|Beskrivelse|
|---|---|
|5007|Hændelse, når indstillingerne ændres|
|1121|Hændelse, når reglen udløses i bloktilstand|
|1122|Hændelse, når reglen udløses i overvågningstilstand|

Den "programversion", der er angivet for hændelser til reduktion af angrebsoverfladen i hændelsesloggen, genereres af Defender til Slutpunkt, ikke af operativsystemet. Defender til Slutpunkt er integreret med Windows 10 Windows 11, så denne funktion fungerer på alle enheder med Windows 10 eller Windows 11 installeret.
