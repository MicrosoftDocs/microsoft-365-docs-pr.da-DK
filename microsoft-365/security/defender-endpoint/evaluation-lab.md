---
title: Microsoft Defender for Endpoint evalueringslaboratorium
description: Få mere Microsoft Defender for Endpoint, kør angrebssimulering, og se, hvordan det forhindrer, registrerer og afhjælper trusler.
keywords: evaluer Microsoft Defender for Endpoint, evaluering, lab, simulering, windows 10, windows server 2019, evalueringslaboratorium
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.prod: m365-security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-evalutatemtp
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2b4c1cd9c37921fbb54633c0fc1bf2e42d308081
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472875"
---
# <a name="microsoft-defender-for-endpoint-evaluation-lab"></a>Microsoft Defender for Endpoint evalueringslaboratorium

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Udførelse af en omfattende sikkerhedsproduktevaluering kan være en kompleks proces, der kræver besværlige miljøer og enhedskonfiguration, før en komplet simulering af angreb faktisk kan udføres. Det er en udfordring at føje noget til kompleksiteten ved at spore, hvor simuleringsaktiviteterne, påmindelserne og resultaterne afspejles under evalueringen.

Evalueringslaboratoriet i Microsoft Defender for Endpoint er udviklet til at eliminere kompleksiteten ved enheds- og miljøkonfiguration, så du kan fokusere på evaluering af platformens funktioner, køre simulering og se, hvilke funktioner til forebyggelse, registrering og afhjælpning, der er i brug.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUM]

Med den forenklede opsætningsoplevelse kan du fokusere på at køre dine egne testscenarier og de foruddefinerede simuleringer for at se, hvordan Defender til Slutpunkt fungerer.

Du har fuld adgang til de effektive egenskaber fra platformen, såsom automatiserede undersøgelser, avanceret jagt og trusselsanalyse, så du kan teste den omfattende beskyttelsestast, som Defender til Slutpunkt tilbyder.

Du kan tilføje Windows 10-, Windows 11-, Windows Server 2019-, Windows Server 2016- og Linux-enheder (Ubuntu), der er forudkonfigureret til at have de nyeste os-versioner og de rigtige sikkerhedskomponenter på plads samt Office 2019 Standard installeret.

Du kan også installere trusler. Defender til Slutpunkt har indgået partnerskab med brancheførende trusselssimuleringsplatforme for at hjælpe dig med at teste Defender for Endpoint-egenskaberne uden at forlade portalen.

Installér din foretrukne platform, kør scenarier i evalueringslaboratoriet, og se øjeblikkeligt, hvordan platformen fungerer – alt sammen praktisk tilgængeligt uden ekstra omkostninger for dig. Du har også nem adgang til en bred vifte af simuleringer, som du kan få adgang til og køre fra simuleringskataloget.

## <a name="before-you-begin"></a>Før du begynder

Du skal opfylde licenskravene eller [have prøveversionsadgang](minimum-requirements.md#licensing-requirements) til dit Microsoft Defender for Endpoint få adgang til evalueringslaboratoriet.

Du skal have **tilladelsen Administrer sikkerhedsindstillinger** for at:

- Opret laboratoriet
- Opret enheder
- Nulstil adgangskode
- Opret simuleringer

Hvis du har aktiveret rollebaseret adgangskontrol (RBAC) og oprettet mindst én maskingruppe, skal brugerne have adgang til Alle maskingrupper.

Få mere at vide under [Opret og administrer roller](user-roles.md).

Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink)

## <a name="get-started-with-the-lab"></a>Kom i gang med laboratoriet

Du kan få adgang til laboratoriet fra menuen. I **navigationsmenuen skal du vælge Evaluering og selvstudier > Evaluation lab**.

> [!NOTE]
>
> - Afhængigt af den type miljøstruktur, du vælger, vil enhederne være tilgængelige i det angivne antal timer fra aktiveringsdagen.
> - Hvert miljø er klargjort med et begrænset antal testenheder. Når du har brugt de klargjorte enheder og har slettet dem, kan du anmode om flere enheder.
> - Du kan anmode om laboratorieressourcer én gang om måneden.

Har du allerede et lab? Sørg for at aktivere de nye trusler og have aktive enheder.

## <a name="setup-the-evaluation-lab"></a>Konfigurer evalueringslaboratoriet

