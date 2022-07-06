---
title: Angiv en udløbsdato for mail, der er krypteret med Avanceret meddelelseskryptering i Microsoft Purview
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 10/8/2019
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Brug Avanceret meddelelseskryptering i Microsoft Purview til at udvide din mailsikkerhed ved at angive en udløbsdato for mails via en brugerdefineret brandet skabelon.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b93aad4f217f956561b686b1415c64456a4360db
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635145"
---
# <a name="set-an-expiration-date-for-email-encrypted-by-microsoft-purview-advanced-message-encryption"></a>Angiv en udløbsdato for mail, der er krypteret med Avanceret meddelelseskryptering i Microsoft Purview

Microsoft Purview Advanced Message Encryption er inkluderet i [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (prisfastsættelse for personale til nonprofitorganisationer), Office 365 Enterprise E5 (priser på personale til nonprofitorganisationer) og Office 365 Education A5. Microsoft 365 E5 Overholdelse SKU-tilføjelsesprogram til Microsoft 365 E3, Microsoft 365 E3 (prisfastsættelse for nonprofitmedarbejdere) eller tilføjelsesprogrammet Avanceret overholdelse i Office 365 SKU for Microsoft 365 E3, Microsoft 365 E3 (pris på personale til nonprofitorganisationer) eller Office 365 SKU'er.

Hvis din organisation har et abonnement, der ikke indeholder avanceret meddelelseskryptering fra Microsoft Purview, kan du købe det med tilføjelsesprogrammet Microsoft 365 E5 Overholdelse SKU til Microsoft 365 E3, Microsoft 365 E3 (prisfastsættelse for personale til nonprofitorganisationer), eller Avanceret overholdelse i Office 365 SKU-tilføjelsesprogram til Microsoft 365 E3, Microsoft 365 E3 (prisfastsættelse for nonprofit-medarbejdere) eller Office 365 SKU'er.

Du kan bruge meddelelsesudløb på mails, som dine brugere sender til eksterne modtagere, som bruger OME-portalen til at få adgang til krypterede mails. Du tvinger modtagere til at bruge OME-portalen til at få vist og besvare krypterede mails, der er sendt af din organisation, ved hjælp af en brugerdefineret brandet skabelon, der angiver en udløbsdato i PowerShell.

Når du som Office 365 global administrator anvender dit firmamærke til at tilpasse udseendet af organisationens mails, kan du også angive et udløb for disse mails. Med Avanceret meddelelseskryptering i Microsoft Purview kan du oprette flere skabeloner til krypterede mails, der stammer fra din organisation. Ved hjælp af en skabelon kan du styre, hvor længe modtagerne har adgang til mails, der sendes af dine brugere.

Når en slutbruger modtager mails, hvor der er angivet en udløbsdato, får brugeren vist udløbsdatoen i ombrydermailen. Hvis en bruger forsøger at åbne en udløbet mail, vises der en fejl på OME-portalen.

Du kan kun angive udløbsdatoer for mails til eksterne modtagere.

Med Avanceret meddelelseskryptering i Microsoft Purview anvender Office 365 ombryderen på mail, der passer til den regel for mailflowet, som du anvender skabelonen på, når du anvender den. Derudover kan du kun bruge udløb, hvis du bruger brugerdefineret branding.

## <a name="create-a-custom-branding-template-to-force-mail-expiration-by-using-powershell"></a>Opret en brugerdefineret brandingskabelon for at gennemtvinge mailudløb ved hjælp af PowerShell

1. [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) med en konto, der har globale administratortilladelser i din organisation.

2. Kør cmdlet'en New-OMEConfiguration.

    ```powershell
    New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
    ```

Hvor:

- `Identity` er navnet på den brugerdefinerede skabelon.

- `ExternalMailExpiryInDays` identificerer det antal dage, modtagerne kan beholde mails, før den udløber. Du kan bruge en hvilken som helst værdi mellem 1-730 dage.

## <a name="more-information-about-microsoft-purview-advanced-message-encryption"></a>Flere oplysninger om avanceret meddelelseskryptering i Microsoft Purview

- [Avanceret meddelelseskryptering](ome-advanced-message-encryption.md)

- [Tilbagekald mail, der er krypteret af Avanceret meddelelseskryptering i Microsoft Purview](revoke-ome-encrypted-mail.md)

- [Beskrivelse af meddelelsespolitik og overholdelsestjeneste](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)
