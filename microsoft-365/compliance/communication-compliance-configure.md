---
title: Kom i gang med kommunikationsoverholdelse
description: Konfigurer politikker for overholdelse af kommunikation for at konfigurere brugerkommunikation til gennemsyn.
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
ms.openlocfilehash: d9d418cee35976e621c173b3563b04ee8bdce7ca
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/01/2022
ms.locfileid: "64595296"
---
# <a name="get-started-with-communication-compliance"></a>Kom i gang med kommunikationsoverholdelse

Brug politikker for overholdelse af kommunikation til at identificere brugerkommunikation om undersøgelse foretaget af interne eller eksterne korrekturlæsere. Du kan finde flere oplysninger om, hvordan politikker for overholdelse af kommunikation kan hjælpe dig med at overvåge kommunikation i din organisation under Politikker for overholdelse af [regler og standarder i Microsoft 365](communication-compliance.md). Hvis du vil gennemgå, hvordan Contoso hurtigt konfigurerede en politik for overholdelse af kommunikation til at overvåge upassende indhold i Microsoft Teams, Exchange Online og Yammer-kommunikation, kan du se dette [casestudie](communication-compliance-case-study.md).

## <a name="subscriptions-and-licensing"></a>Abonnementer og licenser

Før du går i gang med overholdelse af kommunikationsreglerne, [skal du Microsoft 365 dit abonnement](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) og eventuelle tilføjelser. Din organisation skal have et af følgende abonnementer eller tilføjelser for at få adgang til og bruge kommunikationsoverholdelse:

- Microsoft 365 E5/A5/F5/G5-abonnement (betalt version eller prøveversion)
- Microsoft 365 E3/A3/F3/G5 + tilføjelsesprogrammet Microsoft 365 E5/A5/F5/G5 Compliance
- Microsoft 365 E3/A3/F3/G5 + Microsoft 365 E5/A5/F5/G5 Insider Risk Management-tilføjelsesprogrammet
- Office 365 Enterprise E5-abonnement (betalt version eller prøveversion)
- Office 365 A5 -abonnement (betalt version eller prøveversion)
- Office 365 Enterprise E3-abonnement + tilføjelsesprogrammet Avanceret overholdelse i Office 365 (der er ikke længere tilgængeligt for nye abonnementer, se bemærk)

