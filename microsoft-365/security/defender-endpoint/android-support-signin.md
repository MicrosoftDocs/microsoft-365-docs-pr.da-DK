---
title: Foretag fejlfinding af problemer på Microsoft Defender for Endpoint på Android
description: Foretag fejlfinding af problemer med Microsoft Defender for Endpoint på Android
keywords: microsoft, defender, Microsoft Defender for Endpoint, mde, android, cloud, forbindelse, kommunikation
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
ms.openlocfilehash: 0a6f53b0723d7f3e9b4761aa83238e618d947e55
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64783419"
---
# <a name="troubleshooting-issues-on-microsoft-defender-for-endpoint-on-android"></a>Fejlfinding af problemer på Microsoft Defender for Endpoint på Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft Defender for Endpoint plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender for Endpoint? [Tilmeld dig en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Når du onboarder en enhed, kan du se logonproblemer, når appen er installeret.

Under onboarding kan der opstå logonproblemer, når appen er installeret på din enhed.

Denne artikel indeholder løsninger, der kan hjælpe med at løse logonproblemer.

## <a name="sign-in-failed---unexpected-error"></a>Logon mislykkedes - uventet fejl

**Logon mislykkedes:** *Uventet fejl. Prøv senere*

:::image type="content" source="images/f9c3bad127d636c1f150d79814f35d4c.png" alt-text="Der opstod en mislykket fejl under logon. Der opstod en uventet fejl på logonsiden på Microsoft Defender 365-portalen." lightbox="images/f9c3bad127d636c1f150d79814f35d4c.png":::

**Besked:**

Uventet fejl. Prøv senere

**Forårsage:**

Du har installeret en ældre version af appen "Microsoft Authenticator" på enheden.

**Løsning:**

Installér den nyeste version og af [Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator) fra Google Play Store, og prøv igen.

## <a name="sign-in-failed---invalid-license"></a>Logon mislykkedes - ugyldig licens

**Logon mislykkedes:** *Ugyldig licens. Kontakt administratoren*

:::image type="content" source="images/920e433f440fa1d3d298e6a2a43d4811.png" alt-text="Kontaktoplysninger om direktivet på logonsiden på Microsoft Defender 365-portalen" lightbox="images/920e433f440fa1d3d298e6a2a43d4811.png":::

**Meddelelse:** *Ugyldig licens. Kontakt administratoren*

**Forårsage:**

Du har ikke tildelt Microsoft 365 licens, eller din organisation har ikke en licens til Microsoft 365 Enterprise abonnement.

**Løsning:**

Kontakt administratoren for at få hjælp.

## <a name="report-unsafe-site"></a>Rapportér usikkert websted

Phishingwebsteder repræsenterer pålidelige websteder med det formål at indhente dine personlige eller økonomiske oplysninger. Besøg siden [Giv feedback om netværksbeskyttelse](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) , hvis du vil rapportere et websted, der kan være et phishingwebsted.

## <a name="phishing-pages-arent-blocked-on-some-oem-devices"></a>Phishingsider blokeres ikke på nogle OEM-enheder

**Gælder for:** Kun specifikke OEM-producenter

- **Xiaomi**

Phishing og skadelige webtrusler, der registreres af Defender for Endpoint til Android, blokeres ikke på nogle Xiaomi-enheder. Følgende funktionalitet fungerer ikke på disse enheder.

:::image type="content" source="images/0c04975c74746a5cdb085e1d9386e713.png" alt-text="En meddelelse om usikkert websted" lightbox="images/0c04975c74746a5cdb085e1d9386e713.png":::

**Forårsage:**

Xiaomi-enheder indeholder en ny tilladelsesmodel. Dette forhindrer, at Der vises pop op-vinduer i Defender for Endpoint til Android, mens det kører i baggrunden.

Tilladelse til Xiaomi-enheder: "Vis pop op-vinduer, mens du kører i baggrunden".

:::image type="content" source="images/6e48e7b29daf50afddcc6c8c7d59fd64.png" alt-text="Ruden med pop op-indstillinger på Microsoft Defender 365-portalen" lightbox="images/6e48e7b29daf50afddcc6c8c7d59fd64.png":::

**Løsning:**

Aktivér den nødvendige tilladelse på Xiaomi-enheder.

- Vis pop op-vinduer, mens du kører i baggrunden.

## <a name="unable-to-allow-permission-for-permanent-protection-during-onboarding-on-some-oem-devices"></a>Det var ikke muligt at tillade tilladelse til "permanent beskyttelse" under onboarding på nogle OEM-enheder

