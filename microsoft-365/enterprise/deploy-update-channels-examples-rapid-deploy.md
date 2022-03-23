---
title: Eksempel på bred udrulning af de nyeste versioner
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
ms.date: 07/21/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: ''
description: Hvordan en organisation, der installerer den nyeste version, bruger kanaler til Windows 10 og Microsoft 365 apps.
ms.openlocfilehash: 6b0226a226742a89dc65ca0d32792db03c77e465
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63588449"
---
# <a name="example-of-broad-deployment-for-the-latest-releases"></a>Eksempel på bred udrulning af de nyeste versioner

Dette eksempel på kanalkonfiguration er til en organisation, der anvender hurtig udrulning af de seneste udgivelser for at tilpasse sig disse virksomhedsprioriteter:

- Sikring af forretningskontinuitet med Microsoft-apps og -tjenester.
- Maksimér enheds-, tjeneste- og datasikkerhed med de nyeste funktioner og rettelser fra Microsoft.
- Maksimér brugerproduktiviteten med de nyeste funktioner fra Microsoft.

Disse mål omsættes til IT-opgaven med at finde balancen mellem hurtig produktionsinstallation og tidlig vetting med et repræsentativt undersæt af brugere og enheder for at validere funktionelt før bred udrulning.

Vores eksempelorganisation har 5.000 medarbejdere i bygninger over hele verden i Europa, Afrika, Asien og USA. 70 % af medarbejderne bruger Microsoft 365 E3, og resten af organisationen bruger Microsoft 365 E5.

>[!Note]
>Dette eksempel er beregnet til at vise dig, hvordan du kan bruge installationsfaser og grupper, som kan fungere for organisationer af mange typer og størrelser.
>

Organisationens it-infrastruktur: 

- Er i høj grad homogent med Windows, Microsoft 365 Apps og Microsoft-skytjenester, der omfatter 60 % af det installerede grundlager. Nogle få ældre systemer forbliver efter en intensiv, års indsats for at forenkle og strømline it-infrastrukturen.
- Vedligeholdes af meget erfarne medarbejdere og får til opgave at holde brugerne og deres enheder produktive og sikre ved at følge Microsofts kundeemne i deres udgivelser.

## <a name="deployment-and-update-stages"></a>Installations- og opdateringsfaser

Baseret på målene for hurtig installation i den nyeste version anvender dette eksempel en installationsproces i to trin.

1. **Brug en prøveversion eller en pilotinstallation:** Valider og iterate med tidlige ibrugere, it-medarbejdere, brugere med repræsentative konfigurationer og uddannelse af medarbejdere. 

   De tidlige brugere, it-medarbejdere, brugere med repræsentative konfigurationer kan validere funktionalitet med andre apps og på enheder, før de nye funktioner udrulles for resten af organisationen.

   Ledere har et smugkig på de nye funktioner, før den er udbredt, og de kan planlægge meddelelser og udrulning.

   Kursusmedarbejdere kan planlægge nye interne kurser eller opdatere eksisterende kurser for de nye funktioner, før den bliver udbredt.

2. **Produktionsinstallation:** Udrul til alle resterende brugere efter område, afdeling eller anden installationsmetode.

## <a name="deployment-configuration-for-windows-10"></a>Installationskonfiguration til Windows 10

Det overordnede mål er at udføre en bred udrulning af den nyeste version af Semi-Annual-kanalen efter validering af kanalændringer i Release Preview af en gruppe af repræsentative brugere og deres enheder.

Se [Windows 10 installation](/windows/deployment/) for at få mere at vide Windows 10 metoder og strategier for implementering.

| Fase | Kanal | Installationsgruppe |
|:-------|:-------|:-----|
| Pilot |  **Kanal til forhåndsvisning af udgivelse**  <ul><li>Formål: Installation af funktionsopdateringer til it-medarbejdere og tidlige brugere til validering på repræsentative enheder og konfigurationer (sprog, tredjepartsapps). </li><li> Stat: Fuldt kompatibelt og understøttet for kommercielle kunder, og det tæller ikke med i dine supportaftaler. </li></ul> | **Win10ReleasePreviewChannel** (eksempelnavn) <br><br> Medlemmer er grupper, der indeholder: <ul><li> Windows entusiaster på tværs af afdelinger og placeringer </li><li> Personale med konfigurationer, der skal valideres </li><li> It-administratorer og it-installationsmedarbejdere </li><li> Skift ledere </li><li> Interne uddannelsesmedarbejdere </li></ul> |
| Produktion |  **Halvårlige kanal**  <ul><li>Formål: Bred udrulning af de nyeste funktionsopdateringer til resten af organisationen. </li><li> Tilstand: Fuldt kompatibel og understøttet. </li></ul> | **Win10SemiAnnualChannel** (eksempelnavn) <br><br> Medlemmer er alle brugere, der ikke er i gruppen Win10ReleasePreviewChannel. |
||||

