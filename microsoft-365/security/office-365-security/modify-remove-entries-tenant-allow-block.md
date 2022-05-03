---
title: Rediger og fjern poster på listen over tilladte/blokerede lejer
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Administratorer kan få mere at vide om, hvordan de redigerer og fjerner poster på listen over tilladte/blokerede lejere på sikkerhedsportalen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ac612b51cab9069e50c4eec05948b3aa840b9cc9
ms.sourcegitcommit: 4d6a8e9d69a421d6c293b2485a8aa5e806b71616
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/03/2022
ms.locfileid: "65182689"
---
# <a name="modify-and-remove-entries-in-the-tenant-allowblock-list"></a>Rediger og fjern poster på listen over tilladte/blokerede lejer

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Du kan bruge Microsoft 365 Defender-portalen eller PowerShell til at redigere og fjerne poster på listen over tilladte/blokerede lejere.

## <a name="use-the-microsoft-365-defender-portal"></a>Brug Microsoft 365 Defender-portalen

### <a name="modify-entries-in-the-tenant-allowblock-list"></a>Rediger poster på listen over tilladte/blokerede lejere

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> Sektionen **Regler for trusselspolitikker**\>, **lejerlister** \> for tilladelse/blokering. Du kan også gå direkte til siden **Med lejer-/blokliste** ved at bruge <https://security.microsoft.com/tenantAllowBlockList>.

2. Vælg den fane, der indeholder den type post, du vil ændre:
   - **Afsendere**
   - **Spoofing**
   - **Webadresser**
   - **Filer**

3. Vælg den post, du vil redigere, og klik derefter på ![Ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger**. De værdier, du kan ændre i det pop op-vindue, der vises, afhænger af den fane, du valgte i det forrige trin:
   - **Afsendere**
     - **Udløber aldrig** og/eller udløbsdatoen.
     - **Valgfri note**
   - **Spoofing**
     - **Handling**: Du kan ændre værdien til **Tillad** eller **Bloker**.
   - **Webadresser**
     - **Udløber aldrig** og/eller udløbsdatoen.
     - **Valgfri note**
   - **Filer**
     - **Udløber aldrig** og/eller udløbsdatoen.
     - **Valgfri note**

4. Klik på **Gem**, når du er færdig.

> [!NOTE]
> Du kan kun forlænge med maksimalt 30 dage efter oprettelsesdatoen. Blokke kan forlænges i op til 90 dage, men i modsætning til tillader, kan de også indstilles til Aldrig udløber.

### <a name="remove-entries-from-the-tenant-allowblock-list"></a>Fjern poster fra listen over tilladte/blokerede lejere

1. I portalen Microsoft 365 Defender på <https://security.microsoft.com>skal du gå til **Politikker & regler** \> Sektionen **Regler for trusselspolitikker**\>, **lejerlister** \> for tilladelse/blokering. Du kan også gå direkte til siden **Med lejer-/blokliste** ved at bruge <https://security.microsoft.com/tenantAllowBlockList>.

2. Vælg den fane, der indeholder den type post, du vil fjerne:
   - **Afsendere**
   - **Spoofing**
   - **Webadresser**
   - **Filer**

3. Vælg den post, du vil fjerne, og klik derefter på ![Ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet**.

4. Klik på **Slet** i den viste advarselsdialogboks.

## <a name="use-powershell"></a>Brug PowerShell

### <a name="modify-allow-or-block-sender-file-and-url-entries-in-the-tenant-allowblock-list"></a>Rediger tilladelses- eller blokeringsposter for afsendere, filer og URL-adresser på listen over tilladte/blokerede lejere

Hvis du vil redigere poster for afsender, fil og URL-adresse på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Set-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

I dette eksempel ændres udløbsdatoen for den angivne blok-URL-adresse.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="remove-allow-or-block-sender-url-or-file-entries-from-the-tenant-allowblock-list"></a>Fjern tilladelses- eller blokeringsposter for afsendere, URL-adresser eller filer fra listen over tilladte/blokerede lejere

Hvis du vil fjerne afsender-, fil- og URL-adresser fra listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN">
```

I dette eksempel fjernes den angivne url-adresse for blokering fra listen over tilladte/blokerede lejere.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

### <a name="modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>Rediger poster for tillad eller blokerpooferede afsendere fra listen over tilladte/blokerede lejere

Hvis du vil ændre poster af typen Tillad eller bloker efterligning af afsendere på listen over tilladte/blokerede lejere, skal du bruge følgende syntaks:

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

I dette eksempel ændres den spoofede afsenderpost fra Allow til Block.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

### <a name="remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>Fjern tilladte eller blokerpooferede afsenderposter fra listen over tilladte/blokerede lejere

Brug følgende syntaks til at fjerne tilladelse til eller blokering af afsenderposter fra listen over tilladte/blokerede lejere:

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

Du kan finde detaljerede syntaks- og parameteroplysninger under [Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).
