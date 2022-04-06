---
title: Konfiguration og kontrol af ekstern videresendelse af mail i Microsoft 365.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 11/17/2021
audience: ITPro
ms.topic: overview
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Denne artikel omhandler emner, herunder ekstern videresendelse af mail, automatisk videresendelse, 5.7.520 Adgang nægtet meddelelser, deaktivering af ekstern videresendelse, "Din administrator har deaktiveret ekstern videresendelse"-meddelelser samt politikken for udgående uønsket post.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8df0ff9902fe22fd44a0d15f7f01e13e791c7b12
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473601"
---
# <a name="control-automatic-external-email-forwarding-in-microsoft-365"></a>Kontrollere automatisk videresendelse af eksterne mails Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Som administrator kan du komme ud for firmakrav, der begrænser eller styrer automatisk videresendte meddelelser til eksterne modtagere (modtagere uden for organisationen). Videresendelse af mail kan være nyttigt, men kan også udgøre en sikkerhedsrisiko på grund af den potentielle offentliggørelse af oplysninger. Hackere kan bruge disse oplysninger til at angreb din organisation eller partnere.

Følgende typer af automatisk videresendelse er tilgængelige i Microsoft 365:

- Brugere kan konfigurere [indbakkeregler](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) til automatisk at videresende meddelelser til eksterne afsendere (bevidst eller som et resultat af en kompromitteret konto).
- Administratorer kan konfigurere [videresendelse af postkasse](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) (også kaldet _SMTP-videresendelse_) til automatisk at videresende meddelelser til eksterne modtagere. Administratoren kan vælge, om der blot skal videresendes meddelelser, eller om der skal bevares kopier af videresendte meddelelser i postkassen.

> [!NOTE]
> Brugere med automatisk videresendelse fra lokale mailsystemer via Microsoft 365 vil være underlagt de samme politikkontrolelementer som skybaserede postkasser i en kommende opdatering. Denne opdatering kommunikeres via indlægget i Meddelelsescenter.

Du kan bruge politikker for udgående spamfilter til at styre automatisk videresendelse til eksterne modtagere. Der findes tre tilgængelige indstillinger:

- **Automatisk – Systemkontrolleret**: Dette er standardindstillingen. Denne indstilling er nu den samme som **Fra**. Da denne indstilling oprindeligt blev introduceret, svarede den til **Til**. Med tiden blev denne indstilling [gradvist ændret til Fra](secure-by-default.md) **for alle** kunder takket være principperne for sikkerhed som standard. Du kan finde flere oplysninger i [dette blogindlæg](https://techcommunity.microsoft.com/t5/exchange-team-blog/all-you-need-to-know-about-automatic-email-forwarding-in/ba-p/2074888). 
- **Til**: Automatisk ekstern videresendelse er tilladt og ikke begrænset.
- **Fra**: Automatisk ekstern videresendelse er deaktiveret og resulterer i en rapport om manglende levering (også kaldet en NDR eller meddelelse om ikke-leveret mail) til afsenderen.

Du kan finde en vejledning til konfiguration af disse indstillinger [i Konfigurere udgående spamfiltrering i EOP](configure-the-outbound-spam-policy.md).

> [!NOTE]
>
> - Deaktivering af automatisk videresendelse deaktiverer indbakkeregler (brugere) eller videresendelse af postkasser (administratorer), der omdirigerer meddelelser til eksterne adresser.
>
> - Automatisk videresendelse af meddelelser mellem interne brugere påvirkes ikke af indstillingerne i politikkerne for udgående spamfilter.


## <a name="how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls"></a>Sådan fungerer politikindstillingerne for udgående spam med andre kontrolelementer til automatisk videresendelse af mail

Som administrator har du muligvis allerede konfigureret andre kontrolelementer til at tillade eller blokere automatisk videresendelse af mail. Eksempel:

- [Fjerndomæner](/exchange/mail-flow-best-practices/remote-domains/remote-domains) til at tillade eller blokere automatisk videresendelse af mail til nogle eller alle eksterne domæner.
- Betingelser og handlinger i Exchange [regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (også kaldet transportregler) til at registrere og blokere automatisk videresendte meddelelser til eksterne modtagere.

Når en indstilling tillader ekstern videresendelse, men en anden indstilling blokerer ekstern videresendelse, vinder blokken typisk. Eksempler er beskrevet i følgende tabel:

|Scenarie|Resultat|
|---|---|
|<ul><li>Du skal konfigurere eksterne domæneindstillinger for at tillade automatisk videresendelse.</li><li>Automatisk videresendelse i politikken for udgående spamfilter er indstillet til **Fra**.</li></ul>|Automatisk videresendte meddelelser til modtagere i de berørte domæner blokeres.|
|<ul><li>Du skal konfigurere eksterne domæneindstillinger for at tillade automatisk videresendelse.</li><li>Automatisk videresendelse i politikken for udgående spamfilter er indstillet **til Automatisk – Systemkontrolleret**.</li></ul>|Automatisk videresendte meddelelser til modtagere i de berørte domæner blokeres. <p> Som beskrevet tidligere **blev Automatisk – Systemkontrolleret** brugt til at vise " **Til",** men indstillingen har ændret sig med tiden til at betyde **Fra** i alle organisationer. <p> For at gøre den absolutte klarhed skal du konfigurere din politik for udgående spamfilter **til Til** eller **Fra**.|
|<ul><li>Automatisk videresendelse i politikken for udgående spamfilter er indstillet til **Til**</li><li>Du bruger regler for mailflow eller eksterne domæner til at blokere automatisk videresendte mails.</li></ul>|Automatisk videresendte meddelelser til berørte modtagere blokeres af regler for mailflow eller eksterne domæner.|

Du kan bruge denne funktionsmåde (f.eks. til at tillade automatisk videresendelse af politikker for indgående spamfilter, men bruge eksterne domæner til at styre de eksterne domæner, som brugere kan videresende meddelelser til.

## <a name="how-to-find-users-that-are-automatically-forwarding"></a>Sådan finder du brugere, der videresender automatisk

Du kan få vist oplysninger om brugere, der automatisk videresender meddelelser til eksterne modtagere i rapporten [Om automatisk videresendte meddelelser](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) for skybaserede konti. For lokale brugere, der automatisk videresender fra deres lokale mailsystem via Microsoft 365, skal du oprette en regel for mailflow for at spore disse brugere. Du kan finde en vejledning til, hvordan du opretter en regel for mailflow, under [Brug af EAC til at oprette en regel for mailflow](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#use-the-eac-to-create-a-mail-flow-rule).

Følgende oplysninger er nødvendige for at oprette reglen for mailflow i Exchange Administration (EAC):

- **Anvend denne regel, hvis** (betingelse): **En brevhoved svarer** \> **til disse tekstmønstre**. Bemærk, at du muligvis skal klikke **på Flere indstillinger** for at få vist denne indstilling.
  - **Sidehovednavn**: `X-MS-Exchange-Inbox-Rules-Loop`
  - **Overskriftsværdi**: `.`

  Betingelsen ser sådan ud: **'X-MS-Exchange-Inbox-Rules-Loop'** '**.'**

  Denne betingelse matcher enhver værdi for sidehovedet.

- (Valgfrit) **Gør følgende** (handling): Du kan konfigurere en valgfri handling. Du kan f.eks.  \> bruge handlingen Rediger meddelelsesegenskaberne til at angive et brevhoved **med overskriften** **X-Videresendt** og værdien **Sand**. Men det er ikke nødvendigt at konfigurere en handling.
- **Indstil Oversig denne rue med alvorsniveau** til **værdien Lav**, Mellem eller **Høj**.  Denne indstilling gør det muligt at bruge [Exchange transportregelrapport til](view-email-security-reports.md#exchange-transport-rule-report) at få oplysninger om brugere, der videresender.

:::image type="content" source="../../media/mail-flow-rule-for-forwarded-messages.png" alt-text="Egenskaber for regel for mailflow i EAC for en regel til at identificere videresendte meddelelser" lightbox="../../media/mail-flow-rule-for-forwarded-messages.png":::


## <a name="blocked-email-forwarding-messages"></a>Blokerede videresendelse af mails

Når en meddelelse registreres som automatisk videresendt, og politikken for udgående [spamfilter](configure-the-outbound-spam-policy.md) blokerer denne  aktivitet, returneres meddelelsen til afsenderen i en NDR, der indeholder følgende oplysninger:

`5.7.520 Access denied, Your organization does not allow external forwarding. Please contact your administrator for further assistance. AS(7555)`
