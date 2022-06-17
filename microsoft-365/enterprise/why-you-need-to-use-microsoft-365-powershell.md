---
title: Derfor skal du bruge PowerShell til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: ITPro
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: admindeeplinkEXCHANGE
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Oversigt: Forstå, hvorfor du skal bruge PowerShell til at administrere Microsoft 365 i nogle tilfælde mere effektivt og i andre tilfælde af nødvendighed.'
ms.openlocfilehash: 0da00ffe3c492b3bac3da9f435ece89219b4113f
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139357"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>Derfor skal du bruge PowerShell til Microsoft 365

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Med Microsoft 365 Administration kan du administrere dine Microsoft 365 brugerkonti og -licenser. Du kan også administrere dine Microsoft 365 tjenester, f.eks. Exchange Online, Teams og SharePoint Online. Hvis du i stedet bruger PowerShell til at administrere disse tjenester, kan du bruge kommandolinje- og scriptsprogmiljøet til hastighed, automatisering og yderligere funktioner.

I denne artikel kan du se, hvordan du bruger PowerShell til at administrere Microsoft 365 til:

- Vis yderligere oplysninger, som du ikke kan se i Microsoft 365 Administration

- Konfigurer kun funktioner og indstillinger med PowerShell

- Udfører massehandlinger

- Filtrer data

- Udskriv eller gem data

- Administrer på tværs af tjenester

Husk, at PowerShell til Microsoft 365 er et sæt moduler til Windows PowerShell, som er et kommandolinjemiljø til Windows-baserede tjenester og platforme. Dette miljø opretter et command-shell-sprog, der kan udvides med yderligere moduler. Den gør det muligt at udføre enkle eller komplekse kommandoer eller scripts. Når du f.eks. har installeret PowerShell til Microsoft 365 moduler og oprettet forbindelse til dit Microsoft 365-abonnement, kan du køre følgende kommando for at få vist alle brugerpostkasser for Microsoft Exchange Online:

```powershell
Get-Mailbox
```

Du kan også hente listen over postkasser ved hjælp af Microsoft 365 Administration men det er ikke nemt at tælle elementerne på alle listerne for alle webstederne for alle dine webapps.

PowerShell til Microsoft 365 er udviklet til at hjælpe dig med at administrere Microsoft 365 og ikke erstatte Microsoft 365 Administration. Administratorer skal kunne bruge PowerShell til Microsoft 365 fordi der er nogle konfigurationsprocedurer, der kun kan udføres via PowerShell til Microsoft 365 kommandoer. I disse tilfælde skal du vide, hvordan du:

- Installér PowerShell til Microsoft 365 moduler (udføres kun én gang for hver administratorcomputer).

- Forbind til dit Microsoft 365-abonnement (én gang for hver PowerShell-session).

- Indsaml de oplysninger, der er nødvendige for at køre den påkrævede PowerShell til Microsoft 365 kommandoer.

- Kør PowerShell for Microsoft 365 kommandoer.

Når du har lært disse grundlæggende færdigheder, behøver du ikke at angive brugerne af din postkasse ved hjælp af kommandoen **Get-Mailbox** . Du behøver heller ikke at forstå, hvordan du opretter en ny kommando som den kommando, der er nævnt tidligere, for at tælle alle elementerne på alle listerne for alle webstederne for alle dine webapps. Microsoft og community'et af administratorer kan hjælpe dig med disse opgaver efter behov.

## <a name="powershell-for-microsoft-365-can-reveal-information-that-you-cant-see-with-the-microsoft-365-admin-center"></a>PowerShell til Microsoft 365 kan vise oplysninger, som du ikke kan se med Microsoft 365 Administration

I Microsoft 365 Administration vises mange nyttige oplysninger. Men det viser ikke alle de mulige oplysninger, som Microsoft 365 gemmer om brugere, licenser, postkasser og websteder. Her er et eksempel for *brugere og grupper* i Microsoft 365 Administration:

![Eksempel på visning af brugere og grupper i Microsoft 365 Administration.](../media/o365-powershell-users-and-groups.png)

