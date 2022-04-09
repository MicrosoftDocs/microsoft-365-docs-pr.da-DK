---
title: Svar på hændelse med Microsoft 365 Defender
description: Undersøg hændelser på tværs af enheder, brugere og postkasser på Microsoft 365 Defender portalen.
keywords: hændelser, beskeder, undersøge, analysere, svar, korrelation, angreb, maskiner, enheder, brugere, identitet, identitet, postkasse, mail, 365, microsoft, m365, svar på hændelser, cyberangreb
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
ms.openlocfilehash: 70f75fd5986a5d837e33b3caf0b7cb23239ddce5
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731586"
---
# <a name="incident-response-with-microsoft-365-defender"></a>Svar på hændelse med Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

En hændelse i Microsoft 365 Defender er en samling af korrelerede beskeder og tilknyttede data, der udgør historien om et angreb.

Microsoft 365 tjenester og apps opretter beskeder, når de registrerer en mistænkelig eller skadelig hændelse eller aktivitet. Individuelle beskeder giver værdifulde fingerpeg om et fuldført eller igangværende angreb. Angreb anvender dog typisk forskellige teknikker mod forskellige typer enheder, f.eks. enheder, brugere og postkasser. Resultatet er flere beskeder for flere enheder i din lejer.

Da det kan være udfordrende og tidskrævende at samle de enkelte beskeder for at få indsigt i et angreb, Microsoft 365 Defender samler automatisk beskederne og deres tilknyttede oplysninger i en hændelse.

:::image type="content" source="../../media/incidents-overview/incidents.png" alt-text="Sådan korrelerer Microsoft 365 Defender hændelser fra enheder til en hændelse." lightbox="../../media/incidents-overview/incidents.png":::

Se denne korte oversigt over hændelser i Microsoft 365 Defender (4 minutter).

<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Hvis du grupperer relaterede beskeder i en hændelse, får du en omfattende visning af et angreb. Du kan f.eks. se:

- Hvor angrebet startede.
- Hvilken taktik blev brugt.
- Hvor langt angrebet er gået ind i din lejer.
- Omfanget af angrebet, f.eks. hvor mange enheder, brugere og postkasser der blev påvirket.
- Alle de data, der er knyttet til angrebet.

Hvis [indstillingen er aktiveret](m365d-enable.md), kan Microsoft 365 Defender [automatisk undersøge og løse](m365d-autoir.md) beskeder via automatisering og kunstig intelligens. Du kan også udføre yderligere afhjælpningstrin for at løse angrebet.

## <a name="incidents-and-alerts-in-the-microsoft-365-defender-portal"></a>Hændelser og beskeder på Microsoft 365 Defender-portalen

Du kan administrere hændelser fra **hændelser & beskeder > Hændelser** på hurtig start af <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>. Her er et eksempel.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Siden Hændelser på portalen Microsoft 365 Defender." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

Hvis du vælger et hændelsesnavn, vises en oversigt over hændelsen, og du får adgang til faner med yderligere oplysninger. Her er et eksempel.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Oversigtssiden for en hændelse på Microsoft 365 Defender-portalen" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

De ekstra faner for en hændelse er:

- Beskeder

  Alle de beskeder, der er relateret til hændelsen og deres oplysninger.

- Enheder

  Alle de enheder, der er blevet identificeret til at være en del af eller relateret til hændelsen.

- Brugere

  Alle de brugere, der er blevet identificeret til at være en del af eller relateret til hændelsen.

- Postkasser

  Alle de postkasser, der er blevet identificeret til at være en del af eller relateret til hændelsen.

- Undersøgelser

  Alle de [automatiserede undersøgelser, der udløses](m365d-autoir.md) af beskeder i hændelsen.

- Beviser og svar

  Alle understøttede hændelser og mistænkelige enheder i beskederne om hændelsen.

- Graph (eksempelvisning)

  En visuel repræsentation af angrebet, der forbinder de forskellige mistænkelige enheder, der er en del af angrebet, med deres relaterede aktiver, f.eks. brugere, enheder og postkasser.

Her er relationen mellem en hændelse og dens data og fanerne for en hændelse på Microsoft 365 Defender portalen.

:::image type="content" source="../../media/incidents-overview/incidents-security-center.png" alt-text="Relationen mellem en hændelse og dens data til fanerne for en hændelse på Microsoft 365 Defender portalen." lightbox="../../media/incidents-overview/incidents-security-center.png":::

## <a name="example-incident-response-workflow-for-microsoft-365-defender"></a>Eksempel på arbejdsproces for svar på hændelser for Microsoft 365 Defender

Her er et eksempel på en arbejdsproces til besvarelse af hændelser i Microsoft 365 med Microsoft 365 Defender-portalen.

