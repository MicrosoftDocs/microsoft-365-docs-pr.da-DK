---
title: Sammenligning af version af meddelelsekryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Denne artikel hjælper med at forklare forskellene mellem forskellige versioner af meddelelseskryptering.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 64a67ac9423463e4fcf1b5a3ff6c2262801933b0
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66629327"
---
# <a name="compare-versions-of-message-encryption"></a>Sammenlign versioner af meddelelseskryptering

> [!IMPORTANT]
> Den 28. februar 2021 frarådede Microsoft understøttelse af AD RMS i Exchange Online. Hvis du har udrullet et hybridmiljø, hvor dine Exchange-postkasser er online, og du bruger IRM med Active Directory RMS i det lokale miljø, skal du migrere til Azure. Organisationer, der har udrullet i GCC Moderate-miljøet, påvirkes også. Se "Oversigt over AD RMS-udfasning i Exchange Online" i denne artikel for at få flere oplysninger.

I resten af denne artikel sammenlignes ældre Office 365 OME (Message Encryption) med Microsoft Purview-meddelelseskryptering og Avanceret meddelelseskryptering i Microsoft Purview. Microsoft Purview-meddelelseskryptering er en fusion og nyere version af både OME og IRM (Information Rights Management). Der er også skitseret unikke egenskaber ved udrulning i GCC High. De to kan eksistere i din organisation. Du kan få oplysninger om, hvordan de nye funktioner fungerer, [under Office 365 Meddelelseskryptering (OME)](ome.md).

Denne artikel er en del af en større serie artikler om meddelelseskryptering. Denne artikel er beregnet til administratorer og ITPros. Hvis du kun leder efter oplysninger om, hvordan du sender eller modtager en krypteret meddelelse, kan du se listen over artikler i [Meddelelseskryptering](ome.md) og finde den artikel, der passer bedst til dine behov.

## <a name="overview-of-ad-rms-deprecation-in-exchange-online"></a>Oversigt over AD RMS-udfasning i Exchange Online

Exchange Online indeholder IRM-funktionalitet (Information Rights Management), der sikrer online- og offlinebeskyttelse af mails og vedhæftede filer. Som standard bruger Exchange Online Azure Information Protection. Din organisation kan dog have konfigureret Exchange Online IRM til at bruge AD RMS (Active Directory i det lokale miljø Rights Management Service). AD RMS-understøttelse i Exchange Online udgår. Azure Information Protection erstatter i stedet AD RMS helt.

Hvis du vil vurdere, om denne udfasning påvirker din organisation, skal du se [Sådan overfører du AD RMS til Azure RMS i Exchange Online](/exchange/troubleshoot/administration/migrate-ad-rms-to-azure). Denne artikel indeholder anbefalinger til overførselsmuligheder.

## <a name="side-by-side-comparison-of-message-encryption-features-and-capabilities"></a>Sammenligning af funktioner og funktioner til kryptering af meddelelser side om side

