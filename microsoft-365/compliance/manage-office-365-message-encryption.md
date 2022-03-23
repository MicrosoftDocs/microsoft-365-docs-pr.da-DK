---
title: Administrer Office 365-meddelelseskryptering
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
description: Når du er færdig med at konfigurere din Office 365-meddelelseskryptering (OME), kan du få mere at vide om, hvordan du tilpasser din installation på flere måder.
ms.openlocfilehash: 49a3957eb4bc2cf1123f04ab0dea77d2adb638b0
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/16/2022
ms.locfileid: "63587301"
---
# <a name="manage-office-365-message-encryption"></a>Administrer Office 365-meddelelseskryptering

Når du er færdig med at Office 365-meddelelseskryptering (OME), kan du tilpasse konfigurationen af din installation på flere måder. Du kan f.eks. konfigurere, om du vil aktivere engangskoder, få vist **knappen Kryptér** i Outlook på internettet og meget mere. Opgaverne i denne artikel beskriver hvordan.

## <a name="manage-whether-google-yahoo-and-microsoft-account-recipients-can-use-these-accounts-to-sign-in-to-the-office-365-message-encryption-portal"></a>Administrer, om modtagerne af Google-, Yahoo- og Microsoft-konti kan bruge disse konti til at logge på Office 365-meddelelseskryptering-portalen

Når du konfigurerer de Office 365-meddelelseskryptering funktioner, kan brugerne i organisationen sende meddelelser til modtagere, der er uden for organisationen. Hvis modtageren bruger et *socialt* id som f.eks. en Google-konto, Yahoo-konto eller Microsoft-konto, kan modtageren logge på OME-portalen med et socialt id. Hvis du vil, kan du vælge ikke at tillade, at modtagerne bruger sociale oplysninger til at logge på OME-portalen.
  
### <a name="to-manage-whether-recipients-can-use-social-ids-to-sign-in-to-the-ome-portal"></a>Sådan administrerer du, om modtagere kan bruge sociale oplysninger til at logge på OME-portalen
  
