---
title: Bevar eller slet indhold automatisk ved hjælp af opbevaringspolitikker
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Brug en opbevaringspolitik til effektivt at bevare kontrollen over det indhold, som brugerne genererer med mail, dokumenter og samtaler. Hold hvad du vil og slippe af med, hvad du ikke gør.
ms.openlocfilehash: 7b8ca4e909893ec417d3466f825c2c0a1c5c736a
ms.sourcegitcommit: f302de988d98628922eea1f509a3f639634ddc64
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/17/2022
ms.locfileid: "66151178"
---
# <a name="create-and-configure-retention-policies"></a>Opret og konfigurer opbevaringspolitikker

>*[Microsoft 365 licensvejledning til sikkerhed & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Brug en opbevaringspolitik til at administrere dataene for din organisation ved proaktivt at beslutte, om du vil bevare indhold, slette indhold eller gemme og derefter slette indholdet.

Med en opbevaringspolitik kan du gøre dette meget effektivt ved at tildele de samme opbevaringsindstillinger på objektbeholderniveau, der automatisk nedarves af indhold i den pågældende objektbeholder. For eksempel alle elementer på SharePoint websteder, alle mails i brugernes Exchange postkasser, alle kanalmeddelelser for teams, der bruges sammen med Microsoft Teams. Hvis du ikke er sikker på, om du vil bruge en opbevaringspolitik på objektbeholderniveau eller en opbevaringsmærkat på elementniveau, skal du se [Opbevaringspolitikker og opbevaringsmærkater](retention.md#retention-policies-and-retention-labels).

Du kan finde flere oplysninger om opbevaringspolitikker, og hvordan opbevaring fungerer i Microsoft 365, under [Få mere at vide om opbevaringspolitikker og opbevaringsmærkater](retention.md).

> [!NOTE]
> Oplysningerne på denne side er til overholdelsesadministratorer. Hvis du ikke er administrator og gerne vil forstå, hvordan opbevaringspolitikker er konfigureret for de apps, du bruger, skal du kontakte din helpdesk, it-afdeling eller administrator. Hvis du får vist meddelelser om opbevaringspolitikker i Teams chats og kanalmeddelelser, kan det være nyttigt at gennemse [Teams meddelelser om opbevaringspolitikker](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

## <a name="before-you-begin"></a>Før du begynder

Den globale administrator for din organisation har fuld tilladelse til at oprette og redigere opbevaringspolitikker. Hvis du ikke logger på som global administrator, kan du se [oplysninger om tilladelser til administration af datalivscyklus](get-started-with-data-lifecycle-management.md#permissions-for-retention-policies-and-retention-labels).

Beslut, før du opretter din opbevaringspolitik, om den skal være **adaptiv** eller **statisk**. Du kan finde flere oplysninger under [Tilpassede eller statiske politikområder for opbevaring](retention.md#adaptive-or-static-policy-scopes-for-retention). Hvis du beslutter dig for at bruge en tilpasset politik, skal du oprette et eller flere tilpassede områder, før du opretter din opbevaringspolitik og derefter vælger dem under processen til oprettelse af opbevaringspolitik. Du kan finde en vejledning under [Konfigurationsoplysninger for tilpassede områder](retention-settings.md#configuration-information-for-adaptive-scopes).

## <a name="create-and-configure-a-retention-policy"></a>Opret og konfigurer en opbevaringspolitik

Selvom en opbevaringspolitik kan understøtte flere tjenester, der er identificeret som "placeringer" i opbevaringspolitikken, kan du ikke oprette en enkelt opbevaringspolitik, der indeholder alle de understøttede placeringer:

- Exchange mail
- SharePoint websted
- OneDrive konti
- Microsoft 365 grupper
- Skype for Business
- Exchange offentlige mapper
- Teams kanalmeddelelser
- Teams chats
- Teams private kanalmeddelelser
- Yammer communitymeddelelser
- Yammer brugermeddelelser

Hvis du vælger de Teams eller Yammer placeringer, når du opretter en opbevaringspolitik, udelades de andre placeringer automatisk. Det betyder, at de instruktioner, der skal følges, afhænger af, om du skal inkludere de Teams eller Yammer placeringer:

- [Instruktioner til en opbevaringspolitik for Teams placeringer](#retention-policy-for-teams-locations)
- [Instruktioner til en opbevaringspolitik for Yammer placeringer](#retention-policy-for-yammer-locations)
- [Instruktioner til en opbevaringspolitik for andre placeringer end Teams og Yammer](#retention-policy-for-locations-other-than-teams-and-yammer)

> [!NOTE]
> Når du bruger tilpassede politikker i stedet for statiske politikker, kan du konfigurere en enkelt opbevaringspolitik, så den omfatter både Teams og Yammer placeringer. Dette er ikke tilfældet for statiske politikker, hvor Teams og Yammer placeringer kræver deres egen opbevaringspolitik.

Når du har mere end én opbevaringspolitik, og når du også bruger opbevaringsmærkater, skal du se [Principperne for opbevaring, eller hvad har forrang?](retention.md#the-principles-of-retention-or-what-takes-precedence) for at forstå resultatet, når der gælder flere opbevaringsindstillinger for det samme indhold.

### <a name="retention-policy-for-teams-locations"></a>Opbevaringspolitik for Teams placeringer

> [!NOTE]
> Opbevaringspolitikker understøtter nu [delte kanaler](/MicrosoftTeams/shared-channels), der i øjeblikket er en prøveversion. Når du konfigurerer opbevaringsindstillinger for **placeringen af Teams kanalmeddelelsen**, nedarver de opbevaringsindstillinger fra deres overordnede team, hvis et team har delte kanaler.

1. Vælg **Opbevaringspolitikker** for **datalivscyklusstyring** >  i [Microsoft Purview-compliance-portal](https://compliance.microsoft.com/).

2. Vælg **Ny opbevaringspolitik** for at starte konfigurationen **Opret opbevaringspolitik** , og navngiv din nye opbevaringspolitik.

3. På siden **Vælg den type opbevaringspolitik, der skal oprettes** skal du vælge **Adaptiv** eller **Statisk** afhængigt af det valg, du har foretaget i vejledningen [Før du starter](#before-you-begin) . Hvis du ikke allerede har oprettet tilpassede områder, kan du vælge **Adaptivt** , men fordi der ikke er nogen tilpassede områder at vælge, kan du ikke fuldføre konfigurationen med denne indstilling.

4. Afhængigt af dit valgte område:
    
    - Hvis du vælger **Adaptiv**: På siden **Vælg tilpassede politikområder og -placeringer** skal du vælge **Tilføj områder** og vælge et eller flere tilpassede områder, der er blevet oprettet. Vælg derefter en eller flere placeringer. De placeringer, du kan vælge, afhænger af de [tilføjede områdetyper](retention-settings.md#configuration-information-for-adaptive-scopes) . Hvis du f.eks. kun har tilføjet områdetypen **Bruger**, kan du vælge **Teams chats**, men ikke **Teams kanalmeddelelser**. 
    
    - Hvis du vælger **Statisk**: Vælg en eller flere placeringer for Teams på siden **Vælg placeringer, hvor politikken skal anvendes**:
        - **Teams kanalmeddelelse**: Meddelelser fra almindelige og delte kanalchats samt standard- og delte kanalmøder, men ikke fra [private kanaler](/microsoftteams/private-channels), der har deres egen politikplacering.
        - **Teams chats**: Meddelelser fra private 1:1-chats, gruppechats og mødechats.
        - **Teams private kanalmeddelelser**: Meddelelser fra private kanalchats og private kanalmøder.
        
       Som standard [er alle teams og alle brugere valgt](retention-settings.md#a-policy-that-applies-to-entire-locations), men du kan tilpasse dette ved at vælge [indstillingerne **Vælg** og **Udelad**](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).

5. For **Beslut, om du vil bevare indhold, slette det eller begge** sider, skal du angive konfigurationsindstillingerne for at bevare og slette indhold.

   Du kan oprette en opbevaringspolitik, der kun bevarer indhold uden at slette, bevare og derefter slette efter et angivet tidsrum eller blot slette indhold efter et angivet tidsrum. Du kan få flere oplysninger [under Indstillinger til at bevare og slette indhold](retention-settings.md#settings-for-retaining-and-deleting-content).

6. Fuldfør konfigurationen, og gem dine indstillinger.

Hvis du vil have hjælp til, hvornår du skal bruge opbevaringspolitikker til Teams og forstå slutbrugeroplevelsen, skal du se [Administrer opbevaringspolitikker for Microsoft Teams](/microsoftteams/retention-policies) i dokumentationen til Teams.

Du kan finde tekniske oplysninger om, hvordan opbevaring fungerer for Teams, herunder hvilke elementer i meddelelser der understøttes for oplysninger om opbevaring og tidsindstillinger med eksempelgennemgange, under [Få mere at vide om opbevaring for Microsoft Teams](retention-policies-teams.md).

#### <a name="known-configuration-issues"></a>Kendte konfigurationsproblemer

- Selvom du kan vælge indstillingen for at starte opbevaringsperioden, da elementerne sidst blev ændret, bruges værdien af **Når elementer blev oprettet** altid. For meddelelser, der redigeres, gemmes en kopi af den oprindelige meddelelse med det oprindelige tidsstempel for at identificere, hvornår denne forudredigeringsmeddelelse blev oprettet, og den postredigeringerede meddelelse har et nyere tidsstempel.

- Når du vælger **Rediger** for den Teams chatplacering, kan du se gæster og brugere, der ikke har postkasse. Opbevaringspolitikker er ikke udviklet til disse brugere, så vælg dem ikke.


#### <a name="additional-retention-policy-needed-to-support-teams"></a>Yderligere opbevaringspolitik, der er nødvendig for at understøtte Teams

Teams er mere end blot chats og kanalmeddelelser. Hvis du har teams, der er oprettet ud fra en Microsoft 365 gruppe (tidligere Office 365 gruppe), skal du desuden konfigurere en opbevaringspolitik, der omfatter den pågældende Microsoft 365 gruppe, ved hjælp af **den Microsoft 365-grupper** placering. Denne opbevaringspolitik gælder for indhold i gruppens postkasse, websted og filer.

Hvis du har teamwebsteder, der ikke har forbindelse til en Microsoft 365 gruppe, skal du have en opbevaringspolitik, der indeholder **de SharePoint websteder** eller **OneDrive kontoplaceringer** for at gemme og slette filer i Teams:

- Filer, der deles i chat, gemmes på den OneDrive konto for den bruger, der har delt filen.

- Filer, der uploades til kanaler, gemmes på teamets SharePoint websted.

> [!TIP]
> Du kan anvende en opbevaringspolitik på filerne for et bestemt team, når det ikke har forbindelse til en Microsoft 365 gruppe, ved at vælge teamets SharePoint websted og de OneDrive konti for brugere i teamet.

Det er muligt, at en opbevaringspolitik, der anvendes på Microsoft 365 grupper, SharePoint websteder eller OneDrive konti, kan slette en fil, der henvises til i en Teams chat- eller kanalmeddelelse, før disse meddelelser slettes. I dette scenarie vises filen stadig i Teams meddelelse, men når brugerne vælger filen, får de vist fejlen "Filen blev ikke fundet". Denne funktionsmåde er ikke specifik for opbevaringspolitikker, og det kan også ske, hvis en bruger sletter en fil manuelt fra SharePoint eller OneDrive.

### <a name="retention-policy-for-yammer-locations"></a>Opbevaringspolitik for Yammer placeringer

> [!NOTE]
> Opbevaringspolitikker for Yammer informerer i øjeblikket ikke brugerne, når meddelelser slettes som følge af en opbevaringspolitik.
>
> Hvis du vil bruge denne funktion, skal dit Yammer netværk være [oprindelig tilstand](/yammer/configure-your-yammer-network/overview-native-mode) og ikke hybridtilstand.

1. Vælg **Opbevaringspolitikker** for **datalivscyklusstyring** >  i [Microsoft Purview-compliance-portal](https://compliance.microsoft.com/).

2. Vælg **Ny opbevaringspolitik** for at oprette en ny opbevaringspolitik.

3. På siden **Vælg den type opbevaringspolitik, der skal oprettes** skal du vælge **Adaptiv** eller **Statisk** afhængigt af det valg, du har foretaget i vejledningen [Før du starter](#before-you-begin) . Hvis du ikke allerede har oprettet tilpassede områder, kan du vælge **Adaptivt** , men fordi der ikke er nogen tilpassede områder at vælge, kan du ikke fuldføre konfigurationen med denne indstilling.

4. Afhængigt af dit valgte område:
    
    - Hvis du vælger **Adaptiv**: På siden **Vælg tilpassede politikområder og -placeringer** skal du vælge **Tilføj områder** og vælge et eller flere tilpassede områder, der er blevet oprettet. Vælg derefter en eller flere placeringer. De placeringer, du kan vælge, afhænger af de [tilføjede områdetyper](retention-settings.md#configuration-information-for-adaptive-scopes) . Hvis du f.eks. kun har tilføjet områdetypen **Bruger**, kan du vælge **Yammer brugermeddelelser**, men ikke **Yammer communitymeddelelser**. 
    
    - Hvis du vælger **Statisk**: På siden **Vælg placeringer, hvor politikken skal anvendes, skal** du slå den ene eller begge placeringer for Yammer til: **Yammer communitymeddelelse** og **Yammer brugermeddelelser**.
        
        Som standard er alle communities og brugere valgt, men du kan tilpasse dette ved at angive communities og brugere, der skal medtages eller udelades.
        
        For Yammer brugermeddelelser: 
        - Hvis du forlader standarden hos **Alle brugere**, er Azure B2B-gæstebrugere ikke inkluderet. 
        - Hvis du vælger **Rediger** for **alle brugere**, kan du anvende en opbevaringspolitik på eksterne brugere, hvis du kender deres konto.

5. For **Beslut, om du vil bevare indhold, slette det eller begge** sider, skal du angive konfigurationsindstillingerne for at bevare og slette indhold. 
    
    Du kan oprette en opbevaringspolitik, der kun bevarer indhold uden at slette, bevare og derefter slette efter et angivet tidsrum eller blot slette indhold efter et angivet tidsrum. Du kan få flere oplysninger [under Indstillinger til at bevare og slette indhold](retention-settings.md#settings-for-retaining-and-deleting-content).

6. Fuldfør konfigurationen, og gem dine indstillinger.

Du kan finde flere oplysninger om, hvordan opbevaringspolitikker fungerer for Yammer, under [Få mere at vide om opbevaring for Yammer](retention-policies-yammer.md).

#### <a name="additional-retention-policies-needed-to-support-yammer"></a>Yderligere opbevaringspolitikker, der er nødvendige for at understøtte Yammer

Yammer er mere end blot communitymeddelelser og private meddelelser. Hvis du vil bevare og slette mails for dit Yammer netværk, skal du konfigurere en yderligere opbevaringspolitik, der omfatter alle Microsoft 365 grupper, der bruges til Yammer, ved hjælp af **den Microsoft 365-grupper** placering.

Denne placering omfatter også filer, der uploades til Yammer communities. Disse filer gemmes på det gruppetilsluttede SharePoint websted for Yammer community'et.

Det er muligt, at en opbevaringspolitik, der anvendes på SharePoint websteder, kan slette en fil, der refereres til i en Yammer meddelelse, før disse meddelelser slettes. I dette scenarie vises filen stadig i meddelelsen Yammer, men når brugerne vælger filen, får de vist fejlen "Filen blev ikke fundet". Denne funktionsmåde er ikke specifik for opbevaringspolitikker og kan også ske, hvis en bruger sletter en fil manuelt fra SharePoint.

### <a name="retention-policy-for-locations-other-than-teams-and-yammer"></a>Opbevaringspolitik for andre placeringer end Teams og Yammer

Brug følgende instruktioner til opbevaringspolitikker, der gælder for en af disse tjenester:

- Exchange: Mail og offentlige mapper
- SharePoint: Websteder
- OneDrive: Konti
- Microsoft 365 grupper
- Skype for Business

1. Vælg **Opbevaringspolitikker** for **datalivscyklusstyring** >  i [Microsoft Purview-compliance-portal](https://compliance.microsoft.com/).

2. Vælg **Ny opbevaringspolitik** for at starte konfigurationen **Opret opbevaringspolitik** , og navngiv din nye opbevaringspolitik.

3. På siden **Vælg den type opbevaringspolitik, der skal oprettes** skal du vælge **Adaptiv** eller **Statisk** afhængigt af det valg, du har foretaget i vejledningen [Før du starter](#before-you-begin) . Hvis du ikke allerede har oprettet tilpassede områder, kan du vælge **Adaptivt** , men fordi der ikke er nogen tilpassede områder at vælge, kan du ikke fuldføre konfigurationen med denne indstilling. Tilpassede politikker understøtter ikke placeringer for Exchange offentlige mapper eller Skype for Business.

4. Afhængigt af dit valgte område:
    
    - Hvis du vælger **Adaptiv**: På siden **Vælg tilpassede politikområder og -placeringer** skal du vælge **Tilføj områder** og vælge et eller flere tilpassede områder, der er blevet oprettet. Vælg derefter en eller flere placeringer. De placeringer, du kan vælge, afhænger af de [tilføjede områdetyper](retention-settings.md#configuration-information-for-adaptive-scopes) . Hvis du f.eks. kun har tilføjet områdetypen **Bruger**, kan du vælge **Exchange mail**, men ikke **SharePoint websteder**. 
    
    - Hvis du vælger **Statisk**: På siden **Vælg placeringer** skal du slå en af placeringerne til eller fra undtagen placeringerne for Teams og Yammer. For hver placering kan du lade den være som standard for at [anvende politikken på hele placeringen](retention-settings.md#a-policy-that-applies-to-entire-locations) eller [angive "include" og "excludes](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions)".
    
    Oplysninger, der er specifikke for placeringer:
    - [Exchange mail og Exchange offentlige mapper](retention-settings.md#configuration-information-for-exchange-email-and-exchange-public-folders)
    - [SharePoint websteder og OneDrive konti](retention-settings.md#configuration-information-for-sharepoint-sites-and-onedrive-accounts)
    - [Microsoft 365-grupper](retention-settings.md#configuration-information-for-microsoft-365-groups)
    - [Skype for Business](retention-settings.md#configuration-information-for-skype-for-business)

5. For **Beslut, om du vil bevare indhold, slette det eller begge** sider, skal du angive konfigurationsindstillingerne for at bevare og slette indhold.
    
    Du kan oprette en opbevaringspolitik, der kun bevarer indhold uden at slette, bevare og derefter slette efter et angivet tidsrum eller blot slette indhold efter et angivet tidsrum. Du kan få flere oplysninger [under Indstillinger til at bevare og slette indhold](retention-settings.md#settings-for-retaining-and-deleting-content) på denne side.

6. Fuldfør konfigurationen, og gem dine indstillinger.

## <a name="how-long-it-takes-for-retention-policies-to-take-effect"></a>Hvor lang tid det tager for opbevaringspolitikker at træde i kraft

Når du opretter og sender en opbevaringspolitik, kan det tage op til syv dage, før opbevaringspolitikken anvendes:
  
![Diagram over, hvornår opbevaringspolitikken træder i kraft.](../media/retention-policy-timings.png)

Først skal opbevaringspolitikken distribueres til de placeringer, du har valgt, og derefter anvendes på indhold. Du kan altid kontrollere distributionsstatussen for opbevaringspolitikken ved at vælge den på siden **Opbevaringspolitikker** i Microsoft Purview-compliance-portal. Hvis du i pop op-vinduet får vist **(Fejl),** der er inkluderet i status, og i oplysningerne om placeringerne vises en meddelelse om, at det tager længere tid end forventet at installere politikken eller at prøve at geninstallere politikken, kan du prøve at køre Kommandoen [Set-AppRetentionCompliancePolicy](/powershell/module/exchange/set-appretentioncompliancepolicy) eller [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) for at forsøge at distribuere politikken igen:

1. [Forbind til PowerShell til sikkerhed & overholdelse af angivne standarder](/powershell/exchange/connect-to-scc-powershell).

2. Kør en af følgende kommandoer:
    
    - For politikplaceringerne **Teams private kanalmeddelelser** **skal du Yammer brugermeddelelser** og **Yammer communitymeddelelser**:
    
        ```PowerShell
        Set-AppRetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```
    
    - For alle andre politikplaceringer, f.eks. **Exchange mail**, **SharePoint websteder** og **Teams kanalmeddelelser**:
    
        ```PowerShell
        Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```

## <a name="updating-retention-policies"></a>Opdaterer opbevaringspolitikker

Når indstillinger fra opbevaringspolitikken allerede anvendes på indhold, anvendes der automatisk en ændring i konfigurationen af politikken for dette indhold ud over indhold, der er blevet identificeret for nylig.

Nogle indstillinger kan ikke ændres, når politikken er oprettet og gemt, hvilket omfatter navnet på opbevaringspolitikken, områdetypen (adaptiv eller statisk) og opbevaringsindstillingerne undtagen opbevaringsperioden.

## <a name="next-steps"></a>Næste trin

Hvis nogle elementer til Exchange, SharePoint, OneDrive eller Microsoft 365-grupper har brug for andre opbevaringsindstillinger end de indstillinger for opbevaringspolitik, du har konfigureret, skal du [oprette opbevaringsmærkater for disse undtagelser](create-retention-labels-data-lifecycle-management.md).

Men hvis du gerne vil administrere elementer af høj værdi for forretningsrelaterede, juridiske eller lovmæssige krav til registrering, [skal du bruge filplanen til at oprette og administrere opbevaringsmærkater](file-plan-manager.md).
