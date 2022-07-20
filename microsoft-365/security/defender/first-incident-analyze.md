---
title: Trin 1. Triage og analysér din første hændelse
description: Sådan triage og begynde analysen af din første hændelse i Microsoft 365 Defender.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, maskiner, enheder, brugere, identitet, identitet, postkasse, mail, 365, microsoft, m365, svar på hændelser, cyberangreb
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-firstincident
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 596966c7c1975ebb8f20b306be5e4ab0a34bd99e
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66893633"
---
# <a name="step-1-triage-and-analyze-your-first-incident"></a>Trin 1. Triage og analysér din første hændelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Når du bruger lidt tid på at etablere, implementere og vedligeholde sikkerhedsforanstaltninger i henhold til organisationens standarder, kan du konfigurere sikkerhedsløsninger, der kan hjælpe dig med hurtigt at identificere sikkerhedsrisici og trusler. Microsoft 365 Defender giver dig mulighed for at registrere, triage og undersøge hændelser via oplevelsen med en enkelt rude af glas, hvor du kan finde de oplysninger, du har brug for til at træffe rettidige beslutninger.

Når en sikkerhedshændelse er registreret, Microsoft 365 Defender præsenterer de oplysninger, du skal bruge for at prioritere eller prioritere en hændelse eller hændelser i forhold til andre. Når prioriteringen er blevet bestemt, kan analytikere derefter fokusere deres energi på undersøgelsessager, der er tildelt dem.

## <a name="detection-by-microsoft-365-defender"></a>Registrering af Microsoft 365 Defender

Microsoft 365 Defender modtager beskeder og hændelser fra flere Microsoft-sikkerhedsplatforme som registreringskilder for at oprette et holistisk billede og en kontekst med skadelig aktivitet. De mulige registreringskilder er:

- [Microsoft Defender for Endpoint](../defender-endpoint/microsoft-defender-endpoint.md) er en EDR (endpoint detection and response solution), der bruger Microsoft Defender antivirus og cloudaktiveret avanceret trusselsbeskyttelse ved hjælp af Microsoft Security Graph. Defender for Endpoint er en samlet platform til forebyggende beskyttelse, registrering efter sikkerhedsbrud, automatiseret undersøgelse og svar. Den beskytter slutpunkter mod cybertrusler, registrerer avancerede angreb og brud på datasikkerheden, automatiserer sikkerhedshændelser og forbedrer sikkerhedsholdning.
- [Microsoft Defender for Identity](/defender-for-identity/what-is) er en cloudbaseret sikkerhedsløsning, der bruger dine AD DS-signaler (Active Directory i det lokale miljø Domain Services) til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og skadelige insiderhandlinger, der er rettet mod din organisation.
- [Microsoft Defender for Cloud Apps](/cloud-app-security/) fungerer som portvogter for at formidle adgang i realtid mellem dine virksomhedsbrugere og de cloudressourcer, de bruger, uanset hvor dine brugere er placeret, og uanset hvilken enhed de bruger.
- [Microsoft Defender for Office 365](../office-365-security/overview.md) beskytter din organisation mod skadelige trusler i mails, links (URL-adresser) og samarbejdsværktøjer.
- [Azure Security Center](/azure/security-center/security-center-introduction) er et samlet system til administration af infrastruktursikkerhed, der styrker dine datacentres sikkerhedsholdning og giver avanceret trusselsbeskyttelse på tværs af dine hybride arbejdsbelastninger i cloudmiljøet og i det lokale miljø.


I Microsoft 365 Defender [identificeres hændelser](incidents-overview.md) ved at korrelere beskeder fra disse forskellige registreringskilder. I stedet for at bruge ressourcer på at samle eller skelne mellem flere beskeder i deres respektive hændelser kan du starte med hændelseskøen i Microsoft 365 Defender med det samme. Denne fremgangsmåde giver dig mulighed for at triage hændelser på en effektiv måde på tværs af slutpunkter, identiteter, mail og programmer og reducere skaden fra et angreb.

## <a name="triage-your-incidents"></a>Triage dine hændelser

Svar på hændelser i Microsoft 365 Defender starter, når du har prioriteret listen over hændelser ved hjælp af organisationens anbefalede prioriteringsmetode. At triage betyder at tildele en grad af vigtighed eller uopsættelighed til hændelser, som derefter bestemmer den rækkefølge, som de vil blive undersøgt i.

