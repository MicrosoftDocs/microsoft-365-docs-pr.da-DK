---
title: Microsoft 365 Nul tillid implementeringsplan
f1.keywords:
- deploy zero trust
- zero trust strategy
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
description: Lær, hvordan du Microsoft 365 Nul tillid sikkerhed i dit miljø for at beskytte dig mod trusler og beskytte følsomme data.
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- m365solution-zerotrust
- m365solution-overview
- M365-security-compliance
ms.openlocfilehash: f8ffdcb817763589dfb43f7389bc44b7a28459f2
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473051"
---
# <a name="microsoft-365-zero-trust-deployment-plan"></a>Microsoft 365 Nul tillid implementeringsplan

Denne artikel indeholder en installationsplan til at **opbygge Nul tillid** med Microsoft 365. Nul tillid er en ny sikkerhedsmodel, der antager brud og bekræfter hver anmodning, som om den stammer fra et netværk, der er til at netværke. Uanset hvor anmodningen stammer fra, eller hvilken ressource den har adgang til, lærer Nul tillid-modellen os at "hav aldrig tillid til, bekræft altid".


## <a name="zero-trust-security-architecture"></a>Nul tillid sikkerhedsarkitektur

En Nul tillid tilgang strækker sig over hele den digitale ejendom og fungerer som en integreret sikkerhedsekspert og en ende-til-ende-strategi. 

Denne illustration indeholder en repræsentation af de primære elementer, der bidrager Nul tillid.

:::image type="content" source="../media/zero-trust/zero-trust-architecture.png" alt-text="Den Nul tillid sikkerhedsarkitektur" lightbox="../media/zero-trust/zero-trust-architecture.png":::

I illustrationen:
- Håndhævelse af sikkerhedspolitik er centrum for en Nul tillid arkitektur. Dette omfatter multifaktorgodkendelse med betinget adgang, der tager højde for brugerkontorisici, enhedsstatus samt andre kriterier og politikker, du angiver.
- Identiteter, enheder, data, apps, netværk og andre infrastrukturkomponenter er alle konfigureret med den rette sikkerhed. Politikker, der er konfigureret for hver af disse komponenter, koordineres med din overordnede Nul tillid strategi. Eksempelvis bestemmer enhedspolitikker kriterierne for sunde enheder, og politikker for betinget adgang kræver sunde enheder for at få adgang til bestemte apps og data.
- Trusselsbeskyttelse og intelligens overvåger miljøet, viser aktuelle risici og tager automatiseret handling for at afhjælpe angreb.

