---
title: Derfor skal du bruge PowerShell til Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: 'Oversigt: Forstå, hvorfor du skal bruge PowerShell til at administrere Microsoft 365, i nogle tilfælde mere effektivt og i andre tilfælde nødvendigvis.'
ms.openlocfilehash: 11b84fbd10d2a7180637d377c219502e6ffb00aa
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63594211"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>Derfor skal du bruge PowerShell til Microsoft 365

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Med Microsoft 365 Administration kan du administrere dine Microsoft 365 brugerkonti og licenser. Du kan også administrere dine Microsoft 365 tjenester, f.eks. Exchange Online, Teams og SharePoint Online. Hvis du i stedet bruger PowerShell til at administrere disse tjenester, kan og drage fordel af kommandolinje- og scripting-sprogmiljøet for hastighed, automatisering og yderligere funktioner.

Denne artikel viser, hvordan du bruger PowerShell til at administrere Microsoft 365 til:

- Vis yderligere oplysninger, du ikke kan se i Microsoft 365 Administration

- Konfigurer funktioner og indstillinger kun muligt med PowerShell

- Udføre massehandlinger

- Filtrere data

- Udskrive eller gemme data

- Administrer på tværs af tjenester

Husk på, at PowerShell til Microsoft 365 er et sæt moduler til Windows PowerShell, som er et kommandolinjemiljø til Windows-baserede tjenester og platforme. Dette miljø opretter et kommando-shell-sprog, der kan udvides med flere moduler. Det er en metode til at udføre simple eller komplekse kommandoer eller scripts. Når du f.eks. har installeret PowerShell til Microsoft 365-moduler og har forbindelse til dit Microsoft 365-abonnement, kan du køre følgende kommando for at få vist alle brugernes postkasser til Microsoft Exchange Online:

```powershell
Get-Mailbox
```

Du kan også få listen over postkasser ved hjælp af Microsoft 365 Administration men det er ikke nemt at tælle elementerne på alle listerne for alle webstederne for alle dine webapps.

PowerShell til Microsoft 365 designet til at hjælpe dig med at administrere Microsoft 365 ikke at erstatte Microsoft 365 Administration. Administratorer skal kunne bruge PowerShell til Microsoft 365, fordi der er nogle konfigurationsprocedurer, der kun kan udføres via PowerShell til Microsoft 365-kommandoer. I disse tilfælde skal du vide, hvordan du:

- Installer PowerShell til Microsoft 365-moduler (kun én gang for hver administratorcomputer).

- Forbind dit Microsoft 365 -abonnement (én gang for hver PowerShell-session).

- Indsaml de oplysninger, der er nødvendige for at køre de nødvendige PowerShell Microsoft 365-kommandoer.

- Kør PowerShell til Microsoft 365-kommandoer.

Når du har lært disse grundlæggende færdigheder, behøver du ikke at vise dine postkassebrugere ved hjælp af **kommandoen Get-Mailbox** . Du behøver heller ikke at forstå, hvordan du opretter en ny kommando, f.eks. den kommando, der tidligere er blevet citeret, for at tælle alle elementerne på alle listerne for alle webstederne for alle dine webapps. Microsoft og community'et af administratorer kan hjælpe dig med sådanne opgaver efter behov.

## <a name="powershell-for-microsoft-365-can-reveal-information-that-you-cant-see-with-the-microsoft-365-admin-center"></a>PowerShell til Microsoft 365 kan vise oplysninger, du ikke kan se med Microsoft 365 Administration

Den Microsoft 365 Administration viser mange nyttige oplysninger. Men den viser ikke alle de mulige oplysninger, Microsoft 365 gemmer om brugere, licenser, postkasser og websteder. Her er et eksempel for *brugere og grupper* i Microsoft 365 Administration:

![Eksempel på visning af brugere og grupper i Microsoft 365 Administration.](../media/o365-powershell-users-and-groups.png)