Denne organisation anvender den bedste fremgangsmåde til installation af kanalen Release Preview på samme måde, som de installerer Semi-Annual-kanaludgivelser, f.eks. Windows Update eller Windows Server Update Services, og at de anvender de samme politikker for begge kanalopdateringer.

Proces for løbende opdateringer:

1. Kanalændringer for udgivelseseksempel installeres i Installationsgruppen Win10ReleasePreviewChannel (eksempelnavn).
2. Win10ReleasePreviewChannel-gruppemedlemmerne bekræfter, at ændringer i Udgivelsesvisningskanalen fungerer for it-installationsmedarbejdere, som kan give feedback til Microsoft og vente på de næste ændringer for udgivelsesvisningskanalen for yderligere validering.
3. Semi-Annual kanalfunktionsændringer installeres i Win10SemiAnnualChannel-installationsgruppen. 

>[!Note]
>Selvom Semi-Annual-kanalen er den anbefalede kanal, bør din it-afdeling bruge deres administrationsværktøjer og fastlægge, hvornår den nyeste version af Semi-Annual-kanalen skal installeres i organisationen, og derefter udrulle den i runder.
>

## <a name="deployment-configuration-for-microsoft-365-apps"></a>Installationskonfiguration til Microsoft 365 Apps

Det overordnede mål er at udføre en bred udrulning af den seneste udgave af Aktuel kanal efter validering af ændringer i Aktuel kanal (forhåndsvisning) foretaget af en gruppe af repræsentative brugere.

Se [Microsoft 365 Apps installation](/deployoffice/plan-office-365-proplus) for at få mere at vide Microsoft 365 Apps metoder og strategier for implementering.

| Fase | Kanal | Installationsgruppe |
|:-------|:-------|:-----|
| Pilot |  **Aktuel kanal (forhåndsvisning)** <ul><li> Formål: {giv en gruppe af repræsentative brugere et smugkig på nye Microsoft 365 Apps-funktioner} Installation af funktionsopdateringer, så snart de er testet med brugere af Aktuel kanal (forhåndsvisning) og er produktionsklare. </li><li> Tilstand: Fuldt kompatibel og understøttet.</li><li> Hvor ofte: Opdateres 2-3 gange hver måned. </li></ul> | **AppsCurrentChannelPreview** (eksempelnavn) <br><br> Medlemmer er grupper, der indeholder: <ul><li> Office apps-entusiaster på tværs af afdelinger og placeringer </li><li> Personale med konfigurationer, der skal valideres </li><li> It-administratorer og it-installationsmedarbejdere </li><li> Skift ledere </li><li> Interne uddannelsesmedarbejdere </li></ul>|
| Produktion | **Aktuel kanal** <ul><li> Formål: Bred udrulning af de nyeste funktionsopdateringer til resten af organisationen. </li><li> Tilstand: Fuldt kompatibel og understøttet. </li></ul> |  **AppsCurrentChannel** (eksempelnavn) <br><br> Medlemmer er alle brugere, der ikke er i gruppen AppsCurrentChannelPreview. |
|||

Proces for løbende opdateringer:

1. Ændringer i Aktuel kanal (forhåndsvisning) installeres i installationsgruppen AppsCurrentChannelPreview.
2. AppsCurrentChannelPreview-gruppemedlemmer bekræfter, at ændringer i Aktuel kanal (forhåndsvisning) fungerer for it-installationsmedarbejdere, der kan give feedback til Microsoft og vente på den næste udgivelse af Aktuel kanal (forhåndsvisning) for at få yderligere validering.
3. Ændringer af aktuel kanal installeres i installationsgruppen AppsCurrentChannel. 

## <a name="visual-summary"></a>Visuel oversigt

Her er produkterne, deres kanaler og installationsgrupperne, der bruges af denne eksempelorganisation. 

![Installationsgrupper til bred udrulning af de nyeste versioner.](../media/deploy-update-channels-examples-rapid-deploy/group-summary.png)

## <a name="see-also"></a>Se også

[Eksempelkonfigurationer for installation og opdatering af kanal](deploy-update-channels-examples.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Test labvejledninger](m365-enterprise-test-lab-guides.md)