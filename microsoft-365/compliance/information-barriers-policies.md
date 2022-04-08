---
title: Kom i gang med informationsbarrierer
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
ms.openlocfilehash: fb6de09c0c020631f42d8f2f09cb236affb94417
ms.sourcegitcommit: 1c5f9d17a8b095cd88b23f4874539adc3ae021de
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/08/2022
ms.locfileid: "64713531"
---
# <a name="get-started-with-information-barriers"></a>Kom i gang med informationsbarrierer

Med informationsbarrierer kan du definere politikker, der er designet til at forhindre, at visse segmenter af brugere kommunikerer med hinanden, eller tillade, at bestemte segmenter kun kommunikerer med visse andre segmenter. Politikker for informationsbarrierer kan hjælpe din organisation med at opretholde overholdelse af relevante branchestandarder og -regler og undgå potentielle interessekonflikter. Du kan finde flere oplysninger under [Få mere at vide om informationsbarrierer](information-barriers.md).

I denne artikel beskrives det, hvordan du konfigurerer politikker for informationsbarrierer. Der er flere trin involveret, så sørg for at gennemse hele processen, før du begynder at konfigurere politikker for informationsbarrierer.

> [!TIP]
> Denne artikel indeholder et [eksempelscenarie](#example-scenario-contosos-departments-segments-and-policies) , der kan hjælpe dig med at planlægge og definere dine politikker for informationsbarrierer.

## <a name="concepts"></a>Begreber

Når du definerer politikker for informationsbarrierer, arbejder du med brugerkontoattributter, segmenter, 'blok' og/eller 'tillad'-politikker og politikanvendelse.

- Brugerkontoattributter defineres i Azure Active Directory (eller Exchange Online). Disse attributter kan omfatte afdeling, stilling, placering, teamnavn og andre oplysninger om jobprofiler.
- Segmenter er sæt af brugere, der er defineret i Microsoft 365 Overholdelsescenter ved hjælp af en valgt **brugerkontoattribut**. Se [listen over understøttede attributter](information-barriers-attributes.md).
- Politikker for informationsbarrierer bestemmer kommunikationsgrænser eller -begrænsninger. Når du definerer politikker for informationsbarrierer, vælger du mellem to typer politikker:
  - *Blokpolitikker* forhindrer, at ét segment kommunikerer med et andet segment.
  - *Tillad* politikker, at ét segment kun kommunikerer med visse andre segmenter.
- Politikanvendelse udføres, når alle politikker for informationsbarrierer er defineret, og du er klar til at anvende dem i din organisation.

## <a name="configuration-at-a-glance"></a>Konfiguration med et hurtigt øjekast

| **Trin** | **Hvad er involveret** |
|:------|:----------------|
| **Trin 1**: [Sørg for, at forudsætninger er opfyldt](#step-1-make-sure-prerequisites-are-met) | – Kontrollér, at du har de [nødvendige licenser og tilladelser](information-barriers.md#required-licenses-and-permissions)<br/>– Kontrollér, at mappen indeholder data til segmentering af brugere<br/>- Aktivér [søgning efter navn for Microsoft Teams](/microsoftteams/teams-scoped-directory-search)<br/>- Sørg for, at logføring af overvågning er slået til<br/>- Sørg for, at der ikke er nogen Exchange politikker for adressekartoteket<br/>– Brug PowerShell (eksempler er angivet)<br/>– Angiv administratorsamtykke for Microsoft Teams (trinnene er inkluderet) |
| **Trin 2**: [Segmentér brugere i din organisation](#step-2-segment-users-in-your-organization) | – Fastlæg, hvilke politikker der er behov for<br/>– Opret en liste over segmenter, der skal defineres<br/>- Identificer, hvilke attributter der skal bruges<br/>– Definer segmenter med hensyn til politikfiltre |
| **Trin 3**: [Definer politikker for informationsbarrierer](#step-3-define-information-barrier-policies) | – Definer dine politikker (gælder ikke endnu)<br/>- Vælg mellem to typer (blok eller tillad) |
| **Trin 4**: [Anvend politikker for informationsbarrierer](#step-4-apply-information-barrier-policies) | – Angiv politikker til aktiv status<br/>- Kør politikprogrammet<br/>- Få vist politikstatus |
| **Trin 5**: [Konfiguration af informationsbarrierer på SharePoint og OneDrive (valgfrit)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | - Konfigurer informationsbarrierer for SharePoint og OneDrive |
| **Trin 6**: [Informationsbarrierer (valgfrit)](#step-6-information-barriers-modes) | - Opdatere informationsbarrieretilstande, hvis det er relevant |

## <a name="step-1-make-sure-prerequisites-are-met"></a>Trin 1: Sørg for, at forudsætninger er opfyldt

Ud over de [påkrævede licenser og tilladelser](information-barriers.md#required-licenses-and-permissions) skal du sørge for, at følgende krav er opfyldt, før du konfigurerer informationsbarrierer:

- **Mappedata**: Sørg for, at organisationens struktur afspejles i katalogdata. Hvis du vil udføre denne handling, skal du sørge for, at brugerkontoattributter, f.eks. gruppemedlemskab, afdelingsnavn osv. er udfyldt korrekt i Azure Active Directory (eller Exchange Online). Du kan få mere at vide i følgende ressourcer:
  - [Attributter for politikker for informationsbarrierer](information-barriers-attributes.md)
  - [Tilføj eller opdater en brugers profiloplysninger ved hjælp af Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [Konfigurer egenskaber for brugerkonto med Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **Områdebaseret katalogsøgning**: Før du definerer organisationens første politik for informationsbarrierer, skal du [aktivere områdebaseret katalogsøgning i Microsoft Teams](/MicrosoftTeams/teams-scoped-directory-search). Vent mindst 24 timer efter aktivering af områdebaseret katalogsøgning, før du konfigurerer eller definerer politikker for informationsbarrierer.

- **Exchange Online licenser**: Politikker for informationsbarrierer fungerer kun, hvis målbrugerne har fået tildelt en Exchange Online licens.

- **Kontrollér, at overvågningslogføring er aktiveret**: Hvis du vil slå status for et politikprogram op, skal logføring af overvågning være slået til. Overvågning er som standard aktiveret for Microsoft 365 organisationer. Nogle organisationer kan have deaktiveret overvågning af bestemte årsager. Hvis overvågning er deaktiveret for din organisation, kan det skyldes, at en anden administrator har deaktiveret den. Vi anbefaler, at du bekræfter, at det er OK at aktivere overvågning igen, når du fuldfører dette trin. Du kan finde flere oplysninger under [Slå søgning i overvågningslog til eller fra](turn-audit-log-search-on-or-off.md).

- **Ingen politikker for adressekartoteker**: Før du definerer og anvender politikker for informationsbarrierer, skal du sørge for, at der ikke er nogen Exchange politikker for adressekartoteket. Informationsbarrierer er baseret på politikker for adressekartoteker, men de to typer politikker er ikke kompatible. Hvis du har sådanne politikker, skal du først [fjerne politikkerne for adressekartoteket](/exchange/address-books/address-book-policies/remove-an-address-book-policy) . Når politikker for informationsbarrierer er aktiveret, og du har aktiveret et hierarkisk adressekartotek, kan alle brugere, **_der ikke er inkluderet_** i et informationsbarrieresegment, se det [hierarkiske adressekartotek](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) i Exchange online.

- **Administrer brug af PowerShell**: I øjeblikket defineres og administreres politikker for informationsbarrierer i Security & Compliance Center PowerShell. Selvom der er angivet flere eksempler i denne artikel, skal du have kendskab til PowerShell-cmdlet'er og -parametre. Du skal også bruge Azure Active Directory PowerShell-modulet.
  - [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell)
  - [Installér Azure Active Directory PowerShell til Graph](/powershell/azure/active-directory/install-adv2)

- **Administratorsamtykke for informationsbarrierer i Microsoft Teams**: Når dine IB-politikker er på plads, kan de fjerne brugere med ikke-IB-overholdelse fra Grupper (dvs. Teams kanaler, der er baseret på grupper). Denne konfiguration hjælper med at sikre, at din organisation fortsat overholder politikker og regler. Brug følgende procedure til at gøre det muligt for politikker for informationsbarrierer at fungere som forventet i Microsoft Teams.

   1. Forudsætning: [Installér Azure Active Directory PowerShell til Graph](/powershell/azure/active-directory/install-adv2).

   1. Kør følgende PowerShell-cmdlet'er:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   1. Når du bliver bedt om det, skal du logge på med din arbejds- eller skolekonto for Office 365.

   1. Gennemse oplysningerne i dialogboksen **Tilladelser,** og vælg derefter **Acceptér**. De tilladelser, der anmodes om af appen, er angivet nedenfor.

      > [!div class="mx-imgBorder"]
      > ![Billede.](https://user-images.githubusercontent.com/8932063/107690955-b1772300-6c5f-11eb-9527-4235de860b27.png)

Når alle forudsætningerne er opfyldt, skal du gå videre til næste trin.

> [!TIP]
> Som en hjælp til at forberede din plan er der inkluderet et eksempelscenarie i denne artikel. [Se Contosos afdelinger, segmenter og politikker](#example-scenario-contosos-departments-segments-and-policies).

## <a name="step-2-segment-users-in-your-organization"></a>Trin 2: Segmentér brugere i din organisation

I løbet af dette trin bestemmer du, hvilke politikker for informationsbarrierer der er behov for, opretter en liste over segmenter, der skal defineres, og definerer derefter dine segmenter.

### <a name="determine-what-policies-are-needed"></a>Find ud af, hvilke politikker der er brug for

I betragtning af juridiske og brancheregler, hvem er de grupper i organisationen, der har brug for politikker om informationsbarrierer? Opret en liste. Er der nogen grupper, som bør forhindres i at kommunikere med en anden gruppe? Er der nogen grupper, der kun må kommunikere med en eller to andre grupper? Tænk på de politikker, du har brug for, som tilhører en af to grupper:

- "Bloker" politikker forhindrer en gruppe i at kommunikere med en anden gruppe.
- "Tillad"-politikker gør det muligt for en gruppe kun at kommunikere med visse andre, bestemte grupper.

Når du har din første liste over grupper og politikker, skal du fortsætte med at identificere de segmenter, du har brug for.

### <a name="identify-segments"></a>Identificer segmenter

Ud over din indledende liste over politikker kan du oprette en liste over segmenter for din organisation. Brugere, der skal medtages i politikker for informationsbarrierer, bør tilhøre et segment. Planlæg dine segmenter omhyggeligt, da en bruger kun kan være i ét segment. Der kan kun anvendes én politik for informationsbarrierer for hvert segment.

> [!IMPORTANT]
> En bruger kan kun være i ét segment.

Find ud af, hvilke attributter i organisationens katalogdata du skal bruge til at definere segmenter. Du kan bruge *Afdeling*, *MemberOf* eller en af de understøttede attributter. Sørg for, at du har værdier i den attribut, du vælger for brugere. [Se listen over understøttede attributter for informationsbarrierer](information-barriers-attributes.md).

> [!IMPORTANT]
> **Før du fortsætter til næste afsnit, skal du sørge for, at dine katalogdata indeholder værdier for attributter, som du kan bruge til at definere segmenter**. Hvis dine katalogdata ikke har værdier for de attributter, du vil bruge, skal brugerkontiene opdateres, så de indeholder disse oplysninger, før du fortsætter med informationsbarrierer. Du kan få hjælp til dette i følgende ressourcer:<br/>- [Konfigurer egenskaber for brugerkonto med Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [Tilføj eller opdater en brugers profiloplysninger ved hjælp af Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-powershell"></a>Definer segmenter ved hjælp af PowerShell

Definition af segmenter påvirker ikke brugerne. Det sætter blot fasen for, hvordan politikker for informationsbarrierer skal defineres og derefter anvendes.

1. Brug **New-OrganizationSegment-cmdlet'en** med parameteren **UserGroupFilter** , der svarer til den [attribut,](information-barriers-attributes.md) du vil bruge.

    | Syntaks | Eksempel |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>I dette eksempel defineres et segment med navnet *HR* ved hjælp af *HR*, som er en værdi i attributten *Afdeling* . **-eq-delen** af cmdlet'en refererer til "lig med". (Alternativt kan du bruge **-ne** til at betyde "ikke lig med". Se [Brug af "er lig med" og "ikke lig med" i segmentdefinitioner](#using-equals-and-not-equals-in-segment-definitions). |

    Når du har kørt hver cmdlet, får du vist en liste over detaljer om det nye segment. Detaljer omfatter segmentets type, hvem der oprettede eller senest ændrede det osv. 

2. Gentag denne proces for hvert segment, du vil definere.

    > [!IMPORTANT]
    > **Sørg for, at dine segmenter ikke overlapper hinanden**. Hver bruger, der vil blive berørt af informationsbarrierer, bør tilhøre ét (og kun ét) segment. Ingen bruger må tilhøre to eller flere segmenter. (Se [eksempel: Contosos definerede segmenter](#contosos-defined-segments) i denne artikel).

Når du har defineret dine segmenter, skal du fortsætte med at [definere politikker for informationsbarrierer](#step-3-define-information-barrier-policies).

### <a name="using-equals-and-not-equals-in-segment-definitions"></a>Brug af "er lig med" og "ikke lig med" i segmentdefinitioner

I følgende eksempel definerer vi et segment, så "Afdeling er lig med HR". 

| Eksempel | Bemærk |
|:----------|:-------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` | Bemærk, at segmentdefinitionen i dette eksempel indeholder parameteren "er lig med", der er angivet som **-eq**. |

Du kan også definere segmenter ved hjælp af parameteren "ikke lig med", der kaldes **-ne**, som vist i følgende tabel:

| Syntaks | Eksempel |
|:---------|:----------|
| `New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"` | I dette eksempel har vi defineret et segment med navnet *NotSales* , der omfatter alle, der ikke er i *Sales*. Den **-ne-del** af cmdlet'en refererer til "ikke lig med". |

Ud over at definere segmenter, der bruger parametrene "er lig med" eller "ikke lig med", kan du definere et segment ved hjælp af parametrene "er lig med" og "ikke lig med". Du kan også definere komplekse gruppefiltre ved hjælp af logiske *AND* - og *OR-operatorer* .

| Syntaks | Eksempel |
|:---------|:----------|
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | I dette eksempel definerede vi et segment kaldet *LocalFTE* , der omfatter personer, der er placeret lokalt, og hvis stillinger ikke er angivet som *midlertidige*. |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| I dette eksempel definerede vi et segment med navnet *Segment1* , der omfatter personer, der er medlemmer af group1@contoso.com og ikke medlemmer af group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | I dette eksempel definerede vi et segment kaldet *Segment2* , der omfatter personer, der er medlemmer af group2@contoso.com og ikke medlemmer af group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| I dette eksempel definerede vi et segment kaldet *Segment1and2* , der omfatter personer, der er medlemmer af group1@contoso.com og group2@contoso.com og ikke medlemmer af group3@contoso.com. |

> [!TIP]
> Hvis det er muligt, kan du bruge segmentdefinitioner, der omfatter "-eq" eller "-ne". Prøv ikke at definere komplekse segmentdefinitioner.

## <a name="step-3-define-information-barrier-policies"></a>Trin 3: Definer politikker for informationsbarrierer

Find ud af, om du har brug for at forhindre kommunikation mellem bestemte segmenter eller begrænse kommunikationen til bestemte segmenter. Ideelt set skal du bruge det mindste antal politikker til at sikre, at din organisation overholder juridiske krav og branchekrav.

Med din liste over brugersegmenter og de politikker for informationsbarrierer, du vil definere, skal du vælge et scenarie og derefter følge trinnene.

- [Scenarie 1: Bloker kommunikation mellem segmenter](#scenario-1-block-communications-between-segments)
- [Scenarie 2: Tillad, at et segment kun kommunikerer med ét andet segment](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **Sørg for, at når du definerer politikker, kan du ikke tildele mere end én politik til et segment**. Hvis du f.eks. definerer én politik for et segment med navnet *Salg*, skal du ikke definere en yderligere politik for *Salg*.<p> Når du definerer politikker for informationsbarrierer, skal du desuden sørge for at angive disse politikker til inaktiv status, indtil du er klar til at anvende dem. Definition (eller redigering) af politikker påvirker ikke brugerne, før disse politikker er angivet til aktiv status og derefter anvendt.

(Se [eksempel: Contosos politikker for informationsbarrierer](#contosos-information-barrier-policies) i denne artikel).

### <a name="scenario-1-block-communications-between-segments"></a>Scenarie 1: Bloker kommunikation mellem segmenter

Når du vil blokere segmenter fra at kommunikere med hinanden, definerer du to politikker: én for hver retning. Hver politik blokerer kun kommunikation på én måde.

Lad os f.eks. antage, at du vil blokere kommunikation mellem Segment A og Segment B. I dette tilfælde skal du definere én politik, der forhindrer Segment A i at kommunikere med Segment B, og derefter definere en anden politik for at forhindre, at Segment B kommunikerer med Segment A.

1. Hvis du vil definere din første blokeringspolitik, skal du bruge **New-InformationBarrierPolicy-cmdlet'en** med parameteren **SegmentsBlocked** .

    | Syntaks | Eksempel |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> I dette eksempel har vi defineret en politik med navnet *Sales-Research* for et segment med navnet *Sales*. Når denne politik er aktiv og anvendt, forhindrer den personer i *Salg* i at kommunikere med personer i et segment med navnet *Opslag*. |

2. Hvis du vil definere det andet blokeringssegment, skal du bruge **New-InformationBarrierPolicy-cmdlet'en** med parameteren **SegmentsBlocked** igen, denne gang med segmenterne tilbageført.

    | Eksempel | Bemærk |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | I dette eksempel definerede vi en politik med navnet *Research-Sales* for at forhindre *, at Research* kommunikerer med *Sales*. |

3. Fortsæt til en af følgende handlinger:

   - (Hvis det er nødvendigt) [Definer en politik for at tillade, at et segment kun kommunikerer med ét andet segment](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (Når alle dine politikker er defineret) [Anvend politikker for informationsbarrierer](#step-4-apply-information-barrier-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>Scenarie 2: Tillad, at et segment kun kommunikerer med ét andet segment

1. Hvis du vil tillade, at ét segment kun kommunikerer med ét andet segment, skal du bruge cmdlet'en **New-InformationBarrierPolicy** med parameteren **SegmentsAllowed** .

    | Syntaks | Eksempel |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> I dette eksempel definerede vi en politik med navnet *Manufacturing-HR* for et segment med navnet *Manufacturing*. Når denne politik er aktiv og anvendt, giver den kun personer i *Produktion* mulighed for at kommunikere med personer i et segment med navnet *HR*. (I dette tilfælde kan *Produktion* ikke kommunikere med brugere, der ikke er en del af *HR*). |

    **Hvis det er nødvendigt, kan du angive flere segmenter med denne cmdlet, som vist i følgende eksempel.**

    | Syntaks | Eksempel |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> I dette eksempel har vi defineret en politik, der gør det muligt for segmentet *Forskning* kun at kommunikere med *HR* og *Produktion*. |

    Gentag dette trin for hver politik, du vil definere for at tillade, at bestemte segmenter kun kommunikerer med visse andre specifikke segmenter.

2. Fortsæt til en af følgende handlinger:

   - (Hvis det er nødvendigt) [Definer en politik til blokering af kommunikation mellem segmenter](#scenario-1-block-communications-between-segments) 
   - (Når alle dine politikker er defineret) [Anvend politikker for informationsbarrierer](#step-4-apply-information-barrier-policies)

## <a name="step-4-apply-information-barrier-policies"></a>Trin 4: Anvend politikker for informationsbarrierer

Politikker for informationsbarrierer er først i kraft, når du angiver dem til aktiv status og derefter anvender politikkerne.

1. Brug **cmdlet'en Get-InformationBarrierPolicy** til at få vist en liste over de politikker, der er defineret. Bemærk status og id (GUID) for hver politik.

    Syntaks: `Get-InformationBarrierPolicy`

2. Hvis du vil angive en politik til aktiv status, skal du bruge **Set-InformationBarrierPolicy-cmdlet'en** med parameteren **Identity** og parameteren **State** angivet til **Active**. 

    | Syntaks | Eksempel |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> I dette eksempel angiver vi en politik for informationsbarrierer, der har GUID *43c37853-ea10-4b90-a23d-ab8c93772471* til aktiv status. |

    Gentag dette trin efter behov for hver politik.

3. Når du er færdig med at angive dine politikker for informationsbarrierer til aktiv status, skal du bruge cmdlet'en **Start-InformationBarrierPoliciesApplication** i Security & Compliance Center.

    Syntaks: `Start-InformationBarrierPoliciesApplication`

    Når du har kørt `Start-InformationBarrierPoliciesApplication`, kan systemet begynde at anvende politikkerne i 30 minutter. Systemet anvender politikker, som brugeren anvender. Systemet behandler ca. 5.000 brugerkonti pr. time.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>Få vist status for brugerkonti, segmenter, politikker eller politikprogram

Med PowerShell kan du få vist status for brugerkonti, segmenter, politikker og politikprogram som angivet i følgende tabel.

| Sådan får du vist disse oplysninger | Udfør denne handling |
|:---------------|:----------|
| Brugerkonti | Brug cmdlet'en **Get-InformationBarrierRecipientStatus** med identitetsparametre. <p> Syntaks: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Du kan bruge en hvilken som helst værdi, der entydigt identificerer hver bruger, f.eks. navn, alias, entydigt navn, vedtaget domænenavn, mailadresse eller GUID. <p> Eksempel: `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> I dette eksempel henviser vi til to brugerkonti i Office 365: *meganb* for *Megan* og *alexw* for *Alex*. <p> (Du kan også bruge denne cmdlet til en enkelt bruger: `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> Denne cmdlet returnerer oplysninger om brugere, f.eks. attributværdier og eventuelle politikker for informationsbarrierer, der anvendes.|
| Segmenter | Brug cmdlet'en **Get-OrganizationSegment** .<p> Syntaks: `Get-OrganizationSegment` <p> Denne cmdlet viser en liste over alle de segmenter, der er defineret for din organisation. |
| Politikker for informationsbarrierer | Brug cmdlet'en **Get-InformationBarrierPolicy** . <p> Syntaks: `Get-InformationBarrierPolicy` <p> Denne cmdlet viser en liste over definerede politikker for informationsbarrierer og deres status. |
| Den seneste anvendelse af informationsbarrierepolitik | Brug cmdlet'en **Get-InformationBarrierPoliciesApplicationStatus** . <p> Syntaks: `Get-InformationBarrierPoliciesApplicationStatus`<p> Denne cmdlet viser oplysninger om, hvorvidt politikprogrammet er fuldført, mislykket eller er i gang. |
| Alle applikationer til barrierepolitik for information|Bruge `Get-InformationBarrierPoliciesApplicationStatus -All`<p> Denne cmdlet viser oplysninger om, hvorvidt politikprogrammet er fuldført, mislykket eller er i gang.|

<!-- IN the " The most recent information barrier policy application, add link to troubleshooting topic -->

### <a name="what-if-i-need-to-remove-or-change-policies"></a>Hvad gør jeg, hvis jeg har brug for at fjerne eller ændre politikker?

Der er ressourcer til rådighed, som kan hjælpe dig med at administrere dine politikker for informationsbarrierer.

- Hvis noget går galt med informationsbarrierer, kan [du se Fejlfinding af informationsbarrierer](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).
- Hvis du vil forhindre, at politikker anvendes, skal du se [Stop et politikprogram](information-barriers-edit-segments-policies.md#stop-a-policy-application).
- Hvis du vil fjerne en politik for informationsbarrierer, skal du se [Fjern en politik](information-barriers-edit-segments-policies.md#remove-a-policy).
- Hvis du vil foretage ændringer af segmenter eller politikker, skal du se [Rediger (eller fjern) politikker for informationsbarrierer](information-barriers-edit-segments-policies.md).

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>Trin 5: Konfiguration af informationsbarrierer for SharePoint og OneDrive

Hvis du konfigurerer informationsbarrierer for SharePoint og OneDrive, skal du aktivere informationsbarrierer for disse tjenester. Du skal også aktivere informationsbarrierer for disse tjenester, hvis du konfigurerer informationsbarrierer for Microsoft Teams. Når der oprettes et Microsoft Teams team, oprettes der automatisk et SharePoint websted, som er knyttet til Microsoft Teams til filoplevelsen. Politikker for informationsbarrierer anvendes ikke som standard på dette SharePoint websted og filer.

Hvis du vil aktivere informationsbarrierer i SharePoint og OneDrive, skal du følge vejledningen og trinnene i artiklen [Brug informationsbarrierer med SharePoint](/sharepoint/information-barriers).

## <a name="step-6-information-barriers-modes"></a>Trin 6: Informationsbarrierer

Tilstande kan hjælpe med at styrke adgang, deling og medlemskab af en Microsoft 365 ressource baseret på ressourcens IB-tilstand. Tilstande understøttes på Microsoft 365-grupper, Microsoft Teams, OneDrive og SharePoint websteder og aktiveres automatisk i din nye eller eksisterende IB-konfiguration.

Følgende IB-tilstande understøttes i Microsoft 365 ressourcer:

| **Tilstand** | **Beskrivelse** | **Eksempel** |
|:-----|:------------|:--------|
| **Åbne** | Der er ikke knyttet nogen IB-politikker eller -segmenter til den Microsoft 365 ressource. Alle kan inviteres til at være medlem af ressourcen. | Et teamwebsted, der er oprettet til picnicbegivenhed for din organisation. |
| **Ejer ændret (prøveversion)** | IB-politikken for den Microsoft 365 ressource bestemmes ud fra ressourceejerens IB-politik. Ressourceejerne kan invitere alle brugere til ressourcen på baggrund af deres IB-politikker. Denne tilstand er nyttig, når din virksomhed ønsker at tillade samarbejde mellem inkompatible segmentbrugere, der er ændret af ejeren. Det er kun ressourceejeren, der kan tilføje nye medlemmer i henhold til deres IB-politik. | HR-vicedirektøren ønsker at samarbejde med VP'erne til salg og forskning. Et nyt SharePoint websted, der er angivet med Ejer i IB-tilstand *Begrænset* for at føje både brugere af salgs- og opslagssegmentet til det samme websted. Det er ejerens ansvar at sikre, at de relevante medlemmer føjes til ressourcen. |
| **Implicit** | IB-politikken eller -segmenterne for den Microsoft 365 ressource nedarves fra ressourcemedlemmernes IB-politik. Ejeren kan tilføje medlemmer, så længe de er kompatible med de eksisterende medlemmer af ressourcen. Dette er standard-IB-tilstanden for Microsoft Teams. | Brugeren af salgssegmentet opretter et Microsoft Teams team til at samarbejde med andre kompatible segmenter i organisationen. |
| **Eksplicit** | IB-politikken for den Microsoft 365 ressource er pr. de segmenter, der er knyttet til ressourcen. Ressourceejeren eller SharePoint-administratoren har mulighed for at administrere segmenterne på ressourcen.  | Et websted, der kun er oprettet for medlemmer af salgssegmentet for at samarbejde ved at knytte segmentet Salg til webstedet.   |

Du kan få flere oplysninger om informationsbarrieretilstande, og hvordan de konfigureres på tværs af tjenester, i følgende artikler:

- [Informationsbarrierer og -Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [Informationsbarrierer og -OneDrive](/onedrive/information-barriers)
- [Informationsbarrierer og -SharePoint](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>Eksempelscenarie: Contosos afdelinger, segmenter og politikker

Hvis du vil se, hvordan en organisation kan nærme sig definere segmenter og politikker, skal du overveje følgende eksempelscenarie.

### <a name="contosos-departments-and-plan"></a>Contosos afdelinger og plan

Contoso har fem afdelinger: HR, Salg, Marketing, Forskning og Produktion. For at overholde brancheregler skal personer i nogle afdelinger ikke kommunikere med andre afdelinger, som vist i følgende tabel:

| Segment | Kan tale med | Kan ikke tale med |
|:----------|:--------------|:-----------------|
| HR | Alle | (ingen begrænsninger) |
| Salg | HR, marketing, produktion | Opslag |
| Marketing | Alle | (ingen begrænsninger) |
| Opslag | HR, marketing, produktion | Salg |
| Fremstilling | HR, Marketing | Alle andre end HR eller Marketing |

For denne struktur omfatter Contosos plan tre politikker for informationsbarrierer:

1. En politik, der er designet til at forhindre Salg i at kommunikere med Research (og en anden politik for at forhindre, at Research kommunikerer med Sales).

2. En politik, der er designet til kun at gøre det muligt for Produktion at kommunikere med HR og Marketing.

I dette scenarie er det ikke nødvendigt at definere politikker for HR eller Marketing.

### <a name="contosos-defined-segments"></a>Contosos definerede segmenter

Contoso bruger attributten Afdeling i Azure Active Directory til at definere segmenter på følgende måde:

| Institut | Segmentdefinition |
|:-------------|:---------------------|
| HR | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| Salg | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| Marketing | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| Opslag | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| Fremstilling | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

Når segmenterne er defineret, fortsætter Contoso med at definere politikker.

### <a name="contosos-information-barrier-policies"></a>Contosos politik for informationsbarrierer

Contoso definerer tre politikker, som beskrevet i følgende tabel:

| Politik | Politikdefinition |
|:---------|:--------------------|
| **Politik 1: Undgå, at salg kommunikerer med opslag** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> I dette eksempel kaldes politikken for informationsbarrierer *Sales-Research*. Når denne politik er aktiv og anvendt, hjælper det med at forhindre brugere, der er i segmentet Salg, i at kommunikere med brugere i segmentet Opslag. Denne politik er en envejspolitik. Det forhindrer ikke Research i at kommunikere med Sales. Til det formål er Politik 2 nødvendig. |
| **Politik 2: Undgå, at opslag kommunikerer med Salg** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> I dette eksempel kaldes politikken for informationsbarrierer *Research-Sales*. Når denne politik er aktiv og anvendt, hjælper det med at forhindre brugere, der er i segmentet Opslag, i at kommunikere med brugere i segmentet Salg. |
| **Politik 3: Tillad, at produktion kun kommunikerer med HR og marketing** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> I dette tilfælde kaldes politikken for *informationsbarrierer Manufacturing-HRMarketing*. Når denne politik er aktiv og anvendt, kan Produktion kun kommunikere med HR og Marketing. HR og marketing er ikke begrænset til at kommunikere med andre segmenter. |

Når segmenter og politikker er defineret, anvender Contoso politikkerne ved at køre cmdlet'en **Start-InformationBarrierPoliciesApplication** .

Når cmdlet'en er færdig, overholder Contoso juridiske krav og branchekrav.

## <a name="resources"></a>Ressourcer

- [Få et overblik over informationsbarrierer](information-barriers.md)
- [Få mere at vide om informationsbarrierer i Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Få mere at vide om informationsbarrierer i SharePoint Online](/sharepoint/information-barriers)
- [Få mere at vide om informationsbarrierer i OneDrive](/onedrive/information-barriers)
