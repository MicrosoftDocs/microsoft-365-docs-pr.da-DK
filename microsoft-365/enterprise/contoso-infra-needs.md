---
title: Contoso It-infrastruktur og forretningsbehov
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Forstå den grundlæggende struktur i Contosos it-infrastruktur i det lokale miljø, og hvordan virksomhedens forretningsmæssige behov imødekommes af Microsoft 365 for virksomheden.
ms.openlocfilehash: 5dc47898aa0499bc4b62d22d37689d872116a9e7
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101353"
---
# <a name="contoso-it-infrastructure-and-business-needs"></a>Contoso It-infrastruktur og forretningsbehov

Contoso skifter fra en central it-infrastruktur i det lokale miljø til en cloud-inkluderende konfiguration, der omfatter cloudbaserede arbejdsbelastninger og -programmer for personlig produktivitet.

## <a name="existing-contoso-it-infrastructure"></a>Eksisterende Contoso-it-infrastruktur

Contoso bruger en primært centraliseret it-infrastruktur i det lokale miljø med programdatacentre i Paris's hovedkvarter.

Her er hovedkontoret med applikationsdatacentre, en DMZ og internettet.

![Eksisterende Contoso-it-infrastruktur.](../media/contoso-infra-needs/contoso-infra-needs-fig1.png)

Værten for programdatacentrene i det lokale miljø: 

- Brugerdefinerede line of business-programmer, der bruger SQL Server og andre Linux-databaser.
- Et sæt ældre SharePoint servere.
- Servere på organisationsniveau og teamniveau til fillagring.

Derudover understøtter hvert regionalt hubkontor et sæt servere med et tilsvarende sæt programmer. Disse servere er under kontrol af regionale it-afdelinger.

Det er fortsat en udfordring at søge på tværs af programmerne og dataene i disse separate multige geografiske datacentre.

I Contoso-hovedkvarterets DMZ leverer forskellige serversæt:

- Vært for det offentlige Contoso-websted, hvorfra kunderne kan bestille produkter, dele, forsyninger og service.
- Vært for Contoso-partner extranet til partnerkommunikation og samarbejde.
- VPN-baseret fjernadgang (Virtuelt privat netværk) til Contosos intranet og webproxy for arbejdere i Paris's hovedkvarter.

## <a name="contoso-business-needs"></a>Contoso-forretningsbehov

Contosos forretningsbehov falder i fem hovedkategorier:

**Produktivitet**

- Gør samarbejdet nemmere

  Erstat mail- og fildelingsbaseret samarbejde med en onlinemodel, der muliggør ændringer i dokumenter i realtid, nemmere onlinemøder og optagede samtaletråde.
- Øg produktiviteten for fjernarbejdere og mobile arbejdstagere

  Med mange medarbejdere, der arbejder hjemmefra eller i marken, kan du erstatte den flaskehalsede VPN-løsning med effektiv adgang til Contoso-data og -ressourcer i cloudmiljøet.
- Øg kreativiteten og innovationen

  Udnyt de nyeste visuelle lærings- og idéudviklingsmetoder, herunder håndskrift og 3D-visualisering.

**Sikkerhed**

- Identitets- og adgangsstyring

  Gennemtving multifaktor og andre former for godkendelse, og beskyt legitimationsoplysninger til bruger- og administratorkontoen.

- Trusselsbeskyttelse

  Beskyt mod eksterne sikkerhedstrusler, herunder mail og operativsystembaseret malware.

- Beskyttelse af oplysninger

  Lås adgang til og kryptér digitale aktiver med høj værdi, f.eks. kundedata, design- og produktionsspecifikationer og medarbejderoplysninger.

- Sikkerhedsadministration

  Overvåg sikkerhedsholdning, og registrer og reager på trusler i realtid.

**Fjern- og mobiladgang samt forretningspartnere**

- Øg sikkerheden for fjernarbejdere og mobile medarbejdere

  Implementer BYOD (Bring Your Own Device) og virksomhedsejet enhedshåndtering for at sikre sikker adgang, korrekt programfunktion og beskyttelse af virksomhedens data.

