---
title: Oversigt over Microsoft Defender for Endpoint Plan 1
description: Få en oversigt over Defender for Endpoint Plan 1. Få mere at vide om de funktioner og funktioner, der er inkluderet i dette abonnement til beskyttelse af slutpunkter.
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
ms.openlocfilehash: 774d54aee080fbe3d6f5576fb29c85d887717b70
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663506"
---
# <a name="overview-of-microsoft-defender-for-endpoint-plan-1"></a>Oversigt over Microsoft Defender for Endpoint Plan 1

**Gælder for**

- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Microsoft Defender for Endpoint er en sikkerhedsplatform til virksomhedsslutpunkter, der er udviklet til at hjælpe organisationer som dine med at forhindre, registrere, undersøge og reagere på avancerede trusler. Det glæder os at kunne meddele, at Defender for Endpoint nu er tilgængelig i to planer: 

- **Defender for Endpoint Plan 1**, der er beskrevet i denne artikel; Og 
- **[Defender for Endpoint Plan 2](microsoft-defender-endpoint.md)**, offentlig tilgængelig og tidligere kendt som [Defender for Endpoint](microsoft-defender-endpoint.md).

De grønne felter på følgende billede viser, hvad der er inkluderet i Defender for Endpoint Plan 1:

:::image type="content" source="../../media/mde-p1/mde-p1-overview-diagram.png" alt-text="Hvad er inculded med Defender for Endpoint Plan 1" lightbox="../../media/mde-p1/mde-p1-overview-diagram.png":::

Brug denne vejledning til at:

