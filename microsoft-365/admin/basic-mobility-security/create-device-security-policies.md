---
title: Opret politikker for enhedssikkerhed i Grundlæggende mobilitet og sikkerhed
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
description: Brug Basic Mobility and Security til at oprette enhedspolitikker, der beskytter dine organisationsoplysninger.
ms.openlocfilehash: f6cbcd72f5e5cae93b7fa775d7bce6f2906f454e
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863225"
---
# <a name="create-device-security-policies-in-basic-mobility-and-security"></a>Opret politikker for enhedssikkerhed i Grundlæggende mobilitet og sikkerhed

Du kan bruge Basic Mobility and Security til at oprette enhedspolitikker, der hjælper med at beskytte organisationens oplysninger om Microsoft 365 mod uautoriseret adgang. Du kan anvende politikker på alle mobilenheder i din organisation, hvor brugeren af enheden har en gældende Microsoft 365 licens og har tilmeldt enheden i Basic Mobility and Security.

## <a name="before-you-begin"></a>Før du begynder

> [!IMPORTANT]
> Før du kan oprette en politik for mobilenheder, skal du aktivere og konfigurere Grundlæggende mobilitet og sikkerhed. Du kan finde flere oplysninger under Oversigt over grundlæggende mobilitet og sikkerhed.

- Få mere at vide om de enheder, mobilapps og sikkerhedsindstillinger, som Basic Mobility og Security understøtter. Se [Funktioner i Grundlæggende mobilitet og sikkerhed](capabilities.md).
- Opret sikkerhedsgrupper, der omfatter Microsoft 365 brugere, som du vil installere politikker på, og for brugere, som du måske vil udelukke fra at blive blokeret adgang til Microsoft 365. Vi anbefaler, at du tester politikken ved at udrulle den til et lille antal brugere, før du installerer en ny politik i din organisation. Du kan oprette og bruge en sikkerhedsgruppe, der kun indeholder dig selv eller et lille antal Microsoft 365 brugere, der kan teste politikken for dig. Hvis du vil vide mere om sikkerhedsgrupper, skal du se [Opret, rediger eller slet en sikkerhedsgruppe](../email/create-edit-or-delete-a-security-group.md).
- Hvis du vil oprette og installere grundlæggende mobilitets- og sikkerhedspolitikker i Microsoft 365, skal du være Microsoft 365 global administrator. Du kan finde flere oplysninger [under Tilladelser i Security & Compliance Center](../../security/office-365-security/permissions-in-the-security-and-compliance-center.md).
- Før du installerer politikker, skal du give din organisation besked om de potentielle virkninger af at tilmelde en enhed til Basic Mobility and Security. Afhængigt af hvordan du konfigurerer politikkerne, kan enheder, der ikke overholder politikken, blive blokeret fra at få adgang til Microsoft 365 og data, herunder installerede programmer, billeder og personlige oplysninger på en tilmeldt enhed, og data kan slettes.

> [!NOTE]
> Politikker og adgangsregler, der er oprettet i Grundlæggende mobilitet og sikkerhed for Microsoft 365 Business Standard tilsidesætter Exchange ActiveSync politikker for postkasser på mobilenheder og regler for enhedsadgang, der er oprettet i <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange Administration</a>. Når en enhed er tilmeldt Basic Mobility and Security for Microsoft 365 Business Standard, ignoreres alle Exchange ActiveSync politik for postkasser på mobilenheder eller regler for enhedsadgang, der er anvendt på enheden. Du kan få mere at vide om Exchange ActiveSync [under Exchange ActiveSync i Exchange Online](/exchange/clients-and-mobile-in-exchange-online/exchange-activesync/exchange-activesync).

## <a name="step-1-create-a-device-policy-and-deploy-to-a-test-group"></a>Trin 1: Opret en enhedspolitik, og udrul til en testgruppe

Før du kan starte, skal du sørge for, at du har aktiveret og konfigureret Basic Mobility and Security. Du kan finde instruktioner under [Oversigt over grundlæggende mobilitet og sikkerhed](overview.md).

1. Skriv fra din browser <https://compliance.microsoft.com/basicmobilityandsecurity>.

2. Vælg **Opret en politik**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Indstillinger for grundlæggende mobilitets- og sikkerhedspolitik.":::

3. På siden **Politikindstillinger** skal du angive de krav, du vil anvende på mobilenheder i din organisation.

4. **Kræv administration af mailprofil**: Når det er aktiveret, anses enheder, der ikke har en mailprofil, der administreres af Basic Mobility og Security, for ikke at være kompatible. En enhed kan ikke have en administreret mailprofil, når den ikke er målrettet korrekt, eller hvis brugeren manuelt konfigurerer mailkontoen på enheden. Når du lader indstillingen **ikke være aktiveret** (standard), evalueres denne indstilling ikke for overholdelse eller manglende overholdelse. Du kan finde oplysninger om, hvordan brugerne kan blive kompatible, når denne indstilling er valgt, under [En eksisterende mailkonto blev fundet](/intune-user-help/existing-company-email-account-found).

