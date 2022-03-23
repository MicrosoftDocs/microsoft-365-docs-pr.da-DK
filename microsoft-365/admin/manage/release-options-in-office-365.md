---
title: Konfigurer Standard eller Målrettede udgivelsesindstillinger
f1.keywords:
- CSH
ms.author: kwekua
author: kwekua
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
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- BEA160
- GEA150
ms.assetid: 3b3adfa4-1777-4ff0-b606-fb8732101f47
description: Få mere at vide om, hvordan du konfigurerer udgivelsesindstillingen for nye produkter og funktioner i Microsoft 365 Administration.
ms.openlocfilehash: 6e3cf1987d6b3c22ed1414bd8e352da7acf49e60
ms.sourcegitcommit: e246725b0935067aad886530d5178972c0f895d7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/10/2021
ms.locfileid: "63589338"
---
# <a name="set-up-the-standard-or-targeted-release-options"></a>Konfigurer Standard eller Målrettede udgivelsesindstillinger

> [!IMPORTANT]
> De Microsoft 365 opdateringer, der er beskrevet i denne artikel, gælder for Microsoft 365, SharePoint Online og Exchange Online. Disse udgivelsesindstillinger er målrettede og gør den bedste indsats for at udgive ændringer Microsoft 365 men dette kan ikke altid garanteres eller garanteres for alle opdateringer. De gælder ikke for Microsoft 365 Apps, Skype for Business, Microsoft Teams og relaterede tjenester. Du kan finde oplysninger om udgivelsesindstillinger Microsoft 365 Apps i [Oversigt over opdateringskanaler for Microsoft 365 Apps](/deployoffice/overview-update-channels).

Med Microsoft 365 får du nye produktopdateringer og -funktioner, efterhånden som de bliver tilgængelige, i stedet for dyrere opdateringer hvert år. Du kan styre, hvordan din organisation modtager disse opdateringer. Du kan f.eks. tilmelde dig en tidlig version, så din organisation modtager opdateringer først. Du kan angive, at det kun er visse personer, der modtager opdateringerne. Eller du kan forblive på standard udgivelsesplanen og modtage opdateringerne senere. I denne artikel forklares de forskellige udgivelsesindstillinger, og hvordan du kan bruge dem til din organisation.

## <a name="how-it-works---release-validation"></a>Sådan fungerer det – udgivelsesvalidering

En ny version testes først og valideres af funktionsteamet og derefter af hele Microsoft 365, efterfulgt af hele Microsoft. Efter intern test og validering er det næste trin en Målrettet udgivelsesversion **(tidligere** kaldet First release) til kunder, der har tilvalgt den. Ved hver udgivelsesring indsamler Microsoft feedback og validerer kvaliteten yderligere ved at overvåge vigtige målepunkter for brug. Denne serie af gradvis validering er på plads for at sikre, at den globale udgivelsesversion er så robust som muligt. Udgivelsesudgivelserne er afbilledet i følgende figur. 
  
![Valideringsringe for udgivelse for Microsoft 365.](../../media/73611ed3-2d8c-4e7b-8074-9f03b239f9ed.png)
  
