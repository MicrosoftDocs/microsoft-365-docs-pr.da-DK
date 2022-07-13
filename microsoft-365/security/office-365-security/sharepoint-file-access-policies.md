---
title: Anbefalede sikre dokumentpolitikker – Microsoft 365 for enterprise-| Microsoft Docs
description: Beskriver politikkerne for Microsoft-anbefalinger om, hvordan du sikrer SharePoint-filadgang.
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
- zerotrust-solution
ms.technology: mdo
ms.openlocfilehash: e0ca69eb4a330c4ebb067d657d0fdef8a4d09d8b
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/12/2022
ms.locfileid: "66750006"
---
# <a name="policy-recommendations-for-securing-sharepoint-sites-and-files"></a>Politikanbefalinger til sikring af SharePoint-websteder og -filer

I denne artikel beskrives det, hvordan du implementerer de anbefalede Nul tillid identitets- og enhedsadgangspolitikker for at beskytte SharePoint og OneDrive for Business. Denne vejledning bygger på de [fælles politikker for identitets- og enhedsadgang](identity-access-policies.md).

Disse anbefalinger er baseret på tre forskellige niveauer af sikkerhed og beskyttelse af SharePoint-filer, der kan anvendes baseret på granulariteten af dine behov: **udgangspunkt**, **virksomhed** og **specialiseret sikkerhed**. Du kan få mere at vide om disse sikkerhedsniveauer og de anbefalede klientoperativsystemer, som disse anbefalinger refererer [til, i oversigten](microsoft-365-policies-configurations.md).

Ud over at implementere denne vejledning skal du sørge for at konfigurere SharePoint-websteder med den rigtige beskyttelse, herunder angivelse af relevante tilladelser til virksomhedsindhold og specialiseret sikkerhedsindhold.

## <a name="updating-common-policies-to-include-sharepoint-and-onedrive-for-business"></a>Opdatering af almindelige politikker, så de omfatter SharePoint og OneDrive for Business

For at beskytte filer i SharePoint og OneDrive illustrerer følgende diagram, hvilke politikker der skal opdateres fra de fælles politikker for identitet og adgang til enheder.

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png" alt-text="Oversigten over politikopdateringer til beskyttelse af adgangen til SharePoint" lightbox="../../media/microsoft-365-policies-configurations/identity-access-ruleset-sharepoint.png":::

Hvis du inkluderede SharePoint, da du oprettede de fælles politikker, skal du kun oprette de nye politikker. I forbindelse med politikker for betinget adgang inkluderer SharePoint OneDrive.

De nye politikker implementerer enhedsbeskyttelse for virksomhedsindhold og specialiseret sikkerhedsindhold ved at anvende specifikke adgangskrav til SharePoint-websteder, som du angiver.

I følgende tabel vises de politikker, du enten har brug for at gennemse og opdatere eller oprette nye til SharePoint. De fælles politikker linker til de tilknyttede konfigurationsinstruktioner i artiklen [Fælles politikker for identitets- og enhedsadgang](identity-access-policies.md) .

