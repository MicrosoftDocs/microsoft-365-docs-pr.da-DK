---
title: Administrer overvågning af postkasse
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
description: Logføring af overvågning af postkasser er som standard slået til i Microsoft 365 (også kaldet "overvågning af standardpostkasser" eller "overvågning af postkasser slået til som standard"). Denne konfiguration betyder, at visse handlinger, der udføres af postkasseejere, stedfortrædere og administratorer, automatisk logføres i en overvågningslog for postkassen, hvor du kan søge efter aktiviteter, der udføres i postkassen.
ms.openlocfilehash: e869c705df2943c1781c02362c2c38b6713affc5
ms.sourcegitcommit: e13c8fc28c68422308c9d356109797cfcf6f77be
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/14/2022
ms.locfileid: "64841907"
---
# <a name="manage-mailbox-auditing"></a>Administrer overvågning af postkasse

I januar 2019 aktiverede Microsoft som standard logføring af postkasseovervågning for alle organisationer. Denne konfiguration betyder, at visse handlinger udført af postkasseejere, stedfortrædere og administratorer automatisk logføres. Det betyder også, at de tilsvarende postkassens overvågningsposter vil være tilgængelige, når du søger efter dem i postkassens overvågningslog. Før overvågning af postkassen blev slået til som standard, skulle du aktivere den manuelt for hver brugerpostkasse i din organisation.

Her er nogle fordele ved overvågning af postkasser som standard:

- Overvågning aktiveres automatisk, når du opretter en ny postkasse. Du behøver ikke at aktivere den manuelt for nye brugere.
- Du behøver ikke at administrere de postkassehandlinger, der overvåges. Et foruddefineret sæt postkassehandlinger overvåges som standard for hver logontype (administrator, stedfortræder og ejer).
- Når Microsoft frigiver en ny postkassehandling, føjes handlingen muligvis automatisk til listen over postkassehandlinger, der overvåges som standard (forudsat at brugeren har den relevante licens). Det betyder, at du ikke behøver at overvåge tilføj nye handlinger i postkasser.
- Du har en konsekvent overvågningspolitik for postkasser på tværs af organisationen (fordi du overvåger de samme handlinger for alle postkasser).

