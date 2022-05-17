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
description: Administratorer kan få mere at vide om funktionerne til beskyttelse mod phishing i Exchange Online Protection (EOP) og Microsoft Defender for Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8d62d2a32342aa6d409e49d790af717b1ccf7d61
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438745"
---
# <a name="anti-phishing-protection-in-microsoft-365"></a>Beskyttelse mod phishing i Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

*Phishing* er et mailangreb, der forsøger at stjæle følsomme oplysninger i meddelelser, der ser ud til at være fra legitime afsendere eller afsendere, der er tillid til. Der er specifikke kategorier af phishing. Eksempel:

- **Spyd phishing** bruger fokuseret, tilpasset indhold, der er specifikt skræddersyet til de målrettede modtagere (typisk efter rekognoscering på modtagerne af angriberen).

- **Hvalfangst** er rettet mod direktører eller andre mål med høj værdi i en organisation for at opnå maksimal effekt.

- **BEC (Business Email Compromise)** bruger forfalskede afsendere, der er tillid til (økonomichefer, kunder, partnere, der er tillid til osv.), til at narre modtagere til godkendelse af betalinger, overførsel af midler eller til at afsløre kundedata. Få mere at vide ved at se [denne video](https://www.youtube.com/watch?v=8Kn31h9HwIQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=2).

- **Ransomware** , der krypterer dine data og kræver betaling for at dekryptere dem, starter næsten altid i phishing-meddelelser. Anti-phishing-beskyttelse kan ikke hjælpe dig med at dekryptere krypterede filer, men det kan hjælpe med at registrere de indledende phishing-meddelelser, der er knyttet til ransomware-kampagnen. Du kan finde flere oplysninger om gendannelse efter et ransomware-angreb under [Gendan efter et ransomware-angreb i Microsoft 365](recover-from-ransomware.md).

Med den stigende kompleksitet af angreb er det endda svært for oplærte brugere at identificere avancerede phishing-meddelelser. Heldigvis kan Exchange Online Protection (EOP) og de ekstra funktioner i Microsoft Defender for Office 365 hjælpe.

## <a name="anti-phishing-protection-in-eop"></a>Beskyttelse mod phishing i EOP

EOP (dvs. Microsoft 365 organisationer uden Microsoft Defender for Office 365) indeholder funktioner, der kan hjælpe med at beskytte din organisation mod phishing-trusler:

- **Spoof intelligence**: Brug indsigten spoof intelligence til at gennemse registrerede spoofed-afsendere i meddelelser fra eksterne og interne domæner og manuelt tillade eller blokere de registrerede afsendere. Du kan få flere oplysninger under [Spoof intelligence-indsigt i EOP](learn-about-spoof-intelligence.md).

- **Anti-phishing-politikker i EOP**: Slå spoof intelligence til eller fra, slå ikke-godkendte afsenderindikatorer til eller fra i Outlook til eller fra, og angiv handlingen for blokerede misvisende afsendere. Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af phishing i EOP](configure-anti-phishing-policies-eop.md).

- **Tillad eller bloker spooferede afsendere på listen over tilladte/blokerede lejere**: Når du tilsidesætter dommen i indsigten spoof intelligence, bliver den spooferede afsender en manuel tilladelses- eller blokpost, der kun vises under fanen **Spoof** på listen over tilladte/blokerede lejere. Du kan også manuelt oprette tillad eller blokere poster for spoof-afsendere, før de registreres af spoof intelligence. Du kan få flere oplysninger under [Administrer listen over tilladte/blokerede lejere i EOP](tenant-allow-block-list.md).

- **Implicit mailgodkendelse**: EOP forbedrer standardtjek af mailgodkendelse for indgående mail ([SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) og [DMARC](use-dmarc-to-validate-email.md) med afsenderomdømme, afsenderhistorik, modtagerhistorik, adfærdsanalyse og andre avancerede teknikker til at identificere forfalskede afsendere. Du kan få flere oplysninger under [Mailgodkendelse i Microsoft 365](email-validation-and-authentication.md).

## <a name="additional-anti-phishing-protection-in-microsoft-defender-for-office-365"></a>Yderligere beskyttelse mod phishing i Microsoft Defender for Office 365

Microsoft Defender for Office 365 indeholder yderligere og mere avancerede anti-phishing-funktioner:

- **Anti-phishing-politikker i Microsoft Defender for Office 365**: Konfigurer indstillinger for repræsentationsbeskyttelse for bestemte meddelelsesafsendere og afsenderdomæner, indstillinger for postkasseintelligens og justerbare avancerede tærskler for phishing. Du kan få flere oplysninger under [Konfigurer politikker til bekæmpelse af phishing i Microsoft Defender for Office 365](configure-mdo-anti-phishing-policies.md). Du kan få flere oplysninger om forskellene mellem politikker til bekæmpelse af phishing i EOP og politikker til bekæmpelse af phishing i Defender for Office 365 [under Politikker til bekæmpelse af phishing i Microsoft 365](set-up-anti-phishing-policies.md).
- **Kampagnevisninger**: Maskinel indlæring og andre heuristik identificerer og analyserer meddelelser, der er involveret i koordinerede phishingangreb mod hele tjenesten og din organisation. Du kan få flere oplysninger [under Kampagnevisninger i Microsoft Defender for Office 365](campaigns.md).
- **Oplæring i simulering af angreb**: Administratorer kan oprette falske phishing-meddelelser og sende dem til interne brugere som et uddannelsesværktøj. Du kan få flere oplysninger under [Simuler et phishing-angreb](attack-simulation-training.md).

## <a name="other-anti-phishing-resources"></a>Andre anti-phishing-ressourcer

- For slutbrugere: [Beskyt dig selv mod phishing-ordninger og andre former for onlinesvindel](https://support.microsoft.com/office/be0de46a-29cd-4c59-aaaf-136cf177d593).

- [Sådan validerer Microsoft 365 fra-adressen for at forhindre phishing](how-office-365-validates-the-from-address.md).
