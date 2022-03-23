---
title: Lejeradministration for Microsoft 365 til virksomheder
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
- m365solution-tenantmanagement
- m365solution-overview
- tenant-management
ms.custom:
- Ent_Solutions
description: En oversigt over planlægning, installation og vedvarende drift af dine Microsoft 365 lejere.
ms.openlocfilehash: 7a9545800c3f5f08b8094290c4173b4368caff4d
ms.sourcegitcommit: 22cae7ec541268d519d45518c32f22bf5811aec1
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/10/2022
ms.locfileid: "63592757"
---
# <a name="tenant-management-for-microsoft-365-for-enterprise"></a>Lejeradministration for Microsoft 365 til virksomheder

Hvis du vil have en sti til organisationens digitale transformation med cloud computing, kræver det et fast grundlag, som dine medarbejdere kan stole på i forhold til produktivitet, samarbejde, ydeevne, beskyttelse af personlige oplysninger, overholdelse af regler og standarder og sikkerhed.

Korrekt konfiguration af dine Microsoft 365-lejere giver et fundament, så dine medarbejdere kan fokusere på at få deres arbejde udført, og din it-afdeling til at fokusere på ende-til-ende-løsninger, der giver ekstra værdi for virksomheden.

Denne løsning fører dig gennem konfigurationen af det pågældende grundlag i disse trin:

1. Bestem dine lejere
2. Optimer dit netværk
3. Synkroniser dine identiteter, og gennemtving sikre logons
4. Overfør Windows enheder, Office kunder og lokale servere Office data
5. Installér enheds- og appadministration

Men først skal vi bruge et øjeblik på at forstå, hvordan en lejer er, og hvordan en lejer, der giver et firma fundament, ser ud.

## <a name="a-microsoft-365-tenant-defined"></a>En Microsoft 365 lejer defineret

En Microsoft 365 lejer er en dedikeret forekomst af tjenesterne i Microsoft 365 og dine organisationsdata, der er gemt på en bestemt standardplacering, f.eks. Europa eller Nordamerika. Denne placering angives, når du opretter lejeren for organisationen. Hver Microsoft 365 lejer er særskilt, entydig og adskilt fra alle Microsoft 365 lejere. Du opretter en Microsoft 365 lejer, når du køber et eller flere produkter fra Microsoft, f.eks. Microsoft 365 E3 eller E5, og et sæt licenser til hver.

Din Microsoft 365-lejer omfatter også en Azure Active Directory (Azure AD)-lejer, som er en dedikeret forekomst af Azure AD til brugerkonti, grupper og andre objekter. Hver Azure AD-lejer er særskilt, entydig og adskilt fra alle andre Azure AD-lejere. Organisationen kan have flere Azure AD-lejere, som du kan konfigurere med Azure-abonnementer, men Microsoft 365-lejere kan kun bruge en enkelt Azure AD-lejer, som blev oprettet, da du oprettede lejeren.

Her er et eksempel:

![Et eksempel Microsoft 365 lejer med dens Azure AD-lejer.](../media/tenant-management-overview/tenant-management-example-tenant.png)

*Lejeradministration* er planlægning, installation og løbende drift af dine Microsoft 365 lejere.

## <a name="attributes-of-a-well-designed-and-operating-tenant"></a>Attributter for en veldesignet og driftslejer

Ud over det korrekte navn og placering for din lejer er der yderligere elementer at planlægge,&mdash; installere og administrere for at sikre, at dine brugeres oplevelser med skyproduktivitetsapps såsom Microsoft Teams og Exchange Online&mdash; er effektive, sikre og effektive.

Her er elementerne:

- Du har det korrekte sæt produkter (abonnementer) og licenser.
  - Sættet af produkter passer til din virksomhed, it og sikkerhedsbehov.
  - Der er et tilstrækkeligt antal licenser til dine medarbejdere og forventede ændringer i personale.
