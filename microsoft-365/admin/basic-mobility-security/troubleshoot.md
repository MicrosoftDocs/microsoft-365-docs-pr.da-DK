---
title: Fejlfinding af grundlæggende mobilitet og sikkerhed
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
ms.openlocfilehash: 2ac25e36fced24e5b50e7e89d36dae3e842fda04
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63591440"
---
# <a name="troubleshoot-basic-mobility-and-security"></a>Fejlfinding af grundlæggende mobilitet og sikkerhed

Hvis du får problemer, når du forsøger at tilmelde en enhed i Grundlæggende mobilitet og sikkerhed, kan du prøve disse trin for at finde problemet. Hvis de generelle trin ikke løser problemet, skal du se et af de senere afsnit med specifikke trin til din enhedstype.

## <a name="steps-to-try-first"></a>Trin til at prøve først

For at starte skal du kontrollere følgende:

- Sørg for, at enheden ikke allerede er tilmeldt en anden udbyder af administration af mobilenheder, f.eks. Intune.

- Sørg for, at enheden er indstillet til den korrekte dato og det korrekte klokkeslæt.

- Skift til et andet WIFI- eller mobilnetværk på enheden.

- På Android- eller iOS-enheder skal du fjerne og Intune-firmaportal appen på enheden. 

## <a name="ios-phone-or-tablet"></a>iOS-telefon eller -tablet

- Sørg for, at du har konfigureret et APNs-certifikat. Få mere at vide under [Opret et APNs-certifikat til iOS-enheder](create-an-apns-certificate-for-ios-devices.md).

- In  **Indstillinger** >  **GeneralProfile** >  **(eller Enhedshåndtering)** skal du sørge for, at der ikke allerede er installeret en administrationsprofil. Hvis det er, skal du fjerne det.

- Hvis du får vist fejlmeddelelsen "Enheden kunne ikke tilmeldes", skal du logge på Microsoft 365 og kontrollere, at der er tildelt en licens, som omfatter Exchange Online, til den bruger, der er logget på enheden.

- Hvis du får vist fejlmeddelelsen "Profilen kunne ikke installeres", kan du prøve et af følgende:

    - Sørg for, at Safari er standardbrowseren på enheden, og at cookies ikke er deaktiveret.

    - Genstart enheden, og gå derefter til portal.manage.microsoft.com. Log på med dit Microsoft 365-id og din adgangskode, og forsøg at installere profilen manuelt.

## <a name="windows-rt"></a>Windows RT

- Sørg for, at dit domæne er konfigureret i Microsoft 365 til at fungere med Grundlæggende mobilitet og sikkerhed. Du kan få mere at vide [under Konfigurer Grundlæggende mobilitet og sikkerhed](set-up.md).
    
- Sørg for, at brugeren  **vælgerTurn Onrather**  end at  **vælgeJoin**.

## <a name="windows-10-pc"></a>Windows 10 pc

- Sørg for, at dit domæne er konfigureret i Microsoft 365 til at fungere med Grundlæggende mobilitet og sikkerhed. Du kan få mere at vide [under Konfigurer Grundlæggende mobilitet og sikkerhed](set-up.md).
    
- Medmindre du har Azure Active Directory Premium, skal du sørge for, at brugeren  **vælgerEnroll**  i Enhedshåndtering kun lyngt end at  **Forbind**.

## <a name="android-phone-or-tablet"></a>Android-telefon eller -tablet

- Kontrollér, at enheden kører Android.

- Sørg for, at Chrome er opdateret og er indstillet som standardbrowser.

- Hvis du får vist fejlmeddelelsen "Vi kunne ikke tilmelde denne enhed", skal du logge på Microsoft 365 og sørge for, at der er tildelt en licens, der omfatter Exchange Online, til den bruger, der er logget på enheden.

- Kontrollér meddelelsesområdet på enheden for at se, om der er nogle påkrævede slutbrugerhandlinger, der afventer, og hvis de er, kan du udføre handlingerne.