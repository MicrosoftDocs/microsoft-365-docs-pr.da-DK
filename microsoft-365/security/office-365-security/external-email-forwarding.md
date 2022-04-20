---
title: Konfiguration og styring af videresendelse af eksterne mails i Microsoft 365.
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
description: Denne artikel omhandler emner, herunder ekstern videresendelse af mail, automatisk videresendelse, 5.7.520 Meddelelser om adgang nægtet, deaktivering af ekstern videresendelse, "Din administrator har deaktiveret eksterne videresendelse"-meddelelser samt udgående politik mod spam.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 672e6af3d2aef76a0c944a05c438061861e20060
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971897"
---
# <a name="control-automatic-external-email-forwarding-in-microsoft-365"></a>Kontrollér automatisk ekstern videresendelse af mail i Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Som administrator har du muligvis virksomhedens krav om at begrænse eller styre automatisk videresendte meddelelser til eksterne modtagere (modtagere uden for organisationen). Videresendelse af mail kan være nyttigt, men kan også udgøre en sikkerhedsrisiko på grund af en potentiel offentliggørelse af oplysninger. Personer med ondsindede hensigter kan bruge disse oplysninger til at angribe din organisation eller dine partnere.

Følgende typer automatisk videresendelse er tilgængelige i Microsoft 365:

- Brugerne kan konfigurere [indbakkeregler](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) til automatisk at videresende meddelelser til eksterne afsendere (bevidst eller som følge af en kompromitteret konto).
- Administratorer kan konfigurere [videresendelse af postkasser](/exchange/recipients-in-exchange-online/manage-user-mailboxes/configure-email-forwarding) (også kaldet _SMTP-videresendelse_) til automatisk at videresende meddelelser til eksterne modtagere. Administratoren kan vælge, om meddelelser skal videresendes, eller om der skal gemmes kopier af videresendte meddelelser i postkassen.

> [!NOTE]
> Brugere med automatisk videresendelse fra mailsystemer i det lokale miljø via Microsoft 365 vil være underlagt de samme politikkontrolelementer som cloudpostkasser i en kommende opdatering. Denne opdatering vil blive kommunikeret via Meddelelsescenter-indlæg.

Du kan bruge politikker for filtrering af udgående spam til at styre automatisk videresendelse til eksterne modtagere. Der er tre tilgængelige indstillinger:

