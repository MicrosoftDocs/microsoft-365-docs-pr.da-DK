---
title: Microsoft OneDrive
description: Sådan konfigurerer Microsoft-OneDrive til tilmeldte enheder
keywords: Microsoft Managed Desktop, Microsoft 365, service, dokumentation, apps, line of business-apps, LOB-apps
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 89d1851b3a2a7358a36d6a1ddd6f7db24dd2e1cf
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/04/2022
ms.locfileid: "63591957"
---
# <a name="microsoft-onedrive"></a>Microsoft OneDrive

Microsoft Managed Desktop bruger OneDrive for Business [som](/onedrive/plan-onedrive-enterprise) en skylagertjeneste for alle Microsoft-administrerede computerenheder. Det sikrer, at enhederne er så tilstandsløse som muligt. Brugerne vil kunne finde deres filer, uanset hvilken enhed de logger på. Hvis du f.eks. erstatter en Microsoft-administreret skrivebordsenhed med en ny, synkroniseres filerne automatisk med den nye enhed.

Vi konfigurerer automatisk disse indstillinger som standard på Microsoft-administrerede enheder:

| Funktion | Beskrivelse |
| ------ | ------ |
| Automatisk konfiguration | OneDrive er uovervåget konfigureret med brugerkontoen. Den logger automatisk på den brugerkonto, der blev brugt til at logge på med, uden brugerinteraktion, Windows. Få mere at vide under [Konfigurer automatisk brugerkonti – OneDrive](/onedrive/use-silent-account-configuration) |
| Files-On-Demand | Funktionen Filer efter behov giver brugerne mulighed for at få adgang til filer fra deres skylagerplads OneDrive at skulle bruge diskplads unødvendigt. Få mere at vide under [Spar diskplads OneDrive Filer efter behov Windows 10](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e). |
| Flyt kendte mapper | Funktionen Til flytning af kendte mapper er automatisk aktiveret til at sikkerhedskopiere brugernes data i skyen, hvilket giver dem adgang til deres filer fra enhver enhed. Du kan finde flere [oplysninger i Sikkerhedskopiere mapperne Dokumenter, Billeder og Skrivebord OneDrive](https://support.microsoft.com/office/back-up-your-documents-pictures-and-desktop-folders-with-onedrive-d61a7930-a6fb-4b95-b28a-6552e77c3057). <p> Brugere kan ikke deaktivere funktionen Til flytning af kendte mapper eller ændre placeringen af kendte mapper for at sikre en ensartet oplevelse på tværs af Microsoft-administrerede skrivebordsenheder.</p>|

## <a name="user-experience"></a>Brugeroplevelse

Når Microsoft-brugere af administrerede skriveborde modtager en ny enhed, gennemgår de en første kørselsoplevelse ved at angive deres Azure-legitimationsoplysninger, mens de konfigurerer enheden. Når denne proces er fuldført, kan de få adgang til deres skrivebord og OneDrive oplevelse.

1. Systemet fortæller brugerne, at OneDrive er konfigureret, og at de automatisk er logget på OneDrive.

:::image type="content" source="media/onedrive-sync.png" alt-text="Læsning af meddelelser, du nu synkroniserer, OneDrive og du kan redigere filer i OneDrive. Klik her for at få vist dine filer.":::

2. Systemet fortæller brugerne, at OneDrive mappe flyt er konfigureret for dem.

:::image type="content" source="media/onedrive-folders.png" alt-text="Læsning af meddelelser Din it-afdeling sikkerhedskopierede dine vigtige mapper. Mapperne er nu sikkerhedskopieret til OneDrive og tilgængelige fra andre enheder.":::

3. Hvis du vil forhindre dublerede ikoner på skrivebordet, når enheder nulstilles eller genimages, fjerner systemet automatisk Microsoft Edge og Microsoft Teams ikoner fra OneDrive-synkronisering. Disse oplysninger vises i Stifinder.

:::image type="content" source="media/onedrive-teams.png" alt-text="Stifinder viser Teams- og Edge-lister med fjernede afkrydsningsfelter og lader teksten være udeladt fra synkronisering.":::

## <a name="onedrive-sync-restrictions"></a>OneDrive-synkronisering begrænsninger

Hvis du har brug for at begrænse OneDrive-synkronisering, anbefaler vi, at du styrer adgangen med Azure Active Directory politik for betinget adgang. Få mere at vide under [Aktivér understøttelse af betinget adgang i OneDrive-synkronisering appen](/onedrive/enable-conditional-access).

Hvis du ikke kan bruge en politik for betinget adgang til Azure AD i din organisation, skal din IT-administrator følge disse trin:

1. Hvis du ikke allerede kender det, skal du slå dit lejer-id op som beskrevet i [Find dit Microsoft 365-lejer-id](/onedrive/find-your-office-365-tenant-id).
1. Log på OneDrive Administration.
1. Vælg Synkroniser i venstre **rude**.
1. Markér **afkrydsningsfeltet Tillad kun synkronisering** på pc'er, der er forbundet med bestemte domæner, og føj derefter lejer-id'et til listen over domæner. Du kan få mere at vide [under Tillad kun synkronisering på computere, der er forbundet til bestemte domæner](/onedrive/allow-syncing-only-on-specific-domains).

> [!NOTE]
> Denne vejledning gælder kun for lejere i Microsoft Managed Desktop. Der er andre indstillinger i brug, som ikke er nævnt i denne artikel.
