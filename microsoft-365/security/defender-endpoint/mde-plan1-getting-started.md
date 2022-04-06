---
title: Introduktion til Microsoft Defender for Endpoint Plan 1
description: Kom i gang med at bruge Defender til Endpoint Plan 1. Få mere at vide om, hvordan du bruger Defender til skyen, administrerer beskeder og enheder og får vist rapporter.
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
ms.openlocfilehash: c3e7f55a0dd8ad26f2b00b7e2d5840945e777a2a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64470323"
---
# <a name="get-started-with-microsoft-defender-for-endpoint-plan-1"></a>Introduktion til Microsoft Defender for Endpoint Plan 1

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) giver dig mulighed for at få vist oplysninger om registrerede trusler, administrere dine beskeder og hændelser, tage eventuelle nødvendige handlinger på registrerede trusler og administrere enheder. Portalen Microsoft 365 Defender er stedet, hvor du kan komme i gang med at arbejde med de egenskaber til trusselsbeskyttelse, du får med Defender for Endpoint Plan 1. I de følgende afsnit beskrives det, hvordan du kommer i gang:

- [Den Microsoft 365 Defender portal](#the-microsoft-365-defender-portal)
- [Få vist og administrere hændelser & beskeder](#view-and-manage-incidents--alerts)
- [Administration af enheder](#manage-devices)
- [Få vist rapporter](#view-reports)

## <a name="the-microsoft-365-defender-portal"></a>Den Microsoft 365 Defender portal

Den Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) er det sted, hvor du kan få vist beskeder, administrere enheder og få vist rapporter. Når du logger på Microsoft 365 Defender, starter du med startsiden som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/m365-defender-portal.png" alt-text="Portal for Microsoft 365 Defender" lightbox="../../media/mde-p1/m365-defender-portal.png":::

På startsiden får dit sikkerhedsteam en samlet oversigt over vigtige beskeder, enhedsstatus og trusler, der registreres. Defender til skyen er konfigureret, så dit sikkerhedsteam hurtigt og nemt kan finde de oplysninger, de leder efter.

> [!NOTE]
> Vores eksempler, der vises i denne artikel, kan være anderledes end det, du ser i Microsoft 365 Defender-portalen. Hvad du ser i din portal, afhænger af dine licenser og tilladelser. Derudover kan dit sikkerhedsteam tilpasse organisationens portal ved at tilføje, fjerne og omarrangere kort.

### <a name="cards-highlight-key-information-and-include-recommendations"></a>Kort fremhæver vigtige oplysninger og medtager anbefalinger

Startsiden indeholder kort, f.eks. kortet Aktive hændelser, der er vist på følgende billede:

:::image type="content" source="../../media/mde-p1/active-incidents-card.png" alt-text="Kortet Aktive hændelser" lightbox="../../media/mde-p1/active-incidents-card.png":::

Kortet giver dig et hurtigt overblik over oplysninger sammen med et link eller en knap, som du kan vælge for at få vist mere detaljerede oplysninger. Med henvisning til vores eksempel på kortet Aktive hændelser kan vi vælge Se alle **hændelser** for at navigere til vores liste over hændelser.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Listen over hændelser" lightbox="../../media/mde-p1/incidents.png":::

### <a name="navigation-bar-makes-it-easy-to-find-alerts-the-action-center-and-more"></a>Navigationslinjen gør det nemt at finde beskeder, handlingscenter og meget mere

Navigationslinjen i venstre side af skærmen giver dig mulighed for nemt at skifte mellem hændelser, beskeder, handlingscenter, rapporter og indstillinger. I følgende tabel beskrives navigationslinjen.<br/><br/>

| Elementet Navigationslinje | Beskrivelse |
|:---|:---|
| **Home** | Navigerer til startsiden for [Microsoft 365 Defender-portalen](../defender/microsoft-365-security-center-mde.md). |
| **Hændelser & beskeder** | Udvides for at **vise hændelser** **og beskeder**. |
| **Hændelser & beskeder** >  **Hændelser** | Navigerer til **listen Hændelser** . Hændelser oprettes, når der udløses beskeder, og/eller der registreres trusler. Listen hændelser viser **som standard** data for de seneste 30 dage med den seneste hændelse angivet først. <br/><br/> Du kan få mere at vide [under Hændelser](view-incidents-queue.md). |
| **Hændelser & beskeder** >  **Beskeder** | Navigerer til **listen Vigtige** beskeder (også kaldet **køen Vigtige beskeder**). Beskeder udløses, når der registreres en mistænkelig eller skadelig fil, proces eller funktionsmåde. Listen Beskeder viser som **standard** data for de seneste 30 dage med den seneste besked angivet først. <br/><br/> Du kan få mere at vide [under Beskeder](alerts-queue.md). |
| **Handlingscenter** | Navigerer til Handlingscenter, som registrerer afhjælpnings- og manuelle svarhandlinger. Handlingscenter registrerer aktiviteter som disse: <br/>- Microsoft Defender Antivirus en skadelig fil og blokerer/fjerner derefter den pågældende fil. <br/>Sikkerhedsteamet isolerer en enhed.<br/>- Defender til Slutpunkt registrerer og sætter en fil i karantæne. <br/><br/> Du kan få mere at vide i [Handlingscenter](auto-investigation-action-center.md). |
| **Sikker score** | Viser en repræsentation af din organisations sikkerhedsindstillinger sammen med en liste over forbedringshandlinger og målepunkter. <br/><br/> Du kan få mere at vide [under Microsoft Secure Score](../defender/microsoft-secure-score.md). |
| **Learning hub** | Navigerer til en liste over læringsstier, som du kan få mere at vide om Microsoft 365 om sikkerhedsegenskaber.  |
| **Slutpunkter** >  **Søg** | Navigerer til en side, hvor du kan søge efter bestemte enheder efter enhedsnavn. På listen over resultater kan du få vist detaljer, f.eks. risikoniveau og tilstand, med et hurtigt øjekast. |
|  **Slutpunkter** >  **Lagerenhed** | Navigerer til din liste over enheder, der er onboardet til Defender til Slutpunkt. Indeholder oplysninger om enheder, f.eks. deres eksponering og risikoniveauer. <br/><br/> Du kan få mere at vide under [Lager over enheder](machines-view-overview.md). |
|  **Slutpunkter** >  **Konfiguration & oprindelige planer** | Udvides for at vise **Sikkerheds oprindelige planer** og **Konfigurationsstyring**. |
|  **Slutpunkter** >  **Konfiguration & oprindelige planer** >  **Grundlinjer for sikkerhed** | Grundlinjer for sikkerhed er forudkonfigurerede politikker og grupper af indstillinger, der kan hjælpe dig med at anvende anbefalede sikkerhedsindstillinger effektivt. Oprindelige planer omfatter indstillinger, der er baseret på bedste praksis for branchen. Du kan beholde standardindstillingerne eller tilpasse dine oprindelige planer, så de passer til organisationens behov. <br/><br/> Du kan få mere at vide [under Brug sikkerheds oprindelige planer til at konfigurere Windows 10 enheder i Intune](/mem/intune/protect/security-baselines). |
|  **Slutpunkter** >  **Konfiguration & oprindelige planer** >  **Konfigurationsstyring** | Navigerer til siden **Enhedskonfigurationsstyring** , hvor du kan få vist oplysninger om onboardede enheder og tage skridt til at onboarde flere enheder. |
| **Rapporter** | Navigerer til dine rapporter, f.eks. rapporten [om trusselsbeskyttelse](threat-protection-reports.md), enhedens [tilstand og](machine-reports.md) overholdelsesrapporten og din [webbeskyttelsesrapport](web-protection-overview.md). |
| **Tilstand** | Indeholder links til **Tjenestetilstand** og **Meddelelsescenter**.  |
| **Tilstand** >  **Tjenestetilstand** | Navigerer til Tjenestetilstand side i Microsoft 365 Administration. På denne side kan du få vist tilstandsstatussen på tværs af alle de tjenester, der er tilgængelige med organisationens abonnementer.   |
| **Tilstand** >  **Meddelelsescenter** | Navigerer til Meddelelsescenter i Microsoft 365 Administration. Meddelelsescenter indeholder oplysninger om planlagte ændringer. Hver meddelelse beskriver, hvad der kommer, hvordan det kan påvirke brugere, og hvordan du administrerer ændringer. |  
| **Tilladelser & roller** | Giver dig mulighed for at give tilladelse til at bruge Microsoft 365 Defender portal. Tilladelser tildeles gennem roller i Azure Active Directory (Azure AD). Vælg en rolle, så vises en pop op-rude. Pop op-mailen indeholder et link til Azure AD, hvor du kan tilføje eller fjerne medlemmer i en rollegruppe. <br/><br/> Du kan få mere at vide [under Administrer portaladgang ved hjælp af rollebaseret adgangskontrol](rbac.md).  |
| **Indstillinger** | Navigerer til generelle indstillinger for din Microsoft 365 Defender-portal (angivet som **Sikkerhedscenter**) og Defender til slutpunkt (angivet **som slutpunkter**). <br/><br/> Du kan få mere at vide [under Indstillinger](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal). |
| **Flere ressourcer** | Viser en liste over flere portaler og centre, f.eks. Azure Active Directory og Microsoft 365 Overholdelsescenter. <br/><br/> Du kan få mere at vide [under Microsoft-sikkerhedsportaler og administrationscentre](../defender/portals.md). |

> [!TIP]
> Du kan få mere at vide [Microsoft 365 Defender oversigten over portalen](../defender/microsoft-365-security-center-mde.md).

## <a name="view-and-manage-incidents--alerts"></a>Få vist og administrer hændelser & beskeder

Når du logger på Microsoft 365 Defender, skal du sørge for at få vist og administrere dine hændelser og beskeder. Start med listen **Hændelser** . Følgende billede viser en liste over hændelser, herunder en med høj alvorlighed og en anden med mellem alvorlighed.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Liste over hændelser":::

Vælg en hændelse for at få vist detaljer om hændelsen. Detaljer omfatter, hvilke beskeder der blev udløst, hvor mange enheder og brugere, der blev påvirket, samt andre detaljer. Følgende billede viser et eksempel på oplysninger om hændelsen.

:::image type="content" source="../../media/mde-p1/single-incident.png" alt-text="Oplysninger om en hændelse" lightbox="../../media/mde-p1/single-incident.png":::

Brug **fanerne Beskeder****, Enheder** og Brugere  til at få vist flere oplysninger, f.eks. de beskeder, der blev udløst, enheder, der blev påvirket, og brugerkonti, der blev påvirket. Derfra kan du udføre manuelle svarhandlinger, f.eks. isolere en enhed, stoppe og kvarte en fil osv.

> [!TIP]
> Du kan få mere at vide om **at bruge** hændelsesvisningen [under Administrer hændelser](manage-incidents.md).

## <a name="manage-devices"></a>Administrer enheder

Hvis du vil have vist og administrere din organisations enheder, skal du i **navigationslinjen under Slutpunkter** vælge Lager **over enheder**. Du får vist en liste over enheder som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/device-inventory.png" alt-text="Lagerenhed" lightbox="../../media/mde-p1/device-inventory.png":::

Listen indeholder enheder, som der blev oprettet beskeder for. Som standard er de viste data for de seneste 30 dage med de seneste elementer angivet først. Vælg en enhed for at få vist flere oplysninger om den. Der åbnes en rude med pop op-vindue som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/device-inventory-selecteddevice.png" alt-text="Oplysninger om valgt enhed" lightbox="../../media/mde-p1/device-inventory-selecteddevice.png":::

Pop op-ruden viser detaljer, f.eks. alle aktive beskeder for enheden, og indeholder links til at gøre noget, f.eks. at isolere en enhed.

Hvis der er aktive beskeder på enheden, kan du få dem vist i pop op-ruden. Vælg en individuel besked for at få vist flere oplysninger om den. Eller, f.eks. **Isoler** enhed, så du kan undersøge enheden yderligere, mens risikoen for at inficere andre enheder minimeres.

> [!TIP]
> Du kan få mere at vide [under Undersøg enheder på listen Defender for Endpoint-enheder](investigate-machines.md).

## <a name="view-reports"></a>Vis rapporter

I Defender for Endpoint Plan 1 er flere rapporter tilgængelige på Microsoft 365 Defender-portalen. Hvis du vil have adgang til dine rapporter, skal du følge disse trin:

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Vælg Rapporter i **navigationslinjen**.

3. Vælg en rapport på listen. Du får vist følgende tre rapporter:

   - Rapport om trusselsbeskyttelse
   - Tilstandsrapport for enhed
   - Rapport over webbeskyttelse

> [!TIP]
> Du kan få mere at vide [under Rapporter om trusselsbeskyttelse](threat-protection-reports.md).

### <a name="threat-protection-report"></a>Rapport om trusselsbeskyttelse

For at få adgang til rapporten om trusselsbeskyttelse skal Microsoft 365 Defender på portalen **Rapporter** og derefter vælge **Trusselsbeskyttelse**. Rapporten Threat Protection viser beskedtendenser, status, kategorier og meget mere. Visninger er arrangeret i to kolonner: **Påmindelsestendenser** **og beskedstatus** som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/threat-protection-report.png" alt-text="Rapport om trusselsbeskyttelse" lightbox="../../media/mde-p1/threat-protection-report.png":::

Rul ned for at se alle visningerne på hver liste.

- Som standard viser visningerne i kolonnen  Påmindelsestendenser data for de seneste 30 dage, men du kan angive en visning for at få vist data for de sidste tre måneder, sidste seks måneder eller et brugerdefineret tidsinterval (op til 180 dage).
- Visningerne i kolonnen **Beskedstatus** er et øjebliksbillede af den forrige arbejdsdag.

> [!TIP]
> Du kan få mere at vide [under Rapport om trusselsbeskyttelse i Defender til Slutpunkt](threat-protection-reports.md).

### <a name="device-health-report"></a>Tilstandsrapport for enhed

Hvis du vil have adgang til din enhedstilstandsrapport, Microsoft 365 Defender du vælge **Rapporter** i portalen Enhedstilstand og derefter vælge **Enhedstilstand**. Rapporten Enhedstilstand viser tilstand og antivirus på tværs af enheder i organisationen. Ligesom rapporten [Trusselsbeskyttelse arrangeres](#threat-protection-report) visninger i to kolonner: **Enhedstendenser** **og** Enhedsoversigt, som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/device-health-report.png" alt-text="Tilstandsrapport for enhed" lightbox="../../media/mde-p1/device-health-report.png":::

Rul ned for at se alle visningerne på hver liste. Som standard viser visningerne i kolonnen  Enhedstendenser data for de seneste 30 dage, men du kan ændre en visning for at få vist data for de sidste tre måneder, sidste seks måneder eller et brugerdefineret tidsinterval (op til 180 dage). **Oversigtsvisningerne** af Enheden er øjebliksbilleder for den forrige arbejdsdag.

> [!TIP]
> Du kan få mere at vide under [Enhedstilstand](machine-reports.md).

### <a name="web-protection-report"></a>Rapport over webbeskyttelse

For at få adgang til din Enhedstilstandsrapport skal Microsoft 365 Defender på portalen **Rapporter** og derefter vælge **Webbeskyttelse**. Rapporten webbeskyttelse viser registreringer over tid, f.eks. skadelige URL-adresser og forsøg på at få adgang til blokerede URL-adresser, som vist på følgende billede:

:::image type="content" source="../../media/mde-p1/web-protection-report.png" alt-text="Rapport over webbeskyttelse" lightbox="../../media/mde-p1/web-protection-report.png":::

Rul ned for at se alle visningerne i webbeskyttelsesrapporten. Nogle visninger indeholder links, der giver dig mulighed for at få vist flere detaljer, konfigurere dine funktioner til trusselsbeskyttelse og endda administrere indikatorer, der fungerer som undtagelser i Defender til Slutpunkt.

> [!TIP]
> Du kan få mere at vide under [Webbeskyttelse](web-protection-overview.md).

## <a name="next-steps"></a>Næste trin

- [Administrer Microsoft Defender for Endpoint Plan 1](mde-p1-maintenance-operations.md)
- [Microsoft Defender for Endpoint](microsoft-defender-endpoint.md)
