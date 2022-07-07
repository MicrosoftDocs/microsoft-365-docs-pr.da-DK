---
title: Undersøg underretninger i Microsoft 365 Defender
description: Undersøg beskeder, der vises på tværs af enheder, brugere og postkasser.
keywords: hændelser, beskeder, undersøge, analysere, svar, korrelation, angreb, maskiner, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365
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
ms.technology: m365d
ms.openlocfilehash: b0c9e5793ec0ffc97cbbac0308a7e362da279e1b
ms.sourcegitcommit: 5014666778b2d48912c68c2e06992cdb43cfaee3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/07/2022
ms.locfileid: "66663585"
---
# <a name="investigate-alerts-in-microsoft-365-defender"></a>Undersøg underretninger i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

>[!Note]
>I denne artikel beskrives sikkerhedsbeskeder i Microsoft 365 Defender. Du kan dog bruge aktivitetsbeskeder til at sende mailmeddelelser til dig selv eller andre administratorer, når brugerne udfører bestemte aktiviteter i Microsoft 365. Du kan få flere oplysninger under [Opret aktivitetsbeskeder – Microsoft Purview-| Microsoft Docs](../../compliance/create-activity-alerts.md).

Beskeder er grundlaget for alle hændelser og angiver forekomsten af skadelige eller mistænkelige hændelser i dit miljø. Beskeder er typisk en del af et bredere angreb og giver fingerpeg om en hændelse.

I Microsoft 365 Defender samles relaterede beskeder for at danne [hændelser](incidents-overview.md). Hændelser vil altid give den bredere kontekst for et angreb, men analyse af beskeder kan være værdifuld, når en dybere analyse er påkrævet.

