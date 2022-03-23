---
title: Microsoft 365 overvågningsløsninger
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
description: Få mere at vide om, hvordan du overvåge aktiviteter for brugere og administratorer i Microsoft 365 organisation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 92fb008e7fe03b4871b8838d78965c1508a20fdc
ms.sourcegitcommit: 584b4757f715a3eedf748858461c568f45137438
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/15/2022
ms.locfileid: "63592418"
---
# <a name="auditing-solutions-in-microsoft-365"></a>Revisionsløsninger i Microsoft 365

Microsoft 365 overvågningsløsninger giver en integreret løsning, der kan hjælpe organisationer med effektivt at reagere på sikkerhedshændelser, undersøge grundige undersøgelser, interne undersøgelser og overholdelsesforpligtelser. Tusindvis af bruger- og administratorhandlinger udført i masser af Microsoft 365-tjenester og -løsninger registreres, registreres og bevares i din organisations samlede overvågningslog. Revisionsposter for disse begivenheder kan søges i af sikkerhedsadministratorer, it-administratorer, insider-risikoteams og overholdelses- og juridiske enheder i din organisation. Denne funktion giver indblik i de aktiviteter, der udføres på tværs Microsoft 365 organisationen.

## <a name="microsoft-365-auditing-solutions"></a>Microsoft 365 overvågningsløsninger

Microsoft 365 indeholder to revisionsløsninger: Grundlæggende overvågning og Avanceret overvågning.

![Vigtige funktioner i Grundlæggende overvågning og Avanceret overvågning.](..\media\AuditingSolutionsComparison.png)

### <a name="basic-audit"></a>Grundlæggende overvågning

Grundlæggende overvågning giver dig mulighed for at logge og søge efter overvågede aktiviteter og styrke din viden, it, overholdelse og juridiske undersøgelser.

