---
title: Administrer tilføjelsesprogrammer i Administration
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
description: Få mere at vide om, hvordan du bruger centraliserede tilføjelsesprogrammer til at installere tilføjelsesprogrammer til brugere og grupper i din organisation.
ms.openlocfilehash: ec972cd8ce837ae21384bc3b97513bd1263a7d84
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435429"
---
# <a name="manage-add-ins-in-the-microsoft-365-admin-center"></a>Administrer tilføjelsesprogrammer i Microsoft 365 Administration

Office tilføjelsesprogrammer hjælper dig med at tilpasse dine dokumenter og strømline den måde, du får adgang til oplysninger på internettet på. Se [Begynd at bruge dit Office-tilføjelsesprogram](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 

Når en administrator har installeret tilføjelsesprogrammer for brugere i en organisation, kan administratoren slå tilføjelsesprogrammer fra eller til, redigere, slette og administrere adgang til tilføjelsesprogrammer.

Du kan få flere oplysninger om installation af tilføjelsesprogrammer fra Administration under [Udrul tilføjelsesprogrammer i Administration](./manage-deployment-of-add-ins.md).
  
## <a name="add-in-states"></a>Tilstande for tilføjelsesprogrammer

Et tilføjelsesprogram kan være i tilstanden **Til** eller **Fra** .
  
| Staten | Sådan opstår tilstanden | Indvirkning |
|:-----|:-----|:-----|
|**Aktive**  <br/> |Administratoren har uploadet tilføjelsesprogrammet og tildelt det til brugere eller grupper.  <br/> |Brugere og grupper, der er tildelt tilføjelsesprogrammet, kan se det i de relevante klienter.  <br/> |
|**Slukket**  <br/> |Administratoren har deaktiveret tilføjelsesprogrammet.  <br/> |Brugere og grupper, der er tildelt tilføjelsesprogrammet, har ikke længere adgang til det.  <br/> Hvis tilføjelsesprogrammets tilstand ændres til Aktiv, har brugerne og grupperne adgang til det igen.  <br/> |
|**Slettet**  <br/> |Administratoren slettede tilføjelsesprogrammet.  <br/> |Brugere og grupper, der er tildelt tilføjelsesprogrammet, har ikke længere adgang til det.  <br/> |
   
Overvej at slette et tilføjelsesprogram, hvis ingen bruger det længere. Hvis du f.eks. deaktiverer et tilføjelsesprogram, kan det give mening, hvis et tilføjelsesprogram kun bruges på bestemte tidspunkter af året.

## <a name="delete-an-add-in"></a>Slet et tilføjelsesprogram

Du kan også slette et tilføjelsesprogram, der er installeret.

1. I Administration skal du gå til siden **Indstillinger** >  **Integrated apps**.

2. Vælg det installerede tilføjelsesprogram, og vælg derefter fanen **Konfiguration** .

3. I ruden **Konfiguration** skal du gå til **Avanceret Indstillinger** >  **Tilføj-ins**.

4. Vælg tilføjelsesprogrammet på listen igen.

5. Vælg **Fjern tilføjelsesprogram**. Fjern knappen Tilføjelsesprogram i nederste højre hjørne.

6. Valider dine valg, og vælg **Fjern**.

## <a name="edit-add-in-access"></a>Rediger adgang til tilføjelsesprogram

Efter installationen kan administratorer også administrere brugeradgang til tilføjelsesprogrammer.

1. I Administration skal du gå til siden **Indstillinger** >  **Integrated apps**.

2. Vælg det installerede tilføjelsesprogram.

3. Klik på **Rediger** under **Who har Access**.

4. Gem ændringerne.

## <a name="prevent-add-in-downloads-by-turning-off-the-office-store-across-all-clients-except-outlook"></a>Undgå downloads af tilføjelsesprogrammer ved at deaktivere Office Store på tværs af alle klienter (undtagen Outlook)

> [!NOTE]
> Outlook installation af tilføjelsesprogrammet administreres af en [anden proces](/exchange/clients-and-mobile-in-exchange-online/add-ins-for-outlook/specify-who-can-install-and-manage-add-ins).

Som organisation ønsker du måske at forhindre download af nye Office tilføjelsesprogrammer fra Office Store. Dette kan bruges sammen med Central installation for at sikre, at det kun er organisationsgodkendte tilføjelsesprogrammer, der udrulles til brugere i din organisation.
  
**Sådan slår du anskaffelse af tilføjelsesprogrammer fra**
  
1. I Administration skal du gå til siden **Indstillinger** \> [Organisationsindstillinger](https://go.microsoft.com/fwlink/p/?linkid=2053743).

2. Vælg **Brugerejet apps og tjenester**.
    
3. Fjern markeringen i indstillingen for at give brugerne adgang til Office store.

    Dette forhindrer alle brugere i at hente følgende tilføjelsesprogrammer fra butikken.
      
    - Tilføjelsesprogrammer til Word, Excel og PowerPoint 2016 fra:
        
      - Windows
      - Mac
      - Office
        
        
    - Opkøb, der starter i **AppSource**
        
    - Tilføjelsesprogrammer i Microsoft 365
        
    En bruger, der forsøger at få adgang til butikken, får vist følgende meddelelse: **Beklager, Microsoft 365 er konfigureret til at forhindre individuel erhvervelse af Office Store tilføjelsesprogrammer.**
  
Understøttelse af deaktivering af Office Store er tilgængelig i følgende versioner:
  
- Windows: 16.0.9001 – tilgængelig i øjeblikket.
    
- Mac: 16.10.18011401 – tilgængelig i øjeblikket.
    
- iOS: 2.9.18010804 – tilgængelig i øjeblikket.
    
- Internettet – tilgængelig i øjeblikket.
    
Dette forhindrer ikke en administrator i at bruge Central installation til at tildele et tilføjelsesprogram fra Office Store.

> [!NOTE] 
> Tilføjelsesprogrammer som f.eks. Visio Data Visualizer, Bing Kort og People Graph vises stadig på båndet, selvom en administrator har deaktiveret Store. Administratorer skal deaktivere Store via Gruppepolitik-objekt for at fjerne disse links.
  
Hvis du vil forhindre en bruger i at logge på med en Microsoft-konto, kan du begrænse logon til kun at bruge organisationskontoen. Du kan få flere oplysninger [under Identitet, godkendelse og godkendelse i Office 2016](/DeployOffice/security/identity-authentication-and-authorization-in-office).  

> [!NOTE] 
> Hvis brugerne ikke får adgang til Office Store, forhindres de også [i at indlæse Office tilføjelsesprogrammer til test fra et netværksshare](/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins).

## <a name="more-about-the-end-user-experience-with-add-ins"></a>Mere om slutbrugerens oplevelse med tilføjelsesprogrammer

Når du har installeret et tilføjelsesprogram, kan dine slutbrugere begynde at bruge det i deres Office programmer. Tilføjelsesprogrammet vises på alle platforme, som tilføjelsesprogrammet understøtter. Se [Begynd at bruge dit Office-tilføjelsesprogram](https://support.microsoft.com/office/82e665c4-6700-4b56-a3f3-ef5441996862). 
  
Hvis tilføjelsesprogrammet understøtter kommandoer i tilføjelsesprogrammet, vises kommandoerne på båndet Office. I følgende eksempel vises kommandoen **Søg i citat** for tilføjelsesprogrammet **Citater** . 

![Office bånd med søgecitater.](../../media/553b0c0a-65e9-4746-b3b0-8c1b81715a86.png)
  
Hvis det installerede tilføjelsesprogram ikke understøtter tilføjelsesprogrammer, eller hvis du vil have vist alle installerede tilføjelsesprogrammer, kan du få dem vist via **Mine tilføjelsesprogrammer**. 
  
### <a name="in-word-2016-excel-2016-or-powerpoint-2016"></a>I Word 2016, Excel 2016 eller PowerPoint 2016

1. Vælg **Indsæt \> Mine tilføjelsesprogrammer**. 
    
2. Vælg fanen **Administreret administrator** i vinduet Office tilføjelsesprogrammer. 
    
3. Dobbeltklik på det tilføjelsesprogram, du installerede tidligere (i dette eksempel **Citater**).

    ![Fanen Administreret af administratorer på siden Office tilføjelsesprogrammer.](../../media/fd36ba81-9882-40f0-9fce-74f991aa97d5.png)
  
### <a name="in-outlook"></a>I Outlook

1. På båndet **Hjem** skal du vælge **Hent tilføjelsesprogrammer**.

    ![knappen Store i Outlook.](../../media/getaddinsicon.png)
  
2. Vælg **Administratoradministrer** i venstre navigationsrude. 

## <a name="related-content"></a>Relateret indhold

[Mindreårige og hentning af tilføjelsesprogrammer fra Microsoft Store](./minors-and-acquiring-addins-from-the-store.md)

