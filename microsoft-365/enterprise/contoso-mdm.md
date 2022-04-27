---
title: Administration af mobilenheder for Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Forstå, hvordan Contoso bruger Microsoft Intune i Microsoft 365 for enterprise til at administrere sine enheder og de apps, der kører på dem.
ms.openlocfilehash: c321fc9bdaf27577e32d934aa771c92d1a0bdd79
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092685"
---
# <a name="mobile-device-management-for-contoso"></a>Administration af mobilenheder for Contoso

Microsoft 365 til virksomheder omfatter Intune og et sæt Azure-tjenester, der understøtter administration og sikkerhed af mobilenheder og programmer.

Contoso har mange mobilaktiverede medarbejdere. Nogle har kontorer i Contoso steder, og nogle har ingen kontorer. Contoso havde brug for en metode til at aktivere medarbejdernes produktivitet, men bevare de enheder, Contoso-data, der er gemt på disse enheder, og programfunktionsmåden sikker.

## <a name="plan"></a>Plan

Contoso identificerede følgende Intune brugssager for administration af mobilenheder for Microsoft 365 til virksomheder:

- Beskyt Exchange Online mail og data, så mobilenheder kan få adgang til dem på en sikker måde.
- Implementer et BYOD-program (bring-your-own-device) til Contoso-medarbejdere.
- Udsted organisationsejede telefoner og delte tablets med begrænset brug til Contoso-medarbejdere.

Contoso bruger ikke Intune til at:

- Giv medarbejderne sikker adgang til Microsoft 365 fra en ikke-administreret offentlig kiosk.
- Beskyt mail og data i det lokale miljø, så mobilenheder kan få sikker adgang til dem, fordi der ikke er nogen Microsoft Exchange-servere i det lokale miljø.

## <a name="deploy"></a>Rul ud

Sådan konfigurerer Contoso infrastrukturen for administration af mobilenheder:

- Angiv Intune som MDM-autoritet (Mobile Enhedshåndtering), og brug Intune på Azure til at administrere indhold og administrere enhederne
- Oprettede Azure Active Directory (Azure AD)-grupper til enheder til tilmelding og Intune indstillinger og enhedsbaserede politikker for betinget adgang

  Du kan få flere oplysninger under [Politikker for betinget adgang i Contoso](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access).

- Apple-enhedsplatformen understøtter medarbejdere med iPads, iMacs og iPhones og virksomhedsejede iPhones
- Oprettede Contoso-specifikke vilkår og betingelser, som ses under installationen af Firmaportal til Contoso på mobilenheder
- For de enheder, der ikke er tilmeldt, skal du implementere et sæt MAM-politikker (Mobile Application Management), der kræver godkendelse for at få adgang til Microsoft 365-tjenester
- Oprettede Intune politikker, der gennemtvinger:
  - Tilladte apps.
  - Enhedskryptering for at forhindre uautoriseret adgang.
  - En sekscifret pinkode eller adgangskode.
  - En inaktivitetstimeoutperiode.
  - Antivirus- og malwarebeskyttelse samt signaturopdateringer med Windows Defender på Windows 10 enheder.
  - Automatiske opdateringer på Windows 10 enheder, der indeholder de nyeste sikkerhedsopdateringer.
  - Push af certifikater til administrerede enheder.
  - En klar adskillelse af forretningsdata og personlige data. Brugere eller administratorer kan selektivt slette firmadata fra enheden, mens personlige data som billeder, personlige mailkonti og personlige filer ikke berøres.

Contoso tilmeldte pc'er og virksomhedsejede smartphones og tablets ved at føje dem til de relevante Intune enhedsgrupper. De har også etableret et BYOD-program, hvor medarbejderne kan tilmelde deres personlige enheder. Tilmeldte enheder modtager Intune politikker, som resulterer i administrerede og sikrede enheder og deres programmer. Enheder, der ikke er tilmeldt, har MAM-politikker (Mobile Application Management), der angiver tilladte programmer.

Her er arkitekturen til installation af Contoso-mobilenheder.

![Contoso installationsinfrastruktur for administration af mobilenheder.](../media/contoso-mdm/contoso-mdm-fig1.png)

## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan Contoso bruger [funktionerne til beskyttelse af oplysninger](contoso-info-protect.md) i Microsoft 365 til virksomheder til at klassificere, identificere og beskytte vigtige digitale aktiver på tværs af organisationen.

## <a name="see-also"></a>Se også

[Enhedshåndtering for Microsoft 365](device-management-roadmap-microsoft-365.md)

[Microsoft 365 til virksomhedsoversigt](microsoft-365-overview.md)

[Vejledninger til testlaboratorier](m365-enterprise-test-lab-guides.md)

