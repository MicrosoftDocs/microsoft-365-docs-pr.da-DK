---
title: Mindreårige og henløsning af tilføjelsesprogrammet fra Store
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Få mere at vide om persondataforordningen (GDPR), der regulerer persondata for mindreårige.
ms.openlocfilehash: 84a1ecc9eb5d29ae1c2e4597b8299430cc3de038
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63590290"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>Mindreårige og henløsning af tilføjelsesprogrammet fra Store

Den generelle forordning om databeskyttelse (GDPR ) er en EU-forordning, der træder i kraft d. 25. maj 2018. Den giver brugerne rettigheder til og beskyttelse af deres data. Et af aspekterne i GDPR er, at mindreårige ikke kan få deres personlige data sendt til parter, som deres forælder eller værge ikke har godkendt. Den bestemte alder, der er defineret som mindreårig, afhænger af det område, hvor personen er placeret.
  
Områder, der har lovmæssige reguleringer om forældresamtykke omfatter USA, Sydkorea, Storbritannien og EU. For disse områder vil en mindreårig blive blokeret (via Azure Active Directory) fra at hente nye Office-tilføjelsesprogrammet fra Store og køre de tilføjelses programmer, der tidligere er blevet købt. For de lande, der ikke har lovmæssige reguleringer, vil der ikke være nogen begrænsninger for hentning.
  
En bruger vurderes som mindreårig på baggrund af de data, der er angivet i Azure Active Directory. Organisationens administrator har ansvaret for at erklære gruppen for juridisk alder og forældresamtykke for den pågældende bruger.
  
Hvis en forælder/værge giver tilladelse til, at en mindreårig kan bruge et bestemt tilføjelsesprogrammet, kan organisationens administrator bruge centraliseret udrulning til at installere tilføjelsesprogrammet for alle de mindreårige, der har tilladelse.
  
For at overholde GDPR for mindreårige skal du sikre, at et af følgende builds af Office er installeret på din skole/organisation.
 
 **I Word Excel, PowerPoint og Project**: 

|**Platform** <br/> |**Buildnummer** <br/> |
|:-----|:-----|
|Microsoft 365 Apps for enterprise (Aktuel kanal)  <br/> |9001.2138   <br/> |
|Microsoft 365 Apps for enterprise (halvårlige virksomhedskanal)  <br/> |8431.2159  <br/> |
|Office 2016 til Windows  <br/> |16.0.4672.1000  <br/> |
|Office 2013 til Windows  <br/> |15.0.5023.1000  <br/> |
|Office 2016 til Mac  <br/> |16.11.18020200  <br/> |
|Office til internettet  <br/> |I/T  <br/> |
   
 **For Outlook**: 
  
|**Platform** <br/> |**Buildnummer** <br/> |
|:-----|:-----|
|Outlook 2016 til Windows (MSI)  <br/> |Buildnr.  <br/> |
|Outlook 2016 for Windows (C2R)  <br/> |16.0.9323.1000  <br/> |
|Office 2016 til Mac  <br/> |16.0.9318.1000  <br/> |
|Outlook mobil til iOS  <br/> |2.75.0  <br/> |
|Outlook til Android  <br/> |2.2.145  <br/> |
|Outlook.com  <br/> |I/T  <br/> |

 **Office 2013**
  
Word, Excel og PowerPoint 2013 til Windows understøtter de samme mindre kontroller, hvis Active Directory Authentication Library (ADAL) er aktiveret. Der er to muligheder for overholdelse som beskrevet herefter.
  
- **Aktivér ADAL**. Denne artikel forklarer, hvordan du aktiverer ADAL til Office 2013: Brug [Microsoft 365 moderne godkendelse med Office klienter](../../enterprise/modern-auth-for-office-2013-and-2016.md).<br/>Du skal også angive registreringsdatabasenøglerne for at aktivere ADAL som beskrevet i Aktivér moderne godkendelse [Office 2013 på Windows enheder](../security-and-compliance/enable-modern-authentication.md).<br/>Desuden skal du installere følgende opdateringer for april til Office 2013:
    
  - [Beskrivelse af sikkerhedsopdateringen til Office 2013: 10. april 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)
    
  - [3. april 2018, opdatering til Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)
    
- **Aktivér ikke ADAL**. Hvis du ikke kan aktivere ADAL i Office 2013, er vores anbefaling, at du bruger Gruppepolitik til at deaktivere Store for Office-klienterne. Oplysninger om, hvordan du deaktiverer appen for Office indstillinger, findes [her](/previous-versions/office/office-2013-resource-kit/cc178992(v=office.15)).

## <a name="related-articles"></a>Relaterede artikler

[Udrul tilføjelsesprogrammer i administrationen](./manage-deployment-of-add-ins.md)

[Administrer tilføjelser i Administration](./manage-addins-in-the-admin-center.md)
