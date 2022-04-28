---
title: Dataklassificering for dit Microsoft 365 til virksomhedstestmiljø
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Brug denne testlaboratorievejledning til at oprette og bruge opbevaringsmærkater på dokumenter i dit Microsoft 365 til virksomhedstestmiljøer.
ms.openlocfilehash: f5bcde88be148ed883b4ad10e3b8116ed21c9fa8
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096804"
---
# <a name="data-classification-for-your-microsoft-365-for-enterprise-test-environment"></a>Dataklassificering for dit Microsoft 365 til virksomhedstestmiljø

*Denne testlaboratorievejledning kan bruges til både Microsoft 365 til virksomheds- og Office 365 Enterprise testmiljøer.*

I denne artikel beskrives det, hvordan du konfigurerer dataklassificering ved hjælp af opbevaringsmærkater i dit Microsoft 365 til virksomhedstestmiljøer.

Klassificering af data i dit testmiljø omfatter tre faser:
- [Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Fase 2: Opret opbevaringsmærkater](#phase-2-create-retention-labels)
- [Fase 3: Anvend opbevaringsmærkater på dokumenter](#phase-3-apply-retention-labels-to-documents)

![Test Lab Guides til Microsoft-cloudmiljøet.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Hvis du vil have et visuelt kort over alle artiklerne i stakken Microsoft 365 til testlaboratorier til virksomheder, skal du gå til [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Fase 1: Udarbejd dit Microsoft 365 til virksomhedstestmiljø

Hvis du kun vil konfigurere opbevaringsmærkater på en let måde med minimumskravene, skal du følge vejledningen i [Konfiguration af letvægtsbase](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Hvis du vil konfigurere opbevaringsmærkater i en simuleret virksomhed, skal du følge vejledningen i [Pass-through-godkendelse](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test af opbevaringsmærkater kræver ikke det simulerede virksomhedstestmiljø, hvilket omfatter et simuleret intranet, der er forbundet med internet- og katalogsynkronisering for et AD DS-område (Active Directory-domæneservices). Det leveres her som en mulighed, så du kan teste automatiserede licenser og gruppemedlemskab og eksperimentere med det i et miljø, der repræsenterer en typisk organisation.

## <a name="phase-2-create-retention-labels"></a>Fase 2: Opret opbevaringsmærkater

I denne fase skal du oprette opbevaringsmærkater for de forskellige opbevaringsniveauer for mapperne SharePoint Online-dokumenter:

1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender-portalen</a> med din globale administratorkonto.
1. På fanen **Hjem – Microsoft 365 sikkerhed** i din browser skal du vælge **KlassificeringPlaceringsmærkater** > .
1. Vælg **Opret en etiket**.
1. I ruden **Navngiv dit navn** skal du angive **Intern offentlig** i **Navngiv dit navn** og derefter vælge **Næste**.
1. Vælg **Næste** i ruden **Filplanbeskrivelser**.
1. Angiv **Opbevaring** til **Til** i ruden **Etiketindstillinger**, hvis det er nødvendigt, og vælg derefter **Næste**.
1. I ruden **Gennemse dine indstillinger** skal du vælge **Opret mærkaten**.
1. Gentag trin 3-7 for yderligere navne med disse navne:
  - Privat
  - Følsomme
  - Meget fortroligt
1. Vælg Publicer navne i ruden **Opbevaringsmærkater**.
1. I ruden **Vælg navne, der skal publiceres** skal du vælge **Vælg navne, der skal publiceres**.
1. I ruden **Vælg navne** skal du vælge **Tilføj** og vælge alle fire navne.
1. Vælg **Tilføj**, og vælg derefter **Udført**.
1. Vælg **Næste** i ruden **Vælg navne, der skal publiceres**.
1. Vælg **Næste** i ruden **Vælg placeringer**.
1. I ruden **Navngiv din politik** skal du angive **Eksempel på organisation** i **Navn** og derefter vælge **Næste**.
1. Vælg **Publicer navne** i ruden **Gennemse dine indstillinger**.
 
Det kan tage et par minutter, før opbevaringsmærkater publiceres.

## <a name="phase-3-apply-retention-labels-to-documents"></a>Fase 3: Anvend opbevaringsmærkater på dokumenter

I denne fase finder du standardfunktionsmåden for opbevaringsmærkater for filer i mappen Dokumenter på et SharePoint Online-websted og ændrer et dokuments opbevaringsmærkat manuelt.

Først skal du oprette et SharePoint onlineteamwebsted på et følsomt niveau:
  
1. Log på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> ved hjælp af en privat forekomst af din browser ved hjælp af din globale administratorkonto.
1. Vælg **SharePoint** på listen over felter.
1. Vælg **Opret websted** på den nye **fane SharePoint** i browseren.
1. Vælg **Teamwebsted** på siden **Opret et websted**.
1. I feltet **Navn på teamwebsted** skal du angive **Følsommefiler**.
1. Angiv **SharePoint websted for følsomme filer** i feltet **Beskrivelse af teamwebsted**.
1. Under **Indstillinger for beskyttelse af personlige oplysninger** skal du vælge **Privat – kun medlemmer kan få adgang til dette websted** og derefter vælge **Næste**.
1. I ruden **Who vil du tilføje? skal du** vælge **Udfør**.
    
Konfigurer derefter mappen Dokumenter på teamwebstedet SensitiveFiles for den følsomme opbevaringsmærkat.
  
1. Under fanen **Følsommefiler** i din browser skal du vælge **Dokumenter**.
1. Vælg ikonet **Indstillinger**, og vælg derefter **Biblioteksindstillinger**.
1. Under **Tilladelser og administration** skal du vælge **Anvend mærkat på elementer på denne liste eller dette bibliotek**. Hvis denne indstilling ikke vises, er dine opbevaringsmærkater endnu ikke publiceret. Prøv dette trin på et senere tidspunkt.
1. I **Indstillinger-Anvend etiket** skal du vælge **Følsom** på rullelisten og derefter vælge **Gem**.

Derefter skal du oprette et nyt dokument på webstedet SensitiveFiles og ændre dets opbevaringsmærkat.
    
1. Vælg **NewWord-dokument** >  i mappen dokumenter.
1. Skriv noget tekst i det tomme dokument. Vent på, at teksten gemmes.
1. Vælg **Delte dokumenter** på menulinjen.
1. Ud for det **Document.docx** filnavn skal du vælge den lodrette ellipse og derefter vælge **Detaljer**.
1. Bemærk, at dokumentet automatisk har anvendt den **følsomme** opbevaringsmærkat under **Anvend opbevaringsmærkat** i afsnittet **Egenskaber** i ruden til højre.
1. Klik på **Rediger alle**.
1. I ruden **Document.docx** under **Anvend opbevaringsmærkat** skal du vælge mærkaten **Meget fortroligt** og derefter vælge **Gem**.

## <a name="next-step"></a>Næste trin

Udforsk yderligere funktioner og funktioner til [beskyttelse af oplysninger](m365-enterprise-test-lab-guides.md#information-protection) i dit testmiljø.

## <a name="see-also"></a>Se også

[vejledninger til Microsoft 365 til testlaboratorier til virksomheder](m365-enterprise-test-lab-guides.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Microsoft 365 for enterprise-dokumentation](/microsoft-365-enterprise/)
