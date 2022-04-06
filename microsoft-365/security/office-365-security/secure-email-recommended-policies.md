---
title: Sikre politikker for anbefalede mails – Microsoft 365 til | Microsoft Docs
description: Beskriver politikkerne for Microsoft-anbefalinger om, hvordan du anvender mailpolitikker og konfigurationer.
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
ms.technology: mdo
ms.openlocfilehash: 6ab6ff7c043dcceacfbb07d0f6fec5e974999204
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682433"
---
# <a name="policy-recommendations-for-securing-email"></a>Politikanbefalinger til sikring af mail

Denne artikel beskriver, hvordan du implementerer de anbefalede politikker for nultillids identitet og enhedsadgang for at beskytte organisatoriske mails og mailklienter, der understøtter moderne godkendelse og betinget adgang. Denne vejledning bygger på politikkerne [Fælles identitet og Enhedsadgang](identity-access-policies.md) og indeholder også et par yderligere anbefalinger.

Disse anbefalinger er baseret på tre forskellige niveauer af sikkerhed og beskyttelse, der kan anvendes baseret på granulariteten af dine behov **: udgangspunkt**, **virksomhed** **og specialiseret sikkerhed**. Du kan få mere at vide om disse sikkerhedsniveauer og de anbefalede klientoperativsystemer, der refereres til i disse anbefalinger i introduktionen til anbefalede [sikkerhedspolitikker og -konfigurationer](microsoft-365-policies-configurations.md).

Disse anbefalinger kræver, at dine brugere bruger moderne mailklienter, Outlook til iOS og Android på mobilenheder. Outlook til iOS og Android understøtter de bedste funktioner i Office 365. Disse mobile Outlook-apps er også designet med sikkerhedsfunktioner, der understøtter mobilbrug og arbejder sammen med andre Microsoft-skysikkerhedsfunktioner. Du kan finde flere oplysninger [i ofte Outlook til iOS og Android](/exchange/clients-and-mobile-in-exchange-online/outlook-for-ios-and-android/outlook-for-ios-and-android-faq).

## <a name="update-common-policies-to-include-email"></a>Opdater almindelige politikker, der omfatter mail

For at beskytte mail illustrerer følgende diagram, hvilke politikker der skal opdateres fra de fælles politikker for identitet og enhedsadgang.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png" alt-text="Oversigt over politikopdateringer til beskyttelse af adgang til Exchange." lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-mail.png":::

Bemærk tilføjelsen af en ny politik for Exchange Online blokere ActiveSync-klienter. Dette tvinger brugen af Outlook mobile.

Hvis du Exchange Online og Outlook politikkerne, da du konfigurerede dem, skal du kun oprette den nye politik for at blokere ActiveSync-klienter. Gennemgå de politikker, der er angivet i følgende tabel, og foretag enten de anbefalede tilføjelser, eller bekræft, at disse allerede er medtaget. Hver politik linker til de tilknyttede konfigurationsinstruktioner [i Fælles identitets- og enhedsadgangspolitikker](identity-access-policies.md).

