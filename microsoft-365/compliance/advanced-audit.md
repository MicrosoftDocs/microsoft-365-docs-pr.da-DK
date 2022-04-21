---
title: Microsoft Purview Audit (Premium)
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
- M365-security-compliance
- SPO_Content
- m365solution-audit
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft Purview Audit (Premium) indeholder nye overvågningsfunktioner, der kan hjælpe din organisation med tekniske undersøgelser og undersøgelser af overholdelse af angivne standarder.
ms.openlocfilehash: 4f936977c71a933dd05e5c0b2e0d2111b03bc8f7
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64999492"
---
# <a name="microsoft-purview-audit-premium"></a>Microsoft Purview Audit (Premium)

> [!TIP]
> *Vidste du, at du kan prøve premiumversionerne af alle ni Microsoft Purview-løsninger gratis?* Brug den 90-dages prøveversion af Purview-løsninger til at udforske, hvordan robuste Purview-funktioner kan hjælpe din organisation med at opfylde sine behov for overholdelse af angivne standarder. Microsoft 365 E3- og Office 365 E3-kunder kan starte nu ved [hjælp af prøveversionshubben for Microsoft Purview-overholdelsesportalen](https://compliance.microsoft.com/trialHorizontalHub?sku=ComplianceE5&ref=DocsRef). Få mere at vide om [, hvem der kan tilmelde sig og prøvevilkår](compliance-easy-trials.md).

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

[Overvågningsfunktionen](search-the-audit-log-in-security-and-compliance.md) i Microsoft Purview giver organisationer indblik i mange typer overvågede aktiviteter på tværs af mange forskellige tjenester i Microsoft 365. Microsoft Purview Audit (Premium) hjælper organisationer med at udføre tekniske undersøgelser og undersøgelser af overholdelse af angivne standarder ved at øge den opbevaring af overvågningsloggen, der kræves for at foretage en undersøgelse, give adgang til vigtige hændelser (ved hjælp af søgning i overvågningslog på Microsoft Purview-overholdelsesportalen og API'en til Office 365 managementaktivitet), der hjælper med at bestemme omfanget af kompromiser og hurtigere adgang til api'en til administration af Office 365.

> [!NOTE]
> Overvågning (Premium) er tilgængelig for organisationer med et Office 365 E5/A5/G5- eller Microsoft 365 Enterprise E5/A5/G5-abonnement. En Microsoft 365 E5/A5/G5 Compliance eller E5/A5/G5 eDiscovery- og Audit-tilføjelsesprogramlicens skal tildeles til brugere for auditfunktioner (Premium), f.eks. langsigtet opbevaring af overvågningslogge og generering af overvågningshændelser (Premium) til undersøgelser. Du kan få flere oplysninger om licenser under:<br/>- [Overvågningskrav (Premium)](auditing-solutions-overview.md#licensing-requirements)<br/>- [Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#advanced-audit).

Denne artikel indeholder en oversigt over overvågningsfunktioner (Premium) og viser, hvordan du konfigurerer brugere til Overvågning (Premium).

## <a name="long-term-retention-of-audit-logs"></a>Langsigtet opbevaring af overvågningslogge

Overvågning (Premium) bevarer alle Exchange, SharePoint og Azure Active Directory-overvågningsposter i ét år. Dette opnås ved hjælp af en standard opbevaringspolitik for overvågningsloggen, der bevarer alle overvågningsposter, der indeholder værdien af **Exchange**, **SharePoint** eller **AzureActiveDirectory** for egenskaben **Workload** (som angiver den tjeneste, hvor aktiviteten fandt sted) i et år. Opbevaring af overvågningsposter i længere perioder kan hjælpe med igangværende kriminaltekniske undersøgelser eller undersøgelser af overholdelse af angivne standarder. Du kan få flere oplysninger i afsnittet "Standard opbevaringspolitik for overvågningslog" under [Administrer opbevaringspolitikker for overvågningslog](audit-log-retention-policies.md#default-audit-log-retention-policy).

Ud over de etårige opbevaringsfunktioner i Audit (Premium) har vi også frigivet muligheden for at bevare overvågningslogge i 10 år. Den 10-årige opbevaring af overvågningslogge hjælper med at understøtte langvarige undersøgelser og reagere på lovmæssige, juridiske og interne forpligtelser.

> [!NOTE]
> Hvis du bevarer overvågningslogge i 10 år, kræver det en ekstra licens pr. bruger-tilføjelsesprogram. Når denne licens er tildelt til en bruger, og der er angivet en passende 10-års opbevaringspolitik for overvågningsloggen for den pågældende bruger, vil overvågningslogge, der er omfattet af denne politik, blive opbevaret i 10-års perioden. Denne politik har ikke tilbagevirkende kraft og kan ikke bevare overvågningslogge, der blev genereret, før politikken for opbevaring af overvågningslogge på 10 år blev oprettet. Du kan få flere oplysninger i afsnittet [Ofte stillede spørgsmål om overvågning (Premium)](#faqs-for-audit-premium) i denne artikel.

### <a name="audit-log-retention-policies"></a>Opbevaringspolitikker for overvågningslog

Alle overvågningsposter, der genereres i andre tjenester, som ikke er omfattet af standard opbevaringspolitikken for overvågningslog (beskrevet i det forrige afsnit), bevares i 90 dage. Men du kan oprette brugerdefinerede politikker for opbevaring af overvågningslog for at bevare andre overvågningsposter i længere tid op til 10 år. Du kan oprette en politik for at bevare overvågningsposter baseret på et eller flere af følgende kriterier:

- Den Microsoft 365 tjeneste, hvor de overvågede aktiviteter finder sted.

- Specifikke overvågede aktiviteter.

- Den bruger, der udfører en overvåget aktivitet.

Du kan også angive, hvor længe overvågningsposter, der stemmer overens med politikken og et prioritetsniveau, skal bevares, så bestemte politikker får prioritet i forhold til andre politikker. Bemærk også, at enhver brugerdefineret opbevaringspolitik for overvågningslog har forrang frem for standard opbevaringspolitikken for overvågning, hvis du har brug for at bevare Exchange, SharePoint eller Azure Active Directory-overvågningsposter i mindre end et år (eller i 10 år) for nogle eller alle brugere i din organisation. Du kan få flere oplysninger under [Administrer opbevaringspolitikker for overvågningslog](audit-log-retention-policies.md).

## <a name="audit-premium-events"></a>Overvågningshændelser (Premium)

Overvågning (Premium) hjælper organisationer med at udføre tekniske undersøgelser og undersøgelser af overholdelse af angivne standarder ved at give adgang til vigtige hændelser, f.eks. hvornår der blev åbnet mailelementer, hvornår og hvornår og hvad en bruger søgte efter i Exchange Online og SharePoint Online. Disse hændelser kan hjælpe dig med at undersøge mulige brud og fastlægge omfanget af kompromiser. Ud over disse hændelser i Exchange og SharePoint er der hændelser i andre Microsoft 365 tjenester, der betragtes som vigtige hændelser, og som kræver, at brugerne tildeles den [relevante Licens til Overvågning (Premium).](auditing-solutions-overview.md#licensing-requirements) Brugerne skal have tildelt en overvågningslicens (Premium), så der genereres overvågningslogge, når brugerne udfører disse hændelser.

Overvågning (Premium) indeholder følgende hændelser:

- [MailItemsAccessed](#mailitemsaccessed)

- [Send](#send)

- [SearchQueryInitiatedExchange](#searchqueryinitiatedexchange)

- [SearchQueryInitiatedSharePoint](#searchqueryinitiatedsharepoint)

- [Andre overvågningshændelser (Premium) i Microsoft 365](#other-audit-premium-events-in-microsoft-365)

### <a name="mailitemsaccessed"></a>MailItemsAccessed

Hændelsen MailItemsAccessed er en overvågningshandling for postkassen og udløses, når maildata tilgås af mailprotokoller og mailklienter. Denne hændelse kan hjælpe efterforskere med at identificere brud på datasikkerheden og fastlægge omfanget af meddelelser, der kan være blevet kompromitteret. Hvis en hacker fik adgang til mails, udløses handlingen MailItemsAccessed, selvom der ikke er noget eksplicit signal om, at meddelelser faktisk blev læst (med andre ord registreres adgangstypen, f.eks. en binding eller synkronisering i overvågningsposten).

Hændelsen MailItemsAccessed erstatter MessageBind i logføring af overvågning af postkasser i Exchange Online og indeholder disse forbedringer:

- MessageBind kunne kun konfigureres for Logontypen AuditAdmin-bruger. Den blev ikke anvendt på stedfortræder- eller ejerhandlinger. MailItemsAccessed gælder for alle logontyper.

- MessageBind dækkede kun adgang af en mailklient. Det gælder ikke for synkroniseringsaktiviteter. MailItemsAccessed-hændelser udløses af både bindings- og synkroniseringsadgangstyper.

- MessageBind-handlinger udløser oprettelse af flere overvågningsposter, når den samme mail blev åbnet, hvilket resulterede i overvågning af "støj". I modsætning hertil samles MailItemsAccessed-hændelser i færre overvågningsposter.

Du kan få oplysninger om overvågningsposter for MailItemsAccessed-aktiviteter under [Brug overvågning (Premium) til at undersøge kompromitterede konti](mailitemsaccessed-forensics-investigations.md).

Hvis du vil søge efter MailItemsAccessed-overvågningsposter, kan du søge efter aktiviteten **Tilgåede postkasseelementer** på rullelisten **Exchange postkasseaktiviteter** i [søgeværktøjet til overvågningsloggen](search-the-audit-log-in-security-and-compliance.md) på overholdelsesportalen.

![Søger efter MailItemsAccessed-handlinger i søgeværktøjet til overvågningslog.](../media/AdvAudit_MailItemsAccessed.png)

Du kan også køre kommandoerne [Search-UnifiedAuditLog -Operations MailItemsAccessed](/powershell/module/exchange/search-unifiedauditlog) eller [Search-MailboxAuditLog -Operations MailItemsAccessed](/powershell/module/exchange/search-mailboxauditlog) i Exchange Online PowerShell.

### <a name="send"></a>Send

Hændelsen Send er også en overvågningshandling for en postkasse og udløses, når en bruger udfører en af følgende handlinger:

- Sender en mail

- Svarer på en mail

- Videresender en mail

Efterforskere kan bruge Hændelsen Send til at identificere mails, der er sendt fra en kompromitteret konto. Overvågningsposten for en Send-hændelse indeholder oplysninger om meddelelsen, f.eks. hvornår meddelelsen blev sendt, InternetMessage-id, emnelinjen, og om meddelelsen indeholdt vedhæftede filer. Disse overvågningsoplysninger kan hjælpe efterforskere med at identificere oplysninger om mails, der er sendt fra en kompromitteret konto eller sendt af en hacker. Efterforskere kan desuden bruge et Microsoft 365 eDiscovery-værktøj til at søge efter meddelelsen (ved hjælp af emnelinjen eller meddelelses-id' et) til at identificere de modtagere, meddelelsen blev sendt til, og det faktiske indhold i den sendte meddelelse.

Hvis du vil søge efter Send overvågningsposter, kan du søge efter aktiviteten **Sendt meddelelse** på rullelisten **Exchange postkasseaktiviteter** i [søgeværktøjet til overvågningsloggen](search-the-audit-log-in-security-and-compliance.md) på overholdelsesportalen.

![Søger efter handlinger for sendte meddelelser i søgeværktøjet til overvågningsloggen.](../media/AdvAudit_SentMessage.png)

Du kan også køre kommandoerne [Search-UnifiedAuditLog -Operations Send](/powershell/module/exchange/search-unifiedauditlog) eller [Search-MailboxAuditLog -Operations Send](/powershell/module/exchange/search-mailboxauditlog) i Exchange Online PowerShell.

### <a name="searchqueryinitiatedexchange"></a>SearchQueryInitiatedExchange

Hændelsen SearchQueryInitiatedExchange udløses, når en person bruger Outlook til at søge efter elementer i en postkasse. Hændelser udløses, når der udføres søgninger i følgende Outlook miljøer:

- Outlook (desktopklient)

- Outlook på internettet (OWA)

- Outlook til iOS

- Outlook til Android

- Mailapp til Windows 10

Efterforskere kan bruge hændelsen SearchQueryInitiatedExchange til at afgøre, om en hacker, der kan have kompromitteret en konto, har søgt efter eller forsøgt at få adgang til følsomme oplysninger i postkassen. Overvågningsposten for hændelsen SearchQueryInitiatedExchange indeholder oplysninger som f.eks. den faktiske tekst i søgeforespørgslen. Overvågningsposten angiver også det Outlook miljø, som søgningen blev udført i. Ved at se på de søgeforespørgsler, som en hacker kan have udført, kan en efterforsker bedre forstå hensigten med de maildata, der blev søgt efter.

Hvis du vil søge efter SearchQueryInitiatedExchange-overvågningsposter, kan du søge efter søgeaktiviteten **Udført mail** på rullelisten **Søg efter aktiviteter** i [søgeværktøjet til overvågningslog](search-the-audit-log-in-security-and-compliance.md) i overholdelsescenter.

![Søger efter udførte mailsøgningshandlinger i søgeværktøjet til overvågningslog.](../media/AdvAudit_SearchExchange.png)

Du kan også køre [Search-UnifiedAuditLog -Operations SearchQueryInitiatedExchange](/powershell/module/exchange/search-unifiedauditlog) i Exchange Online PowerShell.

> [!NOTE]
> Du skal aktivere SearchQueryInitiatedExchange for at blive logført, så du kan søge efter denne hændelse i overvågningsloggen. Du kan finde instruktioner under [Konfigurer overvågning (Premium)](set-up-advanced-audit.md#step-2-enable-audit-premium-events).

### <a name="searchqueryinitiatedsharepoint"></a>SearchQueryInitiatedSharePoint

På samme måde som med søgning efter postkasseelementer udløses hændelsen SearchQueryInitiatedSharePoint, når en person søger efter elementer i SharePoint. Hændelser udløses, når der udføres søgninger på rod- eller standardsiden for følgende typer SharePoint websteder:

- Websteder til startsider

- Kommunikationswebsteder

- Hubwebsteder

- Websteder, der er knyttet til Microsoft Teams

Efterforskere kan bruge hændelsen SearchQueryInitiatedSharePoint til at afgøre, om en hacker forsøgte at finde (og muligvis tilgået) følsomme oplysninger i SharePoint. Overvågningsposten for en SearchQueryInitiatedSharePoint-hændelse indeholder også den faktiske tekst i søgeforespørgslen. Overvågningsposten angiver også den type SharePoint websted, der blev søgt efter. Ved at se på de søgeforespørgsler, som en hacker kan have udført, kan en efterforsker bedre forstå formålet med og omfanget af de fildata, der søges efter.

Hvis du vil søge efter SearchQueryInitiatedSharePoint-overvågningsposter, kan du søge efter **den udførte SharePoint søgeaktivitet** på rullelisten **Søgeaktiviteter** i [søgeværktøjet til overvågningslog](search-the-audit-log-in-security-and-compliance.md) i overholdelsescenter.

![Søger efter Udført SharePoint søgehandlinger i søgeværktøjet til overvågningslog.](../media/AdvAudit_SearchSharePoint.png)

Du kan også køre [Search-UnifiedAuditLog -Operations SearchQueryInitiatedSharePoint](/powershell/module/exchange/search-unifiedauditlog) i Exchange Online PowerShell.

> [!NOTE]
> Du skal aktivere SearchQueryInitiatedSharePoint for at blive logført, så du kan søge efter denne hændelse i overvågningsloggen. Du kan finde instruktioner under [Konfigurer overvågning (Premium)](set-up-advanced-audit.md#step-2-enable-audit-premium-events).

### <a name="other-audit-premium-events-in-microsoft-365"></a>Andre overvågningshændelser (Premium) i Microsoft 365

Ud over hændelserne i Exchange Online og SharePoint Online er der hændelser i andre Microsoft 365 tjenester, der logføres, når brugerne tildeles den relevante Premium-licens. Følgende Microsoft 365 tjenester leverer overvågningshændelser (Premium). Vælg det tilsvarende link for at gå til en artikel, der identificerer og beskriver disse hændelser.

- [Microsoft Forms](search-the-audit-log-in-security-and-compliance.md#microsoft-forms-activities)

- [Microsoft Stream](/stream/audit-logs#actions-logged-in-stream)

- [Microsoft Teams](/microsoftteams/audit-log-events#teams-activities)

- [Yammer](search-the-audit-log-in-security-and-compliance.md#yammer-activities)

## <a name="high-bandwidth-access-to-the-office-365-management-activity-api"></a>Adgang med høj båndbredde til API'en til administration af Office 365

Organisationer, der får adgang til overvågningslogge via API'en til administration af Office 365, blev begrænset af begrænsninger på udgiverniveau. Det betyder, at for en udgiver, der henter data på vegne af flere kunder, blev grænsen delt af alle disse kunder.

Med udgivelsen af Audit (Premium) flytter vi fra en grænse på udgiverniveau til en grænse på lejerniveau. Resultatet er, at hver organisation får deres egen fuldt allokerede båndbreddekvote for at få adgang til deres overvågningsdata. Båndbredden er ikke en statisk, foruddefineret grænse, men er baseret på en kombination af faktorer, herunder antallet af pladser i organisationen, og at E5/A5/G5-organisationer får mere båndbredde end ikke-E5/A5/G5-organisationer.

Alle organisationer tildeles oprindeligt en oprindelig plan på 2.000 anmodninger pr. minut. Denne grænse øges dynamisk afhængigt af en organisations antal pladser og deres licensabonnement. E5/A5/G5-organisationer får cirka dobbelt så meget båndbredde som ikke-E5/A5/G5-organisationer. Der vil også være et loft på den maksimale båndbredde for at beskytte tjenestens tilstand.

Du kan få flere oplysninger i afsnittet "API-begrænsning" i [Office 365 API-reference til administrationsaktivitet](/office/office-365-management-api/office-365-management-activity-api-reference#api-throttling).

## <a name="faqs-for-audit-premium"></a>Ofte stillede spørgsmål om overvågning (Premium)

**Har alle brugere brug for en E5/A5/G5-licens for at kunne drage fordel af Audit (Premium)?**

En bruger skal tildeles en E5/A5/G5-licens for at kunne drage fordel af overvågningsfunktioner på brugerniveau (Premium). Der er nogle funktioner, der kontrollerer, om der er den relevante licens til at vise funktionen for brugeren. Hvis du f.eks. forsøger at bevare overvågningsposterne for en bruger, der ikke har fået tildelt den relevante licens i mere end 90 dage, returnerer systemet en fejlmeddelelse.

**Min organisation har et E5/A5/G5-abonnement. Skal jeg gøre noget for at få adgang til overvågningsposter for overvågningshændelser (Premium)?.**

For berettigede kunder og brugere, der er tildelt den relevante E5/A5/G5-licens, er der ingen handling, der er nødvendig for at få adgang til Overvågningshændelser (Premium) med undtagelse af aktivering af SearchQueryInitiatedExchange- og SearchQueryInitiatedSharePoint-hændelserne (som tidligere beskrevet i denne artikel). Overvågningshændelser (Premium) genereres kun for brugere med E5/A5/G5-licenser, når disse licenser er blevet tildelt.

**Er de nye hændelser i Overvågning (Premium) tilgængelige i API'en til Office 365-administrationsaktivitet?**

Ja. Så længe der genereres overvågningsposter for brugere med den relevante licens, kan du få adgang til disse poster via API'en til administration af Office 365.

**Hvad sker der med min organisations overvågningslogdata, hvis jeg opretter en opbevaringspolitik for overvågningslog for 10 år, når funktionen blev offentligt tilgængelig, men før den påkrævede licens til tilføjelsesprogrammet blev gjort tilgængelig?**

Alle overvågningslogdata, der er omfattet af en 10-årig opbevaringspolitik for overvågningslog, som du oprettede, efter at funktionen blev frigivet til offentlig tilgængelighed i det sidste kvartal af 2020, bevares i 10 år. Dette omfatter 10-års politikker for opbevaring af overvågningslog, der blev oprettet, før den påkrævede licens til tilføjelsesprogrammet blev frigivet til køb i marts 2021. Men da licensen til tilføjelse til opbevaring af overvågningslog for 10 år nu er tilgængelig, skal du købe og tildele disse tilføjelseslicenser til alle brugere, hvis overvågningsdata er omfattet af en 10-årig politik for opbevaring af overvågning.
