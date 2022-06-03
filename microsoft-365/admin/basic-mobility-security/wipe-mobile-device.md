---
title: Slet en mobilenhed i Basic Mobility and Security
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
description: Brug indbygget basic mobility og sikkerhed til at fjerne oplysninger fra tilmeldte enheder.
ms.openlocfilehash: 5ecdfc691d85b86d882cf05dd5328d41dcdfa767
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863048"
---
# <a name="wipe-a-mobile-device-in-basic-mobility-and-security"></a>Slet en mobilenhed i Basic Mobility and Security

Du kan bruge indbygget grundlæggende mobilitet og sikkerhed til Microsoft 365 til kun at fjerne organisationsoplysninger eller til at udføre en fabriksnulstilling for at slette alle oplysninger fra en mobilenhed og gendanne den til fabriksindstillingerne.

## <a name="before-you-begin"></a>Før du begynder

Mobilenheder kan gemme følsomme organisationsoplysninger og give adgang til organisationens Microsoft 365 ressourcer. Du kan hjælpe med at beskytte din organisations oplysninger ved at nulstille fabriksnulstilling eller fjerne firmadata:

- **Nulstilling af fabrik**: Sletter alle data på en brugers mobilenhed, herunder installerede programmer, billeder og personlige oplysninger. Når sletningen er fuldført, gendannes enheden til fabriksindstillingerne.

- **Fjern firmadata**: Fjerner kun organisationsdata og efterlader installerede programmer, billeder og personlige oplysninger på en brugers mobilenhed.

- **Når en enhed slettes (fabriksnulstilling eller fjern firmadata),** fjernes enheden fra listen over administrerede enheder.

- **Nulstil automatisk en enhed**: Du kan konfigurere en Basic Mobility and Security-politik, der automatisk nulstiller en enhed fra fabriksindstillingerne, når brugeren uden held forsøger at angive enhedens adgangskode et bestemt antal gange. Det gør du ved at følge trinnene i [Opret politikker for enhedssikkerhed i grundlæggende mobilitet og sikkerhed](create-device-security-policies.md).

- **Hvis du vil vide mere om brugeroplevelsen** , når du sletter sin enhed, skal du se [Hvad er brugerens og enhedens indvirkning?](#whats-the-user-and-device-impact).

## <a name="wipe-a-mobile-device"></a>Slet en mobilenhed

1. Log på Microsoft 365 Administration, og gå til [siden Mobil Enhedshåndtering](https://portal.office.com/adminportal/home?#/MifoDevices).

1. Vælg **Administrer enheder**.

1. Vælg den enhed, du vil slette.

1. Vælg **Administrer**.

1. Vælg den type fjernsletning, du vil foretage.

    - Hvis du vil foretage en komplet sletning og gendanne enheden til fabriksindstillingerne, skal du vælge **Nulstil fabrik**.
    - Hvis du vil foretage en selektiv sletning og kun slette Microsoft 365 organisationsoplysninger, skal du vælge **Fjern firmadata**.
    - Hvis du vil fjerne enheden fra din organisation, skal du vælge **Fjern enhed**.

1. Vælg **Ja** for at bekræfte.

## <a name="how-do-i-know-it-worked"></a>Hvordan gør jeg ved, det virkede?

Du kan ikke længere se mobilenheden på listen over administrerede enheder.

## <a name="why-would-you-want-to-wipe-a-device"></a>Hvorfor vil du slette en enhed?

Slet en enhed af følgende årsager:

- Mobilenheder som smartphones og tablets bliver hele tiden mere komplette. Det betyder, at det er nemmere for dine brugere at gemme følsomme virksomhedsoplysninger, f.eks. personligt id eller fortrolig kommunikation, og få adgang til dem, når de er på farten. Hvis en af disse mobilenheder mistes eller bliver stjålet, kan det forhindre, at organisationens oplysninger ender i de forkerte hænder.
- Når en bruger forlader organisationen med en personlig enhed, der er tilmeldt Basic Mobility and Security, kan du hjælpe med at forhindre, at organisationsoplysninger følger med den pågældende bruger ved at udføre en fabriksnulstilling.
- Hvis din organisation leverer mobilenheder til brugere, skal du muligvis omfordele enheder fra tid til anden. Hvis du foretager en fabriksnulstilling på en enhed, før du tildeler den til en ny bruger, hjælper det med at sikre, at alle følsomme oplysninger fra den tidligere ejer slettes.

## <a name="whats-the-user-and-device-impact"></a>Hvad er brugerens og enhedens indvirkning?

Sletningen sendes straks til mobilenheden, og enheden er markeret som ikke-kompatibel i Azure Active Directory. Selvom alle data fjernes, når en enhed nulstilles til fabriksstandarden, beskrives det i følgende tabel, hvilket indhold der fjernes for hver enhedstype, når en enhed fjernes, når du fjerner virksomhedsdata.

|Indholdseffekt|Ios|Android|
|---|---|---|
|Microsoft 365 appdata slettes, hvis enheden er beskyttet af Intune politikker for appbeskyttelse. Appsene fjernes ikke. For enheder, der ikke er beskyttet af MAM-politikker (Mobile Application Management), fjerner Outlook og OneDrive ikke cachelagrede data.<br/>**Bemærk** Hvis du vil anvende Intune Appbeskyttelse politikker, skal du have en Intune licens.|Ja|Ja|
|Politikindstillinger, der anvendes af Basic Mobility og Security på enheder, gennemtvinges ikke længere. brugere kan ændre indstillingerne.|Ja|Ja|
|Mailprofiler, der er oprettet af Basic Mobility og Security, fjernes, og cachelagrede mails på enheden slettes.|Ja|NIELSEN|

> [!NOTE]
> Firmaportal app er tilgængelig på App Store til iOS- og Store til Android-enheder.
