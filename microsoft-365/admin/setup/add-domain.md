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
description: Brug konfigurationsguiden til at føje dit domæne Microsoft 365 på Microsoft 365 Administration ved at tilføje en DNS-post hos din DNS-vært.
ms.openlocfilehash: fa809486b968c4bc0f8c74e466285ee2ce9ac895
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590128"
---
# <a name="add-a-domain-to-microsoft-365"></a>Føj et domæne til Microsoft 365

 **[Tjek ofte stillede spørgsmål om](domains-faq.yml)** domæner, hvis du ikke kan finde det, du leder efter. 
  
## <a name="before-you-begin"></a>Før du begynder

Hvis du vil tilføje, ændre eller fjerne domæner, skal **du være** **domænenavnsadministrator** eller **global administrator** for en [virksomheds- eller virksomhedsplan](https://products.office.com/business/office). Disse ændringer påvirker hele lejeren. *Tilpassede administratorer* *eller almindelige* brugere kan ikke foretage disse ændringer.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

## <a name="watch-add-a-domain"></a>Se: Tilføj et domæne

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

Din virksomhed skal muligvis bruge flere domænenavne til forskellige formål. Det kan f.eks. være, at du vil tilføje en anden stavemåde af dit firmanavn, da kunderne allerede bruger den, og du ikke har fået kontakt til deres kommunikation.

1. Vælg Microsoft 365 Administration under <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**menuen Konfiguration**</a>.
1. Under **Få konfigureret dit brugerdefinerede domæne** skal du **vælge** **ViewManageAdd-domæne** >  > .
1. Angiv det nye domænenavn, du vil tilføje, og vælg derefter **Næste**.
1. Log på din domæneregistrator, og vælg derefter **Næste**.
1. Vælg tjenesterne for dit nye domæne.
1. Vælg **NæsteOrdbogNæste** >  > , og klik derefter på **Udfør**. Dit nye domæne er blevet tilføjet.

## <a name="add-a-domain"></a>Tilføj et domæne

Følg disse trin for at tilføje, konfigurere eller fortsætte med at konfigurere et domæne. 

::: moniker range="o365-worldwide"

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end
    
2. Gå til **Indstillinger** >  **Domæner**. 

3. Vælg **Tilføj domæne**.
    
4. Angiv navnet på det domæne, du vil tilføje, og vælg derefter **Næste**.
    
5. Vælg, hvordan du vil bekræfte, at du ejer domænet.
    
    1. Hvis din domæneregistrator bruger [Domain Forbind](#domain-connect-registrars-integrating-with-microsoft-365), konfigurerer [Microsoft automatisk](../get-help-with-domains/domain-connect.md) dine poster ved at få dig til at logge på din registrator og bekræfte forbindelsen til Microsoft 365. Du kommer tilbage til Administration, og Microsoft bekræfter derefter automatisk dit domæne.
    2. Du kan bruge en TXT-post til at bekræfte dit domæne. Vælg denne, og vælg **Næste** for at få en vejledning i, hvordan du føjer DNS-posten til din registrators websted. Det kan tage op til 30 minutter at bekræfte, når du har tilføjet posten. 
    3. Du kan føje en tekstfil til domænets websted. Vælg og download .txt fra konfigurationsguiden, og overfør derefter filen til webstedets mappe på øverste niveau. Stien til filen skal ligne denne: `http://mydomain.com/ms39978200.txt`. Vi bekræfter, at du ejer domænet, ved at finde filen på dit websted.
    
6. Vælg, hvordan du vil foretage de DNS-ændringer, der kræves, for at Microsoft kan bruge dit domæne.
    
    1. Vælg **Tilføj DNS-posterne for** mig, hvis din registrator understøtter [Domain Forbind](#domain-connect-registrars-integrating-with-microsoft-365), så konfigurerer [Microsoft automatisk](../get-help-with-domains/domain-connect.md) dine poster ved at få dig til at logge på din registrator og bekræfte forbindelsen til Microsoft 365.
    2. Vælg **Jeg tilføjer selv DNS-posterne**, hvis du kun vil knytte bestemte Microsoft 365-tjenester til dit domæne, eller hvis du vil springe dette over nu og gøre det senere. **Vælg denne indstilling, hvis du ved, præcis hvad du foretager dig.**

7. Hvis du vælger selv at tilføje *DNS-poster*,  skal du vælge Næste, så får du vist en side med alle de poster, du skal føje til din registrators websted for at konfigurere dit domæne. 

    Hvis portalen ikke genkender din registrator, kan du følge [disse generelle instruktioner.](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md)
    
    Hvis du ikke kender DNS-udbyderen eller domæneregistratoren for dit domæne, kan du se [Finde din domæneregistrator eller DNS-udbyder](../get-help-with-domains/find-your-domain-registrar.md).
    
    Hvis du vil vente på det senere, skal du enten fjerne markeringen af alle tjenesterne og klikke på **Fortsæt, eller** du kan vælge Flere  indstillinger i det forrige trin til domæneforbindelse og vælge **Spring dette over nu**.
    
8. Vælg **Udfør** – du er færdig!

## <a name="add-or-edit-custom-dns-records"></a>Tilføj eller rediger brugerdefinerede DNS-poster

Følg trinnene nedenfor for at tilføje en brugerdefineret post for et websted eller en tredjepartstjeneste.

1. Log på Microsoft Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

2. Gå til **Indstillinger**  >  **Domæner**.

3. Vælg **et domæne** på siden Domæner. 
    
4. Under **DNS-indstillinger** skal du vælge **Brugerdefinerede poster**. Vælg derefter **Ny brugerdefineret post**.

5. Vælg den type DNS-post, du vil tilføje, og skriv oplysningerne for den nye post.
    
6. Vælg **Gem**.

## <a name="registrars-with-domain-connect"></a>Domæneregistratorer med Forbind

[Domæneregistratorer,](https://www.domainconnect.org/) der Forbind domæneregistratorer, kan du tilføje dit domæne Microsoft 365 i en tretrinsproces, der tager få minutter. 
  
I guiden bekræfter vi blot, at du ejer domænet, og derefter konfigurerer vi automatisk domænets poster, så mail leveres til Microsoft 365 og andre Microsoft 365-tjenester som Teams og arbejder med dit domæne.
  
> [!NOTE]
> Sørg for at deaktivere blokering af pop op-vindue i din browser, før du starter konfigurationsguiden.
  
### <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Domæneregistratorer integrerer Forbind med Microsoft 365

- [11&amp; IONOS](https://www.1and1.com/)
- [EuroDNS](https://www.eurodns.com/)
- [Cloudflare](https://www.cloudflare.com/)
- [GoDaddy](https://www.godaddy.com/)
- [WordPress.com](https://wordpress.com/)
- [Udg.for at](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer eller WildWestDomains (GoDaddy-forhandlere, der bruger SecureServer DNS-hosting)
    - Eksempler:
        - [DomainsPricedRight](https://www.domainspricedright.com/products/domain-registration)
        - [DomainRightNow](https://www.domainrightnow.com/)

### <a name="what-happens-to-my-email-and-website"></a>Hvad sker der med min mail og mit websted?

Når du er færdig med konfigurationen, opdateres MX-posten for dit domæne til at pege på Microsoft 365 og alle mails til dit domæne vil begynde at Microsoft 365. Sørg for, at du har tilføjet brugere og konfigureret postkasser i Microsoft 365 for alle, der modtager mail på dit domæne!
  
Hvis du har et websted, som du bruger sammen med din virksomhed, fungerer det fortsat, hvor det er. Konfigurationstrinnene Forbind domæne har ingen indflydelse på dit websted.

### <a name="add-an-onmicrosoftcom-domain"></a>Tilføje et onmicrosoft.com domæne

Hver Microsoft 365 organisation kan have op til tre onmicrosoft.com domæner.

> [!NOTE]
> Du skal være global administrator eller domænenavnsadministrator for at tilføje et domæne.
> Når du opretter et ekstra .onmicrosoft-domæne og bruger det som standard, omdøbes navnet ikke SharePoint Online. Hvis du vil foretage ændringer i dit .onmicrosoft SharePoint-domæne, skal du bruge prøveversionen af SharePoint-domænets omdøbning (tilgængelig for alle lejere med mindre end 1.000 websteder).[](/sharepoint/change-your-sharepoint-domain-name)
> Hvis du bruger en Microsoft 365, understøttes fjernelse af dit oprindelige .onmicrosoft-domæne ikke.


Sådan tilføjer du onmicrosoft.com domæne:

1. Gå til Microsoft Administration, **Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domæner**</a>.

2. På fanen **Oversigt** skal du vælge **Tilføj onmicrosoft.com domæne**.

Du kan angive et hvilket som helst domæne, du ejer, som dit standarddomæne.

## <a name="related-content"></a>Relateret indhold

[Ofte stillede spørgsmål om domæner](domains-faq.yml) (artikel)</br>
[Hvad er et domæne?](../get-help-with-domains/what-is-a-domain.md) (artikel)</br>
[Køb et domænenavn i Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (artikel)</br>
[Tilføje DNS-poster for at forbinde dit domæne](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) (artikel)</br>
[Ændre navneservere for at konfigurere Microsoft 365 med en domæneregistrator](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md) (artikel)
