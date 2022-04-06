---
title: Kom i gang med styring af insider-risiko
description: Konfigurer insider-risikostyring i din organisation.
keywords: Microsoft 365, insider-risikostyring, risikostyring, overholdelse af regler og standarder
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 05375332df6542cd87e986bba68ef7c6753f8e36
ms.sourcegitcommit: 7aa2441c1f2cc5b4b5495d6fdb993e563f86647f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64637956"
---
# <a name="get-started-with-insider-risk-management"></a>Kom i gang med styring af insider-risiko

Brug insider-politikker til risikostyring til at identificere risikabelt aktivitet og administrationsværktøjer til at handle på risikoadvarsler i din organisation. Udfør følgende trin for at konfigurere forudsætninger og konfigurere en insider-politik for risikostyring.

> [!IMPORTANT]
> Løsningen Microsoft 365 insider-risikostyring giver en mulighed på lejerniveau for at hjælpe kunderne med at muliggøre intern styring på brugerniveau. Administratorer på lejerniveau kan konfigurere tilladelser til at give medlemmer af organisationen adgang til denne løsning og konfigurere dataforbindelser i Microsoft 365 Overholdelsescenter til at importere relevante data for at understøtte identifikation på brugerniveau af potentielt risikabel aktivitet. Kunder anerkender viden, der er relateret til den enkelte brugers adfærd, tegn eller ydeevne materiale relateret til ansættelse, og kan beregnes af administratoren og gøres tilgængelig for andre i organisationen. Desuden anerkender kunderne, at de skal udføre deres egen fulde undersøgelse relateret til den enkelte brugers adfærd, karakter eller ydeevne materiale relateret til ansættelse og ikke kun være afhængig af viden fra Insider Risk Management-tjenesten. Kunder er alene ansvarlige for at bruge Microsoft 365 Insider Risk Management-tjenesten og alle tilknyttede funktioner eller tjenester i overensstemmelse med gældende lovgivning, herunder love om individuel brugeridentifikation og eventuelle afhjælpningshandlinger.

Du kan finde flere oplysninger om, hvordan insider-risikopolitikker kan hjælpe dig med at administrere risici i din organisation, [under Insider-risikostyring i Microsoft 365](insider-risk-management.md).

## <a name="subscriptions-and-licensing"></a>Abonnementer og licenser

Før du går i gang med insider-risikostyring, skal du [bekræfte Microsoft 365 dit abonnement](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) og eventuelle tilføjelser. For at få adgang til og bruge Insider Risk Management skal din organisation have et af følgende abonnementer eller tilføjelser:

- Microsoft 365 E5/A5/F5/G5-abonnement (betalt version eller prøveversion)
- Microsoft 365 E3/A3/F3/G3 + tilføjelsesprogrammet Microsoft 365 E5/A5/F5/G5 Compliance
- Microsoft 365 E3/A3/F3/G3 -abonnement + Microsoft 365 E5/A5/F5/G5 Insider Risk Management-tilføjelsesprogrammet
- Office 365 E3 -abonnement + Enterprise Mobility and Security E3 + Microsoft 365 E5 Overholdelse-tilføjelsesprogrammet

Brugere, der er inkluderet i politikker for insider-risikostyring, skal tildeles en af licenserne ovenfor.

> [!IMPORTANT]
> Insider-risikostyring er i øjeblikket tilgængelig i lejere, der er hostet i geografiske områder, og lande, der understøttes af Azure-tjenesteafhængigheder. For at bekræfte at Insider Risk Management understøttes for din organisation, skal du [se Tilgængelighed af Azure-afhængighed efter land/område](/troubleshoot/azure/general/dependency-availability-by-country).

