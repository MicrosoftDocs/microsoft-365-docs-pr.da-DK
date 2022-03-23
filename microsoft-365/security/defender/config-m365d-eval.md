---
title: Konfigurer Microsoft 365 Defender søjler til prøvelaboratoriet eller pilotmiljøet
description: Konfigurer Microsoft 365 Defender søjler, f.eks. Microsoft Defender til Office 365, Microsoft Defender til identitet, Microsoft Cloud App Security og Microsoft Defender til slutpunkt til dit prøvelaboratorium eller pilotmiljø.
keywords: konfigurere Microsoft 365 Defender prøveversion, Microsoft 365 Defender en prøveversion, konfigurere Microsoft 365 Defender et pilotprojekt, konfigurere Microsoft 365 Defender søjler, Microsoft 365 Defender søjler
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: e50210f02d14be33c357517515d456318aac4bb6
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/16/2021
ms.locfileid: "63593485"
---
# <a name="configure-microsoft-365-defender-pillars-for-your-trial-lab-or-pilot-environment"></a>Konfigurer Microsoft 365 Defender søjler til dit prøvelaboratorium eller pilotmiljø

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Gælder for:**
- Microsoft 365 Defender


Oprettelse af Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø, og udrulning af det er en trefaset proces:

|[![Fase 1: Forbered](../../media/phase-diagrams/prepare.png)](prepare-m365d-eval.md)<br/>[Fase 1: Forbered](prepare-m365d-eval.md) |[![Fase 2: Konfigurer](../../media/phase-diagrams/setup.png)](setup-m365deval.md)<br/>[Fase 2: Konfigurer](setup-m365deval.md) |![Fase 3: Onboard](../../media/phase-diagrams/onboard.png)<br/>Fase 3: Onboard | [![Tilbage til pilotprojekt](../../media/phase-diagrams/backtopilot.png)](m365d-pilot.md)<br/>[Tilbage til pilotspilbog](m365d-pilot.md) |
|--|--|--|--|
|| |*Du er her!* | |

Du er i øjeblikket i konfigurationsfasen.

Forberedelse er nøglen til en vellykket installation. I denne artikel bliver du vejledt om de punkter, du skal overveje, når du forbereder dig på at installere Microsoft Defender til slutpunkt.

## <a name="microsoft-365-defender-pillars"></a>Microsoft 365 Defender søjler
Microsoft 365 Defender består af fire søjler. Selvom én søjle allerede kan give værdi til din netværksorganisations sikkerhed, giver aktivering af de fire Microsoft 365 Defender søjler organisationen den største værdi.

![Billede of_Microsoft 365 Defender-løsning til brugere, Microsoft Defender for Identity, til slutpunkter Microsoft Defender til slutpunkter, til skyapps, Microsoft Cloud App Security og til data, Microsoft Defender til Office 365](../../media/mtp/m365pillars.png)

Dette afsnit hjælper dig med at konfigurere:

- Microsoft Defender til Office 365
- Microsoft Defender for Identity
- Microsoft Cloud App Security
- Microsoft Defender til Slutpunkt

## <a name="configure-microsoft-defender-for-office-365"></a>Konfigurer Microsoft Defender til Office 365

> [!NOTE]
> Spring dette trin over, hvis du allerede har aktiveret Defender Office 365.

Der er et PowerShell-modul kaldet *Office 365 Advanced Threat Protection Recommended Configuration Analyzer (ORCA),* der hjælper med at bestemme nogle af disse indstillinger. Når du kører som administrator i din lejer, hjælper get-ORCAReport med at generere en vurdering af antispam, antiphish og andre indstillinger for beskeder, der modtager beskeder. Du kan hente dette modul fra https://www.powershellgallery.com/packages/ORCA/.

