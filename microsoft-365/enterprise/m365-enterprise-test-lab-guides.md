---
title: vejledninger til Microsoft 365 til testlaboratorier til virksomheder
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/20/2019
audience: ITPro
ms.topic: landing-page
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: Brug disse testlaboratorievejledninger til at konfigurere demonstrations-, blåstemplings- eller udviklings-/testmiljøer for Microsoft 365 til virksomheder.
ms.openlocfilehash: 8c4444b599682ad40ebba88b37d83125fccd99f0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097420"
---
# <a name="microsoft-365-for-enterprise-test-lab-guides"></a>vejledninger til Microsoft 365 til testlaboratorier til virksomheder

*Dette gælder både for Microsoft 365 for store og Office 365 Enterprise.*

Test Lab Guides (TLGs) hjælper dig med hurtigt at få mere at vide om Microsoft-produkter. De indeholder præskriptive instruktioner til konfiguration af forenklede, men repræsentative testmiljøer. Du kan bruge disse miljøer til demonstration, tilpasning eller oprettelse af komplekse blåstemplingsbeviser i varigheden af en prøveversion eller et betalt abonnement.

TLGs er designet til at være modulopbyggede. De bygger på hinanden for at oprette flere konfigurationer, der passer bedre til dine behov for læring eller testkonfiguration. "Jeg har selv bygget det ud, og det fungerer" praktisk erfaring hjælper dig med at forstå installationskravene for et nyt produkt eller scenarie, så du bedre kan planlægge at hoste det i produktion.

Du kan også bruge TLGs til at oprette repræsentative miljøer til udvikling og test af programmer, også kaldet udviklings-/testmiljøer.
  
![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du udvide følgende grafik eller gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

[![Stakken Microsoft 365 til testlaboratorier til virksomheder.](../media/m365-enterprise-test-lab-guides/microsoft-365-enterprise-tlg-stack.png)](../downloads/Microsoft365EnterpriseTLGStack.pdf)

## <a name="base-configuration"></a>Grundlæggende konfiguration

Først skal du oprette et testmiljø for [Microsoft 365 til virksomheder](/microsoft-365-enterprise/). Du kan oprette to forskellige typer basiskonfigurationer:

- [Letvægtsbasekonfiguration](lightweight-base-configuration-microsoft-365-enterprise.md) – Brug dette, når du vil konfigurere og demonstrere Microsoft 365 til virksomhedsfunktioner og -funktioner i et miljø, der kun indeholder cloudmiljøer, og som ikke indeholder komponenter i det lokale miljø.

- [Simuleret basiskonfiguration for virksomheder](simulated-ent-base-configuration-microsoft-365-enterprise.md) – Brug dette, når du vil konfigurere og demonstrere Microsoft 365 til virksomhedsfunktioner og -funktioner i et hybridt cloudmiljø, som bruger komponenter i det lokale miljø, f.eks. et AD DS-domæne (Active Directory-domæneservices).

Du kan også oprette testmiljøer til Office 365 E5 ved ikke at føje Microsoft 365 E5-licensen til dit prøveversions- eller produktionstestmiljø.
    
## <a name="identity"></a>Identitet

Hvis du vil demonstrere identitetsrelaterede funktioner og egenskaber, skal du se:

- [Synkronisering af adgangskode-hash](password-hash-sync-m365-ent-test-environment.md)
  
   Aktivér og test synkronisering af adgangskodehashbaseret katalog fra en AD DS-domænecontroller.

- [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md)
  
   Aktivér og test pass-through-godkendelse til en AD DS-domænecontroller.

- [Federated Authentication](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
   Aktivér og test sammenkædet godkendelse til en AD DS-domænecontroller.

- [Problemfrit enkeltlogon i Azure AD](single-sign-on-m365-ent-test-environment.md)
  
   Aktivér og test Azure AD Seamless Single Sign-on (Seamless SSO) med en AD DS-domænecontroller.

- [Multifaktorgodkendelse](multi-factor-authentication-microsoft-365-test-environment.md)
  
   Aktivér og test multifaktorgodkendelse baseret på smartphones for en bestemt brugerkonto.

- [Beskyt globale administratorkonti](protect-global-administrator-accounts-microsoft-365-test-environment.md)

   Lås dine globale administratorkonti med politikker for betinget adgang.

- [Tilbageførsel af adgangskode](password-writeback-m365-ent-test-environment.md)

   Brug tilbageførsel af adgangskode til at ændre adgangskoden på din AD DS-brugerkonto fra Azure AD.

- [Nulstilling af adgangskode](password-reset-m365-ent-test-environment.md)

   Brug selvbetjent nulstilling af adgangskode til at nulstille din adgangskode.

- [Automatisk licensering og gruppemedlemskab](automate-licenses-group-membership-microsoft-365-test-environment.md)

   Gør det nemmere end nogensinde før at administrere nye konti med automatisk licensering og dynamisk gruppemedlemskab.

- [Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md)

   Scan dine aktuelle brugerkonti for sikkerhedsrisici.

- [Identitets- og enhedsadgang](identity-device-access-m365-test-environment.md)

   Opret et miljø for at teste anbefalede konfigurationer for identitets- og enhedsadgang og politikker for betinget adgang.

## <a name="mobile-device-management"></a>Administration af mobilenheder

Hvis du vil demonstrere funktioner og egenskaber, der er relateret til administration af mobilenheder, skal du se:

- [Politikker for enhedsoverholdelse](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
   Opret en brugergruppe og en politik for enhedsoverholdelse for Windows 10 enheder.
    
- [Tilmeld iOS- og Android-enheder](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
   
   Tilmeld iOS- eller Android-enheder, og administrer dem eksternt.

## <a name="information-protection"></a>Beskyttelse af oplysninger

Hvis du vil demonstrere funktioner og egenskaber, der er relateret til beskyttelse af oplysninger, skal du se:

- [Øget Microsoft 365 sikkerhed](increased-o365-security-microsoft-365-enterprise-dev-test-environment.md)
    
   Konfigurer indstillinger for øget Microsoft 365 sikkerhed, og undersøg indbyggede sikkerhedsværktøjer.
  
- [Klassificering af data](data-classification-microsoft-365-enterprise-dev-test-environment.md)
    
   Konfigurer og anvend mærkater på et dokument på et SharePoint Online-teamwebsted.
    
- [Privileged Access Management](privileged-access-microsoft-365-enterprise-dev-test-environment.md)
    
   Konfigurer privilegeret adgangsstyring for just-in-time-adgang til udvidede og privilegerede opgaver i din organisation.