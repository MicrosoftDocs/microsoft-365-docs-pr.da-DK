---
title: Ældre oplysninger til Office 365-meddelelseskryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 05/22/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.assetid: 5986b9e1-c824-4f8f-9b7d-a2b0ae2a7fe9
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Få mere at vide om, hvordan du overgange ældre filer Office 365-meddelelseskryptering (OME) i organisationen.
ms.openlocfilehash: 6213aec3edd8d55c21ba4137a2052b08147aedc3
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2022
ms.locfileid: "63587497"
---
# <a name="legacy-information-for-office-365-message-encryption"></a>Ældre oplysninger til Office 365-meddelelseskryptering

Hvis du endnu ikke har flyttet organisationen til de nye OME-funktioner, men du allerede har installeret OME, gælder oplysningerne i denne artikel for din organisation. Microsoft anbefaler, at du planlægger at flytte til de nye OME-funktioner, så snart det er fornuftigt for din organisation. Du kan finde en [vejledning under Konfigurere Office 365-meddelelseskryptering funktioner, der er bygget oven på Azure Information Protection](set-up-new-message-encryption-capabilities.md). Hvis du vil vide mere om, hvordan de nye funktioner virker først, skal du se [Office 365-meddelelseskryptering](ome.md). Resten af denne artikel henviser til OME-funktionsmåde før frigivelsen af de nye OME-funktioner.

Med Office 365-meddelelseskryptering kan din organisation sende og modtage krypterede mails mellem personer i og uden for organisationen. Office 365-meddelelseskryptering fungerer sammen med Outlook.com, Yahoo, Gmail og andre mailtjenester. Kryptering af mail er med til at sikre, at det kun er de tilsigtede modtagere, der kan se meddelelsens indhold.

Her er nogle eksempler:

- En bankmedarbejder sender kreditkortopgørelser til kunder
- En repræsentant for et forsikringsselskab leverer oplysninger om politikken til kunder
- En lånemægler anmoder om finansielle oplysninger fra en kunde om et låneprogram
- En sundhedsudbyder sender sundhedsplejeoplysninger til patienter
- En advokat sender fortrolige oplysninger til en kunde eller en anden advokat

## <a name="how-office-365-message-encryption-works-without-the-new-capabilities"></a>Sådan Office 365-meddelelseskryptering fungerer uden de nye funktioner

Office 365-meddelelseskryptering er en onlinetjeneste, der er bygget på Microsoft Azure Rights Management (Azure RMS). Med Azure RMS kan administratorer definere regler for mailflow for at bestemme betingelserne for kryptering. En regel kan f.eks. kræve kryptering af alle meddelelser, der er adresseret til en bestemt modtager.

Når nogen sender en mail i et Exchange Online, der svarer til en krypteringsregel, sendes meddelelsen med en vedhæftet HTML-fil. Modtageren åbner den vedhæftede HTML-fil og følger instruktionerne for at få vist den krypterede meddelelse på Office 365-meddelelseskryptering-portalen. Modtageren kan vælge at få vist meddelelsen ved at logge på med en Microsoft-konto eller en arbejds- eller skolekonto, der er knyttet til Office 365, eller ved hjælp af en engangs-adgangskode. Begge indstillinger hjælper med at sikre, at det kun er den tilsigtede modtager, der kan se den krypterede meddelelse. Denne proces er meget anderledes for de nye OME-funktioner.

Følgende diagram opsummerer passagen af en mail via krypterings- og dekrypteringsprocessen.

![Diagram, der viser stien til en krypteret mail.](../media/O365-Office365MessageEncryption-Concept.png)

