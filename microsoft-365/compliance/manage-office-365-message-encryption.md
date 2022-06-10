---
title: Fjern Office 365-meddelelseskryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 03/04/2022
search.appverid:
- MET150
ms.assetid: 09f6737e-f03f-4bc8-8281-e46d24ee2a74
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Når du er færdig med at konfigurere Office 365 OME (Message Encryption), kan du få mere at vide om, hvordan du tilpasser installationen på flere måder.
ms.openlocfilehash: 2e39f811ec23b2f3b068ef5684fca479850a8744
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014822"
---
# <a name="manage-office-365-message-encryption"></a>Fjern Office 365-meddelelseskryptering

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Når du er færdig med at konfigurere Office 365 OME (Message Encryption), kan du tilpasse konfigurationen af installationen på flere måder. Du kan f.eks. konfigurere, om du vil aktivere engangspaskoder, få vist knappen **Kryptér** i Outlook på internettet og meget mere. Opgaverne i denne artikel beskriver hvordan.

## <a name="manage-whether-google-yahoo-and-microsoft-account-recipients-can-use-these-accounts-to-sign-in-to-the-office-365-message-encryption-portal"></a>Administrer, om modtagere af Google-, Yahoo- og Microsoft-konti kan bruge disse konti til at logge på portalen til Office 365 meddelelsekryptering

Når du konfigurerer de nye funktioner Office 365 Meddelelsekryptering, kan brugere i organisationen sende meddelelser til modtagere uden for organisationen. Hvis modtageren bruger et *socialt id* , f.eks. en Google-konto, Yahoo-konto eller En Microsoft-konto, kan modtageren logge på OME-portalen med et socialt id. Hvis du vil, kan du vælge ikke at tillade, at modtagerne bruger sociale id'er til at logge på OME-portalen.

### <a name="to-manage-whether-recipients-can-use-social-ids-to-sign-in-to-the-ome-portal"></a>Sådan administreres, om modtagere kan bruge sociale id'er til at logge på OME-portalen

