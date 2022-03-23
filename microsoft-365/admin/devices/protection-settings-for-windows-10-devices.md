---
title: Rediger eller angiv indstillinger for programbeskyttelse til Windows 10 enheder
ms.author: sharik
author: skjerland
manager: scotv
audience: Admin
ms.topic: article
f1.keywords:
- Win10AppPolicy
- O365E_Win10AppPolicy
- BCS365_Win10AppPolicy
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 02e74022-44af-414b-9d74-0ebf5c2197f0
description: Få mere at vide om, hvordan du opretter eller redigerer politikker for appadministration og beskytter arbejdsfiler på dine brugeres personlige Windows 10 enheder.
ms.openlocfilehash: 3a565586be4d0dfec308b2dad3b068e01774b161
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63592338"
---
# <a name="set-or-edit-application-protection-settings-for-windows-10-devices"></a>Angive eller redigere indstillinger for programbeskyttelse til Windows 10 enheder

Denne artikel gælder for Microsoft 365 Business Premium.

> [!NOTE]
> Microsoft Defender for Business udrulles til Microsoft 365 Business Premium fra 1. marts 2022. Dette tilbud indeholder yderligere sikkerhedsfunktioner til enheder. [Få mere at vide om Defender for Business](../../security/defender-business/mdb-overview.md).

## <a name="edit-an-app-management-policy-for-windows-10"></a>Rediger en politik for appadministration for Windows 10

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.     
2. I venstre navigationslinje skal du **vælge Enheders** \> **politikker** .
1. Vælg en eksisterende Windows apppolitik, og vælg derefter **Rediger**.
1. Vælg **Rediger** ud for en indstilling, du vil ændre, og klik derefter **på Gem**.

## <a name="create-an-app-management-policy-for-windows-10"></a>Opret en politik for appadministration for Windows 10

Hvis brugerne har personlige Windows 10, hvor de udfører arbejdsopgaver, kan du også beskytte dine data på disse enheder.
  
1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 
2. I venstre navigationslinje skal du vælge **Tilføjelse af** \> **enheder-politikker**\>.
3. Angiv et **entydigt** navn for denne politik i ruden Tilføj politik. 
4. Under **Politiktype** skal du **vælge Programadministration for Windows 10**.
5. Under **Enhedstype skal** du vælge enten **Personlig** eller **Firmaejet**.
6. **Kryptér arbejdsfiler** slås automatisk til. 
7. Angiv Forebyd, at brugere kopierer virksomhedsdata til personlige filer, og tving dem til at gemme arbejdsfiler på **OneDrive for Business** **til Til**, hvis du ikke ønsker, at brugerne skal gemme arbejdsfiler på deres pc. 
9. **Udvid Gendan data Windows enheder**. Vi anbefaler, at du slår den **Til**.
    Før du kan gå til placeringen for certifikatet for Genoprettelsesagent til datagendannelse, skal du først oprette et. Du kan finde en vejledning [i Oprette og bekræfte et certifikat til Encrypting File System (EFS) og Agent til genoprettelse af data (DRA](/windows/security/information-protection/windows-information-protection/create-and-verify-an-efs-dra-certificate)).
    
    Arbejdsfiler krypteres som standard ved hjælp af en hemmelig nøgle, der er gemt på enheden og knyttet til brugerens profil. Kun brugeren kan åbne og dekryptere filen. Men hvis en enhed går tabt, eller en bruger fjernes, kan en fil sidde fast i en krypteret tilstand. En administrator kan bruge DRA-certifikatet (Data Recovery Agent) til at dekryptere filen.
    
    ![Gå til Certifikatet for Genoprettelsesagent til datagendannelse.](../../media/7d7d664f-b72f-4293-a3e7-d0fa7371366c.png)
  
10. **Udvid Beskyt yderligere** netværk og skyplaceringer, hvis du vil tilføje flere domæner eller SharePoint Online-placeringer for at sikre, at filer i alle de viste apps er beskyttet. Hvis du skal angive mere end ét element for et felt, skal du bruge et semikolon (;) mellem elementerne.
    
    ![Udvid Beskyt yderligere netværk og skyplaceringer, og angiv domæner eller SharePoint Online-websteder, du ejer.](../../media/7afaa0c7-ba53-456d-8c61-312c45e09625.png)
  
11. Beslut **derefter Who får disse indstillinger?** Hvis du ikke vil bruge standardsikkerhedsgruppen Alle  brugere, skal du vælge **Rediger og vælge** de sikkerhedsgrupper, der får disse indstillinger \> **Vælg**.
12. Til sidst skal **du** vælge Tilføj for at gemme politikken og tildele den til enheder.

## <a name="see-also"></a>Se også

[De 10 mest populære måder at sikre Microsoft 365 planer til virksomheder på](../security-and-compliance/secure-your-business-data.md)