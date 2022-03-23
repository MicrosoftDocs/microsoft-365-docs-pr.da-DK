---
title: Exchange Online mailkryptering med AD RMS
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
description: Få mere at vide om, hvordan du konfigurerer Exchange Online IRM til at bruge en lokal AD RMS (Active Directory Rights Management Service) for at opfylde organisationens krav.
ms.openlocfilehash: 867293d5afa29242409cc92702ff8b505ed21196
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588690"
---
# <a name="exchange-online-mail-encryption-with-ad-rms"></a>Exchange Online mailkryptering med AD RMS

For at forhindre lækage af oplysninger Exchange Online du inkludere IRM-funktionalitet (Information Rights Management), som giver online- og offlinebeskyttelse af mails og vedhæftede filer. Du kan konfigurere Exchange Online IRM til at bruge den lokale Active Directory Rights Management Service (AD RMS), hvis det er nødvendigt, for at opfylde organisationens krav. Dette er ikke almindeligt. Hvis du ikke har krav om at bruge AD RMS, skal du bruge [Office 365-meddelelseskryptering](ome.md) stedet. 

IRM-beskyttelse kan anvendes af brugere i Microsoft Outlook eller Outlook på internettet, og den kan anvendes af administratorer ved hjælp af transportbeskyttelsesregler eller Outlook-beskyttelsesregler. IRM hjælper dig og dine brugere med at styre, hvem der kan få adgang til, videresende, udskrive eller kopiere følsomme data i en mail.
  
## <a name="changes-to-how-irm-works-with-office-365-message-encryption-ome-and-azure-active-directory"></a>Ændringer i, hvordan IRM fungerer med Office 365-meddelelseskryptering (OME) og Azure Active Directory

Fra september 2017, da du konfigurerede de nye Office 365-meddelelseskryptering-funktioner for organisationen, konfigurerede du også IRM til brug med Azure Rights Management (Azure RMS). Du kan ikke længere konfigurere IRM med Azure RMS separat. I stedet arbejder OME og rettighedsstyring problemfrit sammen. Du kan finde flere oplysninger om de nye funktioner i ofte [Office 365-meddelelseskryptering ofte stillede spørgsmål](./ome-faq.yml). Hvis du er klar til at komme i gang med at bruge de nye OME-funktioner i din organisation, skal du se Konfigurer nye Office 365-meddelelseskryptering-funktioner, der er bygget oven på [Azure Information Protection](./set-up-new-message-encryption-capabilities.md).
  
## <a name="how-irm-works-with-exchange-online-and-active-directory-rights-management-services"></a>Sådan fungerer IRM med Exchange Online og Active Directory Rights Management-tjenester

Exchange Online IRM bruger lokale Active Directory Rights Management-tjenester (AD RMS), som er en teknologi til informationsbeskyttelse i Windows Server 2008 og nyere. IRM-beskyttelse anvendes på mail ved at anvende en AD RMS-rettighedspolitikskabelon på en mail. Rettigheder knyttes til selve meddelelsen, så beskyttelsen sker online og offline og inden for og uden for organisationens firewall.
  
Brugere kan anvende en skabelon på en mail for at styre de tilladelser, som modtagerne har på en meddelelse. Handlinger, som f.eks. videresendelse, udtræk oplysninger fra en meddelelse, lagring af en meddelelse eller udskrivning af en meddelelse, kan styres ved at anvende en AD RMS-rettighedspolitik for meddelelsen.
  
Du kan konfigurere IRM til at bruge en AD RMS-server, der Windows Server 2008 eller nyere. Du kan bruge denne AD RMS-server til at administrere AD RMS-rettighedspolitikskabeloner for din skybaserede organisation. Outlook er også afhængig af AD RMS-serveren for at give brugerne mulighed for at anvende IRM-beskyttelse på meddelelser, de sender. Du kan få mere at [vide under Konfigurer IRM til at bruge en lokal AD RMS-server](configure-irm-to-use-an-on-premises-ad-rms-server.md). 
  
Når funktionen er aktiveret, kan IRM-beskyttelse anvendes på meddelelser på følgende måde:
  
- **Brugerne kan manuelt anvende en skabelon ved hjælp Outlook og Outlook på internettet.** Brugere kan anvende en skabelon til AD RMS-rettigheder på en mail ved at vælge skabelonen **på listen Angiv** tilladelser. Når brugerne sender en IRM-beskyttet meddelelse, får alle vedhæftede filer, der bruger et understøttet format, også samme IRM-beskyttelse som meddelelsen. IRM-beskyttelse anvendes på filer, der er knyttet til Word Excel og PowerPoint samt .xps-filer og vedhæftede mails. 
    
- **Administratorer kan bruge transportbeskyttelsesregler til automatisk at anvende IRM-beskyttelse på både Outlook og Outlook på internettet.** Du kan oprette transportbeskyttelsesregler for IRM-beskytte meddelelser. Konfigurer handlingen for transportbeskyttelsesreglen for at anvende en AD RMS-rettighedspolitikskabelon på meddelelser, der opfylder regelbetingelsesindstillingen. Når du har aktiveret IRM, er organisationens AD RMS-rettighedspolitikskabeloner tilgængelige for brug sammen med handlingen for transportbeskyttelsesreglen kaldet Anvend rettighedsbeskyttelse på **meddelelsen med**.
    
- **Administratorer kan oprette Outlook regler for beskyttelse.** Outlook-beskyttelsesregler anvender automatisk IRM-beskyttelse på meddelelser i Outlook 2010 (ikke Outlook på internettet) baseret på meddelelsesbetingelser, der omfatter afsenderens afdeling, hvem meddelelsen sendes til, og om modtagerne er inden for eller uden for organisationen. Du kan få mere [at vide under oprette Outlook regel for beskyttelse](/exchange/create-an-outlook-protection-rule-exchange-2013-help).
