---
title: It-infrastruktur og forretningsmæssige behov for Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Forstå den grundlæggende struktur i den lokale it-infrastruktur i Contoso, og hvordan virksomhedens forretningsmæssige behov opfyldes af Microsoft 365 for virksomheder.
ms.openlocfilehash: 94118a66f7bb1468a8f27816151a3b4d087b5703
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63589490"
---
# <a name="contoso-it-infrastructure-and-business-needs"></a>It-infrastruktur og forretningsmæssige behov for Contoso

Contoso skifter fra en lokal, centraliseret IT-infrastruktur til en skyomfattende konfiguration, der indeholder skybaserede personlige produktivitetsmængder og programmer.

## <a name="existing-contoso-it-infrastructure"></a>Eksisterende it-infrastruktur for Contoso

Contoso anvender primært en centraliseret it-infrastruktur i det lokale miljø med programdatacentre i Paris's hovedkvarter.

Her er hovedkontoret med programdatacentre, en DMZ og internettet.

![Eksisterende it-infrastruktur for Contoso.](../media/contoso-infra-needs/contoso-infra-needs-fig1.png)

Vært for det lokale programs datacentre: 

- Brugerdefinerede line of business-programmer, der bruger SQL Server og andre Linux-databaser.
- Et sæt ældre SharePoint-servere.
- Servere på organisationsniveau og på teamniveau til fillagring.

Desuden understøtter hvert regionale hubkontor et sæt servere med et lignende sæt programmer. Disse servere er under kontrol af regionale it-afdelinger.

Søgbarhed på tværs af programmer og data i disse separate multi geografiske datacentre er fortsat en udfordring.

I Contoso-hovedkontoret DMZ giver forskellige sæt servere:

- Vært for det offentlige contoso-websted, hvorfra kunder kan bestille produkter, dele, materialer og tjenester.
- Vært for Contoso-partner ekstranet for partnerkommunikation og samarbejde.
- Virtuelt privat netværk (VPN)-baseret fjernadgang til Contoso-intranet og webproxy for medarbejdere i Paris's hovedkvarter.

## <a name="contoso-business-needs"></a>Forretningsbehov i Contoso

Contoso-forretningsbehov kan ind indgå i fem hovedkategorier:

**Produktivitet**

- Gør samarbejde nemmere

  Erstat mail- og fildelingsbaseret samarbejde med en onlinemodel, der giver mulighed for ændringer i dokumenter i realtid, nemmere onlinemøder og hentede samtaletråde.
- Forbedr produktiviteten for fjern- og mobilmedarbejdere

  Når mange medarbejdere arbejder hjemmefra eller i feltet, skal du erstatte VPN-løsningen med flaskehalse med performant adgang til Contoso-data og -ressourcer i skyen.
- Øg kreativiteten og innovationen

  Udnyt de nyeste metoder til visuel læring og udvikling af ideer, herunder håndskrift og 3D-visualisering.

**Sikkerhed**

- Administration af identitet og adgang

  Gennemtving multifaktor og andre former for godkendelse, og beskyt legitimationsoplysninger for bruger- og administratorkonti.

- Trusselsbeskyttelse

  Beskyt dig mod eksterne sikkerhedstrusler, herunder mail og operativsystembaseret malware.

- Beskyttelse af oplysninger

  Lås adgangen til og kryptere digitale aktiver med høj værdi, f.eks. kundedata, design- og produktionsspecifikationer og medarbejderoplysninger.

- Sikkerhedsadministration

  Overvåg sikkerhed, og find og svar på trusler i realtid.

**Fjern- og mobiladgang og forretningspartnere**

- Forbedre sikkerheden for fjern- og mobilmedarbejdere

  Implementer medbring din egen enhed (BYOD) og virksomhedsejede enhedsadministration for at sikre sikret adgang, korrekt programfunktionsmåde og virksomhedens databeskyttelse.

