---
title: Definer regler for mailflow for at kryptere mails
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
description: Administratorer kan få mere at vide om, hvordan de opretter regler for mailflow (transportregler) for at kryptere og dekryptere meddelelser ved hjælp af Microsoft Purview-meddelelseskryptering.
ms.openlocfilehash: 75abd302bf661fda50b144f431572c8c6dfc8bcc
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635693"
---
# <a name="define-mail-flow-rules-to-encrypt-email-messages"></a>Definer regler for mailflow for at kryptere mails

Som administrator, der administrerer Exchange Online, kan du oprette regler for mailflow (også kaldet transportregler) for at beskytte mails, du sender og modtager. Du kan konfigurere regler for at kryptere alle udgående mails og fjerne kryptering fra krypterede meddelelser, der kommer fra din organisation, eller fra svar på krypterede meddelelser, der er sendt fra din organisation. Du kan bruge <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration (EAC)</a> eller Exchange Online PowerShell til at oprette disse regler. Ud over de overordnede krypteringsregler kan du også vælge at aktivere eller deaktivere individuelle indstillinger for meddelelseskryptering for slutbrugere.

Du kan ikke kryptere indgående mails fra afsendere uden for organisationen.

Hvis du for nylig har overført fra Active Directory RMS til Azure Information Protection, skal du gennemse dine eksisterende regler for mailflow for at sikre, at de fortsat fungerer i dit nye miljø. Hvis du vil bruge Microsoft Purview-meddelelseskryptering med Azure Information Protection, skal du også opdatere dine eksisterende regler for mailflow. Ellers vil brugerne fortsat modtage krypteret mail, der bruger det tidligere format for vedhæftede HTML-filer i stedet for den nye, problemfrie oplevelse. Hvis du endnu ikke har konfigureret meddelelseskryptering, [skal du se Konfigurer Microsoft Purview-meddelelseskryptering](set-up-new-message-encryption-capabilities.md) for at få flere oplysninger.

Du kan få oplysninger om de komponenter, der udgør regler for mailflow, og hvordan regler for mailflow fungerer, [under Regler for mailflow (transportregler) i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules). Du kan finde flere oplysninger om, hvordan regler for mailflow fungerer sammen med Azure Information Protection, under [Konfiguration af Exchange Online regler for mailflow for Azure Information Protection-mærkater](/azure/information-protection/deploy-use/configure-exo-rules).

> [!IMPORTANT]
> I forbindelse med hybride Exchange-miljøer kan brugere i det lokale miljø kun sende og modtage krypteret mail ved hjælp af meddelelsekryptering, hvis mail dirigeres gennem Exchange Online. Hvis du vil konfigurere meddelelseskryptering i et hybridt Exchange-miljø, skal du først [konfigurere hybrid ved hjælp af guiden Hybridkonfiguration](/Exchange/exchange-hybrid) og derefter [konfigurere mail til at gå fra Office 365 til din mailserver](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-1-configure-mail-to-flow-from-office-365-to-your-on-premises-email-server) og [konfigurere mail til at blive sendt fra din mailserver til Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365). Når du har konfigureret mail til at gå gennem Office 365, kan du konfigurere regler for mailflow for kryptering af meddelelser ved hjælp af denne vejledning.

## <a name="create-mail-flow-rules-to-encrypt-email-messages-with-microsoft-purview-message-encryption"></a>Opret regler for mailflow for at kryptere mails med Microsoft Purview-meddelelseskryptering

Du kan definere regler for mailflow for udløsning af meddelelseskryptering med ved hjælp af EAC.

### <a name="use-the-eac-to-create-a-rule-for-encrypting-email-messages-with-microsoft-purview-message-encryption"></a>Brug EAC til at oprette en regel for kryptering af mails med Microsoft Purview-meddelelseskryptering

1. Log [på Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) ved hjælp af en arbejds- eller skolekonto, der er tildelt globale administratortilladelser, i en webbrowser.

2. Vælg feltet **Administration**.

3. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> skal du vælge **Administration centre** \> **Exchange**.

