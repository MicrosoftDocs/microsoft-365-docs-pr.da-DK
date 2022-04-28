---
title: Abonnementer, licenser, konti og lejere til Microsofts cloudtilbud
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Forstå relationerne mellem organisationer, abonnementer, licenser, brugerkonti og lejere på tværs af Microsofts cloudtilbud.
ms.openlocfilehash: 9a3f41af3945055ebfc3217837b0bdaf8aab411a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101155"
---
# <a name="subscriptions-licenses-accounts-and-tenants-for-microsofts-cloud-offerings"></a>Abonnementer, licenser, konti og lejere til Microsofts cloudtilbud

Microsoft leverer et hierarki af organisationer, abonnementer, licenser og brugerkonti til ensartet brug af identiteter og fakturering på tværs af sine cloudtilbud:
  
- Microsoft 365 og Microsoft Office 365
- Microsoft Azure
- Microsoft Dynamics 365

## <a name="elements-of-the-hierarchy"></a>Elementer i hierarkiet

Her er elementerne i hierarkiet:
  
### <a name="organization"></a>Organisation

En organisation repræsenterer en forretningsenhed, der bruger Microsofts cloudtilbud, der typisk identificeres af et eller flere dns-domænenavne (Public Domain Name System), f.eks. contoso.com. Organisationen er en objektbeholder til abonnementer.
  
### <a name="subscriptions"></a>Abonnementer

Et abonnement er en aftale med Microsoft om at bruge en eller flere Microsoft-cloudplatforme eller -tjenester, for hvilke der påløber gebyrer baseret på enten et licensgebyr pr. bruger eller på cloudbaseret ressourceforbrug. 

- Microsofts SaaS-baserede cloudtilbud (Software as a Service) (Microsoft 365 og Dynamics 365) opkræver licensafgifter pr. bruger. 
- Microsofts PaaS (Platform as a Service) og IaaS (Infrastructure as a Service) cloudtilbud (Azure) opkræver gebyrer baseret på forbrug af cloudressourcer.
 
Du kan også bruge et prøveabonnement, men abonnementet udløber efter et bestemt tidsrum eller forbrugsgebyrer. Du kan konvertere et prøveabonnement til et betalt abonnement.
  
Organisationer kan have flere abonnementer på Microsofts cloudtilbud. Figur 1 viser en enkelt organisation, der har flere Microsoft 365 abonnementer, et Dynamics 365-abonnement og flere Azure-abonnementer.

**Figur 1: Eksempel på flere abonnementer for en organisation**

![Et eksempel på en organisation med flere abonnementer på Microsofts cloudtilbud.](../media/Subscriptions/Subscriptions-Fig1.png)
  
### <a name="licenses"></a>Licenser

I forbindelse med Microsofts SaaS-cloudtilbud giver en licens en bestemt brugerkonto mulighed for at bruge tjenesterne i cloudtilbud. Du opkræves et fast månedligt gebyr som en del af dit abonnement. Administratorer tildeler licenser til individuelle brugerkonti i abonnementet. I eksemplet i Figur 2 har Contoso Corporation et Microsoft 365 E5-abonnement med 100 licenser, hvilket giver op til 100 individuelle brugerkonti mulighed for at bruge Microsoft 365 E5 funktioner og tjenester.
  
**Figur 2: Licenser i de SaaS-baserede abonnementer for en organisation**

![Et eksempel på flere licenser i abonnementer for Microsofts SaaS-baserede cloudtilbud.](../media/Subscriptions/Subscriptions-Fig2.png)

>[!Note]
>Bedste praksis for sikkerhed er at bruge separate brugerkonti, der er tildelt specifikke roller til administrative funktioner. Disse dedikerede administratorkonti behøver ikke at være tildelt en licens til de cloudtjenester, de administrerer. En SharePoint administratorkonto behøver f.eks. ikke at være tildelt en Microsoft 365 licens.
>

I forbindelse med Azure PaaS-baserede cloudtjenester er softwarelicenser indbygget i tjenestepriserne.
  
