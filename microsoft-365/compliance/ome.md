---
title: Meddelelseskryptering
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 02/07/2020
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.assetid: f87cb016-7876-4317-ae3c-9169b311ff8a
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du sender og modtager krypterede mails mellem personer i og uden for organisationen.
ms.openlocfilehash: 04c2ddd3bfb77199f924a10e29f23dc3d27cc38b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588740"
---
# <a name="message-encryption"></a>Meddelelseskryptering

Folk bruger ofte mail til at udveksle følsomme oplysninger, f.eks. finansielle data, juridiske kontrakter, fortrolige produktoplysninger, salgsrapporter og prognoser, patient sundhedsoplysninger eller kunde- og medarbejderoplysninger. Derfor kan postkasser blive lager til store mængder potentielt følsomme oplysninger, og lækage af oplysninger kan blive en alvorlig trussel mod din organisation.

Med Office 365-meddelelseskryptering kan din organisation sende og modtage krypterede mails mellem personer i og uden for organisationen. Office 365-meddelelseskryptering fungerer sammen med Outlook.com, Yahoo!, Gmail og andre mailtjenester. Kryptering af mail er med til at sikre, at det kun er de tilsigtede modtagere, der kan se meddelelsens indhold.

## <a name="how-office-365-message-encryption-works"></a>Sådan Office 365-meddelelseskryptering fungerer

Resten af denne artikel gælder for de nye OME-funktioner.

