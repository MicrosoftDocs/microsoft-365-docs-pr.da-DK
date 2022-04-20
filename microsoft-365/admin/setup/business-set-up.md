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
description: Se konfigurationstrinnene for Microsoft 365 Business Premium, herunder tilføjelse af et domæne og brugere, konfiguration af sikkerhedspolitikker m.m.
ms.openlocfilehash: 69d158d7193a2f07c6b4c23557474f1458e2fb51
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/19/2022
ms.locfileid: "64935889"
---
# <a name="set-up-microsoft-365-business-premium-in-the-setup-wizard"></a>Konfigurer Microsoft 365 Business Premium i installationsguiden

## <a name="watch-overview-of-microsoft-365-setup"></a>Se: Oversigt over Microsoft 365 konfiguration

Se denne video for at få en oversigt over Microsoft 365 Business Premium konfiguration.<br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4jZwg] 

## <a name="watch-set-up-microsoft-365-business-premium"></a>Se: Konfigurer Microsoft 365 Business Premium

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE471FJ?autoplay=false]

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>, og vælg **Gå til konfiguration**. Installationsguiden starter.
1. Når installationen er fuldført, skal du gå tilbage til Microsoft Administration. I Administration kan du fortsætte med at konfigurere funktioner som f.eks. Windows 10 politikker, DLP osv. på siden **Konfiguration**.

## <a name="add-your-domain-users-and-set-up-policies"></a>Tilføj dit domæne, dine brugere, og konfigurer politikker

Når du køber Microsoft 365 Business Premium, har du mulighed for at bruge et domæne, du ejer, eller købe et under [tilmeldingen](../admin-overview/sign-up-for-office-365.md).

- Hvis du har købt et nyt domæne, da du tilmeldte dig, er dit domæne konfigureret, og du kan flytte til [Tilføj brugere og tildele licenser](#add-users-and-assign-licenses).

### <a name="add-your-domain-to-personalize-sign-in"></a>Tilføj dit domæne for at tilpasse logon

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) ved hjælp af dine globale administratorlegitimationsoplysninger. 

2. Vælg **Gå til installationsprogrammet for at** starte guiden.

    ![Vælg Gå til konfiguration.](../../media/gotosetupinadmincenter.png)

3. På siden **Installér dine Office apps** kan du eventuelt installere appsene på din egen computer.
    
