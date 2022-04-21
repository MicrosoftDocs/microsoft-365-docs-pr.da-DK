---
title: Overvågningsløsninger til Microsoft Purview
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- m365-security-compliance
- m365solution-audit
- m365initiative-compliance
- m365solution-overview
search.appverid:
- MOE150
- MET150
description: Få mere at vide om, hvordan du overvåger brugeres og administratorers aktiviteter i din Microsoft 365 organisation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ee11ee5e02ee4342921776124813b71cf4468ad7
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001406"
---
# <a name="auditing-solutions-in-microsoft-purview"></a>Overvågning af løsninger i Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview-overvågningsløsninger indeholder en integreret løsning, der kan hjælpe organisationer med effektivt at reagere på sikkerhedshændelser, retsmedicinske undersøgelser, interne undersøgelser og overholdelse af angivne standarder. Tusindvis af bruger- og administratorhandlinger, der udføres i mange Microsoft 365 tjenester og løsninger, registreres, registreres og bevares i din organisations samlede overvågningslog. Der kan søges i overvågningsposter for disse hændelser af sikkerhedsadministratorer, it-administratorer, insiderrisikoteams og overholdelses- og juridiske efterforskere i din organisation. Denne funktion giver indblik i de aktiviteter, der udføres på tværs af din Microsoft 365 organisation.

## <a name="microsoft-purview-auditing-solutions"></a>Overvågningsløsninger til Microsoft Purview

Microsoft Purview indeholder to overvågningsløsninger: Audit (Standard) og Audit (Premium).

![Vigtige funktioner i Audit (Standard) og Audit (Premium).](..\media\AuditingSolutionsComparison.png)

### <a name="audit-standard"></a>Overvågning (standard)

Microsoft Purview Audit (Standard) giver dig mulighed for at logge og søge efter overvågede aktiviteter og styrke dine kriminaltekniske, it-, overholdelses- og juridiske undersøgelser.