Denne visning indeholder de oplysninger, du har brug for i mange tilfælde. Der er dog tidspunkter, hvor du har brug for mere. F.eks. afhænger Microsoft 365 licensering (og de Microsoft 365 funktioner, der er tilgængelige for en bruger), delvist af brugerens geografiske placering. De politikker og funktioner, du kan udvide til en bruger, der bor i USA, er muligvis ikke de samme som dem, du kan udvide til en bruger i Indien eller Belgien. Følg disse trin i Microsoft 365 Administration for at bestemme en brugers geografiske placering:

1. Dobbeltklik på brugerens **viste navn**.

2. Vælg **detaljer** i visningsruden med brugeregenskaber.

3. Vælg **flere oplysninger** i visningen med detaljer.

4. Rul, indtil du finder overskriften **Land eller område**:

     ![Eksempel på områdeoplysningerne for en bruger i Microsoft 365 Administration.](../media/o365-powershell-usage-location.png)

5. Skriv brugerens viste navn og placering på et stykke papir, eller kopiér og indsæt det i Notesblok.

Du skal gentage denne procedure for hver bruger. Hvis du har mange brugere, kan denne proces være kedelig. Med PowerShell til Microsoft 365 kan du få vist disse oplysninger for alle dine brugere ved hjælp af følgende kommando:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell modul og cmdlet'er, der har *Msol* i deres navn. Du skal køre disse cmdlet'er fra Windows PowerShell.
>

Her er et eksempel på resultaterne:

```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

Fortolkningen af denne PowerShell-kommando er: Hent alle brugerne i det aktuelle Microsoft 365-abonnement (**Get-AzureADUser**), men vis kun navn og placering for hver bruger (**Vælg DisplayName, UsageLocation**).

Da PowerShell til Microsoft 365 understøtter et command-shell-sprog, kan du yderligere manipulere de oplysninger, der hentes med kommandoen **Get-AzureADUser**. Det kan f.eks. være, at du vil sortere disse brugere efter deres placering, gruppere alle de brasilianske brugere sammen, alle de USA brugere samlet osv. Her er kommandoen:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

Her er et eksempel på resultaterne:

```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

Fortolkningen af denne PowerShell-kommando er: Hent alle brugerne i det aktuelle Microsoft 365-abonnement, men vis kun navn og placering for hver bruger, og sortér dem først efter deres placering og derefter deres navn (**Sort UsageLocation, DisplayName**).

Du kan også bruge yderligere filtrering. Hvis du f.eks. kun vil have vist oplysninger om brugere, der er baseret i Brasilien, skal du bruge denne kommando:

```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation
```

Her er et eksempel på resultaterne:

```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

Fortolkningen af denne PowerShell-kommando er: Hent alle brugerne i det aktuelle Microsoft 365 abonnement, hvis placering er Brasilien (**Hvor {$\_. UsageLocation -eq "BR"}**), og vis derefter navnet og placeringen for hver bruger.

 **En note om store domæner**

Hvis du har et stort domæne med titusinder af brugere, kan det føre til begrænsning at prøve nogle af de eksempler, vi viser i denne artikel. Baseret på faktorer som beregningskraft og tilgængelig netværksbåndbredde forsøger du muligvis at gøre for meget på én gang. Store organisationer vil måske opdele nogle af disse PowerShell-handlinger i to kommandoer.

Følgende kommando returnerer f.eks. alle brugerkontiene og viser navn og placering for hver enkelt:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

Det fungerer fint for mindre domæner. Men i en stor organisation kan det være en god idé at opdele handlingen i to kommandoer: én kommando til at gemme brugerkontooplysningerne i en variabel og en anden til at vise de nødvendige oplysninger. Her er et eksempel:

```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

Fortolkningen af dette sæt PowerShell-kommandoer er:
1. Hent alle brugerne i det aktuelle Microsoft 365-abonnement, og gem oplysningerne i en variabel med navnet $x (**$x = Get-AzureADUser**).
1.  Vis indholdet af variablen *$x*, men medtag kun navn og placering for hver bruger (**$x | Vælg DisplayName, UsageLocation**).

## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>Microsoft 365 indeholder funktioner, som du kun kan konfigurere med PowerShell til Microsoft 365

Microsoft 365 Administration er beregnet til at give adgang til almindelige, nyttige administrative opgaver, der gælder for de fleste miljøer. Med andre ord er Microsoft 365 Administration designet, så den typiske administrator kan udføre de mest almindelige administrationsopgaver. Men der er nogle opgaver, der ikke kan udføres i Administration.

Skype for Business Online Administration indeholder f.eks. et par muligheder for at oprette brugerdefinerede mødeindkaldelser:

![Eksempel på visning af brugerdefinerede mødeindkaldelser i Skype for Business Online Administration center.](../media/o365-powershell-meeting-invitation.png)

Med disse indstillinger kan du føje et strejf af tilpasning og professionalisme til mødeindkaldelser. Men der er mere i indstillinger for mødekonfiguration end blot oprettelse af brugerdefinerede mødeinvitationer. Møder tillader f.eks.som standard:

- Anonyme brugere får automatisk adgang til hvert møde.

- Deltagere, der skal registrere mødet.

- Alle brugere fra din organisation skal udpeges som præsentationsværter, når de deltager i mødet.

Disse indstillinger er ikke tilgængelige fra Skype for Business Online Administration. Du kan styre dem fra PowerShell til Microsoft 365. Her er en kommando, der deaktiverer disse tre indstillinger:

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> Hvis du vil køre denne kommando, skal du installere [Skype for Business Online PowerShell-modulet](/skypeforbusiness/set-up-your-computer-for-windows-powershell/download-and-install-the-skype-for-business-online-connector).

Fortolkningen af denne PowerShell-kommando er:

1. I indstillingerne for nye Skype for Business Onlinemøder (**Set-CsMeetingConfiguration**) skal du deaktivere, så anonyme brugere kan få automatisk adgang til møder (**-AdmitAnonymousUsersByDefault $False**).
2.  Deaktiver deltagernes mulighed for at optage møder (**-AllowConferenceRecording $False**).
3. Angiv ikke alle brugere fra din organisation som præsentationsværter (**-DesignateAsPresenter "Ingen"**).

Kør denne kommando for at gendanne disse standardindstillinger (aktivér indstillingerne):

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

Der er også andre lignende scenarier, og derfor skal administratorer vide, hvordan de skal køre PowerShell til Microsoft 365 kommandoer.

## <a name="powershell-for-microsoft-365-is-great-for-bulk-operations"></a>PowerShell til Microsoft 365 er velegnet til massehandlinger

Visuelle grænseflader som Microsoft 365 Administration er mest værdifulde, når du har en enkelt handling at udføre. Hvis du f.eks. har brug for at deaktivere én brugerkonto, kan du bruge Administration til hurtigt at finde og fjerne markeringen i et afkrydsningsfelt. Det kan være nemmere end at udføre en lignende handling i PowerShell.

Men hvis du er nødt til at ændre mange ting eller nogle valgte ting inden for et stort sæt andre ting, er Microsoft 365 Administration muligvis ikke det bedste værktøj. Lad os f.eks. sige, at du skal ændre præfikset på tusindvis af telefonnumre eller fjerne den specifikke bruger *Ken Myer* fra alle dine SharePoint Online-websteder. Hvordan ville du gøre det i Microsoft 365 Administration?

I det sidste eksempel kan du sige, at du har flere hundrede SharePoint Online-websteder, og du ved ikke, hvilke Ken Meyer er medlem af. Du skal starte på Microsoft 365 Administration og derefter udføre denne procedure for hvert websted:

1. Vælg **WEBSTEDETs URL-adresse** .

2. I feltet **Egenskaber for gruppe af websteder** skal du vælge linket **Webstedsadresse** for at åbne webstedet.

3. Vælg **Del** på webstedet.

