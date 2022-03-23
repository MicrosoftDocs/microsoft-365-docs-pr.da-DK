---
title: Føj organisationens brand til dine krypterede meddelelser
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 4/1/2020
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
description: Få mere Office 365, hvordan globale administratorer kan anvende organisationens branding på krypterede mails & indholdet af krypteringsportalen.
ms.openlocfilehash: b96f87886b6f1dc5ca78de068b86dbbcfb9e460d
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/29/2022
ms.locfileid: "63589123"
---
# <a name="add-your-organizations-brand-to-your-microsoft-365-for-business-message-encryption-encrypted-messages"></a>Føj din organisations brand til din virksomheds Microsoft 365 meddelelseskryptering af krypterede meddelelser

Du kan anvende firmabranding til at tilpasse udseendet af organisationens mails og krypteringsportalen. Du skal anvende globale administratortilladelser til din arbejds- eller skolekonto, før du kan komme i gang. Når du har disse tilladelser, kan du bruge Get-OMEConfiguration og Set-OMEConfiguration Windows PowerShell til at tilpasse disse dele af krypterede mails:

- Introduktionstekst
- Ansvarsfraskrivelsestekst
- URL-adresse til din organisations erklæring om beskyttelse af personlige oplysninger
- Tekst i OME-portalen
- Logo, der vises i mailen og OME-portalen, eller om der overhovedet skal bruges et logo
- Baggrundsfarve i mailen og OME-portalen

Du kan også vende tilbage til standardudseet og -fornemmelsen når som helst.

Hvis du vil have mere kontrol, kan du bruge Avanceret kryptering af meddelelser i Office 365 til at oprette flere skabeloner til krypterede mails, der stammer fra din organisation. Brug disse skabeloner til at styre dele af slutbrugeroplevelsen. Angiv f.eks., om modtagerne kan bruge Google-, Yahoo- og Microsoft-konti til at logge på krypteringsportalen. Brug skabeloner til at opfylde flere use cases, f.eks.:

- Individuelle afdelinger, f.eks. Økonomi, Salg osv.
- Forskellige produkter
- Forskellige geografiske områder eller lande
- Om du vil tillade, at mails tilbagekaldes
- Om du ønsker, at mails, der sendes til eksterne modtagere, skal udløbe efter et angivet antal dage.

Når du har oprettet skabelonerne, kan du anvende dem på krypterede mails ved hjælp Exchange regler for mailflow. Hvis du har Avanceret kryptering af meddelelser i Office 365, kan du tilbagekalde alle mails, som du har brandet, ved hjælp af disse skabeloner.

## <a name="work-with-ome-branding-templates"></a>Arbejde med OME-brandingskabeloner

Du kan ændre flere funktioner i en brandingskabelon. Du kan ændre standardskabelonen, men ikke fjerne den. Hvis du har avanceret meddelelseskryptering, kan du også oprette, redigere og fjerne brugerdefinerede skabeloner. Brug Windows PowerShell til at arbejde med én brandingskabelon ad gangen.

- [Set-OMEConfiguration – Rediger](/powershell/module/exchange/set-omeconfiguration) standardbrandingskabelonen eller en brugerdefineret brandingskabelon, du har oprettet.
- [Ny OMEConfiguration – Opret](/powershell/module/exchange/new-omeconfiguration) en ny brandingskabelon, kun avanceret meddelelseskryptering.
- [Remove-OMEConfiguration – Fjern](/powershell/module/exchange/remove-omeconfiguration) en brugerdefineret brandingskabelon, kun avanceret meddelelseskryptering. Du kan ikke slette standardbrandingskabelonen.

## <a name="modify-an-ome-branding-template"></a>Rediger en OME-brandingskabelon

Brug Windows PowerShell til at redigere én brandingskabelon ad gangen. Hvis du har avanceret meddelelseskryptering, kan du også oprette, redigere og fjerne brugerdefinerede skabeloner.

1. Du kan bruge en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, til at starte en Windows PowerShell-session og oprette forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug cmdletten Set-OMEConfiguration som beskrevet i [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration) , eller brug følgende grafik og tabel som vejledning.

![Brugerdefinerbare maildele.](../media/ome-template-breakout.png)

<br>

****

