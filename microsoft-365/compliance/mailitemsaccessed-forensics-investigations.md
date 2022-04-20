---
title: Brug Overvågning (Premium) til at undersøge kompromitterede konti
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
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Brug overvågningshandlingen MailItemsAccessed-postkasse til at udføre tekniske undersøgelser af kompromitterede brugerkonti.
ms.openlocfilehash: 658a4b079bd7909f8436867efd86d3ac04d61aa2
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946193"
---
# <a name="use-microsoft-purview-audit-premium-to-investigate-compromised-accounts"></a>Brug Microsoft Purview Audit (Premium) til at undersøge kompromitterede konti

En kompromitteret brugerkonto (også kaldet en *kontoovertagelse*) er en type angreb, når en hacker får adgang til en brugerkonto og fungerer som brugeren. Disse typer angreb forårsager nogle gange mere skade, end angriberen har til hensigt. Når du undersøger kompromitterede mailkonti, skal du antage, at flere maildata er blevet kompromitteret, end det kan være angivet, ved at spore personens faktiske tilstedeværelse. Afhængigt af typen af data i mails skal du antage, at følsomme oplysninger blev kompromitteret, eller at de blev pålagt lovmæssige bøder, medmindre du kan bevise, at følsomme oplysninger ikke blev eksponeret. HIPAA-regulerede organisationer står f.eks. over for betydelige bøder, hvis der er tegn på, at patientsundhedsmæssige oplysninger (PHI) blev eksponeret. I disse tilfælde er det usandsynligt, at hackere er interesseret i PHI, men organisationer skal stadig rapportere brud på datasikkerheden, medmindre de kan bevise andet.

For at hjælpe dig med at undersøge kompromitterede mailkonti overvågninger vi nu adgang til maildata via mailprotokoller og klienter med handlingen *MailItemsAccessed* mailbox-auditing. Denne nye overvågede handling vil hjælpe efterforskerne med bedre at forstå brud på maildata og hjælpe dig med at identificere omfanget af kompromiser for bestemte mailelementer, der kan blive kompromitteret. Målet om at bruge denne nye overvågningshandling er teknisk forsvarlighed for at hævde, at en bestemt postdata ikke blev kompromitteret. Hvis en person med ondsindede hensigter fik adgang til en bestemt post, overvåges hændelsen Exchange Online, selvom der ikke er noget, der tyder på, at postelementet blev læst.

## <a name="the-mailitemsaccessed-mailbox-auditing-action"></a>Overvågningshandlingen MailItemsAccessed for postkasse

