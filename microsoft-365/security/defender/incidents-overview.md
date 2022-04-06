---
title: Hændelsesrespons med Microsoft 365 Defender
description: Undersøg hændelser, der kan ses på tværs af enheder, brugere og postkasser i Microsoft 365 Defender portal.
keywords: hændelser, beskeder, undersøge, analysere, svare, korrelation, angreb, maskiner, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365, hændelsesrespons, cyberangreb
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
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 233c9993c8cd5978bcdfcbb54db8b9688c3ac056
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500029"
---
# <a name="incident-response-with-microsoft-365-defender"></a>Hændelsesrespons med Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

> Vil du gerne Microsoft 365 Defender? Du kan [evaluere det i et labmiljø](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) eller [køre dit pilotprojekt i produktion](m365d-pilot.md?ocid=cx-evalpilot).
>

En hændelse i Microsoft 365 Defender er en samling af korrelerede beskeder og tilknyttede data, der udgør historien om et angreb. 

Microsoft 365 og apps opretter beskeder, når de registrerer en mistænkelig eller skadelig hændelse eller aktivitet. Individuelle beskeder giver værdifulde fingerpeg om et fuldført eller igangværende angreb. Men angreb anvender typisk forskellige teknikker mod forskellige typer enheder, f.eks enheder, brugere og postkasser. Resultatet er flere beskeder for flere enheder i din lejer. 

Da det kan være udfordrende og tidskrævende at sammenlægge de enkelte beskeder for at få indsigt i et angreb, samler Microsoft 365 Defender automatisk beskederne og deres tilknyttede oplysninger i en hændelse.

:::image type="content" source="../../media/incidents-overview/incidents.png" alt-text="Hvordan Microsoft 365 Defender korrelerer begivenheder fra enheder til en hændelse." lightbox="../../media/incidents-overview/incidents.png":::

Se denne korte oversigt over hændelser på Microsoft 365 Defender (4 minutter).

<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Gruppering af relaterede beskeder i en hændelse giver dig en omfattende oversigt over et angreb. Du kan f.eks. se:

- Hvor angrebene startede.
- Hvilke taktikker blev brugt.
- Hvor langt angrebene er nået ind i din lejer.
- Omfanget af angrebene, f.eks. hvor mange enheder, brugere og postkasser, der blev påvirket. 
- Alle de data, der er knyttet til angrebene.

Hvis [det er](m365d-enable.md) aktiveret, Microsoft 365 Defender [automatisk undersøge og løse](m365d-autoir.md) beskeder via automatisering og kunstig intelligens. Du kan også udføre yderligere afhjælpningstrin for at løse angrebene. 

## <a name="incidents-and-alerts-in-the-microsoft-365-defender-portal"></a>Hændelser og beskeder i Microsoft 365 Defender-portalen

Du administrerer hændelser **fra hændelser & beskeder > hændelser** i hurtig start af <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portal</a>. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Siden Hændelser i Microsoft 365 Defender portalen." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Når du vælger et hændelsesnavn, vises en oversigt over hændelsen, og du får adgang til faner med yderligere oplysninger. Her er et eksempel.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Oversigtssiden for en hændelse i Microsoft 365 Defender-portalen" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

De ekstra faner for en hændelse er:

- Beskeder 

  Alle beskeder, der er relateret til hændelsen og deres oplysninger.

- Enheder

  Alle de enheder, der er identificeret som en del af eller relateret til hændelsen.

- Brugere

  Alle de brugere, der er identificeret som en del af eller relateret til hændelsen.

- Postkasser

  Alle de postkasser, der er identificeret som en del af eller relateret til hændelsen.

- Undersøgelser

  Alle de [automatiserede undersøgelser,](m365d-autoir.md) der er udløst af beskeder om hændelsen.

- Beviser og svar

  Alle understøttede hændelser og mistænkelige enheder i beskederne om hændelsen.

- Graph (eksempel)

  En visuel repræsentation af de angreb, der forbinder de forskellige mistænkelige enheder, der er en del af angrebene, med deres relaterede aktiver som brugere, enheder og postkasser.

Her er forholdet mellem en hændelse og dens data og fanerne for en hændelse i Microsoft 365 Defender-portalen.

:::image type="content" source="../../media/incidents-overview/incidents-security-center.png" alt-text="Forholdet mellem en hændelse og dens data med fanerne for en hændelse i Microsoft 365 Defender-portalen." lightbox="../../media/incidents-overview/incidents-security-center.png":::

## <a name="example-incident-response-workflow-for-microsoft-365-defender"></a>Eksempel på hændelsesresponsarbejdsproces for Microsoft 365 Defender

Her er et eksempel på en arbejdsproces til at besvare hændelser Microsoft 365 med Microsoft 365 Defender-portalen.