1. [Forbind til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-OMEConfiguration-cmdlet'en med parameteren SocialIdSignIn på følgende måde:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -SocialIdSignIn <$true|$false>
   ```

   Hvis du f.eks. vil deaktivere sociale id'er:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $false
   ```

   Sådan aktiverer du sociale id'er:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $true
   ```

## <a name="manage-the-use-of-one-time-pass-codes-for-the-office-365-message-encryption-portal"></a>Administrer brugen af engangspaskoder for portalen til Office 365 meddelelsekryptering

Hvis modtageren af en meddelelse, der er krypteret af OME, ikke bruger Outlook, uanset hvilken konto der bruges af modtageren, modtager modtageren et link til webvisning i begrænset tid, hvor de kan læse meddelelsen. Dette link indeholder en engangskode. Som administrator kan du beslutte, om modtagerne kan bruge engangsadgangskoder til at logge på OME-portalen.

### <a name="to-manage-whether-ome-generates-one-time-pass-codes"></a>Sådan administreres, om OME genererer engangspaskoder

1. Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, og opret forbindelse til Exchange Online PowerShell. Du kan finde en vejledning under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-OMEConfiguration-cmdlet'en med OTPEnabled-parameteren:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -OTPEnabled <$true|$false>
   ```

   Hvis du f.eks. vil deaktivere engangspaskoder:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $false
   ```

   Sådan aktiverer du engangspaskoder:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $true
   ```

## <a name="manage-the-display-of-the-encrypt-button-in-outlook-on-the-web"></a>Administrer visningen af knappen Krypter i Outlook på internettet

Som administrator kan du administrere, om denne knap skal vises for slutbrugere.

### <a name="to-manage-whether-the-encrypt-button-appears-in-outlook-on-the-web"></a>Sådan administreres, om knappen Krypter vises i Outlook på internettet

1. Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, og opret forbindelse til Exchange Online PowerShell. Du kan finde en vejledning under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-IRMConfiguration-cmdlet'en med parameteren -SimplifiedClientAccessEnabled:

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled <$true|$false>
   ```

   Hvis du f.eks. vil deaktivere knappen **Kryptér** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

   Sådan aktiverer du knappen **Kryptér** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $true
   ```

## <a name="enable-service-side-decryption-of-email-messages-for-ios-mail-app-users"></a>Aktivér dekryptering af mails på tjenestesiden for brugere af iOS-mailappen

IOS-mailappen kan ikke dekryptere meddelelser, der er beskyttet med Office 365 meddelelseskryptering. Som Microsoft 365 administrator kan du anvende dekryptering på tjenestesiden for meddelelser, der leveres til iOS-mailappen. Når du vælger at bruge dekryptering på tjenestesiden, sender tjenesten en dekrypteret kopi af meddelelsen til iOS-enheden. Klientenheden gemmer en dekrypteret kopi af meddelelsen. Meddelelsen bevarer også oplysninger om brugsrettigheder, selvom iOS-mailappen ikke anvender brugsrettigheder på klientsiden for brugeren. Brugeren kan kopiere eller udskrive meddelelsen, selvom vedkommende ikke oprindeligt har ret til at gøre det. Men hvis brugeren forsøger at fuldføre en handling, der kræver den Microsoft 365 mailserver, f.eks. videresendelse af meddelelsen, tillader serveren ikke handlingen, hvis brugeren ikke oprindeligt har brugsret til at gøre det. Slutbrugere kan dog omgå anvendelsesbegrænsningen "Videresend ikke" ved at videresende meddelelsen fra en anden konto i iOS-mailappen. Uanset om du konfigurerer dekryptering af mails på tjenestesiden, kan vedhæftede filer i krypterede og rettighedsbeskyttede mails ikke ses i iOS-mailappen.

Hvis du vælger ikke at tillade, at dekrypterede meddelelser sendes til brugere af iOS-mailappen, modtager brugerne en meddelelse om, at de ikke har rettigheder til at få vist meddelelsen. Som standard er dekryptering af mails på tjenestesiden ikke aktiveret.

Du kan få flere oplysninger og få vist klientoplevelsen under [Få vist krypterede meddelelser på din iPhone eller iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf).

### <a name="to-manage-whether-ios-mail-app-users-can-view-messages-protected-by-office-365-message-encryption"></a>Sådan administrerer du, om brugere af iOS-mailappen kan få vist meddelelser, der er beskyttet af Office 365 meddelelsekryptering

1. Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, og opret forbindelse til Exchange Online PowerShell. Du kan finde en vejledning under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-ActiveSyncOrganizations-cmdlet'en med parameteren AllowRMSSupportForUnenlightenedApps:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps <$true|$false>
   ```

   Hvis du f.eks. vil konfigurere tjenesten til at dekryptere meddelelser, før de sendes til apps, der ikke er fremhævet, f.eks. iOS-mailappen:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $true
   ```

   Eller hvis du vil konfigurere tjenesten til ikke at sende dekrypterede meddelelser til apps, der ikke er fremhævet:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $false
   ```

> [!NOTE]
> Individuelle postkassepolitikker (OWA/ActiveSync) tilsidesætter disse indstillinger (dvs. hvis -IRMEnabled er angivet til Falsk i den respektive OWA-postkassepolitik eller ActiveSync-postkassepolitik, gælder disse konfigurationer ikke).

## <a name="enable-service-side-decryption-of-email-attachments-for-web-browser-mail-clients"></a>Aktivér dekryptering af vedhæftede filer på tjenestesiden for webbrowsermailklienter

Når du bruger Office 365 meddelelsekryptering, krypteres vedhæftede filer normalt automatisk. Som administrator kan du anvende dekryptering på tjenestesiden for vedhæftede filer i mails, som brugerne downloader fra en webbrowser.

Når du bruger dekryptering på tjenestesiden, sender tjenesten en dekrypteret kopi af filen til enheden. Meddelelsen er stadig krypteret. Den vedhæftede fil indeholder også oplysninger om brugsrettigheder, selvom browseren ikke anvender brugsrettigheder på klientsiden for brugeren. Brugeren kan kopiere eller udskrive den vedhæftede fil, selvom vedkommende ikke oprindeligt har rettigheder til at gøre det. Men hvis brugeren forsøger at fuldføre en handling, der kræver den Microsoft 365 mailserver, f.eks. videresendelse af den vedhæftede fil, tillader serveren ikke handlingen, hvis brugeren ikke oprindeligt har brugsret til at gøre det.

Uanset om du konfigurerer dekryptering af vedhæftede filer på tjenestesiden, kan brugerne ikke få vist vedhæftede filer i krypterede og rettighedsbeskyttede mails i iOS-mailappen.

Hvis du vælger ikke at tillade dekrypterede vedhæftede filer i mails, som er standarden, modtager brugerne en meddelelse om, at de ikke har rettigheder til at få vist den vedhæftede fil.

Du kan få flere oplysninger om, hvordan Microsoft 365 implementerer kryptering for mails og vedhæftede filer i mails med indstillingen Encrypt-Only, under [Indstillingen Kryptér kun for mails.](/azure/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)

### <a name="to-manage-whether-email-attachments-are-decrypted-on-download-from-a-web-browser"></a>Sådan administreres, om vedhæftede filer i mails dekrypteres ved download fra en webbrowser

1. Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, og opret forbindelse til Exchange Online PowerShell. Du kan finde en vejledning under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør cmdlet'en Set-IRMConfiguration med parameteren DecryptAttachmentForEncryptOnly:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly <$true|$false>
   ```

   Hvis du f.eks. vil konfigurere tjenesten til at dekryptere vedhæftede filer i mails, når en bruger downloader dem fra en webbrowser:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
   ```

   Sådan konfigurerer du tjenesten til at efterlade krypterede vedhæftede filer i mails, som de er ved download:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $false
   ```

## <a name="ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail"></a>Sørg for, at alle eksterne modtagere bruger OME-portalen til at læse krypterede mails

Du kan bruge brugerdefinerede brandingskabeloner til at tvinge modtagere til at modtage en ombrydermail, der dirigerer dem til at læse krypterede mails på OME-portalen i stedet for at bruge Outlook eller Outlook på internettet. Det kan være en god idé at gøre dette, hvis du bruger større kontrol over, hvordan modtagerne bruger den mail, de modtager. Hvis eksterne modtagere f.eks. får vist mail på webportalen, kan du angive en udløbsdato for mailen, og du kan tilbagekalde mailen. Disse funktioner understøttes kun via OME-portalen. Du kan bruge indstillingen Kryptér og indstillingen Videresend ikke, når du opretter reglerne for mailflowet.

### <a name="use-a-custom-template-to-force-all-external-recipients-to-use-the-ome-portal-and-for-encrypted-email"></a>Brug en brugerdefineret skabelon til at tvinge alle eksterne modtagere til at bruge OME-portalen og til krypteret mail

1. Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, og opret forbindelse til Exchange Online PowerShell. Du kan finde en vejledning under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør cmdlet'en New-TransportRule:

   ```powershell
   New-TransportRule -name "<mail flow rule name>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "<option name>" -ApplyRightsProtectionCustomizationTemplate "<template name>"
   ```

    Hvor:

   - `mail flow rule name` er det navn, du vil bruge til den nye regel for mailflowet.

   - `option name` er enten `Encrypt` eller `Do Not Forward`.

   - `template name` er det navn, du gav den brugerdefinerede brandingskabelon, f.eks `OME Configuration`. .

   Sådan krypteres alle eksterne mails med skabelonen "OME-konfiguration" og anvender indstillingen Encrypt-Only:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Encrypt" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

   Sådan krypterer du alle eksterne mails med skabelonen "OME-konfiguration" og anvender indstillingen Videresend ikke:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Do Not Forward" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

## <a name="customize-the-appearance-of-email-messages-and-the-ome-portal"></a>Tilpas udseendet af mails og OME-portalen

Du kan finde detaljerede oplysninger om, hvordan du tilpasser Microsoft Purview Message Encryption for din organisation, under [Føj organisationens brand til dine krypterede meddelelser](add-your-organization-brand-to-encrypted-messages.md). Hvis du vil aktivere muligheden for at spore og tilbagekalde krypterede meddelelser, skal du føje din brugerdefinerede branding til OME-portalen.

## <a name="disable-microsoft-purview-message-encryption"></a>Deaktiver Kryptering af Microsoft Purview-meddelelse

Vi håber, at det ikke kommer til det, men hvis du har brug for det, deaktivering af Microsoft Purview Message Encryption er meget ligetil. Først skal du fjerne de regler for mailflow, du har oprettet, og som bruger Microsoft Purview Message Encryption. Du kan få oplysninger om, hvordan du fjerner regler for mailflow, under [Administrer regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules). Udfør derefter disse trin i Exchange Online PowerShell.

### <a name="to-disable-microsoft-purview-message-encryption"></a>Sådan deaktiveres Microsoft Purview-meddelelsekryptering

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du oprette forbindelse til Exchange Online PowerShell. Du kan finde en vejledning under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Hvis du har aktiveret knappen **Krypter** i Outlook på internettet, skal du deaktivere den ved at køre Set-IRMConfiguration-cmdlet'en med parameteren SimplifiedClientAccessEnabled. Ellers skal du springe dette trin over.

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

3. Deaktiver Microsoft Purview Message Encryption ved at køre Set-IRMConfiguration-cmdlet'en med parameteren AzureRMSLicensingEnabled angivet til falsk:

   ```powershell
   Set-IRMConfiguration -AzureRMSLicensingEnabled $false
   ```
