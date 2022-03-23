---
title: Administrere postkasserevision
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: aaca8987-5b62-458b-9882-c28476a66918
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Logføring af postkassekontrol er som standard slået til i Microsoft 365 (også kaldet standardpostkasserevision eller postkasserevision som standard). Det betyder, at visse handlinger, der udføres af postkasseejere, stedfortrædere og administratorer, automatisk logføres i en postkasses overvågningslog, hvor du kan søge efter aktiviteter, der udføres på postkassen.
ms.openlocfilehash: 957e0a00a480746d6a70bf70ee02d725f43194f8
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/25/2022
ms.locfileid: "63587709"
---
# <a name="manage-mailbox-auditing"></a>Administrere postkasserevision

Fra januar 2019 slår Microsoft som standard logføring af postkassekontrol til for alle organisationer. Det betyder, at visse handlinger, der udføres af postkasseejere, stedfortrædere og administratorer, automatisk logføres, og de tilsvarende postkassekontrolposter vil være tilgængelige, når du søger efter dem i postkassens overvågningslog. Før overvågning af postkasse var aktiveret som standard, skulle du manuelt aktivere det for hver brugerpostkasse i organisationen.

Her er nogle fordele ved overvågning af postkasser som standard:

- Overvågning aktiveres automatisk, når du opretter en ny postkasse. Du behøver ikke at aktivere det manuelt for nye brugere.
- Du behøver ikke at administrere de postkassehandlinger, der overvåges. Et foruddefineret sæt postkassehandlinger overvåges som standard for hver logontype (Administrator, Stedfortræder og Ejer).
- Når Microsoft udgiver en ny postkassehandling, føjes handlingen muligvis automatisk til listen over postkassehandlinger, der overvåges som standard (underlagt, at brugeren har den korrekte licens). Det betyder, at du ikke behøver at overvåge tilføje nye handlinger i postkasser.
- Du har en ensartet politik for postkasserevision på tværs af organisationen (fordi du overvåge de samme handlinger for alle postkasser).

