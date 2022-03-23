---
title: Onboarding ved hjælp Microsoft Endpoint Manager
description: Få mere at vide om, hvordan du kommer i gang med Microsoft Defender til slutpunkt ved hjælp Microsoft Endpoint Manager
keywords: onboarding, konfiguration, installation, installation, slutpunktsstyring, Microsoft Defender til slutpunkt, oprettelse af samling, svar på registrering af slutpunkter, næste generations beskyttelse, reduktion af angrebsoverfladen, Microsoft Endpoint Manager
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
- M365-security-compliance
- m365solution-endpointprotect
- m365solution-scenario
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 261cb8af0f1fbb4c118aca649945f66015f1d25c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63591131"
---
# <a name="onboarding-using-microsoft-endpoint-manager"></a>Onboarding ved hjælp Microsoft Endpoint Manager

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**

- [Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vil du opleve Microsoft Defender til slutpunkt? [Tilmeld dig for at få en gratis prøveversion.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Denne artikel er en del af Installationsvejledningen og fungerer som et eksempel på onboardingmetoden.

I emnet [Planlægning](deployment-strategy.md) var der flere forskellige metoder for onboardingenheder til tjenesten. Dette emne omhandler den skybaserede arkitektur.

![Billede af skybaseret arkitektur.](images/cloud-native-architecture.png)
 *Diagram over miljøarkitekturer*

Mens Defender til Slutpunkt understøtter onboarding af forskellige slutpunkter og værktøjer, dækker denne artikel dem ikke. Du kan finde oplysninger om generel onboarding ved hjælp af andre understøttede installationsværktøjer og metoder under [Oversigt over onboarding](onboarding.md).

[Microsoft Endpoint Manager](/mem/endpoint-manager-overview) er en løsningsplatform, der samler flere tjenester. Det omfatter [Microsoft Intune](/mem/intune/fundamentals/what-is-intune) baseret administration af enheder.

Dette emne hjælper brugerne i:

- Trin 1: Onboardingenheder til tjenesten ved at oprette en gruppe i Microsoft Endpoint Manager (MEM) til at tildele konfigurationer på
- Trin 2: Konfiguration af Defender til slutpunkt-funktioner ved hjælp Microsoft Endpoint Manager

Denne onboardingvejledning vejleder dig gennem de følgende grundlæggende trin, du skal tage, når du bruger Microsoft Endpoint Manager:

- [Identificere målenheder eller brugere](#identify-target-devices-or-users)
  - Oprette en Azure Active Directory gruppe (bruger eller enhed)
- [Oprette en konfigurationsprofil](#step-2-create-configuration-policies-to-configure-microsoft-defender-for-endpoint-capabilities)
  - I Microsoft Endpoint Manager hjælper vi dig med at oprette en separat politik for hver funktion.

## <a name="resources"></a>Ressourcer

Her er de links, du skal bruge til resten af processen:

- [MEM-portal](https://aka.ms/memac)
- [Microsoft 365 Defender](https://security.microsoft.com)
- [Grundlinjer for Intune Security](/mem/intune/protect/security-baseline-settings-defender-atp#microsoft-defender)

Du kan finde flere Microsoft Endpoint Manager i disse ressourcer:

- [Microsoft Endpoint Manager side](/mem/)
- [Blogindlæg om alle, der bruger Intune og ConfigMgr](https://www.microsoft.com/microsoft-365/blog/2019/11/04/use-the-power-of-cloud-intelligence-to-simplify-and-accelerate-it-and-the-move-to-a-modern-workplace/)
- [Introduktionsvideo om MEM](https://www.microsoft.com/microsoft-365/blog/2019/11/04/use-the-power-of-cloud-intelligence-to-simplify-and-accelerate-it-and-the-move-to-a-modern-workplace)

## <a name="step-1-onboard-devices-by-creating-a-group-in-mem-to-assign-configurations-on"></a>Trin 1: Onboard-enheder ved at oprette en gruppe i MEM til at tildele konfigurationer på

### <a name="identify-target-devices-or-users"></a>Identificer målenheder eller brugere

I dette afsnit opretter vi en testgruppe, som dine konfigurationer skal tildeles.

> [!NOTE]
> Intune bruger Azure Active Directory (Azure AD) til at administrere enheder og brugere. Som Intune-administrator kan du konfigurere grupper, så de passer til virksomhedens behov.
>
> Få mere at vide under [Tilføj grupper for at organisere brugere og enheder](/mem/intune/fundamentals/groups-add).

### <a name="create-a-group"></a>Opret en gruppe

1. Åbn MEM-portalen.

2. Åbn **Grupper > Ny gruppe**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal1.](images/66f724598d9c3319cba27f79dd4617a4.png)

3. Angiv detaljer, og opret en ny gruppe.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal2.](images/b1e0206d675ad07db218b63cd9b9abc3.png)

4. Tilføj din testbruger eller enhed.

5. Åbn **den > gruppe under** ruden Alle grupper.

6. Vælg  **Medlemmer > Tilføj medlemmer**.

7. Find din testbruger eller enhed, og vælg den.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal3.](images/149cbfdf221cdbde8159d0ab72644cd0.png)

8. Din testgruppe skal nu testes af et medlem.

## <a name="step-2-create-configuration-policies-to-configure-microsoft-defender-for-endpoint-capabilities"></a>Trin 2: Opret konfigurationspolitikker for at konfigurere Microsoft Defender for Endpoint-funktioner

I det følgende afsnit skal du oprette en række konfigurationspolitikker.

For det første er en konfigurationspolitik til at vælge, hvilke grupper af brugere eller enheder, der skal onboardes til Defender til slutpunkt:

- [Registrering af slutpunkt og svar](#endpoint-detection-and-response)

Derefter kan du fortsætte ved at oprette flere forskellige typer sikkerhedspolitikker for slutpunkter:

- [Næste generations beskyttelse](#next-generation-protection)
- [Reduktion af angrebsoverfladen](#attack-surface-reduction---attack-surface-reduction-rules)

### <a name="endpoint-detection-and-response"></a>Registrering af slutpunkt og svar

1. Åbn MEM-portalen.

2. Gå til **Slutpunktssikkerhed for > slutpunktsregistrering og -svar**. Klik på **Opret profil**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal4.](images/58dcd48811147feb4ddc17212b7fe840.png)

3. Under **Platform skal du vælge Windows 10 og Senere, Profil – Slutpunktsregistrering og svar > Opret**.

4. Angiv et navn og en beskrivelse, og vælg derefter  **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal5.](images/a5b2d23bdd50b160fef4afd25dda28d4.png)

5. Vælg indstillinger efter behov, og vælg derefter  **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal6.](images/cea7e288b5d42a9baf1aef0754ade910.png)

    > [!NOTE]
    > I dette tilfælde er dette blevet udfyldt automatisk, da Defender for Endpoint allerede er blevet integreret med Intune. Du kan finde flere oplysninger om integration under [Aktivér Microsoft Defender for Endpoint i Intune](/mem/intune/protect/advanced-threat-protection-configure#to-enable-microsoft-defender-atp).
    >
    > Følgende billede er et eksempel på, hvad du får vist, når Microsoft Defender til slutpunkt IKKE er integreret med Intune:
    >
    > ![Billede af Microsoft Endpoint Manager portal7.](images/2466460812371ffae2d19a10c347d6f4.png)

6. Tilføj områdemærker, hvis det er nødvendigt, og vælg  **derefter Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal8.](images/ef844f52ec2c0d737ce793f68b5e8408.png)

7. Tilføj testgruppe ved at klikke på Vælg **grupper, der skal medtages** , og vælg din gruppe, og vælg derefter  **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal9.](images/fc3525e20752da026ec9f46ab4fec64f.png)

8. Gennemse og acceptér, og vælg derefter  **Opret**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal10.](images/289172dbd7bd34d55d24810d9d4d8158.png)

9. Du kan se den politik, du har gennemført.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal11.](images/5a568b6878be8243ea2b9d82d41ed297.png)

### <a name="next-generation-protection"></a>Næste generations beskyttelse

1. Åbn MEM-portalen.

2. Gå til **Endpoint Security > Antivirus > Opret politik**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal12.](images/6b728d6e0d71108d768e368b416ff8ba.png)

3. Vælg **Platform - Windows 10 og senere - Windows og profil - Microsoft Defender Antivirus > Opret**.

4. Angiv navn og beskrivelse, og vælg derefter  **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal13.](images/a7d738dd4509d65407b7d12beaa3e917.png)

5. På siden **Konfigurationsindstillinger**: Indstil de konfigurationer, du skal bruge til Microsoft Defender Antivirus (Skybeskyttelse, Undtagelser, Real-Time Beskyttelse og Afhjælpning).

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal14.](images/3840b1576d6f79a1d72eb14760ef5e8c.png)

