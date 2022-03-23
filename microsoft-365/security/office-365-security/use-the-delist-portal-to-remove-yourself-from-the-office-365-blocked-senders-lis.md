---
title: Fjern dig selv fra listen over blokerede afsendere og adresse 5.7.511 Adgang nægtet fejl
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
description: I denne artikel kan du se, hvordan du kan bruge listeportalen til at fjerne dig selv fra listen Microsoft 365 afsendere af uønsket mail. Dette er det bedste svar på adresse 5.7.511 Access denied errors.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 36187288b2a7acf1a852e6c203cbb84035ba5d7a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587475"
---
# <a name="use-the-delist-portal-to-remove-yourself-from-the-blocked-senders-list-and-address-57511-access-denied-errors"></a>Brug aflistingsportalen til at fjerne dig selv fra listen over blokerede afsendere og adresse 5.7.511 Adgang nægtet fejl

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender til Office 365 plan 1 og plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Får du en fejlmeddelelse, når du forsøger at sende en mail til en modtager, hvis mailadresse er i Microsoft 365 (f.eks. og adresse 5.7.511 Adgang nægtet)? Hvis du mener, at du ikke bør modtage fejlmeddelelsen, kan du bruge frameldingsportalen til at fjerne dig selv fra listen over blokerede afsendere.

## <a name="what-is-the-blocked-senders-list"></a>Hvad er listen over blokerede afsendere?

Microsoft bruger listen over blokerede afsendere til at beskytte sine kunder mod spam, spoofing og phishingangreb. Mailserverens IP-adresse, dvs. den adresse, din mailserver bruger til at identificere sig selv på internettet, blev mærket som en potentiel trussel mod Microsoft 365 af en af en række forskellige årsager. Når Microsoft 365 tilføjer IP-adressen til listen, forhindrer det al yderligere kommunikation mellem IP-adressen og nogen af vores kunder via vores datacentre.

Du ved, at du er blevet føjet til listen, når du modtager et svar på en mail, der indeholder en fejl, der ser ud som denne:

> 550 5.7.606-649 Access denied, banned sending IP [_IP address_] (ex. 5.7.511 Access denied): To request removal from this list please visit <https://sender.office.com/> and follow the directions. Du kan finde flere [oplysninger i Mailrapporter om manglende levering Exchange Online](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/non-delivery-reports-in-exchange-online).

hvor  _IP-adresse_ er IP-adressen på den computer, hvor mailserveren kører.

## <a name="verify-senders-before-removing-them-from-the-blocked-senders-list"></a>Bekræft afsendere, før du fjerner dem fra listen over blokerede afsendere

Der er gode grunde til, at afsendere ender på listen over blokerede afsendere, men der kan opstå fejl. Se denne video for at finde en balanceret forklaring af blokerede afsendere og franotering.
<p>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMhvD]


## <a name="to-use-delist-portal-to-remove-yourself-from-the-blocked-senders-list-after-errors-like-57511-access-denied"></a>For at bruge fralistingsportalen til at fjerne dig selv fra listen over blokerede afsendere (efter fejl som f.eks. 5.7.511 adgang nægtet)

1. I en webbrowser skal du gå til <https://sender.office.com>.

2. Følg vejledningen på siden. Sørg for at bruge den mailadresse, som fejlmeddelelsen blev sendt til, og den IP-adresse, der er angivet i fejlmeddelelsen. Du kan kun angive én mailadresse og én IP-adresse pr. besøg.

3. Klik **på Send**.

    Portalen sender en mail til den mailadresse, du leverer. Mailen ser ud som følger:

    ![Skærmbillede af mails, der modtages, når du sender en anmodning via listen over lister.](../../media/bf13e4f7-f68c-4e46-baa7-b6ab4cfc13f3.png)

4. Klik på bekræftelseslinket i den mail, der sendes til dig fra listen over lister.

    Dette bringer dig tilbage til listens portal.

5. I fralist-portalen skal du klikke **på Fjern liste over IP-adresser**.

    Når IP-adressen er fjernet fra listen over blokerede afsendere, bliver mails fra den pågældende IP-adresse leveret til modtagere, der bruger Microsoft 365. Så sørg for, at du er sikker på, at mails, der sendes fra den pågældende IP-adresse, ikke vil være skadelige eller skadelige. Ellers kan IP-adressen være blokeret igen.

    > [!NOTE]
    > Det kan tage op til 24 timer, eller resultaterne kan variere meget, før begrænsninger fjernes.

Se [Opret lister over afsendere, der er tillid til i EOP](create-safe-sender-lists-in-office-365.md) [og Beskyttelse mod udgående spam i EOP](outbound-spam-controls.md) for at forhindre, at en IP blokeres.

### <a name="how-do-fix-error-code-57511"></a>Hvordan retter jeg fejlkode 5.7.511?
 
Når der er et problem med at levere en mail, du har sendt, sender Microsoft 365 eller Office 365 en mail for at fortælle dig det. Den mail, du modtager, er en besked om leveringsstatus, også kaldet en DSN- eller en meddelelse om ikke-leveret post. Den mest almindelige type kaldes en rapport om manglende levering (NDR), og den fortæller dig, at meddelelsen ikke blev leveret. I visse situationer skal Microsoft foretage yderligere undersøgelser af trafikken fra din IP, og hvis du modtager NDR-koden 5.7.511, kan du ikke bruge frameldingsportalen.
 
>   550 5.7.511 Access denied, banned sender[xxx.xxx.xxx.xxx]. Hvis du vil anmode om at blive fjernet fra denne liste, skal du videresende denne meddelelse delist@messaging.microsoft.com. Du kan få mere at vide ved at gå til https://go.microsoft.com/fwlink/?LinkId=526653. 
 
Angiv den fulde NDR-kode og IP-adresse i mailen for at anmode om at blive fjernet fra denne liste. Microsoft kontakter dig inden for 48 timer med de næste trin. 

## <a name="more-information"></a>Flere oplysninger
  
Formularen til at **Outlook.com, forbrugertjenesten**, kan findes [her](https://support.microsoft.com/supportrequestform/8ad563e3-288e-2a61-8122-3ba03d6b8d75). Sørg for at læse de ofte [stillede spørgsmål](https://sendersupport.olc.protection.outlook.com/pm/troubleshooting.aspx) først for *indsendelsesretning* .
