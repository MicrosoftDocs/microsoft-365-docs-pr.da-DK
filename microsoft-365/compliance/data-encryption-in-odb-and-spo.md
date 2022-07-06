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
ms.openlocfilehash: 5b56caed2a93bf482509a4a90a8bbc3a828d76e7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630141"
---
# <a name="data-encryption-in-onedrive-for-business-and-sharepoint-online"></a>Datakryptering i OneDrive for Business og SharePoint Online

Forstå de grundlæggende elementer i kryptering af datasikkerhed i OneDrive for Business og SharePoint Online.
  
## <a name="security-and-data-encryption-in-office-365"></a>Sikkerhed og datakryptering i Office 365

Microsoft 365 er et yderst sikkert miljø, der tilbyder omfattende beskyttelse i flere lag: sikkerhed i fysiske datacentre, netværkssikkerhed, adgangssikkerhed, programsikkerhed og datasikkerhed. I denne artikel fokuseres der specifikt på krypteringssiden under overførsel og inaktiv kryptering af datasikkerhed for OneDrive for Business og SharePoint Online.
  
Se, hvordan datakryptering fungerer i følgende video.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/dea0dec4-4077-4095-9a32-19b94ea2da4b?autoplay=false]
  
## <a name="encryption-of-data-in-transit"></a>Kryptering af data under overførsel

I OneDrive for Business og SharePoint Online er der to scenarier, hvor data indtaster og afslutter datacentrene.
  
- **Klientkommunikation med serveren** Kommunikation til OneDrive for Business på tværs af internettet bruger SSL/TLS-forbindelser. Alle SSL-forbindelser oprettes ved hjælp af 2048-bit nøgler.

- **Dataflytning mellem datacentre** Den primære årsag til at flytte data mellem datacentre er georeplikering for at aktivere it-katastrofeberedskab. Det kan f.eks. være, at SQL Server transaktionslogge og blob storage-deltaer bevæger sig langs denne pipe. Selvom disse data allerede sendes ved hjælp af et privat netværk, er de yderligere beskyttet med den bedste kryptering. 

## <a name="encryption-of-data-at-rest"></a>Kryptering af inaktive data

Inaktiv kryptering omfatter to komponenter: BitLocker-kryptering på diskniveau og kryptering pr. fil af kundeindhold.
  
BitLocker er installeret til OneDrive for Business og SharePoint Online på tværs af tjenesten. Kryptering pr. fil findes også i OneDrive for Business og SharePoint Online i Microsoft 365-multilejer og nye dedikerede miljøer, der er baseret på teknologi med flere lejere.
  
Selvom BitLocker krypterer alle data på en disk, går kryptering pr. fil endnu længere ved at inkludere en entydig krypteringsnøgle for hver fil. Desuden krypteres alle opdateringer til alle filer ved hjælp af deres egen krypteringsnøgle. Nøglerne til det krypterede indhold gemmes på en fysisk separat placering fra indholdet. Hvert trin i denne kryptering bruger AES (Advanced Encryption Standard) med 256-bit nøgler og er FIPS (Federal Information Processing Standard) 140-2-kompatibel. Det krypterede indhold distribueres på tværs af en række objektbeholdere i hele datacenteret, og hver objektbeholder har entydige legitimationsoplysninger. Disse legitimationsoplysninger gemmes på en separat fysisk placering fra enten indholds- eller indholdsnøglerne.
  
Du kan finde flere oplysninger om OVERHOLDELSE AF FIPS 140-2 i [FIPS 140-2-overholdelse](/previous-versions/sql/sql-server-2008-r2/bb326611(v=sql.105)).
  
Kryptering på filniveau af inaktive data udnytter bloblageret til at sikre en praktisk talt ubegrænset lagervækst og muliggøre beskyttelse uden fortilfælde. Alt kundeindhold i OneDrive for Business og SharePoint Online overføres til blob storage. Sådan sikres disse data:
  
1. Alt indhold krypteres, muligvis med flere nøgler, og distribueres på tværs af datacenteret. Hver fil, der skal gemmes, opdeles i et eller flere dele, afhængigt af dens størrelse. Derefter krypteres hvert afsnit ved hjælp af sin egen entydige nøgle. Opdateringer håndteres på samme måde: Det sæt ændringer eller deltaer, der sendes af en bruger, opdeles i dele, og hver af dem krypteres med sin egen nøgle.

2. Alle disse segmenter – filer, filer og opdateringsdeltaer – gemmes som blobs i vores bloblager. De er også tilfældigt fordelt på tværs af flere blob-objektbeholdere.

3. Det "kort", der bruges til at samle filen igen fra dens komponenter, gemmes i indholdsdatabasen.

4. Hver blobobjektbeholder har sine egne entydige legitimationsoplysninger pr. adgangstype (læse, skrive, optælle og slette). Hvert sæt legitimationsoplysninger opbevares i Secure Key Store og opdateres jævnligt.

Med andre ord er der tre forskellige typer butikker, der er involveret i inaktiv kryptering pr. fil, som hver især har en særskilt funktion:
  
- Indhold gemmes som krypterede blobs i bloblageret. Nøglen til hvert indholdssegment krypteres og gemmes separat i indholdsdatabasen. Selve indholdet indeholder ingen anelse om, hvordan det kan dekrypteres.

- Indholdsdatabasen er en SQL Server database. Det indeholder det kort, der kræves for at finde og samle alle de indholdsblob, der findes i bloblageret, samt de nøgler, der er nødvendige for at dekryptere disse blobs.

Hver af disse tre lagerkomponenter – bloblageret, indholdsdatabasen og nøglelageret – er fysisk adskilt. Oplysningerne i en af komponenterne kan ikke bruges alene. Dette giver et hidtil uset sikkerhedsniveau. Uden adgang til alle tre er det umuligt at hente nøglerne til delene, dekryptere nøglerne for at gøre dem brugbare, knytte nøglerne til deres tilsvarende dele, dekryptere dele eller genskabe et dokument fra dets bestanddele.
