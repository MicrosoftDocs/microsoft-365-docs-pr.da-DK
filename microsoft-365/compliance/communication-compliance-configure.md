---
title: Kom i gang med kommunikationsoverholdelse
description: Konfigurer politikker for overholdelse af kommunikation for at konfigurere brugerkommunikation til gennemsyn.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, kommunikation
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: cd7ff5819f2d3927c9315e96b440a215a6e889eb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633757"
---
# <a name="get-started-with-communication-compliance"></a>Kom i gang med kommunikationsoverholdelse

Brug politikker for overholdelse af kommunikation til at identificere brugerkommunikation, der skal undersøges af interne eller eksterne korrekturlæsere. Du kan finde flere oplysninger om, hvordan politikker for kommunikation med overholdelse af angivne standarder kan hjælpe dig med at registrere kommunikation i din organisation, under [Politikker for kommunikation med overholdelse af angivne standarder](communication-compliance.md). Hvis du vil gennemgå, hvordan Contoso hurtigt konfigurerede en politik for overholdelse af angivne standarder for kommunikation for at registrere upassende indhold i Microsoft Teams, Exchange Online og Yammer-kommunikation, kan du se dette [casestudie](communication-compliance-case-study.md).

## <a name="subscriptions-and-licensing"></a>Abonnementer og licenser

Før du kommer i gang med overholdelse af angivne standarder for kommunikation, skal du bekræfte dit [Microsoft 365-abonnement](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) og eventuelle tilføjelsesprogrammer. Din organisation skal have et af følgende abonnementer eller tilføjelsesprogrammer for at få adgang til og bruge overholdelse af kommunikation:

- Microsoft 365 E5/A5/F5/G5-abonnement (betalt version eller prøveversion)
- Microsoft 365 E3/A3/F3/G5-abonnement + tilføjelsesprogrammet Microsoft 365 E5/A5/F5/G5 Compliance
- Microsoft 365 E3/A3/F3/G5-abonnement + tilføjelsesprogrammet Microsoft 365 E5/A5/F5/G5 Insider Risk Management
- Office 365 Enterprise E5-abonnement (betalt version eller prøveversion)
- Office 365 A5 abonnement (betalt version eller prøveversion)
- Office 365 Enterprise E3-abonnement + tilføjelsesprogrammet Avanceret overholdelse i Office 365 (ikke længere tilgængeligt for nye abonnementer, se note)

