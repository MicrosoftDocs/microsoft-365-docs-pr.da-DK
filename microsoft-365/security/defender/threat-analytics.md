---
title: Trusselsanalyse i Microsoft 365 Defender
ms.reviewer: ''
description: Få mere at vide om nye trusler og angrebsteknikker, og hvordan du stopper dem. Vurder deres indvirkning på din organisation, og vurder din organisatoriske fleksibilitet.
keywords: trusselsanalyse, risikoevaluering, Microsoft 365 Defender, M365D, afhjælpningsstatus, sikker konfiguration, Microsoft Defender til Office 365, Microsoft Defender til Office 365-trusselsanalyse, MDO-trusselsanalyse, integrerede MDE- og MDO-trusselsanalysedata, integration af trusselsanalysedata, integreret Microsoft 365 Defender trusselsanalyse
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
ms.openlocfilehash: 5cb9f0db07ad29618e0dc9d053f4904a70ca52f6
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63606453"
---
# <a name="threat-analytics-in-microsoft-365-defender"></a>Trusselsanalyse i Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Gælder for:**

- Microsoft 365 Defender

> Vil du gerne Microsoft 365 Defender? Du kan [evaluere det i et labmiljø](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) eller [køre dit pilotprojekt i produktion](m365d-pilot.md?ocid=cx-evalpilot).
>

[!INCLUDE [Prerelease](../includes/prerelease.md)]

Trusselsanalyse er vores produktbaserede trusselsintelligens-løsning fra ekspert Microsoft-sikkerhedseksperter. Den er udviklet til at hjælpe sikkerhedsteams med at være så effektive som muligt, mens de står over for nye trusler, f.eks.:

- Aktive trusler og deres kampagner
- Populære og nye angrebsteknikker
- Kritiske sårbarheder
- Almindelige angrebsoverflader
- Mest udbredte malware

Se denne korte video for at få mere at vide om, hvordan trusselsanalyse kan hjælpe dig med at spore de seneste trusler og stoppe dem.

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWwJfU]

Du kan få adgang til trusselsanalyse enten fra den øverste venstre side af Microsoft 365-sikkerhedsportalens navigationslinje eller fra et dedikeret dashboardkort, der viser de vigtigste trusler mod din organisation, både med hensyn til påvirkning og eksponering.

![Billede af dashboardet for trusselsanalyse.](../../media/threat-analytics/ta_inlandingpage_mtp.png)

Trusler med høj effekt har størst risiko for at forvolde skade, mens høje eksponeringstrusler er dem, som aktiverne er mest følsomme over for. Få overblik over aktive eller igangværende kampagner og viden om, hvad du skal gøre, via trusselsanalyse, kan hjælpe dit sikkerhedsteam med at træffe velovervejede beslutninger.

_Hvor får du adgang til trusselsanalyse?_

Med mere avancerede adversar og nye trusler, der opstår ofte og med stor grad, er det vigtigt at kunne hurtigt:

- Identificer og reager på fremspirende trusler
- Få mere at vide om, om du er under angreb i øjeblikket
- Vurder virkningen af trussel mod dine aktiver
- Gennemgå din fleksibilitet over for eller eksponering for truslerne
- Identificer afhjælpnings-, genoprettelses- eller forebyggelseshandlinger, du kan udføre for at stoppe eller inddæmme truslerne

Hver rapport indeholder en analyse af en registret trussel og omfattende vejledning til, hvordan du kan beskytte dig mod denne trussel. Den indeholder også data fra dit netværk, der angiver, om trussel er aktiv, og om du har gældende beskyttelse på plads.

## <a name="view-the-threat-analytics-dashboard"></a>Få vist dashboardet for trusselsanalyse

