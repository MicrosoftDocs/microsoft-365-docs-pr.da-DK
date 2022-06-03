---
title: Konfigurer Basic Mobility og Security
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
description: Konfigurer Basic Mobility og Security for at sikre og administrere dine brugeres mobilenheder ved at udføre handlinger, f.eks. fjernviskering af en enhed.
ms.openlocfilehash: 04480e59177dc9b51bc50e413715e0ad82c7f461
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863170"
---
# <a name="set-up-basic-mobility-and-security"></a>Konfigurer Basic Mobility og Security

Den indbyggede Basic Mobility and Security til Microsoft 365 hjælper dig med at sikre og administrere brugernes mobilenheder, f.eks. iPhones, iPads, Androids og Windows telefoner. Du kan oprette og administrere politikker for enhedssikkerhed, fjerne sletning af en enhed og få vist detaljerede enhedsrapporter.

Har du spørgsmål? Hvis du vil have hjælp til at besvare almindelige spørgsmål, skal du se [Grundlæggende mobilitet og sikkerhed Ofte stillede spørgsmål](frequently-asked-questions.yml). Vær opmærksom på, at du ikke kan bruge en delegeret administratorkonto til at administrere Grundlæggende mobilitet og sikkerhed. Du kan finde flere oplysninger under [Partnere: Tilbyd delegeret administration](https://support.microsoft.com/office/partners-offer-delegated-administration-26530dc0-ebba-415b-86b1-b55bc06b073e). 

Enhedshåndtering er en del af Security & Compliance Center, så du skal gå dertil for at starte konfigurationen af Grundlæggende mobilitet og Sikkerhed.

## <a name="activate-the-basic-mobility-and-security-service"></a>Aktivér tjenesten Basic Mobility and Security

1. Log på for at Microsoft 365 med din globale administratorkonto.

2. Gå til [Aktivér grundlæggende mobilitet og sikkerhed](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx).

   Det kan tage noget tid at aktivere grundlæggende mobilitet og sikkerhed. Når den er færdig, modtager du en mail, der forklarer de næste trin, der skal udføres.

## <a name="set-up-mobile-device-management"></a>Konfigurer mobil Enhedshåndtering

Når tjenesten er klar, skal du fuldføre følgende trin for at fuldføre konfigurationen.

### <a name="step-1-required-configure-domains-for-basic-mobility-and-security"></a>Trin 1: (påkrævet) Konfigurer domæner for Grundlæggende mobilitet og sikkerhed

Hvis du ikke har et brugerdefineret domæne, der er knyttet til Microsoft 365, eller hvis du ikke administrerer Windows enheder, kan du springe dette afsnit over. Ellers skal du tilføje DNS-poster for domænet hos din DNS-vært. Hvis du allerede har tilføjet posterne som en del af indstillingerne for dit domæne med Microsoft 365, er du klar. Når du har tilføjet posterne, omdirigeres Microsoft 365 brugere i din organisation, der logger på deres Windows enhed med en mailadresse, der bruger dit brugerdefinerede domæne, til at tilmelde sig Basic Mobility and Security.

Har du brug for hjælp til at konfigurere posterne? Find din domæneregistrator, og vælg navnet på registratoren for at gå til trinvis hjælp til oprettelse af DNS-post på listen i [Tilføj DNS-poster for at oprette forbindelse til dit domæne](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider). Brug disse instruktioner til at oprette CNAME-poster, der er beskrevet i [Forenkle Windows tilmelding uden Azure AD Premium](/mem/intune/enrollment/windows-enroll#simplify-windows-enrollment-without-azure-ad-premium).

Når du har tilføjet de to CNAME-poster, skal du gå tilbage til Security & Compliance Center og gå til Administration **af forebyggelse af** >  datatab **Enhedshåndtering** for at fuldføre næste trin.

### <a name="step-2-required-configure-an-apns-certificate-for-ios-devices"></a>Trin 2: (påkrævet) Konfigurer et APN-certifikat til iOS-enheder

Hvis du vil administrere iOS-enheder, f.eks. iPad og iPhones, skal du oprette et APN-certifikat.

1. Log på for at Microsoft 365 med din globale administratorkonto.

2. Gå til [Microsoft 365 Administration](https://portal.office.com/adminportal/home?#/MifoDevices), og vælg **APN-certifikat til iOS**.

4. Vælg **Næste** på siden Certifikat til Apple Push-meddelelse Indstillinger.

5. Vælg **Download din CSR-fil** , og gem anmodningen om signering af certifikat et sted på din computer, som du kan huske. Vælg **Næste**.

6. På siden Opret et APN-certifikat:

   - Vælg Apple APNS-portalen for at åbne Portal til Apple Push-certifikater.
   - Log på med et Apple-id.

     > [!IMPORTANT]
     > Brug et Apple-firma-id, der er knyttet til en mailkonto, som forbliver hos din organisation, selvom den bruger, der administrerer kontoen, forlader kontoen. Gem dette id, fordi du skal bruge det samme id, når det er tid til at forny certifikatet.

   - Vælg Opret et certifikat, og acceptér Vilkår for anvendelse.
   - Gå til den anmodning om signering af certifikat, du har downloadet til din computer fra Microsoft 365, og vælgUpload.
   - Download det APN-certifikat, der er oprettet af Apple Push-certifikatportalen, til din computer.

     > [!TIP]
     > Hvis du har problemer med at downloade certifikatet, skal du opdatere din browser.

7. Gå tilbage til Microsoft 365, og vælg **Næste**.

8. Gå til det APN-certifikat, du har downloadet fra Portal til Apple Push-certifikater.

9. Vælg **Udfør**.

### <a name="step-3-recommended-set-up-multi-factor-authentication"></a>Trin 3: (Anbefales) Konfigurer multifaktorgodkendelse

MFA hjælper med at sikre logon på Microsoft 365 til tilmelding af mobilenheder ved at kræve en anden form for godkendelse. Brugerne skal bekræfte et telefonopkald, en sms eller en appmeddelelse på deres mobilenhed, når de har angivet adgangskoden til deres arbejdskonto korrekt. De kan først tilmelde deres enhed, når denne anden form for godkendelse er fuldført. Når brugerenheder er tilmeldt Basic Mobility and Security, kan brugerne få adgang til Microsoft 365 ressourcer med kun deres arbejdskonto.

Hvis du vil vide mere om, hvordan du aktiverer MFA på Azure AD-portalen, skal du se [Konfigurer multifaktorgodkendelse](../security-and-compliance/set-up-multi-factor-authentication.md).

Når du har konfigureret MFA, skal du gå tilbage til Security & Compliance Center og navigere til Forebyggelse **af** >  datatab **Enhedspolitikker** >  for at fuldføre næste trin.

### <a name="step-4-recommended-manage-device-security-policies"></a>Trin 4: (Anbefales) Administrer politikker for enhedssikkerhed

Det næste trin er at oprette og installere politikker for enhedssikkerhed for at beskytte dine Microsoft 365 organisationsdata. Du kan f.eks. hjælpe med at forhindre tab af data, hvis en bruger mister sin enhed ved at oprette en politik for at låse enheder efter fem minutters inaktivitet og slette enheder efter tre logonfejl.

1. Log på for at Microsoft 365 med din globale administratorkonto.

2. Vælg [Aktivér mobil Enhedshåndtering](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). Hvis tjenesten er aktiveret, får du i stedet vist et link til [Administrer enheder](https://admin.microsoft.com/adminportal/home#/MifoDevices) i aktiveringstrinnene.

3. Gå til **Enhedspolitikker**.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Grundlæggende indstillinger for sikkerheds- og mobilitetspolitik.":::

4. Opret og udrul de politikker for enhedssikkerhed, der er relevante for din organisation, ved at følge trinnene i [Opret sikkerhedspolitikker for enheder i Grundlæggende mobilitet og sikkerhed](create-device-security-policies.md).

> [!TIP]
>
> - Når du opretter en ny politik, kan det være en god idé at angive politikken til at tillade adgangs- og rapportpolitikovertrædelse, hvor en brugerenhed ikke overholder politikken. Dette giver dig mulighed for at se, hvor mange mobilenheder der påvirkes af politikken uden at blokere adgangen til Microsoft 365.
>
> - Før du udruller en ny politik til alle i din organisation, anbefaler vi, at du tester den på de enheder, der bruges af et lille antal brugere.
>
> - Før du installerer politikker, skal du også give din organisation besked om de potentielle virkninger af at tilmelde en enhed til Basic Mobility and Security. Afhængigt af hvordan du konfigurerer politikkerne, kan enheder, der ikke overholder politikkerne (ikke-kompatible enheder), blive blokeret fra at få adgang til Microsoft 365. Enheder, der ikke overholder angivne standarder, kan også have apps installeret, billeder og andre personlige oplysninger, som på en tilmeldt enhed kan slettes, hvis enheden slettes. Du kan finde flere oplysninger under [Slet en mobilenhed i Grundlæggende mobilitet og sikkerhed](wipe-mobile-device.md).

## <a name="make-sure-users-enroll-their-devices"></a>Sørg for, at brugerne tilmelder deres enheder

Når du har oprettet og installeret en politik for administration af mobilenheder, modtager alle licenserede Microsoft 365 bruger i organisationen, som enhedspolitikken gælder for, en tilmeldingsmeddelelse, næste gang de logger på Microsoft 365 fra deres mobilenhed. De skal fuldføre tilmeldings- og aktiveringstrinnene, før de kan få adgang til Microsoft 365 mail og dokumenter. Du kan finde flere oplysninger under [Tilmeld din mobilenhed ved hjælp af Basic Mobility og Security](enroll-your-mobile-device.md).

> [!IMPORTANT]
> Hvis en brugers foretrukne sprog ikke understøttes af tilmeldingsprocessen, modtager brugerne muligvis tilmeldingsmeddelelser og trin på deres mobilenheder på et andet sprog. Ikke alle sprog, der understøttes i Microsoft 365 understøttes i øjeblikket for tilmeldingsprocessen på mobilenheder.

Brugere med Android- eller iOS-enheder skal installere Firmaportal-appen som en del af tilmeldingsprocessen.

## <a name="related-content"></a>Relateret indhold

[Funktioner i Grundlæggende mobilitet og sikkerhed](capabilities.md) (artikel)\
[Opret politikker for enhedssikkerhed i Grundlæggende mobilitet og sikkerhed](create-device-security-policies.md) (artikel)
