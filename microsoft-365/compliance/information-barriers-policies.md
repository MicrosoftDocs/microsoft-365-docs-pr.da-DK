---
title: Kom i gang med informationsbarrierer
description: Få mere at vide om, hvordan du kommer i gang med informationsbarrierer i Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, informationsbarrierer
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
ms.openlocfilehash: d2f2eb77dd143f82ced98f8fce424cc729e26df7
ms.sourcegitcommit: 221212fff9737e0ea386755deb8fed62ae9c254b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/14/2022
ms.locfileid: "66787798"
---
# <a name="get-started-with-information-barriers"></a>Kom i gang med informationsbarrierer

I denne artikel beskrives det, hvordan du konfigurerer IB-politikker (Information Barriers) i din organisation. Der er flere trin involveret, så sørg for at gennemse hele processen, før du begynder at konfigurere IB-politikker.

Du konfigurerer IB i din organisation ved hjælp af [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) eller ved hjælp af [Office 365 Security and Compliance PowerShell](/powershell/exchange/scc-powershell). For organisationer, der konfigurerer IB for første gang, anbefaler vi, at du bruger løsningen **Informationsbarrierer** på overholdelsesportalen. Hvis du administrerer en eksisterende IB-konfiguration, og du er tryg ved at bruge PowerShell, har du stadig denne mulighed.

Du kan finde flere oplysninger om IB-scenarier og -funktioner under [Få mere at vide om informationsbarrierer](information-barriers.md).

