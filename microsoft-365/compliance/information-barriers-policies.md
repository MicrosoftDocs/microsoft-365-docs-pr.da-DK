---
title: Introduktion til informationsbarrierer
description: Få mere at vide om, hvordan du kommer i gang med informationsbarrierer.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1a9b6a4000b6d96fa8fe60b3abc60ff01676073e
ms.sourcegitcommit: 7b83e2605895fee5c73cd1d01f4cd16e1457a69f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/11/2021
ms.locfileid: "63589525"
---
# <a name="get-started-with-information-barriers"></a>Introduktion til informationsbarrierer

Med informationsbarrierer kan du definere politikker, der er designet til at forhindre visse segmenter af brugere i at kommunikere med hinanden eller tillade, at bestemte segmenter kun kommunikerer med visse andre segmenter. Politikker for informationsbarrierer kan hjælpe din organisation med at opretholde overholdelse af relevante branchestandarder og -bestemmelser og undgå potentielle konflikter af interesse. Få mere at vide under [Få mere at vide om informationsbarrierer](information-barriers.md).

Denne artikel beskriver, hvordan du konfigurerer politikker for informationsbarrierer. Der er flere trin involveret, så sørg for at gennemgå hele processen, før du går i gang med at konfigurere politikker for informationsbarrierer.

