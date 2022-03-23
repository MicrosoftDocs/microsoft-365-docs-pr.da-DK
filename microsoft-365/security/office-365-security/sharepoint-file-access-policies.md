---
title: Anbefalede politikker for sikre dokumenter – Microsoft 365 til | Microsoft Docs
description: Beskriver politikkerne for Microsoft-anbefalinger om, hvordan du sikrer SharePoint adgang til filer.
ms.author: dansimp
author: dansimp
manager: dansimp
ms.prod: m365-security
ms.topic: article
audience: Admin
f1.keywords:
- NOCSH
ms.reviewer: martincoetzer
ms.custom:
- it-pro
- goldenconfig
ms.collection:
- M365-identity-device-management
- M365-security-compliance
- m365solution-identitydevice
- m365solution-scenario
ms.technology: mdo
ms.openlocfilehash: f024f9d93b44e6d6a679311af914330f0e3db37c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589835"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>Politikanbefalinger til sikring SharePoint websteder og filer

Denne artikel beskriver, hvordan du implementerer de anbefalede politikker for nultillidsidentitet og enhedsadgang for at beskytte SharePoint og OneDrive for Business. Denne vejledning er baseret på de almindelige [politikker for identitet og enhedsadgang](identity-access-policies.md).

Disse anbefalinger er baseret på tre forskellige niveauer af sikkerhed og beskyttelse til SharePoint-filer, der kan anvendes baseret på granulariteten af dine behov: **udgangspunkt****, virksomhed** og **særlig sikkerhed**. Du kan få mere at vide om disse sikkerhedsniveauer og de anbefalede klientoperativsystemer, der refereres til i disse anbefalinger [i oversigten](microsoft-365-policies-configurations.md).

Ud over at implementere denne vejledning skal du sørge for at konfigurere SharePoint-websteder med den rette beskyttelse, herunder at angive relevante tilladelser til virksomhedssikkerhedsindhold og specialiseret sikkerhedsindhold.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>Opdatering af almindelige politikker, så de SharePoint og OneDrive for Business

For at beskytte filer i SharePoint og OneDrive viser nedenstående diagram, hvilke politikker der skal opdateres fra de fælles identitets- og enhedsadgangspolitikker.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png" alt-text="Oversigt over politikopdateringer til beskyttelse af adgang til SharePoint." lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png":::

Hvis du med SharePoint, da du oprettede de fælles politikker, behøver du kun at oprette de nye politikker. I forbindelse med politikker for betinget adgang SharePoint følgende OneDrive.

De nye politikker implementerer enhedsbeskyttelse til virksomheds- og specialsikkerhedsindhold ved at anvende specifikke adgangskrav til SharePoint, du angiver.

I følgende tabel vises de politikker, du enten skal gennemse og opdatere, eller oprette en ny SharePoint. De fælles politikker linker til de tilknyttede konfigurationsinstruktioner i [artiklen Fælles identitets- og enhedsadgangspolitikker](identity-access-policies.md) .

