---
title: Microsoft 365 gruppenavngivningspolitik
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 6ceca4d3-cad1-4532-9f0f-d469dfbbb552
recommendations: false
description: Få mere at vide om, hvordan du opretter en navngivningspolitik for Microsoft 365 grupper.
ms.openlocfilehash: acc521dd5be1dcf630b4801eeb914c45e765e00f
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/17/2021
ms.locfileid: "63589710"
---
# <a name="microsoft-365-groups-naming-policy"></a>Microsoft 365 gruppenavngivningspolitik

Du kan bruge en politik for gruppenavngivning til at gennemtvinge en ensartet navngivningsstrategi for grupper, der er oprettet af brugerne i organisationen. En navngivningspolitik kan hjælpe dig og dine brugere med at identificere funktionen for gruppen, medlemskabet, det geografiske område eller den person, der har oprettet gruppen. Navngivningspolitikken kan også hjælpe med at kategorisere grupper i adressekartoteket. Du kan bruge politikken til at blokere brugen af bestemte ord i gruppenavne og aliasser.

Navngivningspolitikken anvendes på grupper, der er oprettet på tværs af alle gruppearbejdsbelastninger (f.eks. Outlook, Microsoft Teams, SharePoint, Planner, Yammer osv.). Den anvendes både på gruppenavnet og gruppealiasset. Den anvendes også, når en bruger opretter en gruppe, og når gruppenavnet, aliasset, beskrivelsen eller avataren redigeres for en eksisterende gruppe.

> [!TIP]
> En Microsoft 365 gruppenavngivningspolitik gælder kun for Microsoft 365 grupper. Den gælder ikke for distributionsgrupper, der er oprettet i Exchange Online. Hvis du vil oprette en navngivningspolitik for distributionsgrupper, skal du [se Opret en navngivningspolitik for en distributionsgruppe](/exchange/recipients-in-exchange-online/manage-distribution-groups/create-group-naming-policy).

Politikken for gruppenavngivning består af følgende funktioner:

- **Navngivningspolitik for præfiks-suffiks**: Du kan bruge præfikser eller suffikser til at definere navngivningskonventionen af grupper (f.eks.: "USMy\_ GroupEngineering\_"). Præfikserne/suffikserne kan enten være faste strenge eller brugerattributter som [Afdeling], der bliver erstattet baseret på den bruger, der opretter gruppen.

- **Bruger blokerede** ord: Du kan uploade et sæt blokerede ord, der er specifikke for din organisation, og som bliver blokeret i grupper, der er oprettet af brugere. (For eksempel: "Administrerende direktør, Løn, HR").

## <a name="licensing-requirements"></a>Licenskrav

Brug af navngivningspolitik for Azure AD til Microsoft 365 Grupper kræver, at du har, men ikke nødvendigvis tildeler en Azure Active Directory Premium P1-licens eller Azure AD Basic EDU-licens for hver entydige bruger (herunder gæster), som er medlem af en eller flere Microsoft 365-grupper.

Dette er også påkrævet for den administrator, der opretter navngivningspolitikken for grupper.

## <a name="prefix-suffix-naming-policy"></a>Prefix-Suffix navngivningspolitik

Præfikser og suffikser kan enten være faste strenge eller brugerattributter.

### <a name="fixed-strings"></a>Faste strenge

Du kan bruge korte strenge, som kan hjælpe dig med at skelne mellem grupper i GAL og venstre navigationslinje af gruppearbejdsbelastningerne. Nogle af de almindelige præfikser suffikser er nøgleord som 'GrpName\_', '\#Name', '\_Name'

### <a name="attributes"></a>Attributter

Du kan bruge attributter, der kan hjælpe med at identificere, hvem der oprettede gruppen, f.eks. [Afdeling], og hvor den blev oprettet fra f.eks. [Land].

Eksempler:

- Politik = "GRP [Gruppenavn] [Afdeling]"
- Brugerens afdeling = Teknik
- Oprettet gruppenavn = "GRP Min gruppe Teknik"

Understøttede Azure Active Directory (Azure AD) er [Department], [Company], [Office], [StateOrProvince], [CountryOrRegion] og [Title].

- Ikke-understøttede brugerattributter betragtes som faste strenge, f.eks. [postalCode].

