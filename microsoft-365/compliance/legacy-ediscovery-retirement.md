---
title: Ældre eDiscovery-værktøjer er udgået
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
description: In-Place eDiscovery og In-Place Venteposition (og de tilsvarende PowerShell-cmdlet'er) i Exchange Online udgår i første halvdel af 2020. Den Search-Mailbox cmdlet og Microsoft Purview eDiscovery (Premium) v1.0 udgår også inden for samme tidsperiode.
ms.openlocfilehash: 630d72c75f318e6d4f9e68b01c61d5069958a0a1
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636067"
---
# <a name="retirement-of-legacy-ediscovery-tools"></a>Ophør af ældre eDiscovery-værktøjer

> [!IMPORTANT]
> Funktionaliteten af de ældre eDiscovery-værktøjer, der er beskrevet i denne artikel, er enten fjernet fra Microsoft 365-tjenesten eller er stadig tilgængelig, men understøttes ikke længere. Alle funktioner, der stadig er tilgængelige, kan fjernes uden varsel. Hvis du stadig bruger nogle af disse ældre værktøjer, kan du overveje at migrere til eDiscovery-værktøjerne i Microsoft Purview-compliance-portal eller et af de alternativer, der er beskrevet i denne artikel.

Microsoft har gennem årene leveret eDiscovery-værktøjer, som du kan bruge til at søge efter, få vist og eksportere mailindhold fra Exchange Online. Disse værktøjer tilbyder dog ikke længere en effektiv måde at søge efter indhold, der ikke er Exchange, i andre Microsoft 365-tjenester, f.eks. SharePoint Online og Microsoft 365-grupper. For at løse dette har Microsoft andre eDiscovery-værktøjer, der hjælper dig med at søge efter en lang række Microsoft 365-indhold. Og vi har arbejdet hårdt på at inkorporere den mest aktuelle og effektive eDiscovery-funktionalitet på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">overholdelsesportalen</a>. Dette giver organisationer mulighed for at besvare juridiske, interne og andre dokumentanmodninger om indhold på tværs af mange Microsoft 365-tjenester, herunder Exchange Online.

Som et resultat af denne nye og forbedrede eDiscovery-funktionalitet på overholdelsesportalen udfaser vi følgende eDiscovery-relaterede funktioner og funktioner, der er relateret til søgning efter mailindhold i Exchange Online og Microsoft 365:

- [direkte eDiscovery](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery) og [ventepositioner på stedet](/exchange/security-and-compliance/create-or-remove-in-place-holds) i Exchange Administration.

- De Exchange Online PowerShell-cmdlet'er, der understøtter In-Place eDiscovery og In-Place Ventepositioner (disse cmdlet'er identificeres samlet som **-MailboxSearch-cmdlet'er*). Dette omfatter følgende cmdlet'er:

  - [New-MailboxSearch](/powershell/module/exchange/new-mailboxsearch)

  - [Start-MailboxSearch](/powershell/module/exchange/start-mailboxsearch)

  - [Stop-MailboxSearch](/powershell/module/exchange/stop-mailboxsearch)

  - [Set-MailboxSearch](/powershell/module/exchange/set-mailboxsearch)

   > [!NOTE]
   > Cmdlet'erne [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch) og [Remove-MailboxSearch](/powershell/module/exchange/remove-mailboxsearch) vil være tilgængelige, når de andre ****-MailboxSearch*** cmdlet'er udgår, så du kan bruge dem som en hjælp i overgangen til andre eDiscovery- og værktøjer i venteposition. Men efter en bestemt dato (nævnt nedenfor) understøtter Microsoft Support ikke længere disse to cmdlet'er.

- Search-Mailbox-cmdlet'en i Exchange Online PowerShell.[](/powershell/module/exchange/search-mailbox)

- Følgende handlinger i Exchange Web Services-API'en:

   - [GetSearchableMailboxes](/exchange/client-developer/web-service-reference/getsearchablemailboxes-operation)

   - [SearchMailboxes](/exchange/client-developer/web-service-reference/searchmailboxes-operation)
   
   - [AngivHoldOnMailboxes](/exchange/client-developer/web-service-reference/setholdonmailboxes-operation)

   - [GetHoldOnMailboxes](/exchange/client-developer/web-service-reference/getholdonmailboxes-operation)

- [Microsoft Purview eDiscovery (Premium) v1.0](./overview-ediscovery-20.md), som er den første version af eDiscovery (Premium), der tilgås via en Microsoft Purview eDiscovery (Standard) sag i overholdelsesportalen. Udfasning af eDiscovery (Premium) v1.0 påvirker ikke din mulighed for at oprette og administrere eDiscovery-sager (Standard).

> [!NOTE]
> EDiscovery-funktionaliteten, der udgår, gælder kun for cloudbaserede versioner af Microsoft 365 og Office 365. eDiscovery-funktionalitet i lokale versioner af Exchange og SharePoint understøttes stadig indtil videre.

Følgende afsnit i denne artikel indeholder en vejledning om hver funktion, der udgår. Disse oplysninger, herunder tidslinjer og alternative værktøjer, som du kan bruge i stedet for det udgåede værktøj.

## <a name="in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center"></a>In-Place eDiscovery og In-Place ventepositioner i Exchange Administration 

I henhold til den oprindelige meddelelse den 1. juli 2017 udgår funktionen In-Place eDiscovery & Venteposition i Exchange Administration (EAC). Siden In-Place eDiscovery-& ventepositioner i EAC gav dig mulighed for at søge efter, holde og eksportere indhold fra Exchange Online. In-Place eDiscovery kan du også kopiere søgeresultater til en registreringspostkasse, så du eller andre eDiscovery-ledere kan gennemse indhold og gøre det tilgængeligt for juridiske, lovmæssige og offentlige anmodninger.

Da alle disse funktioner (undtagen kopiering af søgeresultater til en registreringspostkasse) nu er tilgængelige i værktøjerne til indholdssøgning, eDiscovery og eDiscovery (Premium) på [overholdelsesportalen](./microsoft-365-compliance-center.md) (med forbedret funktionalitet, pålidelighed og understøttelse af en lang række Microsoft 365-tjenester), anbefaler vi, at du begynder at bruge disse værktøjer hurtigst muligt. For at hjælpe dig med overgangen til disse andre eDiscovery-værktøjer vises de værktøjer, du kan bruge i stedet for In-Place eDiscovery og In-Place Venteposition, i tabellen nedenfor.

### <a name="scope-of-affected-organizations"></a>Omfanget af berørte organisationer

- organisationer med Office 365 og Microsoft 365 Enterprise

- Office 365 og Microsoft 365 Education organisationer

- Office 365 og Microsoft 365 Government-organisationer. Dette omfatter GCC, GCC High og DoD

- Office 365 Tyskland

### <a name="timeline-for-retirement"></a>Tidslinje for tilbagetrækning

- 1. juli 2020: Du kan ikke oprette nye søgninger og ventepositioner, men du kan stadig køre, redigere og slette eksisterende søgninger på egen risiko. Microsoft Support vil ikke længere In-Place eDiscovery & Ventepositioner i EAC.

- 1. oktober 2020: Funktionen In-Place eDiscovery & Ventepositioner i EAC placeres i skrivebeskyttet tilstand. Det betyder, at du kun kan fjerne eksisterende søgninger og ventepositioner.

### <a name="alternative-tools"></a>Alternative værktøjer

I følgende tabel beskrives andre værktøjer, som du kan bruge til at erstatte den eksisterende funktionalitet, der udgår.

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
<td>Søg, eksportér og sæt i venteposition til juridiske formål</td>
<td>eDiscovery-sager (Standard) på overholdelsesportalen </td>
<td><p>Brug af funktionerne i eDiscovery-sager (Standard) giver den funktionelle paritet til at In-Place eDiscovery og In-Place Ventepositioner. Dette omfatter følgende:</p>
<ul>
<li>
<p>Søg skalerer til millioner af placeringer</p>
</li>
<li>
<p>Højere pålidelighed ved søgning, eksport og placering af indhold i venteposition</p>
</li>
<li>
<p>Søgning efter indhold i efter Exchange Online, SharePoint Online, OneDrive for Business, Skype for Business, Microsoft Teams, Yammer-grupper, Microsoft 365-grupper og andet indhold, der er gemt i Office 365 programmer</p></li></ul>
</td>
</tr>
<tr class="even">
<td>Venteposition til opbevaringsformål</td>
<td>Opbevaringspolitikker på overholdelsesportalen</td>
<td><p>Du kan bruge opbevaringspolitikker til at bevare indhold og, hvis det er nødvendigt, slette det, når opbevaringsperioden udløber. Andre funktioner omfatter:</p>
<ul>
<li>
<p>Anvendelse af politikker på hele organisationen </p>
</li><li>
<p>Anvendelse af politikker på bestemte indholdsplaceringer, f.eks. Exchange Online, SharePoint Online, OneDrive for Business, Skype for Business, Microsoft Teams og Office 365 grupper</p></li>
<li>
<p>Anvendelse af politikker på bestemte brugere</p></li></ul>
<p>Du kan finde flere oplysninger under <a href="/microsoft-365/compliance/retention-policies"> Få mere at vide om opbevaringspolitikker og opbevaringsmærkater</a>.</td>
</tr>
<tr class="odd">
<td>Kopiér søgeresultater for mail til en registreringspostkasse til gennemsyn</td><td>Korrektursæt i eDiscovery (Premium) v2.0</td>
<td><p>Det har aldrig været nemmere at gennemse indhold i Microsoft 365. Korrektursæt har mange fantastiske funktioner, der kan hjælpe med at reducere den mængde tid og de data, der skal bruges til gennemsyn, herunder:</p>
<ul>
<li><p>Udfør forespørgsler til hurtig søgning, og filtrer indhold i et korrektursæt</p></li>
<li><p>Analysér indhold i et korrektursæt. Dette omfatter mailtrådning, registrering af næsten dubletter, analyse af temaer og forudsigende kodning</p></li>
<li><p>Markér dokumenter i et valideringssæt</p></li>
<li><p>Mærkningsforslag, der kan hjælpe med at identificere indhold om advokatklientrettigheder</p></li></ul>
<p>Du kan finde flere oplysninger under <a href="/microsoft-365/compliance/overview-ediscovery-20">Oversigt over eDiscovery(Premium)-løsningen i Microsoft 365</a>.</p>
<p>
<p>Du kan også eksportere søgeresultater til PST-filer og derefter bruge Microsoft 365-importtjenesten til at importere psts til en registreringspostkasse. Du kan få en trinvis vejledning under <a href="/microsoft-365/compliance/use-network-upload-to-import-pst-files">Brug netværksupload til at importere PST-filer til Office 365</a>.
</tr>
<tr class=even>
  <td>Kopiér meddelelser fra én postkasse til en anden postkasse</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Tildel tilladelser til en postkasse</a></td>
  <td>Hvis du vil give en person adgang til en anden brugers mail (f.eks. når en medarbejder forlader organisationen, og du skal give en anden person adgang til den tidligere medarbejders mail), anbefaler vi, at du tildeler personen tilladelser til at få adgang til den tidligere medarbejders postkasse. Så i stedet for at kopiere postkasseelementer til en anden brugerpostkasse eller en delt postkasse skal du blot tildele en bruger de tilladelser, der er nødvendige for at få adgang til kildepostkassen.</td>
  
  </tr>
<tr class="odd">
<td>Gendan elementer fra mappen Gendan elementer, der kan gendannes</td>
  <td><a href="/powershell/module/exchange/Restore-RecoverableItems">Restore-RecoverableItems</td>
  <td>Du kan gendanne permanent slettede elementer (også kaldet <i>elementer med blød sletning</i> ) i postkasser, så længe opbevaringsperioden for slettede elementer for et element ikke er udløbet. Du kan finde flere oplysninger <a href="/Exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder">i mappen Elementer, der kan gendannes i Exchange Online</a>.</td>
</tr>
</tbody>
</table>

### <a name="faqs-about-in-place-ediscovery-and-in-place-holds"></a>Ofte stillede spørgsmål om In-Place eDiscovery- og In-Place ventepositioner

**Jeg bruger funktionaliteten til kopiering af søgeresultater i In-Place eDiscovery & Ventepositioner i EAC til at kopiere søgeresultater til en registreringspostkasse til gennemsyn af advokater. Hvilke muligheder har jeg nu?**

Der er to måder at replikere denne funktionalitet på i dag. Den første er at bruge [korrektursæt i eDiscovery (Premium) v2.0](./view-documents-in-review-set.md). Korrektursæt har mange af de samme funktioner, som du kan se i et traditionelt korrekturværktøj, f.eks. hurtig søgning efter dokumenter, mærkning, mailtrådning, næsten duplikeret gruppering, temaanalyse og forudsigende kodning. Hvis du stadig vil bruge registreringspostkasser til gennemsyn, er den anden mulighed at eksportere søgeresultater til PST-filer og derefter importere PST-filerne til en registreringspostkasse ved hjælp af [funktionen PST-import](use-network-upload-to-import-pst-files.md) i Microsoft Compliance Center.

**Hvordan gør jeg styre, hvilke indholdsplaceringer (f.eks. postkasser eller websteder), som en eDiscovery-leder kan søge i ved hjælp af de nye værktøjer?**

Overholdelsesportalen bruger også [overholdelsesgrænser](set-up-compliance-boundaries.md) til at styre, hvilke indholdsplaceringer en eDiscovery Manager kan søge efter. Overholdelsesgrænser er nyttige i offentlige enheder, der har brug for at holde sig inden for agenturgrænser eller multinationale selskaber, der er nødvendige for at respektere geografiske bestyrelser.

**Hvordan kan jeg flytte mine aktuelle søgninger og ventepositioner til Microsoft Purview-compliance-portal?**

Det er muligt at overføre In-Place eDiscovery-søgninger og ventepositioner fra EAC ved hjælp af PowerShell. Du kan finde instruktioner under [Overfør søgninger og ventepositioner fra EAC til overholdelsesportalen](./migrate-legacy-ediscovery-searches-and-holds.md).

## <a name="-mailboxsearch-cmdlets"></a>\*-MailboxSearch-cmdlet'er

I henhold til den oprindelige meddelelse, der blev annonceret den 1. juli 2017 i Exchange Administration, udgår funktionaliteten In-Place eDiscovery & Venteposition og de tilsvarende **\*-MailboxSearch-cmdlet'er** . Disse cmdlet'er giver brugerne mulighed for at søge efter, holde og eksportere postkasseindhold efter juridiske, lovmæssige og offentlige anmodninger.

Da disse funktioner nu er tilgængelige i [<span class="underline">overholdelsesportalen</span>](./microsoft-365-compliance-center.md) og Office 365 Security & Compliance PowerShell med forbedret ydeevne og skalerbarhed, bør du bruge disse forbedrede cmdlet'er. Disse cmdlet'er omfatter [<span class="underline">\*-ComplianceCase</span>](/powershell/module/exchange/get-compliancecase), [<span class="underline">\*-ComplianceSearch</span>](/powershell/module/exchange/get-compliancesearch), [<span class="underline">\*-CaseHoldPolicy</span>](/powershell/module/exchange/get-caseholdpolicy), [<span class="underline">\*-CaseHoldRule</span>](/powershell/module/exchange/get-caseholdrule) og [<span class="underline">\*-ComplianceSearchAction</span>](/powershell/module/exchange/get-compliancesearchaction).

### <a name="scope-of-affected-organizations"></a>Omfanget af berørte organisationer

- organisationer med Office 365 og Microsoft 365 Enterprise

- Office 365 og Microsoft 365 Education organisationer

- Office 365 og Microsoft 365 Government-organisationer. Dette omfatter GCC, GCC High og DoD

- Office 365 Tyskland

### <a name="timeline"></a>Tidslinjen

- 1. juli 2020: Du kan ikke bruge **New-MailboxSearch** til at oprette nye In-Place eDiscovery-søgninger og In-Place Ventepositioner, men du kan stadig bruge cmdlet'er til at køre, redigere og slette eksisterende søgninger og ventepositioner på egen risiko. Microsoft Support yder ikke længere hjælp til disse typer søgninger og ventepositioner.

- 1. oktober 2020: Som tidligere angivet vil funktionen In-Place eDiscovery & Ventepositioner i EAC blive sat i skrivebeskyttet tilstand. Det betyder også, at du ikke kan bruge cmdlet'erne **New-MailboxSearch**, **Start-MailboxSearch** eller **Set-MailboxSearch** . Du kan kun hente og fjerne eksisterende søgninger og ventepositioner.

### <a name="alternative-tools"></a>Alternative værktøjer

I følgende tabel beskrives andre værktøjer, som du kan bruge til at erstatte den eksisterende funktionalitet, der udgår.

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
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-Overholdelsescase</span></a></p>
<p> </p></td>
<td><p>ComplianceSearch- og ComplianceSearchAction-cmdlet'erne arbejder sammen for at hjælpe dig med at søge efter og eksportere indhold. Du kan oprette en ny søgning og få vist søgeestimatet ved hjælp af cmdlet'erne <strong>New-</strong>, <strong>Get-og</strong> <strong>Start-ComplianceSearch</strong> . Derefter kan du bruge Cmdlet'en <strong>New-ComplianceSearchAction</strong> til at eksportere søgeresultaterne. Du skal stadig bruge værktøjet eDiscovery (Standard) på overholdelsesportalen til at downloade disse søgeresultater til din lokale computer.</p>
<p>
<p><strong>Bemærk:</strong> Hvis du bruger disse cmdlet'er til at oprette søgninger, der ikke er knyttet til en eDiscovery-sag (Standard), vil disse søgninger være placeret på siden <strong>indholdssøgning</strong> på overholdelsesportalen.</p></td>
</tr>
<tr class="even">
<td>Hold indhold i en postkasse</td>
<td><p><a href="/powershell/module/exchange/get-caseholdpolicy"><span class="underline">*-CaseHoldPolicy</span></a></p>
<p><a href="/powershell/module/exchange/get-caseholdrule"><span class="underline">*-CaseHoldRule</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancecase"><span class="underline">*-Overholdelsescase</span></a></p>
<p> </p></td>
<td><p>Ventepositioner på overholdelsesportalen skal være knyttet til en Overholdelsescase. Først skal du oprette overholdelsessagen og derefter oprette en CaseHoldPolicy og en CaseHoldRule.</p>
<p><strong>Bemærk:</strong> Oprettelse af en CaseHoldPolicy uden at oprette CaseHoldRule vil gøre ventepositionen inoperabel, indtil CaseHoldRule oprettes og knyttes til CaseHoldPolicy. Du kan få flere oplysninger i dokumentationen til cmdlet'en.</p></td>
</tr>
<tr class="odd">
<td>Kopiér søgeresultater til en registreringspostkasse</td>
<td>Ingen</td>
<td>Der er ingen direkte erstatning for denne funktionalitet, fordi den ikke giver adgang til alle Microsoft 365-tjenester. Se følgende ofte stillede spørgsmål nedenfor for at få alternative løsninger.</td>
</tr>
  <tr class=even>
  <td>Kopiér meddelelser fra én postkasse til en anden postkasse</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Tildel tilladelser til en postkasse</a></td>
  <td>Hvis du vil give en person adgang til en anden brugers mail (f.eks. når en medarbejder forlader organisationen, og du skal give en anden person adgang til den tidligere medarbejders mail), anbefaler vi, at du tildeler personen tilladelser til at få adgang til den tidligere medarbejders postkasse. Så i stedet for at kopiere postkasseelementer til en anden brugerpostkasse eller en delt postkasse skal du blot tildele en bruger tilladelser for at få adgang til kildepostkassen.</td>
  
  </tr>

</tbody>
</table>

### <a name="faqs-about--mailboxsearch-cmdlets"></a>Ofte stillede spørgsmål om ***-MailboxSearch-cmdlet'er**

**Vi bruger Kopiér søgning til at eksportere mails eller chatbeskeder til andre eDiscovery- og juridiske undersøgelser. Hvilke andre muligheder har vi efter disse cmdlet'er er gået på pension?**

[<span class="underline">Microsoft Graph-API'erne</span>](https://developer.microsoft.com/en-us/graph) indeholder en række metoder til udtrækning af data til analyse og andre formål, der er langt mere robuste og skalerbare end brugen af **\*-MailboxSearch-cmdlet'erne**.

**Hvordan kan jeg overføre mine søgninger og ventepositioner til overholdelsesportalen?**

Det er muligt at overføre In-Place eDiscovery-søgninger og ventepositioner fra Exchange Administration ved hjælp af et PowerShell-script. Du kan finde flere oplysninger under [Overfør ældre eDiscovery-søgninger og ventepositioner til overholdelsesportalen](migrate-legacy-eDiscovery-searches-and-holds.md).

**Når cmdlet'erne er udgået, kan jeg så stadig fjerne eller hente søgninger?**

Ja, selvom vi fjerner muligheden for at oprette og redigere søgninger, kan du stadig bruge **Get-MailboxSearch** og **Remove-MailboxSearch** indtil videre. Brugen af disse cmdlet'er er dog på eget ansvar efter udfasningsdatoerne, og Microsoft Support vil ikke længere være i stand til at yde hjælp.

## <a name="search-mailbox-cmdlet"></a>Search-Mailbox cmdlet

**Search-Mailbox-cmdlet'en** i Exchange Online PowerShell udgår som oprindeligt annonceret i en advarsel i cmdlet-outputtet fra 2018. **Search-Mailbox-cmdlet'en** blev oprindeligt brugt til at søge i en brugers postkasse og fjerne skadeligt indhold. Vi anbefaler, at du begynder at bruge **New-ComplianceSearch**- og **New-ComplianceSearchAction-cmdlet'erne** i Office 365 Security & Compliance PowerShell til at søge efter og fjerne indhold. Microsoft [<span class="underline">365-sikkerhedsfunktionerne</span>](../security/index.yml) giver robust trusselsbeskyttelse til mail og mange andre Microsoft-tjenester for at få en indbygget sikkerhedsoplevelse.

### <a name="scope-of-affected-organizations"></a>Omfanget af berørte organisationer

- organisationer med Office 365 og Microsoft 365 Enterprise

- Office 365 og Microsoft 365 Education organisationer

- Office 365 og Microsoft 365 Government-organisationer. Dette omfatter GCC, GCC High og DoD

- Office 365 Tyskland

### <a name="timeline"></a>Tidslinjen

-  1. juli 2020: **Søgepostkasse-cmdlet'en** vil ikke længere være tilgængelig, og Microsoft Support yder ikke længere hjælp.

### <a name="alternative-tools"></a>Alternative værktøjer

I følgende tabel beskrives andre værktøjer, som du kan bruge til at erstatte den eksisterende funktionalitet, der udgår.

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
<td><p>ComplianceSearch- og ComplianceSearchAction-cmdlet'erne arbejder sammen for at hjælpe dig med at søge efter og eksportere indhold. Du kan oprette en ny søgning og få vist søgeestimatet ved hjælp af cmdlet'erne <strong>New-</strong>, <strong>Get-og</strong> <strong>Start-ComplianceSearch</strong> . Du kan derefter bruge kommandoen <strong>New-ComplianceSearchAction -Export</strong> til at eksportere søgeresultaterne. Du skal stadig bruge værktøjet eDiscovery (Standard) på overholdelsesportalen til at downloade disse søgeresultater til din lokale computer.</p></p>
</td>
</tr>
<tr class="even">
<td>Slet massemail fra en postkasse</td>
<td><p><a href="/microsoft-365/compliance/set-up-an-archive-and-deletion-policy-for-mailboxes"><span class="underline">Konfigurer en politik for arkiv og sletning for postkasser</span></a></p>
<p></p></td>
<td><p>Administratorer kan oprette en politik for arkivering og sletning, der automatisk flytter elementer til en brugers arkivpostkasse og automatisk sletter elementer fra postkassen.</p>
</td>
</tr>
<tr class="even">
<td>Kopiér søgeresultater til en registreringspostkasse</td>
<td> </td>
<td>Der er ingen direkte erstatning for denne funktionalitet, fordi den ikke giver adgang til alle Microsoft 365-tjenester. Se ofte stillede spørgsmål i afsnittet <strong>*-MailboxSearch-cmdlet'er</strong> for at få alternative løsninger. </td>
</tr>
<tr class=odd>
  <td>Kopiér meddelelser fra én postkasse til en anden postkasse</td>
  <td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Tildel tilladelser til en postkasse</a></td>
  <td>Hvis du vil give en person adgang til en anden brugers mail (f.eks. når en medarbejder forlader organisationen, og du skal give en anden person adgang til den tidligere medarbejders mail), anbefaler vi, at du tildeler personen tilladelser til at få adgang til den tidligere medarbejders postkasse. Så i stedet for at kopiere postkasseelementer til en anden brugerpostkasse eller en delt postkasse skal du blot tildele en bruger tilladelse til at få adgang til kildepostkassen.</td>
</tr>
<tr class=even>
  <td>Fjern meddelelser fra en postkasse</td>
<td><p><a href="/powershell/module/exchange/get-compliancesearch"><span class="underline">*-ComplianceSearch</span></a></p>
<p><a href="/powershell/module/exchange/get-compliancesearchaction"><span class="underline">*-ComplianceSearchAction</span></a></p>
<p></p></td>
<td><p>Cmdlet'erne ComplianceSearch og ComplianceSearchAction arbejder sammen for at hjælpe dig med at søge efter og fjerne indhold. Du kan oprette og køre en søgning med <strong>New-ComplianceSearch</strong> - og <strong>New-ComplianceSearch-cmdlet'er</strong> , og derefter kan du fjerne indholdet ved hjælp af kommandoen <strong>New-ComplianceSearchAction -Purge -PurgeType</strong> . Du kan finde flere oplysninger under <a href="/microsoft-365/compliance/search-for-and-delete-messages-in-your-organization"><span class="underline">Søg efter og slet meddelelser</span></a>.</p>
</td>
</tr>
<tr class="odd"> 
<td>Fjern meddelelser fra en postkasse</td>
<td><a href="/exchange/recipients-in-exchange-online/manage-permissions-for-recipients">Tildel tilladelser til en postkasse</a></td>
<td>Hvis du vil fjerne meddelelser fra en postkasse, skal du tildele en administrator tilladelser til at få adgang til medarbejderens postkasse. Meddelelser kan slettes og genbruges efter behov ved hjælp af de indbyggede søge- og visningsfunktioner i Outlook.</td>
</tr>
</tbody>
</table>

## <a name="exchange-web-services-api-operations"></a>Exchange Web Services API-handlinger

Disse handlinger i Exchange Web Services-API'en bruges af funktionen In-Place eDiscovery & Ventepositioner i Exchange Administration og de tilsvarende **\*-MailboxSearch-cmdlet'er** i Exchange Online PowerShell. De udgår også som en del af udtrædelsen af de andre ældre eDiscovery-værktøjer.

### <a name="scope-of-affected-organizations"></a>Omfanget af berørte organisationer

- organisationer med Office 365 og Microsoft 365 Enterprise

- Office 365 og Microsoft 365 Education organisationer

- Office 365 og Microsoft 365 Government-organisationer. Dette omfatter GCC, GCC High og DoD

- Office 365 Tyskland

### <a name="timeline"></a>Tidslinjen

- 1. juli 2020: Handlingerne GetSearchableMailboxes, SearchMailboxes, SetHoldOnMailboxes og GetHoldOnMailboxes vil ikke længere være tilgængelige, og Microsoft Support yder ikke længere hjælp.

## <a name="ediscovery-premium-v10"></a>eDiscovery (Premium) v1.0

eDiscovery (Premium) v1.0, som er den version af eDiscovery (Premium), der er tilgængelig i en eDiscovery (Standard)-sag ved at klikke på **Skift til eDiscovery (Premium)**, udgår. Dens funktionalitet er blevet erstattet af den nye [eDiscovery(Premium)-løsning](./ediscovery.md) på overholdelsesportalen.

Sådan finder du ud af, om din organisation bruger eDiscovery (Premium) v1.0:

1. Gå til overholdelsesportalen, vælg **eDiscovery** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank">**Core**</a>, og åbn en eDiscovery(Standard)-sag.

1. Hvis du ser knappen **Skift til eDiscovery (Premium),** bliver du sendt til 1.0-versionen af eDiscovery (Premium), som udgår. Muligheden for at oprette og administrere sager i eDiscovery (Standard) påvirkes ikke. Det er kun muligheden for at tilføje og analysere sagsdata i eDiscovery (Premium) v1.0 (ved at klikke på **Skift til eDiscovery (Premium)**), der udgår.

Den nye eDiscovery (Premium)-løsning i Microsoft 365 (også kendt som *eDiscovery (Premium) v2.0*) indeholder alle funktionerne i den oprindelige løsning, men indeholder nu en tilsynsførende tilgang til identifikation af indhold i andre Microsoft 365-tjenester, indsamling af dette indhold og derefter tilføjelse af det til et korrektursæt, hvor korrekturlæsere kan drage fordel af hurtige søgeforespørgsler,  funktioner til mærkning og analyse for at hjælpe med at fjerne relevante dokumenter. eDiscovery (Premium) indeholder nu forbedret behandling og oprindelige seere til både Microsoft- og ikke-Microsoft-filtyper, en komplet liste over filtyper er [her](./supported-filetypes-ediscovery20.md) , og understøttede metadatafelter er [her](./document-metadata-fields-in-advanced-ediscovery.md). Den nye eDiscovery-løsning (Premium) indeholder også en effektiv funktion til administration af forældremyndigheden over indhold i forskellige tjenester, giver brugerne besked om ventepositionerne og sporer forældremyndighedssvar – alt sammen i en eDiscovery-sag (Premium).

Sådan får du adgang til eDiscovery (Premium) v2.0:

Gå til overholdelsesportalen, vælg **eDiscovery** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2174006" target="_blank">**Advanced**</a>, og åbn en eDiscovery(Standard)-sag.

På nuværende tidspunkt anbefaler vi, at du begynder at overføre din eDiscovery-arbejdsproces til den nye eDiscovery-funktionalitet (Premium). Hvis det er nødvendigt, kan du arkivere dine eDiscovery(Premium) 1.0-sager ved at eksportere indholdet og gemme det offline. Selvom du stadig vil kunne få adgang til eDiscovery (Premium) v1.0 i eksisterende tilfælde indtil den 31. december 2020, yder Microsoft Support ikke support efter den 1. oktober 2020. Se følgende tidslinje for at få flere oplysninger.

### <a name="scope-of-affected-organizations"></a>Omfanget af berørte organisationer

- organisationer med Office 365 og Microsoft 365 Enterprise

- Office 365 og Microsoft 365 Education organisationer

- Office 365 og Microsoft 365 Government-organisationer. Dette omfatter GCC, GCC High og DoD

- Office 365 Tyskland

### <a name="timeline"></a>Tidslinjen

- 1. juli 2020: Du kan ikke oprette nye eDiscovery (Premium) v1.0-sager.

- 1. oktober 2020: Du kan ikke føje nye data (Forbered søgeresultater for eDiscovery (Premium)) til nogen sager. Du kan fortsætte med at arbejde med data i eksisterende tilfælde på egen risiko. Microsoft Support yder ikke længere hjælp. 

- 31. december 2020: Du kan ikke få adgang til eDiscovery (Premium) v1.0-sager.

### <a name="alternative-tools"></a>Alternative værktøjer

[EDiscovery-løsningen (Premium)](./overview-ediscovery-20.md) på overholdelsesportalen.
