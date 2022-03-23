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
description: Få mere at vide Office 365, hvordan du bruger BitLocker-kryptering, hvilket reducerer risikoen for datatyveri på grund af mistede eller stjålne computere og diske.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 343a5966dc24954e98d7d31977aacbc09daaba11
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588953"
---
# <a name="bitlocker-and-distributed-key-manager-dkm-for-encryption"></a>BitLocker og Distributed Key Manager (DKM) til kryptering

Microsoft-servere bruger BitLocker til at kryptere de diskdrev, der indeholder kundens in rest-data, på volumenniveau. BitLocker-kryptering er en funktion til databeskyttelse, der er indbygget i Windows. BitLocker er en af de teknologier, der bruges til at beskytte mod trusler i tilfælde af, at der er udløbet andre processer eller kontroller (f.eks. adgangskontrol eller genbrug af hardware), der kan føre til, at en person får fysisk adgang til diske, der indeholder kundedata. I dette tilfælde fjerner BitLocker risikoen for datatyveri eller eksponering på grund af mistet, stjålet eller upassende udkørede computere og diske.

BitLocker installeres med AES (Advanced Encryption Standard) (AES) 256-bit kryptering på diske, der indeholder kundedata i Exchange Online, SharePoint Online og Skype for Business. Diskdrivelse er krypteret med en FVEK (Full Volume Encryption Key), som er krypteret med VMK (Volume Master Key), som igen er bundet til TPM (Trusted Platform Module) på serveren. VMK beskytter FVEK direkte og beskytter derfor VMK'en bliver kritisk. Følgende figur illustrerer et eksempel på BitLocker-nøglebeskyttelseskæden for en given server (i dette tilfælde ved hjælp af en Exchange Online server).

I følgende tabel beskrives BitLocker-nøglebeskyttelseskæden for en given server (i dette tilfælde en Exchange Online server).

| KEY 2016-TAST | GRANULARITET | HVORDAN GENERERET? | HVOR GEMMES DEN? | BESKYTTELSE |
|--------------------------------------------------------------------------------|-------------------------------------------------|----------------|-------------------------|--------------------------------------------------------------------------------------------------|
| AES 256-bit ekstern nøgle | Pr. server | BitLocker-API'er | TPM eller Secret Pengeskab | Lockbox /Access Control |
|  |  |  | Registreringsdatabase for postkasseserver | TPM-krypteret |
| 48-cifret numerisk adgangskode | Pr. disk | BitLocker-API'er | Active Directory | Lockbox /Access Control |
| X.509-certifikat som Agent til genoprettelse af data (DRA) kaldes også Public Key Recovery | Miljø (f.eks. Exchange Online multitenant) | Microsoft CA | Buildsystem | Ingen brugere har den fulde adgangskode til den private nøgle. Adgangskoden er under fysisk beskyttelse. |


BitLocker-nøgleadministration indebærer administration af genoprettelsesnøgler, der bruges til at låse op/gendanne krypterede diske i et Microsoft-datacenter. Microsoft 365 gemmer masternøglerne i en sikret deling, der kun er tilgængelig for personer, der er blevet screenet og godkendt. Legitimationsoplysningerne til tasterne gemmes i et sikkert lager til adgangskontroldata (det vi kalder et "hemmeligt lager"), hvilket kræver et højt niveau af udvidelses- og administrationsgodkendelser for at få adgang ved hjælp af et just-in-time-adgangs elevationsværktøj.

BitLocker understøtter nøgler, som falder inden for to administrationskategorier:

- BitLocker-administrerede nøgler, som generelt er kortvarige og knyttet til levetiden for en operativsystemforekomst, der er installeret på en server eller en given disk. Disse taster slettes og nulstilles under serverinstallation eller diskformatering.

- BitLocker-genoprettelsesnøgler, som administreres uden for BitLocker, men som bruges til diskkryptering. BitLocker bruger genoprettelsesnøgler til det scenarie, hvor operativsystemet er geninstalleret, og der allerede findes krypterede datadisks. Genoprettelsesnøgler bruges også af overvågning af tilgængelighed i Exchange Online hvor en svarer muligvis skal låse en disk op.

BitLocker-beskyttede volumener krypteres med en nøgle til kryptering af fuld volumen, som igen er krypteret med en volumenmasternøgle. BitLocker anvender FIPS-kompatible algoritmer for at sikre, at krypteringsnøgler aldrig gemmes eller sendes via kablet i rydning. Den Microsoft 365 implementering af kundedata-at-rest-protection, afviger ikke fra standard-BitLocker-implementeringen.
