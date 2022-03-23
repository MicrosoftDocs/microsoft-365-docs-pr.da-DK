---
title: Microsoft 365 til virksomhedstestmiljø multifaktorgodkendelse
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
- seo-marvel-apr2020
- admindeeplinkMAC
description: Konfigurer multifaktorgodkendelse ved hjælp af sms-beskeder, der sendes til en smartphone, Microsoft 365 til virksomhedens testmiljø.
ms.openlocfilehash: d3207db4d8537e78ecc83ae18f8539f0e4f56106
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63587245"
---
# <a name="multi-factor-authentication-for-your-microsoft-365-for-enterprise-test-environment"></a>Multifaktorgodkendelse for din Microsoft 365 for Enterprise Test-miljø

*Denne Test Lab-vejledning kan bruges til både Microsoft 365 til virksomheds- Office 365 Enterprise testmiljøer.*

Hvis du vil have et ekstra sikkerhedsniveau til at logge på Microsoft 365 eller en tjeneste eller et program, der bruger Azure AD-lejeren for dit abonnement, kan du aktivere Azure AD-multifaktorgodkendelse, hvilket kræver mere end blot et brugernavn og en adgangskode for at bekræfte en konto.

Med multifaktorgodkendelse skal brugerne godkende et telefonopkald, indtaste en bekræftelseskode, der er sendt i en sms, eller bekræfte godkendelsen med en app på deres smartphones, når de har indtastet deres adgangskoder korrekt. De kan først logge på, efter denne anden godkendelsesfaktor er tilfreds.
  
I denne artikel beskrives det, hvordan du aktiverer og tester meddelelsesbaseret godkendelse for en bestemt brugerkonto.
  