- Udvidelsesattributter og brugerdefinerede attributter understøttes ikke.

Det anbefales, at du bruger attributter, der har udfyldt værdier for alle brugere i organisationen, og ikke bruger attributter, der har længere værdier.

### <a name="things-to-look-out-for"></a>Ting, du skal holde øje med

- Under oprettelse af politikken er den samlede strenglængde for præfikser og suffikser begrænset til 53 tegn.

- Præfikser og suffikser kan indeholde specialtegn, der understøttes i gruppenavn og gruppealias. Når præfikserne og suffikserne indeholder specialtegn, der ikke er tilladt i gruppealiasset, anvendes de kun på gruppenavnet. Så i dette tilfælde vil de præfikser og suffikser, der er anvendt på gruppenavnet være forskellige fra dem, der er anvendt på gruppealiasset.

  > [!NOTE]
  > Et punktum (.) eller en bindestreg (-) er tilladt et vilkårligt sted i gruppenavnet, undtagen i begyndelsen eller slutningen af navnet. Et understregningstegn (_) er tilladt et vilkårligt sted i gruppenavnet, herunder i begyndelsen eller slutningen af navnet.

- Hvis du bruger Yammer Office 365 forbundne grupper, skal du undgå at bruge følgende tegn i navngivningspolitikken: @ , \#, \[, \]. \<, and \> Hvis disse tegn er i navngivningspolitikken, Yammer brugere ikke kunne oprette grupper.

> [!Tip]
> - Brug korte strenge som suffiks.
> - Brug attributter med værdier.
> - Vær ikke for kreativ. Den samlede længde af navne har maksimalt 264 tegn.
> - Upload ord, der er blokeret i din organisation, for at begrænse brugen.

## <a name="custom-blocked-words"></a>Bruger blokerede ord

Du kan angive en kommasepareret liste over blokerede ord, der blokeres i gruppenavne og aliasser.

Der udføres ingen understrengsøgninger. specifikt kræves der et nøjagtigt match mellem det indtastede navn og de bruger blokerede ord for at udløse en fejl.

**Ting, du skal holde øje med**:

- Der kan ikkeføles store og små bogstaver i de blokerede ord.

- Når en bruger indtaster et blokeret ord, viser gruppeklienten en fejlmeddelelse med det blokerede ord.

- Der er ingen tegnbegrænsninger i de blokerede ord, der bruges.

- Der er en grænse på 5000 ord, der kan angives som blokerede ord.

## <a name="admin-override"></a>Tilsidesætte af administrator

Nogle administratorer er fritaget for disse politikker på tværs af alle gruppearbejdsbelastninger og slutpunkter, så de kan oprette grupper med disse blokerede ord og deres ønskede navngivningskonventioner. I det følgende vises listen over administratorroller, der er fritaget fra gruppen for navngivningspolitik.

- Global administrator

- Partnerniveau 1 Support

- Partnerniveau 2 Support

- Brugerkontoadministrator

## <a name="how-to-set-up-the-naming-policy"></a>Sådan konfigurerer du navngivningspolitikken

Sådan konfigureres en navngivningspolitik:

1. Klik [Azure Active Directory](https://aad.portal.azure.com) grupper under **Administrer** i **gruppen Gruppe**.
2. Under **Indstillinger** skal du klikke **på Navngivningspolitik**.
3. Vælg fanen **Politik for gruppenavngivning** .
4. Under **Aktuel politik skal** du vælge, om du vil kræve et præfiks eller suffiks eller begge, og markere de relevante afkrydsningsfelter.
5. Vælg mellem **Attribut og** **Streng** for hver linje, og angiv derefter attributten eller strengen.
6. Når du har tilføjet de præfikser og suffikser, du skal bruge, skal du klikke på **Gem**.

![Skærmbillede af politikindstillingerne for navngivning af grupper i Azure Active Directory.](../media/groups-naming-policy-azure.png)

## <a name="related-topics"></a>Relaterede emner

[Anbefalinger til planlægning af styring af samarbejde](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Opret din plan for styring af samarbejde](collaboration-governance-first.md)

[Azure Active Directory cmdlet'er til konfiguration af gruppeindstillinger](/azure/active-directory/enterprise-users/groups-settings-cmdlets)