Denne visning indeholder de oplysninger, du skal bruge i mange tilfælde. Der er dog tidspunkter, hvor du har brug for mere. Licens Microsoft 365 (og de Microsoft 365 funktioner, der er tilgængelige for en bruger) afhænger f.eks. delvist af brugerens geografiske placering. De politikker og funktioner, du kan udvide til en bruger, der bor i USA, er muligvis ikke de samme som dem, du kan udvide til en bruger i Indien eller Belgien. Følg disse trin i Microsoft 365 Administration for at bestemme en brugers geografiske placering:

1. Dobbeltklik på brugerens viste **navn**.

2. Vælg detaljer i visningsruden for **brugeregenskaber**.

3. Vælg yderligere detaljer i visningen **af detaljer**.

4. Rul ned, indtil du finder **overskriften Land eller område**:

     ![Eksempel på områdeoplysninger for en bruger i Microsoft 365 Administration.](../media/o365-powershell-usage-location.png)

5. Skriv brugerens viste navn og placering på et stykke papir, eller kopiér og indsæt det i Notesblok.

Du skal gentage denne procedure for hver bruger. Hvis du har mange brugere, kan denne proces være kedelig. Med PowerShell til Microsoft 365 kan du vise disse oplysninger for alle dine brugere ved hjælp af følgende kommando:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>PowerShell Core understøtter ikke Microsoft Azure Active Directory modulet til Windows PowerShell og cmdlet'er, der har *Msol* i deres navn. Du skal køre disse cmdlet'er fra Windows PowerShell.
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

Fortolkningen af denne PowerShell-kommando er: Hent alle brugerne i det aktuelle **Microsoft 365-abonnement (Get-AzureADUser**), men vis kun navn og placering for hver bruger (**Vælg Visningsnavn, Brugsplacering**).

Da PowerShell til Microsoft 365 understøtter et kommando-shell-sprog, kan du yderligere manipulere de oplysninger, der fås med **kommandoen Get-AzureADUser**. Det kan f.eks. være, at du gerne vil sortere disse brugere efter deres placering, gruppere alle de brasilianske brugere sammen, alle de amerikanske brugere sammen osv. Sådan gør du:

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

Fortolkningen af denne PowerShell-kommando er: Hent alle brugere i det aktuelle Microsoft 365-abonnement, men vis kun navn og placering for hver bruger, og sortér dem først efter deres placering og derefter deres navn (Sortér brugsplacering **, Visningsnavn**).

Du kan også bruge yderligere filtrering. Hvis du f.eks. kun vil se oplysninger om brugere baseret på Brasilien, skal du bruge denne kommando:

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

Fortolkningen af denne PowerShell-kommando er: Hent alle brugere i det aktuelle Microsoft 365-abonnement, hvis placering er Brasilien (**hvor {$\_). UsageLocation -eq "BR"}**) og viser derefter navn og placering for hver bruger.

 **En note om store domæner**

Hvis du har et stort domæne med titusindvis af brugere, kan det give en begrænsning at prøve nogle af de eksempler, vi viser i denne artikel. Baseret på faktorer som computerkraft og tilgængelig netværksbåndbredde, forsøger du måske at gøre for meget på én gang. Store organisationer ønsker måske at opdele nogle af disse PowerShell-handlinger i to kommandoer.

Følgende kommando returnerer f.eks. alle brugerkontiene og viser navn og placering for hver enkelt:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

Det fungerer fint til mindre domæner. Men i store organisationer ønsker du måske at opdele denne handling i to kommandoer: én kommando til at gemme oplysningerne om brugerkontoen i en variabel, og en anden til at vise de nødvendige oplysninger. Her er et eksempel:

