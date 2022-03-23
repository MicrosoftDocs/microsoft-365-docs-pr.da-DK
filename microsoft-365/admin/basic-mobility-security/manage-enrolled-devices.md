---
title: Administrer enheder, der er tilmeldt Administration af mobilenheder i Microsoft 365
f1.keywords:
- NOCSH
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
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid:
- MET150
description: Grundlæggende mobilitet og sikkerhed kan hjælpe dig med at sikre og administrere dine organisationers mobilenheder.
ms.openlocfilehash: 152b4cc33fab740516d7138cca8f4a15096c8312
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591438"
---
# <a name="manage-devices-enrolled-in-mobile-device-management-in-microsoft-365"></a>Administrer enheder, der er tilmeldt Administration af mobilenheder i Microsoft 365

Den indbyggede administration af mobilenheder til Microsoft 365 hjælper dig med at sikre og administrere dine brugeres mobilenheder som iPhones, iPads, Android-Windows telefoner. Det første trin er at logge på Microsoft 365 og konfigurere Grundlæggende mobilitet og sikkerhed. Du kan få mere at vide [under Konfigurer Grundlæggende mobilitet og sikkerhed](set-up.md).

Når du har konfigureret det, skal personerne i organisationen tilmelde deres enheder til tjenesten. Du kan få mere at vide [under Tilmeld din mobilenhed ved hjælp af Grundlæggende mobilitet og sikkerhed](enroll-your-mobile-device.md).Derefter kan du bruge Grundlæggende mobilitet og sikkerhed til at administrere enheder i din organisation. Du kan f.eks. bruge sikkerhedspolitikker for enheder til at begrænse mailadgang eller andre tjenester, få vist enheders rapporter og slette en enhed eksternt. Du kommer typisk til Security & Compliance Center for at udføre disse opgaver. Du kan finde flere oplysninger [i Microsoft 365 Overholdelsescenter](../../compliance/microsoft-365-compliance-center.md).

## <a name="device-management-tasks"></a>Administration af enheder

Følg disse trin for at få adgang til panelet for enhedshåndtering:

1. Gå til  [Microsoft 365 Administration](../../admin/admin-overview/about-the-admin-center.md).

2. Skriv Administration af mobilenheder i søgefeltet, og vælg Administration **af**  mobilenheder på listen over resultater.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Indstilling til administration af mobilenheder.":::

3.   **SelectLet'er er i gang**.

## <a name="manage-mobile-devices"></a>Administrer mobilenheder

Når du har konfigureret Grundlæggende mobilitet og sikkerhed, er her nogle måder at administrere mobilenheder i din organisation på.

|**Hvis du vil**|**Skal du**|
|:----------------|:------------------------------------------------------------------------------|
|Slette en enhed |I panelet Enhedshåndtering skal du vælge Navn på  *enhed og*  ****    ****  derefter Fuldstændig sletning for at slette alle oplysninger ellerVælg sletning for kun at slette virksomhedsoplysninger på enheden. Du kan finde flere oplysninger [i Slette en mobilenhed i Grundlæggende mobilitet og sikkerhed](wipe-mobile-device.md).|
|Bloker ikke-understøttede enheder i at få adgang Exchange mails ved hjælp af Exchange ActiveSync |I panelet Enhedshåndtering skal du   **vælgeBlock**. |
|Konfigurer enhedspolitikker som f.eks. adgangskodekrav og sikkerhedsindstillinger |I panelet Enhedshåndtering skal du vælge **Sikkerhedspolitikker for**  **enhederAdd** > +. Du kan få mere at vide  [underOprette sikkerhedspolitikker for enheder i Grundlæggende mobilitet og sikkerhed](create-device-security-policies.md).|
|Vis liste over blokerede enheder  |I panelet Enhedshåndtering   **underVælg en visningBlokeret** .  **** |
|Fjern blokeringen af en ikke-kompatieret eller ikke-understøttet enhed for en bruger eller gruppe af brugere  |Vælg et af følgende for at fjerne blokeringen af enheder:<br/>- Fjern brugeren eller brugerne fra den sikkerhedsgruppe, som politikken er blevet anvendt på. Gå til Microsoft 365 Administration > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**grupper**</a>, og vælg derefter gruppenavn. Vælg **Rediger medlemmer og administratorer**.<br/>- Fjern sikkerhedsgruppen, som brugerne er medlem af, fra enhedens politik. Gå til Security & Compliance Center > **SikkerhedspolitikkerDevice-sikkerhedspolitikker** **** >. Vælg navn på enhedspolitik, og **vælg** **derefter EditDeployment** > .<br/>- Fjern blokeringen af alle enheder, der ikke fungerer som produkter, for en enhedspolitik. Gå til Security & Compliance Center > **SikkerhedspolitikkerDevice-sikkerhedspolitikker** **** >. Vælg navn på enhedspolitik, og vælg **derefter**  **EditAccess-krav** >. Vælg  **Tillad adgang, og rapportér overtrædelse**.<br/>- Hvis du vil fjerne blokeringen af en ikke-kompatibilitetsbaseret eller ikke-understøttet enhed for en bruger eller en gruppe af brugere, skal du gå til Security & Compliance Center > **Security**  **policiesDevice** >  **managementManage** > device access settings. Tilføj en sikkerhedsgruppe med de medlemmer, du vil udelukke fra at blive blokeret adgang til Microsoft 365. Få mere at vide [under Opret, rediger eller slet en sikkerhedsgruppe i Microsoft 365 Administration](../../admin/email/create-edit-or-delete-a-security-group.md).|
|Fjern brugere, så deres enheder ikke længere administreres af Grundlæggende mobilitet og sikkerhed |Hvis du vil fjerne brugeren, skal du redigere den sikkerhedsgruppe, der har politikker for administration af enheder for Grundlæggende mobilitet og sikkerhed. Du kan finde flere   [oplysninger i Oprette, redigere eller slette en sikkerhedsgruppe i Microsoft 365 Administration](../../admin/email/create-edit-or-delete-a-security-group.md).<br/>Hvis du vil fjerne Grundlæggende mobilitet og sikkerhed fra alle Microsoft 365 brugere, skal du [se Slå Grundlæggende mobilitet og sikkerhed fra](turn-off.md).|

Live (v14)