> [!NOTE]
>
> - Som standard er det vigtigt at huske på, at der som standard frigives overvågning af postkasser: Du behøver ikke at gøre noget for at administrere postkasserevision. Men hvis du vil vide mere, tilpasse overvågning af postkasser fra standardindstillingerne eller slå det helt fra, kan denne artikel hjælpe dig.
> - Som standard er det kun postkassekontrolhændelser for E5-brugere, der er tilgængelige i søgninger i overvågningsloggen i Microsoft 365 Overholdelsescenter eller via Office 365 Management Activity API. Du kan finde flere oplysninger i [afsnittet Flere](#more-information) oplysninger i denne artikel.

## <a name="verify-mailbox-auditing-on-by-default-is-turned-on"></a>Bekræft, at overvågning af postkasse er slået til som standard

Du bekræfter, at overvågning af postkasser som standard er aktiveret for din organisation ved at køre følgende kommando [i Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```PowerShell
Get-OrganizationConfig | Format-List AuditDisabled
```

Værdien Falsk **angiver** , at overvågning af postkasser som standard er aktiveret for organisationen. Denne indstilling er som standard indstillet til at tilsidesætte indstillingen for postkasserevision for bestemte postkasser. Hvis f.eks. overvågning af postkasse er deaktiveret for en postkasse (egenskaben *AuditEnabled* er **Falsk** for postkassen), overvåges standardpostkassen stadig for postkassen, fordi overvågning af postkassen som standard er aktiveret for organisationen.

Hvis overvågning af postkasser skal være deaktiveret for bestemte postkasser, skal du konfigurere postkasserevision for postkasseejeren og andre brugere, der har fået delegeret adgang til postkassen. Du kan finde flere oplysninger i afsnittet [Tilsidesætte overvågningslogføring](#bypass-mailbox-audit-logging) for postkasse i denne artikel.

> [!NOTE]
> Når overvågning af postkasser som standard er slået til for organisationen, ændres *egenskaben AuditEnabled* for de berørte postkasser ikke fra **Falsk** til **Sand**. Med andre ord ignorerer overvågning af postkasser som standard *egenskaben AuditEnabled* for postkasser.

## <a name="supported-mailbox-types"></a>Understøttede postkassetyper

Følgende tabel viser de postkassetyper, der aktuelt understøttes af overvågning af postkasser som standard:

<br>

****

|Postkassetype|Understøttet|
|---|:---:|
|Brugerpostkasser|![Markering.](../media/checkmark.png)|
|Delte postkasser|![Markering.](../media/checkmark.png)|
|Microsoft 365 gruppepostkasser|![Markering.](../media/checkmark.png)|
|Ressourcepostkasser||
|Postkasser i offentlige mapper||
|

## <a name="logon-types-and-mailbox-actions"></a>Logontyper og postkassehandlinger

Logontyper klassificerer den bruger, der lavede de reviderede handlinger i postkassen. Følgende liste beskriver de logontyper, der bruges til logføring af postkassekontrol:

- **Ejer**: Postkasseejeren (den konto, der er knyttet til postkassen).
- **Stedfortræder**:
  - En bruger, der har fået tildelt SendAs-, SendOnBehalf- eller FullAccess-tilladelse til en anden postkasse.
  - En administrator, der er blevet tildelt FullAccess-tilladelse til en brugers postkasse.
- **Administrator**:
  - Postkassen søges med et af følgende Microsoft eDiscovery-værktøjer:
    - Indholdssøgning i Overholdelsescenter.
    - eDiscovery eller Advanced eDiscovery i Compliance Center.
    - In-Place eDiscovery i Exchange Online.
  - Postkassen åbnes ved hjælp af MAPI Microsoft Exchange Server-editoren.

### <a name="mailbox-actions-for-user-mailboxes-and-shared-mailboxes"></a>Postkassehandlinger for brugerpostkasser og delte postkasser

I følgende tabel beskrives de postkassehandlinger, der er tilgængelige i logføring af postkassekontrol for brugerpostkasser og delte postkasser.

- En markering (![Markering.](../media/checkmark.png)) angiver, at postkassehandlingen kan logføres for logontypen (ikke alle handlinger er tilgængelige for alle logontyper).
- En stjerne ( ) efter <sup>\*</sup> markeringen angiver, at postkassehandlingen er logført som standard for logontypen.
- Husk, at en administrator med tilladelsen Fuld adgang til en postkasse betragtes som en stedfortræder.

<br>

****

|Postkassehandling|Beskrivelse|Administrator|Stedfortræder|Ejer|
|---|---|:---:|:---:|:---:|
|**AddFolderPermissions**|Selvom denne værdi accepteres som en postkassehandling, er den allerede inkluderet i handlingen **Opdateringsmapper Og overvåges** ikke separat. Med andre ord skal du ikke bruge denne værdi.||||
|**AnvendPost**|Et element navnmærkes som en post.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering.](../media/checkmark.png)<sup>\*</sup>|
|**Kopiér**|En meddelelse blev kopieret til en anden mappe.|![Markering.](../media/checkmark.png)|||
|**Opret**|Et element blev oprettet i mappen Kalender, Kontakter, Noter eller Opgaver i postkassen (der oprettes f.eks. en ny mødeindkaldelse). Oprettelse, afsendelse eller modtagelse af en meddelelse overvåges ikke. Desuden overvåges oprettelse af en postkassemappe ikke.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering.](../media/checkmark.png)|
|**FolderBind**|En postkassemappe blev åbnet. Denne handling logføres også, når administratoren eller stedfortræderen åbner postkassen. <br/><br/> **Bemærk**! Overvågningsposter for handlinger til mappebindinger, der udføres af stedfortrædere, konsolideres. Der genereres en overvågningspost for adgang til individuelle mapper inden for en 24-timers periode.|![Markering.](../media/checkmark.png)|![Markering.](../media/checkmark.png)||
|**HardDelete**|En meddelelse blev slettet fra mappen Genoprettelige elementer.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering.](../media/checkmark.png)<sup>\*</sup>|
|**MailboxLogin**|Brugeren er logget på sin postkasse.|||![Markering](../media/checkmark.png)|
|**MailItemsAccessed**|**Bemærk**! Denne værdi er kun tilgængelig for brugere af abonnementet E5 eller E5 Compliance Add-on. Du kan finde flere oplysninger [i Konfigurere Avanceret overvågning i Microsoft 365](set-up-advanced-audit.md). <p> Maildata tilgås af mailprotokoller og klienter.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|
|**MessageBind**|**Bemærk**! Denne værdi er kun tilgængelig for E3-brugere (brugere uden abonnementer på overholdelse af E5 eller E5). <p> En meddelelse blev vist i indholdsruden eller åbnet af en administrator.|![Markering](../media/checkmark.png)|||
|**Rediger Mappepapirer**|Selvom denne værdi accepteres som en postkassehandling, er den allerede inkluderet i handlingen **Opdateringsmapper Og overvåges** ikke separat. Med andre ord skal du ikke bruge denne værdi.||||
|**Flyt**|En meddelelse blev flyttet til en anden mappe.|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|
|**MoveToDeletedItems**|En meddelelse blev slettet og flyttet til mappen Slettet post.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|
|**OptagSlette**|Et element, der er mærket som en post, blev blød-slettet (flyttet til mappen Genoprettelige elementer). Elementer, der er mærket som poster, kan ikke slettes permanent (fjernes fra mappen Genoprettelige elementer).|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|
|**RemoveFolderPermissions**|Selvom denne værdi accepteres som en postkassehandling, er den allerede inkluderet i handlingen **Opdateringsmapper Og overvåges** ikke separat. Med andre ord skal du ikke bruge denne værdi.||||
|**SearchQueryInitiated**|**Bemærk**! Denne værdi er kun tilgængelig for brugere af abonnementet E5 eller E5 Compliance Add-on. Du kan finde flere oplysninger [i Konfigurere Avanceret overvågning i Microsoft 365](set-up-advanced-audit.md). <p> En person bruger Outlook (Windows, Mac, iOS, Android eller Outlook på internettet) eller mailappen til Windows 10 til at søge efter elementer i en postkasse.|||![Markering](../media/checkmark.png)|
|**Send**|**Bemærk**! Denne værdi er kun tilgængelig for brugere af abonnementet E5 eller E5 Compliance Add-on. Du kan finde flere oplysninger [i Konfigurere Avanceret overvågning i Microsoft 365](set-up-advanced-audit.md). <p> Brugeren sender en mail, svarer på en mail eller videresender en mail.|![Markering.](../media/checkmark.png)<sup>\*</sup>||![Markering](../media/checkmark.png)<sup>\*</sup>|
|**SendAs**|En meddelelse blev sendt ved hjælp af SendAs-tilladelsen. Det betyder, at en anden bruger har sendt meddelelsen, som om den kom fra postkasseejeren.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|En meddelelse blev sendt ved hjælp af SendOnBehalf-tilladelsen. Det betyder, at en anden bruger har sendt meddelelsen på vegne af postkasseejeren. Meddelelsen angiver over for modtageren, hvem meddelelsen blev sendt på vegne af, og hvem der rent faktisk har sendt meddelelsen.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>||
|**BlødSlette**|En meddelelse blev slettet eller slettet permanent fra mappen Slettet post. Blød-slettede elementer flyttes til mappen Genoprettelige elementer.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|
|**Opdater**|En meddelelse eller en af dens egenskaber er blevet ændret.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|
|**UpdateCalendarDelegation**|En kalenderdelegering blev tildelt en postkasse. Kalenderdelegering giver andre i samme organisation tilladelse til at administrere postkasseejerens kalender.|![Markering.](../media/checkmark.png)<sup>\*</sup>||![Markering](../media/checkmark.png)<sup>\*</sup>|
|**UpdateComplianceTag**|Et andet opbevaringsnavn anvendes på et mailelement (et element kan kun have tildelt ét opbevaringsnavn).|![Markering.](../media/checkmark.png)|![Markering](../media/checkmark.png)|![Markering](../media/checkmark.png)|
|**Opdater mappepapirer**|En mappetilladelse blev ændret. Mappetilladelser styrer, hvilke brugere i organisationen der kan få adgang til mapper i en postkasse og de meddelelser, der er placeret i disse mapper.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|
|**UpdateInboxRules**|En indbakkeregel blev tilføjet, fjernet eller ændret. Indbakkeregler bruges til at behandle meddelelser i brugerens indbakke baseret på de angivne betingelser og udføre handlinger, når betingelserne i en regel er opfyldt, f.eks. flytte en meddelelse til en bestemt mappe eller slette en meddelelse.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|
|

