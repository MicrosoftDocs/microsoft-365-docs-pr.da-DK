---
title: Definere regler for mailflow for at kryptere mails
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 9b7daf19-d5f2-415b-bc43-a0f5f4a585e8
ms.collection:
- M365-security-compliance
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Administratorer kan lære at oprette regler for mailflow (transportregler) for at kryptere og dekryptere meddelelser ved hjælp Office 365-meddelelseskryptering.
ms.openlocfilehash: bb50ed5d2b22fd74d4a6f88eba29f82d10be1f50
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/16/2022
ms.locfileid: "63587270"
---
# <a name="define-mail-flow-rules-to-encrypt-email-messages"></a>Definere regler for mailflow for at kryptere mails

Som administrator, der administrerer Exchange Online, kan du oprette regler for mailflow (også kaldet transportregler) for at beskytte de mails, du sender og modtager. Du kan konfigurere regler til at kryptere eventuelle udgående mails og fjerne kryptering fra krypterede meddelelser, der kommer fra din organisation eller fra svar på krypterede meddelelser, der sendes fra organisationen. Du kan bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange (EAC)</a> eller PowerShell Exchange Online at oprette disse regler. Ud over de overordnede krypteringsregler kan du også vælge at aktivere eller deaktivere individuelle krypteringsindstillinger for meddelelser for slutbrugere.

Du kan ikke kryptere indgående mail fra afsendere uden for organisationen.

Hvis du for nylig har overført fra Active Directory RMS til Azure Information Protection, skal du gennemgå dine eksisterende regler for mailflow for at sikre, at de fortsat fungerer i dit nye miljø. Hvis du vil drage fordel af de nye OME-funktioner (Office 365-meddelelseskryptering), der er tilgængelige for dig via Azure Information Protection, skal du opdatere dine eksisterende regler for mailflow. Ellers vil dine brugere fortsat modtage krypteret mail, der bruger det tidligere HTML-format til vedhæftede filer i stedet for den nye, problemfri OME-oplevelse. Hvis du ikke har konfigureret OME endnu, skal du se [Konfigurer nye Office 365-meddelelseskryptering for at](set-up-new-message-encryption-capabilities.md) få flere oplysninger.

Du kan finde oplysninger om de komponenter, der udgør regler for mailflow, og hvordan regler for mailflow fungerer, under Regler for mailflow [(transportregler) Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules). Du kan finde flere oplysninger om, hvordan regler for mailflow fungerer med Azure Information Protection, [under Konfiguration Exchange Online regler for mailflow for Azure Information Protection-navne](/azure/information-protection/deploy-use/configure-exo-rules).

> [!IMPORTANT]
> For hybride Exchange-miljøer kan lokale brugere kun sende og modtage krypteret mail ved hjælp af OME, hvis mail dirigeres gennem Exchange Online. Hvis du vil konfigurere OME i et hybrid Exchange-miljø, skal du først konfigurere hybrid ved hjælp af guiden [Hybridkonfiguration](/Exchange/exchange-hybrid) og derefter konfigurere mail til at flyde fra [Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-1-configure-mail-to-flow-from-office-365-to-your-on-premises-email-server) til mailserveren og konfigurere mail til at flyde fra mailserveren [til Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365). Når du har konfigureret mail til at flyde gennem Office 365, kan du konfigurere regler for mailflow for OME ved hjælp af denne vejledning.

## <a name="create-mail-flow-rules-to-encrypt-email-messages-with-the-new-ome-capabilities"></a>Oprette regler for mailflow for at kryptere mails med de nye OME-funktioner

Du kan definere regler for mailflow til at udløse meddelelseskryptering med de nye OME-funktioner ved hjælp af EAC.

### <a name="use-the-eac-to-create-a-rule-for-encrypting-email-messages-with-the-new-ome-capabilities"></a>Brug EAC til at oprette en regel for kryptering af mails med de nye OME-funktioner

