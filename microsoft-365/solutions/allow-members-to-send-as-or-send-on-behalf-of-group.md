---
title: Tillad, at medlemmer kan sende som eller sende på vegne af en gruppe
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
- m365solution-collabgovernance
ms.custom: admindeeplinkEXCHANGE
search.appverid:
- MET150
ms.assetid: 0ad41414-0cc6-4b97-90fb-06bec7bcf590
recommendations: false
description: Få mere at vide om, hvordan du giver gruppemedlemmer tilladelse til at sende mail som Microsoft 365 en gruppe eller sende mail på vegne af Microsoft 365 gruppe.
ms.openlocfilehash: 588008669359629f5b59498bb7dbf776112d5408
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63591336"
---
# <a name="allow-members-to-send-as-or-send-on-behalf-of-a-group"></a>Tillad, at medlemmer kan sende som eller sende på vegne af en gruppe

Et medlem af en Microsoft 365-gruppe, der har fået tilladelsen **Send** som eller **Send** på vegne af, kan sende mails som gruppen eller på vegne af gruppen. Gæster i gruppen kan ikke tildeles disse tilladelser.

I denne artikel forklares det, hvordan en global Exchange administrator kan angive disse tilladelser.
  
Hvis Megan Bowen f.eks. er en del af **gruppen Training Microsoft 365** og har **Send** som-tilladelser i gruppen, vil det se ud som om, at gruppen Uddannelse har sendt mailen, hvis hun sender en  mail som gruppen. 
  
Tilladelsen **Send på vegne** af giver en bruger mulighed for at sende mail på vegne af Microsoft 365 gruppe. Hvis Alex Wilber f.eks. er en del af gruppen **Marketing** Microsoft 365 og har tilladelsen **Send** på vegne af og sender en mail som gruppen, ser mailen ud som om, den er blevet sendt af **Alex Wilber** på vegne af Marketing.

> [!IMPORTANT]
> Du kan konfigurere **Send som eller** **Send på vegne af** for en given bruger, men ikke begge dele. Hvis du konfigurerer begge, vil den som standard **sende som**.

> [!NOTE]
> **Send som** og **Send på vegne af** understøttes ikke på Outlook til Mac i Exchange konfigurationer.
    
## <a name="allow-members-to-send-email-as-a-group"></a>Tillad medlemmer at sende mail som en gruppe

I dette afsnit forklares det, hvordan du giver brugerne mulighed for at sende mail som en gruppe <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration (EAC)</a> i Exchange Online.
  
1. I Exchange Administration skal du gå **til Modtagergrupper**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>
    
2. Vælg den gruppe, du vil give brugere tilladelse til at sende som. 
    
3. Vælg **Indstillinger** >  **Edit administrer stedfortrædere**.
    
4. I sektionen **Tilføj en stedfortræder** skal du angive mailadressen på den bruger, du vil have **Send som** adgang til.
  
5. Vælg **Tilladelsestype** **som Send** som på rullelisten.

6.  Vælg **Gem ændringer**.
    
    
## <a name="allow-members-to-send-email-on-behalf-of-a-group"></a>Tillad, at medlemmer kan sende mail på vegne af en gruppe

I dette afsnit forklares det, hvordan du giver brugere tilladelse til at sende mail på vegne af en <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">gruppe i Exchange Administration (EAC)</a> i Exchange Online.
  
1. I Exchange Administration skal du gå **til Modtagergrupper**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>
    
2. Vælg den gruppe, du vil give brugere tilladelse til at sende på vegne af. 
    
3. Vælg **Indstillinger** >  **Edit administrer stedfortrædere**.
    
4. I sektionen **Tilføj en stedfortræder** skal du angive mailadressen på den bruger, du vil have **Send som** adgang til.
  
5. Vælg **Tilladelsestype** **som Send på** vegne af på rullelisten.

6.  Vælg **Gem ændringer**.

## <a name="related-articles"></a>Relaterede artikler

[Send mail fra eller på vegne af en Microsoft 365 gruppe](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b)

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Få mere at vide Microsoft 365 grupper](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Tilføjelsesmodtager](/powershell/module/exchange/add-recipientpermission)

[Set-UnifiedGroup](/powershell/module/exchange/set-unifiedgroup)
