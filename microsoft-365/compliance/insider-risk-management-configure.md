---
title: Kom i gang med styring af insider-risiko
description: Konfigurer styring af insiderrisiko i din organisation.
keywords: Microsoft 365, Microsoft Purview, insiderrisiko, risikostyring, overholdelse af angivne standarder
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
ms.openlocfilehash: 8afb59606f4d13e96db5d4f03ffd8126c6ee9ba2
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642563"
---
# <a name="get-started-with-insider-risk-management"></a>Kom i gang med styring af insider-risiko

Brug politikker for styring af insiderrisiko til at identificere risikable aktiviteter og administrationsværktøjer til at reagere på risikobeskeder i din organisation. Fuldfør følgende trin for at konfigurere forudsætninger og konfigurere en insiderrisikostyringspolitik.

> [!IMPORTANT]
> Løsningen til styring af insiderrisiko giver en mulighed på lejerniveau for at hjælpe kunderne med at facilitere intern styring på brugerniveau. Administratorer på lejerniveau kan konfigurere tilladelser til at give medlemmer af organisationen adgang til denne løsning og konfigurere dataconnectors i Microsoft Purview-compliance-portal til at importere relevante data for at understøtte identifikation på brugerniveau af potentielt risikable aktiviteter. Kunder anerkender indsigter, der er relateret til den enkelte brugers adfærd, karakter eller ydeevne, der er relateret til beskæftigelse, kan beregnes af administratoren og gøres tilgængelige for andre i organisationen. Derudover accepterer kunderne, at de skal udføre deres egen fulde undersøgelse relateret til den enkelte brugers adfærd, karakter eller ydeevne, der er materielt relateret til beskæftigelse, og ikke bare stole på indsigt fra insiderrisikostyringstjenesten. Kunderne er alene ansvarlige for at bruge insiderrisikostyringstjenesten og alle tilknyttede funktioner eller tjenester i overensstemmelse med alle gældende love, herunder love vedrørende individuel brugeridentifikation og eventuelle afhjælpningshandlinger.

Du kan finde flere oplysninger om, hvordan insiderrisikopolitikker kan hjælpe dig med at administrere risici i din organisation, under [Få mere at vide om styring af insiderrisiko](insider-risk-management.md).

## <a name="subscriptions-and-licensing"></a>Abonnementer og licenser

Før du går i gang med styring af insiderrisiko, skal du bekræfte dit [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) og eventuelle tilføjelsesprogrammer. Din organisation skal have et af følgende abonnementer eller tilføjelsesprogrammer for at få adgang til og bruge styring af insiderrisiko:

- Microsoft 365 E5/A5/F5/G5-abonnement (betalt version eller prøveversion)
- Microsoft 365 E3/A3/F3/G3-abonnement + tilføjelsesprogrammet Microsoft 365 E5/A5/F5/G5 Compliance
- Microsoft 365 E3/A3/F3/G3-abonnement + tilføjelsesprogrammet Microsoft 365 E5/A5/F5/G5 Insider Risk Management
- Office 365 E3 abonnement + Enterprise Mobility and Security E3 + tilføjelsesprogrammet Microsoft 365 E5 Overholdelse

Brugere, der er inkluderet i politikker for styring af insiderrisiko, skal tildeles en af ovenstående licenser.

> [!IMPORTANT]
> Styring af insiderrisiko er i øjeblikket tilgængelig i lejere, der hostes i geografiske områder og lande, der understøttes af Azure-tjenesteafhængigheder. Hvis du vil bekræfte, at styring af insiderrisiko understøttes for din organisation, skal du se [Tilgængelighed af Azure-afhængighed efter land/område](/troubleshoot/azure/general/dependency-availability-by-country).

