---
title: Beskyttelse mod phishing
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 75af74b2-c7ea-4556-a912-8c48e07271d3
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om funktionerne til beskyttelse mod phishing i Exchange Online Protection (EOP) og Microsoft Defender Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 81cd2870ff3471fbd535415229b3ced20bba1fbf
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/09/2021
ms.locfileid: "63587524"
---
# <a name="anti-phishing-protection-in-microsoft-365"></a>Beskyttelse mod phishing i Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*Phishing* er et mailangreb, der forsøger at stjæle følsomme oplysninger i meddelelser, der ser ud til at være fra legitime eller afsendere, der er tillid til. Der findes bestemte kategorier for phishing. Eksempel:

- **Typisk phishing** bruger fokuseret, tilpasset indhold, der er specifikt skræddersyet til de målrettede modtagere (typisk efter at have omkonfigureret modtagerne af hackeren).

- **Whaling er** henvendt til ledere eller andre mål af høj værdi inden for en organisation for at opnå maksimal effekt.

- **BEC (Business Email Compromise)** anvender forfalskede afsendere (regnskabsmedarbejdere, kunder, pålidelige partnere osv.) til at narre modtagere til at godkende betalinger, overføre penge eller afsløre kundedata. Få mere at vide ved at [se denne video](https://www.youtube.com/watch?v=8Kn31h9HwIQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=2).

- **Ransomware** , der krypterer dine data og kræver betaling for at dekryptere den, starter næsten altid i phishing-meddelelser. Beskyttelse mod phishing kan ikke hjælpe dig med at dekryptere krypterede filer, men det kan hjælpe med at registrere de indledende phishingmeddelelser, der er knyttet til ransomware-kampagnen. Du kan finde flere oplysninger om gendannelse efter en ransomware-angreb under [Gendan efter en ransomware-angreb Microsoft 365](recover-from-ransomware.md).

Med den voksende kompleksitet af angreb er det endda svært for uddannede brugere at identificere avancerede phishing-meddelelser. Heldigvis kan Exchange Online Protection (EOP) og de ekstra funktioner i Microsoft Defender Office 365 hjælpe.

## <a name="anti-phishing-protection-in-eop"></a>Beskyttelse mod phishing i EOP

EOP (dvs. Microsoft 365 uden Microsoft Defender til Office 365) indeholder funktioner, der kan hjælpe med at beskytte din organisation mod phishingtrusler:

- **Efterlignet intelligens**: Brug efterlignet intelligens indsigt til at gennemse registrerede efterlignede afsendere i meddelelser fra eksterne og interne domæner og manuelt tillade eller blokere disse registrerede afsendere. Du kan finde flere oplysninger [under Efterlignet intelligensindsigt i EOP](learn-about-spoof-intelligence.md).

- **Antiphishing-politikker i EOP**: Slå efterlignet intelligens til eller fra, slå ikke-godkendt afsenderidentifikation i Outlook til eller fra og angive handlingen for blokerede spoof-afsendere. Få mere at vide under [Konfigurer antiphishing-politikker i EOP](configure-anti-phishing-policies-eop.md).

- **Tillad eller bloker spoof-afsendere på lejerens tilladelses- eller blokeringsliste**: Når du tilsidesætter konklusionen i spoof intelligence-indsigten, bliver den spooferede afsender til en manuel tillad eller bloker post, der kun vises på fanen **Spoof** på lejerens tilladelses-/blokeringsliste. Du kan også manuelt oprette tillade eller blokere poster for spoof afsendere, før de registreres af efterlignet intelligens. Få mere at vide under [Administrer lejerens tilladelses-/blokeringsliste i EOP](tenant-allow-block-list.md).

- **Implicit mailgodkendelse**: EOP forbedrer standardmailgodkendelseskontroller for indgående mail ([SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) og [DMARC](use-dmarc-to-validate-email.md) med afsender ry, afsenderhistorik, modtagerhistorik, adfærdsanalyse og andre avancerede teknikker til at identificere forfalskede afsendere. Du kan finde flere oplysninger [under Mailgodkendelse i Microsoft 365](email-validation-and-authentication.md).

## <a name="additional-anti-phishing-protection-in-microsoft-defender-for-office-365"></a>Yderligere beskyttelse mod phishing i Microsoft Defender til Office 365

Microsoft Defender til Office 365 indeholder flere og flere avancerede antiphishing-funktioner:

- **Antiphishing-politikker i Microsoft Defender til Office 365**: Konfigurer indstillinger for repræsentationsbeskyttelse for bestemte meddelelsesafsendere og afsenderdomæner, indstillinger for postkasseintelligens og justerbare avancerede phishingtærskler. Få mere at vide under [Konfigurer antiphishing-politikker i Microsoft Defender Office 365](configure-mdo-anti-phishing-policies.md). Du kan finde flere oplysninger om forskellene mellem antiphishing-politikker i EOP og antiphishing-politikker i Defender for Office 365 i [Antiphishing-politikker i Microsoft 365](set-up-anti-phishing-policies.md).
- **Kampagnevisninger**: Maskinel indlæring og anden heuristics identificerer og analyserer meddelelser, der er involveret i koordinerede phishingangreb mod hele tjenesten og organisationen. Få mere at vide under [Kampagnevisninger i Microsoft Defender for Office 365](campaigns.md).
- **Kursus i** angrebssimulering: Administratorer kan oprette falske phishingmeddelelser og sende dem til interne brugere som et uddannelsesværktøj. Du kan finde flere oplysninger i [Simulere et phishingangreb](attack-simulation-training.md).

## <a name="other-anti-phishing-resources"></a>Andre antiphishing-ressourcer

- Til slutbrugere: [Beskyt dig selv mod phishing og andre former for onlinesvindel](https://support.microsoft.com/office/be0de46a-29cd-4c59-aaaf-136cf177d593).

- [Hvordan Microsoft 365 validerer Fra-adressen for at forhindre phishing](how-office-365-validates-the-from-address.md).
