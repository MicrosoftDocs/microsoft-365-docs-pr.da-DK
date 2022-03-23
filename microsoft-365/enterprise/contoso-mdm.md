---
title: Administration af mobilenheder for Contoso
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Få mere at vide om, hvordan Contoso Microsoft Intune i Microsoft 365 til virksomheder til at administrere sine enheder og de apps, der kører på dem.
ms.openlocfilehash: dedda98083dd5a27c4c7721b5ae8e5dc1fed4bad
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 11/19/2021
ms.locfileid: "63588877"
---
# <a name="mobile-device-management-for-contoso"></a>Administration af mobilenheder for Contoso

Microsoft 365 til virksomheder omfatter Intune og et sæt Af Azure-tjenester, der understøtter administration og sikkerhed af mobilenheder og programmer.

Contoso har mange mobile medarbejdere. Nogle har kontorer i Contoso-placeringer, og nogle har ingen kontorer. Contoso havde brug for en metode til at aktivere medarbejdernes produktivitet, men holde enhederne, Contoso-dataene, der er gemt på disse enheder, og programfunktionsmåden sikker.

## <a name="plan"></a>Plan

Contoso identificerede følgende Intune-use cases om administration af mobilenheder til Microsoft 365 til virksomheder:

- Beskyt Exchange Online mail og data, så de kan benyttes sikkert på mobilenheder.
- Implementer et BYOD-program (bring-your-own-device) for Contoso-medarbejdere.
- Udstede organisationsejede telefoner og begrænset brug af delte tablets til Contoso-medarbejdere.

Contoso bruger ikke Intune til at:

- Giv medarbejdere sikker adgang til Microsoft 365 fra en ikke-administreret offentlig kiosk.
- Beskyt lokale mails og data, så de kan benyttes sikkert på mobilenheder, fordi der ikke er nogen lokale Microsoft-Exchange-servere.

## <a name="deploy"></a>Installér

Sådan konfigurerer Contoso deres infrastruktur til administration af mobilenheder:

- Angiv Intune som MDM-autoritet (Mobile Device Management), og brug Intune på Azure til at administrere indhold og administrere enhederne
- Oprettede Azure Active Directory (Azure AD)-grupper til enheder til registrering og Intune-indstillinger og enhedsbaserede politikker for betinget adgang

  Få mere at vide under [Politikker for betinget adgang i Contoso](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access).

- Apple-enhedsplatformen var aktiveret til at understøtte medarbejdere med iPads, iMacs og iPhones samt virksomhedsejede iPhones
- Oprettede contoso-specifikke politikker for vilkår og betingelser, som ses under installationen af Firmaportal for Contoso på mobilenheder
- For enheder, der ikke er tilmeldt, skal du implementere en række politikker for administration af mobilapps (MAM), så der kræves godkendelse for at få adgang til Microsoft 365 tjenester
- Oprettede Intune-politikker, der gennemtvinger:
  - Tilladte apps.
  - Enhedskryptering for at forhindre uautoriseret adgang.
  - En sekscifret pinkode eller adgangskode.
  - En inaktivitetstidsperiode.
  - Beskyttelse mod antivirus og malware samt signaturopdateringer med Windows Defender på Windows 10 enheder.
  - Automatiske opdateringer på Windows 10, der indeholder de nyeste sikkerhedsopdateringer.
  - Skubbe certifikater til administrerede enheder.
  - En klar adskillelse af forretnings- og personlige data. Brugere eller administratorer kan selektivt slette virksomhedens data fra enheden, mens personlige data som billeder, personlige mailkonti og personlige filer ikke ændres.

Contoso tilmeldte udrullede pc'er og virksomhedsejede smartphones og tablets ved at føje dem til de relevante Intune-enhedsgrupper. De har også oprettet et BYOD-program, hvor medarbejderne kan tilmelde deres personlige enheder. Tilmeldte enheder modtager Intune-politikker, som resulterer i administrerede og sikrede enheder og deres programmer. Enheder, der ikke er tilmeldt, har politikker for administration af mobile programmer (MAM), der angiver tilladte programmer.

Her er installationsarkitekturen til administration af Contoso-mobilenheder.

![Installationsinfrastruktur til administration af Contoso-mobilenheder.](../media/contoso-mdm/contoso-mdm-fig1.png)

## <a name="next-step"></a>Næste trin

Få mere at vide om, hvordan [](contoso-info-protect.md) Contoso bruger funktionerne til beskyttelse af oplysninger i Microsoft 365 til virksomheder til at klassificere, identificere og beskytte vigtige digitale aktiver på tværs af organisationen.

## <a name="see-also"></a>Se også

[Enhedshåndtering for Microsoft 365](device-management-roadmap-microsoft-365.md)

[Microsoft 365 for Enterprise-oversigt](microsoft-365-overview.md)

[Test labvejledninger](m365-enterprise-test-lab-guides.md)

