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
description: Delte postkasser bruges, når flere personer skal have adgang til den samme postkasse. Få mere at vide om, hvad du bør vide, før du opretter en delt postkasse.
ms.openlocfilehash: 2fbf07fbe71ccb42411f5808aa923d7179d2f13d
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/27/2022
ms.locfileid: "63590164"
---
# <a name="about-shared-mailboxes"></a>Om delte postkasser

Delte postkasser bruges, når flere personer skal have adgang til den samme postkasse, f.eks. en firmaoplysninger eller en supportmailadresse, receptionsdesk eller andre funktioner, som kan deles af flere personer.

Brugere med tilladelser til gruppepostkassen kan sende som eller sende på vegne af postkassemailadressen, hvis administratoren har givet den pågældende bruger tilladelse til at gøre det. Dette er især nyttigt til hjælp og supportpostkasser, fordi brugere kan sende mails fra "Contoso Support" eller "Building A Reception Desk".

## <a name="before-you-begin"></a>Før du begynder

Før du [opretter en delt postkasse](create-a-shared-mailbox.md), er her nogle ting, du bør vide:

- **Licenser:** Din delte postkasse kan gemme op til 50 GB data, uden at du tildeler den en licens. Derefter skal du tildele postkassen en licens for at lagre flere data. Du kan finde flere oplysninger om licenser til delte postkasser [Exchange Online Begrænsninger](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#StorageLimits). Når en delt postkasse når lagergrænsen, vil du kunne modtage mails i et stykke tid, men du vil ikke kunne sende nye mails. Derefter stopper den med at modtage mails. Afsendere til postkassen får en kvittering for manglende levering.

- **Brugertilladelser:** Du skal give brugere tilladelse (medlemskab) til at bruge den delte postkasse. Kun personer i din organisation kan bruge en delt postkasse.

- **Eksterne brugere:** Du kan ikke give personer uden for virksomheden (f.eks. personer med en Gmail-konto) adgang til din delte postkasse. Hvis du vil gøre dette, skal du overveje at oprette en gruppe til Outlook i stedet. Du kan få mere [at vide Microsoft 365 Opret en gruppe Microsoft 365 Administration](../create-groups/create-groups.md).

- **Brug med Outlook:** Ud over at bruge Outlook på internettet fra din browser til at få adgang til delte postkasser kan du også bruge Outlook til iOS-appen eller Outlook til Android-appen. Du kan få mere at vide [under Føj en delt postkasse Outlook mobile](https://support.microsoft.com/office/f866242c-81b2-472e-8776-6c49c5473c9f). En anden mulighed er at oprette en gruppe til din delte postkasse. Du kan få mere at vide under [Sammenlign grupper](../create-groups/compare-groups.md).

- **Kryptering:** Du kan ikke kryptere mails, der sendes fra en delt postkasse. Det skyldes, at en delt postkasse ikke har sin egen sikkerhedskontekst (brugernavn/adgangskode), så den kan ikke tildeles en nøgle. Hvis mere end én person er medlem, og vedkommende sender/modtager mails, der er krypteret med sine egne nøgler, kan andre medlemmer muligvis læse mailen, mens andre muligvis ikke gør det, afhængigt af hvilken offentlig nøgle mailen blev krypteret med.

- **Postkassekonvertering:** Du kan konvertere brugerpostkasser til delte postkasser. Se [Konvertér en brugerpostkasse til en delt postkasse](convert-user-mailbox-to-shared-mailbox.md).

- **Administratorroller:** Brugere med global administrator eller Exchange administratorroller kan oprette delte postkasser.

- **Abonnementskrav:** Hvis du vil oprette en delt postkasse, skal du abonnere på en Microsoft 365 for business-plan, der omfatter mail (Exchange Online-tjenesten). Abonnementet Microsoft 365 Apps for business ikke mail. Microsoft 365 Business Standard omfatter mail.

- **Logger på:** En delt postkasse er ikke beregnet til direkte logon fra den tilknyttede brugerkonto. Du bør altid blokere logon for den delte postkassekonto og holde det blokeret.

- **For mange brugere:** Når der samtidig er for mange angivne brugere, der tilgår en delt postkasse (det anbefales ikke at have mere end 25), kan de periodisk undlade at oprette forbindelse til denne postkasse eller have uoverensstemmelser som meddelelser, der duplikeres i udbakken. I dette tilfælde kan du overveje at reducere antallet af brugere eller bruge en anden arbejdsbyrde, f.eks. en Microsoft 365 gruppe eller en offentlig mappe.

- **Sletning af meddelelse:** Du kan desværre ikke forhindre folk i at slette meddelelser i en delt postkasse. Den eneste måde at løse dette på er at oprette Microsoft 365 gruppe i stedet for en delt postkasse. En gruppe i Outlook er ligesom en delt postkasse. Se en sammenligning af de to i [Sammenlign grupper](../create-groups/compare-groups.md). Du kan få mere at vide om grupper under [Få mere at vide om grupper](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2).

- **Multi-Geo** I et multi-geo-miljø skal delte postkasser have licens på samme måde, som en brugerpostkasse er licenseret. Bemærk, at overvågning af postkasser på tværs af geografiske geografiske postkasser ikke understøttes. Hvis en bruger f.eks. har fået tildelt adgangstilladelse til en delt postkasse på en anden geoplacering, logføres postkassehandlinger, der udføres af den pågældende bruger, ikke i postkassens overvågningslog for den delte postkasse. 


> [!NOTE]
> For at få adgang til en delt postkasse skal en bruger have en Exchange Online-licens, men den delte postkasse kræver ikke en separat licens. Hver delt postkasse har en tilsvarende brugerkonto. Bemærk, hvordan du ikke blev bedt om at angive en adgangskode, da du oprettede den delte postkasse? Kontoen har en adgangskode, men den er systemgenereret (ukendt). Du bør ikke bruge kontoen til at logge på den delte postkasse. Uden en licens er delte postkasser begrænset til 50 GB. Hvis du vil øge størrelsesgrænsen til 100 GB, skal den delte postkasse være tildelt Exchange Online Plan 2-licens. Licensen Exchange Online Plan 1 med en Exchange Online-arkivering-tilføjelseslicens øger kun størrelsen af arkivpostkassen. Dette gør det også muligt at aktivere automatisk udvidende arkivering for yderligere arkiveringskapacitet. Ligeledes, hvis du vil placere en delt postkasse i retslig venteposition, skal den delte postkasse have en Exchange Online Plan 2-licens eller en Exchange Online Plan 1-licens med en Exchange Online-arkivering-tilføjelseslicens. Hvis du vil anvende avancerede funktioner som f.eks. Microsoft Defender til Office 365, Advanced eDiscovery eller automatiske opbevaringspolitikker, skal den delte postkasse have licens til disse funktioner.

## <a name="related-content"></a>Relateret indhold

[Opret en delt postkasse](create-a-shared-mailbox.md) (artikel)\
[Konfigurer en delt postkasse](configure-a-shared-mailbox.md) (artikel)\
[Konvertér en brugerpostkasse til en delt postkasse](convert-user-mailbox-to-shared-mailbox.md) (artikel)\
[Fjern en licens fra en delt postkasse](remove-license-from-shared-mailbox.md) (artikel)\
[Løse problemer med delte postkasser](resolve-issues-with-shared-mailboxes.md) (artikel)