Brugere, der er inkluderet i politikker for overholdelse af kommunikation, skal tildeles en af licenserne ovenfor. Du kan finde flere oplysninger om abonnementer og licenser [Microsoft 365 vejledning til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> Kommunikationsoverholdelse er i øjeblikket tilgængelig i lejere, der er hostet i geografiske områder og lande, der understøttes af Azure-tjenesteafhængigheder. Hvis du vil kontrollere, at kommunikationsoverholdelse understøttes for din organisation, skal du [se Tilgængelighed af Azure-afhængighed efter land/område](/troubleshoot/azure/general/dependency-availability-by-country).

Hvis du ikke har en eksisterende Office 365 Enterprise E5-plan og gerne vil prøve overholdelse af regler og standarder i kommunikation, kan du føje [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) til dit eksisterende abonnement eller tilmelde dig [en](https://www.microsoft.com/microsoft-365/enterprise) prøveversion af Office 365 Enterprise E5.

> [!NOTE]
> Avanceret overholdelse i Office 365 sælges ikke længere som enkeltstående abonnement. Når aktuelle abonnementer udløber, skal kunder overgå til et af abonnementerne ovenfor, som indeholder de samme eller yderligere funktioner til overholdelse af regler og standarder.

## <a name="recommended-actions-preview"></a>Anbefalede handlinger (eksempel)

Anbefalede handlinger kan hjælpe din organisation med at komme i gang med funktioner til overholdelse af kommunikation og få mest muligt ud af dine eksisterende politikker. På siden Politikker **giver** anbefalede handlinger indsigt og opsummerer typer af følsomme oplysninger og upassende indholdsaktiviteter i din organisation. Insights understøttes af [dataklassificering](data-classification-overview.md) og anvendelse af følsomhedsmærkater, opbevaringsmærkater og klassificering af følsomme oplysninger. Denne indsigt omfatter ikke nogen personidentificerbare oplysninger (PII) for brugere i organisationen.

![Anbefalede handlinger til overholdelse af kommunikation.](../media/communication-compliance-recommended-actions.png)

Aktivitet i meddelelser, der indeholder upassende indhold, [](/microsoft-365/compliance/communication-compliance-policies#classifiers) sammenlægges af klassificeringstype fra eksisterende politikker, der bruger skabelonen til upassende indhold eller brugerdefinerede politikker, der anvender klassificeringer til upassende indhold. Undersøg beskeder for disse meddelelser på dashboardet Besked for dine politikker.

Aktivitet med [følsomme oplysningstyper](/microsoft-365/compliance/communication-compliance-policies#sensitive-information-types) registreres i meddelelser, der er dækket af eksisterende politikker, og for meddelelser, der ikke er omfattet af eksisterende politikker. Insights sammenlægges for alle typer af følsomme oplysninger, herunder dem, din organisation ikke tidligere har defineret i en eksisterende politik for overholdelse af kommunikation. Brug denne indsigt til at oprette en ny politik for overholdelse af kommunikation eller til at opdatere eksisterende politikker.

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>Trin 1 (påkrævet): Aktivér tilladelser til overholdelse af kommunikationsreglerne

> [!IMPORTANT]
> Når du har konfigureret dine rollegrupper, kan det tage op til 30 minutter, før tilladelserne for rollegruppen gælder for tildelte brugere i hele organisationen.

Der bruges seks rollegrupper til at konfigurere starttilladelser til at administrere funktioner til overholdelse af regler og standarder i kommunikation. Hvis overholdelse **af** kommunikationsindstillinger skal gøres tilgængelig som en menuindstilling i Microsoft 365 Overholdelsescenter og fortsætte med disse konfigurationstrin, skal du være tildelt en af følgende roller eller rollegrupper:

- Azure Active Directory [*global administratorrolle*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory [*rolle som overholdelsesadministrator*](/azure/active-directory/roles/permissions-reference#compliance-administrator)
- Microsoft 365 Overholdelsescenter [*rollegruppe for*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) organisationsadministration
- Microsoft 365 Overholdelsescenter af [*rollegruppen Overholdelsesadministrator*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- *Rollegruppen Kommunikationsoverholdelse*
- *Rollegruppen Kommunikationsoverholdelsesadministrator*

Medlemmer af følgende roller har de samme løsningstilladelser, der følger med *rollegruppen* Kommunikationsoverholdelsesadministrator:

- Azure Active Directory *global administrator*
- Azure Active Directory *over overholdelse af regler og standarder*
- Microsoft 365 Overholdelsescenter *organisationsadministration*
- Microsoft 365 Overholdelsescenter over *overholdelse af regler og standarder*

> [!IMPORTANT]
> Sørg for, at du altid har mindst én bruger i  rollegrupperne  Kommunikationsoverholdelse eller Kommunikationsoverholdelse (afhængigt af den indstilling, du vælger), så din konfiguration af kommunikationsoverholdelse ikke kommer ind i et scenarie med "nul administrator", hvis bestemte brugere forlader organisationen.

Afhængigt af hvordan du ønsker at administrere politikker og beskeder om overholdelse af kommunikation, skal du tildele brugere til bestemte rollegrupper for at administrere forskellige sæt af funktioner til overholdelse af regler og standarder i kommunikation. Du har mulighed for at tildele brugere med forskellige ansvarsområder i forbindelse med overholdelse til bestemte rollegrupper for at administrere forskellige områder af funktioner til overholdelse af regler og standarder i kommunikation. Eller du kan vælge at tildele alle brugerkonti til udvalgte administratorer, analytikere, administratorer og seere til rollegruppen *Kommunikationsoverholdelse* . Brug en enkelt rollegruppe eller flere rollegrupper, så de passer bedst til dine krav til overholdelsesstyring.

Vælg mellem disse gruppeindstillinger for løsningsroller, når du konfigurerer og administrerer kommunikationsoverholdelse:

| Rolle | Rolletilladelser |
|:-----|:-----------------|
| **Kommunikationsoverholdelse** | Brug denne rollegruppe til at administrere overholdelse af kommunikationsreglerne for din organisation i en enkelt gruppe. Ved at tilføje alle brugerkonti for udvalgte administratorer, analytikere, seere og seere kan du konfigurere tilladelser til overholdelse af kommunikation i en enkelt gruppe. Denne rollegruppe indeholder alle kommunikationsoverholdelsestilladelsesroller. Denne konfiguration er den nemmeste måde at komme hurtigt i gang med overholdelse af kommunikation på, og den passer godt til organisationer, der ikke har brug for separate tilladelser defineret til separate grupper af brugere. Brugere, der opretter politikker som kommunikationsadministrator for overholdelse af regler og standarder, skal have deres postkasse hostet Exchange Online.|
| **Administrator for overholdelse af kommunikation** | Brug denne rollegruppe til i første omgang at konfigurere kommunikationsoverholdelse og senere for at adskille administratorer af kommunikationsoverholdelse i en defineret gruppe. Brugere, der er tildelt denne rollegruppe, kan oprette, læse, opdatere og slette politikker for overholdelse af kommunikation, globale indstillinger og rollegruppetildelinger. Brugere, der er tildelt denne rollegruppe, kan ikke få vist beskeder om meddelelser. Brugere, der opretter politikker som kommunikationsadministrator for overholdelse af regler og standarder, skal have deres postkasse hostet Exchange Online.|
| **Kommunikationsoverholdelsesanalytiker** | Brug denne gruppe til at tildele tilladelser til brugere, der fungerer som analytikere for kommunikationsoverholdelse. Brugere, der er tildelt denne rollegruppe, kan få vist politikker, hvor de er tildelt som korrekturlæsere, få vist metadata for meddelelser (ikke meddelelsesindhold), eskalere til flere korrekturlæsere eller sende meddelelser til brugere. Analytikere kan ikke løse afventende beskeder. |
| **Communication Compliance Investigator** | Brug denne gruppe til at tildele tilladelser til brugere, der skal fungere som kompatibilitetsgrupper for kommunikation. Brugere, der er tildelt denne rollegruppe, kan få vist metadata og indhold for meddelelser, eskalere til flere korrekturlæsere, eskalere til Advanced eDiscovery-sag, sende meddelelser til brugere og løse beskeden. |
| **Fremviser til overholdelse af kommunikation** | Brug denne gruppe til at tildele tilladelser til brugere, der skal administrere kommunikationsrapporter. Brugere, der er tildelt denne rollegruppe, kan få adgang til alle rapporteringswidgets på startsiden til overholdelse af kommunikation og kan få vist alle rapporter om overholdelse af kommunikation. |

### <a name="option-1-assign-all-compliance-users-to-the-communication-compliance-role-group"></a>Mulighed 1: Tildel alle brugere af overholdelse af regler og standarder til rollegruppen Kommunikationsoverholdelse

1. Log på [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) med legitimationsoplysningerne til en administratorkonto i Microsoft 365 organisation.

2. I Security &amp; Compliance Center skal du gå **til Tilladelser**. Vælg linket for at få vist og administrere roller i Office 365.

3. Vælg *rollegruppen Kommunikationsoverholdelse* , og vælg derefter **Rediger rollegruppe**.

4. Vælg **Vælg medlemmer** i venstre navigationsrude, og vælg derefter **Rediger**.

5. Vælg **Tilføj,** og markér derefter afkrydsningsfeltet for alle brugere, du vil føje til rollegruppen *Kommunikationsoverholdelse* .

6. Vælg **Tilføj**, og vælg derefter **Udført**.

7. Vælg **Gem** for at føje brugerne til rollegruppen. Vælg **Luk** for at fuldføre trinnene

### <a name="option-2-assign-users-to-specific-communication-compliance-role-groups"></a>Mulighed 2: Tildel brugere til bestemte rollegrupper for kommunikationsoverholdelse

Brug denne indstilling til at tildele brugere til bestemte rollegrupper for at segmentere adgang til kommunikationsoverholdelse og ansvarsområder blandt forskellige brugere i organisationen.

1. Log på computeren [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com) legitimationsoplysningerne til en administratorkonto i Microsoft 365, og gå derefter **til Tilladelser**</a>.

2. Vælg linket for at få vist og administrere roller i Office 365.

3. Vælg en af kommunikationsrollegrupperne til overholdelse af regler og standarder, og vælg **derefter Rediger rollegruppe**.

4. Vælg **Vælg medlemmer** i venstre navigationsrude, og vælg derefter **Rediger**.

5. Vælg **Tilføj** , og markér derefter afkrydsningsfeltet for alle brugere, du vil føje til rollegruppen.

6. Vælg **Tilføj**, og vælg derefter **Udført**.

7. Vælg **Gem** for at føje brugerne til rollegruppen.

8. Vælg den næste rollegruppe til overholdelse af kommunikationsoverholdelse, og gentag derefter trin 4-7 for hver påkrævet rollegruppe.

9. Vælg **Luk** for at fuldføre trinnene.

Du kan finde flere oplysninger om rollegrupper og tilladelser [i Tilladelser i Overholdelsescenter](../security/office-365-security/protect-against-threats.md).

## <a name="step-2-required-enable-the-audit-log"></a>Trin 2 (påkrævet): Aktivér overvågningsloggen

Kommunikationsoverholdelse kræver overvågningslogs for at vise beskeder og registrere afhjælpningshandlinger, som er foretaget af korrekturlæsere. Overvågningsloggen er en oversigt over alle aktiviteter, der er knyttet til en defineret organisationspolitik, eller når en politik for overholdelse af kommunikation ændres.

Overvågning er aktiveret for Microsoft 365 organisationer som standard. Nogle organisationer har deaktiveret overvågning af bestemte årsager. Hvis overvågning er deaktiveret for organisationen, kan det skyldes, at en anden administrator har slået det fra. Vi anbefaler, at du bekræfter, at det er OK at slå overvågning til igen, når du udfører dette trin.

Du kan finde en trinvis vejledning i at aktivere overvågning i Slå søgning [i overvågningslogfil til eller fra](turn-audit-log-search-on-or-off.md). Når du har aktiveret overvågning, vises der en meddelelse om, at overvågningsloggen forberedes, og at du kan køre en søgning om et par timer, efter at klargøringen er fuldført. Du behøver kun at udføre denne handling én gang. Du kan finde flere oplysninger om brug af overvågningsloggen [i Søge i overvågningsloggen](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>Trin 3 (valgfrit): Konfigurer grupper til overholdelse af kommunikationsoverensstemmelse

 Når du opretter en politik for overholdelse af kommunikation, definerer du, hvem der har gennemgået deres kommunikation, og hvem der udfører anmeldelser. I politikken skal du bruge mailadresser til at identificere enkeltpersoner eller grupper af personer. For at forenkle din konfiguration kan du oprette grupper for personer, som har gennemgået deres kommunikation, og grupper for personer, der gennemser kommunikationen. Hvis du bruger grupper, skal du muligvis bruge flere. Hvis du f.eks. vil overvåge kommunikationen mellem to forskellige grupper af personer, eller hvis du vil angive en gruppe, der ikke skal overvåges.

Brug følgende diagram som en hjælp til at konfigurere grupper i din organisation til politikker for overholdelse af kommunikation:

| **Medlem af politik** | **Understøttede grupper** | **Ikke-understøttede grupper** |
|:-----|:-----|:-----|
|Overvågede brugere <br> Ekskluderede brugere | Distributionsgrupper <br> Microsoft 365-grupper | Dynamiske distributionsgrupper <br> Indlejrede distributionsgrupper <br> Mailaktiverede sikkerhedsgrupper <br> Microsoft 365 grupper med dynamisk medlemskab |
| Korrekturlæsere | Ingen | Distributionsgrupper <br> Dynamiske distributionsgrupper <br> Indlejrede distributionsgrupper <br> Mailaktiverede sikkerhedsgrupper |

Når du tildeler *en distributionsgruppe* i politikken, overvåger politikken alle mails og chatsamtaler Teams hver bruger i *distributionsgruppen*. Når du tildeler en *Microsoft 365-gruppe* i politikken, overvåger politikken alle mails og Teams-chatsamtaler, der sendes til *Microsoft 365-gruppen**, ikke de individuelle mails og chats, der modtages af hvert gruppemedlem. Brug af distributionsgrupper i politikker for overholdelse af kommunikation anbefales, så individuelle mails og chatsamtaler Teams hver bruger overvåges automatisk.

Hvis du er en organisation med en lokal Exchange-installation eller en ekstern mailudbyder, og du vil overvåge Microsoft Teams-chatsamtaler for dine brugere, skal du oprette en distributionsgruppe, som brugere med lokale eller eksterne postkasser kan overvåge. Senere i disse trin skal du tildele denne distributionsgruppe som valget **Overvågede brugere** og grupper i guiden politik. Du kan finde flere oplysninger om krav og begrænsninger for aktivering af skybaseret lagring og Teams-understøttelse af lokale brugere i Søg efter [Teams-chatdata for lokale brugere](search-cloud-based-mailboxes-for-on-premises-users.md).

For at administrere overvågede brugere i store virksomhedsorganisationer kan det være nødvendigt at overvåge alle brugere på tværs af store grupper. Du kan bruge PowerShell til at konfigurere en distributionsgruppe til en global politik for overholdelse af kommunikation for den tildelte gruppe. Dette giver dig mulighed for at overvåge tusindvis af brugere med en enkelt politik og holde politikken for overholdelse af kommunikation opdateret, når nye medarbejdere tilmelder sig organisationen.

1. Opret en dedikeret [distributionsgruppe](/powershell/module/exchange/new-distributiongroup) til din globale politik for overholdelse af kommunikation med følgende egenskaber: Sørg for, at denne distributionsgruppe ikke bruges til andre formål eller andre Office 365-tjenester.

    - **MemberDepartRestriction = Closed**. Sikrer, at brugerne ikke kan fjerne sig selv fra distributionsgruppen.
    - **MemberJoinRestriction = Closed**. Sikrer, at brugerne ikke kan føje sig selv til distributionsgruppen.
    - **ModerationEnabled = True**. Sikrer, at alle meddelelser, der sendes til denne gruppe, godkendes, og at gruppen ikke bruges til at kommunikere uden for konfigurationen af overholdelsespolitikken for kommunikation.

    ```PowerShell
    New-DistributionGroup -Name <your group name> -Alias <your group alias> -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true
    ```

2. Vælg en ubrugt Exchange [for at spore brugere](/Exchange/recipients/mailbox-custom-attributes), der er føjet til organisationens politik for overholdelse af kommunikation.

3. Kør følgende PowerShell-script på en tilbagevendende tidsplan for at føje brugere til politikken for overholdelse af kommunikation:

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

Du kan finde flere oplysninger om konfiguration af grupper i:

- [Oprette og administrere distributionsgrupper](/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Oversigt over Microsoft 365-grupper](/office365/admin/create-groups/office-365-groups)

## <a name="step-4-optional-verify-your-yammer-tenant-is-in-native-mode"></a>Trin 4 (valgfrit): Bekræft, at Yammer lejer er i oprindelig tilstand

I oprindelig tilstand er alle Yammer-brugere i Azure Active Directory (Azure AD), alle grupper Office 365 Grupper, og alle filer gemmes i SharePoint Online. Din Yammer lejer skal være i indbygget tilstand for politikker for overholdelse af kommunikation for at scanne og identificere risikabelt samtaler i private meddelelser og communitysamtaler i Yammer.

Du kan finde flere oplysninger om konfiguration Yammer i oprindelig tilstand under:

- [Oversigt over Yammer i oprindelig tilstand Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode)
- [Konfigurere dit Yammer for indbygget tilstand for Microsoft 365](/yammer/configure-your-yammer-network/native-mode)

## <a name="step-5-required-create-a-communication-compliance-policy"></a>Trin 5 (påkrævet): Opret en politik for overholdelse af kommunikation

>[!IMPORTANT]
>Brug af PowerShell til at oprette og administrere politikker for overholdelse af kommunikation understøttes ikke. Hvis du vil oprette og administrere disse politikker, skal du bruge kontrolelementerne til administration af politikker i [Microsoft 365 af kommunikationsoverholdelse](https://compliance.microsoft.com/supervisoryreview).

>[!TIP]  
>Vil du se en dybdegående gennemgang af, hvordan du konfigurerer en ny politik for overholdelse af kommunikation og afhjælper en besked? Se denne [15-minutters video](communication-compliance-plan.md#creating-a-communication-compliance-policy-walkthrough) for at se en demonstration af, hvordan politikker til overholdelse af kommunikation kan hjælpe dig med at registrere upassende meddelelser, undersøge potentielle overtrædelser og løse problemer med overholdelse.

1. Log på computeren [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com) legitimationsoplysningerne til en administratorkonto i din Microsoft 365 organisation.

2. Vælg Microsoft 365 Overholdelsescenter **kommunikationsoverholdelse i dialogboksen Indstillinger**.

3. Vælg **fanen** Politikker.

4. Vælg **Opret politik** for at oprette og konfigurere en ny politik ud fra en skabelon eller for at oprette og konfigurere en brugerdefineret politik.

    Hvis du vælger en politikskabelon til at oprette en politik, skal du:

    - Bekræft eller opdater navnet på politikken. Politiknavne kan ikke ændres, når politikken er oprettet.

    - Vælg de brugere eller grupper, du vil overvåge, herunder vælge brugere eller grupper, du vil udelukke. Når du bruger skabelonen i konflikt med interesse, skal du vælge to grupper eller to brugere til at overvåge for intern kommunikation.

    - Vælg korrekturlæserne for politikken. Korrekturlæsere er individuelle brugere, og alle korrekturlæsere skal have postkasser hostet på Exchange Online. Korrekturlæsere, der er tilføjet her, er de korrekturlæsere, du kan vælge mellem, når du eskalerer en besked til undersøgelses- og afhjælpningsarbejdsprocessen. Når korrekturlæsere føjes til en politik, modtager de automatisk en mail, der giver dem besked om tildelingen af politikken og indeholder links til oplysninger om gennemsynsprocessen.

    - Vælg et felt med begrænsede betingelser, normalt en følsom oplysningstype eller ordbog til nøgleord, der skal anvendes på politikken.

    > [!NOTE]
    > Hvis du vil aktivere optisk tegngenkendelse [(OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) for at scanne integrerede eller vedhæftede billeder i meddelelser for trykt eller håndskrevet tekst, der opfylder politikbetingelserne,  >  skal du vælge Tilpas politikKonditioner og procentdel og aktivere Udtræk udskrevet eller håndskrevet tekst fra billeder **til** evaluering.

    Hvis du vælger at bruge guiden Politik til at oprette en brugerdefineret politik, skal du:

    - Giv politikken et navn og en beskrivelse. Politiknavne kan ikke ændres, når politikken er oprettet.

    - Vælg de brugere eller grupper, der skal overvåges, herunder alle brugere i din organisation, bestemte brugere og grupper eller andre brugere og grupper, som du gerne vil udelukke.

    - Vælg korrekturlæserne for politikken. Korrekturlæsere er individuelle brugere, og alle korrekturlæsere skal have postkasser hostet på Exchange Online. Korrekturlæsere, der er tilføjet her, er de korrekturlæsere, du kan vælge mellem, når du eskalerer en besked til undersøgelses- og afhjælpningsarbejdsprocessen. Når korrekturlæsere føjes til en politik, modtager de automatisk en mail, der giver dem besked om tildelingen af politikken og indeholder links til oplysninger om gennemsynsprocessen.

    - Vælg de kommunikationskanaler, du vil scanne, Exchange, Microsoft Teams, Yammer eller Skype for Business. Du kan også vælge at scanne tredjepartskilder, hvis du har konfigureret en forbindelse i Microsoft 365.

    - Vælg kommunikationsretningen for at overvåge, herunder indgående, udgående eller intern kommunikation.

    - Definer politikbetingelserne [for kommunikation.](communication-compliance-policies.md#ConditionalSettings) Du kan vælge mellem meddelelsesadresse, nøgleord, filtyper og betingelser for størrelsesoverensstemmelse.

    - Vælg, om du vil inkludere typer af følsomme oplysninger. Dette trin er stedet, hvor du kan vælge standard og brugerdefinerede typer af følsomme oplysninger. Vælg mellem eksisterende brugerdefinerede typer af følsomme oplysninger eller brugerdefinerede ordbøger til nøgleord i guiden politik til overholdelse af kommunikation. Du kan oprette disse elementer, før du kører guiden, hvis det er nødvendigt. Du kan også oprette nye typer af følsomme oplysninger fra guiden til overholdelse af politik for kommunikation.

    - Vælg, om du vil aktivere klassificeringer. Klassificeringer kan registrere upassende sprog og billeder, der sendes eller modtages i brødteksten i mails eller andre teksttyper. Du kan vælge følgende indbyggede klassificeringer: *Trussel**,* Bandeord, Målrettet *chikane**,* Voksenbilleder, *Racy-billeder* og *Gory-billeder*.

    - [Aktivér optisk tegngenkendelse (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) for at scanne integrerede eller vedhæftede billeder i meddelelser for udskrevne eller håndskrevne tekster, der opfylder politikbetingelserne. I forbindelse med brugerdefinerede politikker skal en eller flere betingede indstillinger, der er knyttet til tekst, nøgleord, klassificeringer eller følsomme oplysningstyper, konfigureres i politikken for at aktivere valget af optisk tegngenkendelsesscanning.

    - Definer procentdelen af kommunikation, der skal gennemgås.

    - Gennemse dine politikvalg, og opret politikken.

5. Vælg **Opret politik,** når du bruger skabelonerne eller **Send, når** du bruger guiden brugerdefineret politik.

6. Siden **Din politik blev oprettet** vises med retningslinjer for, hvornår politikken aktiveres, og hvilken kommunikation der registreres.

## <a name="step-6-optional-update-compliance-boundaries-for-communication-compliance-policies"></a>Trin 6 (valgfrit): Opdater overholdelsesgrænser for politikker for overholdelse af kommunikation

[Overensstemmelsesgrænser](/microsoft-365/compliance/set-up-compliance-boundaries) opretter logiske grænser i en organisation, der styrer brugerens indholdsplaceringer (f.eks. postkasser, OneDrive-konti og SharePoint-websteder), som eDiscovery-ledere kan søge i.

Hvis du har konfigureret overholdelsesgrænser i organisationen, skal du opdatere overholdelsesgrænserne for at give visse brugere adgang til postkasser, der understøtter politikker for overholdelse af regler og standarder i kommunikation. Du skal give adgang til administratorer af kommunikationsoverholdelse og korrekturlæsere af kommunikationsoverholdelse, så din politikadministration og undersøgelse og afhjælpningshandlinger kan fungere korrekt.

For at tillade adgang for administratorer og korrekturlæsere til kommunikation skal du køre følgende PowerShell-kommandoer. Du skal kun køre disse kommandoer én gang, også selvom du tilføjer nye politikker for overholdelse af regler og standarder i kommunikation i fremtiden:

```powershell
Import-Module ExchangeOnlineManagement
$UserCredential = Get-Credential
Connect-IPPSSession -Credential $UserCredential
New-ComplianceSecurityFilter -FilterName "CC_mailbox" -Users <list your communication compliance admins and reviewers user alias or email address> -Filters "Mailbox_Name -like 'SupervisoryReview{*'" -Action All
```

Du kan finde flere oplysninger om cmdlet-syntaks [i New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter).

## <a name="step-7-optional-create-notice-templates-and-configure-user-anonymization"></a>Trin 7 (valgfrit): Opret meddelelsesskabeloner, og konfigurer brugeranonymisering

Hvis du vil have mulighed for at besvare en politikbesked ved at sende en påmindelsesmeddelelse til den tilknyttede bruger, skal du oprette mindst én meddelelsesskabelon i organisationen. Felterne til meddelelsesskabeloner kan redigeres, før de sendes som en del af afhjælpningsprocessen for beskeder, og det anbefales at oprette en brugerdefineret meddelelsesskabelon for hver kommunikationspolitik for overholdelse af regler og standarder.

Du kan også vælge at aktivere anonymisering for viste brugernavne, når der undersøges politik match, og der sker handlinger på meddelelser.

1. Log på computeren [Microsoft 365 Overholdelsescenter](https://compliance.microsoft.com) legitimationsoplysningerne til en administratorkonto i din Microsoft 365 organisation.

2. I Microsoft 365 Overholdelsescenter skal du gå til Overholdelse **af kommunikationsreglerne**.

3. Vælg fanen Beskyttelse af personlige oplysninger for at konfigurere anonymisering **for** brugernavne.

4. Hvis du vil aktivere anonymisering, skal **du vælge Vis anonymiserede versioner af brugernavne**.

5. Vælg **Gem**.

6. Gå til fanen **Meddelelsesskabeloner** , og vælg **derefter Opret meddelelsesskabelon**.

7. På siden **Rediger en meddelelsesskabelon** skal du udfylde følgende felter:

    - Skabelonnavn (påkrævet)
    - Send fra (påkrævet)
    - Cc og Bcc (valgfrit)
    - Emne (påkrævet)
    - Meddelelsestekst (påkrævet)

8. Vælg **Gem** for at oprette og gemme meddelelsesskabelonen.

## <a name="step-8-optional-test-your-communication-compliance-policy"></a>Trin 8 (valgfrit): Test din politik for overholdelse af kommunikation

Når du har oprettet en politik for overholdelse af kommunikation, er det en god ide at teste den for at sikre, at de angivne betingelser håndhæves korrekt af politikken. Det kan også være en god [ide at teste dine DLP-politikker (forebyggelse](create-test-tune-dlp-policy.md) af datatab), hvis politikkerne for overholdelse af regler og standarder i kommunikation omfatter følsomme oplysningstyper. Sørg for at give dine politikker tid til at aktivere, så den kommunikation, du vil teste, registreres.

Følg disse trin for at teste din politik for overholdelse af kommunikation:

1. Åbn en mailklient, Microsoft Teams eller Yammer, mens du er logget på som en overvåget bruger defineret i den politik, du vil teste.

2. Send en mail, Microsoft Teams chatbesked eller en Yammer, der opfylder de kriterier, du har defineret i politikken for overholdelse af kommunikation. Denne test kan være et nøgleord, størrelse på vedhæftede filer, domæne osv. Sørg for, at du afgør, om dine konfigurerede betingede indstillinger i politikken er for restriktive eller for længdere.

    > [!NOTE]
    > Det kan tage op til 24 timer, før mails behandles fuldt ud i en politik. Kommunikation i Microsoft Teams, Yammer og tredjepartsplatforme kan tage op til 48 timer at behandle fuldt ud i en politik.

3. Log på Microsoft 365 som korrekturlæser, der er udpeget i politikken for overholdelse af kommunikation. Gå til **Communication** **complianceAlerts** >  for at få vist beskeder om dine politikker.

4. Afhjulpet påmindelsen ved hjælp af afhjælpningskontrolelementerne, og bekræft, at beskeden er løst korrekt.

## <a name="next-steps"></a>Næste trin

Når du har gennemført disse trin for at oprette din første politik for overholdelse af kommunikation, begynder du at modtage beskeder fra aktivitetsindikatorer efter 24-48 timer. Konfigurer yderligere politikker efter behov ved hjælp af vejledningen i trin 5 i denne artikel.

Du kan få mere at vide om at undersøge beskeder om kommunikationsoverholdelse under [Undersøg og afhjulpet beskeder om kommunikationsoverholdelse](communication-compliance-investigate-remediate.md).

Hvis du vil holde dig opdateret med de nyeste opdateringer til overholdelse af regler og standarder i kommunikation, skal du **vælge Nyheder** [i kommunikationsoverholdelse](https://compliance.microsoft.com/) for organisationen.
