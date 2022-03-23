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
description: Få mere Power BI om, hvordan brugerne i organisationen kan bruge denne virksomhedsanalysetjeneste.
ms.openlocfilehash: f89f03470561cd9c8dcddf4e0bbde60d4d9d4fa2
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63588363"
---
# <a name="power-bi-in-your-organization"></a>Power BI i din organisation

På denne side beskrives det, hvordan brugerne i organisationen kan bruge Power BI og hvordan du kan styre, hvordan organisationen får denne tjeneste.

## <a name="what-is-power-bi"></a>Hvad er Power BI?

Microsoft Power BI giver brugerne mulighed for at visualisere data, dele opdagelser og samarbejde på intuitive, nye måder. Du kan få mere at vide [Power BI webstedet.](https://powerbi.microsoft.com/en-us/)
  
## <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>opfylder Power BI nationale, regionale og branchespecifikke overholdelseskrav?

Du kan få mere at Power BI om overholdelse af regler og standarder i [Microsoft Center for sikkerhed og sikkerhed](https://go.microsoft.com/fwlink/?LinkId=785324).
  
## <a name="how-do-users-sign-up-for-power-bi"></a>Hvordan tilmelder brugerne sig Power BI?

Som administrator kan du tilmelde dig Power BI via [Power BI websted](https://powerbi.microsoft.com/en-us/). Du kan også tilmelde dig via siden til køb af tjenester på Microsoft 365 Administration. Når en administrator tilmelder sig en Power BI, kan de tildele brugerabonnementslicenser til brugere, der skal have adgang.
  
Desuden kan individuelle brugere i organisationen muligvis tilmelde sig Power BI via [Power BI websted](https://powerbi.microsoft.com/en-us/). Når en bruger i organisationen tilmelder sig en Power BI, tildeles den pågældende bruger automatisk Power BI licens.
  
## <a name="how-do-individual-users-in-my-organization-sign-up"></a>Hvordan tilmelder individuelle brugere i organisationen sig?

Der er tre scenarier, der kan gælde for brugere i organisationen:
  
### <a name="scenario-1-your-organization-already-has-an-existing-microsoft-365-environment-and-the-user-signing-up-for-power-bi-already-has-a-microsoft-365-account"></a>Scenarie 1: Organisationen har allerede et eksisterende Microsoft 365, og brugeren, der tilmelder sig Power BI, har allerede en Microsoft 365-konto.

I dette scenarie aktiverer Microsoft blot planen for den pågældende konto, hvis en bruger allerede har en arbejds- eller skolekonto i lejeren (f.eks. contoso.com), men endnu ikke har Power BI, og brugeren får automatisk besked om, hvordan han/hun bruger Power BI-tjenesten.
  
### <a name="scenario-2-your-organization-has-an-existing-microsoft-365-environment-and-the-user-signing-up-for-power-bi-doesnt-have-a-microsoft-365-account"></a>Scenarie 2: Organisationen har et eksisterende Microsoft 365 miljø, og brugeren, der tilmelder sig Power BI, har ikke en Microsoft 365 konto.

I dette scenarie har brugeren en mailadresse på organisationens domæne (f.eks. contoso.com), men endnu ikke har en Microsoft 365 konto. I dette tilfælde kan brugeren tilmelde sig en Power BI og får automatisk en konto. Dette giver brugeren adgang til Power BI tjeneste. Hvis f.eks. en medarbejder ved navn Nancy bruger sin arbejdsmailadresse (f.eks. Nancy@contoso.com) til at tilmelde sig, tilføjer Microsoft automatisk Nancy som bruger i Contoso Microsoft 365-miljøet og aktiverer Power BI for den pågældende konto.
  
### <a name="scenario-3-your-organization-does-not-have-a-microsoft-365-environment-connected-to-your-email-domain"></a>Scenarie 3: Organisationen har ikke et Microsoft 365 knyttet til dit maildomæne.

Der er ingen administrative handlinger, din organisation skal udføre for at udnytte Power BI.
  
> [!IMPORTANT]
> Hvis din organisation har flere maildomæner, og du foretrækker, at alle mailadresseudvidelser er i den samme lejer, skal du, før nogen brugere opretter din primære lejer, føje alle mailadressedomæner til den pågældende lejer, før nogen brugere opretter din primære lejer. Der er ingen automatisk mekanisme til at flytte brugere mellem lejere, efter de er blevet oprettet. Du kan finde flere oplysninger om denne proces under Hvis jeg har flere domæner, kan jeg så kontrollere den lejer, som brugerne [føjes til?](#if-i-have-multiple-domains-can-i-control-the-tenant-that-users-are-added-to) senere i denne artikel og Føje et domæne til [Office 365](../setup/add-domain.md) online.
  
## <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Hvordan vil dette ændre den måde, jeg administrerer identiteter for brugere på i min organisation i dag?

Hvis organisationen allerede har et eksisterende Microsoft 365- og alle brugere i organisationen har Microsoft 365 konti, ændres identitetsstyringen ikke.
  
Hvis organisationen allerede har et eksisterende Microsoft 365-miljø, men alle brugerne i organisationen ikke har Microsoft 365-konti, opretter vi en bruger i lejeren og tildeler licenser baseret på brugerens arbejds- eller skolemailadresse. Det betyder, at det antal brugere, du administrerer på et bestemt tidspunkt, vokser i efterhånden som brugerne i organisationen tilmelder sig tjenesten.
  
Hvis du administrerer dit katalog lokalt og bruger Active Directory Federation Services (AD FS), føjer Microsoft ikke brugere til din lejer, og brugere, der forsøger at tilslutte sig din lejer, modtager en meddelelse om at kontakte organisationens administrator.
  
Hvis din organisation ikke har et Microsoft 365-miljø, der er knyttet til dit maildomæne, ændres den måde, du administrerer identiteter på, ikke. Brugere føjes til et nyt brugerkatalog, der kun findes i skyen, og du får mulighed for at overtage styringen som lejeradministrator og administrere dem.
  
## <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Hvordan administreres en lejer, der er oprettet af Microsoft til mine brugere?

Hvis en lejer er oprettet af Microsoft, kan du gøre krav på og administrere lejeren ved at følge disse trin:
  
1. Tilmeld dig [lejeren ved at tilmelde dig Power BI](https://go.microsoft.com/fwlink/?LinkId=522448) bruger et mailadressedomæne, der svarer til det lejerdomæne, du vil administrere. Hvis Microsoft f.eks. har oprettet contoso.com-lejeren, skal du slutte dig til lejeren med en mailadresse, der slutter med @contoso.com.

1. Få administratorkontrol ved at bekræfte ejerskabet af domænet: Når du er i lejeren, kan du forfremme dig selv til administratorrollen ved at bekræfte ejerskabet af domænet. Det gør du ved at følge disse trin:

::: moniker range="o365-worldwide"

3. Gå til <a href="https://admin.microsoft.com" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

3. Gå til <a href="https://portal.partner.microsoftonline.cn" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end

4. Vælg ikonet for appstarteren øverst til venstre, og vælg **Administrator**.

    ![Appstarteren med administratorappen fremhævet.](../../media/4eea9dbc-591b-48be-9916-322d41c6525b.png)
  
5. Læs instruktionerne på **siden Bliv administrator** , og vælg **derefter Ja, jeg vil gerne være administrator**.

    > [!NOTE]
    >  Hvis denne indstilling ikke vises, er der allerede en administrator på plads.
  
## <a name="if-i-have-multiple-domains-can-i-control-the-tenant-that-users-are-added-to"></a>Hvis jeg har flere domæner, kan jeg så styre, hvem brugerne føjes til?

Hvis du ikke gør noget, oprettes der en lejer for hvert maildomæne og underdomæne til brugerne.
  
Hvis du ønsker, at alle brugere skal være i samme lejer uanset deres mailadresseudvidelse:
  
- Opret en mållejer i forvejen, eller brug en eksisterende lejer, og tilføj alle de eksisterende domæner og underdomæner, der skal samles i den pågældende lejer. Alle brugere med mailadresser, der slutter med disse domæner og underdomæner, sluttes herefter automatisk til denne lejer, når de tilmelder sig.

> [!IMPORTANT]
> Der er ingen understøttet automatisk mekanisme til at flytte brugere mellem lejere, når de først er blevet oprettet. Du kan få mere at vide om at føje domæner Microsoft 365 en enkelt lejer i [Føj et domæne Office 365](../setup/add-domain.md).

> [!IMPORTANT]
> Du kan finde flere oplysninger og vejledning til administration af lejere [i Hvad Power BI administration?](/power-bi/service-admin-administering-power-bi-in-your-organization).
  
## <a name="how-can-i-prevent-users-from-joining-my-existing-tenant"></a>Hvordan kan jeg forhindre brugere i at tilslutte sig min eksisterende lejer?

Som administrator kan du gøre følgende for at forhindre brugere i at tilslutte sig din eksisterende lejer. Hvis du blokerer brugeres tilmelding til lejeren, vil brugernes forsøg på at logge på mislykkes, og de vil blive omdirigeret til deres organisations administrator. Du behøver ikke at gentage denne proces, hvis du allerede har deaktiveret automatisk licensdistribution før (f.eks. Office 365 Education for studerende, fakultetsmedarbejdere og andet personale).
  
Disse trin kræver, at du bruger Windows PowerShell. Se introduktionsvejledningen Windows PowerShell [PowerShell for at komme i gang med programmet](/powershell/scripting/overview).
  
For at udføre følgende trin skal du installere den nyeste 64-bit version af [Azure Active Directory V2 PowerShell-modulet](https://www.powershellgallery.com/packages/AzureADPreview/2.0.2.5).
  
Når du har valgt linket, skal du **vælge Kør** for at køre installationspakken.
  
**Deaktiver automatisk lejerforbindelse**: Brug denne Windows PowerShell til at forhindre nye brugere i at tilslutte sig en administreret lejer:
  
Sådan deaktiverer du automatisk lejerforbindelse for nye brugere:  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $false`
  
Sådan aktiveres automatisk lejerforbindelse for nye brugere:  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $true`
  
> [!NOTE]
> Denne blokering forhindrer nye brugere i organisationen i at tilmelde sig Power BI. Brugere, der tilmelder sig Power BI, før nye tilmeldinger for organisationen deaktiveres, vil stadig bevare deres licenser. Se hvordan fjerner jeg [Power BI for](#how-do-i-remove-power-bi-for-users-that-already-signed-up) brugere, der allerede har tilmeldt sig? for at få en vejledning i, hvordan du kan fjerne adgangen til Power BI for brugere, der tidligere har tilmeldt sig tjenesten.
  
## <a name="how-can-i-allow-users-to-join-my-existing-tenant"></a>Hvordan kan jeg tillade brugere at tilslutte sig min eksisterende lejer?

For at give brugerne mulighed for at tilslutte sig din lejer skal du køre den modsatte kommando som beskrevet i spørgsmålet ovenfor:  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $true`
  
## <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>Hvordan kan jeg kontrollere, om blokeringen er i lejeren?

Brug følgende PowerShell-script:  `Get-MsolCompanyInformation | fl allow*`
  
## <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Hvordan kan jeg forhindre mine eksisterende brugere i at begynde at bruge Power BI?

**Deaktiver automatisk licensdistribution:** Brug dette Windows PowerShell til at deaktivere automatiske licensdistributioner for eksisterende brugere. Du behøver ikke at gentage denne proces, hvis du allerede har deaktiveret automatisk licensdistribution før (f.eks. Office 365 Education for studerende, fakultetsmedarbejdere og andet personale).
  
Sådan deaktiverer du automatisk licensdistribution for eksisterende brugere:  `Set-MsolCompanySettings -AllowAdHocSubscriptions $false`
  
Sådan aktiveres automatisk licensdistribution for eksisterende brugere:  `Set-MsolCompanySettings -AllowAdHocSubscriptions $true`
  
> [!NOTE]
> *Flaget AllowAdHocSubscriptions* bruges til at styre flere brugeregenskaber i organisationen, herunder muligheden for, at brugerne kan tilmelde sig Azure Rights Management Service. Hvis dette flag ændres, påvirkes alle disse funktioner.
  
## <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Hvordan kan jeg give mine eksisterende brugere tilladelse til at tilmelde sig Power BI?

For at give dine eksisterende brugere tilladelse til at tilmelde sig Power BI skal du køre den modsatte kommando som beskrevet i spørgsmålet ovenfor:`Set-MsolCompanySettings -AllowAdHocSubscriptions $true`
  
## <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Hvordan fjerner jeg oplysninger Power BI brugere, der allerede er tilmeldt?

Hvis en bruger har tilmeldt sig Power BI, men du ikke længere vil have, at brugeren skal have adgang til Power BI, kan du fjerne Power BI-licensen for den pågældende bruger.
  
::: moniker range="o365-worldwide"

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

::: moniker-end

::: moniker range="o365-21vianet"

 1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">for</a> brugere.

::: moniker-end

2. Find den bruger, du vil fjerne licensen for, og vælg derefter brugerens navn.

3. Fjern **markeringen i afkrydsningsfeltet** **Microsoft** Power BI fanen Licenser og apps.

4. Vælg **Gem ændringer**.

## <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Hvordan ved jeg, hvornår nye brugere har tilsluttet sig min lejer?

Brugere, der har tilsluttet sig din lejer som en del af dette program, tildeles en entydig licens, som du kan filtrere på i ruden med aktive brugere på administratordashboardet.
  
Hvis du vil oprette den nye visning, skal du i Administration følge trinnene i [Oprette en brugerdefineret brugervisning](../add-users/create-edit-or-delete-a-custom-user-view.md#create-a-custom-user-view). Under **Tildelt produktlicens skal** du **vælge Microsoft Power BI**. Når den nye visning er blevet oprettet, kan du se alle de brugere i din lejer, der har tilmeldt sig dette program.
  
## <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>Er der andre ting, jeg skal være forberedt på?

Du kan komme ud for flere anmodninger om nulstilling af adgangskoder. Du kan finde oplysninger om denne [proces i Nulstille en brugers adgangskode](../add-users/reset-passwords.md).
  
Du kan fjerne en bruger fra din lejer via standardprocessen i Administration. Men hvis brugeren stadig har en aktiv mailadresse fra organisationen, kan de tilmelde sig igen, medmindre du blokerer tilmelding fra alle brugere.
  
## <a name="why-did-1-million-licenses-for-microsoft-power-bi-show-up-in-my-tenant"></a>Hvorfor blev der vist 1 million licenser til Microsoft Power BI min lejer?

Som en kvalificerende organisation er brugerne i din organisation berettiget til at bruge Microsoft Power BI-tjenesten, og disse licenser repræsenterer den tilgængelige kapacitet for nye Power BI brugere i din lejer. Der er ingen gebyrer for disse licenser. Hvis du har valgt at give brugerne mulighed for selv at Power BI, får de tildelt en af disse tilgængelige gratis licenser, når de fuldfører tilmeldingsprocessen. Du kan også vælge selv at tildele disse licenser til brugerne via Administration.
  
## <a name="is-this-free-will-i-be-charged-for-these-licenses"></a>Er dette gratis? Skal jeg betale for disse licenser?

Disse licenser er til den gratis version af Power BI. Hvis du er interesseret i yderligere funktioner, kan du se nærmere på Power BI Pro version.
  
## <a name="why-1-million-licenses"></a>Hvorfor 1 million licenser?

Vi har valgt et antal, der var stort nok til, at størstedelen af organisationer ville have rigeligt med licenser til at kunne tilbyde denne fordel uden forsinkelse til deres brugere.
  
## <a name="what-if-i-need-more-than-1-million-licenses"></a>Hvad gør jeg, hvis jeg har brug for mere end 1 million licenser?

Kontakt din Microsoft-kunderepræsentant for at få flere oplysninger, hvis du skal købe flere licenser.