Ved væsentlige opdateringer underrettes kunderne indledningsvist i [Microsoft 365 Roadmap](https://products.office.com/business/office-365-roadmap). Når en opdatering nærmer sig udrulning, kommunikeres det via [Microsoft 365 Meddelelsescenter](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter).

> [!NOTE]
> Du skal bruge en Microsoft 365 eller Azure AD-konto for at få adgang til meddelelsescenteret [via Administration](/office365/admin/admin-overview/about-the-admin-center). Microsoft 365 home plan-brugere har ikke Administration.


## <a name="standard-release"></a>Standardudgivelsesversion

Dette er standardindstillingen, hvor du og dine brugere modtager de seneste opdateringer, når de frigives til alle kunder.
  
En god fremgangsmåde er at lade størstedelen af brugerne blive i **Standardversionen** og give it-fagfolk og  superbrugere adgang til en målrettet udgivelsesversion for at evaluere nye funktioner og forberede teams til at understøtte forretningsbrugere og ledere. 
  
> [!NOTE]
> Hvis du skifter fra den målrettede udgivelsesversion tilbage til standardversionsversionen, kan dine brugere miste adgang til funktioner, der endnu ikke er udgivet i standardversionen. 
  
## <a name="targeted-release"></a>Målrettet udgivelsesversion

Med denne indstilling kan du og dine brugere være de første til at se de nyeste opdateringer og hjælpe med at forme produktet ved at give tidlig feedback. Du kan vælge at få enkeltpersoner eller hele organisationen til at modtage opdateringerne tidligt.
  
> [!IMPORTANT]
> - Det kan tage længere tid med store eller komplekse opdateringer, så ingen brugere påvirkes negativt. Der er ingen garanti for den nøjagtige tidslinje for en udgivelse.
> - Målrettet udgivelsesversion er i øjeblikket ikke tilgængelig for kunder med enten Office 365 GCC-planen eller den Office 365 GCC High and DoD-plan.
  
### <a name="targeted-release-for-entire-organization"></a>Målrettet udgivelsesversion for hele organisationen

Hvis du [konfigurerer udgivelsesindstillingen i Administration](#set-up-the-release-option-in-the-admin-center) til denne indstilling, får alle dine brugere oplevelsen af den målrettede udgivelsesversion. Til organisationer med mere end 300 brugere anbefaler vi, at du bruger et testabonnement til denne indstilling. Kontakt din Microsoft-kontakt for at få flere oplysninger om testabonnementet. 
  
### <a name="targeted-release-for-selected-users"></a>Målrettet udgivelsesversion for udvalgte brugere

Hvis du [konfigurerer udgivelsesindstillingen](#set-up-the-release-option-in-the-admin-center) i Administration til denne indstilling, kan du definere bestemte brugere, som regel superbrugere, til at få tidlig adgang til funktioner og funktionalitet. 
  
## <a name="benefits-of-targeted-release"></a>Fordele ved den målrettede udgivelsesversion

Den målrettede udgivelsesversion giver administratorer, ændringsledere eller andre ansvarlige for at Microsoft 365 opdateringer til at forberede sig på de kommende ændringer ved at lade dem:
  
- Test og valider nye opdateringer, før de frigives til alle brugere i organisationen.
    
- Forbered brugerbeskeder og dokumentation, før opdateringerne frigives i hele verden.
    
- Forberede intern helpdesk til kommende ændringer.
    
- Gennemgå overholdelse af regler og standarder og sikkerhedsvurderinger.
    
- Brug funktionskontrolelementer til at styre frigivelsen af opdateringer til slutbrugere, hvor det er relevant.
    
## <a name="set-up-the-release-option-in-the-admin-center"></a>Konfigurer udgivelsesindstillingen i Administration

Du kan ændre, hvordan din organisation modtager Microsoft 365 opdateringer ved at følge disse trin. Du skal være global administrator i Microsoft 365 at tilmelde dig.
  
> [!IMPORTANT]
> Det kan tage op til 24 timer, før ændringerne nedenfor træder i kraft Microsoft 365. Hvis du fravælger den målrettede udgivelsesversion, efter du har aktiveret den, kan dine brugere miste adgang til funktioner, der endnu ikke er frigivet. 
  
1. I Administration skal du gå til **indstillingen Indstillinger** >  **Ellerg** og under fanen <a href="https://go.microsoft.com/fwlink/p/?linkid=2067339" target="_blank">**Organisationsprofil** vælge</a> **Udgivelsesindstillinger**.

5. Hvis du vil deaktivere den målrettede udgivelsesversion, **skal du vælge Standardversion** og **derefter vælge Gem ændringer**. 
    
6. Hvis du vil aktivere den målrettede udgivelsesversion for alle brugere i organisationen, skal du **vælge Målrettet udgivelsesversion for alle** og derefter **vælge Gem ændringer**. 
    
7. Hvis du vil aktivere den målrettede udgivelsesversion for nogle personer i organisationen, skal **du vælge Målrettet udgivelsesversion for udvalgte** brugere og derefter **vælge Gem ændringer**. 
    
8. Vælg **Vælg brugere** for at tilføje brugere én ad gangen, eller vælg Upload **at** tilføje dem flere ad gangen.
    
9. Når du er færdig med at tilføje brugere, skal du **vælge Gem ændringer**.
  
## <a name="next-steps"></a>Næste trin

Find ud af[, hvordan du](/office365/admin/manage/message-center) administrerer [meddelelser Microsoft 365 Meddelelsescenter](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter) for at få meddelelser om kommende Microsoft 365 opdateringer og udgivelser.

## <a name="related-content"></a>Relateret indhold

[Deltag i Office Insider Program](https://insider.office.com/join/windows) (artikel)