4. I dialogboksen **Del** skal du vælge det link, der viser alle de brugere, der har tilladelser til webstedet:

     ![Eksempel på visning af medlemmerne af et SharePoint Online-websted i SharePoint Online Administration center.](../media/o365-powershell-view-permissions.png)

5. Vælg **Avanceret** i dialogboksen **Delt med**.

6. Rul ned på listen over brugere, find og vælg Ken Myer (hvis han har tilladelser til webstedet), og vælg derefter **Fjern brugertilladelser**.

Dette ville tage *lang* tid for flere hundrede steder.

Du kan også køre følgende kommando i PowerShell for at Microsoft 365 at fjerne Ken Myer fra alle dine websteder:

```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> Denne kommando kræver, at du installerer [SharePoint Online PowerShell-modulet](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

Fortolkningen af denne PowerShell-kommando er: Hent alle de SharePoint websteder i det aktuelle Microsoft 365-abonnement (**Get-SPOSite**), og fjern Ken Meyer fra listen over brugere, der har adgang til det (**ForEach {Remove-SPOUser -Site $\_. Url -LoginName "kenmyer\@litwareinc.com"}**).

Vi beder Microsoft 365 om at fjerne Ken Meyer fra alle websteder, herunder dem, han ikke har adgang til. Så resultaterne viser fejl for de websteder, som han ikke har adgang til. Vi kan bruge en yderligere betingelse på denne kommando til kun at fjerne Ken Meyer fra de websteder, der har ham på deres logonliste. Men de returnerede fejl skader ikke selve webstederne. Det kan tage et par minutter at køre denne kommando på hundredvis af websteder i stedet for at arbejde i timer i Microsoft 365 Administration.

Her er et andet eksempel på en massehandling. Brug denne kommando til at føje *Bonnie Kearney*, der er en ny SharePoint administrator, til alle websteder i organisationen:

```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

Fortolkningen af denne PowerShell-kommando er: Hent alle de SharePoint websteder i det aktuelle Microsoft 365-abonnement, og for hvert websted giver Bonnie Kearney adgang ved at føje hendes logonnavn til gruppen Medlemmer på webstedet (**ForEach {Add-SPOUser -Site $\_. Url -LoginName "bkearney\@litwareinc.com" -Gruppe "Medlemmer"}**).

## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>PowerShell til Microsoft 365 er god til filtrering af data

Med Microsoft 365 Administration kan du filtrere dine data på flere måder, så du nemt kan finde et målrettet undersæt af oplysninger. For eksempel gør Exchange det nemt at filtrere på praktisk talt enhver egenskab i en brugerpostkasse. Her er f.eks. listen over postkasser for alle de brugere, der bor i byen Bloomington:

![Eksempel på, hvordan du udfører en avanceret søgning i Microsoft 365 Administration for listen over postkasser for alle de brugere, der bor i Bloomington.](../media/o365-powershell-advanced-search.png)

Med <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> kan du også kombinere filterkriterier. Du kan f.eks. finde postkasserne for alle de personer, der bor i Bloomington og arbejder i økonomiafdelingen.

Men der er begrænsninger for, hvad du kan gøre i Exchange Administration center. Du kunne f.eks. ikke så nemt finde postkasserne for personer, der bor i Bloomington *eller* San Diego, eller postkasserne for alle dem, der ikke bor i Bloomington.

Du kan bruge følgende PowerShell til Microsoft 365 kommando til at få en liste over postkasser for alle de personer, der bor i Bloomington eller San Diego:

```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

Her er et eksempel på resultaterne:

```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

Fortolkningen af denne PowerShell-kommando er: Hent alle brugere i det aktuelle Microsoft 365-abonnement, der har en postkasse i byen San Diego eller Bloomington (**Hvor {$\_. RecipientTypeDetails -eq "UserMailbox" -og ($\_. City -eq "San Diego" -eller $\_. City -eq "Bloomington")}**), og vis derefter navnet og byen for hver (**Vælg DisplayName, City**).

Og her er kommandoen til at angive alle postkasser for folk, der bor hvor som helst undtagen Bloomington:

