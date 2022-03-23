---
title: Installér Intune-firmaportal på enheder
description: Oplysninger om installation af appen firmaportal på Microsoft-administrerede skrivebordsenheder
keywords: Microsoft-administreret skrivebord, Microsoft 365, Firmaportal
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: c7edc974bfd4a4f0d2d9611c80d0996aebc3ddb7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587674"
---
# <a name="install-intune-company-portal-on-devices"></a>Installér Intune-firmaportal på enheder

Microsoft Managed Desktop kræver, at it-administratorer installerer Intune-firmaportal til deres brugere med Microsoft-administrerede desktopenheder. Fordelene for din organisation omfatter:

- Brugerne har ét sted at gennemse og installere tilgængelige programmer.
- It-administratorer kan organisere programmer efter kategorier for deres brugere.  
- Nogle programmer (f.eks. Microsoft Project og Microsoft Visio) kræver, Firmaportal installerer med Microsoft Managed Desktop.
- It-administratorer kan tilpasse Firmaportal til deres organisation. Tilpasninger omfatter brand imaging, tilføjelse i lokale supportkontakter og meget mere. Du kan finde flere oplysninger [under Sådan konfigureres Microsoft Intune Firmaportal appen](/intune/company-portal-app).

Denne artikel dokumenterer processen for udrulning af Intune-firmaportal dine Microsoft Managed Desktop-brugere. Den overordnede proces ser sådan ud:

1. [Køb Firmaportal fra Microsoft Store til Virksomheder og synkroniser med Intune](#step-1-purchase-company-portal-from-microsoft-store-for-business-and-sync-with-intune).
2. [Tildel Firmaportal til dine brugere](#step-2-assign-company-portal-to-your-users).
3. [Kommunikere ændringer til dine brugere.](#step-3-communicate-change-to-your-users)

## <a name="step-1-purchase-company-portal-from-microsoft-store-for-business-and-sync-with-intune"></a>Trin 1: Køb Firmaportal fra Microsoft Store til Virksomheder og synkroniser med Intune

Du kan finde oplysninger om, hvordan du køber appsene og synkroniserer med Intune [under Microsoft Store til Virksomheder apps](deploy-apps.md#msfb-apps) i *Installér apps på Microsoft Managed Desktop-enheder*.

Denne artikel indeholder oplysninger om, hvordan du:

- Køb Firmaportal fra Microsoft Store til Virksomheder.
- Gennemtving synkronisering mellem Intune og Microsoft Store til Virksomheder.
- Bekræft aktiv synkronisering mellem Intune og Microsoft Store til Virksomheder.

## <a name="step-2-assign-company-portal-to-your-users"></a>Trin 2: Tildel Firmaportal til dine brugere

Efter din tilmelding til Microsoft Managed Desktop installerer vi automatisk Firmaportal til din lejer og installerer appen på Microsoft-administrerede desktopenheder i organisationen.

## <a name="step-3-communicate-change-to-your-users"></a>Trin 3: Kommunikere ændringen til dine brugere

Som it-administrator for din organisation er det vigtigt at give brugerne besked om, hvordan de Firmaportal i organisationen. Microsoft-administreret skrivebord anbefaler:

- Trin til installation af programmer fra Firmaportal. Du kan finde flere oplysninger [under Installere og dele apps på din enhed](/intune-user-help/install-apps-cpapp-windows).
- Sådan sendes anmodninger til it-administratorer for programmer, der ikke er tilgængelige i øjeblikket. Få mere at vide under [Anmod om en app til arbejde eller skole](/intune-user-help/install-apps-cpapp-windows#request-an-app-for-work-or-school).  

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Trin til at komme i gang med Microsoft-administreret skrivebord

1. Få adgang [til administrationsportalen](access-admin-portal.md).
1. [Tilføj og bekræft administratorkontakter i administrationsportalen](add-admin-contacts.md).
1. [Juster indstillinger efter tilmelding](conditional-access.md).
1. Installere og tildele Intune-firmaportal (denne artikel).
1. [Tildel licenser](assign-licenses.md).
1. [Installér apps](deploy-apps.md).
1. [Klargør enheder](prepare-devices.md)
1. Konfigurer første [kørselsoplevelse med Autopilot og Statussiden For tilmelding](esp-first-run.md).
1. [Aktivér brugersupportfunktioner](enable-support.md).
1. [Gør dine brugere klar til at bruge enheder](get-started-devices.md).
1. [Kom i gang med appstyring](get-started-app-control.md).