- Til netværk:
  - Du har konfigureret de korrekte DNS-domænenavne.
  - Til virksomhedsnetværk har du optimeret netværkstrafik til Microsoft-netværket for medarbejdere på stedet.
  - Du har optimeret netværkstrafik til eksterne medarbejdere, der bruger en VPN-klient.
- Du har synkroniseret dine Active Directory-domæneservices (AD DS) konti, grupper og andre objekter.
  - Dine Azure AD-lejerkonti er knyttet til Exchange Online postkasser med de korrekte DNS-domæner til mailadresser.
  - Dine brugerkonti har fået tildelt de korrekte licenser fra de korrekte købte produkter (f.eks. Microsoft 365 E3 eller E5).
- Du har konfigureret stærk identitet og adgangsstyring.
  - Du kræver sikker bruger login med adgangskodefri eller multifaktorgodkendelse (MFA).
  - Du har Betingede adgangspolitikker, der gennemtvinger krav til logon og begrænsninger for højere sikkerhedsniveauer.
- Lokale servere Office deres data er blevet overført til skyapps, eller de bruges i en hybridkonfiguration.
- Du udfører enhedshåndtering med Intune eller indbygget grundlæggende mobilitet og sikkerhed Microsoft 365.
  - Dine enheder, der ejes af organisationen, registreres og administreres.
  - Appsene til personlige enheder administreres.

Her er et eksempel på en Microsoft 365 lejer med alle disse elementer på plads.

![Et eksempel Microsoft 365 lejer.](../media/tenant-management-overview/tenant-management-tenant-config.png)

I denne illustration Microsoft 365 lejeren:

- Produkter og licenser til Microsoft 365 E3 og E5.
- Microsoft 365 produktivitetsapps.
- Intune med tilmeldte enheder og politikker for enheder og programmer.
- En Azure AD-lejer, der har synkroniseret brugerkonto (grupper og andre katalogobjekter vises ikke), domæner og politikker for betinget adgang.

## <a name="tenant-capabilities-for-microsoft-365-for-enterprise"></a>Lejeregenskaber for Microsoft 365 til virksomheder

De følgende afsnit og tabeller viser de vigtigste funktioner og licenser til trinnene i denne løsning.

### <a name="tenant"></a>Lejer

|Funktionalitet eller funktion|Beskrivelse|Licensering|
|---|---|---|
|Flere lejere|Hver Microsoft 365 lejer er særskilt, entydig og adskilt fra alle Microsoft 365 lejere. Med flere lejere er der begrænsninger og yderligere overvejelser, når du administrerer dem og leverer tjenester til dine brugere.|Microsoft 365 E3 eller E5|
|Overførsel af postkasse på tværs af lejere|Lejeradministratorer kan flytte postkasser mellem lejere med minimal infrastrukturafhængigheder i deres lokale systemer. Dette fjerner behovet for postkasser uden for tavlen og i gang.|Microsoft 365 E3 eller E5|
|Multi-Geo|Din lejer kan gemme in restdata i det andet datacenters geoplaceringer, som du har valgt, så de opfylder kravene til dataopbevaring.|Microsoft 365 E3 eller E5|
|Flyt kernedata til et nyt datacenters geocenter|Efterhånden som Microsoft tilføjer nye datacenter-geos for yderligere kapacitet og beregner ressourcer, kan du anmode om et datacenters geo-flytning for in-geo-dataopbevaring for dine kernekundedata.|Microsoft 365 E3 eller E5|
||||

### <a name="networking"></a>Netværk

|Funktionalitet eller funktion|Beskrivelse|Licensering|
|---|---|---|
|Netværksforbindelse Insights|Målepunkter for netværksydeevne indsamles fra din Microsoft 365 lejer for at hjælpe dig med at designe netværksperimetere for dine kontorplaceringer.|Microsoft 365 E3 eller E5|
|Automatiser slutpunktsopdateringer|Automatiser konfigurationen og løbende opdateringer til Microsoft 365 slutpunkter i PAC-klientens filer og netværksenheder og -tjenester.|Microsoft 365 E3 eller E5|
||||

