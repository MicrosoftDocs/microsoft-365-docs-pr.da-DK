---
title: Automatiser licensering og gruppemedlemskab for dit Microsoft 365 til virksomhedstestmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Konfigurer gruppebaserede licenser og dynamisk gruppemedlemskab i dit Microsoft 365 til virksomhedstestmiljø.
ms.openlocfilehash: 1d471076ac07acb023cdf785233ea2222690b596
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097530"
---
# <a name="automate-licensing-and-group-membership-for-your-microsoft-365-for-enterprise-test-environment"></a>Automatiser licensering og gruppemedlemskab for dit Microsoft 365 til virksomhedstestmiljø

*Denne testlaboratorievejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

Gruppebaserede licenser tildeler eller fjerner automatisk licenser for en brugerkonto baseret på gruppemedlemskab. Medlemskab af dynamisk gruppe tilføjer eller fjerner medlemmer til en gruppe baseret på egenskaber for brugerkonto, f.eks **. Afdeling** eller **Land**. I denne artikel gennemgås demonstrationer af både tilføjelse og fjernelse af gruppemedlemmer i dit Microsoft 365 til virksomhedstestmiljø.

Konfiguration af automatisk licensering og dynamisk gruppemedlemskab i dit Microsoft 365 til virksomhedstestmiljø omfatter to faser:

- [Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Konfigurer og test dynamisk gruppemedlemskab og automatisk licensering](#phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing)

![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø

Hvis du kun vil teste automatiseret licensering og gruppemedlemskab på en let måde med minimumskravene, skal du følge vejledningen i [Konfiguration af Letvægtsbase](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil teste automatiseret licensering og gruppemedlemskab i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af automatiserede licenser og gruppemedlemskaber kræver ikke det simulerede testmiljø for virksomheder, hvilket omfatter et simuleret intranet, der er forbundet til internet- og mappesynkronisering for et AD DS-område (Active Directory-domæneservices). Det leveres her som en mulighed, så du kan teste automatiserede licenser og gruppemedlemskab og eksperimentere med det i et miljø, der repræsenterer en typisk organisation.
  
## <a name="phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing"></a>Fase 2: Konfigurer og test dynamisk gruppemedlemskab og automatisk licensering

Først skal du oprette en ny gruppe med navnet Sales og tilføje en regel for dynamisk gruppemedlemskab, så brugerkonti, hvor **Afdeling** er angivet til **Salg** , automatisk deltager i gruppen Salg.

1. Log på [Microsoft 365 Administration](https://admin.microsoft.com) med den globale administratorkonto for dit Microsoft 365 E5 testlaboratorium i en privat forekomst af din internetbrowser.
2. Gå til Azure Portal på en separat fane i browseren på [https://portal.azure.com](https://portal.azure.com).
3. I Azure Portal skal du angive **grupper** i søgefeltet og derefter vælge **Grupper**.
4. i ruden **Alle grupper** skal du vælge **Ny gruppe**.
5. Vælg **Microsoft 365** i **Gruppetype**.
6. I **Gruppenavn** skal du angive **Salg**.
7. Vælg **Dynamisk bruger** i **Medlemskabstype**.
8. Vælg **Dynamiske brugermedlemmer**.
9. I ruden **Regler for dynamisk medlemskab** : 
   - Vælg **afdelingens** egenskab.
   - Vælg operatoren **Er lig med** .
   - I feltet **Værdi** skal du angive **Salg**.
10. Vælg **Gem**.
11. Vælg **Opret**.

Konfigurer derefter gruppen Salg, så medlemmerne automatisk tildeles den Microsoft 365 E5 licens.

1. Vælg gruppen **Salg** , og vælg derefter **Licenser**.
2. I ruden **Opdater licenstildelinger** skal du vælge **Microsoft 365 E5** og derefter vælge **Gem**.
3. Luk fanen Azure Portal i din browser.

Derefter skal du teste dynamisk gruppemedlemskab og automatisk licensering på bruger 4-kontoen:

1. Vælg **Administrator** på fanen **Microsoft Office Startside** i din browser.
2. Vælg **Aktive brugere** under fanen **Microsoft 365 Administration**.
3. Vælg **bruger 4-kontoen** på siden **Aktive brugere**.
4. I ruden **Bruger 4** skal du vælge **Rediger** for **produktlicenser**.
5. Deaktiver **Microsoft 365 E5-licensen** i ruden **Produktlicenser**, og vælg derefter **GemLuk** > .
6. I egenskaberne for bruger 4-kontoen skal du kontrollere, at der ikke er tildelt nogen produktlicenser, og at der ikke er nogen gruppemedlemskaber.
7. Vælg **Rediger** for **Kontaktoplysninger**.
8. Vælg **Kontaktoplysninger** i ruden **Rediger kontaktoplysninger**.
9. I feltet **Afdeling** skal du angive **Salg** og derefter vælge **GemLuk** > .
10. Vent et par minutter, og vælg derefter jævnligt ikonet **Opdater** øverst til højre i kontoruden Bruger 4.

Med tiden bør du se:

- Egenskaben **Gruppemedlemskaber** blev opdateret med gruppen **Salg**.
- Egenskaben **Produktlicenser** er opdateret med **Microsoft 365 E5-licensen**.

Se disse artikler for at udrulle dynamisk gruppemedlemskab og automatisk licensering i produktion:

- [Gruppebaserede licenser i Azure Active Directory](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)
- [Dynamiske grupper i Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og -funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Udrul identitet](deploy-identity-solution-overview.md)

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)