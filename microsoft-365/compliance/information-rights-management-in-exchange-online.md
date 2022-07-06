---
title: Exchange Online-mailkryptering med AD RMS
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/13/2017
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 2c956776-0016-4be6-b4cd-133a237f4a9e
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du konfigurerer Exchange Online IRM til at bruge AD RMS (Active Directory i det lokale miljø Rights Management Service) for at opfylde organisationens krav.
ms.openlocfilehash: 926bea0b1f9379d2eaad2bc7c5bd672f98329b8a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628787"
---
# <a name="exchange-online-mail-encryption-with-ad-rms"></a>Exchange Online-mailkryptering med AD RMS

For at forhindre lækage af oplysninger indeholder Exchange Online IRM-funktionalitet (Information Rights Management), der giver online- og offlinebeskyttelse af mails og vedhæftede filer. Du kan konfigurere Exchange Online IRM til at bruge AD RMS (Active Directory i det lokale miljø Rights Management Service), hvis det er nødvendigt, for at opfylde organisationens krav. Dette er ikke almindeligt. Hvis du ikke har et krav om at bruge AD RMS, skal du bruge [Microsoft Purview-meddelelseskryptering](ome.md) i stedet.

IRM-beskyttelse kan anvendes af brugere i Microsoft Outlook eller Outlook på internettet, og den kan anvendes af administratorer, der bruger regler for transportbeskyttelse eller Outlook-beskyttelsesregler. IRM hjælper dig og dine brugere med at styre, hvem der kan få adgang til, videresende, udskrive eller kopiere følsomme data i en mail.
  
## <a name="changes-to-how-irm-works-with-message-encryption-and-azure-active-directory"></a>Ændringer af, hvordan IRM fungerer med meddelelseskryptering og Azure Active Directory

Fra og med september 2017, når du konfigurerer Microsoft Purview-meddelelseskryptering for din organisation, konfigurerer du også IRM til brug med Azure Rights Management (Azure RMS). Du konfigurerer ikke længere IRM med Azure RMS separat. I stedet fungerer kryptering af meddelelser og administration af rettigheder problemfrit sammen. Du kan finde flere oplysninger om Microsoft Purview-meddelelseskryptering under [Ofte stillede spørgsmål om meddelelseskryptering](./ome-faq.yml). Hvis du er klar til at komme i gang med at bruge Microsoft Purview-meddelelseskryptering i din organisation, skal du se [Konfigurer Microsoft Purview-meddelelseskryptering](./set-up-new-message-encryption-capabilities.md).
  
## <a name="how-irm-works-with-exchange-online-and-active-directory-rights-management-services"></a>Sådan fungerer IRM sammen med Exchange Online og Active Directory Rights Management Services

Exchange Online IRM bruger AD RMS (Active Directory i det lokale miljø Rights Management Services), som er en teknologi til beskyttelse af oplysninger i Windows Server 2008 og nyere. IRM-beskyttelse anvendes på mail ved at anvende en SKABELON for AD RMS-rettigheder på en mail. Rettigheder vedhæftes selve meddelelsen, så beskyttelsen sker online og offline og i og uden for organisationens firewall.
  
Brugerne kan anvende en skabelon på en mail for at styre de tilladelser, som modtagerne har til en meddelelse. Handlinger, f.eks. videresendelse, udtrækning af oplysninger fra en meddelelse, lagring af en meddelelse eller udskrivning af en meddelelse, kan styres ved at anvende en AD RMS-rettighedspolitik på meddelelsen.
  
Du kan konfigurere IRM til at bruge en AD RMS-server, der kører Windows Server 2008 eller nyere. Du kan bruge denne AD RMS-server til at administrere AD RMS-rettighedspolitikskabeloner for din cloudbaserede organisation. Outlook er også afhængig af AD RMS-serveren for at give brugerne mulighed for at anvende IRM-beskyttelse på meddelelser, de sender. Du kan finde flere oplysninger under [Konfigurer IRM til at bruge en AD RMS-server i det lokale miljø](configure-irm-to-use-an-on-premises-ad-rms-server.md).
  
Når den er aktiveret, kan IRM-beskyttelse anvendes på meddelelser på følgende måde:
  
- **Brugerne kan anvende en skabelon manuelt ved hjælp af Outlook og Outlook på internettet.** Brugerne kan anvende en skabelon for AD RMS-rettighedspolitik på en mail ved at vælge skabelonen på listen **Angiv tilladelser** . Når brugerne sender en IRM-beskyttet meddelelse, modtager vedhæftede filer, der bruger et understøttet format, også den samme IRM-beskyttelse som meddelelsen. IRM-beskyttelse anvendes på filer, der er knyttet til Word, Excel og PowerPoint, samt .xps-filer og vedhæftede mails.

- **Administratorer kan bruge regler for transportbeskyttelse til automatisk at anvende IRM-beskyttelse på både Outlook og Outlook på internettet.** Du kan oprette regler for transportbeskyttelse til IRM-beskyttende meddelelser. Konfigurer handlingen for transportbeskyttelsesreglen for at anvende en AD RMS-rettighedspolitikskabelon på meddelelser, der opfylder regelbetingelsen. Når du har aktiveret IRM, er organisationens AD RMS-rettighedspolitikskabeloner tilgængelige til brug sammen med handlingen med reglen om transportbeskyttelse, der kaldes **Anvend rettighedsbeskyttelse på meddelelsen med**.

- **Administratorer kan oprette outlook-beskyttelsesregler.** Outlook-beskyttelsesregler anvender automatisk IRM-beskyttelse på meddelelser i Outlook 2010 (ikke Outlook på internettet) baseret på meddelelsesbetingelser, der omfatter afsenderens afdeling, hvem meddelelsen sendes til, og om modtagerne er i eller uden for din organisation. Du kan finde flere oplysninger under [Opret en Outlook-beskyttelsesregel](/exchange/create-an-outlook-protection-rule-exchange-2013-help).
