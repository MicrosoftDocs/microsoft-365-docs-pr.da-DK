---
title: Tilbagekald mail, der er krypteret med avanceret meddelelseskryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 03/04/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Som administrator og som meddelelsesafsender kan du tilbagekalde visse mails, der er blevet krypteret med Avanceret kryptering af meddelelser i Office 365.
ms.openlocfilehash: bf793dce23c91e8b45f96114e6c4a56c866adc32
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/16/2022
ms.locfileid: "63587510"
---
# <a name="revoke-email-encrypted-by-advanced-message-encryption"></a>Tilbagekald mail, der er krypteret med avanceret meddelelseskryptering

Tilbagekaldte mails tilbydes som en del af Avanceret kryptering af meddelelser i Office 365. Avanceret kryptering af meddelelser i Office 365 er inkluderet i [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (nonprofitmedarbejderpriser) Office 365 Enterprise E5 (nonprofitorganisationers priser for personale) og Office 365 Education A5. Hvis din organisation har et abonnement, der ikke Avanceret kryptering af meddelelser i Office 365, kan du købe det med Microsoft 365 E5 Overholdelse SKU-tilføjelsesprogrammet til Microsoft 365 E3, Microsoft 365 E3  (Nonprofit Staff Pricing) eller Avanceret overholdelse i Office 365 SKU-tilføjelsesprogrammet til Microsoft 365 E3, Microsoft 365 E3 (nonprofitorganisationers personalepriser) eller Office 365 SKU'er.

Denne artikel er en del af en større række artikler om [Office 365-meddelelseskryptering](ome.md).

Hvis en meddelelse blev krypteret ved hjælp af Avanceret kryptering af meddelelser i Office 365, og du er Microsoft 365-administrator, eller du er afsenderen af meddelelsen, kan du tilbagekalde meddelelsen under visse omstændigheder. Administratorer tilbagekalder meddelelser ved hjælp af PowerShell. Som afsender tilbagekalder du en meddelelse, du har sendt direkte fra Outlook på internettet. I denne artikel beskrives de omstændigheder, hvorunder det er muligt at blive tilbagekaldt, og hvordan du kan gøre det.

> [!NOTE]
> For at sikre at muligheden for at spore og tilbagekalde OME-meddelelser er tilgængelig, skal du tilføje en brugerdefineret brandingskabelon. Se [Føj din organisations brand til dine krypterede meddelelser](add-your-organization-brand-to-encrypted-messages.md)
  
## <a name="encrypted-emails-that-you-can-revoke"></a>Krypterede mails, som du kan tilbagekalde

Administratorer og meddelelsesafsendere kan tilbagekalde krypterede mails, hvis modtageren har modtaget en linkbaseret, brandet krypteret mail. Hvis modtageren har modtaget en indbygget oplevelse i en understøttet Outlook klient, kan du ikke tilbagekalde meddelelsen.

Om en modtager modtager en linkbaseret oplevelse eller en indbygget oplevelse afhænger af modtagerens identitetstype: Office 365- og Microsoft-kontomodtagere (f.eks. outlook.com-brugere) får en indbygget oplevelse i understøttede Outlook-klienter. Alle andre modtagertyper, f.eks. Gmail- og Yahoo-modtagere, får en linkbaseret oplevelse.

Administratorer og meddelelsesafsendere kan tilbagekalde meddelelser, der er krypteret med kryptering, der anvendes direkte Outlook på internettet. Meddelelser, der er krypteret med indstillingen Kryptér kun.

:::image type="content" source="../media/adhocencryptionrevoke.png" alt-text="Skærmbillede, der viser indstillingen Kryptér kun Outlook på internettet.":::

## <a name="recipient-experience-for-revoked-encrypted-emails"></a>Modtageroplevelse for tilbagekaldte krypterede mails

Når en mail er blevet tilbagekaldt, modtager modtageren en fejl, når vedkommende får adgang til den krypterede mail via Office 365-meddelelseskryptering-portalen: "Meddelelsen er blevet tilbagekaldt af afsenderen".

![Skærmbillede, der viser en tilbagekaldt krypteret mail.](../media/revoked-encrypted-email.png)

## <a name="how-to-revoke-an-encrypted-message-that-you-sent"></a>Sådan tilbagekalder du en krypteret meddelelse, du har sendt

Du kan tilbagekalde en mail, du har sendt til en enkelt modtager, som bruger en social konto, f.eks. gmail.com eller yahoo.com. Med andre ord kan du tilbagekalde en mail, der er sendt til en enkelt modtager, som har modtaget den linkbaserede oplevelse.

Du kan ikke tilbagekalde en mail, du har sendt til en modtager, der bruger en arbejds- eller skolekonto, fra Office 365 eller Microsoft 365 eller en bruger, der bruger en Microsoft-konto, f.eks. en outlook.com-konto. 

Hvis du vil tilbagekalde en krypteret meddelelse, du har sendt, skal du udføre disse trin

1. Find Outlook på internettet meddelelse **, du vil** tilbagekalde, i mappen Sendt.

   Hvis mailen kan tilbagekaldes, får du vist linket "Fjern ekstern adgang" øverst i meddelelsen.

    :::image type="content" source="../media/infoprotect-email-encryption/adhocencryptionrevokesentmsg.png" alt-text="Skærmbillede, der viser krypterede mails, som du vil tilbagekalde Outlook på internettet.":::

2. Klik **på Fjern ekstern adgang** for at tilbagekalde meddelelsen.

   Meddelelsen viser, at dens status er tilbagekaldt.

   :::image type="content" source="../media/adhocencryptionrevokedmsg.png" alt-text="Skærmbillede, der viser tilbagekaldte krypterede meddelelser Outlook på internettet.":::

## <a name="how-to-revoke-an-encrypted-message-as-an-administrator"></a>Sådan tilbagekaldes en krypteret meddelelse som administrator

Microsoft 365 disse generelle trin for at tilbagekalde en berettiget krypteret mail:

- Få mailens Meddelelses-id.
- Kontrollér, at du kan tilbagekalde meddelelsen.
- Tilbagekald mailen.

### <a name="step-1-obtain-the-message-id-of-the-email"></a>Trin 1. Hent meddelelses-id'et for mailen

Før du kan tilbagekalde en krypteret mail, skal du indsamle mailens meddelelses-id. Meddelelses-id'et har normalt formatet:

`<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`  

Du kan finde meddelelses-id'et for den mail, du vil tilbagekalde, på flere måder. I dette afsnit beskrives et par muligheder, men du kan bruge en hvilken som helst metode, der indeholder id'et.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-trace-in-the-security-amp-compliance-center"></a>Du kan identificere meddelelses-id'et for den mail, du vil tilbagekalde, ved hjælp af Meddelelsessporing i Security &amp; Compliance Center

1. Søg efter mailen efter afsender eller modtager ved hjælp [af Ny meddelelsessporing i Security & Compliance Center](https://blogs.technet.microsoft.com/exchange/2018/05/02/new-message-trace-in-office-365-security-compliance-center/).

2. Når du har fundet mailen, skal du vælge den for at få vist **detaljeruden Meddelelsessporing** . Udvid **Flere oplysninger for** at finde Meddelelses-id'et.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-office-message-encryption-reports-in-the-security-amp-compliance-center"></a>Sådan identificerer du meddelelses-id'et for den mail, du vil tilbagekalde, ved Office rapporter om Office i Security &amp; Compliance Center

1. I Security Compliance &amp; Center skal du gå til rapporten **om meddelelseskryptering**. Du kan finde flere oplysninger om denne rapport [under Få vist mailsikkerhedsrapporter i Security &amp; Compliance Center](../security/office-365-security/view-email-security-reports.md).

2. Vælg tabellen **Vis detaljer** , og identificer den meddelelse, du vil tilbagekalde.

3. Dobbeltklik på meddelelsen for at få vist oplysninger, der indeholder meddelelses-id'et.

### <a name="step-2-verify-that-the-mail-is-revocable"></a>Trin 2. Kontrollér, at mailen kan tilbagekaldes

Hvis du vil kontrollere, om du kan tilbagekalde en meddelelse, skal du kontrollere, om feltet Status for tilbagekaldelse er synligt i krypteringsrapporten i tabellen Detaljer i Security  &amp; Compliance Center.

Hvis du vil kontrollere, om du kan tilbagekalde en bestemt mail ved hjælp Windows PowerShell, skal du udføre disse trin.

1. Du kan bruge en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, til at starte en Windows PowerShell-session og oprette forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Get-OMEMessageStatus følgende:

     ```powershell
     Get-OMEMessageStatus -MessageId "<message id>" | ft -a  Subject, IsRevocable
     ```

   Denne kommando returnerer meddelelsens emne, og om meddelelsen kan tilbagekaldes. For eksempel

     ```console
     Subject        IsRevocable
     -------        -----------
     "Test message" True
     ```

### <a name="step-3-revoke-the-mail"></a>Trin 3. Tilbagekald mailen

Når du kender meddelelses-id'et for den mail, du vil tilbagekalde, og du har bekræftet, at meddelelsen kan tilbagekaldes, kan du tilbagekalde mailen ved hjælp af Security &amp; Compliance Center eller Windows PowerShell.

Sådan tilbagekalder du meddelelsen ved hjælp af Security &amp; Compliance Center

1. Ved hjælp af en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, skal du oprette forbindelse til Security & Compliance Center.

2. Vælg **Tilbagekald meddelelse** i **tabellen Detaljer** for meddelelsen i **rapporten** Kryptering.

Hvis du vil tilbagekalde en mail ved Windows PowerShell, skal du bruge Set-OMEMessageRevocation cmdlet'en.

1. Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, Forbind [at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-OMEMessageRevocation følgende:

    ```powershell
    Set-OMEMessageRevocation -Revoke $true -MessageId "<messageId>"
    ```

3. For at kontrollere om mailen blev tilbagekaldt, skal du køre Get-OMEMessageStatus cmdlet'en på følgende måde:

    ```powershell
    Get-OMEMessageStatus -MessageId "<messageId>" | ft -a  Subject, Revoked
    ```

    Hvis tilbagekaldelsen blev gennemført, returnerer cmdlet'en følgende resultat:  

     ```console
     Revoked: True
     ```

## <a name="more-information-about-office-365-advanced-message-encryption"></a>Flere oplysninger om Avanceret kryptering af meddelelser i Office 365

- [Avanceret kryptering af meddelelser i Office 365](ome-advanced-message-encryption.md)

- [Avanceret kryptering af meddelelser i Office 365 – udløb af mail](ome-advanced-expiration.md)

- [Beskrivelse af meddelelsespolitik og overholdelsestjeneste](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)