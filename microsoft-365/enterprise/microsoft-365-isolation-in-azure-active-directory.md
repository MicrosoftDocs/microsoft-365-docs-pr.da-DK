---
title: Microsoft 365 isolation og Access Control i Azure Active Directory
ms.author: robmazz
author: robmazz
manager: scotv
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
description: I denne artikel kan du få mere at vide om, hvordan Isolation og Access Control fungerer for at holde data for flere lejere isoleret fra hinanden inden for Azure Active Directory.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 409528847d04a55926138e49128f018b349da0a3
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65093871"
---
# <a name="microsoft-365-isolation-and-access-control-in-azure-active-directory"></a>Microsoft 365 isolation og Access Control i Azure Active Directory

Azure Active Directory (Azure AD) er udviklet til at hoste flere lejere på en yderst sikker måde gennem logisk dataisolation. Adgang til Azure AD er lukket af et godkendelseslag. Azure AD isolerer kunder, der bruger lejerobjektbeholdere, som sikkerhedsgrænser for at beskytte en kundes indhold, så indholdet ikke kan tilgås eller kompromitteres af medlejere. Der udføres tre kontroller af Azure AD's godkendelseslag:

- Er hovedprincipalen aktiveret for at få adgang til Azure AD-lejeren?
- Er hovedprincipalen aktiveret for at få adgang til data i denne lejer?
- Er sikkerhedsprincipalens rolle i denne lejer godkendt for den type dataadgang, der anmodes om?

Ingen programmer, brugere, servere eller tjenester kan få adgang til Azure AD uden den korrekte godkendelse og det korrekte token eller certifikat. Anmodninger afvises, hvis de ikke ledsages af korrekte legitimationsoplysninger.

Azure AD hoster effektivt hver lejer i sin egen beskyttede objektbeholder med politikker og tilladelser til og i objektbeholderen, der udelukkende ejes og administreres af lejeren.
 
![Azure-objektbeholder.](../media/office-365-isolation-azure-container.png)

Begrebet lejerobjektbeholdere er dybt rodfæstet i katalogtjenesten på alle lag lige fra portaler hele vejen til vedvarende lager. Selv når flere Azure AD-lejermetadata er gemt på den samme fysiske disk, er der ingen relation mellem andre objektbeholdere end det, der er defineret af katalogtjenesten, hvilket igen dikteres af lejeradministratoren. Der kan ikke være direkte forbindelser til Azure AD-lageret fra nogen, der anmoder om et program eller en tjeneste, uden først at gå gennem godkendelseslaget.

I eksemplet nedenfor har Både Contoso og Fabrikam separate, dedikerede objektbeholdere, og selvom disse objektbeholdere kan dele nogle af den samme underliggende infrastruktur, f.eks. servere og lager, forbliver de adskilt og isoleret fra hinanden og afspærret af lag af godkendelse og adgangskontrol.
 
![Azure-dedikerede objektbeholdere.](../media/office-365-isolation-azure-dedicated-containers.png)

Derudover er der ingen programkomponenter, der kan udføres fra Azure AD, og det er ikke muligt for én lejer at håndhæve brud på integriteten af en anden lejer, få adgang til krypteringsnøgler i en anden lejer eller læse rådata fra serveren.

Azure AD giver som standard ikke alle handlinger, der er udstedt af identiteter i andre lejere. Hver lejer er logisk isoleret i Azure AD via kravsbaserede adgangskontrolelementer. Læsninger og skrivninger af katalogdata er begrænset til lejerobjektbeholdere og afgrænset af et internt abstraktionslag og et rollebaseret RBAC-lag (Access Control), der tilsammen gennemtvinger lejeren som sikkerhedsgrænse. Alle anmodninger om adgang til mappedata behandles af disse lag, og alle anmodninger om adgang i Microsoft 365 styres af ovenstående logik.

Azure AD har Nordamerika, amerikanske myndigheder, EU, Tyskland og partitioner i hele verden. Der findes en lejer i en enkelt partition, og partitioner kan indeholde flere lejere. Partitionsoplysninger abstrakteres væk fra brugere. En given partition (herunder alle lejere i den) replikeres til flere datacentre. Partitionen for en lejer vælges på baggrund af lejerens egenskaber (f.eks. landekoden). Hemmeligheder og andre følsomme oplysninger i hver partition krypteres med en dedikeret nøgle. Nøglerne genereres automatisk, når der oprettes en ny partition.

Funktioner i Azure AD-systemet er en entydig forekomst af hver brugersession. Desuden bruger Azure AD krypteringsteknologier til at isolere delte systemressourcer på netværksniveau for at forhindre uautoriseret og utilsigtet overførsel af oplysninger.