Hvis du ikke har en eksisterende Microsoft 365 Enterprise E5-plan og gerne vil prøve Insider-risikostyring, kan du føje [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) til dit eksisterende abonnement eller tilmelde dig [en](https://www.microsoft.com/microsoft-365/enterprise) prøveversion af Microsoft 365 Enterprise E5.

## <a name="recommended-actions-preview"></a>Anbefalede handlinger (eksempel)

Anbefalede handlinger kan hjælpe din organisation med hurtigt at få insider-risikostyring. På siden Oversigt **finder du** anbefalede handlinger, der hjælper dig gennem trinnene til konfiguration og implementering af politikker.

![Anbefalede handlinger for Insider-risikostyring.](../media/insider-risk-recommended-actions.png)

Der findes følgende anbefalinger, der kan hjælpe dig med at komme i gang med eller maksimere din insider-risikostyringskonfiguration:

- **Aktiver overvågning**: Når det er slået til, registreres bruger- og administratoraktivitet i organisationen Microsoft 365 overvågningsloggen. Insider-risikopolitikker og analysescanninger bruger denne log til at registrere risikoaktiviteter.
- **Få tilladelser til administration af brugerrisici**: Det adgangsniveau, du har til insider-funktioner til risikostyring, afhænger af, hvilken rollegruppe du er tildelt. Brugere skal være tildelt rollegrupperne *Insider Risk Management eller Insider Risk Management-administratorer* for  at få adgang til og konfigurere anbefalede handlinger.
- **Vælg politikindikatorer**: Symboler er i bund og grund de brugeraktiviteter, du vil registrere og undersøge. Du kan vælge indikatorer til at spore aktivitet på tværs Microsoft 365 placeringer og tjenester.
- **Søg efter potentielle insider-risici**: Kør en analysescanning for at finde potentielle Insider-risici i din organisation. Efter evaluering af resultater skal du gennemse anbefalede politikker for at konfigurere.
- **Tildel tilladelser til** andre: Hvis der er flere teammedlemmer, som skal være ansvarlige for administration af insider-risikofunktioner, skal du tildele dem til de relevante rollegrupper.
- **Opret din første** politik: For at modtage beskeder om potentielt risikabelt arbejde skal du konfigurere politikker, der er baseret på foruddefinerede skabeloner, der definerer de brugeraktiviteter, du vil registrere og undersøge.

Hver anbefalede handling, der er inkluderet i denne oplevelse, har fire attributter:

- **Handling**: Navnet og beskrivelsen af den anbefalede handling.
- **Status**: Status for den anbefalede handling. Værdier er ikke *startet*, *I gang*, *Gemt til senere* eller *Fuldført*.
- **Påkrævet eller valgfrit**: Uanset om den anbefalede handling er påkrævet eller valgfri, for at insider-funktioner til risikostyring fungerer som forventet.
- **Anslået tidspunkt at fuldføre**: Anslået tidspunkt for fuldførelse af den anbefalede handling i minutter.

Vælg en anbefaling på listen for at komme i gang med at konfigurere Insider Risk Management. Hver anbefalede handling fører dig gennem de påkrævede aktiviteter til anbefalingen, herunder eventuelle krav, hvad du kan forvente, og effekten af at konfigurere funktionen i organisationen.   Hver anbefalede handling markeres automatisk som fuldført, når den er konfigureret, ellers skal du manuelt vælge handlingen som fuldført, når den er konfigureret.

## <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Trin 1 (påkrævet): Aktivér tilladelser for Insider Risk Management

> [!IMPORTANT]
> Når du har konfigureret dine rollegrupper, kan det tage op til 30 minutter, før tilladelserne for rollegruppen gælder for tildelte brugere i hele organisationen.

Der bruges seks rollegrupper til at konfigurere insider-funktioner til risikostyring. For at **gøre Insider-risikostyring** tilgængelig som en menuindstilling i Microsoft 365 Overholdelsescenter og for at fortsætte med disse konfigurationstrin skal du være tildelt en af følgende roller eller rollegrupper:

- Azure Active Directory [*global administratorrolle*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory [*rolle som overholdelsesadministrator*](/azure/active-directory/roles/permissions-reference#compliance-administrator)
- Microsoft 365 Overholdelsescenter [*rollegruppe for*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) organisationsadministration
- Microsoft 365 Overholdelsescenter af [*rollegruppen Overholdelsesadministrator*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- *Rollegruppen Insider* Risk Management
- *Rollegruppen Insider Risk Management-administrator*

Afhængigt af hvordan du vil administrere politikker og advarsler for insider-risikostyring, skal du tildele brugere til bestemte rollegrupper for at administrere forskellige sæt insider-funktioner til risikostyring. Du har mulighed for at tildele brugere med forskellige ansvarsområder i forbindelse med overholdelse til bestemte rollegrupper for at administrere forskellige områder af insider-risikostyringsfunktioner. Eller du kan vælge at tildele alle brugerkonti til udvalgte administratorer, analytikere, administratorer og seere til rollegruppen Insider Risk Management. Brug en enkelt rollegruppe eller flere rollegrupper, så de passer bedst til dine krav til overholdelsesstyring.

Du kan vælge mellem disse indstillinger for rollegrupper og løsningshandlinger, når du arbejder med Insider Risk Management:

|**Handlinger**|**Insider Risk Management**|**Insider Risk Management-administrator**|**Analytikere af styring af insider-risiko**|**Undersøgere af styring af insider-risiko**|**Insider-revisorer for risikostyring**|
|:----------|:--------------------------|:--------------------------------|:-----------------------------------|:----------------------------------------|:-----------------------------------|
| Konfigurere politikker og indstillinger | Ja | Ja | Nej | Nej | Nej |
| Få adgang til analyseindsigt | Ja | Ja | Ja | Nej | Nej |
| Access & undersøg beskeder | Ja | Nej | Ja | Ja | Nej |
| Access & undersøge sager | Ja | Nej | Ja | Ja | Nej |
| Få & adgang til at få vist Indholdsstifinder | Ja | Nej | Nej | Ja | Nej |
| Konfigurere meddelelsesskabeloner | Ja | Nej | Ja | Ja | Nej |
| Vise & for eksport af overvågningslogfiler | Ja | Nej | Nej | Nej | Ja |

>[!IMPORTANT]
>Sørg for, at du altid har mindst én bruger i rollegrupperne *Insider Risk Management* eller *Insider Risk Management-administrator* (afhængigt af den indstilling, du vælger), så din insider-risikostyringskonfiguration ikke kommer ind i et scenarie med nul administratorer, hvis bestemte brugere forlader organisationen.

Medlemmer af følgende roller kan tildele brugere rollen som Insider-rollegruppe for risikostyring og have de samme løsningstilladelser i *rollegruppen Insider Risk Management Administration* :

- Azure Active Directory *global administrator*
- Azure Active Directory *over overholdelse af regler og standarder*
- Microsoft 365 Overholdelsescenter *organisationsadministration*
- Microsoft 365 Overholdelsescenter over *overholdelse af regler og standarder*

> [!NOTE]
> Disse rollegrupper understøttes i øjeblikket ikke på Privileged Identity Management (PIM). Du kan få mere at vide om PIM under [Tildel Azure AD-roller Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-how-to-add-role-to-user).

### <a name="add-users-to-an-insider-risk-management-role-group"></a>Føj brugere til en rollegruppe for insider-risikostyring

Udfør følgende trin for at føje brugere til en rollegruppe for insider-risikostyring:

1. Log på [Microsoft 365 Overholdelsescenter bruger](https://compliance.microsoft.com) legitimationsoplysninger til en administratorkonto i din Microsoft 365 organisation.

2. I Security &amp; Compliance Center skal du gå **til Tilladelser**. Vælg linket for at få vist og administrere roller i Office 365.

3. Vælg den insider-rollegruppe for risikostyring, du vil føje brugere til, og vælg derefter **Rediger rollegruppe**.

4. Vælg **Vælg medlemmer** i venstre navigationsrude, og vælg derefter **Rediger**.

5. Vælg **Tilføj** , og markér derefter afkrydsningsfeltet for alle brugere, du vil føje til rollegruppen.

6. Vælg **Tilføj**, og vælg derefter **Udført**.

7. Vælg **Gem** for at føje brugerne til rollegruppen. Vælg **Luk** for at fuldføre trinnene.

## <a name="step-2-required-enable-the-microsoft-365-audit-log"></a>Trin 2 (påkrævet): Aktivér Microsoft 365 overvågningsloggen

Insider-risikostyring bruger Microsoft 365 til brugerindsigt og aktiviteter, der er identificeret i politikker og analyseindsigt. Overvågningsloggen Microsoft 365 en oversigt over alle aktiviteter i din organisation, og politikker for insider-risikostyring kan bruge disse aktiviteter til at generere indsigt i politikker.

Overvågning er aktiveret for Microsoft 365 organisationer som standard. Nogle organisationer har deaktiveret overvågning af bestemte årsager. Hvis overvågning er deaktiveret for organisationen, kan det skyldes, at en anden administrator har slået det fra. Vi anbefaler, at du bekræfter, at det er OK at slå overvågning til igen, når du udfører dette trin.

Du kan finde en trinvis vejledning i at aktivere overvågning i Slå søgning [i overvågningslogfil til eller fra](turn-audit-log-search-on-or-off.md). Når du har aktiveret overvågning, vises der en meddelelse om, at overvågningsloggen forberedes, og at du kan køre en søgning om et par timer, efter at klargøringen er fuldført. Du behøver kun at udføre denne handling én gang. Du kan finde flere oplysninger om Microsoft 365 i Søge [i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-enable-and-view-insider-risk-analytics-insights"></a>Trin 3 (valgfrit): Aktivér og få vist indsigt i Insider Risk Analytics

Insider-analyse af risikostyring gør det muligt at udføre en evaluering af potentielle insider-risici i din organisation uden at konfigurere insider-risikopolitikker. Denne evaluering kan hjælpe din organisation med at identificere potentielle områder med højere brugerrisici og hjælpe med at bestemme typen og omfanget af de insider-risikostyringspolitikker, du kan overveje at konfigurere. Denne evaluering kan også hjælpe dig med at bestemme behov for yderligere licensering eller fremtidig optimering af eksisterende politikker. Analysescanningsresultater kan tage op til 48 timer, før indsigter er tilgængelige som rapporter til gennemsyn. Hvis du vil have mere at vide om analyseindsigt, skal du se Indstillinger for [Insider-risikostyring:](insider-risk-management-settings.md#analytics) Analyse og se videoen [Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) for at få en forståelse af, hvordan analyser kan hjælpe med at fremskynde identifikationen af potentielle Insider-risici og hjælpe dig med hurtigt at reagere.

For at aktivere Insider Risk Analytics skal du være medlem af *Insider Risk Management*, *Insider Risk Management-administrator* eller Microsoft 365 *globale administratorrollegruppe*.

Udfør følgende trin for at aktivere Insider Risk Analytics:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå **til Insider-risikostyring**.
2. Vælg **Kør scanning** på **scanningen for insider-risici i dit organisationskort** på fanen Oversigt over **insider-risikohåndtering** . Denne handling aktiverer analysescanning for din organisation. Du kan også aktivere scanning i din organisation ved at navigere til Insider-risikoindstillingerAnalytics  >  og aktivere Scan din lejers brugeraktivitet for at identificere **potentielle insiderrisici**.
3. På **detaljeruden Analyse skal** du vælge **Kør scanning for at starte scanningen for din organisation**. Analysescanningsresultater kan tage op til 48 timer, før indsigter er tilgængelige som rapporter til gennemsyn.

Når du har gennemset analyseindsigtene, skal du vælge Insider Risk-politikkerne og konfigurere de tilknyttede forudsætninger, der bedst opfylder din organisations Insider-strategi for risikoafhjælpning.

## <a name="step-4-recommended-configure-prerequisites-for-policies"></a>Trin 4 (anbefales): Konfigurer forudsætninger for politikker

De fleste insider-politikker for risikostyring har forudsætninger, der skal konfigureres til politikindikatorer til at generere relevante aktivitetsbeskeder. Konfigurer de relevante forudsætninger afhængigt af de politikker, du planlægger at konfigurere for organisationen.

### <a name="configure-microsoft-365-hr-connector"></a>Konfigurer Microsoft 365 HR-forbindelse

Insider-risikostyring understøtter import af bruger- og logdata importeret fra tredjepartsplatforme til risikostyring og HR-ressourcer. Med Microsoft 365 HR-dataforbindelse (Human Resources) kan du trække HR-data ind fra CSV-filer, herunder datoer for opsigelse af brugere, datoer for seneste ansættelse, meddelelser om forbedring af ydeevneplan, handlinger til evaluering af ydeevne og ændring af status på jobniveau. Disse data hjælper med at udarbejde indikatorer for insider-risikostyring og er en vigtig del af konfigurationen af fuld dækning af risikostyring i organisationen. Hvis du konfigurerer mere end én HR-forbindelse for din organisation, trækker Insider Risk Management automatisk indikatorer fra alle HR-forbindelser.

Forbindelsen Microsoft 365 HR-forbindelsen er påkrævet, når du bruger følgende politikskabeloner:

- Datalækager fra forskellige brugere
- Brugeres datatyveri, der forlader den
- Generel forkert brug af patientdata
- Brud på sikkerhedspolitik ved brugere, der forlader os
- Overtrædelse af sikkerhedspolitik for brugere, der ikke er ens

Se artiklen [Konfigurer en forbindelse for at importere HR-data](import-hr-data.md) for en trinvis vejledning til konfiguration af Microsoft 365 HR-forbindelsen for organisationen. Når du har konfigureret HR-forbindelsen, skal du vende tilbage til disse konfigurationstrin.

### <a name="configure--a-healthcare-specific-data-connector"></a>Konfigurer en sundhedsspecifik dataforbindelse

Insider-risikostyring understøtter import af bruger- og logdata importeret fra tredjeparter i eksisterende elektroniske medicinske registreringssystemer (EMR). Microsoft Healthcare og Episke dataforbindelser giver dig mulighed for at trække aktivitetsdata fra dit EMR-system med CSV-filer, herunder forkert patientjournaladgang, mistænkelige volumenaktiviteter samt redigerings- og eksportaktiviteter. Disse data hjælper med at udarbejde indikatorer for insider-risikostyring og er en vigtig del af konfigurationen af fuld dækning af risikostyring i organisationen.

Hvis du konfigurerer mere end ét sundheds- eller episk forbindelseskomponent til din organisation, understøtter Insider-risikostyring automatisk begivenheds- og aktivitetssignaler fra alle sundhedssektoren og episke forbindelser.
Forbindelsen Microsoft 365 Healthcare eller Episk forbindelse er påkrævet, når du bruger følgende politikskabeloner:

- Generel forkert brug af patientdata

Se artiklen [Konfigurer](import-healthcare-data.md) en forbindelse for at importere sundhedsdata eller Konfigurer en forbindelse for at importere [Ehr-dataar artiklen Ep episk EHR](import-epic-data.md) for at få en trinvis vejledning til konfiguration af en sundhedsspecifik forbindelse til din organisation. Når du har konfigureret en forbindelse, skal du vende tilbage til disse konfigurationstrin.

### <a name="configure-data-loss-prevention-dlp-policies"></a>Konfigurere DLP-politikker (Forebyggelse af datatab)

Insider-risikostyring understøtter brug af DLP-politikker til at identificere bevidst eller utilsigtet eksponering af følsomme oplysninger til uønskede parter for DLP-beskeder på højt niveau. Når du konfigurerer en insider-politik for risikostyring med en  af skabelonerne til datalækager, har du mulighed for at tildele en bestemt DLP-politik til politikken for disse typer af beskeder.

DLP-politikker hjælper med at identificere brugere for at aktivere risikoscore i insider-risikostyring for DLP-beskeder med høj alvorsgrad for følsomme oplysninger og er en vigtig del af konfigurationen af fuld dækning af risikostyring i organisationen. Du kan finde flere oplysninger om insider-risikostyring og integration af DLP-politikker og planlægningsovervejelser i [Insider-politikker for risikostyring](insider-risk-management-policies.md#general-data-leaks).

> [!IMPORTANT]
>Sørg for, at du har fuldført følgende:
>
>- Du forstår og korrekt konfigurerer de in-scope brugere i både DLP- og insider-risikostyringspolitikker for at opnå den politikomfang, du forventer.
>- Sørg *for,* **at indstillingen Hændelsesrapporter** i DLP-politikken for insider-risikostyring, der bruges sammen med disse skabeloner, er konfigureret til beskeder på højt niveau. Insider-beskeder om risikostyring genereres ikke fra DLP-politikker med feltet Hændelsesrapporter indstillet til *Lav* eller *Mellem*.

En DLP-politik er valgfri, når du bruger følgende politikskabeloner:

- Generelle datalækager
- Datalækager efter prioritetsbrugere

Se artiklen [Opret, test og finjuster en DLP-politik](create-test-tune-dlp-policy.md) for at få en trinvis vejledning til at konfigurere DLP-politikker for organisationen. Når du har konfigureret en DLP-politik, skal du vende tilbage til disse konfigurationstrin.

### <a name="configure-priority-user-groups"></a>Konfigurere prioritetsbrugergrupper

Insider-risikostyring omfatter understøttelse af tildeling af prioritetsbrugergrupper til politikker, der hjælper med at identiteten af unikke risikoaktiviteter for brugere med kritiske positioner, høje niveauer af data og netværksadgang eller en tidligere historik over risikoadfærd. Oprettelse af en prioriteret brugergruppe og tildeling af brugere til gruppen er med til at begrænse politikker til de unikke forhold, som disse brugere præsenteres under.

En prioriteret brugergruppe er påkrævet, når du bruger følgende politikskabeloner:

- Prioritetsbrugeres brud på sikkerhedspolitik
- Datalækager efter prioritetsbrugere

Se artiklen [Introduktion til indstillinger for Insider Risk Management](insider-risk-management-settings.md#priority-user-groups-preview) for at få en trinvis vejledning til at oprette en prioriteret brugergruppe. Når du har konfigureret en prioriteret brugergruppe, skal du vende tilbage til disse konfigurationstrin.

### <a name="configure-physical-badging-connector-optional"></a>Konfigurer fysisk badging-forbindelse (valgfrit)

Insider-risikostyring understøtter import af bruger- og logdata fra fysiske kontrol- og adgangsplatforme. Med forbindelsespunktet Fysisk badging kan du trække adgangsdata fra JSON-filer, herunder bruger-id'er, adgangspunkt-id'er, adgangstidspunkter og -datoer samt adgangsstatus. Disse data hjælper med at udarbejde indikatorer for insider-risikostyring og er en vigtig del af konfigurationen af fuld dækning af risikostyring i organisationen. Hvis du konfigurerer mere end én fysisk forbindelse til fysisk badging for din organisation, trækker Insider Risk Management automatisk indikatorer fra alle fysiske dårlige forbindelser. Oplysninger fra forbindelsen Fysisk badging supplerer andre insider-risiko signaler, når du bruger alle insider-politikskabeloner for risici.

> [!IMPORTANT]
> For at insider-risikostyringspolitikker kan bruge og korrelere signaldata, der er relateret til brugere, der forlader og afslutter, med begivenhedsdata fra din fysiske kontrol og adgangsplatforme, skal du også konfigurere Microsoft 365 HR-forbindelsen. Hvis du aktiverer forbindelsen Fysisk badging uden at aktivere Microsoft 365 HR-forbindelsen, behandler politikkerne for insider-risikostyring kun hændelser for uautoriseret fysisk adgang for brugere i organisationen.

Se artiklen [Konfigurer en](import-physical-badging-data.md) forbindelse for at importere fysiske ugyldige data, hvis du vil have en trinvis vejledning til konfiguration af en Fysisk ugyldig forbindelse for organisationen. Når du har konfigureret forbindelsen, skal du vende tilbage til disse konfigurationstrin.

### <a name="configure-microsoft-defender-for-endpoint-optional"></a>Konfigurer Microsoft Defender for Endpoint (valgfrit)

[Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) er en sikkerhedsplatform til virksomheder, der er udviklet med henblik på at hjælpe virksomhedsnetværk med at forhindre, registrere, undersøge og reagere på avancerede trusler. For at få bedre overblik over sikkerhedsbrud i organisationen kan du importere og filtrere Defender for Endpoint-beskeder for aktiviteter, der bruges i politikker, der er oprettet ud fra politikskabeloner til insider-risikostyringssikkerhedsbrud.

Hvis du opretter sikkerhedsfejlspolitikker, skal du have Microsoft Defender for Endpoint konfigureret i din organisation og aktivere Defender for Endpoint for insider-integration af risikostyring i Defender Security Center for at kunne importere sikkerhedsbrudsbeskeder. Du kan finde flere oplysninger om krav [i artiklen Minimumskrav til Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements) artikel.

Se artiklen [Konfigurer avancerede funktioner i Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center) for en trinvis vejledning til konfiguration af Defender til Endpoint for integration af insider-risikostyring. Når du har konfigureret konfigurationen, Microsoft Defender for Endpoint du vende tilbage til disse konfigurationstrin.

## <a name="step-5-required-configure-insider-risk-settings"></a>Trin 5 (påkrævet): Konfigurer indstillinger for insider-risiko

[Insider-risikoindstillinger](insider-risk-management-settings.md) gælder for alle insider-risikostyringspolitikker, uanset hvilken skabelon du vælger, når du opretter en politik. Indstillinger konfigureret ved hjælp af **kontrolelementet Insider-risikoindstillinger**, der er placeret øverst på alle faner for Insider Risk Management. Disse indstillinger styrer beskyttelse af personlige oplysninger, indikatorer, overvågning af vinduer og intelligente registreringer.

Inden du konfigurerer en politik, skal du definere følgende insider-risikoindstillinger:

1. I [Microsoft 365 Overholdelsescenter skal](https://compliance.microsoft.com) du gå til **Insider-risikostyring** og vælge **Insider-risikoindstillinger** i øverste højre hjørne på en hvilken som helst side.
2. På siden **Beskyttelse af** personlige oplysninger skal du vælge en indstilling for beskyttelse af personlige oplysninger for visning af brugernavne for politikbeskeder.
3. På siden **Symboler** skal du vælge de advarselsindikatorer, du vil anvende på alle insider-risikopolitikker.

    > [!IMPORTANT]
    > Hvis du vil modtage beskeder om risikabel aktivitet defineret i dine politikker, skal du vælge en eller flere indikatorer. Hvis symboler ikke er konfigureret i Indstillinger, kan indikatorerne ikke vælges i Insider Risk-politikker.

4. På siden **Politiks tidsrammer** skal du vælge de [](insider-risk-management-settings.md#policy-timeframes) tidsrammer for politikken, der skal træde i kraft for en bruger, når de udløser en match for en Insider-risikopolitik.
5. På siden **Intelligente registreringer** skal du konfigurere følgende indstillinger for insider-risikopolitikker:
    - [Udeladelse af filtyper](insider-risk-management-settings.md#file-type-exclusions)
    - [Minimum antal daglige begivenheder for at øge scoren for usædvanlig aktivitet](insider-risk-management-settings.md#minimum-number-of-daily-events-to-boost-score-for-unusual-activity)
    - [Besked om lydstyrkeniveau](insider-risk-management-settings.md#alert-volume)
    - [Microsoft Defender for Endpoint beskedstatus](insider-risk-management-settings.md#microsoft-defender-for-endpoint-preview)
    - [Domæneindstillinger](insider-risk-management-settings.md#domains)
6. På siden **Eksportér beskeder skal du** aktivere eksport af insider risk alert-oplysninger ved hjælp Office 365 Administrations-API'er, hvis det er nødvendigt.
7. På siden **Prioritetsbrugergrupper** skal du oprette en prioriteret brugergruppe og tilføje brugere, hvis de ikke blev oprettet **i trin 3**.
8. På siden **Power Automate flow skal** du konfigurere et flow fra insider-risikoflowskabeloner eller oprette et nyt flow. Se artiklen [Introduktion til indstillinger for Insider Risk](insider-risk-management-settings.md#power-automate-flows-preview) Management for at få en trinvis vejledning.
9. På siden **Prioritetsaktiver skal** du konfigurere prioritetsaktiver til at bruge data fra din fysiske kontrol og adgangsplatform, der importeres af forbindelsen Fysisk ugyldig forbindelse. Se artiklen [Introduktion til indstillinger for Insider Risk](insider-risk-management-settings.md#priority-physical-assets-preview) Management for at få en trinvis vejledning.
10. På siden **Microsoft Teams** skal du aktivere Microsoft Teams integration med Insider Risk Management for automatisk at oprette et team til sags- eller brugersamarbejde. Se artiklen [Introduktion til indstillinger for Insider Risk](insider-risk-management-settings.md#microsoft-teams-preview) Management for at få en trinvis vejledning.
11. Vælg **Gem** for at aktivere disse indstillinger for dine Insider-risikopolitikker.

## <a name="step-6-required-create-an-insider-risk-management-policy"></a>Trin 6 (påkrævet): Opret en insider-politik for risikostyring

Insider-politikker for risikostyring omfatter tildelte brugere og definerer, hvilke typer risikoindikatorer der konfigureres for beskeder. Før aktiviteter kan udløse beskeder, skal der konfigureres en politik. Brug guiden politik til at oprette nye politikker for insider-risikostyring.

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring** og vælge **fanen** Politikker.
2. Vælg **Opret politik** for at åbne guiden politik.
3. På siden **Politikskabelon** skal du vælge en politikkategori og derefter vælge skabelonen til den nye politik. Disse skabeloner består af betingelser og indikatorer, der definerer de risikoaktiviteter, du vil registrere og undersøge. Gennemse skabelonens forudsætninger, udløsende hændelser og registrerede aktiviteter for at bekræfte, at denne politikskabelon passer til dine behov.

    > [!IMPORTANT]
    > Nogle politikskabeloner har forudsætninger, der skal konfigureres, for at politikken kan generere relevante beskeder. Hvis du ikke har konfigureret forudsætningerne for den gældende politik, skal du **se trin 4** ovenfor.

4. Vælg **Næste for** at fortsætte.
5. På siden **Navn og beskrivelse** skal du udfylde følgende felter:
    - **Navn (påkrævet)**: Angiv et brugervenligt navn til politikken. Dette navn kan ikke ændres, efter politikken er oprettet.
    - **Beskrivelse (valgfrit)**: Angiv en beskrivelse af politikken.

6. Vælg **Næste for** at fortsætte.
7. På siden **Brugere** og grupper skal du vælge  Inkluder alle brugere og  grupper eller Inkluder bestemte brugere og grupper for at definere, hvilke brugere eller grupper, der er inkluderet i politikken, eller hvis du har valgt en prioritetsbaseret skabelon for brugere. skal **du vælge Tilføj eller rediger prioritetsbrugergrupper**. Hvis du **vælger Medtag alle** brugere og grupper, leder du efter udløserhændelser for alle brugere og grupper i organisationen for at begynde at tildele risikopoint for politikken. Hvis du **vælger Medtag bestemte brugere og grupper,** kan du angive, hvilke brugere og grupper der skal tildeles politikken. Gæstebrugerkonti understøttes ikke.
8. Vælg **Næste for** at fortsætte.
9. På siden **Indhold, der** skal prioritere kan du tildele (hvis det er nødvendigt) de kilder, der skal prioriteres, hvilket øger risikoen for at generere en besked om høj alvorsgrad for disse kilder. Vælg en af følgende valgmuligheder:

    - **Jeg vil angive SharePoint, følsomhedsmærkater og/eller følsomme oplysningstyper som prioritetsindhold**. Hvis du vælger denne indstilling, aktiveres detaljesider i guiden til konfiguration af disse kanaler.
    - **Jeg vil ikke angive prioritetsindhold lige nu (det vil du kunne gøre, når politikken er oprettet)**. Hvis du vælger denne indstilling, springer du kanaldetaljesiderne over i guiden.

10. Vælg **Næste for** at fortsætte.

11. Hvis du har valgt Jeg vil angive **SharePoint-websteder,** følsomhedsmærkater og/eller følsomme oplysningstyper som prioritetsindhold i det forrige trin, får du vist detaljesiderne for *SharePoint-websteder**, typer* af følsomme oplysninger og følsomhedsmærkater. Brug disse detaljesider til at definere de SharePoint, typer af følsomme oplysninger og følsomhedsetiketter, der skal prioriteres i politikken.

    - **SharePoint websteder**: Vælg **Tilføj SharePoint websted,** og vælg SharePoint websteder, du har adgang til og vil prioritere. " *group1@contoso.sharepoint.com/sites/group1"*.
    - **Type af følsomme oplysninger**: **Vælg Tilføj følsom oplysningstype** , og vælg de følsomhedstyper, du vil prioritere. For eksempel *"USA Bankkontonummer"* og *"Kreditkortnummer"*.
    - **Følsomhedsmærkater**: **Vælg Tilføj følsomhedsmærkat** , og vælg de etiketter, du vil prioritere. For eksempel *"Fortroligt"* og *"Fortroligt"*.

    >[!NOTE]
    >Brugere, der konfigurerer politikken og vælger prioritet af Share Point-websteder, kan SharePoint websteder, de har tilladelse til at få adgang til. Hvis SharePoint websteder ikke kan vælges i politikken af den aktuelle bruger, kan en anden bruger med de nødvendige tilladelser vælge webstederne til politikken senere, eller den aktuelle bruger skal have adgang til de nødvendige websteder.

12. Vælg **Næste for** at fortsætte.
13. Hvis du har valgt standarddatalækager eller *datalækager* efter *prioritetsbrugerskabeloner* , kan du se valgmuligheder på siden Udløsere **til denne** politik for brugerdefinerede hændelser og politikindikatorer. Du har mulighed for at vælge en DLP-politik eller indikatorer til at udløse hændelser, der bringer brugere, som er tildelt politikkens omfang, til aktivitetsscore. Hvis du vælger brugeren svarer til en indstilling til forebyggelse af datatab **(DLP)** -politik, der udløser hændelse, skal du vælge en DLP-politik på rullelisten for DLP-politikken for at aktivere udløsere indikatorer for DLP-politikken for denne insider-politik for risikostyring. Hvis du vælger Brugeren **udfører en udfyldningsaktivitet** , der udløser hændelsesindstillingen, skal du vælge en eller flere af de angivne indikatorer for den politik, der udløser begivenheden.
    >[!IMPORTANT]
    >Hvis du ikke kan vælge en angivet indikator, skyldes det, at de ikke er aktiveret for din organisation. For at gøre dem tilgængelige til at vælge og tildele til politikken skal du aktivere indikatorerne i **Insider-Indstillinger** >  >  **Policy-indikatorer**.

    Hvis du har valgt andre politikskabeloner, understøttes brugerdefinerede udløserhændelser ikke. Den indbyggede politik, der udløser hændelser, anvendes, og du fortsætter til trin 23 uden at definere politikattributter.

14. Vælg **Næste for** at fortsætte.
15. Hvis du har valgt de generelle datalækager eller *datalækager* efter prioritetsbrugerskabeloner og har valgt, at Brugeren skal udføre en  **udfyldningsaktivitet** og tilknyttede indikatorer, kan du vælge brugerdefinerede eller standardtærskelværdier for de indikatorudløserhændelser, du har valgt. Vælg enten Brug **standardtærskelværdier (anbefales)** eller **Brug brugerdefinerede grænseværdier for udløsningshændelser**.
16. Vælg **Næste for** at fortsætte.
17. Hvis du har valgt Brug brugerdefinerede grænseværdier **for udløsningshændelser**, skal du for hver udløserbegivenhedsindikator, du valgte i trin 13, vælge det relevante niveau for at oprette det ønskede niveau af aktivitetsbeskeder.
18. Vælg **Næste for** at fortsætte.
19. På siden **Politikindikatorer** får du vist de indikatorer, du [](insider-risk-management-settings.md#indicators) har angivet som tilgængelige, på siden Insider-risikoindstillingerIndikatorer > . Vælg de indikatorer, du vil anvende på politikken.

    > [!IMPORTANT]
    > Hvis symboler på denne side ikke kan vælges, skal du vælge de indikatorer, du vil aktivere for alle politikker. Du kan bruge knappen **Aktivér indikatorer** i guiden eller vælge indikatorer på siden **Insider-Indstillinger** >  >  **Policy-indikatorer**.

    Hvis du har valgt mindst én indikator *Office* eller *Enhedsindikator*, skal du vælge **risikoscorecores efter** behov. Risikoscorepoint gælder kun for udvalgte indikatorer.
    Hvis du har valgt en politikskabelon til *datatyveri* eller  *Datalækager*, skal du vælge en eller flere metoder  til registrering af sekvenser og en kumulativ metode til registrering af udfyldning, som kan anvendes på politikken.

20. Vælg **Næste for** at fortsætte.
21. På siden **Beslut, om du vil bruge standard** - eller brugerdefinerede indikatortærskler skal du vælge brugerdefinerede eller standardtærskelværdier for de politikindikatorer, du har valgt. Vælg enten Brug **standardtærskelværdier for alle indikatorer eller** **Angiv brugerdefinerede grænseværdier** for de valgte politikindikatorer. Hvis du har valgt Angiv brugerdefinerede grænseværdier, skal du vælge det relevante niveau for at oprette det ønskede niveau af aktivitetsbeskeder for hver politikindikator.
22. Vælg **Næste for** at fortsætte.
23. På siden **Gennemse** skal du gennemgå de indstillinger, du har valgt for politikken, samt eventuelle forslag eller advarsler for dine valg. Vælg **Rediger** for at ændre nogen af politikværdierne, eller vælg **Send** for at oprette og aktivere politikken.

## <a name="next-steps"></a>Næste trin

Når du har gennemført disse trin for at oprette din første Insider Risk Management-politik, begynder du at modtage beskeder fra aktivitetsindikatorer efter ca. 24 timer. Konfigurer yderligere politikker efter behov ved hjælp af vejledningen i trin 4 i denne artikel eller trinnene i [Opret en ny insider-risikopolitik](insider-risk-management-policies.md#create-a-new-policy).

Du kan få mere at vide om at undersøge insider-risikobeskeder og **dashboardet** Beskeder under [Insider-risikostyringsaktiviteter](insider-risk-management-activities.md#alert-dashboard).
