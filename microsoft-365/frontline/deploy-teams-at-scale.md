---
title: Udrul teams i stor skala til frontlinjemedarbejdere i Microsoft Teams
author: LanaChin
ms.author: v-lanachin
ms.reviewer: rahuldey
manager: samanro
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Få mere at vide om, hvordan du udruller teams i stor skala for frontlinjemedarbejderne i din organisation.
ms.localizationpriority: high
ms.collection:
- M365-collaboration
- m365-frontline
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 6bc62a4179ba712cbf74e3205fd372727db03182
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66823981"
---
# <a name="deploy-teams-at-scale-for-frontline-workers-in-microsoft-teams"></a>Udrul teams i stor skala til frontlinjemedarbejdere i Microsoft Teams

> [!NOTE]
> Denne funktion er i øjeblikket en offentlig prøveversion. Hvis du vil deltage, kan du kontakte os på [dscale@microsoft.com](mailto:dscale@microsoft.com).

## <a name="overview"></a>Oversigt
 
Din organisation kan have mange teams, som du bruger til at skabe kommunikation og samarbejde mellem din frontlinjearbejdsstyrke, som er spredt på tværs af forskellige butikker, placeringer og roller. I øjeblikket er der ikke en nem løsning at udrulle, konfigurere og administrere disse teams og brugere i stor skala.

Vi er ved at bygge en løsning, der gør det muligt for administratorer at udrulle og administrere teams i stor skala.

Her er en oversigt over de funktioner, der er tilgængelige i dag til oprettelse og administration af et stort antal teams ad gangen, og hvad vi planlægger i den nærmeste fremtid.

||Tilgængelig i dag |Senere i 2022  |
|---------|---------|---------|
|**Antal teams, du kan oprette pr. batch**|Op til 100 |Op til 500|
|**Antal brugere, du kan tilføje pr. team**|Op til 25|Op til 25|

Udrulning af teams i stor skala giver dig mulighed for at:

- Opret teams ved hjælp af færdigbyggede skabeloner eller dine egne brugerdefinerede skabeloner.
- Føj brugere til teams som ejere eller medlemmer.
- Administrer teams i stor skala ved at tilføje eller fjerne brugere fra eksisterende teams.
- Få besked via mail, herunder fuldførelse, status og fejl (hvis der er nogen). Du kan vælge at give op til fem personer besked om status for hvert bundt af teams, du udruller. Teamejere og -medlemmer får automatisk besked, når de føjes til et team.

## <a name="how-to-deploy-teams-at-scale"></a>Sådan udruller du teams i stor skala

> [!NOTE]
> Før du udruller dine teams, skal du sørge for, at alle teamsejere har en Licens til Teams.

Følg disse trin for at udrulle et stort antal teams ad gangen.

### <a name="step-1-prepare-your-csv-files"></a>Trin 1: Forbered dine CSV-filer

Du skal oprette to CSV-filer for hvert bundt af teams, du udruller:

- **En CSV-fil, der definerer de teams, du opretter**. Denne fil skal indeholde disse påkrævede kolonner i følgende rækkefølge– startende med den første kolonne:

    |Kolonnenavn  |Beskrivelse  |
    |---------|---------|
    |**Teamnavn**|Navnet på teamet.|
    |**Eksisterende team-id**|Hvis du tilføjer eller fjerner brugere fra et eksisterende team, skal du angive team-id'et for teamet.|
    |**Synlighed**|Uanset om teamet er offentligt (alle i din organisation kan tilmelde sig) eller private (brugerne skal have godkendelse fra teamejerne for at deltage). Indstillingerne er **Offentlige** og **Private**.|
    |**Teamskabelon-id**|Hvis du opretter et team ud fra en færdigbygget eller brugerdefineret skabelon, skal du angive teamskabelon-id'et. Se [Kom i gang med teamskabeloner i Teams Administration](/microsoftteams/get-started-with-teams-templates-in-the-admin-console) for at få en liste over færdigbyggede teamskabeloner og -id'er. Hvis du vil bruge standardskabelonen for team, skal du lade feltet være tomt.|

- **En CSV-fil, der knytter de brugere, du føjer til hvert team**. Denne fil skal indeholde disse påkrævede kolonner i følgende rækkefølge– startende med den første kolonne:

    |Kolonnenavn  |Beskrivelse  |
    |---------|---------|
    |**Brugerens fulde navn**|Brugerens viste navn.|
    |**Bruger-UPN eller -id**|Brugerens hovednavn (UPN) eller id for brugeren. F.eks. averyh@contoso.com.|
    |**Teamnavn**|Navnet på teamet.|
    |**ActionType**|Uanset om du tilføjer eller fjerner brugeren fra teamet. Indstillingerne er **AddMember** og **RemoveMember**.|
    |**Ejer eller medlem**|Angiver, om brugeren er teamejer eller teammedlem. Indstillingerne er **Ejer** og **Medlem**.|

#### <a name="examples"></a>Eksempler

Brug følgende eksempler som en hjælp til at oprette dine CSV-filer. Her har vi navngivet filerne, Teams.csv og Users.csv.

**Teams.csv**