- [Få en oversigt over, hvad der er inkluderet i Defender for Endpoint Plan 1](#defender-for-endpoint-plan-1-capabilities)
- [Sammenlign Defender for Endpoint Plan 1 med Plan 2](defender-endpoint-plan-1-2.md)
- [Få mere at vide om, hvordan du konfigurerer Defender for Endpoint Plan 1](mde-p1-setup-configuration.md)
- [Kom i gang med at bruge Microsoft 365 Defender-portalen, hvor du kan få vist hændelser og beskeder, administrere enheder og bruge rapporter om registrerede trusler](mde-plan1-getting-started.md)
- [Få et overblik over vedligeholdelse og drift](mde-p1-maintenance-operations.md)

> [!TIP]
> [Få mere at vide om forskellene mellem Defender for Endpoint Plan 1 og Plan 2](defender-endpoint-plan-1-2.md).

## <a name="defender-for-endpoint-plan-1-capabilities"></a>Funktionerne Defender for Endpoint Plan 1

Defender for Endpoint Plan 1 indeholder følgende funktioner:

- **[Næste generations beskyttelse](#next-generation-protection)** , der omfatter brancheførende, robust beskyttelse modmalware og antivirus
- **[Manuelle svarhandlinger](#manual-response-actions)**, f.eks. afsendelse af en fil til karantæne, som dit sikkerhedsteam kan udføre på enheder eller filer, når der registreres trusler
- **[Reduktion af angrebsoverfladen](#attack-surface-reduction)** , der hærder enheder, forhindrer nuldagsangreb og giver detaljeret kontrol over adgang til slutpunkter og funktionsmåder
- **[Centraliseret konfiguration og administration](#centralized-management)** med Microsoft 365 Defender-portalen og integration med Microsoft Endpoint Manager
- **[Beskyttelse af en række platforme](#cross-platform-support)**, herunder Windows, macOS, iOS og Android-enheder

Følgende afsnit indeholder flere oplysninger om disse egenskaber. 

## <a name="next-generation-protection"></a>Næste generations beskyttelse

Næste generations beskyttelse omfatter robust antivirus- og antimalwarebeskyttelse. Med næste generations beskyttelse får du: 

- Adfærdsbaseret, heuristisk og antivirusbeskyttelse i realtid 
- Skybaseret beskyttelse, som omfatter registrering og blokering af nye og nye trusler næsten øjeblikkeligt 
- Dedikeret beskyttelse og produktopdateringer, herunder opdateringer relateret til Microsoft Defender Antivirus 

Du kan få mere at vide under [Oversigt over beskyttelse i næste generation](next-generation-protection.md).

## <a name="manual-response-actions"></a>Handlinger for manuelt svar

Manuelle svarhandlinger er handlinger, som dit sikkerhedsteam kan foretage, når der registreres trusler på slutpunkter eller i filer. Defender for Endpoint indeholder visse [manuelle svarhandlinger, der kan udføres på en enhed, der registreres](respond-machine-alerts.md) som potentielt kompromitteret eller har mistænkeligt indhold. Du kan også køre [svarhandlinger på filer](respond-file-alerts.md) , der registreres som trusler. I følgende tabel opsummeres de manuelle svarhandlinger, der er tilgængelige i Defender for Endpoint Plan 1. <br/><br/>

| Fil/enhed | Handling | Beskrivelse |
|:---|:---|:---|
| Enhed | Kør antivirusscanning | Starter en antivirusscanning. Hvis der registreres trusler på enheden, håndteres disse trusler ofte under en antivirusscanning. |
| Enhed | Isoler enhed | Afbryder forbindelsen mellem en enhed og organisationens netværk, samtidig med at forbindelsen til Defender for Endpoint bevares. Denne handling giver dig mulighed for at overvåge enheden og udføre yderligere handlinger, hvis det er nødvendigt. |
| Filer | Stop og sæt karantæne |Stopper processer i at køre og sætte tilknyttede filer i karantæne. |
| Filer | Tilføj en indikator for at blokere eller tillade en fil | Bloker indikatorer forhindrer, at bærbare eksekverbare filer læses, skrives eller udføres på enheder. <p>Tillad indikatorer forhindrer, at filer blokeres eller afhjælpes. |

Du kan få mere at vide i følgende artikler:

- [Udfør svarhandlinger på enheder](respond-machine-alerts.md) 
- [Udfør svarhandlinger på filer](respond-file-alerts.md)

## <a name="attack-surface-reduction"></a>Reduktion af angrebsoverfladen

Din organisations angrebsoverflader er alle de steder, hvor du er sårbar over for cyberangreb. Med Defender for Endpoint Plan 1 kan du reducere dine angrebsoverflader ved at beskytte de enheder og programmer, som din organisation bruger. De funktioner til reduktion af angrebsoverfladen, der er inkluderet i Defender for Endpoint Plan 1, er beskrevet i følgende afsnit.

- [Regler for reduktion af angrebsoverflade](#attack-surface-reduction-rules)
- [Ransomware-afhjælpning](#ransomware-mitigation)
- [Enhedsstyring](#device-control)
- [Webbeskyttelse](#web-protection)
- [Netværksbeskyttelse](#web-protection)
- [Netværksfirewall](#network-firewall)
- [Programkontrolelement](#application-control)

Hvis du vil vide mere om funktionerne til reduktion af angrebsoverfladen i Defender for Endpoint, skal du se [Oversigt over reduktion af angrebsoverfladen](overview-attack-surface-reduction.md).

### <a name="attack-surface-reduction-rules"></a>Regler for reduktion af angrebsoverflade

Regler for reduktion af angrebsoverfladen er målrettet visse softwarefunktioner, der anses for at være risikable. Sådanne funktionsmåder omfatter:

- Start af eksekverbare filer og scripts, der forsøger at downloade eller køre andre filer
- Kørsel af slørede eller på anden måde mistænkelige scripts
- Initierer funktionsmåder, som apps normalt ikke starter under normalt arbejde

Legitime virksomhedsprogrammer kan udvise en sådan softwarefunktionsmåde. Disse funktionsmåder anses dog ofte for at være risikable, fordi de ofte misbruges af hackere via malware. Regler for reduktion af angrebsoverfladen kan begrænse risikable funktionsmåder og hjælpe med at beskytte din organisation.

Du kan få mere at vide under [Brug regler for reduktion af angrebsoverfladen for at forhindre malware-infektion](attack-surface-reduction.md).

### <a name="ransomware-mitigation"></a>Ransomware-afhjælpning

Med kontrolleret mappeadgang får du ransomware-afhjælpning. Med kontrolleret mappeadgang er det kun apps, der er tillid til, der kan få adgang til beskyttede mapper på dine slutpunkter. Apps føjes til listen over apps, der er tillid til, baseret på deres udbredelse og omdømme. Dit team af sikkerhedshandlinger kan også tilføje eller fjerne apps fra listen over apps, der er tillid til.

Du kan få mere at vide under [Beskyt vigtige mapper med kontrolleret mappeadgang](controlled-folders.md).

### <a name="device-control"></a>Enhedsstyring

Nogle gange kommer trusler mod din organisations enheder i form af filer på flytbare drev, f.eks. USB-drev. Defender for Endpoint indeholder funktioner, der kan hjælpe med at forhindre trusler fra uautoriserede eksterne enheder i at kompromittere dine enheder. Du kan konfigurere Defender for Endpoint til at blokere eller tillade flytbare enheder og filer på flytbare enheder. 

Du kan få mere at vide under [Styr USB-enheder og flytbare medier](control-usb-devices-using-intune.md).

### <a name="web-protection"></a>Webbeskyttelse

Med webbeskyttelse kan du beskytte din organisations enheder mod webtrusler og uønsket indhold. Webbeskyttelse omfatter webtrusselbeskyttelse og filtrering af webindhold.

- [Beskyttelse af webtrusler](web-threat-protection.md) forhindrer adgang til phishing-websteder, malwarevektorer, udnyttelseswebsteder, websteder, der ikke er tillid til, eller websteder med lavt omdømme og websteder, som du udtrykkeligt blokerer.
- [Filtrering af webindhold](web-content-filtering.md) forhindrer adgang til visse websteder baseret på deres kategori. Kategorier kan omfatte indhold til voksne, fritidswebsteder, websteder med juridisk ansvar m.m.

Du kan få mere at vide under [webbeskyttelse](web-protection-overview.md).

### <a name="network-protection"></a>Netværksbeskyttelse

Med netværksbeskyttelse kan du forhindre din organisation i at få adgang til farlige domæner, der kan hoste phishing-svindel, udnyttelser og andet skadeligt indhold på internettet. 

Du kan få mere at vide under [Beskyt dit netværk](network-protection.md).

### <a name="network-firewall"></a>Netværksfirewall

Med beskyttelse af netværksfirewall kan du angive regler, der bestemmer, hvilken netværkstrafik der må overføres til eller fra organisationens enheder. Med din netværksfirewall og avanceret sikkerhed, som du får med Defender for Endpoint, kan du:

- Reducer risikoen for netværkssikkerhedstrusler
- Beskyttelse af følsomme data og immaterielle rettigheder
- Udvid din sikkerhedsinvestering

Du kan få mere at vide [under Windows Defender Firewall med avanceret sikkerhed](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security).

### <a name="application-control"></a>Programkontrolelement

Programkontrolelementet beskytter dine Windows slutpunkter ved kun at køre programmer, der er tillid til, og kode i systemkernen (kerne). Dit sikkerhedsteam kan definere regler for programkontrol, der tager højde for et programs attributter, f.eks. dets kodesigneringscertifikater, omdømme, startproces og meget mere. Programkontrolelementet er tilgængeligt i Windows 10 eller nyere.

Du kan få mere at vide under [Programkontrol for Windows](/windows/security/threat-protection/windows-defender-application-control/windows-defender-application-control).

## <a name="centralized-management"></a>Centraliseret administration

Defender for Endpoint Plan 1 indeholder Microsoft 365 Defender-portalen, som gør det muligt for dit sikkerhedsteam at få vist aktuelle oplysninger om registrerede trusler, udføre relevante handlinger for at afhjælpe trusler og centralt administrere organisationens indstillinger for trusselsbeskyttelse.

Du kan få mere at vide [under oversigt over Microsoft 365 Defender portal](portal-overview.md).

### <a name="role-based-access-control"></a>Rollebaseret adgangskontrol

Ved hjælp af rollebaseret adgangskontrol kan sikkerhedsadministratoren oprette roller og grupper for at give passende adgang til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). Med RBAC har du detaljeret kontrol over, hvem der kan få adgang til Defender for Cloud, og hvad de kan se og gøre. 

Du kan få mere at vide under [Administrer portaladgang ved hjælp af rollebaseret adgangskontrol](rbac.md).

### <a name="reporting"></a>Rapportering

Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) giver nem adgang til oplysninger om registrerede trusler og handlinger til at håndtere disse trusler. 

- **Startsiden** indeholder kort, som du hurtigt kan se, hvilke brugere eller enheder der er i fare, hvor mange trusler der blev registreret, og hvilke beskeder/hændelser der blev oprettet.
- Afsnittet **Hændelser & beskeder** viser alle hændelser, der blev oprettet som følge af udløste beskeder. Beskeder og hændelser genereres, når der registreres trusler på tværs af enheder.
- **Handlingscenteret** viser de afhjælpningshandlinger, der er udført. Hvis en fil f.eks. sendes til karantæne, eller en URL-adresse er blokeret, vises hver handling i Løsningscenter under fanen **Oversigt** .
- Afsnittet **Rapporter** indeholder rapporter, der viser registrerede trusler og deres status. 

Du kan få mere at vide under [Kom i gang med Microsoft Defender for Endpoint Plan 1](mde-plan1-getting-started.md).

### <a name="apis"></a>Api'er

Med Defender for Endpoint-API'er kan du automatisere arbejdsprocesser og integrere med din organisations brugerdefinerede løsninger. 

Du kan få mere at vide under [Defender for Endpoint API'er](management-apis.md). 

## <a name="cross-platform-support"></a>Understøttelse på tværs af platforme

De fleste organisationer bruger forskellige enheder og operativsystemer. Defender for Endpoint Plan 1 understøtter i øjeblikket følgende operativsystemer:

- Windows 7 (ESU påkrævet)
- Windows 8.1
- Windows 10, version 1709 eller nyere
- macOS: 11.5 (Big Sur), 10.15.7 (Catalina) eller 10.14.6 (Mojave)
- Ios
- Android OS

## <a name="next-steps"></a>Næste trin

- [Sammenlign Microsoft Defender for Endpoint plan 1 med plan 2](defender-endpoint-plan-1-2.md)
- [Konfigurer Defender for Endpoint Plan 1](mde-p1-setup-configuration.md)
- [Kom i gang med Defender for Endpoint Plan 1](mde-plan1-getting-started.md)
- [Administrer Defender for Endpoint Plan 1](mde-p1-maintenance-operations.md)
