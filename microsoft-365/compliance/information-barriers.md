---
title: Få mere at vide om informationsbarrierer
description: Få mere at vide om informationsbarrierer i Microsoft Purview.
keywords: Microsoft 365, Microsoft Purview, overholdelse af angivne standarder, informationsbarrierer
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
ms.openlocfilehash: 72a53580222b315f86fd397e391b026937b8035b
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/09/2022
ms.locfileid: "65287172"
---
# <a name="learn-about-information-barriers"></a>Få mere at vide om informationsbarrierer

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsofts cloudtjenester omfatter effektive kommunikations- og samarbejdsfunktioner. Lad os antage, at du vil begrænse kommunikationen og samarbejdet mellem to grupper for at undgå, at der opstår en interessekonflikt i din organisation. Eller måske vil du begrænse kommunikationen og samarbejdet mellem bestemte personer i din organisation for at beskytte interne oplysninger. Microsoft 365 muliggør kommunikation og samarbejde på tværs af grupper og organisationer, så er det muligt at begrænse kommunikation og samarbejde mellem bestemte grupper af brugere, når det er nødvendigt? Med Microsoft Purview Information Barriers (IB) kan du!

Microsoft Teams, SharePoint Online og OneDrive for Business understøtter informationsbarrierer. Under forudsætning af at dit [abonnement](#required-licenses-and-permissions) indeholder informationsbarrierer, kan en overholdelsesadministrator eller administrator af informationsbarrierer definere politikker, der tillader eller forhindrer kommunikation mellem grupper af brugere i Microsoft Teams. Politikker for informationsbarrierer kan bruges til situationer som disse:

- Brugeren i dag erhvervsdrivende gruppe bør ikke kommunikere eller dele filer med markedsføring team
- Økonomiafdelingen, der arbejder med fortrolige virksomhedsoplysninger, må ikke kommunikere eller dele filer med bestemte grupper i organisationen
- Et internt team med faghemmeligt materiale må ikke ringe til eller chatte online med personer i visse grupper i organisationen
- Et forskningsteam bør kun ringe til eller chatte online med et produktudviklingsteam
- Et websted for dag erhvervsdrivende gruppe bør ikke deles eller tilgås af nogen uden for den dag erhvervsdrivende gruppe

> [!IMPORTANT]
> Informationsbarrierer ***understøtter kun** _ tovejsbegrænsninger. Envejsbegrænsninger, f.eks. marketing, kan kommunikere og samarbejde med daghandlere, men daghandlere kan ikke kommunikere og samarbejde med marketing _*_understøttes ikke_**.

I alle disse eksempelscenarier (og meget mere) kan der defineres politikker for informationsbarrierer for at forhindre eller tillade kommunikation og samarbejde i Microsoft Teams, SharePoint Online og OneDrive. Sådanne politikker kan forhindre personer i at ringe til eller chatte med dem, de ikke burde, eller give andre mulighed for kun at kommunikere med bestemte grupper i Microsoft Teams. Med politikker for informationsbarrierer i kraft, når brugere, der er omfattet af disse politikker, forsøger at kommunikere og samarbejde med andre i Microsoft Teams, udføres der SharePoint online- eller OneDrive kontrol for at forhindre (eller tillade) kommunikation og samarbejde (som defineret i politikker for informationsbarrierer).

Hvis du vil vide mere om brugeroplevelsen med informationsbarrierer, kan du se:

- [Informationsbarrierer i Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Informationsbarrierer i SharePoint Online](/sharepoint/information-barriers)
- [Informationsbarrierer i OneDrive](/onedrive/information-barriers)

> [!IMPORTANT]
> I øjeblikket gælder informationsbarrierer ikke for e-mailkommunikation. Informationsbarrierer er desuden uafhængige af [overholdelsesgrænser](set-up-compliance-boundaries.md).<p> Før du definerer og anvender politikker for informationsbarrierer, skal du sørge for, at organisationen ikke har [Exchange politikker for adressekartoteker](/exchange/address-books/address-book-policies/address-book-policies) i kraft. (Informationsbarrierer er baseret på politikker for adressekartoteker).

## <a name="what-happens-with-information-barriers"></a>Hvad sker der med informationsbarrierer?

Når politikker for informationsbarrierer er på plads, kan personer, der ikke må kommunikere eller dele filer med andre specifikke brugere, ikke finde, vælge, chatte eller ringe til disse brugere. Med informationsbarrierer er der indført kontroller for at forhindre uautoriseret kommunikation og samarbejde.

Informationsbarrierer gælder for Microsoft Teams (chats og kanaler), SharePoint Online og OneDrive. I Microsoft Teams fastlægger og forhindrer politikker for informationsbarrierer følgende former for uautoriseret kommunikation:

- Søger efter en bruger
- Tilføjelse af et medlem til et team
- Start af en chatsession med en person
- Start af en gruppechat
- Inviterer en person til at deltage i et møde
- Deling af en skærm
- Afgivelse af et opkald
- Deling af en fil med en anden bruger
- Adgang til fil via delingslink

Hvis de involverede personer indgår i en informationsbarrierepolitik for at forhindre aktiviteten, vil de ikke kunne fortsætte. Derudover kan alle, der indgår i en informationspolitik, muligvis blokeres fra at kommunikere med andre i Microsoft Teams. Når personer, der påvirkes af politikker for informationsbarrierer, er en del af det samme team eller gruppechat, kan de blive fjernet fra disse chatsessioner, og yderligere kommunikation med gruppen er muligvis ikke tilladt.

Hvis du vil vide mere om brugeroplevelsen med informationsbarrierer, kan [du se informationsbarrierer i Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams).

I SharePoint Online og OneDrive bestemmer og forhindrer politikker for informationsbarrierer følgende former for uautoriseret samarbejde:

- Tilføjelse af et medlem til et websted
- Adgang til webstedet eller indhold af en bruger
- Deling af websted eller indhold med en anden bruger
- Søger på et websted

Hvis du vil vide mere om brugeroplevelsen med informationsbarrierer, kan [du se informationsbarrierer i SharePoint Online](/sharepoint/information-barriers)

## <a name="required-licenses-and-permissions"></a>Påkrævede licenser og tilladelser

Før du kommer i gang med IB, skal du bekræfte dit [Microsoft 365 abonnement](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) og eventuelle tilføjelsesprogrammer. Hvis du vil have adgang til og bruge IB, skal din organisation have et af følgende abonnementer eller tilføjelsesprogrammer:

- Microsoft 365 E5/A5-abonnement (betalt version eller prøveversion)
- Office 365 E5/A5/A3/A1-abonnement (betalt version eller prøveversion)
- Avanceret overholdelse i Office 365 tilføjelsesprogram (ikke længere tilgængeligt for nye abonnementer)
- Microsoft 365 E3/A3/A1-abonnement + tilføjelsesprogrammet Microsoft 365 E5/A5 Overholdelse
- Microsoft 365 E3/A3/A1-abonnement + tilføjelsesprogrammet Microsoft 365 E5/A5 Insider Risk Management

Du kan finde flere oplysninger [under Microsoft 365 licensvejledning til sikkerheds- & overholdelse af angivne standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

Hvis du vil [definere eller redigere politikker for informationsbarrierer](information-barriers-policies.md), skal du have tildelt en af følgende roller:

- Microsoft 365 global administrator
- Office 365 global administrator
- Overholdelsesadministrator
- Administration af IB-overholdelse

Du kan få mere at vide om roller og tilladelser [under Tilladelser i Office 365 Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

Du skal have kendskab til PowerShell-cmdlet'er for at kunne definere, validere eller redigere politikker for informationsbarrierer. Selvom vi indeholder flere eksempler på PowerShell-cmdlet'er i [artiklen Vejledning](information-barriers-policies.md), skal du kende andre oplysninger, f.eks. parametre, for din organisation.

## <a name="next-steps"></a>Næste trin

- [Få mere at vide om informationsbarrierer i Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Få mere at vide om informationsbarrierer i SharePoint Online](/sharepoint/information-barriers)
- [Få mere at vide om informationsbarrierer i OneDrive](/onedrive/information-barriers)
- [Se de attributter, der kan bruges til politikker for informationsbarrierer](information-barriers-attributes.md)
- [Definer politikker for informationsbarrierer](information-barriers-policies.md)
- [Rediger (eller fjern) politikker for informationsbarrierer](information-barriers-edit-segments-policies.md)
