---
title: Administrer Microsoft 365 grupper med PowerShell
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
description: I denne artikel kan du lære, hvordan du udfører almindelige administrationsopgaver for Microsoft 365 grupper i PowerShell.
ms.openlocfilehash: 460444e1cb2f862f4d96ed6aad0178a146864658
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63589723"
---
# <a name="manage-microsoft-365-groups-with-powershell"></a>Administrer Microsoft 365 grupper med PowerShell

*Denne artikel gælder for både Microsoft 365 Enterprise og Office 365 Enterprise.*

Denne artikel indeholder trinnene til at udføre almindelige administrationsopgaver for grupper i Microsoft PowerShell. Den viser også PowerShell-cmdletter til grupper. Du kan få mere at vide SharePoint administrere websteder under [Administrere SharePoint Online-websteder ved hjælp af PowerShell](/sharepoint/manage-team-and-communication-sites-in-powershell).

## <a name="link-to-your-microsoft-365-groups-usage-guidelines"></a>Link til retningslinjerne for Microsoft 365 gruppebrug

Når brugere [opretter eller redigerer en gruppe Outlook](https://support.office.com/article/04d0c9cf-6864-423c-a380-4fa858f27102.aspx), kan du vise dem et link til organisationens retningslinjer for brug. Hvis du f.eks. skal føje et bestemt præfiks eller suffiks til et gruppenavn.

Brug Azure Active Directory (Azure AD) PowerShell til at pege brugerne på organisationens retningslinjer for brug af Microsoft 365 grupper. Se en [Azure Active Directory til](/azure/active-directory/enterprise-users/groups-settings-cmdlets) konfiguration af gruppeindstillinger, og følg trinnene i Opret indstillinger på mappeniveau for **at** definere linket til retningslinjerne for brug. Når du kører cmdletten AAD, får brugerne vist linket til dine retningslinjer, når de opretter eller redigerer en gruppe Outlook.

![Opret en ny gruppe med link til retningslinjer for brug.](../media/3f74463f-3448-4f24-a0ec-086d9aa95caa.png)

![Klik på Retningslinjer for gruppeanvendelse for at se din Office 365 retningslinjer for grupper.](../media/d0d54ace-f0ec-4946-b2de-50ce23f17765.png)

## <a name="allow-users-to-send-as-the-microsoft-365-group"></a>Tillad brugere at sende som Microsoft 365 gruppe

Hvis du vil aktivere dine Microsoft 365 grupper til "Send som", skal du bruge [cmdletterne Add-RecipientPermission](/powershell/module/exchange/add-recipientpermission) og [Get-RecipientPermission](/powershell/module/exchange/get-recipientpermission) til at konfigurere dette. Når du har aktiveret denne indstilling, Microsoft 365 gruppebrugere bruge Outlook eller Outlook på internettet til at sende og besvare mails som Microsoft 365 gruppe. Brugere kan gå til gruppen, oprette en ny mail og ændre feltet "Send som" til gruppens mailadresse.

([Du kan også gøre dette Exchange Administration](/office365/admin/create-groups/allow-members-to-send-as-or-send-on-behalf-of-group)).

Brug følgende script, der *\<GroupAlias\>* erstattes med aliasset for den gruppe, du vil opdatere, *\<UserAlias\>* og med aliasset for den bruger, du vil tildele tilladelser til. [Forbind at Exchange Online PowerShell til](/powershell/exchange/connect-to-exchange-online-powershell) at køre dette script.

```PowerShell
$groupAlias = "<GroupAlias>"
$userAlias = "<UserAlias>"
$groupsRecipientDetails = Get-Recipient -RecipientTypeDetails groupmailbox -Identity $groupAlias

Add-RecipientPermission -Identity $groupsRecipientDetails.Name -Trustee $userAlias -AccessRights SendAs
```

Når cmdlet'en udføres, kan brugerne gå til Outlook eller Outlook på internettet, der skal sendes som gruppen, ved at tilføje gruppemailadressen i **feltet** Fra.

## <a name="create-classifications-for-microsoft-365-groups-in-your-organization"></a>Opret klassificeringer for Microsoft 365 grupper i organisationen

Du kan oprette følsomhedsmærkater, som brugerne i organisationen kan angive, når de opretter en Microsoft 365 Gruppe. Hvis du vil klassificere grupper, anbefaler vi, at du bruger følsomhedsmærkater i stedet for den forrige klassifikationsfunktion grupper. Du kan finde oplysninger om brug af følsomhedsmærkater under Brug følsomhedsmærkater til at [beskytte indhold Microsoft Teams, Microsoft 365 grupper og SharePoint websteder](../compliance/sensitivity-labels-teams-groups-sites.md).

> [!IMPORTANT]
> Hvis du aktuelt bruger klassificeringsmærkater, vil de ikke længere være tilgængelige for brugere, der opretter grupper, når følsomhedsmærkater er aktiveret.

Du kan stadig bruge den forrige klassifikationsfunktion Grupper. Du kan oprette klassificeringer, som brugerne i organisationen kan angive, når de opretter en Microsoft 365 gruppe. Du kan f.eks. tillade brugere at angive "Standard", "Hemmelig" og "Top Secret" på grupper, de opretter. Gruppeklassificeringer er ikke angivet som standard, og du skal oprette dem, før dine brugere kan angive dem. Brug Azure Active Directory PowerShell til at pege brugerne på organisationens retningslinjer for brug af Microsoft 365 Grupper.

Se Azure Active Directory [til](/azure/active-directory/users-groups-roles/groups-settings-cmdlets) konfiguration af gruppeindstillinger, og følg trinnene i Opret indstillinger på mappeniveau for **at** definere klassificeringen af Microsoft 365 Grupper.

```powershell
$setting["ClassificationList"] = "Low Impact, Medium Impact, High Impact"
```

For at tilknytte en beskrivelse til hver klassificering kan du bruge indstillingsattributten  *ClassificationDescriptions til* at definere.

```powershell
$setting["ClassificationDescriptions"] ="Classification:Description,Classification:Description"
```

Hvor Klassificering svarer til strengene i ClassificationList.

Eksempel:

```powershell
$setting["ClassificationDescriptions"] = "Low Impact: General communication, Medium Impact: Company internal data , High Impact: Data that has regulatory requirements"
```

Når du kører ovenstående Azure Active Directory cmdlet for at angive din klassificering, skal du køre [Set-UnifiedGroup-cmdlet'en](/powershell/module/exchange/Set-UnifiedGroup), hvis du vil angive klassificeringen for en bestemt gruppe.

```powershell
Set-UnifiedGroup <LowImpactGroup@constoso.com> -Classification <LowImpact>
```

Eller opret en ny gruppe med en klassificering.

```powershell
New-UnifiedGroup <HighImpactGroup@constoso.com> -Classification <HighImpact> -AccessType <Public>
```

Se Brug [PowerShell med Exchange Online](/powershell/exchange/exchange-online-powershell) og [Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) for at få mere at vide om brug Exchange Online PowerShell.

Når disse indstillinger er aktiveret, kan gruppeejeren vælge en klassificering fra rullemenuen i Outlook på internettet og Outlook og gemme den fra siden Rediger gruppe.

![Vælg Microsoft 365 klassifikation af gruppe.](../media/f8d4219a-6180-491d-b0e1-4313ac83998b.png)

## <a name="hide-microsoft-365-groups-from-the-global-address-list"></a>Skjul Microsoft 365 grupper fra den globale adresseliste.

Du kan angive, om Microsoft 365 adressegruppe vises i den globale adresseliste (GAL) og andre lister i organisationen. Hvis du f.eks. har en gruppe for en juridisk afdeling, som du ikke vil have vist på adresselisten, kan du forhindre den pågældende gruppe i at blive vist i den globale adresseliste. Kør cmdlet'Set-Unified gruppe for at skjule gruppen fra adresselisten på følgende måde:

```powershell
Set-UnifiedGroup -Identity "Legal Department" -HiddenFromAddressListsEnabled $true
```

## <a name="allow-only-internal-users-to-send-message-to-microsoft-365-groups"></a>Tillad kun interne brugere at sende meddelelse til Microsoft 365 grupper

Hvis du ikke ønsker, at brugere fra andre organisationer skal kunne sende mails til en Microsoft 365 gruppe, kan du ændre indstillingerne for den pågældende gruppe. Det tillader kun interne brugere at sende en mail til din gruppe. Hvis en ekstern bruger forsøger at sende en meddelelse til den pågældende gruppe, afvises den.

Kør cmdletten Set-UnifiedGroup at opdatere denne indstilling, sådan her:

```powershell
Set-UnifiedGroup -Identity "Internal senders only" -RequireSenderAuthenticationEnabled $true
```

## <a name="add-mailtips-to-microsoft-365-groups"></a>Føj MailTips til Microsoft 365 grupper

Når en afsender forsøger at sende en mail til en Microsoft 365 gruppe, kan der vises et mailtip for dem.

Kør cmdlet'Set-Unified Gruppe for at føje et mailtip til gruppen:

```powershell
Set-UnifiedGroup -Identity "MailTip Group" -MailTip "This group has a MailTip"
```

Sammen med MailTip kan du også angive MailTipTranslations, som angiver andre sprog for MailTip. Antag, at du vil have spansk oversættelse, og kør derefter følgende kommando:

```powershell
Set-UnifiedGroup -Identity "MailaTip Group" -MailTip "This group has a MailTip" -MailTipTranslations "@{Add="ES:Esta caja no se supervisa."
```

## <a name="change-the-display-name-of-the-microsoft-365-group"></a>Ændre det viste navn på Microsoft 365 gruppe

Det viste navn angiver navnet på Microsoft 365 Gruppe. Du kan se dette navn <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration eller</a> <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>. Du kan redigere gruppens viste navn eller tildele et visningsnavn til en eksisterende Microsoft 365 ved at køre Set-UnifiedGroup gruppe:

```powershell
Set-UnifiedGroup -Identity "mygroup@contoso.com" -DisplayName "My new group"
```

## <a name="change-the-default-setting-of-microsoft-365-groups-for-outlook-to-public-or-private"></a>Ændre standardindstillingen for Microsoft 365 grupper for Outlook til Offentlig eller Privat

Microsoft 365 grupper i Outlook oprettes som privat som standard. Hvis din organisation ønsker, Microsoft 365 grupper oprettes som offentlig som standard (eller tilbage til privat), skal du bruge denne PowerShell-cmdlet-syntaks:

 `Set-OrganizationConfig -DefaultGroupAccessType Public`

Hvis du vil angive til Privat:

 `Set-OrganizationConfig -DefaultGroupAccessType Private`

Sådan bekræftes indstillingen:

 `Get-OrganizationConfig | ft DefaultGroupAccessType`

Du kan få mere at [vide under Set-OrganizationConfig](/powershell/module/exchange/set-organizationconfig) og [Get-OrganizationConfig](/powershell/module/exchange/get-organizationconfig).

## <a name="microsoft-365-groups-cmdlets"></a>Microsoft 365 Groups-cmdlet'er

Følgende cmdlet'er kan bruges sammen med Microsoft 365 Grupper.

|**Cmdlet-navn**|**Beskrivelse**|
|:-----|:-----|
|[Get-UnifiedGroup](/powershell/module/exchange/get-unifiedgroup) <br/> |Brug denne cmdlet til at søge efter eksisterende Microsoft 365 grupper og til at få vist egenskaberne for gruppeobjektet  <br/> |
|[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup) <br/> |Opdatere egenskaberne for en bestemt Microsoft 365 gruppe  <br/> |
|[New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) <br/> |Opret en ny Microsoft 365 gruppe. Denne cmdlet indeholder et minimalt sæt af parametre. Hvis du vil angive værdier for udvidede egenskaber, skal du Set-UnifiedGroup efter oprettelse af den nye gruppe  <br/> |
|[Remove-UnifiedGroup](/powershell/module/exchange/remove-unifiedgroup) <br/> |Slet en eksisterende Microsoft 365 gruppe  <br/> |
|[Get-UnifiedGroupLinks](/powershell/module/exchange/get-unifiedgrouplinks) <br/> |Hent oplysninger om medlemskab og ejer for en Microsoft 365 gruppe  <br/> |
|[Add-UnifiedGroupLinks](/powershell/module/exchange/add-unifiedgrouplinks) <br/> |Føj medlemmer, ejere og abonnenter til en eksisterende Microsoft 365 gruppe <br/> |
|[Remove-UnifiedGroupLinks](/powershell/module/exchange/remove-unifiedgrouplinks) <br/> |Fjern ejere og medlemmer fra en eksisterende Microsoft 365 gruppe  <br/> |
|[Get-UserPhoto](/powershell/module/exchange/get-userphoto) <br/> |Bruges til at vise oplysninger om det brugerbillede, der er knyttet til en konto. Brugerbilleder gemmes i Active Directory  <br/> |
|[Set-UserPhoto](/powershell/module/exchange/set-userphoto) <br/> |Bruges til at knytte et brugerbillede til en konto. Brugerbilleder gemmes i Active Directory  <br/> |
|[Remove-UserPhoto](/powershell/module/exchange/remove-userphoto) <br/> |Fjern billedet for en Microsoft 365 gruppe  <br/> |

## <a name="related-topics"></a>Relaterede emner

[Opgradere distributionslister til Microsoft 365 grupper](/office365/admin/manage/upgrade-distribution-lists)

[Administrer, hvem der kan oprette Microsoft 365 grupper](/office365/admin/create-groups/manage-creation-of-groups)

[Administrer gæsteadgang til Microsoft 365 Grupper](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Skift statisk gruppemedlemskab til dynamisk i](/azure/active-directory/users-groups-roles/groups-change-type)