> [!TIP]
> Som en hjælp til at forberede din plan er der inkluderet et [eksempelscenarie](#example-scenario-contosos-departments-segments-and-policies) i denne artikel.

## <a name="required-subscriptions-and-permissions"></a>Påkrævede abonnementer og tilladelser

Før du går i gang med IB, skal du bekræfte dit Microsoft 365-abonnement og eventuelle tilføjelsesprogrammer. Hvis du vil have adgang til og bruge IB, skal din organisation have et af følgende abonnementer eller tilføjelsesprogrammer:

- Microsoft 365 E5/A5-abonnement (betalt version eller prøveversion)
- Office 365 E5/A5/A3/A1-abonnement (betalt version eller prøveversion)
- Avanceret overholdelse i Office 365 tilføjelsesprogram (ikke længere tilgængeligt for nye abonnementer)
- Microsoft 365 E3/A3/A1-abonnement + tilføjelsesprogrammet Microsoft 365 E5/A5 Overholdelse
- Microsoft 365 E3/A3/A1-abonnement + tilføjelsesprogrammet Microsoft 365 E5/A5 Insider Risk Management

Du kan finde flere oplysninger i [Microsoft 365-licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

Hvis du vil [administrere politikker for IB](information-barriers-policies.md), skal du være tildelt en af følgende roller:

- Global Microsoft 365-administrator
- Office 365 global administrator
- Overholdelsesadministrator
- Administration af IB-overholdelse

Hvis du vil vide mere om roller og tilladelser, skal du se [Tilladelser i Office 365 Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

## <a name="configuration-concepts"></a>Konfigurationsbegreber

Når du konfigurerer IB, arbejder du med flere objekter og begreber.

- **Brugerkontoattributter** defineres i Azure Active Directory (eller Exchange Online). Disse attributter kan omfatte afdeling, stilling, placering, teamnavn og andre oplysninger om jobprofiler. Du skal tildele brugere eller grupper til segmenter med disse attributter.
- **Segmenter** er grupper eller brugere, der er defineret i overholdelsesportalen eller ved hjælp af PowerShell, der bruger de valgte gruppe- eller brugerkontoattributter. Se listen over [understøttede IB-attributter](information-barriers-attributes.md) for at få flere oplysninger.
- **IB-politikker** bestemmer kommunikationsgrænser eller -begrænsninger. Når du definerer politikker for IB, vælger du mellem to typer politikker:
  - *Blokpolitikker* forhindrer, at ét segment kommunikerer med et andet segment.
  - *Tillad* politikker, at ét segment kun kommunikerer med visse andre segmenter.

    > [!NOTE]
    > I forbindelse *med tilladte* politikker vil ikke-IB-grupper og brugere ikke være synlige for brugere, der er inkluderet i IB-segmenter og -politikker. Hvis du har brug for, at ikke-IB-grupper og brugere skal være synlige for brugere, der er inkluderet i IB-segmenter og -politikker, skal du bruge *blokpolitikker* .

- **Politikprogrammet** udføres, når alle IB-politikker er defineret, og du er klar til at anvende dem i din organisation.
- **Synlighed for ikke-IB-brugere og -grupper**. Ikke-IB-brugere og -grupper er brugere og grupper, der er udelukket fra IB-segmenter og -politikker. Afhængigt af typen af IB-politikker (blokere eller tillade) vil funktionsmåden for disse brugere og grupper variere i Microsoft Teams, SharePoint, OneDrive og på din globale adresseliste. For brugere, der er defineret i *tillad* politikker, vil ikke-IB-grupper og brugere ikke være synlige for brugere, der er inkluderet i IB-segmenter og -politikker. For brugere, der er defineret i *blokpolitikker* , vil ikke-IB-grupper og brugere være synlige for brugere, der er inkluderet i IB-segmenter og -politikker.
- **Gruppesupport**. Det er i øjeblikket kun moderne grupper, der understøttes i IB, og distributionslister/sikkerhedsgrupper behandles som ikke-IB-grupper.
- **Skjulte/deaktiverede brugerkonti**. For skjulte/deaktiverede konti i din organisation angives parameteren *HiddenFromAddressListEnabled* automatisk til *Sand* , når brugerkontiene skjules eller deaktiveres. I IB-aktiverede organisationer forhindres disse konti i at kommunikere med alle andre brugerkonti. I Microsoft Teams er alle chats, herunder disse konti, låst, eller brugerne fjernes automatisk fra samtaler.

## <a name="configuration-overview"></a>Konfigurationsoversigt

| **Trin** | **Hvad er involveret** |
|:------|:----------------|
| **Trin 1**: [Sørg for, at forudsætninger er opfyldt](#step-1-make-sure-prerequisites-are-met) | – Kontrollér, at du har de påkrævede abonnementer og tilladelser <br/>– Kontrollér, at mappen indeholder data til segmentering af brugere<br/>- Aktivér [søgning efter navn for Microsoft Teams](/microsoftteams/teams-scoped-directory-search)<br/>- Sørg for, at logføring af overvågning er slået til<br/>- Sørg for, at der ikke er nogen politikker for Exchange-adressekartoteket på plads <br/>– Giv administratorsamtykke til Microsoft Teams (trinnene er inkluderet) |
| **Trin 2**: [Segmentér brugere i din organisation](#step-2-segment-users-in-your-organization) | – Fastlæg, hvilke politikker der er behov for<br/>– Opret en liste over segmenter, der skal defineres<br/>- Identificer, hvilke attributter der skal bruges<br/>– Definer segmenter med hensyn til politikfiltre |
| **Trin 3**: [Opret politikker for informationsbarrierer](#step-3-create-ib-policies) | – Opret dine politikker (gælder ikke endnu)<br/>- Vælg mellem to typer (blok eller tillad) |
| **Trin 4**: [Anvendelse af politikker for informationsbarrierer](#step-4-apply-ib-policies) | – Angiv politikker til aktiv status<br/>- Kør politikprogrammet<br/>- Få vist politikstatus |
| **Trin 5**: [Konfiguration af informationsbarrierer på SharePoint og OneDrive (valgfrit)](#step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive) | – Konfigurer IB til SharePoint og OneDrive |
| **Trin 6**: [Informationsbarrierer (valgfrit)](#step-6-information-barriers-modes) | – Opdater IB-tilstande, hvis det er relevant |

## <a name="step-1-make-sure-prerequisites-are-met"></a>Trin 1: Sørg for, at forudsætninger er opfyldt

Ud over de påkrævede abonnementer og tilladelser skal du sørge for, at følgende krav er opfyldt, før du konfigurerer IB:

- **Mappedata**: Sørg for, at organisationens struktur afspejles i katalogdata. Hvis du vil udføre denne handling, skal du sørge for, at brugerkontoattributterne (f.eks. gruppemedlemskab, afdelingsnavn osv.) er udfyldt korrekt i Azure Active Directory (eller Exchange Online). Du kan få mere at vide i følgende ressourcer:
  - [Attributter for politikker for informationsbarrierer](information-barriers-attributes.md)
  - [Tilføj eller opdater en brugers profiloplysninger ved hjælp af Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)
  - [Konfigurer egenskaber for brugerkonto med Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)

- **Områdebaseret katalogsøgning**: Før du definerer din organisations første IB-politik, skal du [aktivere områdebaseret katalogsøgning i Microsoft Teams](/MicrosoftTeams/teams-scoped-directory-search). Vent mindst 24 timer efter aktivering af områdebaseret katalogsøgning, før du konfigurerer eller definerer IB-politikker.

- **Kontrollér, at overvågningslogføring er aktiveret**: Hvis du vil slå status for et IB-politikprogram op, skal logføring af overvågning være aktiveret. Overvågning er som standard aktiveret for Microsoft 365-organisationer. Nogle organisationer kan have deaktiveret overvågning af bestemte årsager. Hvis overvågning er deaktiveret for din organisation, kan det skyldes, at en anden administrator har deaktiveret den. Vi anbefaler, at du bekræfter, at det er OK at aktivere overvågning igen, når du fuldfører dette trin. Du kan finde flere oplysninger under [Slå søgning i overvågningslog til eller fra](turn-audit-log-search-on-or-off.md).

- **Fjern eksisterende Exchange Online politikker for adressekartoteket**: Før du definerer og anvender politikker for IB, skal du fjerne alle eksisterende Exchange Online politikker for adressekartoteket i din organisation. IB-politikker er baseret på politikker for adressekartoteker, og eksisterende ABP-politikker er ikke kompatible med de ABP'er, der er oprettet af IB. Hvis du vil fjerne dine eksisterende politikker for adressekartoteker, skal du se [Fjern en adressekartotekspolitik i Exchange Online](/exchange/address-books/address-book-policies/remove-an-address-book-policy). Du kan få flere oplysninger om IB-politikker og -Exchange Online under [Informationsbarrierer og Exchange Online](information-barriers.md#information-barriers-and-exchange-online).

- **Administrer ved hjælp af PowerShell (valgfrit):** IB-segmenter og -politikker kan defineres og administreres i Office 365 Security & Compliance PowerShell. Selvom der er angivet flere eksempler i denne artikel, skal du have kendskab til PowerShell-cmdlet'er og -parametre, hvis du vælger at bruge PowerShell til at konfigurere og administrere IB-segmenter og -politikker. Du skal også bruge Azure Active Directory PowerShell-modulet, hvis du vælger denne konfigurationsindstilling.
  - [Opret forbindelse til Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell)
  - [Installér Azure Active Directory PowerShell til Graph](/powershell/azure/active-directory/install-adv2)

- **Administration samtykke til IB i Microsoft Teams**: Når dine IB-politikker er på plads, kan de fjerne brugere, der ikke overholder IB-politikken, fra Grupper (f.eks. Teams-kanaler, der er baseret på grupper). Denne konfiguration hjælper med at sikre, at din organisation fortsat overholder politikker og regler. Brug følgende procedure til at aktivere, at IB-politikker fungerer som forventet i Microsoft Teams.

   1. Forudsætning: [Installér Azure Active Directory PowerShell til Graph](/powershell/azure/active-directory/install-adv2).

   2. Kør følgende PowerShell-cmdlet'er:

      ```powershell
      Connect-AzureAD -Tenant "<yourtenantdomain.com>"  //for example: Connect-AzureAD -Tenant "Contoso.onmicrosoft.com"
      $appId="bcf62038-e005-436d-b970-2a472f8c1982" 
      $sp=Get-AzureADServicePrincipal -Filter "appid eq '$($appid)'"
      if ($sp -eq $null) { New-AzureADServicePrincipal -AppId $appId }
      Start-Process  "https://login.microsoftonline.com/common/adminconsent?client_id=$appId"
      ```

   3. Når du bliver bedt om det, skal du logge på med din arbejds- eller skolekonto for Office 365.

   4. Gennemse oplysningerne i dialogboksen **Tilladelser,** og vælg derefter **Acceptér**.

Når alle forudsætningerne er opfyldt, skal du gå videre til næste trin.

## <a name="step-2-segment-users-in-your-organization"></a>Trin 2: Segmentér brugere i din organisation

I dette trin bestemmer du, hvilke IB-politikker der skal bruges, opretter en liste over segmenter, der skal defineres, og definerer dine segmenter. Definition af segmenter påvirker ikke brugerne. Det angiver blot fasen for IB-politikker, der skal defineres og derefter anvendes.

### <a name="determine-what-policies-are-needed"></a>Find ud af, hvilke politikker der er brug for

I betragtning af organisationens behov kan du afgøre, hvilke grupper i organisationen der skal bruge IB-politikker. Stil dig selv følgende spørgsmål:

- Er der interne, juridiske eller brancheregler, der kræver begrænsning af kommunikation og samarbejde mellem grupper og brugere i din organisation?
- Er der nogen grupper eller brugere, der bør forhindres i at kommunikere med en anden gruppe af brugere?
- Er der nogen grupper eller brugere, der kun må kommunikere med en eller to andre grupper af brugere?

Tænk på de politikker, du har brug for, som tilhører en af to typer:

- *Bloker* politikker forhindrer en gruppe i at kommunikere med en anden gruppe.
- *Tillad* , at politikker gør det muligt for en gruppe kun at kommunikere med bestemte grupper.

Når du har din indledende liste over nødvendige grupper og politikker, skal du fortsætte med at identificere de segmenter, du skal bruge til IB-politikkerne.

### <a name="identify-segments"></a>Identificer segmenter

Ud over din indledende liste over politikker kan du oprette en liste over segmenter for din organisation. Brugere, der skal medtages i IB-politikker, skal tilhøre et segment. Planlæg dine segmenter omhyggeligt, da en bruger kun kan være i ét segment. Der kan kun anvendes én IB-politik for hvert segment.

> [!IMPORTANT]
> En bruger kan kun være i ét segment.

Find ud af, hvilke attributter i organisationens katalogdata du skal bruge til at definere segmenter. Du kan bruge *Afdeling*, *MemberOf* eller en af de understøttede IB-attributter. Sørg for, at du har værdier i den attribut, du vælger for brugere. Du kan få flere oplysninger i de [understøttede attributter for IB](information-barriers-attributes.md).

> [!IMPORTANT]
> **Før du fortsætter til næste afsnit, skal du sørge for, at dine katalogdata indeholder værdier for attributter, som du kan bruge til at definere segmenter**. Hvis dine mappedata ikke har værdier for de attributter, du vil bruge, skal brugerkontiene opdateres, så de indeholder disse oplysninger, før du fortsætter med at konfigurere IB. Du kan få hjælp til dette i følgende ressourcer:<br/>- [Konfigurer egenskaber for brugerkonto med Office 365 PowerShell](../enterprise/configure-user-account-properties-with-microsoft-365-powershell.md)<br/>- [Tilføj eller opdater en brugers profiloplysninger ved hjælp af Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal)

### <a name="define-segments-using-the-compliance-portal"></a>Definer segmenter ved hjælp af overholdelsesportalen

Hvis du vil definere segmenter på overholdelsesportalen, skal du udføre følgende trin:

1. Log på [overholdelsesportalen](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din organisation.
2. På overholdelsesportalen skal du vælge **Informationsbarrieresegmenter** > .
3. På siden **Segmenter** skal du vælge **Nyt segment** for at oprette og konfigurere et nyt segment.
4. Angiv et navn til segmentet på siden **Navn** . Du kan ikke omdøbe et segment, når det først er oprettet.
5. Vælg **Næste**.
6. På siden **Brugergruppefilter** skal du vælge **Tilføj** for at konfigurere gruppen og brugerattributterne for segmentet. Vælg en attribut for segmentet på listen over tilgængelige attributter.
7. For den valgte attribut skal du vælge enten *Equal* eller *Not equal* og derefter angive værdien for attributten. Hvis du f.eks. har valgt *Afdeling* som attribut og *Lig med*, kan du angive *Marketing* som den definerede *afdeling* for denne segmentbetingelse. Du kan tilføje yderligere betingelser for en attribut ved at vælge **Tilføj betingelse**. Hvis du har brug for at slette en attribut eller en attributbetingelse, skal du vælge sletteikonet for attributten eller betingelsen.
8. Tilføj yderligere attributter efter behov på siden **Brugergruppefilter** , og vælg derefter **Næste**.
9. På siden **Gennemse dine indstillinger** skal du gennemse de indstillinger, du har valgt for segmentet, og eventuelle forslag eller advarsler til dine valg. Vælg **Rediger** for at ændre en af segmentattributterne og -betingelserne, eller vælg **Send** for at oprette segmentet.

    > [!IMPORTANT]
    > **Sørg for, at dine segmenter ikke overlapper hinanden**. Hver bruger, der påvirkes af IB-politikker, skal tilhøre ét (og kun ét) segment. Ingen bruger må tilhøre to eller flere segmenter. Se [eksempel: Contosos definerede segmenter](#contosos-defined-segments) i denne artikel for et eksempelscenarie.

### <a name="define-segments-using-powershell"></a>Definer segmenter ved hjælp af PowerShell

Hvis du vil definere segmenter med PowerShell, skal du fuldføre følgende trin:

1. Brug **New-OrganizationSegment-cmdlet'en** med parameteren **UserGroupFilter** , der svarer til den [attribut,](information-barriers-attributes.md) du vil bruge.

    | Syntaks | Eksempel |
    |:---------|:----------|
    | `New-OrganizationSegment -Name "segmentname" -UserGroupFilter "attribute -eq 'attributevalue'"` |`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` <p>I dette eksempel defineres et segment med navnet *HR* ved hjælp af *HR*, som er en værdi i attributten *Afdeling* . **-eq-delen** af cmdlet'en refererer til "lig med". (Alternativt kan du bruge **-ne** til at betyde "ikke lig med". Se [Brug af "er lig med" og "ikke lig med" i segmentdefinitioner](#using-equals-and-not-equals-in-powershell-segment-definitions). |

    Når du har kørt hver cmdlet, får du vist en liste over detaljer om det nye segment. Detaljer omfatter segmentets type, hvem der oprettede eller senest ændrede det osv. 

2. Gentag denne proces for hvert segment, du vil definere.

    > [!IMPORTANT]
    > **Sørg for, at dine segmenter ikke overlapper hinanden**. Hver bruger, der påvirkes af IB-politikker, skal tilhøre ét (og kun ét) segment. Ingen bruger må tilhøre to eller flere segmenter. Se [eksempel: Contosos definerede segmenter](#contosos-defined-segments) i denne artikel for et eksempelscenarie.

Når du har defineret dine segmenter, skal du gå til [Trin 3: Opret IB-politikker](#step-3-create-ib-policies).

### <a name="using-equals-and-not-equals-in-powershell-segment-definitions"></a>Brug af "er lig med" og "ikke lig med" i PowerShell-segmentdefinitioner

I følgende eksempel konfigurerer vi IB-segmenter ved hjælp af PowerShell og definerer et segment, så "Afdeling er lig med HR".

| Eksempel | Bemærk |
|:----------|:-------|
|`New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` | Bemærk, at segmentdefinitionen i dette eksempel indeholder parameteren "er lig med", der er angivet som **-eq**. |

Du kan også definere segmenter ved hjælp af parameteren "ikke lig med", der kaldes **-ne**, som vist i følgende tabel:

| Syntaks | Eksempel |
|:---------|:----------|
| `New-OrganizationSegment -Name "NotSales" -UserGroupFilter "Department -ne 'Sales'"` | I dette eksempel har vi defineret et segment med navnet *NotSales* , der omfatter alle, der ikke er i *Salg*. Den **-ne-del** af cmdlet'en refererer til "ikke lig med". |

Ud over at definere segmenter, der bruger parametrene "er lig med" eller "ikke lig med", kan du definere et segment ved hjælp af parametrene "er lig med" og "ikke lig med". Du kan også definere komplekse gruppefiltre ved hjælp af logiske *AND* - og *OR-operatorer* .

| Syntaks | Eksempel |
|:---------|:----------|
| `New-OrganizationSegment -Name "LocalFTE" -UserGroupFilter "Location -eq 'Local'" -and "Position -ne 'Temporary'"` | I dette eksempel definerede vi et segment kaldet *LocalFTE* , der omfatter brugere, der er placeret lokalt, og hvis positioner ikke er angivet som *midlertidige*. |
| `New-OrganizationSegment -Name "Segment1" -UserGroupFilter "MemberOf -eq 'group1@contoso.com'' -and MemberOf -ne 'group3@contoso.com'"`| I dette eksempel definerede vi et segment med navnet *Segment1* , der indeholder brugere, der er medlemmer af group1@contoso.com og ikke medlemmer af group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment2" -UserGroupFilter "MemberOf -eq 'group2@contoso.com' -or MemberOf -ne 'group3@contoso.com'"` | I dette eksempel definerede vi et segment kaldet *Segment2* , der indeholder brugere, der er medlemmer af group2@contoso.com og ikke medlemmer af group3@contoso.com. |
| `New-OrganizationSegment -Name "Segment1and2" -UserGroupFilter "(MemberOf -eq 'group1@contoso.com' -or MemberOf -eq 'group2@contoso.com') -and MemberOf -ne 'group3@contoso.com'"`| I dette eksempel definerede vi et segment kaldet *Segment1and2* , der omfatter brugere i group1@contoso.com og group2@contoso.com og ikke medlemmer af group3@contoso.com. |

> [!TIP]
> Hvis det er muligt, kan du bruge segmentdefinitioner, der omfatter "-eq" eller "-ne". Prøv ikke at definere komplekse segmentdefinitioner.

## <a name="step-3-create-ib-policies"></a>Trin 3: Opret IB-politikker

Når du opretter dine IB-politikker, bestemmer du, om du har brug for at forhindre kommunikation mellem bestemte segmenter eller begrænse kommunikationen til bestemte segmenter. Ideelt set skal du bruge det mindste antal IB-politikker til at sikre, at din organisation overholder interne, juridiske og branchemæssige krav. Du kan bruge overholdelsesportalen eller PowerShell til at oprette og anvende IB-politikker.

> [!TIP]
> For konsistens i brugeroplevelsen anbefaler vi, at du bruger Bloker politikker til de fleste scenarier, hvis det er muligt.

Med din liste over brugersegmenter og de IB-politikker, du vil definere, skal du vælge et scenarie og derefter følge trinnene.

- [Scenarie 1: Bloker kommunikation mellem segmenter](#scenario-1-block-communications-between-segments)
- [Scenarie 2: Tillad, at et segment kun kommunikerer med ét andet segment](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment)

> [!IMPORTANT]
> **Sørg for, at når du definerer politikker, kan du ikke tildele mere end én politik til et segment**. Hvis du f.eks. definerer én politik for et segment med navnet *Salg*, skal du ikke definere en yderligere politik for segmentet *Salg* .<br> Når du definerer politikker for IB, skal du desuden sørge for at angive disse politikker til inaktiv status, indtil du er klar til at anvende dem. Definition (eller redigering) af politikker påvirker ikke brugerne, før disse politikker er angivet til aktiv status og derefter anvendt.

### <a name="scenario-1-block-communications-between-segments"></a>Scenarie 1: Bloker kommunikation mellem segmenter

Når du vil blokere segmenter fra at kommunikere med hinanden, definerer du to politikker: én for hver retning. Hver politik blokerer kun kommunikation i én retning.

Lad os f.eks. antage, at du vil blokere kommunikation mellem Segment A og Segment B. I dette tilfælde skal du definere to politikker:

- Én politik, der forhindrer Segment A i at kommunikere med Segment B
- En anden politik, der forhindrer Segment B i at kommunikere med Segment A

#### <a name="create-policies-using-the-compliance-portal-for-scenario-1"></a>Opret politikker ved hjælp af overholdelsesportalen for scenarie 1

Hvis du vil definere politikker på overholdelsesportalen, skal du udføre følgende trin:

1. Log på [overholdelsesportalen](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din organisation.
2. På overholdelsesportalen skal du vælge **Politikker for informationsbarrierer** > .
3. På siden **Politikker** skal du vælge **Opret politik** for at oprette og konfigurere en ny IB-politik.
4. Angiv et navn til politikken på siden **Navn** , og vælg derefter **Næste**.
5. På siden **Tildelt segment** skal du vælge **Vælg segment**. Brug søgefeltet til at søge efter et segment efter navn, eller rul for at vælge segmentet på den viste liste. Vælg **Tilføj** for at føje det valgte segment til politikken. Du kan kun vælge ét segment.
6. Vælg **Næste**.
7. På siden **Kommunikation og samarbejde** skal du vælge politiktypen i feltet **Kommunikation og samarbejde** . Politikindstillingerne er enten *Tilladt* eller *Blokeret*. I dette eksempelscenarie vælges *Blokeret* for den første politik.

    >[!IMPORTANT]
    >Statussen Tilladt og Blokeret for segmenter kan ikke ændres, når du har oprettet en politik. Hvis du vil ændre status, når du har oprettet en politik, skal du slette politikken og oprette en ny.

8. Vælg **Vælg segment** for at definere handlingerne for målsegmentet. Du kan tildele mere end ét segment i dette trin. Hvis du f.eks. vil blokere brugere i et segment, der kaldes *Salg* , fra at kommunikere med brugere i et segment med navnet *Opslag*, ville du have defineret *salgssegmentet* i trin 5, og du ville tildele *Opslag* i indstillingen **Vælg segment** i dette trin.
9. Vælg **Næste**.
10. På siden **Politikstatus** skal du slå den aktive politikstatus til **Til**. Vælg **Næste** for at fortsætte.
11. På siden **Gennemse dine indstillinger** skal du gennemse de indstillinger, du har valgt for politikken, og eventuelle forslag eller advarsler til dine valg. Vælg **Rediger** for at ændre et af politiksegmenterne og status, eller vælg **Send** for at oprette politikken.

I dette eksempel skal du gentage de forrige trin for at oprette endnu en *blokpolitik* for at begrænse til at blokere brugere i et segment kaldet *Opslag* fra at kommunikere med brugere i et segment med navnet *Salg*. Du ville have defineret segmentet *Opslag* i trin 5, og du ville tildele *Salg* (eller flere segmenter) i indstillingen **Vælg segment** .

#### <a name="create-policies-using-powershell-for-scenario-1"></a>Opret politikker ved hjælp af PowerShell til scenarie 1

Hvis du vil definere politikker med PowerShell, skal du fuldføre følgende trin:

1. Hvis du vil definere din første blokeringspolitik, skal du bruge **New-InformationBarrierPolicy-cmdlet'en** med parameteren **SegmentsBlocked** .

    | Syntaks | Eksempel |
    |:--------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsBlocked "segment2name"` | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> I dette eksempel har vi defineret en politik med navnet *Sales-Research* for et segment med navnet *Sales*. Når denne politik er aktiv og anvendt, forhindrer den brugere i *Salg* i at kommunikere med brugere i et segment med navnet *Opslag*. |

2. Hvis du vil definere det andet blokeringssegment, skal du bruge **New-InformationBarrierPolicy-cmdlet'en** med parameteren **SegmentsBlocked** igen, denne gang med segmenterne tilbageført.

    | Eksempel | Bemærk |
    |:----------|:-------|
    |`New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` | I dette eksempel definerede vi en politik med navnet *Research-Sales* for at forhindre *, at Research* kommunikerer med *Sales*. |

3. Fortsæt til en af følgende handlinger:

   - (Hvis det er nødvendigt) [Definer en politik for at tillade, at et segment kun kommunikerer med ét andet segment](#scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment) 
   - (Når alle dine politikker er defineret) [Anvend IB-politikker](#step-4-apply-ib-policies)

### <a name="scenario-2-allow-a-segment-to-communicate-only-with-one-other-segment"></a>Scenarie 2: Tillad, at et segment kun kommunikerer med ét andet segment

Når du vil tillade, at et segment kun kommunikerer med ét andet segment, definerer du kun én politik for det pågældende segment. Det segment, der kommunikeres med, kræver ikke en lignende retningspolitik (fordi de som standard kan kommunikere og samarbejde med alle).

#### <a name="create-a-policy-using-the-compliance-portal-for-scenario-2"></a>Opret en politik ved hjælp af overholdelsesportalen for scenarie 2

Hvis du vil definere politikker på overholdelsesportalen, skal du udføre følgende trin:

1. Log på [overholdelsesportalen](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din organisation.
2. På overholdelsesportalen skal du vælge **Politikker for informationsbarrierer** > .
3. På siden **Politikker** skal du vælge **Opret politik** for at oprette og konfigurere en ny IB-politik.
4. Angiv et navn til politikken på siden **Navn** , og vælg derefter **Næste**.
5. På siden **Tildelt segment** skal du vælge **Vælg segment**. Brug søgefeltet til at søge efter et segment efter navn, eller rul for at vælge segmentet på den viste liste. Vælg **Tilføj** for at føje det valgte segment til politikken. Du kan kun vælge ét segment.
6. Vælg **Næste**.
7. På siden **Kommunikation og samarbejde** skal du vælge politiktypen i feltet **Kommunikation og samarbejde** . Politikindstillingerne er enten *Tilladt* eller *Blokeret*. I dette eksempelscenarie ville *Allowed* blive valgt for politikken.

    >[!IMPORTANT]
    >Statussen Tilladt og Blokeret for segmenter kan ikke ændres, når du har oprettet en politik. Hvis du vil ændre status, når du har oprettet en politik, skal du slette politikken og oprette en ny.

8. Vælg **Vælg segment** for at definere handlingerne for målsegmentet. Du kan tildele mere end ét segment i dette trin. Hvis du f.eks. vil give brugere i et segment kaldet *Produktion* tilladelse til at kommunikere med brugere i et segment med navnet *HR*, ville du have *defineret produktionssegmentet* i trin 5, og du ville tildele *HR* i indstillingen **Vælg segment** på dette trin.
9. Vælg **Næste**.
10. På siden **Politikstatus** skal du slå den aktive politikstatus til **Til**. Vælg **Næste** for at fortsætte.
11. På siden **Gennemse dine indstillinger** skal du gennemse de indstillinger, du har valgt for politikken, og eventuelle forslag eller advarsler til dine valg. Vælg **Rediger** for at ændre et af politiksegmenterne og status, eller vælg **Send** for at oprette politikken.

#### <a name="create-a-policy-using-powershell-for-scenario-2"></a>Opret en politik ved hjælp af PowerShell til scenarie 2

Hvis du vil definere politikker med PowerShell, skal du fuldføre følgende trin:

1. Hvis du vil tillade, at ét segment kun kommunikerer med ét andet segment, skal du bruge cmdlet'en **New-InformationBarrierPolicy** med parameteren **SegmentsAllowed** .

    | Syntaks | Eksempel |
    |:----------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name","segment1name"` | `New-InformationBarrierPolicy -Name "Manufacturing-HR" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Manufacturing" -State Inactive` <p> I dette eksempel definerede vi en politik med navnet *Manufacturing-HR* for et segment med navnet *Manufacturing*. Når denne politik er aktiv og anvendt, giver den kun brugere i *Produktion* mulighed for at kommunikere med brugere i et segment kaldet *HR*. I dette tilfælde kan *Produktion* ikke kommunikere med brugere, der ikke er en del af *HR*. |

    **Hvis det er nødvendigt, kan du angive flere segmenter med denne cmdlet, som vist i følgende eksempel.**

    | Syntaks | Eksempel |
    |:---------|:----------|
    | `New-InformationBarrierPolicy -Name "policyname" -AssignedSegment "segment1name" -SegmentsAllowed "segment2name", "segment3name","segment1name"` | `New-InformationBarrierPolicy -Name "Research-HRManufacturing" -AssignedSegment "Research" -SegmentsAllowed "HR","Manufacturing","Research" -State Inactive` <p> I dette eksempel har vi defineret en politik, der gør det muligt for segmentet *Forskning* kun at kommunikere med *HR* og *Produktion*. |

    Gentag dette trin for hver politik, du vil definere for at tillade, at bestemte segmenter kun kommunikerer med visse andre specifikke segmenter.

2. Fortsæt til en af følgende handlinger:

   - (Hvis det er nødvendigt) [Definer en politik til blokering af kommunikation mellem segmenter](#scenario-1-block-communications-between-segments) 
   - (Når alle dine politikker er defineret) [Anvend IB-politikker](#step-4-apply-ib-policies)

## <a name="step-4-apply-ib-policies"></a>Trin 4: Anvend IB-politikker

IB-politikker er ikke i kraft, før du angiver dem til aktiv status og anvender politikkerne.

### <a name="apply-policies-using-the-compliance-portal"></a>Anvend politikker ved hjælp af overholdelsesportalen

Hvis du vil anvende politikker på overholdelsesportalen, skal du udføre følgende trin:

1. Log på [overholdelsesportalen](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din organisation.
2. På overholdelsesportalen skal du vælge **Program for politik for** **informationsbarrierer** > .
3. På siden **Politikker-program** skal du vælge **Anvend alle politikker** for at anvende alle IB-politikker i din organisation.

    >[!NOTE]
    >Tillad, at systemet anvender politikkerne i 30 minutter. Systemet anvender politikker, som brugeren anvender. Systemet behandler ca. 5.000 brugerkonti pr. time.

### <a name="apply-policies-using-powershell"></a>Anvend politikker ved hjælp af PowerShell

Hvis du vil anvende politikker ved hjælp af PowerShell, skal du udføre følgende trin:

1. Brug **cmdlet'en Get-InformationBarrierPolicy** til at få vist en liste over de politikker, der er defineret. Bemærk status og id (GUID) for hver politik.

    Syntaks: `Get-InformationBarrierPolicy`

2. Hvis du vil angive en politik til aktiv status, skal du bruge **Set-InformationBarrierPolicy-cmdlet'en** med parameteren **Identity** og parameteren **State** angivet til **Active**. 

    | Syntaks | Eksempel |
    |:---------|:----------|
    | `Set-InformationBarrierPolicy -Identity GUID -State Active` | `Set-InformationBarrierPolicy -Identity 43c37853-ea10-4b90-a23d-ab8c93772471 -State Active` <p> I dette eksempel angiver vi en IB-politik, der har GUID *43c37853-ea10-4b90-a23d-ab8c93772471* til aktiv status. |

    Gentag dette trin efter behov for hver politik.

3. Når du er færdig med at angive dine IB-politikker til aktiv status, skal du bruge cmdlet'en **Start-InformationBarrierPoliciesApplication** i Security & Compliance PowerShell.

    Syntaks: `Start-InformationBarrierPoliciesApplication`

    Når du har kørt `Start-InformationBarrierPoliciesApplication`, kan systemet begynde at anvende politikkerne i 30 minutter. Systemet anvender politikker, som brugeren anvender. Systemet behandler ca. 5.000 brugerkonti pr. time.

### <a name="view-status-of-user-accounts-segments-policies-or-policy-application"></a>Få vist status for brugerkonti, segmenter, politikker eller politikprogram

Med PowerShell kan du få vist status for brugerkonti, segmenter, politikker og politikprogram som angivet i følgende tabel.

| Sådan får du vist disse oplysninger | Udfør denne handling |
|:---------------|:----------|
| Brugerkonti | Brug cmdlet'en **Get-InformationBarrierRecipientStatus** med identitetsparametre. <p> Syntaks: `Get-InformationBarrierRecipientStatus -Identity <value> -Identity2 <value>` <p> Du kan bruge en hvilken som helst værdi, der entydigt identificerer hver bruger, f.eks. navn, alias, entydigt navn, vedtaget domænenavn, mailadresse eller GUID. <p> Eksempel: `Get-InformationBarrierRecipientStatus -Identity meganb -Identity2 alexw` <p> I dette eksempel henviser vi til to brugerkonti i Office 365: *meganb* for *Megan* og *alexw* for *Alex*. <p> (Du kan også bruge denne cmdlet til en enkelt bruger: `Get-InformationBarrierRecipientStatus -Identity <value>`) <p> Denne cmdlet returnerer oplysninger om brugere, f.eks. attributværdier og eventuelle IB-politikker, der anvendes.|
| Segmenter | Brug cmdlet'en **Get-OrganizationSegment** .<p> Syntaks: `Get-OrganizationSegment` <p> Denne cmdlet viser en liste over alle de segmenter, der er defineret for din organisation. |
| IB-politikker | Brug cmdlet'en **Get-InformationBarrierPolicy** . <p> Syntaks: `Get-InformationBarrierPolicy` <p> Denne cmdlet viser en liste over de IB-politikker, der er defineret, og deres status. |
| Det seneste IB-politikprogram | Brug cmdlet'en **Get-InformationBarrierPoliciesApplicationStatus** . <p> Syntaks: `Get-InformationBarrierPoliciesApplicationStatus`<p> Denne cmdlet viser oplysninger om, hvorvidt politikprogrammet er fuldført, mislykket eller er i gang. |
| Alle IB-politikprogrammer|Bruge `Get-InformationBarrierPoliciesApplicationStatus -All`<p> Denne cmdlet viser oplysninger om, hvorvidt politikprogrammet er fuldført, mislykket eller er i gang.|

### <a name="what-if-i-need-to-remove-or-change-policies"></a>Hvad gør jeg, hvis jeg har brug for at fjerne eller ændre politikker?

Der findes ressourcer, der kan hjælpe dig med at administrere dine IB-politikker.

- Hvis du vil redigere, stoppe eller fjerne IB-politikker, skal du se [Administrer politikker for informationsbarrierer](information-barriers-edit-segments-policies.md).
- Hvis noget går galt med IB, kan du se [Fejlfinding af informationsbarrierer](/office365/troubleshoot/information-barriers/information-barriers-troubleshooting).

## <a name="step-5-configuration-for-information-barriers-on-sharepoint-and-onedrive"></a>Trin 5: Konfiguration af informationsbarrierer på SharePoint og OneDrive

Hvis du konfigurerer IB til SharePoint og OneDrive, skal du aktivere IB på disse tjenester. Du skal også aktivere IB på disse tjenester, hvis du konfigurerer IB til Microsoft Teams. Når der oprettes et team i Microsoft Teams-teamet, oprettes der automatisk et SharePoint-websted, som knyttes til Microsoft Teams for filoplevelsen. IB-politikker anvendes ikke som standard på dette nye SharePoint-websted og de nye Filer.

Hvis du vil aktivere IB i SharePoint og OneDrive, skal du følge vejledningen og trinnene i artiklen [Brug informationsbarrierer med SharePoint](/sharepoint/information-barriers) .

## <a name="step-6-information-barriers-modes"></a>Trin 6: Informationsbarrierer

Tilstande kan hjælpe med at styrke adgang, deling og medlemskab af en Microsoft 365-ressource baseret på ressourcens IB-tilstand. Tilstande understøttes på Microsoft 365-grupper-, Microsoft Teams-, OneDrive- og SharePoint-websteder og aktiveres automatisk i din nye eller eksisterende IB-konfiguration.

Følgende IB-tilstande understøttes på Microsoft 365-ressourcer:

| **Tilstand** | **Beskrivelse** | **Eksempel** |
|:-----|:------------|:--------|
| **Åbne** | Der er ikke knyttet nogen IB-politikker eller -segmenter til Microsoft 365-ressourcen. Alle kan inviteres til at være medlem af ressourcen. | Et teamwebsted, der er oprettet til picnicbegivenhed for din organisation. |
| **Ejer ændret (prøveversion)** | IB-politikken for Microsoft 365-ressourcen bestemmes ud fra ressourceejerens IB-politik. Ressourceejerne kan invitere alle brugere til ressourcen på baggrund af deres IB-politikker. Denne tilstand er nyttig, når din virksomhed ønsker at tillade samarbejde mellem inkompatible segmentbrugere, der er ændret af ejeren. Det er kun ressourceejeren, der kan tilføje nye medlemmer i henhold til deres IB-politik. | HR-vicedirektøren ønsker at samarbejde med VP'erne til salg og forskning. Et nyt SharePoint-websted, der er angivet med Ejer i IB-tilstand *Begrænset* for at føje både brugere af salgs- og forskningssegmentet til det samme websted. Det er ejerens ansvar at sikre, at de relevante medlemmer føjes til ressourcen. |
| **Implicit** | IB-politikken eller -segmenterne i Microsoft 365-ressourcen nedarves fra ressourcemedlemmernes IB-politik. Ejeren kan tilføje medlemmer, så længe de er kompatible med de eksisterende medlemmer af ressourcen. Denne tilstand er standard-IB-tilstand for Microsoft Teams. | Brugeren af salgssegmentet opretter et Microsoft Teams-team for at samarbejde med andre kompatible segmenter i organisationen. |
| **Eksplicit** | IB-politikken for Microsoft 365-ressourcen er pr. de segmenter, der er knyttet til ressourcen. Ressourceejeren eller SharePoint-administratoren har mulighed for at administrere segmenterne på ressourcen. | Et websted, der kun er oprettet for medlemmer af salgssegmentet for at samarbejde ved at knytte segmentet Salg til webstedet. |
| **Blandet (prøveversion)** | Gælder kun for OneDrive. OneDrives IB-politik gælder for de segmenter, der er knyttet til OneDrive. Ressourceejeren eller OneDrive-administratoren har mulighed for at administrere segmenterne på ressourcen. | Et OneDrive, der er oprettet til salgssegmentmedlemmer for at samarbejde, må deles med ikke-segmenterede brugere. |

Du kan få flere oplysninger om IB-tilstande, og hvordan de er konfigureret på tværs af tjenester, i følgende artikler:

- [Tilstande for informationsbarrierer og Microsoft Teams](/microsoftteams/information-barriers-in-teams)
- [Informationsbarrieretilstande og OneDrive](/onedrive/information-barriers)
- [Informationsbarrieretilstande og SharePoint](/sharepoint/information-barriers)

## <a name="example-scenario-contosos-departments-segments-and-policies"></a>Eksempelscenarie: Contosos afdelinger, segmenter og politikker

Hvis du vil se, hvordan en organisation kan nærme sig definere segmenter og politikker, skal du overveje følgende eksempelscenarie.

### <a name="contosos-departments-and-plan"></a>Contosos afdelinger og plan

Contoso har fem afdelinger: *HR*, *Salg*, *Marketing*, *Forskning* og *Produktion*. For at overholde brancheregler skal brugere i nogle afdelinger ikke kommunikere med andre afdelinger, som vist i følgende tabel:

| **Segment** | **Kan kommunikere med** | **Kan ikke kommunikere med** |
|:------------|:-------------------------|:---------------------------|
| HR | Alle | (ingen begrænsninger) |
| Salg | HR, marketing, produktion | Opslag |
| Marketing | Alle | (ingen begrænsninger) |
| Opslag | HR, marketing, produktion | Salg |
| Fremstilling | HR, Marketing | Alle andre end HR eller Marketing |

I denne struktur omfatter Contosos plan tre IB-politikker:

1. En IB-politik, der er udviklet til at forhindre Salg i at kommunikere med research
2. En anden IB-politik, der forhindrer Research i at kommunikere med Sales.
3. En IB-politik, der er designet til kun at gøre det muligt for Produktion at kommunikere med HR og Marketing.

I dette scenarie er det ikke nødvendigt at definere IB-politikker for *HR* eller *Marketing*.

### <a name="contosos-defined-segments"></a>Contosos definerede segmenter

Contoso bruger attributten Afdeling i Azure Active Directory til at definere segmenter på følgende måde:

| Institut | Segmentdefinition |
|:-------------|:---------------------|
| HR | `New-OrganizationSegment -Name "HR" -UserGroupFilter "Department -eq 'HR'"` |
| Salg | `New-OrganizationSegment -Name "Sales" -UserGroupFilter "Department -eq 'Sales'"` |
| Marketing | `New-OrganizationSegment -Name "Marketing" -UserGroupFilter "Department -eq 'Marketing'"` |
| Opslag | `New-OrganizationSegment -Name "Research" -UserGroupFilter "Department -eq 'Research'"` |
| Fremstilling | `New-OrganizationSegment -Name "Manufacturing" -UserGroupFilter "Department -eq 'Manufacturing'"` |

Når segmenterne er defineret, fortsætter Contoso med at definere IB-politikkerne.

### <a name="contosos-ib-policies"></a>Contosos IB-politikker

Contoso definerer tre IB-politikker, som beskrevet i følgende tabel:

| Politik | Politikdefinition |
|:---------|:--------------------|
| **Politik 1: Undgå, at salg kommunikerer med opslag** | `New-InformationBarrierPolicy -Name "Sales-Research" -AssignedSegment "Sales" -SegmentsBlocked "Research" -State Inactive` <p> I dette eksempel kaldes *IB-politikken Sales-Research*. Når denne politik er aktiv og anvendt, hjælper det med at forhindre brugere, der er i segmentet Salg, i at kommunikere med brugere i segmentet Opslag. Denne politik er en envejspolitik. Det forhindrer ikke Research i at kommunikere med Sales. Til det formål er Politik 2 nødvendig. |
| **Politik 2: Undgå, at opslag kommunikerer med Salg** | `New-InformationBarrierPolicy -Name "Research-Sales" -AssignedSegment "Research" -SegmentsBlocked "Sales" -State Inactive` <p> I dette eksempel kaldes *IB-politikken Research-Sales*. Når denne politik er aktiv og anvendt, hjælper det med at forhindre brugere, der er i segmentet Opslag, i at kommunikere med brugere i segmentet Salg. |
| **Politik 3: Tillad, at produktion kun kommunikerer med HR og marketing** | `New-InformationBarrierPolicy -Name "Manufacturing-HRMarketing" -AssignedSegment "Manufacturing" -SegmentsAllowed "HR","Marketing","Manufacturing" -State Inactive` <p> I dette tilfælde kaldes *IB-politikken Manufacturing-HRMarketing*. Når denne politik er aktiv og anvendt, kan Produktion kun kommunikere med HR og Marketing. HR og marketing er ikke begrænset til at kommunikere med andre segmenter. |

Når segmenter og politikker er defineret, anvender Contoso politikkerne ved at køre cmdlet'en **Start-InformationBarrierPoliciesApplication** .

Når cmdlet'en er færdig, overholder Contoso branchekravene.

## <a name="resources"></a>Ressourcer

- [Få mere at vide om informationsbarrierer](information-barriers.md)
- [Få mere at vide om informationsbarrierer i Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Få mere at vide om informationsbarrierer i SharePoint Online](/sharepoint/information-barriers)
- [Få mere at vide om informationsbarrierer i OneDrive](/onedrive/information-barriers)
