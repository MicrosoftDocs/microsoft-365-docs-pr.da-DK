---
title: Administrer Microsoft 365-grupper med PowerShell
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BSA160
- BCS160
ms.assetid: aeb669aa-1770-4537-9de2-a82ac11b0540
description: I denne artikel kan du få mere at vide om, hvordan du udfører almindelige administrationsopgaver for Microsoft 365 grupper i PowerShell.
ms.openlocfilehash: 407e242728bf37ebf8c11b8094bfa4931229e4ef
ms.sourcegitcommit: 3226bdf213b290ec5262670873c3a75f17b66ddd
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/12/2022
ms.locfileid: "65372197"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a>Administrer Microsoft 365-grupper med PowerShell

*Denne artikel gælder både for Microsoft 365 Enterprise og Office 365 Enterprise.*

Denne artikel indeholder trinnene til at udføre almindelige administrationsopgaver for grupper i Microsoft PowerShell. Den viser også PowerShell-cmdlet'erne til grupper. Du kan finde oplysninger om administration af SharePoint websteder under [Administrer SharePoint Online-websteder ved hjælp af PowerShell](/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a>Link til dine retningslinjer for brug af Microsoft 365-grupper

Når brugerne [opretter eller redigerer en gruppe i Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), kan du vise dem et link til organisationens retningslinjer for anvendelse. Hvis du f.eks. kræver, at der føjes et bestemt præfiks eller suffiks til et gruppenavn.