Office 365-meddelelseskryptering er en onlinetjeneste, der er bygget på Microsoft Azure Rights Management (Azure RMS), som er en del af Azure Information Protection. Denne tjeneste indeholder krypterings-, identitets- og godkendelsespolitikker, som hjælper med at sikre dine mails. Du kan kryptere meddelelser ved hjælp af rettighedsstyringsskabeloner, indstillingen [Videresende](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails) ikke og [indstillingen kun krypteret](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

Brugerne kan derefter kryptere mails og forskellige vedhæftede filer ved hjælp af disse indstillinger. Du kan se en komplet liste over understøttede vedhæftede filer under "Filtyper, der er dækket af IRM-politikker, når de vedhæftes meddelelser" i Introduktion til [IRM til mails](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM).

Som administrator kan du også definere regler for mailflow for at anvende denne beskyttelse. Du kan f.eks. oprette en regel, der kræver kryptering af alle meddelelser, der er adresseret til en bestemt modtager, eller som indeholder bestemte ord i emnelinjen, og du kan også angive, at modtagerne ikke kan kopiere eller udskrive indholdet af meddelelsen.

I modsætning til den tidligere version af OME giver de nye funktioner en samlet afsenderoplevelse, uanset om du sender mails inden for organisationen eller til modtagere uden for Microsoft 365. Desuden behøver modtagere, der modtager en beskyttet mail, der er sendt til en Microsoft 365-konto i Outlook 2016 eller Outlook på internettet, ikke at gøre noget andet for at få vist meddelelsen. Det fungerer problemfrit. Modtagere, der bruger andre mailklienter og mailtjenesteudbydere, har også en bedre oplevelse. Du kan finde flere [oplysninger i Få mere at vide om beskyttede Office 365](https://support.office.com/article/Learn-about-protected-messages-in-Office-365-2baf3ac7-12db-40a4-8af7-1852204b4b67) [og Hvordan åbner jeg en beskyttet meddelelse](https://support.office.com/article/How-do-I-open-a-protected-message-1157a286-8ecc-4b1e-ac43-2a608fbf3098).

Hvis du vil have en detaljeret liste over forskellene mellem den tidligere version af OME og de nye OME-funktioner, skal du [se Sammenlign versioner af OME](ome-version-comparison.md).

Når nogen sender en mail, der svarer til en krypteringsregel for mailflow, krypteres meddelelsen, før den sendes. Alle Microsoft 365-slutbrugere, der bruger Outlook-klienter til at læse mail, modtager oprindelige, førsteklasses læseoplevelser til krypterede og rettighedsbeskyttede mails, selvom de ikke er i samme organisation som afsenderen. Understøttede Outlook-klienter inkluderer Outlook desktop, Outlook Mac, Outlook Mobile på iOS og Android og Outlook på internettet (tidligere kaldet Outlook Web App).

Modtagere af krypterede meddelelser, som modtager krypterede eller rettighedsbeskyttede mails, der sendes til deres Outlook.com-, Gmail- og Yahoo-konti, modtager en wrappermail, der dirigerer dem til OME-portalen, hvor de nemt kan godkende ved hjælp af legitimationsoplysninger for en Microsoft-konto, Gmail eller Yahoo.

Slutbrugere, der læser krypteret eller rettighedsbeskyttet mail på andre klienter end Outlook, bruger også OME-portalen til at få vist krypterede og rettighedsbeskyttede meddelelser, de modtager.

Hvis afsenderen af den beskyttede mail er i GCC High, og modtageren er uden for GCC High, herunder kommercielle brugere, Outlook.com-brugere og brugere af andre mailudbydere som f.eks Gmail, modtager modtageren en ombrydningsmail. Wrapper-mailen dirigerer modtageren til OME-portalen, hvor modtageren kan læse og svare på meddelelsen. Ellers, hvis afsenderen og modtageren begge er i GCC High-miljøet, også selvom de ikke er i den samme organisation, modtager modtagere, der bruger Outlook-klienter til at læse mail, oprindelige læseoplevelser i første klasse til krypterede og rettighedsbeskyttede mails. Du kan finde flere oplysninger om de forskellige GCC High i [Sammenlign versioner af OME](ome-version-comparison.md).

Du kan finde flere oplysninger om størrelsesbegrænsninger for meddelelser og vedhæftede filer, som du kan kryptere ved hjælp af OME, [Exchange Online Begrænsninger](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).

## <a name="how-office-365-advanced-message-encryption-works-on-top-of-ome"></a>Sådan Avanceret kryptering af meddelelser i Office 365 fungerer oven på OME

Avanceret kryptering af meddelelser i Office 365 kan du oprette flere brandingskabeloner, så du kan finjustere kontrollen over modtagermail og oprette brugerdefinerede brandingoplevelser for at understøtte en forskellig organisationsstruktur.

Avanceret meddelelseskryptering i Microsoft 365 til at overholde overholdelsesforpligtelser, som kræver mere fleksibel kontrol over eksterne modtageres adgang til krypterede mails. Med avanceret meddelelseskryptering i Office 365 kan du som administrator styre følsomme mails, der deles uden for organisationen, med automatiske politikker, der registrerer følsomme oplysningstyper (f.eks. PII-, finansielle eller sundheds-id'er) eller nøgleord for at forbedre beskyttelsen ved at udløbe adgang via en sikker webportal til krypterede mails. Som administrator kan du yderligere kontrollere krypterede mails, der åbnes via en Microsoft 365-webportal, ved at tilbagekalde adgangen til en mail når som helst.

Tilbagekaldelse af meddelelser og udløb fungerer kun for mails, som dine brugere sender til modtagere uden for organisationen. Desuden skal modtagerne få adgang til mailen via webportalen. For at sikre at modtageren bruger portalen til at modtage mails, skal du konfigurere en brugerdefineret brandingskabelon, der anvender wrapperen. Derefter skal du anvende skabelonen til branding i en regel for mailflow. Du kan finde flere oplysninger om avanceret meddelelseskryptering [under Avanceret kryptering af meddelelser i Office 365](ome-advanced-message-encryption.md).

## <a name="defining-rules-for-office-365-message-encryption"></a>Definere regler for Office 365-meddelelseskryptering

En måde at aktivere de nye funktioner for Office 365-meddelelseskryptering er for Exchange Online og Exchange Online Protection at definere regler for mailflow. Disse regler bestemmer, under hvilke betingelser mails skal krypteres. Når der er angivet en krypteringshandling for en regel, krypteres meddelelser, der opfylder regelbetingelserne, før de sendes.

Regler for mailflow er fleksible, så du kan kombinere betingelser, så du kan opfylde specifikke sikkerhedskrav i en enkelt regel. Du kan f.eks. oprette en regel for at kryptere alle meddelelser, der indeholder angivne nøgleord, og som er adresseret til eksterne modtagere. De nye funktioner til disse Office 365-meddelelseskryptering også kryptere svar fra modtagere af krypteret mail.

Du kan finde flere oplysninger om, hvordan du opretter regler for mailflow for at drage fordel af de nye OME-funktioner, under [Definer regler for Office 365-meddelelseskryptering](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-the-new-ome-capabilities"></a>Introduktion til de nye OME-funktioner

Hvis du er klar til at gå i gang med at bruge de nye OME-funktioner i din organisation, skal du [se Konfigurer Office 365-meddelelseskryptering funktioner](set-up-new-message-encryption-capabilities.md).

## <a name="sending-viewing-and-replying-to-encrypted-email-messages"></a>Sende, få vist og svare på krypterede mails

Med Office 365-meddelelseskryptering kan brugerne sende krypterede mails fra Outlook og Outlook på internettet. Desuden kan administratorer konfigurere regler for mailflow i Microsoft 365 automatisk kryptere mails baseret på nøgleordssammenholdelse eller andre betingelser.

Modtagerne af krypterede meddelelser i organisationer vil kunne læse disse meddelelser problemfrit i en hvilken som helst version Outlook, herunder Outlook til pc, Outlook til Mac, Outlook på internettet, Outlook til iOS og Outlook til Android. Brugere, der modtager krypterede meddelelser på andre mailklienter, kan få vist meddelelserne i OME-portalen.

Se nærmere på disse artikler for at få detaljeret vejledning i, hvordan du sender og får vist krypterede meddelelser.

|Læs denne artikel...|Hvis du er...|
|:-----|:-----|
|[Få mere at vide om beskyttede meddelelser i Office 365](https://support.office.com/article/2baf3ac7-12db-40a4-8af7-1852204b4b67.aspx)|En slutbruger, der gerne vil vide mere om, hvordan krypterede meddelelser fungerer, og hvilke indstillinger der er tilgængelige for dig.|
|[Hvordan åbner jeg en beskyttet meddelelse?](https://support.office.com/article/1157a286-8ecc-4b1e-ac43-2a608fbf3098.aspx)|En slutbruger, der ønsker at læse en beskyttet meddelelse, der blev sendt til dig. Denne artikel indeholder oplysninger om at læse meddelelser i flere versioner af Outlook og fra forskellige mailkonti, herunder disse konti uden for Microsoft 365 f.eks. gmail og Yahoo! konti.|
|[Send, få vist og svar på krypterede meddelelser i Outlook](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)|En slutbruger, der vil sende, se eller svare på en krypteret meddelelse fra Outlook. Selvom du ikke er medlem af en organisation, modtager du stadig meddelelser om krypterede meddelelser, der er sendt til dig Outlook. Brug denne artikel for at få vejledning i, hvordan du får vist og besvarer krypterede meddelelser, der sendes Office 365.|
|[Sende en digitalt signeret eller krypteret meddelelse](https://support.microsoft.com/office/send-a-digitally-signed-or-encrypted-message-a18ecf7f-a7ac-4edd-b02e-687b05eff547)|En slutbruger, der vil sende, se eller svare på krypterede meddelelser ved hjælp af Outlook til Mac. Denne artikel omhandler også brug af andre krypteringsmetoder end OME, f.eks. S/MIME.|
|[Få vist krypterede meddelelser på din Android-enhed](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb)|En slutbruger, der har modtaget en meddelelse, der er krypteret med Office 365-meddelelseskryptering på din Android-enhed, kan du bruge den gratis OME Viewer-app til at få vist meddelelsen og sende et krypteret svar. I denne artikel forklares det hvordan.|
|[Se krypterede meddelelser på din iPhone eller iPad](https://support.microsoft.com/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|En slutbruger, der har modtaget en meddelelse, der er krypteret med Office 365-meddelelseskryptering på din iPhone eller iPad, kan du bruge den gratis OME Viewer-app til at få vist meddelelsen og sende et krypteret svar. I denne artikel forklares det hvordan.|
||