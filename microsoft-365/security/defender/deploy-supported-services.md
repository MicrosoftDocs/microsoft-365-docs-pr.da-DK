---
title: Udrul tjenester, der understøttes af Microsoft 365 Defender
description: Få mere at vide om Microsoft-sikkerhedstjenester, der kan integreres af Microsoft 365 Defender, deres licenskrav og installationsprocedurer
keywords: installere, licenser, understøttede tjenester, klargøring, konfiguration Microsoft 365 Defender, M365, licensberettigelse, Microsoft Defender for Endpoint, Microsoft Defender for Office 365, Microsoft Defender for Identity, Microsoft Cloud App Security, MCAS, E5, A5, EMS
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 4ac6186f3ec8ca7d4888a995b2352ec50529e4f1
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664892"
---
# <a name="deploy-supported-services"></a>Udrul understøttede tjenester

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

[Microsoft 365 Defender](microsoft-365-defender.md) integrerer forskellige Microsoft-sikkerhedstjenester for at levere central registrerings-, forebyggelses- og undersøgelsesfunktioner mod avancerede angreb. I denne artikel beskrives de understøttede tjenester, deres licenskrav, de fordele og begrænsninger, der er knyttet til udrulning af en eller flere tjenester, og links til, hvordan du fuldt ud kan udrulle dem individuelt.

## <a name="supported-services"></a>Understøttede tjenester

En Microsoft 365 E5-, E5 Security-, A5- eller A5-sikkerhedslicens eller en gyldig kombination af licenser giver adgang til følgende understøttede tjenester og giver dig ret til at bruge Microsoft 365 Defender. [Se licenskrav](prerequisites.md#licensing-requirements)

| Understøttet tjeneste | Beskrivelse |
| ------ | ------ |
| Microsoft Defender for Endpoint | Endpoint Protection-pakke, der er bygget op omkring effektive adfærdssensorer, cloudanalyser og trusselsintelligens |
|Microsoft Defender for Office 365 | Avanceret beskyttelse af dine apps og data i Office 365, herunder mail og andre samarbejdsværktøjer |
| Microsoft Defender for Identity | Forsvar dig mod avancerede trusler, kompromitterede identiteter og ondsindede insidere ved hjælp af korrelerede Active Directory-signaler |
| Microsoft Defender for Cloud Apps | Identificer og bekæmpelse af cybertrusler på tværs af dine Cloudtjenester fra Microsoft og tredjeparter |

## <a name="deployed-services-and-functionality"></a>Udrullede tjenester og funktionalitet

Microsoft 365 Defender giver bedre synlighed, korrelation og afhjælpning, når du udruller flere understøttede tjenester.

### <a name="benefits-of-full-deployment"></a>Fordele ved fuld udrulning

Hvis du vil have de fulde fordele ved Microsoft 365 Defender, anbefaler vi, at du udruller alle understøttede tjenester. Her er nogle af de vigtigste fordele ved fuld udrulning:

- Hændelser identificeres og korreleres baseret på beskeder og hændelsessignaler fra alle tilgængelige sensorer og servicespecifikke analysefunktioner
- Air-playbooks (automatiseret undersøgelse og afhjælpning) gælder på tværs af forskellige objekttyper, herunder enheder, postkasser og brugerkonti
- Der kan forespørges om et mere omfattende avanceret jagtskema for hændelses- og objektdata fra enheder, postkasser og andre enheder

### <a name="limited-deployment-scenarios"></a>Begrænsede installationsscenarier

Hver understøttet tjeneste, som du installerer, leverer et meget omfattende sæt rå signaler samt korrelerede oplysninger. Selvom begrænset udrulning ikke medfører, at Microsoft 365 Defender funktionalitet deaktiveres, påvirkes muligheden for at give omfattende synlighed på tværs af dine slutpunkter, apps, data og identiteter. Samtidig gælder alle afhjælpningsfunktioner kun for enheder, der kan administreres af de tjenester, du har udrullet.

I nedenstående tabel kan du se, hvordan hver understøttet tjeneste giver yderligere data, muligheder for at få yderligere indsigt ved at korrelere dataene og bedre afhjælpnings- og svarfunktioner.

| Tjeneste | Data (signaler & korrelerede oplysninger) | Afhjælpning & svarområde |
| ------ | ------ | ------ |
| Microsoft Defender for Endpoint |<ul><li>Slutpunkttilstande og råhændelser</li><li>Slutpunktsregistreringer og -beskeder, herunder antivirus, Slutpunktsregistrering og -svar, reduktion af angrebsoverflade</li><li>Oplysninger om filer og andre enheder, der er observeret på slutpunkter</li></ul> | Slutpunkter |
|Microsoft Defender for Office 365 |<ul><li>Mail- og postkassetilstande og råhændelser</li><li>Registreringer af mails, vedhæftede filer og links</li></ul> | <ul><li>Postkasser</li><li>Microsoft 365 konti</li></ul> |
| Microsoft Defender for Identity |<ul><li>Active Directory-signaler, herunder godkendelseshændelser</li><li>Identitetsrelaterede adfærdsregistreringer</li></ul> | Identiteter |
| Microsoft Defender for Cloud Apps |<ul><li>Registrering af ikke-registrerede cloudapps og -tjenester (shadow IT)</li><li>Eksponering af data i cloudapps</li><li>Trusselsaktivitet, der er knyttet til cloudapps</li></ul> | Cloudapps |

## <a name="deploy-the-services"></a>Udrul tjenesterne

Udrulning af hver tjeneste kræver typisk klargøring til din lejer og en indledende konfiguration. Se følgende tabel for at forstå, hvordan hver af disse tjenester udrulles.

| Tjeneste | Klargøringsinstruktioner | Indledende konfiguration |
| ------ | ------ | ------ |
| Microsoft Defender for Endpoint | [Microsoft Defender for Endpoint installationsvejledning](../defender-endpoint/deployment-phases.md) | *Se klargøringsinstruktioner* |
|Microsoft Defender for Office 365 | *Ingen, klargjort med Office 365* | [Konfigurer Microsoft Defender for Office 365 politikker](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) |
| Microsoft Defender for Identity | [Hurtig start: Opret din Microsoft Defender for Identity forekomst](/azure-advanced-threat-protection/install-atp-step1) | *Se klargøringsinstruktioner* |
| Microsoft Defender for Cloud Apps | *Ingen* | [Hurtig start: Kom i gang med Microsoft Defender for Cloud Apps](/cloud-app-security/getting-started-with-cloud-app-security) |

Når du har udrullet de understøttede tjenester, [skal du aktivere Microsoft 365 Defender](m365d-enable.md).

## <a name="related-topics"></a>Relaterede emner

- [oversigt over Microsoft 365 Defender](microsoft-365-defender.md)
- [Slå Microsoft 365 Defender til](m365d-enable.md)
- [oversigt over Microsoft Defender for Endpoint](../defender-endpoint/microsoft-defender-endpoint.md)
- [oversigt over Microsoft Defender for Office 365](../office-365-security/defender-for-office-365.md)
- [oversigt over Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security)
- [oversigt over Microsoft Defender for Identity](/azure-advanced-threat-protection/what-is-atp)