1. I en webbrowser skal du logge på med en arbejds- eller skolekonto, der har fået globale administratorrettigheder, [for at Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Vælg **feltet** Administrator.

3. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> **Administrationer i Exchange**\>.

4. I EAC skal du gå til **Regler for mailflow** \> og **vælge Nyt** ![nyt ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Oprette en ny regel**. Du kan finde flere oplysninger om brug af [EAC Exchange Administration i Exchange Online](/exchange/exchange-admin-center).

5. Skriv **et** navn til reglen under Navn, f.eks. Kryptér mail for DrToniRamos@hotmail.com.

6. Vælg **en betingelse i Anvend denne** regel, hvis, og angiv en værdi, hvis det er nødvendigt. Hvis du f.eks. vil kryptere meddelelser, der DrToniRamos@hotmail.com:

   1. Vælg **modtageren i Anvend denne** regel, **hvis**.

   2. Vælg et eksisterende navn på listen over kontakter, eller skriv en ny mailadresse i **afkrydsningsfeltet** Navne.

      - Hvis du vil vælge et eksisterende navn, skal du vælge det på listen og derefter klikke på **OK**.

      - Hvis du vil angive et nyt navn, skal du skrive en mailadresse **i afkrydsningsfeltet Navne** og derefter **vælge Kontrollér navne** \> **OK**.

7. Hvis du vil tilføje flere betingelser, **skal du vælge** Flere indstillinger **og derefter vælge Tilføj** betingelse og vælge på listen.

   Hvis du f.eks. kun vil anvende reglen, hvis modtageren er uden for din  organisation, skal du vælge Tilføj betingelse og derefter vælge Modtageren er ekstern **/intern** \> **Uden for** \> **organisationen OK**.

8. Hvis du vil aktivere kryptering ved hjælp af de nye OME-funktioner, skal du  gå til Gør følgende og vælge Rediger meddelelsessikkerhed **og derefter vælge Office 365-meddelelseskryptering og rettighedsbeskyttelse**. Vælg en RMS-skabelon på listen, **vælg Gem**, og vælg derefter **OK**.
  
  Listen over skabeloner indeholder alle standardskabeloner og -indstillinger samt eventuelle brugerdefinerede skabeloner, du har oprettet til brug for Office 365. Hvis listen er tom, skal du sikre dig, at du har konfigureret Office 365-meddelelseskryptering med de nye funktioner som beskrevet i Konfigurer [nye Office 365-meddelelseskryptering funktioner](set-up-new-message-encryption-capabilities.md). Du kan finde oplysninger om standardskabelonerne [under Konfiguration og administration af skabeloner til Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). Du kan finde oplysninger **om indstillingen Videressendelse** ikke [under Indstillingen Videressendelse ikke for mails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Du kan finde oplysninger **om indstillingen kun krypteret** under [Indstillingen Kryptér kun for mails](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

  Du kan vælge **tilføj handling,** hvis du vil angive en anden handling.

### <a name="use-the-eac-to-update-an-existing-mail-flow-rule-to-use-the-new-ome-capabilities"></a>Brug EAC til at opdatere en eksisterende regel for mailflow for at bruge de nye OME-funktioner

1. I en webbrowser skal du logge på med en arbejds- eller skolekonto, der har fået globale administratorrettigheder, [for at Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Vælg **feltet** Administrator.

3. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> **Administrationer i Exchange**\>.

4. I EAC skal du gå til **Regler for mailflow**\>.

5. På listen over regler for mailflow skal du vælge den regel, du vil ændre for at bruge de nye OME-funktioner, og derefter vælge **Rediger** ![redigeringsikon.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)

6. Hvis du vil aktivere kryptering ved hjælp af de nye OME-funktioner, skal du  gå til Gør følgende og vælge Rediger meddelelsessikkerhed **og derefter vælge Office 365-meddelelseskryptering og rettighedsbeskyttelse**. Vælg en RMS-skabelon på listen, vælg **Gem,** og vælg derefter **OK**.

   Listen over skabeloner indeholder alle standardskabeloner og -indstillinger samt eventuelle brugerdefinerede skabeloner, du har oprettet til brug for Office 365. Hvis listen er tom, skal du sikre dig, at du har konfigureret Office 365-meddelelseskryptering med de nye funktioner som beskrevet i Konfigurer nye Office 365-meddelelseskryptering-funktioner, der er bygget oven på [Azure Information Protection](set-up-new-message-encryption-capabilities.md). Du kan finde oplysninger om standardskabelonerne [under Konfiguration og administration af skabeloner til Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). Du kan finde oplysninger om indstillingen Videressendelse ikke [under Indstillingen Videressendelse ikke for mails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Du kan finde oplysninger om indstillingen kun krypteret under [Indstillingen Kryptér kun for mails](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   Du kan vælge **tilføj handling,** hvis du vil angive en anden handling.

7. Fra listen **Gør følgende skal du** fjerne eventuelle handlinger, der er tildelt Rediger **meddelelsessikkerheden** \> **Anvend den tidligere version af OME**.

8. Vælg **Gem**.

## <a name="create-mail-flow-rules-to-remove-encryption-for-email-messages-with-the-new-ome-capabilities"></a>Opret regler for mailflow for at fjerne kryptering af mails med de nye OME-funktioner

Du kan definere regler for mailflow for at udløse kryptering af meddelelser med de nye OME-funktioner ved hjælp af EAC.

### <a name="use-the-eac-to-create-a-rule-to-remove-encryption-from-email-messages-with-the-new-ome-capabilities"></a>Brug EAC til at oprette en regel til at fjerne kryptering fra mails med de nye OME-funktioner

Du kan fjerne kryptering fra meddelelser, der blev anvendt af din organisation. Du kan også fjerne kryptering fra krypterede vedhæftede filer for at sikre, at hele mailen er uden beskyttelse.

1. I en webbrowser skal du logge på med en arbejds- eller skolekonto, der har fået globale administratorrettigheder, [for at Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Vælg **feltet** Administrator.

3. Vælg <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> **Administrationer i Exchange**\>.

4. I EAC skal du gå til **Regler for mailflow** \> og **vælge Nyt** ![nyt ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Oprette en ny regel**. Du kan finde flere oplysninger om brug af [EAC Exchange Administration i Exchange Online](/exchange/exchange-admin-center).

5. Skriv **et** navn til reglen under Navn, f.eks. Fjern kryptering fra udgående mail.

6. I **Anvend denne regel hvis skal** du vælge de betingelser, hvor kryptering skal fjernes fra meddelelser. Tilføj **Afsenderen er placeret Inden** \> **for organisationen til** at sende mail _,_ **eller modtageren er placeret** \> **inde i organisationen til** at modtage mail.

7. I **Gør følgende skal** du vælge **Rediger meddelelsessikkerhed Fjern Office 365-meddelelseskryptering** \> **og rettighedsbeskyttelse, der anvendes af organisationen**.

8. (Valgfrit) I **Gør følgende skal du** vælge Rediger **meddelelsessikkerhed Fjern beskyttelse** \> **mod vedhæftede filers rettighedsbeskyttelse, som anvendes af organisationen**.

Gem reglen.

## <a name="create-mail-flow-rules-for-office-365-message-encryption-without-the-new-capabilities"></a>Oprette regler for mailflow for Office 365-meddelelseskryptering uden de nye funktioner

Hvis du endnu ikke har flyttet organisationen til de nye OME-funktioner, anbefaler Microsoft, at du planlægger at flytte til de nye OME-funktioner, så snart det er fornuftigt for din organisation. Du kan finde en [vejledning under Konfigurere Office 365-meddelelseskryptering funktioner, der er bygget oven på Azure Information Protection](set-up-new-message-encryption-capabilities.md). Ellers skal [du se Definere regler for mailflow for Office 365-meddelelseskryptering, der ikke bruger de nye OME-funktioner](legacy-information-for-message-encryption.md#defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-the-new-ome-capabilities).

## <a name="related-content"></a>Relateret indhold

[Kryptering i Office 365](encryption.md)

[Konfigurer nye Office 365-meddelelseskryptering funktioner](set-up-new-message-encryption-capabilities.md)

[Føj branding til krypterede meddelelser](add-your-organization-brand-to-encrypted-messages.md)

[Regler for mailflow (transportregler) i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)
