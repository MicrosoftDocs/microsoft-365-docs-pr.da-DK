---
title: Administrer Microsoft-feedback for din organisation
f1.keywords:
- NOCSH
ms.author: Kwekua
author: Kwekua
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
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
description: Administrer feedback, som dine brugere kan sende til Microsoft om Microsoft-produkter.
ms.openlocfilehash: 8cd20b1a6138f389ba996bdaee8cae8ae24d2974
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403561"
---
# <a name="manage-microsoft-feedback-for-your-organization"></a>Administrer Microsoft-feedback for din organisation

Som administrator for en Microsoft 365-organisation er der nu flere politikker, der kan hjælpe dig med at administrere samlingen af feedback og dine brugeres oplevelse af kundeengagement, når du bruger Microsoft 365-programmer. Du kan oprette og bruge eksisterende Azure Active Directory-grupper i organisationen til hver af disse politikker. Med disse politikforanstaltninger kan du styre, hvordan forskellige afdelinger i din organisation kan sende feedback til Microsoft. Microsoft gennemser al feedback, der sendes af kunder, og bruger denne feedback til at forbedre produktet. Når feedback-oplevelserne **er slået Til** , kan du se, hvad dine brugere siger om de Microsoft-produkter, de bruger. Den feedback, vi indsamler fra dine brugere, vil snart være tilgængelig <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">i Microsoft 365 Administration</a>.

Du kan få mere at vide om typer af feedback, og hvordan Microsoft bruger brugerfeedback, under [Få mere at vide om Microsoft-feedback til din organisation](../misc/feedback-user-control.md).

Tabellen nedenfor viser, hvilke apps og tjenester der aktuelt er knyttet til de feedbackpolitikker, der er vist i tabellen med feedbackpolitikker nedenfor. Se eksempler på skærmbilleder nedenfor tabellen.

|**Apps & tjenester**|**Feedback i produktet** <br> |**Produktundersøgelse** <br> |**Samling af metadata** <br> |**Kundeengagement** <br> |
|:-----|:-----|:-----|:-----|:-----|
|**Access**|Ja|Ja|Ja|Ja|
|**Excel**|Ja|Ja|Ja|Ja|
|**Office.com**|Kommer snart|Kommer snart|Kommer snart|Kommer snart|
|**OneNote**|Ja|Ja|Ja|Ja|
|**OneDrive**|[Nogle indstillinger administreres i øjeblikket af andre kontrolelementer.](/onedrive/disable-contact-support-send-feedback)||||
|**Outlook**|Kommer snart|Kommer snart|Kommer snart|Kommer snart|
|**PowerPoint**|Ja|Ja|Ja|Ja|
|**Project**|Kommer snart|Kommer snart|Kommer snart|Kommer snart|
|**Publisher**|Ja|Ja|Ja|Ja|
|**SharePoint**|[Nogle indstillinger administreres i øjeblikket af andre kontrolelementer.](/powershell/module/sharepoint-online/set-spotenant)||||
|**Teams**|[Nogle indstillinger administreres i øjeblikket af andre kontrolelementer.](/microsoftteams/manage-feedback-policies-in-teams)||||
|**Word**|Ja|Ja|Ja|Ja|
|**Visio**|Ja|Ja|Ja|Ja|
|**Yammer**|Ja|Ja|Ja|Ja|

[Se her for at få nogle eksempler på produktundersøgelse og feedback.](/microsoft-365/admin/misc/feedback-user-control#in-product-surveys)

**Samling af metadata**

:::image type="content" source="../../media/feedback-metadata2.png" alt-text="Skærmbillede: Feedbackside med eksempel på metadata":::

**Kundeengagement**

:::image type="content" source="../../media/feedback-in-product-customer-engagement.png" alt-text="Skærmbillede: Eksempel på spørgsmål om kundeundersøgelse i produkt":::

## <a name="before-you-begin"></a>Før du begynder

Dine enheder skal have et buildnummer som minimum for at kunne bruge disse politikker. Se tabellen nedenfor for at få flere oplysninger.

|**Build #**|**Win32**|**iOS**|**Android**|**Mac**|**Web**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|Feedback i produktet|Mindst Version 2010|Mindst 2,42|Mindst 16.0.13328|Mindst 16,42|Offentligt tilgængelig|
|Produktundersøgelse|Mindst Version 2010|Mindst 2,42|Mindst 16.0.13426|Mindst 16,42|Ventende udrulning|
|Samling af metadata|Mindst Version 2010|Mindst 2,42|Mindst 16.0.13328|Mindst 16,42|Offentligt tilgængelig|
|Kundeengagement|Mindst Version 2010|Mindst 2,42|Mindst 16.0.13426|Mindst 16,42|Ventende udrulning|

## <a name="specific-policies-you-can-configure"></a>Specifikke politikker, du kan konfigurere

### <a name="feedback-policies"></a>Feedbackpolitikker

|**Politiknavn**|**Standardtilstand**|**Kontrolelementoversigt**|
|:-----|:-----|:-----|
|Tillad brugere at sende feedback til Microsoft|Til|Styrer feedbackindtastningspunkter på tværs af programmer|
|Tillad brugere at modtage og besvare produktundersøgelse fra Microsoft|Til|Kontrolelementer undersøgelsesprompter i produkt|
|Tillad brugere at medtage skærmbilleder og vedhæftede filer, når de sender feedback til Microsoft|Fra|Bestemmer, hvilke metadata brugeren kan beslutte at indsende med feedback/undersøgelse|
|Tillad Microsoft at følge op på feedback, der sendes af brugere|Fra|Bestemmer, om brugeren kan dele kontaktoplysninger med feedback/undersøgelse|
|Tillad brugere at medtage logfiler og indholdseksempler, når der sendes feedback til Microsoft|Fra|Bestemmer metadata, som brugeren kan beslutte at sende med feedback/undersøgelse|

## <a name="configure-policies"></a>Konfigurere politikker

Hvis du vil konfigurere disse politikindstillinger, kan du bruge Office skypolitiktjeneste. Få mere at vide under [Oversigt over Office skypolitiktjeneste](/deployoffice/overview-office-cloud-policy-service). Du kan søge efter "feedback" eller "undersøgelse" i Office brugergrænsefladen for skypolitik for at finde politikindstillingerne til at konfigurere dem. 

Disse politikindstillinger er også tilgængelige, hvis du bruger Gruppepolitik. For at bruge disse politikindstillinger skal du downloade mindst version 5146.1000 af de administrative skabelonfiler [(ADMX/ADML)](https://www.microsoft.com/download/details.aspx?id=49030), udgivet d. 22. marts 2021.

Du kan finde disse politikindstillinger under Brugerkonfiguration\Politikker\Administrative skabeloner\Microsoft Office 2016\Privacy\Trust Center.

> [!NOTE]
> Det tager et par timer, før klientprogrammer er opdateret.
