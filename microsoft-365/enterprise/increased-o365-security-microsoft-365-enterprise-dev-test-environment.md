---
title: Øget Microsoft 365 sikkerhed for din Microsoft 365 for Enterprise Test Environment
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.custom:
- Ent_TLGs
- admindeeplinkMAC
- admindeeplinkDEFENDER
- admindeeplinkSPO
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Brug denne Test Lab-vejledning til at aktivere Microsoft 365 sikkerhedsindstillinger Microsoft 365 for enterprise test environment.
ms.openlocfilehash: bf64bb23192eb4a4d2b3700a2b0c4390efc1f53e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587251"
---
# <a name="increased-microsoft-365-security-for-your-microsoft-365-for-enterprise-test-environment"></a>Øget Microsoft 365 sikkerhed for din Microsoft 365 for Enterprise Test Environment

*Denne Test Lab-vejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

Med instruktionerne i denne artikel kan du konfigurere flere Microsoft 365 for at øge sikkerheden i dit Microsoft 365 for Enterprise Test Environment.

![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Klik [her](../downloads/Microsoft365EnterpriseTLGStack.pdf) for at få et visuelt kort over alle artikler i Microsoft 365 for Enterprise Test Lab Guide-stak.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment

Hvis du blot ønsker at konfigurere øget Microsoft 365 let måde med minimumskravene, skal du følge vejledningen i [Let basiskonfiguration](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil konfigurere øget Microsoft 365 i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Testning af Microsoft 365 sikkerhed kræver ikke det simulerede virksomhedstestmiljø, som omfatter en simuleret intranetforbindelse til internettet og katalogsynkronisering for en Active Directory-domæneservices (AD DS)-skov. Den findes her som en mulighed, så du kan teste automatiseret licensering og gruppemedlemskab og eksperimentere med den i et miljø, der repræsenterer en typisk organisation. 

## <a name="phase-2-configure-increased-microsoft-365-security"></a>Fase 2: Konfigurer øget Microsoft 365 sikkerhed

I denne fase aktiverer du øget Microsoft 365 sikkerhed for din Microsoft 365 for Enterprise Test Environment. Du kan finde flere oplysninger og indstillinger under [Konfigurer din lejer for at øge sikkerheden](/office365/securitycompliance/tenant-wide-setup-for-increased-security).

### <a name="configure-sharepoint-online-to-block-apps-that-dont-support-modern-authentication"></a>Konfigurer SharePoint Online til at blokere apps, der ikke understøtter moderne godkendelse

Apps, der ikke understøtter moderne godkendelse, kan ikke have identitets- og enhedsadgangskonfigurationer anvendt på dem, hvilket er et vigtigt element til sikring af dit Microsoft 365-abonnement og [dets](../security/office-365-security/microsoft-365-policies-configurations.md) digitale aktiver. 

1. Gå til Microsoft 365 Administration<a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">,</a> og log på dit Microsoft 365 test lab-abonnement med din globale administratorkonto.
    
  - Hvis du bruger det lette Microsoft 365, skal du logge på fra din lokale computer.
    
  - Hvis du bruger den simulerede Microsoft 365 testmiljø, skal du bruge [Azure-portalen](https://portal.azure.com) til at oprette forbindelse til den virtuelle KLIENT1-maskine og derefter logge på fra CLIENT1.
 
2. På den nye **Microsoft 365 Administration** under Administration **i venstre** navigationsrude skal du klikke på **SharePoint**.
3. På den nye **SharePoint Administration skal** du vælge **kontrolelementet** <a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank">**PoliciesAccess**</a> > .
4. Vælg **Apps, der ikke understøtter moderne godkendelse**, vælg **Bloker adgang**, og vælg derefter **Gem**.


### <a name="enable-defender-for-office-365-for-sharepoint-onedrive-for-business-and-microsoft-teams"></a>Aktivér Defender Office 365 for SharePoint, OneDrive for Business og Microsoft Teams

Defender til Office 365 til SharePoint, OneDrive og Microsoft Teams beskytter din organisation mod utilsigtet deling af skadelige filer.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Security & Compliance Center,</a> og log på med din globale administratorkonto.

2. Klik på Politik under Trusselsstyring **i venstre** **navigationsrude**, og klik derefter på Pengeskab **vedhæftede filer**. 

3. Under **Beskyt filer i SharePoint skal du OneDrive og Microsoft Teams**. skal **du vælge Slå ATP til for SharePoint, OneDrive og Microsoft Teams**.

4. Klik på **Gem**.


### <a name="enable-anti-malware"></a>Aktivér antimalware

Malware består af virus og spyware. Virus inficerer andre programmer og data, og de kan spredes til hele din computer og søge efter programmer, der kan inficeres. Spyware er malware, som indsamler dine personlige oplysninger, f.eks. logonoplysninger og personlige data, og sender det tilbage til malwareforfatteren. 

Microsoft 365 indeholder indbyggede malware- og spamfiltreringsfunktioner, som hjælper med at beskytte indgående og udgående meddelelser mod skadelig software og hjælper med at beskytte dig mod spam. Du kan finde flere [oplysninger under Beskyttelse mod & mod malware](../security/office-365-security/anti-spam-and-anti-malware-protection.md).

Sådan sikrer du, at der udføres antimalwarebehandling på filer med almindelige vedhæftede filtyper:

1. Klik på knappen Tilbage i browseren for at vende tilbage til **siden** Politik.
2. Klik **på Antimalware**.
3. Dobbeltklik på **politikken Standard.**
4. I vinduet **for antimalwarepolitik** skal du klikke **Indstillinger**.
4. Under **filteret Almindelige typer af** vedhæftede filer **skal du** vælge Til og derefter klikke på **Gem**.


## <a name="phase-3-examine-the-security-dashboard"></a>Fase 3: Undersøg sikkerhedsdashboardet

Trusselsstyring i Microsoft 365 kan hjælpe dig med at styre og administrere adgangen til din organisations data på mobilenheder, beskytte din organisation mod datatab og beskytte indgående og udgående meddelelser mod skadelig software og spam. Du kan også bruge trusselsstyring til at beskytte dit domænes ry og afgøre, om afsendere er skadelige for spoofing-konti fra dit domæne. 

Sådan får du vist sikkerhedsdashboardet:

1. Hvis det er nødvendigt, kan <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">du gå til Security & Compliance Center</a> og logge på med din globale administratorkonto.

2. Klik på Dashboard under **Trusselsstyring i venstre** **navigationsrude**.

Se nærmere på alle kortene på dashboardet for at gøre dig bekendt med de angivne oplysninger.

Du kan få mere at vide under [Sikkerhedsdashboard](../security/office-365-security/security-dashboard.md).


## <a name="phase-4-examine-microsoft-secure-score"></a>Fase 4: Undersøg Microsoft Secure Score

Microsoft Secure Score viser din sikkerhed som et tal, der angiver dit aktuelle niveau i forhold til de funktioner, der er tilgængelige i dit abonnement. Det giver dig også en liste over de forbedringshandlinger, du kan udføre for at forbedre din score.

1. Opret en ny fane i browseren, gå til Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">, og</a> klik derefter på **Secure score**.
2. På fanen **Oversigt**  skal du notere dit aktuelle Secure Score, og hvordan det ser ud i forhold til det globale gennemsnit og abonnementer med et lignende antal licenser.
3. På fanen **Forbedringshandlinger** skal du læse listen over de handlinger, du kan udføre for at øge din score.

Du kan finde flere oplysninger [i Microsoft Secure Score](../security/defender/microsoft-secure-score.md).

## <a name="next-steps"></a>Næste trin

Udforsk yderligere [funktioner til](m365-enterprise-test-lab-guides.md#information-protection) beskyttelse af oplysninger samt funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)
