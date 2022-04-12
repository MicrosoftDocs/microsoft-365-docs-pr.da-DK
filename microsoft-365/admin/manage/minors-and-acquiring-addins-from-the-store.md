---
title: Mindreårige og hentning af tilføjelsesprogrammer fra Store
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
description: Få mere at vide om den generelle forordning om databeskyttelse (GDPR), der styrer mindreåriges personlige data.
ms.openlocfilehash: 15b35798ba03132b35285dc16ce57b139e4d7222
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782363"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>Mindreårige og hentning af tilføjelsesprogrammer fra Store

Den generelle forordning om databeskyttelse (GDPR) er en EU-forordning, der træder i kraft den 25. maj 2018. Det giver brugerne rettigheder til og beskyttelse af deres data. Et af aspekterne i GDPR er, at mindreårige ikke kan få deres personlige oplysninger sendt til parter, som deres forælder eller værge ikke har godkendt. Den specifikke alder, der defineres som en mindreårig, afhænger af det område, hvor personen er placeret.

Regioner, der har lovgivningsmæssige bestemmelser om forældresamtykke, omfatter USA, Sydkorea, Det Forenede Kongerige og EU. For disse områder blokeres en mindreårig (via Azure Active Directory) fra at hente nye Office tilføjelsesprogrammer fra de Store og kørende tilføjelsesprogrammer, der tidligere blev anskaffet. For lande uden lovbestemte regler er der ingen downloadbegrænsninger.

En bruger bestemmes for at være underordnet baseret på data, der er angivet i Azure Active Directory. Organisationsadministratoren er ansvarlig for at erklære den juridiske aldersgruppe og forældresamtykke for den pågældende bruger.

Hvis den overordnede/værge giver samtykke til en mindreårig ved hjælp af et bestemt tilføjelsesprogram, kan organisationsadministratoren bruge central installation til at udrulle tilføjelsesprogrammet til alle mindreårige, der har samtykke.

Hvis du vil overholde GDPR for mindreårige, skal du sikre, at en af følgende builds af Office udrulles i din skole/organisation.

 **For Word, Excel, PowerPoint og Project**:

|Platform|Buildnummer|
|---|---|
|Microsoft 365 Apps for enterprise (aktuel kanal)|9001.2138|
|Microsoft 365 Apps for enterprise (halvårlig virksomhedskanal)|8431.2159|
|Office 2016 for Windows|16.0.4672.1000|
|Office 2013 for Windows|15.0.5023.1000|
|Office 2016 til Mac|16.11.18020200|
|Office til internettet|NIELSEN|

 **For Outlook**:

|Platform|Buildnummer|
|---|---|
|Outlook 2016 til Windows (MSI)|Byg ingen TBD|
|Outlook 2016 til Windows (C2R)|16.0.9323.1000|
|Office 2016 til Mac|16.0.9318.1000|
|Outlook mobil til iOS|2.75.0|
|Outlook mobil til Android|2.2.145|
|Outlook.com|NIELSEN|

 **krav til Office 2013**

Word, Excel og PowerPoint 2013 til Windows understøtter de samme underordnede kontroller, hvis ADAL (Active Directory Authentication Library) er aktiveret. Der er to muligheder for overholdelse af angivne standarder, som forklaret næste.

- **Aktivér ADAL**. I denne artikel forklares det, hvordan du aktiverer ADAL for Office 2013: [Brug af Microsoft 365 moderne godkendelse med Office klienter](../../enterprise/modern-auth-for-office-2013-and-2016.md).<br/>Du skal også angive registreringsdatabasenøglerne for at aktivere ADAL som beskrevet i [Aktivér moderne godkendelse for Office 2013 på Windows enheder](../security-and-compliance/enable-modern-authentication.md).<br/>Derudover skal du installere følgende opdateringer fra april til Office 2013:

  - [Beskrivelse af sikkerhedsopdateringen til Office 2013: 10. april 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)

  - [3. april 2018, opdatering til Office 2013 (KB4018333)](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)

- **Aktivér ikke ADAL**. Hvis du ikke kan aktivere ADAL i Office 2013, anbefaler vi, at du bruger Gruppepolitik til at deaktivere Store for de Office klienter. Du kan finde oplysninger om, hvordan du slår appen fra for Office indstillinger[, her](/previous-versions/office/office-2013-resource-kit/cc178992(v=office.15)).

## <a name="related-articles"></a>Relaterede artikler

[Udrul tilføjelsesprogrammer i administrationen](./manage-deployment-of-add-ins.md)

[Administrer tilføjelsesprogrammer i Administration](./manage-addins-in-the-admin-center.md)