|**Sådan tilpasser du denne funktion i krypteringsoplevelsen**|**Brug disse kommandoer**|
|---|---|
|Baggrundsfarve|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "<#RRGGBB hexadecimal color code or name value>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -BackgroundColor "#ffffff"` <p> Du kan finde flere oplysninger om baggrundsfarver i [sektionen Baggrundsfarver](#background-color-reference) senere i denne artikel.|
|Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <Byte[]>` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Understøttede filformater: .png, .jpg, .bmp eller .tiff <p> Optimal størrelse på logofil: mindre end 40 KB <p> Optimal størrelse på logobillede: 170x70 pixel. Hvis dit billede overskrider disse dimensioner, ændrer tjenesten størrelsen på dit logo, så det vises på portalen. Tjenesten ændrer ikke selve grafikfilen. Du opnår de bedste resultater ved at bruge den optimale størrelse.|
|Tekst ud for afsenderens navn og mailadresse|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -IntroductionText "<String up to 1024 characters>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -IntroductionText "has sent you a secure message."`|
|Tekst, der vises på knappen "Læs meddelelse"|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -ReadButtonText "<String up to 1024 characters>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -ReadButtonText "Read Secure Message."`|
|Tekst, der vises under knappen "Læs meddelelse"|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<String up to 1024 characters>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system."`|
|URL-adressen til linket Erklæring om beskyttelse af personlige oplysninger|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PrivacyStatementURL "<URL>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -PrivacyStatementURL "https://contoso.com/privacystatement.html"`|
|Ansvarsfraskrivelse i den mail, der indeholder den krypterede meddelelse|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -DisclaimerText "<Disclaimer statement. String of up to 1024 characters.>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -DisclaimerText "This message is confidential for the use of the addressee only."`|
|Tekst, der vises øverst i den krypterede mailvisningsportal|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<Text for your portal. String of up to 128 characters.>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal."`|
|Sådan aktiveres eller deaktiveres godkendelse med en engangs adgangskode til denne brugerdefinerede skabelon|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -OTPEnabled <$true|$false>` <p> **Eksempler:** <br/>Sådan aktiveres engangskoder for denne brugerdefinerede skabelon <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $true` <p> Sådan deaktiverer du engangskoder for denne brugerdefinerede skabelon <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $false`|
|Sådan aktiveres eller deaktiveres godkendelse med Microsoft-, Google- eller Yahoo-identiteter for denne brugerdefinerede skabelon|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -SocialIdSignIn <$true|$false>` <p> **Eksempler:** <br/>Sådan aktiverer du sociale id'er for denne brugerdefinerede skabelon <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $true` <p> Sådan deaktiverer du sociale id'er for denne brugerdefinerede skabelon <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $false`|
|

## <a name="create-an-ome-branding-template-advanced-message-encryption"></a>Oprette en OME-brandingskabelon (Avanceret meddelelseskryptering)

Hvis du har Avanceret kryptering af meddelelser i Office 365, kan du oprette brugerdefinerede brandingskabeloner til organisationen ved hjælp af [New-OMEConfiguration-cmdlet'en](/powershell/module/exchange/new-omeconfiguration). Når du har oprettet skabelonen, kan du redigere skabelonen ved hjælp af cmdletSet-OMEConfiguration som beskrevet i Rediger [en OME-brandingskabelon](#modify-an-ome-branding-template). Du kan oprette flere skabeloner.

Sådan opretter du en ny brugerdefineret branding-skabelon:

1. Du kan bruge en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, til at starte en Windows PowerShell-session og oprette forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug [New-OMEConfiguration-cmdlet'en](/powershell/module/exchange/new-omeconfiguration) til at oprette en ny skabelon.

   ```powershell
   New-OMEConfiguration -Identity "<OMEConfigurationName>"
   ```

   For eksempel

   ```powershell
   New-OMEConfiguration -Identity "Custom branding template"
   ```

## <a name="return-the-default-branding-template-to-its-original-values"></a>Returner standardbrandingskabelonen til dens oprindelige værdier

Hvis du vil fjerne alle ændringer fra standardskabelonen, herunder brandtilpasninger og så videre, skal du udføre disse trin:

1. Du kan bruge en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, til at starte en Windows PowerShell-session og oprette forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug **cmdlet'en Set-OMEConfiguration** som beskrevet i [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration). Hvis du vil fjerne organisationens brandede tilpasninger fra værdierne DisclaimerText, EmailText og PortalText, skal du angive værdien til en tom streng `""`. For alle billedværdier, f.eks Logo, skal du indstille værdien til `"$null"`.

   I følgende tabel beskrives standardindstillingerne for krypteringsindstillinger.

   <br>

   ****

   |For at gendanne denne funktion i krypteringsoplevelsen tilbage til standardtekst og -billede|Brug disse kommandoer|
   |:-----|:-----|
   |Standardtekst, der leveres med krypterede mails. Standardteksten vises over vejledningen til visning af krypterede meddelelser|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<empty string>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Ansvarsfraskrivelse i den mail, der indeholder den krypterede meddelelse|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" DisclaimerText "<empty string>"` <p> **Eksempel:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Tekst, der vises øverst i den krypterede mailvisningsportal|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<empty string>"` <p> **Eksempel på at vende tilbage til standard:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <"$null">` <p> **Eksempel på at vende tilbage til standard:** <p> `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|
   |Baggrundsfarve|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "$null">` <p> **Eksempel på at vende tilbage til standard:** <p> `Set-OMEConfiguration -Identity "OME configuration" -BackgroundColor $null`|
   |

## <a name="remove-a-custom-branding-template-advanced-message-encryption"></a>Fjerne en brugerdefineret brandingskabelon (avanceret meddelelseskryptering)

Du kan kun fjerne eller slette brandingskabeloner, du har oprettet. Du kan ikke fjerne standardbrandingskabelonen.

Sådan fjerner du en brugerdefineret brandingskabelon:

1. Du kan bruge en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, til at starte en Windows PowerShell-session og oprette forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Brug **cmdlet'en Remove-OMEConfiguration** på følgende måde:

   ```powershell
   Remove-OMEConfiguration -Identity ""<OMEConfigurationName>"
   ```

   For eksempel

   ```powershell
   Remove-OMEConfiguration -Identity "Branding template 1"
   ```

   Du kan finde flere oplysninger [under Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration).

## <a name="create-an-exchange-mail-flow-rule-that-applies-your-custom-branding-to-encrypted-emails"></a>Opret en Exchange regel for mailflow, der anvender din brugerdefinerede branding på krypterede mails

> [!IMPORTANT]
> Tredjepartsprogrammer, der scanner og redigerer mail, kan forhindre OME-branding i at blive anvendt korrekt.

Når du enten har ændret standardskabelonen eller oprettet nye brandingskabeloner, kan du oprette Exchange regler for mailflow for at anvende din brugerdefinerede branding baseret på bestemte betingelser. En sådan regel anvender brugerdefineret branding i følgende scenarier:

- Hvis mailen blev krypteret manuelt af slutbrugeren ved hjælp Outlook eller Outlook på internettet, tidligere Outlook Web App
- Hvis mailen blev krypteret automatisk af en Exchange regel for mailflow eller politik til forebyggelse af datatab

Du kan finde oplysninger om, hvordan du Exchange en regel for mailflow, der anvender kryptering, i Definere regler for [mailflow for at kryptere mails Office 365](define-mail-flow-rules-to-encrypt-email.md).

1. I en webbrowser skal du logge på med en arbejds- eller skolekonto, der har fået globale administratorrettigheder, [for at Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Vælg **feltet** Administrator.

3. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> **Administrationer i Exchange**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>

4. I EAC skal du gå til **Regler for mailflow** \> og **vælge Nyt** ![nyt ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Oprette en ny regel**. Du kan finde flere oplysninger om brug af [EAC Exchange Administration i Exchange Online](/exchange/exchange-admin-center).

5. Skriv **et** navn til reglen under Navn, f.eks. Branding for salgsafdelingen.

6. I **Anvend denne regel hvis** skal du vælge betingelsen Afsenderen er placeret inden for organisationen og andre betingelser, du ønsker, på listen over tilgængelige betingelser. Du kan f.eks. anvende en bestemt brandingskabelon på:

   - Alle krypterede mails, der sendes fra medlemmer af økonomiafdelingen
   - Krypterede mails, der sendes med et bestemt nøgleord, f.eks. "Ekstern" eller "Partner"
   - Krypterede mails, der sendes til et bestemt domæne

7. Fra **Gør følgende skal du** vælge Rediger **meddelelsessikkerhed Anvend brugerdefineret** \> **branding på OME-meddelelser**. Vælg derefter en brandingskabelon på rullelisten.

8. (Valgfrit) Du kan konfigurere reglen for mailflow til at anvende kryptering og brugerdefineret branding. Fra **Gør følgende skal** du vælge **Rediger meddelelsessikkerhed** og derefter vælge **Anvend Office 365-meddelelseskryptering og rettighedsbeskyttelse**. Vælg en RMS-skabelon på listen, **vælg Gem**, og vælg derefter **OK**.

   Listen over skabeloner indeholder standardskabeloner og -indstillinger samt eventuelle brugerdefinerede skabeloner, du opretter. Hvis listen er tom, skal du sikre dig, at du har konfigureret Office 365-meddelelseskryptering med de nye funktioner. Du kan finde en [vejledning under Konfigurere Office 365-meddelelseskryptering funktioner](set-up-new-message-encryption-capabilities.md). Du kan finde oplysninger om standardskabelonerne [under Konfiguration og administration af skabeloner til Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). Du kan finde oplysninger **om indstillingen Videressendelse** ikke [under Indstillingen Videressendelse ikke for mails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Du kan finde oplysninger **om indstillingen Kun kryptering** under [Indstillingen Kryptér kun for mails](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   Vælg **tilføj handling** , hvis du vil angive en anden handling.

## <a name="background-color-reference"></a>Reference til baggrundsfarve

De farvenavne, du kan bruge til baggrundsfarven, er begrænsede. I stedet for et farvenavn kan du bruge en hex-kodeværdi (`#RRGGBB`). Du kan bruge en hex-kodeværdi, der svarer til et farvenavn, eller du kan bruge en brugerdefineret hex-kodeværdi. Sørg for at omslutte hex-kodeværdien med anførselstegn (f.eks `"#f0f8ff"`. ).

De tilgængelige baggrundsfarvenavne og deres tilsvarende hex-kodeværdier er beskrevet i nedenstående tabel.

|**Farvenavn**|**Farvekode**|
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
