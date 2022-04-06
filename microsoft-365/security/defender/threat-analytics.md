---
title: Trusselsanalyse i Microsoft 365 Defender
ms.reviewer: ''
description: Få mere at vide om nye trusler og angrebsteknikker, og hvordan du stopper dem. Vurder deres indvirkning på din organisation, og evaluer din organisations robusthed.
keywords: trusselsanalyse, risikoevaluering, Microsoft 365 Defender, M365D, afhjælpningsstatus, sikker konfiguration, Microsoft Defender for Office 365, Microsoft Defender for Office 365  threat analytics, MDO threat analytics, integrated MDE and MDO threat analytics data, threat analytics data integration, integrated Microsoft 365 Defender threat analytics
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 02d7a1e1d80d7891219c9bcf18076b858f4fb1b8
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663308"
---
# <a name="threat-analytics-in-microsoft-365-defender"></a>Trusselsanalyse i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> Vil du opleve Microsoft 365 Defender? Du kan [evaluere det i et laboratoriemiljø](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) eller [køre dit pilotprojekt i produktion](m365d-pilot.md?ocid=cx-evalpilot).
>

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Threat Analytics er vores løsning til trusselsintelligens i produktet fra ekspertforskere i Microsoft-sikkerhed. Den er designet til at hjælpe sikkerhedsteams med at være så effektive som muligt, mens de står over for nye trusler, f.eks.:

- Aktive trusselsaktører og deres kampagner
- Populære og nye angrebsteknikker
- Kritiske sikkerhedsrisici
- Almindelige angrebsoverflader
- Udbredt malware

Se denne korte video for at få mere at vide om, hvordan trusselsanalyser kan hjælpe dig med at spore de nyeste trusler og stoppe dem.

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWwJfU]

Du kan få adgang til trusselsanalyser enten fra øverste venstre side af Microsoft 365 sikkerhedsportalens navigationslinje eller fra et dedikeret dashboardkort, der viser de største trusler mod din organisation, både hvad angår indvirkning og eksponering.

:::image type="content" source="../../media/threat-analytics/ta_inlandingpage_mtp.png" alt-text="Landingssiden for trusselsanalyse" lightbox="../../media/threat-analytics/ta_inlandingpage_mtp.png":::

Trusler med stor indvirkning har det største potentiale til at forårsage skade, mens trusler med høj eksponering er dem, som dine aktiver er mest sårbare over for. Hvis du får synlighed på aktive eller igangværende kampagner, og du ved, hvad du skal gøre via trusselsanalyser, kan det hjælpe med at udstyre dit team med sikkerhedshandlinger med velunderbyggede beslutninger.

_Her kan du få adgang til trusselsanalyser_

Med mere avancerede modstandere og nye trusler, der dukker op ofte og udbredt, er det vigtigt at kunne hurtigt:

- Identificer og reager på nye trusler
- Få mere at vide om, om du i øjeblikket er under angreb
- Vurder effekten af truslen mod dine aktiver
- Gennemse din robusthed mod eller eksponering for truslerne
- Identificer de afhjælpnings-, genoprettelses- eller forebyggelseshandlinger, du kan udføre for at stoppe eller indeholde truslerne

Hver rapport indeholder en analyse af en sporet trussel og en omfattende vejledning i, hvordan man kan forsvare sig mod denne trussel. Den indeholder også data fra dit netværk, der angiver, om truslen er aktiv, og om du har gældende beskyttelse på plads.

## <a name="view-the-threat-analytics-dashboard"></a>Få vist dashboardet til trusselsanalyse

