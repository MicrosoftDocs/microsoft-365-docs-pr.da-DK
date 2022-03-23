---
title: Brug Avanceret overvågning til at undersøge kompromitterede konti
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
description: Brug mailItemsAccessed-overvågningshandlingen for postkasser til at undersøge kompromitterede brugerkonti efter undersøgelse af kompromitterede brugerkonti.
ms.openlocfilehash: 8bfba164bf3bfb0f4fa4bea687d0fe040cff4836
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63588389"
---
# <a name="use-advanced-audit-to-investigate-compromised-accounts"></a>Brug Avanceret overvågning til at undersøge kompromitterede konti

En kompromitteret brugerkonto (også kaldet en *kontoovertagelse*) er en type angreb, når en hacker opnår adgang til en brugerkonto og fungerer som brugeren. Disse typer angreb forårsager nogle gange mere skade, end hackeren kunne have til hensigt. Når du undersøger kompromitterede mailkonti, skal du antage, at flere maildata er blevet kompromitteret, end det kan være angivet ved at spore hackerens faktiske tilstedeværelse. Afhængigt af typen af data i mails er du nødt til at antage, at følsomme oplysninger er blevet kompromitteret eller får lovmæssige finter, medmindre du kan bevise, at følsomme oplysninger ikke blev vist. Eksempelvis oplever HIPAA-regulerede organisationer betydelige fines, hvis der er tegn på, at patient sundhedsoplysninger (PHI) blev eksponeret. I disse tilfælde vil hackere sandsynligvis ikke være interesserede i PHI, men organisationer skal stadig rapportere om databrider, medmindre de kan bevise andet.

For at hjælpe dig med at undersøge kompromitterede mailkonti, overvåger vi nu adgang til maildata efter mailprotokoller og klienter med handlingen *MailItemsAccessed* mailbox-auditing. Denne nye reviderede handling vil hjælpe bedre med at forstå brud på maildata og hjælpe dig med at identificere omfanget af kompromiser til bestemte mailelementer, der kan være blevet kompromitteret. Formålet med at bruge denne nye revisionshandling er at bekræfte, at en bestemt post ikke er blevet kompromitteret. Hvis en hacker har fået adgang til en bestemt mail, vil Exchange Online denne hændelse, selvom der ikke er noget, der indikerer, at mailelementet blev læst.

## <a name="the-mailitemsaccessed-mailbox-auditing-action"></a>Handlingen MailItemsAccessed mailbox-auditing

