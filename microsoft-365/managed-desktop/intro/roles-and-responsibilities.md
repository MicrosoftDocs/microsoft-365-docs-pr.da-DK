---
title: Microsoft-administrerede skrivebordsroller og -ansvarsområder
description: I denne artikel beskrives de roller og ansvarsområder, der leveres af Microsoft til Microsoft til Microsoft Managed Desktop.
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: fc12abb598ead3e7304e51307295f1f9c4866be4
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587466"
---
# <a name="microsoft-managed-desktop-roles-and-responsibilities"></a>Microsoft-administrerede skrivebordsroller og -ansvarsområder

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/admin-access); do not delete.-->
<!-- from Roles and responsibilities -->

Når din organisation er tilmeldt Microsoft Managed Desktop, hvad gør Microsoft så for dig? Og hvad er organisationens ansvarsområder?

## <a name="microsofts-roles-and-responsibilities"></a>Microsofts roller og ansvarsområder

Microsoft leverer disse vigtige roller og ansvarsområder:

| Rolle eller ansvar | Beskrivelse |
| ----- | ----- |
| Administration af MDM-politik | Microsoft vil anvende MDM-politikker i overensstemmelse med bedste praksis og tage højde for anmodninger om ændringer af politikken. Vi vil også foretage ændringer i din lejer, som angivet i [Enhedspolitikker](../service-description/device-policies.md). |
| Brugersupport | Vi giver dig en mekanisme til øget adgang til enheder og problemer, der kan eskaleres gennem en supportanmodning, hvis det er nødvendigt. Du kan finde flere oplysninger [under Brugersupport](../service-description/user-support.md).
| Support til Microsoft-administreret skrivebordstjeneste | Microsoft yder support til din it-afdeling via et Microsoft Managed Desktop Operations Team. Dette team understøtter teknisk fejlfinding, ændringsanmodninger og hændelsesstyring for kundens Microsoft Managed Desktop-miljø. Du kan få mere at vide [under Administratorsupport til Microsoft Managed Desktop](../working-with-managed-desktop/admin-support.md). |
| Sikkerhedsovervågning | Microsoft overvåger dine Microsoft-administrerede skrivebordsenheder ved hjælp af Microsoft Defender til slutpunkt. Hvis Microsoft Managed Desktop Security Operations Center (SOC) registrerer en trussel, giver vi dig besked, isolerer enheden og retter problemet eksternt. Du kan finde flere oplysninger under [Sikkerhed](../service-description/security.md). |
| Opdater overvågning og administration | Vi overvåger aktivt dine Microsoft-administrerede skrivebordsenheder for at sikre, at den nyeste kvalitet og de nyeste funktionsopdateringer installeres til Microsoft Windows og Microsoft Office. Du kan få mere at vide [under Sådan håndteres opdateringer](../service-description/updates.md). |
| Gruppering af brugere og enheder | Microsoft Managed Desktop Operations Team opretter og administrerer nødvendige enheder og brugergrupper som en del af it-handlinger. Ingen medlemskabs- eller konfigurationsændringer er tilladt for disse grupper. Ændring af disse grupper kan føre til uventet konfiguration af enheder og tab af funktionalitet. For eventuelle problemer eller spørgsmål vedrørende disse grupper, når de er etableret, kan it-administratorer kontakte Microsoft Managed Desktop-handlinger. Du kan få mere at vide [under Administratorsupport til Microsoft Managed Desktop](../working-with-managed-desktop/admin-support.md). |

## <a name="your-roles-and-responsibilities"></a>Dine roller og ansvarsområder

Dette sæt almindelige roller og ansvarsområder er påkrævet for installationen, men leveres ikke af Microsoft. Den er ikke komplet, men gælder for de fleste organisationer. Der er nogle få elementer, som både du og Microsoft deler ansvaret for.