> [!NOTE]
>
> - Det er vigtigt at huske på, at overvågning af postkasser er aktiveret som standard: Du behøver ikke at foretage dig noget for at administrere overvågning af postkasser. Men hvis du vil vide mere, tilpasse overvågning af postkasser ud fra standardindstillingerne eller slå den helt fra, kan denne artikel hjælpe dig.
> - Det er som standard kun overvågningshændelser for postkasser for brugere med licenser, der indeholder funktionen [Avanceret overvågning](advanced-audit.md), der er tilgængelige i søgninger i overvågningsloggen i Microsoft 365 Overholdelsescenter eller via API'en til administration af Office 365. Disse licenser er beskrevet [her](auditing-solutions-overview.md#advanced-audit-1). Denne artikel henviser samlet set til licenser, der omfatter Avanceret overvågning som *E5/A5/G5-licenser*.
>   Du kan få flere oplysninger om, hvordan licenser påvirker overvågningshændelser for postkasser i M365 Compliance Center, i afsnittet [Flere oplysninger](#more-information) senere i denne artikel.

## <a name="verify-mailbox-auditing-on-by-default-is-turned-on"></a>Kontrollér, at overvågning af postkassen som standard er slået til

Hvis du vil kontrollere, at overvågning af postkasser som standard er slået til for din organisation, skal du køre følgende kommando i [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```PowerShell
Get-OrganizationConfig | Format-List AuditDisabled
```

Værdien **False** angiver, at overvågning af postkasser som standard er aktiveret for organisationen. Dette er aktiveret som standard for organisationsværdier, og overvågning af postkasser tilsidesættes for bestemte postkasser. Hvis overvågning af postkasser f.eks. er deaktiveret for en postkasse (egenskaben *AuditEnabled* er **Falsk** i postkassen), overvåges standardhandlingerne for postkassen stadig, fordi overvågning af postkassen som standard er aktiveret for organisationen.

Hvis du vil holde overvågning af postkassen deaktiveret for bestemte postkasser, skal du konfigurere overvågning af postkasser for ejeren af postkassen og andre brugere, der er blevet uddelegeret adgang til postkassen. Du kan få flere oplysninger i afsnittet [Overgå logføring af overvågning af postkasser](#bypass-mailbox-audit-logging) senere i denne artikel.

> [!NOTE]
> Når overvågning af postkasser som standard er slået til for organisationen, ændres egenskaben *AuditEnabled* for berørte postkasser ikke fra **Falsk** til **Sand**. Det vil sige, at overvågning af postkasser som standard ignorerer egenskaben *AuditEnabled* på postkasser.

## <a name="supported-mailbox-types"></a>Understøttede postkassetyper

I følgende tabel vises de postkassetyper, der i øjeblikket understøttes af overvågning af postkasser som standard:

|Postkassetype|Understøttes|
|---|:---:|
|Brugerpostkasser|![Markeret.](../media/checkmark.png)|
|Delte postkasser|![Markeret.](../media/checkmark.png)|
|Microsoft 365 gruppepostkasser|![Markeret.](../media/checkmark.png)|
|Ressourcepostkasser||
|Postkasser i offentlige mapper||

## <a name="logon-types-and-mailbox-actions"></a>Logontyper og postkassehandlinger

Logontyper klassificerer den bruger, der udførte de overvågede handlinger i postkassen. På følgende liste beskrives de logontyper, der bruges i logføring af postkassens overvågning:

- **Ejer**: Ejeren af postkassen (den konto, der er knyttet til postkassen).
- **Stedfortræder**:
  - En bruger, der har fået tildelt tilladelsen SendAs, SendOnBehalf eller FullAccess til en anden postkasse.
  - En administrator, der har fået tildelt Tilladelsen FullAccess til en brugers postkasse.
- **Administrator**:
  - Der søges i postkassen med et af følgende Microsoft eDiscovery-værktøjer:
    - Indholdssøgning i Overholdelsescenter.
    - eDiscovery eller Advanced eDiscovery i Compliance Center.
    - In-Place eDiscovery i Exchange Online.
  - Du kan få adgang til postkassen ved hjælp af Microsoft Exchange Server MAPI-editor.

### <a name="mailbox-actions-for-user-mailboxes-and-shared-mailboxes"></a>Postkassehandlinger for brugerpostkasser og delte postkasser

I følgende tabel beskrives de postkassehandlinger, der er tilgængelige i logføring af overvågning af postkasser for brugerpostkasser og delte postkasser.

- En markering (![Markeret.](../media/checkmark.png)) angiver, at postkassehandlingen kan logføres for logontypen (ikke alle handlinger er tilgængelige for alle logontyper).
- En stjerne ( <sup>\*</sup> ), når markeringen angiver, at postkassehandlingen som standard er logført for logontypen.
- Husk, at en administrator med tilladelsen Fuld adgang til en postkasse betragtes som stedfortræder.

|Postkassehandling|Beskrivelse|Admin|Uddelegere|Ejer|
|---|---|:---:|:---:|:---:|
|**AddFolderPermissions**|Selvom denne værdi accepteres som en postkassehandling, er den allerede inkluderet i handlingen **UpdateFolderPermissions** og overvåges ikke separat. Brug med andre ord ikke denne værdi.||||
|**AnvendPost**|Et element er mærket som en post.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret.](../media/checkmark.png)<sup>\*</sup>|
|**Kopiere**|En meddelelse blev kopieret til en anden mappe.|![Markeret.](../media/checkmark.png)|||
|**Opret**|Der blev oprettet et element i mappen Kalender, Kontakter, Kladde, Noter eller Opgaver i postkassen (der oprettes f.eks. en ny mødeindkaldelse). Oprettelse, afsendelse eller modtagelse af en meddelelse overvåges ikke. Desuden overvåges oprettelse af en postkassemappe ikke.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret.](../media/checkmark.png)|
|**Mappebind**|Der blev åbnet en postkassemappe. Denne handling logføres også, når administratoren eller stedfortræderen åbner postkassen. <br/><br/> **Bemærk**! Overvåg poster for handlinger for mappebindinger, der udføres af stedfortrædere, konsolideres. Der genereres én overvågningspost for individuel mappeadgang inden for en 24-timers periode.|![Markeret.](../media/checkmark.png)|![Markeret.](../media/checkmark.png)||
|**HardDelete**|En meddelelse blev fjernet fra mappen Elementer, der kan gendannes.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret.](../media/checkmark.png)<sup>\*</sup>|
|**MailboxLogin**|Brugeren loggede på sin postkasse.|||![Markeret](../media/checkmark.png)|
|**MailItemsAccessed**|**Bemærk**! Denne værdi er kun tilgængelig for brugere med E5/A5/G5-licenser. Du kan få flere oplysninger under [Konfigurer avanceret overvågning i Microsoft 365](set-up-advanced-audit.md). <br/><br/> Maildata tilgås af mailprotokoller og klienter.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|
|**Meddelelsebind**|**Bemærk**! Denne værdi er kun tilgængelig for brugere *uden* E5/A5/G5-licenser. <br/><br/> En meddelelse blev vist i indholdsruden eller åbnet af en administrator.|![Markeret](../media/checkmark.png)|||
|**RedigerMapperTilladelser**|Selvom denne værdi accepteres som en postkassehandling, er den allerede inkluderet i handlingen **UpdateFolderPermissions** og overvåges ikke separat. Brug med andre ord ikke denne værdi.||||
|**Flytte**|En meddelelse blev flyttet til en anden mappe.|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|
|**FlyttilDeletedItems**|En meddelelse blev slettet og flyttet til mappen Slettet post.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|
|**Postsletning**|Et element, der er mærket som en post, blev slettet med blød sletning (flyttet til mappen Genoprettelige elementer). Elementer, der er mærket som poster, kan ikke slettes permanent (fjernes fra mappen Gendanbare elementer).|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|
|**RemoveFolderPermissions**|Selvom denne værdi accepteres som en postkassehandling, er den allerede inkluderet i handlingen **UpdateFolderPermissions** og overvåges ikke separat. Brug med andre ord ikke denne værdi.||||
|**SearchQueryInitiated**|**Bemærk**! Denne værdi er kun tilgængelig for brugere med E5/A5/G5-licenser. Du kan få flere oplysninger under [Konfigurer avanceret overvågning i Microsoft 365](set-up-advanced-audit.md). <br/><br/> En person bruger Outlook (Windows, Mac, iOS, Android eller Outlook på internettet) eller appen Mail til Windows 10 til at søge efter elementer i en postkasse.|||![Markeret](../media/checkmark.png)|
|**Send**|**Bemærk**! Denne værdi er kun tilgængelig for brugere med E5/A5/G5-licenser. Du kan få flere oplysninger under [Konfigurer avanceret overvågning i Microsoft 365](set-up-advanced-audit.md). <br/><br/> Brugeren sender en mail, besvarer en mail eller videresender en mail.|![Markeret.](../media/checkmark.png)<sup>\*</sup>||![Markeret](../media/checkmark.png)<sup>\*</sup>|
|**Send som**|Der blev sendt en meddelelse ved hjælp af tilladelsen SendAs. Det betyder, at en anden bruger sendte meddelelsen, som om den kom fra ejeren af postkassen.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|Der blev sendt en meddelelse ved hjælp af tilladelsen SendOnBehalf. Det betyder, at en anden bruger sendte meddelelsen på vegne af ejeren af postkassen. Meddelelsen angiver til modtageren, hvem meddelelsen blev sendt på vegne af, og hvem der rent faktisk sendte meddelelsen.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>||
|**Blød sletning**|En meddelelse blev slettet eller slettet permanent fra mappen Slettet post. Elementer, der er slettet med blød sletning, flyttes til mappen Elementer, der kan gendannes.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|
|**Opdater**|En meddelelse eller en af dens egenskaber blev ændret.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|
|**UpdateCalendarDelegation**|Der blev tildelt en kalenderdelegering til en postkasse. Kalenderdelegering giver en anden i den samme organisation tilladelse til at administrere postkasseejerens kalender.|![Markeret.](../media/checkmark.png)<sup>\*</sup>||![Markeret](../media/checkmark.png)<sup>\*</sup>|
|**UpdateComplianceTag**|Der anvendes en anden opbevaringsmærkat på et postelement (der kan kun tildeles én opbevaringsmærkat til et element).|![Markeret.](../media/checkmark.png)|![Markeret](../media/checkmark.png)|![Markeret](../media/checkmark.png)|
|**UpdateFolderPermissions**|En mappetilladelse blev ændret. Mappetilladelser styrer, hvilke brugere i din organisation der kan få adgang til mapper i en postkasse og de meddelelser, der er placeret i disse mapper.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|
|**UpdateInboxRules**|Der blev tilføjet, fjernet eller ændret en indbakkeregel. Indbakkeregler bruges til at behandle meddelelser i brugerens indbakke baseret på de angivne betingelser og udføre handlinger, når betingelserne i en regel er opfyldt, f.eks. at flytte en meddelelse til en angivet mappe eller slette en meddelelse.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|

