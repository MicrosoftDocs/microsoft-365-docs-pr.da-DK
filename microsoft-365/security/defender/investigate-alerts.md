---
title: Undersøg beskeder i Microsoft 365 Defender
description: Undersøg beskeder, der er set på tværs af enheder, brugere og postkasser.
keywords: hændelser, beskeder, undersøge, analysere, svare, korrelation, angreb, computere, enheder, brugere, identiteter, identitet, postkasse, mail, 365, microsoft, m365
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
ms.openlocfilehash: c09a3880a9f117d0ce5ce6e5edf3736192fc9c95
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499853"
---
# <a name="investigate-alerts-in-microsoft-365-defender"></a>Undersøg beskeder i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

>[!Note]
>I denne artikel beskrives sikkerhedsadvarsler i Microsoft 365 Defender. Du kan dog bruge aktivitetsbeskeder til at sende beskeder via mail til dig selv eller andre administratorer, når brugere udfører bestemte aktiviteter i Microsoft 365. Få mere at vide under [Opret aktivitetsbeskeder – Microsoft 365 overholdelse | Microsoft Docs](../../compliance/create-activity-alerts.md).

Beskeder er grundlaget for alle hændelser og angiver forekomsten af skadelige eller mistænkelige hændelser i dit miljø. Beskeder er typisk en del af et bredere angreb og giver fingerpeg om en hændelse.

I Microsoft 365 Defender sammenlægges relaterede beskeder for at danne [hændelser](incidents-overview.md). Hændelser vil altid give et bredere perspektiv på et angreb, men analyse af beskeder kan være værdifuld, når en dybere analyse er påkrævet.

