---
title: Administrer tilføjelser i Administration
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
- Adm_NonTOC
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Få mere at vide om brugen af Centraliseret tilføjelses-ins til at installere tilføjelser til brugere og grupper i organisationen.
ms.openlocfilehash: d2d1c4d36bf37ad82ac5c720931146c0dfb2220d
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 01/12/2022
ms.locfileid: "63599885"
---
# <a name="manage-add-ins-in-the-admin-center"></a>Administrer tilføjelser i Administration

Office tilføjelsesprogrammet hjælper dig med at tilpasse dine dokumenter og strømline den måde, hvorpå du får adgang til oplysninger på internettet. Se [Begynd at bruge Office-tilføjelsesprogrammet](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 

Når en administrator installerer tilføjelsesprogrammet for brugere i en organisation, kan administratoren slå tilføjelsesprogrammet til eller fra, redigere, slette og administrere adgang til tilføjelses ins.

Du kan finde flere oplysninger om installation af tilføjelser fra Administration i [Installér tilføjelser i Administration](./manage-deployment-of-add-ins.md).
  
## <a name="add-in-states"></a>Tilføjelsesprogrammets tilstande

Et tilføjelsesprogrammet kan være i **tilstanden Til** **eller** Fra.
  
| Stat | Sådan opstår tilstanden | Virkning |
|:-----|:-----|:-----|
|**Aktiv**  <br/> |Administratoren har uploadet tilføjelsesprogrammet og tildelt det til brugere eller grupper.  <br/> |Brugere og grupper, der er tildelt til tilføjelsesprogrammet, kan se det i de relevante klienter.  <br/> |
|**Deaktiveret**  <br/> |Administratoren har deaktiveret tilføjelsesprogrammet.  <br/> |Brugere og grupper, der er tildelt til tilføjelsesprogrammet, har ikke længere adgang til det.  <br/> Hvis tilføjelsesprogrammets tilstand ændres til Aktiv, har brugere og grupper adgang til det igen.  <br/> |
|**Slettet**  <br/> |Administratoren har slettet tilføjelsesprogrammet.  <br/> |Brugere og grupper, der er tildelt tilføjelsesprogrammet, har ikke længere adgang til det.  <br/> |
   
Overvej at slette et tilføjelsesprogrammet, hvis der ikke længere er nogen, der bruger det. Det kan f.eks. være en god ide at deaktivere et tilføjelsesprogrammet, hvis det kun bruges på bestemte tidspunkter af året.

## <a name="delete-an-add-in"></a>Slette et tilføjelsesprogrammet

Du kan også slette et tilføjelsesprogrammet, der blev installeret.

1. I Administration skal du gå til siden **Indstillinger** >  **Integrerede apps**.

2. Vælg det installerede tilføjelsesprogrammet, og vælg derefter **fanen** Konfiguration.

3. I **ruden** Konfiguration skal du **gå til Avanceret** >  Indstillinger **Add-ins**.

4. Vælg tilføjelsesprogrammet på listen igen.

5. Vælg **Fjern tilføjelsesprogrammet**. Fjern knappen Tilføjelsesprogrammet i nederste højre hjørne.

6. Valider dine valg, og vælg **Fjern**.

## <a name="edit-add-in-access"></a>Rediger adgang til tilføjelsesprogrammet

Efter udrulningen kan administratorer også administrere brugeradgang til tilføjelsesprogrammet.

1. I Administration skal du gå til siden **Indstillinger** >  **Integrerede apps**.

2. Vælg det installerede tilføjelsesprogrammet.

3. Klik på **Rediger** under **Who har Access**.

4. Gem ændringerne.

## <a name="prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook"></a>Undgå downloads af tilføjelsesprogrammet ved at deaktivere tilføjelsesprogrammets Office Store på tværs af alle klienter (undtagen Outlook)

> [!NOTE]
> Outlook installation af tilføjelsesprogrammet administreres af en [anden proces](/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins).

Som organisation kan det være en fordel at forhindre download af Office tilføjelsesprogrammet fra Office Store. Dette kan bruges sammen med Centraliseret udrulning for at sikre, at kun organisationsgodkendte tilføjelser udrulles til brugere i organisationen.
  
**Sådan deaktiverer du anskaffelse af tilføjelsesprogrammet**
  
1. I Administration skal du gå til siden **Indstillinger** \> [Org-indstillinger](https://go.microsoft.com/fwlink/p/?linkid=2053743).

2. Vælg **Brugerejede apps og tjenester**.
    
3. Fjern markeringen af indstillingen for at give brugere adgang til Office butik.

    Dette forhindrer alle brugere i at anskaffe følgende tilføjelser fra Store.
      
    - Tilføjelser til Word, Excel og PowerPoint 2016 fra:
        
      - Windows
      - Mac
      - Office
        
        
    - Anskaffelser, der starter **i AppSource**
        
    - Tilføjelser i Microsoft 365
        
    En bruger, der forsøger at få adgang til store, får vist følgende meddelelse: Beklager, Microsoft 365 er konfigureret til at forhindre individuel anskaffelse **af Office Store tilføjelsesprogrammet.**
  
Support til at deaktivere Office Store fås i følgende versioner:
  
- Windows: 16.0.9001 – tilgængelig i øjeblikket.
    
- Mac: 16.10.18011401 – tilgængelig i øjeblikket.
    
- iOS: 2.9.18010804 – tilgængelig i øjeblikket.
    
- Internettet – tilgængelig i øjeblikket.
    
Dette forhindrer ikke en administrator i at bruge Centraliseret udrulning til at tildele et tilføjelse Office Store.

> [!NOTE] 
> Tilføjelser som f.eks. Visio Data visualizer, Bing Kort og Personer Graph vises stadig på båndet, også selvom en administrator har deaktiveret Store. For at fjerne disse links skal administratorer deaktivere Store til Gruppepolitik-objekt.
  
Hvis du vil forhindre en bruger i at logge på med en Microsoft-konto, kan du begrænse logon til kun at bruge organisationskontoen. Du kan få mere at [vide under Identitet, godkendelse og godkendelse Office 2016](/DeployOffice/security/identity-authentication-and-authorization-in-office).  

> [!NOTE] 
> Hvis du forhindrer brugere i at få adgang til Office Store, vil det også forhindre dem i at [indsætte tilføjelsesprogrammet Office til test fra en netværksshare](/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins).

## <a name="more-about-the-end-user-experience-with-add-ins"></a>Mere om slutbrugeroplevelsen med tilføjelsesprogrammet

Når du har implementeret et tilføjelsesprogrammer, kan slutbrugerne begynde at bruge det i deres Office programmer. Tilføjelsesprogrammet vises på alle platforme, der understøtter tilføjelsesprogrammet. Se [Begynd at bruge Office-tilføjelsesprogrammet](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 
  
Hvis tilføjelsesprogrammet understøtter tilføjelsesprogrammets kommandoer, vises kommandoerne på Office båndet. I følgende eksempel vises kommandoen **Søg citat** for **tilføjelsesprogrammet** Citater. 

![Office båndet med Søg citater.](../../media/553b0c0a-65e9-4746-b3b0-8c1b81715a86.png)
  
Hvis det installerede tilføjelsesprogrammet ikke understøtter tilføjelsesprogrammets kommandoer, eller hvis du vil have vist alle installerede tilføjelsesprogrammet, kan du få dem vist via Mine **tilføjelsesprogrammet.** 
  
### <a name="in-word-2016-excel-2016-or-powerpoint-2016"></a>I Word 2016, Excel 2016 eller PowerPoint 2016

1. **\> Vælg Indsæt mine tilføjelser**. 
    
2. Vælg **fanen Administreret** af administratorer i Office åbne tilføjelsesvinduet. 
    
3. Dobbeltklik på det tilføjelsesprogrammet, du har installeret tidligere (i dette eksempel **Citater**).

    ![Fanen Administreret af administratorer Office siden Tilføjelser.](../../media/fd36ba81-9882-40f0-9fce-74f991aa97d5.png)
  
### <a name="in-outlook"></a>I Outlook

1. Vælg **Hent** tilføjelser **på båndet Hjem**.

    ![Store i Outlook.](../../media/getaddinsicon.png)
  
2. Vælg **Administrator-administreret** i venstre navigationslinje. 

## <a name="related-content"></a>Relateret indhold

[Mindreårige og henløsning af tilføjelsesprogrammet fra Microsoft Store](./minors-and-acquiring-addins-from-the-store.md)

