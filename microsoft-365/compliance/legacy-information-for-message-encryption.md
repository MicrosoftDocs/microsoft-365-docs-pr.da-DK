---
title: Ældre oplysninger om Office 365-meddelelseskryptering
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
description: Forstå, hvordan du kan overføre ældre filer til Office 365 OME (Message Encryption) for din organisation.
ms.openlocfilehash: b34ccbcf077238ba3caee9da3b337cd0d32cf458
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642519"
---
# <a name="legacy-information-for-office-365-message-encryption"></a>Ældre oplysninger om Office 365-meddelelseskryptering

Hvis du endnu ikke har flyttet din organisation til Microsoft Purview-meddelelseskryptering, men du allerede har installeret OME, gælder oplysningerne i denne artikel for din organisation. Microsoft anbefaler, at du planlægger at flytte til Microsoft Purview-meddelelseskryptering, så snart det er rimeligt for din organisation. Du kan finde en vejledning under [Konfigurer Microsoft Purview-meddelelseskryptering](set-up-new-message-encryption-capabilities.md). Hvis du vil vide mere om, hvordan den nye meddelelseskryptering først, skal du se [Meddelelsekryptering](ome.md). Resten af denne artikel refererer til OME-funktionsmåde før udgivelsen af Microsoft Purview-meddelelseskryptering.

Med Office 365 meddelelseskryptering kan din organisation sende og modtage krypterede mails mellem personer i og uden for organisationen. Office 365 Meddelelsekryptering fungerer sammen med Outlook.com, Yahoo, Gmail og andre mailtjenester. Kryptering af mailmeddelelser hjælper med at sikre, at det kun er modtagere, der er beregnet til at få vist meddelelsesindhold.

Her er nogle eksempler:

- En bankmedarbejder sender kreditkortopgørelser til kunder
- En repræsentant for et forsikringsselskab giver forsikringsoplysninger til kunder
- En realkreditmægler anmoder om finansielle oplysninger fra en kunde for en låneansøgning
- En sundhedsplejeudbyder sender oplysninger om sundhedspleje til patienter
- En advokat sender fortrolige oplysninger til en kunde eller en anden advokat

## <a name="how-office-365-message-encryption-works-without-the-new-capabilities"></a>Sådan fungerer Office 365 meddelelseskryptering uden de nye funktioner

Office 365 Message Encryption er en onlinetjeneste, der er baseret på Microsoft Azure Rights Management (Azure RMS). Med Azure RMS kan administratorer definere regler for mailflow for at bestemme betingelserne for kryptering. En regel kan f.eks. kræve kryptering af alle meddelelser, der er adresseret til en bestemt modtager.

Når nogen sender en mail i Exchange Online, der svarer til en krypteringsregel, sendes meddelelsen med en vedhæftet HTML-fil. Modtageren åbner den vedhæftede HTML-fil og følger vejledningen i at få vist den krypterede meddelelse på portalen Office 365 Meddelelsekryptering. Modtageren kan vælge at få vist meddelelsen ved at logge på med en Microsoft-konto eller et arbejde eller en skole, der er knyttet til Office 365, eller ved hjælp af en engangskode. Begge indstillinger er med til at sikre, at det kun er den ønskede modtager, der kan få vist den krypterede meddelelse. Denne proces er meget anderledes for Microsoft Purview-meddelelseskryptering.

I følgende diagram opsummeres passagen af en mail via krypterings- og dekrypteringsprocessen.

![Diagram, der viser stien til en krypteret mail.](../media/O365-Office365MessageEncryption-Concept.png)

