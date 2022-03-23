---
title: Konfigurer Grundlæggende mobilitet og sikkerhed
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
search.appverid:
- MET150
description: Konfigurer Grundlæggende mobilitet og sikkerhed til at sikre og administrere dine brugeres mobilenheder ved at udføre handlinger som f.eks. fjernsletning af en enhed.
ms.openlocfilehash: bbf7cf84dd996a0e548a76978e8fbba58f40c070
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589802"
---
# <a name="set-up-basic-mobility-and-security"></a>Konfigurer Grundlæggende mobilitet og sikkerhed

Den indbyggede standardmobilitet og sikkerhed til Microsoft 365 hjælper dig med at sikre og administrere brugernes mobilenheder som f.eks. iPhones, iPads, Android-Windows telefoner. Du kan oprette og administrere sikkerhedspolitikker for enheder, slette en enhed eksternt og få vist detaljerede enhedsrapporter.

Har du spørgsmål? Hvis du vil have mere at vide om ofte stillede spørgsmål, skal du se Ofte stillede spørgsmål om grundlæggende mobilitet [og](frequently-asked-questions.yml) sikkerhed. Vær opmærksom på, at du ikke kan bruge en delegeret administratorkonto til at administrere Grundlæggende mobilitet og sikkerhed. Få mere at vide under [Partnere: Tilbyd delegeret administration](https://support.microsoft.com/office/partners-offer-delegated-administration-26530dc0-ebba-415b-86b1-b55bc06b073e). 

Enhedshåndtering er en del af Security & Compliance Center, så du skal gå dertil for at starte konfigurationen af Basic Mobility and Security.

## <a name="activate-the-basic-mobility-and-security-service"></a>Aktivér Standardmobilitets- og sikkerhedstjenesten

1. Log på Microsoft 365 med din globale administratorkonto.

2. Gå til [Aktivér Grundlæggende mobilitet og sikkerhed](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx).

   Det kan tage lidt tid at aktivere Grundlæggende mobilitet og sikkerhed. Når den er færdig, modtager du en mail, der forklarer de næste trin, du skal tage.

## <a name="set-up-mobile-device-management"></a>Konfigurer administration af mobilenheder

Når tjenesten er klar, skal du udføre følgende trin for at afslutte konfigurationen.

### <a name="step-1-required-configure-domains-for-basic-mobility-and-security"></a>Trin 1: (Påkrævet) Konfigurer domæner til grundlæggende mobilitet og sikkerhed

Hvis du ikke har et brugerdefineret domæne knyttet til Microsoft 365, eller hvis du ikke administrerer Windows enheder, kan du springe dette afsnit over. Ellers skal du tilføje DNS-poster for domænet hos din DNS-vært. Hvis du allerede har tilføjet posterne som en del af konfigurationen af dit domæne Microsoft 365, er du klar. Når du har tilføjet posterne, Microsoft 365 brugere i organisationen, som logger på deres Windows-enhed med en mailadresse, der bruger dit brugerdefinerede domæne, omdirigeret til tilmeldingen til Grundlæggende mobilitet og sikkerhed.

Har du brug for hjælp til at konfigurere posterne? Find din domæneregistrator, og vælg registratorens navn for at gå til trinvis hjælp til oprettelse af DNS-post på listen  [iAdd DNS-poster](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) for at forbinde dit domæne. Følg disse instruktioner for at oprette CNAME-poster, der [er beskrevet i Windows registrering uden Azure AD Premium](/mem/intune/enrollment/windows-enroll#simplify-windows-enrollment-without-azure-ad-premium).

Når du har tilføjet de to CNAME-poster, skal du gå tilbage til Security & Compliance Center og gå til **Forebyggelse** af datatabAdministrationfor  >  **at fuldføre** næste trin.

### <a name="step-2-required-configure-an-apns-certificate-for-ios-devices"></a>Trin 2: (Påkrævet) Konfigurer et APNs-certifikat til iOS-enheder

For at administrere iOS-enheder iPad og iPhones skal du oprette et APNS-certifikat.

1. Log på Microsoft 365 med din globale administratorkonto.

2. I din browsertype: [https://protection.office.com](https://protection.office.com/).

3.  **SelectData loss**  **preventionDevice** > management, og vælg **APNs Certificate for iOS devices**.

4. På siden Apple Push Notification Certificate Indstillinger du  **vælgeNext**.

5.  **VælgDownload din CSR-fil,**  og gem anmodningen om certifikatunder signering til et sted på din computer, som du kan huske.  **VælgNæste**.

6. På siden Opret et APNs-certifikat:

   - Vælg Apple APNS Portal for at åbne Apple Push Certificates Portal.
   - Log på med et Apple-id.

     > [!IMPORTANT]
     > Brug virksomhedens Apple-id, der er knyttet til en mailkonto, som forbliver hos din organisation, også selvom den bruger, der administrerer kontoen, forlader virksomheden. Gem dette id, da du skal bruge det samme id, når certifikatet skal fornys.

   - Vælg Opret et certifikat, og accepter Vilkår for anvendelse.
   - Gå til den anmodning om certifikatunder signering, du har downloadet til computeren fra Microsoft 365 og vælgUpload.
   - Download det APN-certifikat, der er oprettet af Apple Push Certificate Portal, til computeren.

     > [!TIP]
     > Hvis du har problemer med at downloade certifikatet, skal du opdatere din browser.

7. Gå tilbage til Microsoft 365 og vælg **Næste**.

8. Gå til det APN-certifikat, du har downloadet fra Apple Push Certificates Portal.

9.   **VælgFind**.

### <a name="step-3-recommended-set-up-multi-factor-authentication"></a>Trin 3: (Anbefalet) Konfigurer multifaktorgodkendelse

MFA hjælper med at sikre logon på Microsoft 365 til registrering af mobilenheder ved at kræve en anden form for godkendelse. Brugerne skal bekræfte et telefonopkald, en sms-besked eller en appmeddelelse på deres mobilenhed efter korrekt indtastning af adgangskoden til deres arbejdskonto. De kan først tilmelde deres enhed, når den anden form for godkendelse er fuldført. Når brugerenheder er tilmeldt Grundlæggende mobilitet og sikkerhed, kan brugerne få adgang til Microsoft 365 ressourcer, der kun har deres arbejdskonto.

Hvis du vil lære, hvordan du aktiverer MFA i Azure  [AD-portalen, skal du se Konfigurere multifaktorgodkendelse](../security-and-compliance/set-up-multi-factor-authentication.md).

Når du har konfigureret MFA, skal du gå tilbage til Security & Compliance Center og gå  **tilData loss preventionDevice** >  **managementDevice** >  **policiesfor**  at fuldføre næste trin.

### <a name="step-4-recommended-manage-device-security-policies"></a>Trin 4: (Anbefalet) Administrer sikkerhedspolitikker for enheder

Det næste trin er at oprette og implementere sikkerhedspolitikker for enheder for at beskytte Microsoft 365 organisationens data. Du kan f.eks. hjælpe med at forhindre datatab, hvis en bruger mister sin enhed ved at oprette en politik for at låse enheder efter fem minutters inaktivitet og slette enheder efter tre logonfejl.

1. Log på Microsoft 365 med din globale administratorkonto.

2.  [VælgActivate Mobile Device Management](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). Hvis tjenesten er aktiveret, vises der i stedet et link til Administrere enheder ved at følge  [aktiveringstrinnene](https://admin.microsoft.com/adminportal/home#/MifoDevices) .

3. Gå  **tilDevice-politikker**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Grundlæggende indstillinger for sikkerheds- og mobilitetspolitik.":::

4. Opret og implementer sikkerhedspolitikker for enheder, der er relevante for din organisation, ved at følge trinnene  [iOprette sikkerhedspolitikker for enheder i Grundlæggende mobilitet og sikkerhed](create-device-security-policies.md).

> [!TIP]
>
> - Når du opretter en ny politik, kan det være en god ide at indstille politikken til at tillade adgang og rapportere om overtrædelse af politikken, hvis en brugerenhed ikke overholder politikken. Dette giver dig mulighed for at se, hvor mange mobilenheder, der påvirkes af politikken uden at blokere adgang Microsoft 365.
>
> - Før du installerer en ny politik for alle i organisationen, anbefaler vi, at du tester den på de enheder, der bruges af et lille antal brugere.
>
> - Før du implementerer politikker, skal du desuden give din organisation besked om de potentielle konsekvenser af at registrere en enhed i Grundlæggende mobilitet og sikkerhed. Afhængigt af hvordan du konfigurerer politikkerne, kan enheder, der ikke overholder politikker (ikke-kompatible enheder), blive blokeret fra at få adgang til Microsoft 365. Ikke-kompatible enheder kan også have apps installeret, fotos og andre personlige oplysninger, som på en registreret enhed kan slettes, hvis enheden slettes. Du kan finde flere oplysninger [i Slette en mobilenhed i Grundlæggende mobilitet og sikkerhed](wipe-mobile-device.md).

## <a name="make-sure-users-enroll-their-devices"></a>Sørg for, at brugerne tilmelder deres enheder

Når du har oprettet og installeret en politik for administration af mobilenheder, modtager hver Microsoft 365-bruger med licens i organisationen, som politikken for enheder gælder, en registreringsmeddelelse, næste gang brugeren logger på Microsoft 365 fra sin mobilenhed. De skal udføre registrerings- og aktiveringstrinnene, før de kan få adgang Microsoft 365 mails og dokumenter. Du kan få mere at vide [under Tilmeld din mobilenhed ved hjælp af Grundlæggende mobilitet og sikkerhed](enroll-your-mobile-device.md).

> [!IMPORTANT]
> Hvis en brugers foretrukne sprog ikke understøttes af registreringsprocessen, kan brugerne modtage registreringsbeskeder og trin på deres mobilenheder på et andet sprog. Ikke alle sprog, der understøttes Microsoft 365 sprog, understøttes i øjeblikket i registreringsprocessen på mobilenheder.

Brugere med Android- eller iOS-enheder skal installere Firmaportal-appen som en del af tilmeldingsprocessen.

## <a name="related-content"></a>Relateret indhold

[Funktioner i Grundlæggende mobilitet og sikkerhed](capabilities.md) (artikel)\
[Opret sikkerhedspolitikker for enheder i Grundlæggende mobilitet og sikkerhed](create-device-security-policies.md) (artikel)