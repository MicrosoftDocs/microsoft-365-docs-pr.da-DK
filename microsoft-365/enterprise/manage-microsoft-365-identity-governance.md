---
title: Administrer Microsoft 365 identitetsstyring
ms.author: kvice
author: kelleyvice-msft
manager: scotv
audience: Admin
ms.topic: overview
ms.prod: office-online-server
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-mar2020
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: Få mere at vide om, hvordan du bruger Microsoft 365 funktioner til identitetsstyring.
ms.openlocfilehash: f4fcfed9fcb978e40c3bf7c0e7a35eb717fee343
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/27/2022
ms.locfileid: "65091165"
---
# <a name="manage-microsoft-365-identity-governance"></a>Administrer Microsoft 365 identitetsstyring

Identitetsstyring handler om at beskytte, overvåge og overvåge adgang til kritiske aktiver og samtidig sikre medarbejdernes produktivitet. Med identitetsstyring kan du f.eks. sikre, at de rette brugere har den rette adgang til de rette ressourcer og afgøre, om denne adgang ændres over tid.

Du kan få flere oplysninger i denne [oversigt over identitetsstyring for Azure Active Directory (Azure AD)](/azure/active-directory/governance/identity-governance-overview).

## <a name="set-up-azure-ad-access-reviews"></a>Konfigurer azure AD-adgangsgennemgange

Gennemsyn af Azure AD-adgang giver dig mulighed for at gennemse en brugers adgang for at sikre, at det kun er de rette personer, der har fortsat adgang. Eksempel:

- Når en ny medarbejder tilmelder sig din organisation, skal du sikre, at de har den rette adgang til at være produktive.
- Når medarbejderen flytter til andre teams, placeringer eller afdelinger, skal du sikre, at deres adgang til tidligere teams, placeringer eller afdelinger fjernes efter behov.
- Når medarbejderen eller en gæst forlader organisationen, skal du sikre, at vedkommendes adgang fjernes.

Dette er især vigtigt, hvis din organisation er underlagt sikkerhedsovervågninger for at afgøre, om brugerkonti har for meget adgang, hvilket kan resultere i bøder, hvis det er i strid med brancheregler eller regionale regler.

Du kan få flere oplysninger i [oversigten over adgangsgennemgange](/azure/active-directory/governance/access-reviews-overview).

Se disse artikler for at konfigurere forskellige typer adgangsgennemgange:

- [Grupper og apps](/azure/active-directory/governance/create-access-review)
- [Azure AD-roller](/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [Azure-ressourceroller](/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

## <a name="set-up-azure-ad-entitlement-management"></a>Konfigurer Azure AD-rettighedsstyring

Med Azure AD-rettighedsstyring kan du administrere identitets- og adgangslivscyklussen i stor skala ved at automatisere arbejdsprocesser for anmodninger om adgang, adgangstildelinger, anmeldelser og udløb.

Dine medarbejdere skal have adgang til forskellige grupper, programmer og websteder for at kunne udføre deres job. Det kan være en udfordring at administrere denne adgang, fordi kravene ændres, der tilføjes nye programmer, eller brugerne har brug for yderligere adgangsrettigheder. Når du samarbejder med andre organisationer, ved du muligvis ikke, hvem i den anden organisation der har brug for adgang til organisationens ressourcer, og eksterne brugere ved ikke, hvilke programmer, grupper eller websteder din organisation bruger.

Azure AD-rettighedsstyring kan hjælpe dig med mere effektivt at administrere adgang til grupper, programmer og SharePoint websteder for interne og eksterne brugere.
 
Du kan få flere oplysninger i [oversigten over administration af rettigheder i Azure AD](/azure/active-directory/governance/entitlement-management-overview).