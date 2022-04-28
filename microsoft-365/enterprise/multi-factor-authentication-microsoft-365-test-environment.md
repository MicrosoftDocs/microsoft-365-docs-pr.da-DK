---
title: Microsoft 365 til multifaktorgodkendelse i virksomhedstestmiljø
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
- seo-marvel-apr2020
- admindeeplinkMAC
description: Konfigurer multifaktorgodkendelse ved hjælp af tekstmeddelelser, der sendes til en smartphone i dit Microsoft 365 til virksomhedstestmiljø.
ms.openlocfilehash: aa72375342bdf60e1fe1bc504f14b1f51a48b701
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078729"
---
# <a name="multi-factor-authentication-for-your-microsoft-365-for-enterprise-test-environment"></a>Multifaktorgodkendelse for dit Microsoft 365 til virksomhedstestmiljø

*Denne testlaboratorievejledning kan bruges til både Microsoft 365 til virksomheds- og Office 365 Enterprise testmiljøer.*

Hvis du vil have et yderligere sikkerhedsniveau for at logge på Microsoft 365 eller en hvilken som helst tjeneste eller et hvilket som helst program, der bruger Azure AD-lejeren til dit abonnement, kan du aktivere Multifaktorgodkendelse i Azure AD, hvilket kræver mere end blot et brugernavn og en adgangskode for at bekræfte en konto.

Med multifaktorgodkendelse skal brugerne bekræfte et telefonopkald, skrive en bekræftelseskode, der sendes i en sms, eller bekræfte godkendelsen med en app på deres smartphones, når de har indtastet deres adgangskoder korrekt. De kan kun logge på, når den anden godkendelsesfaktor er opfyldt.
  
I denne artikel beskrives det, hvordan du aktiverer og tester tekstmeddelelsesbaseret godkendelse for en bestemt brugerkonto.
  