- **Automatic – Systemstyret**: Dette er standardindstillingen. Denne indstilling er nu den samme som **Fra**. Da denne indstilling oprindeligt blev introduceret, svarede den til **Til**. Med tiden blev denne indstilling gradvist ændret til **Fra** for alle kunder takket være principperne om [sikker som standard](secure-by-default.md). Du kan få flere oplysninger i [dette blogindlæg](https://techcommunity.microsoft.com/t5/exchange-team-blog/all-you-need-to-know-about-automatic-email-forwarding-in/ba-p/2074888).
- **Til**: Automatisk ekstern videresendelse er tilladt og er ikke begrænset.
- **Fra**: Automatisk ekstern videresendelse er deaktiveret og resulterer i en rapport om manglende levering (også kendt som en meddelelse om manglende levering eller afvisning af levering) til afsenderen.

Du kan finde oplysninger om, hvordan du konfigurerer disse indstillinger, [under Konfigurer filtrering af udgående spam i EOP](configure-the-outbound-spam-policy.md).

> [!NOTE]
>
> - Deaktivering af automatisk videresendelse deaktiverer alle indbakkeregler (brugere) eller videresendelse af postkasser (administratorer), der omdirigerer meddelelser til eksterne adresser.
> - Automatisk videresendelse af meddelelser mellem interne brugere påvirkes ikke af indstillingerne for filterpolitikker for udgående spam.

## <a name="how-the-outbound-spam-filter-policy-settings-work-with-other-automatic-email-forwarding-controls"></a>Sådan fungerer indstillingerne for filterpolitik for udgående spam sammen med andre automatiske kontrolelementer til videresendelse af mail

Som administrator har du muligvis allerede konfigureret andre kontrolelementer til at tillade eller blokere automatisk videresendelse af mail. Eksempel:

- [Fjerndomæner](/exchange/mail-flow-best-practices/remote-domains/remote-domains) , der tillader eller blokerer automatisk videresendelse af mail til nogle eller alle eksterne domæner.
- Betingelser og handlinger i Exchange [regler for mailflow](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) (også kaldet transportregler) for at registrere og blokere automatisk videresendte meddelelser til eksterne modtagere.

Når én indstilling tillader ekstern videresendelse, men en anden indstilling blokerer ekstern videresendelse, vinder blokken typisk. Eksempler er beskrevet i følgende tabel:

|Scenario|Resultat|
|---|---|
|<ul><li>Du kan konfigurere fjerndomæneindstillinger for at tillade automatisk videresendelse.</li><li>Automatisk videresendelse i filterpolitikken for udgående spam er slået **fra**.</li></ul>|Automatisk videresendte meddelelser til modtagere i de berørte domæner blokeres.|
|<ul><li>Du kan konfigurere fjerndomæneindstillinger for at tillade automatisk videresendelse.</li><li>Automatisk videresendelse i filterpolitikken for udgående spam er angivet til **Automatisk – Systemstyret**.</li></ul>|Automatisk videresendte meddelelser til modtagere i de berørte domæner blokeres. <p> Som beskrevet tidligere, **Automatic – Systemstyret** bruges til at betyde **Til**, men indstillingen er ændret over tid til at betyde **Off** i alle organisationer. <p> Af hensyn til klarheden skal du konfigurere din politik for udgående spamfilter til **Til** eller **Fra**.|
|<ul><li>Automatisk videresendelse i filterpolitikken for udgående spam er **slået til**</li><li>Du kan bruge regler for mailflow eller fjerndomæner til at blokere automatisk videresendte mails.</li></ul>|Automatisk videresendte meddelelser til berørte modtagere blokeres af regler for mailflow eller fjerndomæner.|

Du kan bruge denne funktionsmåde (f.eks.) til at tillade automatisk videresendelse af filterpolitikker for udgående spam, men bruge fjerndomæner til at styre de eksterne domæner, som brugerne kan videresende meddelelser til.

## <a name="how-to-find-users-that-are-automatically-forwarding"></a>Sådan finder du brugere, der videresendes automatisk

Du kan se oplysninger om brugere, der automatisk videresender meddelelser til eksterne modtagere, i [rapporten Automatisk videresendte meddelelser](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) for skybaserede konti. For brugere i det lokale miljø, der automatisk videresender fra deres lokale mailsystem via Microsoft 365, skal du oprette en regel for mailflowet for at spore disse brugere. Du kan finde oplysninger om, hvordan du opretter en regel for et mailflow, [under Brug EAC til at oprette en regel for et mailflow](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#use-the-eac-to-create-a-mail-flow-rule).

Følgende oplysninger er påkrævet for at oprette reglen for mailflowet i Exchange Administration (EAC):

- **Anvend denne regel, hvis** (betingelse): **En brevhoved** **svarer til**\> disse tekstmønstre. Bemærk, at du muligvis skal klikke på **Flere indstillinger** for at se denne indstilling.
  - **Overskriftsnavn**: `X-MS-Exchange-Inbox-Rules-Loop`
  - **Headerværdi**: `.`

  Betingelsen ser sådan ud: **Overskriften 'X-MS-Exchange-Inbox-Rules-Loop'** svarer **til '.'**

  Denne betingelse svarer til en hvilken som helst værdi for headeren.

- (Valgfrit) **Gør følgende** (handling): Du kan konfigurere en valgfri handling. Du kan f.eks. bruge handlingen **Rediger meddelelsesegenskaberne** \> **til at angive en meddelelsesoverskrift** med overskriftsnavnet **X-videresendt** og værdien **Sand**. Men konfiguration af en handling er ikke påkrævet.
- Angiv **Overvåg denne rue med alvorsgradsniveau** til værdien **Lav**, **Mellem** eller **Høj**. Denne indstilling giver dig mulighed for at bruge [rapporten med Exchange transportregel](view-email-security-reports.md#exchange-transport-rule-report) til at få oplysninger om de brugere, der videresender.

:::image type="content" source="../../media/mail-flow-rule-for-forwarded-messages.png" alt-text="Regelegenskaberne for mailflowet i EAC for en regel til identifikation af videresendte meddelelser" lightbox="../../media/mail-flow-rule-for-forwarded-messages.png":::

## <a name="blocked-email-forwarding-messages"></a>Blokerede meddelelser om videresendelse af mail

Når en meddelelse registreres som videresendt automatisk, og den [udgående spamfilterpolitik](configure-the-outbound-spam-policy.md) *blokerer* denne aktivitet, returneres meddelelsen til afsenderen i en NDR, der indeholder følgende oplysninger:

`5.7.520 Access denied, Your organization does not allow external forwarding. Please contact your administrator for further assistance. AS(7555)`