|Teamnavn|Eksisterende team-id|Synlighed|Teamskabelon-id|
|---------|---------|---------|---------|
|Contoso Store 1||Offentlige|com.microsoft.teams.template.retailStore|
|Contoso Store 2||Offentlige|com.microsoft.teams.template.retailStore|
|Contoso Store 3||Offentlige|com.microsoft.teams.template.retailStore|
|Contoso Store 4||Offentlige|com.microsoft.teams.template.retailStore|
|Contoso Store 5||Offentlige|com.microsoft.teams.template.ManageAProject|
|Contoso Store 6||Offentlige|com.microsoft.teams.template.ManageAProject|
|Contoso Store 7||Offentlige||
|Contoso Store 8||Privat|com.microsoft.teams.template.OnboardEmployees|
|Contoso Store 9||Privat|com.microsoft.teams.template.OnboardEmployees|
|Contoso Store 10||Privat|com.microsoft.teams.template.OnboardEmployees|

**Users.csv**

|Brugerens fulde navn |Bruger-UPN eller -id|Teamnavn|ActionType|Ejer eller medlem|
|---------|---------|---------|---------|---------|
|Avery Howard|averyh@contoso.com|Contoso Store 1|Tilføjmedlem|Ejer|
|Casey Jensen|caseyj@contoso.com|Contoso Store 2|Tilføjmedlem|Ejer|
|Jessie Irwin|jessiei@contoso.com|Contoso Store 3|Tilføjmedlem|Ejer|
|Manjeet Bhatia|manjeetb@contoso.com|Contoso Store 4|Tilføjmedlem|Ejer|
|Mikaela Lee|mikaelal@contoso.com|Contoso Store 5|Tilføjmedlem|Ejer|
|Morgan Conners|morganc@contoso.com|Contoso Store 6|Tilføjmedlem|Medlem|
|Oscar Ward|oscarw@contoso.com|Contoso Store 7|Tilføjmedlem|Medlem|
|Rene Pelletier|renep@contoso.com|Contoso Store 8|Tilføjmedlem|Medlem|
|Sydney Mattos|sydneym@contoso.com|Contoso Store 9|Tilføjmedlem|Medlem|
|Violet Martinez|violetm@contoso.com|Contoso Store 10|Tilføjmedlem|Medlem|

### <a name="step-2-deploy-your-teams"></a>Trin 2: Udrul dine teams

Nu, hvor du har oprettet dine CSV-filer, er du klar til at konfigurere dit miljø og udrulle dine teams.

Du kan bruge cmdlet'en ```New-CsBatchTeamsDeployment``` til at sende et bundt teams, der skal oprettes. Der genereres et orkestrerings-id for hvert batch. Du kan derefter bruge cmdlet'en ```Get-CsBatchTeamsDeployment``` til at spore status og status for hvert batch.

1. Installér PowerShell version 7 eller nyere. Du kan finde en trinvis vejledning under [Installation af PowerShell på Windows](/powershell/scripting/install/installing-powershell-on-windows).
1. Kør PowerShell i administratortilstand.
1. Kør følgende for at fjerne tidligere installerede Teams PowerShell-modul.

    ```powershell
    Uninstall-module -Name MicrosoftTeams -Force -Allversions
    ```

    Hvis du får vist en fejlmeddelelse, er du allerede angivet. Gå til næste trin.
1. Download og installér den [nyeste version af Teams PowerShell-modulet](https://www.powershellgallery.com/packages/MicrosoftTeams).

1. Kør følgende for at oprette forbindelse til Teams.

    ```powershell
    Connect-MicrosoftTeams
    ```

    Når du bliver bedt om det, skal du logge på med dine administratorlegitimationsoplysninger.

1. Kør følgende for at få vist en liste over kommandoerne i Teams PowerShell-modulet.

    ```powershell
    Get-Command -Module MicrosoftTeams
    ```

    Kontrollér, at ```New-CsBatchTeamsDeployment``` og ```Get-CsBatchTeamsDeployment``` er angivet.

1. Kør følgende for at udrulle en batch af teams. I denne kommando skal du angive stien til dine CSV-filer og mailadresserne på op til fem modtagere for at give besked om denne installation.

    ```powershell
    New-CsBatchTeamsDeployment -TeamsFilePath "Your CSV file path" -UsersFilePath "Your CSV file path" -UsersToNotify "Email addresses" 
    ```

    Eksempel:

    ```powershell
    New-CsBatchTeamsDeployment -TeamsFilePath "C:\dscale\Teams.csv" -UsersFilePath "C:\dscale\Users.csv" -UsersToNotify "adminteams@contoso.com,adelev@contoso.com"
    ```

    Modtagerne modtager mailmeddelelser om installationsstatus. Mailen indeholder orkestrerings-id'et for det batch, du sendte, og eventuelle fejl, der kan være opstået.

1. Kør følgende for at kontrollere status for det batch, du har sendt.

    ```powershell
    Get-CsBatchTeamsDeploymentStatus -OrchestrationId "OrchestrationId"
    ```

## <a name="send-us-feedback"></a>Send os feedback

Vi sætter pris på din feedback. Anvendelighed, pålidelighed, ydeevne&mdash;vi hilser det hele velkommen!

Mail [dscale@microsoft.com](mailto:dscale@microsoft.com) og medtag dit orkestrerings-id og fejlfil, hvis du har det.

## <a name="related-articles"></a>Relaterede artikler

- [Oversigt over Teams PowerShell](/microsoftteams/teams-powershell-overview)
