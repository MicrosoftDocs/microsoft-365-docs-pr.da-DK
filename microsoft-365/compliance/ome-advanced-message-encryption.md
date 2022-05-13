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
ms.date: 05/12/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Avanceret meddelelseskryptering hjælper organisationer med at opfylde deres overholdelsesforpligtelser ved at gøre det muligt for administratorer at gøre endnu mere med beskyttede meddelelser.
ms.openlocfilehash: 077a17921c456ddff30e7490611dd4e78aaa5232
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393280"
---
# <a name="advanced-message-encryption"></a>Avanceret meddelelseskryptering

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview avanceret meddelelseskryptering er inkluderet i [Microsoft 365 Enterprise E5](https://www.microsoft.com/microsoft-365/enterprise/home), Office 365 E5, Microsoft 365 E5 (prisfastsættelse for personale til nonprofitorganisationer), Office 365 Enterprise E5 (personale til nonprofitorganisationer og Office 365 Education A5. Hvis din organisation har et abonnement, der ikke indeholder Microsoft Purview avanceret meddelelseskryptering, kan du købe det med tilføjelsesprogrammet Microsoft 365 E5 Overholdelse SKU til Microsoft 365 E3, Microsoft 365 E3 (prisfastsættelse for medarbejdere til nonprofitorganisationer), eller Avanceret overholdelse i Office 365 SKU-tilføjelsesprogram til Microsoft 365 E3, Microsoft 365 E3 (pris på nonprofitpersonale), Office 365 SKU'er eller Microsoft 365 E5/A5 sku-tilføjelsesprogrammet Information Protection og styring for Microsoft 365 A3/E3.

Avanceret meddelelseskryptering hjælper kunder med at opfylde overholdelsesforpligtelser, der kræver mere fleksible kontroller over eksterne modtagere og deres adgang til krypterede mails. Med Avanceret meddelelseskryptering i Office 365 kan du styre følsomme mails, der deles uden for organisationen, med automatiske politikker og spore disse aktiviteter via de krypterede adgangslogge for meddelelsesportalen. Du kan konfigurere disse politikker til at identificere følsomme oplysningstyper, f.eks. pii-, økonomi- eller sundheds-id'er, eller du kan bruge nøgleord til at forbedre beskyttelsen. Når du har konfigureret politikkerne, parres politikker med brugerdefinerede mailskabeloner med mærkevarer, og du tilføjer derefter en udløbsdato for at få ekstra kontrol over mails, der passer til politikken. Administratorer kan også yderligere kontrollere krypterede mails, der tilgås eksternt via en sikker webportal, ved at tilbagekalde adgangen til mailen når som helst.

Du kan kun tilbagekalde og angive en udløbsdato for mails, der sendes til eksterne modtagere.

## <a name="get-started-with-microsoft-purview-advanced-message-encryption"></a>Kom i gang med Microsoft Purview avanceret meddelelseskryptering

I følgende artikler beskrives det, hvordan du konfigurerer og bruger avanceret meddelelseskryptering.

Organisationen skal have et abonnement, der indeholder Microsoft Purview avanceret meddelelseskryptering. Du kan finde detaljerede oplysninger om understøttede abonnementer i [beskrivelsen af meddelelsespolitik og overholdelse af angivne standarder](/office365/servicedescriptions/exchange-online-service-description/message-policy-and-compliance).

Hvis du ikke allerede har Office 365 meddelelseskryptering, skal du se [Konfigurer nye funktioner til Office 365 Meddelelsekryptering](set-up-new-message-encryption-capabilities.md).

Med Avanceret meddelelseskryptering er du ikke begrænset til en enkelt brandingskabelon. Du kan i stedet oprette og bruge flere brandingskabeloner. Hvis du tilføjer brugerdefineret branding, kan du også aktivere sporing af en tilbagekaldelse af krypterede meddelelser. Du kan få flere oplysninger under [Føj organisationens brand til dine krypterede meddelelser](add-your-organization-brand-to-encrypted-messages.md). Når du bruger brugerdefineret branding, modtager eksterne modtagere en meddelelsesmail, der indeholder et link til OME-portalen. Reglen for mailflow bestemmer, hvilken brandingskabelon meddelelsesmailen og OME-portalen bruger. På denne måde sendes dit sikre indhold ikke uden for din organisation.

Du kan kun tilbagekalde meddelelser og anvende udløbsdatoer på meddelelser, som brugerne modtager via portalen. Med andre ord, mail, hvor der er anvendt en brugerdefineret brandingskabelon. Du kan finde flere oplysninger og et eksempel i vejledningen under [Sørg for, at alle eksterne modtagere bruger OME-portalen til at læse krypterede mails](manage-office-365-message-encryption.md#ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail).

[Angiv en udløbsdato for mail, der er krypteret af Microsoft Purview avanceret meddelelseskryptering](ome-advanced-expiration.md). Styr følsomme mails, der deles uden for organisationen, med automatiske politikker, der forbedrer beskyttelsen ved at udløbe adgangen via en sikker webportal til krypterede mails.

[Tilbagekald mail, der er krypteret af Microsoft Purview avanceret meddelelseskryptering](revoke-ome-encrypted-mail.md). Styr følsomme mails, der deles uden for organisationen, og gør beskyttelsen bedre ved at tilbagekalde adgangen via en sikker webportal til krypterede mails.

[Aktivitetslog for krypteret meddelelsesportal af Microsoft Purview avanceret meddelelseskryptering](ome-message-access-logs.md). Overvåg følsomme mails, der deles uden for organisationen i den krypterede meddelelsesportal.
