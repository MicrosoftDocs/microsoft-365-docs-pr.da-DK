---
title: Fraråde visning af meddelelseskrypteringsapp
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
description: Appen Office 365-meddelelseskryptering (OME) Viewer blev fjernet fra Android- og Apple-butikker i 2018.
ms.openlocfilehash: 0eded17f4da5347e1f1a88031a780cee5f8b1dee
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588904"
---
# <a name="deprecating-message-encryption-viewer-app"></a>Fraråde visning af meddelelseskrypteringsapp

Den 15. august 2018 fjernede vi Office 365-meddelelseskryptering (OME) Viewer-mobilappen fra Android- og Apple Store. Mobilappen Office 365 Message Encryption Viewer at kunne læse mails og vedhæftede filer, der blev krypteret med den tidligere version af OME på Apple- og Android-telefoner. Ud over at fjerne OME Viewer-appen foretager vi ikke andre ændringer i den tidligere version af OME.
  
## <a name="changes-from-august-2018"></a>Ændringer fra august 2018

Som offentliggjort i september 2017 har vi udgivet en ny version af [Office 365-meddelelseskryptering](https://aka.ms/ome2017), så brugerne kan sende krypterede og beskyttede meddelelser til personer i eller uden for organisationen uden krav fra mobilappen. Siden da har vi tilføjet yderligere funktioner:
  
- [Kun krypteret skabelon](https://aka.ms/encryptonly)

- [Kontrolelement til dekryptering af vedhæftede filer](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Admin-control-for-attachments-now-available-in-Office-365/ba-p/204007)

Med denne ændring vil brugerne ikke længere kunne downloade mobilappen til Office 365 Message Encryption Viewer fra den 1. august. Det betyder, at modtagerne af mails muligvis ikke kan læse meddelelser, der er krypteret med den tidligere version af OME, på nogle Android- og Apple-mobilenheder. De vil dog stadig kunne læse disse meddelelser på personlige computere (via skrivebordsbrowsere). Brugere, der allerede har downloadet appen, vil fortsat kunne bruge den.
  
## <a name="why-this-change-was-made"></a>Hvorfor denne ændring blev foretaget

Den nye version af OME kræver ikke længere en mobilapp for at læse beskyttede mails og vedhæftede filer. Kunder, der bruger de nye OME-funktioner, kan få vist den beskyttede meddelelse i Outlook mobil, og ikke-kunder kan få vist beskyttede meddelelser i en browser.
  
Krav om, at brugere skal downloade en mobilapp, er en anden forhindring for, at kunderne kan få vist beskyttede meddelelser. De nye Office 365-meddelelseskryptering giver en bedre mobiloplevelse.
  
## <a name="can-i-still-use-the-previous-version-of-office-365-message-encryption"></a>Kan jeg stadig bruge den tidligere version af Office 365-meddelelseskryptering

Den tidligere version af Office 365-meddelelseskryptering frarådes på nuværende tidspunkt, men vi har foretaget betydelige forbedringer til den nye version af Office 365-meddelelseskryptering , hvilket gør det nemmere at kryptere og rettighedsbeskytte følsomme data til alle og på en hvilken som helst enhed – herunder muligheden for, at brugerne kan læse beskyttede meddelelser direkte i Outlook (computer, mobil og web). 
  
## <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Hvad skal jeg gøre for at forberede denne ændring?

Hvis din organisation i øjeblikket sender krypterede vedhæftede filer til modtagere, der kræver OME Viewer-appen, skal du opdatere din dokumentation og undervisningsressourcer.
  
Vi anbefaler, at Exchange regler for mailflow til at bruge den aktuelle version af OME, så organisationen kan udnytte de nye og forbedrede funktioner. Når du har konfigureret de nye OME-funktioner, behøver modtagerne ikke OME Viewer-appen for at læse krypterede meddelelser på mobilenheder.
  
Microsoft anbefaler, at du planlægger at flytte til de nye OME-funktioner, så snart det er fornuftigt for din organisation. Du kan finde en [vejledning under Konfigurere Office 365-meddelelseskryptering funktioner](set-up-new-message-encryption-capabilities.md). Hvis du vil vide mere om, hvordan de nye funktioner virker først, skal du se [Office 365-meddelelseskryptering](ome.md).
  