```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

Her er et eksempel på resultaterne:

```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

Fortolkningen af denne PowerShell-kommando er: Hent alle brugere i det aktuelle Microsoft 365-abonnement, som har en postkasse, der ikke er placeret i byen Bloomington (**Hvor {$\_. RecipientTypeDetails -eq "UserMailbox" -og $\_. City -ne "Bloomington"}**), og vis derefter navnet og byen for hver enkelt.

### <a name="use-wildcards"></a>Brug jokertegn

Du kan også bruge jokertegn i dine PowerShell-filtre til at matche en del af et navn. Lad os f.eks. antage, at du leder efter en brugerkonto. Alt du kan huske er, at brugerens efternavn var *Anderson* eller måske *Henderson* eller *Jorgenson*.

Du kan spore brugeren i Microsoft 365 Administration ved hjælp af søgeværktøjet og udføre tre forskellige søgninger:

- Et til  *Anderson*

- En til  *Henderson*

- En til  *Jorgenson*

Da alle tre af disse navne ender på "søn", kan du bede PowerShell om at vise alle de brugere, hvis navn ender på "søn". Her er kommandoen:

```powershell
Get-User -Filter '{LastName -like "*son"}'
```

Fortolkningen af denne PowerShell-kommando er: Hent alle brugere i det aktuelle Microsoft 365-abonnement, men brug et filter, der kun viser de brugere, hvis efternavne ender på "søn" (**-Filter '{LastName -like "\*son"}'**). \* står for et vilkårligt sæt tegn, som er bogstaver i brugerens efternavn.

## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>PowerShell til Microsoft 365 gør det nemt at udskrive eller gemme data

Med Microsoft 365 Administration kan du få vist lister over data. Her er et eksempel på Skype for Business Online Administration, der viser en liste over brugere, der er blevet aktiveret til Skype for Business Online:

![Eksempel på Skype for Business Online Administration center, der viser en liste over brugere, der er blevet aktiveret til Skype for Business Online.](../media/o365-powershell-lync-users.png)

Hvis du vil gemme oplysningerne i en fil, skal du indsætte dem i et dokument eller Microsoft Excel regneark. Begge tilfælde kan kræve yderligere formatering. Derudover giver Microsoft 365 Administration ikke mulighed for at udskrive den viste liste direkte.

Heldigvis kan du bruge PowerShell til ikke kun at vise listen, men til at gemme den i en fil, der nemt kan importeres til Excel. Her er et eksempel på en kommando til at gemme Skype for Business Online-brugerdata i en fil med kommaseparerede værdier (CSV), som derefter nemt kan importeres som en tabel i et Excel regneark:

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

Her er et eksempel på resultaterne:

![Eksempel på en tabel, der er importeret til et Excel regneark til Skype for Business Online-brugerdata, som blev gemt i en fil med kommaseparerede værdier.](../media/o365-powershell-data-in-excel.png)

Denne PowerShell-kommando fortolkes således: Hent alle Skype for Business Online-brugere i det aktuelle Microsoft 365-abonnement (**Get-CsOnlineUser**), hent kun brugernavnet, UPN'et og placeringen (**Select DisplayName, UserPrincipalName, UsageLocation**), og gem derefter disse oplysninger i en CSV-fil med navnet C:\\Logs\\SfBUsers.csv (**Export-Csv -Path "C:\\Logs\\ SfBUsers.csv" -NoTypeInformation**).

Du kan også bruge indstillinger til at gemme listen som en XML-fil eller en HTML-side. Med yderligere PowerShell-kommandoer kan du faktisk gemme den direkte som en Excel fil med den ønskede brugerdefinerede formatering.

Du kan også sende outputtet fra en PowerShell-kommando, der viser en liste direkte til standardprinteren i Windows. Her er et eksempel på en kommando:

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

Sådan ser dit udskrevne dokument ud:

![Eksempel på et udskrevet dokument, der var resultatet af en PowerShell-kommando, der blev sendt direkte til standardprinteren i Windows.](../media/o365-powershell-printed-data.png)