**Køen Beskeder** viser det aktuelle sæt beskeder. Du kommer til beskedkøen fra **Hændelser & beskeder > Beskeder** på hurtig start af [portalen Microsoft 365 Defender](https://go.microsoft.com/fwlink/p/?linkid=2077139).

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-queue.png" alt-text="Sektionen Beskeder på Microsoft 365 Defender-portalen" lightbox="../../media/investigate-alerts/alerts-ss-alerts-queue.png":::

Beskeder fra forskellige Microsoft-sikkerhedsløsninger, f.eks. Microsoft Defender for Endpoint, Microsoft Defender for Office 365 og Microsoft 365 Defender vises her.

Som standard viser beskedkøen på Microsoft 365 Defender-portalen de nye og igangværende beskeder fra de seneste 30 dage. Den seneste besked er øverst på listen, så du kan se den først. 

Fra standardkøen for beskeder kan du vælge **Filter** for at få vist ruden **Filter** , hvorfra du kan angive et undersæt af beskederne. Her er et eksempel.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-filter.png" alt-text="Afsnittet Filtre på Microsoft 365 Defender-portalen." lightbox="../../media/investigate-alerts/alerts-ss-alerts-filter.png":::

Du kan filtrere beskeder i henhold til disse kriterier:

- Sværhedsgraden
- Status
- Tjenestekilder
- Enheder (de påvirkede aktiver)
- Automatiseret undersøgelsestilstand

## <a name="required-roles-for-defender-for-office-365-alerts"></a>Påkrævede roller for Defender for Office 365 beskeder

Du skal have en af følgende roller for at få adgang til Microsoft Defender for Office 365 beskeder:

- For globale Azure Active Directory-roller (Azure AD):

   - Global administrator

   - Sikkerhedsadministrator

   - Sikkerhedsoperator

   - Global læser

   - Sikkerhedslæser

- Office 365 rollegrupper for sikkerhed & overholdelse

   - Administrator for overholdelse af angivne standarder

   - Organisationsadministration 

- En [brugerdefineret rolle](custom-roles.md)

## <a name="analyze-an-alert"></a>Analysér en besked

Hvis du vil se hovedbeskedsiden, skal du vælge navnet på beskeden. Her er et eksempel.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-main.png" alt-text="Oplysningerne om en besked på Microsoft 365 Defender-portalen" lightbox="../../media/investigate-alerts/alerts-ss-alerts-main.png":::

Du kan også vælge handlingen **Åbn hovedbeskedsiden** i ruden **Administrer besked** .

En beskedside består af disse afsnit: 

- Beskedhistorie, som er den kæde af hændelser og beskeder, der er relateret til denne besked i kronologisk rækkefølge
- Oversigtsoplysninger

På hele en beskedside kan du vælge ellipsen (**...**) ud for en hvilken som helst enhed for at se tilgængelige handlinger, f.eks. linke beskeden til en anden hændelse. Listen over tilgængelige handlinger afhænger af typen af besked.

### <a name="alert-sources"></a>Beskedkilder

Microsoft 365 Defender beskeder kan komme fra løsninger som Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps og tilføjelsesprogrammet appstyring til Microsoft Defender for Cloud Apps. Du vil muligvis bemærke beskeder med forudberedte tegn i beskeden. Følgende tabel indeholder en vejledning til at hjælpe dig med at forstå tilknytningen af beskedkilder baseret på det forberedte tegn i beskeden.

> [!NOTE]
> - Guid'erne for forberedelse er kun specifikke for samlede oplevelser, f.eks. unified alerts queue, unified alerts page, unified investigation og unified incident.
> - Det forberedte tegn ændrer ikke guid'et for beskeden. Den eneste ændring af GUID'et er den forudforberedte komponent.

| Beskedkilde | Forberedt tegn |
| :---|:--- |
| Microsoft Defender for Office 365 | `fa{GUID}` <br> Eksempel: `fa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender for Endpoint | `da` eller `ed` for beskeder om brugerdefineret registrering <br> |
| Microsoft Defender for Identity | `aa{GUID}` <br> Eksempel: `aa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender for Cloud Apps |`ca{GUID}` <br> Eksempel: `ca123a456b-c789-1d2e-12f1g33h445h6i` |

### <a name="analyze-affected-assets"></a>Analysér berørte aktiver

Afsnittet **Udførte handlinger** indeholder en liste over påvirkede aktiver, f.eks. postkasser, enheder og brugere, der påvirkes af denne besked. 

Du kan også vælge **Vis i Handlingscenter** for at få vist fanen **Oversigt** i **Løsningscenter** på Microsoft 365 Defender portalen. 

### <a name="trace-an-alerts-role-in-the-alert-story"></a>Spor en beskeds rolle i beskedhistorien

Beskedhistorien viser alle aktiver eller enheder, der er relateret til beskeden, i en procestrævisning. Beskeden i titlen er i fokus, første gang du lander på den valgte beskeds side. Aktiver i beskedhistorien kan udvides, og der kan klikkes på dem. De giver yderligere oplysninger og fremskynder dit svar ved at give dig mulighed for at handle direkte i forbindelse med beskedsiden. 

> [!NOTE]
> Afsnittet med beskedhistorien kan indeholde mere end én besked, hvor yderligere beskeder, der er relateret til det samme udførelsestræ, vises før eller efter den besked, du har valgt.

### <a name="view-more-alert-information-on-the-details-page"></a>Få vist flere beskedoplysninger på detaljesiden

Detaljesiden viser detaljerne for den valgte besked med oplysninger og handlinger, der er relateret til den. Hvis du vælger et af de berørte aktiver eller objekter i beskedhistorien, ændres detaljesiden for at angive kontekstafhængige oplysninger og handlinger for det valgte objekt.

Når du har valgt et objekt af interesse, ændres detaljesiden, så der vises oplysninger om den valgte objekttype, historikoplysninger, når den er tilgængelig, og indstillinger, der kan udføres på denne enhed direkte fra beskedsiden.

## <a name="manage-alerts"></a>Administrer beskeder

Hvis du vil administrere en besked, skal du vælge **Administrer besked** i sektionen med oversigtsoplysninger på beskedsiden. For en enkelt besked er her et eksempel på ruden **Administrer besked** .

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage.png" alt-text="Afsnittet Administrer besked på Microsoft 365 Defender-portalen" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage.png":::

Ruden **Administrer beskeder** giver dig mulighed for at få vist eller angive:

- Beskedstatus (Ny, Løst, Igangværende).
- Den brugerkonto, der er tildelt beskeden.
- Klassificeringen af beskeden:

   - **Ikke angivet** (standard).

   - **Sand positiv** med en form for trussel. Brug denne klassificering til beskeder, der nøjagtigt angiver en reel trussel. Angivelse af trusselstypen hjælper dit sikkerhedsteam med at se trusselsmønstre og reagere for at forsvare din organisation mod dem.

   - **Oplysende, forventet aktivitet** med en aktivitetstype. Brug indstillingerne i denne kategori til at klassificere beskeder om sikkerhedstests, rød teamaktivitet og forventet usædvanlig adfærd fra apps og brugere, der er tillid til.

   - **Falsk positiv** for typer af beskeder, der blev oprettet, selvom der ikke er nogen skadelig aktivitet. Hvis du klassificerer beskeder som falske positive, hjælper det Microsoft 365 Defender med at forbedre registreringskvaliteten.

- En kommentar til beskeden.

> [!NOTE]
> En måde at administrere beskeder på ved hjælp af mærker. Mærkningsfunktionen for Microsoft Defender for Office 365 udrulles trinvist og er i øjeblikket en prøveversion. <br>
> I øjeblikket anvendes ændrede kodenavne kun på beskeder, der er oprettet *efter* opdateringen. Beskeder, der blev genereret før ændringen, afspejler ikke det opdaterede kodenavn. 

Hvis du vil administrere et *sæt beskeder, der ligner en bestemt besked*, skal du vælge **Få vist lignende beskeder** i feltet **INSIGHT** i afsnittet med oversigtsoplysninger på beskedsiden.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" alt-text="Administrer en besked på Microsoft 365 Defender-portalen":::

I ruden **Administrer beskeder** kan du derefter klassificere alle relaterede beskeder på samme tid. Her er et eksempel.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" alt-text="Administration af relaterede beskeder på Microsoft 365 Defender-portalen":::

Hvis lignende beskeder allerede tidligere er klassificeret, kan du spare tid ved at bruge Microsoft 365 Defender anbefalinger for at få mere at vide om, hvordan de andre beskeder blev løst. Vælg **Anbefalinger** i afsnittet med oversigtsoplysninger.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" alt-text="Eksempel på valg af anbefalinger til en besked":::

Fanen **Anbefalinger** indeholder næste trins handlinger og råd til undersøgelse, afhjælpning og forebyggelse. Her er et eksempel.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" alt-text="Eksempel på anbefalinger til beskeder":::

 
## <a name="suppress-an-alert"></a>Skjul en besked

Som SOC-analytiker (Security Operations Center) er et af de største problemer at triaging det eneste antal beskeder, der udløses dagligt. I forbindelse med beskeder med lavere prioritet skal en analytiker stadig prioritere og løse den besked, der normalt er en manuel proces. En SOC-analytikers tid er værdifuld og vil kun fokusere på vigtige beskeder med høj alvorsgrad og høj prioritet.

Undertrykkelse af beskeder giver mulighed for at justere og administrere beskeder på forhånd. Dette strømliner beskedkøen og sparer triagetid ved at skjule eller løse beskeder automatisk, hver gang der opstår en bestemt forventet organisationsfunktionsmåde, og regelbetingelserne er opfyldt. 

Du kan oprette regelbetingelser baseret på "bevistyper", f.eks. filer, processer, planlagte opgaver og mange andre bevistyper, der udløser beskeden. Når du har oprettet reglen, kan brugeren anvende reglen på den valgte besked eller en hvilken som helst beskedtype, der opfylder regelbetingelserne, for at undertrykke beskeden. 

> [!NOTE]
> Det anbefales ikke at undertrykke beskeder. I visse situationer udløser et kendt internt virksomhedsprogram eller sikkerhedstest dog en forventet aktivitet, og du vil ikke se disse beskeder. Så du kan oprette en undertrykkelsesregel for beskeden. 

### <a name="create-rule-conditions-to-suppress-alerts"></a>Opret regelbetingelser for at undertrykke beskeder

Sådan opretter du en regel for undertrykkelse for beskeder:

1. Vælg den undersøgte besked. På hovedbeskedsiden skal du vælge **Opret regel for undertrykkelse** i afsnittet med oversigtsoplysninger på beskedsiden. 

    :::image type="content" source="../../media/investigate-alerts/suppression-click.png" lightbox="../../media/investigate-alerts/suppression-click.png" alt-text="Skærmbillede af handlingen Opret adskillelsesregel.":::

2. I ruden **Opret regel for undertrykkelse** skal du **kun vælge denne beskedtype** for at anvende reglen på den valgte besked.

    Hvis du vil anvende reglen på en hvilken som helst beskedtype, der opfylder regelbetingelserne, skal du dog vælge **En hvilken som helst beskedtype baseret på IOC-betingelser**.
 
    IOC'er er indikatorer som f.eks. filer, processer, planlagte opgaver og andre bevistyper, der udløser beskeden.
     
3. I afsnittet **IOC'er** skal du vælge **En hvilken som helst IOC** for at undertrykke beskeden, uanset hvad "beviser" har forårsaget beskeden. 

    Hvis du vil angive flere regelbetingelser, skal du vælge **Vælg IOCs**. Brug **AND**, **OR** og grupperingsindstillinger til at oprette relationer mellem disse flere "bevistyper", der forårsager beskeden.
 
    1. I afsnittet **Betingelser** skal du f.eks. vælge den udløsende **bevisenhedsrolle: Triggering**, **Equals** og vælge bevistypen på rullelisten. 

    :::image type="content" source="../../media/investigate-alerts/evidence-types-drop-down-list.png" alt-text="Skærmbillede af rullelisten Med bevistyper." lightbox="../../media/investigate-alerts/evidence-types-drop-down-list.png":::

    2. Alle egenskaberne for dette 'bevis' udfyldes automatisk som en ny undergruppe i de respektive felter nedenfor.
    :::image type="content" source="../../media/investigate-alerts/properties-evidence.png" alt-text="Skærmbillede af egenskaber for automatisk udfyldning af bevismateriale." lightbox="../../media/investigate-alerts/properties-evidence.png" :::

    > [!NOTE]
    > Der skelnes ikke mellem store og små bogstaver i betingelsesværdier. 

    3. Du kan redigere og/eller slette egenskaberne for dette bevis i henhold til dit krav (ved hjælp af jokertegn, når det understøttes).

    4. Andre end filer og processer, AMSI-script, WMI-hændelse og planlagte opgaver er nogle af de nyligt tilføjede bevistyper, som du kan vælge på rullelisten med bevistyper.
    :::image type="content" source="../../media/investigate-alerts/other-evidence-types.png" alt-text="Skærmbillede af andre typer beviser." lightbox="../../media/investigate-alerts/other-evidence-types.png":::

    5. Klik på **Tilføj filter** for at tilføje endnu en IOC. 
    > [!NOTE]
    > Hvis du vil føje mindst én IOC til regelbetingelsen, skal du undertrykke en hvilken som helst beskedtype.
    
4. Du kan også vælge **Udfyld automatisk alle beskeder 7 relaterede IOC'er** i afsnittet **IOC** for at tilføje alle beskedrelaterede bevistyper og deres egenskaber på én gang i afsnittet **Betingelser** .
    :::image type="content" source="../../media/investigate-alerts/autofill-iocs.png" alt-text="Skærmbillede af automatisk udfyldning af alle beskedrelaterede IOCs." lightbox="../../media/investigate-alerts/autofill-iocs.png":::

5. I afsnittet **Omfang** skal du angive omfanget i underafsnittet **Betingelser** ved at vælge en bestemt enhed, flere enheder, enhedsgrupper, hele organisationen eller efter bruger.
    > [!NOTE]
    > Du skal have Administration tilladelse, når **området** kun er angivet for **Bruger**. Administration tilladelse er ikke påkrævet, når **omfanget** er angivet for **Bruger** sammen med **enhed**, **enhedsgrupper**.

:::image type="content" source="../../media/investigate-alerts/suppression-choose-scope.png" lightbox="../../media/investigate-alerts/suppression-choose-scope.png" alt-text="Skærmbillede af ruden til oprettelse af undertrykkelsesregel: Betingelser, Omfang, Handling.":::
 
6. I afsnittet **Handling** skal du udføre den relevante handling af enten **Skjul besked** eller **Løs besked**.
    Angiv **Navn**, **Kommentar**, og klik på **Gem**.

7. **Undgå, at IOC'erne bliver blokeret i fremtiden:**<br>
Når du gemmer undertrykkelsesreglen, kan du på siden **Oprettelse af regel for vellykket undertrykkelse** , der vises, føje de valgte IOC'er som indikatorer til "listen over tilladte" og forhindre dem i at blive blokeret i fremtiden. <br>
Alle beskedrelaterede IOC'er vises på listen. <br>
IOCs, der blev valgt under undertrykkelsesbetingelserne, vælges som standard.
      1. Du kan f.eks. tilføje filer, der skal have tilladelse til at **vælge beviser (IOC), der skal tillades**. Som standard vælges den fil, der udløste beskeden.
      1. Angiv området i det **Vælg område, der skal anvendes på**. Som standard er området for den relaterede besked valgt.
      1. Klik på **Gem**. Nu er filen ikke blokeret, som den er på listen over tilladte.

    :::image type="content" source="../../media/investigate-alerts/suppression-2-choose-iocs.png" lightbox="../../media/investigate-alerts/suppression-2-choose-iocs.png" alt-text="Skærmbillede af vellykket oprettelse af regel for undertrykkelse. ":::

8.  Den nye funktionalitet til undertrykkelsesbeskeder er tilgængelig som standard. <br> Du kan dog skifte tilbage til den tidligere oplevelse i Microsoft 365 Defender portal ved at gå til **Indstillinger > Slutpunkter > Advarselsundertrykkelse** og derefter slå til/fra-knappen **Oprettelse af nye undertrykkelsesregler aktiveret**. 
 
    :::image type="content" source="../../media/investigate-alerts/suppression-toggle.png" lightbox="../../media/investigate-alerts/suppression-toggle.png" alt-text="Skærmbillede af til/fra-funktionen til at slå funktionen til oprettelse af undertrykkelsesregel til/fra.":::

9.  **Rediger eksisterende regler:** <br> Du kan altid tilføje eller ændre regelbetingelser og omfanget af nye eller eksisterende regler i Microsoft Defender-portalen ved at vælge den relevante regel og klikke på **Rediger regel**.    
    Hvis du vil redigere eksisterende regler, skal du sikre, at til/fra-knappen **Oprettelse af nye undertrykkelsesregler** er aktiveret.         

    :::image type="content" source="../../media/investigate-alerts/suppression-toggle-on-edit.png" lightbox="../../media/investigate-alerts/suppression-toggle-on-edit.png" alt-text="Skærmbillede af redigeringsregel for undertrykkelse.":::
  
## <a name="resolve-an-alert"></a>Løs en besked

Når du er færdig med at analysere en besked, og den kan løses, skal du gå til ruden **Administrer beskeder** for beskeden eller lignende beskeder og markere statussen som **Løst** og derefter klassificere den som en **Sand positiv** med en type trussel, en **oplysende, forventet aktivitet** med en aktivitetstype eller falsk **positiv**.

Klassificering af beskeder hjælper Microsoft 365 Defender med at forbedre registreringskvaliteten.

## <a name="use-power-automate-to-triage-alerts"></a>Brug Power Automate til at triage beskeder

SecOps-teams (Modern Security Operations) har brug for automatisering for at fungere effektivt. For at fokusere på jagt efter og undersøge reelle trusler bruger SecOps-teams Power Automate til at gennemgå listen over beskeder og fjerne dem, der ikke er trusler.  

### <a name="criteria-for-resolving-alerts"></a>Kriterier for løsning af beskeder

- Fraværende-meddelelse er slået til for brugeren

- Brugeren er ikke mærket som høj risiko

Hvis begge er sande, markerer SecOps beskeden som legitim rejse og løser den. Der sendes en meddelelse i Microsoft Teams, når beskeden er løst.

### <a name="connect-power-automate-to-microsoft-defender-for-cloud-apps"></a>Forbind Power Automate med Microsoft Defender for Cloud Apps

Hvis du vil oprette automatiseringen, skal du bruge et API-token, før du kan oprette forbindelse mellem Power Automate og Microsoft Defender for Cloud Apps.

1. Klik på **Indstillinger**, vælg **Sikkerhedsudvidelser**, og klik derefter på **Tilføj token** under fanen **API-tokens** .

2. Angiv et navn til dit token, og klik derefter på **Generér**. Gem tokenet, som du skal bruge det senere.

### <a name="create-an-automated-flow"></a>Opret et automatiseret flow

Se denne korte video for at få mere at vide om, hvordan automatisering fungerer effektivt for at oprette en problemfri arbejdsproces, og hvordan du opretter forbindelse mellem Power Automate og Defender for Cloud Apps. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn]

## <a name="next-steps"></a>Næste trin

Fortsæt [din undersøgelse](investigate-incidents.md) efter behov i forbindelse med igangværende hændelser.

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Administrer hændelser](manage-incidents.md)
- [Undersøg hændelser](investigate-incidents.md)
- [Undersøg datatabshændelser](investigate-dlp.md)