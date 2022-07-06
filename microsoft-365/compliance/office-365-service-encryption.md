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
description: 'Oversigt: Forstå datas robusthed i Microsoft Office 365.'
ms.openlocfilehash: 66899a337e9349a78178df67aa83e44b580c7148
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629373"
---
# <a name="service-encryption"></a>Tjenestekryptering

Ud over at bruge kryptering på diskenhedsniveau bruger Exchange Online, Microsoft Teams, SharePoint Online og OneDrive for Business også Tjenestekryptering til at kryptere kundedata. Tjenestekryptering giver mulighed for to indstillinger for nøgleadministration:

## <a name="microsoft-managed-keys"></a>Microsoft-administrerede nøgler
Microsoft administrerer alle kryptografiske nøgler, herunder rodnøglerne til tjenestekryptering. Denne indstilling er i øjeblikket aktiveret som standard for Exchange Online, SharePoint Online OneDrive for Business. Microsoft-administrerede nøgler leverer standardtjenestekryptering, medmindre du beslutter dig for at onboarde ved hjælp af kundenøglen. Hvis du på et senere tidspunkt beslutter at stoppe med at bruge kundenøglen uden at følge stien til datarensning, forbliver dine data krypteret ved hjælp af de Microsoft-administrerede nøgler. Dine data krypteres altid på dette standardniveau som minimum. 

## <a name="customer-key"></a>Kundenøgle
Du angiver rodnøgler, der bruges sammen med tjenestekryptering, og du administrerer disse nøgler ved hjælp af Azure Key Vault. Microsoft administrerer alle andre nøgler. Denne indstilling kaldes Kundenøgle og er i øjeblikket tilgængelig for Exchange Online, SharePoint Online og OneDrive for Business. (Tidligere kaldet Avanceret kryptering med BYOK. Se [Forbedring af gennemsigtighed og kontrol for Office 365 kunder](https://www.microsoft.com/en-us/microsoft-365/blog/2015/04/21/enhancing-transparency-and-control-for-office-365-customers/) i forbindelse med den oprindelige meddelelse).

Tjenestekryptering giver flere fordele:

- Giver et ekstra beskyttelseslag oven på BitLocker.

- Giver mulighed for at adskille Administratorer af Windows-operativsystemet fra adgang til programdata, der er gemt eller behandlet af operativsystemet.

- Omfatter en kundenøgleindstilling, der gør det muligt for tjenester med flere lejere at levere nøgleadministration pr. lejer.

- Forbedrer muligheden for, at Microsoft 365 kan opfylde kravene fra kunder, der har specifikke krav til overholdelse af angivne standarder i forbindelse med kryptering.

Ved hjælp af kundenøglen kan du generere dine egne kryptografiske nøgler ved hjælp af enten et HSM (Hardware Service Module) i det lokale miljø eller Azure Key Vault (AKV). Uanset hvordan du genererer nøglen, kan du bruge AKV til at styre og administrere de kryptografiske nøgler, der bruges af Office 365. Når dine nøgler er gemt i AKV, kan de bruges som rod i en af de nøgleringe, der krypterer dine postkassedata eller -filer.

En anden fordel ved Customer Key er den kontrol, du har over Microsofts mulighed for at behandle dine data. Hvis du vil fjerne data fra Office 365, f.eks. hvis du vil afslutte tjenesten med Microsoft eller fjerne en del af dine data, der er gemt i cloudmiljøet, kan du gøre det og bruge Kundenøgle som teknisk kontrol. Fjernelse af data sikrer, at ingen, herunder Microsoft, kan få adgang til eller behandle dataene. Kundenøglen supplerer og supplerer Customer Lockbox, som du bruger til at styre Microsoft-medarbejderes adgang til dine data.

Du kan få mere at vide om, hvordan du konfigurerer kundenøgle til Microsoft 365 til Exchange Online, Microsoft Teams, SharePoint Online, herunder teamwebsteder og OneDrive for Business, i disse artikler:

- [Tjenestekryptering med kundenøgle](customer-key-overview.md)

- [Konfigurer kundenøgle](customer-key-set-up.md)

- [Administrer kundenøgle](customer-key-manage.md)

- [Rul eller roter en kundenøgle eller en tilgængelighedsnøgle](customer-key-availability-key-roll.md)

- [Forstå tilgængelighedsnøglen](customer-key-availability-key-understand.md)
