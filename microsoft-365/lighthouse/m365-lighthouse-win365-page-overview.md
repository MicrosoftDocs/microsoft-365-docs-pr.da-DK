---
title: Microsoft 365 siden med Windows 365 (sky-pc'er)
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: For administrerede tjenesteudbydere, der bruger Microsoft 365 Lighthouse, kan du få mere at vide Windows 365 siden (sky-pc'er).
ms.openlocfilehash: fa910e3de992aa3f3f76090f76a473a96aebc8fb
ms.sourcegitcommit: 9d563faeaa50b59b0b468dbb373d886e5270f58e
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/24/2022
ms.locfileid: "64387074"
---
# <a name="windows-365-cloud-pcs-page-overview"></a>Windows 365 (Cloud pc'er) sideoversigt  
  
Windows 365 er en skybaseret tjeneste, der gør det muligt for Microsoft Endpoint Manager-administratorer (MEM) at klargøre og administrere skybaserede pc'er for deres brugere, der har en Windows 365 licens. Windows 365 fuldt integreret med MEM til enhedshåndtering og med Microsoft 365 Lighthouse til partneradministration af sky-pc'er på tværs af alle deres kundelejere.

Du kan finde flere oplysninger Windows 365 under [Hvad er Windows 365?](/windows-365/overview) Du kan finde en Windows 365 over alle krav [i Forudsætninger for Windows 365](/windows-365/enterprise/requirements).

> [!IMPORTANT]
> Du skal gå til [MEM for at](https://go.microsoft.com/fwlink/p/?linkid=2150463) klargøre sky-pc'er til hver kundelejer, før du kan administrere dem i Fyrtårn. Du kan ikke klargøre fra Lighthouse.

Når du har klargjort sky-pc'er til din kundelejer, giver Windows 365-kortet på Microsoft 365-startsiden en kort besked på de skybaserede pc'er, hvor der er behov for handling, f.eks. antallet af sky-pc'er, der ikke kunne klargøres, og fejl i Azure-netværksforbindelsen. Hvis du vil have en detaljeret status, skal du vælge knappen på Windows 365 (eller vælge **Windows 365** i venstre navigationsrude) for at åbne Windows 365 side. Fra denne side kan du få en statusoversigt over de skybaserede pc'er, der er tildelt dine kundelejere, få vist en liste over alle de sky-pc'er, du administrerer, og de lejere, de er tildelt, og få vist Azure-netværksforbindelser mellem dine kundelejere og Azure Active Directory (Azure AD) og deres status.

## <a name="overview-tab"></a>Fanen Oversigt

På fanen Oversigt viser den farvede antal anmærkningslinje det samlede antal sky-pc'er eller Azure-netværksforbindelser på tværs af alle dine kundelejere, der har følgende status: Mislykkede netværksforbindelser, Ikke klargjort, Klargøring mislykkedes og Fjern snart.

Du kan se en oversigt over Cloud PC-statusser for hver kundelejer på listen under anmærkningslinjen. Hvis du vil se, hvilke lejere der har skybaserede pc'er med en bestemt status, skal du vælge denne status på anmærkningslinjen for at filtrere listen. Hvis du vil se statusser for skyen til pc for en eller flere bestemte  lejere, skal du bruge rullemenuen Lejere til at filtrere listen.

Hvis du vil have detaljerede statusoplysninger for en bestemt kundelejer, skal du vælge en værdi under en af statuskolonnerne for den pågældende lejer. Afhængigt af hvilken kolonne værdien er i, åbnes  fanen Azure-netværksforbindelser eller Alle skybaserede **pc'er** og viser flere oplysninger.

Fanen Oversigt indeholder også følgende indstillinger:

- **Opdater:** Vælg for at hente de mest aktuelle Sky-pc-data.
- **Eksportér:** Vælg for at eksportere Sky-pc-data Excel en fil med kommaseparerede værdier (.csv).
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt sky-pc på listen.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png" alt-text="Skærmbillede af Windows 365 Oversigt." lightbox="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png":::

## <a name="all-cloud-pcs-tab"></a>Fanen Alle sky-pc'er

På fanen Alle skybaserede pc'er viser den farvede antal anmærkningslinje det samlede antal sky-pc'er på tværs af alle dine kundelejere, der har følgende statusser: Klargjort, Ikke klargjort, Klargøring mislykkedes og Fjernet snart.

Du kan få vist alle sky-pc'er og deres klargøringsstatus på listen under anmærkningslinjen. Følgende oplysninger gives:

- **Navn på sky-pc:** Navn, der er tildelt cloud-pc'en.
- **Lejer:** Kundelejer, hvor en cloud-pc blev klargjort.
- **Enhedsnavn:** Intune enhedsnavn – et entydig identifier til en sky-pc.
- **Pc-type:** Cloud-pc i overensstemmelse med standard-SKU'er.
- **Status:** Klargøringsstatus for Cloud-pc'en.
- **Bruger:** Bruger, som en sky-pc er blevet klargjort eller forsøgt at blive klargjort til.

Hvis du vil se, hvilke lejere der har skybaserede pc'er med en bestemt klargøringsstatus, skal du vælge denne status på anmærkningslinjen for at filtrere listen. Hvis du vil se klargøringsstatusser for en eller flere bestemte kunder, skal du  bruge rullemenuen Lejere til at filtrere listen.

Vælg en skybaseret pc på listen for at få vist flere oplysninger. Hvis du skal handle på sky-pc'en, er der mulighed for at få vist politikker for klargøring af lejere og enhedsoplysninger Microsoft Endpoint Manager.

Fanen Alle sky-pc'er indeholder også følgende indstillinger:

- **Opdater:** Vælg for at hente de mest aktuelle Sky-pc-data.
- **Eksportér:** Vælg for at eksportere Sky-pc-data Excel en fil med kommaseparerede værdier (.csv).
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt sky-pc på listen.
- **Prøv klargøring igen:** Vælg 1-20 sky-pc'er på listen, der har statussen **Klargøring** mislykkedes, og vælg derefter denne indstilling for at prøve klargøring for disse sky-pc'er igen.

Hvis du vil se en komplet liste over klargøringsstatusser for cloud-pc, og hvad de betyder, skal du se Oversigt over enhedshåndtering [for](/windows-365/enterprise/device-management-overview#column-details) sky-pc'er Windows 365 biblioteket med dokumentation.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Skærmbillede af fanen Windows 365 alle sky-pc'er." lightbox="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png":::

## <a name="azure-network-connections-tab"></a>Fanen Azure-netværksforbindelser

På fanen Azure-netværksforbindelser viser den farvede antal-anmærkningslinje det samlede antal Azure-netværksforbindelser på tværs af alle dine kundelejere, der har følgende status: Vellykkede forbindelser og mislykkede forbindelser.

På listen under antal anmærkningslinjen kan du se alle Azure-netværksforbindelser og deres forbindelsesstatus.

Hvis du vil have vist forbindelser med en bestemt klargøringsstatus, skal du vælge denne status på linjen med antal anmærkninger for at filtrere listen. Hvis du vil se forbindelsesstatusser for en eller flere bestemte kundelejere, skal du **bruge** rullemenuen Lejere til at filtrere listen.

Hvis du skal foretage en handling eller foretage fejlfinding af en forbindelse på listen, skal du **vælge Vis oplysninger om forbindelse Microsoft Endpoint Manager**.

Fanen Azure-netværksforbindelser indeholder også følgende indstillinger:

- **Opdater:** Vælg for at hente de mest aktuelle forbindelsesdata.
- **Eksportér:** Vælg for at eksportere forbindelsesdata til Excel en fil med kommaseparerede værdier (.csv).
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt forbindelse.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png" alt-text="Skærmbillede af fanen Azure-netværksforbindelser." lightbox="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png":::

## <a name="related-content"></a>Relateret indhold

[Hvad er Windows 365?](/windows-365/overview) (artikel)\
[Windows 365 oversigt over enhedsstyring for Cloud-pc'er](/windows-365/enterprise/device-management-overview) (artikel)\
[Microsoft 365 ofte stillede spørgsmål om fyrtårn](m365-lighthouse-faq.yml) (artikel)