Konfiguration af multifaktorgodkendelse for en konto i dit Microsoft 365 for virksomhedstestmiljø omfatter to faser og en tredje valgfri fase:
- [Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Aktivér og test multifaktorgodkendelse for bruger 2-kontoen](#phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account)
- [Fase 3: Aktivér og test multifaktorgodkendelse med en politik for betinget adgang](#phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy)

![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment

Hvis du blot ønsker at teste multifaktorgodkendelse på en let måde med minimumskravene, skal du følge vejledningen i [Let basiskonfiguration](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil teste multifaktorgodkendelse i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af multifaktorgodkendelse kræver ikke det simulerede virksomhedstestmiljø, som omfatter en simuleret intranetforbindelse til internettet og katalogsynkronisering for en Active Directory-domæneservices (AD DS) skov. Den findes her som en mulighed, så du kan teste multifaktorgodkendelse og eksperimentere med den i et miljø, der repræsenterer en typisk organisation.
  
## <a name="phase-2-enable-and-test-multi-factor-authentication-for-the-user-2-account"></a>Fase 2: Aktivér og test multifaktorgodkendelse for bruger 2-kontoen

Aktivér multifaktorgodkendelse for Bruger 2-kontoen ved at følge disse trin:
  
1. Åbn en separat, privat forekomst af din browser, gå til Microsoft 365 Administration ([https://portal.microsoft.com](https://portal.microsoft.com)), og log derefter på med din globale administratorkonto.
    
2. I venstre navigationsrude skal du **vælge** <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**BrugereAktivér**</a> >  brugere.
    
3. I ruden Aktive brugere skal du **vælge Multi-Factor Authentication**.
    
4. Vælg Bruger **2-kontoen på** listen.
    
5. I sektionen **Bruger 2** under Hurtige **trin skal du** vælge **Aktivér**.
    
6. I dialogboksen **Om aktivering af multifaktorgodkendelse** skal du vælge **Aktivér multifaktorgodkendelse**.
    
7. I dialogboksen **Opdateringer fuldførte** skal du vælge **Luk**.
    
8. På fanen **Microsoft 365 Administration** skal du vælge ikonet brugerkonto øverst til højre og derefter vælge **Log af**.
    
9. Luk din browserforekomst.
   
Fuldfør konfigurationen for Bruger 2-kontoen, hvis du vil bruge en sms til validering, og test den med disse trin:
  
1. Åbn en ny, privat forekomst af din browser.
    
2. Gå til siden [Microsoft 365 Administration](https://admin.microsoft.com) og log på med bruger 2-kontonavn og adgangskode.
    
3. Når du har logget på, bliver du bedt om at konfigurere kontoen for at få flere oplysninger. Vælg **Næste**.
    
4. På siden **Yderligere sikkerhedskontrol** :
    
   - Vælg dit land eller område.
    
   - Angiv telefonnummeret på den smartphone, der skal modtage sms-beskeder.
    
   - I **Metode** skal du **vælge Send mig en kode efter SMS-besked**.
    
5. Vælg **Næste**.
    
6. Angiv bekræftelseskoden fra den sms-besked, du har modtaget på din smartphone, og vælg derefter **Bekræft**.
    
7. På siden **Trin 3: Behold dine eksisterende programmer** skal du vælge **Udført**.
    
8. Hvis det er første gang, du er logget på med Bruger 2-kontoen, bliver du bedt om at ændre adgangskoden. Angiv den oprindelige adgangskode og en ny adgangskode to gange, og vælg **derefter Opdater adgangskode, og log på**. Optag den nye adgangskode på et sikkert sted.
    
    Du bør kunne se Office for bruger 2 **på Microsoft Office Startside** i din browser.

## <a name="phase-3-enable-and-test-multi-factor-authentication-with-a-conditional-access-policy"></a>Fase 3: Aktivér og test multifaktorgodkendelse med en politik for betinget adgang

*Denne fase kan kun bruges til en Microsoft 365 til virksomhedstestmiljø.*

I denne fase aktiverer du multifaktorgodkendelse for bruger 3-kontoen ved hjælp af en gruppe og en politik for betinget adgang.

Derefter skal du oprette en ny gruppe med navnet MFAUsers og føje Bruger 3-kontoen til den.

1. På fanen **Microsoft 365 Administration** skal du vælge **Grupper** i venstre navigationsrude og derefter vælge <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupper**</a>.
2. Vælg **Tilføj en gruppe**.
3. I **ruden Vælg en gruppetype** skal du **vælge Sikkerhed** og derefter vælge **Næste**.
4. Vælg **Opret gruppe i ruden Konfigurer** de grundlæggende **funktioner**, og vælg derefter **Luk**.
5. I **ruden Gennemse og afslut tilføjelse af** gruppe skal **du angive MFAUsers** og derefter vælge **Næste**.
6. Vælg gruppen **MFAUsers på listen over** grupper.
7. I **ruden MFAUsers** skal du **vælge Medlemmer** og derefter vælge **Vis alle og administrer medlemmer**.
8. I **ruden MFAUsers** skal du vælge **Tilføj** medlemmer, vælge **Bruger 3-kontoen** og derefter **vælge** **GemLukLuk** >  > .

Dernæst skal du oprette en politik for betinget adgang, der kræver multifaktorgodkendelse for medlemmer af gruppen MFAUsers.

1. Gå til i en ny fane i browseren [https://portal.azure.com](https://portal.azure.com).
2. Vælg **Azure Active Directory** >  **SecurityConditional** >  Access.
3. I **ruden Betinget adgang – Politikker** skal du vælge **Ny politik**.
4. I **ruden** Ny skal du **angive MFA for brugerkonti** i **feltet** Navn.
5. I sektionen **Opgaver skal** du vælge **Brugere og grupper**.
6. På fanen **Medtag** i **ruden Brugere og grupper** skal du **vælge Vælg brugere og grupperBrugere** >  **og grupperVælg** > .
7. Vælg **gruppen** **MFAUsers i** ruden Vælg, og vælg derefter **SelectDone** > .
8. I sektionen **Access-kontrolelementer** i **ruden Ny** skal du vælge **Giv**.
9. I **ruden Giv** skal du **vælge Kræv multifaktorgodkendelse** og derefter vælge **Vælg**.
10. I **ruden Ny** skal du **vælge Til** for **Aktivér politik** og derefter vælge **Opret**.
11. Luk **Azure-portalen,** og **Microsoft 365 Administration fanerne**.

For at teste denne politik skal du logge af og logge på med Bruger 3-kontoen. Du bør blive bedt om at konfigurere MFA. Dette viser, at politikken MFAUsers anvendes.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [identitetsfunktioner](m365-enterprise-test-lab-guides.md#identity) og funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Udrul identitet](deploy-identity-solution-overview.md)

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)