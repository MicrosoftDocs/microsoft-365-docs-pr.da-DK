---
title: Beskyt globale administratorkonti i dit Microsoft 365 til virksomhedstestmiljøer
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/12/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Brug disse trin til at beskytte globale administratorkonti i dit Microsoft 365 til virksomhedstestmiljø.
ms.openlocfilehash: bf053b9767aea4a290c5357d6309c57677a36cad
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098268"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-for-enterprise-test-environment"></a>Beskyt globale administratorkonti i dit Microsoft 365 til virksomhedstestmiljøer

*Denne testlaboratorievejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

Du kan forhindre digitale angreb på din organisation ved at sikre, at dine administratorkonti er så sikre som muligt. 

I denne artikel beskrives det, hvordan du bruger politikker for betinget adgang Azure Active Directory (Azure AD) til at beskytte globale administratorkonti.

Beskyttelse af globale administratorkonti i dit Microsoft 365 til virksomhedstestmiljøer omfatter to faser:
- [Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Konfigurer politikker for betinget adgang](#phase-2-configure-conditional-access-policies)

![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø

Hvis du vil teste den globale administratorkontobeskyttelse på en let måde med minimumskravene, skal du følge vejledningen i [Konfiguration af letvægtsbase](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil teste den globale beskyttelse af administratorkonti i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af global beskyttelse af administratorkonti kræver ikke det simulerede virksomhedstestmiljø, som omfatter et simuleret intranet, der er forbundet med internet- og katalogsynkronisering for en AD DS (Active Directory-domæneservices). Den leveres her som en mulighed, så du kan teste den globale beskyttelse af administratorkonti og eksperimentere med den i et miljø, der repræsenterer en typisk organisation. 
  
## <a name="phase-2-configure-conditional-access-policies"></a>Fase 2: Konfigurer politikker for betinget adgang

Først skal du oprette en ny brugerkonto som en dedikeret global administrator.

1. Åbn [Microsoft 365 Administration](https://admin.microsoft.com/) på en separat fane.
2. Vælg **BrugereAktive** >  brugere, og vælg derefter **Tilføj en bruger**.
3. I ruden **Tilføj bruger** skal du angive **DedicatedAdmin** i felterne **Fornavn**, **Vist navn** og **Brugernavn** .
4. Vælg **Adgangskode**, vælg **Lad mig oprette adgangskoden**, og angiv derefter en stærk adgangskode. Registrer adgangskoden for denne nye konto på en sikker placering.
5. Vælg **Næste**.
6. I ruden **Tildel produktlicenser** skal du vælge **Microsoft 365 E5** og derefter vælge **Næste**.
7. I ruden **Valgfrie indstillinger** skal du vælge **RollerAdministrationsadgangGlobal** >  >  **administratorNæste** > .
8. I ruden **Du er næsten færdig** skal du vælge **Afslut tilføjelse** og derefter vælge **Luk**.

Opret derefter en ny gruppe med navnet GlobalAdmins, og føj kontoen DedicatedAdmin til den.

1. På fanen **Microsoft 365 Administration** skal du vælge **Grupper** i venstre navigationsrude og derefter vælge **Grupper**.
2. Vælg **Tilføj en gruppe**.
3. I ruden **Vælg en gruppetype** skal du vælge **Sikkerhed** og derefter vælge **Næste**.
4. I ruden **Konfigurer de grundlæggende** funktioner skal du vælge **Opret gruppe** og derefter vælge **Luk**.
5. I ruden **Gennemse og afslut tilføjelsen af gruppe** skal du angive **GlobalAdministratorer** og derefter vælge **Næste**.
7. Vælg gruppen **GlobalAdmins** på listen over grupper.
8. I ruden **GlobalAdmins** skal du vælge **Medlemmer** og derefter vælge **Vis alle og administrer medlemmer**.
9. I ruden **GlobalAdmins** skal du vælge **Tilføj medlemmer**, vælge **DedikeretAdministratorkonto** og din globale administratorkonto og derefter vælge **GemLukLuk** >  > .

Opret derefter politikker for betinget adgang for at kræve multifaktorgodkendelse for globale administratorkonti og for at afvise godkendelse, hvis logonrisikoen er mellem eller høj.

Denne første politik kræver, at alle globale administratorkonti bruger MFA.

1. Gå til [https://portal.azure.com](https://portal.azure.com)under en ny fane i browseren.
2. Klik **på Azure Active Directory** >  **SikkerhedKonditional** >  adgang.
3. I ruden **Betinget adgang – politikker** skal du vælge **Oprindelig politik: Kræv MFA for administratorer (prøveversion)**.
4. I ruden **Oprindelig politik** skal du vælge **Brug politik med det samme > Gem**.

Denne anden politik blokerer adgang til global godkendelse af administratorkonto, når logonrisikoen er mellem eller høj.

1. I ruden **Betinget adgang – politikker** skal du vælge **Ny politik**.
2. I ruden **Ny** skal du angive **Globale administratorer** i **Navn**.
3. I afsnittet **Tildelinger** skal du vælge **Brugere og grupper**.
4. På fanen **Medtag** i ruden **Brugere og grupper** skal du vælge **Vælg brugere og grupperBrugere** >  **og** **grupperVælg** > .
5. I ruden **Vælg** skal du vælge gruppen **GlobalAdmins** og derefter vælge **SelectDone** > .
6. I afsnittet **Tildelinger** skal du vælge **Betingelser**.
7. I ruden **Betingelser** skal du vælge **Logonrisiko**, vælge **Ja** for **Konfigurer**, vælge **Høj** og **Mellem** og derefter vælge **Vælg** og **Udført**.
8. I afsnittet **Adgangskontrolelementer** i ruden **Ny** skal du vælge **Giv**.
9. Vælg **Bloker adgang** i ruden **Grant (Giv** adgang), og vælg derefter **Vælg**.
10. I ruden **Ny** skal du vælge **Til** for **Aktivér politik** og derefter vælge **Opret**.
11. Luk **fanerne Azure Portal** og **Microsoft 365 Administration**.

Hvis du vil teste den første politik, skal du logge af og logge på med DedicatedAdmin-kontoen. Du bør blive bedt om at konfigurere MFA. Det viser, at den første politik anvendes.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og -funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Udrul identitet](deploy-identity-solution-overview.md)

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)