**Gælder for:** Kun bestemte OEM-enheder.

- **Xiaomi med Android 11**

Defender App beder om tilladelse til batterioptimering/permanent beskyttelse på enheder som en del af onboarding af apps, og hvis du vælger **Tillad** , returneres der en fejl om, at tilladelsen ikke kunne angives. Den påvirker kun den sidste tilladelse med navnet "Permanent beskyttelse". 

**Forårsage:**

Xiaomi ændrede tilladelserne til batterioptimering i Android 11. Defender for Endpoint har ikke tilladelse til at konfigurere denne indstilling til at ignorere batterioptimering.

**Løsning:**

Vi arbejder sammen med OEM for at finde en løsning, der aktiverer denne tilladelse fra appens onboardingskærm. Vi opdaterer dokumentationen, når dette er løst.
Brugerne kan følge disse trin for at aktivere de samme tilladelser fra enhedsindstillingerne: 

1. Gå til **Indstillinger** på din enhed.

2. Søg efter og vælg **Batterioptimering**.

   :::image type="content" source="images/search-battery-optimisation.png" alt-text="Den side, hvor du kan søge efter og vælge Batterioptimering" lightbox="images/search-battery-optimisation.png":::

3. I **Speciel appadgang** skal du vælge **Batterioptimering**.

   :::image type="content" source="images/special-app-access.png" alt-text="Ruden Speciel appadgang, hvorfra du kan vælge Batterioptimering" lightbox="images/special-app-access.png":::

4. Rediger rullelisten, så den viser **Alle apps**.

   :::image type="content" source="images/show-all-apps-2.png" alt-text="Den rulleliste, hvorfra du kan ændre værdien til Alle apps under ruden Batterioptimering" lightbox="images/show-all-apps-2.png":::

   :::image type="content" source="images/show-all-apps-1.png" alt-text="Den rulleliste, der viser indstillingen Alle apps i ruden Batterioptimering" lightbox="images/show-all-apps-1.png":::

5. Find "Microsoft Defender for Endpoint", og vælg **Optimer ikke**.

   :::image type="content" source="images/select-dont-optimise.png" alt-text="Den side, der aktiverer placeringen af indstillingen Microsoft Defender for Endpoint og valg af Optimer ikke" lightbox="images/select-dont-optimise.png":::

Gå tilbage til Microsoft Defender for Endpoint onboardingskærm, vælg **Tillad**, hvorefter du omdirigeres til dashboardskærmen.

## <a name="send-in-app-feedback"></a>Send feedback i appen

Hvis en bruger står over for et problem, der ikke allerede er behandlet i ovenstående afsnit, eller som ikke kan løse ved hjælp af de angivne trin, kan brugeren give **feedback i appen** sammen med **diagnosticeringsdata**. Vores team kan derefter undersøge loggene for at levere den rigtige løsning. Brugerne kan følge disse trin for at gøre det samme:

1. Åbn **MDE-programmet** på din enhed, og klik på **profilikonet** i øverste venstre hjørne.

    :::image type="content" source="images/select-profile-icon-1.jpg" alt-text="Profilikonet på Microsoft Defender for Endpoint-portalen" lightbox="images/select-profile-icon-1.jpg":::

2. Vælg "Hjælp & feedback".

    :::image type="content" source="images/selecthelpandfeedback2.png" alt-text="Indstillingen Hjælp & feedback, der kan vælges på portalen Microsoft Defender for Endpoint" lightbox="images/selecthelpandfeedback2.png":::

3. Vælg "Send feedback til Microsoft".

    :::image type="content" alt-text="Vælg Send feedback til Microsoft" source="images/send-feedback-to-microsoft-3.jpg":::

4. Vælg mellem de angivne indstillinger. Hvis du vil rapportere et problem, skal du vælge "Jeg vil rapportere et problem".

    :::image type="content" source="images/report-issue-4.jpg" alt-text="Indstillingen Jeg vil rapportere et problem" lightbox="images/report-issue-4.jpg":::

5. Angiv oplysninger om det problem, du står over for, og kontrollér "Send diagnosticeringsdata". Vi anbefaler, at du markerer "Medtag din mailadresse", så teamet kan kontakte dig med en løsning eller en opfølgning.

    :::image type="content" source="images/finalsubmit5.png" alt-text="Den rude, hvor du kan tilføje detaljer og vedhæfte diagnosticeringsdata" lightbox="images/finalsubmit5.png":::

6. Klik på "Send" for at sende feedbacken.

