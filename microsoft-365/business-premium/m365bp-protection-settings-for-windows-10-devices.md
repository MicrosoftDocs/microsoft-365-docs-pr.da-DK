---
title: Rediger eller angiv indstillinger for programbeskyttelse for Windows-enheder
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
f1.keywords:
- Win10AppPolicy
- O365E_Win10AppPolicy
- BCS365_Win10AppPolicy
ms.service: o365-administration
ms.localizationpriority: high
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
description: Få mere at vide om, hvordan du opretter eller redigerer politikker for appadministration og beskytter arbejdsfiler på dine brugeres personlige Windows-enheder.
ms.openlocfilehash: 9e9c98af4279b3e7370959375fc4872f21b73f55
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 06/29/2022
ms.locfileid: "66858862"
---
# <a name="set-or-edit-application-protection-settings-for-windows-devices"></a>Angiv eller rediger indstillinger for programbeskyttelse for Windows-enheder

Nu skal du konfigurere politikker for programbeskyttelse for din organisations Windows-enheder for at sikre, at alle dine brugere er beskyttet, når de bruger programmer til deres arbejde.

## <a name="edit-an-app-management-policy-for-windows-devices"></a>Rediger en politik for appadministration for Windows-enheder

1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.     

2. Vælg **Enhedspolitikker** \> i venstre navigationsrude.

3. Vælg en eksisterende Windows-apppolitik, og vælg derefter **Rediger**.

4. Vælg **Rediger** ud for en indstilling, du vil ændre, og vælg derefter **Gem**.

## <a name="create-an-app-management-policy-for-windows-devices"></a>Opret en politik for appadministration for Windows-enheder

Hvis brugerne har personlige Windows-enheder, som de udfører arbejdsopgaver på, kan du beskytte dine data på disse enheder.
  
1. Gå til Administration på <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>. 

2. Vælg **Enheder** \> **Politikker** \> Tilføj i venstre navigationsrude.

3. Angiv et entydigt navn til denne politik i ruden **Tilføj politik** . 

4. Under **Politiktype** skal du vælge **Programadministration for Windows 10**.

5. Under **Enhedstype** skal du vælge enten **Personlig** eller **Firmaejet**.

6. **Kryptér arbejdsfiler** aktiveres automatisk. 

7. Angiv **Forbyd brugere at kopiere virksomhedsdata til personlige filer, og tving dem til at gemme arbejdsfiler til OneDrive for Business** til **Til**, hvis du ikke ønsker, at brugerne skal gemme arbejdsfiler på deres pc. 

8. Udvid **Gendan data på Windows-enheder**. Vi anbefaler, at du slår den **til**.
    Før du kan gå til placeringen af certifikatet som datagendannelsesagent, skal du først oprette et. Du kan finde instruktioner under [Opret og bekræft et DRA-certifikat (Encrypting File System) (EFS).](/windows/security/information-protection/windows-information-protection/create-and-verify-an-efs-dra-certificate)

    Arbejdsfiler krypteres som standard ved hjælp af en hemmelig nøgle, der er gemt på enheden og knyttet til brugerens profil. Det er kun brugeren, der kan åbne og dekryptere filen. Men hvis en enhed går tabt, eller en bruger fjernes, kan en fil sidde fast i krypteret tilstand. En administrator kan bruge DRA-certifikatet (Data Recovery Agent) til at dekryptere filen.

    ![Gå til certifikat for datagendannelsesagent.](./../media/7d7d664f-b72f-4293-a3e7-d0fa7371366c.png)
  
9. Udvid **Beskyt yderligere netværks- og skyplaceringer** , hvis du vil tilføje flere domæner eller SharePoint Online-placeringer for at sikre, at filer i alle de viste apps er beskyttet. Hvis du har brug for at angive mere end ét element til et af felterne, skal du bruge et semikolon (;) mellem elementerne.

    ![Udvid Beskyt yderligere netværks- og cloudplaceringer, og angiv domæner eller SharePoint Online-websteder, du ejer.](./../media/7afaa0c7-ba53-456d-8c61-312c45e09625.png)
  
10. Beslut derefter **, hvem der får disse indstillinger?** Hvis du ikke vil bruge standardsikkerhedsgruppen **Alle brugere** , skal du vælge **Skift** og vælge de sikkerhedsgrupper, der skal have disse indstillinger \> **Vælg**.
11. Til sidst skal du vælge **Tilføj** for at gemme politikken og tildele den til enheder.

## <a name="see-also"></a>Se også

[Bedste praksis for sikring af Microsoft 365 til virksomheder-planer](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>Næste mål

[Valider dine Windows-indstillinger](m365bp-validate-settings-on-windows-10-pcs.md).