---
title: Om delte postkasser
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- MSStore_Link
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
description: Delte postkasser bruges, når flere personer skal have adgang til den samme postkasse. Få mere at vide, før du opretter en delt postkasse.
ms.openlocfilehash: a384440b64b84618831b8065bd40d89200ea47d0
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/20/2022
ms.locfileid: "64971517"
---
# <a name="about-shared-mailboxes"></a>Om delte postkasser

Delte postkasser bruges, når flere personer skal have adgang til den samme postkasse, f.eks. en firmaoplysninger eller supportmailadresse, receptionsskranke eller en anden funktion, der kan deles af flere personer.

Brugere med tilladelser til gruppepostkassen kan sende som eller sende på vegne af postkassens mailadresse, hvis administratoren har givet denne bruger tilladelse til at gøre det. Dette er især nyttigt i forbindelse med postkasser til hjælp og support, fordi brugerne kan sende mails fra "Contoso Support" eller "Oprettelse af et receptionsskrivebord".

## <a name="before-you-begin"></a>Før du begynder

Før du [opretter en delt postkasse](create-a-shared-mailbox.md), skal du vide følgende:

- **Licenser:** Din delte postkasse kan gemme op til 50 GB data, uden at du tildeler en licens til den. Derefter skal du tildele en licens til postkassen for at gemme flere data. Du kan finde flere oplysninger om licenser til delte postkasser [under Exchange Online Grænser](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#StorageLimits). Når en delt postkasse når lagergrænsen, kan du modtage mail i et stykke tid, men du kan ikke sende ny mail. Derefter stopper den med at modtage mail. Afsendere af postkassen får en kvittering for manglende levering.

- **Brugertilladelser:** Du skal give brugerne tilladelse (medlemskab) til at bruge den delte postkasse. Det er kun personer i organisationen, der kan bruge en delt postkasse.

- **Eksterne brugere:** Du kan ikke give personer uden for din virksomhed (f.eks. personer med en Gmail-konto) adgang til din delte postkasse. Hvis du vil gøre dette, kan du overveje at oprette en gruppe til Outlook i stedet. Du kan få mere at vide under [Opret en Microsoft 365 gruppe i Administration](../create-groups/create-groups.md).

- **Brug sammen med Outlook:** Ud over at bruge Outlook på internettet fra din browser til at få adgang til delte postkasser kan du også bruge Outlook til iOS-appen eller Outlook til Android-appen. Du kan få mere at vide under [Føj en delt postkasse til Outlook mobil](https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f). En anden mulighed er at oprette en gruppe til din delte postkasse. Du kan få mere at vide under [Sammenlign grupper](../create-groups/compare-groups.md).

- **Kryptering:** Du kan ikke kryptere mails, der er sendt fra en delt postkasse. Det skyldes, at en delt postkasse ikke har sin egen sikkerhedskontekst (brugernavn/adgangskode), så den kan ikke tildeles en nøgle. Hvis mere end én person er medlem, og de sender/modtager mails, de krypterede med deres egne nøgler, kan andre medlemmer muligvis læse mailen, og andre muligvis ikke, afhængigt af hvilken offentlig nøgle mailen blev krypteret med.

- **Postkassekonvertering:** Du kan konvertere brugerpostkasser til delte postkasser. Se [Konvertér en brugerpostkasse til en delt postkasse](convert-user-mailbox-to-shared-mailbox.md).

- **Administratorroller:** Brugere med globale administrator- eller Exchange administratorroller kan oprette delte postkasser.

- **Abonnementskrav:** Hvis du vil oprette en delt postkasse, skal du abonnere på en Microsoft 365 til en forretningsplan, der indeholder mail (Exchange Online-tjenesten). Det Microsoft 365 Apps for business abonnement indeholder ikke mail. Microsoft 365 Business Standard indeholder mail.

- **Logger på:** En delt postkasse er ikke beregnet til direkte logon af dens tilknyttede brugerkonto. Du skal altid blokere logon for den delte postkassekonto og holde den blokeret.

- **For mange brugere:** Når der er for mange brugere, der har fået adgang til en delt postkasse samtidig (det anbefales, at der ikke oprettes mere end 25), kan de med jævne mellemrum ikke oprette forbindelse til denne postkasse eller have uoverensstemmelser, f.eks. meddelelser, der duplikeres i udbakken. I dette tilfælde kan du overveje at reducere antallet af brugere eller bruge en anden arbejdsbelastning, f.eks. en Microsoft 365 gruppe eller en offentlig mappe.

- **Sletning af meddelelse:** Du kan desværre ikke forhindre andre i at slette meddelelser i en delt postkasse. Den eneste måde at løse problemet på er ved at [oprette en Microsoft 365 gruppe](/microsoft-365/admin/create-groups/create-groups) i stedet for en delt postkasse. En gruppe i Outlook er som en delt postkasse. Du kan se en sammenligning af de to under [Sammenlign grupper](../create-groups/compare-groups.md). Du kan få mere at vide om grupper under [Få mere at vide om Microsoft 365 grupper](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2).

- **Multi-Geo** I et multi-geo-miljø skal delte postkasser have licens på samme måde, som en brugerpostkasse gives i licens. Bemærk, at overvågning af postkasser på tværs af geografiske områder ikke understøttes. Hvis en bruger f.eks. er tildelt tilladelser til at få adgang til en delt postkasse på en anden geografisk placering, logføres de postkassehandlinger, der udføres af den pågældende bruger, ikke i postkassens overvågningslog for den delte postkasse. 


> [!NOTE]
> For at få adgang til en delt postkasse skal en bruger have en Exchange Online licens, men den delte postkasse kræver ikke en separat licens. Alle delte postkasser har en tilsvarende brugerkonto. Bemærk, hvordan du ikke blev bedt om at angive en adgangskode, da du oprettede den delte postkasse? Kontoen har en adgangskode, men den er oprettet af systemet (ukendt). Du bør ikke bruge kontoen til at logge på den delte postkasse. Uden en licens er delte postkasser begrænset til 50 GB. Hvis du vil øge størrelsesgrænsen til 100 GB, skal den delte postkasse tildeles en Exchange Online Plan 2-licens. Licensen Exchange Online Plan 1 med en Exchange Online-arkivering-tilføjelsesprogramlicens øger kun størrelsen på arkivpostkassen. Dette giver dig også mulighed for automatisk udvidelse af arkivering for at få yderligere arkivlagerkapacitet. På samme måde skal den delte postkasse have en Exchange Online Plan 2-licens eller en Exchange Online Plan 1-licens med en Exchange Online-arkivering-licens, hvis du vil placere en delt postkasse i venteposition. Hvis du vil anvende avancerede funktioner som f.eks. Microsoft Defender for Office 365, eDiscovery (Premium) eller politikker for automatisk opbevaring, skal den delte postkasse have licens til disse funktioner.

## <a name="related-content"></a>Relateret indhold

[Opret en delt postkasse](create-a-shared-mailbox.md) (artikel)\
[Konfigurer en delt postkasse](configure-a-shared-mailbox.md) (artikel)\
[Konvertér en brugerpostkasse til en delt postkasse](convert-user-mailbox-to-shared-mailbox.md) (artikel)\
[Fjern en licens fra en delt postkasse](remove-license-from-shared-mailbox.md) (artikel)\
[Løs problemer med delte postkasser](resolve-issues-with-shared-mailboxes.md) (artikel)
