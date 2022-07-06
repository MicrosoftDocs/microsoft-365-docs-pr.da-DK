---
title: BitLocker til kryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: Få mere at vide om, hvordan Office 365 bruger BitLocker-kryptering, hvilket reducerer risikoen for datatyveri på grund af mistede eller stjålne computere og diske.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: dec62da7bc4d29891dcd86ec378faeb52a2d3d9f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633889"
---
# <a name="bitlocker-and-distributed-key-manager-dkm-for-encryption"></a>BitLocker og DKM (Distributed Key Manager) til kryptering

Microsoft-servere bruger BitLocker til at kryptere de diskdrev, der indeholder kundedata som inaktive data på diskenhedsniveau. BitLocker-kryptering er en databeskyttelsesfunktion, der er indbygget i Windows. BitLocker er en af de teknologier, der bruges til at beskytte mod trusler i tilfælde af bortfald i andre processer eller kontrolelementer (f.eks. adgangskontrol eller genanvendelse af hardware), der kan føre til, at nogen får fysisk adgang til diske, der indeholder kundedata. I dette tilfælde fjerner BitLocker risikoen for datatyveri eller eksponering på grund af mistede, stjålne eller upassende udrangerede computere og diske.

BitLocker installeres med AES (Advanced Encryption Standard) 256-bit kryptering på diske, der indeholder kundedata i Exchange Online, SharePoint Online og Skype for Business. Disksektorer krypteres med en FVEK (Full Volume Encryption Key), som krypteres med VMK (Volume Master Key), som igen er bundet til TPM (Trusted Platform Module) på serveren. VMK beskytter direkte FVEK, og derfor bliver beskyttelsen af VMK kritisk. Følgende figur illustrerer et eksempel på BitLocker-nøglebeskyttelseskæden for en given server (i dette tilfælde ved hjælp af en Exchange Online-server).

I følgende tabel beskrives BitLocker-nøglebeskyttelseskæden for en given server (i dette tilfælde en Exchange Online-server).

| NØGLEBESKYTTER | GRANULERING | HVORDAN GENERERET? | HVOR GEMMES DEN? | BESKYTTELSE |
|--------------------------------------------------------------------------------|-------------------------------------------------|----------------|-------------------------|--------------------------------------------------------------------------------------------------|
| Ekstern AES 256-bit nøgle | Pr. server | BitLocker-API'er | TPM eller Secret Safe | Lockbox/Access Control |
|  |  |  | Registreringsdatabase for postkasseserver | TPM-krypteret |
| 48-cifret numerisk adgangskode | Pr. disk | BitLocker-API'er | Active Directory | Lockbox/Access Control |
| X.509 Certifikat som DRA (Data Recovery Agent) kaldes også offentlig nøglebeskytter | Miljø (f.eks. Exchange Online multitenant) | Microsoft CA | Byg system | Ingen bruger har den fulde adgangskode til den private nøgle. Adgangskoden er under fysisk beskyttelse. |


BitLocker-nøgleadministration omfatter administration af genoprettelsesnøgler, der bruges til at låse/genoprette krypterede diske i et Microsoft-datacenter. Microsoft 365 gemmer masternøglerne på et sikkert share, som kun er tilgængelige for personer, der er blevet screenet og godkendt. Legitimationsoplysningerne for nøglerne gemmes i et sikkert lager til adgangskontroldata (det, vi kalder et "hemmeligt lager"), hvilket kræver et højt niveau af udvidede rettigheder og administrationsgodkendelser for at få adgang ved hjælp af et just-in-time-værktøj til adgangs udvidede rettigheder.

BitLocker understøtter nøgler, der falder i to administrationskategorier:

- BitLocker-administrerede nøgler, der generelt er kortvarige og knyttet til levetiden for en operativsystemforekomst, der er installeret på en server eller på en given disk. Disse nøgler slettes og nulstilles under geninstallation af serveren eller diskformatering.

- BitLocker-genoprettelsesnøgler, der administreres uden for BitLocker, men bruges til diskdekryptering. BitLocker bruger genoprettelsesnøgler til det scenarie, hvor et operativsystem geninstalleres, og der findes allerede krypterede datadisketter. Genoprettelsesnøgler bruges også af overvågningstest af administreret tilgængelighed i Exchange Online hvor en responder muligvis skal låse en disk op.

BitLocker-beskyttede diskenheder krypteres med en fuld krypteringsnøgle til diskenheden, som igen krypteres med en diskenhedsmasternøgle. BitLocker bruger FIPS-kompatible algoritmer til at sikre, at krypteringsnøgler aldrig gemmes eller sendes via kablet i klargøring. Microsoft 365-implementeringen af customer data-at-rest-protection afviger ikke fra standardimplementering af BitLocker.