Du kan få flere oplysninger under [Tjenesteoplysninger om ældre Office 365 Meddelelseskryptering før udgivelsen af Microsoft Purview-meddelelseskryptering](legacy-information-for-message-encryption.md#LegacyServiceInfo).

## <a name="defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-microsoft-purview-message-encryption"></a>Definition af regler for mailflow for Office 365 Meddelelsekryptering, der ikke bruger Microsoft Purview-meddelelseskryptering

Hvis du vil aktivere Office 365 meddelelseskryptering uden de nye funktioner, skal Exchange Online og Exchange Online Protection administratorer definere regler for Exchange-mailflow. Disse regler bestemmer, under hvilke betingelser mails skal krypteres, samt betingelser for fjernelse af meddelelseskryptering. Når der er angivet en krypteringshandling for en regel, udfører tjenesten handlingen på alle meddelelser, der opfylder regelbetingelserne, før meddelelserne sendes.

Regler for mailflow er fleksible, så du kan kombinere betingelser, så du kan opfylde specifikke sikkerhedskrav i en enkelt regel. Du kan f.eks. oprette en regel for at kryptere alle meddelelser, der indeholder angivne nøgleord og er adresseret til eksterne modtagere. Office 365 Meddelelseskryptering krypterer også svar fra modtagere af krypterede mails, og du kan oprette en regel, der dekrypterer disse svar som en hjælp for dine mailbrugere. På den måde behøver brugerne i din organisation ikke at logge på krypteringsportalen for at få vist svar.

Du kan finde flere oplysninger om, hvordan du opretter regler for Exchange-mailflow under [Definer regler for Office 365 meddelelsekryptering](define-mail-flow-rules-to-encrypt-email.md).

### <a name="use-the-eac-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-microsoft-purview-message-encryption"></a>Brug EAC til at oprette en regel for mailflow til kryptering af mails uden Microsoft Purview-meddelelseskryptering

1. Log [på Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) ved hjælp af en arbejds- eller skolekonto, der er tildelt globale administratortilladelser, i en webbrowser.

2. Vælg feltet **Administration**.

3. I Microsoft 365 Administration skal du vælge **Administration centre** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.

4. I EAC skal du gå til **Regler for** **mailflow** \> og vælge **Nyt** ![ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Opret en ny regel**. Du kan få flere oplysninger om brug af EAC [i Exchange Administration i Exchange Online](/exchange/exchange-admin-center).

5. Skriv et navn til reglen i **Navn**, f.eks. Kryptér mail for DrToniRamos@hotmail.com.

6. I **Anvend denne regel, hvis** du vælger en betingelse, og angiv en værdi, hvis det er nødvendigt. Hvis du f.eks. vil kryptere meddelelser, der skal DrToniRamos@hotmail.com:

   1. Vælg **modtageren er i** **Anvend denne regel, hvis**.

   2. Vælg et eksisterende navn på listen over kontakter, eller skriv en ny mailadresse i feltet **Afkrydsningsfelter** .

      - Hvis du vil vælge et eksisterende navn, skal du vælge det på listen og derefter klikke på **OK**.

      - Hvis du vil angive et nyt navn, skal du skrive en mailadresse i **afkrydsningsfeltet Afkrydsningsfelter** og derefter markere **afkrydsningsfeltet ok** \> **.**

7. Hvis du vil tilføje flere betingelser, skal du vælge **Flere indstillinger** og derefter vælge **Tilføj betingelse** og vælge på listen.

   Hvis du f.eks. kun vil anvende reglen, hvis modtageren er uden for din organisation, skal du vælge **Tilføj betingelse** og derefter vælge **Modtageren er ekstern/intern** \> **Uden for organisationen** \> **OK**.

8. Hvis du vil aktivere kryptering uden at bruge de nye OME-funktioner, skal du i **Gør følgende** vælge **Rediger meddelelsessikkerheden** \> **Anvend den tidligere version af OME** og derefter vælge **Gem**.

   Hvis du får vist en fejl om, at IRM-licenser ikke er aktiveret, bruger du ikke ældre OME.

9. (Valgfrit) Vælg **Tilføj handling** for at angive en anden handling.

### <a name="use-exchange-online-powershell-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>Brug Exchange Online PowerShell til at oprette en mailflowregel til kryptering af mails uden de nye OME-funktioner

1. Opret forbindelse til Exchange Online PowerShell. Du kan få flere oplysninger under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Opret en regel ved hjælp af **cmdlet'en New-TransportRule** , og angiv parameteren _ApplyOME_ til `$true`.

   I dette eksempel kræves det, at alle mails, der sendes til DrToniRamos@hotmail.com, skal krypteres.

   ```powershell
   New-TransportRule -Name "Encrypt rule for Dr Toni Ramos" -SentTo "DrToniRamos@hotmail.com" -SentToScope "NotinOrganization" -ApplyOME $true
   ```

   Hvor

   - Det entydige navn på den nye regel er "Kryptér regel for Dr. Toni Ramos".
   - Parameteren _SentTo_ angiver meddelelsesmodtagerne (identificeret ved navn, mailadresse, entydigt navn osv.). I dette eksempel identificeres modtageren af mailadressen "DrToniRamos@hotmail.com".
   - Parameteren _SentToScope_ angiver placeringen af meddelelsesmodtagerne. I dette eksempel er modtagerens postkasse i Hotmail og er ikke en del af organisationen, så værdien `NotInOrganization` bruges.

   Du kan finde detaljerede oplysninger om syntaks og parametre under [New-TransportRule](/powershell/module/exchange/New-TransportRule).

### <a name="remove-encryption-from-email-replies-encrypted-without-microsoft-purview-message-encryption"></a>Fjern kryptering fra mailsvar krypteret uden Microsoft Purview-meddelelseskryptering

Når dine mailbrugere sender krypterede meddelelser, kan modtagere af disse meddelelser svare med krypterede svar. Du kan oprette regler for mailflow for automatisk at fjerne kryptering fra svar, så mailbrugere i din organisation ikke behøver at logge på krypteringsportalen for at få dem vist. Du kan bruge EAC- eller Exchange Online PowerShell-cmdlet'er til at definere disse regler. Du kan dekryptere meddelelser, der sendes fra din organisation, eller meddelelser, der er svar på meddelelser, der sendes fra din organisation. Du kan ikke dekryptere krypterede meddelelser, der stammer fra uden for organisationen.

#### <a name="use-the-eac-to-create-a-rule-for-removing-encryption-from-email-replies-encrypted-without-microsoft-purview-message-encryption"></a>Brug EAC til at oprette en regel for fjernelse af kryptering fra mailsvar krypteret uden Microsoft Purview-meddelelseskryptering

1. Log [på Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) ved hjælp af en arbejds- eller skolekonto, der er tildelt administratortilladelser, i en webbrowser.

2. Vælg feltet **Administration**.

3. I Microsoft 365 Administration skal du vælge **Administration centre** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.

4. I EAC skal du gå til **Regler for** **mailflow** \> og vælge **Nyt** ![ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Opret en ny regel**. Du kan få flere oplysninger om brug af EAC [i Exchange Administration i Exchange Online](/exchange/exchange-admin-center).

5. Skriv et navn til reglen i **Navn**, f.eks. Fjern kryptering fra indgående post.

6. I **Anvend denne regel, hvis** du vælger de betingelser, hvor kryptering skal fjernes fra meddelelser, f.eks **. Modtageren er placeret** \> **i organisationen**.

7. **I Gør følgende** skal du vælge **Rediger meddelelsessikkerheden** \> **Fjern den tidligere version af OME**.

8. Vælg **Gem**.

#### <a name="use-exchange-online-powershell-to-create-a-rule-to-remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Brug Exchange Online PowerShell til at oprette en regel for at fjerne kryptering fra mailsvar krypteret uden de nye OME-funktioner

1. Opret forbindelse til Exchange Online PowerShell. Du kan få flere oplysninger under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Opret en regel ved hjælp af **cmdlet'en New-TransportRule** , og angiv parameteren _RemoveOME_ til `$true`.

   I dette eksempel fjernes krypteringen fra alle mails, der sendes til modtagere i organisationen.

   ```powershell
   New-TransportRule -Name "Remove encryption from incoming mail" -SentToScope "InOrganization" -RemoveOME $true
   ```

   Hvor

   - Det entydige navn på den nye regel er "Fjern kryptering fra indgående post".
   - Parameteren _SentToScope_ angiver placeringen af meddelelsesmodtagerne. I dette eksempel bruges værdiværdien `InOrganization` , hvilket angiver en af følgende:
     - Modtageren er en postkasse, en mailbruger, en gruppe eller en mailaktiveret offentlig mappe i din organisation.
     - Modtagerens mailadresse er i et accepteret domæne, der er konfigureret som et autoritativt domæne eller et internt relædomæne i din organisation, _og_ meddelelsen blev sendt eller modtaget via en godkendt forbindelse.

Du kan finde detaljerede oplysninger om syntaks og parametre under [New-TransportRule](/powershell/module/exchange/New-TransportRule).

## <a name="sending-viewing-and-replying-to-messages-encrypted-without-the-new-capabilities"></a>Afsendelse, visning og svar på meddelelser, der er krypteret uden de nye funktioner

Med Office 365 meddelelseskryptering krypteres mails automatisk baseret på administratordefinerede regler. En mail, der indeholder en krypteret meddelelse, modtages i modtagerens indbakke med en vedhæftet HTML-fil.

Modtagerne følger vejledningen i meddelelsen for at åbne den vedhæftede fil og godkende ved hjælp af en Microsoft-konto eller et arbejde eller en skole, der er knyttet til Office 365. Hvis modtagerne ikke har nogen af kontiene, bliver de bedt om at oprette en Microsoft-konto, hvor de kan logge på for at få vist den krypterede meddelelse. Modtagere kan også vælge at få vist meddelelsen med en engangskode. Når modtagerne har logget på eller brugt en engangskode, kan de få vist den dekrypterede meddelelse og sende et krypteret svar.

## <a name="customize-encrypted-messages-with-office-365-message-encryption"></a>Tilpas krypterede meddelelser med Office 365 meddelelseskryptering

Som Exchange Online og Exchange Online Protection administrator kan du tilpasse dine krypterede meddelelser. Du kan f.eks. tilføje firmaets brand og logo, angive en introduktion og tilføje ansvarsfraskrivelsetekst i krypterede meddelelser og på den portal, hvor modtagerne får vist dine krypterede meddelelser. Ved hjælp af Exchange Online PowerShell-cmdlet'er kan du tilpasse følgende aspekter af visningsoplevelsen for modtagere af krypterede mails:

- Introduktion til den mail, der indeholder den krypterede meddelelse
- Ansvarsfraskrivelsetekst i den mail, der indeholder den krypterede meddelelse
- Portaltekst, der vises i meddelelsesvisningsportalen
- Logo, der vises i mailen og visningsportalen

Du kan også når som helst vende tilbage til standardtypografien.

I følgende eksempel vises et brugerdefineret logo for ContosoPharma i den vedhæftede fil:

> [!div class="mx-imgBorder"]
> ![Eksempel på visningens krypterede meddelelsesside.](../media/TA-OME-3attachment2.jpg)

### <a name="to-customize-encryption-email-messages-and-the-encryption-portal-with-your-organizations-brand"></a>Sådan tilpasser du krypteringsmailmeddelelser og krypteringsportalen med din organisations brand

1. [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug Set-OMEConfiguration-cmdlet'en som beskrevet her: [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) , eller brug følgende tabel for at få vejledning.

   **Indstillinger for tilpasning af kryptering**

   |Sådan tilpasser du denne funktion i krypteringsoplevelsen|Brug disse Exchange Online PowerShell-kommandoer|
   |---|---|
   |Standardtekst, der følger med krypterede mails <p> Standardteksten vises over instruktionerne til visning af krypterede meddelelser|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<string of up to 1024 characters>"` <p> **Eksempel:** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system"`|
   |Ansvarsfraskrivelse-sætning i den mail, der indeholder den krypterede meddelelse|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<your disclaimer statement, string of up to 1024 characters>"` <p> **Eksempel:** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText "This message is confidential for the use of the addressee only"`|
   |Tekst, der vises øverst på den krypterede mailvisningsportal|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<text for your portal, string of up to 128 characters>"` <p> **Eksempel:** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal"`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <Byte[]>` <p> **Eksempel:** `Set-OMEConfiguration -Identity "OME configuration" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Understøttede filformater: .png, .jpg, .bmp eller .tiff <p> Optimal størrelse af logofil: mindre end 40 KB <p> Optimal størrelse af logobillede: 170 x 70 pixel|

### <a name="to-remove-brand-customizations-from-encryption-email-messages-and-the-encryption-portal"></a>Sådan fjerner du brandtilpasninger fra krypteringsmailmeddelelser og krypteringsportalen

1. [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug cmdlet'en Set-OMEConfiguration som beskrevet her: [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration). Hvis du vil fjerne organisationens brandede tilpasninger fra værdierne DisclaimerText, EmailText og PortalText, skal du angive værdien til en tom streng, `""`. For alle billedværdier, f.eks. Logo, skal du angive værdien til `"$null"`.

   **Indstillinger for tilpasning af kryptering**

   |Sådan gendannes denne funktion i krypteringsoplevelsen til standardteksten og -billedet|Brug disse Exchange Online PowerShell-kommandoer|
   |---|---|
   |Standardtekst, der følger med krypterede mails <p> Standardteksten vises over instruktionerne til visning af krypterede meddelelser|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<empty string>"` <p> **Eksempel:** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Ansvarsfraskrivelse-sætning i den mail, der indeholder den krypterede meddelelse <p> |`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<empty string>"` <p> **Eksempel:** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Tekst, der vises øverst på den krypterede mailvisningsportal|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<empty string>"` <p> **Eksempel på gendannelse tilbage til standard:** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <"$null">` <p> **Eksempel på gendannelse tilbage til standard:** `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|

## <a name="service-information-for-legacy-office-365-message-encryption-prior-to-the-release-of-the-new-ome-capabilities"></a>Tjenesteoplysninger for ældre Office 365 meddelelseskryptering før udgivelsen af de nye OME-funktioner
<a name="LegacyServiceInfo"> </a>

Følgende tabel indeholder tekniske oplysninger om tjenesten Office 365 Meddelelsekryptering før udgivelsen af Microsoft Purview-meddelelseskryptering.

|Tjenesteoplysninger|Beskrivelse|
|---|---|
|Krav til klientenhed|Krypterede meddelelser kan vises på en hvilken som helst klientenhed, så længe den vedhæftede HTML-fil kan åbnes i en moderne browser, der understøtter Formularindlæg.|
|Krypteringsalgoritme og FIPS-overholdelse (Federal Information Processing Standards)|Office 365 Meddelelseskryptering bruger de samme krypteringsnøgler som Windows Azure Information Rights Management (IRM) og understøtter Cryptographic Mode 2 (2K-nøgle til RSA og 256 bitnøgle til SHA-1-systemer). Du kan få flere oplysninger om de underliggende kryptografiske IRM-tilstande i [AD RMS-kryptografiske tilstande](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).|
|Understøttede meddelelsestyper|Office 365 Meddelelseskryptering understøttes kun for elementer, der har meddelelsesklasse-id'et **IPM. Bemærk.** Du kan få flere oplysninger under [Elementtyper og meddelelsesklasser](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|Grænser for meddelelsesstørrelse|Office 365 Meddelelsekryptering kan kryptere meddelelser på op til 25 megabyte. Du kan finde flere oplysninger om grænser for meddelelsesstørrelser [under Exchange Online Grænser](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).|
|Exchange Online politikker for mailopbevaring|Exchange Online gemmer ikke de krypterede meddelelser.|
|Understøttelse af sprog for Office 365 meddelelsekryptering|Office 365 Meddelelsekryptering understøtter Microsoft 365-sprog på følgende måde: <p> Indgående mails og vedhæftede HTML-filer lokaliseres på baggrund af afsenderens sprogindstillinger. <p> Visningsportalen lokaliseres på baggrund af modtagerens browserindstillinger. <p> Brødteksten (indholdet) i den krypterede meddelelse lokaliseres ikke.|
|Oplysninger om beskyttelse af personlige oplysninger for OME-portalen og OME Viewer-appen|[Erklæringen om beskyttelse af personlige oplysninger i Office 365 Messaging Encryption Portal](https://privacy.microsoft.com/privacystatement) indeholder detaljerede oplysninger om, hvad Microsoft gør og ikke gør med dine private oplysninger.|

## <a name="frequently-asked-questions-about-legacy-ome"></a>Ofte stillede spørgsmål om ældre OME
<a name="LegacyServiceInfo"> </a>

Har du spørgsmål om Office 365 meddelelseskryptering? Her er nogle svar. Hvis du ikke kan finde det, du har brug for, kan du se [Microsoft Tech Community fora for Office 365](https://techcommunity.microsoft.com/t5/Office-365/ct-p/Office365).

 **Q. Mine brugere sender krypterede mails til modtagere uden for vores organisation. Er der noget, eksterne modtagere skal gøre for at læse og besvare mails, der er krypteret med Office 365 Meddelelseskryptering?**

Modtagere uden for din organisation, der modtager krypterede Microsoft 365-meddelelser, kan få dem vist på to måder:

- Ved at logge på med en Microsoft-konto eller en arbejds- eller skolekonto, der er knyttet til Office 365.

- Ved hjælp af en engangskode.

 **Q. Gemmes Microsoft 365-krypterede meddelelser i skyen eller på Microsoft-servere?**

Nej, de krypterede meddelelser opbevares på modtagerens mailsystem, og når modtageren åbner meddelelsen, sendes den midlertidigt til visning på Microsoft-servere. Meddelelserne gemmes ikke der.

 **Q. Kan jeg tilpasse krypterede mails med mit brand?**

Ja. Du kan bruge Exchange Online PowerShell-cmdlet'er til at tilpasse den standardtekst, der vises øverst i krypterede mails, ansvarsfraskrivelseteksten og det logo, du vil bruge til mailen og krypteringsportalen. Denne funktion er nu tilgængelig i OMEv2. Du kan finde flere oplysninger under [Føj branding til krypterede meddelelser](add-your-organization-brand-to-encrypted-messages.md).

 **Q. Kræver tjenesten en licens til alle brugere i organisationen?**

Der kræves en licens til alle brugere i organisationen, der sender krypterede mails.

 **Q. Kræver eksterne modtagere abonnementer?**

Nej, eksterne modtagere kræver ikke et abonnement for at læse eller besvare krypterede meddelelser.

 **Q. Hvordan adskiller Office 365 meddelelseskryptering sig fra RMS (Rights Management Services)?**

RMS leverer informationsrettighedersbeskyttelsesfunktioner til en organisations interne mails ved at angive indbyggede skabeloner, f.eks.: Videresend ikke og Firmafortrolige. Office 365 Meddelelsekryptering understøtter kryptering af mails for meddelelser, der sendes til eksterne modtagere samt interne modtagere.

 **Q. Hvordan adskiller Office 365 meddelelseskryptering sig fra S/MIME?**

S/MIME er i bund og grund en krypteringsteknologi på klientsiden og kræver kompliceret certifikatadministration og publiceringsinfrastruktur. Office 365 Meddelelsekryptering bruger regler for mailflows (også kaldet transportregler) og er ikke afhængige af certifikatudgivelse.

 **Q. Kan jeg læse de krypterede meddelelser via mobilenheder?**

Ja, du kan få vist meddelelser på Android og iOS ved at downloade OME Viewer-apps fra Google Play Butik og Apple App Store. Åbn den vedhæftede HTML-fil i OME Viewer-appen, og følg derefter vejledningen for at åbne den krypterede meddelelse. For andre mobilenheder kan du åbne den vedhæftede HTML-fil, så længe din mailklient understøtter Formularindlæg.

 **Q. Krypteres svar og videresendte meddelelser?**

Ja. Svar krypteres fortsat under hele trådens varighed.

 **Q. Leverer Office 365 meddelelseskryptering lokalisering?**

Indgående mail og HTML-indhold lokaliseres baseret på indstillinger for afsendermail. Visningsportalen er lokaliseret på baggrund af modtagerens browserindstillinger. Den faktiske brødtekst (indholdet) i den krypterede meddelelse lokaliseres dog ikke.

 **Q. Hvilken krypteringsmetode bruges til Office 365 meddelelseskryptering?**

Office 365 Message Encryption bruger RMS (Rights Management Services) som krypteringsinfrastruktur. Den anvendte krypteringsmetode afhænger af, hvor du henter de RMS-nøgler, der bruges til at kryptere og dekryptere meddelelser.

- Hvis du bruger Microsoft Azure RMS til at hente nøglerne, bruges Cryptographic Mode 2. Cryptographic Mode 2 er en opdateret og forbedret implementering af AD RMS-kryptografi. Den understøtter RSA 2048 til signatur og kryptering og understøtter SHA-256 som signatur.

- Hvis du bruger AD (Active Directory) RMS til at hente nøglerne, bruges enten Cryptographic Mode 1 eller Cryptographic Mode 2. Den anvendte metode afhænger af AD RMS-installationen i det lokale miljø. Cryptographic Mode 1 er den oprindelige AD RMS-kryptografiske implementering. Den understøtter RSA 1024 til signatur og kryptering og understøtter SHA-1 som signatur. Denne tilstand understøttes fortsat af alle aktuelle versioner af RMS.

Du kan få flere oplysninger under [Kryptografiske AD RMS-tilstande](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).

**Q. Hvorfor siger nogle krypterede meddelelser, at de kommer fra** Office365@messaging.microsoft.com?

Når der sendes et krypteret svar fra krypteringsportalen eller via OME Viewer-appen, angives den afsendende mailadresse til Office365@messaging.microsoft.com, fordi den krypterede meddelelse sendes via et Microsoft-slutpunkt. Dette hjælper med at forhindre, at krypterede meddelelser markeres som spam. Det viste navn på mailen og adressen i krypteringsportalen ændres ikke på grund af denne mærkat. Denne mærkning gælder også kun for meddelelser, der sendes via portalen og ikke via nogen anden mailklient.

 **Q. Jeg er en EHE-abonnent (Exchange Hosted Encryption). Hvor kan jeg få mere at vide om opgraderingen til Office 365 meddelelseskryptering?**

Alle EHE-kunder er blevet opgraderet til Office 365 Meddelelseskryptering. Du kan finde flere oplysninger i [Exchange Hosted Encryption Upgrade Center](../security/office-365-security/exchange-online-protection-overview.md).

 **Q. Skal jeg åbne URL-adresser, IP-adresser eller porte i organisationens firewall for at understøtte Office 365 meddelelseskryptering?**

Ja. Du skal føje URL-adresser til Exchange Online til listen over tilladte for din organisation for at aktivere godkendelse af meddelelser, der er krypteret af Office 365 Meddelelsekryptering. Du kan finde en liste over Exchange Online [URL-adresser i Microsoft 365 URL-adresser og IP-adresseområder](../enterprise/urls-and-ip-address-ranges.md).

 **Q. Hvor mange modtagere kan jeg sende en krypteret Meddelelse til Microsoft 365 til?**

Modtagergrænsen er 500 modtagere pr. meddelelse, eller 11.980 tegn i feltet **Til** i meddelelsen, afhængigt af hvad der kommer først, når den kombineres efter distributionslistens udvidelse.

 **Q. Er det muligt at tilbagekalde en meddelelse, der er sendt til en bestemt modtager?**

Nej. Du kan ikke tilbagekalde en meddelelse til en bestemt person, når den er sendt.

 **Q. Kan jeg få vist en rapport over krypterede meddelelser, der er modtaget og læst?**

Der er ikke en rapport, der viser, om en krypteret meddelelse er blevet vist, men der er Microsoft 365-rapporter tilgængelige, som du kan bruge til at bestemme antallet af meddelelser, der matcher en bestemt regel for et mailflow (også kendt som en transportregel), f.eks.

 **Q. Hvad gør Microsoft med de oplysninger, jeg giver via OME-portalen og OME Viewer-appen?**

[Erklæringen om beskyttelse af personlige oplysninger i Office 365 Messaging Encryption Portal](https://privacy.microsoft.com/privacystatement) indeholder detaljerede oplysninger om, hvad Microsoft gør og ikke gør med dine private oplysninger.

**Q. Hvad gør jeg, hvis jeg ikke modtager engangspasskoden, efter jeg har anmodet om den?**

Først skal du kontrollere mappen med uønsket post eller spam i din mailklient. DKIM- og DMARC-indstillinger for din organisation kan medføre, at disse mails ender filtreret som spam.

Derefter skal du kontrollere karantænen i Security & Compliance Center. Meddelelser, der indeholder en engangskode, især de første, din organisation modtager, ender ofte i karantæne.
