---
title: Angiv en udløbsdato for mails, der er krypteret med Avanceret kryptering af meddelelser i Office 365
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
description: Brug Avanceret kryptering af meddelelser i Office 365 til at udvide din mailsikkerhed ved at angive en udløbsdato for mails via en brugerdefineret brandet skabelon.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1213ecf48ee9bd2e04accdd13aaf3ecd74d3faba
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587522"
---
# <a name="set-an-expiration-date-for-email-encrypted-by-office-365-advanced-message-encryption"></a>Angiv en udløbsdato for mails, der er krypteret med Avanceret kryptering af meddelelser i Office 365

Avanceret kryptering af meddelelser i Office 365 er inkluderet i [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (nonprofitmedarbejderpriser) Office 365 Enterprise E5 (nonprofitorganisationers priser for personale) og Office 365 Education A5. Hvis din organisation har et abonnement, der ikke Avanceret kryptering af meddelelser i Office 365, kan du købe det med Microsoft 365 E5 Overholdelse SKU-tilføjelsesprogrammet til Microsoft 365 E3, Microsoft 365 E3  (Nonprofit Staff Pricing) eller Avanceret overholdelse i Office 365 SKU-tilføjelsesprogrammet til Microsoft 365 E3, Microsoft 365 E3 (nonprofitorganisationers personalepriser) eller Office 365 SKU'er.

Du kan bruge udløb af meddelelser på mails, som dine brugere sender til eksterne modtagere, der bruger OME-portalen til at få adgang til krypterede mails. Du tvinger modtagerne til at bruge OME-portalen til at få vist og svare på krypterede mails, der er sendt af din organisation, ved hjælp af en brugerdefineret brandet skabelon, der angiver en udløbsdato i Windows PowerShell.

Som global Office 365 administrator kan du, når du anvender dit firmas brand for at tilpasse udseendet af din organisations mails, også angive en udløb for disse mails. Med Avanceret kryptering af meddelelser i Office 365 kan du oprette flere skabeloner til krypterede mails, der stammer fra din organisation. Ved hjælp af en skabelon kan du styre, hvor længe modtagerne har adgang til mails, der sendes af dine brugere.

Når en slutbruger modtager en mail, der har angivet en udløbsdato, får brugeren vist udløbsdatoen i wrappermailen. Hvis en bruger forsøger at åbne en udløbet mail, vises der en fejl i OME-portalen.

Du kan kun angive udløbsdatoer for mails til eksterne modtagere.

Når Avanceret kryptering af meddelelser i Office 365 bruger brugerdefineret branding, anvender Office 365 wrapperen på mails, der passer til den regel for mailflow, du anvender skabelonen på. Desuden kan du kun bruge udløb, hvis du bruger brugerdefineret branding.

## <a name="create-a-custom-branding-template-to-force-mail-expiration-by-using-powershell"></a>Opret en brugerdefineret brandingskabelon for at gennemtvinge udløb af mails ved hjælp af PowerShell

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) med en konto, der har globale administratorrettigheder i organisationen.

2. Kør New-OMEConfiguration cmdlet'en.

    ```powershell
    New-OMEConfiguration -Identity "Expire in 7 days" -ExternalMailExpiryInDays 7
    ```

Hvor:

- `Identity` er navnet på den brugerdefinerede skabelon.

- `ExternalMailExpiryInDays` identificerer det antal dage, som modtagerne kan beholde mails, før de udløber. Du kan bruge en hvilken som helst værdi mellem 1-730 dage.

## <a name="more-information-about-office-365-advanced-message-encryption"></a>Flere oplysninger om Avanceret kryptering af meddelelser i Office 365

- [Avanceret kryptering af meddelelser i Office 365](ome-advanced-message-encryption.md)

- [Tilbagekald mail, der er krypteret med Avanceret kryptering af meddelelser i Office 365](revoke-ome-encrypted-mail.md)

- [Beskrivelse af meddelelsespolitik og overholdelsestjeneste](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)