---
title: Trin 1. Undersøge og analysere din første hændelse
description: Sådan triages og startes analysen af din første hændelse Microsoft 365 Defender.
keywords: hændelser, beskeder, undersøge, korrelation, angreb, maskiner, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365, hændelsesrespons, cyberangreb
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
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: dd39ace81a6128b9edcc33581c8386c06adf0d5f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63597919"
---
# <a name="step-1-triage-and-analyze-your-first-incident"></a>Trin 1. Undersøge og analysere din første hændelse

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**
- Microsoft 365 Defender

Når du bruger noget tid på at etablere, implementere og vedligeholde sikkerhedsforanstaltninger i overensstemmelse med organisationens standarder, kan du oprette sikkerhedsløsninger, der kan hjælpe dig med hurtigt at identificere sikkerhedsrisici og trusler. Microsoft 365 Defender gør det muligt at registrere, undersøge og undersøge hændelser via dens oplevelse med enkeltglasglas, hvor du kan finde de oplysninger, du skal bruge til at træffe rettidige beslutninger.

Når en sikkerhedshændelse registreres, viser Microsoft 365 Defender oplysninger, som du skal bruge for at triage eller prioritere en hændelse eller hændelser frem for andre. Efter fastlæggelse af prioritering kan analytikere derefter fokusere på at undersøge de sager, der er tildelt dem.

## <a name="detection-by-microsoft-365-defender"></a>Registrering efter Microsoft 365 Defender

Microsoft 365 Defender modtager beskeder og begivenheder fra flere microsoft-sikkerhedsplatforme som registreringskilder for at skabe et billed og kontekst til ondsindet aktivitet. Disse er de mulige registreringskilder:

- [Microsoft Defender til slutpunkt](../defender-endpoint/microsoft-defender-endpoint.md) er en slutpunktsregistrering og -svar-løsning (Slutpunktsregistrering og -svar), der bruger Microsoft Defender antivirus og skyaktiveret avanceret trusselsbeskyttelse ved hjælp af Microsoft Security Graph. Defender til Slutpunkt er en samlet platform til forebyggelse af beskyttelse, registrering efter brud, automatisk undersøgelse og svar. Den beskytter slutpunkter mod cybertrusler, registrerer avancerede angreb og databrister, automatiserer sikkerhedshændelser og forbedrer sikkerheden.
- [Microsoft Defender for Identity](/defender-for-identity/what-is) er en skybaseret sikkerhedsløsning, der bruger dit lokale Active Directory-domæneservices (AD DS) signaler til at identificere, registrere og undersøge avancerede trusler, kompromitterede identiteter og ondsindede Insider-handlinger rettet mod din organisation.
- [Microsoft Defender til skyapps](/cloud-app-security/) fungerer som en gatekeeper til at formidle adgang i realtid mellem dine virksomhedsbrugere og de skyressourcer, de bruger, uanset hvor brugerne er placeret, og uanset hvilken enhed de bruger.
- [Microsoft Defender for Office 365](../office-365-security/overview.md) beskytter din organisation mod skadelige trusler i mails, links (URL-adresser) og samarbejdsværktøjer.
- [Azure Security Center](/azure/security-center/security-center-introduction) er et samlet infrastruktursikkerhedsstyringssystem, der styrker sikkerheden i dine datacentre og giver avanceret trusselsbeskyttelse på tværs af dine hybride arbejdsbelastninger i skyen og i det lokale miljø.


In Microsoft 365 Defender hændelser identificeres ved at korrelere beskeder fra disse forskellige [registreringskilder](incidents-overview.md). I stedet for at bruge ressourcer på at strenge sammen eller skelne flere beskeder i deres respektive hændelser, kan du starte med hændelseskøen Microsoft 365 Defender med det samme. Dette giver dig mulighed for at omdele hændelser på en effektiv måde på tværs af slutpunkter, identiteter, mail og programmer og reducere skaden fra et angreb.

## <a name="triage-your-incidents"></a>Efterse dine hændelser

Hændelsesrespons Microsoft 365 Defender, når du får vist listen over hændelser med din organisations anbefalede prioriteringsmetode. At undersøge problemet betyder, at hændelser tildeles et vigtighedsniveau eller haster, hvilket derefter bestemmer den rækkefølge, hvori de skal undersøges.