- Reducer fjernadgangsinfrastrukturen for medarbejdere

  Reducer vedligeholdelses- og supportomkostningerne, og forbedr ydeevnen for en løsning til fjernadgang ved at flytte almindeligt tilgåde ressourcer til skyen.

- Giver bedre forbindelse og lavere omkostninger ved B2B-transaktioner (business-to-susiness)

  Erstat et ældre og dyrere partner ekstranet med en skybaseret løsning, der bruger federated authentication.

**Overholdelse af regler og standarder**

- Overholde regionale lovmæssige krav

  Sørg for overholdelse af branche og regionale bestemmelser for datalagring, kryptering, beskyttelse af personlige oplysninger og persondata, som f.eks. Persondataforordningen (GDPR) for Europa.

**Administration**

- Få lavere it-omkostninger til administration af software, der kører på klient-pc'er og -enheder

  Automatiser installation af opdateringer til Windows og opdateringer Microsoft 365 Apps for enterprise tværs af organisationen.

## <a name="mapping-contoso-business-needs-to-microsoft-365-for-enterprise"></a>Tilknytning af Contoso-virksomhed Microsoft 365 for virksomheder

It-afdelingen i Contoso har fastlagt følgende tilknytning af forretningsbehov for Microsoft 365 E5 før installation:


| Kategori | Forretningsmæssige behov | Microsoft 365 til virksomhedsprodukter eller -funktioner |
|:-------|:-----|:-----|
| Produktivitet |  |  |
|  | Gør samarbejde nemmere | Microsoft Teams, SharePoint, OneDrive |
|  | Forbedr produktiviteten for fjern- og mobilmedarbejdere | Microsoft 365 arbejdsbelastninger og skybaserede data |
|  | Øg kreativiteten og innovationen | Windows Ink er Cortana på arbejde PowerPoint |
| Sikkerhed |  |  |
|  | Administration & identitetsadgang | Dedikerede globale administratorkonti med Azure AD Multi-Factor Authentication (MFA) og Azure AD Privileged Identity Management (PIM) <br> MFA for alle brugerkonti <br> Betinget adgang <br> Sikkerhedslæser <br> Windows Hello <br> Windows Credential Guard |
|  | Trusselsbeskyttelse | Advanced Threat Analytics <br> Windows Defender <br> Defender til Office 365 <br> Microsoft Defender til Office 365 <br> Microsoft 365 trusselsundersøgelse og -svar <br> |
|  | Beskyttelse af oplysninger | Azure Information Protection <br> Forebyggelse af datatab (DLP) <br> Windows (WIP) <br> Microsoft Defender til skyapps <br> Microsoft Intune |
|  | Sikkerhedsadministration | Microsoft Defender til skyen  <br> Windows Defender Security Center |
| Fjern- og mobiladgang og forretningspartnere |  |  |
|  | Bedre sikkerhed for fjern- og mobilmedarbejdere | Microsoft Intune |
|  | Reducer fjernadgangsinfrastrukturen for medarbejdere | Microsoft 365 arbejdsbelastninger og skybaserede data |
|  | Få bedre forbindelse og lavere omkostninger for B2B-transaktioner | Federated Authentication og skybaserede ressourcer |
| Overholdelse af regler og standarder |  |  |
|  | Overholde regionale lovmæssige krav | GDPR-funktioner i Microsoft 365 |
| Administration |  |  |
|  | Sænke it-omkostninger til installation af klientopdateringer | Windows 10 Enterprise opdateringer <br> Microsoft 365 Apps for enterprise opdateringer |
||||

## <a name="next-step"></a>Næste trin

Få mere at vide om det lokale Contoso [Corporation-netværk](contoso-networking.md), og hvordan det er blevet optimeret til adgang og ventetid til Microsoft 365 skybaserede ressourcer.

## <a name="see-also"></a>Se også

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Test labvejledninger](m365-enterprise-test-lab-guides.md)
