---
title: Føj et andet mailalias til en bruger
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
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 0b0bd900-68b1-4bf5-808b-5d240a7739f4
description: 'Få mere at vide om, hvordan du kan have mere end én mailadresse, der kaldes et mailalias, tilknyttet din Microsoft 365 til virksomhedskonto. '
ms.openlocfilehash: 19303cb2c60455713595dbe23a23bae7e57efb71
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780209"
---
# <a name="add-another-email-alias-for-a-user"></a>Føj et andet mailalias til en bruger
  
Denne artikel henvender sig til Microsoft 365 administratorer, der har virksomhedsabonnementer. Det er ikke til private brugere.
  
En primær mailadresse i Microsoft 365 er normalt den mailadresse, en bruger blev tildelt, da vedkommendes konto blev oprettet. Når brugeren sender en mail til en anden, vises vedkommendes primære mailadresse normalt i feltet  *Fra*  i mailapps. De kan også have mere end én mailadresse tilknyttet deres Microsoft 365 til virksomhedskonto. Disse ekstra adresser kaldes aliasser. 
  
Lad os f.eks. sige, at Jenna har mailadressen jenna@contosoco.com, men hun ønsker også at modtage e-mail på jen@contosoco.com, fordi nogle mennesker henviser til hende ved det navn. Du kan oprette aliasser for hende, så begge mailadresser går til Jennas indbakke.
  
Du kan oprette op til 400 aliasser for en bruger. Der kræves ingen ekstra gebyrer eller licenser.
  
> [!Tip]
> Hvis flere personer skal administrere mails, der sendes til en enkelt mailadresse, f.eks. info@NodPublishers.com eller sales@NodPublishers.com, skal du oprette en delt postkasse. Du kan få mere at vide under [Opret en delt postkasse](create-a-shared-mailbox.md).

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft-specialist i mindre virksomheder](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til specialister i mindre virksomheder, efterhånden som du udvikler din virksomhed – lige fra onboarding til daglig brug.
  
## <a name="add-email-aliases-to-a-user"></a>Føj mailaliasser til en bruger

Du skal have rettigheder som global administrator for at føje mailaliasser til en bruger.

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .

2. På siden **Aktive brugere** skal du vælge den bruger, > **Administrer brugernavn og mail**. Du kan ikke se denne indstilling, hvis personen ikke har fået tildelt en licens. 
    
3. Vælg **+ Tilføj et alias** , og angiv et nyt alias for brugeren.   
    
    > [!Important] 
    > Hvis du får vist fejlmeddelelsen "**Der blev ikke fundet en parameter, der svarer til parameternavnet 'EmailAddresses**', betyder det, at det tager lidt længere tid at konfigurere din lejer eller dit brugerdefinerede domæne, hvis du for nylig har tilføjet et. Det kan tage op til fire timer at fuldføre konfigurationsprocessen. Vent et stykke tid, så konfigurationsprocessen har tid til at afslutte, og prøv derefter igen. Hvis problemet fortsætter, skal du ringe til Support, så udfører de en fuld synkronisering for dig.
    
  
    > [!IMPORTANT]
    > Hvis du har købt dit abonnement fra GoDaddy eller en anden partner, skal du gå til GoDaddy/partneradministrationskonsollen for at angive det nye alias som det primære. 


   > [!IMPORTANT]
   >  Hvis du får vist fejlmeddelelsen **Denne bruger synkroniseres med dit lokale Active Directory. Nogle detaljer kan kun redigeres via dit lokale Active Directory**. Det betyder, at Active Directory er autoritativt for attributter for synkroniserede brugere. Du skal ændre attributterne i din Active Directory i det lokale miljø.
  
    > [!TIP]
    > Mailaliaset skal slutte med et domæne på rullelisten. Hvis du vil føje et andet domænenavn til listen, skal du se [Føj et domæne til Microsoft 365](../setup/add-domain.md). 
  
     
5. Når du er færdig, skal du vælge **Gem ændringer**.
    
6. Vent 24 timer, indtil de nye aliasser udfyldes i hele Microsoft 365.
    
    Brugeren har nu en primær adresse og et alias. Alle mails, der sendes til Eliza Hoffmans primære adresse, Eliza@NodPublishers.com, og hendes alias, Sales@NodPublishers.com, går f.eks. til Elizas indbakke.
    
  
7. **Når brugeren svarer, afhænger *Fra-adressen* af hendes Outlook klient. Outlook på internettet bruger aliasset, hvor mailen blev modtaget (vi kalder dette ping-pong-princippet). Outlook desktop bruger sit primære mailalias.** Lad os f.eks. sige, at der sendes en meddelelse til Sales@NodPublishers.com, og den ankommer i Elizas indbakke. Når Eliza svarer på meddelelsen ved hjælp af Outlook desktop, vises hendes primære mailadresse som Eliza@NodPublishers.com, ikke Sales@NodPublishers.com.
    
## <a name="did-you-get-a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>Fik du "Der blev ikke fundet en parameter, der svarer til parameternavnet EmailAddresses"?

Hvis du får vist fejlmeddelelsen "**En parameter blev ikke fundet, der svarer til parameternavnet EmailAddresses**", betyder det, at det tager lidt længere tid at fuldføre indstillingerne for din lejer eller dit brugerdefinerede domæne, hvis du for nylig har tilføjet et. Det kan tage op til fire timer at fuldføre konfigurationsprocessen. Vent et stykke tid, så konfigurationsprocessen har tid til at afslutte, og prøv derefter igen. Hvis problemet fortsætter, skal du ringe til Support, så udfører de en fuld synkronisering for dig.
  
## <a name="did-you-purchase-your-subscription-from-godaddy-or-another-partner"></a>Har du købt dit abonnement fra GoDaddy eller en anden partner?


Hvis du har købt dit abonnement fra GoDaddy eller en anden partner, skal du gå til GoDaddy/partneradministrationskonsollen for at angive det nye alias som det primære.

## <a name="sending-email-from-the-proxy-address-easily"></a>Det er nemt at sende mail fra proxyadressen

En ny funktion udrulles i juli 2021, der gør det nemt for brugerne at sende fra deres aliasser, når de bruger Outlook på internettet. Når funktionen udrulles til en lejer, hvor lejeradministratoren bruger cmdlet'en`Set-OrganizationConfig -SendFromAliasEnabled $true`, får brugere i lejeren adgang til en liste over afkrydsningsfelter, hvor hver post svarer til et alias i indstillingerne for deres Outlook. Hvis du vælger et alias, vises det på rullelisten Fra i formularen Meddelelse.
  
## <a name="related-content"></a>Relateret indhold

[Send mail fra en anden adresse](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (artikel)

[Skift et brugernavn og en mailadresse](../add-users/change-a-user-name-and-email-address.md) (artikel)

[Konfigurer videresendelse af mail i Microsoft 365](configure-email-forwarding.md) (artikel)
