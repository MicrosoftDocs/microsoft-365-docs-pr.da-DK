---
title: Oversigt over Microsoft Defender for Endpoint Plan 1
description: Få et overblik over Defender for Endpoint Plan 1. Få mere at vide om de funktioner og funktioner, der er inkluderet i dette abonnement på slutpunktsbeskyttelse.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/19/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.custom: intro-overview
ms.openlocfilehash: 50dbe395bee852601aae8e834514c6bbac3dd84d
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63594610"
---
# <a name="overview-of-microsoft-defender-for-endpoint-plan-1"></a>Oversigt over Microsoft Defender for Endpoint Plan 1

**Gælder for**

- [Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender til Slutpunkt er en sikkerhedsplatform til virksomheder, der er udviklet til at hjælpe organisationer som din til at forhindre, registrere, undersøge og reagere på avancerede trusler. Vi er glade for at kunne meddele, at Defender til slutpunkt nu er tilgængelig i to planer: 

- **Defender for Endpoint Plan 1**, beskrevet i denne artikel; og 
- **[Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)**, generelt tilgængelig, og tidligere kendt som [Defender for Endpoint](microsoft-defender-endpoint.md).

De grønne felter i følgende billede afbilder, hvad der er inkluderet i Defender til Endpoint Plan 1:

:::image type="content" source="../../media/mde-p1/mde-p1-overview-diagram.png" alt-text="Defender for Endpoint Plan 1-diagram":::

Brug denne vejledning til at:

- [Få et overblik over, hvad der er inkluderet i Defender til Endpoint Plan 1](#defender-for-endpoint-plan-1-capabilities)
- [Sammenlign Defender for Endpoint Plan 1 med Plan 2](defender-endpoint-plan-1-2.md)
- [Få mere at vide om, hvordan du konfigurerer Defender til Endpoint Plan 1](mde-p1-setup-configuration.md)
- [Kom i gang med Microsoft 365 Defender, hvor du kan se hændelser og beskeder, administrere enheder og bruge rapporter om registrerede trusler](mde-plan1-getting-started.md)
- [Få et overblik over vedligeholdelse og handlinger](mde-p1-maintenance-operations.md)

> [!TIP]
> [Få mere at vide om forskellene mellem Defender for Endpoint Plan 1 og Plan 2](defender-endpoint-plan-1-2.md).

## <a name="defender-for-endpoint-plan-1-capabilities"></a>Defender for Endpoint Plan 1-funktioner

Defender til Endpoint Plan 1 indeholder følgende funktioner:

- **[Næste generations beskyttelse omfatter](#next-generation-protection)** brancheførende, robust antimalware og antivirusbeskyttelse
- **[Manuelle svarhandlinger](#manual-response-actions)**, f.eks. sende en fil til karantæne, som dit sikkerhedsteam kan tage på enheder eller filer, når der registreres trusler
- **[Muligheder for reduktion af angrebsoverfladen](#attack-surface-reduction)** , der gør enhederne hårde, forhindrer zero-day-angreb og giver detaljeret kontrol over adgang og funktionsmåder for slutpunkter
- **[Centraliseret konfiguration og administration](#centralized-management)** med Microsoft 365 Defender portal og integration med Microsoft Endpoint Manager
- **[Beskyttelse til en række platforme](#cross-platform-support)**, herunder Windows, macOS-, iOS- og Android-enheder

De følgende afsnit indeholder flere oplysninger om disse funktioner. 

## <a name="next-generation-protection"></a>Næste generations beskyttelse

Næste generations beskyttelse omfatter robust antivirus- og antimalwarebeskyttelse. Med næste generations beskyttelse får du: 

- Behavior-based, heuristic, and real-time antivirus protection 
- Cloud-leveret beskyttelse, som omfatter øjeblikkelig registrering og blokering af nye og nye trusler 
- Dedikeret beskyttelse og produktopdateringer, herunder opdateringer relateret til Microsoft Defender Antivirus 

Du kan få mere at vide [under Oversigt over næste generations beskyttelse](next-generation-protection.md).

## <a name="manual-response-actions"></a>Manuelle svarhandlinger

Manuelle svarhandlinger er handlinger, som dit sikkerhedsteam kan udføre, når der registreres trusler på slutpunkter eller i filer. Defender til Slutpunkt omfatter visse [manuelle svarhandlinger](respond-machine-alerts.md) , der kan tages på en enhed, der registreres som potentielt kompromitteret eller har mistænkeligt indhold. Du kan også køre [svarhandlinger på filer](respond-file-alerts.md) , der registreres som trusler. Følgende tabel opsummerer de manuelle svarhandlinger, der er tilgængelige i Defender til Endpoint Plan 1. <br/><br/>

| Fil/enhed | Handling | Beskrivelse |
|:---|:---|:---|
| Enhed | Kør antivirusscanning | Starter en antivirusscanning. Hvis der registreres trusler på enheden, håndteres disse trusler ofte under en antivirusscanning. |
| Enhed | Isoler enhed | Afbryder forbindelsen mellem en enhed og organisationens netværk, mens forbindelsen til Defender til slutpunktet bevares. Denne handling gør det muligt at overvåge enheden og træffe yderligere foranstaltninger, hvis det er nødvendigt. |
| Filer | Stop og karantæne |Stopper processer fra at køre og sætte tilknyttede filer i karantæne. |
| Filer | Tilføje en indikator for at blokere eller tillade en fil | Bloker indikatorer forhindrer portable eksekverbare filer i at blive læst, skrevet eller udført på enheder. <p>Tillad indikatorer forhindrer filer i at blive blokeret eller afhjulpet. |

Du kan få mere at vide i følgende artikler:

- [Udføre svarhandlinger på enheder](respond-machine-alerts.md) 
- [Udføre svarhandlinger på filer](respond-file-alerts.md)

## <a name="attack-surface-reduction"></a>Reduktion af angrebsoverfladen

Din organisations angrebsoverflader er alle de steder, hvor du er sårbar over for cyberangreb. Med Defender for Endpoint Plan 1 kan du reducere dine angrebsoverflader ved at beskytte de enheder og programmer, som din organisation bruger. De reduktionsfunktioner til angrebsoverfladen, der er inkluderet i Defender for Endpoint Plan 1, er beskrevet i de følgende afsnit.

- [Regler for reduktion af angrebsoverflade](#attack-surface-reduction-rules)
- [Afhjælpning af ransomware](#ransomware-mitigation)
- [Enhedsstyring](#device-control)
- [Webbeskyttelse](#web-protection)
- [Netværksbeskyttelse](#web-protection)
- [Netværksfirewall](#network-firewall)
- [Programkontrolelement](#application-control)

Du kan få mere at vide om muligheder for reduktion af angrebsoverfladen i Defender til Slutpunkt under [Oversigt over reduktion af angrebsoverfladen](overview-attack-surface-reduction.md).

### <a name="attack-surface-reduction-rules"></a>Regler for reduktion af angrebsoverflade

Regler for reduktion af angrebsoverfladen målretter visse softwarefunktionsmåder, der betragtes som risikabelt. Disse funktionsmåder omfatter:

- Åbne eksekverbare filer og scripts, der forsøger at downloade eller køre andre filer
- Kører obskøne eller på anden måde mistænkelige scripts
- Starte funktionsmåder, som apps normalt ikke starter under normalt arbejde

Legitime forretningsprogrammer kan udvise sådanne softwarefunktionsmåder; Denne adfærd betragtes dog ofte som risikabel, fordi de ofte misbruges af hackere via malware. Regler for reduktion af angrebsoverfladen kan begrænse risikabel adfærd og hjælpe med at holde din organisation sikker.

Du kan få mere at vide [under Brug regler for reduktion af angrebsoverfladen til at forhindre malware inficeret](attack-surface-reduction.md).

### <a name="ransomware-mitigation"></a>Afhjælpning af ransomware

Med styret mappeadgang får du afhjælpning af ransomware. Kontrolleret mappeadgang tillader kun pålidelige apps at få adgang til beskyttede mapper på dine slutpunkter. Apps føjes til listen over de apps, der er tillid til, baseret på deres udvikling og omdømme. Dit sikkerhedsteam kan også tilføje eller fjerne apps fra listen over apps, der er tillid til.

Du kan få mere at vide [under Beskyt vigtige mapper med styret mappeadgang](controlled-folders.md).

### <a name="device-control"></a>Enhedsstyring

Nogle gange kan trusler mod organisationens enheder komme i form af filer på flytbare drev, f.eks. USB-drev. Defender til Slutpunkt omfatter funktioner, der kan hjælpe med at forhindre trusler fra uautoriserede eksterne enheder i at gå på kompromis med dine enheder. Du kan konfigurere Defender til slutpunkt til at blokere eller tillade flytbare enheder og filer på flytbare enheder. 

Du kan få mere at vide [under Styre USB-enheder og flytbare medier](control-usb-devices-using-intune.md).

### <a name="web-protection"></a>Webbeskyttelse

Med webbeskyttelse kan du beskytte din organisations enheder mod webtrusler og uønsket indhold. Webbeskyttelse omfatter beskyttelse mod webtrusler og filtrering af webindhold.

- [Webtrusselsbeskyttelse](web-threat-protection.md) forhindrer adgang til phishingwebsteder, malwarevektorer, udnyttelseswebsteder, upålidelige websteder eller websteder med dårligt ry og websteder, som du eksplicit blokerer.
- [Filtrering af webindhold](web-content-filtering.md) forhindrer adgang til bestemte websteder baseret på deres kategori. Kategorierne kan omfatte indhold beregnet til voksne, websteder med fritid, juridiske ansvarswebsteder og meget mere.

Du kan få mere at vide under [Webbeskyttelse](web-protection-overview.md).

### <a name="network-protection"></a>Netværksbeskyttelse

Med netværksbeskyttelse kan du forhindre din organisation i at få adgang til skadelige domæner, der kan hoste forsøg på phishing, udnyttelse og andet skadeligt indhold på internettet. 

Du kan få mere at vide [under Beskyt dit netværk](network-protection.md).

### <a name="network-firewall"></a>Netværksfirewall

Med beskyttelse af netværksfirewall kan du angive regler, der bestemmer, hvilken netværkstrafik der har tilladelse til at flyde til eller fra organisationens enheder. Med din netværksfirewall og avanceret sikkerhed, som du får med Defender til Slutpunkt, kan du:

- Reducer risikoen for sikkerhedstrusler på netværket
- Beskyt følsomme data og intellektuel ejendom
- Udvid din sikkerhedsinvestering

Du kan få mere at vide [Windows Defender Firewall med avanceret sikkerhed](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).

### <a name="application-control"></a>Programkontrolelement

Programkontrolelementet beskytter dine Windows slutpunkter ved kun at køre pålidelige programmer og kode i systemkernen (kerne). Dit sikkerhedsteam kan definere programkontrolregler, der tager højde for et programs attributter, f.eks. dets codesigningscertifikater, omdømme, lanceringsproces og meget mere. Programkontrolelement er tilgængeligt i Windows 10 eller nyere.

Du kan få mere at vide [under Programkontrol til Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control).

## <a name="centralized-management"></a>Centraliseret administration

Defender til Endpoint Plan 1 omfatter Microsoft 365 Defender-portalen, som gør det muligt for dit sikkerhedsteam at få vist aktuelle oplysninger om registrerede trusler, udføre relevante handlinger for at afhjælpe trusler og administrere din organisations indstillinger for trusselsbeskyttelse centralt.

Du kan få mere at vide [Microsoft 365 Defender oversigt over portal.](portal-overview.md)

### <a name="role-based-access-control"></a>Rollebaseret adgangskontrol

Ved hjælp af rollebaseret adgangskontrol (RBAC) kan sikkerhedsadministratoren oprette roller og grupper for at give den relevante adgang til Microsoft 365 Defender portalen ([https://security.microsoft.com](https://security.microsoft.com)). Med RBAC har du fuld kontrol over, hvem der kan få adgang til Defender til skyen, og hvad de kan se og gøre. 

Du kan få mere at vide [under Administrer portaladgang ved hjælp af rollebaseret adgangskontrol](rbac.md).

### <a name="reporting"></a>Rapportering

Portalen Microsoft 365 Defender () giver[https://security.microsoft.com](https://security.microsoft.com) nem adgang til oplysninger om registrerede trusler og handlinger for at håndtere disse trusler. 

- **Startsiden** indeholder kort, så du hurtigt kan se, hvilke brugere eller enheder der er i fare, hvor mange trusler der blev registreret, og hvilke beskeder/hændelser der blev oprettet.
- Afsnittet **Hændelser & en liste** over hændelser, der er oprettet som et resultat af udløste beskeder. Beskeder og hændelser genereres, efterhånden som trusler registreres på tværs af enheder.
- **Handlingscenter viser** afhjælpningshandlinger, der er blevet foretaget. Hvis en fil f.eks. sendes til karantæne, eller en URL-adresse er blokeret, vises hver handling i Handlingscenter under **fanen Oversigt** .
- Afsnittet **Rapporter** indeholder rapporter, der viser registrerede trusler og deres status. 

Du kan få mere at vide [under Introduktion til Microsoft Defender til Endpoint Plan 1](mde-plan1-getting-started.md).

### <a name="apis"></a>API'er

Med DEFENDER for Endpoint-API'er kan du automatisere arbejdsprocesser og integrere med organisationens brugerdefinerede løsninger. 

Du kan få mere at vide under [Defender til endpoint-API'er](management-apis.md). 

## <a name="cross-platform-support"></a>Understøttelse på tværs af platforme

De fleste organisationer bruger forskellige enheder og operativsystemer. Defender for Endpoint Plan 1 understøtter i øjeblikket følgende operativsystemer:

- Windows 7 (ESU påkrævet)
- Windows 8.1
- Windows 10, version 1709 eller nyere
- macOS: 11.5 (Big Sur), 10.15.7 (Catalina) eller 10.14.6 (Mojave)
- iOS
- Android OS

## <a name="next-steps"></a>Næste trin

- [Sammenlign Microsoft Defender for Endpoint Plan 1 med Plan 2](defender-endpoint-plan-1-2.md)
- [Konfigurere Defender til Endpoint Plan 1 og konfigurere den](mde-p1-setup-configuration.md)
- [Kom i gang med Defender for Endpoint Plan 1](mde-plan1-getting-started.md)
- [Administrer Defender for Endpoint Plan 1](mde-p1-maintenance-operations.md)
