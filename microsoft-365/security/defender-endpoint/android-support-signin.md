---
title: Fejlfinding af problemer på Microsoft Defender for Endpoint på Android
description: Fejlfinding af problemer med Microsoft Defender for Endpoint på Android
keywords: microsoft, defender, Microsoft Defender for Endpoint, mde, android, cloud, connectivity, communication
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 574e02c837ce1f2e3639ed562ed52bacc0e67629
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472215"
---
# <a name="troubleshooting-issues-on-microsoft-defender-for-endpoint-on-android"></a>Fejlfinding af problemer Microsoft Defender for Endpoint på Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du gerne Microsoft Defender for Endpoint? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Når du onboarder en enhed, får du muligvis vist problemer med at logge på, når appen er installeret.

Under onboarding kan der opstå logonproblemer, når appen er installeret på din enhed.

Denne artikel indeholder løsninger til at løse problemerne med at logge på.

## <a name="sign-in-failed---unexpected-error"></a>Logon mislykkedes – uventet fejl

**Logon mislykkedes: Uventet** *fejl, prøv senere*

:::image type="content" source="images/f9c3bad127d636c1f150d79814f35d4c.png" alt-text="Fejl ved logon mislykkedes Uventet fejl på logonsiden på Microsoft Defender 365-portalen." lightbox="images/f9c3bad127d636c1f150d79814f35d4c.png":::

**Meddelelse:**

Uventet fejl, prøv senere

**Årsag:**

Du har en ældre version af "Microsoft Authenticator"-appen installeret på din enhed.

**Løsning:**

Installér den nyeste version [Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator) Google Play Store og prøv igen.

## <a name="sign-in-failed---invalid-license"></a>Logon mislykkedes – ugyldig licens

**Logon mislykkedes: Ugyldig** *licens. Kontakt administratoren*

:::image type="content" source="images/920e433f440fa1d3d298e6a2a43d4811.png" alt-text="Kontaktoplysningerne fra Directive på logonsiden på Microsoft Defender 365-portalen" lightbox="images/920e433f440fa1d3d298e6a2a43d4811.png":::

**Meddelelse:** *Ugyldig licens. Kontakt administratoren*

**Årsag:**

Du har ikke fået Microsoft 365 tildelt, eller din organisation har ikke en licens til at Microsoft 365 Enterprise abonnement.

**Løsning:**

Kontakt administratoren for at få hjælp.

## <a name="report-unsafe-site"></a>Rapportér usikkert websted

Phishingwebsteder udgives som pålidelige websteder for at få dine personlige eller økonomiske oplysninger. Gå til [siden Giv feedback om netværksbeskyttelse](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) , hvis du vil rapportere et websted, der kunne være et phishingwebsted.

## <a name="phishing-pages-arent-blocked-on-some-oem-devices"></a>Phishingsider blokeres ikke på visse OEM-enheder

**Gælder for:** Kun specifikke OEMs

- **Xiami**

Phishing og skadelige webtrusler, der registreres af Defender til Endpoint til Android, blokeres ikke på visse Cybermi-enheder. Følgende funktioner virker ikke på disse enheder.

:::image type="content" source="images/0c04975c74746a5cdb085e1d9386e713.png" alt-text="En websteds ikke-meddelelse" lightbox="images/0c04975c74746a5cdb085e1d9386e713.png":::

**Årsag:**

Standardenheder omfatter en ny tilladelsesmodel. Dette forhindrer Defender for Endpoint til Android i at vise pop op-vinduer, mens den kører i baggrunden.

Tilladelse for trådløse enheder: "Vis pop op-vinduer, mens de kører i baggrunden."

:::image type="content" source="images/6e48e7b29daf50afddcc6c8c7d59fd64.png" alt-text="Pop op-indstillingsruden i Microsoft Defender 365-portalen" lightbox="images/6e48e7b29daf50afddcc6c8c7d59fd64.png":::

**Løsning:**

Aktivér den nødvendige tilladelse påXiami-enheder.

- Få vist pop op-vinduer, mens du kører i baggrunden.

## <a name="unable-to-allow-permission-for-permanent-protection-during-onboarding-on-some-oem-devices"></a>Det er ikke muligt at tillade tilladelse til "Permanent beskyttelse" under onboarding på visse OEM-enheder

**Gælder for:** Kun bestemte OEM-enheder.

- **Smartphone med Android 11**