For Azure IaaS-baserede virtuelle maskiner kan det være nødvendigt med yderligere licenser til at bruge den software eller det program, der er installeret på en virtuel maskine-afbildning. Nogle virtuelle maskiners billeder har licenserede versioner af software installeret, og prisen er inkluderet i minutsatsen for serveren. Eksempler er billeder af virtuelle maskiner til SQL Server 2014 og SQL Server 2016. 
  
Nogle afbildninger af virtuelle maskiner har prøveversioner af programmer installeret og har brug for yderligere softwareprogramlicenser til brug ud over prøveperioden. Den virtuelle maskines SharePoint Server 2016 Trial omfatter f.eks. en prøveversion af SharePoint Server 2016, der er forudinstalleret. Hvis du vil fortsætte med at bruge SharePoint Server 2016 efter udløbsdatoen for prøveversionen, skal du købe en SharePoint Server 2016-licens og klientlicenser fra Microsoft. Disse gebyrer er adskilt fra Azure-abonnementet, og satsen pr. minut for kørsel af den virtuelle maskine gælder stadig.
  
### <a name="user-accounts"></a>Brugerkonti

Brugerkonti for alle Microsofts cloudtilbud gemmes i en azure AD-lejer (Azure Active Directory), som indeholder brugerkonti og grupper. En Azure AD-lejer kan synkroniseres med dine eksisterende AD DS-konti (Active Directory-domæneservices) ved hjælp af Azure AD Forbind, som er en Windows serverbaseret tjeneste. Dette kaldes katalogsynkronisering.
  
Figur 3 viser et eksempel på flere abonnementer på en organisation ved hjælp af en fælles Azure AD-lejer, der indeholder organisationens konti.
  
**Figur 3: Flere abonnementer på en organisation, der bruger den samme Azure AD-lejer**

![Et eksempel på en organisation med flere abonnementer, der alle bruger den samme Azure AD-lejer.](../media/Subscriptions/Subscriptions-Fig3.png)
  
### <a name="tenants"></a>Lejere

For SaaS-cloudtilbud er lejeren den regionale placering, der indeholder de servere, der leverer cloudtjenester. Contoso Corporation valgte f.eks. det europæiske område som vært for abonnementer på Microsoft 365, EMS og Dynamics 365 for de 15.000 medarbejdere i deres hovedkvarter i Paris.
  
Azure PaaS-tjenester og arbejdsbelastninger baseret på virtuelle maskiner, der hostes i Azure IaaS, kan have lejer i et hvilket som helst Azure-datacenter over hele verden. Du angiver Azure-datacenteret, der kaldes placeringen, når du opretter Azure PaaS-appen eller -tjenesten eller -elementet i en IaaS-arbejdsbelastning.
  
En Azure AD-lejer er en bestemt forekomst af Azure AD, der indeholder konti og grupper. Betalte abonnementer eller prøveabonnementer på Microsoft 365 eller Dynamics 365 omfatter en gratis Azure AD-lejer. Denne Azure AD-lejer omfatter ikke andre Azure-tjenester og er ikke det samme som en Prøveversion af Azure eller et betalt abonnement.
  
### <a name="summary-of-the-hierarchy"></a>Oversigt over hierarkiet

Her er en hurtig opsummering:
  
- En organisation kan have flere abonnementer
    
  - Et abonnement kan have flere licenser
    
  - Licenser kan tildeles til individuelle brugerkonti
    
  - Brugerkonti gemmes i en Azure AD-lejer
    
Her er et eksempel på relationen mellem organisationer, abonnementer, licenser og brugerkonti:
  
- En organisation, der identificeres af dens offentlige domænenavn.
    
  - Et Microsoft 365 E3 abonnement med brugerlicenser.
    
    Et Microsoft 365 E5 abonnement med brugerlicenser.
    
    Et Dynamics 365-abonnement med brugerlicenser.
    
    Flere Azure-abonnementer.
    
  - Organisationens brugerkonti i en fælles Azure AD-lejer.
    
