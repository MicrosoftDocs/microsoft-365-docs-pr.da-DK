---
title: Afhjælpningshandlinger i Microsoft Defender til Office 365
keywords: AIR, autoIR, Microsoft Defender til slutpunkt, automatiseret, undersøgelse, svar, afhjælpning, trusler, avanceret, trussel, beskyttelse
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Få mere at vide om afhjælpningshandlinger efter automatiseret undersøgelse i Microsoft Defender Office 365.
ms.date: 04/30/2021
ms.custom:
- air
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5435c063234c2b803e172d6cdc06ff0b9bf417b2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63599699"
---
# <a name="remediation-actions-in-microsoft-defender-for-office-365"></a>Afhjælpningshandlinger i Microsoft Defender til Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="remediation-actions"></a>Afhjælpningshandlinger

Trusselsbeskyttelsesfunktioner i [Microsoft Defender til Office 365](defender-for-office-365.md) omfatter visse afhjælpningshandlinger. Disse afhjælpningshandlinger kan omfatte:

- Blød sletning af mails eller klynger
- Blokere URL-adresse (kliktid)
- Deaktivere ekstern videresendelse af mail
- Delegering deaktiveres

I Microsoft Defender til Office 365 automatisk afhjælpningshandlinger. Der udføres i stedet kun afhjælpningshandlinger, når organisationens sikkerhedsteam har godkendt det.

## <a name="threats-and-remediation-actions"></a>Trusler og afhjælpningshandlinger

Microsoft Defender til Office 365 omfatter afhjælpningshandlinger for at håndtere forskellige trusler. Automatiserede undersøgelser medfører ofte en eller flere afhjælpningshandlinger, der skal gennemses og godkendes. I nogle tilfælde fører en automatiseret undersøgelse ikke til en bestemt afhjælpningshandling. Brug vejledningen i følgende tabel til yderligere at undersøge og udføre relevante handlinger.