Dashboardet trusselsanalyse ([security.microsoft.com/threatanalytics3](https://security.microsoft.com/threatanalytics3)) fremhæver de rapporter, der er mest relevante for din organisation. Den opsummerer truslerne i følgende afsnit:

- **Seneste trusler –** viser de senest udgivne eller opdaterede trusselsrapporter samt antallet af aktive og løste beskeder.
- **Højbelastningstrusler viser** en liste over de trusler, der har størst påvirkning på organisationen. I dette afsnit vises trusler med det højeste antal aktive og løste beskeder først.
- **Højeste eksponering** – viser trusler med de højeste eksponeringsniveauer først. Eksponeringsniveauet for en trussel beregnes ved hjælp af to oplysninger: hvor alvorlige sårbarheder, der er knyttet til truslerne, og hvor mange enheder i organisationen, der kan udnyttes af disse sårbarheder.

Vælg en trussel fra dashboardet for at få vist rapporten for den pågældende trussel.

![Skærmbillede af dashboard for trusselsanalyse.](../../media/threat-analytics/ta_dashboard_mtp.png)

_Dashboard for trusselsanalyse. Du kan også vælge feltet Søg, som skal have en nøgle i et nøgleord, der er relateret til rapporten om trusselsanalyse, som du gerne vil læse._

## <a name="view-a-threat-analytics-report"></a>Få vist en rapport over trusselsanalyse

Hver trusselsanalyserapport indeholder oplysninger i flere sektioner:

- [**Oversigt**](#overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses)
- [**Analytikerrapport**](#analyst-report-get-expert-insight-from-microsoft-security-researchers)
- [**Relaterede hændelser**](#related-incidents-view-and-manage-related-incidents)
- [**På påvirkede aktiver**](#impacted-assets-get-list-of-impacted-devices-and-mailboxes)
- [**Forhindrede forsøg på mail**](#prevented-email-attempts-view-blocked-or-junked-threat-emails)
- [**Afhjælpning af & eksponering**](#exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices)

### <a name="overview-quickly-understand-the-threat-assess-its-impact-and-review-defenses"></a>Oversigt: Forstå hurtigt truslen, vurder dens virkning, og gennemse forsvar

Afsnittet **Oversigt** giver et eksempel på den detaljerede analytikerrapport. Den indeholder også diagrammer, der fremhæver virkningen af truslen mod din organisation og din eksponering via forkert konfigurerede og ikke-kompatible enheder.

![Billede af afsnittet Oversigt i en rapport over trusselsanalyse.](../../media/threat-analytics/ta_overview_mtp.png)

_Afsnittet Oversigt i en rapport over trusselsanalyse_

#### <a name="assess-impact-on-your-organization"></a>Vurder påvirkningen af din organisation

Hver rapport indeholder diagrammer, der er udviklet til at give oplysninger om den organisatoriske indvirkning af en trussel:

- **Relaterede hændelser giver** en oversigt over effekten af den registrerede trussel mod din organisation med følgende data:
  - Antal aktive beskeder og antallet af aktive hændelser, de er knyttet til
  - Alvorsgrad for aktive hændelser
- **Beskeder over tid viser** antallet af relaterede aktive **og** **løste beskeder** over tid. Antallet af løste beskeder angiver, hvor hurtigt organisationen reagerer på beskeder, der er knyttet til en trussel. Ideelt set bør diagrammet vise påmindelser, der er blevet løst inden for et par dage.
- **På påvirkede aktiver** viser antallet af forskellige enheder og mailkonti (postkasser), der i øjeblikket har mindst én aktiv besked knyttet til den registrerede trussel. Der udløses beskeder om postkasser, der modtager trusselsmails. Gennemse både organisation- og brugerniveaupolitikker for tilsidesættelser, der medfører levering af trusselsmails.
- **Forhindrede forsøg på** mail – viser antallet af mails fra de seneste syv dage, der enten blev blokeret før levering eller leveret til mappen med uønsket mail.

#### <a name="review-security-resilience-and-posture"></a>Gennemgå sikkerhedsrobusthed og -efterseelse

Hver rapport indeholder diagrammer, der giver et overblik over, hvor robust din organisation er over for en given trussel:

- **Sikker konfigurationsstatus** – viser antallet af enheder med forkert konfigurerede sikkerhedsindstillinger. Anvend de anbefalede sikkerhedsindstillinger for at reducere risikoen. Enheder betragtes som **sikre** , hvis de har _anvendt alle_ de registrerede indstillinger.
- **Status for sikkerhedsrisikorettelse** – viser antallet af følsomme enheder. Anvend sikkerhedsopdateringer eller -rettelser til at løse sårbarheder, som udnyttes af truslen.

#### <a name="view-reports-per-threat-tags"></a>Få vist rapporter pr. trusselsmærker

Du kan filtrere trusselsrapporten og få vist de mest relevante rapporter efter et bestemt trusselsmærke (kategori) eller en rapporttype.

- **Trusselsmærker** – hjælp dig med at få vist de mest relevante rapporter i henhold til en bestemt trusselskategori. Alle rapporter, der er relateret til ransomware, er f.eks.
- **Rapporttyper** – hjælp dig med at få vist de mest relevante rapporter i henhold til en bestemt rapporttype. Alle rapporter, der dækker værktøjer og teknikker, er f.eks.
- **Filtre** hjælper dig med effektivt at gennemse trusselsrapporten og filtrere visningen baseret på et bestemt trusselsmærke eller en rapporttype. Gennemse f.eks. alle trusselsrapporter, der er relateret til kategorien ransomware, eller trusselsrapporter, der dækker sårbarheder.

##### <a name="how-does-it-work"></a>Hvordan fungerer det?

Microsoft Threat Intelligence-teamet har føjet trusselsmærker til hver trusselsrapport:

- Fire trusselsmærker er nu tilgængelige:
  - Ransomware
  - Phishing
  - Sikkerhedsrisiko
  - Gruppen Aktivitet
- Trusselsmærker vises øverst på siden Trusselsanalyse. Der er tællere for antallet af tilgængelige rapporter under hver kode.

  ![trusselsmærker.](../../media/threat-analytics/ta-threattags-mtp.png)

- Listen kan også sorteres efter trusselsmærker:

  ![lister.](../../media/threat-analytics//ta-taglist-mtp.png)

- Filtre er tilgængelige pr. trusselsmærke og rapporttype:

  ![filtre.](../../media/threat-analytics/ta-threattag-filters-mtp.png)

### <a name="analyst-report-get-expert-insight-from-microsoft-security-researchers"></a>Analytikerrapport: Få ekspertindsigt fra Microsoft-sikkerhedseksperter

I sektionen **Analyst report** skal du læse opskrivningen af den detaljerede ekspert. De fleste rapporter giver detaljerede beskrivelser af angrebskæder, herunder taktikker og teknikker, der er knyttet til MITRE ATT&CK-rammen, udtømmende lister med anbefalinger og effektiv trusselssøgningsvejledning[.](advanced-hunting-overview.md)

[Få mere at vide om analytikerrapporten](threat-analytics-analyst-reports.md)

### <a name="related-incidents-view-and-manage-related-incidents"></a>Relaterede hændelser: Få vist og administrer relaterede hændelser

Fanen **Relaterede hændelser indeholder** en liste over alle hændelser, der er relateret til den registrerede trussel. Du kan tildele hændelser eller administrere beskeder, der er knyttet til hver hændelse.

![Billede af sektionen relaterede hændelser i en rapport over trusselsanalyse.](../../media/threat-analytics/ta_related_incidents_mtp.png)

_Sektionen Relaterede hændelser i en trusselsanalyserapport_

### <a name="impacted-assets-get-list-of-impacted-devices-and-mailboxes"></a>På påvirkede aktiver: Hent liste over på påvirkede enheder og postkasser

Et aktiv anses for at være påvirket, hvis det påvirkes af en aktiv, ikke-fundet besked. Fanen **På påvirkede** aktiver viser følgende typer af på påvirkede aktiver:

- **Påsatte enheder** – slutpunkter, der ikke har fundet Microsoft Defender for slutpunktsbeskeder. Disse beskeder udløses typisk på observationer af kendte trusselsindikatorer og aktiviteter.
- **På påvirkede postkasser** – postkasser, der har modtaget mails, som har udløst Microsoft Defender Office 365 vigtige beskeder. Mens de fleste meddelelser, der udløser beskeder, typisk blokeres, kan politikker på bruger- eller organisationsniveau tilsidesætte filtre.

![Billede af afsnittet om påvirkningte aktiver i en rapport over trusselsanalyse.](../../media/threat-analytics/ta_impacted_assets_mtp.png)

_Afsnittet På påvirkede aktiver i en trusselsanalyserapport_

### <a name="prevented-email-attempts-view-blocked-or-junked-threat-emails"></a>Forhindrede forsøg på mail: Få vist blokerede eller uønskede trusselsmails

Microsoft Defender for Office 365 blokerer typisk mails med kendte trusselsindikatorer, herunder ondsindede links eller vedhæftede filer. I nogle tilfælde vil proaktive filtreringsmekanismer, der kontrollerer mistænkeligt indhold, i stedet sende mails med trusler til mappen med uønsket mail. I begge tilfælde reduceres risikoen for at starte malwarekode på enheden.

Fanen **Forhindrede mailforsøg** viser alle de mails, der enten er blevet blokeret før levering eller sendt til mappen med uønsket mail af Microsoft Defender Office 365.

![Billede af afsnittet forhindrede mailforsøg i en trusselsanalyserapport.](../../media/threat-analytics/ta_prevented_email_attempts_mtp.png)

_Afsnittet forsøg på mail forhindret i en trusselsanalyserapport_

### <a name="exposure-and-mitigations-review-list-of-mitigations-and-the-status-of-your-devices"></a>Eksponering og afhjælpninger: Gennemgå en liste over afhjælpninger og status for dine enheder

I afsnittet **afhjælpninger & eksponering skal** du gennemgå listen over specifikke anbefalinger, der kan handles på, som kan hjælpe dig med at øge din organisatoriske fleksibilitet over for truslerne. Listen over registrerede afhjælpninger omfatter:

- **Sikkerhedsopdateringer –** installation af understøttede softwaresikkerhedsopdateringer til sårbarheder, der findes på onboardede enheder
- **Understøttede sikkerhedskonfigurationer**
  - Cloud-leveret beskyttelse  
  - Potentielt uønsket programbeskyttelse (PUA)
  - Beskyttelse i realtid

Oplysninger om afhjælpning i dette afsnit indeholder data [fra Håndtering af trusler og sikkerhedsrisici](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt), som også indeholder detaljerede oplysninger om afhjælpning fra forskellige links i rapporten.

![Billede af afsnittet afhjælpninger i en rapport over trusselsanalyse, der viser sikre konfigurationsoplysninger.](../../media/threat-analytics/ta_mitigations_mtp.png)

![Billede af afsnittet om afhjælpninger i en rapport over trusselsanalyse, der viser oplysninger om sikkerhedsrisikoen.](../../media/threat-analytics/ta_mitigations_mtp2.png)

_Afsnittet & afhjælpninger af eksponering i en rapport om trusselsanalyse_

## <a name="set-up-email-notifications-for-report-updates"></a>Konfigurer mailbeskeder til rapportopdateringer

Du kan konfigurere mailbeskeder, der sender dig opdateringer til trusselsanalyserapporter.

Du kan konfigurere mailbeskeder til trusselsanalyserapporter ved at udføre følgende trin:

1. Vælg **Indstillinger** i Microsoft 365 Defender sidepanel. Vælg **Microsoft 365 Defender** på listen over indstillinger.
 
![Skærmbillede med "Indstillinger" og "Microsoft 365 Defender" begge fremhævet med rødt](../../media/threat-analytics/ta_create_notification_0.png)

2. Vælg **MailbeskederTrusler** > , og vælg knappen + **Opret en meddelelsesregel**. Der vises en pop op-pop-op-pop-op.

![Skærmbillede med "+ Opret en meddelelsesregel" fremhævet med rødt](../../media/threat-analytics/ta_create_notification_1.png)

3. Følg trinnene i pop op-pop-op-pop-op-uddelingen. Først skal du give den nye regel et navn. Beskrivelsesfeltet er valgfrit, men der kræves et navn. Du kan slå reglen til eller fra ved hjælp af afkrydsningsfeltet under beskrivelsesfeltet.

> [!NOTE]
> Felterne Navn og Beskrivelse for en ny meddelelsesregel accepterer kun engelske bogstaver og tal. De accepterer ikke mellemrum, tankestreger, understregningstegn eller anden tegnsætning.

![Skærmbillede af navngivningsskærmen, hvor alle felter er udfyldt, og afkrydsningsfeltet "Slå regel til" er markeret](../../media/threat-analytics/ta_create_notification_2.png)

4. Vælg, hvilken type rapporter du vil have besked om. Du kan vælge mellem at blive opdateret om alle nyligt publicerede eller opdaterede rapporter eller kun de rapporter, der har et bestemt mærke eller type.

![Skærmbillede af meddelelsesskærmen med Ransomware-mærker markeret og en rullemenu for typer, der er åbne](../../media/threat-analytics/ta_create_notification_3.png)

5. Tilføj mindst én modtager for at modtage meddelelserne i mails. Du kan også bruge dette skærmbillede til at kontrollere, hvordan meddelelserne modtages, ved at sende en testmail.

![Skærmbillede af modtagerskærmbilledet. Der er tre modtagere på listen, og der er sendt en testmail, som angivet af et grønt hak](../../media/threat-analytics/ta_create_notification_4.png)

6. Gennemse den nye regel. Hvis der er noget, du gerne vil ændre, skal **du vælge** knappen Rediger i slutningen af hvert underafsnit. Når gennemsynet er fuldført, skal du **vælge knappen Opret** regel.

![Skærmbillede af skærmbilledet til gennemsyn. Knappen Rediger er fremhævet med rødt](../../media/threat-analytics/ta_create_notification_5.png)

7. Tillykke! Den nye regel er blevet oprettet. Vælg knappen **Udført** for at fuldføre processen og lukke pop op-knappen.

![Skærmbillede af det skærmbillede, der blev oprettet af reglen. En regel, der er oprettet, viser grønne markeringer langs sidepanelet og en stor grøn markering i hovedområdet på skærmen](../../media/threat-analytics/ta_create_notification_6.png)

8. Din nye regel vises nu på listen over meddelelser om Trusselsanalyse.

![Skærmbillede af listen over regler for mailbeskeder i Indstillinger skærmbilledet](../../media/threat-analytics/ta_create_notification_7.png)

## <a name="additional-report-details-and-limitations"></a>Yderligere rapportdetaljer og -begrænsninger

> [!NOTE]
> Som en del af den samlede sikkerhedsoplevelse er trusselsanalyse nu tilgængelig ikke kun for Microsoft Defender til Slutpunkt, men også for Microsoft Defender til Office E5-licensholdere.
>
> Hvis du ikke bruger Microsoft 365-sikkerhedsportalen (Microsoft 365 Defender), kan du også se rapportoplysningerne (uden Microsoft Defender til Office-data) på Microsoft Defender Security Center-portalen (Microsoft Defender til slutpunkt).

For at få adgang til rapporter om trusselsanalyse skal du have bestemte roller og tilladelser. Se [Brugerdefinerede roller i rollebaseret adgangskontrol for at få Microsoft 365 Defender](custom-roles.md) for at få mere at vide.

- Hvis du vil have vist vigtige beskeder, hændelser eller påvirkede data om aktiver, skal du have tilladelser til Microsoft Defender til Office- eller Microsoft Defender for Endpoint-beskeddata eller begge dele.
- Hvis du vil have vist forhindrede mailforsøg, skal du have tilladelse til at Microsoft Defender til at Office data.
- For at få vist afhjælpninger skal du have tilladelse til at Håndtering af trusler og sikkerhedsrisici data i Microsoft Defender til Slutpunkt.

Når du ser på dataene fra trusselsanalyser, skal du huske følgende faktorer:

- Diagrammer afspejler kun afhjælpninger, der registreres. Se rapportoversigten for yderligere afhjælpninger, der ikke vises i diagrammerne.
- Afhjælpninger garanterer ikke fuldstændig fleksibilitet. Afhjælpningerne afspejler de bedst mulige foranstaltninger, der er nødvendige for at forbedre fleksibiliteten.
- Enheder tælles som "utilgængelige", hvis de ikke har overført data til tjenesten.
- Antivirusrelaterede statistikker er baseret på Microsoft Defender Antivirus indstillinger. Enheder med antivirusløsninger fra tredjepart kan vises som "eksponerede".

## <a name="related-articles"></a>Relaterede artikler

- [Find proaktivt trusler med avanceret jagt](advanced-hunting-overview.md)
- [Forstå sektionen for analytikerrapporten](threat-analytics-analyst-reports.md)
- [Vurder og løs sikkerhedsforanstaltninger og eksponeringer](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
