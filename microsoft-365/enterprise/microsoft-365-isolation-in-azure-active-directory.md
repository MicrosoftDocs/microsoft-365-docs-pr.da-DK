---
title: Microsoft 365 isolation og adgangskontrol i Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: I denne artikel kan du lære, hvordan Isolation og adgangskontrol fungerer for at holde data for flere lejere isoleret fra hinanden Azure Active Directory.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 11c2c488f0168815a1485f5833c5520259db0fa5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590366"
---
# <a name="microsoft-365-isolation-and-access-control-in-azure-active-directory"></a>Microsoft 365 isolation og adgangskontrol i Azure Active Directory

Azure Active Directory (Azure AD) blev udviklet til at hoste flere lejere på en meget sikker måde via logisk dataisolation. Adgang til Azure AD begrænses af et godkendelseslag. Azure AD isolerer kunder, der bruger lejerbeholdere som sikkerhedsgrænser for at beskytte en kundes indhold, så indholdet ikke kan tilgås eller kompromitteres af andre lejere. Der udføres tre kontroller af Azure AD's godkendelseslag:

- Er hovedstolen aktiveret for adgang til Azure AD-lejeren?
- Er hovedstolen aktiveret for adgang til data i denne lejer?
- Er hovedstolens rolle i denne lejer autoriseret til den type dataadgang, der anmodes om?

Intet program, bruger, server eller tjeneste kan få adgang til Azure AD uden den rette godkendelse og det rigtige token eller certifikat. Anmodninger afvises, hvis de ikke ledsages af korrekte legitimationsoplysninger.

Azure AD hoster effektivt hver lejer i sin egen beskyttede beholder med politikker og tilladelser til og i beholderen, der udelukkende ejes og administreres af lejeren.
 
![Azure-objektbeholder.](../media/office-365-isolation-azure-container.png)

Begrebet lejerbeholdere er dybt bekymrende i katalogtjenesten på alle lag, fra portaler hele vejen til vedvarende lagerplads. Selvom flere Azure AD-lejermetadata gemmes på den samme fysiske disk, er der ingen relation mellem de andre beholdere end dem, der er defineret af katalogtjenesten, som igen dikteres af lejeradministratoren. Der kan ikke være nogen direkte forbindelser til Azure AD-lagerplads fra et program eller en tjeneste, der anmoder om det, uden først at gå gennem godkendelseslaget.

I eksemplet nedenfor har Contoso og Fabrikam begge separate, dedikerede beholdere, og selvom disse beholdere kan dele noget af den samme underliggende infrastruktur, f.eks. servere og lager, forbliver de adskilte og isolerede fra hinanden, og de er adskilt af lag af godkendelse og adgangskontrol.
 
![Dedikerede Azure-objektbeholdere.](../media/office-365-isolation-azure-dedicated-containers.png)

Desuden er der ingen programkomponenter, der kan udføres inde fra Azure AD, og det er ikke muligt for én lejer at krænke integriteten af en anden lejer, få adgang til krypteringsnøgler fra en anden lejer eller læse rådata fra serveren.

Som standard tillades alle handlinger, der er udstedt af identiteter i andre lejere, ikke i Azure AD. Hver lejer er logisk isoleret i Azure AD via kravbaserede adgangskontrolelementer. Læsning og skrivning af katalogdata er begrænset til lejerbeholdere og af et internt abstraktionslag og et rollebaseret adgangskontrollag (RBAC), som sammen gennemtvinger lejeren som sikkerhedsgrænse. Alle mappedataadgangsanmodninger behandles af disse lag, og alle adgangsanmodninger i Microsoft 365 er under kontrol af den ovenstående logik.

Azure AD har nordamerika, amerikanske myndigheder, EU, Tyskland og World Wide partitioner. En lejer findes i en enkelt partition, og partitioner kan indeholde flere lejere. Partitionsoplysninger indsamles væk fra brugerne. En given partition (herunder alle lejerne i den) replikeres til flere datacentre. Partitionen for en lejer vælges ud fra egenskaberne for lejeren (f.eks. landekoden). Hemmeligheder og andre følsomme oplysninger i hver partition krypteres med en dedikeret nøgle. Tasterne genereres automatisk, når der oprettes en ny partition.

Azure AD-systemfunktionaliteter er en entydig forekomst for hver brugersession. Azure AD bruger desuden krypteringsteknologier til at levere isolation af delte systemressourcer på netværksniveau for at forhindre uautoriseret og utilsigtet overførsel af oplysninger.
