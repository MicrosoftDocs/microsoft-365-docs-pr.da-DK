---
title: Føj dit brand til krypterede meddelelser
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 5/12/2022
search.appverid:
- MET150
- MOE150
ms.assetid: 7a29260d-2959-42aa-8916-feceff6ee51d
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Få mere at vide om, hvordan Office 365 globale administratorer kan anvende organisationens branding på krypterede mails & indholdet af krypteringsportalen.
ms.openlocfilehash: bf6f3b9de64185778be7eeb4da6cc8e537f0305a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637015"
---
# <a name="add-your-organizations-brand-to-your-microsoft-365-for-business-message-encryption-encrypted-messages"></a>Føj organisationens brand til dine krypterede meddelelser i Meddelelseskryptering i Microsoft 365 til virksomheder

Du kan anvende virksomhedens branding til at tilpasse udseendet af organisationens mailmeddelelser og krypteringsportalen. Du skal anvende globale administratortilladelser på din arbejds- eller skolekonto, før du kan komme i gang. Når du har disse tilladelser, kan du bruge Get-OMEConfiguration og Set-OMEConfiguration-cmdlet'er i Exchange Online PowerShell til at tilpasse disse dele af krypterede mails:

- Introduktion
- Ansvarsfraskrivelsetekst
- URL-adresse til din organisations erklæring om beskyttelse af personlige oplysninger
- Tekst i OME-portalen
- Logo, der vises i mailen og OME-portalen, eller om der overhovedet skal bruges et logo
- Baggrundsfarve i mailen og OME-portalen

Du kan også når som helst vende tilbage til standardtypografien.

Hvis du vil have mere kontrol, skal du bruge Avanceret meddelelseskryptering i Microsoft Purview til at oprette flere skabeloner til krypterede mails, der stammer fra din organisation. Brug disse skabeloner til at styre dele af slutbrugeroplevelsen. Angiv f.eks., om modtagere kan bruge Google-, Yahoo- og Microsoft-konti til at logge på krypteringsportalen. Brug skabeloner til at opfylde flere use cases, f.eks.:

- Individuelle afdelinger, f.eks. Økonomi, Salg osv.
- Forskellige produkter
- Forskellige geografiske områder eller lande
- Om du vil tillade, at mails tilbagekaldes
- Angiver, om mails, der sendes til eksterne modtagere, skal udløbe efter et angivet antal dage.

Når du har oprettet skabelonerne, kan du anvende dem på krypterede mails ved hjælp af regler for Exchange-mailflow. Hvis du har Microsoft Purview Advanced Message Encryption, kan du tilbagekalde alle mails, du har mærket, ved hjælp af disse skabeloner.

## <a name="work-with-ome-branding-templates"></a>Arbejd med OME-brandingskabeloner

Du kan redigere flere funktioner i en brandingskabelon. Du kan redigere, men ikke fjerne, standardskabelonen. Hvis du har avanceret meddelelseskryptering, kan du også oprette, redigere og fjerne brugerdefinerede skabeloner. Brug Exchange Online PowerShell til at arbejde med én brandingskabelon ad gangen.

- [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) – Rediger standardskabelonen til branding eller en brugerdefineret brandingskabelon, som du har oprettet.
- [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) – Opret kun en ny brandingskabelon, kun avanceret meddelelseskryptering.
- [Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration) – Fjern kun en brugerdefineret brandingskabelon, Avanceret meddelelseskryptering. Du kan ikke slette standardskabelonen til branding.

## <a name="modify-an-ome-branding-template"></a>Rediger en SKABELON til OME-branding

Brug Exchange Online PowerShell til at redigere én brandingskabelon ad gangen. Hvis du har avanceret meddelelseskryptering, kan du også oprette, redigere og fjerne brugerdefinerede skabeloner.

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du oprette forbindelse til Exchange Online PowerShell. Du kan finde en vejledning under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug cmdlet'en Set-OMEConfiguration som beskrevet i [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration) , eller brug følgende grafik og tabel for at få vejledning.

![Maildele, der kan tilpasses.](../media/ome-template-breakout.png)

