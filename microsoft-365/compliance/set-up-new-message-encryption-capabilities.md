---
title: Konfigurer nye egenskaber for meddelelseskryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/30/2019
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
description: Få mere at vide om de Office 365-meddelelseskryptering funktioner, der muliggør beskyttet mailkommunikation med personer i og uden for organisationen.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.openlocfilehash: 006bef8a78a50e3cc47bfcfe7910621a3fa9ef85
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63587724"
---
# <a name="set-up-new-message-encryption-capabilities"></a>Konfigurer nye egenskaber for meddelelseskryptering

De nye Office 365-meddelelseskryptering (OME)-funktioner giver organisationer mulighed for at dele beskyttet mail med alle på enhver enhed. Brugere kan udveksle beskyttede meddelelser med Microsoft 365 organisationer samt ikke-kunder, der bruger Outlook.com, Gmail og andre mailtjenester.

Følg trinnene nedenfor for at sikre, at de nye OME-funktioner er tilgængelige i din organisation.

## <a name="verify-that-azure-rights-management-is-active"></a>Kontrollér, at Azure Rights Management er aktiv

De nye OME-funktioner udnytter beskyttelsesfunktionerne i [Azure Rights Management Services (Azure RMS),](/azure/information-protection/what-is-information-protection) som er den teknologi, der bruges af [Azure Information Protection](/azure/information-protection/what-is-azure-rms) til at beskytte mails og dokumenter via krypterings- og adgangskontrolelementer.

Den eneste forudsætning for at bruge de nye OME-funktioner er, at [Azure Rights Management](/azure/information-protection/what-is-azure-rms) skal aktiveres i din organisations lejer. Hvis det er, Microsoft 365 aktivere de nye OME-funktioner automatisk, og du behøver ikke at gøre noget.

Azure RMS aktiveres også automatisk for de fleste berettigede planer, så du behøver sandsynligvis heller ikke at gøre noget i denne retning. Se [Aktivering af Azure Rights Management for](/azure/information-protection/activate-service) at få flere oplysninger.

> [!IMPORTANT]
> Hvis du bruger Active Directory Rights Management Service (AD RMS) med Exchange Online, skal du overføre til [Azure Information Protection](/azure/information-protection/migrate-from-ad-rms-to-azure-rms), før du kan bruge de nye OME-funktioner. OME er ikke kompatibel med AD RMS.

Du kan finde flere oplysninger under:

- [Hvilke abonnementer skal jeg bruge for at kunne bruge de nye OME-funktioner?](ome-faq.yml#what-subscriptions-do-i-need-to-use-the-new-ome-capabilities-) for at kontrollere, om din abonnementsplan omfatter Azure Information Protection (som omfatter Azure RMS-funktionalitet).
- [Azure Information Protection for](https://azure.microsoft.com/services/information-protection/) at få oplysninger om at købe et kvalificerede abonnement.

### <a name="manually-activating-azure-rights-management"></a>Aktivere Azure Rights Management manuelt

Hvis du har deaktiveret Azure RMS, eller hvis det af en eller anden grund ikke blev aktiveret automatisk, kan du aktivere det manuelt i:

- **Microsoft 365 Administration**: Se Sådan [aktiverer du Azure Rights Management fra Administration](/azure/information-protection/activate-office365) for at få vejledning.
- **Azure-portal**: Se [Sådan aktiverer du Azure Rights Management fra Azure-portalen for vejledning](/azure/information-protection/activate-azure) .

## <a name="configure-management-of-your-azure-information-protection-tenant-key"></a>Konfigurere administrationen af din Azure Information Protection-lejernøgle

Dette er et valgfrit trin. At give Microsoft tilladelse til at administrere rodnøglen til Azure Information Protection er standardindstillingen og anbefalede bedste praksis for de fleste organisationer. Hvis det er tilfældet, behøver du ikke at gøre noget.

Der er mange årsager, f.eks. overholdelseskrav, som kan være din egen, der genererer og administrerer din egen rodnøgle (også kaldet at medbringe din egen nøgle (BYOK)). Hvis det er tilfældet, anbefaler vi, at du gennemfører de nødvendige trin, før du konfigurerer de nye OME-funktioner. Se [Planlægning og implementering af din Azure Information Protection-lejernøgle for at](/information-protection/plan-design/plan-implement-tenant-key) få mere at vide.

## <a name="verify-new-ome-configuration-in-exchange-online-powershell"></a>Bekræft ny OME-konfiguration Exchange Online PowerShell

Du kan kontrollere, at Microsoft 365 lejer er konfigureret korrekt til at bruge de nye OME-funktioner [i Exchange Online PowerShell](/powershell/exchange/exchange-online-powershell).

1. [Forbind at Exchange Online PowerShell ved](/powershell/exchange/connect-to-exchange-online-powershell) hjælp af en konto med globale administratortilladelser i din Microsoft 365 lejer.

2. Kør Get-IRMConfiguration cmdlet'en.

     Du bør få vist en værdi på $True for AzureRMSLicensingEnabled-parameteren, som angiver, at OME er konfigureret i din lejer. Hvis den ikke er, skal Set-IRMConfiguration til at angive værdien af AzureRMSLicensingEnabled til $True at aktivere OME.

3. Kør cmdletten Test-IRMConfiguration ved hjælp af følgende syntaks:

   ```powershell
   Test-IRMConfiguration [-Sender <email address> -Recipient <email address>]
   ```

   **Eksempel**:

   ```powershell
   Test-IRMConfiguration -Sender securityadmin@contoso.com -Recipient securityadmin@contoso.com
   ```

   - Til afsender og modtager skal du bruge mailadressen på alle brugere i din Microsoft 365 lejer.

     Resultaterne bør ligne følgende:

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

   - Organisationens navn vil erstatte *Contoso*.

   - Standardskabelonnavnene kan være forskellige fra dem, der vises ovenfor. Se [Konfiguration og administration af skabeloner til Azure Information Protection for at](/azure/information-protection/configure-policy-templates) få mere at vide.

4. Kør cmdletten Remove-PSSession at afbryde forbindelsen til Rights Management-tjenesten.

     ```powershell
     Remove-PSSession $session
     ```

## <a name="next-steps-define-mail-flow-rules-to-use-new-ome-capabilities"></a>Næste trin: Definere regler for mailflow for at bruge nye OME-funktioner

Hvis der tidligere er konfigureret regler for mailflow for at kryptere mail i din organisation, skal du opdatere de eksisterende regler for at bruge de nye OME-funktioner. Ved nye installationer skal du oprette nye regler for mailflow.

> [!IMPORTANT]
> Hvis du ikke opdaterer eksisterende regler for mailflow, vil brugerne fortsat modtage krypterede mails, der bruger det tidligere HTML-format til vedhæftede filer, i stedet for den nye problemfri OME-oplevelse.

Regler for mailflow bestemmer under hvilke betingelser mails skal krypteres samt betingelser for fjernelse af denne kryptering. Når du angiver en handling for en regel, krypteres meddelelser, der opfylder regelbetingelserne, når de sendes.

Hvis du vil have en vejledning til oprettelse af regler for mailflow for OME, skal du se Definere regler for mailflow [for at kryptere mails Office 365](define-mail-flow-rules-to-encrypt-email.md).

Sådan opdaterer du eksisterende regler for at bruge de nye OME-funktioner:

1. I Microsoft 365 Administration skal du gå **til Exchange** > .<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>
2. I Exchange Administration skal du gå til **Mailflow > Regler**.
3. Gør følgende for **hver regel**:
    - Vælg **Rediger meddelelsens sikkerhed**.
    - Vælg **Anvend Office 365-meddelelseskryptering og rettighedsbeskyttelse**.
    - Vælg en RMS-skabelon på listen.
    - Vælg **Gem**.
    - Vælg **OK**.
