---
title: Administrere Microsoft 365 identitetsstyring
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
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
description: Få mere at vide om, hvordan du Microsoft 365 funktioner til identitetsstyring.
ms.openlocfilehash: 35b2092412ddbeacd5d6962e110de1931b2d0f4b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63591084"
---
# <a name="manage-microsoft-365-identity-governance"></a>Administrere Microsoft 365 identitetsstyring

Identitetsstyring handler om at beskytte, overvåge og overvåge adgang til vigtige aktiver og samtidig sikre medarbejdernes produktivitet. Med identitetsstyring kan du f.eks. sikre, at de rette brugere har den rette adgang til de rette ressourcer og afgøre, om denne adgang ændres over tid.

Få mere at vide under Denne [oversigt over identitetsstyring for Azure Active Directory (Azure AD)](/azure/active-directory/governance/identity-governance-overview).

## <a name="set-up-azure-ad-access-reviews"></a>Konfigurer Azure AD-adgangsvurderinger

Gennemgange af Azure AD-adgang giver dig mulighed for at gennemse en brugers adgang for at sikre, at kun de rette personer har fortsat adgang. Eksempel:

- Når nye medarbejdere tilmelder sig organisationen, skal du sikre dig, at de har den rette adgang til at være produktive.
- Når medarbejderen flytter til andre teams, placeringer eller afdelinger, skal du sikre, at deres adgang til tidligere teams, placeringer eller afdelinger fjernes efter behov.
- Når medarbejderen eller en gæst forlader organisationen, skal du sikre dig, at deres adgang fjernes.

Dette er især vigtigt, hvis din organisation er underlagt sikkerhedsrevision for at afgøre, om brugerkonti har for meget adgang, hvilket kan give fines, hvis branchereglerne eller de regionale bestemmelser overtræder reglerne.

Du kan finde flere oplysninger i [oversigten over gennemgange af adgang](/azure/active-directory/governance/access-reviews-overview).

Se disse artikler for at konfigurere forskellige typer af adgangsvurderinger:

- [Grupper og apps](/azure/active-directory/governance/create-access-review)
- [Azure AD-roller](/azure/active-directory/privileged-identity-management/pim-how-to-start-security-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)
- [Ressourceroller i Azure](/azure/active-directory/privileged-identity-management/pim-resource-roles-start-access-review?toc=%2fazure%2factive-directory%2fgovernance%2ftoc.json)

## <a name="set-up-azure-ad-entitlement-management"></a>Konfigurer Azure AD rettighedsstyring

Wiht Azure AD rettighedsstyring, du kan administrere identitet og adgang til livscyklus på skala ved at automatisere arbejdsprocesser for adgangsanmodninger, få adgang til opgaver, anmeldelser og udløb.

Dine medarbejdere skal have adgang til forskellige grupper, programmer og websteder for at udføre deres arbejde. Administration af denne adgang kan være udfordrende, fordi krav ændres, nye programmer tilføjes, eller brugere har brug for yderligere adgangsrettigheder. Når du samarbejder med andre organisationer, ved du muligvis ikke, hvem i den anden organisation der skal have adgang til organisationens ressourcer, og eksterne brugere ved ikke, hvilke programmer, grupper eller websteder din organisation bruger.

Azure AD rettighedsstyring kan hjælpe dig med mere effektivt at administrere adgangen til grupper, programmer og SharePoint for interne og eksterne brugere.
 
Du kan finde flere oplysninger i [oversigten over administration af rettighedsstyring i Azure AD](/azure/active-directory/governance/entitlement-management-overview).