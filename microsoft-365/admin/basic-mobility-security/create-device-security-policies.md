---
title: Opret sikkerhedspolitikker for enheder i Grundlæggende mobilitet og sikkerhed
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
search.appverid:
- MET150
description: Brug Grundlæggende mobilitet og sikkerhed til at oprette enhedspolitikker, der beskytter dine organisationsoplysninger.
ms.openlocfilehash: d4e693d27ea71cdd18c9ea668a2102e0ce061b8d
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63591663"
---
# <a name="create-device-security-policies-in-basic-mobility-and-security"></a>Opret sikkerhedspolitikker for enheder i Grundlæggende mobilitet og sikkerhed

Du kan bruge Grundlæggende mobilitet og sikkerhed til at oprette enhedspolitikker, der hjælper med at beskytte dine organisationsoplysninger Microsoft 365 uautoriseret adgang. Du kan anvende politikker på alle mobilenheder i din organisation, hvor brugeren af enheden har en relevant Microsoft 365-licens og har tilmeldt enheden til Grundlæggende mobilitet og sikkerhed.

## <a name="before-you-begin"></a>Før du begynder

> [!IMPORTANT]
> Før du kan oprette en politik for mobilenheder, skal du aktivere og konfigurere Grundlæggende mobilitet og sikkerhed. Få mere at vide under Oversigt over Grundlæggende mobilitet og sikkerhed.

- Få mere at vide om de enheder, apps til mobilenheder og sikkerhedsindstillinger, der understøttes af Basic Mobility og Security. Se [Egenskaber for grundlæggende mobilitet og sikkerhed](capabilities.md).
- Opret sikkerhedsgrupper, der omfatter Microsoft 365 brugere, som du vil udrulle politikker til, og for brugere, som du muligvis ikke vil blokere for at få blokeret adgang til Microsoft 365. Inden du installerer en ny politik for organisationen, anbefaler vi, at du tester politikken ved at udrulle den til et lille antal brugere. Du kan oprette og bruge en sikkerhedsgruppe, der kun omfatter dig selv eller et lille Microsoft 365 brugere, der kan teste politikken for dig. Du kan få mere at vide om [sikkerhedsgrupper under Oprette, redigere eller slette en sikkerhedsgruppe](../email/create-edit-or-delete-a-security-group.md).
- Hvis du vil oprette og implementere standardpolitikker for mobilitet og sikkerhed Microsoft 365, skal du være Microsoft 365 global administrator. Du kan finde flere [oplysninger i Tilladelser i sikkerheds- & Compliance Center](../../security/office-365-security/permissions-in-the-security-and-compliance-center.md).
- Før du implementerer politikker, skal du fortælle din organisation om den potentielle virkning af at registrere en enhed i Grundlæggende mobilitet og sikkerhed. Afhængigt af hvordan du konfigurerer politikkerne, kan ikke-kompilerede enheder blokeres fra at få adgang til Microsoft 365 og data, herunder installerede programmer, billeder og personlige oplysninger på en registreret enhed, og data kan slettes.