En nyttig eksempelvejledning til bestemmelse af, hvilken hændelse der skal prioriteres i Microsoft 365 Defender kan opsummeres med formlen: *Alvorsgrad + Virkning = Prioritet*.

- **Alvorsgrad** er det niveau, der er angivet af Microsoft 365 Defender og dets integrerede sikkerhedskomponenter.
- **Indvirkning** bestemmes af organisationen og omfatter generelt, men ikke begrænset til, et tærskelantal påvirkede brugere, enheder, berørte tjenester (eller en kombination heraf) og endda beskedtype.

Analytikere starter derefter undersøgelser baseret på de **prioritetskriterier** , der er angivet af organisationen.

Prioriteringen af hændelser kan variere afhængigt af organisationen. NIST anbefaler også, at man overvejer den funktionelle og oplysende virkning af hændelsen og gendannelsen.

En tilgang til triage er beskrevet nedenfor:

1. Gå til [hændelsessiden](incidents-overview.md) for at starte triage. Her kan du se en liste over hændelser, der påvirker din organisation. Som standard er de arrangeret fra den seneste til den ældste hændelse. Herfra kan du også se forskellige kolonner for hver hændelse, der bl.a. viser deres alvorsgrad, kategori, antallet af aktive beskeder og påvirkede enheder. Du kan tilpasse sættet af kolonner og sortere hændelseskøen efter nogle af disse kolonner ved at vælge kolonnenavnet. Du kan også filtrere hændelseskøen efter dine behov. Du kan se en komplet liste over tilgængelige filtre under [Prioriter hændelser](incident-queue.md#available-filters).

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-queue.png" alt-text="Hændelserne i Microsoft 365-sikkerhedsportalen" lightbox="../../media/first-incident-analyze/first-incident-analyze-queue.png":::

    Et eksempel på, hvordan du kan udføre triage for dette sæt hændelser, er at prioritere hændelser, der påvirkede flere brugere og enheder. I dette eksempel kan du prioritere hændelses-id 6769, fordi det påvirkede det største antal enheder: syv enheder, seks brugere og to postkasser. Desuden ser hændelsen ud til at indeholde beskeder fra Microsoft Defender for Identity, som angiver en identitetsbaseret advarsel og mulig tyveri af legitimationsoplysninger.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-high-impact.png" alt-text="Siden Hændelser**, der viser et eksempel på en hændelse med stor indvirkning på Microsoft 365-sikkerhedsportalen" lightbox="../../media/first-incident-analyze/first-incident-analyze-high-impact.png":::

2. Vælg cirklen ud for navnet på hændelsen for at gennemse detaljerne. Der vises en siderude i højre side, som indeholder yderligere oplysninger, der kan hjælpe dig med at triage yderligere.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png" alt-text="Siden Hændelser, der viser et eksempel på en rude på hændelsessiden på Microsoft 365-sikkerhedsportalen" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png":::

   Hvis du f.eks. ser på, hvilke [MITRE ATT&CK-taktik](https://attack.mitre.org/) , som hackeren brugte baseret på kategorierne for hændelsen, kan du prioritere denne hændelse, fordi hackeren brugte stjålne legitimationsoplysninger, etablerede kommando og kontrol, udførte tværgående bevægelse og eksfiltrerede nogle data. Disse handlinger tyder på, at hackeren allerede er gået dybt ind i netværket og muligvis stjålet fortrolige oplysninger.

   Hvis din organisation har implementeret Nul tillid struktur, bør du desuden overveje adgang til legitimationsoplysninger som en vigtig sikkerhedsovertrædelse, der er værd at prioritere.

   Når du ruller ned i sideruden, kan du se de specifikke påvirkede enheder, f.eks. brugere, enheder og postkasser. Du kan kontrollere eksponeringsniveauet for hver enhed og ejerne af berørte postkasser.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png" alt-text="Oplysninger om hændelsessidens rude" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png":::

3. Længere nede i sideruden kan du finde de tilknyttede beskeder. Microsoft 365 Defender har allerede udført korrelationen mellem disse beskeder i en enkelt hændelse, hvilket sparer dig tid og ressourcer, der er bedre brugt på at afhjælpe angrebet. Beskeder er mistænkelige og derfor muligvis skadelige systemhændelser, der antyder tilstedeværelsen af en hacker på et netværk.

   I dette eksempel blev 87 individuelle beskeder bestemt til at være en del af én sikkerhedshændelse. Du kan få vist alle beskederne for at få et hurtigt overblik over, hvordan angrebet udspillede sig.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png" alt-text="Beskederne i en rude på hændelsessiden på Microsoft 365-sikkerhedsportalen" lightbox="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png":::

## <a name="analyze-your-first-incident"></a>Analysér din første hændelse

Det er lige så vigtigt at forstå den kontekst, der omgiver beskeder. Ofte er en besked ikke en enkelt uafhængig hændelse. Der er en kæde af processer, der er oprettet, kommandoer og handlinger, som muligvis ikke er opstået på samme tid. Derfor skal en analytiker søge efter den første og sidste aktivitet for den mistænkelige enhed på enhedens tidslinjer for at forstå konteksten for beskederne.

Der er flere måder at læse og analysere data på ved hjælp af Microsoft 365 Defender men det endelige mål for analytikere er at reagere på hændelser så hurtigt som muligt. Selvom Microsoft 365 Defender kan reducere [middeltiden til afhjælpning (MTTR)](https://www.microsoft.com/security/blog/2020/05/04/lessons-learned-microsoft-soc-part-3c/) markant via den brancheførende [automatiserede undersøgelses- og svarfunktion](m365d-autoir.md), er der altid tilfælde, der kræver manuel analyse.

Her er et eksempel:

1. Når prioriteringen er fastlagt, starter en analytiker en dybdegående analyse ved at vælge hændelsesnavnet. På denne side vises **oversigt over hændelser** , hvor data vises under faner for at hjælpe med analysen. Under fanen **Beskeder** vises beskedtyperne. Analytikere kan klikke på hver besked for at analysere ned i den respektive registreringskilde.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png" alt-text="Fanen Oversigt for en hændelse" lightbox="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png":::

    Du kan finde en hurtig vejledning til, hvilket domæne hver registreringskilde dækker, i afsnittet [Registrer](#detection-by-microsoft-365-defender) i denne artikel.

2. Fra fanen **Beskeder** kan du pivotere til registreringskilden for at foretage en mere dybdegående undersøgelse og analyse. Hvis du f.eks. vælger Malware-registrering med Microsoft Defender for Cloud Apps som registreringskilden, føres analytikeren til den tilsvarende beskedside.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-select-alert.png" alt-text="Siden Hændelser, der viser et eksempel på valg af en besked om en hændelse." lightbox="../../media/first-incident-analyze/first-incident-analyze-select-alert.png":::

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png" alt-text="En tilsvarende side i Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png":::

3. Hvis du vil undersøge vores eksempel yderligere, skal du rulle ned til bunden af siden for at få vist de **berørte brugere**. Hvis du vil se aktiviteten og konteksten omkring registrering af malware, skal du vælge Annette Hill's brugerside.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-page.png" alt-text="En brugerside" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-page.png":::

4. På brugersiden vises hændelser kronologisk, startende med en *risikobehæftet logon fra en IP-adressebesked på et TOR-netværk* . Mens mistænkeligheden af en aktivitet afhænger af arten af, hvordan en organisation udfører sin virksomhed, i de fleste tilfælde brugen af Onion Router (TOR), et netværk, der giver brugerne mulighed for at gennemse internettet anonymt, i et virksomhedsmiljø kan betragtes som meget usandsynligt og unødvendigt for regelmæssige online-operationer.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png" alt-text="Den kronologiske liste over hændelser for en bruger" lightbox="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png":::

5. Hver besked kan vælges for at få flere oplysninger om aktiviteten. Hvis du f.eks. vælger **Aktivitet fra en besked om IP-adresse for tor** , kommer du til beskedens egen side. Annette er administrator af Office 365, hvilket angiver øgede rettigheder, og at kildehændelsen kan have ført til adgang til fortrolige oplysninger.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" alt-text="Beskedoplysningerne for Microsoft Defender for Cloud Apps" lightbox="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" :::

6. Når du vælger andre beskeder, kan du få et komplet billede af angrebet.

## <a name="next-step"></a>Næste trin

:::image type="content" source="../../media/first-incident-overview/first-incident-path-step2.png" alt-text="Indstillingen Remediate på siden Besvar din første hændelse" lightbox="../../media/first-incident-overview/first-incident-path-step2.png":::

Få mere at vide om, hvordan [du afhjælper hændelser](first-incident-remediate.md).

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Undersøg hændelser](investigate-incidents.md)
- [Administrer hændelser](manage-incidents.md)
