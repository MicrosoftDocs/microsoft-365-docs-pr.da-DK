---
title: Lær om informationsbarrierer i Microsoft 365
description: Brug informationsbarrierer til at sikre overholdelse af kommunikationsreglerne Microsoft Teams i din organisation.
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
ms.openlocfilehash: fc3d961b8707ba07febd95022580091618086d7f
ms.sourcegitcommit: 7e59802f251da96ec639fb09534aa96acf5d6ce7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/18/2021
ms.locfileid: "63589134"
---
# <a name="learn-about-information-barriers-in-microsoft-365"></a>Lær om informationsbarrierer i Microsoft 365

Microsofts skytjenester indeholder effektive kommunikations- og samarbejdsfunktioner. Men antag, at du vil begrænse kommunikationen og samarbejdet mellem to grupper for at undgå, at der opstår en i konflikt med hinanden i din organisation. Eller du vil måske begrænse kommunikationen og samarbejdet mellem bestemte personer i din organisation for at beskytte interne oplysninger. Microsoft 365 muligt at kommunikere og samarbejde på tværs af grupper og organisationer, så er der en metode til at begrænse kommunikation og samarbejde mellem bestemte grupper af brugere, når det er nødvendigt? Med informationsbarrierer kan du!

Microsoft Teams, SharePoint Online og OneDrive for Business understøtter informationsbarrierer. Hvis dit [abonnement omfatter](#required-licenses-and-permissions) informationsbarrierer, kan en overholdelsesadministrator eller en informationsbarriereadministrator definere politikker, der tillader eller forhindrer kommunikation mellem grupper af brugere Microsoft Teams. Politikker for informationsbarrierer kan bruges i situationer som disse:

- Brugeren i dag-gruppen bør ikke kommunikere eller dele filer med marketingteamet
- Økonomimedarbejdere, der arbejder på fortrolige firmaoplysninger, bør ikke kommunikere eller dele filer med visse grupper inden for organisationen
- Et internt team med handelshemmelighedsmateriale bør ikke ringe til eller chatte online med personer i visse grupper inden for organisationen
- Et forskningsteam bør kun ringe til eller chatte online med et produktudviklingsteam
- Et websted til dagsgrupper bør ikke deles eller tilgås af alle uden for dagsgruppen

> [!IMPORTANT]
> Informationsbarrierer * **understøtter** kun_ tovejsbegrænsninger. Begrænsninger på én måde, f.eks. marketing, kan kommunikere og samarbejde med dagsforhandlere, men dagsforhandlere kan ikke kommunikere og samarbejde med marketing _*_understøttes ikke_**.

I alle disse eksempelscenarier (og mere) kan politikker for informationsbarrierer defineres for at forhindre eller tillade kommunikation og samarbejde i Microsoft Teams, SharePoint Online og OneDrive. Sådanne politikker kan forhindre personer i at ringe eller chatte med dem, de ikke bør, eller gøre det muligt for folk kun at kommunikere med bestemte grupper Microsoft Teams. Når informationsbarrierepolitikker er gældende, når brugere, der er omfattet af disse politikker, forsøger at kommunikere og samarbejde med andre i Microsoft Teams,SharePoint Online- eller OneDrive-kontroller, udføres der for at forhindre (eller tillade) kommunikation og samarbejde (som defineret af informationsbarrierepolitikker).

Du kan få mere at vide om brugeroplevelsen med informationsbarrierer her:

- [Informationsbarrierer i Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Informationsbarrierer i SharePoint Online](/sharepoint/information-barriers)
- [Informationsbarrierer i OneDrive](/onedrive/information-barriers)

> [!IMPORTANT]
> Informationsbarrierer gælder i øjeblikket ikke for mailkommunikation. Informationsbarrierer er desuden uafhængige af [overholdelsesgrænserne](set-up-compliance-boundaries.md).<p> Før du definerer og anvender politikker for informationsbarrierer, skal du sikre dig, at din [organisation ikke Exchange politikker for adressekartoteket](/exchange/address-books/address-book-policies/address-book-policies) i kraft. (Informationsbarrierer er baseret på adressekartotekspolitikker).

## <a name="what-happens-with-information-barriers"></a>Hvad sker der med informationsbarrierer?

Når politikker for informationsbarrierer er på plads, vil personer, der ikke skal kommunikere eller dele filer med andre bestemte brugere, ikke kunne finde, vælge, chatte eller ringe til disse brugere. Med informationsbarrierer er der kontroller på plads for at forhindre uautoriseret kommunikation og samarbejde.

Informationsbarrierer gælder for Microsoft Teams (chat og kanaler), SharePoint Online og OneDrive. In Microsoft Teams, information barrier policies determine and prevent the following kinds of uautoriseret communications:

- Søge efter en bruger
- Føje et medlem til et team
- Starte en chatsession med en person
- Starte en gruppechat
- Invitere nogen til at deltage i et møde
- Dele en skærm
- Foretage et opkald
- Dele en fil med en anden bruger
- Adgang til fil via delingslink

Hvis de involverede personer er en del af en informationsbarrierepolitik for at forhindre aktiviteten, vil de ikke kunne fortsætte. Desuden kan enhver, som er en informationsbarrierepolitik, blive blokeret fra at kommunikere med andre Microsoft Teams. Når personer, der påvirkes af oplysningsbarrierepolitikker, er en del af det samme team- eller gruppechat, kan de blive fjernet fra disse chatsessioner, og yderligere kommunikation med gruppen tillades muligvis ikke.

Du kan få mere at vide om brugeroplevelsen med informationsbarrierer [ved at se informationsbarrierer Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams).

I SharePoint Online og OneDrive bruges politikker for informationsbarrierer til at fastlægge og forhindre følgende typer uautoriserede samarbejder:

- Føje et medlem til et websted
- Få adgang til et websted eller indhold af en bruger
- Dele websted eller indhold med en anden bruger
- Søgning på et websted

Du kan få mere at vide om brugeroplevelsen med informationsbarrierer ved at [se informationsbarrierer SharePoint Online](/sharepoint/information-barriers)

## <a name="required-licenses-and-permissions"></a>Påkrævede licenser og tilladelser

Før du går i gang med insider-risikostyring, skal du [bekræfte Microsoft 365 dit abonnement](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) og eventuelle tilføjelser. For at få adgang til og bruge informationsbarrierer skal din organisation have et af følgende abonnementer eller tilføjelser:

- Microsoft 365 E5/A5-abonnement (betalt version eller prøveversion)
- Office 365 E5/A5/A3/A1-abonnement (betalt version eller prøveversion)
- Avanceret overholdelse i Office 365 tilføjelsesprogrammet (ikke længere tilgængeligt for nye abonnementer)
- Microsoft 365 E3/A3/A1 +Microsoft 365 E5/A5 Compliance-tilføjelsesprogrammet
- Microsoft 365 E3/A3/A1 -abonnement + Microsoft 365 E5/A5 Insider Risk Management-tilføjelsesprogrammet

Du kan finde flere oplysninger [Microsoft 365 vejledning i licenser til sikkerhed og & overholdelse af regler og standarder](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

Hvis [du vil definere eller redigere politikker for informationsbarrierer](information-barriers-policies.md), skal du have tildelt en af følgende roller:

- Microsoft 365 global administrator
- Office 365 global administrator
- Overholdelsesadministrator
- Administration af IB-overholdelse

(Du kan få mere at vide om roller og tilladelser under [Tilladelser i Office 365 Security & Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md)).

Du skal kende PowerShell-cmdlet'er for at definere, validere eller redigere politikker for informationsbarrierer. Selvom vi giver dig flere eksempler på PowerShell-cmdlet'er i sådan gør [du-artiklen](information-barriers-policies.md), skal du kende andre oplysninger, f.eks. parametre, til din organisation.

## <a name="next-steps"></a>Næste trin

- [Få mere at vide om informationsbarrierer i Microsoft Teams](/MicrosoftTeams/information-barriers-in-teams)
- [Få mere at vide om informationsbarrierer SharePoint Online](/sharepoint/information-barriers)
- [Få mere at vide om informationsbarrierer OneDrive](/onedrive/information-barriers)
- [Se de attributter, der kan bruges til politikker for informationsbarrierer](information-barriers-attributes.md)
- [Definer politikker for informationsbarrierer](information-barriers-policies.md)
- [Rediger (eller fjern) politikker for informationsbarrierer](information-barriers-edit-segments-policies.md)
