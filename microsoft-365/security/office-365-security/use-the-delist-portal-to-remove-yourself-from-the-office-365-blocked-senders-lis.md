---
title: Fjern dig selv fra listen over blokerede afsendere og adressen 5.7.511 Adgang nægtet-fejl
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 04/18/2016
audience: ITPro
ms.topic: troubleshooting
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 0bcecdd4-3343-4cc0-9e58-e19d4de515e8
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: I denne artikel får du mere at vide om, hvordan du bruger fralisten til at fjerne dig selv fra listen over Microsoft 365 blokerede afsendere. Dette er det bedste svar på adresse 5.7.511 Fejl, der blev nægtet adgang til.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 43637f8eb72d078223236f78b45034218e34bcbc
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971126"
---
# <a name="use-the-delist-portal-to-remove-yourself-from-the-blocked-senders-list-and-address-57511-access-denied-errors"></a>Brug fralisteportalen til at fjerne dig selv fra listen over blokerede afsendere og adressen 5.7.511 Fejl om adgang nægtet

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender for Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Får du vist en fejlmeddelelse, når du forsøger at sende en mail til en modtager, hvis mailadresse er i Microsoft 365 (f.eks. og adresse 5.7.511 Adgang nægtet)? Hvis du mener, at du ikke skal modtage fejlmeddelelsen, kan du bruge fralisten til at fjerne dig selv fra listen over blokerede afsendere.

## <a name="what-is-the-blocked-senders-list"></a>Hvad er listen over blokerede afsendere?

Microsoft bruger listen over blokerede afsendere til at beskytte sine kunder mod spam-, spoofing- og phishingangreb. Din mailservers IP-adresse, dvs. den adresse, din mailserver bruger til at identificere sig selv på internettet, er mærket som en potentiel trussel mod Microsoft 365 af en af mange forskellige årsager. Når Microsoft 365 føjer IP-adressen til listen, forhindrer det al yderligere kommunikation mellem IP-adressen og nogen af vores kunder gennem vores datacentre.

Du ved, at du er blevet føjet til listen, når du modtager et svar på en mail, der indeholder en fejl, der ser nogenlunde sådan ud:

> 550 5.7.606-649 Adgang nægtet, forbudt afsendelse IP [_IP-adresse_] (ex. 5.7.511 Adgang nægtet): Hvis du vil anmode om fjernelse fra denne liste, skal du besøge <https://sender.office.com/> og følge vejledningen. Du kan få flere oplysninger [under Mailrapporter om manglende levering i Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

hvor  _IP-adressen_ er IP-adressen på den computer, hvor postserveren kører.

## <a name="verify-senders-before-removing-them-from-the-blocked-senders-list"></a>Bekræft afsendere, før du fjerner dem fra listen over blokerede afsendere

Der er gode grunde til, at afsendere ender på listen over blokerede afsendere, men der kan opstå fejl. Se denne video for at få en afbalanceret forklaring af blokerede afsendere og franotering.
<p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvD]

## <a name="to-use-delist-portal-to-remove-yourself-from-the-blocked-senders-list-after-errors-like-57511-access-denied"></a>Sådan bruger du fralisteportalen til at fjerne dig selv fra listen over blokerede afsendere (efter fejl som 5.7.511 Adgang nægtet)

1. Gå til <https://sender.office.com>i en webbrowser.

2. Følg vejledningen på siden. Kontrollér, at du bruger den mailadresse, som fejlmeddelelsen blev sendt til, og den IP-adresse, der er angivet i fejlmeddelelsen. Du kan kun angive én mailadresse og én IP-adresse pr. besøg.

3. Klik på **Send**.

    Portalen sender en mail til den mailadresse, du angiver. Mailen ser nogenlunde sådan ud:

    :::image type="content" source="../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png" alt-text="Den mail, der blev modtaget, da du sendte en anmodning via fralisteportalen" lightbox="../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png":::

4. Klik på bekræftelseslinket i den mail, der er sendt til dig via fralisten.

    Dermed kommer du tilbage til fralistens portal.

5. Klik på **Fraliste IP på fralisten**.

    Når IP-adressen er fjernet fra listen over blokerede afsendere, leveres mails fra den pågældende IP-adresse til modtagere, der bruger Microsoft 365. Så sørg for, at du er sikker på, at mail, der sendes fra den pågældende IP-adresse, ikke vil være stødende eller ondsindet; Ellers kan IP-adressen blive blokeret igen.

    > [!NOTE]
    > Det kan tage op til 24 timer, eller resultaterne kan variere meget, før begrænsningerne fjernes.

Se [Opret lister over sikre afsendere i EOP](create-safe-sender-lists-in-office-365.md) - og [udgående spambeskyttelse i EOP](outbound-spam-controls.md) for at forhindre, at en IP-adresse blokeres.

### <a name="how-do-fix-error-code-57511"></a>Hvordan rettes fejlkoden 5.7.511

Når der er problemer med at levere en mail, som du har sendt, Microsoft 365 eller Office 365 sender en mail for at give dig besked. Den mail, du modtager, er en meddelelse om leveringsstatus, også kendt som en DSN- eller bounce-meddelelse. Den mest almindelige type kaldes en NDR (non-delivery report), og de fortæller dig, at en meddelelse ikke blev leveret. I visse situationer skal Microsoft foretage yderligere undersøgelser af trafik fra din IP, og hvis du modtager NDR-koden 5.7.511, **kan du ikke** bruge delistingsportalen.

> 550 5.7.511 Adgang nægtet, forbudt afsender[xxx.xxx.xxx.xxx]. Hvis du vil anmode om fjernelse fra listen, skal du videresende meddelelsen til delist@messaging.microsoft.com. Du kan få flere oplysninger ved at gå til <https://go.microsoft.com/fwlink/?LinkId=526653>.

I mailen for at anmode om fjernelse fra denne liste skal du angive den fulde NDR-kode og IP-adresse. Microsoft kontakter dig inden for 48 timer med de næste trin.

## <a name="more-information"></a>Flere oplysninger

Brugsformularen for **Outlook.com, som er forbrugertjenesten,** kan findes [her](https://support.microsoft.com/supportrequestform/8ad563e3-288e-2a61-8122-3ba03d6b8d75). Sørg for at læse [ofte stillede spørgsmål](https://sendersupport.olc.protection.outlook.com/pm/troubleshooting.aspx) først for _indsendelsesretning_ .
