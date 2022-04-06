---
title: Undersøg enhederne på listen Defender for Endpoint-enheder
description: Undersøg påvirkede enheder ved at gennemse beskeder, oplysninger om netværksforbindelsen, tilføje enhedsmærker og grupper og kontrollere tjenestestilstanden.
keywords: enheder, mærker, grupper, slutpunkt, beskedkø, beskeder, besked, enhedsnavn, domæne, sidst set, intern IP, aktive beskeder, trusselskategori, filter, sortering, gennemse beskeder, netværk, forbindelse, type, password stjæler, ransomware, udnytte, trussel, lav alvorsgrad, tjeneste sundhed
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 71755add523b3426d144f748ab3582e3a3975dc6
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475229"
---
# <a name="investigate-devices-in-the-microsoft-defender-for-endpoint-devices-list"></a>Undersøg enhederne Microsoft Defender for Endpoint listen Over enheder

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Defender til Slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatemachines-abovefoldlink)

Undersøg oplysningerne om en besked, der er blevet hævet på en bestemt enhed, for at identificere andre funktionsmåder eller hændelser, der kan være relateret til beskeden eller det potentielle omfang af misligholdelsen.

> [!NOTE]
> Som en del af undersøgelsen eller svarprocessen kan du indsamle en undersøgelsespakke fra en enhed. Sådan gør du: Samlet [undersøgelsespakke fra enheder](/microsoft-365/security/defender-endpoint/respond-machine-alerts#collect-investigation-package-from-devices).

Du kan klikke på påvirkede enheder, når du ser dem i portalen for at åbne en detaljeret rapport om den pågældende enhed. Påvirkede enheder identificeres i følgende områder:

- [Liste over enheder](investigate-machines.md)
- [Kø til beskeder](alerts-queue.md)
- [Dashboard for sikkerhedshandlinger](security-operations-dashboard.md)
- Enhver individuel besked
- En hvilken som helst individuel fildetaljeringsvisning
- En hvilken som helst visning af IP-adresser eller domænedetaljer

Når du undersøger en bestemt enhed, får du vist:

- Enhedsoplysninger
- Svarhandlinger
- Faner (oversigt, beskeder, tidslinje, sikkerhedsanbefalinger, lager over software, opdagede sårbarheder, manglende KBs)
- Kort (aktive beskeder, brugere, der er logget på, sikkerhedsvurdering)

:::image type="content" source="images/specific-device.png" alt-text="Enhedsvisning" lightbox="images/specific-device.png":::

> [!NOTE]
> På grund af produktbegrænsning overvejer enhedsprofilen ikke alle cyber beviser, når tidsrammen "Sidst set" bestemmes (som det også ses på enhedens side).
> Værdien "Senest set" på siden Enhed kan f.eks. vise en ældre tidsramme, selvom nyere beskeder eller data er tilgængelige på computerens tidslinje.

## <a name="device-details"></a>Enhedsoplysninger

Afsnittet med enhedsdetaljer indeholder oplysninger som f.eks. enhedens domæne, operativsystem og tilstand. Hvis en undersøgelsespakke er tilgængelig på enheden, får du vist et link, der giver dig mulighed for at downloade pakken.

## <a name="response-actions"></a>Svarhandlinger

Svarhandlinger kører langs toppen af en bestemt enhedsside og omfatter:

- Administrer mærker
- Isoler enhed
- Begræns appudførelse
- Kør antivirusscanning
- Pakke til samlet undersøgelse
- Start direkte svarsession
- Initier automatiseret undersøgelse
- Kontakt en trusselsekspert
- Handlingscenter

Du kan udføre svarhandlinger i Handlingscenter, på en bestemt enhedsside eller på en bestemt filside.

Du kan finde flere oplysninger om, hvordan du reagere på en enhed, [under Reagerehandling på en enhed](respond-machine-alerts.md).

Få mere at vide under [Undersøg brugerobjekter](investigate-user.md).

## <a name="tabs"></a>Faner

Fanerne indeholder relevante oplysninger om sikkerhed og trusselsforebyggelse vedrørende enheden. I hver fane kan du tilpasse de kolonner, der vises, ved at vælge Tilpas **kolonner** fra linjen over kolonneoverskrifterne.

### <a name="overview"></a>Oversigt

Fanen **Oversigt** viser kortene [for aktive](#cards) beskeder, brugere, der er logget på, og sikkerhedsvurdering.

:::image type="content" source="images/overview-device.png" alt-text="Fanen Oversigt på enhedssiden" lightbox="images/overview-device.png":::

### <a name="alerts"></a>Beskeder

Fanen **Beskeder indeholder** en liste over beskeder, der er knyttet til enheden. Denne liste er en filtreret version af køen [Beskeder og viser](alerts-queue.md) en kort beskrivelse af beskeden, alvorsgrad (høj, mellem, lav, informationskø), status i køen (ny, i gang, løst), klassificering (ikke angivet, falsk besked, sand besked), undersøgelsestilstand, beskedkategori, hvem der adresserer beskeden, og den seneste aktivitet. Du kan også filtrere beskederne.

:::image type="content" source="images/alerts-device.png" alt-text="Fanen for de beskeder, der er relateret til enheden" lightbox="images/alerts-device.png":::

Når cirkelikonet til venstre for en besked er markeret, vises en pop op-meddelelse. Fra dette panel kan du administrere beskeden og få vist flere detaljer såsom hændelsesnummer og relaterede enheder. Du kan vælge flere beskeder ad gangen.

Hvis du vil have vist en visning på hele siden af en besked, herunder hændelsesdiagram og procestræ, skal du vælge beskedens titel.

### <a name="timeline"></a>Tidslinje

Fanen **Tidslinje** giver en kronologisk visning af de hændelser og tilknyttede beskeder, der er blevet observeret på enheden. Dette kan hjælpe dig med at korrelere hændelser, filer og IP-adresser i forhold til enheden.

Tidslinjen giver dig også mulighed for selektivt at analysere ned i hændelser, der er opstået inden for en given tidsperiode. Du kan få vist tidssekvensen af hændelser, der er opstået på en enhed i løbet af en valgt tidsperiode. Du kan filtrere efter begivenhedsgrupper eller tilpasse kolonnerne for yderligere at styre visningen.

> [!NOTE]
> For at firewallhændelser kan vises, skal du aktivere overvågningspolitikken under Forbindelse [til overvågningsfiltreringsplatform](/windows/security/threat-protection/auditing/audit-filtering-platform-connection).
>
> Firewallen dækker følgende hændelser:
>
> - [5025 –](/windows/security/threat-protection/auditing/event-5025) firewalltjeneste stoppet
> - [5031](/windows/security/threat-protection/auditing/event-5031) – program blokeret fra at acceptere indgående forbindelser på netværket
> - [5157](/windows/security/threat-protection/auditing/event-5157) – blokeret forbindelse

:::image type="content" source="images/timeline-device.png" alt-text="Enhedens tidslinje med begivenheder" lightbox="images/timeline-device.png":::

Nogle af funktionerne omfatter:

- Søg efter bestemte begivenheder
  - Brug søgelinjen til at søge efter bestemte tidslinjehændelser.
- Filtrere hændelser fra en bestemt dato
  - Vælg kalenderikonet øverst til venstre i tabellen for at få vist begivenheder for den seneste dag, uge, 30 dage eller et brugerdefineret område. Enhedens tidslinje er som standard indstillet til at vise begivenheder fra de seneste 30 dage.
  - Brug tidslinjen til at springe til et bestemt tidspunkt ved at fremhæve sektionen. Pilene på tidslinjen finder automatiserede undersøgelser
- Eksportér detaljerede enhedstidshændelser
  - Eksportér enhedens tidslinje for den aktuelle dato eller et angivet datointerval op til syv dage.

Du kan finde flere oplysninger om visse hændelser i **sektionen Yderligere** oplysninger. Disse detaljer varierer afhængigt af typen af begivenhed, f.eks.:

- Indeholdt af Application Guard – webbrowserhændelsen blev begrænset af en isoleret beholder
- Der blev registreret en aktiv trussel – trusselsregistreringen, mens trusselsbilledet kørte
- Afhjælpning mislykkedes – et forsøg på at løse den registrerede trussel blev startet, men mislykkedes
- Afhjælpning lykkedes – den registrerede trussel blev stoppet og ryddet
- Advarsel er blevet ignoreret af brugeren – Windows Defender SmartScreen-advarslen blev afvist og tilsidesat af en bruger
- Mistænkeligt script registreret – der blev fundet et potentielt skadeligt script, der kørte
- Beskedkategorien – hvis begivenheden førte til generationen af en besked, leveres beskedkategorien ("Lateral Bevægelse" for eksempel)

#### <a name="event-details"></a>Oplysninger om begivenhed

Vælg en begivenhed for at få vist relevante detaljer om den pågældende begivenhed. Et panel vises for at vise generelle oplysninger om begivenheden. Når relevant og data er tilgængelige, vises der også en graf, der viser relaterede enheder og deres relationer.

For yderligere at undersøge begivenheden og relaterede begivenheder kan du hurtigt køre en [avanceret forespørgsel](advanced-hunting-overview.md) på en forespørgsel ved at **vælge Søge efter relaterede begivenheder**. Forespørgslen returnerer den valgte hændelse og listen over andre hændelser, der opstod omkring samme tid på samme slutpunkt.

:::image type="content" source="images/event-details.png" alt-text="Panelet med begivenhedsoplysninger" lightbox="images/event-details.png":::

### <a name="security-recommendations"></a>Sikkerhedsanbefalinger

**Der genereres** sikkerhedsanbefalinger fra Microsoft Defender for Endpoint i [Administration af & af](tvm-dashboard-insights.md) trusler. Når du vælger en anbefaling, vises der et panel, hvor du kan få vist relevante detaljer, f.eks. en beskrivelse af anbefalingen og de potentielle risici ved ikke at gøre det. Se [Sikkerhedsanbefaling](tvm-security-recommendation.md) for at få flere oplysninger.

:::image type="content" source="images/security-recommendations-device.png" alt-text="Fanen med anbefalinger om sikkerhed" lightbox="images/security-recommendations-device.png":::

### <a name="software-inventory"></a>Lager over software

Under **fanen Softwarelager** kan du få vist software på enheden sammen med eventuelle trusler eller trusler. Når du vælger navnet på softwaren, kommer du til siden med softwareoplysninger, hvor du kan få vist sikkerhedsanbefalinger, opdagede sårbarheder, installerede enheder og versionsfordeling. Se [Softwarelager for at](tvm-software-inventory.md) få flere oplysninger

:::image type="content" source="images/software-inventory-device.png" alt-text="Fanen Softwarelager" lightbox="images/software-inventory-device.png":::

### <a name="discovered-vulnerabilities"></a>Opdagede sårbarheder

Fanen **Opdagede** sårbarheder viser navn, alvor og trusselsindsigt for opdagede sårbarheder på enheden. Hvis du vælger bestemte sårbarheder, vises en beskrivelse og detaljer.

:::image type="content" source="images/discovered-vulnerabilities-device.png" alt-text="Fanen Opdagede sårbarheder" lightbox="images/discovered-vulnerabilities-device.png":::

### <a name="missing-kbs"></a>Manglende KBs
Fanen **Manglende KBs** viser de manglende sikkerhedsopdateringer til enheden.

:::image type="content" source="images/missing-kbs-device.png" alt-text="Fanen Manglende KBs" lightbox="images/missing-kbs-device.png":::

## <a name="cards"></a>Kort

### <a name="active-alerts"></a>Aktive beskeder

**Azure Advanced Threat Protection-kortet** viser en omfattende oversigt over beskeder, der er relateret til enheden og deres risikoniveau, hvis du har aktiveret Microsoft Defender for Identity-funktionen, og der er nogen aktive beskeder. Du kan finde flere oplysninger i "Besked"-detaljeadgangen.

:::image type="content" source="images/risk-level-small.png" alt-text="Det aktive beskedkort" lightbox="images/risk-level-small.png":::

> [!NOTE]
> Du skal aktivere integrationen på både Microsoft Defender for Identity Defender for Endpoint for at bruge denne funktion. I Defender til Slutpunkt kan du aktivere denne funktion i avancerede funktioner. Du kan finde flere oplysninger om, hvordan du aktiverer avancerede funktioner, [under Slå avancerede funktioner til](advanced-features.md).

### <a name="logged-on-users"></a>Brugere, der er logget på

Kortet **Brugere, der er** logget på, viser, hvor mange brugere der har logget på de seneste 30 dage sammen med de mest og mindst hyppige brugere. Hvis du vælger linket "Se alle brugere", åbnes detaljeruden, som viser oplysninger som f.eks. brugertype, logontype, og hvornår brugeren først og sidst blev set. Få mere at vide under [Undersøg brugerobjekter](investigate-user.md).

:::image type="content" source="images/logged-on-users.png" alt-text="Ruden med brugeroplysninger" lightbox="images/logged-on-users.png":::

> [!NOTE]
> Den "hyppigste" brugerværdi beregnes kun på baggrund af beviser for brugere, der har logget interaktivt på.
> Men sideruden "Alle brugere" beregner alle typer brugerlogon, så der forventes at være flere hyppige brugere i sideruden, da disse brugere muligvis ikke er interaktive.

### <a name="security-assessments"></a>Sikkerhedsvurderinger

Kortet **til sikkerhedsvurderinger** viser det overordnede eksponeringsniveau, sikkerhedsanbefalinger, installeret software og opdagede sårbarheder. En enheds eksponeringsniveau bestemmes af den kumulative effekt af dens ventende sikkerhedsanbefalinger.

:::image type="content" source="images/security-assessments.png" alt-text="Kortet til sikkerhedsvurderinger" lightbox="images/security-assessments.png":::

## <a name="related-topics"></a>Relaterede emner

- [Få vist og organiser Microsoft Defender for Endpoint i køen vigtige beskeder](alerts-queue.md)
- [Administrer Microsoft Defender for Endpoint vigtige beskeder](manage-alerts.md)
- [Undersøg Microsoft Defender for Endpoint vigtige beskeder](investigate-alerts.md)
- [Undersøg en fil, der er knyttet til en Defender for Endpoint-besked](investigate-files.md)
- [Undersøg en IP-adresse, der er knyttet til en Defender for Endpoint-besked](investigate-ip.md)
- [Undersøg et domæne, der er knyttet til en Defender for Endpoint-besked](investigate-domain.md)
- [Undersøg en brugerkonto i Defender for Endpoint](investigate-user.md)
- [Sikkerhedsanbefaling](tvm-security-recommendation.md)
- [Lager over software](tvm-software-inventory.md)
