---
title: Fjern en tidligere medarbejder – Oversigt
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
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- m365solution-removeemployee
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
description: Følg trinnene i denne løsning for at fjerne en tidligere medarbejder Microsoft 365 og sikre organisationens data.
ms.openlocfilehash: 799a946c85da94fcc3d9e53a4015697d124192ce
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599704"
---
# <a name="overview-remove-a-former-employee-and-secure-data"></a>Oversigt: Fjern en tidligere medarbejder og sikre data

Et spørgsmål, vi ofte får, er: "Hvad skal jeg gøre for at sikre data og beskytte adgangen, når en medarbejder forlader min organisation?" I denne artikelserie forklares det, hvordan du blokerer adgangen til Microsoft 365, så disse brugere ikke kan logge på Microsoft 365, de trin, du skal følge for at sikre organisationsdata, og hvordan du giver andre medarbejdere adgang til mail og OneDrive data.

> [!TIP]
> Hvis du har brug for hjælp til trinnene i dette emne, kan du overveje at [arbejde med en Microsoft Small Business-specialspecialist](https://go.microsoft.com/fwlink/?linkid=2186871). Med Business Assist får du og dine medarbejdere døgnet rundt adgang til små virksomhedsspecialister, efterhånden som du vokser din virksomhed, fra onboarding til daglig brug.

## <a name="before-you-begin"></a>Før du begynder

Du skal være global administrator for at fuldføre trinnene i denne løsning.

For at fuldføre trinnene i denne serie skal du bruge disse Microsoft 365 funktioner.

|Produkt eller komponent|Funktionalitet eller funktion|
|---|---|
|Microsoft 365 Administration|Konvertér postkasse, videreslet mail, tilbagekald adgang, fjern bruger |
|Exchange Administration|Bloker bruger, bloker adgang til mail, slet enhed |
|OneDrive og SharePoint |Give adgang til andre brugere |
|Outlook|Importér pst-filer, tilføj postkasse |
|Active Directory|Fjern brugere i hybridmiljøer |


## <a name="solution-remove-a-former-employee"></a>Løsning: Fjern en tidligere medarbejder

> [!IMPORTANT]
> Selvom vi har nummereret trinnene i denne løsning, og du ikke behøver at fuldføre løsningen med den nøjagtige rækkefølge, anbefaler vi, at du udfører trinnene på denne måde.

:::image type="content" source="../../media/delete-user-account.png" alt-text="Skærmbillede: Trin til at fjerne en tidligere medarbejder fra organisationen":::

<br>

****

|Trin|Hvorfor gøre dette|
|---|---|
|[Trin 1 – Undgå, at en tidligere medarbejder logger på og blokerer adgangen til Microsoft 365-tjenester](remove-former-employee-step-1.md)|Dette blokerer din tidligere medarbejder fra at logge på Microsoft 365 og forhindrer personen i at få adgang til Microsoft 365 tjenester.|
|[Trin 2 – Gem indholdet af en tidligere medarbejders postkasse](remove-former-employee-step-2.md)|Dette er nyttigt for den person, der skal overtage medarbejderens arbejde, eller hvis der er procesførelse.|
|[Trin 3: Slette og blokere en tidligere medarbejders mobilenhed](remove-former-employee-step-3.md)|Fjerner dine virksomhedsdata fra telefonen eller tabletten.|
|[Trin 4 – Videresende en tidligere medarbejders mail til en anden medarbejder eller konvertere til en delt postkasse](remove-former-employee-step-4.md)|Det gør det muligt at holde den tidligere medarbejders mailadresse aktiv. Hvis du har kunder eller partnere, der stadig sender mails til den tidligere medarbejders adresse, får de på denne måde kontakt til den person, der overtager arbejdet.|
|[Trin 5 – Giv en anden medarbejder adgang til OneDrive og Outlook data](remove-former-employee-step-5.md)|Hvis du kun fjerner en brugers licens, men ikke sletter kontoen, vil du fortsat have adgang til indholdet i brugerens OneDrive, selv efter 30 dage. <p> Før du sletter kontoen, skal du give adgang til brugerens OneDrive og Outlook en anden bruger. Når du sletter en medarbejders konto, bevares indholdet i medarbejderens OneDrive Outlook i **30** dage. I dette 30 dage kan du dog gendanne brugerens konto og få adgang til indholdet. Hvis du gendanner brugerens konto, vil OneDrive og Outlook være tilgængeligt for dig selv efter 30 dage.| 
|[Trin 6 – Fjern og slet licensen Microsoft 365 en tidligere medarbejder](remove-former-employee-step-6.md)|Når du fjerner en licens, kan du tildele den til en anden. Eller du kan slette licensen, så du ikke betaler for den, før du ansætter en anden person. <p> Når du fjerner eller sletter en licens, bevares brugerens gamle mail, kontakter og kalender i **30** dage, og de slettes derefter permanent. Hvis du fjerner eller sletter en licens, men ikke sletter kontoen, vil du fortsat have adgang til indholdet i brugerens OneDrive, selv efter 30 dage.|
|[Trin 7 – Slet en tidligere medarbejders brugerkonto](remove-former-employee-step-7.md)|Dette fjerner kontoen fra Administration. Holder tingene rene.|

 ## <a name="watch-delete-a-user"></a>Se: Slet en bruger

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR?autoplay=false]

Når en medarbejder forlader virksomheden, skal du fjerne vedkommende fra Microsoft 365 til virksomheder. Før du gør dette, skal du blokere brugeren fra at få adgang til virksomhedens filer, bevare de dokumenter, vedkommende har oprettet, og udføre flere andre administratoropgaver, der er knyttet til fjernelse af en bruger.

1. Vælg Brugere i Administration, **og** vælg **Aktive brugere**.
1. Vælg den bruger, du vil fjerne, og vælg derefter **Slet bruger**.
1. Markér afkrydsningsfeltet for at fjerne licensen, og markér afkrydsningsfeltet for at fjerne deres mailaliasser.
1. Markér afkrydsningsfeltet for at give en anden bruger adgang til den tidligere medarbejders mail, og vælg **Vælg en bruger, og angiv mailindstillinger**.
1. Hvis du vil fjerne tilknyttede mailaliasser, **skal du vælge X** ud for deres aliasser.
1. Gennemse oplysningerne om den delte postkasse, og vælg **Udfør**.
1. Bekræft, at dine indstillinger er angivet korrekt, og vælg **Tildel og konvertér**.
1. Gennemse resultaterne, og vælg **Luk**.

Når du har fjernet en bruger, har du op til 30 dage til at gendanne brugerens konto.
## <a name="related-content"></a>Relateret indhold

[Gendan en bruger](restore-user.md) (artikel)\
[Føj en ny medarbejder til Microsoft 365](add-new-employee.md) (artikel)\
[Tildel licenser til brugere](../manage/assign-licenses-to-users.md) (artikel)\
[Fjern tildeling af licenser fra brugere](../manage/remove-licenses-from-users.md) (artikel)
