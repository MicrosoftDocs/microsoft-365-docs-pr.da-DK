---
title: Tildel eDiscovery-tilladelser i Microsoft 365 Overholdelsescenter
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
description: Tildel de tilladelser, der kræves for at udføre eDiscovery-relaterede opgaver ved hjælp Microsoft 365 Overholdelsescenter.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: 129363fe614bafef653fe65b39fa15d50a3b1c8a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63589517"
---
# <a name="assign-ediscovery-permissions-in-the-microsoft-365-compliance-center"></a>Tildel eDiscovery-tilladelser i Microsoft 365 Overholdelsescenter

Hvis du ønsker, at folk skal bruge et af [de eDiscovery-relaterede](ediscovery.md) værktøjer i Microsoft 365 Overholdelsescenter, skal du tildele dem de relevante tilladelser. Den nemmeste måde at gøre dette på er at tilføje den relevante rollegruppe **på siden Tilladelser** i Overholdelsescenter. I dette emne beskrives de tilladelser, der kræves for at udføre eDiscovery-opgaver.
  
Den primære eDiscovery-relaterede rollegruppe i Microsoft 365 Overholdelsescenter kaldes **eDiscovery Manager**. Der er to undergrupper i denne rollegruppe.
  
- **eDiscovery Manager** – En eDiscovery-leder kan bruge eDiscovery-søgeværktøjer til at søge efter indholdsplaceringer i organisationen og udføre forskellige søgerelaterede handlinger som f.eks. forhåndsvisning og eksport af søgeresultater. Medlemmer kan også oprette og administrere sager i Core eDiscovery og Advanced eDiscovery, tilføje og fjerne medlemmer til en sag, oprette ventende sager, køre søgninger knyttet til en sag og få adgang til sagsdata. eDiscovery-ledere kan kun få adgang til og administrere de sager, de opretter. De kan ikke få adgang til eller administrere sager, der er oprettet af andre eDiscovery-ledere.
  
