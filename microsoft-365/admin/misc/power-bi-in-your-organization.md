---
title: Power BI i din organisation
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- PWB150
ms.assetid: d7941332-8aec-4e5e-87e8-92073ce73dc5
ROBOTS: NOINDEX
description: Få mere at vide om Power BI, og hvordan brugere i din organisation kan bruge denne virksomhedsanalysetjeneste.
ms.openlocfilehash: b4e1fd299caa4045a68770adc3a2d53dd4b11ec0
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469530"
---
# <a name="using-power-bi-data-in-your-organization"></a>Brug af Power BI data i din organisation

På denne side beskrives det, hvordan brugere i din organisation kan bruge Power BI, og hvordan du kan styre, hvordan din organisation henter denne tjeneste.

## <a name="what-is-power-bi"></a>Hvad er Power BI?

Microsoft Power BI giver brugerne mulighed for at visualisere data, dele opdagelser og samarbejde på intuitive nye måder. Du kan få mere at vide på [Power BI websted](https://powerbi.microsoft.com/en-us/).
  
## <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Opfylder Power BI nationale, regionale og branchespecifikke krav til overholdelse af angivne standarder?

Du kan få mere at vide om Power BI overholdelse af angivne standarder i [Microsoft Center for sikkerhed og rettighedsadministration](https://go.microsoft.com/fwlink/?LinkId=785324).
  
## <a name="how-do-users-sign-up-for-power-bi"></a>Hvordan tilmelder brugerne sig Power BI?

Som administrator kan du tilmelde dig Power BI via [Power BI websted](https://powerbi.microsoft.com/en-us/). Du kan også tilmelde dig via siden købstjenester på Microsoft 365 Administration. Når en administrator tilmelder sig Power BI, kan vedkommende tildele brugerabonnementslicenser til brugere, der skal have adgang.
  
Derudover kan individuelle brugere i din organisation muligvis tilmelde sig Power BI via [Power BI websted](https://powerbi.microsoft.com/en-us/). Når en bruger i organisationen tilmelder sig Power BI, tildeles brugeren automatisk en Power BI licens.
  
## <a name="how-do-individual-users-in-my-organization-sign-up"></a>Hvordan tilmelder individuelle brugere i min organisation sig?

Der er tre scenarier, der kan gælde for brugere i din organisation:
  
### <a name="scenario-1-your-organization-already-has-an-existing-microsoft-365-environment-and-the-user-signing-up-for-power-bi-already-has-a-microsoft-365-account"></a>Scenarie 1: Organisationen har allerede et Microsoft 365 miljø, og brugeren, der tilmelder sig Power BI, har allerede en Microsoft 365 konto.

Hvis en bruger i dette scenarie allerede har en arbejds- eller skolekonto i lejeren (f.eks. contoso.com), men endnu ikke har Power BI, aktiverer Microsoft blot planen for den pågældende konto, og brugeren får automatisk besked om, hvordan Power BI-tjeneste bruges.
  
### <a name="scenario-2-your-organization-has-an-existing-microsoft-365-environment-and-the-user-signing-up-for-power-bi-doesnt-have-a-microsoft-365-account"></a>Scenarie 2: Organisationen har et eksisterende Microsoft 365 miljø, og brugeren, der tilmelder sig Power BI, har ikke en Microsoft 365 konto.

I dette scenarie har brugeren en mailadresse i organisationens domæne (f.eks. contoso.com), men har endnu ikke en Microsoft 365 konto. I dette tilfælde kan brugeren tilmelde sig Power BI og får automatisk en konto. Det giver brugeren adgang til Power BI-tjeneste. Hvis en medarbejder med navnet Nancy f.eks. bruger sin arbejdsmailadresse (f.eks. Nancy@contoso.com) til at tilmelde sig, tilføjer Microsoft automatisk Nancy som bruger i contoso-Microsoft 365-miljøet og aktiverer Power BI for den pågældende konto.
  
### <a name="scenario-3-your-organization-does-not-have-a-microsoft-365-environment-connected-to-your-email-domain"></a>Scenarie 3: Organisationen har ikke et Microsoft 365 miljø, der er forbundet til dit maildomæne.

Der er ingen administrative handlinger, som organisationen skal bruge til at drage fordel af Power BI.
  
> [!IMPORTANT]
> Hvis din organisation har flere maildomæner, og du foretrækker, at alle mailadresseudvidelser er i den samme lejer, skal du føje alle mailadressedomæner til den pågældende lejer, før nogen brugere opretter din primære lejer. Der er ingen automatiseret mekanisme til flytning af brugere på tværs af lejere, efter at de er blevet oprettet. Du kan få flere oplysninger om denne proces under [Kan jeg styre den lejer, som brugerne føjes til, hvis jeg har flere domæner?](#if-i-have-multiple-domains-can-i-control-the-tenant-that-users-are-added-to) senere i denne artikel og [Føj et domæne til Office 365](../setup/add-domain.md) online.
  
## <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Hvordan ændrer dette den måde, jeg administrerer identiteter for brugere i min organisation på i dag?

Hvis organisationen allerede har et eksisterende Microsoft 365 miljø, og alle brugerne i organisationen har Microsoft 365 konti, ændres identitetsstyringen ikke.
  
Hvis organisationen allerede har et eksisterende Microsoft 365 miljø, men det ikke er alle brugerne i organisationen, der har Microsoft 365 konti, opretter vi en bruger i lejeren og tildeler licenser baseret på brugerens arbejds- eller skolemailadresse. Det betyder, at antallet af brugere, du administrerer på et bestemt tidspunkt, vil vokse, efterhånden som brugerne i din organisation tilmelder sig tjenesten.
  
Hvis du administrerer din mappe i det lokale miljø og bruger Active Directory Federation Services (AD FS), føjer Microsoft ikke brugere til din lejer, og brugere, der forsøger at tilmelde sig din lejer, modtager en meddelelse om at kontakte organisationens administrator.
  
Hvis din organisation ikke har et Microsoft 365 miljø, der er forbundet til dit maildomæne, sker der ingen ændring i den måde, du administrerer identiteter på. Brugerne føjes til en ny brugermappe kun i skyen, og du har mulighed for at overtage lejeradministratoren og administrere dem.
  
## <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Hvad er processen til administration af en lejer, der er oprettet af Microsoft for mine brugere?

Hvis en lejer blev oprettet af Microsoft, kan du gøre krav på og administrere den pågældende lejer ved at følge disse trin:
  
1. Tilmeld dig lejeren ved [at tilmelde dig Power BI](https://go.microsoft.com/fwlink/?LinkId=522448) ved hjælp af et mailadressedomæne, der svarer til det lejerdomæne, du vil administrere. Hvis Microsoft f.eks. oprettede den contoso.com lejer, skal du forbinde lejeren med en mailadresse, der slutter med @contoso.com.

1. Få administratorkontrol ved at bekræfte ejerskabet over domænet: Når du er i lejeren, kan du forfremme dig selv til administratorrollen ved at bekræfte ejerskabet over domænet. Det gør du ved at følge disse trin:

::: moniker range="o365-worldwide"

3. Gå til <a href="https://admin.microsoft.com" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

3. Gå til <a href="https://portal.partner.microsoftonline.cn" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end

4. Vælg appstarterikonet øverst til venstre, og vælg **Administrator**.

    ![Appstarter med administratorappen fremhævet.](../../media/4eea9dbc-591b-48be-9916-322d41c6525b.png)
  
5. Læs vejledningen på siden **Bliv administrator** , og vælg derefter **Ja, jeg vil være administrator**.

    > [!NOTE]
    >  Hvis denne indstilling ikke vises, er der allerede en administrator på plads.
  
## <a name="if-i-have-multiple-domains-can-i-control-the-tenant-that-users-are-added-to"></a>Hvis jeg har flere domæner, kan jeg så styre den lejer, som brugerne er føjet til?

Hvis du ikke foretager dig noget, oprettes der en lejer for hvert brugermaildomæne og underdomæne.
  
Hvis du ønsker, at alle brugere skal være i den samme lejer, uanset deres mailadresseudvidelser:
  
- Opret en destinationslejer på forhånd, eller brug en eksisterende lejer, og tilføj alle eksisterende domæner og underdomæner, som du vil konsolidere i lejeren. Derefter vil alle brugere med mailadresser, der slutter med disse domæner og underdomæner, automatisk tilmelde sig destinationslejer, når de tilmelder sig.

> [!IMPORTANT]
> Der er ingen understøttet automatiseret mekanisme til flytning af brugere på tværs af lejere, når de først er oprettet. Hvis du vil vide mere om, hvordan du føjer domæner til en enkelt Microsoft 365 lejer, skal du se [Føj et domæne til Office 365](../setup/add-domain.md).

> [!IMPORTANT]
> Du kan finde flere oplysninger og vejledning om administration af lejere under [Hvad er Power BI administration?](/power-bi/service-admin-administering-power-bi-in-your-organization).
  
## <a name="how-can-i-prevent-users-from-joining-my-existing-tenant"></a>Hvordan kan jeg forhindre brugere i at tilmelde sig min eksisterende lejer?

Der er trin, du kan udføre som administrator for at forhindre brugere i at tilmelde sig din eksisterende lejer. Hvis du blokerer brugere fra at tilmelde sig lejeren, mislykkes brugernes forsøg på at logge på, og de bliver bedt om at kontakte organisationens administrator. Du behøver ikke at gentage denne proces, hvis du allerede har deaktiveret automatisk licensdistribution før (f.eks. Office 365 Education for studerende, fakultetsmedarbejdere og personale).
  
Disse trin kræver brug af Windows PowerShell. Hvis du vil i gang med Windows PowerShell, skal du se [introduktionsvejledningen til PowerShell](/powershell/scripting/overview).
  
Hvis du vil udføre følgende trin, skal du installere den nyeste 64-bit version af [Azure Active Directory V2 PowerShell-modulet](https://www.powershellgallery.com/packages/AzureADPreview/2.0.2.5).
  
Når du har valgt linket, skal du vælge **Kør** for at køre installationspakken.
  
**Deaktiver automatisk lejerjoinforbindelse**: Brug denne Windows PowerShell kommando til at forhindre nye brugere i at tilmelde sig en administreret lejer:
  
Sådan deaktiverer du automatisk lejerjoinforbindelse for nye brugere:  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $false`
  
Sådan aktiverer du automatisk lejerjoinforbindelse for nye brugere:  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $true`
  
> [!NOTE]
> Denne blokering forhindrer nye brugere i din organisation i at tilmelde sig Power BI. Brugere, der tilmelder sig Power BI før deaktivering af nye tilmeldinger til din organisation, bevarer stadig deres licenser. Se [Hvordan gør jeg fjern Power BI for brugere, der allerede har tilmeldt sig? for at](#how-do-i-remove-power-bi-for-users-that-already-signed-up) få vejledning i, hvordan du kan fjerne adgangen til Power BI for brugere, der tidligere har tilmeldt sig tjenesten.
  
## <a name="how-can-i-allow-users-to-join-my-existing-tenant"></a>Hvordan kan jeg tillade brugere at tilmelde sig min eksisterende lejer?

Hvis du vil tillade brugere at tilmelde sig din lejer, skal du køre den modsatte kommando som beskrevet i ovenstående spørgsmål:  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $true`
  
## <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>Hvordan gør jeg bekræfte, om blokeringen er aktiveret i lejeren?

Brug følgende PowerShell-script:  `Get-MsolCompanyInformation | fl allow*`
  
## <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Hvordan kan jeg forhindre mine eksisterende brugere i at begynde at bruge Power BI?

**Deaktiver automatisk licensdistribution:** Brug dette Windows PowerShell script til at deaktivere automatiske licensdistributioner for eksisterende brugere. Du behøver ikke at gentage denne proces, hvis du allerede har deaktiveret automatisk licensdistribution før (f.eks. Office 365 Education for studerende, fakultetsmedarbejdere og personale).
  
Sådan deaktiverer du automatisk licensdistribution for eksisterende brugere:  `Set-MsolCompanySettings -AllowAdHocSubscriptions $false`
  
Sådan aktiverer du automatisk licensdistribution for eksisterende brugere:  `Set-MsolCompanySettings -AllowAdHocSubscriptions $true`
  
> [!NOTE]
> Flaget *AllowAdHocSubscriptions* bruges til at styre flere brugerfunktioner i din organisation, herunder brugernes mulighed for at tilmelde sig Azure Rights Management Service. Hvis du ændrer dette flag, påvirker det alle disse funktioner.
  
## <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Hvordan kan jeg give mine eksisterende brugere tilladelse til at tilmelde sig Power BI?

Hvis du vil tillade dine eksisterende brugere at tilmelde sig Power BI, skal du køre den modsatte kommando, som beskrevet i ovenstående spørgsmål:`Set-MsolCompanySettings -AllowAdHocSubscriptions $true`
  
## <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Hvordan gør jeg fjerne Power BI for brugere, der allerede er tilmeldt?

Hvis en bruger har tilmeldt sig Power BI, men du ikke længere ønsker, at vedkommende skal have adgang til Power BI, kan du fjerne den Power BI licens for den pågældende bruger.
  
::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

::: moniker-end

::: moniker range="o365-21vianet"

 1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> .

::: moniker-end

2. Find den bruger, du vil fjerne licensen for, og vælg derefter vedkommendes navn.

3. Fjern markeringen i afkrydsningsfeltet **Microsoft Power BI** under fanen **Licenser og apps**.

4. Vælg **Gem ændringer**.

## <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Hvordan gør jeg vide, hvornår nye brugere har tilmeldt sig min lejer?

Brugere, der har tilmeldt sig din lejer som en del af dette program, tildeles en entydig licens, som du kan filtrere efter i din aktive brugerrude i administrationsdashboardet.
  
Hvis du vil oprette denne nye visning, skal du i Administration følge trinnene i [Opret en brugerdefineret brugervisning](../add-users/create-edit-or-delete-a-custom-user-view.md#create-a-custom-user-view). Under **Tildelt produktlicens** skal du vælge **Microsoft Power BI**. Når den nye visning er blevet oprettet, kan du se alle de brugere i din lejer, der har tilmeldt sig dette program.
  
## <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>Er der andre ting, jeg skal være forberedt på?

Du oplever muligvis en stigning i anmodninger om nulstilling af adgangskode. Du kan få oplysninger om denne proces under [Nulstil en brugers adgangskode](../add-users/reset-passwords.md).
  
Du kan fjerne en bruger fra din lejer via standardprocessen i Administration. Men hvis brugeren stadig har en aktiv mailadresse fra din organisation, kan vedkommende tilmelde sig igen, medmindre du blokerer for, at alle brugere tilmelder sig.
  
## <a name="why-did-1-million-licenses-for-microsoft-power-bi-show-up-in-my-tenant"></a>Hvorfor blev der vist 1 million licenser til Microsoft Power BI i min lejer?

Som en kvalificerende organisation er brugerne i din organisation berettiget til at bruge Microsoft Power BI-tjeneste, og disse licenser repræsenterer den tilgængelige kapacitet for nye Power BI brugere i din lejer. Der er intet gebyr for disse licenser. Hvis du har valgt at give brugerne tilladelse til selv at tilmelde sig Power BI, får de tildelt en af disse gratis licenser, når de fuldfører tilmeldingsprocessen. Du kan også selv vælge at tildele disse licenser til brugerne via Administration.
  
## <a name="is-this-free-will-i-be-charged-for-these-licenses"></a>Er det gratis? Vil jeg blive opkrævet betaling for disse licenser?

Disse licenser er til den gratis version af Power BI. Hvis du er interesseret i yderligere funktioner, kan du se Power BI Pro version.
  
## <a name="why-1-million-licenses"></a>Hvorfor 1 million licenser?

Vi har valgt et tal, der er stort nok til, at de fleste organisationer ville have rigelige licenser til straks at give denne fordel til deres brugere.
  
## <a name="what-if-i-need-more-than-1-million-licenses"></a>Hvad gør jeg, hvis jeg har brug for mere end 1 million licenser?

Kontakt din Microsoft-kontorepræsentant for at få flere oplysninger, hvis du skal have yderligere licenser.