5. På siden **Vil du anvende denne politik nu? skal du** vælge de grupper, som politikken skal anvendes på.

6. Vælg **Opret denne politik**.

Politikken pushes til enheden for hver bruger, som politikken gælder for, næste gang brugeren logger på Microsoft 365 ved hjælp af sin mobilenhed. Hvis brugerne ikke har fået anvendt en politik på deres mobilenhed, får de en meddelelse på deres enhed, der indeholder trinnene til tilmelding og aktivering af Grundlæggende mobilitet og sikkerhed, når du har installeret politikken. Du kan finde flere oplysninger under [Tilmeld din mobilenhed ved hjælp af Basic Mobility og Security](enroll-your-mobile-device.md). Indtil de fuldfører tilmeldingen til Basic Mobility and Security, der hostes af Intune-tjenesten, er adgangen til mail, OneDrive og andre tjenester begrænset. Når de har fuldført tilmeldingen ved hjælp af Intune-firmaportal-appen, kan de bruge tjenesterne, og politikken anvendes på deres enhed.

## <a name="step-2-verify-that-your-policy-works"></a>Trin 2: Kontrollér, at din politik fungerer

Når du har oprettet en enhedspolitik, skal du kontrollere, at politikken fungerer som forventet, før du installerer den i din organisation.

