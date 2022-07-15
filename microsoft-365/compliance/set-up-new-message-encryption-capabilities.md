---
title: Konfigurer Microsoft Purview-meddelelseskryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/16/2022
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 7ff0c040-b25c-4378-9904-b1b50210d00e
ms.collection:
- Strat_O365_IP
- M365-security-compliance
description: Få mere at vide om Microsoft Purview-meddelelseskryptering, der muliggør beskyttet mailkommunikation med personer i og uden for din organisation.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.openlocfilehash: a77dcb557901f8a159e0c82a084dd02255193c72
ms.sourcegitcommit: a209c9f86a7b4340a426c4cfed2d36a388c71124
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66797945"
---
# <a name="set-up-message-encryption"></a>Konfigurer meddelelsekryptering

Microsoft Purview-meddelelseskryptering gør det muligt for organisationer at dele beskyttet mail med alle på en hvilken som helst enhed. Brugerne kan udveksle beskyttede meddelelser med andre Microsoft 365-organisationer samt tredjeparter ved hjælp af Outlook.com, Gmail og andre mailtjenester.

Følg nedenstående trin for at sikre, at Microsoft Purview-meddelelseskryptering er tilgængelige i din organisation.

## <a name="verify-that-azure-rights-management-is-active"></a>Bekræft, at Azure Rights Management er aktiv

Microsoft Purview-meddelelseskryptering udnytter beskyttelsesfunktionerne i [Azure RMS (Azure Rights Management Services),](/azure/information-protection/what-is-information-protection) den teknologi, der bruges af [Azure Information Protection](/azure/information-protection/what-is-azure-rms) til at beskytte mails og dokumenter via krypterings- og adgangskontrol.

Den eneste forudsætning for at bruge Microsoft Purview-meddelelseskryptering er, at [Azure Rights Management](/azure/information-protection/what-is-azure-rms) skal aktiveres i din organisations lejer. Hvis det er, aktiverer Microsoft 365 automatisk meddelelsekryptering, og du behøver ikke at foretage dig noget.

Azure RMS aktiveres også automatisk for de fleste berettigede planer, så du behøver sandsynligvis heller ikke at foretage dig noget i denne henseende. Se [Aktivering af Azure Rights Management for at](/azure/information-protection/activate-service) få flere oplysninger.

> [!IMPORTANT]
> Hvis du bruger AD RMS (Active Directory Rights Management Service) med Exchange Online, skal du [migrere til Azure Information Protection](/azure/information-protection/migrate-from-ad-rms-to-azure-rms), før du kan bruge meddelelsekryptering. Microsoft Purview-meddelelseskryptering er ikke kompatibel med AD RMS.

Du kan finde flere oplysninger under:

