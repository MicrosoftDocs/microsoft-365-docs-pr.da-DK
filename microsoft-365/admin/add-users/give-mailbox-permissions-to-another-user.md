---
title: Giv postkassetilladelser til en anden bruger – Hjælp til administratorer
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkEXCHANGE
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 1dbcf12f-a9de-4d1d-b0b3-a227f8a736d8
description: Giv en Microsoft 365 bruger ret til at få adgang til en anden brugers postkasse, hvilket gør det muligt for brugeren at læse og sende mails fra den anden brugers postkasse.
ms.openlocfilehash: 5b770b2967072ab6cc8b8abfec8176a7b6aac2c9
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042368"
---
# <a name="give-mailbox-permissions-to-another-microsoft-365-user---admin-help"></a>Giv postkassetilladelser til en anden Microsoft 365 bruger – Hjælp til administratorer

Som administrator har du muligvis virksomhedskrav for at give nogle brugere adgang til en anden brugers postkasse. Det kan f.eks. være, at du vil gøre det muligt for en assistent at sende eller læse mail fra sin chefs postkasse eller en af dine brugeres mulighed for at sende mail på vegne af en anden bruger. I dette emne kan du se, hvordan du gør dette.
  
Hvis du leder efter oplysninger om oprettelse og administration af delte postkasser, skal du se [Opret en delt postkasse](../email/create-a-shared-mailbox.md).

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist har du og dine medarbejdere adgang til specialister i små virksomheder døgnet rundt, efterhånden som du får din virksomhed til at vokse, lige fra onboarding til hverdagsbrug.
    
## <a name="looking-to-set-up-mailbox-permissions"></a>Vil du konfigurere postkassetilladelser?

Med postkassetilladelser kan du give en anden bruger læse-/skriveadgang til en postkasse. Artiklerne nedenfor kan give dig den hjælp, du har brug for til at konfigurere og bruge denne funktion:
  
 **Konfiguration af tilladelserne:**
  
Det første trin til at konfigurere tilladelser er at beslutte, hvilke handlinger du vil tillade den anden bruger at udføre i den angivne postkasse. Du kan give en bruger tilladelse til at læse mails fra postkassen, sende mails på vegne af en anden bruger og sende mails, som om de blev sendt fra den pågældende postkasse. Se følgende artikler om, hvordan du konfigurerer hver type tilladelser:
  
