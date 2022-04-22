---
title: Konfigurer indstillingerne Standard eller Målrettet udgivelse
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
description: Få mere at vide om, hvordan du konfigurerer udgivelsesindstillingen for nye produkt- og funktionsopdateringer i Microsoft 365 Administration.
ms.openlocfilehash: 67c6fe3f08549424c725589a50c647a876c151af
ms.sourcegitcommit: 339d2c2ffea06726f69429f73c1113c649f37b18
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/21/2022
ms.locfileid: "65022443"
---
# <a name="set-up-the-standard-or-targeted-release-options"></a>Konfigurer indstillingerne Standard eller Målrettet udgivelse

> [!IMPORTANT]
> De Microsoft 365 opdateringer, der er beskrevet i denne artikel, gælder for Microsoft 365, SharePoint Online og Exchange Online. Disse udgivelsesindstillinger er målrettede, bedste måder at udgive ændringer på Microsoft 365 men kan ikke garanteres til enhver tid eller for alle opdateringer. De gælder ikke for Microsoft 365 Apps, Skype for Business, Microsoft Teams og relaterede tjenester. Du kan få oplysninger om udgivelsesmuligheder for Microsoft 365 Apps under [Oversigt over opdateringskanaler til Microsoft 365 Apps](/deployoffice/overview-update-channels).

Med Microsoft 365 modtager du nye produktopdateringer og funktioner, efterhånden som de bliver tilgængelige i stedet for at foretage dyre opdateringer hvert andet år. Du kan administrere, hvordan din organisation modtager disse opdateringer. Du kan f.eks. tilmelde dig en tidlig version, så din organisation modtager opdateringer først. Du kan angive, at det kun er bestemte personer, der modtager opdateringerne. Eller du kan forblive i standardversionsplanen og modtage opdateringerne senere. I denne artikel forklares de forskellige udgivelsesmuligheder, og hvordan du kan bruge dem til din organisation.

## <a name="how-it-works---release-validation"></a>Sådan fungerer det – udgivelsesvalidering

Alle nye versioner testes først og valideres af funktionsteamet og derefter af hele Microsoft 365 funktionsteamet efterfulgt af hele Microsoft. Efter intern test og validering er det næste trin en **målrettet udgivelse** (tidligere kaldet Første udgivelse) til kunder, der tilmelder sig. Ved hver udgivelsesring indsamler Microsoft feedback og validerer kvaliteten yderligere ved at overvåge vigtige forbrugsdata. Denne serie af progressiv validering er på plads for at sikre, at den verdensomspændende udgivelse er så robust som muligt. Udgivelserne er afbilledet i følgende figur. 
  
![Frigiv valideringsringe for Microsoft 365.](../../media/73611ed3-2d8c-4e7b-8074-9f03b239f9ed.png)
  
