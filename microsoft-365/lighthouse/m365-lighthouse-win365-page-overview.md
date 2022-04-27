---
title: Oversigt over siden Windows 365 (cloud-pc'er) i Microsoft 365 Lighthouse
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
description: Få mere at vide om siden Windows 365 (cloud-pc'er) for udbydere af administrerede tjenester ved hjælp af Microsoft 365 Lighthouse.
ms.openlocfilehash: 325fe39c144227052c966b81a8a2109a07fb0cf2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65100275"
---
# <a name="overview-of-the-windows-365-cloud-pcs-page-in-microsoft-365-lighthouse"></a>Oversigt over siden Windows 365 (cloud-pc'er) i Microsoft 365 Lighthouse  
  
Windows 365 er en cloudbaseret tjeneste, der gør det muligt for Microsoft Endpoint Manager (MEM)-administratorer at klargøre og administrere cloud-pc'er for deres brugere, der har en Windows 365 licens. Windows 365 er fuldt integreret med MEM til enhedshåndtering og med Microsoft 365 Lighthouse til partneradministration af cloud-pc'er på tværs af alle deres kundelejere.

Du kan få flere oplysninger om Windows 365 under [Hvad er Windows 365?](/windows-365/overview) Du kan se en liste over krav til Windows 365 under [Krav til Windows 365](/windows-365/enterprise/requirements).

> [!IMPORTANT]
> Du skal gå til [MEM](https://go.microsoft.com/fwlink/p/?linkid=2150463) for at klargøre cloud-pc'er for hver kundelejer, før du kan administrere dem i Lighthouse. Du kan ikke klargøre inde fra Lighthouse.

Når du har klargjort cloud-pc'er til din kundelejer, indeholder kortet Windows 365 på siden Microsoft 365 startside en kort besked om de cloud-pc'er, der har brug for handling, f.eks. antallet af cloud-pc'er, der ikke kunne klargøres, og fejl i Azure-netværksforbindelsen. Hvis du vil have en detaljeret status, skal du vælge knappen på kortet Windows 365 (eller vælge **Windows 365** i navigationsruden til venstre) for at åbne den Windows 365 side. Fra denne side kan du få en statusoversigt over de Cloud-pc'er, der er tildelt dine kundelejere, få vist en liste over alle de cloud-pc'er, du administrerer, og de lejere, de er tildelt, og få vist Azure-netværksforbindelserne mellem dine kundelejere og Azure Active Directory (Azure AD) og deres status.

## <a name="overview-tab"></a>Fanen Oversigt

Under fanen Oversigt viser den farvede linje med antal anmærkninger det samlede antal cloud-pc'er eller Azure-netværksforbindelser på tværs af alle dine kundelejere, der har følgende statusser: Mislykkede netværksforbindelser, Ikke klargjort, Klargøring mislykkedes og Klargøring snart.

Du kan se en oversigt over cloud-pc-statusser for hver kundelejer på listen under anmærkningslinjen. Hvis du vil se, hvilke lejere der har cloud-pc'er med en bestemt status, skal du vælge denne status på linjen med antal anmærkninger for at filtrere listen. Hvis du vil se statusser for cloud-pc'er for en eller flere specifikke kundelejere, skal du bruge rullemenuen **Lejere** til at filtrere listen.

Hvis du vil have detaljerede statusoplysninger for en bestemt kundelejer, skal du vælge en værdi under en af statuskolonnerne for den pågældende lejer. Afhængigt af hvilken kolonne værdien er i, åbnes fanen **Azure-netværksforbindelser** eller **Alle cloud-pc'er** , og der vises flere oplysninger.

Fanen Oversigt indeholder også følgende indstillinger:

- **Opdatere:** Vælg at hente de nyeste Cloud PC-data.
- **Eksport:** Vælg at eksportere Cloud PC-data til en Excel fil med kommaseparerede værdier (.csv).
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt Cloud-pc på listen.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png" alt-text="Skærmbillede af fanen Windows 365 Oversigt." lightbox="../media/m365-lighthouse-win365-page-overview/win365-overview-tab.png":::

## <a name="all-cloud-pcs-tab"></a>Fanen Alle cloud-pc'er

Under fanen Alle cloud-pc'er viser den farvede linje med antal anmærkninger det samlede antal cloud-pc'er på tværs af alle dine kundelejere, der har følgende statusser: Klargjort, Ikke klargjort, Klargøring mislykkedes og Klargøring snart.

Du kan få vist alle cloud-pc'er og deres klargøringsstatus på listen under anmærkningslinjen. Følgende oplysninger er angivet:

- **Navn på cloud-pc:** Navn, der er tildelt cloud-pc'en.
- **Bruger:** Bruger, for hvem en Cloud-pc er blevet klargjort eller forsøgt klargjort.
- **Enhedsnavn:** Intune enhedsnavn – et entydigt id for en Cloud-pc.
- **Lejer:** Kundelejer, hvor en Cloud-pc blev klargjort.
- **Status:** Klargøringsstatus for cloud-pc'en.
- **Licenstype:** Enterprise eller Business.
- **Specifikationer:** Cloud-pc-hardwarekonfiguration.

Hvis du vil se, hvilke lejere der har cloud-pc'er med en bestemt klargøringsstatus, skal du vælge den pågældende status på linjen med antal anmærkninger for at filtrere listen. Hvis du vil se klargøringsstatusser for cloud-pc'er for en eller flere specifikke kundelejere, skal du bruge rullemenuen **Lejere** til at filtrere listen.

Vælg en cloud-pc på listen for at få vist flere oplysninger og udføre administrationshandlinger, f.eks.:
- **Genstarte:** Vælg at genstarte enheden. 
- **Klargøring igen:** Vælg at nulstille enheden. Du kan også få vist klargøringspolitikken i linket Microsoft Endpoint Manager.
- **Omdøbe:** Vælg at omdøbe den enhed, der er tildelt en bruger.

Fanen Alle cloud-pc'er indeholder også følgende indstillinger:

- **Eksport:** Vælg at eksportere Cloud PC-data til en Excel fil med kommaseparerede værdier (.csv).
- **Opdatere:** Vælg at hente de nyeste Cloud PC-data.
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt Cloud-pc på listen.

Hvis du vil se en komplet liste over klargøringsstatusser for cloud-pc'er, og hvad de betyder, skal du se [Oversigt over enhedshåndtering for Cloud-pc'er](/windows-365/enterprise/device-management-overview#column-details) i dokumentationsbiblioteket Windows 365.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png" alt-text="Skærmbillede af fanen Windows 365 alle cloud-pc'er." lightbox="../media/m365-lighthouse-win365-page-overview/all-cloud-pcs-tab.png":::

## <a name="azure-network-connections-tab"></a>Fanen Azure-netværksforbindelser

Under fanen Azure-netværksforbindelser vises det samlede antal Azure-netværksforbindelser på tværs af alle dine kundelejere, der har Windows 365 Enterprise Cloud-pc'er, og som kan have følgende statusser: Vellykkede forbindelser og Mislykkede forbindelser.

På listen under linjen med antal anmærkninger kan du få vist alle Azure-netværksforbindelser og deres forbindelsesstatus.

Hvis du vil se forbindelser med en bestemt klargøringsstatus, skal du vælge denne status på linjen med antal anmærkninger for at filtrere listen. Hvis du vil se forbindelsesstatusser for en eller flere specifikke kundelejere, skal du bruge rullemenuen **Lejere** til at filtrere listen.

Hvis du har brug for at foretage en handling eller foretage fejlfinding af en forbindelse på listen, skal du vælge **Få vist forbindelsesoplysninger i Microsoft Endpoint Manager**.

Fanen Azure-netværksforbindelser indeholder også følgende indstillinger:

- **Eksport:** Vælg at eksportere forbindelsesdata til en Excel fil med kommaseparerede værdier (.csv).
- **Opdatere:** Vælg at hente de mest aktuelle forbindelsesdata.
- **Søg:** Angiv nøgleord for hurtigt at finde en bestemt forbindelse.

:::image type="content" source="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png" alt-text="Skærmbillede af fanen Azure-netværksforbindelser." lightbox="../media/m365-lighthouse-win365-page-overview/azure-network-connections-tab.png":::

## <a name="related-content"></a>Relateret indhold

[Hvad er Windows 365?](/windows-365/overview) (artikel)\
[Windows 365 oversigt over enhedshåndtering for cloud-pc'er](/windows-365/enterprise/device-management-overview) (artikel)\
[ofte stillede spørgsmål om Microsoft 365 fyrtårn](m365-lighthouse-faq.yml) (artikel)