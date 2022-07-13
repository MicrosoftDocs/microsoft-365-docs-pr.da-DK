---
title: Anbefalede politikker for sikre mails – Microsoft 365 for enterprise-| Microsoft Docs
description: Beskriver politikkerne for Microsoft-anbefalinger om, hvordan du anvender mailpolitikker og -konfigurationer.
ms.author: dansimp
author: dansimp
manager: Laurawi
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- remotework
- m365solution-identitydevice
- m365solution-scenario
- zerotrust-solution
ms.technology: mdo
ms.openlocfilehash: 1b3afc4988dc5d20a1c6c3e0b1a51c1ef1cf9987
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750160"
---
# <a name="policy-recommendations-for-securing-email"></a>Politikanbefalinger til sikring af mail

I denne artikel beskrives det, hvordan du implementerer de anbefalede Nul tillid identitets- og enhedsadgangspolitikker for at beskytte organisationsmail- og mailklienter, der understøtter moderne godkendelse og betinget adgang. Denne vejledning bygger på [fælles politikker for identitets- og enhedsadgang](identity-access-policies.md) og indeholder også nogle få yderligere anbefalinger.

Disse anbefalinger er baseret på tre forskellige niveauer af sikkerhed og beskyttelse, der kan anvendes på baggrund af granulariteten af dine behov: **udgangspunkt**, **virksomhed** og **specialiseret sikkerhed**. Du kan få mere at vide om disse sikkerhedsniveauer og de anbefalede klientoperativsystemer, som disse anbefalinger refererer til i [introduktionen til de anbefalede sikkerhedspolitikker og konfigurationer](microsoft-365-policies-configurations.md).

Disse anbefalinger kræver, at dine brugere bruger moderne mailklienter, herunder Outlook til iOS og Android på mobilenheder. Outlook til iOS og Android understøtter de bedste funktioner i Office 365. Disse Outlook-mobilapps er også udviklet med sikkerhedsfunktioner, der understøtter mobilbrug og arbejder sammen med andre Microsofts cloudsikkerhedsfunktioner. Du kan få flere oplysninger under [Ofte stillede spørgsmål om Outlook til iOS og Android](/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq).

## <a name="update-common-policies-to-include-email"></a>Opdater almindelige politikker for at inkludere mail

For at beskytte mails illustrerer følgende diagram, hvilke politikker der skal opdateres fra de almindelige politikker for identitets- og enhedsadgang.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png" alt-text="Oversigten over politikopdateringer til beskyttelse af adgang til Microsoft Exchange" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png":::

Bemærk tilføjelsen af en ny politik for Exchange Online til at blokere ActiveSync-klienter. Dette tvinger brugen af Outlook Mobile.

Hvis du inkluderede Exchange Online og Outlook i området for politikkerne, da du konfigurerede dem, skal du kun oprette den nye politik for at blokere ActiveSync-klienter. Gennemse de politikker, der er angivet i følgende tabel, og foretag enten de anbefalede tilføjelser, eller bekræft, at disse allerede er inkluderet. Hver politik linker til de tilknyttede konfigurationsinstruktioner i [Almindelige politikker for identitets- og enhedsadgang](identity-access-policies.md).