I forbindelse med vigtige opdateringer får kunderne i første omgang besked af [Microsoft 365 Roadmap](https://products.office.com/business/office-365-roadmap). Efterhånden som en opdatering kommer tættere på udrulningen, kommunikeres den via dit [Microsoft 365 Meddelelsescenter](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter).

> [!NOTE]
> Du skal bruge en Microsoft 365- eller Azure AD-konto for at få adgang til dit Meddelelsescenter via [Administration](/office365/admin/admin-overview/about-the-admin-center). Microsoft 365 brugere af startplanen har ikke et administrationscenter.

## <a name="standard-release"></a>Standardversion

Dette er standardindstillingen, hvor du og dine brugere modtager de nyeste opdateringer, når de udgives bredt til alle kunder.
  
En god praksis er at lade størstedelen af brugerne i **Standard-versionen** og it-teknikere og superbrugere i **Målrettet udgivelse** evaluere nye funktioner og forberede teams til at understøtte virksomhedsbrugere og direktører. 
  
> [!NOTE]
> Hvis du skifter fra målrettet version tilbage til standardversionsspor, kan dine brugere miste adgangen til funktioner, der endnu ikke har nået standardversionen. 
  
## <a name="targeted-release"></a>Målrettet udgivelse

Med denne indstilling kan du og dine brugere være de første til at se de nyeste opdateringer og hjælpe med at forme produktet ved at give tidlig feedback. Du kan vælge at få enkeltpersoner eller hele organisationen til at modtage opdateringer tidligt.
  
> [!IMPORTANT]
> - Store eller komplekse opdateringer kan tage længere tid end andre, så ingen brugere påvirkes negativt. Der er ingen garanti på den nøjagtige tidslinje for en udgivelse.
> - Målrettet udgivelse er i øjeblikket ikke tilgængelig for kunder med enten Office 365 GCC-planen eller Office 365 GCC High- og DoD-planen.
  
### <a name="targeted-release-for-entire-organization"></a>Målrettet udgivelse for hele organisationen

Hvis du [konfigurerer udgivelsesindstillingen i Administration](#set-up-the-release-option-in-the-admin-center) for denne indstilling, får alle dine brugere oplevelsen Målrettet udgivelse. For organisationer med mere end 300 brugere anbefaler vi, at du bruger et testabonnement til denne indstilling. Kontakt din Microsoft-kontakt for at få oplysninger om testabonnementer. 
  
### <a name="targeted-release-for-selected-users"></a>Målrettet udgivelse til udvalgte brugere

Hvis du [konfigurerer udgivelsesindstillingen i Administration](#set-up-the-release-option-in-the-admin-center) for denne indstilling, kan du definere bestemte brugere, normalt superbrugere, for at modtage tidlig adgang til funktioner og funktionalitet.

> [!IMPORTANT]
> Nogle funktioner udrulles kun pr. organisation. Det betyder, at hele organisationen får adgang til funktionen på samme tid. For funktioner som denne er det ikke muligt for udvalgte brugere i det målrettede udgivelsesprogram at få funktionen tidligt. Det betyder, at din organisation ikke kan modtage disse funktioner tidligt, hvis du har konfigureret udvalgte brugere i målrettet version. Hvis du vil sikre dig, at du kan se alle funktioner i målrettet version, skal du konfigurere målrettet udgivelse for hele organisationen eller konfigurere en testorganisation.
  
## <a name="benefits-of-targeted-release"></a>Fordele ved målrettet udgivelse

Målrettet udgivelse gør det muligt for administratorer, ændringsadministratorer eller andre, der er ansvarlige for Microsoft 365 opdateringer, at forberede sig på de kommende ændringer ved at lade dem:
  
- Test og valider nye opdateringer, før de udgives til alle brugerne i organisationen.
    
- Forbered brugermeddelelser og dokumentation, før der udgives opdateringer over hele verden.
    
- Forbered intern helpdesk til kommende ændringer.
    
- Gennemgå gennemgange af overholdelse af angivne standarder og sikkerhed.
    
- Brug funktionskontrolelementer, hvor det er relevant, til at styre udgivelsen af opdateringer til slutbrugere.
    
## <a name="set-up-the-release-option-in-the-admin-center"></a>Konfigurer udgivelsesindstillingen i Administration

Du kan ændre, hvordan din organisation modtager Microsoft 365 opdateringer, ved at følge disse trin. Du skal være global administrator i Microsoft 365 for at tilmelde dig.
  
> [!IMPORTANT]
> Det kan tage op til 24 timer, før nedenstående ændringer træder i kraft i Microsoft 365. Hvis du fravælger målrettet udgivelse, når du har aktiveret den, kan dine brugere miste adgangen til funktioner, der endnu ikke har nået den planlagte version. 
  
1. I Administration skal du gå til **indstillingen Indstillinger** >  **Ellerg** og under <a href="https://go.microsoft.com/fwlink/p/?linkid=2067339" target="_blank">fanen **Organisationsprofil**</a> vælge **Udgivelsesindstillinger**.

5. Hvis du vil deaktivere målrettet udgivelse, skal du vælge **Standardversion** og derefter vælge **Gem ændringer**. 
    
6. Hvis du vil aktivere målrettet udgivelse for alle brugere i din organisation, skal du vælge **Målrettet udgivelse for alle** og derefter vælge **Gem ændringer**. 
    
7. Hvis du vil aktivere målrettet udgivelse for nogle personer i din organisation, skal du vælge **Målrettet udgivelse for valgte brugere** og derefter vælge **Gem ændringer**. 
    
8. Vælg **Vælg brugere** for at tilføje brugere én ad gangen, eller **Upload brugere** for at tilføje dem samlet.
    
9. Når du er færdig med at tilføje brugere, skal du vælge **Gem ændringer**.
  
## <a name="next-steps"></a>Næste trin

Se, hvordan du [administrerer meddelelser](/office365/admin/manage/message-center) i [dit Microsoft 365 Meddelelsescenter](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/MessageCenter) for at få meddelelser om kommende Microsoft 365 opdateringer og udgivelser.

## <a name="related-content"></a>Relateret indhold

[Deltag i Office Insider Program](https://insider.office.com/join/windows) (artikel)