|           **Situation**           | **Ældre OME**    | **IRM i AD RMS**        | **Microsoft Purview-meddelelseskryptering** |
|-----------------------------------|-------------------|-------------------|--------------------------|
|*Sender en krypteret mail*        |Via Exchange-regler for mailflow|Slutbrugeren startede fra Outlook Desktop eller Outlook på internettet. eller via Regler for Exchange-mailflow|Slutbrugeren startede fra Outlook Desktop, Outlook til Mac eller Outlook på internettet. Via Exchange-regler for mailflow (også kendt som transportregler) og forebyggelse af datatab (DLP)|
|*Skabelon til administration af rettigheder*       |   NIELSEN      |Indstillingen Videresend ikke og brugerdefinerede skabeloner|Indstillingen Videresend ikke, indstillingen Kun krypteret og brugerdefinerede skabeloner|
|*Modtagertype*                   |Interne og eksterne modtagere|Kun interne modtagere         |Interne og eksterne modtagere|
|*Oplevelse for intern modtager*|Modtagerne modtager en HTML-meddelelse, som de downloader og åbner i en webbrowser eller mobilapp|Indbygget oplevelse i Outlook-klienter|Oprindelig indbygget oplevelse for modtagere i den samme organisation ved hjælp af Outlook-klienter.  Modtagere kan læse meddelelse fra OME-portalen ved hjælp af andre klienter end Outlook (ingen download eller app er påkrævet).|
|*Oplevelse for ekstern modtager*|Modtagerne modtager en HTML-meddelelse, som de downloader og åbner i en webbrowser eller mobilapp|NIELSEN|Indbygget oplevelse for Microsoft 365-modtagere. Alle andre modtagere kan læse meddelelse fra OME-portalen (der kræves ingen download eller app).|
|*Tilladelser til vedhæftede filer*           |Ingen begrænsninger for vedhæftede filer|Vedhæftede filer er beskyttet|Vedhæftede filer er beskyttet for indstillingen Videresend ikke og brugerdefinerede skabeloner. Administratorer kan vælge, om vedhæftede filer kun til indstillingen Kun kryptering er beskyttet.|
|*Byok-understøttelse (Bring Your Own Key)*|Ingen                |Ingen               |BYOK understøttes          |
||

## <a name="advantages-of-microsoft-purview-message-encryption-over-legacy-ome"></a>Fordele ved Microsoft Purview-meddelelseskryptering i forhold til ældre OME

De nye funktioner giver følgende fordele:

- Mulighed for at bruge indstillingen Kun krypteret (hvilket muliggør sikkert samarbejde), indstillingen Videresend ikke og brugerdefinerede begrænsninger.
- Afsendere kan sende mails, der er krypteret med de nye funktioner, manuelt fra Outlook Desktop, Outlook til Mac og Outlook på internettet klienter.
- Microsoft 365-modtagere får mulighed for at bruge en indbygget oplevelse i understøttede Outlook-klienter. Alternativt kan administratorer vælge at vise Microsoft 365-modtagere en brandet oplevelse.
- Konti uden for Microsoft 365, f.eks. Gmail-, Yahoo- og Microsoft-konti, er sammenkædet med OME-portalen, hvilket giver en bedre brugeroplevelse for disse modtagere. Alle andre identiteter bruger en engangskode til at få adgang til krypterede meddelelser.
- Administratorer kan tilpasse branding og oprette flere brandingskabeloner.
- Administratorer kan tilbagekalde mails, der er krypteret med de nye funktioner.
- De nye funktioner indeholder detaljerede anvendelsesrapporter via Security &amp; Compliance Center.

## <a name="microsoft-purview-advanced-message-encryption-capabilities"></a>Funktioner til avanceret meddelelseskryptering i Microsoft Purview

Microsoft Purview Advanced Message Encryption indeholder yderligere funktioner oven på Microsoft Purview-meddelelseskryptering. Du skal have Microsoft Purview-meddelelseskryptering konfigureret i din organisation for at kunne bruge avanceret meddelelseskryptering. Hvis modtagerne vil bruge disse funktioner, skal de desuden få vist og svare for at sikre mails via Microsoft Purview-meddelelseskryptering-portalen. De avancerede funktioner omfatter:

- Tilbagekaldelse af meddelelse

- Meddelelsesudløb

- Flere brandingskabeloner

Avanceret meddelelseskryptering understøttes ikke i GCC High.

Du kan få oplysninger om, hvordan du bruger avanceret meddelelseskryptering, under [Avanceret meddelelseskryptering i Microsoft Purview](ome-advanced-message-encryption.md).

## <a name="unique-characteristics-of-microsoft-purview-message-encryption-in-a-gcc-high-deployment"></a>Entydige egenskaber ved Microsoft Purview-meddelelseskryptering i en GCC High-udrulning

Hvis du planlægger at bruge Microsoft Purview-meddelelseskryptering i et GCC High-miljø, er der nogle unikke egenskaber med hensyn til modtageroplevelsen.