Defender-appen beder om tilladelse til batterioptimering/permanent beskyttelse på enheder som en del af app-onboarding, og hvis du vælger Tillad, returneres en fejl, som tilladelsen ikke kunne indstilles til. Det påvirker kun den seneste tilladelse kaldet "Permanent beskyttelse". 

**Årsag:**

Smartphone har ændret tilladelserne til batterioptimering i Android 11. Defender til Slutpunkt har ikke tilladelse til at konfigurere denne indstilling for at ignorere batterioptimeringer.

**Løsning:**

Vi arbejder sammen med OEM for at finde en løsning, der gør det muligt at aktivere denne tilladelse fra appens onboardingskærm. Vi opdaterer dokumentationen, når dette er løst.
Brugerne kan følge disse trin for at aktivere de samme tilladelser fra enhedsindstillingerne: 

1. Gå til **Indstillinger** på din enhed.

2. Søg efter, og vælg **Batterioptimering**.

   :::image type="content" source="images/search-battery-optimisation.png" alt-text="Den side, hvor du kan søge og vælge Batteristrøm" lightbox="images/search-battery-optimisation.png":::

3. Vælg **Batterioptimering i Særlig** **appadgang**.

   :::image type="content" source="images/special-app-access.png" alt-text="Ruden Særlig appadgang, hvorfra du kan vælge Batteristrøm" lightbox="images/special-app-access.png":::

4. Skift rullemenuen for at få **vist Alle apps**.

   :::image type="content" source="images/show-all-apps-2.png" alt-text="Rullemenuen, hvorfra du kan ændre værdien til Alle apps under ruden Batterimål" lightbox="images/show-all-apps-2.png":::

   :::image type="content" source="images/show-all-apps-1.png" alt-text="Rullemenuen, der viser indstillingen Alle apps under ruden Batteristrøm" lightbox="images/show-all-apps-1.png":::

5. Find "Microsoft Defender for Endpoint", og **vælg Optimer ikke**.

   :::image type="content" source="images/select-dont-optimise.png" alt-text="Den side, der aktiverer placeringen af indstillingen Microsoft Defender for Endpoint og valget af Optimer ikke" lightbox="images/select-dont-optimise.png":::

Gå tilbage til Microsoft Defender for Endpoint-onboardingskærmen, **vælg Tillad**, og du bliver omdirigeret til dashboardskærmen.

## <a name="send-in-app-feedback"></a>Send feedback i appen

Hvis en bruger oplever et problem, som ikke allerede er adresseret i ovenstående afsnit eller ikke kan løse ved hjælp af de angivne trin, kan brugeren give **feedback** i appen sammen med diagnostiske **data**. Vores team kan derefter undersøge logfilerne for at finde den rette løsning. Brugerne kan følge disse trin for at gøre det samme:

1.  Åbn **MDE-programmet** på din enhed, og klik **på profilikonet** i øverste venstre hjørne.

    :::image type="content" source="images/select-profile-icon-1.jpg" alt-text="Profilikonet i Microsoft Defender for Endpoint portal" lightbox="images/select-profile-icon-1.jpg":::

2.  Vælg "Hjælp & feedback".

    :::image type="content" source="images/selecthelpandfeedback2.png" alt-text="Indstillingen hjælp & feedback, der kan vælges i Microsoft Defender for Endpoint-portalen" lightbox="images/selecthelpandfeedback2.png":::

3.  Vælg "Send feedback til Microsoft".

    :::image type="content" alt-text="Vælg Send feedback til Microsoft" source="images/send-feedback-to-microsoft-3.jpg":::

4.  Vælg mellem de angivne indstillinger. Hvis du vil rapportere et problem, skal du vælge "Jeg vil rapportere et problem".

    :::image type="content" source="images/report-issue-4.jpg" alt-text="Indstillingen Jeg vil rapportere et problem" lightbox="images/report-issue-4.jpg":::

5.  Angiv oplysninger om det problem, du oplever, og markér "Send diagnostiske data". Vi anbefaler, at du kontrollerer "Medtag din mailadresse", så teamet kan vende tilbage til dig med en løsning eller en opfølgning.

    :::image type="content" source="images/finalsubmit5.png" alt-text="Den rude, hvor du kan tilføje detaljer og vedhæfte diagnostiske data" lightbox="images/finalsubmit5.png":::

6.  Klik på "Send" for at sende feedbacken.
