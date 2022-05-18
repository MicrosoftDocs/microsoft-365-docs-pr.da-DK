---
title: Send mail som en distributionsliste
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
- Adm_O365
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: a7c98273-067e-4162-b3a1-4ba081796012
description: Send mail som en distributionsliste i Microsoft 365, så når et medlem besvarer en meddelelse, ser det ud til at være fra distributionslisten.
ms.openlocfilehash: dd6e1f906481fe1c04bfa7cd275bd108ab558d59
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/18/2022
ms.locfileid: "65468454"
---
# <a name="send-microsoft-365-email-as-a-distribution-list"></a>Send Microsoft 365 mail som en distributionsliste

I Microsoft 365 kan du sende mail som en distributionsliste. Når en person, der er medlem af distributionslisten, besvarer en meddelelse, der er sendt til distributionslisten, ser mailen ud til at være fra distributionslisten og ikke fra den enkelte bruger. I dette emne kan du se, hvordan du gør det.
  
## <a name="before-you-begin"></a>Før du begynder

Før du udfører disse trin, skal du kontrollere, at du er føjet til en Microsoft 365 distributionsliste, og at du har fået tildelt tilladelsen Send som til den.
  
 **Administratorer**: Sørg for, at du har fulgt trinnene i [Føj en Microsoft 365 bruger eller kontakt til en liste](../email/add-user-or-contact-to-distribution-list.md) og [Tillad, at medlemmer sender mail som Microsoft 365 gruppeemner](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md#allow-members-to-send-email-as-a-group), og føj de korrekte personer til distributionslisten.
  
## <a name="outlook-on-the-web"></a>Outlook på internettet

1. Åbn Outlook på internettet, og gå til din indbakke. 
    
2. Åbn en meddelelse, der blev sendt til distributionslisten. 
    
3. Vælg **Svar**. 
    
4. Nederst i meddelelsen skal du vælge **Flere** \> **vis fra**.<br/> ![Vælg Mere, og vælg derefter Vis fra.](../../media/534f13b7-9f15-48ea-8835-ea2ed1863ece.png)
  
5. Højreklik på adressen Fra , f.eks `Ina@weewalter.me` . - og vælg **Fjern**.<br/> ![Fjern aliasset FROM.](../../media/9b8d8e8f-dc46-499c-89bd-0a480603bf1f.png)
  
6. Skriv derefter adressen på distributionslisten, f.eks. support@contoso.com, og send meddelelsen. Næste gang du svarer fra distributionslisten, vises adressen som en indstilling på listen **Fra** .<br/>![Aliasset for den delte postkasse vises.](../../media/f7632a9a-9cab-446c-9e37-23ef50c5b975.png)

## <a name="outlook"></a>Outlook

1. Åbn Outlook desktopklient.

2. Opret en ny mail. Klik på feltet **Fra** , og vælg **Anden mailadresse**. Hvis du ikke kan se feltet Fra, skal du navigere til **Indstillinger** og vælge **Fra** i afsnittet Vis felter.

3. Vælg adressen på **distributionslisten** på den globale adresseliste.

4. Send mailen.

## <a name="related-content"></a>Relateret indhold

[Opret, rediger eller slet en sikkerhedsgruppe i Microsoft 365 Administration](../email/create-edit-or-delete-a-security-group.md) (artikel)\
[Mailsamarbejde](../email/email-collaboration.md) (artikel)\
[Føj en bruger eller kontakt til en distributionsgruppe](../email/add-user-or-contact-to-distribution-list.md) (artikel)