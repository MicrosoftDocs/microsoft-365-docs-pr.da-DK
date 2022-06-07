---
title: Føj et domæne til Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_O365
- Adm_TOC
ms.custom:
- TopSMBIssues
- SaRA
- MSStore_Link
- okr_smb
- business_assist
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 6383f56d-3d09-4dcb-9b41-b5f5a5efd611
description: Brug installationsguiden til at føje dit domæne til Microsoft 365 i Microsoft 365 Administration ved at tilføje en DNS-post hos din DNS-vært.
ms.openlocfilehash: ad4654bce8781607a77272dafeb3eb9135c85765
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922898"
---
# <a name="add-a-domain-to-microsoft-365"></a>Føj et domæne til Microsoft 365

 **[Se ofte stillede spørgsmål om domæner](domains-faq.yml)** , hvis du ikke kan finde det, du leder efter. 
  
## <a name="before-you-begin"></a>Før du begynder

Hvis du vil tilføje, redigere eller fjerne domæner, **skal** du være **administrator af domænenavne** eller **global administrator** af en [virksomheds- eller virksomhedsplan](https://products.office.com/business/office). Disse ændringer påvirker hele lejeren. *Brugerdefinerede administratorer* eller *almindelige brugere* kan ikke foretage disse ændringer.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist har du og dine medarbejdere adgang til specialister i små virksomheder døgnet rundt, efterhånden som du får din virksomhed til at vokse, lige fra onboarding til hverdagsbrug.

## <a name="watch-add-a-domain"></a>Se: Tilføj et domæne

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

Din virksomhed skal muligvis bruge flere domænenavne til forskellige formål. Det kan f.eks. være, at du vil tilføje en anden stavemåde for dit firmanavn, fordi kunderne allerede bruger det, og deres kommunikation ikke har kontaktet dig.

1. I Microsoft 365 Administration skal du vælge <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Installation**</a>.
1. Under **Hent dit brugerdefinerede domænesæt** skal du vælge **Vis** > **Administrer** > **Tilføj domæne**.
1. Angiv det nye domænenavn, du vil tilføje, og vælg derefter **Næste**.
1. Log på din domæneregistrator, og vælg derefter **Næste**.
1. Vælg tjenesterne for dit nye domæne.
1. Vælg **Næste** > **Godkend** > **næste**, og vælg derefter **Udfør**. Dit nye domæne er blevet tilføjet.

## <a name="add-a-domain"></a>Tilføj et domæne

Følg disse trin for at tilføje, konfigurere eller fortsætte med at konfigurere et domæne. 

::: moniker range="o365-worldwide"

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end
    
2. Gå til siden **Indstillinger** > **Domæner** . 

3. Vælg **Tilføj domæne**.
    
4. Angiv navnet på det domæne, du vil tilføje, og vælg derefter **Næste**.
    
5. Vælg, hvordan du vil bekræfte, at du ejer domænet.
    
    1. Hvis din domæneregistrator bruger [Domain Connect](#domain-connect-registrars-integrating-with-microsoft-365), [konfigurerer Microsoft automatisk dine poster](../get-help-with-domains/domain-connect.md) ved at få dig til at logge på din registrator og bekræfte forbindelsen til Microsoft 365. Du vender tilbage til Administration, og Microsoft bekræfter derefter automatisk dit domæne.
    2. Du kan bruge en TXT-post til at bekræfte dit domæne. Vælg dette, og vælg **Næste** for at se instruktioner til, hvordan du føjer denne DNS-post til din registrators websted. Det kan tage op til 30 minutter at bekræfte, når du har tilføjet posten. 
    3. Du kan føje en tekstfil til dit domænes websted. Vælg og download den .txt fil fra installationsguiden, og upload derefter filen til webstedets mappe på øverste niveau. Stien til filen skal ligne: `http://mydomain.com/ms39978200.txt`. Vi bekræfter, at du ejer domænet ved at finde filen på dit websted.
    
6. Vælg, hvordan du vil foretage de DNS-ændringer, der kræves, for at Microsoft kan bruge dit domæne.
    
    1. Vælg **Tilføj DNS-posterne for mig** , hvis din registrator understøtter [Domain Connect](#domain-connect-registrars-integrating-with-microsoft-365), så [konfigurerer Microsoft automatisk dine poster](../get-help-with-domains/domain-connect.md) ved at få dig til at logge på din registrator og bekræfte forbindelsen til Microsoft 365.
    2. Vælg **Jeg tilføjer selv DNS-posterne** , hvis du kun vil knytte bestemte Microsoft 365-tjenester til dit domæne, eller hvis du vil springe dette over nu og gøre dette senere. **Vælg denne indstilling, hvis du ved præcis, hvad du laver.**

7. Hvis du vælger at *tilføje DNS-poster selv*  , skal du vælge **Næste** , hvorefter du får vist en side med alle de poster, du skal føje til dit registratorwebsted for at konfigurere dit domæne. 

    Hvis portalen ikke genkender din registrator, kan du [følge disse generelle instruktioner.](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)
    
    Hvis du ikke kender DNS-hostingudbyderen eller domæneregistratoren for dit domæne, skal du se [Find din domæneregistrator eller DNS-hostingudbyder](../get-help-with-domains/find-your-domain-registrar.md).
    
    Hvis du vil vente på senere, skal du enten fjerne markeringen af alle tjenesterne og klikke på **Fortsæt** eller i det forrige domæneforbindelsestrin vælge **Flere indstillinger** og vælge **Spring dette over indtil videre**.
    
8. Vælg **Udfør** – du er færdig!

## <a name="add-or-edit-custom-dns-records"></a>Tilføj eller rediger brugerdefinerede DNS-poster

Følg nedenstående trin for at tilføje en brugerdefineret post for et websted eller en tredjepartstjeneste.

1. Log på Microsoft Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Gå til siden **Indstillinger**  > **Domæner** .

3. Vælg et domæne på siden **Domæner** . 
    
4. Under **DNS-indstillinger** skal du vælge **Brugerdefinerede poster**. vælg derefter **Ny brugerdefineret post**.

5. Vælg den type DNS-post, du vil tilføje, og skriv oplysningerne for den nye post.
    
6. Vælg **Gem**.

## <a name="registrars-with-domain-connect"></a>Registratorer med domæneforbindelse

[Med Domæneforbindelsesaktiverede](https://www.domainconnect.org/) registratorer kan du føje dit domæne til Microsoft 365 i en tretrinsproces, der tager minutter. 
  
I guiden bekræfter vi blot, at du ejer domænet, og derefter konfigurerer vi automatisk dine domæneposter, så mail kommer til Microsoft 365 og andre Microsoft 365-tjenester, f.eks. Teams, arbejder med dit domæne.
  
> [!NOTE]
> Sørg for at deaktivere pop op-blokeringer i browseren, før du starter installationsguiden.
  
### <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Domæneforbindelsesregistratorer, der integreres med Microsoft 365

- [1&amp;1 IONOS](https://www.1and1.com/)
- [EuroDNS](https://www.eurodns.com/)
- [Cloudflare](https://www.cloudflare.com/)
- [Godaddy](https://www.godaddy.com/)
- [WordPress.com](https://wordpress.com/)
- [Plesk](https://www.plesk.com/)
- [Medietemple](https://mediatemple.net/)
- SecureServer eller WildWestDomains (GoDaddy-forhandlere, der bruger SecureServer DNS-hosting)
    - Eksempler:
        - [DomænerPricedRight](https://www.domainspricedright.com/products/domain-registration)
        - [DomainRightNow](https://www.domainrightnow.com/)

### <a name="what-happens-to-my-email-and-website"></a>Hvad sker der med min mail og mit websted?

Når du er færdig med at konfigurere, opdateres MX-posten for dit domæne, så den peger på Microsoft 365, og alle mails for dit domæne begynder at komme til Microsoft 365. Sørg for, at du har tilføjet brugere og konfigureret postkasser i Microsoft 365 for alle, der får mail på dit domæne!
  
Hvis du har et websted, som du bruger sammen med din virksomhed, fortsætter det med at fungere, hvor det er. Konfigurationstrinnene for Domæneforbindelse påvirker ikke dit websted.

### <a name="add-an-onmicrosoftcom-domain"></a>Tilføj et onmicrosoft.com domæne

Hver Microsoft 365-organisation kan have op til fem onmicrosoft.com domæner.

> [!NOTE]
> Du skal være global administrator eller administrator af domænenavne for at tilføje et domæne.
> Hvis du opretter et ekstra .onmicrosoft-domæne og bruger det som standard, omdøbes sharePoint Online ikke. Hvis du vil foretage ændringer af dit .onmicrosoft SharePoint-domæne, skal du bruge [prøveversionen af omdøbning af SharePoint-domænet](/sharepoint/change-your-sharepoint-domain-name) (i øjeblikket tilgængelig for alle lejere med mindre end 1.000 websteder).
> Hvis du bruger Microsoft 365-mailtjenester, understøttes fjernelse af dit oprindelige .onmicrosoft-domæne ikke.


Sådan tilføjer du et onmicrosoft.com domæne:

1. I Microsoft 365 Administration skal du vælge **Indstillinger** og derefter vælge **Domæner**.
2. Vælg dit onmicrosoft.com standarddomæne.

    ![Siden Domæner.](../../media/onmicrosoft-domains.png)
  
3. På siden med domæneegenskaber skal du i afsnittet **Om dette domæne** vælge **Tilføj microsoft-domæne**.

    ![Om denne domæneside.](../../media/add-onmicrosoft-domain-link.png)

4. Skriv navnet på det nye onmicrosoft.com domæne i feltet **Domænenavn** **på siden Tilføj onmicrosoft-domæne**. 

    ![Skærmbillede af siden Tilføj onmicrosoft-domæne.](../../media/add-an-onmicrosoftcom-domain-page.png)

    > [!NOTE]
    > Sørg for at kontrollere stavemåden og nøjagtigheden af det angivne domænenavn. Du er begrænset til fem onmicrosoft.com domæner, og de kan i øjeblikket ikke slettes, når de først er oprettet.     

5. Vælg **Tilføj domæne**. Når du er tilføjet, får du vist en meddelelse, der angiver dette. 
    
    ![Skærmbillede af det domæne, der er tilføjet.](../../media/domain-added.png)

Du kan angive et hvilket som helst domæne, du ejer, som dit standarddomæne. 

Du kan finde flere oplysninger om, hvordan du tilføjer et onmicrosoft.com domæne, under [Tilføj eller erstat dit onmicrosoft.com domæne](add-or-replace-your-onmicrosoftcom-domain.md).

## <a name="related-content"></a>Relateret indhold

[Ofte stillede spørgsmål om domæner](domains-faq.yml) (artikel)</br>
[Hvad er et domæne?](../get-help-with-domains/what-is-a-domain.md) (artikel)</br>
[Køb et domænenavn i Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (artikel)</br>
[Tilføj DNS-poster for at oprette forbindelse til dit domæne](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (artikel)</br>
[Skift navneservere for at konfigurere Microsoft 365 med en hvilken som helst domæneregistrator](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (artikel)