6. Tilføj områdemærker, hvis det er nødvendigt, og vælg  **derefter Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal15.](images/2055e4f9b9141525c0eb681e7ba19381.png)

7. Vælg grupper, der skal medtages, tildel til din testgruppe, og vælg derefter  **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal16.](images/48318a51adee06bff3908e8ad4944dc9.png)

8. Gennemse og opret, og vælg derefter  **Opret**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal17.](images/dfdadab79112d61bd3693d957084b0ec.png)

9. Du får vist den konfigurationspolitik, du har oprettet.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal18.](images/38180219e632d6e4ec7bd25a46398da8.png)

### <a name="attack-surface-reduction---attack-surface-reduction-rules"></a>Reduktion af angrebsoverfladen – Regler for reduktion af angrebsoverfladen

1. Åbn MEM-portalen.

2. Gå til **Endpoint-sikkerhed > reduktion af angrebsoverfladen**.

3. Vælg  **Opret politik**.

4. Vælg **Platform – Windows 10 og nyere – Profil – Reduktionsregler for angrebsoverfladen > Create**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal19.](images/522d9bb4288dc9c1a957392b51384fdd.png)

5. Angiv et navn og en beskrivelse, og vælg derefter  **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal20.](images/a5a71fd73ec389f3cdce6d1a6bd1ff31.png)

