---
title: Tjenestekryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.date: 10/3/2019
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection: Strat_O365_Enterprise
description: 'Oversigt: Forstå datarobusthed i Microsoft Office 365.'
ms.openlocfilehash: 54bae9fa0203d76c598c4dee337ee15f24a2fc24
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587732"
---
# <a name="service-encryption"></a>Tjenestekryptering

Ud over at bruge kryptering på volumenniveau bruger Exchange Online, Microsoft Teams, SharePoint Online og OneDrive for Business også tjenestekryptering til at kryptere kundedata. Tjenestekryptering giver mulighed for to vigtige administrationsindstillinger:

## <a name="microsoft-managed-keys"></a>Microsoft-administrerede nøgler
Microsoft administrerer alle krypterede nøgler, herunder rodnøgler til tjenestekryptering. Denne indstilling er i øjeblikket aktiveret som standard for Exchange Online, SharePoint Online OneDrive for Business. Microsoft-administrerede nøgler giver standardtjenestekryptering, medmindre du beslutter at onboarde ved hjælp af kundenøgle. Hvis du på et senere tidspunkt beslutter at stoppe med at bruge kundenøgle uden at følge datarensestien, forbliver dine data krypterede ved hjælp af De Microsoft-administrerede nøgler. Dine data er altid krypteret på dette standardniveau som minimum. 

## <a name="customer-key"></a>Kundenøgle
Du leverer rodnøgler, der bruges med tjenestekryptering, og du administrerer disse nøgler ved hjælp af Azure Key Vault. Microsoft administrerer alle andre nøgler. Denne indstilling kaldes Kundenøgle, og den er i øjeblikket tilgængelig for Exchange Online, SharePoint Online og OneDrive for Business. (Tidligere kaldet Avanceret kryptering med BYOK. Se [Forbedring af gennemsigtighed og kontrol for Office 365 kunder](https://www.microsoft.com/en-us/microsoft-365/blog/2015/04/21/enhancing-transparency-and-control-for-office-365-customers/) for den oprindelige meddelelse).

Tjenestekryptering giver flere fordele:

- Giver et ekstra lag af beskyttelse oven på BitLocker.

- Indeholder en adskillelse Windows af administratorer af operativsystemer fra adgang til programdata, der er gemt eller behandlet af operativsystemet.

- Omfatter en kundenøgleindstilling, der gør det muligt for tjenester med flere lejere at levere nøglestyring pr. lejer.

- Forbedrer muligheden for at bruge Microsoft 365 at opfylde kravene fra kunder, der har specifikke krav til overholdelse af regler og standarder vedrørende kryptering.

Ved hjælp af kundenøgle kan du generere dine egne krypterede nøgler ved hjælp af enten et lokalt Hardware Service Module (HSM) eller Azure Key Vault (AKV). Uanset hvordan du opretter nøglen, bruger du AKV til at styre og administrere de krypterede nøgler, der bruges Office 365. Når dine nøgler er gemt i AKV, kan de bruges som roden af en af de nøgleringe, der krypterer dine postkassedata eller filer.

En anden fordel ved kundenøgle er den kontrol, du har over Microsofts mulighed for at behandle dine data. Hvis du vil fjerne data fra Office 365, f.eks. hvis du vil afslutte tjenesten med Microsoft eller fjerne en del af dine data, der er gemt i skyen, kan du gøre det og bruge kundenøgle som et teknisk kontrolelement. Fjernelse af data sikrer, at ingen, herunder Microsoft, kan få adgang til eller behandle dataene. Kundenøgle supplerer og supplerer kundelåsfeltet, som du bruger til at kontrollere Microsoft-medarbejderes adgang til dine data.

Hvis du vil lære, hvordan du konfigurerer en kundenøgle til Microsoft 365 til Exchange Online, Microsoft Teams, SharePoint Online, herunder teamwebsteder og OneDrive for Business, skal du se følgende artikler:

- [Tjenestekryptering med kundenøgle](customer-key-overview.md)

- [Konfigurer kundenøgle](customer-key-set-up.md)

- [Administrer kundenøgle](customer-key-manage.md)

- [Roll or rotate a customer key or an availability key](customer-key-availability-key-roll.md)

- [Forstå tilgængelighedsnøglen](customer-key-availability-key-understand.md)