> [!TIP]
> Denne artikel indeholder et [eksempelscenarie, der kan](#example-scenario-contosos-departments-segments-and-policies) hjælpe dig med at planlægge og definere politikker for informationsbarrierer.

## <a name="concepts"></a>Koncepter

Når du definerer politikker for informationsbarrierer, kommer du til at arbejde med brugerkontoattributter, segmenter, "bloker" og/eller "tillad"-politikker og politikprogram.

- Attributter for brugerkonti er defineret i Azure Active Directory (eller Exchange Online). Disse attributter kan omfatte afdeling, stilling, placering, teamnavn og andre oplysninger om jobprofilen.
- Segmenter er sæt af brugere, der er defineret i Microsoft 365 Overholdelsescenter bruger en valgt **brugerkontoattribut**. (Se listen [over understøttede attributter](information-barriers-attributes.md)).
- Politikker for informationsbarrierer bestemmer kommunikationsgrænser eller -begrænsninger. Når du definerer politikker for informationsbarrierer, kan du vælge mellem to typer politikker:
  - *Bloker* politikker forhindrer ét segment i at kommunikere med et andet segment.
  - *Tillad* politikker tillader, at ét segment kun kommunikerer med visse andre segmenter.
- Politikprogrammet udføres, når alle politikker for informationsbarrierer er defineret, og du er klar til at anvende dem i din organisation.

## <a name="configuration-at-a-glance"></a>Hurtigt overblik over konfiguration

| **Trin** | **Det, der er involveret** |
|:------|:----------------|
| **Trin 1**: [Sørg for, at forudsætningerne er opfyldt](#step-1-make-sure-prerequisites-are-met) | - Bekræft, at du [har de nødvendige licenser og tilladelser](information-barriers.md#required-licenses-and-permissions)<br/>- Kontrollér, at mappen indeholder data til segmentering af brugere<br/>- Aktivér områdebaseret mappesøgning for Microsoft Teams<br/>- Sørg for, at overvågningslogføring er slået til<br/>- Sørg for, Exchange politikkerne for adressekartoteket ikke er på plads<br/>- Brug PowerShell (eksempler er angivet)<br/>- Give administratorsamtykke til Microsoft Teams (trin er inkluderet) |
| **Trin 2**: [Segmenter brugere i organisationen](#step-2-segment-users-in-your-organization) | - Fastlægge, hvilke politikker der skal bruges<br/>- Oprette en liste over segmenter for at definere<br/>- Identificere, hvilke attributter der skal bruges<br/>- Definere segmenter med hensyn til politikfiltre |
| **Trin 3**: [Definer politikker for informationsbarrierer](#step-3-define-information-barrier-policies) | - Definere dine politikker (gælder ikke endnu)<br/>- Vælge mellem to typer (bloker eller tillad) |
| **Trin 4**: [Anvend politikker for informationsbarrierer](#step-4-apply-information-barrier-policies) | - Angive politikker til aktiv status<br/>- Kør politikprogrammet<br/>- Vis politikstatus |
| **Trin 5**: [Konfiguration af informationsbarrierer på SharePoint og OneDrive (valgfrit)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | - Konfigurere informationsbarrierer for SharePoint og OneDrive |
| **Trin 6**: [Informationsbarrieretilstande (valgfrit)](#step-6-information-barriers-modes) | - Opdater tilstandene for informationsbarrierer, hvis det er relevant |

## <a name="step-1-make-sure-prerequisites-are-met"></a>Trin 1: Sørg for, at forudsætningerne er opfyldt

Ud over de nødvendige [licenser og tilladelser skal du sørge](information-barriers.md#required-licenses-and-permissions) for, at følgende krav er opfyldt, før du konfigurerer informationsbarrierer:

- **Katalogdata**: Sørg for, at organisationens struktur afspejles i katalogdata. For at gøre dette skal du sørge for, at attributter for brugerkontoen, f.eks. gruppemedlemskab, afdelingsnavn osv. er udfyldt korrekt i Azure Active Directory (eller Exchange Online). Du kan få mere at vide i følgende ressourcer:
  - [Attributter for politikker for informationsbarrierer](information-barriers-attributes.md)
  - [Tilføj eller opdater en brugers profiloplysninger ved hjælp af Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [Konfigurere egenskaber for brugerkonti med Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **Omfangssøgning i kataloger**: Før du definerer din organisations første politik for informationsbarrierer, skal du aktivere begrænset [katalogsøgning Microsoft Teams](/MicrosoftTeams/teams-scoped-directory-search). Vent mindst 24 timer, efter du har aktiveret en fastsat katalogsøgning, før du konfigurerer eller definerer politikker for informationsbarrierer.

- **Exchange Online licenser**: Politikker for informationsbarrierer fungerer kun, hvis målbrugere har fået tildelt en Exchange Online licens.

- **Kontrollér, at overvågningslogføring** er aktiveret: Overvågningslogføring skal være aktiveret for at kunne slå status for et politikprogram til. Overvågning er aktiveret for Microsoft 365 organisationer som standard. Nogle organisationer har deaktiveret overvågning af bestemte årsager. Hvis overvågning er deaktiveret for organisationen, kan det skyldes, at en anden administrator har slået det fra. Vi anbefaler, at du bekræfter, at det er OK at slå overvågning til igen, når du udfører dette trin. Du kan finde flere oplysninger [i Slå søgning i overvågningslog til eller fra](turn-audit-log-search-on-or-off.md).

- **Ingen politikker for adressekartotek**: Før du definerer og anvender politikker for informationsbarrierer, skal du sikre dig, Exchange politikkerne for adressekartoteket ikke er på plads. Informationsbarrierer er baseret på adressekartotekspolitikker, men de to typer politikker er ikke kompatible. Hvis du har disse politikker, skal du først fjerne [politikkerne for adressekartoteket](/exchange/address-books/address-book-policies/remove-an-address-book-policy) . Når politikker for informationsbarrierer er aktiveret, og du har aktiveret hierarkiske adressekartoteket, vil alle brugere, som [](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) ikke er medtaget i et informationsbarrieresegment, se det hierarkiske adressekartotek i Exchange online.****

- **Administrer ved hjælp af PowerShell**: I øjeblikket defineres og administreres politikker for informationsbarrierer i Security & Compliance Center PowerShell. Selvom der findes flere eksempler i denne artikel, skal du være fortrolig med PowerShell-cmdlet'er og parametre. Du skal også bruge Azure Active Directory PowerShell-modulet.
  - [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell)
  - [Installér Azure Active Directory PowerShell til Graph](/powershell/azure/active-directory/install-adv2)

- **Administratorsamtykke** til informationsbarrierer i Microsoft Teams: Når dine IB-politikker er på plads, kan de fjerne brugere, der ikke er IB-overholdelse, fra grupper (dvs. Teams-kanaler, som er baseret på grupper). Denne konfiguration hjælper med at sikre, at din organisation forbliver i overensstemmelse med politikker og bestemmelser. Brug følgende fremgangsmåde for at aktivere politikker for informationsbarrierer for at fungere som forventet i Microsoft Teams.

   1. Forudsætninger: [Installer Azure Active Directory PowerShell til Graph](/powershell/azure/active-directory/install-adv2).

   1. Kør følgende PowerShell-cmdlet'er:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   1. Når du bliver bedt om det, skal du logge på med din arbejds- eller skolekonto Office 365.

   1. Gennemse oplysningerne **i dialogboksen** Anmodning om tilladelser, og vælg derefter **Acceptér**. De tilladelser, der anmodes om af appen, er angivet nedenfor.

      > [!div class="mx-imgBorder"]
      > ![billede.](https://user-images.githubusercontent.com/8932063/107690955-b1772300-6c5f-11eb-9527-4235de860b27.png)

Når alle forudsætningerne er opfyldt, skal du fortsætte til næste trin.

> [!TIP]
> Som hjælp til at forberede din plan er der inkluderet et eksempelscenarie i denne artikel. [Se Contosos afdelinger, segmenter og politikker](#example-scenario-contosos-departments-segments-and-policies).

## <a name="step-2-segment-users-in-your-organization"></a>Trin 2: Segmenter brugere i organisationen

I dette trin fastlægger du, hvilke politikker for informationsbarrierer der er behov for, laver en liste over segmenter, der skal defineres, og definerer derefter dine segmenter.

### <a name="determine-what-policies-are-needed"></a>Fastlægge, hvilke politikker der skal bruges

I betragtning af juridiske og branchebestemmelser, hvem er de grupper i din organisation, der har brug for politikker for informationsbarrierer? Lav en liste. Er der nogen grupper, der bør være forhindret i at kommunikere med en anden gruppe? Er der nogen grupper, der kun skal have tilladelse til at kommunikere med én eller to andre grupper? Tænk over de politikker, du skal bruge, som tilhørende en af to grupper:

- Politikkerne "Bloker" forhindrer, at én gruppe kommunikerer med en anden gruppe.
- Politikkerne "Tillad" gør det muligt for en gruppe kun at kommunikere med bestemte andre, bestemte grupper.

Når du har din første liste over grupper og politikker, skal du fortsætte med at identificere de segmenter, du skal bruge.

### <a name="identify-segments"></a>Identificer segmenter

Ud over den første liste over politikker kan du oprette en liste over segmenter for organisationen. Brugere, som skal være en del af politikker for informationsbarrierer, bør høre til et segment. Planlæg dine segmenter omhyggeligt, da en bruger kun kan være i ét segment. Der kan kun anvendes én politik for informationsbarrierer i hvert segment.

> [!IMPORTANT]
> En bruger kan kun være i ét segment.

Afgør, hvilke attributter i organisationens katalogdata, du skal bruge til at definere segmenter. Du kan bruge *Afdeling*, *Medlem Af* eller en af de understøttede attributter. Sørg for, at du har værdier i den attribut, du vælger til brugere. [Se listen over understøttede attributter for informationsbarrierer](information-barriers-attributes.md).

> [!IMPORTANT]
> **Før du går videre til næste afsnit, skal du sikre dig, at dine katalogdata indeholder værdier for attributter, som du kan bruge til at definere segmenter**. Hvis dine mappedata ikke har værdier for de attributter, du vil bruge, skal brugerkontiene opdateres for at medtage disse oplysninger, før du går videre med informationsbarrierer. Hvis du vil have hjælp til dette, skal du se følgende ressourcer:<br/>- [Konfigurere egenskaber for brugerkonti med Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [Tilføj eller opdater en brugers profiloplysninger ved hjælp af Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>Definer segmenter ved hjælp af PowerShell

Definition af segmenter påvirker ikke brugerne. Det indstiller blot fasen, hvor politikker for informationsbarrierer kan defineres og derefter anvendes.

1. Brug **New-OrganizationSegment-cmdlet'en** med **parameteren UserGroupFilter** , der svarer til [den attribut](information-barriers-attributes.md) , du vil bruge.

    | Syntaks | Eksempel |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>I dette eksempel defineres et segment med *navnet HR* ved hjælp *af HR*, som er en værdi i *attributten* Afdeling. Cmdlet'ens **-lige-del** refererer til "er lig med". (Alternativt kan du bruge - **ne til** at sige "ikke er lig med". Se [Brug af "er lig med" og "ikke lig med" i segmentdefinitioner](#using-equals-and-not-equals-in-segment-definitions)). |

    Når du har kørt hver cmdlet, får du vist en liste med oplysninger om det nye segment. Detaljer omfatter segmentets type, hvem der har oprettet eller senest ændret den osv. 

2. Gentag denne proces for hvert segment, du vil definere.

    > [!IMPORTANT]
    > **Sørg for, at dine segmenter ikke overlapper**. Hver enkelt bruger, der vil blive påvirket af informationsbarrierer, bør høre til ét (og kun ét) segment. Ingen bruger må høre til to eller flere segmenter. Se eksempel [: Contosos definerede segmenter](#contosos-defined-segments) i denne artikel.

Når du har defineret dine segmenter, skal du fortsætte med [at definere politikker for informationsbarrierer](#step-3-define-information-barrier-policies).

### <a name="using-equals-and-not-equals-in-segment-definitions"></a>Brug af "er lig med" og "ikke lig med" i segmentdefinitioner

I følgende eksempel definerer vi et segment, så "Afdeling er lig med HR". 

| Eksempel | Bemærk! |
|:----------|:-------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` | Bemærk, at i dette eksempel omfatter segmentdefinitionen en "er lig med"-parameter, der er angivet som **-eq**. |

Du kan også definere segmenter ved hjælp af parameteren "ikke lig med" angivet som **-ne**, som vist i følgende tabel:

| Syntaks | Eksempel |
|:---------|:----------|
| `New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"` | I dette eksempel har vi defineret et segment med *navnet NotSales* , som omfatter alle, der ikke er i *Salg*. - **ne-delen** af cmdlet'en refererer til "ikke er lig med". |

Ud over at definere segmenter ved hjælp af "er lig med" eller "ikke lig med" kan du definere et segment ved både at bruge parametrene "er lig med" og "ikke lig med". Du kan også definere komplekse gruppefiltre ved hjælp af logiske *AND-* og *OR-operatorer* .

| Syntaks | Eksempel |
|:---------|:----------|
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | I dette eksempel har vi defineret et segment med navnet *LocalFTE* , der omfatter personer, der er placeret lokalt, og hvis placeringer ikke er angivet som *Midlertidige*. |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| I dette eksempel har vi defineret et segment med navnet *Segment1* , der omfatter personer, der er medlemmer group1@contoso.com og ikke medlemmer af group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | I dette eksempel har vi defineret et segment med navnet *Segment2* , der omfatter personer, der er medlemmer group2@contoso.com og ikke medlemmer af group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| I dette eksempel har vi defineret et segment med navnet *Segment1og2* , der omfatter personer, der group1@contoso.com og group2@contoso.com og ikke medlemmer group3@contoso.com. |

> [!TIP]
> Hvis det er muligt, skal du bruge segmentdefinitioner, der omfatter "-lige" eller "-ne". Prøv ikke at definere komplekse segmentdefinitioner.

## <a name="step-3-define-information-barrier-policies"></a>Trin 3: Definer politikker for informationsbarrierer

Afgør, om du har brug for at forhindre kommunikation mellem bestemte segmenter eller begrænse kommunikationen til bestemte segmenter. Ideelt set skal du bruge det mindste antal politikker for at sikre, at din organisation overholder lovmæssige krav og branchekrav.

Med din liste over brugersegmenter og politikker for informationsbarrierer, du vil definere, skal du vælge et scenarie og derefter følge trinnene.

- [Scenarie 1: Bloker kommunikation mellem segmenter](#scenario-1-block-communications-between-segments)
- [Scenarie 2: Tillad, at et segment kun kommunikerer med ét andet segment](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **Sørg for, at du ikke tildeler mere end én politik til et segment, når du definerer politikker**. Hvis du f.eks. definerer én politik for et *segment med navnet* Salg, skal du ikke definere en ekstra politik for *Salg*.<p> Når du definerer politikker for informationsbarrierer, skal du desuden sørge for at angive disse politikker til inaktiv status, indtil du er klar til at anvende dem. Definition (eller redigering) af politikker påvirker ikke brugerne, før disse politikker er indstillet til aktiv status og derefter anvendes.

Se [eksempel: Contosos politikker for informationsbarrierer](#contosos-information-barrier-policies) i denne artikel.

### <a name="scenario-1-block-communications-between-segments"></a>Scenarie 1: Bloker kommunikation mellem segmenter

Når du vil blokere segmenter fra kommunikationen med hinanden, kan du definere to politikker: én for hver retning. Hver politik blokerer kun kommunikation på én måde.

Antag f.eks., at du vil blokere kommunikation mellem Segment A og Segment B. I dette tilfælde definerer du én politik, der forhindrer Segment A i at kommunikere med Segment B, og definerer derefter en anden politik for at forhindre Segment B i at kommunikere med Segment A.

1. Hvis du vil definere din første blokeringspolitik, skal **du bruge New-InformationBarrierPolicy-cmdlet'en** med **parameteren SegmentsBlocked** .

    | Syntaks | Eksempel |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> I dette eksempel har vi defineret en politik kaldet *Salgsundersøgelse* for et segment med navnet *Salg*. Når denne politik er aktiv og anvendt, forhindrer den personer i salg *i* at kommunikere med personer i et segment kaldet *Research*. |

2. For at definere dit andet blokeringssegment skal du bruge **New-InformationBarrierPolicy-cmdlet'en** med parameteren **SegmentsBlocked** igen, denne gang med segmenter tilbageført.

    | Eksempel | Bemærk! |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | I dette eksempel har vi defineret en politik kaldet *Research-Sales for at* forhindre *, at Research* kommunikerer med *Salg*. |

3. Fortsæt til en af følgende handlinger:

   - (Hvis det er nødvendigt) [Definer en politik for at tillade, at et segment kun kommunikerer med ét andet segment](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (Når alle dine politikker er defineret) [Anvend politikker for informationsbarrierer](#step-4-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>Scenarie 2: Tillad, at et segment kun kommunikerer med ét andet segment

1. Hvis du vil tillade, at ét segment kun kommunikerer med ét andet segment, skal du bruge **new-InformationBarrierPolicy-cmdlet'en** med parameteren **SegmentsAllowed** .

    | Syntaks | Eksempel |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> I dette eksempel har vi defineret en politik kaldet *Produktion-HR* for et segment med navnet *Produktion*. Når denne politik er aktiv og anvendt, giver den personer i *produktion kun* mulighed for at kommunikere med personer i et segment med navnet *HR*. (I dette tilfælde kan *produktion ikke* kommunikere med brugere, der ikke er en del af *HR*.) |

    **Hvis det er nødvendigt, kan du angive flere segmenter med denne cmdlet som vist i følgende eksempel.**

    | Syntaks | Eksempel |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> I dette eksempel har vi defineret en politik, der gør det muligt *for segmentet Forskning* kun at kommunikere med *HR* og *produktion*. |

    Gentag dette trin for hver politik, du vil definere for at tillade, at bestemte segmenter kun kan kommunikere med bestemte andre bestemte segmenter.

2. Fortsæt til en af følgende handlinger:

   - (Hvis det er nødvendigt) [Definere en politik for blokering af kommunikation mellem segmenter](#scenario-1-block-communications-between-segments) 
   - (Når alle dine politikker er defineret) [Anvend politikker for informationsbarrierer](#step-4-apply-information-barrier-policies)

## <a name="step-4-apply-information-barrier-policies"></a>Trin 4: Anvend politikker for informationsbarrierer

Politikker for informationsbarrierer træder ikke i kraft, før du sætter dem til aktiv status og derefter anvender politikkerne.

1. Brug **cmdlet'en Get-InformationBarrierPolicy** for at få vist en liste over de politikker, der er defineret. Bemærk guid-status og identitet for hver politik.

    Syntaks: `Get-InformationBarrierPolicy`

2. Hvis du vil angive en politik til aktiv status, skal du bruge **Cmdlet'en Set-InformationBarrierPolicy med en Identity-parameter** og parameteren **Stat** angivet til **Aktiv**. 

    | Syntaks | Eksempel |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> I dette eksempel har vi indstillet en politik for informationsbarrierer, der har GUID *43c37853-ea10-4b90-a23d-ab8c93772471* til aktiv status. |

    Gentag dette trin efter behov for hver politik.

3. Når du er færdig med at indstille dine politikker for informationsbarrierer til aktiv status, skal du bruge **Start-InformationBarrierPoliciesApplication-cmdlet'en** i Security & Compliance Center.

    Syntaks: `Start-InformationBarrierPoliciesApplication`

    Når du har kørt `Start-InformationBarrierPoliciesApplication`, kan det tage 30 minutter, før systemet begynder at anvende politikkerne. Systemet anvender politikker, som er bruger efter bruger. Systemet behandler ca. 5.000 brugerkonti pr. time.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>Få vist status for brugerkonti, segmenter, politikker eller politikprogram

Med PowerShell kan du få vist status for brugerkonti, segmenter, politikker og politikprogram, som angivet i følgende tabel.

| Sådan får du vist disse oplysninger | Skal du gøre dette |
|:---------------|:----------|
| Brugerkonti | Brug **cmdlet'en Get-InformationBarrierRecipientStatus** med identitetsparametre. <p> Syntaks: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Du kan bruge en hvilken som helst værdi, der entydigt identificerer hver enkelt bruger, f.eks. navn, alias, entydigt navn, ved navn, mailadresse eller GUID. <p> Eksempel: `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> I dette eksempel henviser vi til to brugerkonti i Office 365: *Meganb* for *Megan* og *alexw* for *Alex*. <p> (Du kan også bruge denne cmdlet til en enkelt bruger: `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> Denne cmdlet returnerer oplysninger om brugere, f.eks. attributværdier og eventuelle politikker for informationsbarrierer, der anvendes.|
| Segmenter | Brug **cmdlet'en Get-OrganizationSegment** .<p> Syntaks: `Get-OrganizationSegment` <p> Denne cmdlet viser en liste over alle segmenter, der er defineret for organisationen. |
| Politikker for informationsbarrierer | Brug **cmdlet'en Get-InformationBarrierPolicy** . <p> Syntaks: `Get-InformationBarrierPolicy` <p> Denne cmdlet viser en liste over definerede informationsbarrierepolitikker og deres status. |
| Den nyeste program til informationsbarrierepolitik | Brug **cmdlet'en Get-InformationBarrierPoliciesApplicationStatus** . <p> Syntaks: `Get-InformationBarrierPoliciesApplicationStatus`<p> Denne cmdlet viser oplysninger om, hvorvidt politikprogrammet er afsluttet, mislykket eller er i gang. |
| Alle programmer til informationsbarrierepolitik|Brug `Get-InformationBarrierPoliciesApplicationStatus -All`<p> Denne cmdlet viser oplysninger om, hvorvidt politikprogrammet er afsluttet, mislykket eller er i gang.|

<!-- IN the " The most recent information barrier policy application, add link to troubleshooting topic -->

### <a name="what-if-i-need-to-remove-or-change-policies"></a>Hvad gør jeg, hvis jeg har brug for at fjerne eller ændre politikker?

Der findes ressourcer, som kan hjælpe dig med at administrere politikker for informationsbarrierer.

- Hvis noget går galt med informationsbarrierer, skal du se [Fejlfinding af informationsbarrierer](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).
- Hvis du vil stoppe politikker i at blive anvendt, skal [du se Stop et politikprogram](information-barriers-edit-segments-policies.md#stop-a-policy-application).
- Hvis du vil fjerne en politik for informationsbarrierer, [skal du se Fjern en politik](information-barriers-edit-segments-policies.md#remove-a-policy).
- Hvis du vil foretage ændringer i segmenter eller politikker, skal [du se Rediger (eller fjern) oplysninger om barrierepolitikker](information-barriers-edit-segments-policies.md).

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>Trin 5: Konfiguration af informationsbarrierer på SharePoint og OneDrive

Hvis du konfigurerer informationsbarrierer for SharePoint og OneDrive, skal du aktivere informationsbarrierer for disse tjenester. Du skal også aktivere informationsbarrierer for disse tjenester, hvis du konfigurerer informationsbarrierer for Microsoft Teams. Når der Microsoft Teams oprettet et team, oprettes der automatisk SharePoint et websted, som er tilknyttet Microsoft Teams for filoplevelsen. Politikker for informationsbarrierer bliver ikke imødekommet på dette SharePoint websted og filer som standard.

For at aktivere informationsbarrierer SharePoint og OneDrive, skal du følge vejledningen og trinnene i artiklen [Brug informationsbarrierer SharePoint](/sharepoint/information-barriers) artikel.

## <a name="step-6-information-barriers-modes"></a>Trin 6: Tilstande for informationsbarrierer

Tilstande kan være med til at styrke adgang, deling og medlemskab af Microsoft 365 ressource baseret på ressourcens IB-tilstand. Tilstande understøttes på Microsoft 365 grupper, Microsoft Teams, OneDrive og SharePoint websteder og aktiveres automatisk i din nye eller eksisterende IB-konfiguration.

Følgende IB-tilstande understøttes på Microsoft 365 ressourcer:

| **Tilstand** | **Beskrivelse** | **Eksempel** |
|:-----|:------------|:--------|
| **Åbn** | Der er ikke nogen IB-politikker eller -segmenter, der er knyttet Microsoft 365 ressourcen. Alle kan blive inviteret til at være medlem af ressourcen. | Et teamwebsted, der er oprettet til skovtursbegivenhed for organisationen. |
| **Ejer Modereret (eksempel)** | IB-politikken for den Microsoft 365 ressource bestemmes af ressourceejerens IB-politik. Ressourceejerne kan invitere alle brugere til ressourcen baseret på deres IB-politikker. Denne tilstand er nyttig, når virksomheden vil tillade samarbejde mellem brugere i inkompatible segmenter, der modererer af ejeren. Kun ressourceejeren kan tilføje nye medlemmer pr. deres IB-politik. | THE VP for the HR ønsker at samarbejde med VP'er for Salg og Research. Et nyt SharePoint websted, der er indstillet med IB-tilstand Ejer *Modereret*, for at føje brugere af både salgs- og forskningssegmenter til det samme websted. Det er ejerens ansvar at sikre, at der føjes relevante medlemmer til ressourcen. |
| **Implicit** | IB-politikken eller segmenter i Microsoft 365 nedarves fra ressourcemedlemmers IB-politik. Ejeren kan tilføje medlemmer, så længe de er kompatible med de eksisterende medlemmer af ressourcen. Dette er standard IB-tilstand for Microsoft Teams. | Brugeren af salgssegmentet opretter et Microsoft Teams team for at samarbejde med andre kompatible segmenter i organisationen. |
| **Eksplicit** | IB-politikken for ressourcen Microsoft 365 pr. de segmenter, der er knyttet til ressourcen. Ressourceejeren eller SharePoint har mulighed for at administrere segmenter på ressourcen.  | Et websted, der kun er oprettet for medlemmer af salgssegmentet til at samarbejde ved at knytte salgssegmentet til webstedet.   |

Du kan finde flere oplysninger om tilstandene for informationsbarrierer, og hvordan de er konfigureret på tværs af tjenester, i følgende artikler:

- [Informationsbarrieretilstande og Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [Informationsbarrieretilstande og OneDrive](/onedrive/information-barriers)
- [Informationsbarrieretilstande og SharePoint](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>Eksempelscenarie: Contosos afdelinger, segmenter og politikker

Hvis du vil se, hvordan en organisation kan gå i gang med at definere segmenter og politikker, skal du overveje følgende eksempelscenarie.

### <a name="contosos-departments-and-plan"></a>Contosos afdelinger og plan

Contoso har fem afdelinger: HR, salg, marketing, forskning og produktion. For at overholde branchereglerne skal personer i nogle afdelinger ikke kommunikere med andre afdelinger, sådan som det er angivet i følgende tabel:

| Segment | Kan tale med | Kan ikke tale med |
|:----------|:--------------|:-----------------|
| HR | Alle | (ingen begrænsninger) |
| Salg | HR, marketing, produktion | Opslag |
| Marketing | Alle | (ingen begrænsninger) |
| Opslag | HR, marketing, produktion | Salg |
| Produktion | HR, Marketing | Alle andre end HR eller marketing |

For denne struktur indeholder Contosos plan tre politikker for informationsbarrierer:

1. En politik, der er udviklet til at forhindre salg i at kommunikere med Research (og en anden politik for at forhindre, at Research kommunikerer med Salg).

2. En politik, der er udviklet med henblik på kun at tillade produktion at kommunikere med HR og marketing.

I dette scenarie er det ikke nødvendigt at definere politikker for HR eller marketing.

### <a name="contosos-defined-segments"></a>Contosos definerede segmenter

Contoso bruger attributten Afdeling i Azure Active Directory til at definere segmenter på følgende måde:

| Afdeling | Segmentdefinition |
|:-------------|:---------------------|
| HR | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| Salg | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| Marketing | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| Opslag | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| Produktion | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

Når segmenter er defineret, fortsætter Contoso med at definere politikker.

### <a name="contosos-information-barrier-policies"></a>Contosos politikker for informationsbarrierer

Contoso definerer tre politikker, som beskrevet i følgende tabel:

| Politik | Politikdefinition |
|:---------|:--------------------|
| **Politik 1: Undgå, at salg kommunikerer med Research** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> I dette eksempel kaldes informationsbarrierepolitikken *Sales-Research*. Når denne politik er aktiv og anvendt, kan det hjælpe med at forhindre brugere, der er i salgssegmentet, i at kommunikere med brugere i Research-segmentet. Denne politik er en envejspolitik; det forhindrer ikke Research i at kommunikere med Salg. Til det er politik 2 påkrævet. |
| **Politik 2: Undgå, at Research kommunikerer med Salg** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> I dette eksempel kaldes informationsbarrierepolitikken *Research-Sales*. Når denne politik er aktiv og anvendt, kan det hjælpe med at forhindre brugere, der er i researchsegmentet, i at kommunikere med brugere i salgssegmentet. |
| **Politik 3: Tillad, at produktion kun kommunikerer med HR og marketing** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> I dette tilfælde kaldes politikken for informationsbarrierer *Produktion-HRMarketing*. Når denne politik er aktiv og anvendt, kan produktion kun kommunikere med HR og marketing. HR og marketing er ikke begrænset til kommunikation med andre segmenter. |

Når segmenter og politikker er defineret, anvender Contoso politikkerne ved at køre **cmdlet'en Start-InformationBarrierPoliciesApplication** .

Når cmdlet'en er færdig, overholder Contoso juridiske krav og branchekrav.

## <a name="resources"></a>Ressourcer

- [Få et overblik over informationsbarrierer](information-barriers.md)
- [Få mere at vide om informationsbarrierer i Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Få mere at vide om informationsbarrierer SharePoint Online](/sharepoint/information-barriers)
- [Få mere at vide om informationsbarrierer OneDrive](/onedrive/information-barriers)
