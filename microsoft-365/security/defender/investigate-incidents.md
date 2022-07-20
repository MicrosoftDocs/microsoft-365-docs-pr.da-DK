---
title: Undersøg hændelser i Microsoft 365 Defender
description: Undersøg hændelser, der er relateret til enheder, brugere og postkasser.
keywords: hændelse, hændelser, analysere, svar, maskiner, enheder, brugere, identiteter, mail, mail, postkasse, undersøgelse, graf, beviser
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
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 441f9ce5824c1de82a5629e4c0ba9192ed89a529
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66895069"
---
# <a name="investigate-incidents-in-microsoft-365-defender"></a>Undersøg hændelser i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

Microsoft 365 Defender samler alle relaterede beskeder, aktiver, undersøgelser og beviser på tværs af dine enheder, brugere og postkasser i en hændelse for at give dig et omfattende indblik i hele bredden af et angreb.

I en hændelse analyserer du de beskeder, der påvirker dit netværk, forstår, hvad de betyder, og samler beviserne, så du kan udarbejde en effektiv afhjælpningsplan.

## <a name="initial-investigation"></a>Indledende undersøgelse

Før du går i detaljer, skal du se på egenskaberne og resuméet af hændelsen.

Du kan starte med at vælge hændelsen i markeringskolonnen. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-select.png" alt-text="Valg af en hændelse på Microsoft 365 Defender-portalen" lightbox="../../media/investigate-incidents/incidents-ss-incident-select.png":::

