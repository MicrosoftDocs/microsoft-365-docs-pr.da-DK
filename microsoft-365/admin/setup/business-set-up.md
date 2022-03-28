---
title: Konfigurer Microsoft 365 Business Premium
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
f1.keywords:
- O365E_M365SetupBanner
- BCS365_M365SetupBanner
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- TRN_SMB
- Adm_TOC
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MSB365
- OKR_SMB_M365
- TRN_M365B
- OKR_SMB_Videos
- seo-marvel-mar
- AdminSurgePortfolio
- adminvideo
search.appverid:
- BCS160
- MET150
ms.assetid: 6e7a2dfd-8ec4-4eb7-8390-3ee103e5fece
description: Opdag konfigurationstrinnene til Microsoft 365 Business Premium, herunder at tilføje et domæne og brugere, konfigurere sikkerhedspolitikker og meget mere.
ms.openlocfilehash: b4d12d34e535a58c952a752fca63af6f67e30a61
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63598055"
---
# <a name="set-up-microsoft-365-business-premium-in-the-setup-wizard"></a>Konfigurer Microsoft 365 Business Premium i konfigurationsguiden

## <a name="watch-overview-of-microsoft-365-setup"></a>Se: Oversigt over Microsoft 365 konfiguration

Watch this video for an overview of Microsoft 365 Business Premium setup.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4jZwg] 

## <a name="watch-set-up-microsoft-365-business-premium"></a>Se: Konfigurer Microsoft 365 Business Premium

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ?autoplay=false]

1. Log <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">på Microsoft 365 Administration,</a> og vælg **Gå til konfiguration**. Konfigurationsguiden starter.
1. Når konfigurationen er fuldført, skal du gå tilbage til Microsoft Administration. I Administration kan du fortsætte med at konfigurere funktioner som f.Windows 10 politikker, DLP osv. på **siden** Konfiguration.

## <a name="add-your-domain-users-and-set-up-policies"></a>Tilføj dit domæne, brugere, og konfigurer politikker

Når du køber Microsoft 365 Business Premium, har du mulighed for at bruge et domæne, som du ejer, eller at købe et [under tilmeldingen](../admin-overview/sign-up-for-office-365.md).

