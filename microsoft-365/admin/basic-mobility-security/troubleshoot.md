---
title: Foretag fejlfinding af Grundlæggende mobilitet og sikkerhed
f1.keywords: NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
description: Prøv disse trin for at spore problemer med grundlæggende mobilitet og sikkerhed
ms.openlocfilehash: 1b1b7d67eb07c67c320554c1d64701983da30e15
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/23/2022
ms.locfileid: "65636058"
---
# <a name="troubleshoot-basic-mobility-and-security"></a>Foretag fejlfinding af Grundlæggende mobilitet og sikkerhed

Hvis du støder på problemer, når du forsøger at tilmelde en enhed til Basic Mobility and Security, kan du prøve trinnene her for at spore problemet. Hvis de generelle trin ikke løser problemet, kan du se et af de senere afsnit med bestemte trin til din enhedstype.

## <a name="steps-to-try-first"></a>Trin til at prøve først

Du starter ved at kontrollere følgende:

- Sørg for, at enheden ikke allerede er tilmeldt en anden udbyder af administration af mobilenheder, f.eks. Intune.

- Sørg for, at enheden er indstillet til den korrekte dato og det korrekte klokkeslæt.

- Skift til et andet WIFI- eller mobilnetværk på enheden.

- For Android- eller iOS-enheder skal du fjerne og geninstallere appen Intune-firmaportal på enheden. 

## <a name="ios-phone-or-tablet"></a>iOS-telefon eller -tablet

- Sørg for, at du har konfigureret et APN-certifikat. Du kan finde flere oplysninger under [Opret et APN-certifikat til iOS-enheder](create-an-apns-certificate-for-ios-devices.md).

- I **Indstillinger** >  **GenereltProfile** >  **(eller Enhedshåndtering)** skal du sørge for, at der ikke allerede er installeret en administrationsprofil. Hvis det er, skal du fjerne det.

- Hvis du får vist fejlmeddelelsen "Enheden kunne ikke tilmeldes", skal du logge på Microsoft 365 og kontrollere, at en licens, der indeholder Exchange Online, er tildelt den bruger, der er logget på enheden.

- Hvis du får vist fejlmeddelelsen "Profilen kunne ikke installeres", kan du prøve en af følgende fremgangsmåder:

    - Sørg for, at Safari er standardbrowseren på enheden, og at cookies ikke er deaktiveret.

    - Genstart enheden, og naviger derefter til portal.manage.microsoft.com. Log på med dit Microsoft 365 bruger-id og din adgangskode, og forsøg at installere profilen manuelt.

## <a name="windows-rt"></a>Windows RT

- Sørg for, at dit domæne er konfigureret i Microsoft 365 til at arbejde med grundlæggende mobilitet og sikkerhed. Du kan finde flere oplysninger under [Konfigurer grundlæggende mobilitet og sikkerhed](set-up.md).
    
- Sørg for, at brugeren vælger **Slå til** i stedet for at vælge **Deltag**.

## <a name="windows-10-pc"></a>Windows 10 pc

- Sørg for, at dit domæne er konfigureret i Microsoft 365 til at arbejde med grundlæggende mobilitet og sikkerhed. Du kan finde flere oplysninger under [Konfigurer grundlæggende mobilitet og sikkerhed](set-up.md).
    
- Medmindre du har Azure Active Directory Premium, skal du sørge for, at brugeren **kun vælger Tilmeld dig Enhedshåndtering i** stedet for at vælge **Forbind**.

## <a name="android-phone-or-tablet"></a>Android-telefon eller -tablet

- Kontrollér, at enheden kører Android.

- Sørg for, at Chrome er opdateret og er angivet som standardbrowser.

- Hvis du får vist fejlmeddelelsen "Vi kunne ikke tilmelde denne enhed", skal du logge på Microsoft 365 og kontrollere, at en licens, der indeholder Exchange Online, er tildelt den bruger, der er logget på enheden.

- Kontrollér meddelelsesområdet på enheden for at se, om eventuelle påkrævede slutbrugerhandlinger venter, og om de er, skal du fuldføre handlingerne.