|Beskyttelsesniveau|Politikker|Flere oplysninger|
|---|---|---|
|**Udgangspunkt**|[Kræv MFA, når logonrisikoen er *mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Medtag Exchange Online i tildelingen af cloudapps|
||[Bloker klienter, der ikke understøtter moderne godkendelse](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Medtag Exchange Online i tildelingen af cloudapps|
||[Anvend politikker for databeskyttelse i APP](identity-access-policies.md#apply-app-data-protection-policies)|Sørg for, at Outlook er inkluderet på listen over apps. Sørg for at opdatere politikken for hver platform (iOS, Android, Windows)|
||[Kræv godkendte apps og appbeskyttelse](identity-access-policies.md#require-approved-apps-and-app-protection)|Medtag Exchange Online på listen over cloudapps|
||[Bloker ActiveSync-klienter](#block-activesync-clients)|Tilføj denne nye politik|
|**Enterprise**|[Kræv MFA, når logonrisikoen er *lav*, *mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Medtag Exchange Online i tildelingen af cloudapps|
||[Kræv kompatible pc'er *og* mobilenheder](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Medtag Exchange Online på listen over cloudapps|
|**Specialiseret sikkerhed**|[*Kræv altid* MFA](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Medtag Exchange Online i tildelingen af cloudapps|

## <a name="block-activesync-clients"></a>Bloker ActiveSync-klienter

Exchange ActiveSync kan bruges til at synkronisere meddelelses- og kalenderdata på stationære og mobilenheder.

For mobilenheder er moderne Exchange ActiveSync klienter, der kan godkende, og som ikke understøtter Intune politikker for appbeskyttelse (eller understøttede klienter, der ikke er defineret i beskyttelsespolitikken for apps) og Exchange ActiveSync klienter, der bruger grundlæggende godkendelse, blokeret på baggrund af den politik for betinget adgang, der er oprettet i [ Kræv godkendte apps og appbeskyttelse](identity-access-policies.md#require-approved-apps-and-app-protection).

Hvis du vil blokere Exchange ActiveSync ved hjælp af basisgodkendelse på andre enheder, skal du følge trinnene i [Bloker Exchange ActiveSync på alle enheder](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#block-exchange-activesync-on-all-devices), hvilket forhindrer, at Exchange ActiveSync klienter, der bruger basisgodkendelse på ikke-mobilenheder, opretter forbindelse til Exchange Online.

Du kan også bruge godkendelsespolitikker til at [deaktivere basisgodkendelse](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online), hvilket tvinger alle anmodninger om klientadgang til at bruge moderne godkendelse.

## <a name="limit-access-to-exchange-online-from-outlook-on-the-web"></a>Begræns adgang til Exchange Online fra Outlook på internettet

Du kan begrænse brugernes mulighed for at downloade vedhæftede filer fra Outlook på internettet på ikke-administrerede enheder. Brugere på disse enheder kan få vist og redigere disse filer ved hjælp af Office Online uden at lække og gemme filerne på enheden. Du kan også blokere brugere, så de ikke kan se vedhæftede filer på en ikke-administreret enhed.

Her er trinnene:

1. [Opret forbindelse til Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
2. Hvis du ikke allerede har en OWA-postkassepolitik, skal du oprette en med cmdlet'en [New-OwaMailboxPolicy](/powershell/module/exchange/new-owamailboxpolicy) .
3. Hvis du vil tillade visning af vedhæftede filer, men ingen download, skal du bruge denne kommando:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnly
   ```

4. Hvis du vil blokere vedhæftede filer, skal du bruge denne kommando:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnlyPlusAttachmentsBlocked
   ```

5. I Azure Portal skal du oprette en ny politik for betinget adgang med disse indstillinger:

   **Tildelinger** \> **Brugere og grupper**: Vælg de relevante brugere og grupper, der skal medtages og udelades.

   **Tildelinger** \> **Cloudapps eller -handlinger** \> **Cloudapps** \> **Omfatter** \> **Vælg apps**: Vælg **Office 365 Exchange Online**

   **Adgangskontrolelementer** \> **Session**: Vælg **Brug gennemtvungne begrænsninger for appen**

## <a name="require-that-ios-and-android-devices-must-use-outlook"></a>Kræv, at iOS- og Android-enheder skal bruge Outlook

Hvis du vil sikre, at brugere af iOS- og Android-enheder kun kan få adgang til arbejds- eller skoleindhold ved hjælp af Outlook til iOS og Android, skal du have en politik for betinget adgang, der er målrettet disse potentielle brugere.

Se trinnene til konfiguration af denne politik i [Administrer chatsamarbejde ved hjælp af Outlook til iOS og Android](/mem/intune/apps/app-configuration-policies-outlook#apply-conditional-access).

## <a name="set-up-message-encryption"></a>Konfigurer meddelelsekryptering

Med Microsoft Purview-meddelelseskryptering, som udnytter beskyttelsesfunktionerne i Azure Information Protection, kan din organisation nemt dele beskyttede mails med alle på alle enheder. Brugerne kan sende og modtage beskyttede meddelelser med andre Microsoft 365-organisationer samt ikke-kunder, der bruger Outlook.com, Gmail og andre mailtjenester.

Du kan få flere oplysninger under [Konfigurer nye Office 365 funktioner til meddelelsekryptering](../../compliance/set-up-new-message-encryption-capabilities.md).

## <a name="next-steps"></a>Næste trin

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Politikkerne for Microsoft 365-cloudapps" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Konfigurer politikker for betinget adgang for:

- [Microsoft Teams](teams-access-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
