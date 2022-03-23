---
title: Sårbarheder i min organisation – Håndtering af trusler og sikkerhedsrisici
description: Viser de almindelige sårbarheder og eksponerings-id'er (CVE) for det program, der kører i organisationen. Den findes af Microsoft Defender for Håndtering af trusler og sikkerhedsrisici slutpunktsfunktionaliteten.
keywords: Microsoft Defender for Endpoint threat & håndtering af sikkerhedsrisici, Håndtering af trusler og sikkerhedsrisici, Microsoft Defender for Endpoint tvm at finde flere personer via tvm, liste over tvm-sikkerhedsrisiko, oplysninger om sikkerhedsrisiko i tvm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 23b0235382e748071f0d8e060e15624b5332326d
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/17/2022
ms.locfileid: "63591921"
---
# <a name="vulnerabilities-in-my-organization---threat-and-vulnerability-management"></a>Sårbarheder i min organisation – Håndtering af trusler og sikkerhedsrisici

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Trussel og håndtering af sikkerhedsrisici](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

> [!IMPORTANT]
> Trussels- håndtering af sikkerhedsrisici kan hjælpe med at identificere logfiler i programmer og komponenter. [Få mere at vide](https://www.microsoft.com/security/blog/2021/12/11/guidance-for-preventing-detecting-and-hunting-for-cve-2021-44228-log4j-2-exploitation/#TVM).

Trussels- håndtering af sikkerhedsrisici bruger de samme signaler i Defender til slutpunktsbeskyttelse til at scanne og registrere sårbarheder.

På **siden Det varsler** en liste over de softwarerisici, dine enheder er eksponeret for, ved at angive CVE-id'et (Common Vulnerabilities and Exposures). Du kan også få vist klassifikationen af Common Vulnerability Score System (CVSS), din organisations sikkerhed, tilsvarende brud, trusselsindsigt og meget mere.

> [!NOTE]
> Hvis der ikke er tildelt et officielt CVE-ID til en sikkerhedsrisiko, tildeles navnet på sikkerhedsrisikoen af Håndtering af trusler og sikkerhedsrisici.

> [!TIP]
> Hvis du vil have mails om nye sikkerhedsrisikohændelser, skal [du se Konfigurer mailbeskeder om sikkerhedsrisiko i Microsoft Defender til Endpoint](configure-vulnerability-email-notifications.md)

## <a name="navigate-to-the-weaknesses-page"></a>Gå til siden Foretaler

Få adgang til siden Meddelses her et par forskellige måder:

- Valg af **sårbarheder** fra **navigationsmenuen til** administration af sikkerhedsrisiko [i Microsoft 365 Defender portal](portal-overview.md)
- Global søgning

### <a name="navigation-menu"></a>Navigationsmenu

Gå til **navigationsmenuen for** sikkerhedsrisikoadministration, og vælg **Sikkerhedsrisikoe** for at åbne listen over CVEs.

### <a name="vulnerabilities-in-global-search"></a>Sårbarheder i global søgning

1. Gå til rullemenuen Global søgning.
2. Vælg **Sikkerhedsrisiko** og nøgle-in det CVE-id (Common Vulnerabilities and Exposures), du leder efter, og vælg derefter søgeikonet. **SidenNæs** åbnes med de CVE-oplysninger, du leder efter.
![Global søgefelt med rullelisteindstillingen "sikkerhedsrisiko" markeret og et eksempel på CVE.](images/tvm-vuln-globalsearch.png)
3. Vælg CVE for at åbne et pop op-panel med flere oplysninger, herunder beskrivelse af sikkerhedsrisikoen, detaljer, trusselsindsigt og blotlagte enheder.

Skriv CVE, og vælg derefter søg for at **få vist** resten af sårbarhederne på siden Hjælpende indhold.

## <a name="weaknesses-overview"></a>Oversigt over oversigten over de forskellige fliser

Afhjulpet sårbarhederne i enheder, der er eksponeret for, for at reducere risikoen for aktiverne og organisationen. Hvis kolonnen **Kun eksponerede** enheder viser 0, betyder det, at du ikke er i fare.

![Det viser landingssiden.](images/tvm-weaknesses-overview.png)

### <a name="breach-and-threat-insights"></a>Indsigt i brud og trusler

Få vist relateret indsigt i brud og trusler i **kolonnen Trussel** , når ikonerne er farvet røde.

 > [!NOTE]
 > Prioriter altid anbefalinger, der er knyttet til løbende trusler. Disse anbefalinger er markeret med ikonet trusselsindsigt ![Simpel tegning af en rød fejl.](images/tvm_bug_icon.png) ikon for indsigt i brud ![Tegning af en pil, der rammer et mål](images/tvm_alert_icon.png).

Ikonet for indsigt i brud er fremhævet, hvis der er fundet en sikkerhedsrisiko i din organisation.
![Eksempel på en tekst med indsigt i brud, der kan vises, når du peger på et ikon. Denne her siger "mulig aktiv besked er knyttet til denne anbefaling.](images/tvm-breach-insights.png)

Ikonet for trusselsindsigt fremhæves, hvis der er tilknyttede udnyttelser i den sikkerhedsrisiko, der findes i organisationen. Når du holder musen hen over ikonet, kan du se, om truslerne er en del af en exploit kit eller forbundet til bestemte avancerede, permanente kampagner eller aktivitetsgrupper. Når den er tilgængelig, er der et link til en Threat Analytics-rapport med nyheder om udnyttelse uden dag, oplysninger eller relaterede sikkerhedsrådgivere.

![Tekst med trusselsindsigt, der kan vises, når musen holdes over et ikon. Denne har flere punkttegn og sammenkædet tekst.](images/tvm-threat-insights.png)

### <a name="gain-vulnerability-insights"></a>Få indsigt i sikkerhedsrisiko

Hvis du vælger en CVE, åbnes et pop op-panel med flere oplysninger om sikkerhedsrisikoen, detaljer om sikkerhedsrisikoen, trusselsindsigt og tilgængelige enheder.

- Kategorien "OS-funktion" vises i relevante scenarier
- Du kan gå til den relaterede sikkerhedsanbefaling for hver CVE med blotlagt enhed

 ![Eksempel på valg af pop op-punkt.](images/tvm-weakness-flyout400.png)

### <a name="software-that-isnt-supported"></a>Software, der ikke understøttes

CVEs til software, der i øjeblikket ikke understøttes af & håndtering af sikkerhedsrisici, findes stadig på siden Meddelsestegn. Da softwaren ikke understøttes, vil kun begrænsede data være tilgængelige.

Tilgængelige enhedsoplysninger vil ikke være tilgængelige for CV'er med ikke-understøttet software. Filtrer efter software, der ikke understøttes, ved at vælge indstillingen "Ikke tilgængelig" i afsnittet "Tilgængelige enheder".

:::image type="content" alt-text="Filter for eksponerede enheder." source="images/tvm-exposed-devices-filter.png":::

## <a name="view-common-vulnerabilities-and-exposures-cve-entries-in-other-places"></a>Få vist almindelige sårbarheder og eksponeringer (CVE)-poster andre steder

### <a name="top-vulnerable-software-in-the-dashboard"></a>En af de mest følsomme software på dashboardet

1. Gå til [dashboardet Håndtering af trusler og sikkerhedsrisici, og](tvm-dashboard-insights.md) rul ned til **den mest følsomme softwarewidget**. Du kan se antallet af sårbarheder, der er i hver software, samt trusselsoplysninger og en højniveauvisning af enheds eksponering over tid.

    ![Mest sårbar softwarekort med fire kolonner: software, trusler, enheder, der er eksponeret.](images/tvm-top-vulnerable-software500.png)

2. Vælg den software, du vil undersøge, for at gå til en detaljeud detaljeringsside.

3. Vælg fanen **Opdagede sårbarheder** .

4. Vælg den sikkerhedsrisiko, du vil undersøge for flere oplysninger om sikkerhedsrisikoens detaljer

    ![Windows oversigt over detaljer i Server 2019.](images/windows-server-drilldown.png)

### <a name="discover-vulnerabilities-in-the-device-page"></a>Opdag sårbarheder på enhedssiden

Få vist relaterede oplysninger om enheder på enhedens side.

1. Gå til Microsoft 365 Defender navigationsmenulinjen, og vælg derefter enhedsikonet. **Lagersiden for** enheden åbnes.

2. På siden **Lager over** enheder skal du vælge navnet på den enhed, du vil undersøge.

    ![Enhedsliste med valgt enhed til undersøgelse.](images/tvm_machinetoinvestigate.png)

3. Enhedssiden åbnes med detaljer og svarindstillinger for den enhed, du vil undersøge.

4. Vælg **Opdagede sårbarheder**.

   :::image type="content" alt-text="Enhedsside med detaljer og svarindstillinger." source="images/tvm-discovered-vulnerabilities.png" lightbox="images/tvm-discovered-vulnerabilities.png":::

5. Vælg den sikkerhedsrisiko, du vil undersøge for at åbne et pop op-panel med CVE-oplysninger, f.eks. beskrivelse af sikkerhedsrisiko, trusselsindsigt og registreringslogik.

#### <a name="cve-detection-logic"></a>Logik til registrering af CVE

Ligesom software beviserne viser vi nu den registreringslogik, vi anvendte på en enhed, for at angive, at den er sårbar. Den nye sektion kaldes "Registreringslogik" (i enhver opdaget sikkerhedsrisiko på enhedssiden) og viser registreringslogik og kilde.

Kategorien "OS-funktion" vises også i relevante scenarier. En CVE vil kun påvirke enheder, der kører et sårbar os, hvis en bestemt OS-komponent er aktiveret. Lad os sige, Windows Server 2019 eller Windows Server 2022 er sikkerhedsrisiko i deres DNS-komponent. Med denne nye funktion vedhæfter vi kun denne CVE til Windows Server 2019- og Windows Server 2022-enheder med DNS-funktionen aktiveret i deres OPERATIVSYSTEM.

:::image type="content" alt-text="Eksempel på registreringslogik, der viser den software, der registreres på enheden, og DEK'er." source="images/tvm-cve-detection-logic.png":::

## <a name="report-inaccuracy"></a>Rapportér unøjagtighed

Rapportér en falsk positiv, når der vises uklare, unøjagtige eller ufuldstændige oplysninger. Du kan også rapportere om sikkerhedsanbefalinger, der allerede er blevet løst.

1. Åbn CVE'en på siden Cv'et.
2. Vælg **Unøjagtighed for rapport,** og en rude med pop op-vinduer åbnes.
3. Vælg kategorien unøjagtighed i rullemenuen, og udfyld din mailadresse og oplysninger om unøjagtighed.
4. Vælg **Send**. Din feedback sendes straks til Håndtering af trusler og sikkerhedsrisici eksperter.

## <a name="related-articles"></a>Relaterede artikler

- [Oversigt over trusler håndtering af sikkerhedsrisici sikkerhed](next-gen-threat-and-vuln-mgt.md)
- [Sikkerhedsanbefalinger](tvm-security-recommendation.md)
- [Lager over software](tvm-software-inventory.md)
- [Dashboardindsigt](tvm-dashboard-insights.md)
- [Få vist og organiser listen over Microsoft Defender til slutpunktsenheder](machines-view-overview.md)