Dashboardet til trusselsanalyse ([security.microsoft.com/threatanalytics3](https://security.microsoft.com/threatanalytics3)) fremhæver de rapporter, der er mest relevante for din organisation. Den opsummerer truslerne i følgende afsnit:

- **Seneste trusler** – viser de senest publicerede eller opdaterede trusselsrapporter sammen med antallet af aktive og løste beskeder.
- **Trusler med stor indvirkning** – viser de trusler, der har den største indvirkning på din organisation. I dette afsnit vises en liste over trusler med det højeste antal aktive og løste beskeder først.
- **Højeste eksponering** – viser trusler med de højeste eksponeringsniveauer først. Eksponeringsniveauet for en trussel beregnes ved hjælp af to oplysninger: hvor alvorlige sårbarheder, der er knyttet til truslen, og hvor mange enheder i organisationen der kan udnyttes af disse sikkerhedsrisici.

Vælg en trussel fra dashboardet for at få vist rapporten for den pågældende trussel.

:::image type="content" source="../../media/threat-analytics/ta_dashboard_mtp.png" alt-text="Dashboardet til trusselsanalyse" lightbox="../../media/threat-analytics/ta_dashboard_mtp.png":::

_Dashboard til trusselsanalyse. Du kan også vælge søgefeltet for at angive et nøgleord, der er relateret til den trusselsanalyserapport, du vil læse._

## <a name="view-a-threat-analytics-report"></a>Få vist en rapport over trusselsanalyse

Hver rapport til trusselsanalyse indeholder oplysninger i flere afsnit:

- [**Oversigt**](#overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses)
- [**Analytikerrapport**](#analyst-report-get-expert-insight-from-microsoft-security-researchers)
- [**Relaterede hændelser**](#related-incidents-view-and-manage-related-incidents)
- [**Påvirkede aktiver**](#impacted-assets-get-list-of-impacted-devices-and-mailboxes)
- [**Forhindrede mailforsøg**](#prevented-email-attempts-view-blocked-or-junked-threat-emails)
- [**Eksponering & afhjælpninger**](#exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices)

### <a name="overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses"></a>Oversigt: Forstå hurtigt truslen, vurder dens virkning og gennemgå forsvar

Afsnittet **Oversigt** indeholder et eksempel på den detaljerede analytikerrapport. Den indeholder også diagrammer, der fremhæver virkningen af truslen mod din organisation og din eksponering via forkert konfigurerede og ikke-kompatible enheder.

:::image type="content" source="../../media/threat-analytics/ta_overview_mtp.png" alt-text="Oversigtsafsnittet i en rapport til trusselsanalyse" lightbox="../../media/threat-analytics/../../media/threat-analytics/ta_overview_mtp.png":::

_Oversigtssektion i en rapport til trusselsanalyse_

#### <a name="assess-impact-on-your-organization"></a>Vurder indvirkningen på din organisation

Hver rapport indeholder diagrammer, der er designet til at give oplysninger om en trussels organisatoriske indvirkning:

- **Relaterede hændelser** – giver et overblik over virkningen af den sporede trussel for din organisation med følgende data:
  - Antal aktive beskeder og antallet af aktive hændelser, de er knyttet til
  - Alvorsgrad af aktive hændelser
- **Beskeder over tid** – viser antallet af relaterede **aktive** og **løste** beskeder over tid. Antallet af løste beskeder angiver, hvor hurtigt din organisation reagerer på beskeder, der er knyttet til en trussel. Ideelt set skal diagrammet vise beskeder, der er løst inden for nogle få dage.
- **Påvirkede aktiver** – viser antallet af forskellige enheder og mailkonti (postkasser), der i øjeblikket har mindst én aktiv besked tilknyttet den sporede trussel. Beskeder udløses for postkasser, der har modtaget trusselsmails. Gennemse politikker på både organisations- og brugerniveau for tilsidesættelser, der forårsager levering af trusselsmails.
- **Forhindrede forsøg på mail** – viser antallet af mails fra de seneste syv dage, der enten blev blokeret før levering eller leveret til mappen uønsket mail.

#### <a name="review-security-resilience-and-posture"></a>Gennemse robusthed og arbejdsholdning for sikkerhed

Hver rapport indeholder diagrammer, der giver et overblik over, hvor modstandsdygtig din organisation er mod en given trussel:

- **Status for sikker konfiguration** – viser antallet af enheder med forkert konfigurerede sikkerhedsindstillinger. Anvend de anbefalede sikkerhedsindstillinger for at afhjælpe truslen. Enheder betragtes som **sikre** , hvis de har anvendt _alle_ de sporede indstillinger.
- **Status for programrettelse af sårbarheder** – viser antallet af sårbare enheder. Anvend sikkerhedsopdateringer eller programrettelser for at løse sårbarheder, der udnyttes af truslen.

#### <a name="view-reports-per-threat-tags"></a>Få vist rapporter pr. trusselstags

Du kan filtrere listen over trusselsrapporter og få vist de mest relevante rapporter i henhold til et bestemt trusselsmærke (kategori) eller en rapporttype.

- **Trusselstags** – hjælper dig med at få vist de mest relevante rapporter i henhold til en bestemt trusselskategori. For eksempel alle rapporter relateret til ransomware.
- **Rapporttyper** – hjælper dig med at få vist de mest relevante rapporter i henhold til en bestemt rapporttype. Det kan f.eks. være alle rapporter, der dækker værktøjer og teknikker.
- **Filtre** – hjælper dig med effektivt at gennemse listen over trusselsrapporter og filtrere visningen baseret på et bestemt trusselsmærke eller en rapporttype. For eksempel gennemgå alle trusselsrapporter relateret til ransomware-kategori eller trusselsrapporter, der dækker sårbarheder.

##### <a name="how-does-it-work"></a>Hvordan fungerer det?

Microsoft Threat Intelligence-teamet har føjet trusselskoder til hver trusselsrapport:

- Der er nu fire trusselskoder tilgængelige:
  - Ransomware
  - Phishing
  - Sikkerhedsrisici
  - Aktivitetsgruppe
- Trusselstags vises øverst på siden til trusselsanalyse. Der er tællere for antallet af tilgængelige rapporter under hvert mærke.

  :::image type="content" source="../../media/threat-analytics/ta-threattags-mtp.png" alt-text="Trusselskoderne" lightbox="../../media/threat-analytics/ta-threattags-mtp.png":::

- Listen kan også sorteres efter trusselskoder:

  :::image type="content" source="../../media/threat-analytics//ta-taglist-mtp.png" alt-text="Afsnittet Threat Tags" lightbox="../../media/threat-analytics//ta-taglist-mtp.png":::

- Filtre er tilgængelige pr. trusselskode og rapporttype:

  :::image type="content" source="../../media/threat-analytics/ta-threattag-filters-mtp.png" alt-text="Siden Filtre" lightbox="../../media/threat-analytics/ta-threattag-filters-mtp.png":::

### <a name="analyst-report-get-expert-insight-from-microsoft-security-researchers"></a>Analytikerrapport: Få ekspertindsigt fra Microsofts sikkerhedsforskere

I afsnittet **Analytikerrapport** kan du læse den detaljerede ekspertudskrivning. De fleste rapporter indeholder detaljerede beskrivelser af angrebskæder, herunder taktikker og teknikker, der er knyttet til MITRE ATT-&CK-strukturen, udtømmende lister over anbefalinger og effektiv vejledning [til trusselsjagt](advanced-hunting-overview.md) .

[Få mere at vide om analytikerrapporten](threat-analytics-analyst-reports.md)

### <a name="related-incidents-view-and-manage-related-incidents"></a>Relaterede hændelser: Få vist og administrer relaterede hændelser

Fanen **Relaterede hændelser** indeholder en liste over alle hændelser, der er relateret til den sporede trussel. Du kan tildele hændelser eller administrere beskeder, der er knyttet til hver hændelse. 

:::image type="content" source="../../media/threat-analytics/ta_related_incidents_mtp.png" alt-text="Afsnittet relaterede hændelser i en rapport til trusselsanalyse" lightbox="../../media/threat-analytics/ta_related_incidents_mtp.png":::

_Afsnittet Relaterede hændelser i en rapport til trusselsanalyse_

### <a name="impacted-assets-get-list-of-impacted-devices-and-mailboxes"></a>Påvirkede aktiver: Hent en liste over berørte enheder og postkasser

Et aktiv anses for at være påvirket, hvis det påvirkes af en aktiv, uløst besked. Under fanen **Påvirkede aktiver** vises følgende typer af påvirkede aktiver:

- **Påvirkede enheder** – slutpunkter, der har uløste Microsoft Defender for Endpoint beskeder. Disse beskeder udløses typisk ved observationer af kendte trusselsindikatorer og -aktiviteter.
- **Påvirkede postkasser – postkasser**, der har modtaget mails, der er udløst Microsoft Defender for Office 365 beskeder. Selvom de fleste meddelelser, der udløser beskeder, typisk er blokeret, kan politikker på bruger- eller organisationsniveau tilsidesætte filtre.

:::image type="content" source="../../media/threat-analytics/ta_impacted_assets_mtp.png" alt-text="Sektionen Med indvirkning på aktiver i en rapport til trusselsanalyse" lightbox="../../media/threat-analytics/ta_impacted_assets_mtp.png":::

_Sektionen Påvirkede aktiver i en rapport til trusselsanalyse_

### <a name="prevented-email-attempts-view-blocked-or-junked-threat-emails"></a>Forhindrede mailforsøg: Få vist blokerede eller uønsket trusselsmails

Microsoft Defender for Office 365 blokerer typisk mails med kendte trusselsindikatorer, herunder skadelige links eller vedhæftede filer. I nogle tilfælde sender proaktive filtreringsmekanismer, der søger efter mistænkeligt indhold, i stedet trusselsmails til mappen med uønsket mail. I begge tilfælde reduceres chancerne for, at truslen lancerer malwarekode på enheden.

Fanen **Forhindrede mailforsøg** viser alle de mails, der enten er blevet blokeret før levering eller sendt til mappen med uønsket mail af Microsoft Defender for Office 365.

:::image type="content" source="../../media/threat-analytics/ta_prevented_email_attempts_mtp.png" alt-text="Sektionen forhindrede mailforsøg i en rapport til trusselsanalyse" lightbox="../../media/threat-analytics/ta_prevented_email_attempts_mtp.png":::

_Sektionen Forhindrede mailforsøg i en rapport med trusselsanalyse_

### <a name="exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices"></a>Eksponering og afhjælpninger: Gennemse listen over afhjælpninger og status for dine enheder

I afsnittet **Eksponering & afhjælpninger** skal du gennemse listen over specifikke anbefalinger, der kan handles på, som kan hjælpe dig med at øge din organisations robusthed mod truslen. Listen over sporede afhjælpninger omfatter:

- **Sikkerhedsopdateringer** – installation af understøttede softwaresikkerhedsopdateringer for sikkerhedsrisici, der findes på onboardede enheder
- **Understøttede sikkerhedskonfigurationer**
  - Skybaseret beskyttelse  
  - Potentielt uønsket programbeskyttelse (PUA)
  - Beskyttelse i realtid

Afhjælpningsoplysninger i dette afsnit omfatter data fra [Håndtering af trusler og sikkerhedsrisici](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt), som også indeholder detaljerede oplysninger om detailudledning fra forskellige links i rapporten.

:::image type="content" source="../../media/threat-analytics/ta_mitigations_mtp.png" alt-text="Afsnittet afhjælpninger i en rapport til trusselsanalyse, der viser oplysninger om sikker konfiguration" lightbox="../../media/threat-analytics/ta_mitigations_mtp.png":::

:::image type="content" source="../../media/threat-analytics/ta_mitigations_mtp2.png" alt-text="Afsnittet afhjælpninger i en rapport til trusselsanalyse, der viser oplysninger om sårbarhed" lightbox="../../media/threat-analytics/ta_mitigations_mtp2.png":::

_Afsnittet Eksponering & afhjælpninger i en rapport til trusselsanalyse_

## <a name="set-up-email-notifications-for-report-updates"></a>Konfigurer mailmeddelelser for rapportopdateringer

Du kan konfigurere mailmeddelelser, der sender dig opdateringer om trusselsanalyserapporter.

Hvis du vil konfigurere mailmeddelelser for trusselsanalyserapporter, skal du udføre følgende trin:

1. Vælg **Indstillinger** i Microsoft 365 Defender margentekst. Vælg **Microsoft 365 Defender** på listen over indstillinger.
 
![Skærmbillede med "Indstillinger" og "Microsoft 365 Defender" fremhævet med rødt](../../media/threat-analytics/ta_create_notification_0.png)

2. Vælg **MailmeddelelserDeaktiver** >  analyse, og vælg knappen **+ Opret en meddelelsesregel**. Der vises et pop op-vindue.

![Skærmbillede med "+ Opret en meddelelsesregel" fremhævet med rødt](../../media/threat-analytics/ta_create_notification_1.png)

3. Følg de trin, der er angivet i pop op-vinduet. Først skal du give din nye regel et navn. Beskrivelsesfeltet er valgfrit, men der kræves et navn. Du kan slå reglen til eller fra ved hjælp af afkrydsningsfeltet under beskrivelsesfeltet.

> [!NOTE]
> Navne- og beskrivelsesfelterne for en ny meddelelsesregel accepterer kun engelske bogstaver og tal. De accepterer ikke mellemrum, tankestreger, understregningstegn eller andre tegnsætningstegn.

![Skærmbillede af navngivningsskærmen, hvor alle felter er udfyldt, og afkrydsningsfeltet "Slå regel til" er markeret](../../media/threat-analytics/ta_create_notification_2.png)

4. Vælg, hvilken type rapporter du vil have besked om. Du kan vælge mellem at blive opdateret om alle nyligt publicerede eller opdaterede rapporter eller kun de rapporter, der har en bestemt kode eller type.

![Skærmbillede af meddelelsesskærmen med Ransomware-tags valgt og en rullemenu til åbne typer](../../media/threat-analytics/ta_create_notification_3.png)

5. Tilføj mindst én modtager for at modtage meddelelsesmailene. Du kan også bruge denne skærm til at kontrollere, hvordan meddelelserne modtages, ved at sende en testmail.

![Skærmbillede af skærmbilledet for modtagere. Der er angivet tre modtagere, og der er sendt en testmail, som angivet med et grønt flueben](../../media/threat-analytics/ta_create_notification_4.png)

6. Gennemse din nye regel. Hvis der er noget, du vil ændre, skal du vælge knappen **Rediger** i slutningen af hver undersektion. Når gennemgangen er fuldført, skal du vælge knappen **Opret regel** .

![Skærmbillede af gennemgangsskærmen. En redigeringsknap er fremhævet med rødt](../../media/threat-analytics/ta_create_notification_5.png)

7. Tillykke! Den nye regel er blevet oprettet. Vælg knappen **Udført** for at fuldføre processen og lukke pop op-vinduet.

![Skærmbillede af skærmbilledet med den oprettede regel. En regel, der er oprettet korrekt, viser grønne markeringer langs margenteksten og et stort grønt tjek i hovedområdet på skærmen](../../media/threat-analytics/ta_create_notification_6.png)

8. Din nye regel vises nu på listen over mailmeddelelser om Threat Analytics.

![Skærmbillede af listen over regler for mailbeskeder på skærmen Indstillinger](../../media/threat-analytics/ta_create_notification_7.png)

## <a name="additional-report-details-and-limitations"></a>Yderligere rapportoplysninger og -begrænsninger

> [!NOTE]
> Som en del af den samlede sikkerhedsoplevelse er trusselsanalyse nu ikke kun tilgængelig for Microsoft Defender for Endpoint, men også for Microsoft Defender for Office E5-licensindehavere.
>
> Hvis du ikke bruger Microsoft 365-sikkerhedsportalen (Microsoft 365 Defender), kan du også se rapportoplysningerne (uden Microsoft Defender for Office data) på Microsoft Defender Security Center-portalen ( Microsoft Defender for Endpoint).

Hvis du vil have adgang til rapporter over trusselsanalyser, skal du have visse roller og tilladelser. Se [Brugerdefinerede roller i rollebaseret adgangskontrol for at få Microsoft 365 Defender](custom-roles.md) for at få flere oplysninger.

- Hvis du vil have vist beskeder, hændelser eller påvirkede aktiver, skal du have tilladelser til Microsoft Defender for at få vist Office eller Microsoft Defender for Endpoint beskeddata eller begge dele.
- Hvis du vil have vist forhindrede mailforsøg, skal du have tilladelser til Microsoft Defender til Office jagtdata.
- Hvis du vil have vist afhjælpninger, skal du have tilladelse til at Håndtering af trusler og sikkerhedsrisici data i Microsoft Defender for Endpoint.

Når du ser på dataene til trusselsanalyse, skal du huske følgende faktorer:

- Diagrammer afspejler kun afhjælpninger, der spores. Se rapportens oversigt for yderligere afhjælpninger, der ikke vises i diagrammerne.
- Afhjælpninger garanterer ikke fuldstændig robusthed. De angivne afhjælpninger afspejler de bedst mulige handlinger, der er nødvendige for at forbedre robusthed.
- Enheder tælles som "utilgængelige", hvis de ikke har sendt data til tjenesten.
- Antivirusrelaterede statistikker er baseret på Microsoft Defender Antivirus indstillinger. Enheder med antivirusløsninger fra tredjepart kan vises som "eksponeret".

## <a name="related-articles"></a>Relaterede artikler

- [Find proaktivt trusler med avanceret jagt](advanced-hunting-overview.md)
- [Forstå afsnittet om analytikerrapport](threat-analytics-analyst-reports.md)
- [Vurder og løs sikkerhedsmæssige svagheder og eksponeringer](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