6. På siden **Konfigurationsindstillinger**: Angiv de konfigurationer, du skal bruge til at reducere angrebsoverfladen, og vælg derefter  **Næste**.

    > [!NOTE]
    > Vi konfigurerer alle reduktionsregler for angrebsoverfladen til Audit.
    >
    > Få mere at vide under [Regler for reduktion af angrebsoverfladen](attack-surface-reduction.md).

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal21.](images/dd0c00efe615a64a4a368f54257777d0.png)

7. Tilføj områdemærker efter behov, og vælg derefter  **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal22.](images/6daa8d347c98fe94a0d9c22797ff6f28.png)

8. Vælg grupper, der skal medtages og tildeles til testgruppen, og vælg derefter  **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal23.](images/45cefc8e4e474321b4d47b4626346597.png)

9. Gennemgå oplysningerne, og vælg derefter  **Opret**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal24.](images/2c2e87c5fedc87eba17be0cdeffdb17f.png)

10. Få vist politikken.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal25.](images/7a631d17cc42500dacad4e995823ffef.png)

### <a name="attack-surface-reduction---web-protection"></a>Reduktion af angrebsoverfladen – Webbeskyttelse

1. Åbn MEM-portalen.

2. Gå til **Endpoint-sikkerhed > reduktion af angrebsoverfladen**.

3. Vælg  **Opret politik**.

4. Vælg **Windows 10 og Nyere – Webbeskyttelse > Opret**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal26.](images/cd7b5a1cbc16cc05f878cdc99ba4c27f.png)

5. Angiv et navn og en beskrivelse, og vælg derefter  **Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal27.](images/5be573a60cd4fa56a86a6668b62dd808.png)

6. På siden **Konfigurationsindstillinger**: Angiv de konfigurationer, du skal bruge til Webbeskyttelse, og vælg derefter  **Næste**.

    > [!NOTE]
    > Vi konfigurerer Webbeskyttelse til at blokere.
    >
    > Du kan finde flere oplysninger under [Webbeskyttelse](web-protection-overview.md).

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal28.](images/6104aa33a56fab750cf30ecabef9f5b6.png)

7. Tilføj **omfangsmærker efter behov > Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal29.](images/6daa8d347c98fe94a0d9c22797ff6f28.png)

8. Vælg **Tildel for at teste > Næste**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal30.](images/45cefc8e4e474321b4d47b4626346597.png)

9. Vælg **Gennemse, og opret > Opret**.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal31.](images/8ee0405f1a96c23d2eb6f737f11c1ae5.png)

10. Få vist politikken.

    > [!div class="mx-imgBorder"]
    > ![Billede af Microsoft Endpoint Manager portal32.](images/e74f6f6c150d017a286e6ed3dffb7757.png)

## <a name="validate-configuration-settings"></a>Valider konfigurationsindstillinger

### <a name="confirm-policies-have-been-applied"></a>Bekræft, at politikker er blevet anvendt

Når konfigurationspolitikken er blevet tildelt, tager det et stykke tid at anvende den.