Denne PowerShell-kommando fortolkes således: Hent alle Skype for Business Online-brugere i det aktuelle Microsoft 365-abonnement, hent kun brugernavnet, UPN og placeringen, og send derefter disse oplysninger til standardprinteren Windows (**Out-Printer**).

Det udskrevne dokument har samme enkle formatering som visningen i PowerShell-kommandovinduet. Hvis du vil have en papirkopi, skal du blot tilføje **| Out-Printer** til slutningen af kommandoen.

## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>Med PowerShell til Microsoft 365 kan du administrere på tværs af serverprodukter

De komponenter, der udgør Microsoft 365, er designet til at arbejde sammen. Lad os f.eks. antage, at du føjer en ny bruger til Microsoft 365, og du angiver oplysninger som brugerens afdeling og telefonnummer. Disse oplysninger vil derefter være tilgængelige, hvis du får adgang til brugerens oplysninger i nogen af Microsoft 365-tjenesterne: Skype for Business Online, Exchange eller SharePoint.

Men det er til almindelige oplysninger, der strækker sig over pakken af produkter. Produktspecifikke oplysninger, f.eks. oplysninger om en brugers Exchange postkasse, er normalt ikke tilgængelige på tværs af pakken. Oplysninger om, hvorvidt en brugers postkasse er aktiveret eller ej, er f.eks. kun tilgængelige i Exchange Administration.

Lad os antage, at du vil oprette en rapport, der viser følgende oplysninger for alle dine brugere:

- Brugerens viste navn

- Om brugeren har licens til Microsoft 365

- Angiver, om brugerens Exchange postkasse er blevet aktiveret

- Angiver, om brugeren er aktiveret for Skype for Business Online

Du kan ikke nemt oprette en sådan rapport i Microsoft 365 Administration. Du skal i stedet oprette et separat dokument for at gemme oplysningerne, f.eks. et Excel regneark. Hent derefter alle brugernavne og licensoplysninger fra Microsoft 365 Administration, hent oplysninger om postkasser fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>, hent Skype for Business Online-oplysninger fra Skype for Business Online-Administration  og derefter kombinere disse oplysninger.

Alternativet er at bruge et PowerShell-script til at kompilere rapporten for dig.

Følgende eksempelscript er mere kompliceret end de kommandoer, du har set indtil videre i denne artikel. Men det viser potentialet ved at bruge PowerShell til at oprette informationsvisninger, der er svære at undgå. Her er scriptet til kompilering og visning af den liste, du skal bruge:

```powershell
$x = Get-AzureADUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

Her er et eksempel på resultaterne:

```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

Fortolkningen af dette PowerShell-script er:

1. Hent alle brugerne i det aktuelle Microsoft 365-abonnement, og gem oplysningerne i en variabel med navnet *$x* (**$x = Get-AzureADUser**).
1. Start en løkke, der kører over alle brugere i variablen $x (**foreach ($i i $x)**).
1. Definer en variabel med navnet *$y* , og gem oplysningerne om brugerens postkasse i den (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).
1. Føj en ny egenskab til brugeroplysningerne med navnet *IsMailBoxEnabled*. Angiv den til værdien af egenskaben IsMailBoxEnabled for brugerens postkasse (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).
1. Definer en variabel med navnet *$y*, og gem brugerens Skype for Business Online-oplysninger i den (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).
1. Føj en ny egenskab til brugeroplysningerne med navnet *EnabledForSfB*. Angiv den til værdien af egenskaben Enabled for brugerens Skype for Business Online-oplysninger (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).
1. Vis listen over brugere, men medtag kun deres navn, om de er licenseret, og de to nye egenskaber, der angiver, om deres postkasse er aktiveret, og om de er aktiveret til Skype for Business Online (**$x | Vælg DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).

## <a name="see-also"></a>Se også

[Kom i gang med PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Brug Windows PowerShell til at oprette rapporter i Microsoft 365](use-windows-powershell-to-create-reports-in-microsoft-365.md)
