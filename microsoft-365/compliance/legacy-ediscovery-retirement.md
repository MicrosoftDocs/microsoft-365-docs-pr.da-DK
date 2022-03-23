---
title: Tilbagetrækning af ældre eDiscovery-værktøjer
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
description: In-Place eDiscovery- og In-Place Hold (og de tilsvarende PowerShell-cmdlet'er) i Exchange Online udgår i første halvdel af 2020. CmdletSearch-Mailbox og Advanced eDiscovery v1.0 udgår også inden for samme tidsperiode.
ms.openlocfilehash: f778a31580bb908205c707c1f613f49bd6a576d1
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/04/2021
ms.locfileid: "63587548"
---
# <a name="retirement-of-legacy-ediscovery-tools"></a>Tilbagetrækning af ældre eDiscovery-værktøjer

> [!IMPORTANT]
> Funktionaliteten i de ældre eDiscovery-værktøjer, der er beskrevet i denne artikel, er enten blevet fjernet fra Microsoft 365-tjenesten eller er stadig tilgængelig, men understøttes ikke længere. Funktioner, der stadig er tilgængelige, kan fjernes uden varsel. Hvis du stadig bruger et af disse ældre værktøjer, skal du overveje at overføre til eDiscovery-værktøjerne i Microsoft 365 Overholdelsescenter eller et af de alternativer, der er beskrevet i denne artikel.

I løbet af årene har Microsoft leveret eDiscovery-værktøjer, der giver dig mulighed for at søge, få vist og eksportere mailindhold Exchange Online. Disse værktøjer tilbyder dog ikke længere en effektiv måde at søge efter ikke-Exchange indhold i andre Microsoft 365-tjenester, f.eks. SharePoint Online og Microsoft 365 Grupper. For at løse dette tilbyder Microsoft andre eDiscovery-værktøjer, der hjælper dig med at søge efter en lang række Microsoft 365 indhold. Og vi har arbejdet hårdt på at inkorporere den mest aktuelle og effektive eDiscovery-funktionalitet i <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a>. Dette giver organisationer mulighed for at besvare juridiske, interne og andre dokumentanmodninger om indhold på tværs af Microsoft 365, herunder Exchange Online.

Som et resultat af denne nye og forbedrede eDiscovery-funktionalitet i Microsoft 365 Overholdelsescenter tilbagetvinger vi følgende eDiscovery-relaterede funktioner og funktionalitet i forbindelse med søgning efter mailindhold i Exchange Online og Microsoft 365:

- [Direkte eDiscovery](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery) [og direkte vente hold](/exchange/security-and-compliance/create-or-remove-in-place-holds) i Exchange Administration.

- De Exchange Online PowerShell-cmdlet'er, der understøtter In-Place eDiscovery- og In-Place-ventepositioner (disse cmdlet'er identificeres samlet som **-MailboxSearch-cmdlet'er*). Dette omfatter følgende cmdlet'er:

  - [New-MailboxSearch](/powershell/module/exchange/new-mailboxsearch)

  - [Start-MailboxSearch](/powershell/module/exchange/start-mailboxsearch)

  - [Stop-MailboxSearch](/powershell/module/exchange/stop-mailboxsearch)

  - [Set-MailboxSearch](/powershell/module/exchange/set-mailboxsearch)

   > [!NOTE]
   > Cmdlet'erne [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch) og [Remove-MailboxSearch](/powershell/module/exchange/remove-mailboxsearch) vil være tilgængelige, efter de andre ****-MailboxSearch*** cmdlet'er er udgået, så du kan bruge dem til at hjælpe dig med overgangen til andre eDiscovery- og ventefunktioner. Men efter en bestemt dato (citeret nedenfor) understøtter Microsoft Support ikke længere disse to cmdlet'er.

- [Cmdlet'en](/powershell/module/exchange/search-mailbox) Søgepostkasse i Exchange Online PowerShell.

- Følgende handlinger i Exchange Web Services API:

   - [GetSearchableMailboxes](/exchange/client-developer/web-service-reference/getsearchablemailboxes-operation)

   - [SearchMailboxes](/exchange/client-developer/web-service-reference/searchmailboxes-operation)
   
   - [SetHoldOnMailboxes](/exchange/client-developer/web-service-reference/setholdonmailboxes-operation)

   - [GetHoldOnMailboxes](/exchange/client-developer/web-service-reference/getholdonmailboxes-operation)

- [Avanceret eDiscovery til Office 365 v1.0](./overview-ediscovery-20.md), som er den første version af Advanced eDiscovery, der tilgås via en Core eDiscovery-sag Microsoft 365 Overholdelsescenter. Tilbagetrækningen af Advanced eDiscovery v1.0 påvirker ikke din mulighed for at oprette og administrere kerne eDiscovery-sager.

> [!NOTE]
> EDiscovery-funktionaliteten, der fjernes, gælder kun for skybaserede versioner af Microsoft 365 og Office 365. eDiscovery-funktionalitet i lokale versioner af Exchange og SharePoint understøttes stadig indtil yderligere varsel.

De følgende afsnit i denne artikel indeholder vejledning om hver funktion, der skal udgå. Disse oplysninger, herunder tidslinjer og alternative værktøjer, som du kan bruge i stedet for det udgåede værktøj.

## <a name="in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center"></a>In-Place eDiscovery og In-Place i Exchange Administration 

I henhold til den oprindelige meddelelse d. 1. juli 2017 vil funktionen In-Place eDiscovery & Hold i Exchange Administration (EAC) udgå. Siden In-Place eDiscovery-& i EAC gav dig mulighed for at søge, holde og eksportere indhold fra Exchange Online. In-Place eDiscovery giver dig også mulighed for at kopiere søgeresultater til en postkasse med søgeresultater, så du eller andre eDiscovery-ledere kan gennemse indhold og gøre det tilgængeligt for juridiske, lovgivningsmæssige og offentlige anmodninger.

Da alle disse funktioner (bortset fra kopiering af søgeresultater til en postkasse med søgeresultater) nu er tilgængelige i indholdssøgning, eDiscovery- og Advanced eDiscovery-værktøjer i [Microsoft 365 Overholdelsescenter](./microsoft-365-compliance-center.md) (med forbedret funktionalitet, pålidelighed og understøttelse af en lang række Microsoft 365  tjenester), anbefaler vi, at du begynder at bruge disse værktøjer så hurtigt som muligt. For at hjælpe dig i overgangen til disse andre eDiscovery-værktøjer, viser tabellen nedenfor de værktøjer, du kan bruge i stedet for In-Place eDiscovery og In-Place Hold.

### <a name="scope-of-affected-organizations"></a>Omfanget af berørte organisationer

- Office 365 og Microsoft 365 Enterprise organisationer

- Office 365 og Microsoft 365 Education organisationer

- Office 365 og Microsoft 365 myndigheder; dette omfatter GCC, GCC High og DoD

- Office 365 Tyskland

### <a name="timeline-for-retirement"></a>Tidslinje til tilbagetrækning

- 1. juli 2020: Du kan ikke oprette nye søgninger og ventende filer, men du kan stadig køre, redigere og slette eksisterende søgninger på eget ansvar. Microsoft Support vil ikke længere In-Place eDiscovery & i EAC.

- 1. oktober 2020: In-Place eDiscovery-&-ventende funktioner i EAC anbringes i en skrivebeskyttet tilstand. Det betyder, at du kun kan fjerne eksisterende søgninger og ventende funktioner.

### <a name="alternative-tools"></a>Alternative værktøjer

I følgende tabel beskrives andre værktøjer, du kan bruge til at erstatte de eksisterende funktioner, der fjernes.

<table>
<thead>
<tr class="header">
<th>Funktionalitet</th>
<th>Alternativt værktøj</th>
<th>Kommentarer</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Søg, eksportér og hold det til juridiske formål</td>
<td>Centrale eDiscovery-sager i Microsoft 365 Overholdelsescenter </td>
<td><p>Ved hjælp af funktionerne i de grundlæggende eDiscovery-sager kan du sikre den funktionelle paritet In-Place eDiscovery og In-Place hold. Dette omfatter følgende:</p>
<ul>
<li>
<p>Søgeskalaer til millioner af placeringer</p>
</li>
<li>
<p>Større pålidelighed ved søgning, eksport og placering af indhold i venteposition</p>
</li>
<li>
<p>Søgning efter indhold i for Exchange Online, SharePoint Online, OneDrive for Business, Skype for Business, Microsoft Teams, Yammer Grupper Microsoft 365  Grupper og andet indhold, der er gemt i Office 365 programmer</p></li></ul>
</td>
</tr>
<tr class="even">
<td>Venteposition til opbevaringsformål</td>
<td>Opbevaringspolitikker i Microsoft 365 Overholdelsescenter</td>
<td><p>Du kan bruge Opbevaringspolitikker til at bevare indhold og, hvis det er nødvendigt, slette det, når en opbevaringsperiode udløber. Andre funktioner omfatter:</p>
<ul>
<li>
<p>Anvend politikker på hele organisationen </p>
</li><li>
<p>Anvend politikker på bestemte indholdsplaceringer, f.eks. Exchange Online, SharePoint Online, OneDrive for Business, Skype for Business, Microsoft Teams og Office 365 Grupper</p></li>
<li>
<p>Anvend politikker på bestemte brugere</p></li></ul>
<p>Få mere at vide under <a href="/microsoft-365/compliance/retention-policies"> Få mere at vide om opbevaringspolitikker og opbevaringsnavne</a>.</td>
</tr>
<tr class="odd">
<td>Kopiér søgeresultater fra en mail til en postkasse med søgeresultater til gennemsyn</td><td>Gennemse sæt i Advanced eDiscovery v2.0</td>
<td><p>Det har aldrig været nemmere Microsoft 365 at gennemgå indhold i en 2010-video. Korrektursæt har mange gode funktioner, som kan hjælpe med at reducere den mængde tid og data, der skal gennemgås, herunder:</p>
<ul>
<li><p>Udføre hurtigsøgningsforespørgsler og filtrere indhold i et korrektursæt</p></li>
<li><p>Analysér indhold i et korrektursæt. dette omfatter mailtrådning, registrering af næsten dubletter, analyse af temaer og forudsigelig kodning</p></li>
<li><p>Tag dokumenter i et korrektursæt</p></li>
<li><p>Forslag til mærkning, der hjælper med at identificere indhold i advokatklientens rettigheder</p></li></ul>
<p>Få mere at vide under <a href="/microsoft-365/compliance/overview-ediscovery-20">Oversigt over Advanced eDiscovery løsning i Microsoft 365</a>.</p>
<p>
<p>Alternativt kan du eksportere søgeresultater til PST-filer og derefter bruge tjenesten Microsoft 365 import til at importere PST'er til en postkasse med søgeresultater. Du kan finde en trinvis vejledning under Brug <a href="/microsoft-365/compliance/use-network-upload-to-import-pst-files">netværksupload til at importere PST-filer Office 365</a>.
</tr>
<tr class=even>
  <td>Kopiere meddelelser fra én postkasse til en anden postkasse</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Tildele tilladelser til en postkasse</a></td>
  <td>For at give en person adgang til en anden brugers mail (f.eks. når en medarbejder forlader organisationen, og du skal give en anden person adgang til den tidligere medarbejders mail), anbefales det, at du giver den pågældende person adgangstilladelse til den tidligere medarbejders postkasse. Så i stedet for at kopiere postkasseelementer til en anden brugerpostkasse eller en delt postkasse skal du blot tildele en bruger de nødvendige tilladelser for at få adgang til kildepostkassen.</td>
  
  </tr>
<tr class="odd">
<td>Gendan elementer fra mappen Genoprettelige elementer</td>
  <td><a href="/powershell/module/exchange/Restore-RecoverableItems">Gendan-genopretteligewebsteder</td>
  <td>Du kan gendanne permanent slettede elementer (også kaldet <i>blød-slettede</i> elementer) i postkasser, så længe opbevaringsperioden for et element ikke er udløbet. Du kan finde flere oplysninger <a href="/Exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder">i mappen Genoprettelige elementer i Exchange Online</a>.</td>
</tr>
</tbody>
</table>

### <a name="faqs-about-in-place-ediscovery-and-in-place-holds"></a>Ofte stillede spørgsmål om In-Place eDiscovery og In-Place ventende oplysninger

**Jeg bruger funktionen til kopiering af søgeresultater fra In-Place eDiscovery &-ventende funktioner i EAC til at kopiere søgeresultater til en postkasse til gennemsyn af advokater til gennemsyn. Hvilke muligheder har jeg nu?**

Der er to måder at replikere denne funktionalitet på i dag. Den første er at bruge [korrektursæt i Advanced eDiscovery v2.0](./view-documents-in-review-set.md). Korrektursæt har mange af de samme funktioner, du kan se i et traditionelt korrekturværktøj, som f.eks. hurtig søgning i dokumenter, mærkning, mailtrådning, næsten duplikerede gruppering, temaers analyse og forudsigelig kodning. Hvis du stadig vil bruge postkasser til opdagelse til gennemsyn, er den anden mulighed at eksportere søgeresultater til PST-filer og derefter importere PST-filer til en postkasse ved hjælp af [PST-importfunktionen](use-network-upload-to-import-pst-files.md) i Microsofts overholdelsescenter.

**Hvordan styrer jeg, hvilke indholdsplaceringer (f.eks. postkasser eller websteder), som en eDiscovery-leder kan søge efter med de nye værktøjer?**

Den Microsoft 365 Overholdelsescenter også [overholdelsesgrænser til at](set-up-compliance-boundaries.md) styre, hvilke indholdsplaceringer en eDiscovery-leder kan søge efter. Overholdelsesgrænser er nyttige i enheder inden for offentlige myndigheder, der skal holde sig inden for myndighedernes grænser eller for multi nationale virksomheder, der er nødvendige for at respektere geografiske tavler.

**Hvordan kan jeg flytte mine aktuelle søgninger og ventende funktioner til Microsoft 365 Overholdelsescenter?**

Det er muligt at overføre In-Place eDiscovery-søgninger og -ventepositioner fra EAC ved hjælp af PowerShell. Du kan finde en [vejledning i Overfør søgninger og ventende funktioner fra EAC til Microsoft 365 Overholdelsescenter](./migrate-legacy-ediscovery-searches-and-holds.md).

## <a name="-mailboxsearch-cmdlets"></a>\*-MailboxSearch-cmdlet'er

Som det fremgår af den oprindelige meddelelse, der blev offentliggjort d. 1. juli 2017 i Exchange Administration, udgår funktionen In-Place eDiscovery & Hold **\*og de tilsvarende Postkassesøgning-cmdlet'er**. Disse cmdlet'er giver brugerne mulighed for at søge, holde og eksportere postkasseindhold til juridiske, lovgivningsmæssige og offentlige anmodninger.

Da disse funktioner nu er tilgængelige i [<span class="underline">Microsoft 365 Overholdelsescenter</span>](./microsoft-365-compliance-center.md) og Office 365 Security & Compliance Center PowerShell med forbedret ydeevne og skalerbarhed, bør du bruge disse forbedrede cmdlet'er. Disse cmdlet'er omfatter [<span class="underline">\*-ComplianceCase</span>](/powershell/module/exchange/get-compliancecase), [<span class="underline">\*-ComplianceSearch</span>](/powershell/module/exchange/get-compliancesearch), [<span class="underline">\*-CaseHoldPolicy</span>](/powershell/module/exchange/get-caseholdpolicy), [<span class="underline">\*-CaseHoldRule</span>](/powershell/module/exchange/get-caseholdrule) og [<span class="underline">\*-ComplianceSearchAction</span>](/powershell/module/exchange/get-compliancesearchaction).

### <a name="scope-of-affected-organizations"></a>Omfanget af berørte organisationer

- Office 365 og Microsoft 365 Enterprise organisationer

- Office 365 og Microsoft 365 Education organisationer

- Office 365 og Microsoft 365 myndigheder; dette omfatter GCC, GCC High og DoD

- Office 365 Tyskland

### <a name="timeline"></a>Tidslinje

- 1. juli 2020: Du kan ikke bruge **Ny-PostkasseSøgning** til at oprette nye In-Place eDiscovery-søgninger og In-Place-ventende funktioner, men du kan stadig bruge cmdlet'er til at køre, redigere og slette eksisterende søgninger og indhold på eget ansvar. Microsoft Support yder ikke længere hjælp til disse typer af søgninger og ventende funktioner.

- 1. oktober 2020: Som tidligere nævnt anbringes funktionen In-Place eDiscovery & Hold i EAC i en skrivebeskyttet tilstand. Det betyder også, at du ikke vil kunne bruge **cmdlet'erne New-MailboxSearch**, **Start-MailboxSearch** eller **Set-MailboxSearch** . Du kan kun hente og fjerne eksisterende søgninger og ventende funktioner.

### <a name="alternative-tools"></a>Alternative værktøjer

I følgende tabel beskrives andre værktøjer, du kan bruge til at erstatte de eksisterende funktioner, der fjernes.

<table>
<thead>
<tr class="header">
<th>Funktionalitet</th>
<th>Alternative værktøjer</th>
<th>Kommentarer</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Søg og eksportér</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>Cmdlet'erne ComplianceSearch og ComplianceSearchAction arbejder sammen for at hjælpe dig med at søge og eksportere indhold. Du kan oprette en ny søgning og få vist det anslåede søgeoverslag ved hjælp af cmdlet'erne <strong>New-</strong>, <strong>Get-</strong>, and <strong>Start-ComplianceSearch</strong> . Derefter kan du bruge <strong>New-ComplianceSearchAction-cmdlet'en</strong> til at eksportere søgeresultaterne. Du skal stadig bruge det grundlæggende eDiscovery-værktøj i Microsoft 365 Overholdelsescenter til at downloade søgeresultaterne til din lokale computer.</p>
<p>
<p><strong>Bemærk!</strong> Hvis du bruger disse cmdlet'er til at oprette søgninger, der ikke er knyttet til en grundlæggende eDiscovery-sag, vil disse søgninger være placeret på <strong></strong> siden Indholdssøgning i Microsoft 365 Overholdelsescenter.</p></td>
</tr>
<tr class="even">
<td>Hold indhold i en postkasse</td>
<td><p><a href="/powershell/module/exchange/get-caseholdpolicy"><span class="underline">*-CaseHoldPolicy</span></a></p>
<p><a href="/powershell/module/exchange/get-caseholdrule"><span class="underline">*-CaseHoldrule</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-ComplianceCase</span></a></p>
<p> </p></td>
<td><p>Ventende Microsoft 365 Overholdelsescenter skal være knyttet til en ComplianceCase. Først skal du oprette overholdelsestilfældet og derefter oprette en CaseHoldPolicy og en CaseHoldRule.</p>
<p><strong>Bemærk!</strong> Oprettelse af en CaseHoldPolicy uden en oprettelse af CaseHoldRule vil gøre ventepositionen inoperabel, indtil CaseHoldRule er oprettet og knyttet til CaseHoldPolicy. Se cmdlet-dokumentationen for at få flere oplysninger.</p></td>
</tr>
<tr class="odd">
<td>Kopiér søgeresultater til en postkasse med søgeresultater</td>
<td>Ingen</td>
<td>Der findes ingen direkte erstatning for denne funktionalitet, da den ikke giver adgang til alle Microsoft 365-tjenester. Se de følgende ofte stillede spørgsmål nedenfor for at få alternative løsninger.</td>
</tr>
  <tr class=even>
  <td>Kopiere meddelelser fra én postkasse til en anden postkasse</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Tildele tilladelser til en postkasse</a></td>
  <td>For at give en person adgang til en anden brugers mail (f.eks. når en medarbejder forlader organisationen, og du skal give en anden person adgang til den tidligere medarbejders mail), anbefales det, at du giver den pågældende person adgangstilladelse til den tidligere medarbejders postkasse. Så i stedet for at kopiere postkasseelementer til en anden brugerpostkasse eller en delt postkasse, skal du blot tildele en bruger tilladelser til at få adgang til kildepostkassen.</td>
  
  </tr>

</tbody>
</table>

### <a name="faqs-about--mailboxsearch-cmdlets"></a>Ofte stillede spørgsmål om ***-MailboxSearch-cmdlet'er**

**Vi bruger Kopiér søgning til at eksportere mails eller chatbeskeder til andre formål med eDiscovery og juridiske undersøgelser. Hvilke andre muligheder har vi, når disse cmdlet'er er udgået?**

[<span class="underline">Microsofts Graph-API'er</span>](https://developer.microsoft.com/en-us/graph) leverer en række metoder til at udtrække data **\*** til analyseformål og andre formål, der er langt mere robuste og skalerbare end brugen af cmdlet'erne -MailboxSearch.

**Hvordan kan jeg overføre mine søgninger og fast hold til Microsoft 365 Overholdelsescenter?**

Det er muligt at overføre In-Place eDiscovery-søgninger og -ventepositioner fra Exchange Administration ved hjælp af et PowerShell-script. Få mere at vide under [Overfør ældre eDiscovery-søgninger og -ventende funktioner til Microsoft 365 Overholdelsescenter](migrate-legacy-eDiscovery-searches-and-holds.md).

**Når cmdletterne er udgået, kan jeg så stadig fjerne eller hente søgninger?**

Ja, selvom vi fjerner muligheden for at oprette og redigere søgninger, kan du stadig bruge **Get-MailboxSearch** og **Remove-MailboxSearch** indtil yderligere varsel. Brugen af disse cmdlet'er er dog på eget ansvar efter tilbagetrækningsdatoen, og Microsoft Support vil ikke længere kunne give hjælp.

## <a name="search-mailbox-cmdlet"></a>Search-Mailbox cmdlet

**Cmdlet'en** Søgepostkasse i Exchange Online PowerShell udgår som oprindeligt annonceret i en advarsel i cmdlet-outputtet fra og med 2018. **Cmdlet'en** Søgepostkasse blev oprindeligt brugt til at søge i en brugers postkasse og fjerne skadeligt indhold. Vi anbefaler, at du begynder at bruge **New-ComplianceSearch** og **New-ComplianceSearchAction-cmdlet'er** i Office 365 Security & Compliance Center PowerShell til at søge efter og fjerne indhold. For en indbygget sikkerhedsoplevelse giver [<span class="underline">sikkerhedsfunktionerne Microsoft 365</span>](../security/index.yml) robust trusselsbeskyttelse til mail og mange andre Microsoft-tjenester.

### <a name="scope-of-affected-organizations"></a>Omfanget af berørte organisationer

- Office 365 og Microsoft 365 Enterprise organisationer

- Office 365 og Microsoft 365 Education organisationer

- Office 365 og Microsoft 365 myndigheder; dette omfatter GCC, GCC High og DoD

- Office 365 Tyskland

### <a name="timeline"></a>Tidslinje

-  1. juli 2020 **:** Cmdlet'en Søgepostkasse er ikke længere tilgængelig, og Microsoft Support yder ikke længere hjælp.

### <a name="alternative-tools"></a>Alternative værktøjer

I følgende tabel beskrives andre værktøjer, du kan bruge til at erstatte de eksisterende funktioner, der fjernes.

<table>
<thead>
<tr class="header">
<th>Funktionalitet</th>
<th>Alternative værktøjer</th>
<th>Kommentarer</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Søg i en postkasse</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></a></p></td>
<td><p>Cmdlet'erne ComplianceSearch og ComplianceSearchAction arbejder sammen for at hjælpe dig med at søge og eksportere indhold. Du kan oprette en ny søgning og få vist det anslåede søgeoverslag ved hjælp af cmdlet'erne <strong>New-</strong>, <strong>Get-</strong>, and <strong>Start-ComplianceSearch</strong> . Derefter kan du bruge <strong>kommandoen New-ComplianceSearchAction -Export</strong> til at eksportere søgeresultaterne. Du skal stadig bruge det grundlæggende eDiscovery-værktøj i Microsoft 365 Overholdelsescenter til at downloade søgeresultaterne til din lokale computer.</p></p>
</td>
</tr>
<tr class="even">
<td>Slet massemails fra en postkasse</td>
<td><p><a href="/microsoft-365/compliance/set-up-an-archive-and-deletion-policy-for-mailboxes"><span class="underline">Konfigurere en arkiverings- og sletningspolitik for postkasser</span></a></p>
<p></p></td>
<td><p>Administratorer kan oprette en arkiverings- og sletningspolitik, der automatisk flytter elementer til en brugers arkivpostkasse og automatisk sletter elementer fra postkassen.</p>
</td>
</tr>
<tr class="even">
<td>Kopiér søgeresultater til en postkasse med søgeresultater</td>
<td> </td>
<td>Der findes ingen direkte erstatning for denne funktionalitet, da den ikke giver adgang til alle Microsoft 365-tjenester. Se ofte stillede spørgsmål i afsnittet <strong>*-MailboxSearch cmdlet'er</strong> for alternative løsninger. </td>
</tr>
<tr class=odd>
  <td>Kopiere meddelelser fra én postkasse til en anden postkasse</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Tildele tilladelser til en postkasse</a></td>
  <td>For at give en person adgang til en anden brugers mail (f.eks. når en medarbejder forlader organisationen, og du skal give en anden person adgang til den tidligere medarbejders mail), anbefales det, at du giver den pågældende person adgangstilladelse til den tidligere medarbejders postkasse. Så i stedet for at kopiere postkasseelementer til en anden brugerpostkasse eller en delt postkasse, skal du blot tildele en bruger tilladelse til at få adgang til kildepostkassen.</td>
</tr>
<tr class=even>
  <td>Tøm meddelelser fra en postkasse</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></p></td>
<td><p>Cmdlet'erne ComplianceSearch og ComplianceSearchAction arbejder sammen for at hjælpe dig med at søge efter og fjerne indhold. Du kan oprette og køre en søgning med Cmdlet'er <strong>New-ComplianceSearch</strong> og <strong>New-ComplianceSearch</strong> , og derefter kan du fjerne indholdet ved hjælp af <strong>kommandoen New-ComplianceSearchAction -Purge -PurgeType</strong> . Få mere at vide under <a href="/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization"><span class="underline">Søg efter og slet meddelelser</span></a>.</p>
</td>
</tr>
<tr class="odd"> 
<td>Tøm meddelelser fra en postkasse</td>
<td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Tildele tilladelser til en postkasse</a></td>
<td>Hvis du vil fjerne meddelelser fra en postkasse, skal du tildele en administratortilladelser til at få adgang til medarbejderens postkasse. Meddelelser kan slettes og genbruges efter behov og drage fordel af de indbyggede søge- og visningsfunktioner i Outlook.</td>
</tr>
</tbody>
</table>

## <a name="exchange-web-services-api-operations"></a>Exchange WEB Services API-handlinger

Disse handlinger i Exchange Web Services API'en bruges af funktionen In-Place eDiscovery & Ventepositioner i Exchange Administration og de tilsvarende -MailboxSearch-cmdlet'er i Exchange Online PowerShell.**\*** De vil også udgå som en del af at udgå de andre ældre eDiscovery-værktøjer.

### <a name="scope-of-affected-organizations"></a>Omfanget af berørte organisationer

- Office 365 og Microsoft 365 Enterprise organisationer

- Office 365 og Microsoft 365 Education organisationer

- Office 365 og Microsoft 365 myndigheder; dette omfatter GCC, GCC High og DoD

- Office 365 Tyskland

### <a name="timeline"></a>Tidslinje

- 1. juli 2020: Handlingerne GetSearchableMailboxes, SearchMailboxes, SetHoldOnMailboxes og GetHoldOnMailboxes vil ikke længere være tilgængelige, og Microsoft Support yder ikke længere hjælp.

## <a name="advanced-ediscovery-v10"></a>Advanced eDiscovery v1.0

Advanced eDiscovery v1.0, som er den version af Advanced eDiscovery, der er tilgængelig i en grundlæggende eDiscovery-sag ved at klikke på Skift til **Advanced eDiscovery**, fjernes. Dens funktionalitet er blevet erstattet af den [nye Advanced eDiscovery løsning i](./ediscovery.md) Microsoft 365 Overholdelsescenter.

Sådan finder du ud af, om din organisation bruger Advanced eDiscovery v1.0:

1. Gå til Microsoft 365 Overholdelsescenter, vælg **eDiscoveryCore** > , og åbn en Core eDiscovery-sag.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank"></a>

1. Hvis du kan se knappen **Skift til Advanced eDiscovery**, og du derefter klikker på den, kommer du til 1.0-versionen af Advanced eDiscovery, som udgås. Muligheden for at oprette og administrere sager i Core eDiscovery påvirkes ikke. Kun muligheden for at tilføje og analysere sagsdata i Advanced eDiscovery v1.0 (ved at klikke på Skift til **Advanced eDiscovery**) udgå.

Den nye Advanced eDiscovery-løsning i Microsoft 365 (også kaldet *Advanced eDiscovery v2.0*) indeholder alle funktionerne fra den oprindelige løsning, men omfatter nu en indstillingsbaseret metode til at identificere indhold i andre Microsoft 365  tjenester, indsamling af indhold og derefter tilføjelse af det til et korrektursæt, hvor korrekturlæsere kan benytte hurtig søgeforespørgsler, mærkning og analysefunktioner til at hjælpe med at udsortere relevante dokumenter. Advanced eDiscovery omfatter nu forbedret behandling og oprindelige fremvisere til både Microsoft- og ikke-Microsoft-filtyper, en komplet liste over filtyper er [](./supported-filetypes-ediscovery20.md) her, og understøttede metadatafelter er [her](./document-metadata-fields-in-advanced-ediscovery.md). Desuden indeholder den nye Advanced eDiscovery-løsning en effektiv, øverlig kontrolfunktion, der gør det muligt at anvende ventende funktioner til indhold i forskellige tjenester, underrette brugere af ventende funktioner og registrere svar, der er af en leder, alt sammen i en Advanced eDiscovery-sag.

Sådan får du Advanced eDiscovery v2.0:

Gå til fanen Microsoft 365 Overholdelsescenter, vælg **eDiscoveryAdvanced** > , og åbn en Core eDiscovery-sag.<a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank"></a>

På nuværende tidspunkt anbefaler vi, at du begynder at overgå din eDiscovery-arbejdsproces til den nye Advanced eDiscovery funktionalitet. Hvis det er nødvendigt, kan du arkivere Advanced eDiscovery 1.0-tilfælde ved at eksportere indholdet og gemme det offline. Selvom du stadig kan få adgang til Advanced eDiscovery v1.0 i eksisterende tilfælde indtil d. 31. december 2020, yder Microsoft Support ikke support efter den 1. oktober 2020. Se følgende tidslinje for at få mere at vide.

### <a name="scope-of-affected-organizations"></a>Omfanget af berørte organisationer

- Office 365 og Microsoft 365 Enterprise organisationer

- Office 365 og Microsoft 365 Education organisationer

- Office 365 og Microsoft 365 myndigheder; dette omfatter GCC, GCC High og DoD

- Office 365 Tyskland

### <a name="timeline"></a>Tidslinje

- 1. juli 2020: Du kan ikke oprette nye Advanced eDiscovery v1.0-sager.

- 1. oktober 2020: Du vil ikke kunne tilføje nye data (Forbered søgeresultater for Advanced eDiscovery) til eventuelle tilfælde. Du kan fortsætte med at arbejde med data i eksisterende tilfælde på eget ansvar. Microsoft Support yder ikke længere hjælp. 

- 31. december 2020: Du kan ikke få adgang til alle Advanced eDiscovery v1.0.

### <a name="alternative-tools"></a>Alternative værktøjer

Den [Advanced eDiscovery løsning](./overview-ediscovery-20.md) i Microsoft 365 Overholdelsescenter.