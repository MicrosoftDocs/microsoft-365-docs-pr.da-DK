---
title: Tilbagekald mail, der er krypteret af avanceret meddelelseskryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 05/02/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Som administrator og som afsender af en meddelelse kan du tilbagekalde visse mails, der er krypteret med avanceret meddelelseskryptering i Microsoft Purview.
ms.openlocfilehash: 79d09c13755c0c73e4d68598e83ac41344b9281a
ms.sourcegitcommit: 7e0094ddff54bcbe5d691dba58d4c4fb86f8b1a9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/04/2022
ms.locfileid: "65187937"
---
# <a name="revoke-email-encrypted-by-advanced-message-encryption"></a>Tilbagekald mail, der er krypteret af avanceret meddelelseskryptering

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Tilbagekaldelse af mail tilbydes som en del af avanceret meddelelseskryptering i Microsoft Purview. Microsoft Purview Advanced Message Encryption er inkluderet i [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (prisfastsættelse for personale til nonprofitorganisationer), Office 365 Enterprise E5 (priser på personale til nonprofitorganisationer) og Office 365 Education A5. Hvis du vil bruge funktionerne til tilbagekaldelse og udløb af avanceret meddelelseskryptering, skal du aktivere indstillingen **Premium Kryptering i Office 365** i din E5-licens.

Hvis din organisation har et abonnement, der ikke indeholder avanceret meddelelseskryptering fra Microsoft Purview, kan du købe det med tilføjelsesprogrammet Microsoft 365 E5 Overholdelse SKU til Microsoft 365 E3, Microsoft 365 E3 (prisfastsættelse for personale til nonprofitorganisationer), eller Avanceret overholdelse i Office 365 SKU-tilføjelsesprogram til Microsoft 365 E3, Microsoft 365 E3 (prisfastsættelse for nonprofit-medarbejdere) eller Office 365 SKU'er.

Denne artikel er en del af en større serie af artikler om [Office 365 meddelelseskryptering](ome.md).

Hvis en meddelelse blev krypteret ved hjælp af Avanceret meddelelseskryptering i Microsoft Purview, og du er Microsoft 365 administrator, eller du er afsender af meddelelsen, kan du tilbagekalde meddelelsen under visse betingelser. Administratorer tilbagekalder meddelelser ved hjælp af PowerShell. Som afsender tilbagekalder du en meddelelse, du har sendt direkte fra Outlook på internettet. I denne artikel beskrives de omstændigheder, hvor tilbagekaldelse er mulig, og hvordan du gør det.

> [!NOTE]
> Hvis du vil garantere, at muligheden for at spore og tilbagekalde OME-meddelelser er tilgængelig, skal du tilføje en brugerdefineret brandingskabelon. Se [Føj din organisations brand til dine krypterede meddelelser](add-your-organization-brand-to-encrypted-messages.md)
  
## <a name="encrypted-emails-that-you-can-revoke"></a>Krypterede mails, som du kan tilbagekalde

Administratorer og meddelelsessendere kan tilbagekalde krypterede mails, hvis modtageren har modtaget en linkbaseret, brandet krypteret mail. Hvis modtageren har modtaget en indbygget oplevelse i en understøttet Outlook klient, kan du ikke tilbagekalde meddelelsen.

Om en modtager modtager en linkbaseret oplevelse eller en indbygget oplevelse, afhænger af modtagerens identitetstype: Office 365 og Microsoft-kontomodtagere (f.eks. outlook.com brugere) får en indbygget oplevelse i understøttede Outlook klienter. Alle andre modtagertyper, f.eks. Gmail- og Yahoo-modtagere, får en linkbaseret oplevelse.

Administratorer og afsendere af meddelelser kan tilbagekalde meddelelser, der er krypteret ved hjælp af kryptering, som anvendes direkte fra Outlook på internettet. Meddelelser, der f.eks. er krypteret med indstillingen Krypter kun.

:::image type="content" source="../media/adhocencryptionrevoke.png" alt-text="Skærmbillede, der viser indstillingen Kryptér kun i Outlook på internettet.":::

## <a name="recipient-experience-for-revoked-encrypted-emails"></a>Modtageroplevelse for tilbagekaldte krypterede mails

Når en mail er blevet tilbagekaldt, modtager modtageren en fejl, når vedkommende tilgår den krypterede mail via portalen til Office 365 meddelelseskryptering: "Meddelelsen er tilbagekaldt af afsenderen".

![Skærmbillede, der viser en tilbagekaldt krypteret mail.](../media/revoked-encrypted-email.png)

## <a name="how-to-revoke-an-encrypted-message-that-you-sent"></a>Sådan tilbagekalder du en krypteret meddelelse, du har sendt

Du kan tilbagekalde en mail, som du har sendt til en enkelt modtager, som bruger en social konto, f.eks. gmail.com eller yahoo.com. Med andre ord kan du tilbagekalde en mail, der er sendt til en enkelt modtager, som har modtaget den linkbaserede oplevelse.

Du kan ikke tilbagekalde en mail, du har sendt til en modtager, der bruger en arbejds- eller skolekonto, fra Office 365 eller Microsoft 365 eller en bruger, der bruger en Microsoft-konto, f.eks. en outlook.com konto. 

Hvis du vil tilbagekalde en krypteret meddelelse, du har sendt, skal du udføre disse trin

1. I Outlook på internettet skal du gå til den meddelelse, du vil tilbagekalde, i mappen **Sendt**.

   Hvis mailen kan fortrydes, får du vist linket "Fjern ekstern adgang" øverst i meddelelsen.

    :::image type="content" source="../media/infoprotect-email-encryption/adhocencryptionrevokesentmsg.png" alt-text="Skærmbillede, der viser krypteret mail, som du vil tilbagekalde i Outlook på internettet.":::

2. Klik på **Fjern ekstern adgang** for at tilbagekalde meddelelsen.

   Meddelelsen viser, at dens status er tilbagekaldt.

   :::image type="content" source="../media/adhocencryptionrevokedmsg.png" alt-text="Skærmbillede, der viser tilbagekaldt krypteret meddelelse i Outlook på internettet.":::

## <a name="how-to-revoke-an-encrypted-message-as-an-administrator"></a>Sådan tilbagekalder du en krypteret meddelelse som administrator

Microsoft 365 administratorer følger disse generelle trin for at tilbagekalde en berettiget krypteret mail:

- Hent mailens meddelelses-id.
- Kontrollér, at du kan tilbagekalde meddelelsen.
- Tilbagekald mailen.

### <a name="step-1-obtain-the-message-id-of-the-email"></a>Trin 1. Hent mailens meddelelses-id

Før du kan tilbagekalde en krypteret mail, skal du indsamle mailens meddelelses-id. MessageId har normalt formatet:

`<xxxxxxxxxxxxxxxxxxxxxxx@xxxxxx.xxxx.prod.outlook.com>`  

Der er flere måder at finde meddelelses-id'et for den mail, du vil tilbagekalde. I dette afsnit beskrives et par indstillinger, men du kan bruge en hvilken som helst metode, der indeholder id'et.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-trace-in-the-security-amp-compliance-center"></a>Til at identificere meddelelses-id'et for den mail, du vil tilbagekalde ved hjælp af Meddelelsessporing i Security &amp; Compliance Center

1. Søg efter mailen efter afsender eller modtager ved hjælp af [Ny meddelelsessporing i Security & Compliance Center](https://blogs.technet.microsoft.com/exchange/2018/05/02/new-message-trace-in-office-365-security-compliance-center/).

2. Når du har fundet mailen, skal du vælge den for at få vist ruden **Meddelelsessporingsoplysninger** . Udvid **Flere oplysninger** for at finde meddelelses-id'et.

#### <a name="to-identify-the-message-id-of-the-email-you-want-to-revoke-by-using-message-encryption-reports-in-the-security-amp-compliance-center"></a>Til at identificere meddelelses-id'et for den mail, du vil tilbagekalde ved hjælp af rapporter om meddelelsekryptering i Security &amp; Compliance Center

1. I Security &amp; Compliance Center skal du navigere til **rapporten Meddelelsekryptering**. Du kan få oplysninger om denne rapport under [Få vist mailsikkerhedsrapporter i Security &amp; Compliance Center](../security/office-365-security/view-email-security-reports.md).

2. Vælg tabellen **Vis detaljer** , og identificer den meddelelse, du vil tilbagekalde.

3. Dobbeltklik på meddelelsen for at få vist oplysninger, der indeholder meddelelses-id'et.

### <a name="step-2-verify-that-the-mail-is-revocable"></a>Trin 2. Kontrollér, at mailen kan fortrydes

Hvis du vil kontrollere, om du kan tilbagekalde en meddelelse, skal du kontrollere, om feltet Tilbagekaldsstatus er synligt i rapporten Kryptering i tabellen **Detaljer** i Security &amp; Compliance Center.

Udfør disse trin for at bekræfte, om du kan tilbagekalde en bestemt mail ved hjælp af Windows PowerShell.

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, skal du starte en Windows PowerShell session og oprette forbindelse til Exchange Online. Du kan finde instruktioner [under Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Get-OMEMessageStatus-cmdlet'en på følgende måde:

     ```powershell
     Get-OMEMessageStatus -MessageId "<message id>" | ft -a  Subject, IsRevocable
     ```

   Denne kommando returnerer meddelelsens emne, og om meddelelsen kan fortrydes. Det kan f.eks.

     ```console
     Subject        IsRevocable
     -------        -----------
     "Test message" True
     ```

### <a name="step-3-revoke-the-mail"></a>Trin 3. Tilbagekald mailen

Når du kender meddelelses-id'et for den mail, du vil tilbagekalde, og du har bekræftet, at meddelelsen kan tilbagekaldes, kan du tilbagekalde mailen ved hjælp af Security &amp; Compliance Center eller Windows PowerShell.

Sådan tilbagekaldes meddelelsen ved hjælp af Security &amp; Compliance Center

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du oprette forbindelse til Security & Compliance Center.

2. I **rapporten Kryptering** skal du i tabellen **Detaljer** for meddelelsen vælge **Tilbagekald meddelelse**.

Hvis du vil tilbagekalde en mail ved hjælp af Windows PowerShell, skal du bruge cmdlet'en Set-OMEMessageRevocation.

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, [Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-OMEMessageRevocation-cmdlet'en på følgende måde:

    ```powershell
    Set-OMEMessageRevocation -Revoke $true -MessageId "<messageId>"
    ```

3. Hvis du vil kontrollere, om mailen blev tilbagekaldt, skal du køre cmdlet'en Get-OMEMessageStatus på følgende måde:

    ```powershell
    Get-OMEMessageStatus -MessageId "<messageId>" | ft -a  Subject, Revoked
    ```

    Hvis tilbagekaldelsen lykkedes, returnerer cmdlet'en følgende resultat:  

     ```console
     Revoked: True
     ```

## <a name="more-information-about-microsoft-purview-advanced-message-encryption"></a>Flere oplysninger om avanceret meddelelseskryptering i Microsoft Purview

- [Avanceret meddelelseskryptering i Microsoft Purview](ome-advanced-message-encryption.md)

- [Avanceret meddelelseskryptering i Microsoft Purview – mailudløb](ome-advanced-expiration.md)

- [Beskrivelse af meddelelsespolitik og overholdelsestjeneste](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance)