|Sådan tilpasser du denne funktion i krypteringsoplevelsen|Brug disse kommandoer|
|---|---|
|Baggrundsfarve|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "<#RRGGBB hexadecimal color code or name value>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -BackgroundColor "#ffffff"` <p> Du kan få flere oplysninger om [baggrundsfarver i afsnittet Baggrundsfarver](#background-color-reference) senere i denne artikel.|
|Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <Byte[]>` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Understøttede filformater: .png, .jpg, .bmp eller .tiff <p> Optimal størrelse af logofil: mindre end 40 KB <p> Optimal størrelse af logobillede: 170 x 70 pixel. Hvis billedet overstiger disse dimensioner, tilpasser tjenesten størrelsen på dit logo, så det vises på portalen. Tjenesten ændrer ikke selve grafikfilen. Du opnår det bedste resultat ved at bruge den optimale størrelse.|
|Tekst ud for afsenderens navn og mailadresse|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -IntroductionText "<String up to 1024 characters>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -IntroductionText "has sent you a secure message."`|
|Tekst, der vises på knappen "Læs meddelelse"|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -ReadButtonText "<String up to 1024 characters>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -ReadButtonText "Read Secure Message."`|
|Tekst, der vises under knappen "Læs meddelelse"|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<String up to 1024 characters>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system."`|
|URL-adresse til linket til erklæringen om beskyttelse af personlige oplysninger|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PrivacyStatementURL "<URL>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -PrivacyStatementURL "https://contoso.com/privacystatement.html"`|
|Ansvarsfraskrivelse-sætning i den mail, der indeholder den krypterede meddelelse|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -DisclaimerText "<Disclaimer statement. String of up to 1024 characters.>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -DisclaimerText "This message is confidential for the use of the addressee only."`|
|Tekst, der vises øverst på den krypterede mailvisningsportal|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<Text for your portal. String of up to 128 characters.>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal."`|
|Sådan aktiverer eller deaktiverer du godkendelse med en engangskode for denne brugerdefinerede skabelon|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -OTPEnabled <$true|$false>` <p> **Eksempler:** <br/>Sådan aktiverer du engangskoder for denne brugerdefinerede skabelon <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $true` <p> Sådan deaktiverer du engangskoder for denne brugerdefinerede skabelon <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $false`|
|Sådan aktiverer eller deaktiverer du godkendelse med Microsoft-, Google- eller Yahoo-identiteter for denne brugerdefinerede skabelon|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -SocialIdSignIn <$true|$false>` <p> **Eksempler:** <br/>Sådan aktiverer du sociale id'er for denne brugerdefinerede skabelon <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $true` <p> Sådan deaktiveres sociale id'er for denne brugerdefinerede skabelon <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $false`|

## <a name="create-an-ome-branding-template-advanced-message-encryption"></a>Opret en SKABELON til OME-branding (avanceret meddelelseskryptering)

Hvis du har Microsoft Purview Advanced Message Encryption, kan du oprette brugerdefinerede brandingskabeloner for din organisation ved hjælp af cmdlet'en [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) . Når du har oprettet skabelonen, kan du ændre skabelonen ved hjælp af Set-OMEConfiguration-cmdlet'en, som beskrevet i [Rediger en OME-brandingskabelon](#modify-an-ome-branding-template). Du kan oprette flere skabeloner.

Sådan opretter du en ny brugerdefineret brandingskabelon:

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du oprette forbindelse til Exchange Online PowerShell. Du kan finde en vejledning under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug [Cmdlet'en New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) til at oprette en ny skabelon.

   ```powershell
   New-OMEConfiguration -Identity "<OMEConfigurationName>"
   ```

   Det kan f.eks.

   ```powershell
   New-OMEConfiguration -Identity "Custom branding template"
   ```

## <a name="return-the-default-branding-template-to-its-original-values"></a>Returner standardskabelonen for branding til de oprindelige værdier

Hvis du vil fjerne alle ændringer fra standardskabelonen, herunder tilpasninger af mærker osv., skal du fuldføre disse trin:

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du oprette forbindelse til Exchange Online PowerShell. Du kan finde en vejledning under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug **Set-OMEConfiguration-cmdlet'en** som beskrevet i [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration). Hvis du vil fjerne organisationens brandede tilpasninger fra værdierne DisclaimerText, EmailText og PortalText, skal du angive værdien til en tom streng, `""`. For alle billedværdier, f.eks. Logo, skal du angive værdien til `"$null"`.

   I følgende tabel beskrives standardindstillingerne for tilpasning af kryptering.

   |Sådan gendannes denne funktion i krypteringsoplevelsen til standardteksten og -billedet|Brug disse kommandoer|
   |:-----|:-----|
   |Standardtekst, der følger med krypterede mails. Standardteksten vises over instruktionerne til visning af krypterede meddelelser|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<empty string>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Ansvarsfraskrivelse-sætning i den mail, der indeholder den krypterede meddelelse|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" DisclaimerText "<empty string>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Tekst, der vises øverst på den krypterede mailvisningsportal|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<empty string>"` <p> **Eksempel på gendannelse tilbage til standard:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <"$null">` <p> **Eksempel på gendannelse tilbage til standard:** <p> `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|
   |Baggrundsfarve|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "$null">` <p> **Eksempel på gendannelse tilbage til standard:** <p> `Set-OMEConfiguration -Identity "OME configuration" -BackgroundColor $null`|

## <a name="remove-a-custom-branding-template-advanced-message-encryption"></a>Fjern en brugerdefineret brandingskabelon (avanceret meddelelseskryptering)

Du kan kun fjerne eller slette de brandingskabeloner, du har oprettet. Du kan ikke fjerne standardskabelonen til branding.

Sådan fjerner du en brugerdefineret brandingskabelon:

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, kan du oprette forbindelse til Exchange Online PowerShell. Du kan finde en vejledning under [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug cmdlet'en **Remove-OMEConfiguration** på følgende måde:

   ```powershell
   Remove-OMEConfiguration -Identity ""<OMEConfigurationName>"
   ```

   Det kan f.eks.

   ```powershell
   Remove-OMEConfiguration -Identity "Branding template 1"
   ```

   Du kan få flere oplysninger under [Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration).

## <a name="create-an-exchange-mail-flow-rule-that-applies-your-custom-branding-to-encrypted-emails"></a>Opret en regel for Exchange-mailflow, der anvender din brugerdefinerede branding på krypterede mails

> [!IMPORTANT]
> Tredjepartsprogrammer, der scanner og ændrer mails, kan forhindre, at OME-branding anvendes korrekt.

Når du enten har ændret standardskabelonen eller oprettet nye brandingskabeloner, kan du oprette exchange-regler for mailflow for at anvende din brugerdefinerede branding på baggrund af visse betingelser. Vigtigst af alt skal mailen krypteres. En sådan regel anvender brugerdefineret branding i følgende scenarier:

- Hvis mailen blev krypteret manuelt af slutbrugeren ved hjælp af Outlook eller Outlook på internettet, tidligere Outlook Web App
- Hvis mailen automatisk blev krypteret af en exchange-mailflowregel eller Microsoft Purview Forebyggelse af datatab politik

Hvis du vil sikre, at Microsoft Purview-meddelelseskryptering anvender din brugerdefinerede branding, skal du konfigurere en regel for mailflow for at kryptere dine mails. Prioriteten for krypteringsreglen skal være højere end brandingreglen, så krypteringsreglen behandles først. Hvis du opretter krypteringsreglen før brandingreglen, har krypteringsreglen som standard en højere prioritet. Du kan finde oplysninger om, hvordan du opretter en Exchange-regel for mailflow, der anvender kryptering, under [Definer regler for mailflow til kryptering af mails i Office 365](define-mail-flow-rules-to-encrypt-email.md). Du kan få oplysninger om, hvordan du angiver prioriteten for en regel for et mailflow, under [Administrer regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#set-the-priority-of-a-mail-flow-rule).

1. Log [på Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) ved hjælp af en arbejds- eller skolekonto, der er tildelt globale administratortilladelser, i en webbrowser.

2. Vælg feltet **Administration**.

3. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> skal du vælge **Administration centre** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.

4. I EAC skal du gå til **Regler for** **mailflow** \> og vælge **Nyt** ![ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Opret en ny regel**. Du kan få flere oplysninger om brug af EAC [i Exchange Administration i Exchange Online](/exchange/exchange-admin-center).

5. I **Navn** skal du skrive et navn til reglen, f.eks Branding for salgsafdelingen.

6. I **Anvend denne regel, hvis** skal du vælge betingelsen **Afsenderen er placeret i organisationen** og andre betingelser, du vil have, på listen over tilgængelige betingelser. Det kan f.eks. være, at du vil anvende en bestemt brandingskabelon på:

   - Alle krypterede mails, der sendes fra medlemmer af økonomiafdelingen
   - Krypterede mails, der er sendt med et bestemt nøgleord, f.eks. "ekstern" eller "Partner"
   - Krypterede mails, der sendes til et bestemt domæne

7. Hvis du allerede har defineret en regel for mailflow for at anvende kryptering, skal du springe dette trin over. Ellers skal du konfigurere reglen for mailflowet til at anvende kryptering ved at vælge **Rediger meddelelsessikkerheden** i **Gør følgende** og derefter vælge **Anvend Office 365 Meddelelsekryptering og rettighedsbeskyttelse**. Vælg en RMS-skabelon på listen, og vælg derefter **Tilføj handling**.

   Listen over skabeloner indeholder standardskabeloner og -indstillinger og eventuelle brugerdefinerede skabeloner, du opretter. Hvis listen er tom, skal du kontrollere, at du har konfigureret Microsoft Purview-meddelelseskryptering. Du kan finde en vejledning under [Konfigurer Microsoft Purview-meddelelseskryptering](set-up-new-message-encryption-capabilities.md). Du kan få oplysninger om standardskabelonerne under [Konfiguration og administration af skabeloner til Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). Du kan få oplysninger om indstillingen **Videresend ikke** under [Videresend ikke for mails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Du kan få oplysninger om indstillingen **Kun kryptering** under [Kryptér kun for mails](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

8. **Fra Gør følgende** skal du vælge **Rediger meddelelsessikkerheden** \> **Anvend brugerdefineret branding på OME-meddelelser**. Vælg derefter en brandingskabelon på rullelisten.

   Vælg **Tilføj handling** , hvis du vil angive en anden handling, eller vælg **Gem**, og vælg derefter **OK**.

## <a name="background-color-reference"></a>Reference til baggrundsfarve

De farvenavne, du kan bruge til baggrundsfarven, er begrænsede. I stedet for et farvenavn kan du bruge en heksadecimal kodeværdi (`#RRGGBB`). Du kan bruge en heksadecimal kodeværdi, der svarer til et farvenavn, eller du kan bruge en brugerdefineret heksadecimal kodeværdi. Sørg for at sætte heksadecimal kodeværdien i anførselstegn (f.eks. `"#f0f8ff"`).