4. I trinnet **Tilføj domæne** skal du angive det domænenavn, du vil bruge (f.eks. contoso.com).

    > [!IMPORTANT]
    > Hvis du har købt et domæne under tilmeldingen, kan du ikke se trinnet **Tilføj et domæne** her. Gå i stedet til [Tilføj brugere](#add-users-and-assign-licenses) .

    ![Skærmbillede af siden Tilpas dit logon.](../../media/adddomain.png)

    
4. Følg trinnene i guiden for at [oprette DNS-poster hos en hvilken som helst DNS-hostingudbyder for Microsoft 365](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider), der kontrollerer, at du ejer domænet. Hvis du kender din domænevært, skal du også se [Føj et domæne til Microsoft 365](/microsoft-365/admin/setup/add-domain).

    Hvis din hostingudbyder er GoDaddy eller en anden vært aktiveret med [domæneforbindelse](/office365/admin/get-help-with-domains/domain-connect), er processen nem, og du bliver automatisk bedt om at logge på og lade Microsoft godkende på dine vegne.

    ![På Siden Bekræft adgang på GoDaddy skal du vælge Godkend.](../../media/godaddyauth.png)

### <a name="add-users-and-assign-licenses"></a>Tilføj brugere, og tildel licenser

Du kan tilføje brugere i guiden, men du kan også [tilføje brugere senere](../add-users/add-users.md) i Administration. Hvis du har en lokal domænecontroller, kan du desuden tilføje brugere med [Azure AD-Forbind](/azure/active-directory/hybrid/how-to-connect-install-express).

#### <a name="add-users-in-the-wizard"></a>Tilføj brugere i guiden

Alle brugere, du tilføjer i guiden, tildeles automatisk en Microsoft 365 Business Premium licens.

![Skærmbillede af siden Tilføj nye brugere i guiden.](../../media/addnewuserspage.png)

1. Hvis dit Microsoft 365 Business Premium-abonnement har eksisterende brugere (f.eks. hvis du har brugt Azure AD Forbind), får du mulighed for at tildele licenser til dem nu. Du kan også føje licenser til dem.

2. Når du har tilføjet brugerne, får du også mulighed for at dele legitimationsoplysninger med de nye brugere, du har tilføjet. Du kan vælge at udskrive dem, sende dem en mail eller downloade dem.

### <a name="connect-your-domain"></a>Forbind dit domæne

> [!NOTE]
> Hvis du har valgt at bruge domænet .onmicrosoft eller brugt Azure AD-Forbind til at konfigurere brugere, får du ikke vist dette trin.
  
Hvis du vil konfigurere tjenester, skal du opdatere nogle poster hos din DNS-vært eller domæneregistrator.
  
1. Installationsguiden registrerer typisk din registrator og giver dig et link til en trinvis vejledning til opdatering af dine NS-poster på registratorwebstedet. Hvis den ikke gør det, [skal du ændre navneservere for at konfigurere Microsoft 365 med en domæneregistrator](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md). 

    - Hvis du har eksisterende DNS-poster, f.eks. et eksisterende websted, men din DNS-vært er aktiveret til [domæneforbindelse](/office365/admin/get-help-with-domains/domain-connect), skal du vælge **Tilføj poster for mig**. Acceptér alle standardindstillingerne på siden **Vælg dine onlinetjenester**, vælg **Næste**, og vælg **Godkend** på din DNS-værts side.
    - Hvis du har eksisterende DNS-poster med andre DNS-værter (ikke aktiveret for domæneforbindelse), skal du administrere dine egne DNS-poster for at sikre, at de eksisterende tjenester forbliver forbundne. Du [kan](/office365/admin/get-help-with-domains/dns-basics) finde flere oplysninger under Grundlæggende om domæner.

        ![Siden Aktivér poster.](../../media/activaterecords.png)

2. Følg trinnene i guiden, og mail og andre tjenester konfigureres for dig.

### <a name="protect-your-organization"></a>Beskyt din organisation 

De politikker, du konfigurerer i guiden, anvendes automatisk på en [sikkerhedsgruppe](/office365/admin/create-groups/compare-groups#security-groups) med navnet *Alle brugere*. Du kan også oprette yderligere grupper for at tildele politikker til i Administration.

1. På **Øg beskyttelse mod avancerede cybertrusler** anbefales det, at du accepterer standarderne for at lade [Office 365 Advance Threat Protection](../../security/office-365-security/defender-for-office-365.md) scanne filer og links i Office apps.

    ![Skærmbillede af siden Øg beskyttelse.](../../media/increasetreatprotection.png)


2. På siden **Undgå lækager af følsomme data** skal du acceptere standarderne for at aktivere Microsoft Purview Data Loss Prevention for at spore følsomme data i Office apps og forhindre utilsigtet deling af disse uden for din organisation.

3. På siden **Beskyt data i Office til mobil** skal du lade administration af mobilapp være aktiveret, udvide indstillingerne og gennemse dem og derefter vælge **Opret politik for administration af mobilapps**.

    ![Skærmbillede af siden Beskyt data i Office til mobil.](../../media/protectdatainmobile.png)


## <a name="secure-windows-10-pcs"></a>Sikker Windows 10 pc'er

Vælg **Konfigurer** i venstre navigationsrude, og vælg derefter **Beskyt dine Windows 10 computere** under **Logon og sikkerhed**. Vælg **Vis** for at komme i gang. Se [Beskyt dine Windows 10 computere](secure-win-10-pcs.md) for at få en komplet vejledning.

## <a name="deploy-office-365-client-apps"></a>Installér Office 365 klientapps

Hvis du vælger automatisk at installere Office apps under konfigurationen, installeres appsene på de Windows 10 enheder, når brugerne er logget på Azure AD fra deres Windows enheder ved hjælp af deres legitimationsoplysninger til arbejdet.

Hvis du vil installere Office på mobile iOS- eller Android-enheder, skal du se [Konfigurer mobilenheder til Microsoft 365 Business Premium brugere](set-up-mobile-devices.md).

Du kan også installere Office enkeltvis. Se [Installér Office på en pc eller Mac](https://support.microsoft.com/office/4414eaaf-0478-48be-9c42-23adc4716658) for at få instruktioner.

## <a name="related-content"></a>Relateret indhold

[Microsoft 365 til træningsvideoer til virksomheder](../../business-video/index.yml) (linkside)
