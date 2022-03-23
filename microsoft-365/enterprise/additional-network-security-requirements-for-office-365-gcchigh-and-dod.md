---
title: Yderligere krav til netværkssikkerhed for Office 365 GCC High og DoD
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150m
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: 'Oversigt: Office 365 GCC High og DoD har yderligere krav til netværkssikkerhed'
hideEdit: true
ms.openlocfilehash: c4fbfc52085b634329130c2785ce683109b8febe
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590346"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Yderligere krav til netværkssikkerhed for Office 365 GCC High og DOD

*Denne artikel gælder for Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High og Microsoft 365 DOD.*

Office 365 GCC High og DOD er sikre skymiljøer, der opfylder behovene i den amerikanske stat og dens leverandører og underleverandører.  Disse skymiljøer har yderligere netværksbegrænsninger, hvor eksterne slutpunkter tjenesterne har tilladelse til at få adgang til.

GCC High- og DOD-kunder, der planlægger at bruge identiteter i organisationsnetværket eller hybrid coexistence, kan kræve, at Microsoft tillader indgående og/eller udgående adgang til dine eksisterende lokale installationer.  Eksempler på disse aktiviteter omfatter:

* Brug af identiteter i organisationsnetværket (med Active Directory Federation Services eller lignende understøttede STS)
* Hybrid sameksistens med en lokal Exchange Server eller Skype for Business installation
* Overførsel af eksisterende brugerindhold fra et lokalt system

Hvis du vil tillade, at tjenesten kommunikerer med dine slutpunkter i det lokale miljø, skal du sende en mail til Office 365 til netværksændringer.

> [!WARNING]
> Alle anmodninger **har en** serviceaftale på tre uger og kan ikke fremskyndes på grund af de nødvendige sikkerheds- og overholdelseskontroller og installationspipelines.  Dette omfatter indledende onboarding-netværksanmodninger samt eventuelle ændringer, når du har overført til tjenesten.  Sørg for, at dine netværksteams er opmærksomme på denne tidslinje og medtager den i deres planlægningscyklus.

Send en mail til [Office 365 Government Allow-List med](mailto:o365gwlt@microsoft.com) følgende oplysninger:

* **Sådan**: [Office 365 Government Allow-List anmodninger](mailto:o365gwlt@microsoft.com)
* **Fra**: En lejeradministrator – send-mailen **skal svare** til en global administratorkontakt i din lejer
* **Mail emne**: Office 365 GCC High Network Request - contoso.onmicrosoft.us (erstat med dit lejernavn)

Brødteksten i meddelelsen skal indeholde følgende data:

* Dit Microsoft Online Services-lejernavn (f.eks. contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)
* En maildistributionsliste, som Microsoft kommunikerer med for den lokale kommunikation i forbindelse med netværksændringer og/eller opfølgning for ugyldige undernet
* Angiv, om du vil Microsoft Teams en hybrid sameksistens med dine lokale installationer
* Eksternt handicapvenligt URL-adresse (f.eks. sts.contoso.com) og IP-adresseområde i CIDR-notation (f.eks. 10.1.1.0/28)
* Lokal PKI-liste over tilbagekaldte certifikater og IP-adresseområde i CIDR-notation
* Eksternt handicapvenlig URL- og IP-adresseområde Exchange Server lokal installation i CIDR-notation
* Eksternt handicapvenlig URL- og IP-adresseområde Skype for Business lokal installation i CIDR-notation

Af hensyn til sikkerhed og overholdelse af regler og standarder skal du huske følgende begrænsninger på din anmodning:

* Der er en begrænsning på fire undernet pr. lejer
* Undernet skal være i CIDR-notation (f.eks. 10.1.1.0/28)
* Undernetintervaller må ikke være større end /24
* Vi **kan** ikke tage højde for anmodninger om at tillade adgang til kommercielle skytjenester (kommercielle Office 365, Google G-Suite, Amazon Web Services osv.)

Når din anmodning er modtaget og godkendt af Microsoft, er der en tre-ugers SLA til implementering og kan ikke fremskyndes.  Du modtager en indledende bekræftelse, når vi har modtaget din anmodning og en endelig bekræftelse, når den er fuldført.
