---
title: Avanceret overvågning i Microsoft 365
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
description: Avanceret overvågning i Microsoft 365 indeholder nye overvågningsfunktioner, der kan hjælpe din organisation med at undersøge og overholde regler og standarder.
ms.openlocfilehash: 4a378071a59d2462cff1af5b87f9ab99d1e1337f
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63587342"
---
# <a name="advanced-audit-in-microsoft-365"></a>Avanceret overvågning i Microsoft 365

Funktionen [Overvågning i](search-the-audit-log-in-security-and-compliance.md) Microsoft 365 giver organisationer indblik i mange typer overvågede aktiviteter på tværs af mange forskellige tjenester Microsoft 365. Avanceret overvågning hjælper organisationer med at foretage undersøgelser af omfang og overholdelse ved at øge opbevaringen af overvågningslogfiler, der kræves for at udføre en undersøgelse, hvilket giver adgang til vigtige begivenheder (ved hjælp af søgning i overvågningsloggen i Microsoft 365 Overholdelsescenter og Office 365 Management Activity API), som hjælper med at fastlægge omfanget af kompromis og hurtigere adgang til Office 365 Api til aktivitetsstyring.

> [!NOTE]
> Avanceret overvågning er tilgængelig for organisationer med et Office 365 E5/A5/G5 eller Microsoft 365 Enterprise E5/A5/G5-abonnement. En Microsoft 365 E5/A5/G5-overholdelses- eller E5/A5/G5 eDiscovery- og overvågning-tilføjelseslicens bør tildeles til brugere med avancerede overvågningsfunktioner, f.eks. langsigtet opbevaring af overvågningslogfiler og generationen af avancerede overvågningshændelser til undersøgelser. Du kan finde flere oplysninger om licenser i:<br/>- [Avancerede krav til overvågningslicenser](auditing-solutions-overview.md#licensing-requirements)<br/>- [Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#advanced-audit).

Denne artikel indeholder en oversigt over avancerede overvågningsfunktioner og viser, hvordan du konfigurerer brugere til Avanceret overvågning.

## <a name="long-term-retention-of-audit-logs"></a>Langsigtet opbevaring af overvågningslogfiler

Avanceret overvågning bevarer alle Exchange-, SharePoint- Azure Active Directory-overvågningsposter i et år. Dette opnås med en standardopbevaringspolitik for overvågningsloggen, der bevarer en overvågningspost, der indeholder værdien af **Exchange**, **SharePoint** eller **AzureActiveDirectory** for egenskaben **Arbejdsbyrde** (som angiver den tjeneste, hvor aktiviteten forekom) for et år. Bevarelse af overvågningsposter i længere perioder kan hjælpe med igangværende undersøgelser eller undersøgelser af overholdelse af regler og standarder. Du kan finde flere oplysninger i afsnittet "Standardopbevaringspolitik for overvågningslog" i Administrere opbevaringspolitikker [for overvågningslogfiler](audit-log-retention-policies.md#default-audit-log-retention-policy).

Ud over de etårige opbevaringsfunktioner fra Avanceret overvågning har vi også udgivet muligheden for at bevare overvågningslogfiler i 10 år. Den 10-års opbevaring af overvågningslogfiler hjælper med at understøtte længere igangværende undersøgelser og reagere på lovgivningsmæssige, juridiske og interne forpligtelser.

> [!NOTE]
> Bevarelse af overvågningslogfiler i 10 år kræver en ekstra licens til tilføjelsesprogrammet pr. bruger. Når denne licens er tildelt en bruger, og en passende 10-års opbevaringspolitik for overvågningsloggen er angivet for den pågældende bruger, vil overvågningslogfiler, der er dækket af denne politik, begynde at blive bevaret i den 10-års periode. Denne politik har ikke tilbagevirkende kraft og kan ikke bevare overvågningslogger, der blev oprettet, før opbevaringspolitikken for den 10-års overvågningslog blev oprettet. Du kan finde flere oplysninger i [afsnittet Ofte stillede spørgsmål om avanceret](#faqs-for-advanced-audit) overvågning i denne artikel.

### <a name="audit-log-retention-policies"></a>Opbevaringspolitikker for overvågningslogfiler

Alle overvågningsposter, der er oprettet i andre tjenester, som ikke er dækket af standardopbevaringspolitikken for overvågningslogfiler (beskrevet i forrige afsnit), bevares i 90 dage. Men du kan oprette brugerdefinerede opbevaringspolitikker for overvågningslogfiler for at bevare andre overvågningsposter i længere perioder op til 10 år. Du kan oprette en politik for at bevare overvågningsposter baseret på et eller flere af følgende kriterier:

- Den Microsoft 365 tjeneste, hvor de overvågede aktiviteter udføres.

- Bestemte overvågede aktiviteter.

- Den bruger, der udfører en overvåget aktivitet.

Du kan også angive, hvor lang tid overvågningsposter, der svarer til politikken og et prioritetsniveau, så bestemte politikker prioriteres højere end andre politikker. Bemærk også, at en brugerdefineret opbevaringspolitik for overvågningsloggen tilsidesætter standardopbevaringspolitikken for overvågning, i tilfælde af at du har brug for at bevare Exchange-, SharePoint- eller Azure Active Directory-overvågningsposter i mindre end et år (eller i 10 år) for nogle eller alle brugere i organisationen. Du kan få mere at vide under [Administrere opbevaringspolitikker for overvågningslogfiler](audit-log-retention-policies.md).

## <a name="advanced-audit-events"></a>Avancerede overvågningshændelser

Avanceret overvågning hjælper organisationer med at foretage besvarelser og undersøgelser af overholdelse ved at give adgang til vigtige begivenheder, f.eks. hvornår mailelementer blev åbnet, hvornår mailelementer blev besvaret og videresendt, og hvornår og hvad en bruger søgte efter i Exchange Online og SharePoint Online. Disse hændelser kan hjælpe dig med at undersøge eventuelle overtrædelser og fastlægge omfanget af forlig. Ud over disse hændelser i Exchange og SharePoint, er der begivenheder i andre Microsoft 365-tjenester, der betragtes som vigtige begivenheder og kræver, at brugerne tildeles den relevante licens til [Avanceret overvågning](auditing-solutions-overview.md#licensing-requirements). Brugere skal have tildelt en avanceret overvågningslicens, så der genereres overvågningslogfiler, når brugerne udfører disse hændelser.

Avanceret overvågning indeholder følgende hændelser:

- [MailItemsAccessed](#mailitemsaccessed)

- [Send](#send)

- [SearchQueryInitiatedExchange](#searchqueryinitiatedexchange)

- [SearchQueryInitiatedSharePoint](#searchqueryinitiatedsharepoint)

- [Andre avancerede overvågningshændelser i Microsoft 365](#other-advanced-audit-events-in-microsoft-365)

### <a name="mailitemsaccessed"></a>MailItemsAccessed

Hændelsen MailItemsAccessed er en overvågningshandling for postkassen og udløses, når maildata tilgås af mailprotokoller og mailklienter. Denne hændelse kan hjælpe registrerede databribrider og fastlægge omfanget af meddelelser, der kan være blevet kompromitteret. Hvis en hacker har fået adgang til mails, udløses den MailItemsAccessed-handling, selvom der ikke er noget eksplicit signal om, at meddelelser faktisk blev læst (med andre ord, at typen af adgang som f.eks. en indbinding eller synkronisering registreres i overvågningsposten).

Hændelsen MailItemsAccessed erstatter MessageBind i logføring af postkasserevision i Exchange Online og leverer disse forbedringer:

- MessageBind kunne kun konfigureres for AuditAdmin-brugerlogontypen. den gælder ikke for handlinger som stedfortræder eller ejer. MailItemsAccessed gælder for alle logontyper.

- MessageBind omfattede kun adgang fra en mailklient. Den gælder ikke for synkroniseringsaktiviteter. MailItemsAccessed-hændelser udløses af både adgangstyperne indbinding og synkronisering.

- Handlingerne Meddelelsesbind udløser oprettelse af flere overvågningsposter, når den samme mail blev åbnet, hvilket resulterede i overvågning af "støj". Til sammenligning sammenlægges MailItemsAccessed-hændelser i færre overvågningsposter.

Du kan finde oplysninger om overvågningsposter for MailItemsAccessed-aktiviteter under [Brug Avanceret overvågning til at undersøge kompromitterede konti](mailitemsaccessed-forensics-investigations.md).

Hvis du vil søge efter MailItemsAccessed-overvågningsposter, kan du  søge efter aktiviteten Tilgåede postkasseelementer på rullelisten **Exchange-postkasseaktiviteter** i søgeværktøjet [](search-the-audit-log-in-security-and-compliance.md) til overvågningslogfiler i Microsoft 365 Overholdelsescenter.

![Søgning efter MailItemsAccessed-handlinger i overvågningsloggens søgeværktøj.](../media/AdvAudit_MailItemsAccessed.png)

Du kan også køre [Search-UnifiedAuditLog -Operations MailItemsAccessed](/powershell/module/exchange/search-unifiedauditlog) eller [Search-MailboxAuditLog -Operations MailItemsAccessed-kommandoer](/powershell/module/exchange/search-mailboxauditlog) i Exchange Online PowerShell.

### <a name="send"></a>Send

Hændelsen Send er også en overvågningshandling for en postkasse og udløses, når en bruger udfører en af følgende handlinger:

- Sender en mail

- Besvarer en mail

- Videresender en mail

Beskeder kan bruge hændelsen Send til at identificere mails, der sendes fra en kompromitteret konto. Overvågningsposten for en Send-hændelse indeholder oplysninger om meddelelsen, f.eks. hvornår meddelelsen blev sendt, InternetMessage-id'et, emnelinjen, og om meddelelsen indeholdt vedhæftede filer. Disse revisionsoplysninger kan hjælpe dig med at identificere oplysninger om mails, der er sendt fra en kompromitteret konto eller sendt af en hacker. Desuden kan modtagerne bruge et Microsoft 365 eDiscovery-værktøj til at søge efter meddelelsen (ved hjælp af emnelinjen eller meddelelses-id'et) for at identificere de modtagere, meddelelsen blev sendt til, og det faktiske indhold i den sendte meddelelse.

Hvis du vil søge efter Send overvågningsposter, kan du søge  efter aktiviteten Sendt meddelelse på rullelisten **Exchange-postkasseaktiviteter** i overvågningsloggens søgeværktøj i Microsoft 365 Overholdelsescenter.[](search-the-audit-log-in-security-and-compliance.md)

![Søge efter sendt meddelelseshandlinger i søgeværktøjet til overvågningslogfiler.](../media/AdvAudit_SentMessage.png)

Du kan også køre [kommandoerne Search-UnifiedAuditLog -Operations Send](/powershell/module/exchange/search-unifiedauditlog) eller [Search-MailboxAuditLog -Operations Send](/powershell/module/exchange/search-mailboxauditlog) i Exchange Online PowerShell.

### <a name="searchqueryinitiatedexchange"></a>SearchQueryInitiatedExchange

Hændelsen SearchQueryInitiatedExchange udløses, når en person bruger en Outlook til at søge efter elementer i en postkasse. Hændelser udløses, når der udføres søgninger i følgende Outlook miljøer:

- Outlook (computerklient)

- Outlook på internettet (OWA)

- Outlook til iOS

- Outlook til Android

- Mailapp til Windows 10

Kriterier kan bruge SearchQueryInitiatedExchange-begivenheden til at afgøre, om en hacker, der kan have kompromitteret en konto, søgt efter eller forsøgt at få adgang til følsomme oplysninger i postkassen. Overvågningsposten for en SearchQueryInitiatedExchange-hændelse indeholder oplysninger som f.eks. den faktiske tekst i søgeforespørgslen. Overvågningsposten angiver også det Outlook, som søgningen blev udført i. Ved at se på de søgeforespørgsler, en hacker kan have udført, kan en hacker bedre forstå formålet med de maildata, der blev søgt efter.

Hvis du vil søge efter SearchQueryInitiatedExchange-overvågningsposter, kan du  søge efter udført mailsøgningsaktivitet på rullelisten Søgeaktiviteter i overvågningsloggens søgeværktøj i overholdelsescenteret. [](search-the-audit-log-in-security-and-compliance.md)

![Søgning efter udførte mailsøgningshandlinger i overvågningsloggens søgeværktøj.](../media/AdvAudit_SearchExchange.png)

Du kan også køre [Search-UnifiedAuditLog -Operations SearchQueryInitiatedExchange](/powershell/module/exchange/search-unifiedauditlog) Exchange Online PowerShell.

> [!NOTE]
> Du skal aktivere SearchQueryInitiatedExchange for at blive logført, så du kan søge efter denne hændelse i overvågningsloggen. Du kan finde en vejledning [under Konfigurere Avanceret overvågning](set-up-advanced-audit.md#step-2-enable-advanced-audit-events).

### <a name="searchqueryinitiatedsharepoint"></a>SearchQueryInitiatedSharePoint

På samme måde som søgning efter postkasseelementer udløses hændelsen SearchQueryInitiatedSharePoint, når en person søger efter elementer i SharePoint. Hændelser udløses, når der udføres søgninger på rod- eller standardsiden af følgende typer SharePoint websteder:

- Startsider

- Kommunikationswebsteder

- Hubwebsteder

- Websteder, der er knyttet Microsoft Teams

Lige meget kan de bruge SearchQueryInitiatedSharePoint-hændelsen til at afgøre, om en hacker har forsøgt at finde (og muligvis få adgang til) følsomme oplysninger i SharePoint. Overvågningsposten for en SearchQueryInitiatedSharePoint-hændelse indeholder også den faktiske tekst i søgeforespørgslen. Overvågningsposten angiver også typen af websted SharePoint der blev søgt i. Ved at se på de søgeforespørgsler, en hacker kan have udført, kan en hacker bedre forstå formålet og omfanget af de fildata, der søges efter.

Hvis du vil søge efter SearchQueryInitiatedSharePoint-overvågningsposter, kan du søge efter søgeaktiviteten Udført **SharePoint** på rullelisten Søgeaktiviteter i overvågningsloggens [](search-the-audit-log-in-security-and-compliance.md) søgeværktøj i overholdelsescenteret.

![Søgning efter udført SharePoint søgehandlinger i overvågningsloggens søgeværktøj.](../media/AdvAudit_SearchSharePoint.png)

Du kan også køre [Search-UnifiedAuditLog -Operations SearchQueryInitiatedSharePoint](/powershell/module/exchange/search-unifiedauditlog) Exchange Online PowerShell.

> [!NOTE]
> Du skal aktivere SearchQueryInitiatedSharePoint for at blive logført, så du kan søge efter denne hændelse i overvågningsloggen. Du kan finde en vejledning [under Konfigurere Avanceret overvågning](set-up-advanced-audit.md#step-2-enable-advanced-audit-events).

### <a name="other-advanced-audit-events-in-microsoft-365"></a>Andre avancerede overvågningshændelser i Microsoft 365

Ud over hændelserne i Exchange Online og SharePoint Online er der hændelser i andre Microsoft 365-tjenester, der logføres, når brugere tildeles de relevante licenser til Avanceret overvågning. Følgende tjenester Microsoft 365 Avancerede overvågningshændelser. Vælg det tilsvarende link for at gå til en artikel, der identificerer og beskriver disse hændelser.

- [Microsoft Forms](search-the-audit-log-in-security-and-compliance.md#microsoft-forms-activities)

- [Microsoft Stream](/stream/audit-logs#actions-logged-in-stream)

- [Microsoft Teams](/microsoftteams/audit-log-events#teams-activities)

- [Yammer](search-the-audit-log-in-security-and-compliance.md#yammer-activities)

## <a name="high-bandwidth-access-to-the-office-365-management-activity-api"></a>Adgang med høj båndbredde til Office 365 Management Activity API

Organisationer, der har adgang til overvågningslogfiler via Office 365 Management Activity API, blev begrænset af begrænsninger på udgiverniveau. Det betyder, at grænsen blev delt af alle disse kunder for en udgiver, der trækker data på vegne af flere kunder.

Med udgivelsen af Avanceret overvågning flytter vi fra en grænse på udgiverniveau til en grænse på lejerniveau. Resultatet er, at hver organisation får deres egen fuldt allokerede båndbreddekvote for at få adgang til deres overvågningsdata. Båndbredden er ikke en statisk, foruddefineret grænse, men er modelleret ud fra en kombination af faktorer, herunder antallet af pladser i organisationen, og at E5/A5/G5-organisationer får mere båndbredde end ikke-E5/A5/G5-organisationer.

Alle organisationer får i første omgang tildelt en oprindelig plan på 2.000 anmodninger i minuttet. Denne grænse øges dynamisk afhængigt af en organisations antal sæder og deres licenseringsabonnement. E5/A5/G5-organisationer får ca. dobbelt så meget båndbredde som ikke-E5/A5/G5-organisationer. Der vil også være en grænse for den maksimale båndbredde for at beskytte tjenestens tilstand.

Du kan finde flere oplysninger i afsnittet "API-begrænsning" i Office 365 [Management Activity API-reference](/office/office-365-management-api/office-365-management-activity-api-reference#api-throttling).

## <a name="faqs-for-advanced-audit"></a>Ofte stillede spørgsmål til Avanceret overvågning

**Skal alle brugere have en E5/A5/G5-licens for at kunne drage fordel af Avanceret overvågning?**

For at kunne drage fordel af avancerede overvågningsfunktioner på brugerniveau skal en bruger have tildelt en E5/A5/G5-licens. Der er nogle funktioner, der kontrollerer, om den relevante licens skal vise funktionen for brugeren. Hvis du f.eks. forsøger at bevare overvågningsposterne for en bruger, der ikke har fået tildelt den relevante licens i mere end 90 dage, returnerer systemet en fejlmeddelelse.

**Min organisation har et E5/A5/G5-abonnement. Skal jeg gøre noget for at få adgang til overvågningsposter for Avancerede overvågningshændelser?**

For berettigede kunder og brugere, der er tildelt den relevante E5/A5/G5-licens, er der ingen handling nødvendig for at få adgang til avancerede overvågningshændelser med undtagelse af aktivering af SearchQueryInitiatedExchange og SearchQueryInitiatedSharePoint-hændelser (som beskrevet tidligere i denne artikel). Avancerede overvågningshændelser genereres kun for brugere med E5/A5/G5-licenser, når disse licenser er blevet tildelt.

**Er de nye hændelser i Avanceret overvågning tilgængelig i Office 365 Management Activity API?**

Ja. Så længe der genereres overvågningsposter for brugere med den relevante licens, vil du kunne få adgang til disse poster via Office 365 Management Activity API.

**Hvad sker der med min organisations overvågningslogdata, hvis jeg opretter en 10-års opbevaringspolitik for overvågningsloggen, når funktionen blev frigivet til generel tilgængelighed, men før den nødvendige tilføjelseslicens blev gjort tilgængelig?**

Alle data i overvågningsloggen, der er dækket af en 10-års opbevaringspolitik for overvågningsloggen, som du oprettede, efter funktionen blev frigivet til generel tilgængelighed i sidste kvartal i 2020, bevares i 10 år. Dette omfatter 10-års opbevaringspolitikker for overvågningsloggen, der blev oprettet, før den nødvendige tilføjelseslicens blev frigivet til køb i marts 2021. Men da en opbevaringslicens til en 10-års overvågningslog er tilgængelig, skal du købe og tildele disse tilføjelseslicenser til alle brugere, hvis overvågningsdata er dækket af en 10-års opbevaringspolitik for overvågning.