|Beskyttelsesniveau|Politikker|Flere oplysninger|
|---|---|---|
|**Udgangspunkt**|[Kræv MFA, når logonrisici er *mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Medtag SharePoint i tildelingen af skyapps.|
||[Blokere klienter, der ikke understøtter moderne godkendelse](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Medtag SharePoint i tildelingen af skyapps.|
||[Anvend politikker for beskyttelse af app-data](identity-access-policies.md#apply-app-data-protection-policies)|Sørg for, at alle anbefalede apps er inkluderet på listen over apps. Sørg for at opdatere politikken for hver platform (iOS, Android, Windows).|
||[Brug tvungne appbegrænsninger i SharePoint](#use-app-enforced-restrictions-in-sharepoint)|Tilføj denne nye politik. Dette giver Azure Active Directory (Azure AD) besked om at bruge de indstillinger, der er angivet SharePoint. Denne politik gælder for alle brugere, men påvirker kun adgang til websteder, der er inkluderet SharePoint adgangspolitikker.|
|**Enterprise**|[Kræv MFA, når risikoen for at logge *på er* *lav, mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Medtag SharePoint opgaver fra skyapps.|
||[Kræv kompatible *pc'er* og mobilenheder](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Medtag SharePoint på listen over skyapps.|
||[SharePoint politik for adgangskontrol](#sharepoint-access-control-policies): Tillad kun browseradgang til bestemte SharePoint fra enheder, der ikke er administrerede.|Dette forhindrer redigering og hentning af filer. Brug PowerShell til at angive websteder.|
|**Speciel sikkerhed**|[*Kræv* altid MFA](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Medtag SharePoint i tildelingen af skyapps.|
||[SharePoint for adgangskontrol](#use-app-enforced-restrictions-in-sharepoint): Bloker adgangen til bestemte SharePoint fra enheder, der ikke er administrerede.|Brug PowerShell til at angive websteder.|
|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>Brug app-tvungne begrænsninger i SharePoint

Hvis du implementerer adgangskontrolelementer i SharePoint, skal du oprette denne Politik for betinget adgang i Azure AD for at bede Azure AD om at håndhæve de politikker, du konfigurerer i SharePoint. Denne politik gælder for alle brugere, men påvirker kun adgangen til de websteder, du angiver ved hjælp af PowerShell, når du opretter adgangskontrollerne SharePoint.

Hvis du vil konfigurere denne politik, skal du se "Bloker eller begræns adgangen til bestemte SharePoint grupper af websteder eller OneDrive-konti" i Kontrollere adgang fra enheder, der ikke [er administrerede](/sharepoint/control-access-from-unmanaged-devices).

## <a name="sharepoint-access-control-policies"></a>SharePoint politikker for adgangskontrol

Microsoft anbefaler, at du beskytter indholdet på SharePoint med virksomheds- og specialsikkerhedsindhold med kontrolelementer til enhedsadgang. Det gør du ved at oprette en politik, der angiver beskyttelsesniveauet og de websteder, beskyttelsen skal anvendes på.

- Virksomhedswebsteder: Tillad kun browseradgang. Dette forhindrer brugere i at redigere og downloade filer.
- Specialiserede sikkerhedswebsteder: Bloker adgang fra enheder, der ikke er administrerede.

Se "Bloker eller begræns adgangen til bestemte SharePoint grupper af websteder eller OneDrive-konti" i Kontrollere adgang fra [enheder, der ikke er administrerede](/sharepoint/control-access-from-unmanaged-devices).

## <a name="how-these-policies-work-together"></a>Sådan fungerer disse politikker sammen

Det er vigtigt at forstå, SharePoint webstedstilladelser typisk er baseret på forretningsmæssige behov for adgang til websteder. Disse tilladelser administreres af webstedsejere og kan være meget dynamiske. Brug SharePoint politikker for enhedsadgang sikrer beskyttelse af disse websteder, uanset om brugerne er tildelt til en Azure AD-gruppe, der er knyttet til startpunkt, virksomhed eller særlig sikkerhedsbeskyttelse.

Følgende illustration er et eksempel på, hvordan SharePoint adgangspolitikker for enheder beskytter en brugers adgang til websteder.

:::image type="content" source="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png" alt-text="Eksempel på, SharePoint politikker for enhedsadgang beskytter websteder." lightbox="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png":::

James har fået tildelt betingede adgangspolitikker som udgangspunkt, men han kan få adgang til SharePoint websteder med virksomheds- eller særlig sikkerhedsbeskyttelse.

- Hvis James får adgang til et websted, han er medlem af med Enterprise eller særlig sikkerhedsbeskyttelse ved hjælp af sin pc, får han adgang.
- Hvis James åbner et virksomhedsbeskyttelseswebsted, som han er medlem af ved hjælp af sin ikke-administrerede telefon, som er tilladt for startbrugere, modtager han kun browseradgang til virksomhedswebstedet på grund af politikken for enhedsadgang, der er konfigureret for dette websted.
- Hvis James får adgang til et særligt sikkerhedswebsted, som han er medlem af ved hjælp af sin ikke-administrerede telefon, blokeres han på grund af den adgangspolitik, der er konfigureret for dette websted. Han kan kun få adgang til dette websted ved hjælp af sin administrerede pc.

## <a name="next-step"></a>Næste trin

![Trin 4: Politikker for Microsoft 365 skyapps.](../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png)

Konfigurere Betingede adgangspolitikker for:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)