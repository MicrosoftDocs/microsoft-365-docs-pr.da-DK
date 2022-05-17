---
title: Skift din mailadresse til at bruge dit brugerdefinerede domæne
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: f4d8cae9-6d06-4c4b-b4e5-6581fd05ea82
description: Skift din mailadresse til en brugervenlig mailadresse som tom@fourthcoffee.com ved at købe et domænenavn og føje den til Microsoft 365.
ms.openlocfilehash: a71e92b48e7091ae243b62ec594cd2be5ce52406
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65437277"
---
# <a name="change-your-microsoft-365-email-address-to-use-your-custom-domain"></a>Skift din Microsoft 365 mailadresse, så den bruger dit brugerdefinerede domæne

 **[Se ofte stillede spørgsmål om domæner](../setup/domains-faq.yml)** , hvis du ikke kan finde det, du leder efter. 
  
::: moniker range="o365-worldwide"

Din oprindelige mailadresse i Microsoft 365 omfatter .onmicrosoft.com, f.eks. tom@fourthcoffee.onmicrosoft.com. Du kan ændre den til en mere brugervenlig adresse, f.eks. tom@fourthcoffee.com. Du skal bruge dit eget domænenavn, f.eks. fourthcoffee.com først. Hvis du allerede har en, fantastisk! Hvis ikke, kan du få mere at vide om, hvordan du [køber en fra en domæneregistrator](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

::: moniker range="o365-21vianet"

Din oprindelige mailadresse i Office 365, der drives af 21Vianet, omfatter partner.onmschina.cn, f.eks. tom@fourthcoffee.partner.onmschina.cn. Du kan ændre den til en mere brugervenlig adresse, f.eks. tom@fourthcoffee.cn. Du skal bruge dit eget domænenavn, f.eks. fourthcoffee.cn først. Hvis du allerede har en, fantastisk! Hvis ikke, kan du få mere at vide om, hvordan du [køber en fra en domæneregistrator](../get-help-with-domains/buy-a-domain-name.md).

::: moniker-end

Når du ændrer dit domænes mail, så den kommer til Microsoft 365, ved at opdatere dit domænes MX-post under konfigurationen, begynder ALLE mails, der sendes til domænet, at komme til Microsoft 365. Sørg for, at du har tilføjet brugere og oprettet postkasser i Microsoft 365 for alle, der har mail på dit domæne, FØR du ændrer MX-posten. Vil du ikke flytte mail for alle på dit domæne for at Microsoft 365? Du kan tage skridt til at [styre Microsoft 365 med blot nogle få mailadresser i stedet](../misc/pilot-microsoft-365-from-my-custom-domain.md).
  
## <a name="set-up-business-email-with-a-new-domain"></a>Konfigurer firmamail med et nyt domæne

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWyVVA?autoplay=false]

Køb et nyt domænenavn til din mailadresse, og konfigurer mailadresserne med Microsoft 365.

1. Køb et nyt domænenavn til din mailadresse ved at angive dine kontaktoplysninger for det nye domænenavn, vælge din betalingsmetode og derefter placere din ordre.
1. Rediger den første del af adressen (før @-tegnet), eller lad den være, som den er. 
1. Log af Microsoft 365, og log derefter på igen med din nye mailadresse. Medarbejdernes mailadresser opdateres med det nye domæne. 

## <a name="set-up-business-email-with-an-existing-domain"></a>Konfigurer firmamail med et eksisterende domæne

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWxApu?autoplay=false]

Brug et domænenavn, du allerede ejer, uanset om du bruger det til en webstedsadresse eller en mailadresse hos en anden udbyder.

1. Log på det websted, der er vært for dit domæne. Klik på en knap for at bekræfte automatisk eller opdatere domænet manuelt. 
1. Tilpas mailadressen, eller lad den være, som den er.
1. Log af Microsoft 365, og log derefter på igen med din nye mailadresse. Medarbejdernes mailadresser opdateres med det nye domæne.

## <a name="change-your-email-address-to-use-your-custom-domain-using-the-microsoft-365-admin-center"></a>Skift din mailadresse til at bruge dit brugerdefinerede domæne ved hjælp af Microsoft 365 Administration

Du skal være global administrator for at kunne udføre disse trin.

::: moniker range="o365-worldwide"

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank"> https://portal.partner.microsoftonline.cn</a>.

::: moniker-end

2. Gå til siden **SetupDomains** > .

3. På siden **Domæner** skal du vælge **Tilføj domæne**.

4. Følg trinnene for at bekræfte, at du ejer dit domæne. Du bliver guidet til at få alt konfigureret korrekt med dit domæne i Microsoft 365.

5. Gå til **BrugereAktive** >  brugere.

6. Vælg en bruger for at redigere brugerens brugernavn og ændre det til det domæne, du lige har tilføjet.

> [!NOTE]
> Hvis du ikke bruger en Exchange licens, kan du ikke bruge domænet til at sende eller modtage mails fra den Microsoft 365 lejer.
  
## <a name="related-content"></a>Relateret indhold

[Køb et brugerdefineret domæne ved hjælp af Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (artikel)\
[Administrer domæner](/admin) (linkside)\
[Ofte stillede spørgsmål om domæner](../setup/domains-faq.yml) (artikel)