- [Læs mail fra en anden brugers postkasse](give-mailbox-permissions-to-another-user.md#read-email-in-another-users-mailbox)
    
- [Send mail fra en anden brugers postkasse](give-mailbox-permissions-to-another-user.md#send-email-from-another-users-mailbox)

- [Send mail på vegne af en anden bruger](give-mailbox-permissions-to-another-user.md#send-email-on-behalf-of-another-user)
    
 **Ændrer overførsel:**
  
Når du har konfigureret tilladelserne, kan det tage op til 60 minutter, før ændringerne overføres via systemet og træder i kraft.
  
 **Sådan bruges den, når tilladelserne er konfigureret:**
  
Der er et par forskellige måder, du kan få adgang til en postkasse på, når du har fået adgang. Du kan få hjælp til dette i denne artikel: [Få adgang til en anden persons postkasse](https://support.microsoft.com/office/A909AD30-E413-40B5-A487-0EA70B763081).

> [!NOTE]
> Tilladelserne kan kun konfigureres i den aktuelle organisationslejer. Det er ikke muligt at konfigurere postkassetilladelser uden for lejerbrugere.
  
## <a name="send-email-from-another-users-mailbox"></a>Send mail fra en anden brugers postkasse

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .  
    
2. Vælg navnet på den bruger (fra hvem du planlægger at give en afsendelsestilladelse) for at åbne ruden med egenskaber.
    
3. Under fanen **Mail** skal du vælge **Administrer tilladelser for postkasse**.

4. Vælg **Rediger** ud for **Send som**. 

5. Vælg **Tilføj tilladelser**, og vælg derefter navnet på den person, som brugeren skal kunne sende som. 
    
6. Vælg **Tilføj**.
 
::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> . 

2. Vælg den ønskede bruger, udvid **Mail Indstillinger**, og vælg derefter **Rediger** ud for **Tilladelser for Postkasse**.

3. Vælg **Rediger** ud for **Send som**. 

4. Vælg **Tilføj tilladelser**, og vælg derefter navnet på den person, som brugeren skal kunne sende som. 
    
5. Vælg **Tilføj**.

::: moniker-end
  
## <a name="read-email-in-another-users-mailbox"></a>Læs mail i en anden brugers postkasse

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .  
    
2. Vælg navnet på den bruger (hvis postkasse du vil tillade læsning) for at åbne ruden med egenskaber.
    
3. Under fanen **Mail** skal du vælge **Administrer tilladelser for postkasse**.
    
4. Ud for **Læs og administrer** skal du vælge **Rediger**. 
    
5. Vælg **Tilføj tilladelser**, og vælg derefter navnet på den eller de brugere, du vil tillade at læse mail fra denne postkasse.

6. Vælg **Tilføj**.


> [!NOTE]
> **Læse****- og administrer-tilladelser** kaldes **tilladelsen Fuld adgang**, når de tildeles i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. Denne tilladelse gør det muligt for den tildelte brugerpostkasse at læse og administrere mails i den brugerpostkasse, som tilladelsen er tildelt til. Tilladelsen Fuld adgang giver ikke tilladelsen **Send som** eller **Send på vegne**  af.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> . 
  
2. Vælg den ønskede bruger, udvid **Mail Indstillinger**, og vælg derefter **Rediger** ud for **Postkassetilladelser**.
    
3. Ud for **Læs og administrer** skal du vælge **Rediger**. 
    
4. Vælg **Tilføj tilladelser**, og vælg derefter navnet på den eller de brugere, du vil tillade at læse mail fra denne postkasse.

5. Vælg **Tilføj**.

::: moniker-end


## <a name="send-email-on-behalf-of-another-user"></a>Send mail på vegne af en anden bruger

::: moniker range="o365-worldwide"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Aktive brugere</a> .  

2. Vælg navnet på den bruger (fra hvem du planlægger at give tilladelsen **Send på vegne** ) for at åbne ruden med egenskaber.
    
3. Under fanen **Mail** skal du vælge **Administrer tilladelser for postkasse**.
    
4. Ud for **Send på vegne** skal du vælge **Rediger**.

5. Vælg **Tilføj tilladelser**, og vælg derefter navnet på den eller de brugere, du vil tillade at sende mail på vegne af denne postkasse.

6. Vælg **Tilføj**.

::: moniker-end

::: moniker range="o365-21vianet"

1. I Administration skal du gå til siden **Brugere** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Aktive brugere</a> . 

2. Vælg den ønskede bruger, udvid **Mail Indstillinger**, og vælg derefter **Rediger** ud for **Postkassetilladelser**.

3. Ud for **Send på vegne** skal du vælge **Rediger**.
    
4. Vælg **Tilføj tilladelser**, og vælg derefter navnet på den eller de brugere, du vil tillade at sende mail på vegne af denne postkasse.

5. Vælg **Tilføj**.

::: moniker-end

> [!NOTE]
> Tilladelserne **Send som** og **Send på vegne** fungerer ikke i Outlook Desktop-klienten med parameteren *HiddenFromAddressListsEnabled* for postkassen angivet til **Sand**, da de kræver, at postkassen er synlig i Outlook via den globale adresseliste.

## <a name="related-content"></a>Relateret indhold
  
[Administrer en anden persons mail- og kalenderelementer](https://support.microsoft.com/office/afb79d6b-2967-43b9-a944-a6b953190af5) (artikel)\   
[Send mail fra en anden person eller gruppe](https://support.microsoft.com/office/0f4964af-aec6-484b-a65c-0434df8cdb6b) (artikel)\
[Skift et brugernavn og en mailadresse](../add-users/change-a-user-name-and-email-address.md) (video)