- Reducer fjernadgangsinfrastrukturen for medarbejdere

  Reducer vedligeholdelses- og supportomkostninger, og øg ydeevnen for fjernadgangsløsning ved at flytte ressourcer, der ofte tilgås, til cloudmiljøet.

- Giver bedre forbindelse og lavere omkostninger ved B2B-transaktioner (business-to-susiness)

  Erstat et aldrende og dyrt partner-ekstranet med en cloudbaseret løsning, der bruger godkendelse i organisationsnetværket.

**Overholdelse af regler og standarder**

- Overhold regionale lovmæssige krav

  Sørg for overholdelse af brancheregler og regionale regler for datalagring, kryptering, beskyttelse af personlige oplysninger og persondataregler, f.eks. den generelle forordning om databeskyttelse (GDPR) for EU.

**Administration**

- Lavere it-omkostninger til administration af software, der kører på klient-pc'er og -enheder

  Automatiser installation af opdateringer til Windows operativsystem og Microsoft 365 Apps for enterprise på tværs af organisationen.

## <a name="mapping-contoso-business-needs-to-microsoft-365-for-enterprise"></a>Tilknytning af Contoso-virksomheden skal Microsoft 365 for virksomheden

Contoso-it-afdelingen bestemte følgende tilknytning af forretningsbehov for at Microsoft 365 E5 funktioner før udrulningen:


| Kategori | Forretningsbehov | Microsoft 365 til virksomhedsprodukter eller -funktioner |
|:-------|:-----|:-----|
| Produktivitet |  |  |
|  | Gør samarbejdet nemmere | Microsoft Teams, SharePoint, OneDrive |
|  | Øg produktiviteten for fjernarbejdere og mobile arbejdstagere | Microsoft 365 arbejdsbelastninger og cloudbaserede data |
|  | Øg kreativiteten og innovationen | Windows Ink, Cortana på arbejde, PowerPoint |
| Sikkerhed |  |  |
|  | Administration af identitet & adgang | Dedikerede globale administratorkonti med Azure AD Multi-Factor Authentication (MFA) og Azure AD Privileged Identity Management (PIM) <br> MFA for alle brugerkonti <br> Betinget adgang <br> Sikkerhedslæser <br> Windows Hello <br> Windows Credential Guard |
|  | Trusselsbeskyttelse | Advanced Threat Analytics <br> Windows Defender <br> Defender for Office 365 <br> Microsoft Defender for Office 365 <br> Microsoft 365 trusselsundersøgelse og -reaktion <br> |
|  | Beskyttelse af oplysninger | Azure Information Protection <br> Forebyggelse af datatab (DLP) <br> Windows Information Protection (IGVA) <br> Microsoft Defender for Cloud Apps <br> Microsoft Intune |
|  | Sikkerhedsadministration | Microsoft Defender for Cloud  <br> Windows Defender Security Center |
| Fjern- og mobiladgang samt forretningspartnere |  |  |
|  | Bedre sikkerhed for fjernarbejdere og mobile arbejdstagere | Microsoft Intune |
|  | Reducer fjernadgangsinfrastrukturen for medarbejdere | Microsoft 365 arbejdsbelastninger og cloudbaserede data |
|  | Gør forbindelsen bedre og lavere omkostninger ved B2B-transaktioner | Godkendelse i organisationsnetværk og cloudbaserede ressourcer |
| Overholdelse af regler og standarder |  |  |
|  | Overhold regionale lovmæssige krav | GDPR-funktioner i Microsoft 365 |
| Administration |  |  |
|  | Lavere it-omkostninger ved installation af klientopdateringer | Windows 10 Enterprise opdateringer <br> Microsoft 365 Apps for enterprise opdateringer |
||||

## <a name="next-step"></a>Næste trin

Få mere at vide om Contoso [Corporations netværk i det lokale miljø](contoso-networking.md), og hvordan det er optimeret til adgang og ventetid til Microsoft 365 cloudbaserede ressourcer.

## <a name="see-also"></a>Se også

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Vejledninger til testlaboratorier](m365-enterprise-test-lab-guides.md)
