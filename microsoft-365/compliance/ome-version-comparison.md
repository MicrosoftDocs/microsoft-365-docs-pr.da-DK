---
title: Sammenligning af meddelelseskryptering (OME)
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
description: Denne artikel hjælper med at forklare forskellene mellem de forskellige versioner Office 365-meddelelseskryptering.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 508a129cd472c8843e2af4a012560b17a44c49aa
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587738"
---
# <a name="compare-versions-of-ome"></a>Sammenlign versioner af OME

> [!IMPORTANT]
> Den 28. februar 2021 forrådede Microsoft support til AD RMS Exchange Online. Hvis du har installeret et hybridmiljø, hvor dine Exchange-postkasser er online, og du bruger IRM med Active Directory RMS lokalt, skal du overføre til Azure. Organisationer, der har installeret i GCC moderate miljø, påvirkes også. Se "Overview of AD RMS deprecation in Exchange Online" in this article for information.

Resten af denne artikel sammenligner ældre Office 365-meddelelseskryptering (OME) med de nye OME-funktioner og Avanceret kryptering af meddelelser i Office 365. De nye funktioner er en fusion og en nyere version af både OME og Information Rights Management (IRM). Unikke egenskaber ved implementering i GCC High fremhæves også. De to kan være i din organisation. Du kan finde oplysninger om, hvordan de nye funktioner [fungerer under Office 365-meddelelseskryptering (OME)](ome.md).

Denne artikel er en del af en større række artikler om Office 365-meddelelseskryptering. Denne artikel er beregnet til administratorer og ITPros. Hvis du blot leder efter oplysninger om at sende eller modtage en krypteret meddelelse, kan du se listen over artikler i [Office 365-meddelelseskryptering (OME)](ome.md) og finde den artikel, der passer bedst til dine behov.

## <a name="overview-of-ad-rms-deprecation-in-exchange-online"></a>Oversigt over udrådning af AD RMS i Exchange Online

Exchange Online IRM-funktionalitet (Information Rights Management), der giver online- og offlinebeskyttelse af mails og vedhæftede filer. Som standard bruger Exchange Online Azure Information Protection. Din organisation kan dog have konfigureret Exchange Online IRM til at bruge en lokal ACTIVE Directory Rights Management Service (AD RMS). AD RMS-understøttelse Exchange Online din politik om, at en AD RMS-understøttelse trækkes tilbage. I stedet erstatter Azure Information Protection helt AD RMS.

For at vurdere, om denne udrådning påvirker din organisation, skal du se Sådan overføres [AD RMS til Azure RMS Exchange Online](/exchange/troubleshoot/administration/migrate-ad-rms-to-azure). Denne artikel indeholder anbefalinger om indstillinger for overførsel.

## <a name="side-by-side-comparison-of-ome-features-and-capabilities"></a>Side om side-sammenligning af OME-funktioner og -egenskaber

|           **Situation**           | **Ældre OME**    | **IRM i AD RMS**        | **Nye OME-funktioner** |
|-----------------------------------|-------------------|-------------------|--------------------------|
|*Afsendelse af en krypteret mail*        |Gennem Exchange regler for mailflow|Slutbruger startet fra en Outlook eller Outlook på internettet eller via Exchange regler for mailflow|Slutbruger startet fra Outlook desktop, Outlook til Mac eller Outlook på internettet; via Exchange regler for mailflow (også kaldet transportregler) og forebyggelse af datatab (DLP)|
|*Skabelon til rettighedsstyring*       |   I/T      |Indstillingen Videres videresende ikke og brugerdefinerede skabeloner|Indstillingen Videressendelse, indstillingen Kryptering kun og Brugerdefinerede skabeloner|
|*Modtagertype*                   |Interne og eksterne modtagere|Kun interne modtagere         |Interne og eksterne modtagere|
|*Oplevelse for intern modtager*|Modtagerne modtager en HTML-meddelelse, som de downloader og åbner i en webbrowser eller en mobilapp|Indbygget oplevelse i Outlook klienter|Indbygget oplevelse for modtagere i den samme organisation, der bruger Outlook klienter.  Modtagerne kan læse meddelelser fra OME-portalen ved hjælp af klienter, der ikke Outlook (ingen download eller app påkrævet).|
|*Oplevelse for ekstern modtager*|Modtagerne modtager en HTML-meddelelse, som de downloader og åbner i en webbrowser eller en mobilapp|I/T|Indbygget oplevelse for Microsoft 365 modtagere. Alle andre modtagere kan læse meddelelse fra OME-portalen (ingen download eller app påkrævet).|
|*Tilladelser for vedhæftede filer*           |Ingen begrænsninger for vedhæftede filer|Vedhæftede filer er beskyttet|Vedhæftede filer er beskyttet med indstillingen Videressendelse ikke og brugerdefinerede skabeloner. Administratorer kan vælge, om vedhæftede filer til indstillingen kun at kryptere er beskyttede eller ej.|
|*Medbring din egen understøttelse af nøgler (BYOK)*|Ingen                |Ingen               |BYOK understøttes          |
||

## <a name="advantages-of-the-new-ome-capabilities-over-legacy-ome"></a>Fordele ved de nye OME-funktioner i forhold til den ældre OME

De nye funktioner har følgende fordele:

- Mulighed for at bruge indstillingen kun krypteret (som aktiverer sikkert samarbejde), indstillingen Videresende ikke og brugerdefinerede begrænsninger.
- Afsendere kan sende mails krypteret med de nye funktioner manuelt fra Outlook Desktop, Outlook til Mac og Outlook på internettet klienter.
- Microsoft 365 modtagere får mulighed for at bruge en indbygget oplevelse i understøttede Outlook klienter. Administratorer kan også vælge at vise alle Microsoft 365 en brandet oplevelse.
- Konti uden for Microsoft 365, f.eks. Gmail-, Yahoo- og Microsoft-konti, er sammenkædet med OME-portalen, hvilket giver en bedre brugeroplevelse for disse modtagere. Alle andre identiteter bruger en engangsadgangskode til at få adgang til krypterede meddelelser.
- Administratorer kan tilpasse branding og oprette flere brandingskabeloner.
- Administratorer kan tilbagekalde mails, der er krypteret med de nye funktioner.
- De nye funktioner leverer detaljerede brugsrapporter via Security &amp; Compliance Center.

## <a name="office-365-advanced-message-encryption-capabilities"></a>Avanceret kryptering af meddelelser i Office 365 funktioner

Avanceret kryptering af meddelelser i Office 365 tilbyder yderligere funktioner oven i de nye OME-funktioner. Du skal have de Office 365-meddelelseskryptering funktioner konfigureret i organisationen for at kunne bruge funktionerne avanceret meddelelseskryptering. Hvis du vil bruge disse funktioner, skal modtagerne også se og svare på sikker mail via OME-portalen. De avancerede funktioner omfatter:

- Tilbagekaldelse af meddelelse

- Meddelelses udløb

- Flere brandingskabeloner

Avanceret kryptering af meddelelser i Office 365 understøttes ikke i GCC Høj.

Du kan finde oplysninger om brug af avanceret [meddelelseskryptering under Avanceret kryptering af meddelelser i Office 365](ome-advanced-message-encryption.md).

## <a name="unique-characteristics-of-office-365-message-encryption-in-a-gcc-high-deployment"></a>Unikke karakteristika ved Office 365-meddelelseskryptering i en GCC High-installation

Hvis du planlægger at bruge Office 365-meddelelseskryptering i et GCC High-miljø, er der nogle unikke karakteristika vedrørende modtageroplevelsen.

### <a name="encrypted-email-between-gcc-high-and-gcc-high-recipients"></a>Krypterede mails mellem GCC Høj GCC Modtagere høj

Afsendere kan kryptere mails manuelt i Outlook til pc og Mac og Outlook på internettet, eller organisationer kan konfigurere en politik for at kryptere mails ved hjælp Exchange regler for mailflow.

Modtagere i GCC High får den samme indbyggede læseoplevelse i Outlook til pc og Mac og Outlook på internettet som alle andre brugere.

### <a name="encrypted-email-between-gcc-high-and-non-gcc-high-recipients"></a>Krypterede mails mellem GCC modtagere med høj og GCC høj

Afsendere inden GCC High kan sende krypterede mails uden for GCC Høj grænse og omvendt.

Alle modtagere uden for GCC High, herunder kommercielle Microsoft 365-brugere, Outlook.com-brugere og andre brugere af andre mailudbydere, f.eks. Gmail og Yahoo, modtager en wrappermail. Denne ombrydningsmail omdirigerer modtageren til OME-portalen, hvor modtageren kan læse og svare på meddelelsen. Dette gælder også for afsendere uden for GCC High sender OME-krypteret mail til GCC Høj.

## <a name="coexistence-of-legacy-ome-and-the-new-capabilities-in-the-same-tenant"></a>Sameksistering af den ældre OME og de nye funktioner i samme lejer

Du kan bruge både den ældre OME og de nye funktioner i samme lejer. Som administrator kan du gøre dette ved at vælge, hvilken version af OME du vil bruge, når du opretter dine regler for mailflow.

- Hvis du vil angive den ældre version af OME, skal Exchange for **mailflowregelhandlingen Anvend den tidligere version af OME**.

- For at angive de nye funktioner skal du bruge Exchange for mailflowregel **anvend Office 365-meddelelseskryptering og rettighedsbeskyttelse**.

Brugerne kan manuelt sende mails, der er krypteret med de nye funktioner fra Outlook Desktop, Outlook til Mac og Outlook på internettet.

## <a name="migrate-from-legacy-ome-to-the-new-capabilities"></a>Overfør fra den ældre OME til de nye funktioner

Selvom begge versioner af OME kan bruges samtidig, anbefaler vi, at du redigerer dine gamle regler for mailflow, der bruger regelhandlingen Anvend den tidligere **version af OME** for at bruge de nye funktioner. Opdater disse regler for at bruge handlingen regel for **mailflow Anvend Office 365-meddelelseskryptering og rettighedsbeskyttelse**. Du kan finde en vejledning [i Definere regler for mailflow for at kryptere mails Office 365](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-ome"></a>Introduktion til OME

De nye OME-funktioner aktiveres typisk automatisk for din organisation. Du kan finde flere oplysninger om de nye OME-funktioner i din organisation under [Konfigurer Office 365-meddelelseskryptering funktioner](set-up-new-message-encryption-capabilities.md).

Den ældre version af OME aktiveres automatisk for din organisation, hvis du har aktiveret Azure Information Protection. Tidligere fungerede ældre OME, selvom Azure Information Protection ikke var aktiveret. Dette er ikke længere tilfældet.

Hvis du har aktiveret Azure Information Protection, skal du konfigurere regler for mailflow, der bruger regelhandlingen Anvend den tidligere **version af OME** for at begynde at bruge den tidligere OME. Du kan finde en vejledning i [Definere regler for mailflow for at kryptere mails](define-mail-flow-rules-to-encrypt-email.md).