**Køen Beskeder** viser det aktuelle sæt af beskeder. Du får adgang til køen med beskeder **fra & og > vigtige** beskeder, når den hurtige start af [Microsoft 365 Defender-portalen](https://go.microsoft.com/fwlink/p/?linkid=2077139).

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-queue.png" alt-text="Afsnittet Beskeder i Microsoft 365 Defender portal" lightbox="../../media/investigate-alerts/alerts-ss-alerts-queue.png":::

Beskeder fra forskellige Microsoft-sikkerhedsløsninger som f.Microsoft Defender for Endpoint, Microsoft Defender for Office 365 og Microsoft 365 Defender vises her.

Som standard viser køen til beskeder i Microsoft 365 Defender portal de nye og igangværende beskeder fra de seneste 30 dage. Den seneste besked er øverst på listen, så du kan se den først. 

Fra standardkøen til beskeder kan du vælge **Filtrer** for at få vist en **Filter-rude** , hvorfra du kan angive et undersæt af beskederne. Her er et eksempel.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-filter.png" alt-text="Sektionen Filtre i Microsoft 365 Defender portal." lightbox="../../media/investigate-alerts/alerts-ss-alerts-filter.png":::

Du kan filtrere beskeder efter disse kriterier:

- Alvorsgrad
- Status
- Tjenestekilder
- Enheder (de på påvirkede aktiver)
- Automatiseret undersøgelsestilstand

## <a name="required-roles-for-defender-for-office-365-alerts"></a>Påkrævede roller for Defender for Office 365 vigtige beskeder

Du skal have en af følgende roller for at få adgang til Microsoft Defender for Office 365 vigtige beskeder:

- For Azure Active Directory globale roller (Azure AD):

   - Global administrator

   - Sikkerhedsadministrator

   - Sikkerhedsoperator

   - Global læser

   - Sikkerhedslæser

- Office 365 sikkerheds- & rollegrupper for overholdelse af regler og standarder

   - Overholdelsesadministrator

   - Organisationsadministration 

- En [brugerdefineret rolle](custom-roles.md)

## <a name="analyze-an-alert"></a>Analysér en besked

Hvis du vil se den primære beskedside, skal du vælge navnet på beskeden. Her er et eksempel.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-main.png" alt-text="Oplysninger om en besked i Microsoft 365 Defender portal" lightbox="../../media/investigate-alerts/alerts-ss-alerts-main.png":::

Du kan også vælge handlingen **Åbn den primære beskedside** fra **ruden Administrer** besked.

En beskedside består af disse sektioner: 

- Beskedens historie, som er kæden af hændelser og beskeder, der er relateret til denne besked i kronologisk rækkefølge
- Oversigtsoplysninger

I hele siden med beskeder kan du vælge ellipserne (**...**) ud for en enhed for at få vist tilgængelige handlinger, f.eks. at sammenkæde beskeden med en anden hændelse. Listen over tilgængelige handlinger afhænger af beskedtypen.

### <a name="alert-sources"></a>Beskedkilder

Microsoft 365 Defender vigtige beskeder kan komme fra løsninger som f.Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps og tilføjelsesprogrammet appstyring til Microsoft Defender for Cloud Apps. Du bemærker muligvis beskeder med tegn, der allerede er blevet brug for, i beskeden. Den følgende tabel giver en vejledning til, hvordan du kan forstå tilknytningen af beskedkilder baseret på det foranstillede tegn i beskeden.

> [!NOTE]
> - De forhåndsinstallerede GUID'er er kun specifikke for samlede oplevelser som samlet kø for beskeder, samlet beskedside, samlet undersøgelse og samlet hændelse.
> - Det foranstillede tegn ændrer ikke GUID'et for beskeden. Den eneste ændring af GUID'et er den forhåndsinstallerede komponent.

| Advarselskilde | Forudindstillet tegn |
| :---|:--- |
| Microsoft Defender for Office 365 | `fa{GUID}` <br> Eksempel: `fa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender for Endpoint | `da` eller `ed` for brugerdefinerede registreringsbeskeder <br> |
| Microsoft Defender for Identity | `aa{GUID}` <br> Eksempel: `aa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender for Cloud Apps |`ca{GUID}` <br> Eksempel: `ca123a456b-c789-1d2e-12f1g33h445h6i` |

### <a name="analyze-affected-assets"></a>Analysér påvirkede aktiver

Afsnittet **Handlinger, der** er taget, har en liste over påvirkede aktiver, f.eks. postkasser, enheder og brugere, der er påvirket af denne besked. 

Du kan også vælge **Vis i handlingscenter** **for at få** vist fanen Oversigt **i handlingscenter** Microsoft 365 Defender portalen. 

### <a name="trace-an-alerts-role-in-the-alert-story"></a>Spore en beskeds rolle i påmindelseshistorien

Beskedenheden viser alle aktiver eller enheder, der er relateret til beskeden, i en procestrævisning. Beskeden i titlen er den, der er i fokus, når du første gang lander på din valgte beskeds side. Aktiver i beskedens tekstenhed kan udvides og klikkes på dem. De indeholder yderligere oplysninger og fremskynder dit svar, så du kan reagere direkte i konteksten af påmindelsessiden. 

> [!NOTE]
> Sektionen med besked tekstenhed kan indeholde mere end én besked, hvor flere vigtige beskeder om det samme eksekveringstræ vises før eller efter den besked, du har valgt.

### <a name="view-more-alert-information-on-the-details-page"></a>Få vist flere beskedoplysninger på detaljesiden

Detaljesiden viser detaljerne for den valgte besked med oplysninger og handlinger, der er relateret til den. Hvis du vælger nogen af de påvirkede aktiver eller enheder i beskedenheden, ændres detaljesiden for at give kontekstafhængige oplysninger og handlinger for det markerede objekt.

Når du har valgt en enhed af interesse, ændres detaljesiden for at vise oplysninger om den valgte enhedstype, historiske oplysninger, når den er tilgængelig, og muligheder for at handle på denne enhed direkte fra påmindelsessiden.

## <a name="manage-alerts"></a>Administrer beskeder

Hvis du vil administrere en besked, **skal du vælge** Administrer besked i sektionen med oversigtsoplysninger på påmindelsessiden. Her er et eksempel på ruden Administrer vigtige beskeder for **en enkelt besked** .

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage.png" alt-text="Afsnittet Administrer påmindelse i Microsoft 365 Defender portal" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage.png":::

I **ruden Administrer** besked kan du få vist eller angive:

- Beskedens status (Ny, Løst, I gang).
- Den brugerkonto, der har fået tildelt beskeden.
- Klassificeringen af beskeden:

   - **Ikke angivet** (standard).

   - **Sand positiv** med en type af trussel. Brug denne klassificering til beskeder, der præcist angiver en reel trussel. Hvis du angiver trusselstypen, kan dit sikkerhedsteam se trusselsmønstre og beskytte din organisation mod dem.

   - **Informationel, forventet aktivitet** med en type aktivitet. Brug indstillingerne i denne kategori til at klassificere beskeder om sikkerhedstests, røde teamaktiviteter og forventet usædvanlig adfærd fra apps og brugere, der er tillid til.

   - **Falsk positiv** for typer af beskeder, der blev oprettet, selvom der ikke er nogen ondsindet aktivitet. Klassificering af beskeder som falsk positiv hjælper dig med Microsoft 365 Defender forbedre registreringskvaliteten.

- En kommentar til beskeden.

> [!NOTE]
> En måde at administrere beskeder på via brug af mærker. Mærkningsfunktionaliteten for en Microsoft Defender for Office 365 rulles trinvist ud og er i øjeblikket i forhåndsvisning. <br>
> I øjeblikket anvendes ændrede kodenavne kun på beskeder, der er *oprettet* efter opdateringen. Beskeder, der blev oprettet før ændringen, afspejler ikke det opdaterede mærkenavn. 

Hvis du vil *administrere et sæt* vigtige beskeder, der ligner en bestemt besked, skal du vælge Vis lignende beskeder i feltet **INSIGHT** i sektionen med oversigtsoplysninger på beskedsiden.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" alt-text="Administrer en besked i Microsoft 365 Defender portalen":::

I **ruden Administrer** vigtige beskeder kan du derefter klassificere alle de relaterede beskeder på samme tid. Her er et eksempel.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" alt-text="Administrere relaterede beskeder i Microsoft 365 Defender portal":::

Hvis lignende beskeder allerede er blevet klassificeret tidligere, kan du spare tid ved at bruge anbefalinger Microsoft 365 Defender at lære, hvordan de andre beskeder blev løst. I sektionen Med oversigtsdetaljer skal du **vælge Anbefalinger**.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" alt-text="Eksempel på valg af anbefalinger til en besked":::

Fanen **Anbefalinger** indeholder de næste trin handlinger og råd til undersøgelse, afhjælpning og forebyggelse. Her er et eksempel.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" alt-text="Eksempel på anbefalinger til påmindelser":::

## <a name="resolve-an-alert"></a>Løs en besked

Når du er færdig med at analysere en besked, og den kan løses, skal du gå  til ruden Administrer påmindelse for beskeden eller lignende vigtige beskeder og markere status som Løst  og derefter klassificere den som Sand **positiv** med en type af trusler, en informationsaktivitet **med** en aktivitetstype eller en **falsk positiv**.

Klassificering af beskeder hjælper dig Microsoft 365 Defender at forbedre dens registreringskvalitet.

## <a name="use-power-automate-to-triage-alerts"></a>Brug Power Automate til at omdele beskeder

Moderne sikkerhedsteams (SecOps) skal bruge automatisering for at kunne fungere effektivt. Hvis du vil fokusere på at lede efter og undersøge reelle trusler, skal SecOps-teams bruge Power Automate til at gennemgå listen over vigtige beskeder og fjerne dem, der ikke er trusler.  

### <a name="criteria-for-resolving-alerts"></a>Kriterier for løsning af beskeder

- Bruger har Ikke til tilstede-meddelelse aktiveret

- Brugeren er ikke mærket som høj risiko

Hvis begge er sande, markerer SecOps beskeden som legitim rejse og løser den. Der sendes en meddelelse i Microsoft Teams, når beskeden er løst.

### <a name="connect-power-automate-to-microsoft-defender-for-cloud-apps"></a>Forbind Power Automate til Microsoft Defender for Cloud Apps

Hvis du vil oprette automatiseringen, skal du bruge et API-token, før du kan Power Automate til Microsoft Defender for Cloud Apps.

1. Klik **Indstillinger**, vælg **Sikkerhedsudvidelser**, og klik derefter **på Tilføj token** på **fanen API-tokens**.

2. Angiv et navn til din token, og klik derefter på **Generér**. Gem tokenet, som du skal bruge det senere.

### <a name="create-an-automated-flow"></a>Opret et automatiseret flow

Du kan se den detaljerede trinvise proces i videoen [her](https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn).

I denne video beskrives det også, hvordan du opretter forbindelse til Power Automate for Defender til skyapps.

## <a name="next-steps"></a>Næste trin

Fortsæt undersøgelsen, hvis det er nødvendigt for in-processhændelser.[](investigate-incidents.md)

## <a name="see-also"></a>Se også

- [Oversigt over hændelser](incidents-overview.md)
- [Administrer hændelser](manage-incidents.md)
- [Undersøg hændelser](investigate-incidents.md)