Flere Abonnementer på Microsoft-cloudtilbud kan bruge den samme Azure AD-lejer, der fungerer som en almindelig identitetsudbyder. En central Azure AD-lejer, der indeholder de synkroniserede konti for din AD DS i det lokale miljø, leverer cloudbaseret IDaaS (Identity as a Service) for din organisation. 
  
**Figur 4: Synkroniserede konti i det lokale miljø og IDaaS for en organisation**

![IDaaS (Identity as a Service) (IaaS) for din organisation.](../media/Subscriptions/Subscriptions-Fig4.png)
  
Figur 4 viser, hvordan en fælles Azure AD-lejer bruges af Microsofts SaaS-cloudtilbud, Azure PaaS-apps og virtuelle maskiner i Azure IaaS, der bruger Azure AD-domænetjenester. Azure AD Forbind synkroniserer AD DS-området i det lokale miljø med Azure AD-lejeren.
  
## <a name="combining-subscriptions-for-multiple-microsoft-cloud-offerings"></a>Kombination af abonnementer på flere Microsoft-cloudtilbud

I følgende tabel beskrives det, hvordan du kan kombinere flere Microsoft-cloudtilbud, der er baseret på, at du allerede har et abonnement på én type cloudtilbud (mærkaterne i den første kolonne) og tilføje et abonnement på et andet cloudtilbud (på tværs af kolonnerne).
  
||**Microsoft 365**|**Azure**|**Dynamics 365**|
|:-----|:-----|:-----|:-----|:-----|
|**Microsoft 365** <br/> |NA  <br/> |Du føjer et Azure-abonnement til din organisation fra Azure Portal.  <br/> |Du føjer et Dynamics 365-abonnement til din organisation fra Microsoft 365 Administration.  <br/> |
|**Azure** <br/> |Du føjer et Microsoft 365-abonnement til din organisation.  <br/> |NA  <br/> |Du føjer et Dynamics 365-abonnement til din organisation.  <br/> |
|**Dynamics 365** <br/> |Du føjer et Microsoft 365-abonnement til din organisation.  <br/> |Du føjer et Azure-abonnement til din organisation fra Azure Portal.  <br/> |NA  <br/> |
   
En nem måde at føje abonnementer til din organisation til Microsoft SaaS-baserede tjenester på er via Administration:
  
1. Log på Microsoft 365 Administration ([https://admin.microsoft.com](https://admin.microsoft.com)) med din **brugeradministrator**- eller **global administratorkonto**.
    
2. Klik på **Fakturering** i venstre navigationsrude på startsiden **i Administration**, og klik derefter på **Køb tjenester**.
    
3. Køb dine nye abonnementer på siden **Køb tjenester** .
    
Administration tildeler organisationen og Azure AD-lejeren for dit Microsoft 365 abonnement til de nye abonnementer på SaaS-baserede cloudtilbud.
  
Sådan tilføjer du et Azure-abonnement med den samme organisation og Azure AD-lejer som dit Microsoft 365-abonnement:
  
1. Log på Azure Portal ([https://portal.azure.com](https://portal.azure.com)) med din Microsoft 365 **Azure AD DC-administrator** eller **global administratorkonto**.
    
2. Klik på Abonnementer i venstre **navigationsrude**, og klik derefter på **Tilføj**.
    
3. På siden **Tilføj abonnement** skal du vælge et tilbud og udfylde betalingsoplysningerne og aftalen.
    
Hvis du har købt Azure- og Microsoft 365-abonnementer separat og vil have adgang til den Microsoft 365 Azure AD-lejer fra dit Azure-abonnement, skal du se vejledningen i [Føj et eksisterende Azure-abonnement til din Azure Active Directory lejer](/azure/active-directory/fundamentals/active-directory-how-subscriptions-associated-directory).
 
## <a name="see-also"></a>Se også

[Illustrationer af Microsoft Cloud til virksomhedsarkitekter](../solutions/cloud-architecture-models.md)
  
[Arkitektoniske modeller til SharePoint, Exchange, Skype for Business og Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Hybridløsninger](hybrid-solutions.md)

## <a name="next-step"></a>Næste trin

[Vurderer Microsoft 365 netværksforbindelse](assessing-network-connectivity.md)