:::image type="content" source="../../media/incidents-overview/incidents-example-workflow.png" alt-text="Et eksempel på en arbejdsproces for svar på hændelser for Microsoft 365 Defender-portalen." lightbox="../../media/incidents-overview/incidents-example-workflow.png":::

Identificer løbende de højeste prioritetshændelser til analyse og løsning i hændelseskøen, og gør dem klar til svar. Dette er en kombination af:

- [Sortering](incident-queue.md) for at bestemme de højeste prioritetshændelser via filtrering og sortering af hændelseskøen.
- [Administration af](manage-incidents.md) hændelser ved at ændre deres titel, tildele dem til en analytiker og tilføje mærker og kommentarer.

Overvej disse trin for din egen arbejdsproces for svar på hændelser:

1. Start en [undersøgelse og analyse af angreb og advarsler](investigate-incidents.md) for hver hændelse:

   1. Få vist en oversigt over hændelsen for at forstå dens omfang og alvorsgrad, og hvilke enheder der påvirkes med fanerne **Oversigt** og **Graph** (prøveversion).

   1. Begynd at analysere beskederne for at forstå deres oprindelse, omfang og alvorsgrad med fanen **Beskeder** .

   1. Indsaml oplysninger om påvirkede enheder, brugere og postkasser efter behov med fanerne **Enheder**, **Brugere** og **Postkasser** .

   1. Se, hvordan Microsoft 365 Defender [automatisk har løst nogle beskeder](m365d-autoir.md) under fanen **Undersøgelser**.

   1. Brug oplysninger i datasættet for hændelsen efter behov for at få flere oplysninger under fanen **Beviser og svar** .

2. Udfør indeslutning efter eller under din analyse for at reducere eventuelle yderligere konsekvenser af angrebet og udryddelsen af sikkerhedstruslen.

3. Så meget som muligt kan du gendanne efter angrebet ved at gendanne dine lejerressourcer til den tilstand, de var i før hændelsen.

