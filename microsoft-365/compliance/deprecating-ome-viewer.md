---
title: Fraråder OME Viewer-app
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6336cabb-b06e-402f-9e85-8bb9eb4ce68f
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Appen OME (Office 365 Message Encryption) blev fjernet fra Android- og Apple Stores i 2018.
ms.openlocfilehash: 2e1e0ead7d34761a3159b4b51368ea4460acb596
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630075"
---
# <a name="deprecating-message-encryption-viewer-app"></a>Fraråder appen Meddelelsekrypteringsfremviser

Den 15. august 2018 fjernede vi mobilappen Office 365 Message Encryption (OME) Viewer fra Android- og Apple-butikker. Mobilappen Office 365 Message Encryption Viewer var påkrævet for at læse mails og vedhæftede filer, der blev krypteret med den tidligere version af OME på Apple- og Android-telefoner. Ud over at fjerne OME Viewer-appen foretager vi ikke andre ændringer af den tidligere version af OME.
  
## <a name="changes-from-august-2018"></a>Ændringer fra august 2018

Som annonceret i september 2017 har vi udgivet en ny version af [Office 365 Meddelelseskryptering](https://aka.ms/ome2017), så brugerne kan sende krypterede og beskyttede meddelelser til alle i eller uden for organisationen uden mobilappens krav. Siden da har vi tilføjet yderligere funktioner:
  
- [Skabelon kun til kryptering](https://aka.ms/encryptonly)

- [Kontrolelement til dekryptering af vedhæftede filer](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Admin-control-for-attachments-now-available-in-Office-365/ba-p/204007)

Med denne ændring kan brugerne ikke længere downloade mobilappen Office 365 Message Encryption Viewer fra den 1. august. Det betyder, at mailmodtagere muligvis ikke kan læse meddelelser, der er krypteret med den tidligere version af OME, på nogle Android- og Apple-mobilenheder. De vil dog stadig kunne læse disse meddelelser på personlige computere (via skrivebordsbrowsere). Brugere, der allerede har downloadet appen, vil fortsat kunne bruge den.
  
## <a name="why-this-change-was-made"></a>Hvorfor denne ændring blev foretaget

Den nye version af OME kræver ikke længere, at en mobilapp læser beskyttede mails og vedhæftede filer. Kunder, der bruger Microsoft Purview-meddelelseskryptering, kan få vist den beskyttede meddelelse i Outlook Mobile, og ikke-kunder kan få vist beskyttede meddelelser i en browser.
  
Det er en anden forhindring for kunderne at få vist beskyttede meddelelser, hvis brugerne skal downloade en mobilapp. Microsoft Purview-meddelelseskryptering giver en bedre mobiloplevelse.
  
## <a name="can-i-still-use-the-previous-version-of-office-365-message-encryption"></a>Kan jeg stadig bruge den tidligere version af Office 365 Meddelelsekryptering

Den tidligere version af Office 365 meddelelseskryptering frarådes på nuværende tidspunkt, men vi har foretaget betydelige forbedringer af Microsoft Purview-meddelelseskryptering, hvilket gør det nemmere at kryptere og rettigheder beskytte følsomme data for alle og på en hvilken som helst enhed – herunder brugernes mulighed for at læse beskyttede meddelelser direkte i Outlook (desktop,  mobil og web).
  
## <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hvad skal jeg gøre for at forberede mig på denne ændring

Hvis din organisation i øjeblikket sender krypterede vedhæftede filer til modtagere, der kræver OME Viewer-appen, skal du opdatere dokumentationen og undervisningsressourcerne.
  
Vi anbefaler, at du opdaterer eksisterende regler for Exchange-mailflow for at bruge Microsoft Purview-meddelelseskryptering, så din organisation kan drage fordel af de nye og forbedrede funktioner. Når du har konfigureret Microsoft Purview-meddelelseskryptering, behøver modtagerne ikke APPEN OME Viewer til at læse krypterede meddelelser på mobilenheder.
  
Microsoft anbefaler, at du planlægger at flytte til Microsoft Purview-meddelelseskryptering, så snart det er rimeligt for din organisation. Du kan finde en vejledning under [Konfigurer Microsoft Purview-meddelelseskryptering](set-up-new-message-encryption-capabilities.md). Hvis du vil vide mere om, hvordan kryptering af meddelelser fungerer først, skal du se [Meddelelsekryptering](ome.md).
