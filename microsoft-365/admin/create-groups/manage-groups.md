---
title: Administrere en gruppe i Administration
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 74a1ef8b-3844-4d08-9980-9f8f7a36000f
description: Lær at administrere Microsoft 365 grupper, herunder tilføje fjerne gruppemedlemmer, redigere mailadresse, gruppenavn eller beskrivelse og tilpasse den måde, gruppen fungerer på.
ms.openlocfilehash: e04d91219f1bfd51b609b9be749bd98c2798a52a
ms.sourcegitcommit: 954c8af658adb270fe843991e048c6a30e86e77c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/06/2022
ms.locfileid: "63587440"
---
# <a name="manage-a-group-in-the-microsoft-365-admin-center"></a>Administrer en gruppe i Microsoft 365 Administration

Når du har [oprettet en Microsoft 365 gruppe](create-groups.md) og tilføjet gruppemedlemmer, kan du konfigurere din gruppe. Du kan redigere gruppenavnet eller -beskrivelsen, administrere ejere eller medlemmer og angive, om eksterne afsendere kan sende mails til gruppen, og om der skal sendes kopier af gruppesamtaler til medlemmer.

Gå til Microsoft 365 Administration på [https://admin.microsoft.com](https://admin.microsoft.com).

## <a name="edit-the-group-name-or-description"></a>Rediger gruppenavnet eller -beskrivelsen

1. I Administration skal du udvide **Grupper** og derefter klikke på <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupper**</a>.

2. Vælg den gruppe, du vil redigere, og klik derefter på **Rediger navn og beskrivelse**.

3. Opdater navn og beskrivelse, og vælg derefter **Gem**.

## <a name="manage-group-owners-and-members"></a>Administrer gruppeejere og -medlemmer

1. I Administration skal du udvide **Grupper** og derefter klikke på <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupper**</a>.

2. Klik på navnet på den gruppe, du vil administrere, for at åbne ruden med indstillinger.

3. På fanen **Medlemmer** skal du vælge, om du vil administrere ejere eller medlemmer.

4. Vælg **Tilføj for** at tilføje en person, eller klik **på X** for at fjerne en person.

5. Klik **på Luk**.

## <a name="send-copies-of-conversations-to-group-members-inboxes"></a>Send kopier af samtaler til gruppemedlemmers indbakker
  
Når du bruger Administration til at oprette en gruppe, får brugerne som standard ikke kopier af gruppemails sendt til deres indbakker, selvom brugerne får kopier af gruppemødeinvitationer sendt til deres indbakker. De skal gå til gruppen for at få vist samtaler. Du kan ændre denne indstilling i Administration.

Når du slår denne indstilling til, får gruppemedlemmerne en kopi af gruppemails og mødeinvitationer sendt til deres Outlook indbakke. De kan læse og slette denne kopi af mailen uden at påvirke andre personer. Der findes stadig en kopi af mailen i gruppens indbakke.

Gruppemedlemmer kan fravælge at modtage disse mails ved at vælge at holde op med at følge gruppen Outlook.

1. I Administration skal du udvide **Grupper** og derefter klikke på <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupper**</a>.

2. Klik på navnet på den gruppe, du vil administrere, for at åbne ruden med indstillinger.

3. På fanen **Indstillinger** skal du vælge **Send** kopier af gruppesamtaler og -begivenheder til gruppemedlemmer, hvis du ønsker, at medlemmer skal modtage kopier af gruppemeddelelser og kalenderelementer i deres egen indbakke.

4. Vælg **Gem**.

## <a name="let-people-outside-the-organization-email-the-group"></a>Giv personer uden for organisationen lov til at sende mails til gruppen

Denne indstilling er god, hvis du vil have en firmamailadresse som f.eks info@contoso.com.
 
1. I Administration skal du udvide **Grupper** og derefter klikke på <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupper**</a>.

2. Klik på navnet på den gruppe, du vil administrere, for at åbne ruden med indstillinger.

3. På listen Grupper i Administration skal du vælge navnet på den gruppe, du vil ændre, og derefter skal du på fanen **Indstillinger** vælge Tillad eksterne afsendere at sende mails til **denne gruppe**.
    
4. Vælg **Gem**.

> [!NOTE]
> Det kan tage op til 30 minutter, før brugere uden for organisationen kan sende mails til gruppen.

## <a name="permanently-delete-a-microsoft-365-group"></a>Slet en Microsoft 365 permanent

Nogle gange kan det være en god ide at slette en gruppe permanent uden at vente på, at perioden for blød sletning på 30 dage udløber. Det gør du ved at starte PowerShell og køre denne kommando for at hente gruppens objekt-id:
 
 ```powershell
Get-AzureADMSDeletedGroup
```

Vær opmærksom på objekt-id'et for den gruppe eller de grupper, du vil slette permanent.
  
> [!CAUTION]
> Når du fjerner gruppen, fjernes gruppen og dens data permanent. 
  
Hvis du vil fjerne gruppen, skal du køre denne kommando i PowerShell:

```powershell
Remove-AzureADMSDeletedDirectoryObject -Id <objectId>
```

Du bekræfter, at gruppen er blevet slettet, ved at køre cmdlet'en  *Get-AzureADMSDeletedGroup*  igen for at bekræfte, at gruppen ikke længere vises på listen over blød-slettede grupper. I nogle tilfælde kan det tage helt op til 24 timer, før gruppen og alle dens data er blevet slettet permanent. 
  
## <a name="related-articles"></a>Relaterede artikler

[Opret en Microsoft 365 gruppe](create-groups.md)

[Administrer gæsteadgang til Microsoft 365 Grupper](https://support.microsoft.com/office/bfc7a840-868f-4fd6-a390-f347bf51aff6)

[Vælg domænet, der skal bruges, når du Microsoft 365 grupper](../../solutions/choose-domain-to-create-groups.md)

[Tillad, at medlemmer kan sende som eller sende på vegne af Microsoft 365 gruppe](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md)

[Opgradere distributionslister til Microsoft 365 grupper](../manage/upgrade-distribution-lists.md)

[Administrer Microsoft 365 grupper med PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md)