|Beskyttelsesniveau|Politikker|Flere oplysninger|
|---|---|---|
|**Udgangspunkt**|[Kræv MFA, når logonrisikoen er *mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Medtag SharePoint i tildelingen af cloudapps.|
||[Bloker klienter, der ikke understøtter moderne godkendelse](identity-access-policies.md#block-clients-that-dont-support-multi-factor)|Medtag SharePoint i tildelingen af cloudapps.|
||[Anvend politikker for databeskyttelse i APP](identity-access-policies.md#apply-app-data-protection-policies)|Sørg for, at alle anbefalede apps er inkluderet på listen over apps. Sørg for at opdatere politikken for hver platform (iOS, Android, Windows).|
||[Brug gennemtvungne begrænsninger for apps i SharePoint](#use-app-enforced-restrictions-in-sharepoint)|Tilføj denne nye politik. Dette fortæller Azure Active Directory (Azure AD) om at bruge de indstillinger, der er angivet i SharePoint. Denne politik gælder for alle brugere, men påvirker kun adgang til websteder, der er inkluderet i SharePoint-adgangspolitikker.|
|**Enterprise**|[Kræv MFA, når logonrisikoen er *lav*, *mellem* eller *høj*](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Medtag SharePoint i tildelinger af cloudapps.|
||[Kræv kompatible pc'er *og* mobilenheder](identity-access-policies.md#require-compliant-pcs-and-mobile-devices)|Medtag SharePoint på listen over cloudapps.|
||[SharePoint-politik for adgangskontrol](#sharepoint-access-control-policies): Tillad kun browseradgang til bestemte SharePoint-websteder fra ikke-administrerede enheder.|Dette forhindrer redigering og download af filer. Brug PowerShell til at angive websteder.|
|**Specialiseret sikkerhed**|[*Kræv altid* MFA](identity-access-policies.md#require-mfa-based-on-sign-in-risk)|Medtag SharePoint i tildelingen af cloudapps.|
||[SharePoint-politik for adgangskontrol](#use-app-enforced-restrictions-in-sharepoint): Bloker adgang til bestemte SharePoint-websteder fra ikke-administrerede enheder.|Brug PowerShell til at angive websteder.|

## <a name="use-app-enforced-restrictions-in-sharepoint"></a>Brug app-gennemtvungne begrænsninger i SharePoint

Hvis du implementerer adgangskontrolelementer i SharePoint, oprettes politikker for betinget adgang i Azure AD for at fortælle Azure AD at gennemtvinge de politikker, du konfigurerer i SharePoint. Denne politik gælder som standard for alle brugere, men påvirker kun adgangen til de websteder, du angiver ved hjælp af PowerShell, når du opretter adgangskontrolelementerne i SharePoint. Politikken kan også være begrænset til bestemte brugere, grupper eller websteder.

Hvis du vil konfigurere denne politik, skal du se "Bloker eller begræns adgang til bestemte Grupper af SharePoint-websteder eller OneDrive-konti" i [Kontrollér adgang fra ikke-administrerede enheder](/sharepoint/control-access-from-unmanaged-devices).

## <a name="sharepoint-access-control-policies"></a>Politikker for adgangskontrol i SharePoint

Microsoft anbefaler, at du beskytter indhold på SharePoint-websteder med virksomhedsindhold og specialiseret sikkerhedsindhold med kontrolelementer for enhedsadgang. Det gør du ved at oprette en politik, der angiver det beskyttelsesniveau og de websteder, som beskyttelsen skal anvendes på.

- Virksomhedswebsteder: Tillad kun browseradgang. Dette forhindrer brugerne i at redigere og downloade filer.
- Specialiserede sikkerhedswebsteder: Bloker adgang fra ikke-administrerede enheder.

Se "Bloker eller begræns adgang til bestemte Grupper af SharePoint-websteder eller OneDrive-konti" i [Kontrollér adgang fra ikke-administrerede enheder](/sharepoint/control-access-from-unmanaged-devices).

## <a name="how-these-policies-work-together"></a>Sådan arbejder disse politikker sammen

Det er vigtigt at forstå, at sharePoint-webstedstilladelser typisk er baseret på virksomhedens behov for adgang til websteder. Disse tilladelser administreres af webstedsejere og kan være meget dynamiske. Brug af politikker for enhedsadgang til SharePoint sikrer beskyttelse af disse websteder, uanset om brugerne er tildelt til en Azure AD gruppe, der er knyttet til startpunkt, virksomhed eller specialiseret sikkerhedsbeskyttelse.

Følgende illustration indeholder et eksempel på, hvordan politikker for adgang til SharePoint-enheder beskytter en brugers adgang til websteder.

:::image type="content" source="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png" alt-text="Et eksempel på, hvordan politikker for adgang til SharePoint-enheder beskytter websteder" lightbox="../../media/microsoft-365-policies-configurations/SharePoint-rules-scenario.png":::

James har fået tildelt politikker for betinget adgang, men han kan få adgang til SharePoint-websteder med virksomheds- eller specialiseret sikkerhedsbeskyttelse.

- Hvis James tilgår et websted, han er medlem af med enterprise eller specialiseret sikkerhedsbeskyttelse ved hjælp af sin pc, er hans adgang tildelt.
- Hvis James tilgår et websted til beskyttelse af virksomheder, som han er medlem af, ved hjælp af sin ikke-administrerede telefon, hvilket er tilladt for startpunktbrugere, vil han modtage browseradgang til virksomhedswebstedet på grund af den politik for enhedsadgang, der er konfigureret for dette websted.
- Hvis James tilgår et særligt sikkerhedswebsted, han er medlem af, ved hjælp af sin ikke-administrerede telefon, blokeres han på grund af den adgangspolitik, der er konfigureret for dette websted. Han kan kun få adgang til dette websted ved hjælp af sin administrerede pc.

## <a name="next-step"></a>Næste trin

:::image type="content" source="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png" alt-text="Trin 4 – Politikker for Microsoft 365-cloudapps" lightbox="../../media/microsoft-365-policies-configurations/identity-device-access-steps-next-step-4.png":::

Konfigurer politikker for betinget adgang for:

- [Microsoft Teams](teams-access-policies.md)
- [Exchange Online](secure-email-recommended-policies.md)