1. [Forbind til Exchange Online bruge Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-OMEConfiguration med parameteren SocialIdSignIn på følgende måde:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -SocialIdSignIn <$true|$false>
   ```

   Hvis du f.eks. vil deaktivere sociale oplysninger, skal du gøre følgende:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $false
   ```

   Sådan aktiveres sociale iD'er:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $true
   ```

## <a name="manage-the-use-of-one-time-pass-codes-for-the-office-365-message-encryption-portal"></a>Administrer brugen af engangskoder for Office 365-meddelelseskryptering-portalen

Hvis modtageren af en meddelelse, der er krypteret med OME, ikke bruger Outlook, uanset hvilken konto der bruges af modtageren, modtager modtageren et tidsbegrænset webvisningslink, hvor modtageren kan læse meddelelsen. Dette link indeholder en engangs-adgangskode. Som administrator kan du beslutte, om modtagerne kan bruge engangsadgangskoderne til at logge på OME-portalen.
  
### <a name="to-manage-whether-ome-generates-one-time-pass-codes"></a>Sådan administreres det, om OME genererer engangskoder
  
1. Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, og start en Windows PowerShell session og opret forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-OMEConfiguration-cmdlet'en med OTPEnabled-parameteren:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -OTPEnabled <$true|$false>
   ```

   Hvis du f.eks. vil deaktivere engangskoder:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $false
   ```

   Sådan aktiveres engangskoder:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $true
   ```

## <a name="manage-the-display-of-the-encrypt-button-in-outlook-on-the-web"></a>Administrer visningen af knappen Kryptér i Outlook på internettet

Som administrator kan du styre, om denne knap skal vises for slutbrugere.
  
### <a name="to-manage-whether-the-encrypt-button-appears-in-outlook-on-the-web"></a>Sådan administrerer du, om knappen Kryptér vises i Outlook på internettet
  
1. Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, og start en Windows PowerShell session og opret forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-IRMConfiguration-cmdlet'en med parameteren -SimplifiedClientAccessEnabled:

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled <$true|$false>
   ```

   Sådan deaktiverer du f.eks **. knappen Kryptér** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

   Sådan aktiveres knappen **Kryptér** :

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $true
   ```

## <a name="enable-service-side-decryption-of-email-messages-for-ios-mail-app-users"></a>Aktivér dekryptering på tjenestesiden af mails for iOS-mailappbrugere

IOS-mailappen kan ikke dekryptere meddelelser, der er beskyttet Office 365-meddelelseskryptering. Som administrator Microsoft 365 du anvende dekryptering på tjenestesiden for meddelelser, der leveres til iOS-mailappen. Når du vælger at bruge dekryptering på tjenestesiden, sender tjenesten en dekrypteret kopi af meddelelsen til iOS-enheden. Klientenheden gemmer en dekrypteret kopi af meddelelsen. Meddelelsen bevarer også oplysninger om brugsrettigheder, selvom iOS-mailappen ikke anvender brugerrettigheder på klientsiden på brugeren. Brugeren kan kopiere eller udskrive meddelelsen, selvom de ikke oprindeligt har rettigheder til at gøre det. Men hvis brugeren forsøger at udføre en handling, der kræver Microsoft 365-mailserveren, f.eks. videresendelse af meddelelsen, tillader serveren ikke handlingen, hvis brugeren oprindeligt ikke har brugstilladelse til at gøre dette. Slutbrugere kan imidlertid løse brugsbegrænsningen ved ikke at videresende meddelelsen fra en anden konto i iOS-mailappen. Uanset om du har konfigureret dekryptering af mail fra tjenestesiden, kan vedhæftede filer til krypterede og rettighedsbeskyttede mails ikke vises i iOS-mailappen.
  
Hvis du vælger ikke at tillade, at dekrypterede meddelelser sendes til iOS-mailappbrugere, modtager brugerne en meddelelse om, at de ikke har rettigheder til at få vist meddelelsen. Dekryptering af mails på tjenestesiden er som standard ikke aktiveret.
  
Du kan finde flere oplysninger og få vist klientoplevelsen i Få vist [krypterede meddelelser på din iPhone eller iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf).
  
### <a name="to-manage-whether-ios-mail-app-users-can-view-messages-protected-by-office-365-message-encryption"></a>Sådan administrerer du, om brugere af iOS-mailappen kan få vist meddelelser beskyttet af Office 365-meddelelseskryptering
  
1. Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, og start en Windows PowerShell session og opret forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-ActiveSyncOrganizations-cmdletten med parameteren AllowRMSSupportForUnenlightenedApps:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps <$true|$false>
   ```

   Hvis du f.eks. vil konfigurere tjenesten til at dekryptere meddelelser, før de sendes til ikke-åbnede apps som f.eks. iOS-mailappen:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $true
   ```

   Eller, hvis du vil konfigurere tjenesten til ikke at sende dekrypterede meddelelser til ikke-åbnede apps:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $false
   ```

> [!NOTE]
> Individuelle postkassepolitikker (OWA/ActiveSync) tilsidesætter disse indstillinger (dvs. hvis -IRMEnabled er indstillet til Falsk inden for den respektive OWA-postkassepolitik eller ActiveSync-postkassepolitik, gælder disse konfigurationer ikke).

## <a name="enable-service-side-decryption-of-email-attachments-for-web-browser-mail-clients"></a>Aktivér dekryptering af vedhæftede filer på tjenestesiden for mailklienter i webbrowseren

Normalt krypteres vedhæftede Office 365 automatisk, når du bruger kryptering af meddelelser. Som administrator kan du anvende dekryptering på tjenestesiden for vedhæftede filer, som brugere henter fra en webbrowser.
  
Når du bruger dekryptering på tjenestesiden, sender tjenesten en dekrypteret kopi af filen til enheden. Meddelelsen er stadig krypteret. Den vedhæftede fil i en mail gemmer også oplysninger om brugerrettigheder, selvom browseren ikke anvender brugerrettigheder på klientsiden. Brugeren kan kopiere eller udskrive den vedhæftede fil i en mail, selvom de oprindeligt ikke havde rettigheder til at gøre det. Men hvis brugeren forsøger at udføre en handling, der kræver Microsoft 365-mailserveren, f.eks. videresendelse af den vedhæftede fil, tillader serveren ikke handlingen, hvis brugeren oprindeligt ikke har brugstilladelse til at gøre dette.
  
Uanset om du har konfigureret dekryptering af vedhæftede filer på tjenestesiden, kan brugerne ikke få vist vedhæftede filer til krypterede og rettighedsbeskyttede mails i iOS-mailappen.
  
Hvis du vælger ikke at tillade dekrypterede vedhæftede filer, som er standard, modtager brugerne en meddelelse om, at de ikke har rettigheder til at få vist den vedhæftede fil.
  
Du kan finde flere oplysninger om, hvordan Microsoft 365 implementerer kryptering til mails og vedhæftede filer i mails med indstillingen Encrypt-Only, under Krypterings eneste [indstilling for mails.](/azure/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)
  
### <a name="to-manage-whether-email-attachments-are-decrypted-on-download-from-a-web-browser"></a>Sådan administreres det, om vedhæftede filer i mails dekrypteres ved download fra en webbrowser
  
1. Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, og start en Windows PowerShell session og opret forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-IRMConfiguration med parameteren DecryptAttachmentForEncryptOnly:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly <$true|$false>
   ```

   Hvis du f.eks. vil konfigurere tjenesten til at dekryptere vedhæftede filer i mails, når en bruger henter dem fra en webbrowser:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
   ```

   Sådan konfigurerer du tjenesten til at lade krypterede vedhæftede filer, som de er ved overførsel, være:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $false
   ```

## <a name="ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail"></a>Sørg for, at alle eksterne modtagere bruger OME-portalen til at læse krypteret mail

Du kan bruge brugerdefinerede brandingskabeloner til at tvinge modtagerne til at modtage en wrapper mail, der dirigerer dem til at læse krypterede mails i OME-portalen i stedet for at bruge Outlook eller Outlook på internettet. Det kan du gøre, hvis du vil have større kontrol over, hvordan modtagerne bruger mailen, de modtager. Hvis eksterne modtagere f.eks. får vist mail i webportalen, kan du angive en udløbsdato for mailen, og du kan tilbagekalde mailen. Disse funktioner understøttes kun via OME-portalen. Du kan bruge indstillingen Kryptér og indstillingen Videressendelse ikke, når du opretter regler for mailflow.

### <a name="use-a-custom-template-to-force-all-external-recipients-to-use-the-ome-portal-and-for-encrypted-email"></a>Brug en brugerdefineret skabelon til at tvinge alle eksterne modtagere til at bruge OME-portalen og til krypteret mail

1. Brug en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, og start en Windows PowerShell session og opret forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør New-TransportRule cmdlet:

   ```powershell
   New-TransportRule -name "<mail flow rule name>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "<option name>" -ApplyRightsProtectionCustomizationTemplate "<template name>"
   ```

    hvor:

   - `mail flow rule name` er det navn, du vil bruge til den nye regel for mailflow.

   - `option name` er enten `Encrypt` eller `Do Not Forward`.

   - `template name` er det navn, du har givet skabelonen til brugerdefineret branding, f.eks `OME Configuration`. .

   Hvis du vil kryptere alle eksterne mails med skabelonen "OME-konfiguration", og Encrypt-Only mailindstillingen:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Encrypt" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

   Hvis du vil kryptere alle eksterne mails med skabelonen "OME-konfiguration", og anvend indstillingen Videressendelse ikke:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Do Not Forward" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

## <a name="customize-the-appearance-of-email-messages-and-the-ome-portal"></a>Tilpasse udseendet af mails og OME-portalen

Du kan finde detaljerede oplysninger om, hvordan du kan tilpasse OME til din organisation, under Føje [organisationens brand til dine krypterede meddelelser](add-your-organization-brand-to-encrypted-messages.md). For at aktivere muligheden for at spore og tilbagekalde krypterede meddelelser skal du tilføje din brugerdefinerede branding til OME-portalen.
  
## <a name="disable-the-new-capabilities-for-ome"></a>Deaktiver de nye funktioner for OME

Vi håber, det ikke bliver til det, men hvis der er brug for det, er det meget nemt at deaktivere de nye funktioner i OME. Først skal du fjerne alle regler for mailflow, du har oprettet, som bruger de nye OME-funktioner. Du kan finde oplysninger om, hvordan du fjerner regler for mailflow [i Administrere regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules). Fuldfør derefter disse trin i Exchange Online PowerShell.
  
### <a name="to-disable-the-new-capabilities-for-ome"></a>Deaktiver de nye funktioner i OME
  
1. Du kan bruge en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, til at starte en Windows PowerShell-session og oprette forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Hvis du har aktiveret knappen Kryptér i Outlook på internettet, skal du deaktivere den ved at Set-IRMConfiguration køre cmdlet'en SimplifiedClientAccessEnabled med parameteren SimplifiedClientAccessEnabled. Ellers kan du springe dette trin over.

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

3. Deaktiver de nye funktioner for OME ved at køre Set-IRMConfiguration-cmdlet'en med AzureRMSLicensingEnabled-parameteren angivet til falsk:

   ```powershell
   Set-IRMConfiguration -AzureRMSLicensingEnabled $false
   ```
