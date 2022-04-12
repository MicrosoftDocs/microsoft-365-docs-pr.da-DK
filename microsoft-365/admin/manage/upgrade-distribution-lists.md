---
title: Opgrader distributionslister til Microsoft 365-grupper i Outlook
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
description: Få mere at vide om, hvordan du opgraderer en eller flere distributionslister for at Microsoft 365-grupper i Outlook, og hvordan du bruger PowerShell til at opgradere flere distributionslister samtidigt.
ms.openlocfilehash: 832d65854a6a18ad28e3d9fca6d1d11c17146c80
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782253"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Opgrader distributionslister til Microsoft 365-grupper i Outlook

Du kan opgradere distributionslister til Microsoft 365-grupper i Outlook. Dette er en fantastisk måde at give din organisations distributionslister alle funktionerne og funktionaliteten i Microsoft 365-grupper. [Derfor skal du opgradere distributionslisterne til grupper i Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

Du kan opgradere DLs én ad gangen eller flere på samme tid.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Opgrader en eller mange distributionslistegrupper til Microsoft 365-grupper i Outlook

Du skal være global administrator eller Exchange administrator for at opgradere en distributionslistegruppe. Hvis du vil opgradere til Microsoft 365-grupper, skal distributionslistegruppen have en ejer med en postkasse.

### <a name="use-the-new-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Brug den nye EAC til at opgradere en eller mange distributionslistegrupper for at Microsoft 365-grupper i Outlook

1. Gå til det nye Exchange Administration > **Modtagergrupper**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>

2. Vælg den distributionslistegruppe (også kaldet en **distributionsgruppe**), som du vil opgradere til Microsoft 365 gruppe, på siden **Grupper**.

3. Vælg **gruppen Opgrader distribution** på værktøjslinjen.

4. Klik på **Opgrader** i dialogboksen **Klar til opgradering.** Processen starter med det samme. Afhængigt af størrelsen og antallet af distributionslistegrupper, du opgraderer, kan processen tage minutter eller timer.

> [!NOTE]
> Et banner øverst angiver, at opgraderingen, f.eks *. distributionsgrupper, er blevet opgraderet. Det tager 5 minutter at afspejle ændringerne. Filtrer efter Microsoft 365 grupper for at se de opgraderede distributionsgrupper*.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Brug Klassisk EAC til at opgradere en eller mange distributionslistegrupper for at Microsoft 365-grupper i Outlook

1. Gå til Exchange Administration > **Modtagergrupper**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a><br/>Du får vist en meddelelse om, at du har distributionslister (også kaldet **distributionsgrupper**), der er berettiget til at blive opgraderet til Microsoft 365-grupper.<br/> ![Vælg knappen Kom i gang.](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

1. Vælg en eller flere distributionslister (også kaldet en **distributionsgruppe**) på **gruppesiden** .<br/>![Vælg en distributionsgruppe.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

1. Vælg opgraderingsikonet.<br/>![Opgrader til Microsoft 365-grupper-ikon.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

1. I dialogboksen med oplysninger skal du vælge **Ja** for at bekræfte opgraderingen. Processen starter med det samme. Afhængigt af størrelsen og antallet af DLs, du opgraderer, kan processen tage minutter eller timer.<br/>Hvis distributionslisten ikke kan opgraderes, vises der en dialogboks med dette ord. Se [Hvilke distributionslister kan ikke opgraderes?](#which-distribution-lists-cant-be-upgraded).

1. Hvis du opgraderer flere distributionslister, skal du bruge rullelisten til at filtrere, hvilke distributionslister der er blevet opgraderet. Hvis listen ikke er fuldført, skal du vente et stykke tid længere og derefter vælge **Opdater** for at se, hvad der er blevet opgraderet.<br/>Der er ingen meddelelse, der fortæller dig, hvornår opgraderingsprocessen er fuldført for alle de DLs, du har valgt. Du kan finde ud af dette ved at se, hvad der er angivet under **Tilgængelig til opgradering** eller **Opgraderede URL-adresser**.

1. Hvis du har valgt en DL til opgradering, men den stadig vises på siden som Tilgængelig til opgradering, blev den ikke opgraderet. Se [Hvad du skal gøre, hvis opgraderingen ikke virker](#what-to-do-if-the-upgrade-doesnt-work).

> [!NOTE]
> Hvis du får vist gruppernes oversigtsmails, vil du muligvis bemærke nederst, at den nogle gange tilbyder at lade dig opgradere alle berettigede distributionslister, som du er ejer af. Se [Hav en gruppesamtale i Outlook](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22) for at få flere oplysninger om oversigt over mails.

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>Sådan gør du, hvis opgraderingen ikke virker

Distributionslister, der ikke kan opgraderes, forbliver uændrede.

Hvis en eller flere **kvalificerede** distributionslister ikke kan opgraderes, 

1. Brug [dette script](https://aka.ms/DLToM365Group) til at søge efter mulige problemer, der kan forhindre, at distributionslisten opgraderes til Microsoft 365 gruppe. Løs eventuelle problemer, der er rapporteret af scriptet, og prøv at opgradere distributionslisten én gang mere. 

2. Hvis ovenstående script ikke hjælper, eller hvis problemet fortsætter, skal du åbne en [supportanmodning](../../business-video/get-help-support.md). Problemet skal eskaleres til gruppernes teknikerteam, for at de kan finde ud af problemet.

## <a name="how-to-use-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>Sådan bruger du PowerShell til at opgradere flere distributionslister på samme tid

Hvis du har erfaring med at bruge PowerShell, kan det være en god idé at gå denne rute i stedet for at bruge brugergrænsefladen. Vi har et sæt cmdlet'er, der kan hjælpe dig med at opgradere distributionslister. Se nedenfor.

### <a name="upgrade-a-single-dl"></a>Opgrader en enkelt DL

Kør følgende kommando for at opgradere en enkelt DL:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <Dl SMTP address>
```

Hvis du f.eks. vil opgradere en DL med SMTP-adressen dl1@contoso.com, skal du køre følgende kommando:

```PowerShell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com
```

> [!NOTE]
> Du kan også opgradere en enkelt distributionsliste til en Microsoft 365 gruppe ved hjælp af [PowerShell-cmdlet'en New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup)

### <a name="upgrade-multiple-dls-in-a-batch"></a>Opgrader flere DLS i et batch

Du kan også overføre flere URL-adresser som et batch og opgradere dem sammen:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <DL SMTP address1>, <DL SMTP address2>,
<DL SMTP address3>, <DL SMTP address4>
```

Hvis du f.eks. vil opgradere fem URL-adresser med SMTP-adressen `dl1@contoso.com` og `dl2@contoso.com`, `dl3@contoso.com``dl4@contoso.com` og `dl5@contoso.com`, skal du køre følgende kommando:

```powershell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com, dl2@contoso.com, dl3@contoso.com, dl4@contoso.com, dl5@contoso.com
```

### <a name="upgrade-all-eligible-dls"></a>Opgrader alle berettigede URL-adresser

Du kan opgradere alle berettigede DLs på to måder.

> [!NOTE]
> Den Upgrade-DistributionGroup cmdlet modtager ikke data fra pipelinen. Derfor er det nødvendigt at bruge operatoren "foreach-object{}" for at køre korrekt.

1. Hent de berettigede URL-adresser i lejeren, og opgrader dem ved hjælp af opgraderingskommandoen:

   ```PowerShell
   Get-EligibleDistributionGroupForMigration | Foreach-Object{
       Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
   }
   ```

2. Hent listen over alle url-adresser, og opgrader kun de berettigede URL-adresser:

   ```PowerShell
   Get-DistributionGroup| Foreach-Object{
       Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
   }
   ```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Ofte stillede spørgsmål om opgradering af distributionslister til Microsoft 365-grupper i Outlook

### <a name="which-distribution-lists-cant-be-upgraded"></a>Hvilke distributionslister kan ikke opgraderes?

Du kan kun opgradere skyadministrerede, enkle, ikke-indlejrede distributionslister. I tabellen nedenfor vises distributionslister, der **IKKE kan** opgraderes.

|Ejendom|Støtteberettigede?|
|---|---|
|Administreret distributionsliste i det lokale miljø.|Nej|
|Indlejrede distributionslister. Distributionslisten har enten underordnede grupper eller er medlem af en anden gruppe.|Nej|
|Distributionslister med andet medlem **af RecipientTypeDetails** end **UserMailbox**, **SharedMailbox**, **TeamMailbox**, **MailUser**|Nej|
|Distributionsliste med mere end 100 ejere|Nej|
|Distributionsliste, der kun har medlemmer, men ingen ejer|Nej|
|Distributionsliste med alias, der indeholder specialtegn|Nej|
|Hvis distributionslisten er konfigureret til at være en videresendelsesadresse for delt postkasse|Nej|
|Hvis DL'en er en del af **afsenderbegrænsningen** i en anden DL.|Nej|
|Sikkerhedsgrupper|Nej|
|Dynamiske distributionslister|Nej|
|Distributionslister, der blev konverteret til **RoomLists**|Nej|

### <a name="check-which-dls-are-eligible-for-upgrade"></a>Kontrollér, hvilke DLS der er berettiget til opgradering

Hvis du vil kontrollere, om en DL er berettiget eller ej, kan du køre nedenstående kommando:

```PowerShell
Get-DistributionGroup <DL SMTP address> | Get-EligibleDistributionGroupForMigration
```

Hvis du vil kontrollere, hvilke DLS der er berettiget til opgradering, skal du blot køre følgende kommando:

```PowerShell
Get-EligibleDistributionGroupForMigration
```

### <a name="who-can-run-the-upgrade-scripts"></a>Who kan køre opgraderingsscripts?

Personer med globale administrator- eller Exchange administratorrettigheder.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>Hvorfor vises der stadig en distributionsliste på visitkortet? Hvad skal jeg gøre for at forhindre, at en opgraderet distributionsliste vises på min liste med automatisk forslag?

- For Outlook: Når nogen forsøger at sende en mail i Outlook ved at skrive Microsoft 365 gruppenavn efter migreringen, fortolkes modtageren som distributionslisten i stedet for gruppen. Modtagerens visitkort er distributionslisternes visitkort. Dette skyldes, at modtagercachen eller kaldenavnscachen er i Outlook. Mailen sendes til gruppen, men kan skabe forvirring hos afsenderen.<br/>Du kan udføre trinnene i denne artikel [Oplysninger om listen over Outlook autofuldførelse](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list) for at nulstille cachen, hvilket vil løse problemet.

- For Outlook på internettet: Hvis der er Outlook på internettet, forbliver modtageren af distributionslisten i cachen. Du kan følge trinnene i [Fjern foreslået navn eller mailadresse fra listen Automatisk fuldførelse](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58) for at opdatere cachen for at se gruppens visitkort.

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>Modtager nye gruppemedlemmer en velkomstmail i deres indbakke?

Nej. Indstillingen for aktivering af velkomstmeddelelser er som standard angivet til falsk. Denne indstilling påvirker både eksisterende og nye gruppemedlemmer, der kan tilmelde sig, når migreringen er fuldført. Hvis gruppeejeren senere tillader gæstebrugere, modtager gæstebrugere ikke en velkomstmail i deres indbakke. Gæstemedlemmer kan fortsætte med at arbejde med gruppen.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>Hvad sker der, hvis en eller nogle af URL-adresserne ikke opgraderes?

Der er nogle tilfælde, hvor selvom DL er berettiget, men ikke kunne opgraderes. DL'en bliver ikke opgraderet og forbliver som en DL.

- Hvor administratoren har anvendt **politik for gruppemailadresse** for grupperne i en organisation, og de forsøger at opgradere DLs, der ikke opfylder kriterierne, opgraderes DL'en ikke

- DLs med **MemberJoinRestriction** eller **MemberDepartRestriction** angivet til **Lukket**, kunne ikke opgraderes

- Oprettelse af Microsoft 365 gruppe er kun tilladt for få brugere ved hjælp af trinnene i [denne artikel](/microsoft-365/solutions/manage-creation-of-groups). Hvis ejeren af distributionslisten i dette scenarie ikke har tilladelse til at oprette Microsoft 365 gruppe, opgraderes distributionslisten ikke til Microsoft 365 gruppe.
Løsning: Brug en af følgende midlertidige løsninger i ovenstående scenarie:

1. Sørg for, at alle de brugere, der er nævnt som ejere af DL'en, har tilladelse til at oprette M365-gruppen, dvs. er medlem af den sikkerhedsgruppe, der har tilladelse til M365-gruppen.

   ELLER

2. Erstat midlertidigt ejeren af den DL, der ikke har tilladelse til at oprette M365-gruppe, med den bruger, der har tilladelse til at oprette M365-gruppe.

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>Hvad sker der med DL,hvis opgraderingen fra EAC mislykkes?

Opgraderingen sker kun, når opkaldet sendes til serveren. Hvis opgraderingen mislykkes, er dine URL-adresser intakte. De vil fungere som de plejede.

### <a name="what-happens-to-message-approval-moderation-settings-on-distribution-groups-after-upgrading"></a>Hvad sker der med indstillinger for meddelelsesgodkendelse (indstilling) for distributionsgrupper efter opgradering?

Indstillingerne for meddelelsesgodkendelse (indstilling) bevares og fungerer fortsat fint, når distributionsgruppen er opgraderet til en Microsoft 365 gruppe.

## <a name="related-content"></a>Relateret indhold

[Sammenlign grupper](../create-groups/compare-groups.md) (artikel)\
[Forklaring af Microsoft 365-grupper til dine brugere](../create-groups/explain-groups-knowledge-worker.md) (artikel)\
[Tilføj eller fjern medlemmer fra Microsoft 365 grupper ved hjælp af Administration](../create-groups/add-or-remove-members-from-groups.md)