De tilgængelige baggrundsfarvenavne og deres tilsvarende heksadecimale kodeværdier er beskrevet i følgende tabel.

|Farvenavn|Farvekode|
|---|---|
|`aliceblue`|#f0f8ff|
|`antiquewhite`|#faebd7|
|`aqua`|#00ffff|
|`aquamarine`|#7fffd4|
|`azure`|#f0ffff|
|`beige`|#f5f5dc|
|`bisque`|#ffe4c4|
|`black`|#000000|
|`blanchedalmond`|#ffebcd|
|`blue`|#0000ff|
|`blueviolet`|#8a2be2|
|`brown`|#a52a2a|
|`burlywood`|#deb887|
|`cadetblue`|#5f9ea0|
|`chartreuse`|#7fff00|
|`chocolate`|#d2691e|
|`coral`|#ff7f50|
|`cornflowerblue`|#6495ed|
|`cornsilk`|#fff8dc|
|`crimson`|#dc143c|
|`cyan`|#00ffff|
|`darkblue`|#00008b|
|`darkcyan`|#008b8b|
|`darkgoldenrod`|#b8860b|
|`darkgray`|#a9a9a9|
|`darkgreen`|#006400|
|`darkkhaki`|#bdb76b|
|`darkmagenta`|#8b008b|
|`darkolivegreen`|#556b2f|
|`darkorange`|#ff8c00|
|`darkorchid`|#9932cc|
|`darkred`|#8b0000|
|`darksalmon`|#e9967a|
|`darkseagreen`|#8fbc8f|
|`darkslateblue`|#483d8b|
|`darkslategray`|#2f4f4f|
|`darkturquoise`|#00ced1|
|`darkviolet`|#9400d3|
|`deeppink`|#ff1493|
|`deepskyblue`|#00bfff|
|`dimgray`|#696969|
|`dodgerblue`|#1e90ff|
|`firebrick`|#b22222|
|`floralwhite`|#fffaf0|
|`forestgreen`|#228b22|
|`fuchsia`|#ff00ff|
|`gainsboro`|#dcdcdc|
|`ghostwhite`|#f8f8ff|
|`gold`|#ffd700|
|`goldenrod`|#daa520|
|`gray`|#808080|
|`green`|#008000|
|`greenyellow`|#adff2f|
|`honeydew`|#f0fff0|
|`hotpink`|#ff69b4|
|`indianred`|#cd5c5c|
|`indigo`|#4b0082|
|`ivory`|#fffff0|
|`khaki`|#f0e68c|
|`lavender`|#e6e6fa|
|`lavenderblush`|#fff0f5|
|`lawngreen`|#7cfc00|
|`lemonchiffon`|#fffacd|
|`lightblue`|#add8e6|
|`lightcoral`|#f08080|
|`lightcyan`|#e0ffff|
|`lightgoldenrodyellow`|#fafad2|
|`lightgray`|#d3d3d3|
|`lightgrey`|#d3d3d3|
|`lightgreen`|#90ee90|
|`lightpink`|#ffb6c1|
|`lightsalmon`|#ffa07a|
|`lightseagreen`|#20b2aa|
|`lightskyblue`|#87cefa|
|`lightslategray`|#778899|
|`lightsteelblue`|#b0c4de|
|`lightyellow`|#ffffe0|
|`lime`|#00ff00|
|`limegreen`|#32cd32|
|`linen`|#faf0e6|
|`magenta`|#ff00ff|
|`maroon`|#800000|
|`mediumaquamarine`|#66cdaa|
|`mediumblue`|#0000cd|
|`mediumorchid`|#ba55d3|
|`mediumpurple`|#9370db|
|`mediumseagreen`|#3cb371|
|`mediumslateblue`|#7b68ee|
|`mediumspringgreen`|#00fa9a|
|`mediumturquoise`|#48d1cc|
|`mediumvioletred`|#c71585|
|`midnightblue`|#191970|
|`mintcream`|#f5fffa|
|`mistyrose`|#ffe4e1|
|`moccasin`|#ffe4b5|
|`navajowhite`|#ffdead|
|`navy`|#000080|
|`oldlace`|#fdf5e6|
|`olive`|#808000|
|`olivedrab`|#6b8e23|
|`orange`|#ffa500|
|`orangered`|#ff4500|
|`orchid`|#da70d6|
|`palegoldenrod`|#eee8aa|
|`palegreen`|#98fb98|
|`paleturquoise`|#afeeee|
|`palevioletred`|#db7093|
|`papayawhip`|#ffefd5|
|`peachpuff`|#ffdab9|
|`peru`|#cd853f|
|`pink`|#ffc0cb|
|`plum`|#dda0dd|
|`powderblue`|#b0e0e6|
|`purple`|#800080|
|`red`|#ff0000|
|`rosybrown`|#bc8f8f|
|`royalblue`|#4169e1|
|`saddlebrown`|#8b4513|
|`salmon`|#fa8072|
|`sandybrown`|#f4a460|
|`seagreen`|#00ff00|
|`seashell`|#fff5ee|
|`sienna`|#a0522d|
|`silver`|#c0c0c0|
|`skyblue`|#87ceeb|
|`slateblue`|#6a5acd|
|`slategray`|#708090|
|`snow`|#fffafa|
|`springgreen`|#00ff7f|
|`steelblue`|#4682b4|
|`tan`|#d2b48c|
|`teal`|#008080|
|`thistle`|#d8bfd8|
|`tomato`|#ff6347|
|`turquoise`|#40e0d0|
|`violet`|#ee82ee|
|`wheat`|#f5deb3|
|`white`|#ffffff|
|`whitesmoke`|#f5f5f5|
|`yellow`|#ffff00|
|`yellowgreen`|#9acd32|
