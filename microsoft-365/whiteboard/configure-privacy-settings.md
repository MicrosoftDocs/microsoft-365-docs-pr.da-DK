---
title: Konfigurer indstillinger for beskyttelse af personlige oplysninger i Microsoft Whiteboard
ms.author: chucked
author: chuckedmonson
manager: alexfaulkner
ms.reviewer: ''
audience: admin
ms.topic: article
ms.custom: ''
ms.prod: microsoft-365-enterprise
search.appverid: MET150
ms.collection: ''
ms.localizationpriority: medium
description: Få mere at vide om overholdelse af angivne standarder, og hvordan du konfigurerer indstillinger for beskyttelse af personlige oplysninger i Microsoft Whiteboard.
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: a2708d3eda92f3d29ea9ad6ee15e518d32d93a22
ms.sourcegitcommit: 49c275f78664740988bbc4ca4b14d3ad758e1468
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/19/2022
ms.locfileid: "66882778"
---
# <a name="configure-privacy-settings-in-microsoft-whiteboard"></a>Konfigurer indstillinger for beskyttelse af personlige oplysninger i Microsoft Whiteboard

>[!NOTE]
> Hvis du eller dine brugere vil vide mere om standardindstillingerne for beskyttelse af personlige oplysninger, valgfri forbundne oplevelser, og hvordan diagnosticeringsdata indsamles, skal du sende dem til [Microsoft Whiteboards beskyttelse af personlige oplysninger og overholdelse af angivne standarder](https://support.microsoft.com/office/privacy-and-compliance-ed9f0de9-71be-44c2-837d-e0f448660be1).

Hvis du er Microsoft Whiteboard-administrator for din organisation, kan du styre følgende:

- Hvilket niveau af diagnosticeringsdata der indsamles og sendes til Microsoft om Whiteboard-klientsoftwaren, der kører på brugerens enhed.

- Om valgfri forbundne oplevelser i Whiteboard er tilgængelige for dine brugere.

Hvis du vil konfigurere niveauet af diagnosticeringsdata, [skal du](/microsoft-365/admin/admin-overview/admin-center-overview?view=o365-worldwide) logge på Microsoft 365 Administration med din administratorkonto. På startsiden for Administration skal du gå til **Vis alle indstillinger for > > Organisationsindstillinger > Whiteboard**.

Hvis du vil konfigurere tilgængeligheden af valgfri forbundne oplevelser, skal du bruge [tjenesten Office-skypolitik](/deployoffice/admincenter/overview-office-cloud-policy-service) i [Microsoft 365 Apps Administration](https://config.office.com). Log på med din administratorkonto, og gå til **Tilpasning > Politikadministration**. Den politik, du vil konfigurere, er navngivet: **Tillad brugen af yderligere valgfri forbundne oplevelser i Office**.

## <a name="diagnostic-data-setting-for-your-organization"></a>Indstillinger for diagnosticeringsdata for din organisation

Du kan vælge det niveau af diagnosticeringsdata, der indsamles og sendes til Microsoft om Whiteboard-klientsoftwaren, der kører på enheder i din organisation. Valgfrie diagnosticeringsdata sendes til Microsoft, medmindre du ændrer indstillingen i Microsoft 365 Administration. Hvis du vælger at sende valgfri diagnosticeringdata, er de påkrævede diagnosticeringsdata også inkluderet.

Ud over **Påkrævet** eller **Valgfri** er der også et valg af Ingen af **delene**. Hvis du vælger denne indstilling, sendes der ingen diagnosticeringsdata om Whiteboard-klientsoftware, der kører på brugerens enhed, til Microsoft. Denne indstilling begrænser dog markant Microsofts mulighed for at registrere, diagnosticere og løse problemer, som dine brugere kan støde på, når de bruger Whiteboard.

Brugerne kan ikke ændre niveauet af diagnosticeringsdata for deres enheder, hvis de er logget på Whiteboard med deres organisations legitimationsoplysninger (også kaldet en arbejds- eller skolekonto). Men hvis de er logget på Whiteboard med en Microsoft-konto, f.eks. en personlig outlook.com mailadresse, kan de ændre niveauet af diagnosticeringsdata på deres enheder ved at gå til **Indstillinger > Beskyttelse af personlige oplysninger og sikkerhed**.

## <a name="optional-connected-experiences-setting-for-your-organization"></a>Valgfri indstilling for forbundne oplevelser for din organisation

Du kan vælge, om du vil gøre valgfri forbundne oplevelser i Whiteboard tilgængelige for dine brugere. Disse forbundne oplevelser vil være tilgængelige for dine brugere, medmindre du ændrer indstillingen i Microsoft 365 Administration. 

Disse forbundne oplevelser er anderledes, fordi de ikke er omfattet af din organisations kommercielle aftale med Microsoft. Valgfri forbundne oplevelser leveres af Microsoft direkte til dine brugere og er underlagt [Microsoft-serviceaftalen](https://www.microsoft.com/servicesagreement) og ikke [Vilkårene for onlinetjenester](https://www.microsoft.com/licensing/product-licensing/products).

Selvom du vælger at gøre disse valgfri forbundne oplevelser tilgængelige for dine brugere, har dine brugere mulighed for at slå dem fra som en gruppe ved at gå til **Indstillinger > Beskyttelse af personlige oplysninger og sikkerhed**. Dine brugere har kun dette valg, hvis de er logget på Whiteboard med deres organisations legitimationsoplysninger (også kaldet en arbejds- eller skolekonto), ikke hvis de er logget på med en Microsoft-konto, f.eks. en personlig outlook.com mailadresse.

## <a name="required-diagnostic-data-events-collected-by-whiteboard"></a>Påkrævede hændelser for diagnosticeringsdata, der indsamles af Whiteboard

Følgende er de påkrævede hændelser for diagnosticeringsdata, der indsamles af Whiteboard, herunder en liste over datafelter i hver enkelt hændelse.

**Intentional.CanvasObject.Ink.DrawFirstStroke**

Førstegangs blæk, der indsamles, føjes til et tavle i Microsoft Whiteboard. Disse oplysninger er vigtige for at registrere fejl, der er knyttet til tilføjelse af håndskrift til et tavle. Microsoft bruger disse data til at diagnosticere problemet for at garantere, at Microsoft Whiteboard kører som forventet.

- **Handling** – type pennestrøg
- **Kilde** – inputmetode for pennestrøg

**Intentional.SurfSide.ActivationProtocol.LoadFromUri**

Indsamles, hver gang Microsoft Whiteboard startes af et opkald fra et andet program eller en anden proces. Disse oplysninger er vigtige for at registrere, om Whiteboard ikke startes korrekt af et andet program eller en anden proces. Microsoft bruger disse data til at diagnosticere problemet for at garantere, at Microsoft Whiteboard kører som forventet.

- **ApplicationExecutionState** – appens udførelsestilstand, når aktiveringsprotokollen sker
- **IsSignedIn** – brugeren er godkendelsesstatus
- **Kind** – program eller proces, der starter Whiteboard

**Intentional.Whiteboard.Init.DisplayWhiteboard**

Indsamles første gang Microsoft Whiteboard faktisk vises på en klient pr. session. Disse oplysninger er vigtige for at registrere startproblemer. Microsoft bruger disse data til at diagnosticere problemet for at garantere, at Microsoft Whiteboard kører som forventet.

- **IsPrelaunched** – status for forhåndsafsender
- **IsProtocolActivation** – programstarttype

**Intentional.Whiteboard.Init.StartApp**

Indsamles hver gang, når Microsoft Whiteboard starter, efter at den forrige tilstand sluttede uden at gå ned. Disse oplysninger er vigtige for at registrere nedbrudsproblemer. Microsoft bruger disse data til at diagnosticere problemet for at garantere, at Microsoft Whiteboard kører som forventet.

- **Første start** – første gang appen blev startet på klienten

**Intentional.Whiteboard.KeyCategory.UseCategory**

Indsamles, hver gang en funktion bruges for første gang (og kun første gang) pr. bruger/session/whiteboard i Microsoft Whiteboard. Disse oplysninger er vigtige for at sikre, at nøglekategorierne bruges. Microsoft bruger disse data til at diagnosticere problemet for at garantere, at Microsoft Whiteboard kører som forventet.

- **CategoryName** – Navnet på nøglekategorien

**Intentional.Whiteboard.KeyFeature.UseFeature**

Indsamles, hver gang en funktion bruges for første gang (og kun første gang) pr. bruger/session/whiteboard i Microsoft Whiteboard. Disse oplysninger er vigtige for at sikre, at funktionerne kaldes og bruges. Microsoft bruger disse data til at diagnosticere problemet for at garantere, at Microsoft Whiteboard kører som forventet.

- **FeatureName** – Navnet på nøglefunktionen

**Intentional.Whiteboard.SafeBoot.StartApp**

Indsamles, hver gang Microsoft Whiteboard starter, efter at den forrige tilstand sluttede i et nedbrud. Disse oplysninger er vigtige for at registrere nedbrudsproblemer. Microsoft bruger disse data til at diagnosticere problemet for at garantere, at Microsoft Whiteboard kører som forventet.

- **Første start** – første gang appen blev startet på klienten

**Intentional.Whiteboard.Scrub.LoadSettings**

Indsamles, hver gang Microsoft Whiteboard starter. Disse oplysninger er vigtige for at registrere fejl, der er knyttet til brugerkonfigurerede indstillinger. Microsoft bruger disse data til at diagnosticere problemet for at garantere, at Microsoft Whiteboard kører som forventet.

- **ActivePen** – pennetilstandstilstand
- **CollectFullTelemetryWithoutSignIn** – komplet telemetriindsamling uden logonaktivering
- **DefaultWhiteboardBackgroundColor** – standardbaggrundsfarve for tavle
- **DefaultWhiteboardBackgroundPattern** – standardbaggrundsmønster for bord
- **FlightStatus** – flightstatus
- **InkToShape** – aktivering af håndskrift til figur
- **InkToTable** – aktivering af håndskrift til tabel
- **SignInEnabled** – aktivering af brugerlogon
- **SharingWithoutSignInEnabled** – aktivering af delingstavle
- **ToolbarLocation** – standardplacering af værktøjslinjer på skærmen
- **TeamSettingsSource** – indstillingsaktivering for Teams
