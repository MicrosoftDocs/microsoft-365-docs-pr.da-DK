---
title: Opgrader distributionslister Microsoft 365 grupper i Outlook
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
description: Lær, hvordan du opgraderer en eller mange distributionslister til Microsoft 365 grupper i Outlook, og hvordan du bruger PowerShell til at opgradere flere distributionslister samtidigt.
ms.openlocfilehash: 5394ce52f865d0b9a0383619cb11b9ebf3a94fc8
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/12/2022
ms.locfileid: "63589335"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Opgrader distributionslister Microsoft 365 grupper i Outlook

Du kan opgradere distributionslister til Microsoft 365 grupper i Outlook. Dette er en god måde at give din organisations distributionslister alle funktionerne og funktionaliteterne fra Microsoft 365 Groups. [Derfor skal du opgradere dine distributionslister til grupper i Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

Du kan opgradere url-adresser én ad gangen eller flere ad gangen.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Opgrader en eller flere distributionslistegrupper Microsoft 365 grupper i Outlook

Du skal være global administrator eller Exchange administrator for at opgradere en distributionslistegruppe. Hvis du vil opgradere Microsoft 365 grupper, skal distributionslistegruppen have en ejer med en postkasse.

### <a name="use-the-new-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Brug den nye EAC til at opgradere en eller flere distributionslistegrupper til Microsoft 365 grupper i Outlook

1. Gå til den nye Exchange Administration > **modtagergrupper**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>

2. Vælg den distributionslistegruppe (også kaldet **en distributionsgruppe**), du vil opgradere Microsoft 365 fra **siden** Grupper.

3. Vælg **distributionsgruppen Opgrader** på værktøjslinjen.

4. Klik på **Opgrader i dialogboksen Klar** til at **opgradere**. Processen starter med det samme. Afhængigt af størrelsen og antallet af distributionslistegrupper, du opgraderer, kan processen tage minutter eller timer.

> [!NOTE]
> Et banner øverst angiver opgraderingen, f.eks. *at distributionsgruppe(er) er blevet opgraderet. Det tager fem minutter at afspejle ændringerne. Filtrer efter Microsoft 365 for at få vist de opgraderede distributionsgrupper*.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Brug den klassiske EAC til at opgradere en eller flere distributionslistegrupper til Microsoft 365 grupper i Outlook

1. Gå til Exchange Administration > **modtagergrupper**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a><br/>Du får vist en meddelelse om, at du har distributionslister (også kaldet **distributionsgrupper**), der er berettiget til at blive opgraderet til Microsoft 365 grupper.<br/> ![Vælg knappen Introduktion.](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

1. Vælg en eller flere distributionslister (også kaldet **en distributionsgruppe**) på **siden** Grupper.<br/>![Vælg en distributionsgruppe.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

1. Vælg ikonet for opgradering.<br/>![Ikonet Opgrader Microsoft 365 Grupper.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

1. Vælg Ja i dialogboksen med oplysninger **for** at bekræfte opgraderingen. Processen starter med det samme. Afhængigt af størrelsen og antallet af URL-adresser, du opgraderer, kan processen tage minutter eller timer.<br/>Hvis distributionslisten ikke kan opgraderes, vises en dialogboks, der siger dette. Se [Hvilke distributionslister kan ikke opgraderes?](#which-distribution-lists-cant-be-upgraded).

1. Hvis du opgraderer flere distributionslister, skal du bruge rullelisten til at filtrere de distributionslister, der er blevet opgraderet. Hvis listen ikke er færdig, skal du vente lidt længere og **derefter vælge Opdater** for at se, hvad der er blevet opgraderet.<br/>Der er ingen meddelelse, der fortæller dig, hvornår opgraderingen er fuldført for alle de webadresser, du har valgt. Du kan regne dette ud ved at se, hvad der er angivet under **Tilgængelig for opgradering** eller **Opgraderede url-adresser**.

1. Hvis du har valgt en DL til opgradering, men den stadig vises på siden som Tilgængelig for opgradering, er opgraderingen ikke lykkedes. Se [Hvad du skal gøre, hvis opgraderingen ikke virker](#what-to-do-if-the-upgrade-doesnt-work).

> [!NOTE]
> Hvis du får gruppens oversigtsmails, har du måske bemærket nederst, at den nogle gange tilbyder at lade dig opgradere alle berettigede distributionslister, som du ejer. Se [Før en gruppesamtale i gang Outlook](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22) for at få mere at vide om mails med en gruppesamtale.

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>Hvad du skal gøre, hvis opgraderingen ikke virker

Distributionslister, som ikke kan opgraderes, forbliver uændrede.

Hvis en eller flere **berettigede** distributionslister ikke opgraderes, 

1. Brug [dette script](https://aka.ms/DLToM365Group) til at scanne for mulige problemer, der kan forhindre, at en distributionsliste opgraderes til Microsoft 365-gruppen, løse eventuelle problemer, der rapporteres af scriptet, og prøve at opgradere distributionslisten en gang til. 

2. Hvis det ovenstående script ikke hjælper, eller hvis problemet fortsætter, skal du åbne en [Supportanmodning](../../business-video/get-help-support.md). Problemet skal eskaleres til Groups Engineering-teamet, så de kan finde ud af, hvad problemet er.

## <a name="how-to-use-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>Sådan bruger du PowerShell til at opgradere flere distributionslister på samme tid

Hvis du er en erfaren bruger af PowerShell, kan det være en ide at gå denne vej i stedet for at bruge brugergrænsefladen. Vi har et sæt cmdlet'er, der kan hjælpe dig med at opgradere distributionslister. Se nedenfor.

### <a name="upgrade-a-single-dl"></a>Opgrader en enkelt DL

Hvis du vil opgradere en enkelt DL, skal du køre følgende kommando:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <Dl SMTP address>
```

Hvis du f.eks. vil opgradere en DL med SMTP-adresse dl1@contoso.com, skal du køre følgende kommando:

```PowerShell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com
```

> [!NOTE]
> Du kan også opgradere en enkelt distributionsliste til en Microsoft 365 gruppe ved hjælp af [New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) PowerShell-cmdlet'en

### <a name="upgrade-multiple-dls-in-a-batch"></a>Opgradere flere url-adresser i en batch

Du kan også videregive flere url-adresser som en batch og opgradere dem sammen:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <DL SMTP address1>, <DL SMTP address2>,
<DL SMTP address3>, <DL SMTP address4>
```

Hvis du f.eks. vil opgradere fem DLs med SMTP-adresse `dl1@contoso.com` `dl2@contoso.com`og , `dl3@contoso.com`og `dl5@contoso.com`, `dl4@contoso.com` skal du køre følgende kommando:

`Upgrade-DistributionGroup -DlIdentities dl1@contoso.com, dl2@contoso.com, dl3@contoso.com, dl4@contoso.com, dl5@contoso.com`

### <a name="upgrade-all-eligible-dls"></a>Opgrader alle berettigede url-adresser

Du kan opgradere alle de berettigede url-adresser på to måder.

> [!NOTE]
> Cmdletten Upgrade-DistributionGroup ikke data fra pipelinen, derfor er det påkrævet at bruge operatoren "foreach-object{}" for at køre korrekt.

1. Hent de berettigede url-adresser i lejeren, og opgrader dem ved hjælp af opgraderingskommandoen:

```PowerShell
Get-EligibleDistributionGroupForMigration | Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
}
```

2. Hent listen over alle url-adresser, og opgrader kun de berettigede url-adresser:

```PowerShell
Get-DistributionGroup| Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
}
```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Ofte stillede spørgsmål om opgradering af distributionslister Microsoft 365 grupper i Outlook

### <a name="which-distribution-lists-cant-be-upgraded"></a>Hvilke distributionslister kan ikke opgraderes?

Du kan kun opgradere sky-administrerede, enkle, ikke-indlejrede distributionslister. Tabellen nedenfor viser distributionslister, **som IKKE** kan opgraderes.

|**Egenskab**|**Berettiget?**|
|:-----|:-----|
|Lokalt administreret distributionsliste.  <br/> |Nej  <br/> |
|Indlejrede distributionslister. Distributionslisten har enten underordnede grupper eller er medlem af en anden gruppe.  <br/> |Nej  <br/> |
|Distributionslister med **medlems-RecipientTypeDetails** bortset **fra UserMailbox**, **SharedMailbox**, **TeamMailbox**, **MailUser**  <br/> |Nej  <br/> |
|Distributionsliste, der har mere end 100 ejere  <br/> |Nej  <br/> |
|Distributionsliste, der kun har medlemmer, men ingen ejer  <br/> |Nej  <br/> |
|Distributionsliste, der har alias, der indeholder specialtegn  <br/> |Nej  <br/> |
|Hvis distributionslisten er konfigureret til at være en videresendelsesadresse for delt postkasse  <br/> |Nej  <br/> |
|Hvis DL er en del af **afsenderbegrænsningen i** en anden DL.  <br/> |Nej  <br/> |
|Sikkerhedsgrupper  <br/> |Nej  <br/> |
|Dynamiske distributionslister  <br/> |Nej  <br/> |
|Distributionslister, der blev konverteret **til RoomLists**  <br/> |Nej  <br/> |

### <a name="check-which-dls-are-eligible-for-upgrade"></a>Kontrollér, hvilke url-adresser der er berettiget til opgradering

Hvis du vil kontrollere, om en DL er berettiget eller ej, kan du køre nedenstående kommando:

`Get-DistributionGroup <DL SMTP address> | Get-EligibleDistributionGroupForMigration`

Hvis du vil kontrollere, hvilke url-adresser der er berettiget til opgradering, skal du blot køre følgende kommando:

`Get-EligibleDistributionGroupForMigration`

### <a name="who-can-run-the-upgrade-scripts"></a>Who kan køre opgraderingsscriptene?

Personer med global administrator eller Exchange administratorrettigheder.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>Hvorfor viser visitkortet stadig en distributionsliste? Hvad skal jeg gøre for at forhindre, at en opgraderet distributionsliste vises på min liste med automatiske forslag?

- Eksempel Outlook: Når nogen forsøger at sende en mail i Outlook ved at skrive Microsoft 365-gruppenavnet efter overførslen, løses modtageren som distributionslisten i stedet for gruppen. Modtagerens visitkort bliver distributionslistens visitkort. Dette skyldes modtagerens cache eller kaldenavnscachen i Outlook. Mailen sendes korrekt til gruppen, men kan skabe forvirring om afsenderen.<br/>Du kan udføre trinnene i denne artikel, Oplysninger om [listen Outlook Autofuldførelse](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list) for at nulstille cachen, hvilket vil løse dette problem.

- For Outlook på internettet: Hvis du Outlook på internettet, forbliver distributionslistemodtageren stadig i cachen. Du kan følge trinnene i Fjern foreslået navn eller mailadresse fra listen [til](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58) autofuldfør for at opdatere cachehukommelsen for at få vist gruppens visitkort.

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>Får nye gruppemedlemmer en velkomstmail i deres indbakke?

Nej. Indstillingen til aktivering af velkomstmeddelelser er indstillet til FALSK som standard. Denne indstilling påvirker både eksisterende og nye gruppemedlemmer, der tilmelder sig, når overførslen er fuldført. Hvis gruppeejeren senere tillader gæstebrugere, modtager gæstebrugere ikke en velkomstmail i deres indbakke. Gæstemedlemmer kan fortsætte med at arbejde med gruppen.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>Hvad nu, hvis en eller nogle af disse url-adresser ikke opgraderes?

Der er visse tilfælde, hvor selvom DL er berettiget, men ikke kunne opgraderes. DL opgraderes ikke og forbliver som en DL.

- Hvis administratoren har anvendt gruppemailadressepolitik **for** grupperne i en organisation, og de forsøger at opgradere url-adresser, der ikke opfylder kriterierne, bliver DL ikke opgraderet

- DLs med **MemberJoinRestriction** **eller MemberDepartRestriction** angivet til **Closed**, kunne ikke opgraderes

- Gruppen Microsoft 365 er kun tilladt for få brugere ved hjælp af trinnene fra [denne artikel](/microsoft-365/solutions/manage-creation-of-groups). Hvis ejeren af en distributionsliste ikke har tilladelse til at oprette en Microsoft 365 gruppe, opgraderes distributionslisten ikke til en Microsoft 365 gruppe. Løsning: Brug en af følgende løsninger i ovenstående scenarie:
1)  Sørg for, at alle de brugere, der er nævnt som ejere af datagruppen, har tilladelse til at oprette M365-gruppen, dvs. er medlem af sikkerhedsgruppen, der har tilladelse til at oprette en M365-gruppe.
ELLER
2)  Erstat midlertidigt ejeren af den slutbruger, der ikke har tilladelse til at oprette M365-gruppe, med bruger, der har tilladelse til at oprette M365-gruppe

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>Hvad sker der med DL, hvis opgraderingen fra EAC mislykkes?

Opgraderingen finder først sted, når opkaldet er sendt til serveren. Hvis opgraderingen mislykkes, vil dine url-adresser være intakte. De vil fungere som tidligere.

### <a name="what-happens-to-message-approval-moderation-settings-on-distribution-groups-after-upgrading"></a>Hvad sker der med indstillinger for godkendelse af meddelelser (moderation) for distributionsgrupper efter opgraderingen?

Indstillingerne for godkendelse af meddelelser bevares og fungerer fortsat fint, når distributionsgruppen er blevet opgraderet til en Microsoft 365 gruppe.

## <a name="related-content"></a>Relateret indhold

[Sammenlign grupper](../create-groups/compare-groups.md) (artikel)\
[Forklaring Microsoft 365 grupper til dine brugere](../create-groups/explain-groups-knowledge-worker.md) (artikel)\
[Tilføj eller fjern medlemmer fra Microsoft 365 grupper ved hjælp af Administration](../create-groups/add-or-remove-members-from-groups.md)
