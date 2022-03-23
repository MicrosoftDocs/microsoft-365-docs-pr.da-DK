---
title: Datakryptering i OneDrive for Business og SharePoint Online
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 9/20/2021
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- M365-security-compliance
- SPO_Content
description: Forstå de grundlæggende elementer i kryptering af datasikkerhed i OneDrive for Business og SharePoint Online.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 25bebc8fd5ab9b820667f5220785b021230ca6e1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63587271"
---
# <a name="data-encryption-in-onedrive-for-business-and-sharepoint-online"></a>Datakryptering i OneDrive for Business og SharePoint Online

Forstå de grundlæggende elementer i kryptering af datasikkerhed i OneDrive for Business og SharePoint Online.
  
## <a name="security-and-data-encryption-in-office-365"></a>Sikkerhed og datakryptering i Office 365

Microsoft 365 er et meget sikkert miljø, der yder omfattende beskyttelse i flere lag: fysisk datacentersikkerhed, netværkssikkerhed, adgangssikkerhed, programsikkerhed og datasikkerhed. Denne artikel fokuserer specifikt på krypteringssiden under overførsel og in-rest af datasikkerhed til OneDrive for Business og SharePoint Online.
  
Se, hvordan datakryptering fungerer i følgende video.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/dea0dec4-4077-4095-9a32-19b94ea2da4b?autoplay=false]
  
## <a name="encryption-of-data-in-transit"></a>Kryptering af data under overførsel

I OneDrive for Business og SharePoint Online er der to scenarier, hvor data kommer ind i og forlader datacentrene.
  
- **Klientkommunikation med serveren** Kommunikation til OneDrive for Business over internettet bruger SSL/TLS-forbindelser. Alle SSL-forbindelser etableres ved hjælp af 2048-bit nøgler.

- **Databevægelse mellem datacentre** Den primære årsag til at flytte data mellem datacentre er for geo-replikering for at aktivere gendannelse efter nedbrud. For eksempel SQL Server transaktionslogfiler og blob-lagerdeltas langs dette rør. Selvom disse data allerede overføres ved hjælp af et privat netværk, beskyttes de yderligere med klassens bedste kryptering. 

## <a name="encryption-of-data-at-rest"></a>Kryptering af in rest-data

Kryptering omfatter to komponenter: BitLocker-kryptering på diskniveau og kryptering pr. fil af kundeindhold.
  
BitLocker installeres til OneDrive for Business og SharePoint Online på tværs af tjenesten. Kryptering pr. fil er også i OneDrive for Business og SharePoint Online i Microsoft 365-miljøer med flere lejere og nye dedikerede miljøer, der er bygget på teknologi med flere lejere.
  
Mens BitLocker krypterer alle data på en disk, går kryptering pr. fil endnu mere ved at medtage en unik krypteringsnøgle for hver fil. Desuden krypteres alle opdateringer til alle filer ved hjælp af sin egen krypteringsnøgle. Nøgler til det krypterede indhold gemmes fysisk adskilt fra indholdet. Hvert trin i denne kryptering bruger AES (Advanced Encryption Standard) (AES) med 256-bit nøgler og er Federal Information Processing Standard (FIPS) 140-2 kompatibel. Det krypterede indhold fordeles på tværs af et antal objektbeholdere i hele datacenteret, og hver beholder har entydige legitimationsoplysninger. Disse legitimationsoplysninger gemmes på en separat fysisk placering fra enten indholdsnøglerne eller indholdsnøglerne.
  
Du kan finde flere oplysninger om overholdelse af FIPS 140-2 i [OVERHOLDELSE AF FIPS 140-2](/previous-versions/sql/sql-server-2008-r2/bb326611(v=sql.105)).
  
Kryptering på filniveau udnytter blob-lagerplads til næsten ubegrænset lagringsvækst og giver mulighed for beskyttelse på alle dine filer. Alt kundeindhold i OneDrive for Business og SharePoint Online overføres til BLOB-lagerplads. Sådan sikres disse data:
  
1. Alt indhold er krypteret, potentielt med flere nøgler og fordelt på tværs af datacenteret. Hver fil, der skal gemmes, er opdelt i et eller flere dele afhængigt af størrelsen. Derefter krypteres hvert afsnit ved hjælp af sin egen entydige nøgle. Opdateringer håndteres på samme måde: sættet af ændringer, eller deltaer, der sendes af en bruger, er opdelt i dele, og hver er krypteret med sin egen nøgle.

2. Alle disse dele – filer, filer og opdatering af deltaer – gemmes som blobs i vores blob-lager. De er også tilfældigt fordelt på tværs af flere blobbeholdere.

3. Det "kort", der bruges til at samle filen igen fra dens komponenter, gemmes i indholdsdatabasen.

4. Hver blobbeholder har sine egne entydige legitimationsoplysninger pr. adgangstype (læs, skriv, optælling og sletning). Hvert sæt af legitimationsoplysninger opbevares i den sikre nøgles Store og opdateres jævnligt.

Med andre ord er der tre forskellige typer butikker involveret i kryptering pr. fil i hvile, hver med en særskilt funktion:
  
- Indhold gemmes som krypterede blobs i blob-lageret. Nøglen til hver del af indholdet krypteres og gemmes separat i indholdsdatabasen. Selve indholdet giver ingen fingerpeg om, hvordan det kan dekrypteres.

- Indholdsdatabasen er en SQL Server database. Den indeholder kortet, der er påkrævet for at finde og samle alt indhold blobs, der opbevares i bloblageret, samt de taster, der skal bruges til at dekryptere disse blobs.

Hver af disse tre lagringskomponenter – bloblageret, indholdsdatabasen og nøglenøglen Store – er fysisk adskilt. De oplysninger, der opbevares i en af komponenterne, er ubrugelige i sig selv. Dette giver et sikkerhedsniveau på alle niveauer. Uden adgang til alle tre er det umuligt at hente tasterne til delene, dekryptere tasterne for at gøre dem anvendelige, knytte nøglerne til deres tilsvarende dele, dekryptere et hvilket som helst afsnit eller genoprette et dokument fra dets dele.