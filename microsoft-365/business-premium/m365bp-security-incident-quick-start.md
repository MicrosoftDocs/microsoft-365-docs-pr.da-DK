---
title: En vejledning til sikkerhedshandlinger for Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
ms.assetid: 80bdae57-f8bc-4e40-a58c-956007117ecb
description: 'Et sæt forslag til, hvad du skal fokusere på i Defender-portalen, når det kommer til daglige, ugentlige eller månedlige handlinger. '
ms.openlocfilehash: e97176eab4d846709fb51dbab0f6d6122e45b7f5
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66858940"
---
# <a name="microsoft-365-business-premium-security-operations-guide"></a>vejledning til Microsoft 365 Business Premium sikkerhedshandlinger

Hvis du ikke tidligere har Microsoft 365 Business Premium, eller hvis du ikke allerede har en vejledning til sikkerhedshandlinger, kan denne artikel fungere som udgangspunkt. Hvis du allerede har en vejledning til sikkerhedshandlinger, kan du gennemse den i forhold til anbefalingerne i denne artikel.

Du kan bruge denne vejledning til at træffe beslutninger om prioriteter og opgaver for sikkerhedshændelser, som dit sikkerhedsteam skal udføre på Microsoft Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)).

| Foreslået hyppighed | Opgaver  |
|---------|---------|
| Daglige  | [Kontrollér din trusselssårbarhed](#check-your-threat-vulnerability).<br/>[Gennemse ventende handlinger i Løsningscenter](#review-pending-actions-in-the-action-center).<br/>[Gennemse enheder med trusselsregistreringer](#review-devices-with-threat-detections).<br/>[Få mere at vide om nye hændelser eller beskeder](#learn-about-new-incidents-or-alerts). |
| Ugentlige | [Overvåg og øg din Microsoft Secure-score](#monitor-and-improve-your-microsoft-secure-score).<br/>[Gennemse den sikre score for enheder](#review-the-secure-score-for-devices).<br/>[Gør din sikre score for enheder bedre](#improve-your-secure-score-for-devices). |
| Månedlige | [Kør rapporter](#run-reports).<br/>[Kør et simulerings selvstudium](#run-a-simulation-tutorial).<br/>[Udforsk Læringshubben](#explore-the-learning-hub). |
| Efter behov | [Brug dashboardet Threat Analytics](#use-the-threat-analytics-dashboard).<br/>[Kør en scanning eller en automatiseret undersøgelse](#run-a-scan-or-automated-investigation).<br/>[Afhjælp et element](#remediate-an-item). | 

Følgende afsnit indeholder flere oplysninger om hver opgave.
  
## <a name="suggested-daily-tasks"></a>Foreslåede daglige opgaver

Her er nogle forslag til sikkerhedsopgaver, som du kan udføre dagligt.

- [Kontrollér din trusselssårbarhed](#check-your-threat-vulnerability).
- [Gennemse ventende handlinger i Løsningscenter](#review-pending-actions-in-the-action-center).
- [Gennemse enheder med trusselsregistreringer](#review-devices-with-threat-detections).
- [Få mere at vide om nye hændelser eller beskeder](#learn-about-new-incidents-or-alerts).

### <a name="check-your-threat-vulnerability"></a>Kontrollér din trusselssårbarhed

Kort fortalt kan du få et snapshot af trusselssårbarheden ved at se på dashboardet Administration af sårbarheder. Den afspejler, hvor sårbar din organisation er over for cybersikkerhedstrusler. En høj eksponeringsscore betyder, at dine enheder er mere sårbare over for udnyttelse.

1. I Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) i navigationsruden skal du vælge **Administration af sårbarheder > Dashboard**.

2. Se din organisations eksponeringsscore. Hvis den er inden for det acceptable område eller "Høj", kan du gå videre. Hvis det ikke er det, skal du vælge **Øg score** for at få vist flere detaljer og sikkerhedsanbefalinger for at forbedre denne score.

Hvis du er opmærksom på din eksponeringsscore, hjælper det dig med at:

- Få hurtigt indsigt i og identificer vigtige ting om sikkerhedstilstanden i din organisation
- Registrer og reager på områder, der kræver undersøgelse eller handling for at forbedre den aktuelle tilstand
- Kommuniker med peers og administration om effekten af sikkerhedsindsatsen

### <a name="review-pending-actions-in-the-action-center"></a>Gennemse ventende handlinger i Løsningscenter

I takt med at der registreres trusler, spiller afhjælpningshandlinger ind. Afhængigt af den specifikke trussel, og hvordan dine sikkerhedsindstillinger er konfigureret, kan afhjælpningshandlinger udføres automatisk eller kun efter godkendelse, hvilket er grunden til, at disse bør overvåges regelmæssigt. Eksempler på afhjælpningshandlinger omfatter afsendelse af en fil til karantæne, stop af en proces i at køre og fjernelse af en planlagt opgave. Alle afhjælpningshandlinger spores i Løsningscenter.

1. Vælg **Løsningscenter** i navigationsruden i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)).

2. Vælg fanen **Ventende** for at få vist og godkende (eller afvise) ventende handlinger. Sådanne handlinger kan opstå som følge af antivirus- eller antimalwarebeskyttelse, automatiserede undersøgelser, manuelle svaraktiviteter eller live-svarsessioner.

3. Vælg fanen **Oversigt** for at få vist en liste over fuldførte handlinger.

### <a name="review-devices-with-threat-detections"></a>Gennemse enheder med trusselsregistreringer

Hvis du vil finde ud af, om du har nogen enheder, der har haft trusler mod dem, skal du gøre følgende.

1. På Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) i navigationsruden skal du vælge **Rapporter > Generelt > Sikkerhedsrapport**.

2. Rul ned til rækken Sårbare enheder. Hvis der blev registreret trusler på enheder, kan du se disse oplysninger i denne række.

### <a name="learn-about-new-incidents-or-alerts"></a>Få mere at vide om nye hændelser eller beskeder

1. Vælg **Hændelser** i navigationsmenuen i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)). Hændelser vises på siden med tilknyttede beskeder.

2. Vælg en besked for at åbne dens pop op-rude, hvor du kan få mere at vide om beskeden.

3. I pop op-vinduet kan du se beskedens titel, få vist en liste over aktiver (f.eks. slutpunkter eller brugerkonti), der er berørt, udføre tilgængelige handlinger og bruge links til at få vist flere oplysninger og endda åbne detaljesiden for den valgte besked.

### <a name="run-a-scan-or-automated-investigation"></a>Kør en scanning eller en automatiseret undersøgelse

1. Vælg Enhedslager i Microsoft 365 Defender-portalen (https://security.microsoft.com)vælg Enhedslager i navigationsruden.

2. Vælg en enhed for at åbne det tilhørende pop op-panel, og gennemse de oplysninger, der vises.

3. Vælg ellipsen (...) for at åbne handlingsmenuen.

4. Vælg en handling, f.eks **. Kør antivirusscanning** eller **Start automatiseret undersøgelse**.

## <a name="suggested-weekly-tasks"></a>Foreslåede ugentlige opgaver

Her er nogle forslag til vigtige sikkerhedsopgaver, som i det mindste skal udføres ugentligt.

- [Overvåg og øg din Microsoft Secure-score](#monitor-and-improve-your-microsoft-secure-score).
- [Gennemse den sikre score for enheder](#review-the-secure-score-for-devices).
- [Gør din sikre score for enheder bedre](#improve-your-secure-score-for-devices).

### <a name="monitor-and-improve-your-microsoft-secure-score"></a>Overvåg og øg din Microsoft Secure-score

Microsoft Secure Score er en måling af en organisations sikkerhedsholdning, hvor et højere antal angiver, at der er behov for færre forbedringshandlinger.

Secure Score hjælper organisationer med at:

- Rapportér om den aktuelle tilstand af organisationens sikkerhedsholdning.
- Forbedre deres sikkerhedsholdning ved at levere registrering, synlighed, vejledning og kontrol.
- Sammenlign med benchmarks, og fastlæg KPI'er (key performance indicators).

1. Hvis du vil kontrollere din sikre score, skal du vælge **Sikker score** i portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i navigationsruden. 

2. Gennemse og træd beslutninger om afhjælpninger og handlinger for at forbedre din overordnede Microsoft Secure Score.

### <a name="review-the-secure-score-for-devices"></a>Gennemse den sikre score for enheder

Microsoft Secure-scoren for enhedskortet findes også i dashboardet til administration af sårbarheder. Dette kort viser din aktuelle score, og en højere score angiver, at dine slutpunkter er mere modstandsdygtige over for cyberangreb. Det afspejler sikkerhedstilstanden for alle enheder samlet.

Dataene på dette kort er produktet af en omhyggelig og løbende opdagelsesproces for sårbarheder. Den samles med konfigurationsregistreringsvurderinger, der løbende:

- Sammenlign indsamlede konfigurationer med de indsamlede benchmarks for at finde forkert konfigurerede aktiver
- Knyt konfigurationer til sikkerhedsrisici, der kan afhjælpes eller afhjælpes delvist (risikoreduktion)
- Indsaml og vedligehold benchmarks for konfiguration af bedste praksis (leverandører, sikkerhedsopdateringer, interne forskningsteams)
- Indsaml og overvåg ændringer af konfigurationstilstanden for sikkerhedskontrol fra alle aktiver

### <a name="improve-your-secure-score-for-devices"></a>Gør din sikre score for enheder bedre

Gør sikkerhedskonfigurationen bedre ved at løse problemer ved hjælp af listen over sikkerhedsanbefalinger. Når du gør det, forbedres din Microsoft Secure Score for Devices, og din organisation bliver mere modstandsdygtig mod cybersikkerhedstrusler og sårbarheder fremover. Det er altid værd at bruge tid på at gennemse og forbedre din score.

1. Hvis du vil kontrollere din sikre score, skal du vælge **Sikker score** i portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) i navigationsruden.

2. Vælg en af kategorierne på kortet **Microsoft Secure Score for Devices** på dashboardet Defender Vulnerability Management. Der vises en liste over anbefalinger, der er relateret til den pågældende kategori, sammen med anbefalinger.

3. Vælg et element på listen for at få vist oplysninger, der er relateret til anbefalingen.

4. Vælg **Afhjælpningsindstillinger**.

5. Læs beskrivelsen for at forstå konteksten af problemet, og hvad du derefter skal gøre. Vælg en forfaldsdato, tilføj noter, og vælg Eksportér alle afhjælpningsaktivitetsdata til CSV, så du kan vedhæfte dem i en mail til opfølgning. En bekræftelsesmeddelelse fortæller dig, at afhjælpningsopgaven er blevet oprettet.

6. Send en opfølgende mail til it-administratoren, og giv den tid, du har tildelt afhjælpningen, mulighed for at overføre i systemet.

7. Gå tilbage til kortet Microsoft Secure Score for Devices på dashboardet. Antallet af anbefalinger til sikkerhedskontroller er faldet som følge af dine handlinger.

8. Vælg **Sikkerhedskontrolelementer** for at gå tilbage til siden Sikkerhedsanbefalinger. Det element, du har behandlet, er ikke længere angivet der, hvilket resulterer i, at din Microsofts sikre score forbedres.

## <a name="suggested-monthly-tasks"></a>Foreslåede månedlige opgaver

Disse opgaver bør udføres mindst en gang om måneden, hvis ikke oftere. 

- [Kør rapporter](#run-reports).
- [Kør et simulerings selvstudium](#run-a-simulation-tutorial).
- [Udforsk Læringshubben](#explore-the-learning-hub).

### <a name="run-reports"></a>Kør rapporter

Der findes flere rapporter på Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)).

1. Vælg **Rapporter** i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) i navigationsruden.

2. Vælg en rapport, der skal gennemses. Hver rapport viser mange relevante kategorier for den pågældende rapport.

3. Vælg **Vis detaljer** for at få vist flere oplysninger for hver kategori.

4. Vælg titlen på en bestemt trussel for at få vist detaljer, der er specifikke for den.

### <a name="run-a-simulation-tutorial"></a>Kør et simulerings selvstudium

Det er altid en god idé at øge sikkerhedsforberedeligheden for dig og dit team gennem træning. Du kan få adgang til simuleringsvejledninger på portalen Microsoft 365 Defender. Selvstudierne dækker flere typer cybertrusler. 

Sådan kommer du i gang:

1. Vælg **Selvstudier** i navigationsruden i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)).

2. Læs gennemgangen af et selvstudium, du er interesseret i at køre, og download derefter filen, eller kopiér det script, der er nødvendigt for at køre simuleringen i henhold til instruktionerne.

### <a name="explore-the-learning-hub"></a>Udforsk Læringshub

Der er mange områder i Læringshubben, hvor du kan øge din viden om mange af de trusler, der er derude, og hvordan du håndterer dem. Vi anbefaler, at du og dine teams bruger lidt tid på at udforske de ressourcer, der tilbydes, især i sektionerne Microsoft 365 Defender og Slutpunkter.

1. Vælg **Læringshub** i navigationsruden i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)).

2. Vælg et område, f.eks. **Microsoft 365 Defender** eller **slutpunkter**.

3. Vælg et element for at få mere at vide om hvert koncept. 

> [!NOTE]
> Nogle ressourcer i Læringshub kan dække funktioner, der faktisk ikke er inkluderet i Microsoft 365 Business Premium. Avancerede jagtegenskaber er f.eks. inkluderet i virksomhedsabonnementer, f.eks. Defender for Endpoint Plan 2 eller Microsoft 365 Defender, men ikke i Microsoft 365 Business Premium. [Sammenlign sikkerhedsfunktioner i Microsoft 365-planer for små og mellemstore virksomheder](../security/defender-business/compare-mdb-m365-plans.md).

## <a name="as-needed"></a>Efter behov

Udfør disse opgaver efter behov eller efter behov:

- [Brug dashboardet Threat Analytics](#use-the-threat-analytics-dashboard).
- [Kør en scanning eller en automatiseret undersøgelse](#run-a-scan-or-automated-investigation).
- [Afhjælp et element](#remediate-an-item).

### <a name="use-the-threat-analytics-dashboard"></a>Brug dashboardet Threat Analytics

Brug dashboardet til trusselsanalyse til at få et overblik over det aktuelle trusselsbillede ved at fremhæve rapporter, der er mest relevante for din organisation. 

1. I Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)) i navigationsruden skal du vælge **Trusselsanalyse** for at få vist dashboardet Threat Analytics. 

   Dashboardet opsummerer truslerne i følgende afsnit:

   - Seneste trusler – viser de senest publicerede eller opdaterede trusselsrapporter sammen med antallet af aktive og løste beskeder.
   - Trusler med stor indvirkning – viser de trusler, der har den største indvirkning på din organisation. I dette afsnit vises en liste over trusler med det højeste antal aktive og løste beskeder først.
   - Højeste eksponering – viser trusler med de højeste eksponeringsniveauer først. Eksponeringsniveauet for en trussel beregnes ved hjælp af to oplysninger: hvor alvorlige sårbarheder, der er knyttet til truslen, og hvor mange enheder i organisationen der kan udnyttes af disse sikkerhedsrisici.

2. Vælg titlen på den, du vil undersøge, og læs den tilknyttede rapport. 

3. Du kan også gennemse hele analytikerrapporten for at få flere oplysninger eller vælge andre overskrifter for at få vist relaterede hændelser, påvirkede aktiver og eksponering og afhjælpninger.

### <a name="remediate-an-item"></a>Afhjælp et element

Microsoft 365 Business Premium omfatter flere afhjælpningshandlinger. Disse handlinger omfatter manuelle svarhandlinger, handlinger efter automatiseret undersøgelse og liveresponshandlinger.

1. Vælg **Enhedslager** i navigationsruden i Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)).

   :::image type="content" source="./../media/defender-business/mdb-deviceinventory.png" alt-text="Skærmbillede af enhedslager":::

