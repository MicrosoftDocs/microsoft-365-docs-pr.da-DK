---
title: Avanceret meddelelseskryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 04/01/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Avanceret meddelelseskryptering hjælper organisationer med at opfylde deres overholdelsesforpligtelser ved at give administratorerne mulighed for at gøre endnu mere med beskyttede meddelelser.
ms.openlocfilehash: 74d94bdb837531fdbbb819c86f9dbb7dd80272e8
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634333"
---
# <a name="advanced-message-encryption"></a>Avanceret meddelelseskryptering

Avanceret kryptering af meddelelser i Office 365 er inkluderet i [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (nonprofitmedarbejderpriser) Office 365 Enterprise E5 (nonprofitorganisationers priser for personale) og Office 365 Education A5. Hvis du vil bruge funktionerne avanceret tilbagekaldelse af meddelelseskryptering og udløb, **skal du Premium indstillingen kryptering Office 365** i din E5-licens.

Hvis din organisation har et abonnement, der ikke Avanceret kryptering af meddelelser i Office 365, kan du købe det med Microsoft 365 E5 Overholdelse SKU-tilføjelsesprogrammet til Microsoft 365 E3, Microsoft 365 E3  (Nonprofit Staff Pricing) eller Avanceret overholdelse i Office 365-tilføjelsesprogrammet Microsoft 365 E3, Microsoft 365 E3 (nonprofitorganisationers personalepriser), Office 365 SKU'er eller Microsoft 365 E5/A5 Information Protection og tilføjelsesprogrammet Styrings-SKU til Microsoft 365 A3/E3.

Avanceret meddelelseskryptering hjælper kunder med at opfylde overholdelsesforpligtelser, der kræver mere fleksible kontroller over eksterne modtagere og deres adgang til krypterede mails. Med avanceret meddelelseskryptering Office 365 du styre følsomme mails, der deles uden for organisationen, ved hjælp af automatiske politikker. Du kan konfigurere disse politikker for at identificere følsomme oplysningstyper, f.eks. PII-, finansielle eller tilstands-id'er, eller du kan bruge nøgleord til at forbedre beskyttelsen. Når du har konfigureret politikkerne, kan du parre politikker med brugerdefinerede brandede mailskabeloner og derefter tilføje en udløbsdato for at få ekstra kontrol over mails, der passer til politikken. Administratorer kan desuden når som helst kontrollere krypterede mails, der er åbnet eksternt, ved at tilbagekalde adgangen til mailen.

Du kan kun tilbagekalde og angive en udløbsdato for mails, der sendes til eksterne modtagere.

## <a name="get-started-with-office-365-advanced-message-encryption"></a>Introduktion til Avanceret kryptering af meddelelser i Office 365

I følgende artikler beskrives det, hvordan du konfigurerer og bruger avanceret meddelelseskryptering.

Din organisation skal have et abonnement, der omfatter Avanceret kryptering af meddelelser i Office 365. Du kan finde detaljerede oplysninger om understøttede abonnementer i Beskrivelse af [meddelelsespolitik og overholdelsestjeneste](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

Hvis du ikke har konfigureret Office 365 af meddelelseskryptering, skal du se Konfigurer [Office 365 egenskaber for meddelelseskryptering](set-up-new-message-encryption-capabilities.md).

Med avanceret meddelelseskryptering er du ikke begrænset til en enkelt brandingskabelon. I stedet kan du oprette og bruge flere brandingskabeloner. Ved at tilføje brugerdefineret branding kan du også aktivere sporing af en tilbagekaldelse af krypterede meddelelser. Du kan finde flere [oplysninger i Føje organisationens brand til dine krypterede meddelelser](add-your-organization-brand-to-encrypted-messages.md). Når du bruger brugerdefineret branding, modtager eksterne modtagere en mail, der indeholder et link til OME-portalen. Reglen for mailflow bestemmer, hvilken brandingskabelon mailen og OME Portal bruger. På denne måde sendes dit sikre indhold ikke uden for organisationen.

Du kan kun tilbagekalde meddelelser og anvende udløbsdatoer på meddelelser, som brugerne modtager via portalen. Med andre ord mails, hvor der er anvendt en brugerdefineret brandingskabelon. Du kan finde flere oplysninger og et eksempel i vejledningen i Sikre, at alle eksterne modtagere bruger [OME-portalen til at læse krypteret mail](manage-office-365-message-encryption.md#ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail).

[Angiv en udløbsdato for mails, der er krypteret med Avanceret kryptering af meddelelser i Office 365](ome-advanced-expiration.md). Styr følsomme mails, der deles uden for organisationen, med automatiske politikker, der forbedrer beskyttelsen ved at udløbe adgang via en sikker webportal til krypterede mails.

[Tilbagekald mails, der er krypteret Avanceret kryptering af meddelelser i Office 365](revoke-ome-encrypted-mail.md). Styr følsomme mails, der deles uden for organisationen, og forbedr beskyttelsen ved at tilbagekalde adgangen via en sikker webportal til krypterede mails.  