> [!IMPORTANT]
> Hvis du har tilpasset de postkassehandlinger, der skal overvåges for en hvilken som helst logontype, *før* overvågning af postkassen som standard blev aktiveret i din organisation, bevares de brugerdefinerede indstillinger i postkassen og overskrives ikke af standardhandlingerne for postkassen, som beskrevet i dette afsnit. Hvis du vil gendanne handlingerne i overvågningspostkassen til deres standardværdier (hvilket du kan gøre når som helst), skal du se afsnittet [Gendan handlinger for standardpostkassen](#restore-the-default-mailbox-actions) senere i denne artikel.

### <a name="mailbox-actions-for-microsoft-365-group-mailboxes"></a>Postkassehandlinger for Microsoft 365 gruppepostkasser

Overvågning af postkasser er som standard slået til, så logføring af overvågning af postkasser overføres til Microsoft 365 gruppepostkasser, men du kan ikke tilpasse det, der logføres (du kan ikke tilføje eller fjerne postkassehandlinger, der logføres for alle logontyper).

I følgende tabel beskrives de postkassehandlinger, der som standard logføres på Microsoft 365 Gruppepostkasser for hver logontype.

Husk, at en administrator med tilladelsen Fuld adgang til en Microsoft 365 gruppepostkasse betragtes som stedfortræder.

|Postkassehandling|Beskrivelse|Admin|Uddelegere|Ejer|
|---|---|:---:|:---:|:---:|
|**Opret**|Oprettelse af et kalenderelement. Oprettelse, afsendelse eller modtagelse af en meddelelse overvåges ikke.|![Markeret](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>||
|**HardDelete**|En meddelelse blev fjernet fra mappen Elementer, der kan gendannes.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|
|**FlyttilDeletedItems**|En meddelelse blev slettet og flyttet til mappen Slettet post.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|
|**Send som**|Der blev sendt en meddelelse ved hjælp af tilladelsen SendAs.|![Markeret](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>||
|**SendOnBehalf**|Der blev sendt en meddelelse ved hjælp af tilladelsen SendOnBehalf.|![Markeret](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>||
|**Blød sletning**|En meddelelse blev slettet eller slettet permanent fra mappen Slettet post. Elementer, der er slettet med blød sletning, flyttes til mappen Elementer, der kan gendannes.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|
|**Opdater**|En meddelelse eller en af dens egenskaber blev ændret.|![Markeret.](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|![Markeret](../media/checkmark.png)<sup>\*</sup>|

### <a name="verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type"></a>Bekræft, at der logføres standardpostkassehandlinger for hver logontype

Overvågning af postkasser er som standard slået til, og der føjes en ny *defaultauditSet-egenskab* til alle postkasser. Værdien af denne egenskab angiver, om standardhandlingerne for postkassen (administreret af Microsoft) overvåges i postkassen.

Hvis du vil have vist værdien for brugerpostkasser eller delte postkasser, skal du erstatte \<MailboxIdentity\> med postkassens navn, alias, mailadresse eller brugerens hovednavn (brugernavn) og køre følgende kommando i Exchange Online PowerShell:

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Format-List DefaultAuditSet
```

Hvis du vil have vist værdien for Microsoft 365 gruppepostkasser, skal du erstatte \<MailboxIdentity\> med navnet, aliaset eller mailadressen på den delte postkasse og køre følgende kommando i Exchange Online PowerShell:

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> -GroupMailbox | Format-List DefaultAuditSet
```

Værdien `Admin, Delegate, Owner` angiver:

- Standardhandlingerne for postkassen for alle tre logontyper overvåges. Dette er den eneste værdi, du kan se i Microsoft 365 gruppepostkasser.
- En administrator *har ikke* ændret de overvågede postkassehandlinger for nogen logontype på en brugerpostkasse eller en delt postkasse. Bemærk, at dette er standardtilstanden, efter at overvågning af postkassen er slået til som standard er aktiveret i din organisation.

Hvis en administrator nogensinde har ændret de postkassehandlinger, der overvåges for en logontype (ved hjælp af parametrene *AuditAdmin*, *AuditDelegate* eller *AuditOwner* på cmdlet'en **Set-Mailbox** ), vil egenskabsværdien være anderledes.

Værdien `Owner` for egenskaben *DefaultAuditSet* for en brugerpostkasse eller delt postkasse angiver f.eks.:

- Standardpostkassehandlingerne for ejeren af postkassen overvåges.
- De overvågede postkassehandlinger for logontyperne `Delegate` og `Admin` er blevet ændret fra standardhandlingerne.

En tom værdi for egenskaben *DefaultAuditSet* angiver, at postkassehandlinger for alle tre logontyper er blevet ændret i brugerpostkassen eller en delt postkasse.

Du kan finde flere oplysninger i afsnittet [Skift eller gendan postkassehandlinger, der er logført som standard](#change-or-restore-mailbox-actions-logged-by-default) i denne artikel

### <a name="display-the-mailbox-actions-that-are-being-logged-on-mailboxes"></a>Vis de postkassehandlinger, der logføres i postkasser

Hvis du vil se de postkassehandlinger, der i øjeblikket logføres på brugerpostkasser eller delte postkasser, skal du erstatte \<MailboxIdentity\> med navnet, aliaset, mailadressen eller brugerens hovednavn (brugernavn) for postkassen og køre en eller flere af følgende kommandoer i Exchange Online PowerShell.

> [!NOTE]
> Selvom du kan føje `-GroupMailbox` parameteren til følgende **Get-Mailbox-kommandoer** for Microsoft 365 gruppepostkasser, skal du ikke tro de værdier, der returneres. De standardhandlinger og statiske postkassehandlinger, der overvåges for Microsoft 365 gruppepostkasser, er beskrevet i afsnittet [Postkassehandlinger for Microsoft 365 gruppepostkasser](#mailbox-actions-for-microsoft-365-group-mailboxes) tidligere i denne artikel.

#### <a name="owner-actions"></a>Ejerhandlinger

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditOwner
```

#### <a name="delegate-actions"></a>Deleger handlinger

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditDelegate
```

#### <a name="admin-actions"></a>Administratorhandlinger

```PowerShell
Get-Mailbox -Identity <MailboxIdentity> | Select-Object -ExpandProperty AuditAdmin
```

## <a name="change-or-restore-mailbox-actions-logged-by-default"></a>Skift eller gendan postkassehandlinger, der som standard logføres

Som tidligere forklaret er en af de vigtigste fordele ved at have overvågning af postkasser som standard: Du behøver ikke at administrere de postkassehandlinger, der overvåges. Microsoft gør dette for dig, og vi tilføjer automatisk nye postkassehandlinger, der som standard skal overvåges, efterhånden som de udgives.

Din organisation kan dog blive bedt om at overvåge et andet sæt postkassehandlinger for brugerpostkasser og delte postkasser. Procedurerne i dette afsnit viser dig, hvordan du ændrer de postkassehandlinger, der overvåges for hver logontype, og hvordan du vender tilbage til de Microsoft-administrerede standardhandlinger.

> [!IMPORTANT]
> Hvis du bruger følgende procedurer til at tilpasse de postkassehandlinger, der er logget på brugerpostkasser eller delte postkasser, overvåges alle nye standardpostkassehandlinger, der udgives af Microsoft, ikke automatisk i disse postkasser. Du skal manuelt føje nye postkassehandlinger til din brugerdefinerede liste over handlinger.

### <a name="change-the-mailbox-actions-to-audit"></a>Skift postkassehandlinger, der skal overvåges

Du kan bruge parametrene *AuditAdmin*, *AuditDelegate* eller *AuditOwner* på **set-mailbox-cmdlet'en** til at ændre de postkassehandlinger, der overvåges for brugerpostkasser og delte postkasser (overvågede handlinger for Microsoft 365 gruppepostkasser kan ikke tilpasses).

Du kan bruge to forskellige metoder til at angive postkassehandlinger:

- *Erstat* (overskriv) de eksisterende postkassehandlinger ved hjælp af denne syntaks: `action1,action2,...actionN`.
- *Tilføj eller fjern* postkassehandlinger uden at påvirke andre eksisterende værdier ved hjælp af denne syntaks: `@{Add="action1","action2",..."actionN"}` eller `@{Remove="action1","action2",..."actionN"}`.

I dette eksempel ændres administratorpostkassens handlinger for postkassen med navnet "Gabriela Laureano" ved at overskrive standardhandlingerne med SoftDelete og HardDelete.

```PowerShell
Set-Mailbox -Identity "Gabriela Laureano" -AuditAdmin HardDelete,SoftDelete
```

I dette eksempel føjes handlingen MailboxLogin owner til den postkasse, laura@contoso.onmicrosoft.com.

```PowerShell
Set-Mailbox -Identity laura@contoso.onmicrosoft.com -AuditOwner @{Add="MailboxLogin"}
```

I dette eksempel fjernes stedfortræderhandlingen FlytTilDeletedItems for postkassen Teamdiskussion.

```PowerShell
Set-Mailbox -Identity "Team Discussion" -AuditDelegate @{Remove="MoveToDeletedItems"}
```

Uanset hvilken metode du bruger, har tilpasning af de overvågede postkassehandlinger på brugerpostkasser eller delte postkasser følgende resultater:

- For den logontype, du har tilpasset, administreres de overvågede postkassehandlinger ikke længere af Microsoft.
- Den brugerdefinerede logontype vises ikke længere i egenskabsværdien *DefaultAuditSet* for postkassen som [tidligere beskrevet](#verify-that-default-mailbox-actions-are-being-logged-for-each-logon-type).

### <a name="restore-the-default-mailbox-actions"></a>Gendan standardhandlingerne for postkassen

> [!NOTE]
> Følgende procedurer gælder ikke for Microsoft 365 gruppepostkasser (de er begrænset til standardhandlingerne, som beskrevet [her](#mailbox-actions-for-microsoft-365-group-mailboxes)).

Hvis du har tilpasset de postkassehandlinger, der overvåges i en brugerpostkasse eller en delt postkasse, kan du gendanne standardhandlingerne for postkassen for en eller alle logontyper ved hjælp af denne syntaks:

```PowerShell
Set-Mailbox -Identity <MailboxIdentity> -DefaultAuditSet <Admin | Delegate | Owner>
```

Du kan angive flere *DefaultAuditSet-værdier* adskilt af kommaer

I dette eksempel gendannes standardhandlingerne for overvågede postkasser for alle logontyper i postkassen mark@contoso.onmicrosoft.com.

```PowerShell
Set-Mailbox -Identity mark@contoso.onmicrosoft.com -DefaultAuditSet Admin,Delegate,Owner
```

I dette eksempel gendannes standardhandlingerne for overvågede postkasser for logontypen Administrator på postkassen chris@contoso.onmicrosoft.com, men de brugerdefinerede overvågede postkassehandlinger for logontyperne Stedfortræder og Ejer bevares.

```PowerShell
Set-Mailbox -Identity chris@contoso.onmicrosoft.com -DefaultAuditSet Admin
```

Gendannelse af standardhandlinger i overvågede postkasser for en logontype har følgende resultater:

- Den aktuelle liste over postkassehandlinger erstattes af standardpostkassehandlinger for logontypen.
- Alle nye postkassehandlinger, der udgives af Microsoft, føjes automatisk til listen over overvågede handlinger for logontypen.
- Egenskabsværdien *DefaultAuditSet* for postkassen opdateres, så den omfatter den gendannede logontype.

## <a name="turn-off-mailbox-auditing-on-by-default-for-your-organization"></a>Slå overvågning af postkasser til som standard for din organisation

Du kan slå overvågning af postkasser til som standard for hele organisationen ved at køre følgende kommando i Exchange Online PowerShell:

```PowerShell
Set-OrganizationConfig -AuditDisabled $true
```

Deaktivering af overvågning af postkasser er som standard aktiveret med følgende resultater:

- Overvågning af postkasser er deaktiveret for din organisation.
- Fra det tidspunkt, hvor du deaktiverede overvågning af postkasser som standard, overvåges ingen postkassehandlinger, selvom overvågning er aktiveret for en postkasse (egenskaben *AuditEnabled* i postkassen er **Sand**).
- Overvågning af postkasser er ikke aktiveret for nye postkasser, og angivelse af egenskaben *AuditEnabled* for en ny eller eksisterende postkasse til **Sand** ignoreres.
- Alle indstillinger for overvågning af postkasser tilsidesætter tilknytninger (konfigureret ved hjælp af **Set-MailboxAuditBypassAssociation-cmdlet'en** ) ignoreres.
- Eksisterende overvågningsposter i postkassen bevares, indtil aldersgrænsen for overvågningsloggen for posten udløber.

### <a name="turn-on-mailbox-auditing-on-by-default"></a>Slå overvågning af postkasser til som standard

Hvis du vil slå overvågning af postkasser til igen for din organisation, skal du køre følgende kommando i Exchange Online PowerShell:

```PowerShell
Set-OrganizationConfig -AuditDisabled $false
```

## <a name="bypass-mailbox-audit-logging"></a>Spring logføring af postkassens overvågning over

I øjeblikket kan du ikke deaktivere overvågning af postkasser for bestemte postkasser, når overvågning af postkasser som standard er slået til i din organisation. Indstillingen af egenskaben *AuditEnabled* for postkassen til **Falsk** ignoreres f.eks.

Du kan dog stadig bruge **Set-MailboxAuditBypassAssociation-cmdlet'en** i Exchange Online PowerShell til at forhindre, at *alle* handlinger i postkassen af de angivne brugere logføres, uanset hvor handlingerne forekommer. Eksempel:

- Handlinger for postkasseejeren, der udføres af de forbigåede brugere, logføres ikke.
- Stedfortræderhandlinger, der udføres af de forbigåede brugere på andre brugeres postkasser (herunder delte postkasser), logføres ikke.
- Administratorhandlinger, der udføres af de forbigåede brugere, logføres ikke.

Hvis du vil tilsidesætte logføring af overvågning af postkassen for en bestemt bruger, skal du erstatte \<MailboxIdentity\> med brugerens navn, mailadresse, alias eller brugerens hovednavn (brugernavn) og køre følgende kommando:

```PowerShell
Set-MailboxAuditBypassAssociation -Identity <MailboxIdentity> -AuditByPassEnabled $true
```

Kør følgende kommando for at kontrollere, at overvågning tilsidesættes for den angivne bruger:

```PowerShell
Get-MailboxAuditBypassAssociation -Identity <MailboxIdentity> | Format-List AuditByPassEnabled
```

Værdien **Sand** angiver, at logføring af overvågning af postkasser tilsidesættes for brugeren.

## <a name="more-information"></a>Flere oplysninger

- Selvom logføring af overvågning af postkasser som standard er aktiveret for alle organisationer, er det kun brugere med [licenser, der indeholder funktionen Avanceret overvågning](auditing-solutions-overview.md#advanced-audit-1) (samlet kaldet *E5/A5/G5-licenser*), der returnerer hændelser i [overvågningsloggen for postkasser i søgninger i Microsoft 365 Overholdelsescenter](search-the-audit-log-in-security-and-compliance.md) eller via [API'en](/office/office-365-management-api/office-365-management-activity-api-reference) **til Office 365 administration af aktivitet som standard**.

  Hvis du vil hente overvågningslogposter for postkasser for brugere uden E5/A5/G5-licenser, kan du bruge en af følgende løsninger:

  - Aktivér overvågning af postkasser manuelt på de berørte brugerpostkasser ved at køre følgende kommando: `Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true`. Når du har aktiveret overvågning af postkassen i postkassen, kan du bruge søgninger i overvågningsloggen i Microsoft 365 Overholdelsescenter eller via API'en til Office 365 administrationsaktivitet.

    > [!NOTE]
    > Hvis overvågning af postkassen allerede ser ud til at være aktiveret i postkassen, men dine søgninger ikke returnerer nogen resultater, skal du ændre værdien af parameteren *AuditEnabled* til `$false` og derefter tilbage til `$true`.

  - Brug følgende cmdlet'er i Exchange Online PowerShell:
    - [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) for at søge i postkassens overvågningslog for bestemte brugere.
    - [New-MailboxAuditLogSearch](/powershell/module/exchange/new-mailboxauditlogsearch) til at søge i postkassens overvågningslog for bestemte brugere og få resultaterne sendt via mail til angivne modtagere.

  - Brug Exchange Administration (EAC) i Exchange Online til at udføre følgende handlinger:
    - [Eksportér overvågningslogge for postkasse](/Exchange/security-and-compliance/exchange-auditing-reports/export-mailbox-audit-logs)
    - [Kør en rapport over adgang til en postkasse, der ikke er ejer](/Exchange/security-and-compliance/exchange-auditing-reports/non-owner-mailbox-access-report)

- Posterne i overvågningsloggen for postkassen bevares som standard i 90 dage, før de slettes. Du kan ændre aldersgrænsen for overvågningslogposter ved hjælp af parameteren *AuditLogAgeLimit* i **Set-Mailbox-cmdlet'en** i Exchange Online PowerShell. Hvis du øger denne værdi, kan du dog ikke søge efter hændelser, der er ældre end 90 dage i overvågningsloggen.

  Hvis du øger aldersgrænsen, skal du bruge cmdlet'en [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) i Exchange Online PowerShell til at søge i brugerens overvågningslog for postkasser efter poster, der er ældre end 90 dage.

- Hvis du har ændret egenskaben *AuditLogAgeLimit* for en postkasse, før overvågning af postkassen som standard er slået til for organisationen, ændres postkassens eksisterende aldersgrænse for overvågningsloggen ikke. Overvågning af postkasser på påvirker med andre ord som standard ikke den aktuelle aldersgrænse for overvågningsposter i postkasser.

- Hvis du vil ændre værdien *for AuditLogAgeLimit* i en Microsoft 365 gruppepostkasse, skal du medtage `-GroupMailbox` parameteren i kommandoen **Set-Mailbox**.

- Overvågningslogposter i postkassen gemmes i en undermappe (kaldet *Overvågninger*) i mappen Gendanbare elementer i hver brugers postkasse. Vær opmærksom på følgende ting i forbindelse med overvågningsposter i postkassen og mappen Elementer, der kan gendannes:

  - Overvågningsposter i postkasser tæller i forhold til lagerkvoten for mappen Gendanbare elementer, som som standard er 30 GB (advarselskvoten er 20 GB). Lagerkvoten øges automatisk til 100 GB (med en advarselskvote på 90 GB), når:
    - En venteposition placeres i en postkasse.
    - Postkassen er tildelt en opbevaringspolitik i Overholdelsescenter.

  - Overvågningsposter i postkasser tæller også med i [mappegrænsen for mappen Elementer, der kan gendannes](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#mailbox-folder-limits). Der kan maksimalt gemmes 3 millioner elementer (overvågningsposter) i undermappen Overvågninger.

    > [!NOTE]
    > Det er usandsynligt, at overvågning af postkasser som standard påvirker lagerkvoten eller mappegrænsen for mappen Gendanbare elementer.

    - Du kan køre følgende kommando i Exchange Online PowerShell for at få vist størrelsen og antallet af elementer i undermappen Overvågning i mappen Gendanbare elementer:

      ```PowerShell
      Get-MailboxFolderStatistics -Identity <MailboxIdentity> -FolderScope RecoverableItems | Where-Object {$_.Name -eq 'Audits'} | Format-List FolderPath,FolderSize,ItemsInFolder
      ```

    - Du kan ikke få direkte adgang til en overvågningslogpost i mappen Gendanbare elementer. Du kan i stedet bruge cmdlet'en **Search-MailboxAuditLog** eller søge i overvågningsloggen for at finde og få vist overvågningsposter i postkassen.

- Hvis en postkasse er sat i venteposition eller tildelt en opbevaringspolitik i Overholdelsescenter, bevares overvågningslogposter stadig i den varighed, der er defineret af egenskaben *AuditLogAgeLimit* for postkassen (som standard 90 dage). Hvis du vil bevare overvågningslogposter længere for postkasser i venteposition, skal du øge værdien for *AuditLogAgeLimit* for postkassen.

- I et multi-geo-miljø understøttes overvågning af postkasser på tværs af geografiske områder ikke. Hvis en bruger f.eks. er tildelt tilladelser til at få adgang til en delt postkasse på en anden geografisk placering, logføres de postkassehandlinger, der udføres af den pågældende bruger, ikke i postkassens overvågningslog for den delte postkasse. Exchange administrationsovervågningshændelser er i øjeblikket kun tilgængelige for standardplaceringen.