Hvis du ikke har en eksisterende Microsoft 365 Enterprise E5-plan og vil prøve insiderrisikostyring, kan du [føje Microsoft 365](/office365/admin/try-or-buy-microsoft-365) til dit eksisterende abonnement eller [tilmelde dig en prøveversion](https://www.microsoft.com/microsoft-365/enterprise) af Microsoft 365 Enterprise E5.

## <a name="recommended-actions-preview"></a>Anbefalede handlinger (prøveversion)

Anbefalede handlinger kan hjælpe din organisation med hurtigt at komme i gang med styring af insiderrisiko. De anbefalede handlinger, der er inkluderet på siden **Oversigt** , hjælper dig med at gennemgå trinnene til konfiguration og installation af politikker.

![Anbefalede handlinger til styring af insiderrisiko.](../media/insider-risk-recommended-actions.png)

Følgende anbefalinger er tilgængelige, som kan hjælpe dig med at komme i gang med eller maksimere din konfiguration af styring af insiderrisiko:

- **Slå overvågning** til: Når funktionen er slået til, registreres bruger- og administratoraktivitet i din organisation i Microsoft 365-overvågningsloggen. Politikker for insiderrisiko og analysescanninger bruger denne log til at registrere risikoaktiviteter.
- **Få tilladelser til styring af brugerrisiko**: Det adgangsniveau, du har til insiderrisikostyringsfunktioner, afhænger af, hvilken rollegruppe du blev tildelt. Hvis du vil have adgang til og konfigurere anbefalede handlinger, skal brugerne tildeles rollegrupperne *Insider Risk Management* eller *Insider Risk Management Admins* .
- **Vælg politikindikatorer**: Indikatorer er grundlæggende de brugeraktiviteter, du vil registrere og undersøge. Du kan vælge indikatorer til at spore aktiviteter på tværs af flere Microsoft 365-placeringer og -tjenester.
- **Scan for potentielle insiderrisici**: Kør en analysescanning for at finde potentielle insiderrisici, der forekommer i din organisation. Når du har evalueret resultaterne, skal du gennemse anbefalede politikker, der skal konfigureres.
- **Tildel tilladelser til andre**: Hvis der er flere teammedlemmer, der er ansvarlige for administration af insiderrisikofunktioner, skal du tildele dem til de relevante rollegrupper.
- **Opret din første politik**: Hvis du vil modtage beskeder om potentielt risikable aktiviteter, skal du konfigurere politikker baseret på foruddefinerede skabeloner, der definerer de brugeraktiviteter, du vil registrere og undersøge.

Hver anbefalet handling, der er inkluderet i denne oplevelse, har fire attributter:

- **Handling**: Navnet på og beskrivelsen af den anbefalede handling.
- **Status**: Status for den anbefalede handling. Værdier *startes ikke*, *er i gang*, *gemmes til senere* eller *er fuldført*.
- **Påkrævet eller valgfri:** Om den anbefalede handling er påkrævet eller valgfri, for at insiderrisikostyringsfunktioner kan fungere som forventet.
- **Anslået tid til fuldførelse**: Anslået tid til at fuldføre den anbefalede handling i minutter.

Vælg en anbefaling på listen for at komme i gang med at konfigurere styring af insiderrisiko. Hver anbefalet handling guider dig gennem de påkrævede aktiviteter for anbefalingen, herunder eventuelle krav, hvad du kan forvente, og virkningen af at konfigurere funktionen i din organisation.   Hver anbefalet handling markeres automatisk som fuldført, når den er konfigureret, eller du skal manuelt vælge handlingen som fuldført, når den er konfigureret.

## <a name="step-1-required-enable-permissions-for-insider-risk-management"></a>Trin 1 (påkrævet): Aktivér tilladelser til styring af insiderrisiko

> [!IMPORTANT]
> Når du har konfigureret dine rollegrupper, kan det tage op til 30 minutter, før rollegruppens tilladelser gælder for tildelte brugere på tværs af organisationen.

Der er seks rollegrupper, der bruges til at konfigurere funktioner til styring af insiderrisiko. Hvis du vil gøre **Insider-risikostyring** tilgængelig som en menuindstilling i Microsoft Purview-compliance-portal og fortsætte med disse konfigurationstrin, skal du være tildelt en af følgende roller eller rollegrupper:

- Rolle som global Azure Active [*Directory-administrator*](/azure/active-directory/roles/permissions-reference#global-administrator)
- [*Rolle som Azure Active Directory-overholdelsesadministrator*](/azure/active-directory/roles/permissions-reference#compliance-administrator)
- Microsoft Purview-compliance-portal [*rollegruppe for organisationsadministration*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- rollegruppe for Microsoft Purview-compliance-portal [*overholdelsesadministrator*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- Rollegruppe *for styring af insiderrisiko*
- *Rollegruppen Insider Risk Management Administration*

Afhængigt af hvordan du vil administrere politikker og beskeder for styring af insiderrisiko, skal du tildele brugere til bestemte rollegrupper for at administrere forskellige sæt insiderrisikostyringsfunktioner. Du har mulighed for at tildele brugere med forskellige overholdelsesansvar til bestemte rollegrupper for at administrere forskellige områder af insiderrisikostyringsfunktioner. Du kan også vælge at tildele alle brugerkonti for udpegede administratorer, analytikere, efterforskere og seere til rollegruppen Insider Risk Management. Brug en enkelt rollegruppe eller flere rollegrupper, så de passer bedst til dine krav til administration af overholdelse.

Du skal vælge mellem disse indstillinger for rollegrupper og løsningshandlinger, når du arbejder med styring af insiderrisiko:

|Handlinger|Styring af insiderrisiko|Styring af insiderrisiko Administration|Analytikere af styring af insider-risiko|Undersøgere af styring af insider-risiko|Auditører for styring af insiderrisiko|
|---|---|---|---|---|---|
|Konfigurer politikker og indstillinger|Ja|Ja|Nej|Nej|Nej|
|Få adgang til indsigt i analyse|Ja|Ja|Ja|Nej|Nej|
|Få adgang & undersøge beskeder|Ja|Nej|Ja|Ja|Nej|
|Adgang & undersøge sager|Ja|Nej|Ja|Ja|Nej|
|Få adgang & få vist Indholdsoversigt|Ja|Nej|Nej|Ja|Nej|
|Konfigurer meddelelsesskabeloner|Ja|Nej|Ja|Ja|Nej|
|Vis & eksport af overvågningslogge|Ja|Nej|Nej|Nej|Ja|

> [!IMPORTANT]
> Sørg for, at du altid har mindst én bruger i *Insider Risk Management* eller *Insider Risk Management Administration* rollegrupper (afhængigt af den indstilling, du vælger), så konfigurationen af styring af insiderrisiko ikke kommer ind i et scenarie med "nul administrator", hvis bestemte brugere forlader organisationen.

Medlemmer af følgende roller kan tildele brugere til insiderrisikostyringsrollegrupper og have de samme løsningstilladelser som i rollegruppen *Insider Risk Management Administration*:

- Global Azure Active *Directory-administrator*
- Azure Active Directory *Compliance Administrator*
- Microsoft Purview-compliance-portal *organisationsstyring*
- Microsoft Purview-compliance-portal *overholdelsesadministrator*

> [!NOTE]
> Disse rollegrupper understøttes i øjeblikket ikke på Privileged Identity Management (PIM). Du kan få mere at vide om PIM under [Tildel Azure AD roller i Privileged Identity Management](/azure/active-directory/privileged-identity-management/pim-how-to-add-role-to-user).

### <a name="add-users-to-an-insider-risk-management-role-group"></a>Føj brugere til en rollegruppe for styring af insiderrisiko

Fuldfør følgende trin for at føje brugere til en rollegruppe for styring af insiderrisiko:

1. Log på [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365-organisation.

2. I Security &amp; Compliance Center skal du gå til **Tilladelser**. Vælg linket for at få vist og administrere roller i Office 365.

3. Vælg den insiderrisikostyringsrollegruppe, du vil føje brugere til, og vælg derefter **Rediger rollegruppe**.

4. Vælg **Vælg medlemmer** i navigationsruden til venstre, og vælg derefter **Rediger**.

5. Vælg **Tilføj** , og markér derefter afkrydsningsfeltet for alle de brugere, du vil føje til rollegruppen.

6. Vælg **Tilføj**, og vælg derefter **Udført**.

7. Vælg **Gem** for at føje brugerne til rollegruppen. Vælg **Luk** for at fuldføre trinnene.

## <a name="step-2-required-enable-the-microsoft-365-audit-log"></a>Trin 2 (påkrævet): Aktivér Microsoft 365-overvågningsloggen

Insiderrisikostyring bruger Microsoft 365-overvågningslogge til brugerindsigt og aktiviteter, der er identificeret i politikker og analyseindsigt. Microsoft 365-overvågningslogge er en oversigt over alle aktiviteter i din organisation, og politikker for styring af insiderrisiko kan bruge disse aktiviteter til at generere indsigt i politikker.

Overvågning er som standard aktiveret for Microsoft 365-organisationer. Nogle organisationer kan have deaktiveret overvågning af bestemte årsager. Hvis overvågning er deaktiveret for din organisation, kan det skyldes, at en anden administrator har deaktiveret den. Vi anbefaler, at du bekræfter, at det er OK at aktivere overvågning igen, når du fuldfører dette trin.

Du kan finde en trinvis vejledning til, hvordan du slår overvågning til, under [Slå søgning i overvågningslog til eller fra](turn-audit-log-search-on-or-off.md). Når du har slået overvågning til, vises der en meddelelse om, at overvågningsloggen er ved at blive forberedt, og at du kan køre en søgning om et par timer, efter at forberedelsen er fuldført. Du behøver kun at gøre denne handling én gang. Du kan finde flere oplysninger om, hvordan du bruger Microsoft 365-overvågningsloggen, under [Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-enable-and-view-insider-risk-analytics-insights"></a>Trin 3 (valgfrit): Aktivér og få vist indsigt i insiderrisikoanalyse

Analyse af styring af insiderrisiko giver dig mulighed for at evaluere potentielle insiderrisici i din organisation uden at konfigurere nogen politikker for insiderrisiko. Denne evaluering kan hjælpe din organisation med at identificere potentielle områder med højere brugerrisiko og hjælpe med at bestemme typen og omfanget af politikker for styring af insiderrisiko, som du kan overveje at konfigurere. Denne evaluering kan også hjælpe dig med at bestemme behovet for yderligere licensering eller fremtidig optimering af eksisterende politikker. Resultaterne af analysescanningen kan tage op til 48 timer, før indsigt er tilgængelig som rapporter til gennemsyn. Du kan få mere at vide om indsigt i analyse under [Indstillinger for styring af insiderrisiko: Analytics](insider-risk-management-settings.md#analytics) og se [videoen Insider Risk Management Analytics](https://www.youtube.com/watch?v=5c0P5MCXNXk) for at få hjælp til at forstå, hvordan analyser kan hjælpe med at fremskynde identifikationen af potentielle insiderrisici og hjælpe dig med hurtigt at handle.

Hvis du vil aktivere insiderrisikoanalyse, skal du være medlem af rollegruppen *Insider Risk Management*, *Insider Risk Management Administration* eller Microsoft 365 *Global admin*.

Fuldfør følgende trin for at aktivere insiderrisikoanalyse:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Insider Risk Management**.
2. Vælg **Kør scanning** på fanen **Scan for insiderrisici på dit organisationskort** under fanen **Oversigt over** styring af insiderrisiko. Denne handling aktiverer analysescanning for din organisation. Du kan også aktivere scanning i din organisation ved at gå til **Insider-risikoindstillinger** > **Analytics** og aktivere **Scan din lejers brugeraktivitet for at identificere potentielle insiderrisici**.
3. I ruden **Analysedetaljer** skal du vælge **Kør scanning for at starte scanningen for din organisation**. Resultaterne af analysescanningen kan tage op til 48 timer, før indsigt er tilgængelig som rapporter til gennemsyn.

Når du har gennemset indsigterne i analyser, skal du vælge politikker for insiderrisiko og konfigurere de tilknyttede forudsætninger, der bedst opfylder organisationens strategi til reduktion af insiderrisiko.

## <a name="step-4-recommended-configure-prerequisites-for-policies"></a>Trin 4 (anbefales): Konfigurer forudsætninger for politikker

De fleste politikker til styring af insiderrisiko har forudsætninger, der skal konfigureres, for at politikindikatorer kan generere relevante aktivitetsbeskeder. Konfigurer de relevante forudsætninger afhængigt af de politikker, du planlægger at konfigurere for din organisation.

### <a name="configure-microsoft-365-hr-connector"></a>Konfigurer Microsoft 365 HR-connector

Styring af insiderrisiko understøtter import af bruger- og logdata, der er importeret fra tredjepartsplatforme for risikostyring og HR. Microsoft 365 HR-dataconnectoren giver dig mulighed for at hente HR-data ind fra CSV-filer, herunder datoer for brugerterminering, seneste ansættelsesdatoer, meddelelser om ydeevneforbedringsplan, handlinger til gennemsyn af ydeevne og status for ændring af jobniveau. Disse data hjælper med at skabe advarselsindikatorer i politikker for styring af insiderrisiko og er en vigtig del af konfigurationen af fuld dækning af risikostyring i din organisation. Hvis du konfigurerer mere end én HR-connector for din organisation, henter insiderrisikostyring automatisk indikatorer fra alle HR-connectors.

Microsoft 365 HR-connectoren er påkrævet, når du bruger følgende politikskabeloner:

- Datalækager fra utilfredse brugere
- Fjernelse af brugerdatatyveri
- Generel misbrug af patientdata
- Sikkerhedspolitikovertrædelser af afrejsende brugere
- Sikkerhedspolitiske overtrædelser af utilfredse brugere

Se artiklen [Konfigurer en connector til import af HR-data](import-hr-data.md) for at få en trinvis vejledning til, hvordan du konfigurerer Microsoft 365 HR-connectoren for din organisation. Når du har konfigureret HR-connectoren, skal du vende tilbage til disse konfigurationstrin.

### <a name="configure--a-healthcare-specific-data-connector"></a>Konfigurer en sundhedsspecifik dataconnector

Styring af insiderrisiko understøtter import af bruger- og logdata, der er importeret fra tredjepart, på eksisterende EMR-systemer (Electronic Medical Record). Microsoft Healthcare- og Epic-dataconnectors giver dig mulighed for at hente aktivitetsdata fra dit EMR-system med CSV-filer, herunder forkert adgang til patientpost, mistænkelige volumenaktiviteter samt redigerings- og eksportaktiviteter. Disse data hjælper med at skabe advarselsindikatorer i politikker for styring af insiderrisiko og er en vigtig del af konfigurationen af fuld dækning af risikostyring i din organisation.

Hvis du konfigurerer mere end én Healthcare- eller Epic-connector for din organisation, understøtter insiderrisikostyring automatisk hændelses- og aktivitetssignaler fra alle Healthcare- og Epic-connectors.
Microsoft 365 Healthcare- eller Epic-connectoren er påkrævet, når du bruger følgende politikskabeloner:

- Generel misbrug af patientdata

Se artiklen [Konfigurer en connector til import af sundhedsdata](import-healthcare-data.md) eller [Konfigurer en connector til import af Epic EHR-data](import-epic-data.md) for at få en trinvis vejledning til, hvordan du konfigurerer en sundhedsspecifik connector for din organisation. Når du har konfigureret en connector, skal du vende tilbage til disse konfigurationstrin.

### <a name="configure-data-loss-prevention-dlp-policies"></a>Konfigurer DLP-politikker (Forebyggelse af datatab)

Styring af insiderrisiko understøtter brug af DLP-politikker til at identificere bevidst eller utilsigtet eksponering af følsomme oplysninger for uønskede parter i forbindelse med DLP-beskeder på højt alvorsgradniveau. Når du konfigurerer en politik for styring af insiderrisiko med en af skabelonerne **til datalækage,** har du mulighed for at tildele en bestemt DLP-politik til politikken for disse typer beskeder.

DLP-politikker hjælper med at identificere brugere for at aktivere risikoscore i styring af insiderrisiko for DLP-beskeder med høj alvorsgrad for følsomme oplysninger og er en vigtig del af konfiguration af fuld dækning af styring af risici i din organisation. Du kan få flere oplysninger om insiderrisikostyring og DLP-politikintegration og overvejelser i forbindelse med planlægning under [Politikker for styring af insiderrisiko](insider-risk-management-policies.md#general-data-leaks).

> [!IMPORTANT]
>Kontrollér, at du har fuldført følgende:
>
> - Du forstår og konfigurerer brugerne i området korrekt i både DLP- og insiderrisikostyringspolitikker for at skabe den politikdækning, du forventer.
> - Sørg for, at indstillingen **Hændelsesrapporter** i DLP-politikken for styring af insiderrisiko, der bruges sammen med disse skabeloner, er konfigureret til beskeder på *højt* alvorsgradsniveau. Beskeder om styring af insiderrisiko genereres ikke fra DLP-politikker med feltet **Hændelsesrapporter** angivet til *Lav* eller *Mellem*.

En DLP-politik er valgfri, når du bruger følgende politikskabeloner:

- Generelle datalækager
- Datalækager fra prioriterede brugere

Se artiklen [Opret, test og juster en DLP-politik](create-test-tune-dlp-policy.md) for at få en trinvis vejledning til, hvordan du konfigurerer DLP-politikker for din organisation. Når du har konfigureret en DLP-politik, skal du vende tilbage til disse konfigurationstrin.

### <a name="configure-priority-user-groups"></a>Konfigurer prioritetsbrugergrupper

Styring af insiderrisiko omfatter understøttelse af tildeling af prioriterede brugergrupper til politikker for at hjælpe med at identificere entydige risikoaktiviteter for brugere med kritiske positioner, høje niveauer af data og netværksadgang eller en tidligere oversigt over risikoadfærd. Oprettelse af en prioriteret brugergruppe og tildeling af brugere til gruppen hjælper med at tilpasse politikkerne til de entydige omstændigheder, som disse brugere præsenteres for.

Der kræves en prioritetsbrugergruppe, når følgende politikskabeloner bruges:

- Sikkerhedspolitiske overtrædelser af prioriterede brugere
- Datalækager fra prioriterede brugere

Se artiklen [Introduktion til indstillinger for styring af insiderrisiko](insider-risk-management-settings.md#priority-user-groups-preview) for at få en trinvis vejledning til, hvordan du opretter en prioriteret brugergruppe. Når du har konfigureret en prioriteret brugergruppe, skal du gå tilbage til disse konfigurationstrin.

### <a name="configure-physical-badging-connector-optional"></a>Konfigurer den fysiske dårligging-connector (valgfrit)

Styring af insiderrisiko understøtter import af bruger- og logdata fra fysiske kontrol- og adgangsplatforme. Med den fysiske badging-connector kan du hente adgangsdata fra JSON-filer, herunder bruger-id'er, adgangspunkt-id'er, adgangstidspunkt og -datoer og adgangsstatus. Disse data hjælper med at skabe advarselsindikatorer i politikker for styring af insiderrisiko og er en vigtig del af konfigurationen af fuld dækning af risikostyring i din organisation. Hvis du konfigurerer mere end én fysisk badging-connector for din organisation, henter styring af insiderrisiko automatisk indikatorer fra alle fysiske dårligging-connectors. Oplysninger fra den fysiske badging-connector supplerer andre insiderrisikosignaler, når alle skabeloner for insiderrisikopolitik bruges.

> [!IMPORTANT]
> Hvis politikker for styring af insiderrisiko skal bruge og korrelere signaldata, der er relateret til afrejsende og afbrudte brugere med hændelsesdata fra dine fysiske kontrol- og adgangsplatforme, skal du også konfigurere Microsoft 365 HR-connectoren. Hvis du aktiverer den fysiske badging-connector uden at aktivere Microsoft 365 HR-connectoren, behandler politikker for styring af insiderrisiko kun hændelser for uautoriseret fysisk adgang for brugere i din organisation.

Se artiklen [Konfigurer en connector til import af fysiske badging-data](import-physical-badging-data.md) for at få en trinvis vejledning til, hvordan du konfigurerer den fysiske badging-connector for din organisation. Når du har konfigureret connectoren, skal du vende tilbage til disse konfigurationstrin.

### <a name="configure-microsoft-defender-for-endpoint-optional"></a>Konfigurer Microsoft Defender for Endpoint (valgfrit)

[Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) er en sikkerhedsplatform til virksomhedsslutpunkter, der er udviklet til at hjælpe virksomhedsnetværk med at forhindre, registrere, undersøge og reagere på avancerede trusler. Hvis du vil have bedre synlighed af sikkerhedsovertrædelser i din organisation, kan du importere og filtrere Defender for Endpoint-beskeder for aktiviteter, der bruges i politikker, der er oprettet ud fra skabeloner til sikkerhedsovertrædelse for insiderrisikostyring.

Hvis du opretter politikker for sikkerhedsovertrædelse, skal du have Microsoft Defender for Endpoint konfigureret i din organisation og aktivere Defender for Endpoint for integration af styring af insiderrisiko i Defender Security Center for at importere beskeder om sikkerhedsovertrædelse. Du kan få flere oplysninger om krav i artiklen [Minimumkrav til Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements).

Se artiklen [Konfigurer avancerede funktioner i Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/advanced-features#share-endpoint-alerts-with-microsoft-compliance-center) for at få en trinvis vejledning til, hvordan du konfigurerer Defender for Endpoint til integration af styring af insiderrisiko. Når du har konfigureret Microsoft Defender for Endpoint, skal du vende tilbage til disse konfigurationstrin.

## <a name="step-5-required-configure-insider-risk-settings"></a>Trin 5 (påkrævet): Konfigurer indstillinger for insiderrisiko

[Indstillinger for insiderrisiko](insider-risk-management-settings.md) gælder for alle politikker for styring af insiderrisiko, uanset hvilken skabelon du vælger, når du opretter en politik. Indstillinger konfigureres ved hjælp af kontrolelementet **Insider-risikoindstillinger** , der er placeret øverst på alle faner til styring af insiderrisiko. Disse indstillinger styrer beskyttelse af personlige oplysninger, indikatorer, overvågningsvinduer og intelligente registreringer.

Før du konfigurerer en politik, skal du definere følgende indstillinger for insiderrisiko:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til Styring af **insiderrisiko** og vælge **Insider-risikoindstillinger** i øverste højre hjørne af en hvilken som helst side.
2. På siden **Beskyttelse af personlige oplysninger** skal du vælge en indstilling for beskyttelse af personlige oplysninger for at få vist brugernavne for politikbeskeder.
3. På siden **Indikatorer** skal du vælge de beskedindikatorer, du vil anvende på alle politikker for insiderrisiko.

    > [!IMPORTANT]
    > Hvis du vil modtage beskeder om risikable aktiviteter, der er defineret i dine politikker, skal du vælge en eller flere indikatorer. Hvis indikatorer ikke er konfigureret i Indstillinger, kan indikatorerne ikke vælges i politikker for insiderrisiko.

4. På siden **Politiktidsrammer** skal du vælge de [politiktidsrammer](insider-risk-management-settings.md#policy-timeframes) , der skal træde i kraft for en bruger, når de udløser et match for en insiderrisikopolitik.
5. Konfigurer følgende indstillinger for politikker for insiderrisiko på siden **Intelligente registreringer** :
    - [Undtagelser for filtype](insider-risk-management-settings.md#file-type-exclusions)
    - [Minimum antal daglige hændelser for at øge scoren for usædvanlig aktivitet](insider-risk-management-settings.md#minimum-number-of-daily-events-to-boost-score-for-unusual-activity)
    - [Niveau for beskedmængde](insider-risk-management-settings.md#alert-volume)
    - [Microsoft Defender for Endpoint beskedstatus](insider-risk-management-settings.md#microsoft-defender-for-endpoint-preview)
    - [Domæneindstillinger](insider-risk-management-settings.md#domains)
6. På siden **Eksportér beskeder** skal du aktivere eksport af oplysninger om insiderrisikobeskeder ved hjælp af API'erne til administration af Office 365, hvis det er nødvendigt.
7. På siden **Prioriterede brugergrupper** skal du oprette en prioriteret brugergruppe og tilføje brugere, hvis de ikke er oprettet i **trin 3**.
8. Konfigurer et flow fra skabeloner for insiderrisikoflow på siden **Power Automate-flow** , eller opret et nyt flow. Se artiklen [Introduktion til indstillinger for styring af insiderrisiko](insider-risk-management-settings.md#power-automate-flows-preview) for at få en trinvis vejledning.
9. På **siden Prioritetsaktiver** skal du konfigurere prioritetsaktiver til at bruge data fra din fysiske kontrol- og adgangsplatform, der er importeret af connectoren Physical badging. Se artiklen [Introduktion til indstillinger for styring af insiderrisiko](insider-risk-management-settings.md#priority-physical-assets-preview) for at få en trinvis vejledning.
10. På siden **Microsoft Teams** skal du aktivere Microsoft Teams-integration med insiderrisikostyring for automatisk at oprette et team til sag- eller brugersamarbejde. Se artiklen [Introduktion til indstillinger for styring af insiderrisiko](insider-risk-management-settings.md#microsoft-teams-preview) for at få en trinvis vejledning.
11. Vælg **Gem** for at aktivere disse indstillinger for dine politikker for insiderrisiko.

## <a name="step-6-required-create-an-insider-risk-management-policy"></a>Trin 6 (påkrævet): Opret en politik for styring af insiderrisiko

Politikker for styring af insiderrisiko omfatter tildelte brugere og definerer, hvilke typer risikoindikatorer der er konfigureret til beskeder. Før aktiviteter kan udløse beskeder, skal der konfigureres en politik. Brug guiden Politik til at oprette nye politikker for styring af insiderrisiko.

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Politikker**.
2. Vælg **Opret politik** for at åbne politikguiden.
3. Vælg en politikkategori på siden **Politikskabelon** , og vælg derefter skabelonen til den nye politik. Disse skabeloner består af betingelser og indikatorer, der definerer de risikoaktiviteter, du vil registrere og undersøge. Gennemse skabelonforudsætningerne, udløsende hændelser og registrerede aktiviteter for at bekræfte, at denne politikskabelon passer til dine behov.

    > [!IMPORTANT]
    > Nogle politikskabeloner har forudsætninger, der skal konfigureres, for at politikken kan generere relevante beskeder. Hvis du ikke har konfigureret de relevante politikforudsætningerne, skal du se **trin 4** ovenfor.

4. Vælg **Næste** for at fortsætte.
5. Udfyld følgende felter på siden **Navn og beskrivelse** :
    - **Navn (obligatorisk)**: Angiv et brugervenligt navn til politikken. Dette navn kan ikke ændres, når politikken er oprettet.
    - **Beskrivelse (valgfrit)**: Angiv en beskrivelse af politikken.

6. Vælg **Næste** for at fortsætte.
7. På siden **Brugere og grupper** skal du vælge **Medtag alle brugere og grupper** eller **Medtag bestemte brugere og grupper** for at definere, hvilke brugere eller grupper der er inkluderet i politikken, eller hvis du har valgt en prioriteret brugerbaseret skabelon. vælg **Tilføj eller rediger prioritetsbrugergrupper**. Hvis du vælger **Medtag alle brugere og grupper** , vil du søge efter udløsende hændelser for alle brugere og grupper i din organisation for at begynde at tildele risikoscores til politikken. Hvis du vælger **Medtag bestemte brugere og grupper** , kan du definere, hvilke brugere og grupper der skal tildeles politikken. Gæstebrugerkonti understøttes ikke.
8. Vælg **Næste** for at fortsætte.
9. På siden Indhold, der **skal prioriteres** kan du tildele (hvis det er nødvendigt) de kilder, der skal prioriteres, hvilket øger chancen for at generere en besked med høj alvorsgrad for disse kilder. Vælg et af følgende muligheder:

    - **Jeg vil angive SharePoint-websteder, følsomhedsmærkater, typer af følsomme oplysninger og/eller filtypenavne som prioriteret indhold**. Hvis du vælger denne indstilling, kan detaljesider i guiden konfigurere disse kanaler.
    - **Jeg vil ikke angive prioritetsindhold lige nu (det kan du gøre, når politikken er oprettet).** Hvis du vælger denne indstilling, springes kanaldetaljesiderne i guiden over.

10. Vælg **Næste** for at fortsætte.

11. Hvis du har valgt **Jeg vil angive SharePoint-websteder, følsomhedsmærkater, typer af følsomme oplysninger og/eller filtypenavne som prioriteret indhold** i det forrige trin, får du vist detaljesiderne for *SharePoint-websteder*, *følsomme oplysningstyper*, *følsomhedsmærkater* og *filtypenavne*. Brug disse detaljesider til at definere SharePoint, følsomme infotyper, følsomhedsmærkater og filtypenavne, der skal prioriteres i politikken.

    - **SharePoint-websteder**: Vælg **Tilføj SharePoint-websted** , og vælg de SharePoint-websteder, du har adgang til, og som du vil prioritere. For eksempel *"group1@contoso.sharepoint.com/sites/group1"*.
    - **Type af følsomme oplysninger**: Vælg **Tilføj type følsomme oplysninger** , og vælg de følsomhedstyper, du vil prioritere. Det kan f.eks *. være "Bankkontonummer for USA"* og *"Kreditkortnummer"*.
    - **Følsomhedsmærkater**: Vælg **Tilføj følsomhedsmærkat** , og vælg de mærkater, du vil prioritere. Det kan f.eks. være *"Fortroligt"* og *"Hemmelig"*.
    - Filtypenavne: Tilføj op til 50 filtypenavne. Du kan medtage eller udelade '.' med filtypenavnet. *.py* eller *py* vil f.eks. prioritere Python-filer.

    > [!NOTE]
    > Brugere, der konfigurerer politikken og vælger prioriterede Share Point-websteder, kan vælge SharePoint-websteder, som de har tilladelse til at få adgang til. Hvis den aktuelle bruger ikke kan vælge SharePoint-websteder i politikken, kan en anden bruger med de nødvendige tilladelser vælge webstederne til politikken senere, eller den aktuelle bruger skal have adgang til de påkrævede websteder.

12. Vælg **Næste** for at fortsætte.
13. Hvis du har valgt skabelonerne *Generelle datalækager* eller *Datalækager af prioriterede brugere* , kan du se indstillinger på siden **Udløsere** for denne politikside for hændelser med brugerdefinerede udløsere og politikindikatorer. Du har mulighed for at vælge en DLP-politik eller indikatorer til udløsning af hændelser, der giver brugere, der er tildelt politikken, adgang til aktivitetsscore. Hvis du vælger indstillingen **Bruger matcher en politik til forebyggelse af datatab (DLP),** skal du vælge en DLP-politik på rullelisten DLP-politik for at aktivere udløserindikatorer for DLP-politikken for denne politik for styring af insiderrisiko. Hvis du vælger indstillingen **Bruger, der udløser en eksfiltrationsaktivitet** , skal du vælge en eller flere af de viste indikatorer for hændelsen, der udløser politikken.

    > [!IMPORTANT]
    > Hvis du ikke kan vælge en angivet indikator, skyldes det, at de ikke er aktiveret for din organisation. Hvis du vil gøre dem tilgængelige for at vælge og tildele til politikken, skal du aktivere indikatorerne i **Indstillinger for styring** **af insiderrisikostyring** >  > **Politikindikatorer**.

    Hvis du har valgt andre politikskabeloner, understøttes brugerdefinerede udløserhændelser ikke. De indbyggede hændelser for politikudløsende handlinger gælder, og du fortsætter til trin 23 uden at definere politikattributter.

14. Vælg **Næste** for at fortsætte.
15. Hvis du har valgt skabelonerne *Generelle datalækager* eller *Datalækager af prioriterede brugere* og har valgt **, at Brugeren udfører en eksfiltrationsaktivitet og tilknyttede indikatorer**, kan du vælge brugerdefinerede tærskler eller standardgrænser for de indikatorudløsende hændelser, du har valgt. Vælg enten **Brug standardtærskler (anbefales)** eller **Brug brugerdefinerede tærskler for udløserhændelser**.
16. Vælg **Næste** for at fortsætte.
17. Hvis du har valgt **Brug brugerdefinerede tærskler for udløserhændelser**, skal du for hver indikator for udløsende hændelser, som du valgte i trin 13, vælge det relevante niveau for at generere det ønskede niveau af aktivitetsbeskeder. Du kan bruge de anbefalede tærskler, brugerdefinerede tærskler eller tærskler baseret på unormale aktiviteter (for visse indikatorer) over den daglige norm for brugere.
18. Vælg **Næste** for at fortsætte.
19. På siden **Politikindikatorer** kan du se de [indikatorer](insider-risk-management-settings.md#indicators), du har defineret som tilgængelige på siden **Indikatorer** **for insiderrisikoindstillinger** > . Vælg de indikatorer, du vil anvende på politikken.

    > [!IMPORTANT]
    > Hvis indikatorer på denne side ikke kan vælges, skal du vælge de indikatorer, du vil aktivere for alle politikker. Du kan bruge knappen **Slå indikatorer** til i guiden eller vælge indikatorer på siden **Indstillinger for politikindikatorer** >  **for styring af insiderrisikostyring** > .

    Hvis du har valgt mindst én *Office* - eller *enhedsindikator* , skal du vælge **boosterne for risikoscore** efter behov. Boostere til risikoscore gælder kun for udvalgte indikatorer.
    Hvis du har valgt en politikskabelon *for datatyveri* eller *datalækager* , skal du vælge en eller flere metoder til **registrering af sekvenser** og en kumulativ metode til **registrering af eksfiltration** , der skal anvendes på politikken.

20. Vælg **Næste** for at fortsætte.
21. På siden **Beslut, om du vil bruge standardtærskelværdier eller brugerdefinerede indikatortærskler** , skal du vælge brugerdefinerede eller standardgrænser for de politikindikatorer, du har valgt. Vælg enten **Brug standardgrænser for alle indikatorer** eller **Angiv brugerdefinerede tærskler** for de valgte politikindikatorer. Hvis du har valgt Angiv brugerdefinerede tærskler, skal du vælge det relevante niveau for at generere det ønskede niveau af aktivitetsbeskeder for hver politikindikator.
22. Vælg **Næste** for at fortsætte.
23. Gennemse de indstillinger, du har valgt for politikken, og eventuelle forslag eller advarsler til dine valg på siden **Gennemse** . Vælg **Rediger** for at ændre en af politikværdierne, eller vælg **Send** for at oprette og aktivere politikken.

## <a name="next-steps"></a>Næste trin

Når du har fuldført disse trin for at oprette din første politik for styring af insiderrisiko, begynder du at modtage beskeder fra aktivitetsindikatorer efter ca. 24 timer. Konfigurer yderligere politikker efter behov ved hjælp af vejledningen i trin 4 i denne artikel eller trinnene i [Opret en ny politik for insiderrisiko](insider-risk-management-policies.md#create-a-new-policy).

Hvis du vil vide mere om undersøgelse af insiderrisikobeskeder og **dashboardet Beskeder**, skal du se [Aktiviteter til styring af insiderrisiko](insider-risk-management-activities.md#alert-dashboard).
