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
- m365initiative-m365-defender
- incidentresponse
- m365solution-incidentresponse
- m365solution-overview
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 4bba9797572193199dba0bd4c928693d94bf00de
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569152"
---
# <a name="investigate-incidents-in-microsoft-365-defender"></a>Undersøg hændelser i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

Microsoft 365 Defender samler alle relaterede beskeder, aktiver, undersøgelser og beviser på tværs af dine enheder, brugere og postkasser i en hændelse for at give dig et omfattende indblik i hele dit angrebs brød.

Inden for en hændelse kan du analysere de beskeder, der påvirker dit netværk, forstå, hvad de betyder, og indsamle beviserne, så du kan udtænke en effektiv afhjælpningsplan.

## <a name="initial-investigation"></a>Indledende undersøgelse

Før du går i gang med detaljerne, skal du se på egenskaberne for og oversigten over hændelsen.

Du kan starte med at vælge hændelsen fra markeringskolonnen. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-select.png" alt-text="Valg af en hændelse i Microsoft 365 Defender-portalen" lightbox="../../media/investigate-incidents/incidents-ss-incident-select.png":::

Når du gør det, åbnes en oversigtsrude med vigtige oplysninger om hændelsen, f.eks. alvorsgrad, som den er tildelt, og [MITRE ATT&CK-kategorierne&trade;](https://attack.mitre.org/) for hændelsen. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incidents-ss-incident-side-panel.png" alt-text="Ruden, der viser oversigtsoplysninger om en hændelse i Microsoft 365 Defender portal." lightbox="../../media/investigate-incidents/incidents-ss-incident-side-panel.png":::

Herfra kan du vælge **Åbn hændelsesside**. Dette åbner hovedsiden for hændelsen, hvor du kan finde flere oversigtsoplysninger og faner til beskeder, enheder, brugere, undersøgelser og beviser.

Du kan også åbne hovedsiden for en hændelse ved at vælge navnet på hændelsen fra hændelseskøen.

## <a name="summary"></a>Oversigt

**Oversigtssiden** giver dig et øjebliksbillede af de vigtigste ting, du kan lægge mærke til om hændelsen.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Oversigtsoplysninger om en hændelse i Microsoft 365 Defender-portalen" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

Oplysningerne er organiseret i disse afsnit.

| Sektion | Beskrivelse |
|:-------|:-----|
| Beskeder og kategorier | En visuel og numerisk visning af, hvordan avancerede angrebene har udviklet sig mod kill-kæden. Som med andre Microsoft-sikkerhedsprodukter er Microsoft 365 Defender justeret til [MITRE ATT&CK-framework&trade;](https://attack.mitre.org/). Tidslinjen for vigtige beskeder viser den kronologiske rækkefølge, hvori beskederne blev foretaget, samt deres status og navn. |
| Omfang |  Viser antallet af på påvirkede enheder, brugere og postkasser og viser enhederne i rækkefølge efter risikoniveau og prioritet af undersøgelsen. |
| Beviser | Viser antallet af enheder, der påvirkes af hændelsen. |
| Oplysninger om hændelse | Viser egenskaberne for hændelsen, f.eks. mærker, status og alvorsgrad. |
|||

Brug siden **Oversigt** til at vurdere den relative vigtighed af hændelsen og hurtigt få adgang til de tilknyttede beskeder og påknyttede enheder.

## <a name="alerts"></a>Beskeder

Under fanen **Vigtige beskeder kan** du få vist beskedkøen for vigtige beskeder om hændelsen og andre oplysninger om dem, f.eks.:

- Alvorsgrad.
- De enheder, der var involveret i beskeden.
- Kilden til beskederne (Microsoft Defender for Identity, Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Defender til skyapps og tilføjelsesprogrammet Appstyring).
- Årsagen til, at de er kædet sammen.

Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-alerts.png" alt-text="Ruden Beskeder om en hændelse i Microsoft 365 Defender-portalen" lightbox="../../media/investigate-incidents/incident-alerts.png":::

Som standard er beskederne sorteret kronologisk, så du kan se, hvordan angrebene udspiller over tid. Når du vælger en besked i en hændelse, Microsoft 365 Defender en meddelelse, der er specifik for den overordnede hændelse. 

Du kan se hændelserne for beskeden, som andre udløste beskeder forårsagede den aktuelle besked, og alle de påvirkede enheder og aktiviteter, der er involveret i angrebene, herunder enheder, filer, brugere og postkasser.

Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-alert-example.png" alt-text="Oplysninger om en besked i en hændelse i Microsoft 365 Defender portal." lightbox="../../media/investigate-incidents/incident-alert-example.png":::

Siden besked om hændelser indeholder følgende afsnit:

- Tekstenhed, som omfatter:

   - Hvad skete der

   - Handlinger, der er foretaget

   - Relaterede begivenheder

- Beskedegenskaber i højre rude (tilstand, detaljer, beskrivelse og andre)

Ikke alle vigtige beskeder har alle de angivne underafsnit i sektionen **Beskedhistorie** .

Få mere at vide om, hvordan du bruger beskedkøen og [beskedsiderne under undersøg vigtige beskeder](investigate-alerts.md).

## <a name="devices"></a>Enheder

Under **fanen** Enheder vises alle de enheder, der er relateret til hændelsen. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-devices.png" alt-text="Siden Enheder for en hændelse i Microsoft 365 Defender-portalen" lightbox="../../media/investigate-incidents/incident-devices.png":::

Du kan markere afkrydsningsfeltet for en enhed for at få vist oplysninger om enheden, biblioteksdata, aktive beskeder og brugere, der er logget på. Vælg navnet på enheden for at få vist enhedens detaljer i Defender for endpoint-enhedens lager. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-devices-details.png" alt-text="Indstillingssiden for lager for enhed i Microsoft Defender for Endpoint." lightbox="../../media/investigate-incidents/incident-devices-details.png":::

Fra enhedssiden kan du indsamle yderligere oplysninger om enheden, f.eks. alle dens vigtige beskeder, en tidslinje og sikkerhedsanbefalinger. Fra fanen Tidslinje kan du  f.eks. rulle gennem computertidslinjen og få vist alle hændelser og funktionsmåder, der er observeret på computeren i kronologisk rækkefølge og afbrudt med beskederne hævet.

> [!TIP]
> Du kan udføre scanninger efter behov på en enhedsside. I Microsoft 365 Defender skal du vælge **Slutpunkter > lager over enheder**. Vælg en enhed, der har beskeder, og kør derefter en antivirus-scanning. Handlinger, f.eks. antivirusscanninger, registreres og er synlige på **lagersiden for** enheden. Du kan få mere at vide [under Kør Defender Antivirus-scanning på enheder](/microsoft-365/security/defender-endpoint/respond-machine-alerts#run-microsoft-defender-antivirus-scan-on-devices).

## <a name="users"></a>Brugere

Fanen **Brugere viser** alle de brugere, der er identificeret som en del af eller relateret til hændelsen. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Siden Brugere i Microsoft 365 Defender portal." lightbox="../../media/investigate-incidents/incident-users.png":::

Du kan markere afkrydsningsfeltet for en bruger for at få vist oplysninger om brugerkontoens trussel, eksponering og kontaktoplysninger. Vælg brugernavnet for at få vist yderligere oplysninger om brugerkontoen.

Få mere at vide om, hvordan du får vist yderligere brugeroplysninger og administrerer brugere af en hændelse [under undersøg brugerne](investigate-users.md).


## <a name="mailboxes"></a>Postkasser

Fanen **Postkasser** viser alle de postkasser, der er blevet identificeret som en del af eller relateret til hændelsen. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-mailboxes.png" alt-text="Siden Postkasser for en hændelse i Microsoft 365 Defender portal." lightbox="../../media/investigate-incidents/incident-mailboxes.png":::

Du kan markere afkrydsningsfeltet for en postkasse for at få vist en liste over aktive beskeder. Vælg postkassenavnet for at få vist yderligere postkasseoplysninger på siden Stifinder for at Defender for Office 365.

## <a name="investigations"></a>Undersøgelser

Fanen **Undersøgelser viser** alle de automatiske [undersøgelser, der udløses](m365d-autoir.md) af beskeder om denne hændelse. Automatiserede undersøgelser vil udføre afhjælpningshandlinger eller vente på godkendelser af handlinger fra en analytiker, afhængigt af hvordan du har konfigureret dine automatiske undersøgelser til at køre i Defender til Slutpunkt og Defender for Office 365.

:::image type="content" source="../../media/investigate-incidents/incident-investigations.png" alt-text="Siden Undersøgelser for en hændelse i Microsoft 365 Defender-portalen" lightbox="../../media/investigate-incidents/incident-investigations.png":::

Vælg en undersøgelse for at gå til dens detaljeside for at få alle oplysninger om undersøgelsens og afhjælpningsstatus. Hvis der er handlinger, der afventer godkendelse som en del af undersøgelsen, vises de på **fanen Ventende handlinger historik** . Foranstaltninger som en del af afhjælpning af hændelser.

Der er også en **Undersøgelse-graf-fane** , der viser:

- Forbindelse af beskeder til de på påvirkede aktiver i organisationen.
- Hvilke enheder er relateret til hvilke beskeder, og hvordan de er en del af historien om angrebene.
- Beskederne om hændelsen.

Undersøgelsesgrafen hjælper dig med hurtigt at forstå det fulde omfang af angrebene ved at forbinde de forskellige mistænkelige enheder, der er en del af angrebene, med deres relaterede aktiver som brugere, enheder og postkasser. 

Få mere at vide under [Automatiseret undersøgelse og svar Microsoft 365 Defender](m365d-autoir.md).

## <a name="evidence-and-response"></a>Beviser og svar

Fanen **Beviser og svar** viser alle de understøttede hændelser og mistænkelige enheder i beskederne for hændelsen. Her er et eksempel.

:::image type="content" source="../../media/investigate-incidents/incident-evidence.png" alt-text="Siden Bevis og svar for en hændelse i Microsoft 365 Defender portal" lightbox="../../media/investigate-incidents/incident-evidence.png":::

Microsoft 365 Defender undersøger automatisk alle hændelsers understøttede begivenheder og mistænkelige enheder i beskederne og giver dig oplysninger om vigtige mails, filer, processer, tjenester, IP-adresser og meget mere. Dette hjælper dig med hurtigt at finde og blokere potentielle trusler i hændelsen.

Hver af de analyserede enheder er markeret med en konklusion (Ondsindet, Mistænkelig, Rens) og en afhjælpningsstatus. Dette hjælper dig med at forstå afhjælpningsstatus for hele hændelsen, og hvilke næste trin der kan tages.

## <a name="graph-preview"></a>Graph (eksempel)

Fanen **Graph** viser det fulde omfang af angrebene, hvordan angrebene spredte sig gennem dit netværk over tid, hvor det startede, og hvor langt hackeren var. Det forbinder de forskellige mistænkelige enheder, der er en del af angrebene, med deres relaterede aktiver som brugere, enheder og postkasser. 

Under **Graph** kan du:

1. Afspil beskederne og noderne på grafen, når de opstod over tid, for at forstå kronologien af angrebene.


   :::image type="content" source="../../media/investigate-incidents/incident-graph-play.gif" alt-text="Afspilning af beskeder og noder på siden Graph beskeder":::
 

2. Åbn en enhedsrude, hvor du kan gennemse enhedsdetaljerne og reagere på afhjælpningshandlinger, f.eks. sletning af en fil eller isolere en enhed.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-entity-pane.png" alt-text="Enhedsruden på Graph i Microsoft 365 Defender portal" lightbox="../../media/investigate-incidents/incident-graph-entity-pane.png":::

3. Fremhæv beskederne baseret på den enhed, de er relateret til.
 
   :::image type="content" source="../../media/investigate-incidents/incident-graph-alert.png" alt-text="En fremhævet besked på Graph side" lightbox="../../media/investigate-incidents/incident-graph-alert.png":::

## <a name="next-steps"></a>Næste trin

Efter behov:

- [Undersøg beskederne om en hændelse](investigate-alerts.md)
- [Undersøg brugerne af en hændelse](investigate-users.md)

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Prioriter hændelser](incident-queue.md)
- [Administrer hændelser](manage-incidents.md)