|Kategori|Trussel/risiko|Afhjælpningshandling(er)|
|:---|:---|:---|
|Mail|Malware|Blød sletning af mail/klynge <p> Hvis mere end en håndfuld mails i en klynge indeholder malware, anses klyngen for at være skadelig.|
|Mail|Ondsindet URL <br> (En ondsindet URL-adresse blev registreret [af Pengeskab Links](safe-links.md).)|Blød sletning af mail/klynge <br> Bloker URL-adresse (tids-for-klik-bekræftelse) <p> Mails, der indeholder en ondsindet URL-adresse, anses for at være skadelige.|
|Mail|Phish|Blød sletning af mail/klynge <p> Hvis mere end en håndfuld mails i en klynge indeholder phishingforsøg, betragtes hele klyngen som et forsøg på phishing.|
|Mail|Zapped phish <br> (Mails blev leveret og derefter [zappet](zero-hour-auto-purge.md).)|Blød sletning af mail/klynge <p> Rapporter er tilgængelige til at få vist zappede meddelelser. [Se, om ZAP har flyttet en meddelelse og ofte stillede spørgsmål](zero-hour-auto-purge.md#how-to-see-if-zap-moved-your-message).|
|Mail|Mistede phish-mails [rapporteret](enable-the-report-message-add-in.md) af en bruger|[Automatiseret undersøgelse udløst af brugerens rapport](automated-investigation-response-office.md#example-a-user-reported-phish-message-launches-an-investigation-playbook)|
|Mail|Volumennomenorm <br> (Seneste antal mails overskrider de forrige 7-10 dage for matchende kriterier.)|Automatiseret undersøgelse fører ikke til en bestemt afventende handling. <p>Volumenanomen er ikke en klar trussel, men blot en angivelse af større mailmængde i de seneste dage sammenlignet med de seneste 7-10 dage. <p>Selvom en stor mængde mail kan indikere potentielle problemer, er bekræftelse nødvendig i forbindelse med enten ondsindede advarsler eller en manuel gennemgang af mails/klynger. Se [Find mistænkelige mails, der blev leveret](investigate-malicious-email-that-was-delivered.md#find-suspicious-email-that-was-delivered).|
|Mail|Der blev ikke fundet nogen trusler <br> Systemet fandt ikke nogen trusler baseret på filer, URL-adresser eller analyse af mailklyngens konklusioner.|Automatiseret undersøgelse fører ikke til en bestemt afventende handling. <p>Trusler, der [er fundet og](zero-hour-auto-purge.md) toppet, efter en undersøgelse er afsluttet, afspejles ikke i en undersøgelses numeriske fund, men disse trusler kan ses i [Threat Explorer](threat-explorer.md).|
|Bruger|En bruger klikkede på en ondsindet URL-adresse <br> (En bruger har navigeret til en side, der senere blev fundet skadelig, eller en bruger har overgået en [advarselsside i Pengeskab Links](safe-links.md#warning-pages-from-safe-links) for at komme til en skadelig side).|Automatiseret undersøgelse fører ikke til en bestemt afventende handling. <p> Blokere URL-adresse (kliktid) <p> Brug Trusselsstifinder til [at få vist data om URL-adresser og klikke på konklusioner](threat-explorer.md#view-phishing-url-and-click-verdict-data). <p> Hvis din organisation bruger [Microsoft Defender til Slutpunkt, skal du overveje](/windows/security/threat-protection/) at [undersøge brugeren for](/microsoft-365/security/defender-endpoint/investigate-user) at finde ud af, om deres konto er kompromitteret.|
|Bruger|En bruger sender malware/phish|Automatiseret undersøgelse fører ikke til en bestemt afventende handling. <p> Brugeren rapporterer muligvis malware/phish, eller en person kan være [efterlignet af brugeren som](anti-spoofing-protection.md) en del af et angreb. Brug [Threat Explorer til](threat-explorer.md) at få vist og håndtere mails, der [indeholder malware](threat-explorer-views.md#email--malware) [eller phish](threat-explorer-views.md#email--phish).|
|Bruger|Videresendelse af mail <br> (Regler for videresendelse af postkasse er konfigureret, hvilket kan bruges til dataudfyldning).|Fjern reglen for videresendelse <p> Brug [mailflowindsigt](mail-flow-insights-v2.md), herunder [rapporten over autoindderede](mfi-auto-forwarded-messages-report.md) meddelelser, til at få vist mere specifikke oplysninger om videresendte mails.|
|Bruger|Regler for maildelegering <br> En brugers konto er konfigureret til at konfigurere.|Fjern delegeringsregel <p> Hvis din organisation bruger [Microsoft Defender til Slutpunkt, skal du](/windows/security/threat-protection/) overveje [at undersøge](/microsoft-365/security/defender-endpoint/investigate-user) den bruger, der får delegeringstilladelser.|
|Bruger|Dataudfyldning <br> (En bruger har brudt mail- eller fildeling [dlp-politikker](../../compliance/dlp-learn-about-dlp.md) |Automatiseret undersøgelse fører ikke til en bestemt afventende handling. <p> [Få vist DLP-rapporter, og gør noget](../../compliance/view-the-dlp-reports.md).|
|Bruger|Unormal afsendelse af mails <br> (En bruger har for nylig sendt flere mails end i de forrige 7-10 dage.)|Automatiseret undersøgelse fører ikke til en bestemt afventende handling. <p> At sende en stor mængde mails er ikke i sig selv skadelig; Brugeren har måske lige sendt mail til en stor gruppe af modtagere af en begivenhed. For at undersøge dette skal [du bruge indsigt i mailflow](mail-flow-insights-v2.md), herunder rapporten [for mailflowoversigten](mfi-mail-flow-map-report.md) til at bestemme, hvad der foregår og gøre noget.|

## <a name="next-steps"></a>Næste trin

- [Få vist detaljer og resultater af en automatisk undersøgelse i Microsoft Defender for Office 365](air-view-investigation-results.md)
- [Få vist afventende eller fuldførte afhjælpningshandlinger efter en automatisk undersøgelse i Microsoft Defender Office 365](air-review-approve-pending-completed-actions.md)

## <a name="related-articles"></a>Relaterede artikler

- [Få mere at vide om automatiseret undersøgelse i Microsoft Defender til Endpoint](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations)
- [Få mere at vide om funktioner i Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)