Få mere at vide [under Tjenesteoplysninger for ældre Office 365-meddelelseskryptering før udgivelsen af de nye OME-funktioner](legacy-information-for-message-encryption.md#LegacyServiceInfo).

## <a name="defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-the-new-ome-capabilities"></a>Definition af regler for mailflow Office 365-meddelelseskryptering, der ikke bruger de nye OME-funktioner

For at Office 365-meddelelseskryptering mailflow uden de nye funktioner definerer Exchange Online og Exchange Online Protection administratorerne Exchange regler for mailflow. Disse regler bestemmer under hvilke betingelser mails skal krypteres samt betingelser for fjernelse af meddelelseskryptering. Når en krypteringshandling er indstillet for en regel, udfører tjenesten handlingen på alle meddelelser, der opfylder regelbetingelserne, før meddelelserne sendes.

Regler for mailflow er fleksible, så du kan kombinere betingelser, så du kan opfylde specifikke sikkerhedskrav i en enkelt regel. Du kan f.eks. oprette en regel for at kryptere alle meddelelser, der indeholder angivne nøgleord, og som er adresseret til eksterne modtagere. Office 365-meddelelseskryptering krypterer også svar fra modtagere af krypteret mail, og du kan oprette en regel, der dekrypterer disse svar som en praktisk hjælp for dine mailbrugere. På den måde behøver brugerne i organisationen ikke at logge på krypteringsportalen for at få vist svar.

Du kan finde flere oplysninger om, hvordan Exchange regler for mailflow, i [Definere regler for Office 365-meddelelseskryptering](define-mail-flow-rules-to-encrypt-email.md).

### <a name="use-the-eac-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>Brug EAC til at oprette en regel for mailflow til kryptering af mails uden de nye OME-funktioner

1. I en webbrowser skal du logge på med en arbejds- eller skolekonto, der har fået globale administratorrettigheder, [for at Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Vælg **feltet** Administrator.

3. Vælg Microsoft 365 Administration **administration i Exchange**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>

4. I EAC skal du gå til **Regler for mailflow** \> og **vælge Nyt** ![nyt ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Oprette en ny regel**. Du kan finde flere oplysninger om brug af [EAC Exchange Administration i Exchange Online](/exchange/exchange-admin-center).

5. Skriv **et** navn til reglen under Navn, f.eks. Kryptér mail for DrToniRamos@hotmail.com.

6. I **Anvend denne regel, hvis du** vælger en betingelse, og angiv en værdi, hvis det er nødvendigt. Hvis du f.eks. vil kryptere meddelelser, der DrToniRamos@hotmail.com:

   1. Vælg **modtageren i Anvend denne** regel, **hvis**.

   2. Vælg et eksisterende navn på listen over kontakter, eller skriv en ny mailadresse i **afkrydsningsfeltet** Navne.

      - Hvis du vil vælge et eksisterende navn, skal du vælge det på listen og derefter klikke på **OK**.

      - Hvis du vil angive et nyt navn, skal du skrive en mailadresse **i afkrydsningsfeltet Navne** og derefter **vælge Kontrollér navne** \> **OK**.

7. Hvis du vil tilføje flere betingelser, **skal du vælge** Flere indstillinger **og derefter vælge Tilføj** betingelse og vælge på listen.

   Hvis du f.eks. kun vil anvende reglen, hvis modtageren er uden for din  organisation, skal du vælge Tilføj betingelse og derefter vælge Modtageren er ekstern **/intern** \> **Uden for** \> **organisationen OK**.

8. Hvis du vil aktivere kryptering uden at bruge de nye OME-funktioner,  \> skal du i Gør følgende vælge Rediger meddelelsessikkerhed Anvend den tidligere **version af OME** og derefter vælge **Gem**.

   Hvis du får en fejlmeddelelse om, at IRM-licenser ikke er aktiveret, bruger du ikke den ældre OME.

9. (Valgfrit) Vælg **Tilføj handling for** at angive en anden handling.

### <a name="use-exchange-online-powershell-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>Brug Exchange Online PowerShell til at oprette en regel for mailflow til kryptering af mails uden de nye OME-funktioner

1. Forbind til Exchange Online PowerShell. Du kan finde flere oplysninger [Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Opret en regel ved hjælp af **New-TransportRule-cmdlet'en** , og angiv _ApplyOME-parameteren_ til `$true`.

   I dette eksempel kræves det, at alle mails, der DrToniRamos@hotmail.com til en mailkonto, skal krypteres.

   ```powershell
   New-TransportRule -Name "Encrypt rule for Dr Toni Ramos" -SentTo "DrToniRamos@hotmail.com" -SentToScope "NotinOrganization" -ApplyOME $true
   ```

   Hvor

   - Det entydige navn på den nye regel er "Krypteringsregel for Dr Toni Ramos".
   - _Parameteren SentTo_ angiver modtagerne af meddelelsen (identificeres ved navn, mailadresse, entydigt navn osv.). I dette eksempel identificeres modtageren af mailadressen "DrToniRamos@hotmail.com".
   - _Parameteren SentToScope_ angiver placeringen af meddelelsens modtagere. I dette eksempel er modtagerens postkasse i hotmail og er ikke en del af organisationen, så værdien `NotInOrganization` bruges.

   Du kan finde detaljerede oplysninger om syntaks og parameter [i New-TransportRule](/powershell/module/exchange/New-TransportRule).

### <a name="remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Fjern kryptering fra mailsvar, der er krypteret uden de nye OME-funktioner

Når dine mailbrugere sender krypterede meddelelser, kan modtagerne af disse meddelelser svare med krypterede svar. Du kan oprette regler for mailflow for automatisk at fjerne kryptering fra svar, så mailbrugere i organisationen ikke behøver at logge på krypteringsportalen for at få dem vist. Du kan bruge EAC- eller Windows PowerShell-cmdlet'er til at definere disse regler. Du kan dekryptere meddelelser, der sendes fra din organisation, eller meddelelser, der er svar på meddelelser, der sendes fra din organisation. Du kan ikke dekryptere krypterede meddelelser, der stammer fra uden for organisationen.

#### <a name="use-the-eac-to-create-a-rule-for-removing-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Brug EAC til at oprette en regel for at fjerne kryptering fra mailsvar, der er krypteret uden de nye OME-funktioner

1. I en webbrowser, der bruger en arbejds- eller skolekonto, som har fået administratortilladelser, skal du [logge på Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Vælg **feltet** Administrator.

3. Vælg >Microsoft 365 Administration Administration **i Exchange**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>

4. I EAC skal du gå til **Regler for mailflow** \> og **vælge Nyt** ![nyt ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Oprette en ny regel**. Du kan finde flere oplysninger om brug af [EAC Exchange Administration i Exchange Online](/exchange/exchange-admin-center).

5. Skriv **et** navn til reglen under Navn, f.eks. Fjern kryptering fra indgående mail.

6. In **Apply this rule if** select the conditions where encryption should be removed from messages, such as **The recipient is located** \> **Inside the organization**.

7. I **Gør følgende skal** du vælge **Rediger meddelelsessikkerheden Fjern** \> **den tidligere version af OME**.

8. Vælg **Gem**.

#### <a name="use-exchange-online-powershell-to-create-a-rule-to-remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Brug Exchange Online PowerShell til at oprette en regel til at fjerne kryptering fra mailsvar, der er krypteret uden de nye OME-funktioner

1. Forbind til Exchange Online PowerShell. Du kan finde flere oplysninger [Forbind Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Opret en regel ved hjælp af **New-TransportRule-cmdlet'en** , og angiv _removeOME-parameteren_ til `$true`.

   I dette eksempel fjernes krypteringen fra alle de mails, der sendes til modtagere i organisationen.

   ```powershell
   New-TransportRule -Name "Remove encryption from incoming mail" -SentToScope "InOrganization" -RemoveOME $true
   ```

   Hvor

   - Det entydige navn på den nye regel er "Fjern kryptering fra indgående mail".
   - _Parameteren SentToScope_ angiver placeringen af meddelelsens modtagere. I dette eksempel bruges værdien `InOrganization` , som angiver en af følgende:
     - Modtageren er en postkasse, mailbruger, gruppe eller mailaktiveret offentlig mappe i organisationen.
     - Modtagerens mailadresse er i et accepteret domæne, der er konfigureret som et autoritativt domæne eller en internt relædomæne i _organisationen, og_ meddelelsen blev sendt eller modtaget via en godkendt forbindelse.

Du kan finde detaljerede oplysninger om syntaks og parameter [i New-TransportRule](/powershell/module/exchange/New-TransportRule).

## <a name="sending-viewing-and-replying-to-messages-encrypted-without-the-new-capabilities"></a>Sende, vise og svare på meddelelser, der er krypteret uden de nye funktioner

Med Office 365-meddelelseskryptering krypteres mails automatisk baseret på administratordefinerede regler. En mail, der modtager en krypteret meddelelse i modtagerens indbakke med en vedhæftet HTML-fil.

Modtagerne skal følge instruktionerne i meddelelsen for at åbne den vedhæftede fil og godkende ved hjælp af en Microsoft-konto eller en arbejds- eller skolekonto, der er knyttet Office 365. Hvis modtagerne ikke har nogen konto, bliver de henvist til at oprette en Microsoft-konto, så de kan logge på for at få vist den krypterede meddelelse. Alternativt kan modtagerne vælge at få en engangskode for at få vist meddelelsen. Når modtagerne har logget på eller brugt en engangs-adgangskode, kan de se den dekrypterede meddelelse og sende et krypteret svar.

## <a name="customize-encrypted-messages-with-office-365-message-encryption"></a>Tilpasse krypterede meddelelser med Office 365-meddelelseskryptering

Som administrator Exchange Online administrator Exchange Online Protection du tilpasse dine krypterede meddelelser. Du kan f.eks. tilføje virksomhedens brand og logo, angive en introduktion og tilføje ansvarsfraskrivelsestekst i krypterede meddelelser og i den portal, hvor modtagerne får vist dine krypterede meddelelser. Ved Windows PowerShell af cmdlet'er kan du tilpasse følgende aspekter af visningsoplevelsen for modtagere af krypterede mails:

- Introduktionstekst til den mail, der indeholder den krypterede meddelelse
- Ansvarsfraskrivelsestekst for den mail, der indeholder den krypterede meddelelse
- Portaltekst, der vises i meddelelsesvisningsportalen
- Logo, der vises i mailen og visningsportalen

Du kan også vende tilbage til standardudseet og -fornemmelsen når som helst.

I følgende eksempel vises et brugerdefineret logo for ContosoPharma i den vedhæftede fil:

> [!div class="mx-imgBorder"]
> ![Eksempel på siden med krypterede meddelelser.](../media/TA-OME-3attachment2.jpg)

### <a name="to-customize-encryption-email-messages-and-the-encryption-portal-with-your-organizations-brand"></a>Sådan tilpasser du krypteringsmails og krypteringsportalen med organisationens brand

1. Forbind til Exchange Online bruge Remote PowerShell, som beskrevet i [Forbind to Exchange Online Using Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug cmdletten Set-OMEConfiguration beskrevet her: [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) , eller brug følgende tabel som vejledning.

   **Indstillinger for krypteringstilpasning**

   |Sådan tilpasser du denne funktion i krypteringsoplevelsen|Brug disse Windows PowerShell kommandoer|
   |---|---|
   |Standardtekst, der accompanies krypterede mails <p> Standardteksten vises over vejledningen til visning af krypterede meddelelser|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<string of up to 1024 characters>"` <p> **Eksempel:** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system"`|
   |Ansvarsfraskrivelse i den mail, der indeholder den krypterede meddelelse|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<your disclaimer statement, string of up to 1024 characters>"` <p> **Eksempel:** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText "This message is confidential for the use of the addressee only"`|
   |Tekst, der vises øverst i den krypterede mailvisningsportal|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<text for your portal, string of up to 128 characters>"` <p> **Eksempel:** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal"`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <Byte[]>` <p> **Eksempel:** `Set-OMEConfiguration -Identity "OME configuration" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Understøttede filformater: .png, .jpg, .bmp eller .tiff <p> Optimal størrelse på logofil: mindre end 40 KB <p> Optimal størrelse på logobillede: 170x70 pixel|

### <a name="to-remove-brand-customizations-from-encryption-email-messages-and-the-encryption-portal"></a>Sådan fjerner du brandtilpasninger fra kryptering af mails og krypteringsportalen

1. Forbind til Exchange Online bruge Remote PowerShell, som beskrevet i [Forbind to Exchange Online Using Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug Set-OMEConfiguration som beskrevet her: [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration). Hvis du vil fjerne organisationens brandede tilpasninger fra værdierne DisclaimerText, EmailText og PortalText, skal du angive værdien til en tom streng `""`. For alle billedværdier, f.eks Logo, skal du indstille værdien til `"$null"`.

   **Indstillinger for krypteringstilpasning**

   |For at gendanne denne funktion i krypteringsoplevelsen tilbage til standardtekst og -billede|Brug disse Windows PowerShell kommandoer|
   |---|---|
   |Standardtekst, der accompanies krypterede mails <p> Standardteksten vises over vejledningen til visning af krypterede meddelelser|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<empty string>"` <p> **Eksempel:** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Ansvarsfraskrivelse i den mail, der indeholder den krypterede meddelelse <p> |`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<empty string>"` <p> **Eksempel:** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Tekst, der vises øverst i den krypterede mailvisningsportal|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<empty string>"` <p> **Eksempel på at vende tilbage til standard:** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <"$null">` <p> **Eksempel på at vende tilbage til standard:** `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|

## <a name="service-information-for-legacy-office-365-message-encryption-prior-to-the-release-of-the-new-ome-capabilities"></a>Tjenesteoplysninger for ældre Office 365-meddelelseskryptering før udgivelsen af de nye OME-funktioner
<a name="LegacyServiceInfo"> </a>

Den følgende tabel indeholder tekniske detaljer for Office 365-meddelelseskryptering, før de nye OME-funktioner frigives.

|Serviceoplysninger|Beskrivelse|
|---|---|
|Krav til klientenhed|Krypterede meddelelser kan vises på alle klientenheden, så længe den vedhæftede HTML-fil kan åbnes i en moderne browser, der understøtter formularindlæg.|
|Krypteringsalgoritme og overholdelse af føderale standarder for informationsbehandling (FIPS)|Office 365-meddelelseskryptering bruger de samme krypteringsnøgler som Windows Azure Information Rights Management (IRM) og understøtter Cryptographic Mode 2 (2K-nøgle til RSA- og 256 bit-nøgle til SHA-1-systemer). Du kan finde flere oplysninger om de underliggende IRM-krypterede tilstande i [AD RMS-krypterede tilstande](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).|
|Understøttede meddelelsestyper|Office 365-meddelelseskryptering understøttes kun for elementer, der har et meddelelsesklasse-id for **IPM. Bemærk!** Du kan få mere at vide [under Elementtyper og meddelelsesklasser](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|Begrænsninger for meddelelsesstørrelse|Office 365-meddelelseskryptering kan kryptere meddelelser på op til 25 megabyte. Du kan finde flere oplysninger om begrænsninger for [meddelelsesstørrelser Exchange Online Begrænsninger](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).|
|Exchange Online politikker for opbevaring af mail|Exchange Online gemmer ikke de krypterede meddelelser.|
|Sprogsupport til Office 365-meddelelseskryptering|Office 365 meddelelseskryptering understøtter Microsoft 365 sprog, som følger: <p> Indgående mails og vedhæftede HTML-filer lokaliseres baseret på afsenderens sprogindstillinger. <p> Visningsportalen er lokaliseret baseret på modtagerens browserindstillinger. <p> Brødteksten (indholdet) i den krypterede meddelelse er ikke lokaliseret.|
|Oplysninger om beskyttelse af personlige oplysninger for OME Portal og OME Viewer-appen|Erklæringen [Office 365 messaging encryption Portal](https://privacy.microsoft.com/privacystatement) indeholder detaljerede oplysninger om, hvad Microsoft gør og ikke gør med dine private oplysninger.|

## <a name="frequently-asked-questions-about-legacy-ome"></a>Ofte stillede spørgsmål om den ældre OME
<a name="LegacyServiceInfo"> </a>

Har du spørgsmål om Office 365-meddelelseskryptering? Her er nogle svar. Hvis du ikke kan finde det, du skal bruge, kan du kigge [i Microsoft Tech Community-forummerne for at Office 365](https://techcommunity.microsoft.com/t5/Office-365/ct-p/Office365).

 **Q. Mine brugere sender krypterede mails til modtagere uden for organisationen. Er der noget, eksterne modtagere skal gøre for at kunne læse og svare på mails, der er krypteret med Office 365-meddelelseskryptering?**

Modtagere uden for organisationen, som modtager Microsoft 365 krypterede meddelelser, kan se dem på en af to måder:

- Ved at logge på med en Microsoft-konto eller en arbejds- eller skolekonto, der er knyttet Office 365.

- Ved hjælp af en engangs-adgangskode.

 **Q. Gemmes Microsoft 365 krypterede meddelelser i skyen eller på Microsoft-servere?**

Nej, de krypterede meddelelser gemmes på modtagerens mailsystem, og når modtageren åbner meddelelsen, sendes den midlertidigt til visning på Microsoft-servere. Meddelelserne gemmes ikke der.

 **Q. Kan jeg tilpasse krypterede mails med mit brand?**

Ja. Du kan bruge Windows PowerShell-cmdlet'er til at tilpasse den standardtekst, der vises øverst i krypterede mails, ansvarsfraskrivelsesteksten og det logo, du vil bruge til mailen og krypteringsportalen. Denne funktion er nu tilgængelig i OMEv2. Du kan få mere at [vide under Føj branding til krypterede meddelelser](add-your-organization-brand-to-encrypted-messages.md).

 **Q. Kræver tjenesten en licens for hver bruger i organisationen?**

Der kræves en licens til alle brugere i organisationen, der sender krypterede mails.

 **Q. Kræver eksterne modtagere abonnementer?**

Nej, eksterne modtagere kræver ikke, at et abonnement læser eller besvarer krypterede meddelelser.

 **Q. Hvordan er Office 365-meddelelseskryptering forskellig fra RMS (Rights Management Services)?**

RMS leverer information Rights Protection-funktioner til en organisations interne mails ved at levere indbyggede skabeloner, f.eks.: Videresende og Virksomhedsfortrolige. Office 365-meddelelseskryptering understøtter kryptering af mail til meddelelser, der sendes til eksterne modtagere samt interne modtagere.

 **Q. Hvordan er Office 365-meddelelseskryptering forskellig fra S/MIME?**

S/MIME er i bund og grund en krypteringsteknologi på klientsiden og kræver kompliceret certifikatstyrings- og publiceringsinfrastruktur. Office 365-meddelelseskryptering bruger regler for mailflow (også kaldet transportregler) og afhænger ikke af certifikatpublicering.

 **Q. Kan jeg læse de krypterede meddelelser over mobilenheder?**

Ja, du kan få vist meddelelser på Android og iOS ved at downloade OME Viewer-appsene fra Google Play Butik og Apple App Store. Åbn den vedhæftede HTML-fil i OME Viewer-appen, og følg derefter vejledningen for at åbne den krypterede meddelelse. For andre mobilenheder kan du åbne den vedhæftede HTML-fil, så længe din mailklient understøtter Formularindlæg.

 **Q. Krypteres svar og videresendte meddelelser?**

Ja. Svar fortsætter med at være krypteret i hele trådens varighed.

 **Q. Leverer Office 365-meddelelseskryptering lokalisering?**

Indgående mail- og HTML-indhold lokaliseres baseret på indstillinger for afsendermail. Visningsportalen er lokaliseret baseret på modtagerens browserindstillinger. Men det faktiske brødtekst (indhold) af krypteret meddelelse er ikke lokaliseret.

 **Q. Hvilken krypteringsmetode bruges til Office 365-meddelelseskryptering?**

Office 365-meddelelseskryptering bruger RMS (Rights Management Services) som sin krypteringsinfrastruktur. Den anvendte krypteringsmetode afhænger af, hvor du får de RMS-nøgler, der bruges til at kryptere og dekryptere meddelelser.

- Hvis du bruger Microsoft Azure RMS til at hente nøgler, bruges krypteret tilstand 2. Cryptographic Mode 2 er en opdateret og forbedret krypteret AD RMS-implementering. Den understøtter RSA 2048 til signatur og kryptering og understøtter SHA-256 til signatur.

- Hvis du bruger Active Directory (AD) RMS til at hente nøgler, bruges enten Cryptographic Mode 1 eller Cryptographic Mode 2. Den anvendte metode afhænger af din lokale AD RMS-installation. Cryptographic Mode 1 er den oprindelige kryptografiske AD RMS-implementering. Den understøtter RSA 1024 til signatur og kryptering og understøtter SHA-1 til signatur. Denne tilstand understøttes fortsat af alle aktuelle versioner af RMS.

Du kan finde flere oplysninger [under AD RMS-krypterede tilstande](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).

**Q. Hvorfor fortæller nogle krypterede meddelelser sig, at de kommer** fra Office365@messaging.microsoft.com?

Når der sendes et krypteret svar fra krypteringsportalen eller via OME Viewer-appen, angives den afsendende mailadresse til Office365@messaging.microsoft.com, fordi den krypterede meddelelse sendes via et Microsoft-slutpunkt. Dette hjælper med at forhindre krypterede meddelelser i at blive markeret som spam. Det viste navn på mailen og adressen i krypteringsportalen ændres ikke på grund af denne mærkning. Desuden gælder denne mærkning kun for meddelelser, der sendes via portalen, ikke via andre mailklienter.

 **Q. Jeg er Exchange-abonnent af hosted kryptering (EHE). Hvor kan jeg få mere at vide om opgraderingen til Office 365-meddelelseskryptering?**

Alle EHE-kunder er blevet opgraderet til Office 365-meddelelseskryptering. Du kan finde flere oplysninger i Exchange [Hosted Encryption Upgrade Center](../security/office-365-security/exchange-online-protection-overview.md).

 **Q. Har jeg brug for at åbne eventuelle URL-adresser, IP-adresser eller porte i min organisations firewall for at understøtte Office 365-meddelelseskryptering?**

Ja. Du skal føje URL-adresser til Exchange Online listen over tilladte for organisationen for at aktivere godkendelse for meddelelser, der er krypteret Office 365-meddelelseskryptering. Du kan finde en liste Exchange Online URL-adresser Microsoft 365 [URL-adresser og IP-adresseintervaller](../enterprise/urls-and-ip-address-ranges.md).

 **Q. Hvor mange modtagere kan jeg sende en Microsoft 365 krypteret meddelelse til?**

Modtagergrænsen er 500 modtagere pr. meddelelse, eller, når de kombineres efter udvidelse af distributionslisten, 11.980 tegn i meddelelsens Til-felt, alt efter hvad der kommer først.

 **Q. Er det muligt at tilbagekalde en meddelelse, der er sendt til en bestemt modtager?**

Nej. Du kan ikke tilbagekalde en meddelelse til en bestemt person, efter den er sendt.

 **Q. Kan jeg få vist en rapport over krypterede meddelelser, der er blevet modtaget og læst?**

Der er ikke en rapport, der viser, om en krypteret meddelelse er blevet vist, men der er tilgængelige Microsoft 365-rapporter, som du kan udnytte til at bestemme antallet af meddelelser, der matchede en bestemt regel for mailflow (også kaldet en transportregel), f.eks.

 **Q. Hvad gør Microsoft med de oplysninger, jeg angiver via OME-portalen og OME Viewer-appen?**

Erklæringen [Office 365 messaging encryption Portal](https://privacy.microsoft.com/privacystatement) indeholder detaljerede oplysninger om, hvad Microsoft gør og ikke gør med dine private oplysninger.

**Q. Hvad gør jeg, hvis jeg ikke modtager engangspasskoden, efter jeg har anmodet om den?**

Først skal du kontrollere mappen med uønsket mail eller spam i din mailklient. DKIM- og DMARC-indstillinger for din organisation kan medføre, at disse mails ender med at blive filtreret som spam.

Dernæst skal du tjekke karantæne i Security & Compliance Center. Ofte ender meddelelser, der indeholder en engangskode, især de første, din organisation modtager, i karantæne.
