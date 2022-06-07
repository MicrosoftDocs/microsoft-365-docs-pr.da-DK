---
title: Opgrader distributionslister til Microsoft 365-grupper i Exchange Online
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 787d7a75-e201-46f3-a242-f698162ff09f
description: Få mere at vide om, hvordan du opgraderer en eller flere distributionslister til Microsoft 365-grupper i Exchange Online, og hvordan du bruger PowerShell til at opgradere flere distributionslister samtidigt.
ms.openlocfilehash: 6f27c4a7df345a25f4b5ca7d2a9f2979a97e7c6a
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922169"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-exchange-online"></a>Opgrader distributionslister til Microsoft 365-grupper i Exchange Online

Opgradering af en distributionsliste til en Microsoft 365-gruppe er en fantastisk måde at forbedre funktionerne og egenskaberne i grupper i din organisation på. Du kan få flere oplysninger under [Hvorfor du skal opgradere distributionslisterne til grupper i Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

Du kan opgradere distributionslisterne én ad gangen eller flere ad gangen. Du kan bruge Exchange Administration (EAC) eller Exchange Online PowerShell.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups"></a>Opgrader en eller mange distributionslistegrupper til Microsoft 365-grupper

Du skal være global administrator eller Exchange-administrator for at opgradere en distributionsliste. Hvis du vil opgradere til Microsoft 365 Grupper, skal distributionslisten have en angivet ejer, og den pågældende ejer skal være en postkasse.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Brug Den klassiske EAC til at opgradere en eller mange distributionslistegrupper til Microsoft 365-grupper i Outlook

> [!NOTE]
> Procedurerne i dette afsnit er ikke tilgængelige i den nye EAC.

1. Gå til Exchange Administration > **modtagergrupper**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>

   Du får vist en meddelelse, der angiver, at du har distributionslister (også kaldet **distributionsgrupper**), der er berettiget til at blive opgraderet til Microsoft 365 Grupper.
   
   ![Vælg knappen Kom i gang.](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

1. Vælg en eller flere distributionslister (også kaldet **distributionsgrupper**) på **gruppesiden** .

   ![Vælg en distributionsgruppe.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

1. Vælg opgraderingsikonet.

   ![Ikonet Opgrader til Microsoft 365 Grupper.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

1. I dialogboksen med oplysninger skal du vælge **Ja** for at bekræfte opgraderingen. Processen starter med det samme. Afhængigt af størrelsen og antallet af distributionslamper, du opgraderer, kan processen tage minutter eller timer.

   Hvis distributionslisten ikke kan opgraderes, vises der en dialogboks med dette ord. Se [Hvilke distributionslister kan ikke opgraderes?](#which-distribution-lists-cant-be-upgraded).

1. Hvis du opgraderer flere distributionslister, skal du bruge rullelisten til at filtrere, hvilke distributionslister der er blevet opgraderet. Hvis listen ikke er fuldført, skal du vente et stykke tid længere og derefter vælge **Opdater** for at se, hvad der er blevet opgraderet.

**Noter**:

- Du får ikke en meddelelse, når opgraderingerne er fuldført. I stedet kan du se, hvad der er angivet under **Tilgængelig til opgradering** eller **Opgraderede URL-adresser**.

- Hvis du har valgt en distributionsliste til opgradering, men den stadig vises på siden som **Tilgængelig til opgradering**, blev den ikke opgraderet. Se [Hvad du skal gøre, hvis opgraderingen ikke virker](#what-to-do-if-the-upgrade-doesnt-work).

- En gruppes oversigtsmail kan tilbyde, at du kan opgradere alle berettigede distributionslister, som du er ejer af. Du kan finde flere oplysninger om samlet mail under [Hav en gruppesamtale i Outlook](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22).

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>Sådan gør du, hvis opgraderingen ikke virker

Distributionslister, der ikke kan opgraderes, forbliver uændrede.

Hvis en eller flere **berettigede** distributionslister ikke kan opgraderes, skal du gøre følgende:

1. Brug [dette script](https://aka.ms/DLToM365Group) til at søge efter mulige problemer. Løs eventuelle problemer, der er rapporteret af scriptet, og prøv at opgradere distributionslisten én gang mere. 

2. Hvis scriptet ikke hjælper, skal du åbne en [supportanmodning](../../business-video/get-help-support.md). Problemet skal eskaleres til gruppernes teknikerteam.

## <a name="how-to-use-exchange-online-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>Sådan bruger du Exchange Online PowerShell til at opgradere flere distributionslister på samme tid

Hvis du vil oprette forbindelse til Exchange Online PowerShell, skal du se [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="upgrade-a-single-distribution-list"></a>Opgrader en enkelt distributionsliste

Hvis du vil opgradere en enkelt distributionsliste, skal du bruge følgende syntaks:

```PowerShell
Upgrade-DistributionGroup -DLIdentities <EmailAddress>
```

I dette eksempel opgraderes distributionslisten marketing@contoso.com:

```PowerShell
Upgrade-DistributionGroup -DLIdentities marketing@contoso.com
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Upgrade-DistributionGroup](/powershell/module/exchange/upgrade-distributiongroup).

> [!NOTE]
> Du kan også opgradere en enkelt distributionsliste til en Microsoft 365-gruppe ved hjælp af cmdlet'en [New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) .

### <a name="upgrade-multiple-distribution-lists-at-the-same-time"></a>Opgrader flere distributionslister på samme tid

Hvis du vil opgradere flere distributionslister på samme tid, skal du bruge følgende syntaks:

```PowerShell
Upgrade-DistributionGroup -DLIdentities <EmailAddress1>,<EmailAddress2>,...
```

I dette eksempel opgraderes de angivne distributionslister til Microsoft 365 Grupper.

```powershell
Upgrade-DistributionGroup -DLIdentities marketing@contoso.com,finanace@contoso.com,hr@contoso.com
```

Du kan finde detaljerede oplysninger om syntaks og parametre under [Upgrade-DistributionGroup](/powershell/module/exchange/upgrade-distributiongroup).

### <a name="upgrade-all-eligible-distribution-lists"></a>Opgrader alle berettigede distributionslister

Brug en af følgende metoder til at opgradere alle berettigede distributionslister til Microsoft 365 Grupper:

- Opgrader alle berettigede distributionslister:

   ```PowerShell
   $All = Get-EligibleDistributionGroupForMigration -ResultSize unlimited
   $All | Foreach-Object {Upgrade-DistributionGroup -DLIdentities $_.PrimarySMTPAddress}
   ```

- Prøv at opgradere alle distributionslister, uanset om de er berettigede eller ej:

   ```PowerShell
   $All Get-DistributionGroup -RecipientTypeDetails MailUniversalDistributionGroup -ResultSize unlimited
   $All | Foreach-Object {Upgrade-DistributionGroup -DLIdentities $_.PrimarySMTPAddress}
   ```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Ofte stillede spørgsmål om opgradering af distributionslister til Microsoft 365-grupper i Outlook

### <a name="which-distribution-lists-cant-be-upgraded"></a>Hvilke distributionslister kan ikke opgraderes?

Du kan kun opgradere skyadministrerede, enkle, ikke-indlejrede distributionslister. I tabellen nedenfor vises distributionslister, der **IKKE kan** opgraderes.

|Ejendom|Støtteberettigede?|
|---|:---:|
|Administreret distributionsliste i det lokale miljø.|Nej|
|Indlejrede distributionslister. Distributionslisten har enten underordnede grupper eller er medlem af en anden gruppe.|Nej|
|Distributionslister, hvor et eller flere medlemmer er andet end en brugerpostkasse, delt postkasse, teampostkasse eller mailbruger. Med andre ord er værdien **RecipientTypeDetails** for et hvilket som helst medlem af distributionslisten ikke **UserMailbox**, **SharedMailbox**, **TeamMailbox** eller **MailUser**.|Nej|
|Distributionsliste, der har mere end 100 ejere.|Nej|
|Distributionsliste, der kun har medlemmer, men ingen ejer.|Nej|
|Distributionsliste med alias, der indeholder specialtegn.|Nej|
|Distributionslisten er konfigureret til at være en videresendelsesadresse for en delt postkasse.|Nej|
|Distributionslisten er en del af **Afsenderbegrænsning** på en anden distributionsliste.|Nej|
|Mailaktiverede sikkerhedsgrupper.|Nej|
|Dynamiske distributionsgrupper.|Nej|
|Distributionslister, der blev konverteret til **RoomLists**.|Nej|

### <a name="check-which-distribution-lists-are-eligible-for-upgrade"></a>Kontrollér, hvilke distributionslister der er berettiget til opgradering

Kør følgende kommando for at kontrollere, om en bestemt distributionsliste er berettiget til opgradering:

```PowerShell
Get-DistributionGroup <EmailAddress> | Get-EligibleDistributionGroupForMigration
```

Hvis du vil se alle distributionsgrupper, der er berettiget til opgradering, skal du køre følgende kommando:

```PowerShell
Get-EligibleDistributionGroupForMigration
```

### <a name="who-can-run-the-upgrade-scripts"></a>Hvem kan køre opgraderingsscriptene?

Personer med rettigheder som global administrator eller Exchange-administrator.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>Hvorfor vises der stadig en distributionsliste på visitkortet? Hvad skal jeg gøre for at forhindre, at en opgraderet distributionsliste vises på min liste med automatisk forslag?

- **Outlook**: Når du har opgraderet en ditributionsliste til en Microsoft 365-gruppe, er brugerens lokale modtagercache (også kendt som kaldenavnscachen) ikke klar over ændringen. Følg trinnene i følgende artikel for at nulstille brugerens lokale modtagercache: [Oplysninger om autofuldførelseslisten i Outlook](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list). 

  Hvis du ikke opdaterer modtagercachen, leveres alle mails, der sendes til Microsoft 365-gruppen, korrekt, men følgende problemer forbliver:
  
  - Modtageren af gruppen fortolkes som distributionslisten i stedet for Microsoft 365-gruppen.
  - Visitkortet er distributionslistens kontakt i stedet for Microsoft 365-gruppens.

- **Outlook på internettet**: På samme måde som Outlook forbliver distributionslisten i modtagercachen. Følg trinnene i denne artikel for at opdatere cachen for at se gruppens visitkort: [Fjern foreslået navn eller mailadresse fra listen automatisk fuldførelse](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58).

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>Modtager nye gruppemedlemmer en velkomstmail i deres indbakke?

Nej. Indstillingen for aktivering af velkomstmeddelelser er som standard angivet til falsk. Denne indstilling påvirker både eksisterende og nye gruppemedlemmer, der kan tilmelde sig, når migreringen er fuldført. Hvis gruppeejeren senere tillader gæstebrugere, modtager gæstebrugere ikke en velkomstmail i deres indbakke. Gæstemedlemmer kan fortsætte med at arbejde med gruppen.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>Hvad sker der, hvis en eller nogle af URL-adresserne ikke opgraderes?

Der er nogle tilfælde, hvor berettigede distributionslister ikke kan opgraderes. Eksempel:

- En administrator har anvendt en **politik for gruppemailadresse**, og distributionslisten opfylder ikke kravene i politikken.

- En distributionsliste har **MemberJoinRestriction** eller **MemberDepartRestriction** angivet til værdien **Lukket**.

- Oprettelsen af Microsoft 365-gruppeoprettelse er begrænset som beskrevet i denne artikel: [denne artikel](/microsoft-365/solutions/manage-creation-of-groups).

  Brug en af følgende løsninger til dette specifikke problem:

  - Sørg for, at alle ejere af distributionslisten har tilladelse til at oprette Microsoft 365-grupper (dvs. at ejerne er medlem af den sikkerhedsgruppe, der har tilladelse til at oprette Microsoft 365-grupper).

  - Erstat midlertidigt ejeren af distributionslisten med en bruger, der har tilladelse til at oprette Microsoft 365-grupper.

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>Hvad sker der med DL,hvis opgraderingen fra EAC mislykkes?

Opgraderingen sker kun, når opkaldet sendes til serveren. Hvis opgraderingen mislykkes, forbliver dine distributionslister og fungerer, som de plejede.

### <a name="what-happens-to-message-approval-moderation-settings-on-distribution-groups-after-upgrading"></a>Hvad sker der med indstillinger for meddelelsesgodkendelse (indstilling) for distributionsgrupper efter opgradering?

Indstillingerne for meddelelsesgodkendelse (indstilling) bevares og fungerer fortsat fint, når distributionsgruppen er opgraderet til en Microsoft 365-gruppe.

## <a name="related-content"></a>Relateret indhold

[Sammenlign grupper](../create-groups/compare-groups.md) (artikel)\
[Forklaring af Microsoft 365-grupper til dine brugere](../create-groups/explain-groups-knowledge-worker.md) (artikel)\
[Tilføj eller fjern medlemmer fra Microsoft 365-grupper ved hjælp af Administration](../create-groups/add-or-remove-members-from-groups.md)