### <a name="encrypted-email-between-gcc-high-and-gcc-high-recipients"></a>Krypteret mail mellem GCC High- og GCC High-modtagere

Afsendere kan kryptere mails manuelt i Outlook til pc og Mac og Outlook på internettet, eller organisationer kan konfigurere en politik til kryptering af mails ved hjælp af regler for Exchange-mailflow.

Modtagere i GCC High modtager den samme indbyggede læseoplevelse i Outlook til pc og Mac og Outlook på internettet som alle andre brugere.

### <a name="encrypted-email-between-gcc-high-and-non-gcc-high-recipients"></a>Krypteret mail mellem GCC High-modtagere og ikke-GCC High-modtagere

Afsendere i GCC High kan sende krypteret mail uden for GCC High-grænsen og omvendt.

Alle modtagere uden for GCC High, herunder kommercielle Microsoft 365-brugere, Outlook.com-brugere og andre brugere af andre mailudbydere, f.eks. Gmail og Yahoo, modtager en indpakningsmail. Denne ombrydermail omdirigerer modtageren til Microsoft Purview-meddelelseskryptering Portal, hvor modtageren kan læse og besvare meddelelsen. Dette er også tilfældet for afsendere uden for GCC High sender OME krypteret mail til GCC High.

## <a name="coexistence-of-legacy-ome-and-microsoft-purview-message-encryption-in-the-same-tenant"></a>Sameksisten af ældre OME og Microsoft Purview-meddelelseskryptering i samme lejer

Du kan bruge både ældre OME og Microsoft Purview-meddelelseskryptering i den samme lejer. Som administrator gør du dette ved at vælge, hvilken version af meddelelseskryptering du vil bruge, når du opretter reglerne for mailflowet.

- Hvis du vil angive den ældre version af OME, skal du bruge regelhandlingen **for Exchange-mailflowet Anvend den tidligere version af OME**.

- Hvis du vil angive Microsoft Purview-meddelelseskryptering, skal du bruge regelhandlingen **Anvend Office 365 meddelelsekryptering og rettighedsbeskyttelse i** Exchange-mailflowet.

Brugerne kan manuelt sende mails, der er krypteret med Microsoft Purview-meddelelseskryptering fra Outlook Desktop, Outlook til Mac og Outlook på internettet.

## <a name="migrate-from-legacy-ome-to-microsoft-purview-message-encryption"></a>Overfør fra ældre OME til Microsoft Purview-meddelelseskryptering

Selvom begge versioner kan eksistere sammen, anbefaler vi på det kraftigste, at du redigerer dine gamle regler for mailflow, der bruger **regelhandlingen Anvend den tidligere version af OME** til at bruge Microsoft Purview-meddelelseskryptering. Opdater disse regler for at bruge regelhandlingen for mailflowet **Anvend Office 365 Meddelelsekryptering og rettighedsbeskyttelse**. Du kan finde instruktioner under [Definer regler for mailflow for at kryptere mails](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-ome"></a>Kom i gang med OME

Normalt aktiveres Microsoft Purview-meddelelseskryptering automatisk for din organisation. Du kan få flere oplysninger om Microsoft Purview-meddelelseskryptering i din organisation under [Konfigurer Microsoft Purview-meddelelseskryptering](set-up-new-message-encryption-capabilities.md).

Den ældre version af OME aktiveres automatisk for din organisation, hvis du har aktiveret Azure Information Protection. Tidligere fungerede ældre OME, selvom Azure Information Protection ikke var aktiveret. Det er ikke længere tilfældet.

Hvis du vil bruge ældre OME, skal du konfigurere regler for mailflow, der bruger regelhandlingen **Anvend den tidligere version af OME**, hvis du har aktiveret Azure Information Protection. Du kan finde instruktioner under [Definer regler for mailflow for at kryptere mails](define-mail-flow-rules-to-encrypt-email.md).
