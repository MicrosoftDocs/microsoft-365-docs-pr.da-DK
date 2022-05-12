---
title: Nul tillid udrulningsplan i Microsoft 365
f1.keywords:
- deploy zero trust
- zero trust strategy
ms.author: bcarter
author: brendacarter
manager: dansimp
audience: Admin
description: Få mere at vide om, hvordan du udruller Microsoft 365 Nul tillid sikkerhed i dit miljø for at forsvare dig mod trusler og beskytte følsomme data.
ms.topic: tutorial
ms.prod: m365-security
ms.technology: m365d
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- m365solution-zerotrust
- m365solution-overview
- M365-security-compliance
ms.openlocfilehash: bb452c74763e31be11a6431cc260667319d2582f
ms.sourcegitcommit: 570c3be37b6ab1d59a4988f7de9c9fb5ca38028f
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/12/2022
ms.locfileid: "65363186"
---
# <a name="microsoft-365-zero-trust-deployment-plan"></a>Nul tillid udrulningsplan i Microsoft 365

Denne artikel indeholder en udrulningsplan til opbygning **Nul tillid** sikkerhed med Microsoft 365. Nul tillid er en ny sikkerhedsmodel, der forudsætter brud og kontrollerer hver anmodning, som om den stammer fra et ikke-kontrolleret netværk. Uanset hvor anmodningen stammer fra, eller hvilken ressource den får adgang til, lærer Nul tillid-modellen os at "hav aldrig tillid til, bekræft altid".

Brug denne artikel sammen med denne plakat.

