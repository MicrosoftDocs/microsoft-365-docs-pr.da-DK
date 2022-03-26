---
title: Samarbejde med personer uden for organisationen
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-securecollab
- m365solution-scenario
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Få mere at vide om, hvordan Microsoft 365 konfigurerer apps som Teams, OneDrive og SharePoint til samarbejde med personer uden for organisationen.
ms.openlocfilehash: 65511cbafdc1f5a666c11e1bef7fefd6e6852ee3
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/22/2022
ms.locfileid: "63712768"
---
# <a name="collaborating-with-people-outside-your-organization"></a>Samarbejde med personer uden for organisationen

De eksterne delingsfunktioner i Microsoft 365 giver personer i organisationen mulighed for at samarbejde med partnere, leverandører, kunder og andre, der ikke har en konto i kataloget. Du kan dele hele teams, kanaler eller websteder med personer uden for organisationen eller blot individuelle filer.

Samarbejde med personer uden for organisationen består af disse overordnede komponenter:

- **Aktivér** deling – Konfigurer kontrolelementerne for deling på tværs af Azure Active Directory, Teams, Microsoft 365 Groups og SharePoint for at tillade det niveau af deling, du ønsker for organisationen.
- **Konfigurer organisationsrelationer** – Hvis du bruger delte kanaler, skal du konfigurere adgangsindstillinger for flere lejere i Azure Active Directory for at tillade B2B direkte forbindelsesadgang for hver organisation, du vil samarbejde med. (Disse organisationer skal også konfigurere organisationsrelationer med din lejer).
- **Aktivér** ekstra sikkerhed – Mens de grundlæggende delingsfunktioner kan konfigureres til at kræve, at personer uden for organisationen skal godkendes, indeholder Microsoft 365 mange ekstra funktioner til sikkerhed og overholdelse, som kan hjælpe dig med at beskytte dine data og vedligeholde dine styringspolitikker, mens du deler eksternt.

Læs [Konfigurer sikkert samarbejde med Microsoft 365 og Microsoft Teams](/microsoft-365/solutions/setup-secure-collaboration-with-teams) for at få mere at vide om, hvordan eksterne deling bindinger med den overordnede Microsoft 365 samarbejdsvejledning.

## <a name="enable-sharing"></a>Aktivér deling

Som standard er deling med personer uden for organisationen ved hjælp af gæsteadgang eller anonym adgang aktiveret, men delte kanaler skal være aktiveret ved at konfigurere organisationsrelationer i Azure AD. De fleste scenarier for gæstedeling fungerer uden yderligere konfiguration. Hvis du vil bekræfte indstillingerne for et scenarie, du bruger, eller aktivere et nyt, skal du vælge mellem følgende indstillinger:

- [Samarbejde om dokumenter](collaborate-on-documents.md) – Få mere at vide om, hvordan du konfigurerer Microsoft 365 til at tillade deling og samarbejde med personer uden for organisationen (både gæster og ikke-godkendte brugere) om filer og mapper.
- [Samarbejd på et websted –](collaborate-in-site.md) Få mere at vide om, hvordan du konfigurerer Microsoft 365 at aktivere deling SharePoint websteder med gæster.
- [Samarbejd som et team](collaborate-as-team.md) – Lær, hvordan du konfigurerer Microsoft 365 for at aktivere gæstesamarbejde Teams.
- [Samarbejd med eksterne deltagere i en kanal](/microsoft-365/solutions/collaborate-teams-direct-connect) for at samarbejde med personer uden for organisationen i en delt kanal.

Du kan finde et nærmere overblik over de indstillinger for gæstedeling, der er tilgængelige Microsoft 365, [Microsoft 365 reference til indstillinger for gæstedeling](microsoft-365-guest-settings.md).

## <a name="enable-additional-security"></a>Aktivér ekstra sikkerhed

Når du har aktiveret det scenarie, du vil bruge til deling med personer uden for organisationen, kan du overveje yderligere sikkerhedsforanstaltninger for at beskytte dit indhold mod utilsigtet eller bevidst upassende deling.

- [Bedste praksis for deling af filer og mapper](best-practices-anonymous-sharing.md) med ikke-godkendte brugere – Få mere at vide om de bedste fremgangsmåder for deling med ikke-godkendte brugere.
- [Begræns](share-limit-accidental-exposure.md) utilsigtet eksponering – Få mere at vide om, hvordan du reducerer risikoen for utilsigtet deling af følsomt indhold med personer uden for organisationen.
- [Opret et sikkert](create-secure-guest-sharing-environment.md) miljø til gæstedeling – Få mere at vide om de værktøjer, der findes i Microsoft 365 for at sikre, at deling med personer uden for organisationen udføres på en sikker måde og opfylder dine styringskrav.

## <a name="collaborate-with-partner-companies"></a>Samarbejd med partnervirksomheder

Når du arbejder på et stort projekt, der involverer gæster fra en anden organisation, bør du overveje delte kanaler. Da delte kanaler ikke bruger gæstekonti, kan brugerne i den anden organisation få direkte adgang til den delte kanal uden at skulle logge på din organisation separat.

Hvis du har en igangværende leverandørrelation, hvor gæster ofte ændrer sig, kan du bruge rettighedsstyring i Azure Active Directory til at forenkle gæsteadministration og tillade partnerfirmaet at dele det pågældende ansvar. Se [Opret et B2B-ekstranet med administrerede gæster](b2b-extranet.md) for at få flere oplysninger.

## <a name="limit-sharing"></a>Begræns deling

Hvis nogle af delingsfunktionerne i Microsoft 365 konflikt med dine styringspolitikker, kan du se Begræns deling [i Microsoft 365](microsoft-365-limit-sharing.md) for at få mere at vide om muligheder for at begrænse deling.

## <a name="related-topics"></a>Relaterede emner

[Introduktion til filsamarbejde i Microsoft 365](/sharepoint/intro-to-file-collaboration)

[Planlæg filsamarbejde SharePoint med Microsoft 365](/sharepoint/deploy-file-collaboration)