- [Ofte stillede spørgsmål om meddelelseskryptering](ome-faq.yml) for at kontrollere, om din abonnementsplan indeholder Azure Information Protection (som omfatter Azure RMS-funktionalitet).
- [Azure Information Protection](https://azure.microsoft.com/services/information-protection/) for at få oplysninger om køb af et berettiget abonnement.

### <a name="manually-activating-azure-rights-management"></a>Manuel aktivering af Azure Rights Management

Hvis du har deaktiveret Azure RMS, eller hvis det af en eller anden grund ikke blev aktiveret automatisk, kan du aktivere det manuelt. 

Du kan finde instruktioner under [Sådan aktiverer eller bekræfter du status for beskyttelsestjeneste](/azure/information-protection/activate-service#how-to-activate-or-confirm-the-status-of-the-protection-service).

## <a name="configure-management-of-your-azure-information-protection-tenant-key"></a>Konfigurer administration af din Azure Information Protection-lejernøgle

Dette er et valgfrit trin. Det er standardindstillingen og anbefalet bedste praksis for de fleste organisationer at give Microsoft tilladelse til at administrere rodnøglen til Azure Information Protection. Hvis det er tilfældet, behøver du ikke at gøre noget.

Der er mange årsager, f.eks. krav til overholdelse af angivne standarder, som kan nødvendiggøre, at du genererer og administrerer din egen rodnøgle (også kendt som BYOK (Bring Your Own Key)). Hvis det er tilfældet, anbefaler vi, at du fuldfører de påkrævede trin, før du konfigurerer Microsoft Purview-meddelelseskryptering. Se [Planlægning og implementering af din Azure Information Protection-lejernøgle](/information-protection/plan-design/plan-implement-tenant-key) for at få mere at vide.

## <a name="verify-microsoft-purview-message-encryption-configuration-in-exchange-online-powershell"></a>Kontrollér Microsoft Purview-meddelelseskryptering konfiguration i Exchange Online PowerShell

Du kan bekræfte, at din Microsoft 365-lejer er konfigureret korrekt til at bruge Microsoft Purview-meddelelseskryptering i [Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell).

1. [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) ved hjælp af en konto med globale administratortilladelser i din Microsoft 365-lejer.

2. Kør cmdlet'en Get-IRMConfiguration.

     Du får vist værdien $True for parameteren AzureRMSLicensingEnabled, hvilket angiver, at Microsoft Purview-meddelelseskryptering er konfigureret i din lejer. Hvis det ikke er det, skal du bruge Set-IRMConfiguration til at angive værdien af AzureRMSLicensingEnabled til $True for at aktivere Microsoft Purview-meddelelseskryptering.

3. Kør Test-IRMConfiguration-cmdlet'en ved hjælp af følgende syntaks:

   ```powershell
   Test-IRMConfiguration [-Sender <email address> -Recipient <email address>]
   ```

   **Eksempel**:

   ```powershell
   Test-IRMConfiguration -Sender securityadmin@contoso.com -Recipient securityadmin@contoso.com
   ```

   - Til afsender og modtager skal du bruge mailadressen på alle brugere i din Microsoft 365-lejer.

     Dine resultater skal ligne:

     ```console
     Results : Acquiring RMS Templates ...
                - PASS: RMS Templates acquired.  Templates available: Contoso  - Confidential View Only, Contoso  - Confidential, Do Not
            Forward.
            Verifying encryption ...
                - PASS: Encryption verified successfully.
            Verifying decryption ...
                - PASS: Decryption verified successfully.
            Verifying IRM is enabled ...
                - PASS: IRM verified successfully.

            OVERALL RESULT: PASS
     ```

   - Navnet på din organisation erstatter *Contoso*.

   - Standardskabelonnavnene kan være forskellige fra dem, der vises ovenfor. Se [Konfiguration og administration af skabeloner til Azure Information Protection](/azure/information-protection/configure-policy-templates) for at få mere at vide.

4. Hvis testen mislykkes med en fejlmeddelelse **, der ikke kunne hente RMS-skabeloner**, skal du udføre følgende kommandoer og køre Test-IRMConfiguration-cmdlet'en for at kontrollere, at den består.

   ```powershell
   $RMSConfig = Get-AadrmConfiguration
   $LicenseUri = $RMSConfig.LicensingIntranetDistributionPointUrl
   Set-IRMConfiguration -LicensingLocation $LicenseUri
   Set-IRMConfiguration -InternalLicensingEnabled $true
   ```
5. Kør Remove-PSSession-cmdlet'en for at afbryde forbindelsen til Rights Management-tjenesten.

     ```powershell
     Remove-PSSession $session
     ```

## <a name="next-steps-define-mail-flow-rules-to-use-microsoft-purview-message-encryption"></a>Næste trin: Definer regler for mailflow, der skal bruges Microsoft Purview-meddelelseskryptering

Hvis der tidligere er konfigureret regler for mailflow til kryptering af mail i din organisation, skal du opdatere de eksisterende regler for at bruge Microsoft Purview-meddelelseskryptering. I forbindelse med nye udrulninger skal du oprette nye regler for mailflow.

> [!IMPORTANT]
> Hvis du ikke opdaterer eksisterende regler for mailflow, modtager brugerne fortsat krypterede mails, der bruger det tidligere format for vedhæftede HTML-filer, i stedet for den nye problemfrie oplevelse.

Regler for mailflow bestemmer, under hvilke betingelser mails skal krypteres, samt betingelser for fjernelse af denne kryptering. Når du angiver en handling for en regel, krypteres alle meddelelser, der opfylder regelbetingelserne, når de sendes.

Du kan finde trin til oprettelse af meddelelseskryptering af regler for mailflow under [Definer regler for mailflow for at kryptere mails i Office 365](define-mail-flow-rules-to-encrypt-email.md).

Sådan opdaterer du eksisterende regler til at bruge Microsoft Purview-meddelelseskryptering:

1. I Microsoft 365 Administration skal du gå til **Exchange Administration centre** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>
2. I Exchange Administration skal du gå til **Mailflow > Regler**.
3. For hver regel skal **du gøre følgende**:
    - Vælg **Rediger meddelelsessikkerheden**.
    - Vælg **Anvend Office 365 Meddelelsekryptering og rettighedsbeskyttelse**.
    - Vælg en RMS-skabelon på listen.
    - Vælg **Gem**.
    - Vælg **OK**.
