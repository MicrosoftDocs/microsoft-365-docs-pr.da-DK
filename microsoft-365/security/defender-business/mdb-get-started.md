---
title: Kom i gang med at bruge Microsoft 365 Defender portalen
description: Se, hvordan du kommer i gang med Microsoft 365 Defender portal. Få mere at vide om, hvordan du navigerer i portalen og får vist din aktuelle sikkerhedsstatus og anbefalinger
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 3e46ee70c1c745c336d049f039de04282c5848d8
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/17/2022
ms.locfileid: "63593045"
---
# <a name="get-started-using-the-microsoft-365-defender-portal"></a>Kom i gang med at bruge Microsoft 365 Defender portalen

> [!IMPORTANT]
> Microsoft Defender for Business udrulles til [Microsoft 365 Business Premium](../../business-premium/index.md) kunder fra d. 1. marts 2022. Defender for Business som et enkeltstående abonnement er i preview, og den udrulles gradvist til kunder og [it-partnere](https://aka.ms/mdb-preview) , der tilmelder sig her for at anmode om det. [Forhåndsvisning indeholder et indledende sæt scenarier](mdb-tutorials.md#try-these-preview-scenarios), og vi tilføjer funktioner regelmæssigt.
> 
> Nogle oplysninger i denne artikel relaterer til foreløbige produkter/tjenester, der kan være væsentligt ændret, før de frigives kommercielt. Microsoft giver ingen garantier, udtrykkelige eller underforståede, for de oplysninger, du har angivet her. 

Når du har tilmeldt dig Microsoft Defender for Business, skal du lære portalen for Microsoft 365 Defender at kende ([https://security.microsoft.com](https://security.microsoft.com)). Denne artikel indeholder følgende afsnit:

- [Sådan navigerer du Microsoft 365 Defender-portalen](#navigate-the-microsoft-365-defender-portal)

- [Learning moduler om hændelser og svarhandlinger](#complete-a-learning-module-about-incidents-and-response-actions) 

- [Næste trin](#next-steps)

>
> **Har du et minut?**
> Tag vores korte <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">undersøgelse om Microsoft Defender for Business</a>. Vi vil meget gerne høre fra dig!
>

## <a name="navigate-the-microsoft-365-defender-portal"></a>Navigere i Microsoft 365 Defender portal

Portalen Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) er dit sted, hvor du kan bruge og administrere Microsoft Defender for Business. Det indeholder et velkomstbanner og uddelingskopier, som kan hjælpe dig med at komme i gang, kort med relevante oplysninger og en navigationslinje, der giver dig nem adgang til de forskellige funktioner og egenskaber.
 
Brug et øjeblik på at blive fortrolig med Microsoft 365 Defender portal.

:::image type="content" source="../../media/defender-business/mdb-portal-home.png" alt-text="Microsoft 365 Defender-portal":::

### <a name="use-the-navigation-bar"></a>Brug navigationslinjen

Brug navigationslinjen i venstre side af skærmen til at få adgang til dine hændelser, få vist rapporter og administrere dine sikkerhedspolitikker. I følgende tabel beskrives elementer, der vises i navigationslinjen.

| Element | Beskrivelse |
|:---|:---|
| **Home** | Fører dig til din startside Microsoft 365 Defender. Startsiden indeholder kort, der fremhæver eventuelle aktive trusler, der blev registreret, samt anbefalinger, der kan hjælpe med at sikre din virksomheds data og enheder. <br/><br/>Anbefalinger er inkluderet i Defender for Business, kan du spare tid og besvær for dit sikkerhedsteam. Anbefalinger er baseret på bedste praksis for branchen. Du kan få mere at vide om anbefalinger [under Sikkerhedsanbefalinger – Håndtering af trusler og sikkerhedsrisici](../defender-endpoint/tvm-security-recommendation.md). |
| **Hændelser** | Fører dig til din liste over de seneste hændelser. Når der udløses beskeder, oprettes der hændelser. En hændelse kan indeholde flere beskeder. Sørg for at gennemgå dine hændelser regelmæssigt. <br/><br/>Du kan få mere at vide om hændelser [under Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md).|
| **Handlingscenter** | Fører dig til listen over svarhandlinger, herunder fuldførte eller afventende handlinger. <br/>- Vælg fanen **Oversigt for** at se de handlinger, der blev foretaget. Nogle handlinger bliver foretaget automatisk. andre tages manuelt eller fuldført, efter de er blevet godkendt. <br/>- Vælg fanen **Afventer** for at få vist handlinger, der kræver godkendelse for at fortsætte. <br/><br/>Du kan få mere at vide om handlingscenter [i Gennemse afhjælpningshandlinger i Handlingscenter](mdb-review-remediation-actions.md). |
| **Trusselsanalyse** | Tager dig til et overblik over aktuelle trusler og giver dig et hurtigt overblik over dit trusselsbillede. Trusselsanalyse omfatter også rapporter og oplysninger fra Microsofts sikkerhedseksperter. <br/><br/>Hvis du vil have mere at vide om trusselsanalyse, [skal du se Spore og reagere på nye trusler via trusselsanalyse](../defender-endpoint/threat-analytics.md). |
| **Sikker score** | Giver dig en repræsentation af din virksomheds sikkerhedsposition og kommer med forslag til at forbedre den.<br/><br/>Du kan få mere at vide om Secure Score [under Microsoft Secure Score til enheder](../defender-endpoint/tvm-microsoft-secure-score-devices.md). |
| **Learning hub** | Giver adgang til sikkerhedskurser og andre ressourcer via læringsstier, der er inkluderet i dit abonnement. Du kan filtrere efter produkt, kompetenceniveau, rolle og meget mere. Hubben Learning kan hjælpe dit sikkerhedsteam med at sætte gang i sikkerhedsfunktioner & funktioner i Defender for Business og flere Microsoft-tilbud, f.eks. [Microsoft Defender til Endpoint](../defender-endpoint/microsoft-defender-endpoint.md) og [Microsoft Defender Office 365](../office-365-security/defender-for-office-365.md).  |
| **Slutpunkter** >  **Søg** | Gør det muligt at søge efter en eller flere enheder, der blev onboardet til Microsoft Defender for Business. |
| **Slutpunkter** >  **Lagerenhed** | Gør det muligt at søge efter en eller flere enheder, der blev onboardet til Microsoft Defender for Business. |
| **Slutpunkter** >  **Administration af sikkerhedsrisiko** | Giver dig et dashboard, anbefalinger, afhjælpningsaktiviteter, en lagerliste til software og en liste over potentielle muligheder i din virksomhed. |
| **Slutpunkter** >  **Selvstudier** | Giver adgang til gennemgange og simuleringer, så du kan få mere at vide om, hvordan dine funktioner til trusselsbeskyttelse fungerer. <br/><br/>Vælg linket **Læs gennemgangen, før du** forsøger at få simuleringsfilen for hvert selvstudium. Nogle simuleringssprogrammer Office apps, f.eks. Microsoft Word, for at læse gennemgangen. |
| **Slutpunkter** >  **Enhedskonfiguration** | Viser sikkerhedspolitikkerne efter operativsystem og type. <br/><br/>Du kan få mere at vide om [sikkerhedspolitikkerne i Få vist eller rediger politikker i Microsoft Defender for Business](mdb-view-edit-policies.md). |
| **Rapporter** | Viser dine tilgængelige sikkerhedsrapporter. Disse rapporter gør det muligt for dig at se dine sikkerhedstendenser, få vist detaljer om trusselsregistreringer og advarsler og få mere at vide om din virksomheds sårbar enheder. |
| **Tilstand** | Giver dig mulighed for at få vist status for tjenestetilstanden og planlægge kommende ændringer. <br/>- Vælg **Tjenestetilstand for** at få vist tilstandsstatussen for Microsoft 365, der er inkluderet i din virksomheds abonnement. <br/>- Vælg **Meddelelsescenter for at** få mere at vide om planlagte ændringer, og hvad du kan forvente.  |
| **Tilladelser & roller** | Giver dig mulighed for at tildele tilladelser til de personer i virksomheden, der skal administrere din sikkerhed og få vist hændelser og rapporter Microsoft 365 Defender portalen. Giver dig også mulighed for at konfigurere og administrere enhedsgrupper, så du kan onboarde din virksomheds enheder og tildele dine politikker for trusselsbeskyttelse.  |
| **Indstillinger** | Gør det muligt at redigere indstillingerne for Microsoft 365 Defender portal og Microsoft Defender for Business. Du kan f.eks. onboarde (eller offboard) og firmaets enheder (også kaldet slutpunkter). Du kan også definere regler, f.eks regler for beskedundertrykning, og konfigurere indikatorer til at blokere eller tillade bestemte filer eller processer.  |
| **Flere ressourcer** | Gå til andre portaler, f.eks. Azure Active Directory. Husk, at portalen Microsoft 365 Defender skal opfylde dine behov, uden at du behøver at navigere til andre portaler. |

## <a name="complete-a-learning-module-about-incidents-and-response-actions"></a>Fuldfør et læringsmodul om hændelser og svarhandlinger

Se læringsmodulet, [Find og svar på sikkerhedsproblemer](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/), for at få et overblik over hændelser og svarhandlinger. Du kan få mere at vide om hændelseskøen, beskeder og svarhandlinger, som du kan udføre. Dette kursus hjælper dig i gang med at arbejde med hændelser i Defender for Business.

> [!NOTE]
> Selvom læringsmodulet ([Registrer](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/) og svar på sikkerhedsproblemer) faktisk er for Microsoft Defender til slutpunkt, ligner de grundlæggende begreber og det overordnede flow det, du ser i Defender for Business.

## <a name="next-steps"></a>Næste trin

Nu hvor du har et overblik over Defender for Business, kan du prøve en eller flere af følgende opgaver:

- [Prøv selvstudier og simulering i Microsoft Defender for Business](mdb-tutorials.md)

- [Administrer enheder i Microsoft Defender for Business](mdb-manage-devices.md)

- [Få vist og administrer hændelser i Microsoft Defender for Business](mdb-view-manage-incidents.md)

- [Re besvare og afhjælpe trusler i Microsoft Defender for Business](mdb-respond-mitigate-threats.md)

- [Gennemse afhjælpningshandlinger i Handlingscenter](mdb-review-remediation-actions.md)

- [Få vist eller rediger politikker i Microsoft Defender for Business](mdb-view-edit-policies.md)