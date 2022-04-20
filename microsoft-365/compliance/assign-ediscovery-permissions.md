---
title: Tildel eDiscovery-tilladelser på Microsoft Purview-overholdelsesportalen
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
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
ms.assetid: 5b9a067b-9d2e-4aa5-bb33-99d8c0d0b5d7
description: Tildel de tilladelser, der kræves for at udføre eDiscovery-relaterede opgaver ved hjælp af Microsoft Purview-overholdelsesportalen.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: 1f19c43e65993652628703f002b9537c71066013
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64946523"
---
# <a name="assign-ediscovery-permissions-in-the-compliance-portal"></a>Tildel eDiscovery-tilladelser på overholdelsesportalen

Hvis du vil have, at brugerne skal bruge et af de [eDiscovery-relaterede værktøjer](ediscovery.md) på Microsoft Purview-overholdelsesportalen, skal du tildele dem de relevante tilladelser. Den nemmeste måde at gøre dette på er at tilføje den person, der er den relevante rollegruppe, på siden **Tilladelser** i Overholdelsescenter. I dette emne beskrives de tilladelser, der kræves for at udføre eDiscovery-opgaver.
  
Den primære eDiscovery-relaterede rollegruppe i overholdelsesportalen kaldes **eDiscovery Manager**. Der er to undergrupper i denne rollegruppe.
  
- **eDiscovery Manager** – En eDiscovery Manager kan bruge eDiscovery-søgeværktøjer til at søge efter indholdsplaceringer i organisationen og udføre forskellige søgerelaterede handlinger, f.eks. få vist og eksportere søgeresultater. Medlemmer kan også oprette og administrere sager i Microsoft Purview eDiscovery (Standard) og Microsoft Purview eDiscovery (Premium), tilføje og fjerne medlemmer til en sag, oprette ventepositioner for sager, køre søgninger, der er knyttet til en sag, og få adgang til sagsdata. eDiscovery-ledere kan kun få adgang til og administrere de sager, de opretter. De kan ikke få adgang til eller administrere sager, der er oprettet af andre eDiscovery-ledere.
  
