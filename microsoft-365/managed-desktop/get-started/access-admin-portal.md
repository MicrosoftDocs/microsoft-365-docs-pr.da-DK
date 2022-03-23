---
title: Få adgang til administrationsportalen
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
description: Sådan finder og bruger du administrationsportalen, herunder kontrol af adgang til den.
ms.service: m365-md
ms.author: tiaraquan
author: tiaraquan
ms.topic: article
audience: ITPro
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.openlocfilehash: aee590f7479119ee7e8679b1048a691f156ccc77
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589480"
---
# <a name="access-the-admin-portal"></a>Få adgang til administrationsportalen

Din gateway til tjenesten Microsoft Managed Desktop er [Microsoft Endpoint Manager](https://endpoint.microsoft.com/). Hvis du ikke er bekendt med funktionerne i denne portal til enhedshåndtering, skal du se Microsoft Endpoint Manager [dokumentationen](/mem/).

> [!NOTE]
> I [Microsoft Endpoint Manager](https://endpoint.microsoft.com/) understøttes følgende browsere:
> - Microsoft Edge (nyeste version)
> - Safari (nyeste version, kun Mac)
> - Chrome (nyeste version)
> - Firefox (nyeste version)

Din administrative konto skal have specifikke tilladelser for at få adgang til administrative funktioner i Microsoft Managed Desktop Microsoft Endpoint Manager.

Du kan administrere administratoradgang til disse funktioner i din organisation ved hjælp af rollebaseret adgangskontrol. Flere Azure Active Directory -administratorroller (Azure AD) og indbyggede Microsoft-administrerede skrivebordsroller er tilgængelige, så der er mere detaljeret kontrol over de forskellige funktioner i administrationsportalen til Microsoft-computere. Du kan finde flere oplysninger Azure Active Directory dine roller i [indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference).

I modsætning til Azure AD-administratorroller, der gælder for forskellige Microsoft-produkter og -tjenester, er de indbyggede roller specifikke for Microsoft Managed Desktop og garanterer kun adgang til administratorfunktionerne for denne tjeneste. Administratorer kan tildele indbyggede roller til brugere enkeltvis eller i kombination med Azure AD-administratorroller for at føje Microsoft Managed Desktop-tilladelser til eksisterende administratorkonti.

## <a name="azure-active-directory-roles-with-microsoft-managed-desktop-access"></a>Azure Active Directory med Microsoft-administreret skrivebordsadgang

| Azure AD-rolle | Microsoft-administreret skrivebordstilladelser |
| ----- | ----- |
| Global Administrator | Administratorer med denne rolle har læse **- og skrivetilladelser til alle funktioner i** Administrationsportalen for Microsoft Managed Desktop. |
| Global læser | Administratorer med denne rolle har **skrivebeskyttede tilladelser til alle funktioner i** Administrationsportalen for Microsoft-administreret skrivebord. |
| Intune-tjenesteadministrator | Administratorer med denne rolle har læse- **og** skrivetilladelser til funktioner, der ikke er relateret til sikkerhed i administrationsportalen for Microsoft Managed Desktop. |
| Tjenestesupportadministrator | Administratorer med denne rolle har skrivebeskyttede tilladelser til funktioner, der ikke er relateret til sikkerhed og skrivetilladelser til at administrere **supportanmodninger**, herunder eskaleringsanmodninger, i Microsoft Managed **Desktop-administrationsportalen**. |
| Sikkerhedsadministrator | Administratorer med denne rolle har **skrivebeskyttede** tilladelser til alle funktioner og skrivetilladelser til  sikkerhedsrelaterede funktioner i Microsoft Managed Desktop på administrationsportalen. |
| Sikkerhedslæser |Administratorer med denne rolle har **skrivebeskyttede tilladelser til alle funktioner i** Administrationsportalen for Microsoft-administreret skrivebord. |

Hvis du har brug for hjælp til at tildele Azure Active Directory, skal du [se Indbyggede roller i Azure AD](/azure/active-directory/roles/permissions-reference).

> [!IMPORTANT]
> Kun den globale administratorrolle har de nødvendige tilladelser til at *tilmelde din* organisation i Microsoft Managed Desktop. Vær opmærksom på, Azure Active Directory brugerroller giver brugerkonti rettigheder på tværs af en række Microsoft-tjenester. Når du har fuldført tilmeldingen til Microsoft Managed Desktop, bør du altid bruge rollen med de  mindst nødvendige rettigheder til at udføre dine andre opgaver.

## <a name="built-in-roles-provided-by-microsoft-managed-desktop"></a>Indbyggede roller leveret af Microsoft Managed Desktop

Følgende er de indbyggede roller, der leveres af Microsoft Managed Desktop:

| Indbygget rolle | Microsoft-administreret skrivebordstilladelser |
| ----- | ----- |
| Microsoft Managed Desktop Service-administrator | Når denne rolle er tildelt en bruger, giver den administrator læse- og skrivetilladelser til **Microsoft-administrerede** computerfunktioner, der ikke er relateret til sikkerhed i administrationsportalen for Microsoft-administreret skrivebord. |
| Microsoft Managed Desktop Service Reader | Når denne rolle er tildelt en bruger, giver den administrator skrivebeskyttede tilladelser til **Microsoft-administrerede** computerfunktioner, der ikke er relateret til sikkerhed i administrationsportalen for Microsoft-administreret skrivebord. |
| Microsoft Managed Desktop Security Manager | Når denne rolle er tildelt en bruger, giver den pågældende administrator kun læse **-** og skrivetilladelser til sikkerhedsrelaterede funktioner i administrationsportalen for Microsoft Managed Desktop. |
| Microsoft-partner med administreret skrivebordssupport |Når denne rolle er tildelt en bruger, giver den kun administrator læse- og skrivetilladelser til oprettelse og administration af **udvidelsesanmodninger og supportpartnerens engagerede eskaleringsanmodninger** i Administrationsportalen for Microsoft-administreret skrivebord. |

> [!NOTE]
> Sikkerhedsfunktionerne omfatter sikkerhedsrelateret kommunikation, administration af sikkerhedskontakter, administration af sikkerhedsrelaterede supportanmodninger og adgang til sikkerhedsrelaterede rapporter.

### <a name="assigning-built-in-roles-to-user"></a>Tildele indbyggede roller til brugeren

For nem administration af indbyggede roller er der en sikkerhedsgruppe for hver brugerdefineret rolle med navnet "Roller på den moderne arbejdsplads – _rollenavn_". F.eks. "Roller på den moderne arbejdsplads – Sikkerhedsadministrator").

**Sådan tildeler du brugere til en af disse sikkerhedsgrupper:**

1. Gå til Microsoft Endpoint Manager portalen.
2. Vælg Grupper i venstre **rude**.
3. Søg efter **Roller på den moderne arbejdsplads**, og vælg derefter den gruppe, der er knyttet til den rolle, du vil tildele.
4. Vælg **Medlemmer** i venstre side, og vælg **derefter + Tilføj** medlemmer på kommandolinjen.
5. Angiv mailadressen på den person, der bliver tilføjet. Hvis de er gæster, skal du invitere dem, før du kan tildele gruppen.
6. Vælg **Vælg** nederst.

> [!NOTE]
> Indlejring af sikkerhedsgrupper for rolletildeling understøttes ikke i øjeblikket.

### <a name="assigning-built-in-roles-to-groups"></a>Tildele indbyggede roller til grupper

**Sådan tildeler du en eller flere af de indbyggede roller til en eksisterende gruppe:**

1. Gå til [portal.azure.com](https://portal.azure.com/).
2. Søg efter og åbn **Enterprise-programmer**.
3. Skift **filteret Programtype** til _Microsoft Programmer_ , og vælg derefter **Anvend**.
4. Søg efter og vælg _Moderne Workplace Customer-API'er_.
5. Vælg **Brugere og grupper** i ruden til venstre, og vælg derefter **+ Tilføj bruger/gruppe**.
6. Søg efter den gruppe, du ønsker fra **Brugere og grupper**.
7. Søg efter den relevante rolle fra **Vælg en rolle**, og vælg den derefter.
8. Vælg **Tildel**.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Trin til at komme i gang med Microsoft-administreret skrivebord

1. Adgang til administrationsportalen (denne artikel).
1. [Tilføj og bekræft administratorkontakter i administrationsportalen](add-admin-contacts.md).
1. [Juster indstillinger efter tilmelding](conditional-access.md).
1. Installér og [tildel Intune-firmaportal](company-portal.md).
1. [Tildel licenser](assign-licenses.md).
1. [Installér apps](deploy-apps.md).
1. [Klargør enheder](prepare-devices.md).
1. Konfigurer første [kørselsoplevelse med Autopilot og Statussiden For tilmelding](esp-first-run.md).
1. [Aktivér brugersupportfunktioner](enable-support.md).
1. [Gør dine brugere klar til at bruge enheder](get-started-devices.md).
1. [Kom i gang med appstyring](get-started-app-control.md).