> [!IMPORTANT]
> Hvis du har tilpasset postkassehandlinger, der skal overvåges for en  hvilken som helst logontype, før overvågning af postkassen som standard blev aktiveret i organisationen, bevares de brugerdefinerede indstillinger i postkassen og overskrives ikke med standardpostkassehandlingerne som beskrevet i dette afsnit. Hvis du vil gendanne handlingerne i overvågningspostkassen til deres standardværdier (som du når som helst kan gøre), [](#restore-the-default-mailbox-actions) skal du se afsnittet Gendan standardpostkassens handlinger senere i denne artikel.

### <a name="mailbox-actions-for-microsoft-365-group-mailboxes"></a>Postkassehandlinger for Microsoft 365 gruppepostkasser

Overvågning af postkasser er som standard aktiveret for logføring af postkassekontrol i Microsoft 365-gruppepostkasser, men du kan ikke tilpasse det, der logføres (du kan ikke tilføje eller fjerne postkassehandlinger, der logføres for nogen logontype).

I følgende tabel beskrives de postkassehandlinger, der som standard logføres på Microsoft 365 gruppepostkasser for hver logontype.

Husk, at en administrator med tilladelsen Fuld adgang til en Microsoft 365 gruppepostkasse betragtes som en stedfortræder.

<br>

****

|Postkassehandling|Beskrivelse|Administrator|Stedfortræder|Ejer|
|---|---|:---:|:---:|:---:|
|**Opret**|Oprettelse af et kalenderelement. Oprettelse, afsendelse eller modtagelse af en meddelelse overvåges ikke.|![Markering](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>||
|**HardDelete**|En meddelelse blev slettet fra mappen Genoprettelige elementer.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|
|**MoveToDeletedItems**|En meddelelse blev slettet og flyttet til mappen Slettet post.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|
|**SendAs**|En meddelelse blev sendt ved hjælp af SendAs-tilladelsen.|![Markering](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|En meddelelse blev sendt ved hjælp af SendOnBehalf-tilladelsen.|![Markering](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>||
|**BlødSlette**|En meddelelse blev slettet eller slettet permanent fra mappen Slettet post. Blød-slettede elementer flyttes til mappen Genoprettelige elementer.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|
|**Opdater**|En meddelelse eller en hvilken som helst af dens egenskaber er blevet ændret.|![Markering.](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|![Markering](../media/checkmark.png)<sup>\*</sup>|
|

### <a name="verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type"></a>Kontrollér, at der logføres standardpostkassehandlinger for hver logontype

Postkasserevision er som standard tilføjet en ny *DefaultAuditSet-egenskab* til alle postkasser. Værdien af denne egenskab angiver, om standardpostkassens handlinger (administreres af Microsoft) overvåges i postkassen.

For at \<MailboxIdentity\> få vist værdien i brugerpostkasser eller delte postkasser skal du erstatte med postkassens navn, alias, mailadresse eller brugerens hovednavn (brugernavn) og køre følgende kommando i Exchange Online PowerShell:

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Format-List DefaultAuditSet
```

For at få vist værdien på Microsoft 365 gruppepostkasser skal \<MailboxIdentity\> du erstatte med navnet, aliasset eller mailadressen på den delte postkasse og køre følgende kommando i Exchange Online PowerShell:

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> -GroupMailbox | Format-List DefaultAuditSet
```

`Admin, Delegate, Owner` Værdien angiver:

- Standardpostkassens handlinger for alle tre logontyper overvåges. Dette er den eneste værdi, du får vist på Microsoft 365 gruppepostkasser.
- En administrator *har ikke ændret* de reviderede postkassehandlinger for nogen logontype på en brugerpostkasse eller en delt postkasse. Bemærk, at dette er standardtilstanden, når overvågning af postkasser som standard er slået til i organisationen.

Hvis en administrator nogensinde har ændret de postkassehandlinger, der overvåges for en logontype (ved hjælp af parametrene *AuditAdmin*, *AuditDelegate* eller *AuditOwner* på **cmdlet'en Set-Mailbox** ), vil egenskabsværdien være forskellig.

Eksempelvis angiver værdien for egenskaben `Owner` *DefaultAuditSet* for en brugerpostkasse eller delt postkasse:

- Standardpostkassens handlinger for postkasseejeren overvåges.
- De overvågede postkassehandlinger for logontyperne `Delegate` `Admin` og er blevet ændret fra standardhandlingerne.

En tom værdi for *egenskaben DefaultAuditSet* angiver postkassehandlingerne for alle tre logontyper er blevet ændret i brugerpostkassen eller en delt postkasse.

Du kan finde flere oplysninger i afsnittet [Ændre eller gendanne postkassehandlinger, der er logført](#change-or-restore-mailbox-actions-logged-by-default) som standard i denne artikel

### <a name="display-the-mailbox-actions-that-are-being-logged-on-mailboxes"></a>Få vist de postkassehandlinger, der logføres på postkasser

For at se de postkassehandlinger, der i øjeblikket logføres på brugerpostkasser eller delte postkasser, \<MailboxIdentity\> skal du erstatte med postkassens navn, alias, mailadresse eller brugerens hovednavn (brugernavn) og køre en eller flere af følgende kommandoer i Exchange Online PowerShell.

> [!NOTE]
> Selvom du kan føje parameteren `-GroupMailbox` til følgende **Get-Mailbox-kommandoer** for Microsoft 365 gruppepostkasser, tror du ikke på de værdier, der returneres. Standardhandlingerne og statiske postkassehandlinger, der overvåges for Microsoft 365-gruppepostkasser, er beskrevet i afsnittet Postkassehandlinger [for](#mailbox-actions-for-microsoft-365-group-mailboxes) Microsoft 365-gruppepostkasser tidligere i denne artikel.

#### <a name="owner-actions"></a>Ejerhandlinger

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditOwner
```

#### <a name="delegate-actions"></a>Stedfortræderhandlinger

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditDelegate
```

#### <a name="admin-actions"></a>Administratorhandlinger

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditAdmin
```

## <a name="change-or-restore-mailbox-actions-logged-by-default"></a>Ændre eller gendanne postkassehandlinger, der er logført som standard

Som tidligere nævnt er en af de vigtigste fordele ved at have overvågning af postkassen som standard: Du behøver ikke at administrere de postkasser, der overvåges. Microsoft gør dette for dig, og vi tilføjer automatisk nye postkassehandlinger, så de som standard bliver overvåget, når de frigives.

Det kan dog være nødvendigt for din organisation at overvåge et andet sæt postkassehandlinger for brugerpostkasser og delte postkasser. Fremgangsmåderne i dette afsnit viser, hvordan du ændrer de postkassehandlinger, der overvåges for hver logontype, og hvordan du vender tilbage til microsoft-administrerede standardhandlinger.

> [!IMPORTANT]
> Hvis du bruger følgende procedurer til at tilpasse postkassehandlinger, der er logget på brugerpostkasser eller delte postkasser, så bliver nye standardpostkassehandlinger, der udgives af Microsoft, ikke automatisk overvåget for disse postkasser. Du skal manuelt føje alle nye postkassehandlinger til din brugerdefinerede liste over handlinger.

### <a name="change-the-mailbox-actions-to-audit"></a>Ændre postkassehandlinger, der skal overvåges

Du kan bruge parametrene *AuditAdmin*, *AuditDelegate* eller *AuditOwner* på cmdlet'en **Set-Mailbox** til at ændre de postkassehandlinger, der overvåges for brugerpostkasser og delte postkasser (reviderede handlinger for Microsoft 365-gruppepostkasser kan ikke tilpasses).

Du kan bruge to forskellige metoder til at angive postkassehandlingerne:

- *Erstat* (overse) de eksisterende postkassehandlinger ved hjælp af denne syntaks: `action1,action2,...actionN`.
- *Tilføj eller fjern postkassehandlinger* uden at påvirke andre eksisterende værdier ved hjælp af denne syntaks: `@{Add="action1","action2",..."actionN"}` eller `@{Remove="action1","action2",..."actionN"}`.

I dette eksempel ændres administratorpostkassens handlinger for postkassen "Gabriela Laureano" ved at overskrive standardhandlingerne med BlødSlette og HardDelete.

```PowerShell
Set-Mailbox -Identity "Gabriela Laureano" -AuditAdmin HardDelete,SoftDelete
```

I dette eksempel føjes ejerhandlingen MailboxLogin til laura@contoso.onmicrosoft.com.

```PowerShell
Set-Mailbox -Identity laura@contoso.onmicrosoft.com -AuditOwner @{Add="MailboxLogin"}
```

I dette eksempel fjernes stedfortræderhandlingen FlytTilSlettetWebsteder for teamdiskussionspostkassen.

```PowerShell
Set-Mailbox -Identity "Team Discussion" -AuditDelegate @{Remove="MoveToDeletedItems"}
```

Uanset hvilken metode du bruger, har tilpasning af de overvågede postkassehandlinger for brugerpostkasser eller delte postkasser følgende resultater:

- For den logontype, du har tilpasset, administreres de overvågede postkassehandlinger ikke længere af Microsoft.
- Den logontype, du har tilpasset, vises ikke længere i *StandardAuditSet-egenskabsværdien* for postkassen som [beskrevet tidligere](#verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type).

### <a name="restore-the-default-mailbox-actions"></a>Gendan standardpostkassens handlinger

> [!NOTE]
> Følgende procedurer gælder ikke for postkasser i Microsoft 365 (de er begrænset til standardhandlingerne som beskrevet [her](#mailbox-actions-for-microsoft-365-group-mailboxes)).

Hvis du har tilpasset de postkassehandlinger, der overvåges i en brugerpostkasse eller en delt postkasse, kan du gendanne standardpostkassens handlinger for en eller alle logontyper ved hjælp af denne syntaks:

```PowerShell
Set-Mailbox -Identity <MailboxIdentity> -DefaultAuditSet <Admin | Delegate | Owner>
```

Du kan angive flere *DefaultAuditSet-værdier* adskilt af kommaer

I dette eksempel gendannes standardhandlingerne for de overvågede postkasser for alle logontyper på mark@contoso.onmicrosoft.com.

```PowerShell
Set-Mailbox -Identity mark@contoso.onmicrosoft.com -DefaultAuditSet Admin,Delegate,Owner
```

I dette eksempel gendannes standardhandlingerne for de overvågede postkasser for administratorlogontypen i postkassens chris@contoso.onmicrosoft.com, men de brugerdefinerede overvågede postkassehandlinger ændres til logontyperne Stedfortræder og Ejer.

```PowerShell
Set-Mailbox -Identity chris@contoso.onmicrosoft.com -DefaultAuditSet Admin
```

Hvis han som standard gendanner de overvågede postkassehandlinger for en logontype, får du følgende resultater:

- Den aktuelle liste over postkassehandlinger erstattes med standardpostkassens handlinger for logontypen.
- Alle nye postkassehandlinger, der udgives af Microsoft, føjes automatisk til listen over reviderede handlinger for logontypen.
- Egenskaben *DefaultAuditSet* for postkassen opdateres, så den indeholder den gendannede logontype.

## <a name="turn-off-mailbox-auditing-on-by-default-for-your-organization"></a>Slå overvågning af postkasse fra som standard for organisationen

Du kan som standard slå overvågning af postkasse fra for hele organisationen ved at køre følgende kommando i Exchange Online PowerShell:

```PowerShell
Set-OrganizationConfig -AuditDisabled $true
```

Hvis du slår overvågning af postkasse fra, har det som standard følgende resultater:

- Postkasserevision er deaktiveret for din organisation.
- Fra det tidspunkt, hvor du har deaktiveret overvågning af postkassen som standard, overvåges ingen postkassehandlinger, heller ikke selvom overvågning er aktiveret for en postkasse ( *egenskaben AuditEnabled* for postkassen er **Sand**).
- Postkasserevision er ikke aktiveret for nye postkasser, og indstilling af egenskaben *AuditEnabled* i en ny eller eksisterende postkasse til **Sand** ignoreres.
- Alle indstillinger for postkassekontrol til overføring af tilknytning (konfigureret ved hjælp af **Cmdlet'en Set-MailboxAuditBypassAssociation** ) ignoreres.
- Eksisterende postkassekontrolposter bevares, indtil aldersgrænsen for overvågningsloggen for posten udløber.

### <a name="turn-on-mailbox-auditing-on-by-default"></a>Slå postkasserevision til som standard

Hvis du vil slå overvågning af postkasse til igen for din organisation, skal du køre følgende kommando i Exchange Online PowerShell:

```PowerShell
Set-OrganizationConfig -AuditDisabled $false
```

## <a name="bypass-mailbox-audit-logging"></a>Tilgå logføring af postkassekontrol

I øjeblikket kan du ikke deaktivere postkasserevision for bestemte postkasser, når overvågning af postkasser som standard er aktiveret i organisationen. Eksempelvis ignoreres indstilling *af postkasseegenskaben AuditEnabled* **til** False.

Du kan dog stadig bruge **Set-MailboxAuditBypassAssociation-cmdlet'en** i Exchange Online PowerShell til at forhindre  eventuelle og alle postkassehandlinger fra de angivne brugere i at blive logført, uanset hvor handlingerne sker. Eksempel:

- Postkasseejerhandlinger, der udføres af de tilgåede brugere, logføres ikke.
- Stedfortræderhandlinger, der udføres af de omgåede brugere på andre brugeres postkasser (herunder delte postkasser), logføres ikke.
- Administratorhandlinger, der udføres af de omgåede brugere, logføres ikke.

Hvis du vil tilsidesætte logføring af postkassekontrol for en bestemt bruger, \<MailboxIdentity\> skal du erstatte med brugerens navn, mailadresse, alias eller brugerens hovednavn (brugernavn) og køre følgende kommando:

```PowerShell
Set-MailboxAuditBypassAssociation -Identity <MailboxIdentity> -AuditByPassEnabled $true
```

Kør følgende kommando for at kontrollere, at overvågning er tilsidesættet for den angivne bruger:

```PowerShell
Get-MailboxAuditBypassAssociation -Identity <MailboxIdentity> | Format-List AuditByPassEnabled
```

Værdien Sand **angiver** , at logføring af postkassekontrol er blevet ignoreret for brugeren.

## <a name="more-information"></a>Flere oplysninger

- Selvom logføring af postkassekontrol som standard er aktiveret for alle organisationer, er det kun brugere med E5-licenser, der returnerer postkassens overvågningsloghændelser i overvågningsloggens søgninger i [Microsoft 365 Overholdelsescenter](search-the-audit-log-in-security-and-compliance.md) eller via [Office 365 Management Activity API](/office/office-365-management-api/office-365-management-activity-api-reference) som **standard**.

  Hvis du vil hente poster i postkasse overvågningsloggen for brugere uden E5-licenser, kan du:

  - Aktivér postkasserevision for individuelle postkasser manuelt (kør kommandoen). `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true` Når du har gjort dette, kan du bruge overvågningslogsøgninger i Microsoft 365 Overholdelsescenter eller via Office 365 Management Activity API.

    > [!NOTE]
    > Hvis overvågning af postkasser allerede ser ud til at være aktiveret på postkassen, men dine søgninger ikke returnerer nogen resultater, skal du ændre værdien af _parameteren AuditEnabled_ `$false` til og derefter tilbage til `$true`.

  - Brug følgende cmdlet'er i Exchange Online PowerShell:
    - [Search-MailboxAuditLog til at](/powershell/module/exchange/search-mailboxauditlog) søge i postkassens overvågningslog efter bestemte brugere.
    - [New-MailboxAuditLogSearch](/powershell/module/exchange/new-mailboxauditlogsearch) for at søge i postkassens overvågningslog efter bestemte brugere og for at få sendt resultaterne via mail til bestemte modtagere.

  - Brug <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration (EAC)</a> i Exchange Online til at udføre følgende handlinger:
    - [Eksportér postkasse overvågningslogfiler](/Exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs)
    - [Kør en rapport om adgang til en postkasse uden ejer](/Exchange/security-and-compliance/exchange-auditing-reports/non-owner-mailbox-access-report)

- Som standard bevares postkasses overvågningslogposter i 90 dage, før de slettes. Du kan ændre aldersgrænsen for overvågningslogposter ved hjælp af *auditLogAgeLimit-parameteren* på **Set-Mailbox-cmdlet'en** Exchange Online PowerShell. Men hvis du øger denne værdi, kan du ikke søge efter begivenheder, der er ældre end 90 dage i overvågningsloggen.

  Hvis du øger aldersgrænsen, skal du bruge [Search-MailboxAuditLog-cmdlet'en](/powershell/module/exchange/search-mailboxauditlog) i Exchange Online PowerShell til at søge i brugerens postkasses overvågningslog efter poster, der er ældre end 90 dage.

- Hvis du har ændret *egenskaben AuditLogAgeLimit* for en postkasse, før overvågning af postkasse som standard er slået til for organisationen, ændres postkassens eksisterende aldersgrænse for overvågningsloggen ikke. Med andre ord påvirker overvågning af postkasser som standard ikke den aktuelle aldersgrænse for postkassekontrolposter.

- Hvis du vil *ændre værdien AuditLogAgeLimit* på en Microsoft 365-gruppepostkasse, `-GroupMailbox` skal du medtage parameteren i **kommandoen Set-Mailbox**.

- Poster i overvågningsloggen for postkassen gemmes i en undermappe (med navnet *Revisioner)* i mappen Genoprettelige elementer i hver brugers postkasse. Vær opmærksom på følgende ting vedrørende postkassepostkasser og mappen Genoprettelige elementer:

  - Postkassekontrolposter tæller med i lagerkvoten for mappen Genoprettelige elementer, der som standard er 30 GB (advarselskvoten er 20 GB). Lagerkvoten øges automatisk til 100 GB (med en advarselskvote på 90 GB), når:
    - En venteposition placeres i en postkasse.
    - Postkassen tildeles til en opbevaringspolitik i Overholdelsescenter.

  - Postkassekontrolposter tæller også med i [mappegrænsen for mappen Genoprettelige elementer](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-folder-limits). Der kan maksimalt gemmes 3 millioner elementer (overvågningsposter) i undermappen Revisioner.

    > [!NOTE]
    > Det er usandsynligt, at overvågning af postkasser som standard påvirker lagerkvoten eller mappegrænsen for mappen Genoprettelige elementer.

    - Du kan køre følgende kommando i Exchange Online PowerShell for at få vist størrelsen og antallet af elementer i undermappen Revisioner i mappen Genoprettelige elementer:

      ```PowerShell
      Get-MailboxFolderStatistics -Identity <MailboxIdentity> -FolderScope RecoverableItems | Where-Object {$_.Name -eq 'Audits'} | Format-List FolderPath,FolderSize,ItemsInFolder
      ```

    - Du kan ikke få direkte adgang til en overvågningslogpost i mappen Genoprettelige elementer. I stedet skal du bruge **cmdlet'en Search-MailboxAuditLog** eller søge i overvågningsloggen for at finde og få vist overvågningsposter for postkassen.

- Hvis en postkasse er sat i venteposition eller er tildelt en opbevaringspolitik i Overholdelsescenter, bevares overvågningslogposter stadig i den varighed, der er defineret af postkassens *AuditLogAgeLimit-egenskab* (90 dage som standard). Hvis du vil bevare overvågningslogposter længere for postkasser i venteposition, skal du øge postkassens *AuditLogAgeLimit-værdi* .

- I et multi-geo-miljø understøttes overvågning af postkasser på tværs af geografiske miljøer ikke. Hvis en bruger f.eks. har fået tildelt adgangstilladelse til en delt postkasse på en anden geoplacering, logføres postkassehandlinger, der udføres af den pågældende bruger, ikke i postkassens overvågningslog for den delte postkasse. Exchange overvågningshændelser for administratorer er i øjeblikket kun tilgængelige for standardplaceringen.