> [!NOTE]
> Politikker og adgangsregler, der er oprettet i Grundlæggende mobilitet og sikkerhed for Microsoft 365 Business Standard tilsidesætter Exchange ActiveSync politikker for mobilenheder og adgangsregler for enheder, der er oprettet <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>. Når en enhed er tilmeldt Basic Mobility and Security for Microsoft 365 Business Standard, ignoreres alle Exchange ActiveSync-postkassepolitik eller adgangsregel for enheder, der anvendes på enheden. Du kan få mere at vide Exchange ActiveSync om Exchange ActiveSync [under Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="step-1-create-a-device-policy-and-deploy-to-a-test-group"></a>Trin 1: Opret en enhedspolitik, og installer den i en testgruppe

Før du kan starte, skal du kontrollere, at du har aktiveret og konfigureret Grundlæggende mobilitet og sikkerhed. Du kan finde en vejledning [under Oversigt over Grundlæggende mobilitet og sikkerhed](overview.md).

1. I din browser skal du skrive <https://protection.office.com/devicev2>.

2. Vælg **Opret en politik**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Indstillinger for standardpolitikken for mobilitet og sikkerhedspolitik.":::

3. På siden **Politikindstillinger** skal du angive de krav, du vil have anvendt på mobilenheder i organisationen.

4. **Kræv administration af mailprofil**: Enheder, der ikke har en mailprofil administreret af Grundlæggende mobilitet og sikkerhed, betragtes som ikke kompatible, når de er aktiveret. En enhed kan ikke have en administreret mailprofil, når den ikke er målrettet korrekt, eller hvis brugeren har konfigureret mailkontoen på enheden manuelt. Når du lader den **være ikke aktiveret** (standard), evalueres denne indstilling ikke for overholdelse eller manglende overholdelse. Du kan finde en vejledning til, hvordan brugerne kan overholde reglerne, når denne indstilling er valgt, [under Der blev fundet en eksisterende mailkonto](/intune-user-help/existing-company-email-account-found).

5. På siden **Vil du anvende denne politik nu? skal** du vælge de grupper, du vil anvende denne politik på.

6. Vælg **Opret denne politik**.

Politikken anvendes på enheden for hver bruger, som politikken gælder for, næste gang brugeren logger på Microsoft 365 sin mobilenhed. Hvis brugerne ikke har haft en politik anvendt på deres mobilenhed før, efter du har udrullet politikken, får de en meddelelse på deres enhed, der indeholder trinene til at tilmelde og aktivere Grundlæggende mobilitet og sikkerhed. Du kan få mere at vide [under Tilmeld din mobilenhed ved hjælp af Grundlæggende mobilitet og sikkerhed](enroll-your-mobile-device.md). Indtil de har fuldført tilmeldingen til Basic Mobility and Security, der hostes af Intune-tjenesten, er adgangen til mail, OneDrive og andre tjenester begrænset. Når tilmeldingen er fuldført ved hjælp af Intune-firmaportal appen, kan de bruge tjenesterne, og politikken anvendes på deres enhed.

## <a name="step-2-verify-that-your-policy-works"></a>Trin 2: Kontrollér, at din politik fungerer

Når du har oprettet en enhedspolitik, skal du kontrollere, at politikken fungerer som forventet, før du installerer den i organisationen.

1. I din browser skal du skrive [https://protection.office.com/devicev2](https://protection.office.com/devicev2).
2. Vælg **Få vist listen over administrerede enheder**.
3. Kontrollér status for brugerenheder, der har politikken anvendt. Du ønsker **, at** tilstanden for enheder skal **administreres.**
4. Du kan også udføre en komplet eller selektiv sletning på en enhed ved at klikke på  Nulstilling til fabriksindstillingerne eller  Fjern **firmadata** fra knappen Administrer, når du har valgt en enhed. Du kan finde en vejledning under [Slet en mobilenhed i Microsoft 365.

## <a name="step-3-deploy-a-policy-to-your-organization"></a>Trin 3: Installér en politik for organisationen

Når du har oprettet en enhedspolitik og bekræftet, at den fungerer som forventet, skal du udrulle den i organisationen.

1. Fra din browsertype: [https://protection.office.com/devicev2](https://protection.office.com/devicev2).
2. Vælg den politik, du vil installere, og vælg Rediger **ud** for Grupper **anvendt på.**
3. Søg efter en gruppe, du vil tilføje, og klik på **Vælg**.
4. Vælg **indstillingen Luk** **og Skift.**
5. Vælg **Luk** og **rediger politik.**

Politikken skubbes til mobilenheden for hver bruger, som politikken gælder for, næste gang brugeren logger på Microsoft 365 sin mobilenhed. Hvis brugerne ikke har anvendt en politik på deres mobilenhed, får de en meddelelse på deres enhed med trin for at tilmelde og aktivere den til Grundlæggende mobilitet og sikkerhed. Når de har fuldført tilmeldingen, anvendes politikken på deres enhed. Du kan få mere at vide [under Tilmeld din mobilenhed ved hjælp af Grundlæggende mobilitet og sikkerhed](enroll-your-mobile-device.md).

## <a name="step-4-block-email-access-for-unsupported-devices"></a>Trin 4: Bloker mailadgang for enheder, der ikke understøttes

For at beskytte dine organisationsoplysninger skal du blokere appadgang til mail fra Microsoft 365 til mobilenheder, der ikke understøttes af Grundlæggende mobilitet og sikkerhed. Du kan finde en liste over understøttede enheder under [Understøttede enheder](../../admin/basic-mobility-security/capabilities.md).

**Sådan blokeres appadgang:**

1. I din browser skal du skrive [https://protection.office.com/devicev2](https://protection.office.com/devicev2).
2. Vælg **Administrer indstillinger for adgang til enheder for hele organisationen**.
3. Hvis du vil blokere ikke-understøttede enheder, skal du vælge **Bloker under** Hvis en enhed ikke understøttes af Standardmobilitet og sikkerhed **for Microsoft 365**, og vælg derefter **Gem**.

   :::image type="content" source="../../media/basic-mobility-security/bms-5-block-access.png" alt-text="Indstillingen Grundlæggende mobilitet og sikkerhed blokadgang.":::

## <a name="step-5-choose-security-groups-to-be-excluded-from-conditional-access-checks"></a>Trin 5: Vælg sikkerhedsgrupper, der skal udelukkes fra betingede adgangskontroller

Hvis du vil udelukke nogle personer fra betinget adgangskontrol på deres mobilenheder, og du har oprettet en eller flere sikkerhedsgrupper for disse personer, skal du tilføje sikkerhedsgrupperne her. Personerne i disse grupper gennemtvinges ikke nogen politikker for deres understøttede mobilenheder. Dette er den anbefalede indstilling, hvis du ikke længere ønsker at bruge Grundlæggende mobilitet og sikkerhed i din organisation.

1. I din browser skal du skrive [https://protection.office.com/devicev2](https://protection.office.com/devicev2).

2. Vælg **Administrer indstillinger for adgang til enheder for hele organisationen**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Grundlæggende mobilitet og sikkerhed opret en politikindstilling.":::

3. Vælg **Tilføj** for at tilføje den sikkerhedsgruppe, der indeholder brugere, som du vil udelukke fra at have blokeret adgang Microsoft 365. Når en bruger er blevet føjet til denne liste, kan Microsoft 365 mail, når de bruger en enhed, der ikke understøttes.

4. Vælg den sikkerhedsgruppe, du vil bruge, i **panelet Vælg** gruppe.

5. Vælg navnet og derefter **AddSave** > .

6. På panelet **Indstillinger for adgang til enheder for hele** organisationen skal du vælge **Gem**.

   :::image type="content" source="../../media/basic-mobility-security/bms-8-allow-access.png" alt-text="Indstillingen Grundlæggende mobilitet og sikkerhed tillader adgang.":::

## <a name="what-is-the-impact-of-security-policies-on-different-device-types"></a>Hvad betyder sikkerhedspolitikkerne for forskellige enhedstyper?

Når du anvender en politik på brugerenheder, varierer effekten på hver enhed noget i forhold til enhedstyper. Se følgende tabel for at få eksempler på effekten af politikker på forskellige enheder.

|**Sikkerhedspolitik**|**Android**|**Samsung KNOX**|**iOS**|**Bemærkninger**|
|:-----|:-----|:-----|:-----|:-----|
|Kræv krypteret sikkerhedskopiering|Nej|Ja|Ja|iOS-krypteret sikkerhedskopi påkrævet.|
|Bloker sikkerhedskopiering i skyen|Ja|Ja|Ja|Bloker google-sikkerhedskopiering på Android (nedtonet), sikkerhedskopiering i skyen på iOS.|
|Bloker dokumentsynkronisering|Nej|Nej|Ja|iOS: Bloker dokumenter i skyen.|
|Bloker fotosynkronisering |Nej|Nej|Ja|iOS (indbygget): Bloker Photo Stream.|
|Bloker skærmklip |Nej|Ja|Ja|Blokeret, når du forsøger.|
|Bloker videomøde |Nej|Nej|Ja|FaceTime blokeret på iOS, ikke på Skype eller andre.|
|Bloker afsendelse af diagnostiske data |Nej|Ja|Ja|Bloker afsendelse af Google-nedbrudsrapport på Android.|
|Bloker adgang til App Store |Nej|Ja|Ja|Ikonet App Store mangler på Android-startsiden, deaktiveret Windows, mangler på iOS.|
|Kræv adgangskode til App Store |Nej|Nej|Ja|iOS: Adgangskode påkrævet til iTunes-køb.|
|Bloker forbindelse til flytbart lager |Nej|Ja|I/T|Android: SD-kort er nedtonet i indstillinger, Windows giver brugeren besked, installerede apps er ikke tilgængelige|
|Blokere Bluetooth forbindelse |Se noter|Se noter|Ja|Vi kan ikke deaktivere BlueTooth som en indstilling på Android. I stedet deaktiverer vi alle de transaktioner, der kræver BlueTooth: Advanced Audio Distribution, Audio/Video Remote Control, håndfri enheder, headset, Telefon Book Access og Serial Port. Der vises en lille toastmeddelelse nederst på siden, når en af disse bruges.|

## <a name="what-happens-when-you-delete-a-policy-or-remove-a-user-from-the-policy"></a>Hvad sker der, når du sletter en politik eller fjerner en bruger fra politikken?

Når du sletter en politik eller fjerner en bruger fra en gruppe, som politikken blev installeret i, fjernes politikindstillingerne, Microsoft 365 mailprofilen og cachelagrede mails fra brugerens enhed. Se følgende tabel for at se, hvad der fjernes for de forskellige enhedstyper.

|**Hvad er fjernet**|**iOS**|**Android (herunder Samsung KNOX**|
|:-----|:-----|:-----|
|Administrerede <sup>mailprofiler1</sup>|Ja|Nej|
|Bloker sikkerhedskopiering i skyen|Ja|Nej|

<sup>1</sup> Hvis politikken blev installeret med indstillingen Mailprofil er  administreret, slettes den administrerede mailprofil og cachelagrede mails i den pågældende profil fra brugerenheden.

Politikken fjernes fra mobilenheden for hver bruger, politikken gælder for næste gang, deres enhed tjekker ind med Grundlæggende mobilitet og sikkerhed. Hvis du implementerer en ny politik, der gælder for disse brugerenheder, bliver de bedt om at tilmelde sig grundlæggende mobilitet og sikkerhed igen.

Du kan også slette en enhed helt eller selektivt slette organisationsoplysninger fra enheden. Du kan finde flere oplysninger [i Slette en mobilenhed i Grundlæggende mobilitet og sikkerhed](wipe-mobile-device.md).

## <a name="related-content"></a>Relateret indhold

[Oversigt over Grundlæggende mobilitet og sikkerhed](overview.md) (artikel)\
[Funktioner i grundlæggende mobilitet og sikkerhed](capabilities.md) (artikel)