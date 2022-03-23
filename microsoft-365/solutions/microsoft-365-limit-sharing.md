---
title: Begræns deling i Microsoft 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
search.appverid:
- SPO160
- MET150
f1.keywords: NOCSH
ms.custom:
- admindeeplinkMAC
- admindeeplinkTEAMS
- admindeeplinkSPO
ms.localizationpriority: high
recommendations: false
description: Få mere at vide om indstillingerne for at begrænse eller deaktivere deling Microsoft 365.
ms.openlocfilehash: b2e327d5a5c670ada389a3dfceb2775e516ac2aa
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63590231"
---
# <a name="limit-sharing-in-microsoft-365"></a>Begræns deling i Microsoft 365

Du kan ikke deaktivere intern deling helt eller fjerne knappen Del fra websteder, men der er en række forskellige måder, hvorpå du kan begrænse deling i Microsoft 365, så den opfylder organisationens behov.

Metoderne til deling af filer er angivet i tabellen nedenfor. Klik på linket i kolonnen **Delingsmetode** for at få detaljerede oplysninger.

|Delingsmetode|Beskrivelse|Begrænse muligheder|
|:-------------|:----------|:-------------|
|[Microsoft 365 gruppe eller team](#microsoft-365-group-or-team)|Personer, der har fået adgang Microsoft Teams et team eller Microsoft 365 gruppe, har redigeringsadgang til filer på det tilknyttede SharePoint websted.|Hvis gruppen eller teamet er privat, sendes invitationer til deling om at deltage i teamet til ejeren med henblik på godkendelse. Administratorer kan deaktivere gæsteadgang eller bruge følsomhedsmærkater til at forhindre adgang for personer uden for organisationen.|
|[SharePoint websted](#sharepoint-site)|Personer kan tildeles ejer-, medlems- eller gæsteadgang til et SharePoint-websted og vil få adgang til filer på webstedet på dette niveau.|Webstedstilladelser kan begrænses, så kun webstedsejere kan dele webstedet. Administratorer kan indstille et websted til skrivebeskyttet eller blokere adgangen helt.|
|[Deling med bestemte personer](#sharing-with-specific-people)|Webstedets medlemmer og personer med redigeringstilladelser kan give direkte tilladelser til filer og mapper eller dele dem ved hjælp af links *til Bestemte* personer.|Webstedstilladelser kan begrænses, så kun webstedsejere kan dele filer og mapper. I dette tilfælde går direkte adgang og *linkdeling af* bestemte personer efter webstedsmedlemmer til webstedsejeren for at få godkendelse.|
|[SharePoint og OneDrive gæstedeling](#sharepoint-guest-sharing)|SharePoint webstedsejere og -OneDrive-ejere kan dele filer og mapper med personer uden for organisationen.|Gæstedeling kan deaktiveres for hele organisationen eller for individuelle websteder.|
|[*Personer i din organisation, som* deler links](#people-in-your-organization-sharing-links)|SharePoint webstedsejere og medlemmer kan dele filer ved hjælp *af links til* Personer i organisationen, som fungerer for alle i organisationen.|*Links i organisationen kan* deaktiveres på webstedsniveau.|
|[Opret websteder, grupper og teams](#create-sites-groups-and-teams)|Som standard kan brugerne oprette nye websteder, grupper og teams, hvorfra de kan dele indhold.|Administratorer kan begrænse, hvem der kan oprette websteder, grupper og teams.|
|[Mail](#email)|Personer med adgang til en fil kan sende den til andre via mail.|Administratorer kan kryptere filer ved hjælp af følsomhedsmærkater for at forhindre, at de deles med uautoriserede personer.|
|[Download eller filkopi](#download-or-file-copy)|Personer med adgang til en fil kan downloade eller kopiere den og dele den med andre uden for Microsoft 365.|Administratorer kan kryptere filer ved hjælp af følsomhedsmærkater for at forhindre, at de deles med uautoriserede personer.|

Du kan også begrænse de betingelser, som folk får adgang til delt indhold under. Se [betinget adgang senere](#conditional-access) i denne artikel for at få mere at vide.

Selvom du kan bruge de administratorkontrolelementer, der er beskrevet i denne artikel, til at begrænse deling i din organisation, anbefaler vi, at du overvejer at bruge de funktioner til sikkerhed og overholdelse, der er tilgængelige i Microsoft 365 til at oprette et sikkert delingsmiljø. Se [Filsamarbejde i SharePoint med Microsoft 365 og](/sharepoint/deploy-file-collaboration) [Konfigurer et team med sikkerhedsisolation](secure-teams-security-isolation.md) for at få flere oplysninger.

For at forstå, hvordan deling bruges i din organisation, skal [du køre en rapport om fil- og mappedeling](/sharepoint/sharing-reports).

## <a name="microsoft-365-group-or-team"></a>Microsoft 365 gruppe eller team

Hvis du vil begrænse deling i en Microsoft 365 gruppe eller Microsoft Teams team, er det vigtigt at gøre gruppen eller teamet privat. Personer i din organisation kan deltage i en offentlig gruppe eller et offentligt team når som helst. Medmindre gruppen eller teamet er privat, er det ikke muligt at begrænse delingen af teamet eller dets filer i organisationen.

### <a name="guest-sharing"></a>Gæstedeling

Hvis du vil forhindre gæsteadgang i Teams, kan du deaktivere gæstedeling i Teams Administration.

Sådan deaktiverer du gæstedeling for Teams
1. I administration Teams skal du udvide **fanen Indstillinger for hele** <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**organisationenGuest-adgang**</a> > .
2. Slå Tillad **gæsteadgang fra Teams**.
3. Klik på **Gem**.

Hvis du vil forhindre gæsteadgang i Microsoft 365 Grupper, kan du deaktivere indstillingerne for gæsteadgang for grupper i Microsoft 365 Administration.

Sådan deaktiverer du gæstedeling i Microsoft 365 Grupper
1. Klik Microsoft 365 Administration fanen **Indstillinger Microsoft 365 Administration** >  **Org Indstillinger** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2053743" target="_blank">**Services i dialogboksen** Side</a>.
2. Klik **Microsoft 365 Grupper**.
3. Fjern markeringen **i afkrydsningsfelterne Lad gruppemedlemmer uden** for organisationen få adgang til gruppeindhold og Lad gruppeejere føje **personer uden for organisationen til** grupper.
4. Klik på **Gem ændringer**.

    ![Skærmbillede af Microsoft 365 gruppedelingsindstillinger i Microsoft 365 Administration.](../media/office-365-groups-guest-settings-off.png)

> [!NOTE]
> Hvis du vil forhindre gæstedeling for en bestemt gruppe eller et bestemt team, kan du gøre det ved hjælp [af Microsoft PowerShell](per-group-guest-access.md) eller [følsomhedsmærkater](../compliance/sensitivity-labels-teams-groups-sites.md).

Du kan begrænse gæstedeling til brugere fra bestemte domæner ved at tillade eller blokere domæner i Azure Active Directory. Dette påvirker også gæstedeling i et SharePoint hvis du har aktiveret [SharePoint og OneDrive integration med Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview).

Sådan tillader du kun invitationer til deling fra bestemte domæner
1. I Azure Active Directory på siden Oversigt skal du klikke **på Organisationsrelationer**.
2. Klik **Indstillinger**.
3. Under **Begrænsninger for samarbejde** skal du vælge Afvisning **af invitationer** til de angivne domæner eller Tillad **kun invitationer** til de angivne domæner, og skriv derefter de domæner, du vil bruge.
4. Klik på **Gem**.

    ![Skærmbillede af indstillinger for begrænsninger for samarbejde i Azure Active Directory.](../media/azure-ad-allow-only-specified-domains.png)

## <a name="sharepoint-site"></a>SharePoint websted

Du kan begrænse SharePoint webstedsdeling til webstedsejere. Dette forhindrer webstedsmedlemmer i at dele webstedet. Husk på, at hvis webstedet har forbindelse til en Microsoft 365 gruppe, kan gruppemedlemmer invitere andre til gruppen, og disse brugere vil få adgang til webstedet.

Sådan begrænser du webstedsdeling til ejere
1. Klik på tandhjulsikonet på webstedet, og klik derefter **på Webstedstilladelser**.
2. Klik **på Skift indstillinger** for deling **under Indstillinger for deling**.
3. Vælg **Webstedsejere og -medlemmer, og personer med redigeringstilladelser kan dele filer og mapper, men det er kun webstedsejere, der kan dele webstedet**.
4. Klik på **Gem**.

    ![Skærmbillede af indstillinger for delingstilladelser i et SharePoint websted.](../media/sharepoint-site-sharing-permissions-level-two.png)

Du kan forhindre brugere, der ikke er medlemmer af webstedet, i at anmode om adgang ved at deaktivere anmodninger om adgang.

Sådan deaktiverer du adgangsanmodninger
1. Klik på tandhjulsikonet på webstedet, og klik derefter **på Webstedstilladelser**.
2. Klik **på Skift indstillinger** for deling **under Indstillinger for deling**.
3. Slå Tillad **anmodninger om adgang fra**, og klik derefter på **Gem**.

Du kan begrænse webstedsdeling til bestemte domæner ved at tillade eller blokere domæner for webstedet.

Sådan begrænser du webstedsdeling efter domæne

1. Vælg aktive SharePoint i **Administration** under <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Websteder**</a>.
2. Vælg det websted, du vil konfigurere.
3. På fanen **Politikker** under Ekstern **deling skal du** vælge **Rediger**.
4. Under **Avancerede indstillinger for ekstern deling skal** du vælge **Begræns deling efter domæne**.
5. Tilføj de domæner, du vil tillade eller blokere, og vælg derefter **Gem**.
6. Vælg **Gem**.

    ![Skærmbillede af indstillingen for tilladte domæner på webstedsniveau.](../media/limit-site-sharing-by-domain.png)

### <a name="block-access-to-a-site"></a>Bloker adgang til et websted

Du kan blokere adgangen til et websted eller gøre et websted skrivebeskyttet ved at ændre låsetilstanden for webstedet. Du kan få mere at vide [under Lås og lås op for websteder](/sharepoint/manage-lock-status).

### <a name="permissions-inheritance"></a>Nedarvning af tilladelser

Selvom det ikke anbefales, kan du SharePoint [nedarvning af tilladelser](/sharepoint/what-is-permissions-inheritance) til at tilpasse adgangsniveauer til websteder og underordnede websteder.

## <a name="sharing-with-specific-people"></a>Deling med bestemte personer

Hvis du vil begrænse delingen af et websted eller dets indhold, kan du konfigurere webstedet til kun at tillade, at webstedsejere deler filer, mapper og webstedet. Når denne konfiguration er konfigureret, vil webstedsmedlemmers forsøg på at dele filer eller mapper ved hjælp *af links til* Bestemte personer gå til webstedsejeren for at få godkendelse.

Sådan begrænser du websteds-, fil- og mappedeling til ejere
1. Klik på tandhjulsikonet på webstedet, og klik derefter **på Webstedstilladelser**.
2. Klik **på Skift indstillinger** for deling **under Indstillinger for deling**.
3. Vælg **Kun webstedsejere kan dele filer, mapper og webstedet**.
4. Klik på **Gem**.

    ![Skærmbillede af indstillinger for delingstilladelser i et SharePoint der er indstillet til kun ejere.](../media/sharepoint-site-only-site-owners-can-share.png)

## <a name="sharepoint-guest-sharing"></a>SharePoint gæstedeling

Hvis du vil forhindre deling af SharePoint- eller OneDrive-filer og -mapper med personer uden for organisationen, kan du deaktivere gæstedeling for hele organisationen eller for et enkelt websted.

Sådan deaktiverer SharePoint gæstedeling for organisationen

1. Vælg SharePoint i Administration **under** <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Politikker**</a>.
2. Under **Ekstern deling** skal du trække SharePoint ned til **Kun personer i organisationen**.
3. Vælg **Gem**.

    ![Skærmbillede af SharePoint indstillinger for deling på organisationsniveau, der er indstillet til Alle.](../media/sharepoint-tenant-sharing-off.png)


Sådan deaktiverer du gæstedeling for et websted
1. Vælg aktive SharePoint i **Administration** under <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Websteder**</a>.
2. Vælg det websted, du vil konfigurere.
3. På fanen **Politikker** under Ekstern **deling skal du** vælge **Rediger**.
4. Under **Ekstern deling** skal du **vælge Kun personer i organisationen** og derefter vælge **Gem**.

    ![Skærmbillede af SharePoint indstillinger for deling på webstedsniveau, der er indstillet til Kun personer i organisationen.](../media/sharepoint-site-external-sharing-settings-off.png)

Du kan deaktivere gæstedeling for en enkelt OneDrive ved at klikke på brugeren i Microsoft 365 Administration og vælge Administrer ekstern deling **på fanen OneDrive** brugere.

Hvis du vil tillade deling med personer uden for organisationen, men du vil sikre dig, at alle godkender, kan du deaktivere *Alle (anonym* deling)-links for hele organisationen eller for et enkelt websted.

Sådan deaktiverer *du alle* links på organisationsniveau

1. Vælg SharePoint i Administration **under** <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**Politikker**</a>.
2. Under **Ekstern deling** skal du trække SharePoint ned til **Nye og eksisterende gæster**.
3. Vælg **Gem**.

    ![Skærmbillede af SharePoint indstillinger for deling på organisationsniveau, der er indstillet til Nye og eksisterende gæster.](../media/sharepoint-guest-sharing-new-existing-guests.png)

Sådan deaktiverer du *alle* links for et websted

1. Vælg aktive SharePoint i **Administration** under <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Websteder**</a>.
2. Vælg det websted, du vil konfigurere.
3. På fanen **Politikker** under Ekstern **deling skal du** vælge **Rediger**.
4. Under **Ekstern deling** skal du **vælge Ny og eksisterende gæster** og derefter vælge **Gem**.

    ![Skærmbillede af SharePoint indstillinger for deling på webstedsniveau angivet til Nye og eksisterende indstillinger.](../media/sharepoint-site-external-sharing-settings-new-existing-guests.png)

## <a name="people-in-your-organization-sharing-links"></a>*Personer i din organisation, som* deler links

Som standard kan medlemmer af et websted dele filer og mapper med andre personer i organisationen ved hjælp af et *link til Personer i organisationen* . Du kan deaktivere *links til Personer i organisationen* ved hjælp af PowerShell:

```powershell
Set-SPOSite -Identity <site> -DisableCompanyWideSharingLinks Disabled
```

Eksempel:

```powershell
Set-SPOSite -Identity https://contoso.sharepoint.com -DisableCompanyWideSharingLinks Disabled
```

## <a name="create-sites-groups-and-teams"></a>Opret websteder, grupper og teams

Som standard kan brugerne oprette nye websteder, grupper og teams, hvorfra de kan dele indhold (afhængigt af dine indstillinger for deling). Du kan begrænse, hvem der kan oprette websteder, grupper og teams. Se følgende referencer:

- [Administrer oprettelse af websteder i SharePoint](/sharepoint/manage-site-creation)
- [Administrer, hvem der kan oprette Microsoft 365 grupper](./manage-creation-of-groups.md)

> [!NOTE]
> Begrænsning af gruppeoprettelse begrænser oprettelse af teams.

## <a name="email"></a>Mail

Du kan forhindre uønsket deling af mails ved hjælp af kryptering. Dette forhindrer, at mails videresendes eller på anden måde deles med uautoriserede brugere. Mailkryptering kan aktiveres ved hjælp af følsomhedsmærkater. Se [Begræns adgang til indhold ved hjælp af kryptering i følsomhedsmærkater](../compliance/encryption-sensitivity-labels.md) for at få flere oplysninger.

## <a name="download-or-file-copy"></a>Download eller filkopi

Brugere, der har adgang til filer og mapper i Microsoft 365, kan downloade filer og kopiere dem til eksterne medier. Du kan reducere risikoen for uønsket fildeling ved at kryptere indholdet ved hjælp af følsomhedsmærkater.

## <a name="conditional-access"></a>Betinget adgang

Azure Active Directory betinget adgang indeholder indstillinger til at begrænse eller forhindre deling med personer baseret på netværksplacering, enhedstilstand, logonrisici og andre faktorer. Se [Hvad er Betinget adgang?](/azure/active-directory/conditional-access/overview).

SharePoint direkte integration med betinget Azure AD-adgang for både ikke-administrerede enheder og netværksplacering. Se følgende referencer for at få mere at vide:

- [Kontrollere adgang fra enheder, der ikke er administrerede](/sharepoint/control-access-from-unmanaged-devices)
- [Kontrollere adgang til SharePoint og OneDrive baseret på netværksplacering](/sharepoint/control-access-based-on-network-location)

## <a name="see-also"></a>Se også

[Reference for Microsoft 365-gæstedelingsindstillinger](microsoft-365-guest-settings.md)
