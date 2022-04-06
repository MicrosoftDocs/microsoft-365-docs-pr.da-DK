---
title: Microsoft 365 til Enterprise Test Lab-vejledninger
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Brug disse Test Lab-vejledninger til at konfigurere demonstration, koncepttest eller udviklings-/testmiljøer for Microsoft 365 til virksomheder.
ms.openlocfilehash: 18b243a0fea9cb4864a0375740c4ebadcc44d6c3
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681650"
---
# <a name="microsoft-365-for-enterprise-test-lab-guides"></a>Microsoft 365 til Enterprise Test Lab-vejledninger

*Dette gælder både for Microsoft 365 til virksomheder og Office 365 Enterprise.*

Test Lab Guides (TLG'er) hjælper dig med hurtigt at få mere at vide om Microsoft-produkter. De giver præskrivive instruktioner til konfiguration af forenklede, men repræsentative testmiljøer. Du kan bruge disse miljøer til demonstration, tilpasning eller oprettelse af komplekse koncept gennem prøveabonnementer eller betalte abonnementer.

TGS er designet til at være modulære. De bygger videre på hinanden for at oprette flere konfigurationer, der i højere grad passer til dine behov for lærings- eller testkonfiguration. Den praktiske oplevelse "Jeg har udviklet det selv, og det fungerer" hjælper dig med at forstå installationskravene til et nyt produkt eller scenarie, så du bedre kan planlægge at hoste det i produktion.

Du kan også bruge TGS til at oprette repræsentative miljøer til udvikling og test af programmer, også kaldet udviklings-/testmiljøer.
  
![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

Hvis du vil have et visuelt kort over alle artikler i Microsoft 365 for Enterprise Test Lab Guide-stakken, skal du udvide følgende grafik eller gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

[![The Microsoft 365 for enterprise Test Lab Guide stack.](../media/m365-enterprise-test-lab-guides/microsoft-365-enterprise-tlg-stack.png)](../downloads/Microsoft365EnterpriseTLGStack.pdf)

## <a name="base-configuration"></a>Grundlæggende konfiguration

Først skal du oprette et testmiljø [til Microsoft 365 til virksomheder](/microsoft-365-enterprise/). Du kan oprette to forskellige typer grundlæggende konfigurationer:

- [Let basiskonfiguration](lightweight-base-configuration-microsoft-365-enterprise.md) – Brug dette, når du vil konfigurere og demonstrere Microsoft 365 til virksomhedsfunktioner og -funktioner i et miljø, der kun findes i skyen, og som ikke omfatter nogen lokale komponenter.

- [Simuleret virksomhedsbasekonfiguration](simulated-ent-base-configuration-microsoft-365-enterprise.md) – Brug dette, når du vil konfigurere og demonstrere Microsoft 365 til virksomhedsfunktioner og -funktioner i et hybridt skymiljø, som bruger lokale komponenter som f.eks. et Active Directory-domæneservices-domæne (AD DS).

Du kan også oprette testmiljøer til Office 365 E5 ved ikke at føje Microsoft 365 E5-licensen til dit prøve- eller produktionstestmiljø.
    
## <a name="identity"></a>Identitet

Hvis du vil demonstrere identitetsrelaterede funktioner og egenskaber, skal du se:

- [Synkronisering af adgangskodehash](password-hash-sync-m365-ent-test-environment.md)
  
   Aktivér og test adgangskodehashbaseret katalogsynkronisering fra en AD DS domænecontroller.

- [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md)
  
   Aktivér og test pass-through-godkendelse for en AD DS domænecontroller.

- [Federated Authentication](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
   Aktivér og test godkendelse i organisationsnetværket for en AD DS domænecontroller.

- [Azure AD Seamless Single Sign-on](single-sign-on-m365-ent-test-environment.md)
  
   Aktivér og test Azure AD Seamless Single Sign-on (Seamless SSO) med en AD DS domænecontroller.

- [Multifaktorgodkendelse](multi-factor-authentication-microsoft-365-test-environment.md)
  
   Aktivér og test smart phone-baseret multifaktorgodkendelse for en bestemt brugerkonto.

- [Beskyt globale administratorkonti](protect-global-administrator-accounts-microsoft-365-test-environment.md)

   Lås dine globale administratorkonti med politikker for betinget adgang.

- [Tilbageførsel af adgangskode](password-writeback-m365-ent-test-environment.md)

   Brug tilbageførsel af adgangskode til at ændre adgangskoden AD DS din brugerkonto fra Azure AD.

- [Nulstilling af adgangskode](password-reset-m365-ent-test-environment.md)

   Brug selvbetjening til nulstilling af adgangskode til at nulstille din adgangskode.

- [Automatisk licensering og gruppemedlemskab](automate-licenses-group-membership-microsoft-365-test-environment.md)

   Gør administration af nye konti nemmere end nogensinde før med automatisk licensering og dynamisk gruppemedlemskab.

- [Azure AD Identity Protection](azure-ad-identity-protection-microsoft-365-test-environment.md)

   Scan dine aktuelle brugerkonti for sårbarheder.

- [Identitets- og enhedsadgang](identity-device-access-m365-test-environment.md)

   Opret et miljø til test af anbefalede identitets- og enhedsadgangskonfigurationer og politikker for betinget adgang.

## <a name="mobile-device-management"></a>Administration af mobilenheder

Hvis du vil demonstrere funktioner og funktioner relateret til administration af mobilenheder, skal du se:

- [Politikker for overholdelse af enhed](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
    
   Opret en brugergruppe og en politik for enhedsoverholdelse for Windows 10 enheder.
    
- [Tilmeld iOS- og Android-enheder](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
   
   Tilmeld dig iOS- eller Android-enheder, og administrer dem eksternt.

## <a name="information-protection"></a>Beskyttelse af oplysninger

Hvis du vil demonstrere funktioner og funktioner til beskyttelse af oplysninger, skal du se:

- [Øget Microsoft 365 sikkerhed](increased-o365-security-microsoft-365-enterprise-dev-test-environment.md)
    
   Konfigurer indstillinger for at øge Microsoft 365 sikkerhed og undersøge indbyggede sikkerhedsværktøjer.
  
- [Dataklassificering](data-classification-microsoft-365-enterprise-dev-test-environment.md)
    
   Konfigurere og anvende navne på et dokument på et SharePoint-teamwebsted.
    
- [Adgangsstyring med rettigheder](privileged-access-microsoft-365-enterprise-dev-test-environment.md)
    
   Konfigurer adgangsstyring med rettigheder til just-in-time adgang til administrator- og privilegerede opgaver i organisationen.