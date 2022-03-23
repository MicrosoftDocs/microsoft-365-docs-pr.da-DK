---
title: Dataklassificering for Microsoft 365 for virksomhedstestmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-security-compliance
ms.custom:
- Ent_TLGs
- admindeeplinkMAC
- admindeeplinkDEFENDER
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Brug denne Test Lab-vejledning til at oprette og bruge opbevaringsetiketter på dokumenter i dit Microsoft 365 for Enterprise Test Environment.
ms.openlocfilehash: 3cb3a07b4f636fcf8770432a825356269ff6d94c
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63587670"
---
# <a name="data-classification-for-your-microsoft-365-for-enterprise-test-environment"></a>Dataklassificering for Microsoft 365 for virksomhedstestmiljø

*Denne Test Lab-vejledning kan bruges til både Microsoft 365 til virksomheds- Office 365 Enterprise testmiljøer.*

I denne artikel beskrives det, hvordan du konfigurerer dataklassificering ved hjælp af opbevaringsnavne Microsoft 365 din virksomheds testmiljø.

Klassificering af data i dit testmiljø omfatter tre faser:
- [Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Opret opbevaringsnavne](#phase-2-create-retention-labels)
- [Fase 3: Anvend opbevaringsnavne på dokumenter](#phase-3-apply-retention-labels-to-documents)

![Test Lab-vejledninger til Microsoft-skyen.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Du kan få et visuelt kort over alle artikler i Microsoft 365 for enterprise Test Lab Guide stack ved at gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Opbyg din Microsoft 365 for Enterprise Test Environment

Hvis du blot ønsker at konfigurere opbevaringsmærkater på en let måde med minimumskravene, skal du følge vejledningen i [Let basiskonfiguration](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil konfigurere opbevaringsnavne i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af opbevaringsetiketter kræver ikke det simulerede virksomhedstestmiljø, som omfatter en simuleret intranetforbindelse til internettet og katalogsynkronisering for en Active Directory-domæneservices (AD DS) skov. Den findes her som en mulighed, så du kan teste automatiserede licenser og gruppemedlemskaber og eksperimentere med den i et miljø, der repræsenterer en typisk organisation.

## <a name="phase-2-create-retention-labels"></a>Fase 2: Opret opbevaringsnavne

I denne fase skal du oprette opbevaringsetiketter til de forskellige opbevaringsniveauer for SharePoint Onlinedokumenter:

1. Log på Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">med</a> din globale administratorkonto.
1. Fra fanen **Hjem – Microsoft 365 i** browseren skal du vælge **ClassificationRetention-etiketter** > .
1. Vælg **Opret en etiket**.
1. I **ruden Navngive dit** navn skal du **skrive Intern offentlig** **under Navngive din** etiket og derefter vælge **Næste**.
1. I **ruden med beskrivelse af filplan** skal du vælge **Næste**.
1. Angiv Opbevaring **til Til** i ruden Navneindstillinger, hvis det **er** **nødvendigt,** og vælg derefter **Næste**.
1. Vælg **Opret etiketten i** ruden **Gennemse dine indstillinger**.
1. Gentag trin 3-7 for yderligere navne med disse navne:
  - Privat
  - Følsom
  - Meget fortrolig
1. Vælg **Publicer navne i** ruden **Opbevaringsnavne**.
1. I **ruden Vælg navne for at publicere** skal du vælge **Vælg navne for at publicere**.
1. I **ruden Vælg navne** skal du **vælge Tilføj** og vælge alle fire navne.
1. Vælg **Tilføj**, og vælg derefter **Udført**.
1. I **ruden Vælg navne for at publicere** skal du vælge **Næste**.
1. I **ruden Vælg placeringer** skal du vælge **Næste**.
1. I **ruden Navngive din** politik skal du **skrive Eksempelorganisation** **i Navn** og derefter vælge **Næste**.
1. Vælg **Publicer navne i** ruden Gennemse **dine indstillinger**.
 
Det kan tage et par minutter, før opbevaringsetiketterne er publiceret.

## <a name="phase-3-apply-retention-labels-to-documents"></a>Fase 3: Anvend opbevaringsnavne på dokumenter

I denne fase opdager du standardopbevaringsetiketten for filer i mappen Dokumenter på et SharePoint Online-websted og ændrer manuelt opbevaringsmærkaten for et dokument.

Først skal du oprette et følsomt niveau SharePoint Online-teamwebsted:
  
1. Ved hjælp af en privat forekomst af din browser skal du logge på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration via</a> din globale administratorkonto.
1. På listen over felter skal du vælge **SharePoint**.
1. På den nye **SharePoint** i browseren skal du vælge **Opret websted**.
1. På siden **Opret et websted** skal du vælge **Teamwebsted**.
1. Skriv **SensitiveFiles i feltet Navn på teamwebsted**.
1. I feltet **Beskrivelse af teamwebsted** skal du **SharePoint websted til følsomme filer**.
1. I **Indstillinger for beskyttelse** af personlige **oplysninger skal du vælge Privat – kun medlemmer kan få adgang til dette** websted, og vælg derefter **Næste**.
1. På siden **Who du vil tilføje? skal du** vælge **Udfør**.
    
Dernæst skal du konfigurere mappen Dokumenter på teamwebstedet SensitiveFiles for opbevaringsnavnet Følsom.
  
1. I fanen **SensitiveFiles** i din browser skal du vælge **Dokumenter**.
1. Vælg ikonet **Indstillinger**, og vælg derefter **Indstillinger for bibliotek**.
1. Under **Tilladelser og administration skal du** vælge **Anvend etiket på elementer på denne liste eller dette bibliotek**. Hvis denne indstilling ikke vises, er dine opbevaringsnavne endnu ikke publiceret. Prøv dette trin på et senere tidspunkt.
1. I **Indstillinger Anvend etiket** skal **du vælge** Følsom på rullelisten og derefter vælge **Gem**.

Derefter skal du oprette et nyt dokument på sensitiveFiles-webstedet og ændre dets opbevaringsnavn.
    
1. Vælg **NewWord-dokument i dokumentmappen** > .
1. Skriv noget tekst i det tomme dokument. Vent på, at teksten gemmes.
1. Vælg Delte dokumenter på **menulinjen**.
1. Vælg den **lodretteDocument.docx** ud for filnavnet, og vælg derefter **Detaljer**.
1. I højre rude i sektionen **Egenskaber under Anvend** opbevaringsmærkat skal du bemærke, at dokumentet har fået automatisk anvendt  **følsom opbevaringsmærkat**.
1. Klik **på Rediger alle**.
1. I **rudenDocument.docx** under Anvend **en opbevaringsetiket** skal du vælge **etiketten Meget** fortrolig og derefter vælge **Gem**.

## <a name="next-step"></a>Næste trin

Udforsk yderligere [funktioner til](m365-enterprise-test-lab-guides.md#information-protection) beskyttelse af oplysninger samt funktioner i dit testmiljø.

## <a name="see-also"></a>Se også

[Microsoft 365 til Enterprise Test Lab-vejledninger](m365-enterprise-test-lab-guides.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Microsoft 365 til virksomhedsdokumentation](/microsoft-365-enterprise/)