Konfiguration af multifaktorgodkendelse for en konto i dit Microsoft 365 til virksomhedstestmiljø omfatter to faser og en tredje valgfri fase:
- [Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Aktivér og test multifaktorgodkendelse for bruger 2-kontoen](#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account)
- [Fase 3: Aktivér og test multifaktorgodkendelse med en politik for betinget adgang](#phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy)

![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø

Hvis du blot vil teste multifaktorgodkendelse på en let måde med minimumskravene, skal du følge vejledningen i [Konfiguration af letvægtsbase](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil teste multifaktorgodkendelse i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af multifaktorgodkendelse kræver ikke det simulerede virksomhedstestmiljø, som omfatter et simuleret intranet, der er forbundet med internet- og katalogsynkronisering for et AD DS-område (Active Directory-domæneservices). Den leveres her som en mulighed, så du kan teste multifaktorgodkendelse og eksperimentere med den i et miljø, der repræsenterer en typisk organisation.
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Fase 2: Aktivér og test multifaktorgodkendelse for bruger 2-kontoen

Aktivér multifaktorgodkendelse for Bruger 2-kontoen ved hjælp af disse trin:
  
1. Åbn en separat privat forekomst af din browser, gå til Microsoft 365 Administration ([https://portal.microsoft.com](https://portal.microsoft.com)), og log derefter på med din globale administratorkonto.
    
2. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**BrugereAktive**</a> >  brugere i venstre navigationsrude.
    
3. I ruden Aktive brugere skal du vælge **Multifaktorgodkendelse**.
    
4. Vælg **bruger 2-kontoen** på listen.
    
5. I afsnittet **Bruger 2** under **Hurtige trin** skal du vælge **Aktivér**.
    
6. I dialogboksen **Om aktivering af godkendelse med flere faktorer** skal du vælge **Aktivér godkendelse med flere faktorer**.
    
7. Vælg **Luk** i dialogboksen **Opdateringer lykkedes**.
    
8. På fanen **Microsoft 365 Administration** skal du vælge brugerkontoikonet øverst til højre og derefter vælge **Log af**.
    
9. Luk din browserforekomst.
   
Fuldfør konfigurationen for bruger 2-kontoen for at bruge en tekstmeddelelse til validering, og test den med disse trin:
  
1. Åbn en ny privat forekomst af browseren.
    
2. Gå til [Microsoft 365 Administration](https://admin.microsoft.com), og log på med bruger 2-kontonavnet og -adgangskoden.
    
3. Når du er logget på, bliver du bedt om at konfigurere kontoen for at få flere oplysninger. Vælg **Næste**.
    
4. På siden **Yderligere sikkerhedsgodkendelse** :
    
   - Vælg dit land eller område.
    
   - Angiv telefonnummeret på den smartphone, der skal modtage sms'er.
    
   - I **Metode** skal du vælge **Send mig en kode via sms**.
    
5. Vælg **Næste**.
    
6. Angiv bekræftelseskoden fra den tekstmeddelelse, du har modtaget på din smartphone, og vælg derefter **Bekræft**.
    
7. På siden **Trin 3: Bevar dine eksisterende programmer** skal du vælge **Udført**.
    
8. Hvis det er første gang, du logger på med bruger 2-kontoen, bliver du bedt om at ændre adgangskoden. Angiv den oprindelige adgangskode og en ny adgangskode to gange, og vælg derefter **Opdater adgangskode, og log på**. Registrer den nye adgangskode på en sikker placering.
    
    Du kan se Office-portalen for Bruger 2 på fanen **Microsoft Office Startside** i browseren.

## <a name="phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy"></a>Fase 3: Aktivér og test multifaktorgodkendelse med en politik for betinget adgang

*Denne fase kan kun bruges til et Microsoft 365 til virksomhedstestmiljøer.*

I denne fase aktiverer du multifaktorgodkendelse for bruger 3-kontoen ved hjælp af en gruppe og en politik for betinget adgang.

Opret derefter en ny gruppe med navnet MFAUsers, og føj kontoen User 3 til den.

1. På fanen **Microsoft 365 Administration** skal du vælge **Grupper** i venstre navigationsrude og derefter vælge <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupper**</a>.
2. Vælg **Tilføj en gruppe**.
3. I ruden **Vælg en gruppetype** skal du vælge **Sikkerhed** og derefter vælge **Næste**.
4. I ruden **Konfigurer de grundlæggende** funktioner skal du vælge **Opret gruppe** og derefter vælge **Luk**.
5. I ruden **Gennemse og afslut tilføjelsen af gruppe** skal du angive **MFAUsers** og derefter vælge **Næste**.
6. Vælg gruppen **MFAUsers** på listen over grupper.
7. I ruden **MFAUsers** skal du vælge **Medlemmer** og derefter vælge **Få vist alle og administrere medlemmer**.
8. I ruden **MFAUsers** skal du vælge **Tilføj medlemmer**, vælge **bruger 3-kontoen** og derefter vælge **GemLukLuk** >  > .

Opret derefter en politik for betinget adgang for at kræve multifaktorgodkendelse for medlemmer af gruppen MFAUsers.

1. Gå til [https://portal.azure.com](https://portal.azure.com)under en ny fane i browseren.
2. Vælg **Azure Active Directory** >  **SikkerhedKonditional** >  adgang.
3. I ruden **Betinget adgang – politikker** skal du vælge **Ny politik**.
4. I ruden **Ny** skal du angive **MFA for brugerkonti** i feltet **Navn** .
5. I afsnittet **Tildelinger** skal du vælge **Brugere og grupper**.
6. På fanen **Medtag** i ruden **Brugere og grupper** skal du vælge **Vælg brugere og grupperBrugere** >  **og** **grupperVælg** > .
7. I ruden **Vælg** skal du vælge gruppen **MFAUsers** og derefter vælge **SelectDone** > .
8. I afsnittet **Adgangskontrolelementer** i ruden **Ny** skal du vælge **Giv**.
9. I ruden **Grant** skal du vælge **Kræv multifaktorgodkendelse** og derefter vælge **Vælg**.
10. I ruden **Ny** skal du vælge **Til** for **Aktivér politik** og derefter vælge **Opret**.
11. Luk **fanerne Azure Portal** og **Microsoft 365 Administration**.

Hvis du vil teste denne politik, skal du logge af og logge på med bruger 3-kontoen. Du bør blive bedt om at konfigurere MFA. Dette viser, at MFAUsers-politikken anvendes.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og -funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Udrul identitet](deploy-identity-solution-overview.md)

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)