1. Skriv fra din browser [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. Vælg **Vis listen over administrerede enheder**.
3. Kontrollér status for de brugerenheder, hvor politikken er anvendt. Du vil have **, at tilstanden** for enheder skal **administreres.**
4. Du kan også foretage en komplet eller selektiv sletning på en enhed ved at klikke på **Nulstil fabrik** eller **Fjern firmadata** fra knappen **Administrer** , når du har valgt en enhed. Du kan finde instruktioner under [Slet en mobilenhed i Microsoft 365.

## <a name="step-3-deploy-a-policy-to-your-organization"></a>Trin 3: Udrul en politik til din organisation

Når du har oprettet en enhedspolitik og bekræftet, at den fungerer som forventet, skal du installere den i din organisation.

1. Fra din browsertype: [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. Vælg den politik, du vil installere, og vælg **Rediger** ud for **Grupper, der er anvendt på.**
3. Søg efter en gruppe, der skal tilføjes, og klik på **Vælg**.
4. Vælg **Indstillingen Luk** og **Skift.**
5. Vælg **Luk** og **rediger politik.**

Politikken pushes til hver brugers mobilenhed, som politikken gælder for, næste gang brugeren logger på Microsoft 365 fra sin mobilenhed. Hvis brugerne ikke har fået anvendt en politik på deres mobilenhed, får de en meddelelse på deres enhed med trin til at tilmelde og aktivere den til Basic Mobility and Security. Når de har fuldført tilmeldingen, anvendes politikken på deres enhed. Du kan finde flere oplysninger under [Tilmeld din mobilenhed ved hjælp af Basic Mobility og Security](enroll-your-mobile-device.md).

## <a name="step-4-block-email-access-for-unsupported-devices"></a>Trin 4: Bloker mailadgang for ikke-understøttede enheder

For at hjælpe med at beskytte dine organisationsoplysninger skal du blokere appens adgang til Microsoft 365 mail til mobilenheder, der ikke understøttes af Basic Mobility og Security. Du kan se en liste over understøttede enheder under [Understøttede enheder](../../admin/basic-mobility-security/capabilities.md).

**Sådan blokerer du appadgang:**

1. Skriv fra din browser [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).
2. Vælg **Administrer indstillinger for enhedsadgang i hele organisationen**.
3. Hvis du vil blokere enheder, der ikke understøttes, skal du vælge **Adgang** under **Hvis en enhed ikke understøttes af Grundlæggende mobilitet og sikkerhed for Microsoft 365** og derefter vælge **Gem**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-access.png" alt-text="Grundlæggende mobilitet og sikkerhed blokerer adgangsmulighed.":::

## <a name="step-5-choose-security-groups-to-be-excluded-from-conditional-access-checks"></a>Trin 5: Vælg de sikkerhedsgrupper, der skal udelukkes fra kontrol af betinget adgang

Hvis du vil udelukke nogle personer fra kontrol af betinget adgang på deres mobilenheder, og du har oprettet en eller flere sikkerhedsgrupper for disse personer, skal du tilføje sikkerhedsgrupperne her. Personerne i disse grupper vil ikke få gennemtvunget nogen politikker for deres understøttede mobilenheder. Dette er den anbefalede indstilling, hvis du ikke længere vil bruge Basic Mobility og Security i din organisation.

1. Skriv fra din browser [https://compliance.microsoft.com/basicmobilityandsecurity](https://compliance.microsoft.com/basicmobilityandsecurity).

2. Vælg **Administrer indstillinger for enhedsadgang i hele organisationen**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Grundlæggende mobilitet og sikkerhed skaber en politikmulighed.":::

3. Vælg **Tilføj** for at tilføje den sikkerhedsgruppe, der indeholder brugere, som du vil udelukke fra at have blokeret adgang til Microsoft 365. Når en bruger er føjet til denne liste, kan vedkommende få adgang til Microsoft 365 mail, når vedkommende bruger en enhed, der ikke understøttes.

4. Vælg den sikkerhedsgruppe, du vil bruge, i panelet **Vælg gruppe** .

5. Vælg navnet, og tilføj derefter **Tilføj** > **gem**.

6. Vælg **Gem** på panelet **Indstillinger for enhedsadgang i hele organisationen**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-groups.png" alt-text="Basic Mobility and Security giver adgangsmulighed.":::

## <a name="what-is-the-impact-of-security-policies-on-different-device-types"></a>Hvad er virkningen af sikkerhedspolitikker på forskellige enhedstyper?

Når du anvender en politik på brugerenheder, varierer indvirkningen på hver enhed noget blandt enhedstyper. Se følgende tabel for at få eksempler på virkningen af politikker på forskellige enheder.

|**Sikkerhedspolitik**|**Android**|**Samsung KNOX**|**Ios**|**Bemærkninger**|
|:-----|:-----|:-----|:-----|:-----|
|Kræv krypteret sikkerhedskopiering|Nej|Ja|Ja|Der kræves krypteret iOS-sikkerhedskopiering.|
|Bloker cloudsikkerhedskopiering|Ja|Ja|Ja|Bloker Google-sikkerhedskopiering på Android (nedtonet), cloudsikkerhedskopiering på iOS.|
|Bloker dokumentsynkronisering|Nej|Nej|Ja|iOS: Bloker dokumenter i skyen.|
|Bloker fotosynkronisering |Nej|Nej|Ja|iOS (oprindelig): Bloker Photo Stream.|
|Bloker hentning af skærmbillede |Nej|Ja|Ja|Blokeret, når det forsøges.|
|Bloker videokonference |Nej|Nej|Ja|FaceTime er blokeret på iOS, ikke på Skype eller andre.|
|Bloker afsendelse af diagnosticeringsdata |Nej|Ja|Ja|Bloker afsendelse af Google-nedbrudsrapport på Android.|
|Bloker adgang til App Store |Nej|Ja|Ja|App store-ikonet mangler på Android-startsiden, deaktiveret på Windows, mangler på iOS.|
|Kræv adgangskode til App Store |Nej|Nej|Ja|iOS: Adgangskode kræves til iTunes-køb.|
|Bloker forbindelse til flytbart lager |Nej|Ja|NIELSEN|Android: SD-kort er nedtonet under indstillinger, Windows giver brugeren besked, er de installerede apps ikke tilgængelige|
|Bloker Bluetooth forbindelse |Se noter|Se noter|Ja|Vi kan ikke deaktivere BlueTooth som en indstilling på Android. I stedet deaktiverer vi alle de transaktioner, der kræver BlueTooth: Avanceret lyddistribution, Lyd-/video-fjernbetjening, håndfri enheder, headset, Telefon Book Access og Serial Port. Der vises en lille toastmeddelelse nederst på siden, når nogen af disse bruges.|

## <a name="what-happens-when-you-delete-a-policy-or-remove-a-user-from-the-policy"></a>Hvad sker der, når du sletter en politik eller fjerner en bruger fra politikken?

Når du sletter en politik eller fjerner en bruger fra en gruppe, som politikken blev installeret i, kan politikindstillingerne, Microsoft 365 mailprofil og cachelagrede mails blive fjernet fra brugerens enhed. Se følgende tabel for at se, hvad der er fjernet for de forskellige enhedstyper.

|**Hvad er fjernet**|**Ios**|**Android (herunder Samsung KNOX**|
|:-----|:-----|:-----|
|Administrerede mailprofiler<sup>1</sup>|Ja|Nej|
|Bloker cloudsikkerhedskopiering|Ja|Nej|

<sup>1</sup> Hvis politikken blev installeret med indstillingen **Mailprofil administreres** valgt, slettes den administrerede mailprofil og cachelagrede mails i den pågældende profil fra brugerenheden.

Politikken fjernes fra mobilenheden for hver bruger, som politikken gælder for, næste gang enheden tjekker ind med Basic Mobility og Security. Hvis du installerer en ny politik, der gælder for disse brugerenheder, bliver de bedt om at tilmelde sig Basic Mobility og Security igen.

Du kan også slette en enhed helt eller selektivt slette organisationsoplysninger fra enheden. Du kan finde flere oplysninger under [Slet en mobilenhed i Grundlæggende mobilitet og sikkerhed](wipe-mobile-device.md).

## <a name="related-content"></a>Relateret indhold

[Oversigt over grundlæggende mobilitet og sikkerhed](overview.md) (artikel)\
[Funktioner i grundlæggende mobilitet og sikkerhed](capabilities.md) (artikel)