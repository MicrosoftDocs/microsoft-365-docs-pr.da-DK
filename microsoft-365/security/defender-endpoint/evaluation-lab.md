---
title: Microsoft Defender for Endpoint evalueringslaboratorium
description: Få mere at vide om Microsoft Defender for Endpoint funktioner, kør simuleringer af angreb, og se, hvordan det forhindrer, registrerer og afhjælper trusler.
keywords: evaluate Microsoft Defender for Endpoint, evaluation, lab, simulation, windows 10, windows server 2019, evaluation lab
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
ms.openlocfilehash: 8a369aba012d7de23f72501ef1ce042750c57f7d
ms.sourcegitcommit: 9fdb5c5b9eaf0c8a8d62b579a5fb5a5dc2d29fa9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/11/2022
ms.locfileid: "66714591"
---
# <a name="microsoft-defender-for-endpoint-evaluation-lab"></a>Microsoft Defender for Endpoint evalueringslaboratorium

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Udførelse af en omfattende evaluering af sikkerhedsprodukt kan være en kompleks proces, der kræver besværlig miljø- og enhedskonfiguration, før der rent faktisk kan udføres en komplet simulering af angreb. Hvis du tilføjer kompleksiteten, er det en udfordring at spore, hvor simuleringsaktiviteterne, beskederne og resultaterne afspejles under evalueringen.

Det Microsoft Defender for Endpoint evalueringslaboratorium er designet til at fjerne kompleksiteten i enheds- og miljøkonfigurationen, så du kan fokusere på at evaluere platformens funktioner, køre simuleringer og se funktionerne til forebyggelse, registrering og afhjælpning i aktion.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUM]

Med den forenklede konfiguration kan du fokusere på at køre dine egne testscenarier og de forudlavede simuleringer for at se, hvordan Defender for Endpoint klarer sig.

Du har fuld adgang til platformens effektive funktioner, f.eks. automatiserede undersøgelser, avanceret jagt og trusselsanalyse, så du kan teste den omfattende beskyttelsesstak, som Defender for Endpoint tilbyder.

Du kan tilføje enheder af typen Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 og Linux (Ubuntu), der er forudkonfigureret til at have de nyeste operativsystemversioner og de rette sikkerhedskomponenter installeret samt Office 2019 Standard installeret.

Du kan også installere trusselssimulatorer. Defender for Endpoint har indgået partnerskab med brancheførende trusselssimuleringsplatforme for at hjælpe dig med at teste Defender for Endpoint-funktionerne uden at skulle forlade portalen.

Installér din foretrukne simulator, kør scenarier i evalueringslaboratoriet, og se straks, hvordan platformen fungerer - alt er bekvemt tilgængeligt uden ekstra omkostninger for dig. Du har også nem adgang til en lang række simuleringer, som du kan få adgang til og køre fra simuleringskataloget.

## <a name="before-you-begin"></a>Før du begynder

Du skal opfylde [licenskravene](minimum-requirements.md#licensing-requirements) eller have adgang til prøveversionen af Microsoft Defender for Endpoint for at få adgang til evalueringslaboratoriet.

Du skal have tilladelse til at **administrere sikkerhedsindstillinger** for at:

- Opret øvelsen
- Opret enheder
- Nulstil adgangskode
- Opret simuleringer

Hvis du har aktiveret rollebaseret adgangskontrol (RBAC) og oprettet mindst én computergruppe, skal brugerne have adgang til Alle computergrupper.

Du kan få flere oplysninger under [Opret og administrer roller](user-roles.md).

Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink)

## <a name="get-started-with-the-lab"></a>Kom i gang med øvelsen

Du kan få adgang til laboratoriet fra menuen. I navigationsmenuen skal du vælge **Evaluering og selvstudier > Evalueringslaboratorium**.

> [!NOTE]
>
> - Afhængigt af den type miljøstruktur, du vælger, vil enhederne være tilgængelige i det angivne antal timer fra aktiveringsdagen.
> - Hvert miljø er klargjort med et begrænset sæt testenheder. Når du har brugt de klargjorte enheder og slettet dem, kan du anmode om flere enheder.
> - Du kan anmode om laboratorieressourcer én gang om måneden.

Har du allerede et laboratorie? Sørg for at aktivere de nye trusselssimulatorer og have aktive enheder.

## <a name="setup-the-evaluation-lab"></a>Konfigurer evalueringslaboratoriet

1. I navigationsruden skal du vælge **Evaluering & selvstudier** **Evalueringslaboratorium**\> og derefter vælge **Opsætningslaboratorium**.

   :::image type="content" source="../../media/evaluationtutormenu.png" alt-text="Velkomstsiden for evalueringslaboratoriet" lightbox="../../media/evaluationtutormenu.png":::

