---
title: Eksempel på bred udrulning for de nyeste udgivelser
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
ms.date: 07/21/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Strat_O365_Enterprise
- M365-subscription-management
ms.custom: ''
description: Den måde, en organisation udruller den seneste version på, bruger kanaler til Windows 10 og Microsoft 365 apps.
ms.openlocfilehash: 43cd5deed9801de6ff044781bebf9d96cdac7c12
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754704"
---
# <a name="example-of-broad-deployment-for-the-latest-releases"></a>Eksempel på bred udrulning for de nyeste udgivelser

Dette eksempel på kanalkonfiguration er til en organisation, der bruger hurtig udrulning af de nyeste udgivelser, så de passer til disse forretningsprioriteter:

- Sørg for forretningskontinuitet med Microsoft-apps og -tjenester.
- Maksimer enheds-, tjeneste- og datasikkerhed med de nyeste funktioner og rettelser fra Microsoft.
- Maksimer brugernes produktivitet med de nyeste funktioner fra Microsoft.

Disse mål betyder, at it-opgaven med at finde balancen mellem hurtig produktionsudrulning og tidlig kontrol med et repræsentativt undersæt af brugere og enheder for at validere funktionelt før en bred udrulning.

Vores eksempelorganisation har 5.000 medarbejdere i bygninger over hele verden i Europa, Afrika, Asien og Amerika. 70 % af medarbejderne bruger Microsoft 365 E3, og resten af organisationen bruger Microsoft 365 E5.

>[!Note]
>Dette eksempel er designet til at vise dig, hvordan du kan bruge udrulningsfaser og -grupper, som kan fungere for organisationer af mange typer og størrelser.
>

Denne organisations it-infrastruktur: 

- Er stort set homogen med Windows, Microsoft 365 Apps og Microsoft-cloudtjenester, der består af 60 % af den installerede base. Der er nogle få ældre systemer tilbage efter en intensiv og flerårig indsats for at forenkle og strømline it-infrastrukturen.
- Vedligeholdes af meget erfarne medarbejdere og har til opgave at holde brugerne og deres enheder produktive og sikre ved at følge Microsofts forspring i deres udgivelser.

## <a name="deployment-and-update-stages"></a>Udrulnings- og opdateringsfaser

Baseret på målene for hurtig udrulning i den seneste version bruger organisationen i dette eksempel en udrulningsproces med to trin.

1. **Brug en prøveversion eller en pilotinstallation:** Valider og gentage med tidlige brugere, it-medarbejdere, brugere med repræsentative konfigurationer og oplæringspersonale. 

   De tidlige brugere, it-medarbejdere og brugere med repræsentative konfigurationer kan validere funktionaliteten med andre apps og på enheder, før de nye funktioner udrulles til resten af organisationen.

   Ændringsadministratorer har et tidligt smugkig på de nye funktioner før omfattende udrulning og kan planlægge beskeder og udrulning.

   Oplæringspersonalet kan planlægge nye interne kurser eller opdatere eksisterende kurser for de nye funktioner, før udrulningen er udbredt.

2. **Udrulning af produktion:** Udrulning til alle resterende brugere efter område, afdeling eller anden udrulningsmetode.

## <a name="deployment-configuration-for-windows-10"></a>Udrulningskonfiguration for Windows 10

Det overordnede mål er at udføre en bred udrulning af den seneste udgivelse af Semi-Annual Channel efter validering af ændringer i udgivelseseksemplet af en gruppe repræsentative brugere og deres enheder.

Se [Windows 10 udrulning](/windows/deployment/) for at få flere oplysninger om Windows 10 udrulningsmetoder og -strategier.

| Fase | Kanal | Udrulningsgruppe |
|:-------|:-------|:-----|
| Pilot |  **Udgivelseskanal til eksempelvisning**  <ul><li>Formål: Installation af funktionsopdateringer til it-medarbejdere og tidlige adoptører til validering på repræsentative enheder og konfigurationer (sprog, tredjepartsapps). </li><li> Tilstand: Fuldt kompatibel og understøttet for kommercielle kunder, og det tæller ikke i forhold til dine supportaftaler. </li></ul> | **Win10ReleasePreviewChannel** (eksempelnavn) <br><br> Medlemmer er grupper, der indeholder: <ul><li> Windows entusiaster på tværs af afdelinger og steder </li><li> Medarbejdere med konfigurationer, der skal valideres </li><li> It-administratorer og it-installationspersonale </li><li> Skift ledere </li><li> Interne uddannelsespersonale </li></ul> |
| Produktion |  **Halvårlig kanal**  <ul><li>Formål: Bred udrulning af de nyeste funktionsopdateringer til resten af organisationen. </li><li> Tilstand: Fuldt kompatibel og understøttet. </li></ul> | **Win10SemiAnnualChannel** (eksempelnavn) <br><br> Medlemmer er alle brugere, der ikke er i gruppen Win10ReleasePreviewChannel. |
||||