- **eDiscovery-administrator** – En eDiscovery-administrator er medlem af rollegruppen eDiscovery Manager og kan udføre de samme indholdssøgnings- og sagsstyringsrelaterede opgaver, som en eDiscovery Manager kan udføre. En eDiscovery-administrator kan desuden:
  
  - Få adgang til alle sager, der er angivet på siderne **eDiscovery (Standard)** og **eDiscovery (Premium)** på overholdelsesportalen.

  - Få adgang til sagsdata i eDiscovery (Premium) for alle tilfælde i organisationen.
  
  - Administrer alle eDiscovery-sager, når de tilføjer sig selv som medlem af sagen.
  
  - Fjern medlemmer fra en eDiscovery-sag. Det er kun en eDiscovery-administrator, der kan fjerne medlemmer fra en sag. Brugere, der er medlemmer af undergruppen eDiscovery Manager, kan ikke fjerne medlemmer fra en sag, selvom brugeren har oprettet sagen.
  
  Hvis du vil have eDiscovery-administratorer i din organisation, skal du se [Flere oplysninger](#more-information).

> [!NOTE]
> Hvis du vil analysere en brugers data ved hjælp af eDiscovery (Premium), skal brugeren (datamyndigheden over dataene) tildeles en Office 365 E5 eller Microsoft 365 E5 licens. Alternativt kan brugere med en Office 365 E1 eller en Office 365- eller Microsoft 365 E3-licens tildeles en Microsoft 365 E5 Overholdelse eller Microsoft 365 eDiscovery- og overvågningstilføjelsesprogramlicens. Administratorer, overholdelsesansvarlige eller juridisk personale, der er tildelt sager som medlemmer, og bruger eDiscovery (Premium) til at indsamle, få vist og analysere data, behøver ikke en E5-licens. Du kan finde flere oplysninger om eDiscovery-licenser (Premium) [under Abonnementer og licenser i eDiscovery (Premium)](overview-ediscovery-20.md#subscriptions-and-licensing).
  
## <a name="before-you-assign-permissions"></a>Før du tildeler tilladelser

- Du skal være medlem af rollegruppen Organisationsadministration eller tildeles rollen Rolleadministration for at tildele eDiscovery-tilladelser på overholdelsesportalen.

- Du kan bruge [Cmdlet'en Add-RoleGroupMember](/powershell/module/exchange/Add-RoleGroupMember) i Security & Compliance Center PowerShell til at tilføje en mailaktiveret sikkerhedsgruppe som medlem af undergruppen eDiscovery Managers i rollegruppen eDiscovery Manager. Du kan dog ikke føje en mailaktiveret sikkerhedsgruppe til undergruppen eDiscovery-administratorer. Du kan finde [flere oplysninger under Flere oplysninger](#more-information).
  
## <a name="assign-ediscovery-permissions"></a>Tildel eDiscovery-tilladelser

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">overholdelsesportalen</a> , og log på med en konto, der kan tildele tilladelser.
  
2. Vælg **Tilladelser** i ruden til venstre.

3. Klik på **Roller** under **Overholdelsescenter** på siden **Tilladelser & roller**.

4. Vælg **eDiscovery Manager** på siden **Med overholdelsescenterroller**.
  
5. Gør et af følgende på siden **eDiscovery Manager** på baggrund af de eDiscovery-tilladelser, du vil tildele.
  
    **Sådan gør du en bruger til eDiscovery Manager:** Ud for **eDiscovery Manager** skal du vælge **Rediger**. Klik på Tilføj ikon på ![guidesiden **Vælg eDiscovery Manager**.](../media/ITPro-EAC-AddIcon.gif) **Tilføj**. Vælg den bruger (eller de brugere), du vil tilføje som eDiscovery-chef, og vælg derefter **Tilføj**. Når du er færdig med at tilføje brugere, skal du vælge **Udført**. Vælg derefter **Gem** på siden **Redigering vælg eDiscovery Manager** for at gemme ændringerne i eDiscovery Manager-medlemskabet.
  
    **Sådan gør du en bruger til eDiscovery-administrator:** Ud for **eDiscovery-administrator** skal du vælge **Rediger**. Klik på Tilføj ikon på ![siden **Vælg eDiscovery-administrator**.](../media/ITPro-EAC-AddIcon.gif) **Tilføj**. Vælg den bruger (eller de brugere), du vil tilføje som **eDiscovery-administrator**, og  **tilføj** derefter. Når du er færdig med at tilføje brugere, skal du vælge **Udført**. Vælg derefter **Gem** på siden **Redigering vælg eDiscovery-administrator** for at gemme ændringerne i eDiscovery-administratormedlemskabet.
  
> [!NOTE]
> Du kan også bruge **Add-eDiscoveryCaseAdmin-cmdlet'en** til at gøre en bruger til eDiscovery-administrator. Brugeren skal dog tildeles rollen Sagsstyring, før du kan bruge denne cmdlet til at gøre vedkommende til eDiscovery-administrator. Du kan finde flere oplysninger under [Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin).
  
På siden **Tilladelser i overholdelsesportalen** kan du også tildele brugere eDiscovery-relaterede tilladelser ved at føje dem til rollegrupperne Overholdelsesadministrator, Organisationsadministration og Korrekturlæser. Du kan finde en beskrivelse af de eDiscovery-relaterede RBAC-roller, der er tildelt til hver af disse rollegrupper, under [RBAC-roller, der er relateret til eDiscovery](#rbac-roles-related-to-ediscovery).

## <a name="rbac-roles-related-to-ediscovery"></a>RBAC-roller, der er relateret til eDiscovery

I følgende tabel vises de eDiscovery-relaterede RBAC-roller på overholdelsesportalen, og den angiver de indbyggede rollegrupper, som hver rolle er tildelt som standard.
  
| Rolle | Administrator for overholdelse af angivne standarder | & administrator af eDiscovery Manager | Organisationsadministration | Reviewer |
|:-----|:-----:|:-----:|:-----:|:-----:|
|Sagsstyring <br/> |![Markeret.](../media/checkmark.png) <br/> |![Markeret.](../media/checkmark.png) <br/> |![Markeret.](../media/checkmark.png) <br/> | <br/> |
|Kommunikation <br/> | <br/> |![Markeret.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Søgning efter overholdelse <br/> |![Markeret.](../media/checkmark.png) <br/> |![Markeret.](../media/checkmark.png) <br/> |![Markeret.](../media/checkmark.png) <br/> | <br/> |
|Vogter <br/> | <br/> |![Markeret.](../media/checkmark.png) <br/> | <br/> | <br/> |
|eksportér <br/> | <br/> |![Markeret.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Holde <br/>  |![Markeret.](../media/checkmark.png) <br/> |![Markeret.](../media/checkmark.png) <br/> |![Markeret.](../media/checkmark.png) <br/> | <br/> |
|Preview <br/>  | <br/> |![Markeret.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Vurder <br/>  | <br/> |![Markeret.](../media/checkmark.png) <br/> | <br/> |![Markeret](../media/checkmark.png) <br/> |
|RMS-dekryptering <br/>  ||![Markeret](../media/checkmark.png) <br/> |||
|Søg og fjern <br/> | <br/> | <br/> |![Markeret](../media/checkmark.png)<br/> | <br/> |
||||||
  
I følgende afsnit beskrives hver af de eDiscovery-relaterede RBAC-roller, der er angivet i den forrige tabel.

### <a name="case-management"></a>Sagsstyring

Denne rolle giver brugerne mulighed for at oprette, redigere, slette og styre adgangen til sager med eDiscovery (Standard) og eDiscovery (Premium) i overholdelsesportalen. Som tidligere forklaret skal en bruger tildeles rollen Sagsstyring, før du kan bruge **cmdlet'en Add-eDiscoveryCaseAdmin** til at gøre vedkommende til eDiscovery-administrator.

Du kan finde flere oplysninger under:

- [Kom i gang med eDiscovery (Standard)](get-started-core-ediscovery.md)

- [Kom i gang med eDiscovery (Premium)](get-started-with-advanced-ediscovery.md)

### <a name="communication"></a>Kommunikation

Denne rolle giver brugerne mulighed for at administrere al kommunikation med de tilsynsførende, der er identificeret i en eDiscovery-sag (Premium). Dette omfatter oprettelse af meddelelser om venteposition, påmindelser om venteposition og eskalering til administration. Brugeren kan også spore den tilsynsførendes anerkendelse af meddelelser om venteposition og administrere adgangen til den tilsynsførende portal, der bruges af hver tilsynsførende til at spore kommunikation i de tilfælde, hvor de blev identificeret som tilsynsførende.

Du kan finde flere oplysninger [under Arbejd med kommunikation i eDiscovery (Premium)](managing-custodian-communications.md).

### <a name="compliance-search"></a>Søgning efter overholdelse

Denne rolle giver brugerne mulighed for at køre værktøjet indholdssøgning på overholdelsesportalen til søgepostkasser og offentlige mapper, SharePoint onlinewebsteder, OneDrive for Business websteder, Skype for Business samtaler, Microsoft 365 grupper og Microsoft Teams og Yammer grupper. Denne rolle giver en bruger mulighed for at få et estimat over søgeresultaterne og oprette eksportrapporter, men der kræves andre roller for at starte søgehandlinger for indhold, f.eks. visning, eksport eller sletning af søgeresultater.

I Indholdssøgning og eDiscovery (Standard) kan brugere, der har fået tildelt rollen Søgning efter overholdelse, men ikke har rollen Eksempelvisning, få vist resultaterne af en søgning, hvor eksempelhandlingen er blevet startet af en bruger, der har fået tildelt eksempelrollen. Brugeren uden prøveversionsrollen kan få vist resultater i op til to uger, efter at den indledende eksempelhandling blev oprettet.

På samme måde kan brugere i indholdssøgning og eDiscovery (Standard), der har fået tildelt rollen Søgning efter overholdelse, men ikke har rollen Eksportér, hente resultaterne af en søgning, hvor eksporthandlingen blev startet af en bruger, der har fået tildelt rollen Eksportér. Brugeren uden rollen Eksportér kan hente resultaterne af en søgning i op til to uger, efter at den første eksporthandling blev oprettet. Derefter kan de ikke downloade resultaterne, medmindre en person med rollen Eksport genstarter eksporten.

Den udvidede periode på to uger til visning og eksport af søgeresultater (uden de tilsvarende søge- og eksportroller) gælder ikke for eDiscovery (Premium). Brugerne skal have tildelt rollerne Eksempel og Eksportér for at få vist og eksportere indhold i eDiscovery (Premium).

### <a name="custodian"></a>Vogter

Denne rolle giver brugerne mulighed for at identificere og administrere tilsynsførende for eDiscovery-sager (Premium) og bruge oplysningerne fra Azure Active Directory og andre kilder til at finde datakilder, der er knyttet til tilsynsførende. Brugeren kan knytte andre datakilder, f.eks. postkasser, SharePoint websteder, og Teams med tilsynsførende i en sag. Brugeren kan også tilbageholde de datakilder, der er knyttet til tilsynsførende, for at bevare indhold i forbindelse med en sag.

Du kan finde flere oplysninger [under Arbejd med vogtere i eDiscovery (Premium)](managing-custodians.md).

### <a name="export"></a>eksportér

Rollen giver brugerne mulighed for at eksportere resultaterne af en indholdssøgning til en lokal computer. Det giver dem også mulighed for at forberede søgeresultater til analyse i eDiscovery (Premium).

Du kan finde flere oplysninger om eksport af søgeresultater under [Eksportér søgeresultater fra Microsoft Purview-overholdelsesportalen](export-search-results.md).

### <a name="hold"></a>Holde

Denne rolle giver brugerne mulighed for at placere indhold i venteposition i postkasser, offentlige mapper, websteder, Skype for Business samtaler og Microsoft 365 grupper. Når indhold er i venteposition, kan indholdsejere stadig ændre eller slette det oprindelige indhold, men indholdet bevares, indtil ventepositionen fjernes, eller indtil varigheden af ventepositionen udløber.

Du kan få flere oplysninger om ventepositioner i:

- [Opret en venteposition i eDiscovery (Standard)](create-ediscovery-holds.md) 

- [Opret en venteposition i eDiscovery (Premium)](add-custodians-to-case.md)

### <a name="preview"></a>Preview

Denne rolle giver brugerne mulighed for at få vist en liste over elementer, der blev returneret fra en indholdssøgning. De kan også åbne og få vist hvert element på listen for at få vist indholdet.

### <a name="review"></a>Vurder

Denne rolle giver brugerne adgang til korrektursæt i [eDiscovery (Premium)](overview-ediscovery-20.md). Brugere, der har fået tildelt denne rolle, kan se og åbne listen over sager på siden **eDiscovery > Avanceret** på den overholdelsesportal, de er medlem af. Når brugeren har adgang til en eDiscovery-sag (Premium), kan vedkommende vælge **Gennemse sæt** for at få adgang til sagsdata. Denne rolle tillader ikke, at brugeren får vist resultaterne af en samlingssøgning, der er knyttet til sagen, eller udfører andre søge- eller sagsstyringsopgaver. Brugere med denne rolle kan kun få adgang til dataene i et korrektursæt.

### <a name="rms-decrypt"></a>RMS-dekryptering

Denne rolle giver brugerne mulighed for at få vist rettighedsbeskyttede mails, når de får vist søgeresultater og eksportere dekrypterede rettighedsbeskyttede mails. Denne rolle giver også brugerne mulighed for at få vist (og eksportere) en fil, der er krypteret med en [Microsoft-krypteringsteknologi](encryption.md) , når den krypterede fil er knyttet til en mail, der er inkluderet i resultaterne af en eDiscovery-søgning. Denne rolle giver desuden brugerne mulighed for at gennemse og forespørge på krypterede vedhæftede filer i mails, der føjes til et korrektursæt i eDiscovery (Premium). Du kan finde flere oplysninger om dekryptering i eDiscovery [under Dekryptering i Microsoft 365 eDiscovery-værktøjer](ediscovery-decryption.md).

### <a name="search-and-purge"></a>Søg og fjern

Denne rolle giver brugerne mulighed for at udføre massefjernelse af data, der opfylder kriterierne for en indholdssøgning. Du kan finde flere oplysninger under [Søg efter og slet mails i din organisation](search-for-and-delete-messages-in-your-organization.md).

## <a name="adding-role-groups-as-members-of-ediscovery-cases"></a>Tilføjelse af rollegrupper som medlemmer af eDiscovery-sager

Du kan tilføje rollegrupper som medlemmer af eDiscovery-sager (Standard) og eDiscovery-sager (Premium), så medlemmer af rollegrupperne kan få adgang til og udføre opgaver i de tildelte sager. De roller, der er tildelt rollegruppen, definerer, hvad medlemmer af rollegruppen kan gøre. Hvis du derefter tilføjer en rollegruppe som medlem af sagen, kan medlemmerne få adgang til og udføre disse opgaver i en bestemt sag. Du kan få flere oplysninger om tilføjelse af rollegrupper som medlemmer af sager i:

- [Kom i gang med eDiscovery (Standard)](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-ediscovery-standard-case)

- [Tilføj eller fjern medlemmer fra en eDiscovery-sag (Premium)](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

Med dette in mente er det vigtigt at vide, at hvis en rolle tilføjes eller fjernes fra en rollegruppe, fjernes denne rollegruppe automatisk som medlem af alle tilfælde, som rollegruppen er medlem af. Årsagen til dette er at beskytte din organisation mod utilsigtet at give yderligere tilladelser til medlemmer af en sag. Hvis en rollegruppe slettes, fjernes den på samme måde fra alle de sager, den var medlem af.

Før du tilføjer eller fjerner roller til en rollegruppe, der kan være medlem af en eDiscovery-sag, kan du køre følgende kommandoer i [Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) for at få en liste over sager, som rollegruppen er medlem af. Når du har opdateret rollegruppen, tilføjer du rollegruppen igen som medlem af disse sager.

### <a name="get-a-list-of-ediscovery-standard-cases-a-role-group-is-assigned-to"></a>Hent en liste over eDiscovery-sager (Standard), som en rollegruppe er tildelt til

```powershell
Get-ComplianceCase -RoleGroup "Name of role group"
```

### <a name="get-a-list-of-ediscovery-premium-cases-a-role-group-is-assigned-to"></a>Hent en liste over eDiscovery-sager (Premium), som en rollegruppe er tildelt

```powershell
Get-ComplianceCase -RoleGroup "Name of role group" -CaseType AdvancedEdiscovery
```

## <a name="more-information"></a>Flere oplysninger

- **Hvorfor oprette en eDiscovery-administrator?** Som tidligere forklaret er en eDiscovery-administrator medlem af rollegruppen eDiscovery Manager, som kan få vist og få adgang til alle eDiscovery-sager i din organisation. Denne mulighed for at få adgang til alle eDiscovery-sager har to vigtige formål:

  - Hvis en person, der er det eneste medlem af en eDiscovery-sag, forlader organisationen, kan ingen (herunder medlemmer af rollegruppen Organisationsadministration eller et andet medlem af rollegruppen eDiscovery Manager) få adgang til denne eDiscovery-sag, fordi de ikke er medlem af en sag. I denne situation er der ingen måde at få adgang til dataene på i dette tilfælde. Men da en eDiscovery-administrator kan få adgang til alle eDiscovery-sager i organisationen, kan vedkommende få vist sagen og tilføje sig selv eller en anden eDiscovery-administrator som medlem af sagen.

  - Da en eDiscovery-administrator kan få vist og få adgang til alle sager med eDiscovery (Standard) og eDiscovery (Premium), kan de overvåge og overvåge alle sager og tilknyttede søgninger efter overholdelse af angivne standarder. Dette kan hjælpe med at forhindre misbrug af søgninger i overholdelse af angivne standarder eller eDiscovery-sager. Og da eDiscovery-administratorer kan få adgang til potentielt følsomme oplysninger i resultaterne af en søgning efter overholdelse, skal du begrænse antallet af personer, der er eDiscovery-administratorer.

- **Kan jeg tilføje en gruppe som medlem af rollegruppen eDiscovery Manager?** Som tidligere forklaret kan du tilføje en mailaktiveret sikkerhedsgruppe som medlem af undergruppen eDiscovery Managers i rollegruppen eDiscovery Manager ved hjælp af cmdlet'en **Add-RoleGroupMember** i Security & Compliance Center PowerShell. Du kan f.eks. køre følgende kommando for at føje en mailaktiveret sikkerhedsgruppe til rollegruppen eDiscovery Manager. 

  ```powershell
  Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
  ```

    Exchange distributionsgrupper og Microsoft 365-grupper understøttes ikke. Du skal bruge en mailaktiveret sikkerhedsgruppe, som du kan oprette i Exchange Online PowerShell ved at køre `New-DistributionGroup -Type Security`. Du kan også oprette en mailaktiveret sikkerhedsgruppe (og tilføje medlemmer) i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> eller i [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339). Det kan tage op til 60 minutter, efter du har oprettet den, for at en ny mailaktiveret sikkerhedsgruppe kan føjes til rollegruppen eDiscovery-ledere.

    Som tidligere angivet kan du heller ikke gøre en mailaktiveret sikkerhedsgruppe til eDiscovery-administrator ved hjælp af cmdlet'en **Add-eDiscoveryCaseAdmin** i Security & Compliance Center PowerShell. Du kan kun tilføje individuelle brugere som eDiscovery-administratorer.

    Du kan heller ikke tilføje en mailaktiveret sikkerhedsgruppe som medlem af en sag.