Når du gør det, åbnes en oversigtsrude med vigtige oplysninger om hændelsen, f.eks. alvorsgrad, hvem den er tildelt, og [MITRE ATT-&CK-kategorierne&trade;](https://attack.mitre.org/) for hændelsen. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-side-panel.png" alt-text="Den rude, der viser oversigtsoplysningerne for en hændelse på Microsoft 365 Defender-portalen." lightbox="../../media/investigate-incidents/incidents-ss-incident-side-panel.png":::

Herfra kan du vælge **Åbn hændelsesside**. Dette åbner hovedsiden for hændelsen, hvor du kan finde flere oversigtsoplysninger og faner for beskeder, enheder, brugere, undersøgelser og beviser.

Du kan også åbne hovedsiden for en hændelse ved at vælge hændelsesnavnet i hændelseskøen.

## <a name="summary"></a>Oversigt

Siden **Oversigt** giver dig et øjebliksbillede af de vigtigste ting, du kan lægge mærke til om hændelsen.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Oversigtsoplysningerne for en hændelse på Microsoft 365 Defender-portalen" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

Oplysningerne er organiseret i disse afsnit.

| Afsnit | Beskrivelse |
|:-------|:-----|
| Beskeder og kategorier | Et visuelt og numerisk billede af, hvor avanceret angrebet har udviklet sig mod kill-kæden. Som med andre Microsoft-sikkerhedsprodukter er Microsoft 365 Defender justeret i forhold til [MITRE ATT-&CK-strukturen&trade;](https://attack.mitre.org/). Tidslinjen for beskeder viser den kronologiske rækkefølge, som beskederne indtraf i, og for hver af dem deres status og navn. |
| Omfanget |  Viser antallet af påvirkede enheder, brugere og postkasser og viser enhederne i rækkefølge efter risikoniveau og undersøgelsesprioritet. |
| Beviser | Viser antallet af enheder, der påvirkes af hændelsen. |
| Oplysninger om hændelse | Viser egenskaberne for hændelsen, f.eks. mærker, status og alvorsgrad. |
|||

Brug siden **Oversigt** til at vurdere den relative vigtighed af hændelsen og hurtigt få adgang til de tilknyttede beskeder og påvirkede enheder.

## <a name="alerts"></a>Beskeder

Under fanen **Beskeder** kan du få vist beskedkøen for beskeder, der er relateret til hændelsen, og andre oplysninger om dem, f.eks.:

- Sværhedsgraden.
- De enheder, der var involveret i beskeden.
- Kilden til beskederne (Microsoft Defender for Identity, Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Defender for Cloud Apps og tilføjelsesprogrammet til appstyring).
- Grunden til at de var forbundet.

Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-alerts.png" alt-text="Ruden Beskeder for en hændelse på Microsoft 365 Defender-portalen" lightbox="../../media/investigate-incidents/incident-alerts.png":::

Som standard er beskederne sorteret kronologisk, så du kan se, hvordan angrebet udspillede sig over tid. Når du vælger en besked i en hændelse, viser Microsoft 365 Defender de beskedoplysninger, der er specifikke for konteksten for den overordnede hændelse. 

Du kan se hændelserne for beskeden, som andre udløste beskeder forårsagede den aktuelle besked, og alle de berørte enheder og aktiviteter, der er involveret i angrebet, herunder enheder, filer, brugere og postkasser.

Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-alert-example.png" alt-text="Oplysningerne om en besked i en hændelse på portalen Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-alert-example.png":::

Siden med hændelsesbeskeder indeholder følgende sektioner:

- Beskedhistorie, som omfatter:

   - Hvad skete der

   - Udførte handlinger

   - Relaterede hændelser

- Egenskaber for beskeder i ruden til højre (tilstand, detaljer, beskrivelse m.m.)

Det er ikke alle beskeder, der har alle de viste undersektioner i afsnittet **Beskedhistorie** .

Få mere at vide om, hvordan du bruger beskedkøen og beskedsiderne i [undersøg beskeder](investigate-alerts.md).

## <a name="devices"></a>Enheder

Fanen **Enheder** viser alle de enheder, der er relateret til hændelsen. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-devices.png" alt-text="Siden Enheder for en hændelse på Microsoft 365 Defender-portalen" lightbox="../../media/investigate-incidents/incident-devices.png":::

Du kan markere afkrydsningsfeltet for en enhed for at få vist oplysninger om enheden, mappedata, aktive beskeder og brugere, der er logget på. Vælg navnet på enheden for at få vist enhedsoplysningerne i oversigten over Defender for Endpoint-enheder. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-devices-details.png" alt-text="Siden Med indstillingen Enhedslager i Microsoft Defender for Endpoint." lightbox="../../media/investigate-incidents/incident-devices-details.png":::

Fra enhedssiden kan du indsamle yderligere oplysninger om enheden, f.eks. alle dens beskeder, en tidslinje og sikkerhedsanbefalinger. Fra fanen **Tidslinje** kan du f.eks. rulle gennem computerens tidslinje og få vist alle hændelser og funktionsmåder, der er observeret på computeren i kronologisk rækkefølge, og som er afbrudt af de udløste beskeder.

> [!TIP]
> Du kan udføre scanninger efter behov på en enhedsside. Vælg **Slutpunkter > Enhedslager** på portalen Microsoft 365 Defender. Vælg en enhed, der har beskeder, og kør derefter en antivirusscanning. Handlinger, f.eks. antivirusscanninger, spores og er synlige på **enhedens lagerside** . Du kan få mere at vide under [Kør Defender Antivirus-scanning på enheder](/microsoft-365/security/defender-endpoint/respond-machine-alerts#run-microsoft-defender-antivirus-scan-on-devices).

## <a name="users"></a>Brugere

Under fanen **Brugere** vises alle de brugere, der er blevet identificeret til at være en del af eller relateret til hændelsen. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Siden Brugere på Microsoft 365 Defender-portalen." lightbox="../../media/investigate-incidents/incident-users.png":::

Du kan vælge fluebenet for en bruger for at få vist detaljer om brugerkontoens trussel, eksponering og kontaktoplysninger. Vælg brugernavnet for at få vist flere oplysninger om brugerkontoen.

Få mere at vide om, hvordan du får vist yderligere brugeroplysninger og administrerer brugerne af en hændelse i [Undersøg brugere](investigate-users.md).


## <a name="mailboxes"></a>Postkasser

Fanen **Postkasser** viser alle de postkasser, der er blevet identificeret til at være en del af eller relateret til hændelsen. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-mailboxes.png" alt-text="Siden Postkasser for en hændelse på portalen Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-mailboxes.png":::

Du kan markere afkrydsningsfeltet for en postkasse for at få vist en liste over aktive beskeder. Vælg navnet på postkassen for at få vist flere oplysninger om postkassen på siden Stifinder for Defender for Office 365.

## <a name="investigations"></a>Undersøgelser

Under fanen **Undersøgelser** vises alle de [automatiserede undersøgelser, der udløses](m365d-autoir.md) af beskeder i denne hændelse. Automatiserede undersøgelser udfører afhjælpningshandlinger eller venter på analytikergodkendelse af handlinger, afhængigt af hvordan du har konfigureret dine automatiserede undersøgelser til at køre i Defender for Endpoint og Defender for Office 365.

:::image type="content" source="../../media/investigate-incidents/incident-investigations.png" alt-text="Siden Undersøgelser for en hændelse på Microsoft 365 Defender-portalen" lightbox="../../media/investigate-incidents/incident-investigations.png":::

Vælg en undersøgelse for at navigere til siden med oplysninger for at få alle oplysninger om undersøgelses- og afhjælpningsstatus. Hvis der er handlinger, der venter på godkendelse som en del af undersøgelsen, vises de under fanen **Ventende handlingers historik** . Udfør handlinger som en del af afhjælpning af hændelser.

Der er også en **graffane for undersøgelse** , der viser:

- Forbindelsen mellem beskeder og de påvirkede aktiver i din organisation.
- Hvilke enheder er relateret til hvilke beskeder og hvordan de er en del af historien om angrebet.
- Beskederne for hændelsen.

Undersøgelsesgrafen hjælper dig med hurtigt at forstå det fulde omfang af angrebet ved at forbinde de forskellige mistænkelige enheder, der er en del af angrebet, med deres relaterede aktiver, f.eks. brugere, enheder og postkasser. 

Du kan få flere oplysninger [under Automatiseret undersøgelse og svar i Microsoft 365 Defender](m365d-autoir.md).

## <a name="evidence-and-response"></a>Beviser og svar

Fanen **Beviser og Svar** viser alle understøttede hændelser og mistænkelige enheder i beskederne i hændelsen. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-evidence.png" alt-text="Siden Beviser og svar for en hændelse på Microsoft 365 Defender-portalen" lightbox="../../media/investigate-incidents/incident-evidence.png":::

Microsoft 365 Defender undersøger automatisk alle hændelsers understøttede hændelser og mistænkelige enheder i beskederne, hvilket giver dig oplysninger om vigtige mails, filer, processer, tjenester, IP-adresser med mere. Dette hjælper dig med hurtigt at registrere og blokere potentielle trusler i hændelsen.

Hver af de analyserede enheder er markeret med en dom (Ondsindet, Mistænkelig, Ren) og en afhjælpningsstatus. Dette hjælper dig med at forstå afhjælpningsstatus for hele hændelsen, og hvilke næste trin der kan udføres.

## <a name="graph-preview"></a>Graph (prøveversion)

Under fanen **Graph** kan du se det fulde omfang af angrebet, hvordan angrebet spredte sig gennem dit netværk over tid, hvor det startede, og hvor langt angriberen gik. Den forbinder de forskellige mistænkelige enheder, der er en del af angrebet, med deres relaterede aktiver, f.eks. brugere, enheder og postkasser. 

Under fanen **Graph** kan du:

1. Afspil beskederne og noderne på grafen, som de fandt sted over tid for at forstå kronologien af angrebet.


   :::image type="content" source="../../media/investigate-incidents/incident-graph-play.gif" alt-text="Afspilningen af beskeder og noder på siden Graph":::
 

2. Åbn en objektrude, så du kan gennemse enhedsoplysningerne og reagere på afhjælpningshandlinger, f.eks. slette en fil eller isolere en enhed.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-entity-pane.png" alt-text="Objektruden på siden Graf på Microsoft 365 Defender-portalen" lightbox="../../media/investigate-incidents/incident-graph-entity-pane.png":::

3. Fremhæv de beskeder, der er baseret på det objekt, de er relateret til.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-alert.png" alt-text="En fremhævning af en besked på grafsiden" lightbox="../../media/investigate-incidents/incident-graph-alert.png":::

## <a name="next-steps"></a>Næste trin

Efter behov:

- [Undersøg beskeder om en hændelse](investigate-alerts.md)
- [Undersøg brugerne af en hændelse](investigate-users.md)

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Prioriter hændelser](incident-queue.md)
- [Administrer hændelser](manage-incidents.md)