- **Er aktiveret som standard**. Grundlæggende overvågning er som standard slået til for alle organisationer med det relevante abonnement. Det betyder, at poster for overvågede aktiviteter registreres og kan søges i. Den eneste konfiguration, der kræves, er at tildele de nødvendige tilladelser til at få adgang til overvågningsloggens søgeværktøj (og den tilsvarende cmdlet) og sikre, at brugerens er tildelt den rette licens til avancerede overvågningsfunktioner.
- **Tusindvis af søgbare overvågningshændelser**. Du kan søge efter en lang række overvågede aktiviteter, der forekommer, som de fleste Microsoft 365 i organisationen. Hvis du vil have en delvis liste over de aktiviteter, du kan søge efter, [skal du se Overvågede aktiviteter](search-the-audit-log-in-security-and-compliance.md#audited-activities). Du kan finde en liste over de tjenester og funktioner, der understøtter overvågede aktiviteter, [under Posttypen Overvågningslog](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).
- **Overvågningssøgningsværktøjet i Microsoft 365 Overholdelsescenter**. Brug søgeværktøjet Til overvågningslogfil i Microsoft 365 Overholdelsescenter til at søge efter overvågningsposter. Du kan søge efter bestemte aktiviteter, efter aktiviteter, der er udført af bestemte brugere, og aktiviteter, der er udført med et datointerval. Her er et skærmbillede af søgeværktøjet Overvågning i Overholdelsescenter.

   ![Søgeværktøjet til overvågningslogfiler i Microsoft 365 Overholdelsescenter.](../media/AuditLogSearchToolMCC.png)

- **Search-UnifiedAuditLog cmdlet**. Du kan også bruge **Search-UnifiedAuditLog-cmdlet'en** i Exchange Online PowerShell (den underliggende cmdlet til søgeværktøjet) til at søge efter overvågningshændelser eller til at bruge i et script. Du kan finde flere oplysninger under:

  - [Reference til Search-UnifiedAuditLog-cmdlet](/powershell/module/exchange/search-unifiedauditlog)
  - [Brug et PowerShell-script til at søge i overvågningsloggen](audit-log-search-script.md)

- **Eksportere overvågningsposter til en CSV-fil**. Når du har kørt søgeværktøjet Overvågningslog i overholdelsescenteret, kan du eksportere de overvågningsposter, der returneres af søgningen, til en CSV-fil. Dette giver dig mulighed for Microsoft Excel sortere og filtrere efter forskellige egenskaber for overvågningsposten. Du kan også bruge Excel transformationsfunktionaliteten i Power-forespørgsel til at opdele hver egenskab i AuditData JSON-objektet i sin egen kolonne. Dette giver dig mulighed for effektivt at få vist og sammenligne ensartede data for forskellige begivenheder. Få mere at vide under [Eksportér, konfigurer og få vist overvågningslogposter](export-view-audit-log-records.md).

- **Adgang til overvågningslogfiler via Office 365 Management Activity API**. En tredje metode til at få adgang til og hente overvågningsposter er at bruge Office 365 Management Activity API. Det giver organisationer mulighed for at bevare overvågningsdata i længere perioder end standardtiden på 90 dage, og giver dem mulighed for at importere deres overvågningsdata til en SIEM-løsning. Du kan finde flere oplysninger [Office 365 Reference til Management Activity API](/office/office-365-management-api/office-365-management-activity-api-reference).

- **Opbevaring af overvågningslog med 90 dage**. Når en overvåget aktivitet udføres af en bruger eller administrator, genereres og gemmes en overvågningspost i overvågningsloggen for organisationen. I Grundlæggende overvågning bevares poster i 90 dage, hvilket betyder, at du kan søge efter aktiviteter, der er foretaget inden for de seneste tre måneder.

### <a name="advanced-audit"></a>Avanceret overvågning

Avanceret overvågning bygger på funktionerne i Grundlæggende overvågning ved at levere opbevaringspolitikker for overvågningslogfiler, længere opbevaring af overvågningsposter, vigtige hændelser med høj værdi og større båndbreddeadgang til Office 365 Management Activity API.

- **Opbevaringspolitikker for overvågningslogfiler**. Du kan oprette brugerdefinerede opbevaringspolitikker til overvågningslogfiler for at bevare overvågningsposter i længere perioder op til et år (og op til 10 år for brugere med påkrævet tilføjelseslicens). Du kan oprette en politik for at bevare overvågningsposter baseret på den tjeneste, hvor de overvågede aktiviteter sker, bestemte overvågede aktiviteter eller den bruger, der udfører en overvåget aktivitet.

- **Længere opbevaring af overvågningsposter**. Exchange, SharePoint og Azure Active Directory-revisionsposter bevares som standard i ét år. Overvågningsposter for alle andre aktiviteter bevares som standard i 90 dage, eller du kan bruge opbevaringspolitikker for overvågningslogfiler til at konfigurere længere opbevaringsperioder.

- **Vigtige avancerede overvågningshændelser med høj værdi**. Overvågningsposter for vigtige begivenheder kan hjælpe organisationen med at undersøge og undersøge overholdelse ved at synliggøre hændelser som f.eks. hvornår mailelementer blev åbnet, hvornår mailelementer blev besvaret og videresendt, eller hvornår og hvad en bruger søgte efter i Exchange Online og SharePoint Online. Disse vigtige begivenheder kan hjælpe dig med at undersøge eventuelle overtrædelser og fastlægge omfanget af forlig.

- **Højere båndbredde til Office 365 Management Activity API**. Avanceret overvågning giver organisationer mere båndbredde til at få adgang til overvågningslogfiler via Office 365 Management Activity API. Selvom alle organisationer (der har Grundlæggende overvågning eller Avanceret overvågning) indledningsvist får tildelt en oprindelig plan på 2.000 anmodninger i minuttet, øges denne grænse dynamisk afhængigt af en organisations antal sæder og deres licenseringsabonnement. Dette resulterer i, at organisationer med Avanceret overvågning får ca. dobbelt så meget båndbredde som organisationer med Grundlæggende overvågning.

Hvis du vil have mere at vide om avancerede overvågningsfunktioner, [skal du se Avanceret overvågning Microsoft 365](advanced-audit.md).

## <a name="comparison-of-key-capabilities"></a>Sammenligning af vigtige funktioner

Følgende tabel sammenligner de vigtigste funktioner, der er tilgængelige i Grundlæggende overvågning og Avanceret overvågning. Alle grundlæggende overvågningsfunktioner er inkluderet i Avanceret overvågning.

|Funktion|Grundlæggende overvågning|Avanceret overvågning|
|:------|:-------------|:-------------|
|Aktiveret som standard|![Understøttet.](../media/check-mark.png)|![Understøttet.](../media/check-mark.png)|
|Tusindvis af søgbare overvågningshændelser|![Understøttet.](../media/check-mark.png)|![Understøttet.](../media/check-mark.png)|
|Overvågningssøgningsværktøjet i Microsoft 365 Overholdelsescenter|![Understøttet.](../media/check-mark.png)|![Understøttet.](../media/check-mark.png)|
|Search-UnifiedAuditLog cmdlet|![Understøttet.](../media/check-mark.png)|![Understøttet.](../media/check-mark.png)|
|Eksportere overvågningsposter til CSV-fil|![Understøttet.](../media/check-mark.png)|![Understøttet.](../media/check-mark.png)|
|Adgang til overvågningslogfiler via Office 365 Management Activity API <sup>1</sup>|![Understøttet.](../media/check-mark.png)|![Understøttet.](../media/check-mark.png)</sup>|
|90-dages opbevaring af overvågningslog|![Understøttet.](../media/check-mark.png)|![Understøttet.](../media/check-mark.png)|
|Opbevaring af 1 års overvågningslog||![Understøttet.](../media/check-mark.png)|
|Opbevaringslog over 10 år for <sup>overvågningsloggen 2</sup>||![Understøttet](../media/check-mark.png)|
|Opbevaringspolitikker for overvågningslogfiler||![Understøttet](../media/check-mark.png)|
|Vigtige begivenheder af høj værdi||![Understøttet](../media/check-mark.png)|
||||
> [!NOTE]
> <sup>1</sup> Avanceret overvågning omfatter højere båndbreddeadgang til Office 365 Management Activity API, som giver hurtigere adgang til overvågningsdata.<br/><sup>2</sup> Ud over de påkrævede licenser til Avanceret overvågning (beskrevet i næste afsnit) skal en bruger have tildelt en 10-års opbevaringslog for at bevare sine overvågningsposter i ti år.

## <a name="licensing-requirements"></a>Licenskrav

I de følgende afsnit kan du se licenskravene til Grundlæggende overvågning og Avanceret overvågning. Grundlæggende overvågningsfunktionalitet er inkluderet i Avanceret overvågning.

### <a name="basic-audit"></a>Grundlæggende overvågning

- Microsoft 365 Business Basic-abonnement
- Microsoft 365 Apps for Business-abonnement
- Microsoft 365 Enterprise E3-abonnement
- Microsoft 365 Business Premium
- Microsoft 365 Education A3-abonnement
- Microsoft 365 Government G3-abonnement
- Microsoft 365 Government G1-abonnement
- Microsoft 365 frontline F1- eller F3-abonnement eller tilføjelsesprogrammet F5 Security
- Office 365 Enterprise E3-abonnement
- Office 365 Enterprise E1-abonnement
- Office 365 Education A1-abonnement
- Office 365 Education A3-abonnement

### <a name="advanced-audit"></a>Avanceret overvågning

- Microsoft 365 Enterprise E5-abonnement
- Microsoft 365 Enterprise E3-abonnement + Microsoft 365 E5 Overholdelse-tilføjelsesprogrammet
- Microsoft 365 Enterprise E3-abonnement + Microsoft 365 E5 tilføjelsesprogrammet eDiscovery og Revision
- Microsoft 365 Education A5-abonnement
- Microsoft 365 Education A3-abonnement + Microsoft 365 A5 tilføjelsesprogrammet Overholdelse af regler og standarder
- Microsoft 365 Education A3-abonnement + Microsoft 365 A5 tilføjelsesprogrammet eDiscovery og Overvågning
- Microsoft 365 Government G5-abonnement
- Microsoft 365 Government G3-abonnement + Microsoft 365 G5 Compliance-tilføjelsesprogrammet
- Microsoft 365 Government G3-abonnement + Microsoft 365 G5 eDiscovery og Audit-tilføjelsesprogrammet
- Microsoft 365 Frontline F5 Compliance eller tilføjelsesprogrammet & Overholdelse af regler og standarder
- Office 365 Enterprise E5-abonnement
- Office 365 Education A5-abonnement

## <a name="set-up-microsoft-365-auditing-solutions"></a>Konfigurere Microsoft 365 overvågningsløsninger

For at komme i gang med at bruge overvågningsløsninger Microsoft 365 skal du se følgende installationsvejledning.

### <a name="set-up-basic-audit"></a>Konfigurere grundlæggende overvågning

Det første trin er at konfigurere Grundlæggende overvågning og derefter starte søgning i overvågningsloggen.

![Arbejdsproces til at konfigurere Grundlæggende overvågning.](../media/BasicAuditingWorkflow.png)

1. Kontrollér, at din organisation har et abonnement, der understøtter Grundlæggende overvågning og, hvis det er relevant, et abonnement, der understøtter Avanceret overvågning.

2. Tildel tilladelser i Exchange Online til personer i organisationen, der skal bruge overvågningsloggens søgeværktøj i Microsoft 365 Overholdelsescenter eller bruge cmdlet'en **Search-UnifiedAuditLog**. Brugerne skal specifikt have tildelt rollen View-Only overvågningslogfiler eller overvågningslogfiler i Exchange Online.

3. Søg i overvågningsloggen. Når du har fuldført trin 1 og 2, kan brugerne i organisationen bruge søgeværktøjet til overvågningslogfiler (eller en tilsvarende cmdlet) til at søge efter overvågede aktiviteter.

Du kan finde en mere detaljeret vejledning [under Konfigurere grundlæggende overvågning](set-up-basic-audit.md).

### <a name="set-up-advanced-audit"></a>Konfigurere Avanceret overvågning

Hvis din organisation har et abonnement, der understøtter Avanceret overvågning, skal du udføre følgende trin for at konfigurere og bruge de ekstra funktioner i Avanceret overvågning.

![Arbejdsproces til at konfigurere Avanceret overvågning.](../media/AdvancedAuditWorkflow.png)

1. Konfigurer Avanceret overvågning for brugere. Dette trin består af følgende opgaver:

   - Bekræftelse af, at brugere er tildelt den relevante licens eller tilføjelseslicens til Avanceret overvågning.
  
   - Aktivering af avanceret overvågning-app/serviceabonnement skal være for disse brugere.
  
   - Aktivering af overvågning af vigtige hændelser og aktivering af Advanced Auditing-appen/serviceplanen for disse brugere.

2. Aktivér Avancerede overvågningshændelser, der logføres, når brugere udfører søgninger i Exchange Online og SharePoint Online.

3. Konfigurer opbevaringspolitikker for overvågningslogfiler. Ud over standardpolitikken, der bevarer Exchange-, SharePoint- og Azure AD-overvågningsposter i et år, kan du oprette yderligere politikker for opbevaring af overvågningslogfiler, der opfylder kravene til organisationens sikkerhedshandlinger, IT og overholdelsesteams.

4. Søg efter vigtige Avancerede overvågningshændelser og andre aktiviteter, når du foretager undersøgelser, der undersøges. Når du har fuldført trin 1 og 2, kan du søge i overvågningsloggen efter Avancerede overvågningshændelser og andre aktiviteter under undersøgelse af kompromitterede konti og andre typer af sikkerheds- eller overholdelsesundersøgelse.

Du kan finde en mere detaljeret vejledning [under Konfigurere Avanceret overvågning](set-up-advanced-audit.md).

## <a name="training"></a>Kurser

Undervis dit sikkerhedsteam, it-administratorer og overholdelsesteamet i det grundlæggende for Grundlæggende overvågning og Avanceret overvågning for at hjælpe organisationen med at komme hurtigere i gang med at bruge overvågning som en hjælp til dine undersøgelser. Microsoft 365 indeholder følgende ressource, der kan hjælpe disse brugere i organisationen med at komme i gang med overvågning: Beskriv [eDiscovery- og overvågningsegenskaber for Microsoft 365](/learn/modules/describe-ediscovery-capabilities-of-microsoft-365).