1. Vælg Evalueringslaboratorium i **navigationsruden& evalueringslaboratorium** \> **, og** vælg derefter **Konfigurationslaboratorium**.

   :::image type="content" source="../../media/evaluationtutormenu.png" alt-text="Velkomstsiden for evalueringslaboratorium" lightbox="../../media/evaluationtutormenu.png":::

2. Afhængigt af dine evalueringsbehov kan du vælge at konfigurere et miljø med færre enheder i en længere periode eller flere enheder i en kortere periode. Vælg din foretrukne labkonfiguration, og vælg derefter **Næste**.

    :::image type="content" source="images/lab-creation-page.png" alt-text="Konfigurationsindstillingerne for øvelser" lightbox="images/lab-creation-page.png":::

3. (Valgfrit) Du kan vælge at installere trusselsinstallationer i laboratoriet.

    :::image type="content" source="images/install-agent.png" alt-text="Installationsagentsiden" lightbox="images/install-agent.png":::

   > [!IMPORTANT]
   > Du skal først acceptere og give samtykke til vilkårene og erklæringerne om deling af oplysninger.

4. Vælg den trusselssimuleringsagent, du vil bruge, og angiv dine oplysninger. Du kan også vælge at installere trusler på et senere tidspunkt. Hvis du vælger at installere trusselssimuleringsagenter under installationen, får du fordelen af at have dem installeret på de enheder, du tilføjer.

   :::image type="content" source="images/lab-setup-summary.png" alt-text="Oversigtssiden" lightbox="images/lab-setup-summary.png":::

5. Gennemgå oversigten, og vælg **Konfigurationslaboratorium**.

Når installationen er fuldført, kan du tilføje enheder og køre simulering.

## <a name="add-devices"></a>Tilføj enheder

Når du føjer en enhed til dit miljø, konfigurerer Defender til Slutpunkt en korrekt konfigureret enhed med forbindelsesoplysninger. Du kan Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 og Linux (Ubuntu).

Enheden konfigureres med den mest opdaterede version af operativsystemet og Office 2019 Standard samt andre apps som Java, Python og SysIntenals.

Hvis du vælger at tilføje en trussel under installationen, vil alle enheder have trusselsagenten installeret på de enheder, du tilføjer.

Enheden vil automatisk blive onboardet til din lejer med de anbefalede Windows sikkerhedskomponenter slået til og i overvågningstilstand – uden at skulle gøre noget på din side.

Følgende sikkerhedskomponenter er forudkonfigureret på testenhederne:

