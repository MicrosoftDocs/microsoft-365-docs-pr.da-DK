---
title: playbook til Microsoft Defender til virksomheder Premium-prøveversion
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.collection: m365-security-compliance
ms.localizationpriority: high
ms.date: 07/19/2022
ms.prod: m365-security
search.appverid:
- MOE150
- MET150
description: Få mest ud af din Microsoft 365 Business Premium prøveversion. Prøv nogle af de vigtigste produktivitets- og sikkerhedsfunktioner.
ms.openlocfilehash: fd1871d6902fa7d39a755ea8d7d857baabff2413
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/20/2022
ms.locfileid: "66894893"
---
# <a name="trial-playbook-microsoft-business-premium"></a>Playbook til prøveversion: Microsoft Business Premium

Velkommen til microsoft Business Premium-prøveversionens playbook. Denne playbook hjælper dig med at få mest ud af din 30-dages gratis prøveversion ved at opleve, hvordan Microsoft 365 Business Premium øger produktiviteten og hjælper med at beskytte din organisation med avancerede sikkerhedsfunktioner. Ved hjælp af Microsoft-anbefalinger kan du få mere at vide om, hvordan du kan konfigurere dine trusselsbeskyttelsesfunktioner, analysere registrerede trusler og reagere på cyberangreb.

## <a name="set-up-the-microsoft-365-business-premium-trial"></a>Konfigurer prøveversionen af Microsoft 365 Business Premium

Når du [starter en prøveversion eller køber Microsoft 365 Business Premium](get-microsoft-365-business-premium.md), er dit første skridt at konfigurere alt.

> [!TIP]
> Gem denne playbook i dine browserfavoritter. Når links i playbook tager dig væk fra dette sted, skal du blot vende tilbage til denne playbook for at fortsætte.

Først skal [du konfigurere din prøveversion](../business-premium/m365bp-setup.md)!

Når du har startet prøveversionen og fuldført konfigurationsprocessen, kan det tage op til to timer, før ændringerne træder i kraft.

Microsoft 365 Business Premium indeholder [forudindstillede sikkerhedspolitikker](/security/office-365-security/preset-security-policies.md), som du kan bruge i dit miljø. Disse politikker repræsenterer en profil for grundlæggende beskyttelse, der passer til de fleste brugere. Standardbeskyttelse omfatter:

- [Sikre links](../security/office-365-security/safe-links.md), [vedhæftede filer](../security/office-365-security/safe-attachments.md) og [anti-phishing-politikker](../security/office-365-security/anti-phishing-protection.md) , der er begrænset til hele lejeren eller det undersæt af brugere, du har valgt under installationen af prøveversionen. (Dit prøveabonnement er til op til 25 brugere).

- Beskyttelse af produktivitetsapps, f.eks [. SharePoint](/sharepoint/introduction), [OneDrive](/onedrive/one-drive-quickstart-small-business), [Office-apps](/deployoffice/about-microsoft-365-apps) og [Microsoft Teams](/microsoftteams/teams-overview).

## <a name="add-a-domain"></a>Tilføj et domæne

Når du prøver eller køber Microsoft 365 Business Premium, har du mulighed for at bruge et domæne, du ejer, eller købe et under tilmeldingsprocessen.

> [!NOTE]
> Hvis du har købt et nyt domæne, da du tilmeldte dig, er dit domæne konfigureret, og du kan flytte til Tilføj brugere og tildele licenser. Gå til Administration([https://admin.microsoft.com](https://admin.microsoft.com)).

1. Vælg **Installation** i menuen Administration for at starte guiden.

2. Vælg **Konfigurer mail med et brugerdefineret domæne** , og **brug derefter et domæne, du allerede ejer** , f.eks `contoso.com`. .

3. Følg resten af trinnene i guiden for at fuldføre processen.

   > [!Important]
   > Hvis du har købt et domæne under tilmeldingen, kan du ikke se trinnet **Tilføj et domæne** her. Gå i stedet til **Tilføj brugere** .

4. Følg trinnene i guiden for at [oprette DNS-poster hos en hvilken som helst DNS-hostingudbyder for Office 365](/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider), der bekræfter, at du ejer domænet. Hvis du kender din domænevært, skal du se [Føj et domæne til Microsoft 365](/microsoft-365/admin/setup/add-domain).

5. Hvis din hostingudbyder er GoDaddy eller en anden vært aktiveret med domæneforbindelse, er processen nem, og du bliver automatisk bedt om at logge på og lade Microsoft godkende på dine vegne.

## <a name="onboard-and-protect-devices"></a>Onboarde og beskyt enheder

> [!NOTE]
> Muligheden for at onboarde slutpunkter, der kører Windows Server eller Linux Server, fås nu som prøveversion! Se [Onboard-enheder for at Microsoft Defender til virksomheder](../security/defender-business/mdb-onboard-devices.md).

1. Gå til Microsoft 365 Defender-portalen ([https://security.microsoft.com](https://security.microsoft.com)), og log på.

2. Kør [installationsguiden](../security/defender-business/mdb-use-wizard.md).

3. [Onboarde enheder](../security/defender-business/mdb-onboard-devices.md).

4. [Gennemse dine sikkerhedspolitikker](../security/defender-business/mdb-configure-security-settings.md).

## <a name="use-office-apps-on-devices"></a>Brug Office-apps på enheder

1. Først skal du [installere Office](m365bp-install-office-apps.md).

2. Gå til office.com, og [log på](https://support.microsoft.com/office/get-started-at-office-com-91a4ec74-67fe-4a84-a268-f6bdf3da1804).

3. Opret et Office-dokument, f.eks. et [Word-dokument](https://support.microsoft.com/office/basic-tasks-in-word-87b3243c-b0bf-4a29-82aa-09a681999fdc).

4. [Del et dokument](https://support.microsoft.com/office/share-your-documents-651e1cb9-9a51-46dc-8d32-bdb7d928eedd) med et teammedlem.

## <a name="start-using-the-microsoft-365-defender-portal"></a>Begynd at bruge Microsoft 365 Defender-portalen 

1. Få adgang til Microsoft 365 Defender-portalen på [https://security.microsoft.com](https://security.microsoft.com).

2. Brug lidt tid på at [blive fortrolig med portalen](../security/defender-business/mdb-get-started.md).

3. [Vurder din sikkerhedsholdning](../security/defender/microsoft-secure-score.md).

4. Bliv fortrolig med [, hvordan du besvarer en sikkerhedshændelse](../security/defender-business/mdb-respond-mitigate-threats.md).

5. Endelig [skal du gennemse afhjælpningshandlinger](../security/defender-business/mdb-review-remediation-actions.md).

## <a name="see-also"></a>Se også

- [&mdash; Microsoft 365 Business Premium cybersikkerhed til mindre virksomheder](index.md)