2. Vælg en enhed, f.eks. en enhed med et højt risiko- eller eksponeringsniveau. Der åbnes en pop op-rude, og der vises flere oplysninger om beskeder og hændelser, der genereres for det pågældende element, som vist på følgende billede:  

   :::image type="content" source="./../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Skærmbillede af pop op-ruden for en valgt enhed":::

3. Få vist de oplysninger, der vises, i pop op-vinduet. Vælg ellipsen (...) for at åbne en menu, der viser en liste over tilgængelige handlinger, som vist på følgende billede: 

   :::image type="content" source="./../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Skærmbillede af tilgængelige handlinger for en valgt enhed":::

4. Vælg en tilgængelig handling. Du kan f.eks. vælge **Kør antivirusscanning**, hvilket medfører, at Microsoft Defender Antivirus starter en hurtig scanning på enheden. Du kan også vælge **Start automatiseret undersøgelse** for at udløse en automatiseret undersøgelse på enheden.

#### <a name="remediation-actions-in-microsoft-365-business-premium"></a>Afhjælpningshandlinger i Microsoft 365 Business Premium

I følgende tabel opsummeres afhjælpningshandlinger, der er tilgængelige i Microsoft 365 Business Premium:

| Kilde  | Handlinger  |
|---------|---------|
| Automatiserede undersøgelser      | - Sæt en fil i karantæne <br/>- Fjern en registreringsdatabasenøgle <br/>- Dræb en proces <br/>- Stop en tjeneste <br/>- Deaktiver en driver <br/>- Fjern en planlagt opgave        |
| Handlinger for manuelt svar   | - Kør antivirusscanning <br/>- Isoler enhed <br/>- Stop og sæt karantæne <br/>– Tilføj en indikator for at blokere eller tillade en fil       |
| Live-svar  | - Indsaml tekniske data <br/>- Analysér en fil <br/>- Kør et script <br/>- Send en mistænkelig enhed til Microsoft til analyse <br/>- Afhjælpning af en fil <br/>- Proaktiv jagt efter trusler  |




## <a name="see-also"></a>Se også

[Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)