- **Aktiveret som standard**. Overvågning (Standard) er som standard slået til for alle organisationer med det relevante abonnement. Det betyder, at poster for overvågede aktiviteter registreres og kan søges i. Den eneste konfiguration, der kræves, er at tildele de nødvendige tilladelser til at få adgang til søgeværktøjet til overvågningsloggen (og den tilsvarende cmdlet) og sikre, at brugerens er tildelt den rette licens til Funktioner i Microsoft Purview Audit (Premium).
- **Tusindvis af overvågningshændelser, der kan søges i**. Du kan søge efter en lang række overvågede aktiviteter, der forekommer, er de fleste af de Microsoft 365 tjenester i din organisation. Du kan finde en delvis liste over de aktiviteter, du kan søge efter, under [Overvågede aktiviteter](search-the-audit-log-in-security-and-compliance.md#audited-activities). Du kan se en liste over de tjenester og funktioner, der understøtter overvågede aktiviteter, under [Overvågningslogposttype](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).
- **Overvåg søgeværktøjet på Microsoft Purview-overholdelsesportalen**. Brug søgeværktøjet Overvågningslog på overholdelsesportalen til at søge efter overvågningsposter. Du kan søge efter bestemte aktiviteter, aktiviteter, der er udført af bestemte brugere, og aktiviteter, der fandt sted med et datointerval. Her er et skærmbillede af værktøjet Til overvågning af søgning i Overholdelsescenter.

   ![Søgeværktøj til overvågningslog på overholdelsesportalen.](../media/AuditLogSearchToolMCC.png)

- **Search-UnifiedAuditLog-cmdlet**. Du kan også bruge cmdlet'en **Search-UnifiedAuditLog** i Exchange Online PowerShell (den underliggende cmdlet til søgeværktøjet) til at søge efter overvågningshændelser eller til at bruge i et script. Du kan finde flere oplysninger under:

  - [Reference til search-UnifiedAuditLog-cmdlet](/powershell/module/exchange/search-unifiedauditlog)
  - [Brug et PowerShell-script til at søge i overvågningsloggen](audit-log-search-script.md)

- **Eksportér overvågningsposter til en CSV-fil**. Når du har kørt søgeværktøjet Overvågningslog i Overholdelsescenter, kan du eksportere de overvågningsposter, der returneres af søgningen, til en CSV-fil. Det giver dig mulighed for at bruge Microsoft Excel sortere og filtrere på forskellige egenskaber for overvågningsposter. Du kan også bruge Excel Power Query transformeringsfunktionalitet til at opdele hver egenskab i AuditData JSON-objektet i sin egen kolonne. Det giver dig mulighed for effektivt at få vist og sammenligne lignende data for forskellige hændelser. Du kan finde flere oplysninger under [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md).

- **Adgang til overvågningslogge via api'en til administration af Office 365**. En tredje metode til at få adgang til og hente overvågningsposter er at bruge API'en til administration af Office 365. Dette gør det muligt for organisationer at bevare overvågningsdata i længere perioder end de 90 standarddage, og gør det muligt for dem at importere deres overvågningsdata til en SIEM-løsning. Du kan få flere oplysninger under [Office 365 API-reference til administrationsaktivitet](/office/office-365-management-api/office-365-management-activity-api-reference).

- **90-dages opbevaring af overvågningslog**. Når en overvåget aktivitet udføres af en bruger eller administrator, oprettes der en overvågningspost, som gemmes i overvågningsloggen for din organisation. I Overvågning (Standard) bevares poster i 90 dage, hvilket betyder, at du kan søge efter aktiviteter, der er opstået inden for de seneste tre måneder.

### <a name="audit-premium"></a>Overvågning (Premium)

Overvågning (Premium) bygger på funktionerne i Audit (Standard) ved at levere politikker for opbevaring af overvågningslog, længere opbevaring af overvågningsposter, vigtige hændelser af høj værdi og større båndbreddeadgang til API'en til administration af Office 365.

- **Politikker for opbevaring af overvågningslog**. Du kan oprette brugerdefinerede politikker for opbevaring af overvågningslog for at bevare overvågningsposter i længere tid op til ét år (og op til 10 år for brugere med den påkrævede licens til tilføjelsesprogrammet). Du kan oprette en politik for at bevare overvågningsposter baseret på den tjeneste, hvor de overvågede aktiviteter finder sted, bestemte overvågede aktiviteter eller den bruger, der udfører en overvåget aktivitet.

- **Længere opbevaring af overvågningsposter**. Exchange, SharePoint og Azure Active Directory-overvågningsposter bevares som standard i ét år. Overvågningsposter for alle andre aktiviteter bevares som standard i 90 dage, eller du kan bruge opbevaringspolitikker for overvågningslog til at konfigurere længere opbevaringsperioder.

- **Vigtige overvågningshændelser (Premium) med høj værdi**. Overvågningsposter for vigtige hændelser kan hjælpe din organisation med at udføre tekniske undersøgelser og undersøgelser af overholdelse af angivne standarder ved at give synlighed til hændelser, f.eks. hvornår mailelementer blev åbnet, eller hvornår mailelementer blev besvaret og videresendt, eller hvornår og hvad en bruger søgte efter i Exchange Online og SharePoint Online. Disse vigtige hændelser kan hjælpe dig med at undersøge mulige brud og fastlægge omfanget af kompromiser.

- **Højere båndbredde til API'en til administration af Office 365**. Overvågning (Premium) giver organisationer større båndbredde til at få adgang til overvågningslogge via API'en til administration af Office 365. Selvom alle organisationer (der har Audit (Standard) eller Audit (Premium)) indledningsvist tildeles en baseline på 2.000 anmodninger pr. minut, øges denne grænse dynamisk afhængigt af en organisations antal pladser og deres licensabonnement. Dette resulterer i, at organisationer med Audit (Premium) får ca. dobbelt så meget båndbredde som organisationer med Audit (Standard).

Du kan finde flere detaljerede oplysninger om overvågningsfunktioner (Premium) [under Overvågning (Premium) i Microsoft 365](advanced-audit.md).

## <a name="comparison-of-key-capabilities"></a>Sammenligning af nøglefunktioner

I følgende tabel sammenlignes de vigtigste funktioner, der er tilgængelige i Audit (Standard) og Audit (Premium). Alle overvågningsfunktioner (Standard) er inkluderet i Audit (Premium).

|Kapacitet|Overvågning (standard)|Overvågning (Premium)|
|:------|:-------------|:-------------|
|Aktiveret som standard|![Understøttes.](../media/check-mark.png)|![Understøttes.](../media/check-mark.png)|
|Tusindvis af overvågningshændelser, der kan søges i|![Understøttes.](../media/check-mark.png)|![Understøttes.](../media/check-mark.png)|
|Overvågningssøgeværktøj på overholdelsesportalen|![Understøttes.](../media/check-mark.png)|![Understøttes.](../media/check-mark.png)|
|Search-UnifiedAuditLog cmdlet|![Understøttes.](../media/check-mark.png)|![Understøttes.](../media/check-mark.png)|
|Eksportér overvågningsposter til CSV-fil|![Understøttes.](../media/check-mark.png)|![Understøttes.](../media/check-mark.png)|
|Adgang til overvågningslogge via API til administration af Office 365 <sup>1</sup>|![Understøttes.](../media/check-mark.png)|![Understøttes.](../media/check-mark.png)</sup>|
|90-dages opbevaring af overvågningslog|![Understøttes.](../media/check-mark.png)|![Understøttes.](../media/check-mark.png)|
|Opbevaring af 1 års overvågningslog||![Understøttes.](../media/check-mark.png)|
|Opbevaring af 10-års overvågningslog <sup>2</sup>||![Understøttes](../media/check-mark.png)|
|Opbevaringspolitikker for overvågningslog||![Understøttes](../media/check-mark.png)|
|Vigtige hændelser med høj værdi||![Understøttes](../media/check-mark.png)|
||||
> [!NOTE]
> <sup>1</sup> Overvågning (Premium) omfatter adgang til større båndbredde til API'en til Office 365 managementaktivitet, hvilket giver hurtigere adgang til overvågningsdata.<br/><sup>2</sup> Ud over den krævede licens til Audit (Premium) (beskrevet i næste afsnit) skal en bruger tildeles en 10-årig overvågningslogopbevaring for at bevare sine overvågningsposter i 10 år.

## <a name="licensing-requirements"></a>Licenskrav

I følgende afsnit identificeres licenskravene for Audit (Standard) og Audit (Premium). Overvågningsfunktionalitet (Standard) er inkluderet i Audit (Premium).

### <a name="audit-standard"></a>Overvågning (standard)

- Microsoft 365 Business Basic abonnement
- abonnement på Microsoft 365 Apps til virksomheder
- Microsoft 365 Enterprise E3-abonnement
- Microsoft 365 Business Premium
- Microsoft 365 Education A3-abonnement
- G3-abonnement til Microsoft 365 offentlige myndigheder
- G1-abonnement for Microsoft 365 offentlige myndigheder
- Microsoft 365 Frontline F1- eller F3-abonnement eller tilføjelsesprogrammet F5 Security
- Office 365 Enterprise E3-abonnement
- Office 365 Enterprise E1-abonnement
- Office 365 Education A1-abonnement
- Office 365 Education A3-abonnement

### <a name="audit-premium"></a>Overvågning (Premium)

- Microsoft 365 Enterprise E5-abonnement
- Microsoft 365 Enterprise E3-abonnement + tilføjelsesprogrammet Microsoft 365 E5-overholdelse
- Microsoft 365 Enterprise E3-abonnement + tilføjelsesprogrammet Microsoft 365 E5 eDiscovery og Overvågning
- Microsoft 365 Education A5-abonnement
- Microsoft 365 Education A3-abonnement + tilføjelsesprogrammet Microsoft 365 A5-overholdelse
- Microsoft 365 Education A3-abonnement + tilføjelsesprogrammet Microsoft 365 A5 eDiscovery og overvågning
- G5-abonnement Microsoft 365 offentlige myndigheder
- Microsoft 365 Government G3-abonnement + tilføjelsesprogrammet Microsoft 365 G5-overholdelse
- Microsoft 365 G3-abonnement til offentlige myndigheder + tilføjelsesprogrammet Microsoft 365 G5 eDiscovery og Audit
- Microsoft 365 Frontline F5 Compliance eller tilføjelsesprogrammet F5 Security & Compliance
- Office 365 Enterprise E5-abonnement
- Office 365 Education A5-abonnement

## <a name="set-up-microsoft-purview-auditing-solutions"></a>Konfigurer Microsoft Purview-overvågningsløsninger

Hvis du vil i gang med at bruge overvågningsløsningerne i Microsoft Purview, skal du se følgende konfigurationsvejledning.

### <a name="set-up-audit-standard"></a>Konfigurer overvågning (standard)

Det første trin er at konfigurere Overvågning (Standard) og derefter begynde at køre søgninger i overvågningsloggen.

![Arbejdsproces til konfiguration af overvågning (Standard).](../media/BasicAuditingWorkflow.png)

1. Bekræft, at din organisation har et abonnement, der understøtter Overvågning (Standard) og, hvis det er relevant, et abonnement, der understøtter Overvågning (Premium).

2. Tildel tilladelser i Exchange Online til personer i organisationen, som skal bruge søgeværktøjet til overvågningslog på overholdelsesportalen eller bruge cmdlet'en **Search-UnifiedAuditLog**. Brugerne skal specifikt tildeles rollen View-Only overvågningslogge eller overvågningslogge i Exchange Online.

3. Søg i overvågningsloggen. Når du har fuldført trin 1 og trin 2, kan brugerne i din organisation bruge søgeværktøjet til overvågningslog (eller tilsvarende cmdlet) til at søge efter overvågede aktiviteter.

Du kan finde mere detaljerede instruktioner under [Konfigurer overvågning (Standard).](set-up-basic-audit.md)

### <a name="set-up-audit-premium"></a>Konfigurer overvågning (Premium)

Hvis din organisation har et abonnement, der understøtter Overvågning (Premium), skal du udføre følgende trin for at konfigurere og bruge de yderligere funktioner i Overvågning (Premium).

![Arbejdsproces til konfiguration af overvågning (Premium).](../media/AdvancedAuditWorkflow.png)

1. Konfigurer overvågning (Premium) for brugere. Dette trin består af følgende opgaver:

   - Kontrollerer, at brugerne har fået tildelt den relevante licens eller tilføjelseslicens til Audit (Premium).
  
   - Aktivering af appen/serviceplanen Audit (Premium) skal være for disse brugere.
  
   - Aktivering af overvågning af vigtige hændelser og derefter aktivering af appen Avanceret overvågning/tjenesteplan for disse brugere.

2. Aktivér overvågningshændelser (Premium), der skal logføres, når brugerne udfører søgninger i Exchange Online og SharePoint Online.

3. Konfigurer opbevaringspolitikker for overvågningslog. Ud over standardpolitikken, der bevarer Exchange, SharePoint og Azure AD-overvågningsposter i ét år, kan du oprette yderligere politikker for opbevaring af overvågningslog for at opfylde kravene i organisationens sikkerhedshandlinger, it og overholdelsesteams.

4. Søg efter vigtige overvågningshændelser (Premium) og andre aktiviteter, når der udføres kriminaltekniske undersøgelser. Når du har fuldført trin 1 og trin 2, kan du søge i overvågningsloggen efter overvågningshændelser (Premium) og andre aktiviteter under retsmedicinske undersøgelser af kompromitterede konti og andre typer sikkerheds- eller overholdelsesundersøgelser.

[Se Konfigurer overvågning (Premium)](set-up-advanced-audit.md) for at få mere detaljerede instruktioner.

## <a name="training"></a>Uddannelse

Oplæring af dit team af sikkerhedshandlinger, it-administratorer og team af overholdelsesundersøgere i de grundlæggende funktioner i Audit (Standard) og Audit (Premium) kan hjælpe din organisation med at komme hurtigere i gang med at bruge overvågning til at hjælpe med dine undersøgelser. Microsoft 365 indeholder følgende ressource, der kan hjælpe disse brugere i din organisation med at komme i gang med overvågning: [Beskriv eDiscovery- og overvågningsegenskaberne i Microsoft 365](/learn/modules/describe-ediscovery-capabilities-of-microsoft-365).