Den nye MailItemsAccessed-handling er en del af den nye [overvågningsfunktion (Premium).](advanced-audit.md) Det er en del af [overvågning af Exchange postkasse](/office365/securitycompliance/enable-mailbox-auditing#mailbox-auditing-actions) og er som standard aktiveret for brugere, der har fået tildelt en Office 365- eller Microsoft 365 E5-licens, eller for organisationer med et Microsoft 365 E5 Overholdelse tilføjelsesprogramabonnement.

Handlingen MailItemsAccessed mailbox-auditing dækker alle mailprotokoller: POP, IMAP, MAPI, EWS, Exchange ActiveSync og REST. Den dækker også begge typer af adgang til mail: *synkroniser* og *bind*.

### <a name="auditing-sync-access"></a>Overvågning af synkroniseringsadgang

Synkroniseringshandlinger registreres kun, når en postkasse tilgås af en skrivebordsversion af Outlook-klienten til Windows eller Mac. Under synkroniseringshandlingen downloader disse klienter typisk et stort sæt postelementer fra skyen til en lokal computer. Overvågningsmængden for synkroniseringshandlinger er enorm. Så i stedet for at generere en overvågningspost for hvert postelement, der er synkroniseret, genererer vi en overvågningshændelse for den mailmappe, der indeholder elementer, der er synkroniseret, og antager, at *alle* postelementer i den synkroniserede mappe er blevet kompromitteret. Adgangstypen registreres i feltet OperationProperties for overvågningsposten.

Se trin 2 i afsnittet [Brug MailItemsAccessed-overvågningsposter til retsmedicinske undersøgelser](#use-mailitemsaccessed-audit-records-for-forensic-investigations) for et eksempel på visning af adgangstypen for synkronisering i en overvågningspost.

### <a name="auditing-bind-access"></a>Overvågningsbindingsadgang

En bindingshandling er en individuel adgang til en mail. I forbindelse med bindingsadgang registreres InternetMessageId for individuelle meddelelser i overvågningsposten. Posterne for MailItemsAccessed-overvågningshandlingen binder handlinger og samles derefter i en enkelt overvågningspost. Alle bindingshandlinger, der forekommer inden for et 2-minutters interval, samles i en enkelt overvågningspost i feltet Mapper i egenskaben AuditData. Hver meddelelse, der blev åbnet, identificeres af dens InternetMessageId. Antallet af bindingshandlinger, der er samlet i posten, vises i feltet OperationCount i egenskaben AuditData.

Se trin 4 i afsnittet [Brug MailItemsAccessed-overvågningsposter til tekniske undersøgelser](#use-mailitemsaccessed-audit-records-for-forensic-investigations) for et eksempel på visning af bindingsadgangstypen i en overvågningspost.

### <a name="throttling-of-mailitemsaccessed-audit-records"></a>Begrænsning af MailItemsAccessed-overvågningsposter

Hvis der genereres mere end 1.000 MailItemsAccessed-overvågningsposter på mindre end 24 timer, stopper Exchange Online med at generere overvågningsposter for MailItemsAccessed-aktivitet. Når en postkasse er begrænset, logføres MailItemsAccessed-aktivitet ikke i 24 timer, efter postkassen blev begrænset. Hvis postkassen blev begrænset, er der et potentiale for, at postkassen kan være blevet kompromitteret i denne periode. Optagelsen af MailItemsAccessed-aktivitet genoptages efter en 24-timers periode.

Her er et par ting, du skal være opmærksom på i forbindelse med begrænsning:

- Mindre end 1 % af alle postkasser i Exchange Online er begrænset
- Når en postkasse begrænses, overvåges kun poster for MailItemsAccessed-aktivitet ikke. Andre handlinger til overvågning af postkasser påvirkes ikke.
- Postkasser begrænses kun for bind-handlinger. Overvågningsposterne for synkroniseringshandlinger begrænses ikke.
- Hvis en postkasse er begrænset, kan du sandsynligvis antage, at der var MailItemsAccessed-aktivitet, der ikke blev registreret i overvågningsloggene.

Se trin 1 i afsnittet [Brug MailItemsAccessed-overvågningsposter til retsmedicinske undersøgelser](#use-mailitemsaccessed-audit-records-for-forensic-investigations) for et eksempel på visning af egenskaben IsThrottled i en overvågningspost.

## <a name="use-mailitemsaccessed-audit-records-for-forensic-investigations"></a>Brug MailItemsAccessed-overvågningsposter til tekniske undersøgelser

Overvågning af postkasser genererer overvågningsposter for at få adgang til mails, så du kan være sikker på, at mails ikke er blevet kompromitteret. I de tilfælde, hvor vi ikke er sikre på, at nogle data er blevet tilgået, antager vi derfor, at det er det, ved at registrere al postadgangsaktivitet.

Brug af MailItemsAccessed-overvågningsposter til tekniske formål udføres typisk, når et databrud er blevet løst, og hackeren er blevet fjernet. For at begynde din undersøgelse skal du identificere det sæt postkasser, de er blevet kompromitteret, og fastlægge tidsrammen for, hvornår hackeren havde adgang til postkasser i din organisation. Derefter kan du bruge cmdlet'erne **Search-UnifiedAuditLog** eller **Search-MailboxAuditLog** i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) til at søge efter overvågningsposter, der svarer til databrud.

Du kan køre en af følgende kommandoer for at søge efter MailItemsAccessed-overvågningsposter:

**Samlet overvågningslog**:

```powershell
Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000
```

**Overvågningslog for postkasse**:

```powershell
Search-MailboxAuditLog -Identity <user> -StartDate 01/06/2020 -EndDate 01/20/2020 -Operations MailItemsAccessed -ResultSize 1000 -ShowDetails
```

> [!TIP]
> En primær forskel mellem disse to cmdlet'er, da du kan bruge cmdlet'en **Search-UnifiedAuditLog** til at søge efter overvågningsposter for aktivitet, der er udført af en eller flere brugere. Det skyldes, at *UserIds* er en parameter med flere værdier. **Cmdlet'en Search-MailboxAuditLog** søger i postkassens overvågningslog for en enkelt bruger.

Her er trinnene til brug af MailItemsAccessed-overvågningsposter til at undersøge et kompromitteret brugerangreb. Hvert trin viser kommandosyntaksen for cmdlet'erne **Search-UnifiedAuditLog** eller **Search-MailboxAuditLog** .

1. Kontrollér, om postkassen er blevet begrænset. Hvis det er tilfældet, betyder det, at nogle poster til overvågning af postkasser ikke ville være logført. Hvis alle overvågningsposter har "IsThrottled", er "True", skal du antage, at den post blev genereret i en 24-timers periode, at adgangen til postkassen ikke blev overvåget, og at alle maildata er blevet kompromitteret.

   Kør følgende kommando for at søge efter PostItemsAccessed-poster, hvor postkassen blev begrænset:

   **Samlet overvågningslog**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"IsThrottled","Value":"True"*'} | FL
   ```

   **Overvågningslog for postkasse**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*IsThrottled:True*"} | FL
   ```

2. Kontrollér, om der er synkroniseringsaktiviteter. Hvis en hacker bruger en mailklient til at downloade meddelelser i en postkasse, kan vedkommende afbryde forbindelsen mellem computeren og internettet og få adgang til meddelelserne lokalt uden at interagere med serveren. I dette tilfælde kan overvågning af postkasser ikke overvåge disse aktiviteter.

   Hvis du vil søge efter PostItemsAccessed-poster, hvor postelementerne blev åbnet af en synkroniseringshandling, skal du køre følgende kommando:

   **Samlet overvågningslog**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 02/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Sync"*'} | FL
   ```

   **Overvågningslog for postkasse**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Sync*"} | FL
   ```

3. Kontrollér synkroniseringsaktiviteter for at finde ud af, om de er opstået i den samme kontekst som den, der bruges af hackeren til at få adgang til postkassen. Konteksten identificeres og differentieres af IP-adressen på den klientcomputer, der bruges til at få adgang til postkassen og mailprotokollen. Du kan finde flere oplysninger i afsnittet [Identificere adgangskontekster for forskellige overvågningsposter](#identifying-the-access-contexts-of-different-audit-records) .

   Brug de egenskaber, der er angivet nedenfor, til at undersøge det. Disse egenskaber er placeret i egenskaben AuditData eller OperationProperties. Hvis nogen af synkroniseringerne finder sted i samme kontekst som hackeraktiviteten, skal du antage, at hackeren har synkroniseret alle mailelementer til deres klient, hvilket betyder, at hele postkassen sandsynligvis er blevet kompromitteret.

   <br>

   ****

   |Ejendom|Beskrivelse|
   |---|---|
   |ClientInfoString|Beskriver protokol, klient (omfatter version)|
   |ClientIPAddress|KLIENTcomputerens IP-adresse.|
   |Sessionid|Sessions-id hjælper med at differentiere hackerhandlinger i forhold til daglige brugeraktiviteter på den samme konto (nyttigt til kompromitterede konti)|
   |Userid|UPN for den bruger, der læser meddelelsen.|
   |

4. Kontrollér, om der er bind-aktiviteter. Når du har udført trin 2 og trin 3, kan du være sikker på, at al anden adgang til mails fra hackeren registreres i MailItemsAccessed-overvågningsposter, der har egenskaben MailAccessType med værdien "Bind".

   Hvis du vil søge efter PostItemsAccessed-poster, hvor postelementerne blev åbnet af en bind-handling, skal du køre følgende kommando.

   **Samlet overvågningslog**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Bind"*'} | FL
   ```

   **Overvågningslog for postkasse**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Bind*"} | FL
   ```

   De mails, der blev åbnet, identificeres af deres internetmeddelelses-id. Du kan også kontrollere, om nogen overvågningsposter har samme kontekst som dem for andre personer med ondsindede hensigter. Du kan finde flere oplysninger i afsnittet [Identificere adgangskontekster for forskellige overvågningsposter](#identifying-the-access-contexts-of-different-audit-records) .

   Du kan bruge overvågningsdataene til bindingshandlinger på to forskellige måder:

   - Få adgang til eller saml alle mails, som hackeren har adgang til, ved hjælp af InternetMessageId for at finde dem og derefter kontrollere, om nogen af disse meddelelser indeholder følsomme oplysninger.
   - Brug InternetMessageId til at søge efter overvågningsposter, der er relateret til et sæt potentielt følsomme mails. Dette er nyttigt, hvis du kun er bekymret for nogle få meddelelser.

## <a name="filtering-of-duplicate-audit-records"></a>Filtrering af duplikerede overvågningsposter

Duplikerede overvågningsposter for de samme bindingshandlinger, der forekommer inden for en time efter hinanden, filtreres ud for at fjerne overvågningsstøj. Synkroniseringshandlinger filtreres også ud med en times intervaller. Undtagelsen til denne deduplikeringsproces opstår, hvis en af de egenskaber, der er beskrevet i følgende tabel, er forskellige for det samme InternetMessageId. Hvis en af disse egenskaber er anderledes i en dublethandling, oprettes der en ny overvågningspost. Denne proces er beskrevet mere detaljeret i næste afsnit.

<br>

****

|Ejendom|Beskrivelse|
|---|---|
|ClientIPAddress|Klientcomputerens IP-adresse.|
|ClientInfoString|Klientprotokollen, der bruges til at få adgang til postkassen.|
|Overordnetmappe|Den fulde mappesti til det postelement, der blev åbnet.|
|Logon_type|Logontypen for den bruger, der udførte handlingen. Logontyperne (og deres tilsvarende Enum-værdi) er Ejer (0), Administrator (1) eller Stedfortræder (2).|
|MailAccessType|Angiver, om adgangen er en binding eller en synkroniseringshandling.|
|PostkasseUPN|UPN'et for den postkasse, hvor meddelelsen, der læses, er placeret.|
|Bruger|UPN for den bruger, der læser meddelelsen.|
|Sessionid|Sessions-id'et hjælper med at differentiere hackerhandlinger og daglige brugeraktiviteter i den samme postkasse (i tilfælde af kompromitteret konto) Du kan få flere oplysninger om sessioner under [Kontekstualisere hackeraktivitet i sessioner i Exchange Online](https://techcommunity.microsoft.com/t5/exchange-team-blog/contextualizing-attacker-activity-within-sessions-in-exchange/ba-p/608801).|
|

## <a name="identifying-the-access-contexts-of-different-audit-records"></a>Identificering af adgangskontekster for forskellige overvågningsposter

Det er almindeligt, at en person med ondsindede hensigter kan få adgang til en postkasse samtidig med, at ejeren af postkassen får adgang til den. Hvis du vil skelne mellem adgang for hackeren og ejeren af postkassen, er der overvågningspostegenskaber, der definerer adgangens kontekst. Som tidligere forklaret, oprettes der separate overvågningsposter, når værdierne for disse egenskaber er forskellige, selvom aktiviteten forekommer inden for sammenlægningsintervallet. I følgende eksempel er der tre forskellige overvågningsposter. Hver enkelt adskiller sig fra egenskaberne Session ID og ClientIPAddress. De meddelelser, der blev åbnet, identificeres også.

<br>

****

|Overvågningspost 1|Overvågningspost 2|Overvågningspost 3|
|---|---|---|
|ClientIPAddress1<br/>**SessionId2**|ClientIPAddress2<br/>**SessionId2**|ClientIPAddress1<br/>**SessionId3**|
|InternetMessageIdA<br/>InternetMessageIdD<br/>InternetMessageIdE<br/>InternetMessageIdF<br/>|InternetMessageIdA<br/>InternetMessageIdC|InternetMessageIdB|
|

Hvis nogle af de egenskaber, der er angivet i tabellen i det [forrige afsnit](#filtering-of-duplicate-audit-records) , er forskellige, oprettes der en separat overvågningspost for at spore den nye kontekst. Adgange sorteres i de separate overvågningsposter afhængigt af den kontekst, som aktiviteten fandt sted i.

I overvågningsposter, der vises på følgende skærmbillede, er adgangsaktiviteten sorteret i forskellige overvågningsposter, afhængigt af den kontekst, som adgangen fandt sted i, selvom vi tilgår mail fra EWSEditor og OWA samtidig. I dette tilfælde defineres konteksten af forskellige værdier for egenskaben ClientInfoString.

![Forskellige overvågningsposter baseret på kontekst.](../media/MailItemsAccessed4.png)

Her er syntaksen for den kommando, der blev vist på det forrige skærmbillede:

```powershell
Search-MailboxAuditLog -Identity admin -ShowDetails -Operations MailItemsAccessed -ResultSize 2000 | Select LastAccessed,Operation,AuditOperationsCountInAggregatedRecord,ClientInfoString
```
