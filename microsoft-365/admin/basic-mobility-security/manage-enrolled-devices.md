---
title: Administrer de enheder, der er tilmeldt mobile Enhedshåndtering i Microsoft 365
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
description: Basic Mobility and Security kan hjælpe dig med at sikre og administrere dine organisationers mobilenheder.
ms.openlocfilehash: 02c8efbed8f781dfdb0e9abfaa2af3a2c92733ff
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64780797"
---
# <a name="manage-devices-enrolled-in-mobile-device-management-in-microsoft-365"></a>Administrer de enheder, der er tilmeldt mobile Enhedshåndtering i Microsoft 365

Den indbyggede administration af mobilenheder til Microsoft 365 hjælper dig med at sikre og administrere dine brugeres mobilenheder, f.eks. iPhones, iPads, Androids og Windows telefoner. Det første trin er at logge på Microsoft 365 og konfigurere Grundlæggende mobilitet og sikkerhed. Du kan finde flere oplysninger under [Konfigurer grundlæggende mobilitet og sikkerhed](set-up.md).

Når du har konfigureret den, skal personerne i din organisation tilmelde deres enheder i tjenesten. Du kan finde flere oplysninger under [Tilmeld din mobilenhed ved hjælp af Basic Mobility og Security](enroll-your-mobile-device.md). Du kan derefter bruge Basic Mobility and Security til at administrere enheder i din organisation. Du kan f.eks. bruge politikker for enhedssikkerhed til at begrænse mailadgang eller andre tjenester, få vist enhedsrapporter og fjerne sletning af en enhed. Du går typisk til Security & Compliance Center for at udføre disse opgaver. Du kan finde flere oplysninger under [Microsoft 365 Overholdelsescenter](../../compliance/microsoft-365-compliance-center.md).

## <a name="device-management-tasks"></a>Opgaver i forbindelse med enhedshåndtering

Følg disse trin for at få vist panelet for enhedshåndtering:

1. Gå til [Microsoft 365 Administration](../../admin/admin-overview/about-the-admin-center.md).

2. Skriv Mobile Enhedshåndtering i søgefeltet, og vælg **Mobile Enhedshåndtering** på listen over resultater.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Indstilling for administration af mobilenheder.":::

3. Vælg **Lad os komme i gang**.

## <a name="manage-mobile-devices"></a>Administrer mobilenheder

Når du har konfigureret Basic Mobility og Security, kan du administrere mobilenhederne i din organisation på følgende måder.

|For at gøre dette|Gør dette|
|---|---|
|Slet en enhed|I panelet Enhedshåndtering skal du vælge *enhedsnavn* og derefter **Fuld sletning** for at slette alle oplysninger eller **Selektiv sletning** for kun at slette organisationsoplysninger på enheden. Du kan finde flere oplysninger under [Slet en mobilenhed i Grundlæggende mobilitet og sikkerhed](wipe-mobile-device.md).|
|Bloker enheder, der ikke understøttes, i at få adgang til Exchange mail ved hjælp af Exchange ActiveSync|Vælg **Bloker** i panelet Enhedshåndtering.|
|Konfigurer enhedspolitikker, f.eks. krav til adgangskode og sikkerhedsindstillinger|I panelet Enhedshåndtering skal du vælge **Politikker for** >  **enhedssikkerhedTilføj +**. Du kan finde flere oplysninger under [Opret politikker for enhedssikkerhed i Grundlæggende mobilitet og sikkerhed](create-device-security-policies.md).|
|Vis liste over blokerede enheder|Vælg **Blokeret** under **Vælg en visning** i panelet Enhedshåndtering.|
|Fjern blokeringen af en enhed, der ikke overholder eller ikke understøttes, for en bruger eller gruppe af brugere|Vælg en af følgende for at fjerne blokeringen af enheder:<br/>– Fjern den eller de brugere fra sikkerhedsgruppen, som politikken er anvendt på. Gå til Microsoft 365 Administration > <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Grupper**</a>, og vælg derefter gruppenavn. Vælg **Rediger medlemmer og administratorer**.<br/>– Fjern den sikkerhedsgruppe, som brugerne er medlem af, fra enhedspolitikken. Gå til Security & Compliance Center > **Security** **policiesDevice** >  security policies. Vælg navnet på enhedens politik, og vælg derefter **RedigerInstallation** > .<br/>- Fjern blokeringen af alle enheder, der ikke overholder politikken, for en enhedspolitik. Gå til Security & Compliance Center > **Security** **policiesDevice** >  security policies. Vælg enhedens politiknavn, og vælg derefter **EditAccess-krav** > . Vælg **Tillad adgangs- og rapportovertrædelse**.<br/>– Hvis du vil fjerne blokeringen af en enhed, der ikke overholder politikken, eller som ikke understøttes for en bruger eller en gruppe af brugere, skal du gå til Security & Compliance Center > **SikkerhedspolitikkerAdministration** >  >  af **tjenesteadministrationAdministrer indstillinger for enhedsadgang**. Tilføj en sikkerhedsgruppe med de medlemmer, du vil udelukke fra at blive blokeret adgang til Microsoft 365. Du kan finde flere oplysninger under [Opret, rediger eller slet en sikkerhedsgruppe i Microsoft 365 Administration](../../admin/email/create-edit-or-delete-a-security-group.md).|
|Fjern brugere, så deres enheder ikke længere administreres af Basic Mobility og Security|Hvis du vil fjerne brugeren, skal du redigere den sikkerhedsgruppe, der har politikker for enhedshåndtering for Grundlæggende mobilitet og sikkerhed. Du kan finde flere oplysninger under [Opret, rediger eller slet en sikkerhedsgruppe i Microsoft 365 Administration](../../admin/email/create-edit-or-delete-a-security-group.md).<br/>Hvis du vil fjerne Basic Mobility and Security fra alle dine Microsoft 365 brugere, skal du se [Slå grundlæggende mobilitet og sikkerhed fra](turn-off.md).|

Live (v14)