4. I EAC skal du gå til **Regler for** **mailflow** \> og vælge **Nyt** ![ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Opret en ny regel**. Du kan få flere oplysninger om brug af EAC [i Exchange Administration i Exchange Online](/exchange/exchange-admin-center).

5. Skriv et navn til reglen i **Navn**, f.eks. Kryptér mail for DrToniRamos@hotmail.com.

6. I **Anvend denne regel, hvis** skal du vælge en betingelse og angive en værdi, hvis det er nødvendigt. Hvis du f.eks. vil kryptere meddelelser, der skal DrToniRamos@hotmail.com:

   1. Vælg **modtageren er i** **Anvend denne regel, hvis**.

   2. Vælg et eksisterende navn på listen over kontakter, eller skriv en ny mailadresse i feltet **Afkrydsningsfelter** .

      - Hvis du vil vælge et eksisterende navn, skal du vælge det på listen og derefter klikke på **OK**.

      - Hvis du vil angive et nyt navn, skal du skrive en mailadresse i **afkrydsningsfeltet Afkrydsningsfelter** og derefter markere **afkrydsningsfeltet ok** \> **.**

7. Hvis du vil tilføje flere betingelser, skal du vælge **Flere indstillinger** og derefter vælge **Tilføj betingelse** og vælge på listen.

   Hvis du f.eks. kun vil anvende reglen, hvis modtageren er uden for din organisation, skal du vælge **Tilføj betingelse** og derefter vælge **Modtageren er ekstern/intern** \> **Uden for organisationen** \> **OK**.

8. Hvis du vil aktivere meddelelseskryptering, skal du vælge **Rediger meddelelsessikkerheden** fra **Gør følgende** og derefter vælge **Anvend Office 365 Meddelelsekryptering og rettighedsbeskyttelse**. Vælg en RMS-skabelon på listen, vælg **Gem**, og vælg derefter **OK**.
  
  Listen over skabeloner indeholder alle standardskabeloner og -indstillinger samt alle brugerdefinerede skabeloner, du har oprettet til brug af Office 365. Hvis listen er tom, skal du kontrollere, at du har konfigureret Microsoft Purview-meddelelseskryptering som beskrevet i [Konfigurer Microsoft Purview-meddelelseskryptering](set-up-new-message-encryption-capabilities.md). Du kan få oplysninger om standardskabelonerne under [Konfiguration og administration af skabeloner til Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). Du kan få oplysninger om indstillingen **Videresend ikke** under [Videresend ikke for mails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Du kan få mere at vide om indstillingen **Kun kryptering** under [Kryptér kun for mails](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

  Du kan vælge **Tilføj handling** , hvis du vil angive en anden handling.

### <a name="use-the-eac-to-update-an-existing-mail-flow-rule-to-use-microsoft-purview-message-encryption"></a>Brug EAC til at opdatere en eksisterende regel for mailflowet, så den bruger Microsoft Purview-meddelelseskryptering

1. Log [på Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) ved hjælp af en arbejds- eller skolekonto, der er tildelt globale administratortilladelser, i en webbrowser.

2. Vælg feltet **Administration**.

3. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> skal du vælge **Administration centre** \> **Exchange**.

4. I EAC skal du gå til **Regler for** **mailflow**\>.

5. På listen over regler for mailflow skal du vælge den regel, du vil ændre, så den kan bruges sammen med Microsoft Purview-meddelelseskryptering og derefter vælge **Rediger ikonet Rediger**![.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).

6. Hvis du vil aktivere kryptering ved hjælp af Microsoft Purview-meddelelseskryptering, skal du vælge **Rediger meddelelsessikkerheden** i **Gør følgende** og derefter vælge **Anvend Office 365 Meddelelsekryptering og rettighedsbeskyttelse**. Vælg en RMS-skabelon på listen, vælg **Gem** , og vælg derefter **OK**.

   Listen over skabeloner indeholder alle standardskabeloner og -indstillinger samt alle brugerdefinerede skabeloner, du har oprettet til brug af Office 365. Hvis listen er tom, skal du kontrollere, at du har konfigureret Microsoft Purview-meddelelseskryptering som beskrevet i [Konfigurer Microsoft Purview-meddelelseskryptering](set-up-new-message-encryption-capabilities.md). Du kan få oplysninger om standardskabelonerne under [Konfiguration og administration af skabeloner til Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). Du kan få oplysninger om indstillingen Videresend ikke under [Videresend ikke for mails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Du kan få oplysninger om indstillingen Kun kryptering under [Kryptér kun for mails](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   Du kan vælge **Tilføj handling** , hvis du vil angive en anden handling.

7. Fra listen **Gør følgende skal** du fjerne de handlinger, der er tildelt til **Rediger meddelelsessikkerheden** \> **Anvend den tidligere version af OME**.

8. Vælg **Gem**.

## <a name="create-mail-flow-rules-to-remove-encryption-for-email-messages-with-microsoft-purview-message-encryption"></a>Opret regler for mailflow for at fjerne kryptering for mails med Microsoft Purview-meddelelseskryptering

Du kan definere regler for mailflow for at fjerne meddelelseskryptering med Microsoft Purview-meddelelseskryptering ved hjælp af EAC.

### <a name="use-the-eac-to-create-a-rule-to-remove-encryption-from-email-messages-with-microsoft-purview-message-encryption"></a>Brug EAC til at oprette en regel for at fjerne kryptering fra mails med Microsoft Purview-meddelelseskryptering

Du kan fjerne kryptering fra meddelelser, der er anvendt af din organisation. Du kan også fjerne kryptering fra alle krypterede vedhæftede filer for at sikre, at hele mailen er uden nogen beskyttelse.

1. Log [på Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser) ved hjælp af en arbejds- eller skolekonto, der er tildelt globale administratortilladelser, i en webbrowser.

2. Vælg feltet **Administration**.

3. I <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 Administration</a> skal du vælge **Administration centre** \> **Exchange**.

4. I EAC skal du gå til **Regler for** **mailflow** \> og vælge **Nyt** ![ikon.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Opret en ny regel**. Du kan få flere oplysninger om brug af EAC [i Exchange Administration i Exchange Online](/exchange/exchange-admin-center).

5. Skriv et navn til reglen i **Navn**, f.eks `Remove encryption from outgoing mail`. .

6. I **Anvend denne regel, hvis** skal du vælge de betingelser, hvor kryptering skal fjernes fra meddelelser. Tilføj **Afsenderen er placeret** \> **i organisationen** til afsendelse af mail _, eller_ **modtageren er placeret** \> **i organisationen** til modtagelse af mail.

7. **I Gør følgende** skal du vælge **Rediger meddelelsessikkerheden** \> **Fjern Office 365 Meddelelsekryptering og rettighedsbeskyttelse, der anvendes af organisationen**.

8. (Valgfrit) **I Gør følgende** skal du vælge **Rediger meddelelsessikkerheden** \> **Fjern beskyttelse mod beskyttelse af vedhæftede filer, der anvendes af organisationen**.

Gem reglen.

## <a name="create-mail-flow-rules-for-office-365-message-encryption-without-microsoft-purview-message-encryption"></a>Opret regler for mailflow for Office 365 meddelelsekryptering uden Microsoft Purview-meddelelseskryptering

Hvis du endnu ikke har flyttet din organisation til Microsoft Purview-meddelelseskryptering, anbefaler Microsoft, at du planlægger at flytte, så snart det er rimeligt for din organisation. Du kan finde en vejledning under [Konfigurer Microsoft Purview-meddelelseskryptering](set-up-new-message-encryption-capabilities.md). Ellers skal du se [Definition af regler for mailflow for Office 365 Meddelelsekryptering, der ikke bruger Microsoft Purview-meddelelseskryptering](legacy-information-for-message-encryption.md#defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-microsoft-purview-message-encryption).

## <a name="related-content"></a>Relateret indhold

[Kryptering i Office 365](encryption.md)

[Konfigurer Microsoft Purview-meddelelseskryptering](set-up-new-message-encryption-capabilities.md)

[Føj branding til krypterede meddelelser](add-your-organization-brand-to-encrypted-messages.md)

[Regler for mailflow (transportregler) i Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)
