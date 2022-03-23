---
title: Tildel enheder til en installationsgruppe
description: Sådan angiver du, hvilken installationsgruppe du vil have enhederne til at være i
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 6f3d2c79c23a37e1e1a965f9a3f416052a49fa76
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/31/2022
ms.locfileid: "63593300"
---
# <a name="assign-devices-to-a-deployment-group"></a>Tildel enheder til en installationsgruppe

Microsoft Managed Desktop vil tildele enheder til de forskellige installationsgrupper. Du kan angive eller ændre den gruppe, som en enhed er tildelt til, ved hjælp af administrationsportalen. Du ændrer tildelingen, når en enhed er registreret, eller når en bruger har tilmeldt sig.

> [!IMPORTANT]
> Hvis du ændrer tildelingen, anvendes de politikker, der er specifikke for den pågældende gruppe, på enheden. Ændringen kan installere den nyeste version af Windows 10 (herunder nye funktioner eller kvalitetsopdateringer). Det er bedst kun at flytte nogle få enheder i starten og derefter kontrollere den resulterende brugeroplevelse. Vær opmærksom på, at visse opdateringer genstarter enheden. Kontrollér, at du har valgt de rigtige enheder at tildele. Det kan tage op til 24 timer, før opgaven træder i kraft.

**Sådan tildeles enheder til en installationsgruppe:**

Hvis du vil flytte separate enheder til forskellige grupper, skal du gentage disse trin for hver gruppe.

1. I Microsoft Endpoint Manager du vælge **Enheder** i venstre rude.
1. I sektionen **Microsoft Managed Desktop** skal du vælge **Enheder**.
1. Vælg de enheder, du vil tildele. Alle valgte enheder tildeles til den gruppe, du angiver.
1. Vælg **Enhedshandlinger** i menuen.
1. Vælg **Tildel enhed til gruppe**. Der åbnes et pop op-vindue.
1. Brug rullemenuen til at vælge den gruppe, enheder skal flyttes til, og vælg derefter **Gem**. Den **gruppe, der er tildelt** efter kolonne, ændres til **Afventer**.

Når tildelingen er **fuldført, ændres** Gruppe tildelt efter kolonne til **Administrator** (angivet, at du har foretaget ændringen), og kolonnen  Gruppe viser den nye gruppetildeling.

> [!NOTE]
> Du kan ikke flytte enheder til andre grupper, hvis de er i registreringstilstanden "fejl" eller "afventer".
>
>Hvis en enhed ikke er blevet fjernet korrekt, kan den vise statussen "klar". Hvis du flytter sådan en enhed, er det muligt, at flytningen ikke fuldføres. Hvis du ikke kan se,  at Gruppe tildelt efter kolonne ændres til Afventer i trin 5, skal du kontrollere, at enheden er tilgængelig ved at søge efter den i Intune. Få mere at vide under [Se enhedsdetaljer i Intune](/mem/intune/remote-actions/device-inventory).