Denne organisation bruger bedste praksis for udrulning af nyttedata for udgivelseseksempler på samme måde, som de installerer Semi-Annual kanalversioner, f.eks. Windows Update eller Windows Server Update Services, og at de anvender de samme politikker for begge kanalopdateringer.

Igangværende opdateringsproces:

1. Ændringer af udgivelseskanalen installeres i udrulningsgruppen Win10ReleasePreviewChannel (eksempelnavn).
2. Gruppemedlemmer af Win10ReleasePreviewChannel bekræfter, at ændringer i udgivelseseksemplet af kanalen fungerer for it-installationspersonalet, som kan give feedback til Microsoft og vente på, at de næste ændringer i Udgivelseseksemplets kanal ændres med henblik på yderligere validering.
3. Semi-Annual kanalfunktionsændringer installeres i win10SemiAnnualChannel-installationsgruppen. 

>[!Note]
>Selvom Semi-Annual-kanalen er den anbefalede kanal, skal it-afdelingen bruge deres administrationsværktøjer og bestemme, hvornår den seneste udgivelse af Semi-Annual kanal skal udrulles i organisationen, og derefter udrulle den i bølger.
>

## <a name="deployment-configuration-for-microsoft-365-apps"></a>Udrulningskonfiguration for Microsoft 365 Apps

Det overordnede mål er at udføre en bred udrulning af den seneste version af den aktuelle kanal efter validering af ændringer i den aktuelle kanal (prøveversion) af en gruppe repræsentative brugere.

Se [Microsoft 365 Apps udrulning](/deployoffice/plan-office-365-proplus) for at få flere oplysninger om Microsoft 365 Apps udrulningsmetoder og -strategier.

| Fase | Kanal | Udrulningsgruppe |
|:-------|:-------|:-----|
| Pilot |  **Aktuel kanal (prøveversion)** <ul><li> Formål: {Giv en gruppe repræsentative brugere et smugkig på nye Microsoft 365 Apps funktioner} Udrulning af funktionsopdateringer, så snart de testes med brugere af den aktuelle kanal (prøveversion) og er klar til produktion. </li><li> Tilstand: Fuldt kompatibel og understøttet.</li><li> Hvor ofte: Opdaterer 2-3 gange hver måned. </li></ul> | **AppsCurrentChannelPreview** (eksempelnavn) <br><br> Medlemmer er grupper, der indeholder: <ul><li> Office apps-entusiaster på tværs af afdelinger og steder </li><li> Medarbejdere med konfigurationer, der skal valideres </li><li> It-administratorer og it-installationspersonale </li><li> Skift ledere </li><li> Interne uddannelsespersonale </li></ul>|
| Produktion | **Aktuel kanal** <ul><li> Formål: Bred udrulning af de nyeste funktionsopdateringer til resten af organisationen. </li><li> Tilstand: Fuldt kompatibel og understøttet. </li></ul> |  **AppsCurrentChannel** (eksempelnavn) <br><br> Medlemmer er alle brugere, der ikke er i gruppen AppsCurrentChannelPreview. |
|||

Igangværende opdateringsproces:

1. Ændringer af den aktuelle kanal (prøveversion) installeres i installationsgruppen AppsCurrentChannelPreview.
2. Medlemmer af gruppen AppsCurrentChannelPreview bekræfter, at ændringer af den aktuelle kanal (prøveversion) fungerer for it-installationspersonalet, som kan give feedback til Microsoft og vente på den næste version af Den aktuelle kanal (prøveversion) med henblik på yderligere validering.
3. De aktuelle kanalændringer installeres i installationsgruppen AppsCurrentChannel. 

## <a name="visual-summary"></a>Visuel oversigt

Her er de produkter, deres kanaler og de udrulningsgrupper, der bruges af denne eksempelorganisation. 

![Udrulningsgrupper til bred udrulning af de nyeste udgivelser.](../media/deploy-update-channels-examples-rapid-deploy/group-summary.png)

## <a name="see-also"></a>Se også

[Konfigurationer af eksempel på udrulning og opdatering af kanal](deploy-update-channels-examples.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Vejledninger til testlaboratorier](m365-enterprise-test-lab-guides.md)