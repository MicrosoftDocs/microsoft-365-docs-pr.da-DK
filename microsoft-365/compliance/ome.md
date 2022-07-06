---
title: Office 365 meddelelsekryptering
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
description: Få mere at vide om, hvordan du sender og modtager krypterede mails mellem personer i og uden for din organisation.
ms.openlocfilehash: 746a1cbb1d4fa5e98fb3fc3cbba529232178987c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640560"
---
# <a name="message-encryption"></a>Meddelelsekryptering

Folk bruger ofte mail til at udveksle følsomme oplysninger, f.eks. økonomiske data, juridiske kontrakter, fortrolige produktoplysninger, salgsrapporter og projektioner, patient sundhedsoplysninger eller kunde- og medarbejderoplysninger. Derfor kan postkasser blive lagre for store mængder potentielt følsomme oplysninger, og datalækage kan blive en alvorlig trussel for din organisation.

Med Office 365 meddelelseskryptering kan din organisation sende og modtage krypterede mails mellem personer i og uden for organisationen. Office 365 Meddelelsekryptering fungerer sammen med Outlook.com, Yahoo!, Gmail og andre mailtjenester. Kryptering af mailmeddelelser hjælper med at sikre, at det kun er modtagere, der er beregnet til at få vist meddelelsesindhold.

## <a name="how-message-encryption-works"></a>Sådan fungerer meddelelseskryptering

Resten af denne artikel gælder for Microsoft Purview-meddelelseskryptering.

