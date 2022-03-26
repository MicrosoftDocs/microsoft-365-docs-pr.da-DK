---
title: Opret og konfigurer opbevaringspolitikker til automatisk at bevare eller slette indhold
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
description: Brug en opbevaringspolitik til effektivt at holde styr på det indhold, som brugerne genererer med mail, dokumenter og samtaler. Behold det, du ønsker, og afvis det, du ikke ønsker.
ms.openlocfilehash: 94388a375c3c50d97e696637ef6ef4ebefc96aab
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63715487"
---
# <a name="create-and-configure-retention-policies"></a>Opret og konfigurer opbevaringspolitikker

>*[Microsoft 365 licenseringsvejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Brug en opbevaringspolitik til at administrere data for organisationen ved proaktivt at beslutte, om du vil bevare indhold, slette indhold eller bevare og derefter slette indholdet.

Med en opbevaringspolitik kan du gøre dette meget effektivt ved at tildele de samme opbevaringsindstillinger på objektbeholderniveau, der automatisk nedarves af indhold i den pågældende beholder. Eksempelvis alle elementer på SharePoint websteder, alle mails i brugernes postkasser Exchange, alle kanalmeddelelser for teams, der bruges Microsoft Teams. Hvis du ikke er sikker på, om du vil bruge en opbevaringspolitik på beholderniveau eller en opbevaringsetiket på elementniveau, skal du se Opbevaringspolitikker [og opbevaringsetiketter](retention.md#retention-policies-and-retention-labels).

Du kan finde flere oplysninger om opbevaringspolitikker, og hvordan opbevaring fungerer i Microsoft 365, i [Få mere at vide om opbevaringspolitikker og opbevaringsetiketter](retention.md).

> [!NOTE]
> Oplysningerne på denne side er til administratorer af overholdelse af regler og standarder. Hvis du ikke er administrator og vil have oplysninger om, hvordan opbevaringspolitikker er konfigureret for de apps, du bruger, skal du kontakte din helpdesk, it-afdeling eller administrator. Hvis du får vist meddelelser om opbevaringspolitikker i Teams chats og kanalmeddelelser, kan det være nyttigt at gennemse [Teams om opbevaringspolitikker](https://support.microsoft.com/office/teams-messages-about-retention-policies-c151fa2f-1558-4cf9-8e51-854e925b483b).

## <a name="before-you-begin"></a>Før du begynder

Den globale administrator i organisationen har fuld tilladelse til at oprette og redigere opbevaringspolitikker. Hvis du ikke logger på som global administrator, skal du se oplysninger [om tilladelser til informationsstyring](get-started-with-information-governance.md#permissions-for-retention-policies-and-retention-labels).

Beslut før du opretter din opbevaringspolitik, om den **vil være tilpasset** eller **statisk**. Få mere at vide under [Tilpasnings- eller statiske politikomfang for opbevaring](retention.md#adaptive-or-static-policy-scopes-for-retention). Hvis du beslutter dig for at bruge en tilpasset politik, skal du oprette et eller flere tilpassede områder, før du opretter din opbevaringspolitik, og derefter vælge dem under processen til oprettelse af en opbevaringspolitik. Du kan finde en vejledning [i Konfigurationsoplysninger for adaptive områder](retention-settings.md#configuration-information-for-adaptive-scopes).

## <a name="create-and-configure-a-retention-policy"></a>Opret og konfigurer en opbevaringspolitik

Selvom en opbevaringspolitik kan understøtte flere tjenester, der er identificeret som "placeringer" i opbevaringspolitikken, kan du ikke oprette en enkelt opbevaringspolitik, der omfatter alle de understøttede placeringer:

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

Hvis du vælger placeringerne Teams en Yammer, når du opretter en opbevaringspolitik, udelades de andre placeringer automatisk. Det betyder, at den vejledning, du skal følge, afhænger af, om du skal medtage Teams eller Yammer placeringer:

- [Vejledning til en opbevaringspolitik for Teams placeringer](#retention-policy-for-teams-locations)
- [Vejledning til en opbevaringspolitik for Yammer placeringer](#retention-policy-for-yammer-locations)
- [Vejledning til opbevaringspolitik for andre placeringer end Teams og Yammer](#retention-policy-for-locations-other-than-teams-and-yammer)

> [!NOTE]
> Når du bruger adaptive politikker i stedet for statiske politikker, kan du konfigurere en enkelt opbevaringspolitik, så den Teams og Yammer placeringer. Dette er ikke tilfældet for statiske politikker, hvor Teams og Yammer kræver deres egen opbevaringspolitik.

Når du har mere end én opbevaringspolitik, og når du også bruger opbevaringsetiketter, skal du se Principperne for opbevaring, eller hvad der skal have forrang [?](retention.md#the-principles-of-retention-or-what-takes-precedence) for at forstå resultatet, når flere opbevaringsindstillinger gælder for det samme indhold.

### <a name="retention-policy-for-teams-locations"></a>Opbevaringspolitik for Teams placeringer

> [!NOTE]
> Opbevaringspolitikker understøtter nu [delte kanaler](/MicrosoftTeams/shared-channels), der i øjeblikket er i forhåndsvisning. Når du konfigurerer opbevaringsindstillinger for **Teams** kanalmeddelelsesplaceringen, arver de opbevaringsindstillinger fra deres overordnede team, hvis et team har nogen delte kanaler.

1. Vælg [Microsoft 365 Overholdelsescenter politikker](https://compliance.microsoft.com/) **for informationsstyring** >  **på listen**.

2. Vælg **Ny opbevaringspolitik for** at starte Konfiguration **af Opret opbevaringspolitik** , og navngive din nye opbevaringspolitik.

3. For siden **Vælg den type opbevaringspolitik** , der skal oprettes skal du vælge **Tilpasset** eller **Statisk afhængigt** af det valg, du har foretaget fra vejledningen [Før du begynder](#before-you-begin) . Hvis du ikke allerede har oprettet tilpassede områder, kan du vælge Tilpasset, men  da der ikke vil være nogen tilpassede områder at vælge, kan du ikke afslutte konfigurationen med denne indstilling.

4. Afhængigt af det valgte område:
    
    - Hvis du vælger **Tilpasset**: På siden Vælg  tilpassede politikomfang og -placeringer skal du vælge Tilføj områder  og vælge et eller flere tilpassede områder, der er blevet oprettet. Vælg derefter en eller flere placeringer. De placeringer, du kan vælge, afhænger af de tilføjede [omfangstyper](retention-settings.md#configuration-information-for-adaptive-scopes) . Hvis du f.eks. kun har tilføjet en omfangstype af **bruger, kan** du vælge Teams **,** men ikke Teams **kanalmeddelelser**. 
    
    - Hvis du vælger **Statisk**: På **siden Vælg placeringer for at** anvende politikken skal du vælge en eller flere placeringer Teams:
        - **Teams kanalmeddelelse**: Meddelelser fra standardchats og delte kanalchats samt standard- og delte kanalmøder, men ikke fra [private](/microsoftteams/private-channels) kanaler, der har deres egen politikplacering.
        - **Teams chatsamtaler**: Beskeder fra private 1:1-chats, gruppechats og mødechats.
        - **Teams private kanalmeddelelser**: Beskeder fra private kanalchats og private kanalmøder.
        
       Som standard er [alle teams og alle brugere markeret](retention-settings.md#a-policy-that-applies-to-entire-locations), men du kan finjustere dette ved at vælge [**indstillingerne Vælg** **og Udelad**](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).

5. Ud **for Beslut, om du vil** bevare indhold, slette det eller begge sider, skal du angive konfigurationsindstillingerne for at bevare og slette indhold.

   Du kan oprette en opbevaringspolitik, der kun bevarer indhold uden at slette, bevarer og derefter sletter efter en bestemt tidsperiode eller blot sletter indhold efter en bestemt tidsperiode. Du kan finde flere oplysninger [Indstillinger oplysninger om at bevare og slette indhold](retention-settings.md#settings-for-retaining-and-deleting-content).

6. Fuldfør konfigurationen, og gem dine indstillinger.

Du kan finde en vejledning til, hvornår du kan bruge opbevaringspolitikker til Teams og forstå slutbrugeroplevelsen i Administrere opbevaringspolitikker [for Microsoft Teams](/microsoftteams/retention-policies) fra Teams dokumentationen.

Hvis du vil have tekniske oplysninger om, hvordan opbevaring fungerer for Teams, herunder hvilke elementer af meddelelser, der understøttes til opbevaring og tidsindstillinger med eksempler på gennemgange, skal du se Få mere at vide om opbevaring [for Microsoft Teams](retention-policies-teams.md).

#### <a name="known-configuration-issues"></a>Kendte konfigurationsproblemer

- Selvom du kan vælge at starte opbevaringsperioden, når elementer sidst blev ændret, så bruges værdien af Hvornår **elementer** blev oprettet altid. For meddelelser, der er redigeret, gemmes en kopi af den oprindelige meddelelse med dens oprindelige tidsstempel for at identificere, hvornår denne redigerede meddelelse blev oprettet, og den redigerede meddelelse har et nyere tidsstempel.

- Når du vælger **Rediger** for placeringen Teams chats, får du muligvis vist gæster og brugere uden postkasse. Opbevaringspolitikker er ikke udviklet til disse brugere, så du skal ikke markere dem.


#### <a name="additional-retention-policy-needed-to-support-teams"></a>Yderligere opbevaringspolitik er nødvendig for at Teams

Teams er mere end blot chats og kanalmeddelelser. Hvis du har teams, der er oprettet fra en Microsoft 365-gruppe (tidligere Office 365-gruppe), skal du desuden konfigurere en opbevaringspolitik, der omfatter Microsoft 365-gruppen, ved hjælp af placeringen **Microsoft 365 Grupper**. Denne opbevaringspolitik gælder for indhold i gruppens postkasse, websted og filer.

Hvis du har teamwebsteder, der ikke er knyttet til en Microsoft 365-gruppe, skal du have en opbevaringspolitik, der omfatter **placeringerne SharePoint-websteder** eller **OneDrive-konti** for at kunne opbevare og slette filer i Teams:

- Filer, der deles i chat, gemmes på OneDrive for den bruger, der har delt filen.

- Filer, der er overført til kanaler, gemmes SharePoint teamets websted.

> [!TIP]
> Du kan anvende en opbevaringspolitik på kun et bestemt teams filer, når den ikke har forbindelse til en Microsoft 365-gruppe, ved at vælge SharePoint-webstedet for teamet og OneDrive-konti for brugere i teamet.

Det er muligt, at en opbevaringspolitik, der anvendes på Microsoft 365-grupper, SharePoint-websteder eller OneDrive-konti, kan slette en fil, der refereres til i en Teams-chat eller kanalmeddelelse, før disse meddelelser slettes. I dette scenarie vises filen stadig i dialogboksen Teams, men når brugerne vælger filen, får de fejlmeddelelsen "Filen blev ikke fundet". Denne funktionsmåde er ikke specifik for opbevaringspolitikker og kan også opstå, hvis en bruger manuelt sletter en fil SharePoint eller OneDrive.

### <a name="retention-policy-for-yammer-locations"></a>Opbevaringspolitik for Yammer placeringer

> [!NOTE]
> Opbevaringspolitikker for Yammer er i forhåndsvisning og giver i øjeblikket ikke brugerne besked, når meddelelser slettes som et resultat af en opbevaringspolitik.
>
> Hvis du vil bruge denne funktion, Yammer dit netværk være [indbygget tilstand](/yammer/configure-your-yammer-network/overview-native-mode) og ikke hybridtilstand.

1. Vælg [Microsoft 365 Overholdelsescenter politikker](https://compliance.microsoft.com/) **for informationsstyring** >  **på listen**.

2. Vælg **Ny opbevaringspolitik for** at oprette en ny opbevaringspolitik.

3. For siden **Vælg den type opbevaringspolitik** , der skal oprettes skal du vælge **Tilpasset** eller **Statisk afhængigt** af det valg, du har foretaget fra vejledningen [Før du begynder](#before-you-begin) . Hvis du ikke allerede har oprettet tilpassede områder, kan du vælge Tilpasset, men  da der ikke vil være nogen tilpassede områder at vælge, kan du ikke afslutte konfigurationen med denne indstilling.

4. Afhængigt af det valgte område:
    
    - Hvis du vælger **Tilpasset**: På siden Vælg  tilpassede politikomfang og -placeringer skal du vælge Tilføj områder  og vælge et eller flere tilpassede områder, der er blevet oprettet. Vælg derefter en eller flere placeringer. De placeringer, du kan vælge, afhænger af de tilføjede [omfangstyper](retention-settings.md#configuration-information-for-adaptive-scopes) . Hvis du f.eks. kun har tilføjet en omfangstype af **bruger, kan** du vælge en **Yammer,** men ikke Yammer **gruppemeddelelser**. 
    
    - Hvis **du vælger Statisk**: På siden  Vælg placeringer for at anvende politikken skal du vælge en eller begge placeringer for Yammer: **Yammer-communitymeddelelse** **og Yammer-brugermeddelelser**.
        
        > [!IMPORTANT]
        > Selvom du kan oprette en opbevaringspolitik kun til Yammer brugermeddelelser, kan en opbevaringspolitik for denne placering slette communitymeddelelser fra Yammer-appen for alle communitymedlemmer.
        > 
        > Hvis du vælger denne indstilling, og opbevaringspolitikken konfigureres til at slette brugermeddelelser, skal du sikre dig, at du forstår dette. Få mere at vide under [Sådan fungerer opbevaring med Yammer](retention-policies-yammer.md#how-retention-works-with-yammer).
        
        Som standard vælges alle communities og brugere, men du kan finjustere dette ved at angive grupper og brugere, der skal medtages eller udelades.
        
        For Yammer om brugermeddelelser: 
        - Hvis du lader standardindstillingen være **Alle brugere**, er Azure B2B-gæstebrugere ikke inkluderet. 
        - Hvis du vælger **Rediger** for **alle brugere**, kan du anvende en opbevaringspolitik på eksterne brugere, hvis du kender deres konto.

5. Ud **for Beslut, om du vil** bevare indhold, slette det eller begge sider, skal du angive konfigurationsindstillingerne for at bevare og slette indhold. 
    
    Du kan oprette en opbevaringspolitik, der kun bevarer indhold uden at slette, bevarer og derefter sletter efter en bestemt tidsperiode eller blot sletter indhold efter en bestemt tidsperiode. Du kan finde flere oplysninger [Indstillinger oplysninger om at bevare og slette indhold](retention-settings.md#settings-for-retaining-and-deleting-content).

6. Fuldfør konfigurationen, og gem dine indstillinger.

Du kan finde flere oplysninger om, hvordan opbevaringspolitikker fungerer for Yammer, i [Få mere at vide om opbevaring Yammer](retention-policies-yammer.md).

#### <a name="additional-retention-policies-needed-to-support-yammer"></a>Yderligere opbevaringspolitikker er nødvendige for at understøtte Yammer

Yammer er mere end blot communitymeddelelser og private meddelelser. Hvis du vil bevare og slette mails til dit Yammer-netværk, skal du konfigurere en ekstra opbevaringspolitik, der omfatter alle Microsoft 365-grupper, der bruges til Yammer, ved hjælp af placeringen **Microsoft 365 Grupper**. 

Hvis du vil bevare og slette filer, der er gemt i Yammer, skal du have en opbevaringspolitik, der omfatter placeringen **Microsoft 365 grupper** eller **OneDrive-kontoplaceringer**:

- Filer, der deles i private meddelelser, gemmes på OneDrive den bruger, der har delt filen. 

- Filer, der overføres til community'er, gemmes i gruppens forbundne SharePoint-webstedet for Yammer community'et.

Det er muligt, at en opbevaringspolitik, der anvendes på SharePoint-websteder eller OneDrive-konti, kan slette en fil, der refereres til i en Yammer-meddelelse, før disse meddelelser slettes. I dette scenarie vises filen stadig i dialogboksen Yammer, men når brugerne vælger filen, får de fejlmeddelelsen "Filen blev ikke fundet". Denne funktionsmåde er ikke specifik for opbevaringspolitikker og kan også opstå, hvis en bruger manuelt sletter en fil SharePoint eller OneDrive.

### <a name="retention-policy-for-locations-other-than-teams-and-yammer"></a>Opbevaringspolitik for andre placeringer end Teams og Yammer

Brug følgende vejledning til opbevaringspolitikker, der gælder for en af disse tjenester:

- Exchange: Mail og offentlige mapper
- SharePoint: Websteder
- OneDrive: Konti
- Microsoft 365 grupper
- Skype for Business

1. Vælg [Microsoft 365 Overholdelsescenter politikker](https://compliance.microsoft.com/) **for informationsstyring** >  **på listen**.

2. Vælg **Ny opbevaringspolitik for** at starte Konfiguration **af Opret opbevaringspolitik** , og navngive din nye opbevaringspolitik.

3. For siden **Vælg den type opbevaringspolitik** , der skal oprettes skal du vælge **Tilpasset** eller **Statisk afhængigt** af det valg, du har foretaget fra vejledningen [Før du begynder](#before-you-begin) . Hvis du ikke allerede har oprettet tilpassede områder, kan du vælge Tilpasset, men  da der ikke vil være nogen tilpassede områder at vælge, kan du ikke afslutte konfigurationen med denne indstilling. Adaptive politikker understøtter ikke placeringer for Exchange offentlige mapper eller Skype for Business.

4. Afhængigt af det valgte område:
    
    - Hvis du vælger **Tilpasset**: På siden Vælg  tilpassede politikomfang og -placeringer skal du vælge Tilføj områder  og vælge et eller flere tilpassede områder, der er blevet oprettet. Vælg derefter en eller flere placeringer. De placeringer, du kan vælge, afhænger af de tilføjede [omfangstyper](retention-settings.md#configuration-information-for-adaptive-scopes) . Hvis du f.eks. kun har tilføjet en omfangstype af **bruger, kan** du vælge Exchange **,** men ikke SharePoint **websteder**. 
    
    - Hvis du vælger **Statisk**: På siden  Vælg placeringer skal du slå en af placeringerne til eller fra undtagen placeringer for Teams og Yammer. For hver placering kan du lade den være som standard for at anvende politikken på hele [placeringen eller angive](retention-settings.md#a-policy-that-applies-to-entire-locations) [omfatter og udelader](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions).
    
    Oplysninger, der er specifikke for placeringer:
    - [Exchange mail og Exchange offentlige mapper](retention-settings.md#configuration-information-for-exchange-email-and-exchange-public-folders)
    - [SharePoint websteder og OneDrive-konti](retention-settings.md#configuration-information-for-sharepoint-sites-and-onedrive-accounts)
    - [Microsoft 365 grupper](retention-settings.md#configuration-information-for-microsoft-365-groups)
    - [Skype for Business](retention-settings.md#configuration-information-for-skype-for-business)

5. Ud **for Beslut, om du vil** bevare indhold, slette det eller begge sider, skal du angive konfigurationsindstillingerne for at bevare og slette indhold.
    
    Du kan oprette en opbevaringspolitik, der kun bevarer indhold uden at slette, bevarer og derefter sletter efter en bestemt tidsperiode eller blot sletter indhold efter en bestemt tidsperiode. Du kan finde flere [oplysninger Indstillinger oplysninger om at bevare og slette indhold](retention-settings.md#settings-for-retaining-and-deleting-content) på denne side.

6. Fuldfør konfigurationen, og gem dine indstillinger.

## <a name="how-long-it-takes-for-retention-policies-to-take-effect"></a>Hvor lang tid det tager at opbevaringspolitikkerne træder i kraft

Når du opretter og indsender en opbevaringspolitik, kan det tage op til syv dage, før opbevaringspolitikken anvendes:
  
![Diagram over, hvornår opbevaringspolitikken træder i kraft.](../media/retention-policy-timings.png)

For det første skal opbevaringspolitikken fordeles til de placeringer, du har valgt, og derefter anvendes den på indholdet. Du kan altid kontrollere opbevaringspolitikkens distributionsstatus ved at vælge den på siden **Opbevaringspolitikker** i Overholdelsescenter. Hvis (Fejl **)** er inkluderet i status i pop op-ruden med pop-op-vinduet, får du vist en meddelelse om, at det tager længere tid end forventet at implementere politikken, eller hvis du vil prøve at implementere politikken igen, kan du prøve at køre kommandoen [Set-AppRetentionCompliancePolicy](/powershell/module/exchange/set-appretentioncompliancepolicy) eller [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell for at prøve politikfordelingen igen:

1. [Forbind til Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell).

2. Kør en af følgende kommandoer:
    
    - Du kan se **politikplaceringerne Teams private kanalmeddelelser**, Yammer **brugermeddelelser** **og Yammer-communitymeddelelser**:
    
        ```PowerShell
        Set-AppRetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```
    
    - For alle andre politikplaceringer, f.eks. **Exchange mail**, **SharePoint** websteder og **Teams kanalmeddelelser**:
    
        ```PowerShell
        Set-RetentionCompliancePolicy -Identity <policy name> -RetryDistribution
        ```

## <a name="updating-retention-policies"></a>Opdatering af opbevaringspolitikker

Når indstillingerne fra opbevaringspolitikken allerede anvendes på indhold, vil en ændring i konfigurationen af politikken automatisk blive anvendt på dette indhold ud over indhold, der er identificeret for nylig.

Nogle indstillinger kan ikke ændres, når politikken er oprettet og gemt, hvilket omfatter navnet på opbevaringspolitikken, omfangstypen (tilpasset eller statisk) og opbevaringsindstillingerne undtagen opbevaringsperioden.

## <a name="next-steps"></a>Næste trin

Hvis nogle elementer til Exchange, SharePoint, OneDrive eller Microsoft 365 Grupper har brug for andre opbevaringsindstillinger end de indstillinger for opbevaringspolitik, du har konfigureret, skal du oprette [opbevaringsnavne for](create-retention-labels-information-governance.md) disse undtagelser.

Men hvis du leder efter administration af livscyklus for elementer af høj værdi til forretningsmæssige, juridiske eller lovgivningsmæssige krav til registrering, kan du [](file-plan-manager.md)bruge filplan til at oprette og administrere opbevaringsmærkater.
