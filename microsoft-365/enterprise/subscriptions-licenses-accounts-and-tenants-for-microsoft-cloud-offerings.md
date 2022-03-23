---
title: Abonnementer, licenser, konti og lejere til Microsofts skybaserede tilbud
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365initiative-coredeploy
f1.keywords:
- CSH
ms.assetid: c720cffc-f9b5-4f43-9100-422f86a1027c
ms.custom:
- seo-marvel-apr2020
- Ent_Architecture
description: Forstå relationerne mellem organisationer, abonnementer, licenser, brugerkonti og lejere på tværs af Microsofts skybaserede tilbud.
ms.openlocfilehash: c8f6fca0a5c9ce56c3565612e0de9b40d6e0254c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590547"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Abonnementer, licenser, konti og lejere til Microsofts skybaserede tilbud

Microsoft leverer et hierarki af organisationer, abonnementer, licenser og brugerkonti til konsekvent brug af identiteter og fakturering på tværs af skybaserede tilbud:
  
- Microsoft 365 og Microsoft Office 365
- Microsoft Azure
- Microsoft Dynamics 365

## <a name="elements-of-the-hierarchy"></a>Elementer i hierarkiet

Her er elementerne i hierarkiet:
  
### <a name="organization"></a>Organisation

En organisation repræsenterer en forretningsenhed, der bruger Microsoft-skybaserede tilbud, typisk identificeret af et eller flere offentlige DNS-domænenavne (f.eks. contoso.com. Organisationen er en beholder for abonnementer.
  
### <a name="subscriptions"></a>Abonnementer

Et abonnement er en aftale med Microsoft om at bruge en eller flere Microsoft-skyplatforme eller -tjenester, hvor gebyrerne periodiseres baseret på enten et gebyr pr. bruger eller skybaseret ressourceforbrug. 

- Microsofts Software as a Service-baserede (SaaS) skybaserede tilbud (Microsoft 365 og Dynamics 365) pr. brugers licensgebyrer. 
- Microsofts platform som en tjeneste (PaaS) og infrastruktur som en service (IaaS)-skybaserede tilbud (Azure) baseret på ressourceforbrug i skyen.
 
Du kan også bruge et prøveabonnement, men abonnementet udløber efter en bestemt mængde tids- eller forbrugsgebyrer. Du kan konvertere et prøveabonnement til et betalt abonnement.
  
Organisationer kan have flere abonnementer til Microsofts skybaserede tilbud. Figur 1 viser en enkelt organisation, der har flere Microsoft 365-abonnementer, et Dynamics 365-abonnement og flere Azure-abonnementer.

**Figur 1: Eksempel på flere abonnementer for en organisation**

![Et eksempel på en organisation med flere abonnementer til Microsofts skybaserede tilbud.](../media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a>Licenser

For Microsofts SaaS-skybaserede tilbud giver en licens en bestemt brugerkonto mulighed for at bruge tjenesterne i skyen. Du debiteres et fast månedligt gebyr som en del af dit abonnement. Administratorer tildeler licenser til individuelle brugerkonti i abonnementet. I eksemplet i Figur 2 har Contoso Corporation et Microsoft 365 E5-abonnement med 100 licenser, hvilket giver op til 100 individuelle brugerkonti mulighed for at bruge Microsoft 365 E5-funktioner og -tjenester.
  
**Figur 2: Licenser inden for de SaaS-baserede abonnementer for en organisation**

![Et eksempel på flere licenser inden for abonnementer til Microsofts SaaS-baserede skybaserede tilbud.](../media/Subscriptions/Subscriptions-Fig2.png)

>[!Note]
>En sikkerheds bedste fremgangsmåde er at bruge separate brugerkonti, der er tildelt bestemte roller til administrative funktioner. Disse dedikerede administratorkonti behøver ikke at være tildelt en licens til de skytjenester, de administrerer. Eksempelvis behøver en SharePoint administratorkonto ikke at være tildelt en Microsoft 365 licens.
>

For Azure PaaS-baserede skytjenester er softwarelicenser indbygget i servicepriser.
  
For virtuelle Azure IaaS-baserede computere kan det være nødvendigt med yderligere licenser for at bruge softwaren eller programmet, der er installeret på et virtuelt maskinbillede. Nogle virtuelle maskinbilleder har licenserede versioner af software installeret, og omkostningerne er inkluderet i minuttet for serveren. Eksempler er de virtuelle maskinbilleder for SQL Server 2014 og SQL Server 2016. 
  
Nogle virtuelle maskinbilleder har prøveversioner af programmer installeret og skal bruge flere softwareprogramlicenser til brug ud over prøveperioden. For eksempel omfatter SharePoint Server 2016 Trial virtual machine image en prøveversion af SharePoint Server 2016 forudinstalleret. Hvis du vil fortsætte med at bruge SharePoint Server 2016 efter udløbsdatoen for prøveversionen, skal du købe en SharePoint Server 2016-licens og -klientlicenser fra Microsoft. Disse gebyrer er adskilt fra Azure-abonnementet, og den minuttakst, der anvendes for at køre den virtuelle maskine, gælder stadig.
  
### <a name="user-accounts"></a>Brugerkonti

Brugerkonti for alle Microsofts skybaserede tilbud er gemt i en Azure Active Directory -lejer (Azure AD), som indeholder brugerkonti og grupper. En Azure AD-lejer kan synkroniseres med dine eksisterende Active Directory-domæneservices-konti (AD DS), der bruger Azure AD Forbind, som Windows-serverbaserede tjeneste. Dette kaldes katalogsynkronisering.
  
Figur 3 viser et eksempel på flere abonnementer i en organisation, der bruger en fælles Azure AD-lejer, der indeholder organisationens konti.
  
**Figur 3: Flere abonnementer for en organisation, der bruger den samme Azure AD-lejer**

![Et eksempel på en organisation med flere abonnementer, der alle bruger den samme Azure AD-lejer.](../media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>Lejere

For SaaS-skybaserede tilbud er lejeren den regionale placering, der rummer de servere, der leverer skytjenester. Contoso Corporation valgte f.eks. det europæiske område som vært for sine Microsoft 365-, EMS- og Dynamics 365-abonnementer for de 15.000 medarbejdere i deres Paris-hovedkvarter.
  
Azure PaaS-tjenester og virtuelle maskinbaserede arbejdsbelastninger, der er hostet i Azure IaaS, kan have leje i ethvert Azure-datacenter over hele verden. Du angiver Azure-datacenteret, også kaldet placeringen, når du opretter Azure PaaS-appen eller -tjenesten eller -elementet i en IaaS-arbejdsbyrde.
  
En Azure AD-lejer er en bestemt forekomst af Azure AD, der indeholder konti og grupper. Betalte abonnementer eller prøveabonnementer på Microsoft 365 Dynamics 365 omfatter en gratis Azure AD-lejer. Denne Azure AD-lejer omfatter ikke andre Azure-tjenester og er ikke det samme som en Azure-prøveversion eller et betalt abonnement.
  
### <a name="summary-of-the-hierarchy"></a>Oversigt over hierarkiet

Her er en kort opsummering:
  
- En organisation kan have flere abonnementer
    
  - Et abonnement kan have flere licenser
    
  - Licenser kan tildeles til individuelle brugerkonti
    
  - Brugerkonti gemmes i en Azure AD-lejer
    
Her er et eksempel på relationen mellem organisationer, abonnementer, licenser og brugerkonti:
  
- En organisation, der er identificeret med dens offentlige domænenavn.
    
  - Et Microsoft 365 E3 med brugerlicenser.
    
    Et Microsoft 365 E5 med brugerlicenser.
    
    Et Dynamics 365-abonnement med brugerlicenser.
    
    Flere Azure-abonnementer.
    
  - Organisationens brugerkonti i en fælles Azure AD-lejer.
    
Flere Microsoft-skybaserede tilbudsabonnementer kan bruge den samme Azure AD-lejer, der fungerer som en fælles identitetsudbyder. En central Azure AD-lejer, der indeholder de synkroniserede konti for din lokale AD DS indeholder skybaseret identitet som en tjeneste (IDaaS) for din organisation. 
  
**Figur 4: Synkroniserede lokale konti og IDaaS for en organisation**

![Identitet som tjeneste (IaaS) IDaaS for din organisation.](../media/Subscriptions/Subscriptions-Fig4.png)
  
Figur 4 viser, hvordan en almindelig Azure AD-lejer bruges af Microsofts SaaS-skybaserede tilbud, Azure PaaS-apps og virtuelle maskiner i Azure IaaS, der bruger Azure AD-domænetjenester. Azure AD Forbind synkroniserer den lokale AD DS med Azure AD-lejeren.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Kombinering af abonnementer til flere skybaserede Microsoft-tilbud

Følgende tabel beskriver, hvordan du kan kombinere flere Microsoft-skybaserede tilbud, der er baseret på allerede at have et abonnement til én type skybaserede tilbud (etiketterne går ned i den første kolonne) og føje et abonnement til et andet skybaseret tilbud (går på tværs af kolonnerne).
  
||**Microsoft 365**|**Azure**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Microsoft 365** <br/> |IKKE.TIL.IKKE  <br/> |Du føjer et Azure-abonnement til din organisation fra Azure-portalen.  <br/> |Du tilføjer et Dynamics 365-abonnement til din organisation fra Microsoft 365 Administration.  <br/> |
|**Azure** <br/> |Du føjer Microsoft 365 abonnement til organisationen.  <br/> |IKKE.TIL.IKKE  <br/> |Du tilføjer et Dynamics 365-abonnement til din organisation.  <br/> |
|**Dynamics 365** <br/> |Du føjer Microsoft 365 abonnement til organisationen.  <br/> |Du føjer et Azure-abonnement til din organisation fra Azure-portalen.  <br/> |IKKE.TIL.IKKE  <br/> |
   
En nem metode til at føje abonnementer til din organisation til Microsoft SaaS-baserede tjenester er via Administration:
  
1. Log på Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com)) med din **brugeradministrator** eller **globale administratorkonto**.
    
2. Klik på Fakturering i venstre **navigationsrude på** administrationens **startside**, og klik derefter **på Køb tjenester**.
    
3. På siden **Køb tjenester** skal du købe dine nye abonnementer.
    
Administration tildeler organisationen og Azure AD-lejeren af dit Microsoft 365-abonnement til de nye abonnementer til SaaS-baserede skybaserede tilbud.
  
Sådan tilføjer du et Azure-abonnement med den samme organisation og Azure AD-lejer som Microsoft 365-abonnement:
  
1. Log på Azure-portalen ([https://portal.azure.com](https://portal.azure.com)) med din Microsoft 365 **Azure AD DC-administrator** eller **global administratorkonto**.
    
2. I venstre navigationsrude skal du **klikke på Abonnementer** og derefter klikke på **Tilføj**.
    
3. På siden **Tilføj abonnement** skal du vælge et tilbud og udfylde betalingsoplysningerne og aftalen.
    
Hvis du har købt Azure- og Microsoft 365-abonnementer separat og vil have adgang til Microsoft 365 Azure AD-lejeren fra dit Azure-abonnement, skal du se instruktionerne i Føj et eksisterende Azure-abonnement til din [Azure Active Directory-lejer](/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).
 
## <a name="see-also"></a>Se også

[Illustrationer af Microsoft Cloud for Enterprise Architects](../solutions/cloud-architecture-models.md)
  
[Arkitektoniske modeller til SharePoint, Exchange, Skype for Business og Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Hybridløsninger](hybrid-solutions.md)

## <a name="next-step"></a>Næste trin

[Vurdering Microsoft 365 af netværksforbindelsen](assessing-network-connectivity.md)