Microsoft Purview-meddelelseskryptering er en onlinetjeneste, der er baseret på Microsoft Azure Rights Management (Azure RMS), som er en del af Azure Information Protection. Denne tjeneste indeholder politikker for kryptering, identitet og godkendelse, der hjælper med at beskytte din mail. Du kan kryptere meddelelser ved hjælp af rettighedsadministrationsskabeloner, [indstillingen Videresend ikke](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails) og [indstillingen Kun kryptering](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

Brugerne kan derefter kryptere mails og forskellige vedhæftede filer ved hjælp af disse indstillinger. Du kan se en komplet liste over understøttede typer vedhæftede filer under ["Filtyper, der er omfattet af IRM-politikker, når de er knyttet til meddelelser" i Introduktion til IRM for mails](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM).

Som administrator kan du også definere regler for mailflow for at anvende denne beskyttelse. Du kan f.eks. oprette en regel, der kræver kryptering af alle meddelelser, der er adresseret til en bestemt modtager, eller som indeholder bestemte ord i emnelinjen, og også angive, at modtagerne ikke kan kopiere eller udskrive indholdet af meddelelsen.

I modsætning til den tidligere version af OME giver de nye funktioner en samlet afsenderoplevelse, uanset om du sender mail i din organisation eller til modtagere uden for Microsoft 365. Desuden behøver modtagere, der modtager en beskyttet mail, der er sendt til en Microsoft 365-konto i Outlook 2016 eller Outlook på internettet, ikke at foretage sig andet for at få vist meddelelsen. Det fungerer problemfrit. Modtagere, der bruger andre mailklienter og udbydere af mailtjenester, har også en forbedret oplevelse. Du kan finde oplysninger under [Få mere at vide om beskyttede meddelelser i Office 365](https://support.office.com/article/Learn-about-protected-messages-in-Office-365-2baf3ac7-12db-40a4-8af7-1852204b4b67) og [Hvordan gør jeg åbne en beskyttet meddelelse](https://support.office.com/article/How-do-I-open-a-protected-message-1157a286-8ecc-4b1e-ac43-2a608fbf3098).

Du kan finde en detaljeret liste over forskellene mellem den tidligere version af OME og Microsoft Purview-meddelelseskryptering under [Sammenlign versioner af meddelelseskryptering](ome-version-comparison.md).

Når nogen sender en mail, der svarer til en regel for et krypteringsmailflow, krypteres meddelelsen, før den sendes. Alle Microsoft 365-slutbrugere, der bruger Outlook-klienter til at læse mails, modtager oprindelige læseoplevelser i første klasse for krypterede og rettighedsbeskyttede mails, også selvom de ikke er i samme organisation som afsenderen. Understøttede Outlook-klienter omfatter Outlook Desktop, Outlook Mac, Outlook Mobile på iOS og Android og Outlook på internettet (tidligere kaldet Outlook Web App).

Modtagere af krypterede meddelelser, der modtager krypterede eller rettighedsbeskyttede mails, der sendes til deres Outlook.com-, Gmail- og Yahoo-konti, modtager en ombrydermail, der sender dem til OME-portalen, hvor de nemt kan godkende ved hjælp af en Microsoft-konto, Gmail eller Yahoo-legitimationsoplysninger.

Slutbrugere, der læser krypterede eller rettighedsbeskyttede mails på andre klienter end Outlook, bruger også OME-portalen til at få vist krypterede og rettighedsbeskyttede meddelelser, som de modtager.

Hvis afsenderen af den beskyttede mail er i GCC High, og modtageren er uden for GCC High, herunder kommercielle brugere, Outlook.com brugere og brugere af andre mailudbydere, f.eks. Gmail, modtager modtageren en indpakningsmail. Ombrydningsmailen sender modtageren til OME-portalen, hvor modtageren kan læse og besvare meddelelsen. Ellers modtager modtagere, der bruger Outlook-klienter til at læse mails, oprindelige første klasses læseoplevelser for krypterede og rettighedsbeskyttede mails, selvom afsenderen og modtageren begge befinder sig i GCC High-miljøet, selvom de ikke er i samme organisation. Du kan få flere oplysninger om den forskellige oplevelse i GCC High under [Sammenlign versioner af OME](ome-version-comparison.md).

Du kan få flere oplysninger om størrelsesgrænser for meddelelser og vedhæftede filer, som du kan kryptere ved hjælp af OME, [under Exchange Online Grænser](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).

## <a name="how-microsoft-purview-advanced-message-encryption-works-on-top-of-microsoft-purview-message-encryption"></a>Sådan fungerer Avanceret meddelelseskryptering i Microsoft Purview oven på Microsoft Purview-meddelelseskryptering

Med Microsoft Purview Advanced Message Encryption kan du oprette flere brandingskabeloner, så du kan finjustere kontrollen over modtagermails og oprette brugerdefinerede brandingoplevelser, der understøtter en alsidig organisationsstruktur.

Avanceret meddelelseskryptering i Microsoft 365 hjælper dig med at opfylde overholdelsesforpligtelser, der kræver mere fleksibel kontrol over den eksterne modtagers adgang til krypterede mails. Med Avanceret meddelelseskryptering kan du som administrator styre følsomme mails, der deles uden for organisationen, med automatiske politikker, der registrerer følsomme informationstyper (f.eks. pii-id'er, finansielle id'er eller sundheds-id'er) eller nøgleord for at forbedre beskyttelsen ved at udløbe adgang via en sikker webportal til krypterede mails. Som administrator kan du yderligere styre krypterede mails, der tilgås via en webportal, ved at tilbagekalde adgangen til en mail når som helst.

Tilbagekaldelse og udløb af meddelelser fungerer kun for mails, som brugerne sender til modtagere uden for organisationen. Modtagerne skal desuden have adgang til mailen via webportalen. Hvis du vil sikre, at modtageren bruger portalen til at modtage mail, skal du konfigurere en brugerdefineret brandingskabelon, der anvender ombrydningen. Derefter skal du anvende brandingskabelonen i en regel for et mailflow. Du kan få flere oplysninger om avanceret meddelelseskryptering under [Avanceret meddelelseskryptering](ome-advanced-message-encryption.md).

## <a name="defining-rules-for-microsoft-purview-message-encryption"></a>Definition af regler for Microsoft Purview-meddelelseskryptering

En måde at aktivere Microsoft Purview-meddelelseskryptering på er ved at Exchange Online og Exchange Online Protection administratorer kan definere regler for mailflow. Disse regler bestemmer, under hvilke betingelser mails skal krypteres. Når der angives en krypteringshandling for en regel, krypteres alle meddelelser, der opfylder regelbetingelserne, før de sendes.

Regler for mailflow er fleksible, så du kan kombinere betingelser, så du kan opfylde specifikke sikkerhedskrav i en enkelt regel. Du kan f.eks. oprette en regel for at kryptere alle meddelelser, der indeholder angivne nøgleord og er adresseret til eksterne modtagere. Microsoft Purview-meddelelseskryptering også kryptere svar fra modtagere af krypteret mail.

Du kan finde flere oplysninger om, hvordan du opretter regler for mailflow for at drage fordel af Microsoft Purview-meddelelseskryptering, under [Definer regler for mailflow for at kryptere mails](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-the-microsoft-purview-message-encryption"></a>Kom i gang med Microsoft Purview-meddelelseskryptering

Hvis du er klar til at komme i gang med at bruge Microsoft Purview-meddelelseskryptering i din organisation, skal du se [Konfigurer Microsoft Purview-meddelelseskryptering](set-up-new-message-encryption-capabilities.md).

## <a name="sending-viewing-and-replying-to-encrypted-email-messages"></a>Sender, får vist og besvarer krypterede mails

Med Microsoft Purview-meddelelseskryptering kan brugerne sende krypteret mail fra Outlook og Outlook på internettet. Derudover kan administratorer konfigurere regler for mailflow i Microsoft 365 for automatisk at kryptere mails baseret på nøgleordsmatch eller andre betingelser.

Modtagere af krypterede meddelelser, der er i organisationer, kan uden problemer læse disse meddelelser i alle versioner af Outlook, herunder Outlook til pc, Outlook til Mac, Outlook på internettet, Outlook til iOS og Outlook til Android. Brugere, der modtager krypterede meddelelser på andre mailklienter, kan få vist meddelelserne på OME-portalen.

Du kan finde en detaljeret vejledning i, hvordan du sender og får vist krypterede meddelelser, i disse artikler.

|Læs denne artikel...|Hvis du er...|
|:-----|:-----|
|[Få mere at vide om beskyttede meddelelser i Office 365](https://support.office.com/article/2baf3ac7-12db-40a4-8af7-1852204b4b67.aspx)|En slutbruger, der gerne vil vide mere om, hvordan krypterede meddelelser fungerer, og hvilke indstillinger der er tilgængelige for dig.|
|[Hvordan gør jeg du åbne en beskyttet meddelelse?](https://support.office.com/article/1157a286-8ecc-4b1e-ac43-2a608fbf3098.aspx)|En slutbruger, der vil læse en beskyttet meddelelse, der er sendt til dig. Denne artikel indeholder oplysninger om læsning af meddelelser i flere versioner af Outlook og fra forskellige mailkonti, herunder disse konti uden for Microsoft 365, f.eks Gmail og Yahoo! Konti.|
|[Send, få vist og besvar krypterede meddelelser i Outlook](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)|En slutbruger, der ønsker at sende, få vist eller besvare en krypteret meddelelse fra Outlook. Selvom du ikke er medlem af en organisation, modtager du stadig en meddelelse om krypterede meddelelser, der sendes til dig i Outlook. Brug denne artikel til at få vist og besvare krypterede meddelelser, der er sendt fra Office 365.|
|[Send en digitalt signeret eller krypteret meddelelse](https://support.microsoft.com/office/send-a-digitally-signed-or-encrypted-message-a18ecf7f-a7ac-4edd-b02e-687b05eff547)|En slutbruger, der ønsker at sende, få vist eller besvare krypterede meddelelser ved hjælp af Outlook til Mac. Denne artikel dækker også brug af andre krypteringsmetoder end OME, f.eks. S/MIME.|
|[Få vist krypterede meddelelser på din Android-enhed](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb)|En slutbruger, der har modtaget en meddelelse, der er krypteret med Office 365 meddelelseskryptering på din Android-enhed, kan du bruge den gratis OME Viewer-app til at få vist meddelelsen og sende et krypteret svar. I denne artikel forklares det, hvordan.|
|[Få vist krypterede meddelelser på din iPhone eller iPad](https://support.microsoft.com/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|En slutbruger, der har modtaget en meddelelse, der er krypteret med Office 365 meddelelseskryptering på din iPhone eller iPad, kan du bruge den gratis OME Viewer-app til at få vist meddelelsen og sende et krypteret svar. I denne artikel forklares det, hvordan.|
||