1. Gå til [Office 365 Security & Compliance](https://protection.office.com/homepage) **CenterThreat** >  **managementPolicy** > .

   ![Billede of_Office 365 Security & Compliance Center– politikside for administration af trusler](../../media/mtp-eval-32.png)

2. Klik **på Antiphishing**, **vælg Opret** , og udfyld politikkens navn og beskrivelse. Klik på **Næste**.

   ![Billede of_Office 365 Security & Compliance Center for antiphishing-politik, hvor du kan navngive din politik](../../media/mtp-eval-33.png)

   > [!NOTE]
   > Rediger din Avancerede antiphishing-politik i Microsoft Defender for Office 365. Skift **Grænseværdi for avanceret** phishing **til 2 - aggressive**.

3. Klik på **rullemenuen Tilføj** en betingelse, og vælg dit/dine domæner som modtagerdomæne. Klik på **Næste**.

   ![Billede of_Office 365 Security & Compliance Center for antiphishing-politik, hvor du kan tilføje en betingelse for programmet](../../media/mtp-eval-34.png)

4. Gennemse dine indstillinger. Klik **på Opret denne politik for** at bekræfte.

   ![Billede of_Office 365 Security & Compliance Center for antiphishing-politik, hvor du kan gennemse dine indstillinger og klikke på knappen Opret denne politik](../../media/mtp-eval-35.png)

5. Vælg **Pengeskab vedhæftede** filer, og vælg indstillingen **Slå ATP til for SharePoint, OneDrive og Microsoft Teams** filer.

   ![Billede of_Office 365 Security & Compliance Center, hvor du kan slå ATP til for SharePoint, OneDrive og Microsoft Teams](../../media/mtp-eval-36.png)

6. Klik på ikonet + for at oprette en ny politik for sikre vedhæftede filer, og anvend den som modtagerdomæne på dine domæner. Klik på **Gem**.

   ![Billede of_Office 365 Security & Compliance Center, hvor du kan oprette en ny politik for sikker vedhæftede filer](../../media/mtp-eval-37.png)

7. Vælg derefter politikken **Pengeskab links**, og klik derefter på blyantsikonet for at redigere standardpolitikken.

8. Sørg for, at **indstillingen Spor ikke, når** brugere klikker på sikre kæder ikke er markeret, mens resten af indstillingerne er markeret. Se [Pengeskab Links for at](/microsoft-365/security/office-365-security/recommended-settings-for-eop-and-office365) få mere at vide. Klik på **Gem**.

   ![Billede of_Office 365 Security & Compliance Center, som viser, at indstillingen Spor ikke, når brugere klikker på Safe ikke er valgt](../../media/mtp-eval-38.png)

9. Vælg derefter **antimalwarepolitikken** , vælg standardindstillingen, og vælg blyantsikonet.

10. Klik **Indstillinger, og** vælg Ja **, og brug standardmeddelelsesteksten til at** aktivere **svar ved registrering af malware**. Slå **filteret Almindelige vedhæftede typer til** . Klik på **Gem**.

    ![Billede of_Office 365 Security & Compliance Center, som viser, at svaret til registrering af malware er aktiveret med standardmeddelelse, og det almindelige filter for vedhæftede filer er slået til](../../media/mtp-eval-39.png)

11. Gå til [Office 365 Security & Compliance](https://protection.office.com/homepage) **CenterSearchAudit-logsøgning** >  > , og slå Overvågning til.

    ![Billede of_Office 365 Security & Compliance Center, hvor du kan aktivere søgning i overvågningsloggen](../../media/mtp-eval-40.png)

12. Integrer Microsoft Defender Office 365 med Microsoft Defender til slutpunkt. Gå til [Office 365 Security & Compliance](https://protection.office.com/homepage) **CenterThreat** >  **managementExplorer** > , og vælg **Microsoft Defender til Indstillinger** i øverste højre hjørne af skærmen. I dialogboksen Defender for Endpoint-forbindelse skal du slå **Forbind til Microsoft Defender for Endpoint**.

    ![Billede of_Office 365 Security & Compliance Center, hvor du kan slå Microsoft Defender for Endpoint-forbindelsen til](../../media/mtp-eval-41.png)

## <a name="configure-microsoft-defender-for-identity"></a>Konfigurer Microsoft Defender for Identity

> [!NOTE]
> Spring dette trin over, hvis du allerede har aktiveret Microsoft Defender for Identity

1. Gå til [Microsoft 365 Security Center >](https://security.microsoft.com/info) vælge **Flere ressourcerMicrosoft** >  **Defender for Identity**.

   ![Billede of_Microsoft 365 Security Center, hvor du kan åbne Microsoft Defender for Identity](../../media/mtp-eval-42.png)

2. Klik **på Opret** for at starte guiden Microsoft Defender for Identity.

   ![Billede of_Microsoft side i guiden Defender for Identity, hvor du skal klikke på knappen Opret](../../media/mtp-eval-43.png)

3. Vælg **Angiv et brugernavn og en adgangskode for at oprette forbindelse til din Active Directory-skov**.

   ![Billede of_Microsoft velkomstsiden for Defender for Identity](../../media/mtp-eval-44.png)

4. Angiv dine lokale Active Directory-legitimationsoplysninger. Dette kan være en hvilken som helst brugerkonto, der har læseadgang til Active Directory.

   ![Billede of_Microsoft siden Defender for Identity Directory-tjenester, hvor du skal angive dine legitimationsoplysninger](../../media/mtp-eval-45.png)

5. Vælg derefter Download **sensorkonfiguration, og** overfør fil til domænecontrolleren.

   ![Billede of_Microsoft Defender for Identity-side, hvor du kan vælge Download sensorkonfiguration](../../media/mtp-eval-46.png)

6. Udfør konfigurationen af Microsoft Defender for Identity Sensor, og begynd at følge guiden.

   ![Billede of_Microsoft siden Defender for Identity, hvor du skal klikke på ved siden af for at følge guiden til Microsoft Defender for Identity-sensoren](../../media/mtp-eval-47.png)

7. Klik **på Næste** ved sensorinstallationstypen.

   ![Billede of_Microsoft siden Defender for Identity, hvor du skal klikke på ud for gå til næste side](../../media/mtp-eval-48.png)

8. Kopiér adgangsnøglen, fordi du skal angive den næste i guiden.

   ![Billede of_the side med sensorer, hvor du skal kopiere adgangstasten, som du skal angive i den næste guideside til konfiguration af Microsoft Defender for Identity-sensor](../../media/mtp-eval-49.png)

9. Kopiér adgangsnøglen til guiden, og klik på **Installér**.

   ![Billede of_Microsoft guidesiden for Defender for Identity-sensoren, hvor du skal angive adgangstasten og derefter klikke på installationsknappen](../../media/mtp-eval-50.png)

10. Tillykke, du har konfigureret Microsoft Defender til identitet på din domænecontroller.

    ![Billede of_Microsoft fuldførelse af guiden Defender for Identity-sensor, hvor du skal klikke på afslutningsknappen](../../media/mtp-eval-51.png)

11. I sektionen [Microsoft Defender for Identity settings](https://go.microsoft.com/fwlink/?linkid=2040449) skal du vælge **Microsoft Defender for Endpoint **, og slå derefter til/fra-knappen til. Klik på **Gem**.

    ![Billede of_the siden med indstillinger for Microsoft Defender for Identity, hvor du skal slå Til/fra-knappen for Microsoft Defender til Slutpunkt til](../../media/mtp-eval-52.png)

## <a name="configure-microsoft-cloud-app-security"></a>Konfigurer Microsoft Cloud App Security

> [!NOTE]
> Spring dette trin over, hvis du allerede har aktiveret Microsoft Cloud App Security.

1. Gå til [Microsoft 365 Security CenterMore](https://security.microsoft.com/info) >  **Resources** >  **Microsoft Cloud App Security**.

   ![Billede of_Microsoft 365 Security Center, hvor du kan se kortet Microsoft Cloud-app og klikke på knappen Åbn](../../media/mtp-eval-53.png)

2. Når du bliver bedt om at integrere Microsoft Defender for Identity, skal du **vælge Aktivér dataintegration med Microsoft Defender for Identity**.

   ![Billede of_the om integration af Microsoft Defender for Identity, hvor du skal vælge linket Aktivér dataintegration med Microsoft Defender for Identity](../../media/mtp-eval-54.png)

   > [!NOTE]
   > Hvis du ikke får vist denne prompt, kan det betyde, at din integration med Microsoft Defender for Identity-data allerede er aktiveret. Men hvis du ikke er sikker, skal du kontakte din it-administrator for at bekræfte.

3. Gå til **Indstillinger**, slå microsoft **Defender for Identity-integration til, og** klik derefter på **Gem**.

   ![Siden of_the indstillinger, hvor du skal slå til/fra-knappen for Microsoft Defender for Identity-integration til, og klik derefter på Gem](../../media/mtp-eval-55.png)

   > [!NOTE]
   > For nye Microsoft Defender for Identity-forekomster er denne integrationskontakt automatisk slået til. Bekræft, at din Microsoft Defender for Identity-integration er blevet aktiveret, før du går videre til næste trin.

4. Under indstillingerne for Cloud Discovery skal du **vælge Microsoft Defender for Endpoint-integration** og derefter aktivere integrationen. Klik på **Gem**.

   ![Billede of_the siden Microsoft Defender til slutpunkt, hvor afkrydsningsfeltet for blokering af ikke-installerede apps under Integration af Microsoft Defender for Slutpunkt er markeret. Klik på Gem.](../../media/mtp-eval-56.png)

5. Under Indstillinger for skyregistrering skal du **vælge Brugerberigelse** og derefter aktivere integration med Azure Active Directory.

   ![Billede af afsnittet Brugerberigende, hvor afkrydsningsfeltet de berigende opdagede brugeridentifikatorer Azure Active Directory afkrydsningsfeltet Brugernavne er markeret](../../media/mtp-eval-57.png)

## <a name="configure-microsoft-defender-for-endpoint"></a>Konfigurer Microsoft Defender til slutpunkt

> [!NOTE]
> Spring dette trin over, hvis du allerede har aktiveret Microsoft Defender til slutpunkt.

1. Gå til [Microsoft 365 Security CenterMore](https://security.microsoft.com/info) >  **Resources** >  **Microsoft Defender Security Center**. Klik **på Åbn**.

   ![Billede of_Microsoft indstillingen Defender Security Center på siden Microsoft 365 Security Center](../../media/mtp-eval-58.png)

2. Følg guiden Microsoft Defender for Endpoint. Klik på **Næste**.

   ![Side med of_the Microsoft Defender Security Center i guiden Til velkomst](../../media/mtp-eval-59.png)

3. Vælg baseret på din foretrukne datalagringsplacering, dataopbevaringspolitik, organisationens størrelse og tilvalg for visningsfunktioner.

   ![Billede of_the for at vælge dit datalagerland, din opbevaringspolitik og organisationens størrelse. Klik på Næste, når du er færdig med at vælge.](../../media/mtp-eval-60.png)

   > [!NOTE]
   > Du kan ikke ændre nogle af indstillingerne, f.eks. placering af datalagring, bagefter.

   Klik på **Næste**.

4. Klik **på Fortsæt** , så klargør den din Microsoft Defender til endpoint-lejeren.

   ![Billede of_the, hvor du klikker på knappen Fortsæt for at oprette din skyforekomst](../../media/mtp-eval-61.png)

5. Onboard dine slutpunkter via Gruppepolitikker, Microsoft Endpoint Manager eller ved at køre et lokalt script til Microsoft Defender for Endpoint. For overskuelighedens skyld bruger denne vejledning det lokale script.

6. Klik **på Download pakke** , og kopiér onboardingscriptet til dine slutpunkter.

   ![Billede of_page, hvor du klikker på knappen Download pakke for at kopiere onboardingscriptet til dine slutpunkter eller slutpunkter](../../media/mtp-eval-62.png)

7. På dit slutpunkt skal du køre onboardingscriptet som administrator og vælge Y.

   ![Billede of_the kommandolinje, hvor du kører onboarding-scriptet, og vælg Y for at fortsætte](../../media/mtp-eval-63.png)

8. Tillykke, du har onboardet dit første slutpunkt.

   ![Billede of_the kommandolinjen, hvor du får en bekræftelse på, at du har onboardet dit første slutpunkt. Tryk på en tast for at fortsætte](../../media/mtp-eval-64.png)

9. Kopiér registreringstesten fra guiden Microsoft Defender for Endpoint.

   ![Billedteste of_the et registreringstesttrin, hvor du skal klikke på Kopiér for at kopiere registreringstestscriptet, som du skal indsætte i kommandoprompten](../../media/mtp-eval-65.png)

10. Kopiér PowerShell-scriptet til en kommandoprompt med administrator administrator, og kør det.

    ![Image of_command prompt where you should copy the PowerShell script to an elevated command prompt and run it](../../media/mtp-eval-66.png)

11. Vælg **Begynd at bruge Microsoft Defender til slutpunkt** i guiden.

    ![Billedbekræftelse of_the bekræftelsesprompt fra guiden, hvor du skal klikke på Begynd at bruge Microsoft Defender til slutpunkt](../../media/mtp-eval-67.png)

12. Gå [til Microsoft Defender Security Center](https://securitycenter.windows.com/). Gå til **Indstillinger og** vælg derefter **Avancerede funktioner**.

    ![Billede of_Microsoft Defender Security Center Indstillinger menu, hvor du skal vælge Avancerede funktioner](../../media/mtp-eval-68.png)

13. Slå integration med **Microsoft Defender for Identity til**.

    ![Billede of_Microsoft til indstillingen Avanceret i Defender Security Center, indstillingen Microsoft Defender for Identity, som du skal slå til](../../media/mtp-eval-69.png)

14. Aktiver integration med **Office 365 Threat Intelligence**.

    ![Billede of_Microsoft avancerede funktioner i Defender Security Center Office 365 indstillingen Threat Intelligence, som du skal aktivere](../../media/mtp-eval-70.png)

15. Aktiver integration **med Microsoft Cloud App Security**.

    ![Billede of_Microsoft avancerede funktioner i Defender Security Center Microsoft Cloud App Security indstillingen, som du skal slå til](../../media/mtp-eval-71.png)

16. Rul ned, og **klik på Gem indstillinger** for at bekræfte de nye integrationer.

    ![Knappen of_Save indstillinger, du skal klikke på](../../media/mtp-eval-72.png)

## <a name="start-the-microsoft-365-defender-service"></a>Start Microsoft 365 Defender tjeneste

> [!NOTE]
> Fra 1. juni 2020 aktiverer Microsoft automatisk Microsoft 365 Defender funktioner for alle berettigede lejere. Se denne [Microsoft Tech Community-artikel om berettigelse til licenser](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/microsoft-threat-protection-will-automatically-turn-on-for/ba-p/1345426) for at få flere oplysninger.

Gå til [Microsoft 365 Security Center](https://security.microsoft.com/homepage). Gå til **Indstillinger,** og vælg **Microsoft 365 Defender**.

![Billede of_Microsoft af indstillingen 365 Defender Microsoft 365 siden Indstillinger Security Center](../../media/mtp-eval-72b.png)

Du kan finde en mere omfattende vejledning [under Slå Microsoft 365 Defender](m365d-enable.md).

Tillykke! Du har lige oprettet dit Microsoft 365 Defender-prøvelaboratorium eller pilotmiljø! Nu kan du gøre dig bekendt med Microsoft 365 Defender brugergrænsefladen! Se, hvad du kan lære af følgende Microsoft 365 Defender interaktiv vejledning, og find ud af, hvordan du bruger hvert dashboard til dine daglige sikkerhedsopgaver.

[Se den interaktive vejledning](https://aka.ms/MTP-Interactive-Guide)

Derefter kan du simulere et angreb og se, hvordan de forskellige produktfunktioner registrerer, opretter beskeder og automatisk reagerer på et filløst angreb på et slutpunkt.

## <a name="next-step"></a>Næste trin

- [Opret en testbesked –](generate-test-alert.md) Kør en angrebssimulering i Microsoft 365 Defender prøvelaboratorium.