:::image type="content" source="../../media/incidents-overview/incidents-example-workflow.png" alt-text="Et eksempel på en arbejdsproces for hændelsesrespons for Microsoft 365 Defender-portalen." lightbox="../../media/incidents-overview/incidents-example-workflow.png":::

Identificer løbende de hændelser, der har den højeste prioritet, for analyse og løsning i hændelseskøen, og gør dem klar til svar. Dette er en kombination af:

- [Triaging](incident-queue.md) to determining the highest priority incidents through filtering and sorting of the incident queue.
- [Administrer](manage-incidents.md) hændelser ved at ændre deres titel, tildele dem til en analytiker og tilføje mærker og kommentarer.

Overvej disse trin for din egen arbejdsproces for hændelsesrespons:

1. Start et angreb og en undersøgelse og analyse [af beskeder for hver hændelse](investigate-incidents.md):
 
   1. Få vist oversigten over hændelsen for at forstå dens omfang og alvor, og hvilke enheder der påvirkes  med fanerne **Oversigt Graph** (eksempel).

   1. Begynd at analysere beskederne for at forstå deres oprindelse, omfang og alvorsgrad med **fanen Beskeder** .

   1. Efter behov kan du indsamle oplysninger om på påvirkede enheder, brugere og postkasser ved hjælp **af fanerne** **Enheder,** Brugere **og Postkasser** .

   1. Se, Microsoft 365 Defender har [løst nogle af beskederne](m365d-autoir.md) på **fanen Undersøgelser** automatisk.
   
   1. Efter behov kan du bruge oplysningerne i datasættet for hændelsen for at få flere oplysninger med **fanen Bevis og** svar.

2. Efter eller under din analyse skal du udføre en inddædning for at reducere eventuelle yderligere indvirkninger af angrebene og den sikkerhedstrussel, du er i.

3. Så meget som muligt kan du gendanne fra angrebene ved at gendanne dine lejerressourcer i den tilstand, de var i før hændelsen.