- Hvis du har købt et nyt domæne, da du tilmeldte dig, er dit domæne helt konfigureret, og du kan flytte [til Tilføj brugere og tildele licenser](#add-users-and-assign-licenses).

### <a name="add-your-domain-to-personalize-sign-in"></a>Tilføj dit domæne for at tilpasse logon

1. Log på Microsoft 365 Administration [ved](https://admin.microsoft.com) hjælp af dine globale legitimationsoplysninger. 

2. Vælg **Gå til konfiguration** for at starte guiden.

    ![Vælg Gå til konfiguration.](../../media/gotosetupinadmincenter.png)

3. På siden **Installér Office apps** kan du også installere appsene på din egen computer.
    
4. I **trinnet Tilføj** domæne skal du skrive det domænenavn, du vil bruge (f.eks. contoso.com).

    > [!IMPORTANT]
    > Hvis du har købt et domæne under tilmeldingen, kan du ikke se **Tilføj et domænetrin** her. Gå til [Tilføj brugere i](#add-users-and-assign-licenses) stedet.

    ![Skærmbillede af siden Tilpas din logon.](../../media/adddomain.png)

    
4. Følg trinnene i guiden for [at oprette DNS-poster hos en hvilken som helst DNS-udbyder for Microsoft 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider), der bekræfter, at du ejer domænet. Hvis du kender din domænevært, kan du se [også Føj et domæne til Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Hvis din udbyder er GoDaddy eller en anden vært aktiveret med domænetilslutning [, er](/office365/admin/get-help-with-domains/domain-connect) processen let, og du vil automatisk blive bedt om at logge på og lade Microsoft godkende på dine vegne.

    ![På siden Bekræft adgang på GoDaddy skal du vælge Godkend.](../../media/godaddyauth.png)

### <a name="add-users-and-assign-licenses"></a>Tilføj brugere, og tildel licenser

Du kan tilføje brugere i guiden, men du kan [også tilføje brugere](../add-users/add-users.md) senere i Administration. Hvis du har en lokal domænecontroller, kan du desuden tilføje brugere med [Azure AD Forbind](/azure/active-directory/hybrid/how-to-connect-install-express).

#### <a name="add-users-in-the-wizard"></a>Tilføj brugere i guiden

Alle brugere, du tilføjer i guiden, tildeles automatisk en Microsoft 365 Business Premium licens.

![Skærmbillede af siden Tilføj nye brugere i guiden.](../../media/addnewuserspage.png)

1. Hvis dit Microsoft 365 Business Premium-abonnement har eksisterende brugere (f.eks. hvis du har brugt Azure AD Forbind), får du mulighed for at tildele licenser til dem nu. Du kan også føje licenser til dem.

2. Når du har tilføjet brugerne, får du også mulighed for at dele legitimationsoplysninger med de nye brugere, du har tilføjet. Du kan vælge at udskrive dem, maile dem eller downloade dem.

### <a name="connect-your-domain"></a>Forbind dit domæne

> [!NOTE]
> Hvis du vælger at bruge domænet .onmicrosoft eller brugte Azure AD Forbind til at konfigurere brugere, kan du ikke se dette trin.
  
Hvis du vil konfigurere tjenester, skal du opdatere nogle poster hos din DNS-vært eller domæneregistrator.
  
1. Konfigurationsguiden registrerer typisk din registrator og giver dig et link til trinvise instruktioner om opdatering af NS-posterne på registratorens websted. Hvis det ikke sker, skal [du ændre navneservere for at konfigurere Microsoft 365 med en domæneregistrator](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - Hvis du har eksisterende DNS-poster, f.eks. et eksisterende websted, men din DNS-vært er aktiveret [til domæne](/office365/admin/get-help-with-domains/domain-connect) connect, skal du **vælge Tilføj poster for mig**. På siden **Vælg dine onlinetjenester** skal du acceptere alle standardindstillingerne og vælge **Næste** og vælge **Godkend** på DNS-værtens side.
    - Hvis du har eksisterende DNS-poster med andre DNS-værter (ikke aktiveret til domæneforbindelser), skal du administrere dine egne DNS-poster for at sikre, at de eksisterende tjenester forbliver forbundet. Se [grundlæggende om domæner for at](/office365/admin/get-help-with-domains/dns-basics) få flere oplysninger.

        ![Siden Aktivér poster.](../../media/activaterecords.png)

2. Følg trinnene i guiden, og mail og andre tjenester konfigureres for dig.

### <a name="protect-your-organization"></a>Beskyt din organisation 

De politikker, du konfigurerer i guiden, anvendes automatisk på en [sikkerhedsgruppe kaldet](/office365/admin/create-groups/compare-groups#security-groups) *Alle brugere*. Du kan også oprette flere grupper, som politikker skal tildeles i Administration.

1. På siden **Forøg beskyttelsen** mod avancerede cybertrusler anbefales det, at du accepterer standardindstillingerne, så [Office 365 Advance Threat Protection](../../security/office-365-security/defender-for-office-365.md) kan scanne filer og links i Office apps.

    ![Skærmbillede af siden Forøg beskyttelse.](../../media/increasetreatprotection.png)


2. På siden Undgå lækager fra følsomme **data** skal du acceptere standardindstillingerne for at aktivere Office 365 Forebyggelse af datatab (DLP) for at spore følsomme data i Office-apps og forhindre utilsigtet deling af disse uden for organisationen.

3. På siden **Beskyt data i Office til** mobil skal du lade administration af mobilapps være tændt, udvide indstillingerne og gennemse dem og derefter vælge Opret politik for administration af **mobilapps**.

    ![Skærmbillede af Beskyt data Office for mobilsiden.](../../media/protectdatainmobile.png)


## <a name="secure-windows-10-pcs"></a>Sikre Windows 10 pc'er

I venstre navigationslinje skal **du vælge** Konfiguration og derefter under **Logon og sikkerhed vælge** **Beskyt dine Windows 10 computere**. Vælg **Vis for** at komme i gang. Se [beskyt dine Windows 10 computere](secure-win-10-pcs.md) for at få en komplet vejledning.

## <a name="deploy-office-365-client-apps"></a>Installér Office 365 klientapps

Hvis du vælger at installere Office-apps automatisk under installationen, installeres appsene på Windows 10-enheder, når brugerne har logget på Azure AD fra deres Windows-enheder ved hjælp af deres arbejdslegitimationsoplysninger.

Hvis du Office på en mobil iOS- eller Android-enhed, skal du se Konfigurer [mobilenheder Microsoft 365 Business Premium brugere](set-up-mobile-devices.md).

Du kan også installere Office enkeltvis. Se [installér Office på en pc eller Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) for at få vejledning.

## <a name="related-content"></a>Relateret indhold

[Microsoft 365 til virksomhedsvideoer](../../business-video/index.yml) (linkside)
