---
title: Partnerregistrering
description: Partnere kan registrere enheder, der skal administreres af Microsoft Managed Desktop
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: af1e187c77acde257fa3458709fae50616cf810d
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63704835"
---
# <a name="partner-registration"></a>Partnerregistrering

I denne artikel beskrives trinnene for partnere til registrering af enheder. Processen for selv at registrere enheder er dokumenteret i [Manuel registrering](manual-registration.md).

## <a name="prepare-for-registration"></a>Forbered dig til registrering

Før du afslutter tilmeldingen for en kunde, skal du først etablere en relation til kunden i [Partnercenter](https://partner.microsoft.com/dashboard). Du kan finde flere oplysninger om processen i [dokumentationen om samtykke](/windows/deployment/windows-autopilot/registration-auth#csp-authorization). Enhver CSP-partner kan tilføje enheder på vegne af en hvilken som helst kunde, så længe kunden giver sit samtykke. Du kan også få mere at vide om partnerrelationer og Autopilot-tilladelser i [Hjælp til Partnercenter](/partner-center/customers_revoke_admin_privileges#windows-autopilot).

> [!NOTE]
> Denne dokumentation er kun til partnere og OEMs. Processen for selvregistrering er dokumenteret i [Manuel registrering](manual-registration.md).

## <a name="register-devices-using-the-partner-center"></a>Registrer enheder ved hjælp af Partnercenter

Når du har etableret relationen til dine kunder, kan du bruge Partnercenter til at føje enheder til Autopilot for nogen af kunderne.

**Sådan registrerer du enheder ved hjælp af Partnercenter:**

1. Gå til [Partnercenter](https://partner.microsoft.com/dashboard).
2. Vælg **Kunder** fra menuen Partnercenter, og vælg derefter den kunde, hvis enheder du vil administrere.
3. Vælg Enheder på kundens **detaljeside**.
4. Under **Anvend profiler på** enheder skal du vælge **Tilføj enheder**.
5. Angiv det relevante Gruppemærke for den enhedsprofil, du har valgt (som vist i følgende tabel), og vælg derefter **Gennemse** for at uploade kundens liste (i .csv-filformat) til Partnercenter.

| [Enhedsprofil](../service-description/profiles.md) | Gruppemærke |
| ----- | -----|
| Følsomme data | **Microsoft365ManagedSensitiveData\_** |
| Superbruger | **Microsoft365ManagedPowerUser\_** |
| Standard | **Microsoft365ManagedStandard\_** |

> [!IMPORTANT]
> Gruppenavnet skal svare nøjagtigt til dem, der er angivet i tabellen, herunder store bogstaver og specialtegn. Dette gør det muligt for de nyligt registrerede enheder at blive tildelt Microsoft Managed Desktop Autopilot-profilen.

>[!NOTE]
> Du burde have modtaget denne .csv med købet af enheden. Hvis du ikke har modtaget en .csv, kan du oprette en selv ved at følge trinnene i Føj enheder til [Windows Autopilot](/windows/deployment/windows-autopilot/add-devices#collecting-the-hardware-id-from-existing-devices-using-powershell). Krav: <ul><li>Ekstra kolonner understøttes ikke.</li> <li>Tilbud understøttes ikke.</li> <li>Det er kun tekstfiler i ANSI-format, der kan bruges (ikke Unicode).</li> <li>Der er store og små bogstaver i sidehoveder.</li></ul> Når du redigerer filen Excel filen og gemmer den som en CSV-fil, genereres der ikke en brugbar fil på grund af disse krav. Sørg for, at du bevarer eventuelle foranstillede nuller i enhedens serienumre. Partnere skal bruge [Get-WindowsAutoPilotInfo til at registrere](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) enheder til Microsoft Managed Desktop-enheder i Partnercenter.

Hvis du modtager en fejlmeddelelse, når du forsøger at overføre .csv, skal du kontrollere filformatet for filen. Sørg for, at kolonnerækkefølgen svarer til det, der er beskrevet [i Brug Windows Autopilot-profiler på nye enheder til at tilpasse en kundes out of box-oplevelse](/partner-center/autopilot#add-devices-to-a-customers-account). Du kan også bruge eksempelfilen .csv fra linket ud for Tilføj **enheder for at** oprette en liste over enheder.

Du kan finde flere oplysninger om Autopilot i Partnerscenarier [under Føj enheder til en kundes konto](/partner-center/autopilot#add-devices-to-a-customers-account).

## <a name="register-devices-by-using-the-oem-api"></a>Registrer enheder ved hjælp af OEM API

Før du afslutter registreringen for en kunde, skal du først etablere en relation til kunden. Du skal have et entydigt link, du kan give til dine respektive kunder. Se Sådan [etablerer du OEM-relation](/windows/deployment/windows-autopilot/registration-auth#oem-authorization).

Når du har etableret relationen, kan du begynde at registrere enheder for kunder ved hjælp af det relevante gruppemærke for hver enhedsprofil, de har valgt:

| Enhedsprofil | Gruppemærke |
| ----- | ----- |
| Følsomme data | **Microsoft365ManagedSensitiveData\_** |
| Superbruger | **Microsoft365ManagedPowerUser\_** |
| Standard | **Microsoft365ManagedStandard\_** |

> [!IMPORTANT]
> Gruppemærkerne skal svare nøjagtigt til dem, der er angivet i tabellen, herunder store bogstaver og specialtegn. Dette gør det muligt for de nyligt registrerede enheder at blive tildelt Microsoft Managed Desktop Autopilot-profilen.