### <a name="identity"></a>Identitet

|Funktionalitet eller funktion|Beskrivelse|Licensering|
|---|---|---|
|Synkroniser lokale Active Directory-domæneservices (AD DS) med din Azure AD-lejer|Udnyt din lokale identitetsudbyder til brugerkonti, grupper og andre objekter.|Microsoft 365 E3 eller E5|
|MFA gennemtvunget med sikkerhedsstandard|Beskyt dig mod kompromitterede identiteter og enheder ved at kræve en anden form for godkendelse til logon. Sikkerhedsstandarden kræver MFA for alle brugerkonti.|Microsoft 365 E3 eller E5|
|MFA gennemtvunget med Betinget adgang|Kræv MFA baseret på attributterne for logon med politikker for betinget adgang.|Microsoft 365 E3 eller E5|
|MFA gennemtvunget med risikobaseret betinget adgang|Kræv MFA baseret på risikoen for, at brugeren logger på med Microsoft Defender for Identity.|Microsoft 365 E5 eller E3 med Azure AD Premium P2-licenser|
|Self-Service til nulstilling af adgangskode (SSPR)|Giv dine brugere mulighed for at nulstille eller låse deres adgangskoder eller konti op.|Microsoft 365 E3 eller E5|
||||

### <a name="migration"></a>Overførsel

|Funktionalitet eller funktion|Beskrivelse|Licensering|
|---|---|---|
|Overfør til Windows 10|Overfør dine enheder, der kører Windows 7 eller Windows 8.1, til Windows 10 Enterprise.|Windows 10 Enterprise licenser inkluderet med Microsoft 365 E3 eller E5|
|Overfør til Microsoft 365 Apps for enterprise|Overfør dine Office-klientapps som Word og PowerPoint til de versioner, der er installeret fra skyen, og som er opdateret med nye funktioner.|Microsoft 365 E3 eller E5|
|Overfør lokale servere og data til Microsoft 365|Overfør Exchange postkasser, SharePoint websteder og Skype for Business Online til Microsoft 365 skytjenester.|Microsoft 365 E3 eller E5|
||||

### <a name="device-and-app-management"></a>Enheds- og appadministration

|Funktionalitet eller funktion|Beskrivelse|Licensering|
|---|---|---|
|Microsoft Intune|En skybaseret tjeneste, der giver administration af mobilenheder (MDM) og administration af mobilapps (MAM), der bruges til at styre, hvordan organisationens program og enhederne bruges, herunder mobiltelefoner, tablets og bærbare computere.|Microsoft 365 E3 eller E5|
|Grundlæggende mobilitet og sikkerhed|Gør dine brugeres mobilenheder sikre, f.eks. iPhones, iPads, Android-telefoner Windows telefoner med denne indbyggede tjeneste.|Microsoft 365 E3 eller E5|
||||

## <a name="next-steps"></a>Næste trin

Brug disse trin til at konfigurere og administrere dine Microsoft 365 lejere.

1. [Bestem dine lejere](tenant-management-tenants.md)
2. [Optimer dit netværk](tenant-management-networking.md)
3. [Synkroniser dine identiteter, og gennemtving sikre logons](tenant-management-identity.md)
4. [Overfør dine lokale Office servere og data](tenant-management-migration.md)
5. [Installér enheds- og appadministration](tenant-management-device-management.md)

[![Trinnene til at installere og administrere en Microsoft 365 lejer.](../media/tenant-management-overview/tenant-management-step-grid.png)](tenant-management-tenants.md)

Hvert trin beskriver installationsindstillinger, opsummerer resultaterne og løbende vedligeholdelsesopgaver.

For at forstå, hvordan en fiktiv, men repræsentativ, multi-national organisation udrullede elementerne fra deres Microsoft 365 lejer, skal du se [Contoso-casestudiet](../enterprise/contoso-case-study.md).