Du kan finde oplysninger om tidsindstilling [under Oplysninger om konfiguration i Intune](/mem/intune/configuration/device-profile-troubleshoot#how-long-does-it-take-for-devices-to-get-a-policy-profile-or-app-after-they-are-assigned).

Hvis du vil bekræfte, at konfigurationspolitikken er blevet anvendt på din testenhed, skal du følge følgende proces for hver konfigurationspolitik.

1. Åbn MEM-portalen, og gå til den relevante politik, sådan som det er vist i ovenstående trin. Følgende eksempel viser den næste generations beskyttelsesindstillinger.

    > [!div class="mx-imgBorder"]
    > [![Billede af Microsoft Endpoint Manager portal33.](images/43ab6aa74471ee2977e154a4a5ef2d39.png)](images/43ab6aa74471ee2977e154a4a5ef2d39.png#lightbox)

2. Vælg **Konfigurationspolitik for** at få vist politikstatus.

    > [!div class="mx-imgBorder"]
    > [![Billede af Microsoft Endpoint Manager portal34.](images/55ecaca0e4a022f0e29d45aeed724e6c.png)](images/55ecaca0e4a022f0e29d45aeed724e6c.png#lightbox)

3. Vælg  **Enhedsstatus** for at få vist status.

    > [!div class="mx-imgBorder"]
    > [![Billede af Microsoft Endpoint Manager portal35.](images/18a50df62cc38749000dbfb48e9a4c9b.png)](images/18a50df62cc38749000dbfb48e9a4c9b.png#lightbox)

4. Vælg  **Brugerstatus** for at få vist status.

    > [!div class="mx-imgBorder"]
    > [![Billede af Microsoft Endpoint Manager portal36.](images/4e965749ff71178af8873bc91f9fe525.png)](images/4e965749ff71178af8873bc91f9fe525.png#lightbox)

5. Vælg  **Status pr. indstilling for** at få vist status.

    > [!TIP]
    > Denne visning er meget nyttig til at identificere indstillinger, der er i konflikt med en anden politik.

    > [!div class="mx-imgBorder"]
    > [![Billede af Microsoft Endpoint Manager portal37.](images/42acc69d0128ed09804010bdbdf0a43c.png)](images/42acc69d0128ed09804010bdbdf0a43c.png#lightbox)

### <a name="confirm-endpoint-detection-and-response"></a>Bekræft slutpunktsregistrering og -svar

1. Før du anvender konfigurationen, bør Defender for Endpoint Protection-tjenesten ikke startes.

    > [!div class="mx-imgBorder"]
    > [![Billede af panelet Tjenester1.](images/b418a232a12b3d0a65fc98248dbb0e31.png)](images/b418a232a12b3d0a65fc98248dbb0e31.png#lightbox)

2. Når konfigurationen er blevet anvendt, skulle Defender for Endpoint Protection Service være startet.

    > [!div class="mx-imgBorder"]
    > [![Billede af panelet Tjenester2.](images/a621b699899f1b41db211170074ea59e.png)](images/a621b699899f1b41db211170074ea59e.png#lightbox)

3. Når tjenesterne kører på enheden, vises enheden i Microsoft 365 Defender portal.

    > [!div class="mx-imgBorder"]
    > [![Billede af Microsoft 365 Defender portal.](images/df0c64001b9219cfbd10f8f81a273190.png)](images/df0c64001b9219cfbd10f8f81a273190.png#lightbox)

### <a name="confirm-next-generation-protection"></a>Bekræft næste generations beskyttelse

1. Før du anvender politikken på en testenhed, bør du kunne administrere indstillingerne manuelt som vist nedenfor.

    > [!div class="mx-imgBorder"]
    > ![Billede af indstillingsside1.](images/88efb4c3710493a53f2840c3eac3e3d3.png)

2. Når politikken er blevet anvendt, bør du ikke kunne administrere indstillingerne manuelt.

    > [!NOTE]
    > På følgende billede **Aktiver beskyttelse i skyen** og **Aktiver beskyttelse** i realtid vises som administreret.

    > [!div class="mx-imgBorder"]
    > ![Billede af indstilling af side2.](images/9341428b2d3164ca63d7d4eaa5cff642.png)

### <a name="confirm-attack-surface-reduction---attack-surface-reduction-rules"></a>Bekræft reduktion af angrebsoverfladen – Regler for reduktion af angrebsoverfladen

1. Før du anvender politikken på en testenhed, skal du skrive et PowerShell-vindue og skrive `Get-MpPreference`.

2. Dette bør svare med følgende linjer uden indhold:

    > AttackSurfaceReductionOnlyExclusions:
    >
    > AttackSurfaceReductionRules_Actions:
    >
    > AttackSurfaceReductionRules_Ids:

    ![Billede af kommandolinje1.](images/cb0260d4b2636814e37eee427211fe71.png)

3. Når du har anvendt politikken på en testenhed, skal du åbne en PowerShell Windows og skrive `Get-MpPreference`.

4. Dette bør svare med følgende linjer med indhold som vist nedenfor:

    ![Billede af kommandolinje2.](images/619fb877791b1fc8bc7dfae1a579043d.png)

### <a name="confirm-attack-surface-reduction---web-protection"></a>Bekræft reduktion af angrebsoverfladen – Webbeskyttelse

1. På testenheden skal du åbne en PowerShell-Windows og skrive `(Get-MpPreference).EnableNetworkProtection`.

2. Dette bør svare med et 0, som vist nedenfor.

    ![Billede af kommandolinje3.](images/196a8e194ac99d84221f405d0f684f8c.png)

3. Når du har anvendt politikken, skal du åbne en PowerShell Windows og skrive `(Get-MpPreference).EnableNetworkProtection`.

4. Dette bør svare med 1 som vist nedenfor.

    ![Billede af kommandolinje4.](images/c06fa3bbc2f70d59dfe1e106cd9a4683.png)