| Rolle eller ansvar | Beskrivelse |
| ----- | ----- |
| Administration af ændringer | Microsoft giver kunderne besked på forhånd, når der skal foretages ændringer i deres Microsoft Managed Desktop-miljø. Du kan få mere at vide [under Tjenesteændringer og -kommunikation](../service-description/servicechanges.md).<br><br>Du skal have din egen proces til styring af ændringer og have etableret en kontakt med Microsoft Managed Desktop Operations-teamet. Du skal også have ressourcer til at gennemse og godkende disse ændringer. Du kan finde flere oplysninger [under Handlinger og overvågning](../service-description/operations-and-monitoring.md). |
| Administration af identitet | Du er ansvarlig for at oprette brugerkonti, tildele grupper brugere og holde metadata opdateret. |
| Microsoft 365 Apps for enterprise konfiguration og administration | Microsoft er ansvarlig for at Office, at programmerne installeres til brugere, og at disse programmer holdes opdaterede. <br><br> Du er ansvarlig for at administrere Microsoft 365 tjenester og politikker, herunder Exchange Online administrationens ansvarsområder:<br><ul><li>Mailadministration</li><li> Konfiguration af postkasse og regel</li><li>Exchange lokal administration</li></ul><br>Du er også ansvarlig for samarbejdsværktøjer, SharePoint serveradministration, domæneadministration og politikker for sikkerhed og oplysninger, som er angivet i Microsoft 365 Administration. |
| Brugersupport | Giv al brugersupport og teknisk hjælp fra første kontakt til løsning for brugeren, enten af dig eller gennem en udpeget supportpartner. Du skal enten yde brugersupport direkte eller arbejde sammen med en partner for at yde support til disse områder: <br><ul><li>Infrastruktur på stedet: al netværks- og internetforbindelse, VPN-infrastruktur og klientkonfiguration, lokalt mødelokaleudstyr, printere, proxyserver og konfiguration samt firewalls.</li><li>Skybaserede ressourcer i hele virksomheden: mail, SharePoint, samarbejdstjenester og anden skyinfrastruktur, der relaterer til virksomhedens teknologiforbrug.</li><li>Line of business og andre virksomhedsspecifikke programmer.</li></ul>
| Apps | Roller og ansvarsområder varierer i nogen grad for de apps, der leveres som en del af Microsoft-administreret skrivebord, i forhold til de apps, du angiver. <br><br>Til apps, der leveres af Microsoft (Microsoft 365 Apps for enterprise, der omfatter Word, Excel, PowerPoint, Outlook, Publisher, Access, Skype for Business, Teams og OneNote), yder **Microsoft** den komplette tjeneste til installation, opdatering og support. **Du** skal hente og tildele licenser til disse apps, føje brugere til sikkerhedsgrupper, administrere slutningen af levetiden og installere de tilføjelsesprogrammer, du har brug for.<br><br>For apps, du leverer (f.eks. dine line of business-apps), er du ansvarlig for disse **handlinger, uanset** om du pakker dem selv eller ansætter en ikke-Microsoft-leverandør til at gøre det: <br><ul><li>Identificere de programmer, der skal bruges til målrettede brugergrupper</li><li>Oprettelse og administration af Azure AD-grupper til installation af apps</li><li>Pakke apps, så de Microsoft Intune til installationsstandarder</li><li> Overførsel af apps til Microsoft Intune</li><li>Test af apps i Microsoft Managed Desktop-miljø</li><li>Test af apps med dine brugere</li><li>Administration og tildeling af brugere til programmer</li><li>Identificer og installér programopdateringer via Microsoft Intune</li><li>Fjernelse og fjernelse af programmer, når de er udgået</li><li>Fremskaffe og tildele licenser</li><li>Give brugersupport til line of business-apps</li><li> Administrere appindstillinger eksternt</li></ul><br>**Microsoft** leverer Microsoft Intune til levering af programmerne til fjernklienter.<br><br>Du kan finde flere oplysninger under [Apps](../get-ready/apps.md).
| Sikkerhedsovervågning og -svar | Du er ansvarlig for at undersøge og løse hændelser for enheder, der ikke er Microsoft-administrerede stationære enheder. Du skal sikre dig, at Microsoft Managed Desktop Operations Team er orienteret om eventuelle problemer, der kan påvirke tjenesten.
| Driftssupport | Du skal angive en liste over foretrukne kontakter og emneeksperter i organisationen. Vi har brug for disse kontakter, hvis der er en driftshændelse, der ikke er relateret til Microsoft Managed Desktop. <br><br>Du er også ansvarlig for at undersøge og løse hændelser for enheder og tjenester, der ikke findes i Microsoft Managed Desktop. Du skal sørge for, at Microsoft Managed Desktop Operations Team altid er informeret.
| Netværksinfrastruktur, herunder VPN | Du er ansvarlig for konfiguration og administration (herunder fejlfinding og fejlfinding) af al netværksrelateret infrastruktur og alle netværkstjenester. Dette omfatter også internetforbindelse, netværkskontrolelementer, proxykonfiguration og fjernforbindelsesinfrastruktur.<br><br>Hvis en proxy er konfigureret (i hardware eller software), er der en samling af URL-adresser, der skal være tilladt af proxyen. Du er ansvarlig for fejlfinding af eventuelle konflikter eller kompatibiliteter på grund af flere proxyer. Du kan tilføje netværks proxyer, der er specifikke for organisationen, ved hjælp af konfigurerbare indstillinger. Du kan finde flere oplysninger [under Konfigurerbare indstillinger](../working-with-managed-desktop/config-setting-ref.md#proxy).<br><br>Du kan finde flere oplysninger under [Konfiguration af proxy](../get-ready/network.md).
| Udskrivning | Du er ansvarlig for at installere, vedligeholde og administrere printere og udskriftskøer. Udskrivning i skyen er en anbefalet løsning, men det er ikke påkrævet.
