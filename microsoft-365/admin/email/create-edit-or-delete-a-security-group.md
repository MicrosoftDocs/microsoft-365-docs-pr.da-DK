---
title: Opret, rediger eller slet en sikkerhedsgruppe i Microsoft 365 Administration
f1.keywords:
- NOCSH
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
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 55c96b32-e086-4c9e-948b-a018b44510cb
description: Lær at oprette, redigere eller slette en sikkerhedsgruppe.
ms.openlocfilehash: 3f054842abc5111c654b8da02afc418c36f7db11
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/13/2021
ms.locfileid: "63588108"
---
# <a name="create-edit-or-delete-a-security-group-in-the-microsoft-365-admin-center"></a>Opret, rediger eller slet en sikkerhedsgruppe i Microsoft 365 Administration

På Microsoft 365 **Grupper** kan du oprette grupper af brugerkonti, som du kan bruge til at tildele de samme tilladelser til i SharePoint Online og CRM Online. Eksempelvis kan en administrator oprette en sikkerhedsgruppe for at give en bestemt gruppe personer adgang til en SharePoint websted. Kun globale administratorer og brugeradministratorer har tilladelse til at oprette, redigere eller slette sikkerhedsgrupper. Du kan finde flere oplysninger om administratorroller [i Tildel administratorroller](../add-users/assign-admin-roles.md). 
  
