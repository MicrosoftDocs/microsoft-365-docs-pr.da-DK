---
title: Beskyt globale administratorkonti i din Microsoft 365 for Enterprise Test-miljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/12/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Brug disse trin til at beskytte globale administratorkonti i Microsoft 365 for Enterprise Test Environment.
ms.openlocfilehash: a759d4e8720216019886f33ca0df7325b5209930
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63587858"
---
# <a name="protect-global-administrator-accounts-in-your-microsoft-365-for-enterprise-test-environment"></a>Beskyt globale administratorkonti i din Microsoft 365 for Enterprise Test-miljø

*Denne Test Lab-vejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

Du kan forhindre digitale angreb på din organisation ved at sikre, at dine administratorkonti er så sikre som muligt. 

I denne artikel beskrives det, hvordan du Azure Active Directory politikker for betinget adgang (Azure AD) til at beskytte globale administratorkonti.

Beskyttelse af globale administratorkonti i Microsoft 365 virksomhedens testmiljø omfatter to faser:
- [Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Konfigurere politikker for betinget adgang](#phase-2-configure-conditional-access-policies)

![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment

Hvis du let vil teste global administratorkontobeskyttelse på en let måde med minimumskravene, skal du følge vejledningen i [Let basiskonfiguration](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil teste global administratorkontobeskyttelse i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af global administratorkontobeskyttelse kræver ikke det simulerede virksomhedstestmiljø, som omfatter en simuleret intranetforbindelse til internettet og katalogsynkronisering for en Active Directory-domæneservices (AD DS). Den findes her som en mulighed, så du kan teste global administratorkontobeskyttelse og eksperimentere med den i et miljø, der repræsenterer en typisk organisation. 
  
## <a name="phase-2-configure-conditional-access-policies"></a>Fase 2: Konfigurere politikker for betinget adgang

Først skal du oprette en ny brugerkonto som en dedikeret global administrator.

1. På en separat fane skal du åbne [Microsoft 365 Administration](https://admin.microsoft.com/).
2. Vælg **BrugereAktivér** >  brugere, og vælg derefter **Tilføj en bruger**.
3. I **ruden Tilføj** bruger skal du **skrive DedicatedAdmin** **i felterne Fornavn**, Vist navn **og** Brugernavn.
4. Vælg **Adgangskode**, vælg **Lad mig oprette adgangskoden**, og angiv derefter en stærk adgangskode. Optag adgangskoden til denne nye konto på et sikkert sted.
5. Vælg **Næste**.
6. I **ruden Tildel produktlicenser** skal **du Microsoft 365 E5** produktlicenser og derefter vælge **Næste**.
7. I **ruden Valgfri indstillinger** skal du **vælge RolesAdmin** >  **center accessGlobal** >  **adminNext** > .
8. I **ruden Du er næsten færdig skal** du vælge **Afslut tilføjelse** og derefter vælge **Luk**.

Derefter skal du oprette en ny gruppe med navnet GlobalAdmins og føje DedicatedAdmin-kontoen til den.

1. På fanen **Microsoft 365 Administration** skal du vælge **Grupper** i venstre navigationsrude og derefter vælge **Grupper**.
2. Vælg **Tilføj en gruppe**.
3. I **ruden Vælg en gruppetype** skal du **vælge Sikkerhed** og derefter vælge **Næste**.
4. Vælg **Opret gruppe i ruden Konfigurer** de grundlæggende **funktioner**, og vælg derefter **Luk**.
5. I **ruden Gennemse og afslut tilføjelse** af gruppe skal **du angive GlobalAdmins** og derefter vælge **Næste**.
7. Vælg gruppen **GlobalAdmins på listen over** grupper.
8. I **ruden GlobalAdmins** skal du **vælge Medlemmer** og derefter vælge **Vis alle og administrer medlemmer**.
9. I **ruden GlobalAdmins** skal du vælge Tilføj **medlemmer, vælge** **DedicatedAdmin-kontoen** og din globale administratorkonto og derefter vælge **GemLukLuk** >  > .

Dernæst skal du oprette betingede adgangspolitikker, der kræver multifaktorgodkendelse for globale administratorkonti og for at afvise godkendelse, hvis risikoen for logon er mellem eller høj.

Denne første politik kræver, at alle globale administratorkonti bruger MFA.

1. Gå til i en ny fane i browseren [https://portal.azure.com](https://portal.azure.com).
2. Klik **Azure Active Directory** >  **SecurityConditional** >  Access.
3. I **ruden Betinget adgang – Politikker** skal du vælge **Oprindelig politik: Kræv MFA for administratorer (eksempel)**.
4. I **ruden Oprindelig planpolitik** skal du **vælge Brug politik med det samme > Gem**.

Denne anden politik blokerer adgangen til global administratorkontogodkendelse, når logon risikoen er mellem eller høj.

1. I **ruden Betinget adgang – Politikker** skal du vælge **Ny politik**.
2. I **ruden Ny** skal du angive **Globale administratorer** i **Navn**.
3. I sektionen **Opgaver skal** du vælge **Brugere og grupper**.
4. På fanen **Medtag** i **ruden Brugere og grupper** skal du **vælge Vælg brugere og grupperBrugere** >  **og grupperVælg** > .
5. I **ruden** Vælg skal du **vælge gruppen GlobalAdmins** og derefter vælge **SelectDone** > .
6. I sektionen **Opgaver skal** du vælge **Betingelser**.
7. I **ruden** Betingelser skal du **vælge Logonrisici**, vælge **Ja** **til Konfigurer**, vælge Høj og  **Mellem** og derefter vælge **Vælg** og **Udført**.
8. I sektionen **Access-kontrolelementer** i **ruden Ny** skal du vælge **Giv**.
9. I **ruden Giv** skal du **vælge Bloker adgang** og derefter vælge **Vælg**.
10. I **ruden Ny** skal du **vælge Til** for **Aktivér politik** og derefter vælge **Opret**.
11. Luk **Azure-portalen,** og **Microsoft 365 Administration fanerne**.

For at teste den første politik skal du logge af og logge på med DedicatedAdmin-kontoen. Du bør blive bedt om at konfigurere MFA. Dette viser, at den første politik anvendes.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Udrul identitet](deploy-identity-solution-overview.md)

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)