---
title: Øget Microsoft 365 sikkerhed for dine Microsoft 365 til virksomhedstestmiljøer
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
ms.collection: M365-security-compliance
ms.custom:
- Ent_TLGs
- admindeeplinkMAC
- admindeeplinkDEFENDER
- admindeeplinkSPO
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Brug denne testlaboratorievejledning til at aktivere yderligere Microsoft 365 sikkerhedsindstillinger for dit Microsoft 365 til virksomhedstestmiljø.
ms.openlocfilehash: 4c69fadd3fb3e6744fad850e76282ea2339f48ee
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100715"
---
# <a name="increased-microsoft-365-security-for-your-microsoft-365-for-enterprise-test-environment"></a>Øget Microsoft 365 sikkerhed for dine Microsoft 365 til virksomhedstestmiljøer

*Denne testlaboratorievejledning kan kun bruges til Microsoft 365 til virksomhedstestmiljøer.*

Med vejledningen i denne artikel kan du konfigurere yderligere indstillinger for Microsoft 365 for at øge sikkerheden i dit Microsoft 365 til virksomhedstestmiljø.

![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Klik [her](../downloads/Microsoft365EnterpriseTLGStack.pdf) for at få et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø

Hvis du blot vil konfigurere øget Microsoft 365 sikkerhed på en let måde med minimumskravene, skal du følge vejledningen i [Konfiguration af letvægtsbase](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil konfigurere øget Microsoft 365 sikkerhed i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af øget Microsoft 365 sikkerhed kræver ikke det simulerede virksomhedstestmiljø, som omfatter et simuleret intranet, der er forbundet med internet- og katalogsynkronisering for et AD DS-område (Active Directory-domæneservices). Det leveres her som en mulighed, så du kan teste automatiserede licenser og gruppemedlemskab og eksperimentere med det i et miljø, der repræsenterer en typisk organisation. 

## <a name="phase-2-configure-increased-microsoft-365-security"></a>Fase 2: Konfigurer øget Microsoft 365 sikkerhed

I denne fase aktiverer du øget Microsoft 365 sikkerhed for dine Microsoft 365 til virksomhedstestmiljøer. Du kan finde flere oplysninger og indstillinger under [Konfigurer din lejer for at få øget sikkerhed](/office365/securitycompliance/tenant-wide-setup-for-increased-security).

### <a name="configure-sharepoint-online-to-block-apps-that-dont-support-modern-authentication"></a>Konfigurer SharePoint Online for at blokere apps, der ikke understøtter moderne godkendelse

Apps, der ikke understøtter moderne godkendelse, kan ikke have [konfigurationer af identitets- og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md) anvendt på dem, hvilket er et vigtigt element i sikringen af dit Microsoft 365 abonnement og dets digitale aktiver. 

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a>, og log på dit Microsoft 365 testlaboratorium-abonnement med din globale administratorkonto.
    
  - Hvis du bruger det lette Microsoft 365 testmiljø, skal du logge på fra din lokale computer.
    
  - Hvis du bruger det simulerede Microsoft 365 testmiljø, skal du bruge [Azure Portal](https://portal.azure.com) til at oprette forbindelse til den virtuelle klient1-maskine og derefter logge på fra CLIENT1.
 
2. Klik på **SharePoint** under **Administrationscentre** i venstre navigationsrude under den nye fane **Microsoft 365 Administration**.
3. På den nye **SharePoint fanen Administration** skal du vælge <a href="https://go.microsoft.com/fwlink/?linkid=2185071" target="_blank">**PolitikkerKontrolelementetAccess**</a> > .
4. Vælg **Apps, der ikke understøtter moderne godkendelse**, vælg **Bloker adgang**, og vælg derefter **Gem**.


### <a name="enable-defender-for-office-365-for-sharepoint-onedrive-for-business-and-microsoft-teams"></a>Aktivér Defender for Office 365 for SharePoint, OneDrive for Business og Microsoft Teams

Defender for Office 365 til SharePoint, OneDrive og Microsoft Teams beskytter din organisation mod utilsigtet deling af skadelige filer.

1. Gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Security & Compliance Center</a> , og log på med din globale administratorkonto.

2. Klik på **Politik** under **Trusselsadministration** i navigationsruden til venstre, og klik derefter på **Pengeskab Vedhæftede filer**. 

3. Under **Beskyt filer i SharePoint, OneDrive og Microsoft Teams**. Vælg **Slå ATP til for SharePoint, OneDrive og Microsoft Teams**.

4. Klik på **Gem**.


### <a name="enable-anti-malware"></a>Aktivér antimalware

Malware består af virus og spyware. Virus inficerer andre programmer og data, og de spredes over hele computeren på udkig efter programmer til at inficere. Spyware refererer til malware, der indsamler dine personlige oplysninger, f.eks. logonoplysninger og personlige data, og sender dem tilbage til malwareforfatteren. 

Microsoft 365 har indbyggede funktioner til filtrering af malware og spam, der hjælper med at beskytte indgående og udgående meddelelser mod skadelig software og beskytte dig mod spam. Du kan få flere oplysninger under [Beskyttelse mod spam & beskyttelse mod skadelig software](../security/office-365-security/anti-spam-and-anti-malware-protection.md).

Sådan sikrer du, at der udføres antimalwarebehandling på filer med almindelige filtyper til vedhæftede filer:

1. Klik på knappen Tilbage i browseren for at vende tilbage til siden **Politik** .
2. Klik på **Antimalware**.
3. Dobbeltklik på politikken **med navnet Standard**.
4. Klik på **Indstillinger** i vinduet **Politik for antimalware**.
4. Under **Filter for almindelige vedhæftede filer** skal du vælge **Til** og derefter klikke på **Gem**.


## <a name="phase-3-examine-the-security-dashboard"></a>Fase 3: Undersøg sikkerhedsdashboardet

Trusselsstyring i Microsoft 365 kan hjælpe dig med at styre og administrere adgang til din organisations data på mobilenheder, beskytte din organisation mod datatab og beskytte indgående og udgående meddelelser mod skadelig software og spam. Du kan også bruge trusselsstyring til at beskytte dit domænes omdømme og til at afgøre, om afsendere er ondsindede spoofing-konti fra dit domæne eller ej. 

Sådan får du vist sikkerhedsdashboardet:

1. Hvis det er nødvendigt, skal du gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Security & Compliance Center</a> og logge på med din globale administratorkonto.

2. Klik på **Dashboard** under **Trusselsadministration** i navigationsruden til venstre.

Se nærmere på alle kortene på dashboardet for at blive fortrolig med de angivne oplysninger.

Du kan få flere oplysninger under [Sikkerhedsdashboard](../security/office-365-security/security-dashboard.md).


## <a name="phase-4-examine-microsoft-secure-score"></a>Fase 4: Undersøg Microsoft Secure Score

Microsoft Secure Score viser din sikkerhedsholdning som et tal, hvilket angiver dit aktuelle niveau i forhold til de funktioner, der er tilgængelige i dit abonnement. Det giver dig også en liste over forbedringshandlinger, du kan udføre for at forbedre din score.

1. Opret en ny fane i browseren, gå til <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a>, og klik derefter på **Sikker score**.
2. Bemærk din aktuelle Secure Score under fanen **Oversigt**  , og hvordan den sammenlignes med det globale gennemsnit og abonnementer med et tilsvarende antal licenser.
3. På fanen **Forbedringshandlinger** skal du læse listen over handlinger, du kan udføre for at øge din score.

Du kan få flere oplysninger under [Microsoft Secure Score](../security/defender/microsoft-secure-score.md).

## <a name="next-steps"></a>Næste trin

Udforsk yderligere funktioner og funktioner til [beskyttelse af oplysninger](m365-enterprise-test-lab-guides.md#information-protection) i dit testmiljø.

## <a name="see-also"></a>Se også

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)