<!---
For more information about this architecture, including deployment objectives for your entire digital estate, see [Zero Trust Rapid Modernization Plan (RaMP)](https://review.docs.microsoft.com/security/zero-trust/zero-trust-ramp-overview?branch=zt-content-prototype). 
-->

Du kan finde flere Nul tillid i Microsofts [_**Nul tillid Guidance Center**_](/security/zero-trust).

## <a name="deploying-zero-trust-for-microsoft-365"></a>Installation af Nul tillid til Microsoft 365

Microsoft 365 er opbygget bevidst med mange funktioner til sikkerhed og informationsbeskyttelse for at hjælpe dig med Nul tillid i dit miljø. Mange af funktionerne kan udvides for at beskytte adgangen til andre SaaS-apps, som din organisation bruger, og dataene i disse apps.

Denne illustration viser arbejdet med at implementere Nul tillid funktioner. Dette arbejde er opdelt i arbejdsenheder, der kan konfigureres sammen, startende fra bunden og arbejde til toppen for at sikre, at det nødvendige arbejde er udført.


:::image type="content" source="../media/zero-trust/m365-zero-trust-deployment-stack.png" alt-text="Den Microsoft 365 Nul tillid installationsstabling" lightbox="../media/zero-trust/m365-zero-trust-deployment-stack.png":::

I denne illustration:
- Nul tillid begynder med et fundament af identitet og enhedsbeskyttelse. 
- Funktionaliteterne til trusselsbeskyttelse er bygget oven på dette grundlag for at levere overvågning i realtid og afhjælpning af sikkerhedstrusler. 
- Beskyttelse og styring af oplysninger giver avancerede kontroller, der er målrettet bestemte typer data for at beskytte dine mest værdifulde oplysninger og for at hjælpe dig med at overholde overholdelsesstandarder, herunder beskyttelse af personlige oplysninger.

## <a name="step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies"></a>Trin 1. Konfigurere Nul tillid og beskyttelse af enhedsadgang – udgangspunktspolitikker

Det første trin er at opbygge dit Nul tillid fundament ved at konfigurere identitets- og enhedsadgangsbeskyttelse. 


:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-1b.png" alt-text="Processen til konfiguration af Nul tillid og beskyttelse af enhedsadgang" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-1b.png":::



Gå til [**_Nul tillid og beskyttelse af enhedsadgang_**](office-365-security/microsoft-365-policies-configurations.md) for at få foruddefineret vejledning til at gøre dette. I denne serie af artikler beskrives et sæt konfigurationer, der er nødvendige for identitet og enhedsadgang, og et sæt betinget adgang (Azure AD) til Azure Active Directory (Azure AD), Microsoft Intune og andre politikker for at sikre adgang til Microsoft 365  til virksomhedsskyapps og -tjenester, andre SaaS-tjenester og programmer i det lokale miljø, der er udgivet med Azure AD Programproxy.



|Omfatter  |Forudsætninger  |Omfatter ikke  |
|---------|---------|---------|
|Anbefalede identitets- og enhedsadgangspolitikker for tre beskyttelsesniveauer:<br>- Udgangspunkt<br>- Enterprise (anbefales)<br>- Specialiseret<br><br>Yderligere anbefalinger til:<br>- Eksterne brugere (gæster)<br>- Microsoft Teams<br>- SharePoint Online<br>- Microsoft Defender for Cloud Apps| Microsoft E3 eller E5<br><br>Azure Active Directory i en af disse tilstande:<br>- Kun i skyen<br>- Hybrid med godkendelse af synkronisering af adgangskodehash<br>- Hybrid med pass-through-godkendelse (PTA)<br>- Medlem af organisationsnetværk     |Enhedsregistrering for politikker, der kræver administrerede enheder. Se "Administrer slutpunkter med Intune" for at tilmelde enheder |
| | | |

Start med at implementere startniveauet. Disse politikker kræver ikke registrering af enheder i administration. 


:::image type="content" source="../media/zero-trust/identity-access-starting-point-tier.png" alt-text="Siden Nul tillid politikker for identitet og enhedsadgang – udgangspunktet" lightbox="../media/zero-trust/identity-access-starting-point-tier.png":::


## <a name="step-2-manage-endpoints-with-intune"></a>Trin 2. Administrer slutpunkter med Intune

Dernæst skal du tilmelde dine enheder til administration og begynde at beskytte disse med mere avancerede kontrolelementer. 

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-2.png" alt-text="Administrer slutpunkter med Intune element" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-2.png":::


Gå til [**_Administrer enheder med Intune_**](../solutions/manage-devices-with-intune-overview.md) for at få foruddefineret vejledning til at gøre dette. 


|Omfatter  |Forudsætninger  |Omfatter ikke  |
|---------|---------|---------|
|Tilmeld enheder med Intune<br>- Virksomhedsejede enheder<br>- Autopilot/automated<br>- registrering<br><br>Konfigurere politikker<br>- Politikker for appbeskyttelse<br>- Overholdelsespolitikker<br>- Politikker for enhedsprofil | Registrer slutpunkter med Azure AD     | Konfiguration af funktioner til beskyttelse af oplysninger, herunder:<br>- Typer af følsomme oplysninger<br>- Etiketter<br>- DLP-politikker<br>For disse funktioner skal du se Trin 5. Beskytte og styre data (senere i denne artikel).       |
|    |         |         |

## <a name="step-3-add-zero-trust-identity-and-device-access-protection--enterprise-policies"></a>Trin 3. Tilføj Nul tillid identitet og beskyttelse af enhedsadgang – virksomhedspolitikker

Med enheder, der er tilmeldt administration, kan du nu implementere det komplette sæt anbefalede politikker Nul tillid identitet og enhedsadgang, hvilket kræver kompatible enheder.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png" alt-text="Politikker Nul tillid identitet og adgang med enhedshåndtering" lightbox="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png":::

Gå tilbage [**_til Fælles identitets- og enhedsadgangspolitikker_**](office-365-security/identity-access-policies.md) , og tilføj politikkerne på Enterprise-niveau.  

:::image type="content" source="../media/zero-trust/identity-access-enterprise-tier.png" alt-text="Siden Nul tillid identitets- og adgangspolitikker – Enterprise-niveau (anbefales)" lightbox="../media/zero-trust/identity-access-enterprise-tier.png":::

## <a name="step-4-evaluate-pilot-and-deploy-microsoft-365-defender"></a>Trin 4. Evaluer, pilotér og installer Microsoft 365 Defender

Microsoft 365 Defender er en udvidet registrerings- og svarløsning (XDR), der automatisk indsamler, korrelerer og analyserer signal-, trussels- og advarselsdata fra hele dit Microsoft 365-miljø, herunder slutpunkt, mail, programmer og identiteter.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-defender.png" alt-text="Processen med at føje Microsoft 365 Defender til Nul tillid arkitektur" lightbox="../media/zero-trust/m365-zero-trust-architecture-defender.png":::

Gå til [**_Evaluer og Microsoft 365 Defender_**](defender/eval-overview.md) for at få en metodisk vejledning til pilotprojekter og installation Microsoft 365 Defender komponenter. 

|Omfatter  |Forudsætninger  |Omfatter ikke  |
|---------|---------|---------|
| Konfigurer evaluerings- og pilotmiljøet for alle komponenter:<br>- Defender for Identity<br>- Defender for Office 365<br>- Defender til Slutpunkt<br>- Microsoft Defender for Cloud Apps<br><br>Beskyt dig mod trusler<br><br> Undersøg og svar på trusler   | Se vejledningen for at læse om arkitekturkravene for hver komponent Microsoft 365 Defender.        | Azure AD Identity Protection er ikke inkluderet i denne løsningsvejledning. Den er inkluderet i Trin 1: Konfigurer Nul tillid og beskyttelse af enhedsadgang.        |
|    |         |         |

## <a name="step-5-protect-and-govern-sensitive-data"></a>Trin 5. Beskytte og styre følsomme data

Implementer Microsoft Information Protection (MIP) for at hjælpe dig med at opdage, klassificere og beskytte følsomme oplysninger, uanset hvor de befinder sig eller rejser.

MIP-funktioner er inkluderet Microsoft 365 overholdelse af regler og standarder og giver dig værktøjerne til at kende dine data, beskytte dine data og forhindre tab af data.


:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-info-protect.png" alt-text="De funktioner til beskyttelse af oplysninger, der beskytter data gennem håndhævelse af politikker" lightbox="../media/zero-trust/m365-zero-trust-architecture-info-protect.png":::

Mens dette arbejde er repræsenteret øverst i installationsstakken illustreret tidligere i denne artikel, kan du starte dette arbejde når som helst. 

Microsoft Information Protection udgør en ramme, proces og egenskaber, som du kan bruge til at opfylde dine specifikke forretningsmål.

:::image type="content" source="../media/zero-trust/mip-solution-overview.png" alt-text="Rammen Microsoft Information Protection (MIP)" lightbox="../media/zero-trust/mip-solution-overview.png":::


Du kan finde flere oplysninger om, hvordan du planlægger og installerer informationsbeskyttelse under [**_Installér Microsoft Information Protection løsning_**](../compliance/information-protection-solution.md). 

Hvis du implementerer informationsbeskyttelse til bestemmelser om beskyttelse af datas personlige oplysninger, giver denne løsningsvejledning en anbefalet ramme for hele processen: Implementere beskyttelse af oplysninger for regler om beskyttelse af data med [**_Microsoft 365_**](../solutions/information-protection-deploy.md).