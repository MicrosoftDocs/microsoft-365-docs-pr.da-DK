---
title: Tilføje et andet mailalias for en bruger
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
description: 'Få mere at vide om, hvordan du kan have mere end én mailadresse, kaldet et mailalias, der er knyttet Microsoft 365 for business-konto. '
ms.openlocfilehash: f5adc9e48110aa1e2a2e6c87f2c2f7847986d741
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/12/2022
ms.locfileid: "63599761"
---
# <a name="add-another-email-alias-for-a-user"></a>Tilføje et andet mailalias for en bruger
  
Denne artikel gælder for Microsoft 365 administratorer, der har erhvervsabonnementer. Det er ikke for private brugere.
  
En primær mailadresse i Microsoft 365 er som regel den mailadresse, en bruger blev tildelt, da brugerens konto blev oprettet. Når brugeren sender en mail til en anden, vises deres primære mailadresse typisk i  *feltet Fra*  i mailapps. De kan også have mere end én mailadresse knyttet til deres Microsoft 365 for business-konto. Disse yderligere adresser kaldes aliasser. 
  
Lad os f.eks. sige, at Jenna har mailadressen jenna@contosoco.com, men at hun også gerne vil modtage mails på jen@contosoco.com, fordi hun også går under det navn. Du kan oprette aliasser for hende, så begge mailadresser sendes til Jennas indbakke.
  
Du kan oprette op til 400 aliasser for en bruger. Der opkræves ingen ekstra gebyrer, og du behøver ikke at betale yderligere licenser.
  
> [!Tip]
> Hvis du vil have flere personer til at administrere mails, der sendes til en enkelt mailadresse som f.info@NodPublishers.com eller sales@NodPublishers.com, skal du oprette en delt postkasse. Du kan få mere at vide [under Opret en delt postkasse](create-a-shared-mailbox.md).

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.
  
## <a name="add-email-aliases-to-a-user"></a>Føje mailaliasser til en bruger

Du skal have globale administratorrettigheder for at føje mailaliasser til en bruger.

1. I Administration skal du gå til **siden Aktive** \> brugere <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">for</a> brugere.

2. På siden **Aktive brugere** skal du vælge > **Administrer brugernavn og mail**. Du får ikke vist denne indstilling, hvis personen ikke har fået tildelt en licens. 
    
3. Vælg **+ Tilføj et alias** , og angiv et nyt alias for brugeren.   
    
    > [!Important] 
    > Hvis fejlmeddelelsen " Der blev ikke fundet en parameter, der svarer til **parameternavnet "Mailadresser**" vises, betyder det, at det tager lidt længere tid at fuldføre konfigurationen af din lejer eller dit brugerdefinerede domæne, hvis du for nyligt tilføjede et. Installationen kan tage op til fire timer at gennemføre. Vent lidt, så installationen kan blive fuldført, og prøv derefter igen. Hvis problemet fortsætter, skal du ringe til Support, som så vil udføre en fuld synkronisering for dig.
    
  
    > [!IMPORTANT]
    > Hvis du har købt dit abonnement hos GoDaddy eller en anden partner, skal du gå til GoDaddy/partneradministrationskonsollen for at angive det nye alias som primært. 


   > [!IMPORTANT]
   >  Hvis du får fejlmeddelelsen **Denne bruger er synkroniseret med din lokale Active Directory. Nogle detaljer** kan kun redigeres via dit lokale Active Directory, det betyder, at Active Directory er autoritativt for attributter på synkroniserede brugere, du skal ændre attributterne i dit lokale Active Directory.
  
    > [!TIP]
    > Mailaliasset skal slutte med et domæne fra rullelisten. Hvis du vil føje et andet domænenavn til listen, skal [du se Føje et domæne Microsoft 365](../setup/add-domain.md). 
  
     
5. Vælg Gem ændringer, når du er **færdig**.
    
6. Vent 24 timer, før de nye aliasser udfyldes Microsoft 365.
    
    Brugeren har nu en primær adresse og et alias. Alle mails, der f.eks. sendes til Elizas primære adresse, Eliza@NodPublishers.com og hendes alias, Sales@NodPublishers.com, går til Elizas indbakke.
    
  
7. **Når brugeren svarer, afhænger *Fra-adressen* af hendes Outlook klient. Outlook på internettet vil bruge aliasset, hvor mailen blev modtaget (vi kalder dette ping-pong-princippet). Outlook skrivebord bruger hendes primære mailalias.** Lad os f.eks. sige, at der sendes en meddelelse til Sales@NodPublishers.com, og den ankommer i Elizas indbakke. Når Eliza svarer på meddelelsen ved hjælp Outlook skrivebord, vises hendes primære mailadresse som Eliza@NodPublishers.com, ikke Sales@NodPublishers.com.
    
## <a name="did-you-get-a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>Fik du vist "Der blev ikke fundet en parameter, der svarer til parameternavnet Mailadresser"?

Hvis fejlmeddelelsen "Der blev ikke fundet en parameter, der svarer til **parameternavnet Mailadresser**" vises, betyder det, at det tager lidt længere tid at fuldføre konfigurationen af din lejer eller dit brugerdefinerede domæne, hvis du for nylig har tilføjet et. Installationen kan tage op til fire timer at gennemføre. Vent lidt, så installationen kan blive fuldført, og prøv derefter igen. Hvis problemet fortsætter, skal du ringe til Support, som så vil udføre en fuld synkronisering for dig.
  
## <a name="did-you-purchase-your-subscription-from-godaddy-or-another-partner"></a>Har du købt dit abonnement hos GoDaddy eller en anden Partner?


Hvis du har købt dit abonnement hos GoDaddy eller en anden partner, skal du gå til GoDaddy/partneradministrationskonsollen for at angive det nye alias som primært.

## <a name="sending-email-from-the-proxy-address-easily"></a>Det er nemt at sende mail fra proxyadressen

En ny funktion udrulles i juli 2021, der gør det nemt for brugerne at sende fra deres aliasser, når de bruger Outlook på internettet. Når funktionen udrulles `Set-OrganizationConfig -SendFromAliasEnabled $true` til et lejemål, hvor lejeradministratoren bruger cmdlet'en, får brugere inden for lejeren adgang til en liste over afkrydsningsfelter, hvor hver post svarer til et alias i deres Outlook-indstillinger. Når du vælger et alias, vises det på rullelisten Fra i formularen Opret.
  
## <a name="related-content"></a>Relateret indhold

[Send mail fra en anden adresse](https://support.microsoft.com/office/ccba89cb-141c-4a36-8c56-6d16a8556d2e) (artikel)

[Ændre et brugernavn og en mailadresse](../add-users/change-a-user-name-and-email-address.md) (artikel)

[Konfigurere videresendelse af mail i Microsoft 365](configure-email-forwarding.md) (artikel)
