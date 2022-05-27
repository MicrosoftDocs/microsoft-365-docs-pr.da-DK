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
description: 'Oversigt: Office 365 GCC High og DoD har yderligere sikkerhedskrav til netværket'
hideEdit: true
ms.openlocfilehash: 86d3eb3fb4db42eda2be0c2c66fc754fbfd35f1e
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754262"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Yderligere krav til netværkssikkerhed for Office 365 GCC High og DOD

*Denne artikel gælder for Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High og Microsoft 365 DOD.*

Office 365 GCC High og DOD er sikre cloudmiljøer, der opfylder behovene hos USA Government og dens leverandører og leverandører.  Disse cloudmiljøer har yderligere netværksbegrænsninger, som de eksterne slutpunkter tjenesterne har adgang til.

GCC High- og DOD-kunder, der planlægger at bruge organisationsnetværksidentiteter eller hybride sameksisterende, kan kræve, at Microsoft tillader indgående og/eller udgående adgang til dine eksisterende installationer i det lokale miljø.  Eksempler på disse aktiviteter omfatter:

* Brug af organisationsnetværksidentiteter (med Active Directory Federation Services eller lignende understøttede STS)
* Hybrid sameksistens med en udrulning af Exchange Server eller Skype for Business i det lokale miljø
* Overflytning af eksisterende brugerindhold fra et lokalt system

Hvis du vil tillade tjenesten at kommunikere med dine slutpunkter i det lokale miljø, **skal** du sende en mail til Office 365 tekniker for netværksændringer.

> [!WARNING]
> Alle anmodninger har en SLA på **tre uger** og kan ikke fremskyndes på grund af de påkrævede sikkerheds- og overholdelseskontrolfunktioner og udrulningspipelines.  Dette omfatter indledende onboarding af netværksanmodninger samt eventuelle ændringer, efter at du har migreret til tjenesten.  Sørg for, at dine netværksteams er opmærksomme på denne tidslinje og inkluderer den i deres planlægningscyklusser.

Send en mail til [Office 365 Government Allow-List anmodninger](mailto:o365gwlt@microsoft.com) med følgende oplysninger:

* **Til**: [Office 365 Government Allow-List anmodninger](mailto:o365gwlt@microsoft.com)
* **Fra**: En lejeradministrator – send-mailen **skal** svare til en global administratorkontakt i din lejer
* **Mailemne**: Office 365 GCC anmodning om højt netværk – contoso.onmicrosoft.us (erstat med dit lejernavn)

Meddelelsens brødtekst skal indeholde følgende data:

* Navnet på din Microsoft Online Services-lejer (f.eks. contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)
* En maildistributionsliste, som Microsoft kommunikerer med i forbindelse med igangværende kommunikation i forbindelse med netværksændringer og/eller opfølgning på ugyldige undernet
* Angiv, om du planlægger at bruge Microsoft Teams hybrid sameksistens med dine udrulninger i det lokale miljø
* Eksternt tilgængelig URL-adresse (f.eks. sts.contoso.com) og IP-adresseinterval i CIDR-notation (f.eks. i organisationsnetværket). 10.1.1.0/28)
* URL-adresse til liste over tilbagekaldte certifikater i det lokale miljø og IP-adresseområde i CIDR-notation
* Eksternt tilgængeligt URL-adresse- og IP-adresseinterval for Exchange Server installation i det lokale miljø i CIDR-notation
* Eksternt tilgængeligt URL-adresse- og IP-adresseinterval for Skype for Business installation i det lokale miljø i CIDR-notation

Af hensyn til sikkerheden og overholdelse af angivne standarder skal du være opmærksom på følgende begrænsninger for din anmodning:

* Der er en begrænsning på fire undernet pr. lejer
* Undernet skal være i CIDR-notation (f.eks. 10.1.1.0/28)
* Undernetområder må ikke være større end /24
* Vi **kan ikke** imødekomme anmodninger om at give adgang til kommercielle cloudtjenester (kommercielle Office 365, Google G-Suite, Amazon Web Services osv.)

Når din anmodning er modtaget og godkendt af Microsoft, er der en SLA på tre uger til implementering og kan ikke fremskyndes.  Du modtager en indledende bekræftelse, når vi har modtaget din anmodning og en endelig bekræftelse, når den er fuldført.
