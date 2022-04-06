---
title: Rediger og fjern poster i lejerens tilladelses-/blokeringsliste
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
description: Administratorer kan få mere at vide om, hvordan de redigerer og fjerner poster på lejerens liste over tilladte/blokerede elementer i sikkerhedsportalen.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f1ab3f815cc64af6d1383df228ef7961c3afdcec
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63606644"
---
# <a name="modify-and-remove-entries-in-the-tenant-allowblock-list"></a>Rediger og fjern poster i lejerens tilladelses-/blokeringsliste

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Du kan bruge Microsoft 365 Defender-portalen eller PowerShell til at ændre og fjerne poster på lejerens tilladelses-/blokeringsliste.

## <a name="use-the-microsoft-365-defender-portal"></a>Brug Microsoft 365 Defender portalen

### <a name="modify-entries-in-the-tenant-allowblock-list"></a>Rediger poster i lejerens tilladelses-/blokeringsliste

1. I portalen Microsoft 365 Defender skal du  gå til **Politikker & regler** \>  \> for trusselspolitikker i **afsnittet Lejers**\> tilladelses-/blokeringslister.

2. Vælg den fane, der indeholder den type indtastning, du vil ændre:
   - **Afsendere**
   - **Spoofing**
   - **URL-adresser**
   - **Filer**


3. Markér det element, du vil ændre, og klik derefter på ![Ikonet Rediger.](../../media/m365-cc-sc-edit-icon.png) **Rediger**. De værdier, du kan ændre i pop op-pop-siden, afhænger af den fane, du valgte i forrige trin:
   - **Afsendere**
     - **Udløber aldrig** og/eller udløbsdato.
     - **Valgfri note**
   - **Spoofing**
     - **Handling**: Du kan ændre værdien til **Tillad** eller **Bloker**.
   - **URL-adresser**
     - **Udløber aldrig** og/eller udløbsdato.
     - **Valgfri note**
   - **Filer**
     - **Udløber aldrig** og/eller udløbsdato.
     - **Valgfri note**

4. Klik på **Gem**, når du er færdig.

> [!NOTE]
> Du kan kun udvide og giver mulighed for maksimalt 30 dage efter oprettelsesdatoen. Blokke kan forlænges i op til 90 dage, men i modsætning til dette kan de også indstilles til Udløber aldrig.

### <a name="remove-entries-from-the-tenant-allowblock-list"></a>Fjern poster fra lejerens tilladelses-/blokeringsliste

1. I portalen Microsoft 365 Defender skal du  gå til **Politikker & regler** \>  \> for trusselspolitikker i **afsnittet Lejers**\> tilladelses-/blokeringslister.

2. Vælg den fane, der indeholder den type post, du vil fjerne:
   - **Afsendere**
   - **Spoofing**
   - **URL-adresser**
   - **Filer**
 
3. Markér den post, du vil fjerne, og klik derefter på ![ikonet Slet.](../../media/m365-cc-sc-delete-icon.png) **Slet**.

4. Klik på Slet i den dialogboks, der vises med **advarslen**.

## <a name="use-powershell"></a>Brug PowerShell

### <a name="modify-allow-or-block-sender-file-and-url-entries-in-the-tenant-allowblock-list"></a>Rediger tillade eller blokere afsender-, fil- og URL-poster på lejerens tilladelses-/blokeringsliste

Hvis du vil ændre tilladte eller blokere afsender-, fil- og URL-poster på lejerens tilladelses-/blokeringsliste, skal du bruge følgende syntaks:

```powershell
Set-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

I dette eksempel ændres udløbsdatoen for den angivne URL-adresse for blokering.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="remove-allow-or-block-sender-url-or-file-entries-from-the-tenant-allowblock-list"></a>Fjern tillad eller bloker afsender-, URL- eller filposter fra lejerens tilladelses-/blokeringsliste

Hvis du vil fjerne tilladte eller blokere afsender-, fil- og URL-poster fra lejerens tilladelses-/blokeringsliste, skal du bruge følgende syntaks:

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN">
```

I dette eksempel fjernes den angivne URL-adresse for blokering fra lejerens tilladelses-/blokeringsliste.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

### <a name="modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>Rediger tillad eller bloker efterlignede afsenderposter fra lejerens tilladelses-/blokeringsliste

Hvis du vil ændre tillad eller blokere efterlignede afsenderposter i lejerens tilladelses-/blokeringsliste, skal du bruge følgende syntaks:

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

I dette eksempel ændres efterlignet afsenderpost fra Tillad til blokering.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

Du kan finde detaljerede oplysninger om syntaks og [parameter i Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

### <a name="remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>Fjern tillad eller bloker efterlignede afsenderposter fra lejerens tilladelses-/blokeringsliste
 
Hvis du vil fjerne tillade eller blokere spoof afsenderposter fra lejerens tilladelses-/blokeringsliste, skal du bruge følgende syntaks:

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

Du kan finde detaljerede oplysninger om syntaks og parameter [i Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).