En nyttig eksempelvejledning til at afgøre, hvilken hændelse der skal prioriteres i Microsoft 365 Defender kan opsummeres af formlen: *Alvorsgrad + Virkning = Prioritet*.

- **Alvorsgrad** er det niveau, der er angivet Microsoft 365 Defender og dets integrerede sikkerhedskomponenter.
- **Virkningen** bestemmes af organisationen og omfatter, men ikke begrænset til, et tærskeltal for påvirkede brugere, enheder, tjenester, der påvirkes (eller en kombination af disse) og endda beskedtype.

Analytikere igangsætter derefter undersøgelser baseret på **de kriterier for Prioritet** , der er angivet af organisationen.

Prioritering af hændelser kan variere afhængigt af organisationen. NIST anbefaler også, at du overvejer hændelsens funktionelle og informationsmæssige virkning og mulighed for gendannelse.

Følgende er blot én fremgangsmåde, du skal overveje:

1. Gå til siden [hændelser for](incidents-overview.md) at starte triage. Her kan du se en liste over hændelser, der påvirker din organisation. Som standard arrangeres de fra den seneste til den ældste hændelse. Herfra kan du også se forskellige kolonner for hver hændelse, der viser deres alvorsgrad, kategori, antal af aktive beskeder og på påvirkede enheder blandt andre. Du kan tilpasse sættet af kolonner og sortere hændelseskøen efter nogle af disse kolonner ved at vælge kolonnenavnet. Du kan også filtrere hændelseskøen efter dine behov. Du kan se en komplet liste over tilgængelige filtre [under Prioriter hændelser](incident-queue.md#available-filters).

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-queue.png" alt-text="Eksempel på hændelseskøen.":::

    Et eksempel på, hvordan du kan udføre prioriteringen af dette sæt hændelser, er at prioritere hændelser, der påvirkede flere brugere og enheder. I dette eksempel kan du prioritere hændelses-id'et 6769, fordi det har påvirket det største antal enheder: 7 enheder, 6 brugere og 2 postkasser. Desuden ser det ud til, at hændelsen indeholder beskeder fra Microsoft Defender for Identity, som angiver en identitetsbaseret besked og muligt tyveri af legitimationsoplysninger.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-high-impact.png" alt-text="Eksempel på en hændelse med høj effekt.":::

2. Vælg cirklen ud for navnet på hændelsen for at gennemgå oplysningerne. Der vises en siderude i højre side, som indeholder yderligere oplysninger, der kan hjælpe din triage yderligere.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout.png" alt-text="Eksempel på en hændelsessiderude.":::

   Ved f.eks. at se på, hvilke [MITRE ATT&CK-taktikker](https://attack.mitre.org/) hackeren brugte baseret på hændelsens kategorier, kan du prioritere denne hændelse, fordi hackeren har brugt legitimationsoplysninger, etableret kommando og kontrol, udført efterfølgende bevægelser og eksfiltreret nogle data. Det antyder, at hackeren allerede er gået dybt ind i netværket og muligvis stjålet fortrolige oplysninger.

   Desuden, hvis din organisation har implementeret Zero Trust Framework, vil du overveje adgang til legitimationsoplysninger som en vigtig sikkerhedskrænkelse, der er værd at prioritere.

   Når du ruller ned i sideruden, får du vist de specifikke på påvirkede enheder som brugere, enheder og postkasser. Du kan kontrollere eksponeringsniveauet for hver enhed og ejerne af de berørte postkasser.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-details.png" alt-text="Eksempel på detaljer i sideruden hændelser.":::

3. Længere nede i sideruden kan du finde de tilknyttede beskeder. Microsoft 365 Defender allerede udført korrelationen af disse beskeder til en enkelt hændelse, hvilket sparer dig tid og bedre ressourcer, der bruges på at løse angrebene. Beskeder er mistænkelige og derfor muligvis skadelige systemhændelser, der antyder, at en hacker er på et netværk.

   I dette eksempel blev 87 individuelle beskeder fundet at være en del af én sikkerhedshændelse. Du kan få vist alle beskederne for at få et hurtigt overblik over, hvordan angrebene blev udspilet.

   :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-incident-flyout-alerts.png" alt-text="Eksempel på beskeder i en siderude for hændelser.":::

## <a name="analyze-your-first-incident"></a>Analysér din første hændelse

Det er lige så vigtigt at forstå konteksten omkring vigtige beskeder. En besked er ofte ikke en enkelt uafhængig hændelse. Der er en kæde af processer, der er oprettet, kommandoer og handlinger, som muligvis ikke er blevet oprettet på samme tid. Derfor skal du se efter den mistænkelige enheds første og sidste aktiviteter på enhedens tidslinjer for at forstå konteksten for beskederne.

Der er flere måder at læse og analysere data på ved hjælp af Microsoft 365 Defender men analytikernes endelige mål er at reagere på hændelser så hurtigt som muligt. Selvom Microsoft 365 Defender betydeligt reducere [MTTR (Mean Time to Remediate)](https://www.microsoft.com/security/blog/2020/05/04/lessons-learned-microsoft-soc-part-3c/) via den [brancheførende funktion](m365d-autoir.md) til automatisk undersøgelse og svar, er der altid tilfælde, der kræver manuel analyse.

Her er et eksempel:

1. Når prioriteringsprioriteten er blevet fastlagt, kan du starte en dybdegående analyse ved at vælge navnet på hændelsen. På denne side vises **Hændelsesoversigt,** hvor data vises i faner for at hjælpe med analysen. Under **fanen Beskeder** vises beskedtypen. Analytikere kan klikke på hver besked for at analysere ned i den pågældende registreringskilde.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-summary-tab.png" alt-text="Eksempel på fanen Oversigt over en hændelse.":::

    Hvis du vil have en hurtig vejledning til, hvilket domæne hver registreringskilde dækker, skal [du se afsnittet](#detection-by-microsoft-365-defender) Registrer i denne artikel.

2. Fra fanen **Beskeder kan** du dreje til registreringskilden for at udføre en mere dybdegående undersøgelse og analyse. Hvis du f.eks. vælger Registrering af malware med Microsoft Defender til skyapps som registreringskilde, kommer analytikeren til sin tilsvarende beskedside.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-select-alert.png" alt-text="Eksempel på valg af en besked om en hændelse.":::

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-link-to-mcas.png" alt-text="Eksempel på en tilsvarende side i Microsoft Defender til skyapps.":::

3. Hvis du vil undersøge vores eksempel yderligere, skal du rulle til bunden af siden for at få vist **de pågældende Brugere**. Hvis du vil se aktiviteten og konteksten omkring malwareregistreringen, skal du vælge An hele Hills brugerside.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-page.png" alt-text="Eksempel på en brugerside.":::

4. På brugersiden vises en kronologisk liste over hændelser, der starter med et risikabelt logon fra en *BESKED om IP-adresse til tor-netværk* . Selvom mistænkeligheden af en aktivitet afhænger af, hvordan en organisation udfører sin virksomhed, kan det i de fleste tilfælde være meget usandsynligt og unødvendigt for almindelige onlinehandlinger, at brugerne kan søge anonymt på internettet i et virksomhedsmiljø.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-user-event-list.png" alt-text="Eksempel på den kronologiske liste over hændelser for en bruger.":::

5. Hver besked kan vælges for at få flere oplysninger om aktiviteten. Hvis du f.eks. **vælger Aktivitet fra en Tor IP-adressebesked** , får du adgang til den pågældende beskeds egen side. Angie er administrator for Office 365, hvilket betyder, at hun har administratorrettigheder, og kildehændelsen kan have ført til adgang til fortrolige oplysninger.

    :::image type="content" source="../../media/first-incident-analyze/first-incident-analyze-mcas-alert.png" alt-text="Eksempel på oplysninger om vigtige beskeder for Microsoft Defender til skyapps .":::

6. Ved at vælge andre beskeder kan du få et komplet billede af angrebene.

## <a name="next-step"></a>Næste trin

[![Trin 2: Lær, hvordan du afhjælper hændelser.](../../media/first-incident-overview/first-incident-path-step2.png)](first-incident-remediate.md)

Få mere at vide [om, hvordan du afhjælper hændelser](first-incident-remediate.md).

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Undersøg hændelser](investigate-incidents.md)
- [Administrer hændelser](manage-incidents.md)
