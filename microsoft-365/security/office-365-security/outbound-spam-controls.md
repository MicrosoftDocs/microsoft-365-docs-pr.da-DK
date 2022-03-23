---
title: Beskyttelse mod udgående spam
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6a601501-a6a8-4559-b2e7-56b59c96a586
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Administratorer kan få mere at vide om de udgående spamkontrolelementer i Exchange Online Protection (EOP), og hvad de skal gøre, hvis du har brug for at sende masseforsendelser.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 26be514584a8fb2f8c024c0f4db208018d951868
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587934"
---
# <a name="outbound-spam-protection-in-eop"></a>Beskyttelse mod udgående spam i EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

I Microsoft 365 med postkasser i Exchange Online eller enkeltstående Exchange Online Protection-organisationer (EOP) uden Exchange Online-postkasser tager vi administration af udgående spam alvorligt. Selvom en kunde bevidst eller utilsigtet sender spam fra sin organisation, kan denne handling forringe omdømmet af hele tjenesten og påvirke leveringen af mail for andre kunder.

I denne artikel beskrives de kontrolelementer og meddelelser, der er beregnet til at forhindre udgående spam, og hvad du kan gøre, hvis du har brug for at sende masseforsendelser.

## <a name="what-admins-can-do-to-control-outbound-spam"></a>Hvad administratorer kan gøre for at kontrollere udgående spam

- Brug **indbyggede** meddelelser: Når en bruger overskrider grænsen for afsendelse af tjenesten [](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) eller politikker for udgående [spam](configure-the-outbound-spam-policy.md) og er begrænset i forbindelse med afsendelse af mail, vil standardpolitikken for  påmindelser med navnet Bruger begrænset i at sende mails sende mailmeddelelser til medlemmer af **gruppen TenantAdmins** (**globale** administratorer). Hvis du vil konfigurere, hvem der ellers modtager disse meddelelser, [skal du se Bekræft beskedindstillingerne for begrænsede brugere](removing-user-from-restricted-users-portal-after-spam.md#verify-the-alert-settings-for-restricted-users). Desuden er standardpolitikken for påmindelser  med navnet Grænse for afsendelse af  mail overskredet, og mistænkelige mønstre for afsendelse af mails sender meddelelser via mail til medlemmer af gruppen **TenantAdmins** (**globale** administratorer). Du kan finde flere oplysninger om beskedpolitikker [under Påmindelsespolitikker i Microsoft 365](../../compliance/alert-policies.md).

- Gennemse **spamklager** fra tredjepartsmailudbydere: Mange mailtjenester som Outlook.com, Yahoo og AOL giver en feedbackløkke, hvor hvis en bruger i deres tjeneste markerer en mail fra Microsoft 365 som spam, pakkes meddelelsen sammen og sendes tilbage til os til gennemsyn. Du kan få mere at vide om support til Outlook.com ved at gå til <https://sendersupport.olc.protection.outlook.com/pm/services.aspx>.

## <a name="how-eop-controls-outbound-spam"></a>Sådan styrer EOP udgående spam

- **Opdeling af udgående mailtrafik**: Hver udgående meddelelse, der sendes via tjenesten, scannes for spam. Hvis meddelelsen vurderes som spam, leveres den fra en sekundær, mindre velrenommeret IP-adressepulje, der er navngivet puljen af _leveringer med høj risiko_. Få mere at vide under [Større risikoleveringspulje for udgående meddelelser](high-risk-delivery-pool-for-outbound-messages.md).

- **Overvågning af vores IP-adresse ry** for kilder: Microsoft 365 forespørgsler fra forskellige IP-blokeringslister fra tredjeparter. Der genereres en besked, hvis nogen af de IP-adresser, vi bruger til udgående mail, vises på disse lister. Denne overvågning giver os mulighed for at reagere hurtigt, når spam har fået vores ry til at forringes. Når der genereres en besked, har vi intern dokumentation, der beskriver, hvordan du får vores IP-adresser fjernet (fjernet) fra blokeringslister.

- **Deaktiver** konti, der sender for meget spam <sup>\*</sup>: Selvom vi opdelte udgående spam i puljen af levering med høj risiko, kan vi ikke tillade en konto (ofte en kompromitteret konto) at sende spam på ubestemt tid. Vi overvåger konti, der sender spam, og når de overskrider en ukendt grænse, blokeres kontoen fra at sende mail. Der er forskellige grænseværdier for individuelle brugere og hele lejeren.

- **Deaktivering**<sup>\*</sup> af konti, der sender for mange mails for hurtigt: Ud over de begrænsninger, der søger efter meddelelser, der er markeret som spam, er der også begrænsninger, der blokerer konti, når de når en overordnet grænse for udgående meddelelser, uanset om spamfiltrering tager hensyn til udgående meddelelser. En kompromitteret konto kan sende spam, som ikke tidligere er blevet ukendt, og som spamfilteret ikke har mistet. Da det kan være svært at identificere en legitim masseforsendelseskampagne vs. en spamkampagne, hjælper disse begrænsninger med at minimere eventuelle skader.

<sup>\*</sup> Vi annoncerer ikke de nøjagtige begrænsninger, så spammere kan ikke spille systemet, og så vi kan øge eller mindske grænserne efter behov. Begrænsningerne er høje nok til at forhindre en almindelig forretningsbruger i overhovedet at overskride dem og er lav nok til at hjælpe med at indeholde de skader, en spammer har forårsaget.

## <a name="recommendations-for-customers-who-want-to-send-mass-mailings-through-eop"></a>Anbefalinger til kunder, der ønsker at sende masseforsendelser via EOP

Det er svært at finde en balance mellem kunder, der ønsker at sende en stor mængde mail i forhold til at beskytte tjenesten mod kompromitterede konti og massemailafsendere med dårlige fremgangsmåder for anskaffelse af modtagere. Omkostningerne for en mailkilde Microsoft 365 en tredjeparts IP-blokeringsliste er større end at blokere en bruger, der sender for mange mails.

Som beskrevet i [beskrivelse af Exchange Online-tjenesten](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits) er brugen af EOP til at sende massemails ikke en understøttet brug af tjenesten og er kun tilladt på grundlag af "bedste indsats". Til kunder, der ønsker at sende massemails, anbefaler vi følgende løsninger:

- **Send massemails via lokale mailservere**: Kunderne vedligeholder deres egen mailinfrastruktur til masseforsendelser.

- **Brug en tredjepartsudbyder af massemail**: Der findes flere tredjepartsudbydere af massemailløsninger, som du kan bruge til at sende masseforsendelser. Disse virksomheder har en egen interesse i at arbejde sammen med kunder for at sikre gode fremgangsmåder for afsendelse af mails.

Messaging, Mobile, Malware Anti-Abuse Working Group (DEWG) publicerer sin medlemskabsliste på <https://www.maawg.org/about/roster>. Flere massemailudbydere er på listen og er kendt for at være ansvarlige internetudbydere.