2. Afhængigt af dine evalueringsbehov kan du vælge at konfigurere et miljø med færre enheder i en længere periode eller flere enheder i en kortere periode. Vælg din foretrukne laboratoriekonfiguration, og vælg derefter **Næste**.

    :::image type="content" source="images/lab-creation-page.png" alt-text="Konfigurationsindstillinger for laboratorie" lightbox="images/lab-creation-page.png":::

3. (Valgfrit) Du kan vælge at installere trusselssimulatorer i laboratoriet.

    :::image type="content" source="images/install-agent.png" alt-text="Installationssimulatoragentsiden" lightbox="images/install-agent.png":::

   > [!IMPORTANT]
   > Du skal først acceptere og give samtykke til vilkårene og erklæringerne om deling af oplysninger.

4. Vælg den trusselssimuleringsagent, du vil bruge, og angiv dine oplysninger. Du kan også vælge at installere trusselssimulatorer på et senere tidspunkt. Hvis du vælger at installere trusselssimuleringsagenter under konfigurationen af laboratoriet, kan du drage fordel af at have dem installeret på de enheder, du tilføjer.

   :::image type="content" source="images/lab-setup-summary.png" alt-text="Oversigtssiden" lightbox="images/lab-setup-summary.png":::

5. Gennemse oversigten, og vælg **Installationslaboratorium**.

Når konfigurationsprocessen for laboratoriet er fuldført, kan du tilføje enheder og køre simuleringer.

## <a name="add-devices"></a>Tilføj enheder

Når du føjer en enhed til dit miljø, konfigurerer Defender for Endpoint en velkonfigureret enhed med forbindelsesoplysninger. Du kan tilføje Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 og Linux (Ubuntu).

Enheden konfigureres med den nyeste version af operativsystemet og Office 2019 Standard samt andre apps som Java, Python og SysIntenals.

Hvis du vælger at tilføje en trusselssimulator under opsætningen af laboratoriet, vil alle enheder have trusselssimulatoragenten installeret på de enheder, du tilføjer.

Enheden bliver automatisk onboardet til din lejer med de anbefalede Windows-sikkerhedskomponenter slået til og i overvågningstilstand – uden at du behøver at gøre noget.

Følgende sikkerhedskomponenter er forudkonfigureret på testenhederne:

- [Reduktion af angrebsoverfladen](attack-surface-reduction.md)
- [Blok ved første øjekast](configure-block-at-first-sight-microsoft-defender-antivirus.md)
- [Styret mappeadgang](controlled-folders.md)
- [Exploit Protection](enable-exploit-protection.md)
- [Netværksbeskyttelse](network-protection.md)
- [Potentielt uønsket programregistrering](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
- [Skybaseret beskyttelse](cloud-protection-microsoft-defender-antivirus.md)
- [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

> [!NOTE]
> Microsoft Defender Antivirus er slået til (ikke i overvågningstilstand). Hvis Microsoft Defender Antivirus blokerer dig fra at køre din simulering, kan du slå beskyttelse i realtid fra på enheden via Windows Sikkerhed. Du kan få flere oplysninger under [Konfigurer altid aktiveret beskyttelse](configure-real-time-protection-microsoft-defender-antivirus.md).

Automatiserede undersøgelsesindstillinger afhænger af lejerindstillingerne. Den konfigureres som standard til at være semiautomatisk. Du kan få flere oplysninger under [Oversigt over automatiserede undersøgelser](automated-investigations.md).

> [!NOTE]
> Forbindelsen til testenhederne udføres ved hjælp af RDP. Sørg for, at firewallindstillingerne tillader RDP-forbindelser.

1. Vælg **Tilføj enhed** på dashboardet.

2. Vælg den type enhed, der skal tilføjes. Du kan vælge at tilføje Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 og Linux (Ubuntu).

   :::image type="content" source="../../media/add-machine-optionsnew.png" alt-text="Konfiguration af øvelse med enhedsindstillinger" lightbox="../../media/add-machine-optionsnew.png":::

   > [!NOTE]
   > Hvis der går noget galt med enhedsoprettelsesprocessen, får du besked, og du skal sende en ny anmodning. Hvis enhedsoprettelsen mislykkes, tælles den ikke med i forhold til den samlede tilladte kvote.

3. Forbindelsesoplysningerne vises. Vælg **Kopiér** for at gemme adgangskoden til enheden.

   > [!NOTE]
   > Adgangskoden vises kun én gang. Sørg for at gemme den til senere brug.

    :::image type="content" source="../../media/add-machine-eval-lab-new.png" alt-text="Enheden er tilføjet med forbindelsesoplysninger" lightbox="../../media/add-machine-eval-lab-new.png":::

4. Enhedsopsæt starter. Dette kan tage op til ca. 30 minutter.

5. Se status for testanordninger, risiko- og eksponeringsniveauer og status for simulatorinstallationer ved at vælge fanen **Enheder** .

   :::image type="content" source="images/machines-tab.png" alt-text="Fanen Enheder" lightbox="images/machines-tab.png":::
    

   > [!TIP]
   > I kolonnen **Simulatorstatus** kan du holde markøren over oplysningsikonet for at få kendskab til installationsstatussen for en agent.


## <a name="add-a-domain-controller"></a>Tilføj en domænecontroller 

Tilføj en domænecontroller for at køre komplekse scenarier, f.eks. tværgående flytning og angreb på fleretage på tværs af flere enheder.


>[!NOTE]
>Domænesupport er kun tilgængelig på Microsoft 365 Defender-portalen (security.microsoft.com).

1. Vælg **Tilføj enhed** på dashboardet.

2. Vælg **Windows Server 2019**, og vælg derefter **Angiv som domænecontroller**. 

3. Når domænecontrolleren er klargjort, kan du oprette domænetilsluttede enheder ved at klikke på **Tilføj enhed**. Vælg derefter Windows 10/Windows 11, og vælg **Deltag i domæne**. 

>[!NOTE]
>Kun én domænecontroller kan være dynamisk ad gangen. Domænecontrollerenheden forbliver dynamisk, så længe der er oprettet forbindelse til en liveenhed.



## <a name="request-for-more-devices"></a>Anmod om flere enheder

Når alle eksisterende enheder bruges og slettes, kan du anmode om flere enheder. Du kan anmode om laboratorieressourcer én gang om måneden.

1. Vælg **Anmod om flere enheder** på dashboardet til evalueringslaboratoriet.

   :::image type="content" source="images/request-more-devices.png" alt-text="Indstillingen Anmodning om flere enheder" lightbox="images/request-more-devices.png":::

2. Vælg din konfiguration.
3. Send anmodningen.

Når anmodningen er indsendt, får du vist et grønt bekræftelsesbanner og datoen for sidste indsendelse.

Du kan finde status for din anmodning under fanen **Brugerhandlinger** , som godkendes inden for få timer.

Når de er godkendt, føjes de ønskede enheder til laboratoriet, og du kan oprette flere enheder.

> [!TIP]
> Hvis du vil have mere ud af dit laboratorie, skal du huske at se vores bibliotek med simuleringer.

## <a name="simulate-attack-scenarios"></a>Simuler angrebsscenarier

Brug testenhederne til at køre dine egne angrebssimuleringer ved at oprette forbindelse til dem.

Du kan simulere angrebsscenarier ved hjælp af:

- [Angrebsscenarierne "Gør det selv"](https://security.microsoft.com/tutorials/all)
- Trusselssimulatorer

Du kan også bruge [Avanceret jagt](advanced-hunting-overview.md) til at forespørge om data og [trusselsanalyser](threat-analytics.md) for at få vist rapporter om nye trusler.

### <a name="do-it-yourself-attack-scenarios"></a>Gør-det-selv-angrebsscenarier

Hvis du er på udkig efter en færdig simulering, kan du bruge vores ["Gør det selv" angrebsscenarier](https://security.microsoft.com/tutorials/all). Disse scripts er sikre, dokumenterede og nemme at bruge. Disse scenarier afspejler funktionerne i Defender for Endpoint og fører dig gennem undersøgelsesoplevelsen.

> [!NOTE]
> Forbindelsen til testenhederne udføres ved hjælp af RDP. Sørg for, at firewallindstillingerne tillader RDP-forbindelser.

1. Opret forbindelse til din enhed, og kør en simulering af angreb ved at vælge **Opret forbindelse**.

    :::image type="content" source="images/test-machine-table.png" alt-text="Knappen Opret forbindelse for testenhederne" lightbox="images/test-machine-table.png":::


   :::image type="content" source="images/remote-connection.png" alt-text="Forbindelsesskærmen til fjernskrivebord" lightbox="images/remote-connection.png":::

    Til **Linux-enheder**: Du skal bruge en lokal SSH-klient og den angivne kommando. 


    > [!NOTE]
    > Hvis du ikke har gemt en kopi af adgangskoden under den indledende konfiguration, kan du nulstille adgangskoden ved at vælge **Nulstil adgangskode** i menuen:
    >
    > :::image type="content" source="images/reset-password-test-machine.png" alt-text="Indstillingen Nulstil adgangskode" lightbox="images/reset-password-test-machine.png":::
    >
    > Enheden ændrer dens tilstand til "Udfører nulstilling af adgangskode", og derefter får du vist din nye adgangskode om et par minutter.

3. Angiv den adgangskode, der blev vist under trinnet til enhedsoprettelse.

   :::image type="content" source="images/enter-password.png" alt-text="Skærmen, hvor du angiver legitimationsoplysninger" lightbox="images/enter-password.png":::

4. Kør Gør-det-selv-angrebssimuleringer på enheden.

### <a name="threat-simulator-scenarios"></a>Trusselssimulatorscenarier

Hvis du vælger at installere nogen af de understøttede trusselssimulatorer under konfigurationen af laboratoriet, kan du køre de indbyggede simuleringer på evalueringslaboratoriets enheder.

Kørsel af trusselssimuleringer ved hjælp af tredjepartsplatforme er en god måde at evaluere Microsoft Defender for Endpoint funktioner inden for rammerne af et laboratoriemiljø.

> [!NOTE]
>
> Før du kan køre simuleringer, skal du sikre dig, at følgende krav er opfyldt:
>
> - Enheder skal føjes til evalueringslaboratoriet
> - Trusselssimulatorer skal installeres i evalueringslaboratoriet

1. Vælg **Opret simulering** på portalen.

2. Vælg en trusselssimulator.

   :::image type="content" source="images/select-simulator.png" alt-text="Valget af trusselssimulator" lightbox="images/select-simulator.png":::

3. Vælg en simulering, eller gennemse simuleringsgalleriet for at gennemse de tilgængelige simuleringer.

    Du kan få vist simuleringsgalleriet fra:
    - Det primære evalueringsdashboard i feltet **Oversigt over simuleringer** eller
    - Når du navigerer fra navigationsruden **Evaluering og selvstudier** \> **Simulering & selvstudier**, skal du vælge **Kataloget Simuleringer**.

4. Vælg de enheder, hvor du vil køre simuleringen på.

5. Vælg **Opret simulering**.

6. Få vist statussen for en simulering ved at vælge fanen **Simuleringer** . Få vist simuleringstilstanden, aktive beskeder og andre oplysninger.

   :::image type="content" source="images/simulations-tab.png" alt-text="Fanen Simuleringer" lightbox="images/simulations-tab.png":::

Når du har kørt dine simuleringer, opfordrer vi dig til at gennemgå statuslinjen for laboratoriet og udforske **Microsoft Defender for Endpoint udløste en automatiseret undersøgelse og afhjælpning**. Se de beviser, der er indsamlet og analyseret af funktionen.

Gå på jagt efter angrebsresultater gennem avanceret jagt ved hjælp af det omfattende forespørgselssprog og rå telemetri, og se nogle trusler over hele verden, der er dokumenteret i Threat-analyse.

## <a name="simulation-gallery"></a>Simuleringsgalleri

Microsoft Defender for Endpoint har indgået partnerskab med forskellige trusselssimuleringsplatforme for at give dig nem adgang til at teste platformens funktioner direkte fra portalen.

Få vist alle tilgængelige simuleringer ved at gå til **kataloget Simuleringer og selvstudier** \> i menuen.

Der er angivet en liste over understøttede trusselssimuleringsagenter fra tredjepart, og der findes specifikke typer simuleringer sammen med detaljerede beskrivelser i kataloget.

Du kan nemt køre enhver tilgængelig simulering direkte fra kataloget.

:::image type="content" source="images/simulations-catalog.png" alt-text="Simuleringskatalog" lightbox="images/simulations-catalog.png":::

Hver simulering leveres med en detaljeret beskrivelse af angrebsscenariet og referencer, f.eks. DE MITRE-angrebsteknikker, der bruges, og eksempler på avancerede jagtforespørgsler, du kører.

**Eksempler:**

:::image type="content" source="images/simulation-details-aiq.png" alt-text="Ruden med oplysninger om simuleringsbeskrivelse for fastholdelsesmetoder" lightbox="images/simulation-details-aiq.png":::

:::image type="content" source="images/simulation-details-sb.png" alt-text="Oplysninger om simuleringsbeskrivelsen for APT29" lightbox="images/simulation-details-sb.png":::

## <a name="evaluation-report"></a>Evalueringsrapport

Laboratorierapporterne opsummerer resultaterne af de simuleringer, der udføres på enhederne.

:::image type="content" source="images/eval-report.png" alt-text="Evalueringsrapport" lightbox="images/eval-report.png":::

Med et hurtigt øjekast kan du hurtigt se:

- Hændelser, der blev udløst
- Genererede beskeder
- Vurderinger af eksponeringsniveau
- Observerede trusselskategorier
- Registreringskilder
- Automatiserede undersøgelser

## <a name="provide-feedback"></a>Giv feedback

Din feedback hjælper os med at blive bedre til at beskytte dit miljø mod avancerede angreb. Del dine erfaringer og visninger fra produktegenskaber og evalueringsresultater.

Fortæl os, hvad du synes, ved at vælge **Giv feedback**.

:::image type="content" source="images/send-us-feedback-eval-lab.png" alt-text="Feedbacksiden" lightbox="images/send-us-feedback-eval-lab.png":::