- [Reduktion af angrebsoverfladen](attack-surface-reduction.md)
- [Bloker ved første synsvidens](configure-block-at-first-sight-microsoft-defender-antivirus.md)
- [Styret mappeadgang](controlled-folders.md)
- [Exploit Protection](enable-exploit-protection.md)
- [Netværksbeskyttelse](network-protection.md)
- [Potentielt uønsket programregistrering](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
- [Cloud-leveret beskyttelse](cloud-protection-microsoft-defender-antivirus.md)
- [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

> [!NOTE]
> Microsoft Defender Antivirus er aktiveret (ikke i overvågningstilstand). Hvis Microsoft Defender Antivirus forhindrer dig i at køre din simulering, kan du deaktivere beskyttelse i realtid på enheden via Windows Sikkerhed. Få mere at vide under [Konfigurer altid til beskyttelse](configure-real-time-protection-microsoft-defender-antivirus.md).

Indstillinger for automatiserede undersøgelser vil være afhængige af lejerindstillingerne. Den konfigureres til at være semi-automatiseret som standard. Få mere at vide under [Oversigt over automatiserede undersøgelser](automated-investigations.md).

> [!NOTE]
> Forbindelsen til testenhederne udføres ved hjælp af RDP. Sørg for, at dine firewallindstillinger tillader RDP-forbindelser.

1. Vælg Tilføj enhed på **dashboardet**.

2. Vælg den type enhed, der skal tilføjes. Du kan vælge at Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 og Linux (Ubuntu).

   :::image type="content" source="../../media/add-machine-optionsnew.png" alt-text="Laboratoriekonfigurationen med enhedsindstillinger" lightbox="../../media/add-machine-optionsnew.png":::

   > [!NOTE]
   > Hvis noget går galt med enhedsoprettelsesprocessen, får du besked, og du skal sende en ny anmodning. Hvis enhedsoprettelsen mislykkes, tælles det ikke med i den samlede tilladte kvote.

3. Forbindelsesdetaljerne vises. Vælg **Kopiér** for at gemme adgangskoden til enheden.

   > [!NOTE]
   > Adgangskoden vises kun én gang. Sørg for at gemme den til senere brug.

    :::image type="content" source="../../media/add-machine-eval-lab-new.png" alt-text="Enheden er tilføjet med forbindelsesoplysninger" lightbox="../../media/add-machine-eval-lab-new.png":::

4. Opsætning af enhed starter. Det kan tage op til ca. 30 minutter.

5. Se status for testenheder, risiko- og eksponeringsniveauer og status for installationer ved at vælge **fanen** Enheder.

   :::image type="content" source="images/machines-tab.png" alt-text="Fanen Enheder" lightbox="images/machines-tab.png":::
    

   > [!TIP]
   > Du kan **pege på oplysningsikonet** for at kende installationsstatussen for en agent i kolonnenRapporteringsstatus.


## <a name="request-for-more-devices"></a>Anmod om flere enheder

Når alle eksisterende enheder bruges og slettes, kan du anmode om flere enheder. Du kan anmode om laboratorieressourcer én gang om måneden.

1. Fra dashboardet til evalueringslaboratorium **skal du vælge Anmod om flere enheder**.

   :::image type="content" source="images/request-more-devices.png" alt-text="Indstillingen Anmodning om flere enheder" lightbox="images/request-more-devices.png":::

2. Vælg din konfiguration.
3. Indsend anmodningen.

Når anmodningen er sendt, får du vist et grønt bekræftelsesbanner og datoen for den seneste indsendelse.

Du kan finde status for din anmodning under **fanen Brugerhandlinger** , som godkendes i løbet af få timer.

Når de er godkendt, føjes de nødvendige enheder til din lab-opsætning, og du vil kunne oprette flere enheder.

> [!TIP]
> Hvis du vil have mere ud af dit lab, skal du huske at tjekke vores simuleringsbibliotek.

## <a name="simulate-attack-scenarios"></a>Simulere angrebsscenarier

Brug testenhederne til at køre dine egne angrebssimulering ved at oprette forbindelse til dem.

Du kan simulere angrebsscenarier ved hjælp af:

- [Angrebsscenarierne "Gør det selv"](https://security.microsoft.com/tutorials/all)
- Trusselstrusler

Du kan også bruge [Avanceret på jagt](advanced-hunting-overview.md) til at forespørge data [og trusselsanalyser](threat-analytics.md) for at få vist rapporter om fremspirende trusler.

### <a name="do-it-yourself-attack-scenarios"></a>Gør-det-selv-angrebsscenarier

Hvis du leder efter en foruddefineret simulering, kan du bruge vores [scenarier med "Gør det selv"-angreb](https://security.microsoft.com/tutorials/all). Disse scripts er sikre, dokumenterede og nemme at bruge. Disse scenarier afspejler Defender for Endpoint-egenskaber og hjælper dig gennem din undersøgelsesoplevelse.

> [!NOTE]
> Forbindelsen til testenhederne udføres ved hjælp af RDP. Sørg for, at dine firewallindstillinger tillader RDP-forbindelser.

1. Forbind din enhed, og kør en angrebssimulering ved at **vælge Forbind**.

    :::image type="content" source="images/test-machine-table.png" alt-text="Knappen Forbind til testenhederne" lightbox="images/test-machine-table.png":::


   :::image type="content" source="images/remote-connection.png" alt-text="Skærmbilledet forbindelse til fjernskrivebord" lightbox="images/remote-connection.png":::

    Til **Linux-enheder**: Du skal bruge en lokal SSH-klient og den angivne kommando. 


    > [!NOTE]
    > Hvis du ikke har en kopi af den adgangskode, der blev gemt under den indledende konfiguration, kan du nulstille adgangskoden ved at vælge **Nulstil** adgangskode i menuen:
    >
    > :::image type="content" source="images/reset-password-test-machine.png" alt-text="Indstillingen Nulstil adgangskode" lightbox="images/reset-password-test-machine.png":::
    >
    > Enheden ændrer tilstanden til "Udfører nulstilling af adgangskode", og derefter får du vist den nye adgangskode om et par minutter.

3. Angiv den adgangskode, der blev vist under trinnet til oprettelse af enhed.

   :::image type="content" source="images/enter-password.png" alt-text="Det skærmbillede, hvor du skal angive legitimationsoplysninger" lightbox="images/enter-password.png":::

4. Kør Do-it-yourself-angrebssimeringer på enheden.

### <a name="threat-simulator-scenarios"></a>Trusselsscenarier

Hvis du vælger at installere en af de understøttede trusselsinstallationer under installationen, kan du køre de indbyggede simuleringer på evalueringslaboratorerne.

At køre trusselssimulering ved hjælp af tredjepartsplatforme er en god måde at evaluere Microsoft Defender for Endpoint funktioner inden for rammerne af et labmiljø.

> [!NOTE]
>
> Før du kan køre simuleringer, skal du sikre dig, at følgende krav er opfyldt:
>
> - Enheder skal føjes til evalueringslaboratoriet
> - Trusselsbilledet skal installeres i evalueringslaboratoriet

1. Vælg Opret simulering **på portalen**.

2. Vælg en trussel.

   :::image type="content" source="images/select-simulator.png" alt-text="Valg af trusselsmarkering" lightbox="images/select-simulator.png":::

3. Vælg en simulering, eller gennemse simuleringsgalleriet for at gennemse de tilgængelige simuleringer.

    Du kan komme til simuleringsgalleriet fra:
    - Det primære dashboard til evaluering i **flisen simuleringsoversigt** eller
    - Ved at navigere fra **navigationsruden** **Evaluering og selvstudier Simulering &**\>, og vælg derefter **Simuleringskatalog**.

4. Vælg de enheder, hvor du vil køre simulering på.

5. Vælg **Opret simulering**.

6. Få vist status for en simulering ved at vælge **fanen Simuleringer** . Få vist simuleringstilstand, aktive beskeder og andre oplysninger.

   :::image type="content" source="images/simulations-tab.png" alt-text="Fanen Simuleringer" lightbox="images/simulations-tab.png":::

Når du har kørt dine simuleringer, opfordrer vi dig til at gå gennem statuslinjen i øvelserne og udforske de Microsoft Defender for Endpoint udløst en automatiseret undersøgelse **og afhjælpning**. Se de beviser, der indsamles og analyseres af funktionen.

Søg efter angrebsdokumentførelse gennem avanceret jagt ved at bruge det omfattende forespørgselssprog og rå telemetri, og tjek nogle globale trusler, der er dokumenteret i Threat analytics.

## <a name="simulation-gallery"></a>Simuleringsgalleri

Microsoft Defender for Endpoint har indgået partnerskab med forskellige trusselssimuleringsplatforme for at give dig nem adgang til at teste platformens funktioner direkte fra portalen.

Få vist alle tilgængelige simuleringer ved at gå til  **kataloget Simulering og** \> **selvstudier Simulering**  fra menuen.

Der vises en liste over understøttede simuleringsagenter fra tredjeparter, og der findes bestemte typer simulering sammen med detaljerede beskrivelser i kataloget.

Du kan nemt køre enhver tilgængelig simulering direkte fra kataloget.

:::image type="content" source="images/simulations-catalog.png" alt-text="Simuleringskatalog" lightbox="images/simulations-catalog.png":::

Hver simulering leveres med en dybdegående beskrivelse af angrebsscenariet og referencer som f.eks. de MITRE-angrebsteknikker, der bruges, og eksempler på Avancerede forespørgselsforespørgsler, du kører.

**Eksempler:**

:::image type="content" source="images/simulation-details-aiq.png" alt-text="Eksempel på detaljerede oplysninger om simuleringsbeskrivelse for vedholdende metoder" lightbox="images/simulation-details-aiq.png":::

:::image type="content" source="images/simulation-details-sb.png" alt-text="Oplysninger om simuleringsbeskrivelse for APT29" lightbox="images/simulation-details-sb.png":::

## <a name="evaluation-report"></a>Evalueringsrapport

Laboratorierapporterne opsummerer resultaterne af simuleringer, der udføres på enhederne.

:::image type="content" source="images/eval-report.png" alt-text="Evalueringsrapport" lightbox="images/eval-report.png":::

Med et hurtigt øjekast vil du hurtigt kunne se:

- Hændelser, der blev udløst
- Genererede beskeder
- Vurderinger af eksponeringsniveau
- Trusselskategorier observeret
- Registrering af kilder
- Automatiserede undersøgelser

## <a name="provide-feedback"></a>Giv feedback

Din feedback hjælper os med at blive bedre til at beskytte dit miljø mod avancerede angreb. Del din oplevelse og dine indtryk fra produktegenskaber og evalueringsresultater.

Fortæl os, hvad du synes, ved at vælge **Giv feedback**.

:::image type="content" source="images/send-us-feedback-eval-lab.png" alt-text="Feedbacksiden" lightbox="images/send-us-feedback-eval-lab.png":::