Brug PowerShell Azure Active Directory (Azure AD) til at pege brugerne på organisationens retningslinjer for brug af Microsoft 365 grupper. Se [Azure Active Directory cmdlet'er til konfiguration af gruppeindstillinger](/azure/active-directory/enterprise-users/groups-settings-cmdlets), og følg trinnene i linket **Opret indstillinger på mappeniveau** for at definere linket med forbrugsretningslinjen. Når du kører AAD-cmdlet'en, får brugerne vist linket til dine retningslinjer, når de opretter eller redigerer en gruppe i Outlook.

![Opret en ny gruppe med linket retningslinjer for brug.](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)

![Klik på Retningslinjer for gruppebrug for at se dine organisationers Office 365 retningslinjer for grupper.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)

## <a name="allow-users-to-send-as-the-microsoft-365-group"></a>Tillad brugere at sende som den Microsoft 365 gruppe

Hvis du vil aktivere dine Microsoft 365 grupper til "Send som", skal du bruge cmdlet'erne [Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission) og [Get-RecipientPermission](/powershell/module/exchange/get-recipientpermission) til at konfigurere dette. Når du aktiverer denne indstilling, kan Microsoft 365 gruppebrugere bruge Outlook eller Outlook på internettet til at sende og besvare mails som den Microsoft 365 gruppe. Brugerne kan gå til gruppen, oprette en ny mail og ændre feltet "Send som" til gruppens mailadresse.

[Det kan du også gøre i Exchange Administration](/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group).

Brug følgende script, hvor aliasset for den gruppe, du vil opdatere, erstattes *\<GroupAlias\>* med aliasset for den bruger, *\<UserAlias\>* du vil give tilladelser til. [Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) for at køre dette script.

```PowerShell
$groupAlias = "<GroupAlias>"
$userAlias = "<UserAlias>"
$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Når cmdlet'en er udført, kan brugerne gå til Outlook eller Outlook på internettet at sende som gruppen ved at føje gruppens mailadresse til feltet **Fra**.

## <a name="create-classifications-for-microsoft-365-groups-in-your-organization"></a>Opret klassificeringer for Microsoft 365-grupper i din organisation

Du kan oprette følsomhedsmærkater, som brugerne i din organisation kan angive, når de opretter en Microsoft 365 gruppe. Hvis du vil klassificere grupper, anbefaler vi, at du bruger følsomhedsmærkater i stedet for den tidligere klassificeringsfunktion for grupper. Du kan finde oplysninger om brug af følsomhedsmærkater [under Brug følsomhedsmærkater til at beskytte indhold på Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!IMPORTANT]
> Hvis du i øjeblikket bruger klassificeringsmærkater, vil de ikke længere være tilgængelige for brugere, der opretter grupper, når følsomhedsmærkater er aktiveret.

Du kan stadig bruge den tidligere klassificeringsfunktion for grupper. Du kan oprette klassificeringer, som brugerne i din organisation kan angive, når de opretter en Microsoft 365 gruppe. Du kan f.eks. give brugerne tilladelse til at angive "Standard", "Hemmelig" og "Tophemmelighed" for grupper, de opretter. Gruppeklassificeringer er ikke angivet som standard, og du skal oprette dem, før dine brugere kan angive dem. Brug Azure Active Directory PowerShell til at pege dine brugere på organisationens retningslinjer for brug af Microsoft 365-grupper.

Se [Azure Active Directory cmdlet'er til konfiguration af gruppeindstillinger](/azure/active-directory/users-groups-roles/groups-settings-cmdlets), og følg trinnene i **Opret indstillinger på mappeniveau** for at definere klassificeringen for Microsoft 365-grupper.

```powershell
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

Hvis du vil knytte en beskrivelse til hver klassificering, kan du bruge indstillingsattributten  *ClassificationDescriptions* til at definere.

```powershell
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

Hvor Classification stemmer overens med strengene på ClassificationList.

Eksempel:

```powershell
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Når du har kørt ovenstående Azure Active Directory cmdlet for at angive din klassificering, skal du køre [Set-UnifiedGroup-cmdlet'en](/powershell/module/exchange/Set-UnifiedGroup), hvis du vil angive klassificeringen for en bestemt gruppe.

```powershell
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact>
```

Eller opret en ny gruppe med en klassificering.

```powershell
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public>
```

Se [Brug af PowerShell med Exchange Online](/powershell/exchange/exchange-online-powershell) og [Forbind til at Exchange Online PowerShell for at](/powershell/exchange/connect-to-exchange-online-powershell) få flere oplysninger om brug af Exchange Online PowerShell.

Når disse indstillinger er aktiveret, kan gruppeejeren vælge en klassificering i rullemenuen i Outlook på internettet og Outlook og gemme den på siden **Rediger** gruppe.

![Vælg Microsoft 365 Gruppeklassificering.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)

## <a name="hide-microsoft-365-groups-from-the-global-address-list"></a>Skjul Microsoft 365-grupper fra den globale adresseliste.

Du kan angive, om en Microsoft 365 gruppe skal vises på den globale adresseliste (GAL) og andre lister i din organisation. Hvis du f.eks. har en juridisk afdelingsgruppe, som du ikke vil vise på adresselisten, kan du forhindre, at gruppen vises i den globale adresseliste. Kør cmdlet'en Set-Unified-gruppe for at skjule gruppen fra adresselisten på følgende måde:

```powershell
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-microsoft-365-groups"></a>Tillad kun, at interne brugere sender meddelelser til Microsoft 365-grupper

Hvis du ikke ønsker, at brugere fra andre organisationer skal sende mails til en Microsoft 365 gruppe, kan du ændre indstillingerne for den pågældende gruppe. Det giver kun interne brugere mulighed for at sende en mail til din gruppe. Hvis en ekstern bruger forsøger at sende en meddelelse til den pågældende gruppe, afvises den.

Kør Set-UnifiedGroup-cmdlet'en for at opdatere denne indstilling på følgende måde:

```powershell
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-microsoft-365-groups"></a>Føj MailTips til Microsoft 365-grupper

Når en afsender forsøger at sende en mail til en Microsoft 365 gruppe, kan de få vist et MailTip.

Kør cmdlet'en Set-Unified gruppe for at føje et mailtip til gruppen:

```powershell
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Sammen med MailTip kan du også angive MailTipTranslations, som angiver andre sprog for MailTip. Lad os antage, at du vil have den spanske oversættelse og derefter køre følgende kommando:

```powershell
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-the-display-name-of-the-microsoft-365-group"></a>Rediger det viste navn på Microsoft 365-gruppen

Det viste navn angiver navnet på Microsoft 365-gruppen. Du kan se dette navn i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a> eller <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">i Microsoft 365 Administration</a>. Du kan redigere det viste navn for gruppen eller tildele et vist navn til en eksisterende Microsoft 365 Gruppe ved at køre kommandoen Set-UnifiedGroup:

```powershell
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-microsoft-365-groups-for-outlook-to-public-or-private"></a>Skift standardindstillingen for Microsoft 365-grupper for Outlook til Offentlig eller Privat

Microsoft 365-grupper i Outlook oprettes som standard som Privat. Hvis din organisation ønsker, at Microsoft 365-grupper som standard skal oprettes som offentlig (eller tilbage til Privat), skal du bruge denne PowerShell-cmdlet-syntaks:

 ```powershell
 Set-OrganizationConfig -DefaultGroupAccessType Public
 ```

Sådan angives til Privat:

 ```powershell
 Set-OrganizationConfig -DefaultGroupAccessType Private
 ```

Sådan kontrollerer du indstillingen:

 ```powershell
 Get-OrganizationConfig | ft DefaultGroupAccessType
 ```

Du kan få mere at vide under [Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) og [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

## <a name="microsoft-365-groups-cmdlets"></a>Microsoft 365-grupper cmdlet'er

Følgende cmdlet'er kan bruges sammen med Microsoft 365-grupper.

|**Cmdlet-navn**|**Beskrivelse**|
|:-----|:-----|
|[Get-UnifiedGroup](/powershell/module/exchange/get-unifiedgroup) <br/> |Brug denne cmdlet til at søge efter eksisterende Microsoft 365-grupper og til at få vist egenskaber for gruppeobjektet  <br/> |
|[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup) <br/> |Opdater egenskaberne for en bestemt Microsoft 365 gruppe  <br/> |
|[Ny UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) <br/> |Opret en ny Microsoft 365-gruppe. Denne cmdlet indeholder et minimalt sæt parametre. Hvis du vil angive værdier for udvidede egenskaber, skal du bruge Set-UnifiedGroup, når du har oprettet den nye gruppe  <br/> |
|[Fjern UnifiedGroup](/powershell/module/exchange/remove-unifiedgroup) <br/> |Slet en eksisterende Microsoft 365 gruppe  <br/> |
|[Get-UnifiedGroupLinks](/powershell/module/exchange/get-unifiedgrouplinks) <br/> |Hent oplysninger om medlemskab og ejer for en Microsoft 365 gruppe  <br/> |
|[Add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks) <br/> |Føj medlemmer, ejere og abonnenter til en eksisterende Microsoft 365-gruppe <br/> |
|[Remove-UnifiedGroupLinks](/powershell/module/exchange/remove-unifiedgrouplinks) <br/> |Fjern ejere og medlemmer fra en eksisterende Microsoft 365 gruppe  <br/> |
|[Get-UserPhoto](/powershell/module/exchange/get-userphoto) <br/> |Bruges til at få vist oplysninger om det brugerfoto, der er knyttet til en konto. Brugerfotos gemmes i Active Directory  <br/> |
|[Set-UserPhoto](/powershell/module/exchange/set-userphoto) <br/> |Bruges til at knytte et brugerfoto til en konto. Brugerfotos gemmes i Active Directory  <br/> |
|[Fjern-Brugerfoto](/powershell/module/exchange/remove-userphoto) <br/> |Fjern billedet for en Microsoft 365 gruppe  <br/> |

## <a name="related-topics"></a>Relaterede emner

[Opgrader distributionslister til Microsoft 365-grupper](/office365/admin/manage/upgrade-distribution-lists)

[Administrer, hvem der kan oprette Microsoft 365-grupper](/office365/admin/create-groups/manage-creation-of-groups)

[Administrer gæsteadgang til Microsoft 365-grupper](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Skift medlemskab af statisk gruppe til dynamisk i](/azure/active-directory/users-groups-roles/groups-change-type)