| Element | Beskrivelse |
|:-----|:-----|
|[![Illustration af Microsoft 365 Nul tillid udrulningsplan.](../media/solutions-architecture-center/m365-zero-trust-deployment-plan-thumb.png) ](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.pdf) <br/> [PDF](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.pdf) \| [Visio](https://download.microsoft.com/download/f/d/b/fdb6ab0c-34bb-4cb8-84e6-5de8f13298da/m365-zero-trust-deployment-plan.vsdx) <br/> Opdateret marts 2022 | **Relaterede løsningsvejledninger** <br/> <ul><li>[Udrul din identitetsinfrastruktur til Microsoft 365](/microsoft-365/enterprise/deploy-identity-solution-overview)</li><li>[Anbefalede konfigurationer for identitet og enhedsadgang](../security/office-365-security/microsoft-365-policies-configurations.md)</li><li>[Administrer enheder med Intune](../solutions/manage-devices-with-intune-overview.md)</li><li>[Evaluer og test Microsoft 365 Defender](../security/defender/eval-overview.md)</li><li>[Installér en Microsoft Information Protection løsning](../compliance/information-protection-solution.md)</li><li>[Udrul beskyttelse af oplysninger i forbindelse med bestemmelser om beskyttelse af personlige oplysninger med Microsoft 365](../solutions/information-protection-deploy.md)</li></ul>

## <a name="zero-trust-security-architecture"></a>Nul tillid sikkerhedsarkitektur

En Nul tillid tilgang strækker sig over hele den digitale ejendom og fungerer som en integreret sikkerhedsfilosofi og end-to-end-strategi.

Denne illustration indeholder en repræsentation af de primære elementer, der bidrager til Nul tillid.

:::image type="content" source="../media/zero-trust/zero-trust-architecture.png" alt-text="Sikkerhedsarkitekturen Nul tillid" lightbox="../media/zero-trust/zero-trust-architecture.png":::

I illustrationen:

- Håndhævelse af sikkerhedspolitik er midt i en Nul tillid arkitektur. Dette omfatter multifaktorgodkendelse med betinget adgang, der tager højde for brugerkontorisici, enhedsstatus og andre kriterier og politikker, som du angiver.
- Identiteter, enheder, data, apps, netværk og andre infrastrukturkomponenter er alle konfigureret med den relevante sikkerhed. Politikker, der er konfigureret for hver af disse komponenter, koordineres med din overordnede Nul tillid strategi. Enhedspolitikker bestemmer f.eks. kriterierne for sunde enheder, og politikker for betinget adgang kræver sunde enheder for at få adgang til bestemte apps og data.
- Trusselsbeskyttelse og -intelligens overvåger miljøet, viser aktuelle risici og udfører automatiserede handlinger for at afhjælpe angreb.

<!---
For more information about this architecture, including deployment objectives for your entire digital estate, see [Zero Trust Rapid Modernization Plan (RaMP)](https://review.docs.microsoft.com/security/zero-trust/zero-trust-ramp-overview?branch=zt-content-prototype).
-->

Du kan finde flere oplysninger om Nul tillid i Microsofts [_**Nul tillid Guidance Center**_](/security/zero-trust).

## <a name="deploying-zero-trust-for-microsoft-365"></a>Installerer Nul tillid til Microsoft 365

Microsoft 365 er bygget bevidst med mange funktioner til beskyttelse af sikkerhed og oplysninger, der kan hjælpe dig med at bygge Nul tillid i dit miljø. Mange af funktionerne kan udvides for at beskytte adgangen til andre SaaS-apps, som din organisation bruger, og dataene i disse apps.

Denne illustration repræsenterer arbejdet med at udrulle Nul tillid egenskaber. Dette arbejde opdeles i arbejdsenheder, der kan konfigureres sammen fra bunden og arbejder til toppen for at sikre, at det påkrævede arbejde er fuldført.

:::image type="content" source="../media/zero-trust/m365-zero-trust-deployment-stack.png" alt-text="Den Microsoft 365 Nul tillid udrulningsstak" lightbox="../media/zero-trust/m365-zero-trust-deployment-stack.png":::

I denne illustration:

- Nul tillid begynder med et fundament af identitets- og enhedsbeskyttelse.
- Trusselsbeskyttelsesfunktioner er bygget oven på dette fundament for at levere overvågning og afhjælpning af sikkerhedstrusler i realtid.
- Beskyttelse og styring af oplysninger leverer avancerede kontroller, der er målrettet til bestemte typer data, for at beskytte dine mest værdifulde oplysninger og for at hjælpe dig med at overholde angivne standarder, herunder beskyttelse af personlige oplysninger.

## <a name="step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies"></a>Trin 1. Konfigurer Nul tillid beskyttelse af identitet og enhedsadgang – startpunktspolitikker

Det første trin er at opbygge dit Nul tillid fundament ved at konfigurere beskyttelse mod identitets- og enhedsadgang.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-1b.png" alt-text="Processen til konfiguration af Nul tillid identitets- og enhedsadgangsbeskyttelse" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-1b.png":::

Gå til [**_Nul tillid beskyttelse af identitet og enhedsadgang_**](office-365-security/microsoft-365-policies-configurations.md) for at få en præskriptiv vejledning til at opnå dette. I denne artikelserie beskrives et sæt konfigurationer af forudsætninger for identitet og adgang til enheden og et sæt Azure Active Directory (Azure AD) betinget adgang, Microsoft Intune og andre politikker, der sikrer adgang til Microsoft 365  til cloudapps og -tjenester til virksomheder, andre SaaS-tjenester og programmer i det lokale miljø, der er publiceret med Azure AD Programproxy.

|Omfatter|Forudsætninger|Omfatter ikke|
|---------|---------|---------|
|Anbefalede politikker for identitets- og enhedsadgang for tre beskyttelsesniveauer: <ul><li>Udgangspunkt</li><li>Enterprise (anbefales)</li><li>Specialiseret</li></ul> <br> Yderligere anbefalinger til: <ul><li>Eksterne brugere (gæster)</li><li>Microsoft Teams</li><li>SharePoint Online</li><li>Microsoft Defender for Cloud Apps</lu></ul>|Microsoft E3 eller E5 <br><br> Azure Active Directory i en af disse tilstande: <ul><li>Kun i skyen</li><li>Hybrid med PHS-godkendelse (Password Hash Sync)</li><li>Hybrid med pass-through-godkendelse (PTA)</li><li>Sammenkædet</li></ul>|Enhedsregistrering for politikker, der kræver administrerede enheder. Se [trin 2. Administrer slutpunkter med Intune](#step-2-manage-endpoints-with-intune) til at tilmelde enheder|

Start med at implementere startpunktniveauet. Disse politikker kræver ikke, at enheder tilmeldes administration.

:::image type="content" source="../media/zero-trust/identity-access-starting-point-tier.png" alt-text="Politikkerne for Nul tillid identitet og enhedsadgang – startpunktsniveau" lightbox="../media/zero-trust/identity-access-starting-point-tier.png":::

## <a name="step-2-manage-endpoints-with-intune"></a>Trin 2. Administrer slutpunkter med Intune

Derefter skal du tilmelde dine enheder til administration og begynde at beskytte dem med mere avancerede kontrolelementer.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-step-2.png" alt-text="Administrer slutpunkter med Intune element" lightbox="../media/zero-trust/m365-zero-trust-architecture-step-2.png":::

Gå til [**_Administrer enheder med Intune_**](../solutions/manage-devices-with-intune-overview.md) for at få en præskriptiv vejledning til at opnå dette.

|Omfatter|Forudsætninger|Omfatter ikke|
|---------|---------|---------|
|Tilmeld enheder med Intune: <ul><li>Virksomhedsejede enheder</li><li>Autopilot/automatiseret</li><li>Tilmelding</li></ul> <br> Konfigurer politikker: <ul><li>Politikker for appbeskyttelse</li><li>Politikker for overholdelse af regler og standarder</li><li>Politikker for enhedsprofil</li></ul>|Registrer slutpunkter med Azure AD|Konfiguration af funktioner til beskyttelse af oplysninger, herunder: <ul><li>Typer af følsomme oplysninger</li><li>Etiketter</li><li>DLP-politikker</li></ul> <br> Du kan se disse funktioner [under Trin 5. Beskyt og styr følsomme data](#step-5-protect-and-govern-sensitive-data) (senere i denne artikel).|

## <a name="step-3-add-zero-trust-identity-and-device-access-protection--enterprise-policies"></a>Trin 3. Tilføj Nul tillid beskyttelse af identitet og enhedsadgang – virksomhedspolitikker

Med enheder, der er tilmeldt administration, kan du nu implementere det fulde sæt anbefalede Nul tillid politikker for identitet og enhedsadgang, hvilket kræver kompatible enheder.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png" alt-text="Politikkerne for Nul tillid identitet og adgang med enhedshåndtering" lightbox="../media/zero-trust/m365-zero-trust-architecture-enterprise-policies.png":::

Vend tilbage til [**_Almindelige politikker for identitets- og enhedsadgang_**](office-365-security/identity-access-policies.md) , og tilføj politikkerne på virksomhedsniveau.

:::image type="content" source="../media/zero-trust/identity-access-enterprise-tier.png" alt-text="Politikkerne for Nul tillid identitet og adgang – virksomhedsniveau (anbefales)" lightbox="../media/zero-trust/identity-access-enterprise-tier.png":::

## <a name="step-4-evaluate-pilot-and-deploy-microsoft-365-defender"></a>Trin 4. Evaluer, pilot og udrul Microsoft 365 Defender

Microsoft 365 Defender er en udvidet løsning til registrering og svar (XDR), der automatisk indsamler, korrelerer og analyserer signal-, trussels- og beskeddata fra hele dit Microsoft 365 miljø, herunder slutpunkt, mail, programmer og identiteter.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-defender.png" alt-text="Processen med at føje Microsoft 365 Defender til Nul tillid-arkitekturen" lightbox="../media/zero-trust/m365-zero-trust-architecture-defender.png":::

Gå til [**_Evaluer og pilot Microsoft 365 Defender_**](defender/eval-overview.md) for at få en metodisk vejledning i test og installation af Microsoft 365 Defender komponenter.

|Omfatter|Forudsætninger|Omfatter ikke|
|---------|---------|---------|
|Konfigurer evaluerings- og pilotmiljøet for alle komponenter: <ul><li>Defender for Identity</li><li>Defender for Office 365</li><li>Defender for Endpoint</li><li>Microsoft Defender for Cloud Apps</li></ul> <br> Beskyt mod trusler <br><br> Undersøg og reager på trusler|Se vejledningen for at læse om arkitekturkravene for hver komponent i Microsoft 365 Defender.| Azure AD Identitetsbeskyttelse er ikke inkluderet i denne løsningsvejledning. Den er inkluderet i [trin 1. Konfigurer Nul tillid beskyttelse mod identitet og enhedsadgang](#step-1-configure-zero-trust-identity-and-device-access-protection--starting-point-policies).|

## <a name="step-5-protect-and-govern-sensitive-data"></a>Trin 5. Beskyt og styr følsomme data

Implementer Microsoft Purview Information Protection for at hjælpe dig med at finde, klassificere og beskytte følsomme oplysninger, uanset hvor de bor eller rejser.

Microsoft Purview Information Protection funktioner er inkluderet i Microsoft Purview og giver dig værktøjer til at kende dine data, beskytte dine data og forhindre tab af data.

:::image type="content" source="../media/zero-trust/m365-zero-trust-architecture-info-protect.png" alt-text="Funktionerne til beskyttelse af oplysninger, der beskytter data gennem håndhævelse af politikker" lightbox="../media/zero-trust/m365-zero-trust-architecture-info-protect.png":::

Selvom dette arbejde er repræsenteret øverst i udrulningsstakken, der er illustreret tidligere i denne artikel, kan du starte dette arbejde når som helst.

Microsoft Purview Information Protection indeholder en struktur, proces og egenskaber, som du kan bruge til at nå dine specifikke forretningsmål.

![Microsoft Purview Information Protection](../media/zero-trust/mip-solution-overview.png)

Du kan få flere oplysninger om, hvordan du planlægger og installerer beskyttelse af oplysninger, under [**_Installér en Microsoft Purview Information Protection løsning_**](../compliance/information-protection-solution.md). 

Hvis du udruller beskyttelse af oplysninger i forbindelse med regler for beskyttelse af personlige oplysninger, indeholder denne løsningsvejledning en anbefalet struktur for hele processen: [**_Udrul bestemmelser om beskyttelse af personlige oplysninger i forbindelse med Microsoft 365_**](../solutions/information-protection-deploy.md).