Brugere, der er inkluderet i politikker for kommunikation med overholdelse af angivne standarder, skal tildeles en af licenserne ovenfor. Du kan finde flere oplysninger om abonnementer og licenser under [Vejledning til sikkerhed & overholdelse af angivne standarder i Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> Kommunikationsoverholdelse er i øjeblikket tilgængelig i lejere, der hostes i geografiske områder og lande, der understøttes af Azure-tjenesteafhængigheder. Hvis du vil kontrollere, at overholdelse af angivne standarder for kommunikation understøttes for din organisation, skal du se [Tilgængelighed af Azure-afhængighed efter land/område](/troubleshoot/azure/general/dependency-availability-by-country).

Hvis du ikke har en eksisterende Office 365 Enterprise E5-plan og vil prøve overholdelse af angivne standarder for kommunikation, kan du [føje Microsoft 365](/office365/admin/try-or-buy-microsoft-365) til dit eksisterende abonnement eller [tilmelde dig en prøveversion](https://www.microsoft.com/microsoft-365/enterprise) af Office 365 Enterprise E5.

> [!NOTE]
> Avanceret overholdelse i Office 365 sælges ikke længere som et separat abonnement. Når de aktuelle abonnementer udløber, skal kunderne overgå til et af abonnementerne ovenfor, som indeholder de samme eller yderligere funktioner til overholdelse af angivne standarder.

## <a name="recommended-actions"></a>Anbefalede handlinger

Anbefalede handlinger kan hjælpe din organisation med at komme i gang med funktioner til overholdelse af kommunikation og få mest muligt ud af dine eksisterende politikker. Inkluderet på siden **Politikker** giver anbefalede handlinger indsigt og opsummerer følsomme informationstyper og upassende indholdsaktiviteter i kommunikation i din organisation. Indsigt understøttes af [dataklassificering](data-classification-overview.md) og anvendelse af følsomhedsmærkater, opbevaringsmærkater og klassificering af følsomme oplysninger. Disse indsigter omfatter ikke nogen personidentificerbare oplysninger for brugere i din organisation.

![Handlinger, der anbefales i forbindelse med kommunikation med overholdelse af angivne standarder.](../media/communication-compliance-recommended-actions.png)

Aktivitet i meddelelser, der indeholder upassende indhold, samles efter [klassificeringstype](/microsoft-365/compliance/communication-compliance-policies#classifiers) fra eksisterende politikker, der bruger den upassende indholdsskabelon eller brugerdefinerede politikker, der bruger klassificeringer til upassende indhold. Undersøg beskeder for disse meddelelser på dashboardet Vigtig besked for dine politikker.

Aktivitet, der involverer [følsomme oplysningstyper](/microsoft-365/compliance/communication-compliance-policies#sensitive-information-types) , registreres i meddelelser, der er omfattet af eksisterende politikker, og for meddelelser, der ikke er omfattet af eksisterende politikker. Indsigter samles for alle følsomme informationstyper, herunder dem, som din organisation ikke tidligere har defineret i en eksisterende politik for overholdelse af angivne standarder for kommunikation. Brug denne indsigt til at oprette en ny politik for overholdelse af angivne standarder for kommunikation eller til at opdatere eksisterende politikker.

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>Trin 1 (påkrævet): Aktivér tilladelser til kommunikation med overholdelse af angivne standarder

> [!IMPORTANT]
> Når du har konfigureret dine rollegrupper, kan det tage op til 30 minutter, før rollegruppens tilladelser gælder for tildelte brugere på tværs af organisationen.

Der er seks rollegrupper, der bruges til at konfigurere de første tilladelser til at administrere funktioner til kommunikation med overholdelse af angivne standarder. Hvis du vil gøre **Overholdelse af kommunikation** tilgængelig som en menuindstilling i Microsoft Purview-compliance-portal og fortsætte med disse konfigurationstrin, skal du være tildelt en af følgende roller eller rollegrupper:

- Rolle som global Azure Active [*Directory-administrator*](/azure/active-directory/roles/permissions-reference#global-administrator)
- [*Rolle som Azure Active Directory-overholdelsesadministrator*](/azure/active-directory/roles/permissions-reference#compliance-administrator)
- Microsoft Purview-compliance-portal [*rollegruppe for organisationsadministration*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- rollegruppe for Microsoft Purview-compliance-portal [*overholdelsesadministrator*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- *Rollegruppe for kommunikation med overholdelse af angivne standarder*
- Administration rollegruppe for *kommunikationoverholdelse*

Medlemmer af følgende roller har de samme løsningstilladelser, der er inkluderet i rollegruppen *Kommunikationsoverholdelse Administration*:

- Global Azure Active *Directory-administrator*
- Azure Active Directory *Compliance Administrator*
- Microsoft Purview-compliance-portal *organisationsstyring*
- Microsoft Purview-compliance-portal *overholdelsesadministrator*

> [!IMPORTANT]
> Sørg for, at du altid har mindst én bruger i rollegrupperne *Communication Compliance* eller *Communication Compliance Administration* (afhængigt af den indstilling, du vælger), så konfigurationen af kommunikationsoverholdelse ikke kommer ind i et scenarie med "nul administrator", hvis bestemte brugere forlader din organisation.

Afhængigt af hvordan du vil administrere politikker og beskeder om overholdelse af kommunikation, skal du tildele brugere til bestemte rollegrupper for at administrere forskellige sæt funktioner til kommunikation med overholdelse af angivne standarder. Du har mulighed for at tildele brugere med forskellige overholdelsesansvar til bestemte rollegrupper for at administrere forskellige områder af funktioner til kommunikation med overholdelse af angivne standarder. Du kan også vælge at tildele alle brugerkonti for udpegede administratorer, analytikere, efterforskere og seere til rollegruppen *Kommunikationsoverholdelse* . Brug en enkelt rollegruppe eller flere rollegrupper, så de passer bedst til dine krav til administration af overholdelse.

Vælg mellem disse indstillinger for løsningsrollegruppen, når du konfigurerer og administrerer kommunikation med overholdelse af angivne standarder:

| Rolle | Rolletilladelser |
|:-----|:-----------------|
| **Kommunikation med overholdelse af angivne standarder** | Brug denne rollegruppe til at administrere overholdelse af kommunikation for din organisation i en enkelt gruppe. Ved at tilføje alle brugerkonti for udpegede administratorer, analytikere, efterforskere og seere kan du konfigurere tilladelser til kommunikation med overholdelse af angivne standarder i en enkelt gruppe. Denne rollegruppe indeholder alle tilladelser til kommunikation med overholdelse af angivne standarder. Denne konfiguration er den nemmeste måde hurtigt at komme i gang med overholdelse af angivne standarder for kommunikation på, og den er velegnet til organisationer, der ikke har brug for separate tilladelser, der er defineret for separate grupper af brugere. Brugere, der opretter politikker som administrator af kommunikationsoverholdelse, skal have deres postkasse hostet på Exchange Online.|
| **Administration for overholdelse af angivne standarder for kommunikation** | Brug denne rollegruppe til først at konfigurere overholdelse af kommunikation og senere til at adskille administratorer af kommunikation med overholdelse af angivne standarder i en defineret gruppe. Brugere, der er tildelt denne rollegruppe, kan oprette, læse, opdatere og slette politikker for kommunikation med overholdelse af angivne standarder, globale indstillinger og tildelinger af rollegrupper. Brugere, der er tildelt denne rollegruppe, kan ikke få vist meddelelsesbeskeder. Brugere, der opretter politikker som administrator af kommunikationsoverholdelse, skal have deres postkasse hostet på Exchange Online.|
| **Kommunikationsoverholdelsesanalytiker** | Brug denne gruppe til at tildele tilladelser til brugere, der fungerer som analytikere af kommunikation med overholdelse af angivne standarder. Brugere, der er tildelt til denne rollegruppe, kan få vist politikker, hvor de er tildelt som korrekturlæsere, få vist meddelelsesmetadata (ikke meddelelsesindhold), eskalere til yderligere korrekturlæsere eller sende meddelelser til brugere. Analytikere kan ikke løse ventende beskeder. |
| **Efterforsker af kommunikation med overholdelse af angivne standarder** | Brug denne gruppe til at tildele tilladelser til brugere, der fungerer som undersøgere af kommunikation med overholdelse af angivne standarder. Brugere, der er tildelt denne rollegruppe, kan få vist meddelelsesmetadata og indhold, eskalere til yderligere korrekturlæsere, eskalere til en eDiscovery (Premium)-sag, sende meddelelser til brugere og løse beskeden. |
| **Meddelelsesoverholdelsesfremviser** | Brug denne gruppe til at tildele tilladelser til brugere, der skal administrere kommunikationsrapporter. Brugere, der er tildelt denne rollegruppe, kan få adgang til alle rapporteringswidgets på startsiden for kommunikation med overholdelse af angivne standarder og kan få vist alle rapporter om kommunikation med overholdelse af angivne standarder. |

### <a name="option-1-assign-all-compliance-users-to-the-communication-compliance-role-group"></a>Mulighed 1: Tildel alle brugere af overholdelse af angivne standarder til rollegruppen Kommunikationsoverholdelse

1. [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) Log på med legitimationsoplysninger for en administratorkonto i din Microsoft 365-organisation.

2. I Security &amp; Compliance Center skal du gå til **Tilladelser**. Vælg linket for at få vist og administrere roller i Office 365.

3. Vælg rollegruppen *Kommunikationsoverholdelse* , og vælg derefter **Rediger rollegruppe**.

4. Vælg **Vælg medlemmer** i navigationsruden til venstre, og vælg derefter **Rediger**.

5. Vælg **Tilføj** , og markér derefter afkrydsningsfeltet for alle de brugere, du vil føje til rollegruppen *Kommunikationsoverholdelse* .

6. Vælg **Tilføj**, og vælg derefter **Udført**.

7. Vælg **Gem** for at føje brugerne til rollegruppen. Vælg **Luk** for at fuldføre trinnene

### <a name="option-2-assign-users-to-specific-communication-compliance-role-groups"></a>Mulighed 2: Tildel brugere til bestemte rollegrupper for overholdelse af kommunikationsoverholdelse

Brug denne indstilling til at tildele brugere til bestemte rollegrupper til at segmentere adgang til og ansvar for overholdelse af angivne standarder for kommunikation mellem forskellige brugere i din organisation.

1. Log på [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365-organisation, og gå derefter til **Tilladelser**</a>.

2. Vælg linket for at få vist og administrere roller i Office 365.

3. Vælg en af rollegrupperne for kommunikation med overholdelse af angivne standarder, og vælg derefter **Rediger rollegruppe**.

4. Vælg **Vælg medlemmer** i navigationsruden til venstre, og vælg derefter **Rediger**.

5. Vælg **Tilføj** , og markér derefter afkrydsningsfeltet for alle de brugere, du vil føje til rollegruppen.

6. Vælg **Tilføj**, og vælg derefter **Udført**.

7. Vælg **Gem** for at føje brugerne til rollegruppen.

8. Vælg den næste rollegruppe for overholdelse af kommunikation, og gentag derefter trin 4-7 for hver påkrævet rollegruppe.

9. Vælg **Luk** for at fuldføre trinnene.

Du kan få flere oplysninger om rollegrupper og tilladelser [under Tilladelser i Overholdelsescenter](../security/office-365-security/protect-against-threats.md).

## <a name="step-2-required-enable-the-audit-log"></a>Trin 2 (påkrævet): Aktivér overvågningsloggen

Kommunikationsoverholdelse kræver overvågningslogge for at vise beskeder og spore afhjælpningshandlinger, der udføres af korrekturlæsere. Overvågningsloggene er en oversigt over alle aktiviteter, der er knyttet til en defineret organisationspolitik, eller når en politik for kommunikation med overholdelse af regler og standarder ændres.

Overvågning er som standard aktiveret for Microsoft 365-organisationer. Nogle organisationer kan have deaktiveret overvågning af bestemte årsager. Hvis overvågning er deaktiveret for din organisation, kan det skyldes, at en anden administrator har deaktiveret den. Vi anbefaler, at du bekræfter, at det er OK at aktivere overvågning igen, når du fuldfører dette trin.

Du kan finde en trinvis vejledning til, hvordan du slår overvågning til, under [Slå søgning i overvågningslog til eller fra](turn-audit-log-search-on-or-off.md). Når du har slået overvågning til, vises der en meddelelse om, at overvågningsloggen er ved at blive forberedt, og at du kan køre en søgning om et par timer, efter at forberedelsen er fuldført. Du behøver kun at gøre denne handling én gang. Du kan finde flere oplysninger om, hvordan du bruger overvågningsloggen, [under Søg i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>Trin 3 (valgfrit): Konfigurer grupper til overholdelse af kommunikation

 Når du opretter en politik for overholdelse af angivne standarder for kommunikation, definerer du, hvem der har gennemgået deres kommunikation, og hvem der udfører korrekturer. I politikken skal du bruge mailadresser til at identificere enkeltpersoner eller grupper af personer. For at forenkle konfigurationen kan du oprette grupper for personer, der har gennemgået deres kommunikation, og grupper for personer, der gennemser denne kommunikation. Hvis du bruger grupper, har du muligvis brug for flere. Hvis du f.eks. vil registrere kommunikation mellem to forskellige grupper af personer, eller hvis du vil angive en gruppe, der ikke overvåges.

Brug følgende diagram til at hjælpe dig med at konfigurere grupper i din organisation til politikker for kommunikation med overholdelse af angivne standarder:

| **Politikmedlem** | **Understøttede grupper** | **Ikke-understøttede grupper** |
|:-----|:-----|:-----|
|Overvågede brugere <br> Udeladte brugere | Distributionsgrupper <br> Microsoft 365-grupper | Dynamiske distributionsgrupper <br> Indlejrede distributionsgrupper <br> Mailaktiverede sikkerhedsgrupper <br> Microsoft 365-grupper med dynamisk medlemskab |
| Korrekturlæsere | Ingen | Distributionsgrupper <br> Dynamiske distributionsgrupper <br> Indlejrede distributionsgrupper <br> Mailaktiverede sikkerhedsgrupper |

Når du tildeler en *distributionsgruppe* i politikken, overvåger politikken alle mails og Teams-chats fra hver bruger i *distributionsgruppen*. Når du tildeler en *Microsoft 365-gruppe* i politikken, registrerer politikken alle mails og Teams-chats, der sendes til *Microsoft 365-gruppen**, ikke de enkelte mails og chats, der modtages af hvert gruppemedlem. Brug af distributionsgrupper i politikker for overholdelse af kommunikation anbefales, så individuelle mails og Teams-chats fra hver bruger overvåges automatisk.

Hvis du er en organisation med en Exchange-installation i det lokale miljø eller en ekstern mailudbyder, og du vil registrere Microsoft Teams-chats for dine brugere, skal du oprette en distributionsgruppe, som brugerne med lokale eller eksterne postkasser kan overvåge. Senere i disse trin skal du tildele denne distributionsgruppe som valg af **overvågede brugere og grupper** i politikguiden. Du kan finde flere oplysninger om kravene og begrænsningerne for aktivering af skybaseret lager og Teams-understøttelse for brugere i det lokale miljø under [Søg efter Teams-chatdata for brugere i det lokale miljø](search-cloud-based-mailboxes-for-on-premises-users.md).

Hvis du vil administrere overvågede brugere i store virksomhedsorganisationer, skal du muligvis overvåge alle brugere på tværs af store grupper. Du kan bruge PowerShell til at konfigurere en distributionsgruppe for en global politik for overholdelse af kommunikation for den tildelte gruppe. Dette giver dig mulighed for at overvåge tusindvis af brugere med en enkelt politik og holde politikken for kommunikation med overholdelse af angivne standarder opdateret, efterhånden som nye medarbejdere tilmelder sig din organisation.

1. Opret en dedikeret [distributionsgruppe](/powershell/module/exchange/new-distributiongroup) for din globale politik for overholdelse af angivne standarder for kommunikation med følgende egenskaber: Sørg for, at denne distributionsgruppe ikke bruges til andre formål eller andre Office 365 tjenester.

    - **MemberDepartRestriction = Lukket**. Sikrer, at brugerne ikke kan fjerne sig selv fra distributionsgruppen.
    - **MemberJoinRestriction = Lukket**. Sikrer, at brugerne ikke kan føje sig selv til distributionsgruppen.
    - **ModerationEnabled = Sand**. Sikrer, at alle meddelelser, der sendes til denne gruppe, er underlagt godkendelse, og at gruppen ikke bruges til at kommunikere uden for konfigurationen af politikken for kommunikation med overholdelse af angivne standarder.

    ```PowerShell
    New-DistributionGroup -Name <your group name> -Alias <your group alias> -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true
    ```

2. Vælg en [ubrugt brugerdefineret Exchange-attribut](/Exchange/recipients/mailbox-custom-attributes) for at spore brugere, der er føjet til politikken for kommunikation med overholdelse af angivne standarder i din organisation.

3. Kør følgende PowerShell-script efter en tilbagevendende tidsplan for at føje brugere til politikken for kommunikation med overholdelse af angivne standarder:

    ```PowerShell
    $Mbx = (Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited -Filter {CustomAttribute9 -eq $Null})
    $i = 0
    ForEach ($M in $Mbx)
    {
      Write-Host "Adding" $M.DisplayName
      Add-DistributionGroupMember -Identity <your group name> -Member $M.DistinguishedName -ErrorAction SilentlyContinue
      Set-Mailbox -Identity $M.Alias -<your custom attribute name> SRAdded
      $i++
    }
    Write-Host $i "Mailboxes added to supervisory review distribution group."
    ```

Du kan få flere oplysninger om konfiguration af grupper under:

- [Opret og administrer distributionsgrupper](/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Oversigt over Microsoft 365-grupper](/office365/admin/create-groups/office-365-groups)

## <a name="step-4-optional-verify-your-yammer-tenant-is-in-native-mode"></a>Trin 4 (valgfrit): Kontrollér, at din Yammer-lejer er i oprindelig tilstand

I oprindelig tilstand er alle Yammer-brugere i Azure Active Directory (Azure AD), alle grupper er Office 365 grupper, og alle filer gemmes i SharePoint Online. Din Yammer-lejer skal være i oprindelig tilstand for politikker for overholdelse af kommunikation for at scanne og identificere risikable samtaler i private meddelelser og communitysamtaler i Yammer.

Du kan få flere oplysninger om konfiguration af Yammer i oprindelig tilstand under:

- [Oversigt over Oprindelig Yammer-tilstand i Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode)
- [Konfigurer dit Yammer-netværk til oprindelig tilstand til Microsoft 365](/yammer/configure-your-yammer-network/native-mode)

## <a name="step-5-required-create-a-communication-compliance-policy"></a>Trin 5 (påkrævet): Opret en politik for kommunikation med overholdelse af angivne standarder

>[!IMPORTANT]
>Brug af PowerShell til at oprette og administrere politikker for kommunikation med overholdelse af angivne standarder understøttes ikke. Hvis du vil oprette og administrere disse politikker, skal du bruge kontrolelementerne til administration af politikker i [kommunikationsoverholdelsesløsningen](https://compliance.microsoft.com/supervisoryreview).

>[!TIP]  
>Vil du se en detaljeret gennemgang af, hvordan du konfigurerer en ny politik for overholdelse af angivne standarder for kommunikation og afhjælper en besked? Se [denne 15-minutters video](communication-compliance-plan.md#creating-a-communication-compliance-policy-walkthrough) for at se en demonstration af, hvordan politikker for kommunikation med overholdelse af angivne standarder kan hjælpe dig med at registrere upassende meddelelser, undersøge potentielle overtrædelser og afhjælpe problemer med overholdelse af angivne standarder.

1. Log på [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365-organisation.

2. Vælg **Kommunikation med overholdelse af angivne standarder** i Microsoft Purview-compliance-portal.

3. Vælg fanen **Politikker** .

4. Vælg **Opret politik** for at oprette og konfigurere en ny politik fra en skabelon eller for at oprette og konfigurere en brugerdefineret politik.

    Hvis du vælger en politikskabelon til at oprette en politik, skal du:

    - Bekræft eller opdater politiknavnet. Politiknavne kan ikke ændres, når politikken er oprettet.

    - Vælg de brugere eller grupper, der skal overvåges, herunder valg af brugere eller grupper, du vil udelade. Når du bruger skabelonen interessekonflikt, skal du vælge to grupper eller to brugere, der skal overvåges for intern kommunikation.

    - Vælg korrekturlæserne for politikken. Korrekturlæsere er individuelle brugere, og alle korrekturlæsere skal have postkasser, der hostes på Exchange Online. De korrekturlæsere, der tilføjes her, er de korrekturlæsere, du kan vælge imellem, når du eskalerer en besked i undersøgelses- og afhjælpningsarbejdsprocessen. Når validatorer føjes til en politik, modtager de automatisk en mail, der giver dem besked om tildelingen til politikken og indeholder links til oplysninger om korrekturprocessen.

    - Vælg et felt med begrænsede betingelser, som normalt er en følsom infotype eller nøgleordsordbog, der skal anvendes på politikken.

    > [!NOTE]
    > Hvis du vil aktivere [optisk tegngenkendelse (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) for at scanne integrerede eller vedhæftede billeder i meddelelser til trykt eller håndskrevet tekst, der svarer til politikbetingelser, skal du vælge **Tilpas politikbetingelser** > **og procentdel** og aktivere **Udtræk trykt eller håndskrevet tekst fra billeder til evaluering**.

    Hvis du vælger at bruge politikguiden til at oprette en brugerdefineret politik, skal du gøre følgende:

    - Giv politikken et navn og en beskrivelse. Politiknavne kan ikke ændres, når politikken er oprettet.

    - Vælg de brugere eller grupper, der skal overvåges, herunder alle brugere i organisationen, bestemte brugere og grupper eller andre brugere og grupper, du vil ekskludere.

    - Vælg korrekturlæserne for politikken. Korrekturlæsere er individuelle brugere, og alle korrekturlæsere skal have postkasser, der hostes på Exchange Online. De korrekturlæsere, der tilføjes her, er de korrekturlæsere, du kan vælge imellem, når du eskalerer en besked i undersøgelses- og afhjælpningsarbejdsprocessen. Når validatorer føjes til en politik, modtager de automatisk en mail, der giver dem besked om tildelingen til politikken og indeholder links til oplysninger om korrekturprocessen.

    - Vælg de kommunikationskanaler, der skal scannes, herunder Exchange, Microsoft Teams eller Yammer. Du kan også vælge at scanne tredjepartskilder, hvis du har konfigureret en connector i Microsoft 365.

    - Vælg kommunikationsretningen for at registrere, herunder indgående, udgående eller intern kommunikation.

    - Definer betingelserne for politikken for kommunikation med overholdelse af [regler og standarder](communication-compliance-policies.md#ConditionalSettings). Du kan vælge mellem betingelser for meddelelsesadresse, nøgleord, filtyper og størrelsesmatch.

    - Vælg, om du vil medtage følsomme oplysningstyper. I dette trin kan du vælge standardtyper og brugerdefinerede følsomme oplysninger. Vælg mellem eksisterende brugerdefinerede typer følsomme oplysninger eller brugerdefinerede nøgleordsordbøger i guiden til kommunikation med overholdelse af regler og standarder. Du kan oprette disse elementer, før du kører guiden, hvis det er nødvendigt. Du kan også oprette nye typer følsomme oplysninger fra guiden til kommunikation med overholdelse af regler og standarder.

    - Vælg, om du vil aktivere klassificeringer. Klassificeringer kan registrere upassende sprog og billeder, der sendes eller modtages i brødteksten i mails eller andre typer tekst. Du kan vælge følgende indbyggede klassificeringer: *Threat*, *Profanity*, *Målrettet chikane*, *Voksenbilleder*, *Racy-billeder* og *Gory-billeder*.

    - Aktivér [optisk tegngenkendelse (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) for at scanne integrerede eller vedhæftede billeder i meddelelser for trykt eller håndskrevet tekst, der opfylder politikbetingelserne. I forbindelse med brugerdefinerede politikker skal en eller flere betingede indstillinger, der er knyttet til tekst, nøgleord, klassificeringer eller følsomme infotyper, konfigureres i politikken for at muliggøre valg af scanning af optisk tegngenkendelse.

    - Definer den procentdel af kommunikationen, der skal gennemses.

    - Gennemse dine politikvalg, og opret politikken.

5. Vælg **Opret politik** , når du bruger skabelonerne eller **Send** , når du bruger guiden brugerdefineret politik.

6. Siden **Din politik blev oprettet** vises med retningslinjer for, hvornår politikken aktiveres, og hvilken kommunikation der registreres.

## <a name="step-6-optional-update-compliance-boundaries-for-communication-compliance-policies"></a>Trin 6 (valgfrit): Opdater overholdelsesgrænser for kommunikationspolitikker

[Overholdelsesgrænser](/microsoft-365/compliance/set-up-compliance-boundaries) opretter logiske grænser i en organisation, der styrer placeringen af brugerindhold (f.eks. postkasser, OneDrive-konti og SharePoint-websteder), som eDiscovery-ledere kan søge i.

Hvis du har konfigureret overholdelsesgrænser i din organisation, skal du opdatere overholdelsesgrænserne for at give visse brugere adgang til postkasser, der understøtter politikker for kommunikation med overholdelse af angivne standarder. Du skal tillade adgang til administratorer af overholdelse af kommunikation og brugere af overholdelse af angivne standarder, så din politikstyring og undersøgelses- og afhjælpningshandlinger kan fungere korrekt.

Kør følgende PowerShell-kommandoer for at give administratorer og korrekturlæsere adgang til kommunikation. Du skal kun køre disse kommandoer én gang, selvom du tilføjer nye politikker for kommunikation med overholdelse af angivne standarder i fremtiden:

```powershell
Import-Module ExchangeOnlineManagement
$UserCredential = Get-Credential
Connect-IPPSSession -Credential $UserCredential
New-ComplianceSecurityFilter -FilterName "CC_mailbox" -Users <list your communication compliance admins and reviewers user alias or email address> -Filters "Mailbox_Name -like 'SupervisoryReview{*'" -Action All
```

Du kan få flere oplysninger om [cmdlet-syntaks under New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter).

## <a name="step-7-optional-create-notice-templates-and-configure-user-anonymization"></a>Trin 7 (valgfrit): Opret meddelelsesskabeloner, og konfigurer brugeranonymisering

Hvis du vil have mulighed for at svare på en politikbesked ved at sende en påmindelsesmeddelelse til den tilknyttede bruger, skal du oprette mindst én skabelon for meddelelser i din organisation. Meddelelsesskabelonfelterne kan redigeres, før de sendes som en del af afhjælpningsprocessen for beskeder, og det anbefales at oprette en brugerdefineret meddelelsesskabelon for hver politik for kommunikation med overholdelse af angivne standarder.

Du kan også vælge at aktivere anonymisering for viste brugernavne, når du undersøger politikforekomster og udfører handlinger på meddelelser.

1. Log på [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) ved hjælp af legitimationsoplysninger for en administratorkonto i din Microsoft 365-organisation.

2. I Microsoft Purview-compliance-portal skal du gå til **Kommunikation med overholdelse af angivne standarder**.

3. Hvis du vil konfigurere anonymisering for brugernavne, skal du vælge fanen **Beskyttelse af personlige oplysninger** .

4. Hvis du vil aktivere anonymisering, skal du vælge **Vis anonymiserede versioner af brugernavne**.

5. Vælg **Gem**.

6. Gå til fanen **Meddelelsesskabeloner** , og vælg derefter **Opret meddelelsesskabelon**.

7. På siden **Rediger en meddelelsesskabelon** skal du udfylde følgende felter:

    - Skabelonnavn (påkrævet)
    - Send fra (påkrævet)
    - Cc og Bcc (valgfrit)
    - Emne (påkrævet)
    - Meddelelsestekst (påkrævet)

8. Vælg **Gem** for at oprette og gemme meddelelsesskabelonen.

## <a name="step-8-optional-test-your-communication-compliance-policy"></a>Trin 8 (valgfrit): Test politikken for overholdelse af angivne standarder for kommunikation

Når du har oprettet en politik for overholdelse af angivne standarder for kommunikation, er det en god idé at teste den for at sikre, at de betingelser, du har defineret, håndhæves korrekt af politikken. Det kan også være en god idé at [teste dine DLP-politikker (Microsoft Purview Forebyggelse af datatab),](create-test-tune-dlp-policy.md) hvis politikkerne for kommunikation med overholdelse af angivne standarder omfatter følsomme oplysningstyper. Sørg for, at du giver dine politikker tid til at aktivere, så den kommunikation, du vil teste, registreres.

Følg disse trin for at teste politikken for overholdelse af angivne standarder for kommunikation:

1. Åbn en mailklient, Microsoft Teams eller Yammer, mens du er logget på som en overvåget bruger, der er defineret i den politik, du vil teste.

2. Send en mail, Microsoft Teams-chat eller Yammer-meddelelse, der opfylder de kriterier, du har defineret i politikken for kommunikation med overholdelse af angivne standarder. Denne test kan være et nøgleord, størrelse på vedhæftede filer, domæne osv. Sørg for, at du finder ud af, om dine konfigurerede betingede indstillinger i politikken er for restriktive eller for milde.

    > [!NOTE]
    > Det kan tage ca. 24 timer, før mails behandles fuldt ud i en politik. Kommunikation i Microsoft Teams, Yammer og tredjepartsplatforme kan tage ca. 48 timer at behandle fuldt ud i en politik.

3. Log på Microsoft 365 som en korrekturlæser, der er angivet i politikken for kommunikation med overholdelse af angivne standarder. Gå til **Meddelelser om** **overholdelse af angivne standarder** >  Beskeder for at få vist beskederne for dine politikker.

4. Afhjælp beskeden ved hjælp af afhjælpningskontrolelementerne, og kontrollér, at beskeden er korrekt løst.

## <a name="next-steps"></a>Næste trin

Når du har fuldført disse trin for at oprette din første politik for overholdelse af angivne standarder for kommunikation, begynder du at modtage beskeder fra aktivitetsindikatorer efter 24-48 timer. Konfigurer yderligere politikker efter behov ved hjælp af vejledningen i trin 5 i denne artikel.

Hvis du vil vide mere om undersøgelse af beskeder om kommunikation med overholdelse af angivne standarder, skal du se [Undersøg og afhjælp beskeder om kommunikation med overholdelse af angivne standarder](communication-compliance-investigate-remediate.md).

Hvis du vil holde dig ajour med de seneste opdateringer af kommunikationsoverholdelse, skal du vælge **Nyheder** i [overholdelse af kommunikation](https://compliance.microsoft.com/) for din organisation.