4. [Løs](manage-incidents.md#resolve-an-incident) hændelsen, og brug tid på læring efter hændelser til:

   - Forstå typen af angrebet og dets indvirkning.
   - Undersøg angrebet i [Threat Analytics](threat-analytics.md) og sikkerheds community'et for at se en tendens til sikkerhedsangreb.
   - Tilbagekald den arbejdsproces, du brugte til at løse hændelsen, og opdater dine standardarbejdsprocesser, -processer, -politikker og -playbooks efter behov.
   - Find ud af, om der er behov for ændringer i sikkerhedskonfigurationen, og implementer dem.

Hvis du ikke kender til sikkerhedsanalyser, kan du se [introduktionen til at besvare din første hændelse for at](incidents-overview.md) få flere oplysninger og gennemgå en eksempelhændelse.

Du kan få flere oplysninger om svar på hændelser på tværs af Microsoft-produkter i [denne artikel](/security/compass/incident-response-overview).

## <a name="example-security-operations-for-microsoft-365-defender"></a>Eksempel på sikkerhedshandlinger for Microsoft 365 Defender

Her er et eksempel på sikkerhedshandlinger (SecOps) for Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-example-operations.png" alt-text="Et eksempel på sikkerhedshandlinger for Microsoft 365 Defender" lightbox="../../media/incidents-overview/incidents-example-operations.png":::

Daglige opgaver kan omfatte:

- [Administration af](manage-incidents.md) hændelser
- Gennemgå [air-handlinger (automatiseret undersøgelse og svar)](m365d-action-center.md) i Løsningscenter
- Gennemgang af den seneste [Threat Analytics](threat-analytics.md)
- [Svar på](investigate-incidents.md) hændelser

Månedlige opgaver kan omfatte:

- Gennemse [AIR-indstillinger](m365d-configure-auto-investigation-response.md)
- Gennemgang af [Secure Score](microsoft-secure-score-improvement-actions.md) og [Threat & Sårbarhedsstyring](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Rapportering til din it-sikkerhedsadministrationskæde

Kvartalsvise opgaver kan omfatte en rapport og orientering om sikkerhedsresultater til CISO (Chief Information Security Officer).

Årlige opgaver kan omfatte udførelse af en større hændelse eller sikkerhedsbrudsøvelse for at teste dine medarbejdere, systemer og processer.

Daglige, månedlige, kvartalsvise og årlige opgaver kan bruges til at opdatere eller afgrænse processer, politikker og sikkerhedskonfigurationer.

Se [Integration af Microsoft 365 Defender i dine sikkerhedshandlinger](integrate-microsoft-365-defender-secops.md) for at få flere oplysninger.

### <a name="secops-resources-across-microsoft-products"></a>SecOps-ressourcer på tværs af Microsoft-produkter

Du kan få flere oplysninger om SecOps på tværs af Microsofts produkter i disse ressourcer:

- [Kapaciteter](/security/compass/security-operations-capabilities)
- [Best practices](/security/compass/security-operations)
- [Videoer og slides](/security/compass/security-operations-videos-and-decks)

## <a name="get-incident-notifications-by-email"></a>Få meddelelser om hændelser via mail

Du kan konfigurere Microsoft 365 Defender til at give dine medarbejdere besked med en mail om nye hændelser eller opdateringer til eksisterende hændelser. Du kan vælge at få meddelelser baseret på:

- Hændelses alvorsgrad.
- Enhedsgruppe.
- Kun ved den første opdatering pr. hændelse.

Mailmeddelelsen indeholder vigtige oplysninger om hændelsen, f.eks. hændelsesnavn, alvorsgrad og kategorier. Du kan også gå direkte til hændelsen og starte din analyse med det samme. Du kan få flere oplysninger under [Undersøg hændelser](investigate-incidents.md).

Du kan tilføje eller fjerne modtagere i mailmeddelelserne. Nye modtagere får besked om hændelser, når de er tilføjet.

> [!NOTE]
> Du skal have tilladelse til at **administrere sikkerhedsindstillinger** for at konfigurere indstillinger for mailbeskeder. Hvis du har valgt at bruge grundlæggende administration af tilladelser, kan brugere med rollerne Sikkerhedsadministrator eller Global administrator konfigurere mailmeddelelser. <br> <br>
På samme måde kan du, hvis din organisation bruger rollebaseret adgangskontrol, kun oprette, redigere, slette og modtage meddelelser baseret på enhedsgrupper, som du har tilladelse til at administrere.

### <a name="create-a-rule-for-email-notifications"></a>Opret en regel for mailmeddelelser

Følg disse trin for at oprette en ny regel og tilpasse indstillingerne for mailmeddelelser.

1. Vælg **Indstillinger > Microsoft 365 Defender > Meddelelser via mail om hændelse i** navigationsruden.
2. Vælg **Tilføj element**.
3. Skriv navnet på reglen og en beskrivelse på siden **Grundlæggende** , og vælg derefter **Næste**.
4. Konfigurer på siden **Meddelelsesindstillinger** :
    - **Alvorsgrad af besked** – Vælg de beskeder, der udløser en hændelsesmeddelelse. Hvis du f.eks. kun vil have besked om hændelser med høj alvorsgrad, skal du vælge **Høj**.
    - **Område for enhedsgruppe** – Du kan angive alle enhedsgrupper eller vælge på listen over enhedsgrupper i din lejer.
    - **Giv kun besked ved første forekomst pr. hændelse** – Vælg, hvis du kun vil have en meddelelse for den første besked, der svarer til dine andre valg. Senere opdateringer eller beskeder, der er relateret til hændelsen, sender ikke yderligere meddelelser.
    - **Medtag organisationsnavn i mailen** – Vælg, om organisationens navn skal vises i mailmeddelelsen.
    - **Medtag lejerspecifikt portallink** – Vælg, om du vil tilføje et link med lejer-id'et i mailmeddelelsen for at få adgang til en bestemt Microsoft 365 lejer.

    :::image type="content" source="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png" alt-text="Siden Meddelelsesindstillinger for meddelelser om hændelsesmail på Microsoft 365 Defender-portalen." lightbox="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png":::

5. Vælg **Næste**. På siden **Modtagere** skal du tilføje de mailadresser, der skal modtage hændelsesmeddelelserne. Vælg **Tilføj** efter at have skrevet hver ny mailadresse. Hvis du vil teste meddelelser og sikre, at modtagerne modtager dem i indbakkerne, skal du vælge **Send testmail**.
6. Vælg **Næste**. Gennemse indstillingerne for reglen på siden **Gennemse regel** , og vælg derefter **Opret regel**. Modtagerne begynder at modtage hændelsesmeddelelser via mail baseret på indstillingerne.

Hvis du vil redigere en eksisterende regel, skal du vælge den på listen over regler. I ruden med regelnavnet skal du vælge **Rediger regel** og foretage dine ændringer på siderne **Grundlæggende**, **Meddelelsesindstillinger** og **Modtagere** .

Hvis du vil slette en regel, skal du vælge den på listen over regler. Vælg **Slet** i ruden med regelnavnet.

## <a name="training-for-security-analysts"></a>Oplæring af sikkerhedsanalytikere

Brug dette læringsmodul fra Microsoft Learn til at forstå, hvordan du bruger Microsoft 365 Defender til at administrere hændelser og beskeder.

|Uddannelse:|Undersøg hændelser med Microsoft 365 Defender|
|---|---|
|![Undersøg hændelser med Microsoft 365 Defender træningsikon.](../../media/incidents-overview/m365-defender-address-security-investigation.svg)| Microsoft 365 Defender samler trusselsdata fra flere tjenester og bruger KUNSTIG intelligens til at kombinere dem i hændelser og beskeder. Få mere at vide om, hvordan du minimerer tiden mellem en hændelse og dens administration for efterfølgende svar og løsning. <p> 27 min. - 6 enheder |

> [!div class="nextstepaction"]
> [Start >](/learn/modules/defender-investigate-incidents/)

## <a name="next-steps"></a>Næste trin

Brug de angivne trin baseret på dit erfaringsniveau eller din rolle i dit sikkerhedsteam.

### <a name="experience-level"></a>Oplevelsesniveau

Følg denne tabel for at få din erfaring med sikkerhedsanalyse og svar på hændelser.

| Niveau | Trin |
|:-------|:-----|
| **Nye** | <ol><li> Se [gennemgangen Besvar din første hændelse](first-incident-overview.md) for at få en guidet præsentation af en typisk proces med analyse, afhjælpning og gennemgang efter hændelser på Microsoft 365 Defender portalen med et eksempel på et angreb. </li><li> Se, hvilke hændelser der skal [prioriteres](incident-queue.md) baseret på alvorsgrad og andre faktorer. </li><li> [Administrer hændelser](manage-incidents.md), som omfatter omdøbning, tildeling, klassificering og tilføjelse af mærker og kommentarer baseret på arbejdsprocessen for administration af hændelser.</li></ol> |
| **Erfarne** | <ol><li> Kom i gang med hændelseskøen fra siden **Hændelser** på Microsoft 365 Defender portalen. Herfra kan du: </li> <ul><li> Se, hvilke hændelser der skal [prioriteres](incident-queue.md) baseret på alvorsgrad og andre faktorer. </li><li> [Administrer hændelser](manage-incidents.md), som omfatter omdøbning, tildeling, klassificering og tilføjelse af mærker og kommentarer baseret på arbejdsprocessen for administration af hændelser. </li><li> Udfør [undersøgelser](investigate-incidents.md) af hændelser. </li></ul> </li><li> Spor og reager på nye trusler med [trusselsanalyser](threat-analytics.md). </li><li>  Proaktivt jagt efter trusler med [avanceret trusselsjagt](advanced-hunting-overview.md). </li><li> Se disse [strategibøger for svar på hændelser](/security/compass/incident-response-playbooks) for at få en detaljeret vejledning i phishing, adgangskodespray og appsamtykketilmeldingsangreb. </li></ol> |

### <a name="security-team-role"></a>Rolle i sikkerhedsteam

Følg denne tabel baseret på din rolle i sikkerhedsteamet.

| Rolle | Trin |
|---|---|
| Hændelsesreager (niveau 1) | Kom i gang med hændelseskøen fra siden **Hændelser** på Microsoft 365 Defender portalen. Herfra kan du: <ul><li> Se, hvilke hændelser der skal [prioriteres](incident-queue.md) baseret på alvorsgrad og andre faktorer. </li><li> [Administrer hændelser](manage-incidents.md), som omfatter omdøbning, tildeling, klassificering og tilføjelse af mærker og kommentarer baseret på arbejdsprocessen for administration af hændelser. </li></ul> |
| Sikkerhedsefterforsker eller -analytiker (niveau 2) | <ol><li> Udfør [undersøgelser](investigate-incidents.md) af hændelser fra siden **Hændelser** på portalen Microsoft 365 Defender. </li><li> Se disse [strategibøger for svar på hændelser](/security/compass/incident-response-playbooks) for at få en detaljeret vejledning i phishing, adgangskodespray og appsamtykketilmeldingsangreb. </li></ol> |
| Avanceret sikkerhedsanalytiker eller trusselsjæger (niveau 3) | <ol><li>Udfør [undersøgelser](investigate-incidents.md) af hændelser fra siden **Hændelser** på portalen Microsoft 365 Defender. </li><li> Spor og reager på nye trusler med [trusselsanalyser](threat-analytics.md). </li><li> Proaktivt jagt efter trusler med [avanceret trusselsjagt](advanced-hunting-overview.md). </li><li> Se disse [strategibøger for svar på hændelser](/security/compass/incident-response-playbooks) for at få en detaljeret vejledning i phishing, adgangskodespray og appsamtykketilmeldingsangreb. |
| SOC-leder | Se, hvordan [du integrerer Microsoft 365 Defender i SOC (Security Operations Center).](integrate-microsoft-365-defender-secops.md) |