Der er også grupper i [Exchange Online og SharePoint Online](#groups-in-exchange-online-and-sharepoint-online), som du kan bruge til at sende mails eller tildele tilladelser til en gruppe af brugere og grupper i [Exchange Online og SharePoint Online](#groups-in-exchange-online-and-sharepoint-online), der giver brugere rettigheder og adgang til websteder og grupper af websteder. 
  
> [!IMPORTANT]
>  Planlægger du at bruge webstedspostkasser? Alle de brugere, der føjes SharePoint et websted via en sikkerhedsgruppe i stedet for at blive tilføjet enkeltvis, kan kun bruge webstedspostkassen SharePoint. Disse brugere kan ikke få adgang til webstedspostkassen fra Outlook. Du kan få mere at vide [under Brug Microsoft 365 grupper i stedet for webstedspostkasser](https://support.microsoft.com/office/737d6b1f-67cc-41fe-8db8-f2d09dd1673b). 
  
## <a name="manage-security-groups-in-the-admin-center"></a>Administrere sikkerhedsgrupper i Administration

### <a name="add-a-security-group"></a>Tilføj en sikkerhedsgruppe

1. I Microsoft 365 Administration du gå til **siden** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">GrupperGrupper</a>.
  
2. På siden **Grupper** skal du vælge **Tilføj en gruppe**.
    
3. På siden **Vælg en gruppetype** skal du vælge **Sikkerhed**. 
    
4. Følg trinnene for at fuldføre oprettelsen af gruppen. 
 
### <a name="add-members-to-a-security-group"></a>Føj medlemmer til en sikkerhedsgruppe
    
1. Vælg navnet på sikkerhedsgruppen på **siden** Grupper, og vælg Vis **alle og** administrer medlemmer **under fanen Medlemmer**. 
    
2. I grupperuden skal du vælge  Tilføj medlemmer og vælge personen på listen eller skrive navnet på den person, du vil tilføje, i feltet Søg og  derefter vælge **Gem**.
    
    Hvis du vil fjerne medlemmer, skal du vælge X ud for deres navn. 
  
### <a name="edit-a-security-group"></a>Redigere en sikkerhedsgruppe

1. I Administration skal du gå til **siden Grupper**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank"></a>
  
2. Vælg **gruppens** navn på siden Grupper. 
    
3. I ruden med indstillinger skal du **vælge fanen** Generelt eller **fanen Medlemmer** for at redigere enten gruppedetaljer eller medlemmer.

### <a name="delete-a-security-group"></a>Slette en sikkerhedsgruppe

1. I Administration skal du gå til **siden** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">GrupperGrupper</a>.
    
2. Vælg **gruppens** navn på siden Grupper. 
    
3. Vælg **Slet gruppe** (wasetbin-ikon), og bekræft derefter ved at vælge **Slet**.
    
    Vælg **Luk** , når gruppen er slettet. 
    
## <a name="groups-in-exchange-online-and-sharepoint-online"></a>Grupper i Exchange Online og SharePoint Online

Hvis du vil oprette grupper af brugere, så du kan sende mails til dem alle på samme tid, kan du gøre det i Exchange  \> Administration ved at gå til **Administrator Exchange** \> **Modtagergrupper**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a> Vælg derefter **NewAdd**![,](../../media/328ffb57-5f31-430a-b653-4a6b8e76d338.png) og vælg den type gruppe, du vil oprette: 
  
- **Distributionsgruppe**: Bruges til at distribuere meddelelser til en gruppe af brugere. Det kaldes også en  *mailaktiveret distributionsgruppe* eller en  *distributionsliste*. Du kan få mere at vide [under Administrere distributionsgrupper](/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups).
    
- **Sikkerhedsgruppe**: Kan bruges til at distribuere meddelelser til en gruppe af brugere eller til at give adgangstilladelser til ressourcer. Denne gruppe kaldes også for en *mailaktiveret sikkerhedsgruppe*. Du kan finde flere oplysninger [under Administrere mailaktiverede sikkerhedsgrupper](/Exchange/recipients/mail-enabled-security-groups).
    
- **Dynamisk distributionsgruppe**: En distributionsgruppetype, hvor listen over modtagere genberegnes, hver gang du sender en meddelelse, ud fra filtre og betingelser, du definerer. Du kan finde flere oplysninger i [Administrere dynamiske distributionsgrupper](/Exchange/recipients/dynamic-distribution-groups/dynamic-distribution-groups).
    
Når du har oprettet distributionsgrupper og mailaktiverede sikkerhedsgrupper <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">i Exchange Administration</a>, vises deres navne og brugerlister på **siden Sikkerhedsgrupper**. Du kan slette disse grupper på begge placeringer, men du kan kun redigere dem i Exchange Administration. Dynamiske distributionsgrupper vises ikke på siden **Sikkerhedsgrupper** . 
  
 SharePoint oprettes automatisk, når du opretter en gruppe af websteder. Standardgrupperne bruger standardtilladelsesniveauerne i SharePoint , også kaldet "SharePoint roller", til at tildele brugerne rettigheder og adgang. Du kan finde flere oplysninger [i SharePoint standardgrupper i SharePoint Online](/sharepoint/default-sharepoint-groups).
  
## <a name="how-is-a-security-group-different-from-security-groups-i-create-in-sharepoint"></a>Hvordan er en sikkerhedsgruppe forskellig fra sikkerhedsgrupper, jeg opretter i SharePoint?

Sikkerhedsgrupper kan bruges sammen med SharePoint, Exchange, MDM, Windows m.m. En sikkerhedsgruppe, du opretter i SharePoint, genkendes kun af den pågældende SharePoint gruppe af websteder.
  
## <a name="do-i-have-to-use-security-groups-for-my-organization-to-be-secure"></a>Skal jeg bruge sikkerhedsgrupper, for at min organisation er sikker?

Nej. Dette er blot én af flere måder at administrere sikkerhed for din organisation på. Du kan altid give brugertilladelser og adgang til websteder enkeltvis. Men med sikkerhedsgrupper kan du nemt administrere større grupper af brugere.
  
## <a name="can-i-send-email-to-a-security-group"></a>Kan jeg sende mails til en sikkerhedsgruppe?

Ja. Men hvis du vil bruge grupper til mail og samarbejde, anbefaler vi, at [du opretter en Microsoft 365 gruppe i](../create-groups/create-groups.md) stedet. 

## <a name="related-content"></a>Relateret indhold

[Opret en gruppe i Microsoft 365 Administration](../create-groups/create-groups.md) (artikel)\
[Forklaring Microsoft 365 grupper til dine brugere](../create-groups/explain-groups-knowledge-worker.md) (artikel)\
[Administrere en gruppe i Microsoft 365 Administration](../create-groups/manage-groups.md) (artikel)