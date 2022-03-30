---
title: Tildel roller og tilladelser i Microsoft Defender for Business
description: Få mere at vide om, hvordan du tildeler roller og tilladelser i Microsoft Defender for Business
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: e18fa5e2c52e76b6920e5aa604ebe0b0ba8a46f1
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63598567"
---
# <a name="assign-roles-and-permissions-in-microsoft-defender-for-business"></a>Tildel roller og tilladelser i Microsoft Defender for Business

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

Hvis du vil udføre opgaver på Microsoft 365 Defender-portalen, f.eks. konfiguration af Microsoft Defender for Business, visning af rapporter eller udførelse af svarhandlinger vedrørende registrerede trusler, skal relevante tilladelser tildeles til sikkerhedsteamet. Tilladelser tildeles gennem roller, der er tildelt i Microsoft 365 Defender portalen ([https://security.microsoft.com](https://security.microsoft.com)) eller i [Azure Active Directory](/azure/active-directory/roles/manage-roles-portal). 

## <a name="what-to-do"></a>Hvad kan du gøre?

1. [Få mere at vide om roller i Defender for Business](#roles-in-defender-for-business).

2. [Få vist eller rediger rolletildelinger for dit sikkerhedsteam](#view-or-edit-role-assignments).

3. [Fortsæt til de næste trin](#next-steps).

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>


## <a name="roles-in-defender-for-business"></a>Roller i Defender for Business

I følgende tabel beskrives de tre roller, der kan tildeles i Defender for Business. [Få mere at vide om administratorroller](../../admin/add-users/about-admin-roles.md). <br/><br/>

| Tilladelsesniveau | Beskrivelse |
|:---|:---|
| **Globale administratorer** (også kaldet globale administratorer) <br/><br/> *Som bedste fremgangsmåde skal du begrænse antallet af globale administratorer.* | Globale administratorer kan udføre alle typer opgaver. Den person, der tilmeldte sig din virksomhed Microsoft 365 til Microsoft Defender for Business, er som standard global administrator. <br/><br/> Globale administratorer kan få adgang til/ændre indstillinger på tværs af Microsoft 365 portaler, f.eks.: <br/>- Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com)) <br/>- Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) |
| **Sikkerhedsadministratorer** (også kaldet sikkerhedsadministratorer) | Sikkerhedsadministratorer kan udføre følgende opgaver: <br/>- Få vist og administrere sikkerhedspolitikker <br/>- Få vist og administrere sikkerhedstrusler og beskeder (disse aktiviteter omfatter at tage svarhandlinger på slutpunkter) <br/>- Få vist sikkerhedsoplysninger og rapporter |
| **Sikkerhedslæser** | Sikkerhedslæsere kan udføre følgende opgaver: <br/>- Få vist sikkerhedspolitikker <br/>- Få vist sikkerhedstrusler og beskeder <br/>- Få vist sikkerhedsoplysninger og rapporter  |


## <a name="view-or-edit-role-assignments"></a>Få vist eller rediger rolletildelinger

1. Gå til Microsoft 365 Defender -portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. I navigationsruden skal du **vælge Tilladelser & roller**, og derefter skal du under **Azure AD** vælge **Roller**.

3. Vælg en af følgende roller for at åbne sideruden:

   - Global administrator
   - Sikkerhedsadministrator
   - Sikkerhedslæser

   > [!IMPORTANT]
   > Microsoft anbefaler, at du kun giver personer adgang til det, de skal bruge for at udføre deres opgaver. Vi kalder dette *mindste rettighedskoncept* for tilladelser. Du kan få mere at vide [under Bedste fremgangsmåder for adgang med de mindste rettigheder til programmer](/azure/active-directory/develop/secure-least-privileged-access). 

4. I sideruden skal du vælge **linket Administrer medlemmer i Azure AD** . Denne handling fører dig til Azure Active Directory (Azure AD), hvor du kan få vist og administrere dine rolletildelinger.

5. Vælg en bruger for at åbne sin profil, og vælg derefter **Tildelte roller**.

   - Hvis du vil tilføje en rolle, skal **du vælge + Tilføj opgaver**.
   - Hvis du vil fjerne en rolle, skal **du vælge X Fjern tildelinger**. 

## <a name="next-steps"></a>Næste trin

Fortsæt til:

- [Trin 3: Konfigurer mailbeskeder](mdb-email-notifications.md)

- [Trin 4: Onboard-enheder til Microsoft Defender for Business](mdb-onboard-devices.md)