```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

Fortolkningen af dette sæt af PowerShell-kommandoer er:
1. Hent alle brugerne i det aktuelle Microsoft 365-abonnement, og gem oplysningerne i en variabel, der hedder $x (**$x = Get-AzureADUser**).
1.  Vise indholdet af variablen *$x*, men kun medtage navn og placering for hver bruger (**$x | Vælg DisplayName, UsageLocation**).

## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>Microsoft 365 indeholder funktioner, som du kun kan konfigurere med PowerShell til Microsoft 365

The Microsoft 365 Administration har til formål at give adgang til almindelige, nyttige administrative opgaver, der gælder for de fleste miljøer. Med andre ord er Microsoft 365 Administration udviklet, så den typiske administrator kan udføre de mest almindelige administrationsopgaver. Men der er nogle opgaver, som ikke kan udføres i Administration.

Eksempelvis indeholder administration i Skype for Business Online Administration nogle få muligheder for at oprette brugerdefinerede mødeinvitationer:

![Eksempel på visning af brugerdefinerede mødeinvitationer i Skype for Business Online Administration.](../media/o365-powershell-meeting-invitation.png)

Med disse indstillinger kan du føje et touch af tilpasning og professionalitet til mødeinvitationer. Men der er mere at konfigurere for møder end blot at oprette brugerdefinerede mødeinvitationer. Som standard tillader møder f.eks.:

- Anonyme brugere får automatisk adgang til hvert møde.

- Deltagere, som skal optage mødet.

- Alle brugere fra din organisation skal udpeges som præsentationsvært, når de deltager i mødet.

Disse indstillinger er ikke tilgængelige fra Skype for Business Online Administration. Du kan styre dem fra PowerShell til Microsoft 365. Her er en kommando, der deaktiverer disse tre indstillinger:

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> For at køre denne kommando skal du installere [Skype for Business Online PowerShell-modul](https://www.microsoft.com/download/details.aspx?id=39366).

Fortolkningen af denne PowerShell-kommando er:

1. I indstillingerne for nye Skype for Business **Online-møder (Set-CsMeetingConfiguration**) skal du deaktivere, så anonyme brugere får automatisk adgang til møder (**-AdmitAnonymousUsersByDefault $False**).
2.  Deaktiver muligheden for, at deltagerne kan optage møder (**-AllowConferenceRecording $False**).
3. Udped ikke alle brugere fra organisationen som præsentationsværter (**-DesignateAsPresenter "Ingen"**).

Kør denne kommando for at gendanne disse standardindstillinger (aktivér indstillingerne):

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

Der findes også andre lignende scenarier, hvilket er grunden til, at administratorer skal vide, hvordan de skal køre PowerShell Microsoft 365-kommandoer.

## <a name="powershell-for-microsoft-365-is-great-for-bulk-operations"></a>PowerShell til Microsoft 365 er fantastisk til massehandlinger

Visuelle grænseflader som disse Microsoft 365 Administration er mest værdifulde, når du skal udføre en enkelt handling. Hvis du f.eks. vil deaktivere én brugerkonto, kan du bruge Administration til hurtigt at finde og fjerne markeringen i et afkrydsningsfelt. Dette kan være nemmere end at udføre en lignende handling i PowerShell.

Men hvis du skal ændre mange ting eller nogle markerede ting inden for et stort sæt andre ting, er Microsoft 365 Administration muligvis ikke det bedste værktøj. Lad os f.eks. sige, at du er nødt til at ændre præfikset på tusindvis af telefonnumre eller fjerne den bestemte bruger *Ken Myer* fra alle dine SharePoint Online-websteder. Hvordan ville du gøre det i Microsoft 365 Administration?

I det sidste eksempel kan du f.eks. sige, at du har flere hundrede SharePoint Online-websteder, og du ikke ved, hvilke af dem Ken Websted er medlem af. Du skal starte ved starten Microsoft 365 Administration og derefter udføre denne procedure for hvert websted:

1. Vælg **url-adressen** til webstedet.

2. I feltet **Egenskaber for gruppe af** websteder skal du vælge **linket Webadresse** for at åbne webstedet.

3. Vælg Del på **webstedet**.

4. I dialogboksen **Del** skal du vælge det link, der viser alle de brugere, der har tilladelser til webstedet:

     ![Eksempel på visning af medlemmer af et SharePoint Online-websted i SharePoint Online Administration.](../media/o365-powershell-view-permissions.png)

5. I dialogboksen **Delt med** skal du vælge **Avanceret**.

6. Rul ned på listen over brugere, find og vælg Ken Myer (hvis han har tilladelser til webstedet), og vælg **derefter Fjern brugertilladelser**.

Det vil tage lang *tid* for flere hundrede websteder.

Alternativet er at køre følgende kommando i PowerShell til Microsoft 365 at fjerne Ken Myer fra alle dine websteder:

```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> Denne kommando kræver, at du installerer [SharePoint Online PowerShell-modulet](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

Fortolkningen af denne PowerShell-kommando er: Hent alle SharePoint-webstederne i det aktuelle **Microsoft 365-abonnement (Get-SPOSite**), og fjern Ken Position fra listen over brugere, der kan få adgang til det for hvert websted (**ForEach {Remove-SPOUser -Site $\_. URL -LoginName "kenmyer\@ litwareinc.com"}**).

Vi vil Microsoft 365 om at fjerne Ken Websted fra alle websteder, også dem han ikke har adgang til. Så resultaterne viser fejl for de websteder, han ikke har adgang til. Vi kan bruge en ekstra betingelse for denne kommando til at fjerne Ken Websteder kun fra de websteder, der har ham på deres logonliste. Men de fejl, der returneres, forårsager ingen skade på selve webstederne. Denne kommando kan tage et par minutter at køre op mod hundredvis af websteder i stedet for at arbejde timer Microsoft 365 Administration.

Her er et andet eksempel på en massehandling. Brug denne kommando til at *føje Bonnie Kearney*, SharePoint administrator, til alle websteder i organisationen:

```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

Fortolkningen af denne PowerShell-kommando er: Hent alle SharePoint-webstederne i det aktuelle Microsoft 365-abonnement, og giv Bonnie Kearney adgang ved at føje hendes logonnavn til gruppen Medlemmer på webstedet (**ForEach {Add-SPOUser -Site $\_. URL -LoginName "bkearney\@ litwareinc.com" -Group "Members"}**).

## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>PowerShell til Microsoft 365 er god til at filtrere data

I Microsoft 365 Administration findes der flere måder at filtrere dine data på, så du nemt kan finde en målrettet delmængde af oplysninger. Eksempelvis gør Exchange det nemt at filtrere næsten enhver egenskab for en brugerpostkasse. Her er f.eks. en liste over postkasser for alle brugere, der bor i byen Bloomington:

![Eksempel på avanceret søgning i Microsoft 365 Administration efter listen over postkasser for alle brugere, der bor i byen Bloomington.](../media/o365-powershell-advanced-search.png)

I <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration kan</a> du også kombinere filterkriterier. Du kan f.eks. finde postkasserne for alle de personer, der bor i Bloomington og arbejder i økonomiafdelingen.

Men der er begrænsninger for, hvad du kan gøre Exchange Administration. Du kan f.eks. ikke lige så nemt finde postkasser af personer, der bor i *Bloomington eller* San Cluster, eller postkasser til alle personer, der ikke bor i Bloomington.

Du kan bruge følgende PowerShell til Microsoft 365 til at få en liste over postkasser for alle de personer, der bor i Bloomington eller San Vietnam:

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

Fortolkningen af denne PowerShell-kommando er: Få alle brugerne i det aktuelle Microsoft 365-abonnement, der har en postkasse i byen San Bloomington (**Hvor {$\_). RecipientTypeDetails -eq "UserMailbox" -and ($\_. City -eq "SanEring" -eller $\_. City -eq "Bloomington")}**), og derefter vises navn og by for hver (**Vælg Visningsnavn, By**).

Og her er kommandoen til at få vist alle postkasser for personer, der bor et sted undtagen Bloomington:

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

Fortolkningen af denne PowerShell-kommando er: Hent alle brugere i det aktuelle Microsoft 365-abonnement, der har en postkasse, der ikke er placeret i byen Bloomington (**Hvor {$\_). RecipientTypeDetails -eq "UserMailbox" -and $\_. City -ne "Bloomington"}**), og derefter vises navn og by for hver.

### <a name="use-wildcards"></a>Brug jokertegn

Du kan også bruge jokertegn i dine PowerShell-filtre til at matche en del af et navn. Antag f.eks., at du leder efter en brugerkonto. Alt, hvad du kan huske, er, at brugerens efternavn var *Hansen* eller måske *Henderson* eller *Venezuela*.

Du kan finde den pågældende bruger i Microsoft 365 Administration ved hjælp af søgeværktøjet og udføre tre forskellige søgninger:

- One for  *2010*

- En til  *Henderson*

- One for  *Jorgenson*

Da alle tre af disse navne slutter med "søn", kan du bede PowerShell om at vise alle de brugere, hvis navn slutter med "søn". Sådan gør du:

```powershell
Get-User -Filter '{LastName -like "*son"}'
```

Fortolkningen af denne PowerShell-kommando er: Hent alle brugere i det aktuelle Microsoft 365-abonnement, men brug et filter, der kun viser de brugere, hvis efternavn slutter med "søn" (**-Filter '{Efternavn -like "\*son"}").** Står \* for et vilkårligt tegnsæt, som er bogstaver i brugerens efternavn.

## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>PowerShell til Microsoft 365 gør det nemt at udskrive eller gemme data

I Microsoft 365 Administration kan du se lister med data. Her er et eksempel på Skype for Business Online Administration, der viser en liste over brugere, der er blevet aktiveret til Skype for Business Online:

![Eksempel på den Skype for Business Administration, der viser en liste over brugere, der er blevet aktiveret til Skype for Business Online.](../media/o365-powershell-lync-users.png)

Hvis du vil gemme disse oplysninger i en fil, skal du indsætte dem i et dokument eller Microsoft Excel regneark. Begge tilfælde kan kræve yderligere formatering. Derudover indeholder Microsoft 365 Administration ikke en måde at udskrive den viste liste direkte på.

Heldigvis kan du bruge PowerShell til ikke kun at vise listen, men også til at gemme den i en fil, der nemt kan importeres Excel. Her er en eksempelkommando til at gemme Skype for Business Online-brugerdata i en kommasepareret fil (CSV), som derefter nemt kan importeres som en tabel i et Excel-regneark:

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

Her er et eksempel på resultaterne:

![Eksempel på en tabel, der er importeret Excel et Skype for Business onlinebrugerdata, der blev gemt i en fil med kommaseparerede værdier.](../media/o365-powershell-data-in-excel.png)

Fortolkningen af denne PowerShell-kommando er: Få alle Skype for Business **Online-brugere i det aktuelle Microsoft 365-abonnement (Get-CsOnlineUser**); få kun brugernavnet, UPN og placeringen (**Select DisplayName, UserPrincipalName, UsageLocation**), og gem derefter disse oplysninger i en CSV-fil med navnet C:\\Logs\\SfBUsers.csv (**Export-Csv -Path "C:\\Logs\\ SfBUsers.csv" -NoTypeInformation**).

Du kan også bruge indstillingerne til at gemme denne liste som en XML-fil eller en HTML-side. Faktisk kan du med flere PowerShell-kommandoer gemme den direkte som en Excel fil med en brugerdefineret formatering, du ønsker.

Du kan også sende output fra en PowerShell-kommando, der viser en liste direkte til standardprinteren Windows. Her er en eksempelkommando:

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

Sådan ser det udskrevne dokument ud:

![Eksempel på et udskrevet dokument, der blev output fra en PowerShell-kommando sendt direkte til standardprinteren Windows.](../media/o365-powershell-printed-data.png)

Fortolkningen af denne PowerShell-kommando er: Få alle Skype for Business **Online-brugere i det aktuelle Microsoft 365-abonnement**, indskr udelukkende brugernavnet, UPN og placering, og send derefter disse oplysninger til standardprinteren til Windows (Out-Printer).

Det udskrevne dokument har samme enkle formatering som visningen i PowerShell-kommandovinduet. Hvis du vil have en papirkopi, skal du **blot tilføje | Out-Printer** til slutningen af kommandoen.

## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>Med PowerShell til Microsoft 365 kan du administrere på tværs af serverprodukter

De komponenter, der udgør Microsoft 365, er udviklet til at arbejde sammen. Antag f.eks., at du føjer en ny bruger til Microsoft 365, og du angiver disse oplysninger som f.eks. brugerens afdeling og telefonnummer. Disse oplysninger vil derefter være tilgængelige, hvis du får adgang til brugerens oplysninger i nogen af Microsoft 365-tjenesterne: Skype for Business Online, Exchange eller SharePoint.

Men det er til almindelige oplysninger, der strækker sig over produktpakken. Produktspecifikke oplysninger, f.eks. oplysninger om en brugers postkasse Exchange, er typisk ikke tilgængelige i hele pakken. Oplysninger om, hvorvidt en brugers postkasse er aktiveret eller ej, er f.eks. kun tilgængelige Exchange Administration.

Antag, at du gerne vil lave en rapport, der viser følgende oplysninger for alle dine brugere:

- Brugerens viste navn

- Om brugeren har licens til Microsoft 365

- Om brugerens postkasse Exchange blevet aktiveret

- Om brugeren er aktiveret til Skype for Business Online

Det er ikke nemt at oprette en sådan rapport i Microsoft 365 Administration. I stedet skal du oprette et separat dokument for at gemme oplysningerne, f.eks. Excel regneark. Hent derefter alle brugernavne og licensoplysninger fra Microsoft 365 Administration, få postkasseoplysninger fra <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> Administration, få Skype for Business Online-oplysninger fra Skype for Business Online Administration, og kombiner derefter dette oplysninger.

Alternativet er at bruge et PowerShell-script til at kompilere rapporten for dig.

Det følgende eksempelscript er mere kompliceret end de kommandoer, du har set indtil videre i denne artikel. Men den viser mulighederne for at bruge PowerShell til at oprette oplysningsvisninger, der ellers er svære at få. Her er scriptet til kompilering og visning af den liste, du skal bruge:

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

1. Hent alle brugerne i det aktuelle Microsoft 365-abonnement, og gem oplysningerne i en variabel, der hedder *$x* (**$x = Get-AzureADUser**).
1. Start en løkke, der kører over alle brugere i variablen $x (**forgrund ($i i $x)**).
1. Definer en variabel *med $y* og gem brugerens postkasseoplysninger i den (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).
1. Føj en ny egenskab til de brugeroplysninger, der hedder *IsMailBoxEnabled*. Indstil den til værdien af egenskaben IsMailBoxEnabled for brugerens postkasse (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).
1. Definer en variabel *med $y*, og gem brugerens Skype for Business Online-oplysninger i den (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).
1. Føj en ny egenskab til de brugeroplysninger, der hedder *EnabledForSfB*. Indstil den til værdien af egenskaben Aktiveret for brugerens Skype for Business Online-oplysninger (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).
1. Få vist listen over brugere, men medtag kun deres navn, uanset om de har licens, og de to nye egenskaber, der angiver, om deres postkasse er aktiveret, og om de er aktiveret til Skype for Business Online (**$x | Vælg DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB**).

## <a name="see-also"></a>Se også

[Introduktion til PowerShell til Microsoft 365](getting-started-with-microsoft-365-powershell.md)

[Administrer Microsoft 365 brugerkonti, licenser og grupper med PowerShell](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Brug Windows PowerShell til at oprette rapporter i Microsoft 365](use-windows-powershell-to-create-reports-in-microsoft-365.md)