Den nye Handling MailItemsAccessed er en del af den nye funktionalitet [Avanceret](advanced-audit.md) overvågning. Det er en del af [](/office365/securitycompliance/enable-mailbox-auditing#mailbox-auditing-actions) Exchange-postkasserevision og er aktiveret som standard for brugere, der er tildelt en Office 365- eller Microsoft 365 E5-licens eller for organisationer med et Microsoft 365 E5 Overholdelse-tilføjelsesabonnement.

Handlingen MailItemsAccessed til overvågning af postkasse dækker alle mailprotokoller: POP, IMAP, MAPI, EWS, Exchange ActiveSync og REST. Den dækker også begge typer adgang til mail: *synkronisering og* *indbinding*.

### <a name="auditing-sync-access"></a>Overvågning af synkroniseringsadgang

Synkroniseringshandlinger registreres kun, når en postkasse åbnes i en skrivebordsversion af Outlook til Windows eller Mac. Under synkroniseringen downloader disse klienter typisk et stort sæt mailelementer fra skyen til en lokal computer. Overvågningsmængden for synkroniseringshandlinger er enorm. Så i stedet for at generere en overvågningspost for hvert mailelement, der er synkroniseret, genererer vi en overvågningshændelse for mailmappen, der indeholder elementer, der blev synkroniseret, og vi antager, at *alle mailelementer* i den synkroniserede mappe er blevet kompromitteret. Adgangstypen registreres i feltet OperationProperties i overvågningsposten.

Se trin 2 i afsnittet [Brug MailItemsAccessed-overvågningsposter](#use-mailitemsaccessed-audit-records-for-forensic-investigations) til undersøgelse af undersøgelser, hvor der kan vises et eksempel på synkroniseringsadgangstypen i en overvågningspost.

### <a name="auditing-bind-access"></a>Overvågning af binding af adgang

En indbindingshandling er en individuel adgang til en mail. For bind-adgang registreres InternetMessageId for individuelle meddelelser i overvågningsposten. MailItemsAccessed-overvågningshandlingsposter binder handlinger og sammenlægges derefter til en enkelt overvågningspost. Alle indbindingshandlinger, der forekommer inden for et interval på 2 minutter, sammenlægges i en enkelt overvågningspost i feltet Mapper i egenskaben AuditData. Hver meddelelse, der blev tilgået, identificeres af dens InternetMessageId. Antallet af indbindingshandlinger, der blev sammenlagt i posten, vises i feltet OperationCount i egenskaben AuditData.

Se trin 4 i afsnittet [Brug MailItemsAccessed-overvågningsposter](#use-mailitemsaccessed-audit-records-for-forensic-investigations) til undersøgelse af undersøgelser, hvor der kan ses et eksempel på den indbindede adgangstype i en overvågningspost.

### <a name="throttling-of-mailitemsaccessed-audit-records"></a>Begrænsning af MailItemsAccessed-overvågningsposter

Hvis der genereres mere end 1.000 MailItemsAccessed-overvågningsposter på mindre end 24 timer, stopper Exchange Online med at generere overvågningsposter for MailItemsAccessed-aktivitet. Når en postkasse er begrænset, logføres MailItemsAccessed-aktivitet ikke i 24 timer, efter postkassen blev begrænset. Hvis postkassen blev sat på, kan det være, at postkassen er blevet kompromitteret i denne periode. Optagelsen af MailItemsAccessed-aktivitet genoptages efter en 24-timers periode.

Her er nogle ting, du skal huske om begrænsning:

- Mindre end 1 % af alle postkasser i Exchange Online bliver begrænser
- Når en postkasse er begrænset, overvåges kun overvågningsposter for MailItemsAccessed-aktivitet ikke. Andre postkassehandlinger påvirkes ikke.
- Postkasser er kun bundet for Indbindingshandlinger. Overvågningsposter for synkroniseringshandlinger bliver ikke begrænser.
- Hvis en postkasse er begrænset, kan du sandsynligvis antage, at der var MailItemsAccessed-aktivitet, der ikke blev registreret i overvågningslogfilerne.

Se trin 1 i afsnittet [Brug MailItemsAccessed-overvågningsposter](#use-mailitemsaccessed-audit-records-for-forensic-investigations) til undersøgelse af undersøgelser, hvor der kan vises et eksempel på egenskaben IsThrottled i en overvågningspost.

## <a name="use-mailitemsaccessed-audit-records-for-forensic-investigations"></a>Brug MailItemsAccessed-overvågningsposter til undersøgelse af undersøgelser, der undersøges

Overvågning af postkasser genererer overvågningsposter for adgang til mails, så du kan være sikker på, at mails ikke er blevet kompromitteret. I tilfælde, hvor vi ikke er sikre på, at der er adgang til nogle data, antager vi derfor, at det har ved at registrere alle aktiviteter for adgang til mail.

Brug af MailItemsAccessed-overvågningsposter til informationsformål udføres typisk, når en databristning er blevet løst, og hackeren er blevet fjernet. For at påbegynde din undersøgelse skal du identificere sættet af postkasser, som de er blevet kompromitteret, og fastlægge tidsrammen, hvor hacker havde adgang til postkasser i din organisation. Derefter kan du bruge **cmdlet'erne Search-UnifiedAuditLog** eller **Search-MailboxAuditLog** i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) til at søge i overvågningsposter, der svarer til databruddene.

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
> En primær forskel mellem disse to cmdlet'er, da du kan bruge cmdlet'en **Search-UnifiedAuditLog** til at søge efter overvågningsposter for aktivitet, der er udført af en eller flere brugere. Det skyldes, at *UserIds er* en parameter med flere værdier. **Cmdlet'en Search-MailboxAuditLog** søger i postkassens overvågningslog for en enkelt bruger.

Her er trinnene til brug af MailItemsAccessed-overvågningsposter til at undersøge et kompromitteret brugerangreb. Hvert trin viser kommandosyntaksen for **cmdlet'erne Search-UnifiedAuditLog** eller **Search-MailboxAuditLog** .

1. Kontrollér, om postkassen er blevet kontrolleret. Hvis det er ja, betyder det, at nogle postkasserevisionsposter ikke er blevet logført. Hvis alle overvågningsposter har "IsThrottled" er "Sand", skal du antage, at i en 24-timers periode senere blev den pågældende post oprettet, at al adgang til postkassen ikke blev overvåget, og at alle maildata er blevet kompromitteret.

   Hvis du vil søge efter MailItemsAccessed-poster, hvor postkassen blev begrænset, skal du køre følgende kommando:

   **Samlet overvågningslog**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"IsThrottled","Value":"True"*'} | FL
   ```

   **Overvågningslog for postkasse**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*IsThrottled:True*"} | FL
   ```

2. Kontrollér, om der er synkroniseringsaktiviteter. Hvis en hacker bruger en mailklient til at hente meddelelser i en postkasse, kan de afbryde forbindelsen mellem computeren og internettet og få adgang til meddelelserne lokalt uden at interagere med serveren. I dette tilfælde vil postkasserevisionen ikke kunne overvåge disse aktiviteter.

   Hvis du vil søge efter MailItemsAccessed-poster, hvor mailelementer blev åbnet via en synkroniseringshandling, skal du køre følgende kommando:

   **Samlet overvågningslog**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 02/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Sync"*'} | FL
   ```

   **Overvågningslog for postkasse**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Sync*"} | FL
   ```

3. Kontrollér synkroniseringsaktiviteter for at fastlægge, om nogen af dem er sket i samme sammenhæng som den, der blev brugt af hackeren til at få adgang til postkassen. Kontekst identificeres og skelnes ud fra IP-adressen på klientcomputeren, der bruges til at få adgang til postkassen og mailprotokol. Du kan finde flere oplysninger [i afsnittet Identificere adgangskontekster for forskellige overvågningsposter](#identifying-the-access-contexts-of-different-audit-records) .

   Brug de egenskaber, der er angivet nedenfor, til at undersøge sagen. Disse egenskaber findes i egenskaben AuditData eller OperationProperties. Hvis nogen af synkroniseringerne sker i samme kontekst som hackerens aktivitet, skal det antages, at hackeren har synkroniseret alle mailelementer til deres klient, hvilket betyder, at hele postkassen sandsynligvis er blevet kompromitteret.

   <br>

   ****

   |Egenskab|Beskrivelse|
   |---|---|
   |ClientInfoString|Beskriver protokol, klient (omfatter version)|
   |ClientIPAddress|Klientcomputerens IP-adresse.|
   |SessionId|Sessions-id hjælper med at skelne mellem hackerhandlinger vs. daglige brugeraktiviteter på den samme konto (nyttige ved kompromitterede konti)|
   |UserId|UPN for den bruger, der læser meddelelsen.|
   |

4. Kontrollér for indbindingsaktiviteter. Når du har udført trin 2 og 3, kan du være sikker på, at alle andre hackerens adgang til mails vil blive registreret i PostItemsAccessed-overvågningsposterne, der har en MailAccessType-egenskab med værdien "Bind".

   Hvis du vil søge efter MailItemsAccessed-poster, hvor mailelementer blev åbnet via en Bind-handling, skal du køre følgende kommando.

   **Samlet overvågningslog**:

   ```powershell
   Search-UnifiedAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -UserIds <user1,user2> -Operations MailItemsAccessed -ResultSize 1000 | Where {$_.AuditData -like '*"MailAccessType","Value":"Bind"*'} | FL
   ```

   **Overvågningslog for postkasse**:

   ```powershell
   Search-MailboxAuditLog -StartDate 01/06/2020 -EndDate 01/20/2020 -Identity <user> -Operations MailItemsAccessed -ResultSize 10000 -ShowDetails | Where {$_.OperationProperties -like "*MailAccessType:Bind*"} | FL
   ```

   De mails, der blev åbnet, identificeres ved hjælp af deres internetmeddelelses-id. Du kan også kontrollere, om nogen overvågningsposter har samme kontekst som dem for andre hackeraktiviteter. Du kan finde flere oplysninger [i afsnittet Identificere adgangskontekster for forskellige overvågningsposter](#identifying-the-access-contexts-of-different-audit-records) .

   Du kan bruge overvågningsdataene til at binde handlinger på to forskellige måder:

   - Få adgang til eller indsaml alle mails, som hackeren har adgang til ved hjælp af InternetMessageId, for at finde dem og derefter kontrollere, om nogen af disse meddelelser indeholder følsomme oplysninger.
   - Brug InternetMessageId til at søge i overvågningsposter, der er relateret til et sæt potentielt følsomme mails. Dette er nyttigt, hvis du kun er bekymret over nogle få meddelelser.

## <a name="filtering-of-duplicate-audit-records"></a>Filtrering af dublerede overvågningsposter

Dublerede overvågningsposter for de samme opbindingshandlinger, der forekommer inden for en time af hinanden, filtreres fra for at fjerne overvågningsstøj. Synkroniseringshandlinger filtreres også fra med intervaller på én time. Undtagelsen til denne duplikeringsproces forekommer, hvis nogen af de egenskaber, der er beskrevet i nedenstående tabel, er anderledes for det samme InternetMessageId. Hvis en af disse egenskaber er anderledes i en dublethandling, oprettes der en ny overvågningspost. Denne proces beskrives mere detaljeret i næste afsnit.

<br>

****

|Egenskab|Beskrivelse|
|---|---|
|ClientIPAddress|Klientcomputerens IP-adresse.|
|ClientInfoString|Klientprotokol, som er klient, der bruges til at få adgang til postkassen.|
|ParentFolder|Hele mappestien for det mailelement, der blev åbnet.|
|Logon_type|Logontypen for den bruger, der udførte handlingen. Logontyperne (og deres tilsvarende Enum-værdi) er Ejer (0), Administrator (1) eller Stedfortræder (2).|
|MailAccessType|Uanset om adgang er en indbindings- eller synkroniseringshandling.|
|MailboxUPN|UPN'et for den postkasse, hvor den meddelelse, der læses, er placeret.|
|Bruger|UPN'et for den bruger, der læser meddelelsen.|
|SessionId|Sessions-id'et hjælper med at skelne mellem hackerhandlinger og daglige brugeraktiviteter i den samme postkasse (i tilfælde af kontoforlig) Du kan finde flere oplysninger om sessioner i Kontekstafhængig aktivitet for hackere i sessioner [i Exchange Online](https://techcommunity.microsoft.com/t5/exchange-team-blog/contextualizing-attacker-activity-within-sessions-in-exchange/ba-p/608801).|
|

## <a name="identifying-the-access-contexts-of-different-audit-records"></a>Identificere adgangskontekster for forskellige overvågningsposter

Det er almindeligt, at en hacker kan få adgang til en postkasse på samme tid, som postkasseejeren har adgang til den. For at skelne mellem adgang for hackeren og postkasseejeren er der overvågningspostegenskaber, der definerer adgangskonteksten. Som beskrevet tidligere genereres der separate overvågningsposter, når værdierne for disse egenskaber er forskellige, selv når aktiviteten forekommer inden for sammenlægningsintervallet. I følgende eksempel er der tre forskellige overvågningsposter. Hver enkelt skelnes ud fra egenskaberne Sessions-id og ClientIPAddress. De meddelelser, der blev åbnet, identificeres også.

<br>

****

|Overvågningspost 1|Overvågningspost 2|Overvågningspost 3|
|---|---|---|
|ClientIPAddress1<br/>**SessionId2**|ClientIPAddress2<br/>**SessionId2**|ClientIPAddress1<br/>**SessionId3**|
|InternetMessageIdA<br/>InternetMessageIdD<br/>InternetMessageIdE<br/>InternetMessageIdF<br/>|InternetMessageIdA<br/>InternetMessageIdC|InternetMessageIdB|
|

Hvis nogen af de egenskaber, der er angivet i tabellen [](#filtering-of-duplicate-audit-records) i forrige afsnit, er anderledes, genereres der en separat overvågningspost for at spore den nye kontekst. Adgange sorteres i de separate overvågningsposter afhængigt af den kontekst, hvori aktiviteten fandt sted.

I overvågningsposter, der er vist på følgende skærmbillede, selvom vi tilgår mail fra EWSEditor og OWA samtidigt, samles adgangsaktiviteten f.eks. i forskellige overvågningsposter afhængigt af den kontekst, hvori adgang fandt sted. I dette tilfælde defineres konteksten af forskellige værdier for egenskaben ClientInfoString.

![Forskellige overvågningsposter baseret på kontekst.](../media/MailItemsAccessed4.png)

Her er syntaksen for den kommando, der vises på det forrige skærmbillede:

```powershell
Search-MailboxAuditLog -Identity admin -ShowDetails -Operations MailItemsAccessed -ResultSize 2000 | Select LastAccessed,Operation,AuditOperationsCountInAggregatedRecord,ClientInfoString
```