- **eDiscovery-administrator** – En eDiscovery-administrator er medlem af rollegruppen eDiscovery Manager og kan udføre den samme indholdssøgning og sagsstyringsrelaterede opgaver, som en eDiscovery-leder kan udføre. Desuden kan en eDiscovery-administrator:
  
  - Få adgang til alle sager, der er angivet **på Core eDiscovery****- Advanced eDiscovery** siderne i Microsoft 365 Overholdelsescenter.

  - Få adgang til sagsdata Advanced eDiscovery i alle tilfælde i organisationen.
  
  - Administrer en hvilken som helst eDiscovery-sag, når de tilføjer sig selv som medlem af sagen.
  
  - Fjern medlemmer fra en eDiscovery-sag. Kun en eDiscovery-administrator kan fjerne medlemmer fra en sag. Brugere, der er medlemmer af undergruppen eDiscovery Manager, kan ikke fjerne medlemmer fra en sag, heller ikke selvom brugeren har oprettet sagen.
  
  Du kan finde mulige årsager til, at du bør have eDiscovery-administratorer i din organisation, [under Flere oplysninger](#more-information).

> [!NOTE]
> For at analysere en brugers data ved hjælp Advanced eDiscovery, skal brugeren (den, der skal have tilladelse til dataene) tildeles Office 365 E5 en Microsoft 365 E5 licens. Alternativt kan brugere med en Office 365 E1- eller Office 365- eller Microsoft 365 E3-licens tildeles en licens til Microsoft 365 E5 Overholdelse eller Microsoft 365 eDiscovery og Overvågning tilføjelsesprogrammet. Administratorer, compliance officers, or legal personnel who are assigned to cases as members and use Advanced eDiscovery to collect, view, and analyze data don't need an E5 license. Du kan finde flere Advanced eDiscovery om licenser i [Abonnementer og licenser i Advanced eDiscovery](overview-ediscovery-20.md#subscriptions-and-licensing).
  
## <a name="before-you-assign-permissions"></a>Før du tildeler tilladelser

- Du skal være medlem af rollegruppen Organisationsadministration eller være tildelt rollen som rollestyring for at tildele eDiscovery-tilladelser i Microsoft 365 Overholdelsescenter.

- Du kan bruge cmdlet'en [Add-RoleGroupMember](/powershell/module/exchange/Add-RoleGroupMember) i Security & Compliance Center PowerShell til at tilføje en mailaktiveret sikkerhedsgruppe som medlem af undergruppen eDiscovery-ledere i rollegruppen eDiscovery Manager. Du kan dog ikke føje en mailaktiveret sikkerhedsgruppe til undergruppen eDiscovery-administratorer. Du kan få mere at vide [under Flere oplysninger](#more-information).
  
## <a name="assign-ediscovery-permissions"></a>Tildel eDiscovery-tilladelser

1. Gå til siden <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 Overholdelsescenter</a> og log på med en konto, der kan tildele tilladelser.
  
2. I venstre rude skal du **vælge Tilladelser**.

3. Klik på **Roller & Siden** Tilladelser **og** roller under **Overholdelsescenter**.

4. På siden **Roller for Overholdelsescenter** skal du vælge **eDiscovery Manager**.
  
5. På pop **op-siden eDiscovery Manager** skal du gøre et af følgende baseret på de eDiscovery-tilladelser, du vil tildele.
  
    **Sådan gør du en bruger til eDiscovery Manager:** Ud for **eDiscovery Manager skal** du vælge **Rediger**. På siden **Vælg guiden eDiscovery Manager** skal du klikke på ![Tilføj ikon.](../media/ITPro-EAC-AddIcon.gif) **Tilføj**. Vælg den bruger (eller brugere), du vil tilføje som eDiscovery-leder, og vælg derefter **Tilføj**. Når du er færdig med at tilføje brugere, skal du vælge **Udført**. På siden med guiden **Redigeringsvælg eDiscovery Manager** skal  du vælge Gem for at gemme ændringerne til medlemskabet af eDiscovery Manager.
  
    **Sådan gør du en bruger til eDiscovery-administrator:** Ud for **eDiscovery-administrator skal** du vælge **Rediger**. Klik på **Tilføj ikon på siden Vælg** ![eDiscovery-administrator.](../media/ITPro-EAC-AddIcon.gif) **Tilføj**. Vælg den bruger (eller brugere), du vil tilføje som **eDiscovery-administrator**, og vælg derefter  **Tilføj**. Når du er færdig med at tilføje brugere, skal du vælge **Udført**. På siden med guiden **Redigeringsvælg eDiscovery-administrator** skal du vælge Gem for at gemme ændringerne til eDiscovery-administratormedlemskabet.
  
> [!NOTE]
> Du kan også bruge **Add-eDiscoveryCaseAdmin-cmdlet'en** til at gøre en bruger til eDiscovery-administrator. Brugeren skal dog have tildelt rollen som sagsadministration, før du kan bruge denne cmdlet til at gøre vedkommende til eDiscovery-administrator. Du kan få mere at [vide under Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin). 
  
På siden Tilladelser i Microsoft 365 Overholdelsescenter kan du også tildele brugere eDiscovery-relaterede tilladelser ved at føje dem til rollegrupperne **Overholdelsesadministrator**, Organisationsadministration og Korrekturlæser. Hvis du vil have en beskrivelse af de eDiscovery-relaterede RBAC-roller, der er tildelt hver af disse rollegrupper, skal du se RBAC-roller, der er relateret til [eDiscovery](#rbac-roles-related-to-ediscovery).

## <a name="rbac-roles-related-to-ediscovery"></a>RBAC-roller relateret til eDiscovery

I følgende tabel vises de eDiscovery-relaterede RBAC-roller i Microsoft 365 Overholdelsescenter og angiver de indbyggede rollegrupper, som hver rolle er tildelt som standard.
  
| Rolle | Overholdelsesadministrator | eDiscovery Manager & administrator | Organisationsadministration | Korrekturlæser |
|:-----|:-----:|:-----:|:-----:|:-----:|
|Sagsadministration <br/> |![Markering.](../media/checkmark.png) <br/> |![Markering.](../media/checkmark.png) <br/> |![Markering.](../media/checkmark.png) <br/> | <br/> |
|Kommunikation <br/> | <br/> |![Markering.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Søgning i overholdelse af regler og standarder <br/> |![Markering.](../media/checkmark.png) <br/> |![Markering.](../media/checkmark.png) <br/> |![Markering.](../media/checkmark.png) <br/> | <br/> |
|Øvøvrisk <br/> | <br/> |![Markering.](../media/checkmark.png) <br/> | <br/> | <br/> |
|eksportér <br/> | <br/> |![Markering.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Venteposition <br/>  |![Markering.](../media/checkmark.png) <br/> |![Markering.](../media/checkmark.png) <br/> |![Markering.](../media/checkmark.png) <br/> | <br/> |
|Eksempel <br/>  | <br/> |![Markering.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Gennemse <br/>  | <br/> |![Markering.](../media/checkmark.png) <br/> | <br/> |![Markering](../media/checkmark.png) <br/> |
|RMS Dekrypter <br/>  ||![Markering](../media/checkmark.png) <br/> |||
|Søg og tøm <br/> | <br/> | <br/> |![Markering](../media/checkmark.png)           <br/> | <br/> |
||||
  
I de følgende afsnit beskrives hver af de eDiscovery-relaterede RBAC-roller, der er angivet i den forrige tabel.

### <a name="case-management"></a>Sagsadministration

Denne rolle giver brugerne mulighed for at oprette, redigere, slette og kontrollere adgangen til kerne eDiscovery og Advanced eDiscovery sager i Microsoft 365 Overholdelsescenter. Som beskrevet tidligere skal en bruger tildeles rollen som sagsadministration, før du kan bruge **Add-eDiscoveryCaseAdmin-cmdlet'en** til at gøre brugeren til en eDiscovery-administrator.

Du kan finde flere oplysninger under:

- [Introduktion til Core eDiscovery](get-started-core-ediscovery.md)

- [Introduktion til Advanced eDiscovery](get-started-with-advanced-ediscovery.md)

### <a name="communication"></a>Kommunikation

Denne rolle gør det muligt for brugerne at administrere al kommunikation med de ledende brugere, der er identificeret Advanced eDiscovery sag. Dette omfatter oprettelse af ventepositionsmeddelelser, ventepositionspåmindelser og eskaleringer til administrationen. Brugeren kan også registrere anerkendelse af ventepositionsmeddelelser og administrere adgangen til den modtagende portal, der bruges af hver leder, til at spore kommunikation for de tilfælde, hvor de blev identificeret som en hjælper.

Få mere at vide under [Arbejd med kommunikation i Advanced eDiscovery](managing-custodian-communications.md).

### <a name="compliance-search"></a>Søgning i overholdelse af regler og standarder

Denne rolle giver brugerne mulighed for at køre værktøjet indholdssøgning i Microsoft 365 Overholdelsescenter til at søge i postkasser og offentlige mapper, SharePoint Online-websteder, OneDrive for Business websteder, Skype for Business samtaler, Microsoft 365 grupper, Microsoft Teams og Yammer grupper. Denne rolle gør det muligt for en bruger at få et skøn over søgeresultaterne og oprette eksportrapporter, men der er behov for andre roller for at starte handlinger til indholdssøgning, f.eks. visning, eksport eller sletning af søgeresultater.

I Indholdssøgning og Core eDiscovery kan brugere, der er tildelt overholdelsessøgningsrollen, men ikke har rollen Eksempel, få vist resultaterne af en søgning, hvor eksempelhandlingen er blevet startet af en bruger, der er tildelt rollen Preview. Brugeren uden rollen Eksempel kan få vist resultaterne i op til to uger efter, at den første eksempelhandling blev oprettet.

På samme måde kan brugere i Indholdssøgning og Core eDiscovery, der er tildelt rollen Overholdelsessøgning, men ikke har eksportrollen, hente resultaterne af en søgning, hvor eksporthandlingen blev startet af en bruger, der er tildelt eksportrollen. Brugeren uden eksportrollen kan hente resultaterne af en søgning i op til to uger efter, at den indledende eksporthandling blev oprettet. Derefter kan de ikke hente resultaterne, medmindre en person med eksportrollen genstarter eksporten.

Den ekstra periode på to uger til forhåndsvisning og eksport af søgeresultater (uden de tilsvarende søge- og eksportroller) gælder ikke for Advanced eDiscovery. Brugere skal have tildelt rollerne Eksempel og Eksportér for at få vist og eksportere indhold Advanced eDiscovery.

### <a name="custodian"></a>Øvøvrisk

Denne rolle gør det muligt for brugerne at identificere og administrere ledende personer for Advanced eDiscovery og bruge oplysningerne fra Azure Active Directory og andre kilder til at finde datakilder, der er knyttet til ledende personer. Brugeren kan knytte andre datakilder, f.eks. postkasser, SharePoint websteder og Teams med øvvarsler i en sag. Brugeren kan også placere retsligt fast hold på de datakilder, der er knyttet til brugerere, for at bevare indhold i forbindelse med en sag.

Du kan få mere at vide [under Arbejde med y-y-Advanced eDiscovery](managing-custodians.md).

### <a name="export"></a>eksportér

Rollen gør det muligt for brugerne at eksportere resultaterne af en indholdssøgning til en lokal computer. Det gør det også muligt for dem at forberede søgeresultaterne til analyse Advanced eDiscovery.

Du kan finde flere oplysninger om eksport af søgeresultater [under Eksportér søgeresultater fra Microsoft 365 Overholdelsescenter](export-search-results.md).

### <a name="hold"></a>Venteposition

Denne rolle giver brugerne mulighed for at placere indhold i venteposition i postkasser, offentlige mapper, websteder, Skype for Business samtaler og Microsoft 365 grupper. Når indhold er i venteposition, kan indholdsejere stadig redigere eller slette det oprindelige indhold, men indholdet bevares, indtil ventepositionen fjernes, eller indtil varigheden af ventepositionen udløber.

Hvis du vil have mere at vide om ventende ting, skal du se:

- [Opret en venteposition i Core eDiscovery](create-ediscovery-holds.md) 

- [Opret en venteposition i Advanced eDiscovery](add-custodians-to-case.md)

### <a name="preview"></a>Eksempel

Denne rolle giver brugerne mulighed for at få vist en liste over elementer, der blev returneret fra en indholdssøgning. De kan også åbne og få vist hvert element på listen for at få vist indholdet.

### <a name="review"></a>Gennemse

Denne rolle giver brugerne adgang til korrektursæt [i Advanced eDiscovery](overview-ediscovery-20.md). Brugere, der er tildelt denne rolle, kan se og åbne listen over sager på siden **eDiscovery > Avanceret** i Microsoft 365 Overholdelsescenter, som de er medlem af. Når brugeren har adgang til en Advanced eDiscovery sag, kan de vælge Gennemse sæt for **at få** adgang til sagsdata. Denne rolle tillader ikke, at brugeren får vist resultaterne af en søgning i en samling, der er knyttet til sagen, eller at udføre andre søgninger eller opgaver i forbindelse med sagsadministration. Brugere med denne rolle kan kun få adgang til dataene i et gennemsynssæt.

### <a name="rms-decrypt"></a>RMS Dekrypter

Denne rolle giver brugerne mulighed for at få vist rettighedsbeskyttede mails, når de får vist søgeresultaterne og eksportere dekrypterede rettighedsbeskyttede mails. Denne rolle giver også brugerne mulighed for at få vist (og eksportere) en fil, der er [](encryption.md) krypteret med en Microsoft-krypteringsteknologi, når den krypterede fil vedhæftes en mail, der medtages i resultaterne af en eDiscovery-søgning. Denne rolle giver desuden brugerne mulighed for at gennemse og forespørge på krypterede vedhæftede filer i mails, der er føjet til et gennemsynssæt Advanced eDiscovery. Du kan finde flere oplysninger om dekryptering i eDiscovery i [Dekryptering Microsoft 365 eDiscovery-værktøjer](ediscovery-decryption.md).

### <a name="search-and-purge"></a>Søg og tøm

Denne rolle gør det muligt for brugerne at fjerne flere data, der opfylder kriterierne for en indholdssøgning. Få mere at vide under [Søg efter og slet mails i din organisation](search-for-and-delete-messages-in-your-organization.md).

## <a name="adding-role-groups-as-members-of-ediscovery-cases"></a>Tilføje rollegrupper som medlemmer af eDiscovery-sager

Du kan tilføje rollegrupper som medlemmer af Core eDiscovery og Advanced eDiscovery-sager, så medlemmer af rollegrupperne kan få adgang til og udføre opgaver i de tildelte sager. De roller, der er tildelt rollegruppen, definerer, hvad medlemmer af rollegruppen kan gøre. Når der derefter tilføjes en rollegruppe som medlem af sagen, kan medlemmer få adgang til og udføre disse opgaver i en bestemt sag. Du kan finde flere oplysninger om at tilføje rollegrupper som medlemmer af sager i:

- [Introduktion til Core eDiscovery](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-core-ediscovery-case)

- [Tilføj eller fjern medlemmer fra en Advanced eDiscovery sag](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

Med dette i baghovedet er det vigtigt at vide, at hvis en rolle tilføjes eller fjernes fra en rollegruppe, fjernes den pågældende rollegruppe automatisk som medlem af alle tilfælde, hvor rollegruppen er medlem af. Dette skyldes, at du beskytter din organisation mod utilsigtet at give ekstra tilladelser til medlemmer af en sag. På samme måde vil en rollegruppe, hvis den slettes, blive fjernet fra alle tilfælde, den var medlem af.

Før du tilføjer eller fjerner roller til en rollegruppe, der kan være medlem af en eDiscovery-sag, kan du køre følgende kommandoer i [Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) for at få en liste over de tilfælde, rollegruppen er medlem af. Når du har opdateret rollegruppen, kan du tilføje rollegruppen tilbage som medlem af disse sager.

### <a name="get-a-list-of-core-ediscovery-cases-a-role-group-is-assigned-to"></a>Få en liste over kerne eDiscovery-sager, som en rollegruppe er tildelt

```powershell
Get-ComplianceCase -RoleGroup "Name of role group"
```

### <a name="get-a-list-of-advanced-ediscovery-cases-a-role-group-is-assigned-to"></a>Få en liste over Advanced eDiscovery der er tildelt en rollegruppe til

```powershell
Get-ComplianceCase -RoleGroup "Name of role group" -CaseType AdvancedEdiscovery
```

## <a name="more-information"></a>Flere oplysninger

- **Hvorfor oprette en eDiscovery-administrator?** Som beskrevet tidligere er en eDiscovery-administrator medlem af rollegruppen eDiscovery Manager, der kan få vist og få adgang til alle eDiscovery-sager i din organisation. Denne mulighed for at få adgang til alle eDiscovery-sager har to vigtige formål:

  - Hvis en person, der er det eneste medlem af en eDiscovery-sag, forlader din organisation, kan ingen (herunder medlemmer af rollegruppen organisationsadministration eller et andet medlem af rollegruppen eDiscovery-leder) få adgang til denne eDiscovery-sag, fordi de ikke er medlem af en sag. I denne situation er det ikke muligt at få adgang til dataene i dette tilfælde. Men fordi en eDiscovery-administrator kan få adgang til alle eDiscovery-sager i organisationen, kan de få vist sagen og tilføje sig selv eller en anden eDiscovery-leder som medlem af sagen.

  - Da en eDiscovery-administrator kan få vist og få adgang til alle kerne eDiscovery- og Advanced eDiscovery-sager, kan de overvåge og overvåge alle tilfælde og tilknyttede overholdelsessøgninger. Dette kan hjælpe med at forhindre misbrug af søgninger i overholdelse eller eDiscovery-sager. Og da eDiscovery-administratorer kan få adgang til potentielt følsomme oplysninger i resultaterne af en overholdelsessøgning, skal du begrænse antallet af personer, der er eDiscovery-administratorer.

- **Kan jeg tilføje en gruppe som medlem af rollegruppen eDiscovery Manager?** Som beskrevet tidligere kan du tilføje en mailaktiveret sikkerhedsgruppe som medlem af undergruppen eDiscovery-ledere i rollegruppen eDiscovery Manager ved hjælp af **Cmdlet'en Add-RoleGroupMember** i Security & Compliance Center PowerShell. Du kan f.eks. køre følgende kommando for at føje en mailaktiveret sikkerhedsgruppe til rollegruppen eDiscovery Manager. 

  ```powershell
  Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
  ```

    Exchange distributionsgrupper og Microsoft 365-grupper understøttes ikke. Du skal bruge en mailaktiveret sikkerhedsgruppe, som du kan oprette i Exchange Online PowerShell ved at køre `New-DistributionGroup -Type Security`. Du kan også oprette en mailaktiveret sikkerhedsgruppe (og tilføje medlemmer) <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a> eller i [Microsoft 365 Administration](https://go.microsoft.com/fwlink/p/?linkid=2024339). Det kan tage op til 60 minutter, efter du har oprettet den, før en ny mailaktiveret sikkerhedsgruppe kan føjes til rollegruppen eDiscovery-ledere.

    Som tidligere nævnt kan du heller ikke gøre en mailaktiveret sikkerhedsgruppe til en eDiscovery-administrator ved hjælp af **Add-eDiscoveryCaseAdmin-cmdlet'en** i Security & Compliance Center PowerShell. Du kan kun tilføje individuelle brugere som eDiscovery-administratorer.

    Du kan heller ikke tilføje en mailaktiveret sikkerhedsgruppe som medlem af en sag.