|Beskyttelsesniveau|Politikker|Flere oplysninger|
|---|---|---|
|**Udgangspunkt**|[Kræv MFA, når logonrisici er *mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Medtag Exchange Online i tildelingen af skyapps|
||[Blokere klienter, der ikke understøtter moderne godkendelse](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Medtag Exchange Online i tildelingen af skyapps|
||[Anvend politikker for beskyttelse af app-data](identity-access-policies.md#apply-app-data-protection-policies)|Sørg for Outlook er inkluderet i listen over apps. Sørg for at opdatere politikken for hver platform (iOS, Android, Windows)|
||[Kræv godkendte apps og APP-beskyttelse](identity-access-policies.md#require-approved-apps-and-app-protection)|Medtag Exchange Online på listen over skyapps|
||[Bloker ActiveSync-klienter](#block-activesync-clients)|Tilføj denne nye politik|
|**Enterprise**|[Kræv MFA, når risikoen for at logge *på er* *lav, mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Medtag Exchange Online i tildelingen af skyapps|
||[Kræv kompatible *pc'er* og mobilenheder](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Medtag Exchange Online på listen over skyapps|
|**Speciel sikkerhed**|[*Kræv* altid MFA](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Medtag Exchange Online i tildelingen af skyapps|

## <a name="block-activesync-clients"></a>Bloker ActiveSync-klienter

Exchange ActiveSync kan bruges til at synkronisere meddelelses- og kalenderdata på stationære computere og mobilenheder.

For mobilenheder blokeres moderne godkendelses-kompatible Exchange ActiveSync-klienter, der ikke understøtter Intune-politikker for appbeskyttelse (eller understøttede klienter, som ikke er defineret i appbeskyttelsespolitikken), og Exchange ActiveSync-klienter, der bruger grundlæggende godkendelse, blokeres på baggrund af den politik for betinget adgang, der er oprettet i Kræv godkendte [apps og appbeskyttelse](identity-access-policies.md#require-approved-apps-and-app-protection).

Hvis du vil blokere Exchange ActiveSync grundlæggende godkendelse på andre enheder, skal du følge trinnene i Bloker [Exchange ActiveSync](/azure/active-directory/conditional-access/howto-policy-approved-app-or-app-protection#block-exchange-activesync-on-all-devices) på alle enheder, hvilket forhindrer Exchange ActiveSync-klienter, der bruger grundlæggende godkendelse på ikke-mobilenheder, i at oprette forbindelse til Exchange Online.

Du kan også bruge godkendelsespolitikker til at [deaktivere Grundlæggende godkendelse](/exchange/clients-and-mobile-in-exchange-online/disable-basic-authentication-in-exchange-online), hvilket tvinger alle klientadgangsanmodninger til at bruge moderne godkendelse.

## <a name="limit-access-to-exchange-online-from-outlook-on-the-web"></a>Begræns adgangen Exchange Online fra Outlook på internettet

Du kan begrænse brugernes mulighed for at hente vedhæftede filer Outlook på internettet enheder på enheder, der ikke er administrerede. Brugere på disse enheder kan få vist og redigere disse filer ved hjælp Office Online uden at lækage og gemme filerne på enheden. Du kan også blokere brugere i at se vedhæftede filer på en ikke-administreret enhed.

Sådan gør du:

1. [Forbind til en Exchange Online Remote PowerShell-session](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).
2. Hvis du ikke allerede har en OWA-postkassepolitik, kan du oprette en med [New-OwaMailboxPolicy-cmdlet'en](/powershell/module/exchange/new-owamailboxpolicy) .
3. Hvis du vil tillade visning af vedhæftede filer, men ingen download, skal du bruge denne kommando:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnly
   ```

4. Hvis du vil blokere vedhæftede filer, skal du bruge denne kommando:

   ```powershell
   Set-OwaMailboxPolicy -Identity Default -ConditionalAccessPolicy ReadOnlyPlusAttachmentsBlocked
   ```

5. I Azure-portalen skal du oprette en ny politik for betinget adgang med disse indstillinger:

   **Opgaver** \> **Brugere og grupper**: Vælg relevante brugere og grupper, der skal medtages og udelades.

   **Opgaver** \> **Skyapps eller -handlinger** \> **Skyapps** \> **Medtag** \> **Vælg apps**: Vælg **Office 365 Exchange Online**

   **Access-kontrolelementer** \> **Session**: Vælg **Brug tvungne appbegrænsninger**

## <a name="require-that-ios-and-android-devices-must-use-outlook"></a>Kræv, at iOS- og Android-enheder skal bruge Outlook

For at sikre at brugere af iOS- og Android-enheder kun kan få adgang til arbejds- eller skoleindhold ved hjælp af Outlook til iOS og Android, skal du have en politik for betinget adgang, der er målrettet disse potentielle brugere.

Se trinnene til konfiguration af denne politik i [Administrere adgang til meddelelsesamarbejde ved hjælp Outlook til iOS og Android](/mem/intune/apps/app-configuration-policies-outlook#apply-conditional-access).

## <a name="set-up-message-encryption"></a>Konfigurere meddelelseskryptering

Med de nye Office 365-meddelelseskryptering (OME)-funktioner, som udnytter beskyttelsesfunktionerne i Azure Information Protection, kan din organisation nemt dele beskyttet mail med hvem som helst på en hvilken som helst enhed. Brugere kan sende og modtage beskyttede meddelelser med andre Microsoft 365 organisationer samt ikke-kunder, der bruger Outlook.com, Gmail og andre mailtjenester.

Du kan få mere at [vide under Konfigurer Office 365-meddelelseskryptering egenskaber](../../compliance/set-up-new-message-encryption-capabilities.md).

## <a name="next-steps"></a>Næste trin

![Trin 4: Politikker for Microsoft 365 skyapps.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

Konfigurere Betingede adgangspolitikker for:

- [Microsoft Teams](teams-access-policies.md)
- [SharePoint](sharepoint-file-access-policies.md)
