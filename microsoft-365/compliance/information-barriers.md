---
title: Få mere at vide om informationsbarrierer
description: Få mere at vide om informationsbarrierer i Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, overensstemmelse
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.localizationpriority: ''
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 214a2614b6ca7381bbded39ff5f5143236f6c001
ms.sourcegitcommit: 570c3be37b6ab1d59a4988f7de9c9fb5ca38028f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/12/2022
ms.locfileid: "65363109"
---
# <a name="learn-about-information-barriers"></a>Få mere at vide om informationsbarrierer

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview Information Barriers (IB) er en overholdelsesløsning, der giver dig mulighed for at begrænse tovejskommunikation og samarbejde mellem grupper og brugere i Microsoft Teams, SharePoint Online og OneDrive for Business. IB bruges ofte i stærkt regulerede brancher og kan hjælpe med at undgå interessekonflikter og beskytte interne oplysninger mellem brugere og organisatoriske områder.

Når IB-politikker er på plads, kan brugere, der ikke skal kommunikere eller dele filer med andre specifikke brugere, ikke finde, vælge, chatte eller ringe til disse brugere. IB-politikker placerer automatisk kontroller for at registrere og forhindre uautoriseret kommunikation og samarbejde mellem definerede grupper og brugere. IB-politikker er uafhængige af [overholdelsesgrænser](/microsoft-365/compliance/set-up-compliance-boundaries) for eDiscovery-undersøgelser, der styrer placering af brugerindhold, som eDiscovery-ledere kan søge efter.

IB-politikker kan tillade eller forhindre kommunikation og samarbejde mellem grupper og brugere i følgende eksempelscenarier:

- Brugere i *Day Trader-gruppen* må ikke kommunikere eller dele filer med *marketingteamet*
- Økonomiafdelingen, der arbejder med fortrolige firmaoplysninger, må ikke kommunikere eller dele filer med visse grupper i organisationen
- Et internt team med faghemmeligt materiale må ikke ringe til eller chatte online med personer i visse grupper i organisationen
- Et forskningsteam bør kun ringe til eller chatte online med et produktudviklingsteam
- Et SharePoint websted for *Day Trader-gruppen* må ikke deles eller tilgås af nogen uden for *Day Trader-gruppen*

> [!IMPORTANT]
> Informationsbarrierer **understøtter kun** tovejskommunikations- og samarbejdsbegrænsninger. Et scenarie, hvor marketing kan kommunikere og samarbejde med Day Traders, men Day Traders ikke kan kommunikere og samarbejde med Marketing **, understøttes f.eks. ikke**.

## <a name="information-barriers-and-microsoft-teams"></a>Informationsbarrierer og -Microsoft Teams

I Microsoft Teams bestemmer og forhindrer IB-politikker følgende former for uautoriseret kommunikation og samarbejde:

- Søger efter en bruger
- Tilføjelse af et medlem til et team
- Start af en chatsession med en person
- Start af en gruppechat
- Inviterer en person til at deltage i et møde
- Deling af en skærm
- Afgivelse af et opkald
- Deling af en fil med en anden bruger
- Adgang til en fil via deling af et link

Hvis de brugere, der udfører disse aktiviteter i Microsoft Teams, er inkluderet i en IB-politik for at forhindre aktiviteten, kan de ikke fortsætte. Desuden kan alle, der er inkluderet i en IB-politik, potentielt blokeres fra at kommunikere med andre brugere i Microsoft Teams. Når personer, der påvirkes af IB-politikker, er en del af den samme team- eller gruppechat, kan de blive fjernet fra disse chatsessioner, og yderligere kommunikation med gruppen er muligvis ikke tilladt.

Se [informationsbarrierer i Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams) for at få flere oplysninger.

## <a name="information-barriers-and-sharepoint-and-onedrive"></a>Informationsbarrierer, SharePoint og OneDrive

I SharePoint Online og OneDrive registrerer og forhindrer IB-politikker følgende former for uautoriseret samarbejde:

- Tilføjelse af et medlem til et websted
- Adgang til webstedet eller indhold af en bruger
- Deling af websted eller indhold med en anden bruger
- Søger på et websted

For mere information, se [Informationsbarrierer i SharePoint](/sharepoint/information-barriers) og [Informationsbarrierer i OneDrive](/onedrive/information-barriers).

## <a name="information-barriers-and-exchange-online"></a>Informationsbarrierer og Exchange Online

IB-politikker er ikke tilgængelige til at begrænse kommunikation og samarbejde mellem grupper og brugere i mails. IB-politikker er baseret på [Exchange Online politikker for adressekartoteker.](/exchange/address-books/address-book-policies/address-book-policies) ABPs gør det muligt for organisationer praktisk talt at tildele brugere til bestemte grupper for at kunne levere tilpassede visninger af organisationens globale adressekartotek (GAL). Når der oprettes IB-politikker, oprettes ABP'er for politikkerne automatisk. Efterhånden som IB-politikker tilføjes i din organisation, ændres strukturen og funktionsmåden for din globale adresseliste for at overholde IB-politikker.

Før du definerer og anvender politikker for IB, skal du fjerne alle eksisterende Exchange politikker for adressekartoteker i din organisation. IB-politikker er baseret på politikker for adressekartoteker, og eksisterende ABP-politikker er ikke kompatible med de ABP'er, der er oprettet af IB. Hvis du vil fjerne dine eksisterende politikker for adressekartoteker, skal du se [Fjern en adressekartotekspolitik i Exchange Online](/exchange/address-books/address-book-policies/remove-an-address-book-policy). Når IB-politikker er aktiveret, og hvis du har aktiveret hierarkisk adressekartotek, kan alle brugere, der ikke er inkluderet i et IB-segment, se det [hierarkiske adressekartotek](/exchange/address-books/hierarchical-address-books/hierarchical-address-books) i Exchange online.

Det er kun Exchange Online installationer, der understøttes i øjeblikket for IB-politikker. Hvis din organisation har brug for at definere og styre mailkommunikation, kan du overveje at bruge [Exchange regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules).

## <a name="ready-to-get-started"></a>Er du klar til at komme i gang?

- [Kom i gang med informationsbarrierer](information-barriers-policies.md)
- [Administrer politikker for informationsbarrierer](information-barriers-edit-segments-policies.md)
- [Se de attributter, der kan bruges til politikker for informationsbarrierer](information-barriers-attributes.md)
