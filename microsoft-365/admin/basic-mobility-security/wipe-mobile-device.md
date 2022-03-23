---
title: Slet en mobilenhed i Standardmobilitet og -sikkerhed
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
description: Brug indbygget grundlæggende mobilitet og sikkerhed til at fjerne oplysninger fra tilmeldte enheder.
ms.openlocfilehash: d5f610e2a9180f1d147f68e6aabf4a7291787033
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/09/2022
ms.locfileid: "63591641"
---
# <a name="wipe-a-mobile-device-in-basic-mobility-and-security"></a>Slet en mobilenhed i Standardmobilitet og -sikkerhed

Du kan bruge indbygget grundlæggende mobilitet og sikkerhed til Microsoft 365 til kun at fjerne virksomhedsoplysninger eller til at udføre en nulstilling til fabriksindstilling for at slette alle oplysninger fra en mobilenhed og gendanne den til fabriksindstillingerne.

## <a name="before-you-begin"></a>Før du begynder

Mobilenheder kan lagre følsomme virksomhedsoplysninger og give adgang til organisationens Microsoft 365 ressourcer. For at beskytte din organisations oplysninger kan du udføre nulstilling eller Fjern virksomhedsdata fra fabriksindstillingerne:

- **Nulstil** til fabriksindstillingerne: Sletter alle data på en brugers mobilenhed, herunder installerede programmer, billeder og personlige oplysninger. Når sletningen er fuldført, gendannes enheden til fabriksindstillingerne.

- **Fjern virksomhedsdata**: Fjerner kun virksomhedsdata og efterlader installerede programmer, billeder og personlige oplysninger på en brugers mobilenhed.

- **Når en enhed slettes (nulstilling eller fjern firmadata fra** fabriksindstillingerne), fjernes enheden fra listen over administrerede enheder.
    
- **Nulstil automatisk en** enhed: Du kan konfigurere en standardpolitik for mobilitet og sikkerhedspolitik, som automatisk nulstiller en enhed til fabriksindstilling, når brugeren uden held forsøger at angive adgangskoden til enheden et bestemt antal gange. For at gøre dette skal du følge trinnene  [iOprette sikkerhedspolitikker for enheder inden for grundlæggende mobilitet og sikkerhed](create-device-security-policies.md).
    
- **Hvis du vil kende brugeroplevelsen, når** du slette enheden, skal du seHvad   [påvirker brugeren og enheden?](#whats-the-user-and-device-impact).

## <a name="wipe-a-mobile-device"></a>Slette en mobilenhed

1. Gå til  [Microsoft 365 Administration](../../admin/admin-overview/about-the-admin-center.md).

2. Skriv Administration af mobilenheder i søgefeltet, og vælg **Administration af** mobilenheder på listen over resultater.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Indstilling for administration af grundlæggende mobilitet og brugeradministration af mobilenheder.":::

3. Vælg **Administrer enheder**.

4. Vælg den enhed, du vil slette.

5. Vælg **Administrer**.

6. Vælg den type fjernsletning, du vil udføre.

    - Hvis du vil udføre en komplet sletning og gendanne enheden til fabriksindstillingerne, skal du vælge **Nulstilling til fabriksindstilling**.
    - Hvis du vil udføre en selektiv sletning og kun slette Microsoft 365 firmaoplysninger, skal du **vælge Fjern virksomhedsdata**.
    - Hvis du vil fjerne enheden fra din organisation, skal du **vælge Fjern enhed**.

7. Vælg **Ja for** at bekræfte.

## <a name="how-do-i-know-it-worked"></a>Hvordan ved jeg, det virkede?

Du kan ikke længere se mobilenheden på listen over administrerede enheder.

## <a name="why-would-you-want-to-wipe-a-device"></a>Hvorfor skulle du slette en enhed?

Slet en enhed af følgende årsager:

- Mobilenheder som smartphones og tablets bliver hele tiden mere fuldt udvalgte. Det betyder, at det er nemmere for dine brugere at gemme følsomme virksomhedsoplysninger som f.eks. personlig identifikation eller fortrolig kommunikation og få adgang til den på farten. Hvis en af disse mobilenheder mistes eller bliver stjålet, kan aftørring af enheden hjælpe med at forhindre, at din organisations oplysninger ender i de forkerte hænder.
- Når en bruger forlader organisationen med en personlig enhed, der er tilmeldt Grundlæggende mobilitet og sikkerhed, kan du hjælpe med at forhindre, at den pågældende bruger tager virksomhedsoplysninger med sig ved at udføre en nulstilling til fabriksindstillinger.
- Hvis din organisation giver brugere mobilenheder, kan det også være nødvendigt at tildele enhederne igen fra tid til anden. Hvis du udfører en nulstilling til fabriksindstillingerne på en enhed, før du tildeler den til en ny bruger, sikrer du, at følsomme oplysninger fra den tidligere ejer slettes.

## <a name="whats-the-user-and-device-impact"></a>Hvad påvirker brugeren og enheden?

Sletningen sendes straks til mobilenheden, og enheden er markeret som ikke kompatibel i Azure Active Directory. Mens alle data fjernes, når en enhed nulstilles til fabriksindstillinger, beskriver den følgende tabel, hvilket indhold der fjernes for hver enhedstype, når du fjerner virksomhedsdata fra en enhed.

|**Påvirkning af indhold**|**iOS**|**Android**|
|:-----|:-----|:-----|
|Microsoft 365 slettes alle appdata, hvis enheden er beskyttet af politikkerne for Intune App Protection. Appsene fjernes ikke. For enheder, der ikke er beskyttet af politikker for administration af mobilapps (MAM), fjerner Outlook og OneDrive ikke cachelagrede data.<br/>**Bemærk!** Hvis du vil anvende Beskyttelsespolitikker for Intune-apps, skal du have en Intune-licens.|Ja|Ja|
|Politikindstillinger, der anvendes af Standardmobilitet og Sikkerhed på enheder, håndhæves ikke længere; kan brugerne ændre indstillingerne.|Ja|Ja|
|Mailprofiler, der er oprettet ved hjælp af Grundlæggende mobilitet og sikkerhed, fjernes, og cachelagrede mails på enheden slettes.|Ja|I/T|

> [!NOTE]
> Firmaportal-appen er tilgængelig på appen Store til iOS og appen Play Store til Android-enheder.