4. [Løs](manage-incidents.md#resolve-an-incident) hændelsen, og tag tid, før efter hændelsen lærer at:

   - Forstå typen af angreb og dens virkning.
   - Underse angrebene [i Threat Analytics](threat-analytics.md) og sikkerhedsfællesskabet for en tendens for sikkerhedsangreb.
   - Tilbagekald den arbejdsproces, du brugte til at løse hændelsen, og opdater dine almindelige arbejdsprocesser, processer, politikker og afspilningsbøger efter behov.
   - Afgør, om der er behov for ændringer i sikkerhedskonfigurationen, og implementer dem.

Hvis du er ny bruger af sikkerhedsanalyse, kan du se introduktionen til at besvare din første [hændelse for at](incidents-overview.md) få flere oplysninger og gennemgå en eksempelhændelse.

Du kan finde flere oplysninger om hændelsesrespons på tværs af Microsoft-produkter [i denne artikel](/security/compass/incident-response-overview).

## <a name="example-security-operations-for-microsoft-365-defender"></a>Eksempel på sikkerhedshandlinger for Microsoft 365 Defender

Her er et eksempel på sikkerhedshandlinger (SecOps) for Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-example-operations.png" alt-text="Et eksempel på sikkerhedshandlinger for Microsoft 365 Defender" lightbox="../../media/incidents-overview/incidents-example-operations.png":::

Daglige opgaver kan omfatte:

- [Administrer](manage-incidents.md) hændelser
- Gennemgang af [automatiserede undersøgelses- og svarhandlinger (AIR)](m365d-action-center.md) i handlingscenteret
- Gennemgå de nyeste [Threat Analytics](threat-analytics.md)
- [Sådan](investigate-incidents.md) reagerer du på hændelser

Månedlige opgaver kan omfatte:

- Gennemgang af [AIR-indstillinger](m365d-configure-auto-investigation-response.md)
- Gennemgang af [Secure Score](microsoft-secure-score-improvement-actions.md) and [Threat & Vulnerability Management](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Rapportering til din IT-sikkerhedsstyringskæde

Kvartalsopgaver kan omfatte en rapport og briefing af sikkerhedsresultater til Chief Information Security Officer (CISO).

Årlige opgaver kan omfatte udførelse af en større hændelse eller brudstræning for at teste medarbejdere, systemer og processer. 

Daglige, månedlige, kvartalsvise og årlige opgaver kan bruges til at opdatere eller forbedre processer, politikker og sikkerhedskonfigurationer.

Se [ Integration af Microsoft 365 Defender i dine sikkerhedshandlinger for at](integrate-microsoft-365-defender-secops.md) få flere oplysninger.

### <a name="secops-resources-across-microsoft-products"></a>SecOps-ressourcer på tværs af Microsoft-produkter

Du kan finde flere oplysninger om SecOps på tværs af Microsofts produkter i disse ressourcer:

- [Funktioner](/security/compass/security-operations-capabilities)
- [Best practices](/security/compass/security-operations)
- [Videoer og slides](/security/compass/security-operations-videos-and-decks)


## <a name="get-incident-notifications-by-email"></a>Få hændelsesmeddelelser via mail

Du kan konfigurere en Microsoft 365 Defender at give dine medarbejdere besked via mail om nye hændelser eller opdateringer til eksisterende hændelser. Du kan vælge at få meddelelser baseret på:

- Hændelsens alvorsgrad.
- Enhedsgruppe.
- Kun ved den første opdatering pr. hændelse.

Mailmeddelelsen indeholder vigtige oplysninger om hændelsen, f.eks. hændelsens navn, alvorsgrad og kategorier, blandt andre. Du kan også gå direkte til hændelsen og starte din analyse med det samme. Få mere at vide under [Undersøg hændelser](investigate-incidents.md).

Du kan tilføje eller fjerne modtagere i mailmeddelelser. Nye modtagere får besked om hændelser, når de er tilføjet. 

>[!NOTE]
>Du skal have tilladelsen **Administrer sikkerhedsindstillinger** for at konfigurere indstillinger for mailbeskeder. Hvis du har valgt at bruge grundlæggende administration af tilladelser, kan brugere med sikkerhedsadministratorroller eller globale administratorroller konfigurere mailbeskeder. <br> <br>
På samme måde kan du, hvis din organisation bruger rollebaseret adgangskontrol, kun oprette, redigere, slette og modtage meddelelser baseret på enhedsgrupper, som du har tilladelse til at administrere.

### <a name="create-a-rule-for-email-notifications"></a>Opret en regel for mailbeskeder

Følg disse trin for at oprette en ny regel og tilpasse indstillinger for mailbeskeder.

1. I navigationsruden skal du vælge Indstillinger > Microsoft 365 Defender > **hændelsesmailmeddelelser**.
2. Vælg **Tilføj element**.
3. Skriv **regelnavnet og** en beskrivelse på siden Grundlæggende, og vælg derefter **Næste**.
4. På siden **Meddelelsesindstillinger** skal du konfigurere:
    - **Alvorsgrad for besked** – Vælg de alvorsgrader for beskeden, der udløser en hændelsesmeddelelse. Hvis du f.eks. kun vil informeres om hændelser med høj alvorlighed, skal du vælge **Høj**.
    - **Omfang for enhedsgrupper** – Du kan angive alle enhedsgrupper eller vælge på listen over enhedsgrupper i din lejer.
    - **Giv kun besked ved første forekomst pr. hændelse** – Vælg, om du kun vil have en besked på den første besked, der svarer til dine andre valg. Senere opdateringer eller beskeder, der er relateret til hændelsen, sender ikke yderligere meddelelser.
    - **Medtag organisationsnavn i mailen** – Vælg, om din organisations navn skal vises i mailmeddelelsen.
    - **Medtag lejerspecifik portallink** – Vælg, om du vil tilføje et link til lejer-id'et i mailmeddelelsen om adgang til en bestemt Microsoft 365 lejer.

    :::image type="content" source="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png" alt-text="Siden Meddelelsesindstillinger for beskeder om hændelsesmail i Microsoft 365 Defender-portalen." lightbox="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png":::

5. Vælg **Næste**. På siden **Modtagere skal** du tilføje de mailadresser, der modtager beskeder om hændelser. Vælg **Tilføj,** når du har skrevet hver ny mailadresse. Hvis du vil teste meddelelser og sikre, at modtagerne modtager dem i indbakkerne, skal du vælge **Send testmail**. 
6. Vælg **Næste**. Gennemgå **reglens indstillinger** på siden Gennemse regel, og vælg derefter **Opret regel**. Modtagerne begynder at modtage beskeder om hændelser via mail baseret på indstillingerne.

Hvis du vil redigere en eksisterende regel, skal du vælge den på listen over regler. I ruden med regelnavnet skal du **vælge Rediger** regel og foretage dine ændringer på **siderne Grundlæggende,** **Meddelelsesindstillinger og** Modtagere. 

Hvis du vil slette en regel, skal du markere den på listen over regler. Vælg Slet i ruden med **regelnavnet**.


## <a name="training-for-security-analysts"></a>Kurser til sikkerhedsanalytikere

Brug dette læringsmodul fra Microsoft Learn til at forstå, hvordan Microsoft 365 Defender bruges til at administrere hændelser og beskeder.

|Kursus:|Undersøg hændelser med Microsoft 365 Defender|
|---|---|
|![Undersøg hændelser med Microsoft 365 Defender undervisningsikon.](../../media/incidents-overview/m365-defender-address-security-investigation.svg)| Microsoft 365 Defender samlede trusselsdata fra flere tjenester og bruger intelligens til at kombinere dem i hændelser og beskeder. Få mere at vide om, hvordan du minimerer tiden mellem en hændelse og dens administration for efterfølgende svar og løsning. <p> 27 min- 6 enheder |

> [!div class="nextstepaction"]
> [Start >](/learn/modules/defender-investigate-incidents/)

## <a name="next-steps"></a>Næste trin

Brug de angivne trin baseret på dit oplevelsesniveau eller din rolle på sikkerhedsteamet.

### <a name="experience-level"></a>Oplevelsesniveau

Følg denne tabel for at få oplysninger om dit erfaringsniveau med sikkerhedsanalyse og hændelsesrespons.

| Niveau | Trin |
|:-------|:-----|
| **Ny** | <ol><li> Se [gennemgangen](first-incident-overview.md) Svar på din første hændelse for at få en rundvisning i en typisk analyse-, afhjælpnings- og efterfølgende gennemgang i Microsoft 365 Defender-portalen med et eksempelangreb. </li><li> Se, hvilke hændelser der [skal prioriteres ud](incident-queue.md) fra alvorsgrad og andre faktorer. </li><li> [Administrer hændelser,](manage-incidents.md) som omfatter omdøbning, tildeling, klassificering og tilføjelse af mærker og kommentarer baseret på arbejdsprocessen for hændelsesstyring.</li></ol> |
| **Erfaren** | <ol><li> Kom i gang med hændelseskøen **fra siden** Hændelser på Microsoft 365 Defender-portalen. Herfra kan du gøre følgende: </li> <ul><li> Se, hvilke hændelser der [skal prioriteres ud](incident-queue.md) fra alvorsgrad og andre faktorer. </li><li> [Administrer hændelser,](manage-incidents.md) som omfatter omdøbning, tildeling, klassificering og tilføjelse af mærker og kommentarer baseret på arbejdsprocessen for hændelsesstyring. </li><li> Udfør [undersøgelser](investigate-incidents.md) af hændelser. </li></ul> </li><li> Hold styr på og svar på nye trusler med [trusselsanalyse](threat-analytics.md). </li><li>  Proaktivt på jagt efter trusler med [avanceret trusselssøgning](advanced-hunting-overview.md). </li><li> Se disse [playbooks for hændelsesrespons](/security/compass/incident-response-playbooks) for at få detaljeret vejledning til phishing, adgangskoder og appsamtykke til at tildele angreb. </li></ol> |


### <a name="security-team-role"></a>Sikkerhedsteamrolle

Følg denne tabel baseret på din sikkerhedsteamrolle.

| Rolle | Trin |
|:-------|:-----|
| Hændelses responder (niveau 1) | Kom i gang med hændelseskøen **fra siden** Hændelser på Microsoft 365 Defender-portalen. Herfra kan du gøre følgende: <ul><li> Se, hvilke hændelser der [skal prioriteres ud](incident-queue.md) fra alvorsgrad og andre faktorer. </li><li> [Administrer hændelser,](manage-incidents.md) som omfatter omdøbning, tildeling, klassificering og tilføjelse af mærker og kommentarer baseret på arbejdsprocessen for hændelsesstyring. </li></ul> |
| Sikkerhedsanalytiker eller analytiker (niveau 2) | <ol><li> Udfør [undersøgelser](investigate-incidents.md) af hændelser fra **siden Hændelser** på Microsoft 365 Defender-portalen. </li><li> Se disse [playbooks for hændelsesrespons](/security/compass/incident-response-playbooks) for at få detaljeret vejledning til phishing, adgangskoder og appsamtykke til at tildele angreb. </li></ol> |
| Avanceret sikkerhedsanalytiker eller trusselsekspert (Niveau 3) | <ol><li>Udfør [undersøgelser](investigate-incidents.md) af hændelser fra **siden Hændelser** på Microsoft 365 Defender-portalen. </li><li> Hold styr på og svar på nye trusler med [trusselsanalyse](threat-analytics.md). </li><li> Proaktivt på jagt efter trusler med [avanceret trusselssøgning](advanced-hunting-overview.md). </li><li> Se disse [playbooks for hændelsesrespons](/security/compass/incident-response-playbooks) for at få detaljeret vejledning til phishing, adgangskoder og appsamtykke til at tildele angreb. |
| SOC-manager | Se, hvordan [du Microsoft 365 Defender integreret i dit Security Operations Center (SOC)](integrate-microsoft-365-defender-secops.md). |

