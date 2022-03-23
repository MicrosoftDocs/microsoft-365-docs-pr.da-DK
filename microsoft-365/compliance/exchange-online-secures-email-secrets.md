---
title: Sådan Exchange Online dine mailhemmeligheder
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 07/01/2019
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 989ba10c-f73f-4efb-ad1b-af3322e5f376
ms.collection:
- M365-security-compliance
description: Ud over det Office 365 Sikkerhedscenter, der indeholder oplysninger om sikkerhed, beskyttelse af personlige oplysninger og overholdelse af regler og standarder til Microsoft 365, vil du måske gerne vide, hvordan Microsoft hjælper med at beskytte hemmeligheder, du gemmer i dets datacentre. Vi bruger en teknologi kaldet Distributed Key Manager (DKM).
ms.openlocfilehash: a1d939ebfc1ecba1e7cb8b97111f677f754894b1
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/14/2022
ms.locfileid: "63589132"
---
# <a name="how-exchange-online-secures-your-email-secrets"></a>Sådan Exchange Online dine mailhemmeligheder

Denne artikel beskriver, hvordan Microsoft sikrer dine mailhemmeligheder i sine datacentre.
  
## <a name="how-do-we-secure-secret-information-provided-by-you"></a>Hvordan sikrer vi hemmelige oplysninger, du har afgivet?

Ud over det Office 365 Sikkerhedscenter, der indeholder oplysninger om sikkerhed, beskyttelse af personlige oplysninger og overholdelse af regler og standarder [til Office 365](./get-started-with-service-trust-portal.md), kan det være en god ide at vide, hvordan Microsoft beskytter de hemmeligheder, du angiver i sine datacentre. Vi bruger en teknologi kaldet Distributed Key Manager (DKM).
  
[Distributed Key Manager](office-365-bitlocker-and-distributed-key-manager-for-encryption.md) (DKM) er en funktionalitet på klientsiden, der bruger et sæt hemmelige nøgler til at kryptere og dekryptere oplysninger. Kun medlemmer af en bestemt sikkerhedsgruppe i Active Directory-domæneservices kan få adgang til disse nøgler for at dekryptere de data, der er krypteret af DKM. I Exchange Online er det kun visse tjenestekonti, Exchange kører under, der er en del af den pågældende sikkerhedsgruppe. Som en del af standardoperativsystemet i datacenteret er der ikke givet nogen legitimationsoplysninger, som er en del af denne sikkerhedsgruppe, og derfor har ingen mennesker adgang til de nøgler, der kan dekryptere disse hemmeligheder.
  
Ved fejlfindings-, fejlfindings- eller overvågningsformål skal en datacenteradministrator anmode om administratorrettigheder for at få midlertidige legitimationsoplysninger, som er en del af sikkerhedsgruppen. Denne proces kræver flere niveauer af juridisk godkendelse. Hvis der tildeles adgang, logføres og overvåges al aktivitet. Desuden gives der kun adgang i et bestemt tidsrum, hvorefter adgangen udløber automatisk.
  
For ekstra beskyttelse omfatter DKM-teknologi automatiseret nøglerulle og arkivering. Dette sikrer også, at du kan fortsætte med at få adgang til dit ældre indhold uden at skulle stole på den samme nøgle på ubestemt tid.
  
## <a name="where-does-exchange-online-make-use-of-dkm"></a>Hvor Exchange Online dkM?

Microsoft bruger [Distributed Key Manager](office-365-bitlocker-and-distributed-key-manager-for-encryption.md) til at kryptere dine Exchange Online datacentre. Eksempel:
  
- Legitimationsoplysninger for mailkonto for forbundne konti. Forbundne konti er tredjepartskonti som f.eks. Hotmail, Gmail og Yahoo! mailkonti.

- Kundenøgle. Hvis du bruger [tjenestekryptering med kundenøgle](customer-key-overview.md), skal du bruge [Azure Key Vault](/azure/key-vault/key-vault-whatis) til at beskytte dine hemmeligheder.

## <a name="related-topics"></a>Relaterede emner

[Kryptering i Office 365](encryption.md)
  
[Tekniske referenceoplysninger om kryptering](technical-reference-details-about-encryption.md)
  
[Tjenestesikring i Security &amp; Compliance Center](./service-assurance.md)
