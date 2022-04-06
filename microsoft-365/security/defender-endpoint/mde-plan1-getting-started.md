---
title: Kom i gang med Microsoft Defender for Endpoint Plan 1
description: Kom i gang med at bruge Defender for Endpoint Plan 1. Få mere at vide om, hvordan du bruger Defender for Cloud, administrerer beskeder og enheder og får vist rapporter.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/03/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.custom: intro-get-started
ms.openlocfilehash: 68315c6cf7947c2d42e58e34b4496e0ef790c8b0
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64665486"
---
# <a name="get-started-with-microsoft-defender-for-endpoint-plan-1"></a>Kom i gang med Microsoft Defender for Endpoint Plan 1

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

På Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) kan du få vist oplysninger om registrerede trusler, administrere dine beskeder og hændelser, udføre de nødvendige handlinger på registrerede trusler og administrere enheder. På Microsoft 365 Defender-portalen kan du komme i gang med at interagere med de trusselsbeskyttelsesfunktioner, du får med Defender for Endpoint Plan 1. I følgende afsnit beskrives det, hvordan du kommer i gang:

- [Portalen Microsoft 365 Defender](#the-microsoft-365-defender-portal)
- [Visning og administration af hændelser & beskeder](#view-and-manage-incidents--alerts)
- [Administration af enheder](#manage-devices)
- [Visning af rapporter](#view-reports)

## <a name="the-microsoft-365-defender-portal"></a>Portalen Microsoft 365 Defender

På Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) kan du få vist beskeder, administrere enheder og få vist rapporter. Når du logger på Microsoft 365 Defender-portalen, starter du med startsiden som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/m365-defender-portal.png" alt-text="Portalen for Microsoft 365 Defender" lightbox="../../media/mde-p1/m365-defender-portal.png":::

På startsiden får dit sikkerhedsteam et snapshot med en samlet visning af beskeder, enhedsstatus og registrerede trusler. Defender for Cloud er konfigureret, så dit sikkerhedsteam kan finde de oplysninger, de leder efter, hurtigt og nemt.

> [!NOTE]
> Vores eksempler, der vises i denne artikel, kan afvige fra det, du ser på din Microsoft 365 Defender-portal. Det, du ser på din portal, afhænger af dine licenser og tilladelser. Derudover kan dit sikkerhedsteam tilpasse organisationens portal ved at tilføje, fjerne og omarrangere kort.

### <a name="cards-highlight-key-information-and-include-recommendations"></a>Kort fremhæver vigtige oplysninger og indeholder anbefalinger

Startsiden indeholder kort som f.eks. kortet Aktive hændelser, der vises på følgende billede:

:::image type="content" source="../../media/mde-p1/active-incidents-card.png" alt-text="Kortet Aktive hændelser" lightbox="../../media/mde-p1/active-incidents-card.png":::

Kortet giver dig et hurtigt overblik over oplysninger sammen med et link eller en knap, som du kan vælge for at få vist mere detaljerede oplysninger. Med henvisning til vores eksempel på kortet Aktive hændelser kan vi vælge **Få vist alle hændelser** for at navigere til vores liste over hændelser.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Listen over hændelser" lightbox="../../media/mde-p1/incidents.png":::

### <a name="navigation-bar-makes-it-easy-to-find-alerts-the-action-center-and-more"></a>Navigationslinjen gør det nemt at finde beskeder, Løsningscenter m.m.

Navigationslinjen i venstre side af skærmen giver dig mulighed for nemt at flytte mellem hændelser, beskeder, Løsningscenter, rapporter og indstillinger. I følgende tabel beskrives navigationslinjen.<br/><br/>

| Navigationslinjeelement | Beskrivelse |
|:---|:---|
| **Home** | Navigerer til startsiden for [Microsoft 365 Defender-portalen](../defender/microsoft-365-security-center-mde.md). |
| **Hændelser & beskeder** | Udvides for at vise **hændelser** og **beskeder**. |
| **Hændelser & beskeder** >  **Hændelser** | Navigerer til listen **Hændelser** . Hændelser oprettes, når beskeder udløses og/eller trusler registreres. Listen **Hændelser** viser som standard data for de seneste 30 dage, hvor den seneste hændelse vises først. <br/><br/> Du kan få mere at vide under [Hændelser](view-incidents-queue.md). |
| **Hændelser & beskeder** >  **Indberetninger** | Navigerer til listen **Beskeder** (også kaldet **køen Beskeder**). Beskeder udløses, når der registreres en mistænkelig eller skadelig fil, proces eller funktionsmåde. Som standard viser listen **Beskeder** data for de seneste 30 dage, hvor den seneste besked vises først. <br/><br/> Du kan få mere at vide under [Beskeder](alerts-queue.md). |
| **Handlingscenter** | Navigerer til Løsningscenter, som sporer afhjælpningshandlinger og manuelle svarhandlinger. Handlingscenter sporer aktiviteter som disse: <br/>– Microsoft Defender Antivirus støder på en skadelig fil og derefter blokerer/fjerner filen. <br/>- Sikkerhedsteamet isolerer en enhed.<br/>– Defender for Endpoint registrerer og sætter en fil i karantæne. <br/><br/> Du kan få mere at vide i [Løsningscenter](auto-investigation-action-center.md). |
| **Secure Score** | Viser en repræsentation af din organisations sikkerhedsholdning sammen med en liste over forbedringshandlinger og målepunkter. <br/><br/> Du kan få mere at vide under [Microsoft Secure Score](../defender/microsoft-secure-score.md). |
| **Learning hub** | Navigerer til en liste over læringsforløb, som du kan få adgang til for at få mere at vide om Microsoft 365 sikkerhedsfunktioner.  |
| **Slutpunkter** >  **Søg** | Navigerer til en side, hvor du kan søge efter bestemte enheder efter enhedsnavn. På listen over resultater kan du hurtigt se detaljer, f.eks. risikoniveau og tilstand. |
|  **Slutpunkter** >  **Enhedslager** | Navigerer til listen over enheder, der er onboardet til Defender for Endpoint. Indeholder oplysninger om enheder, f.eks. deres eksponerings- og risikoniveauer. <br/><br/> Du kan få mere at vide under [Enhedsoversigt](machines-view-overview.md). |
|  **Slutpunkter** >  **Konfiguration & oprindelige planer** | Udvides for at vise **grundlæggende sikkerhedsdata** og **konfigurationsstyring**. |
|  **Slutpunkter** >  **Konfiguration & oprindelige planer** >  **Grundlæggende sikkerhedslinjer** | Grundlæggende sikkerhedsindstillinger er forudkonfigurerede politikker og grupper af indstillinger, der kan hjælpe dig med at anvende de anbefalede sikkerhedsindstillinger effektivt og effektivt. Grundlinjer omfatter indstillinger, der er baseret på bedste praksis i branchen. Du kan beholde standardindstillingerne eller tilpasse dine grundlinjer, så de passer til organisationens behov. <br/><br/> Du kan få mere at vide under [Brug grundlinjer for sikkerhed til at konfigurere Windows 10 enheder i Intune](/mem/intune/protect/security-baselines). |
|  **Slutpunkter** >  **Konfiguration & oprindelige planer** >  **Konfigurationsstyring** | Navigerer til siden **Administration af enhedskonfiguration** , hvor du kan få vist oplysninger om onboardede enheder og tage skridt til at onboarde flere enheder. |
| **Rapporter** | Navigerer til dine rapporter, f.eks. din [rapport om trusselsbeskyttelse](threat-protection-reports.md), [enhedens tilstand og overholdelse af angivne standarder](machine-reports.md) og din [webbeskyttelsesrapport](web-protection-overview.md). |
| **Sundhed** | Indeholder links til **Tjenestetilstand** og **Meddelelsescenter**.  |
| **Sundhed** >  **Tjenestetilstand** | Navigerer til siden Tjenestetilstand i Microsoft 365 Administration. På denne side kan du få vist tilstandsstatussen på tværs af alle de tjenester, der er tilgængelige med organisationens abonnementer.   |
| **Sundhed** >  **Meddelelsescenter** | Navigerer til Meddelelsescenter i Microsoft 365 Administration. Meddelelsescenteret indeholder oplysninger om planlagte ændringer. Hver meddelelse beskriver, hvad der kommer, hvordan det kan påvirke brugerne, og hvordan du administrerer ændringer. |  
| **Tilladelser & roller** | Giver dig mulighed for at give tilladelser til at bruge Microsoft 365 Defender-portalen. Tilladelser tildeles via roller i Azure Active Directory (Azure AD). Vælg en rolle, hvorefter der vises en pop op-rude. Pop op-vinduet indeholder et link til Azure AD, hvor du kan tilføje eller fjerne medlemmer i en rollegruppe. <br/><br/> Du kan få mere at vide under [Administrer portaladgang ved hjælp af rollebaseret adgangskontrol](rbac.md).  |
| **Indstillinger** | Navigerer til generelle indstillinger for Microsoft 365 Defender-portalen (angivet som **Security Center**) og Defender for Endpoint (angivet som **Slutpunkter**). <br/><br/> Du kan få mere at vide under [Indstillinger](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal). |
| **Flere ressourcer** | Viser en liste over flere portaler og centre, f.eks. Azure Active Directory og Microsoft 365 Overholdelsescenter. <br/><br/> Du kan få mere at vide under [Microsofts sikkerhedsportaler og administrationscentre](../defender/portals.md). |

> [!TIP]
> Du kan få mere at vide i [oversigten over Microsoft 365 Defender portal](../defender/microsoft-365-security-center-mde.md).

## <a name="view-and-manage-incidents--alerts"></a>Få vist og administrer hændelser & beskeder

Når du logger på Microsoft 365 Defender-portalen, skal du sørge for at få vist og administrere dine hændelser og beskeder. Start med listen **Over hændelser** . På følgende billede vises en liste over hændelser, herunder én med høj alvorsgrad og en anden med medium alvorsgrad.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Liste over hændelser":::

Vælg en hændelse for at få vist detaljer om hændelsen. Detaljer omfatter, hvilke beskeder der blev udløst, hvor mange enheder og brugere der blev påvirket, og andre oplysninger. På følgende billede kan du se et eksempel på oplysninger om hændelser.

:::image type="content" source="../../media/mde-p1/single-incident.png" alt-text="Detaljerne for en hændelse" lightbox="../../media/mde-p1/single-incident.png":::

Brug fanerne **Beskeder**, **Enheder** og **Brugere** til at få vist flere oplysninger, f.eks. de beskeder, der blev udløst, enheder, der blev berørt, og brugerkonti, der blev påvirket. Herfra kan du foretage manuelle svarhandlinger, f.eks. isolere en enhed, stoppe og quarantinere en fil osv.

> [!TIP]
> Hvis du vil vide mere om brug af **visningen Hændelse** , skal du se [Administrer hændelser](manage-incidents.md).

## <a name="manage-devices"></a>Administrer enheder

Hvis du vil have vist og administrere din organisations enheder, skal du vælge **Enhedslager** under **Slutpunkter** på navigationslinjen. Du får vist en liste over enheder, som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/device-inventory.png" alt-text="Enhedslager" lightbox="../../media/mde-p1/device-inventory.png":::

Listen indeholder de enheder, som der blev genereret beskeder for. De viste data er som standard de seneste 30 dage, hvor de nyeste elementer vises først. Vælg en enhed for at få vist flere oplysninger om den. Der åbnes en pop op-rude som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/device-inventory-selecteddevice.png" alt-text="Oplysninger om valgt enhed" lightbox="../../media/mde-p1/device-inventory-selecteddevice.png":::

I pop op-ruden vises detaljer, f.eks. eventuelle aktive beskeder for enheden, og den indeholder links, der kan udføres, f.eks. isolering af en enhed.

Hvis der er aktive beskeder på enheden, kan du få dem vist i pop op-ruden. Vælg en individuel besked for at få vist flere oplysninger om den. Eller du kan udføre en handling, f.eks **. Isolere enhed**, så du kan undersøge enheden yderligere, samtidig med at du minimerer risikoen for at inficere andre enheder.

> [!TIP]
> Du kan få mere at vide under [Undersøg enheder på listen Defender for Endpoint-enheder](investigate-machines.md).

## <a name="view-reports"></a>Få vist rapporter

I Defender for Endpoint Plan 1 er der flere tilgængelige rapporter på portalen Microsoft 365 Defender. Følg disse trin for at få adgang til dine rapporter:

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg **Rapporter** på navigationslinjen.

3. Vælg en rapport på listen. Du får vist følgende tre rapporter:

   - Rapport om trusselsbeskyttelse
   - Rapport over enhedens tilstand
   - Webbeskyttelsesrapport

> [!TIP]
> Du kan få flere oplysninger under [Trusselsbeskyttelsesrapporter](threat-protection-reports.md).

### <a name="threat-protection-report"></a>Rapport om trusselsbeskyttelse

Hvis du vil have adgang til din rapport om trusselsbeskyttelse, skal du på portalen Microsoft 365 Defender vælge **Rapporter** og derefter vælge **Trusselsbeskyttelse**. Rapporten Threat Protection viser tendenser, status, kategorier med mere. Visninger er arrangeret i to kolonner: **Tendenser for beskeder** og **Beskedstatus**, som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/threat-protection-report.png" alt-text="Rapport om trusselsbeskyttelse" lightbox="../../media/mde-p1/threat-protection-report.png":::

Rul ned for at se alle visningerne på hver liste.

- Visningerne i kolonnen **Vigtige tendenser** viser som standard data for de seneste 30 dage, men du kan angive en visning til at vise data for de sidste tre måneder, de seneste seks måneder eller et brugerdefineret tidsinterval (op til 180 dage).
- Visningerne i kolonnen **Status for besked** er et snapshot for den forrige arbejdsdag.

> [!TIP]
> Du kan få mere at vide under [Trusselsbeskyttelsesrapport i Defender for Endpoint](threat-protection-reports.md).

### <a name="device-health-report"></a>Rapport over enhedens tilstand

Hvis du vil have adgang til din rapport over enhedstilstand, skal du på portalen Microsoft 365 Defender vælge **Rapporter** og derefter vælge **Enhedstilstand**. Rapporten Enhedstilstand viser tilstandstilstand og antivirus på tværs af enheder i din organisation. På samme måde som [med rapporten Threat Protection](#threat-protection-report) er visninger arrangeret i to kolonner: **Enhedstendenser** og **Enhedsoversigt**, som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/device-health-report.png" alt-text="Rapport over enhedens tilstand" lightbox="../../media/mde-p1/device-health-report.png":::

Rul ned for at se alle visningerne på hver liste. Visningerne i kolonnen **Enhedstendenser** viser som standard data for de seneste 30 dage, men du kan ændre en visning for at få vist data for de sidste tre måneder, de seneste seks måneder eller et brugerdefineret tidsinterval (op til 180 dage). **Visningerne af enhedsoversigten** er snapshots for den forrige arbejdsdag.

> [!TIP]
> Du kan få mere at vide under [Enhedstilstand](machine-reports.md).

### <a name="web-protection-report"></a>Webbeskyttelsesrapport

Hvis du vil have adgang til din rapport over enhedstilstand, skal du vælge **Rapporter** på Microsoft 365 Defender portal og derefter vælge **Webbeskyttelse**. Rapporten webbeskyttelse viser registreringer over tid, f.eks. skadelige URL-adresser og forsøg på at få adgang til blokerede URL-adresser, som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/web-protection-report.png" alt-text="Webbeskyttelsesrapport" lightbox="../../media/mde-p1/web-protection-report.png":::

Rul ned for at se alle visningerne i webbeskyttelsesrapporten. Nogle visninger omfatter links, der giver dig mulighed for at få vist flere oplysninger, konfigurere dine trusselsbeskyttelsesfunktioner og endda administrere indikatorer, der fungerer som undtagelser i Defender for Endpoint.

> [!TIP]
> Du kan få mere at vide under [Webbeskyttelse](web-protection-overview.md).

## <a name="next-steps"></a>Næste trin

- [Administrer Microsoft Defender for Endpoint Plan 1](mde-p1-maintenance-operations.md)
- [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md)
