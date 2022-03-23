---
title: Konfigurer en forbindelse til at arkivere LinkedIn-data
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Lær, hvordan administratorer kan konfigurere & bruge en oprindelig forbindelse til at importere data fra en LinkedIn-firmaside for at Microsoft 365.
ms.openlocfilehash: 944a8bcbd06a07653ccf5e98e28807d279b66023
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63587894"
---
# <a name="set-up-a-connector-to-archive-linkedin-data"></a>Konfigurer en forbindelse til at arkivere LinkedIn-data

Brug en forbindelse på Microsoft 365 Overholdelsescenter til at importere og arkivere data fra sider af virksomheden LinkedIn. Når du konfigurerer en forbindelse, oprettes der forbindelse til kontoen for den specifikke LinkedIn-firmaside én gang hver 24 timer. Forbindelsen konverterer de meddelelser, der er sendt til siden Firma, til en mail og importerer derefter disse elementer til en postkasse Microsoft 365.

Når linkedIn Company-sidedataene er gemt i en postkasse, kan du anvende Microsoft 365-overholdelsesfunktioner som f.eks Retslig tilbageholdelse, Indholdssøgning, In-Place Arkivering, Overvågning og Microsoft 365-opbevaringspolitikker til LinkedIn-data. Du kan f.eks. søge efter disse elementer ved hjælp af Indholdssøgning eller knytte lagerpostkassen til en assistent, der er i Advanced eDiscovery tilfælde. Oprettelse af en forbindelseskomponent til at importere og arkivere LinkedIn-data i Microsoft 365 kan hjælpe din organisation med at overholde offentlige og lovmæssige politikker.

## <a name="before-you-set-up-a-connector"></a>Før du konfigurerer en forbindelse

- Den bruger, der opretter en LinkedIn-firmasideforbindelse, skal have tildelt rollen som dataforbindelsesadministrator. Denne rolle er påkrævet for at tilføje forbindelser **på siden Dataforbindelser** i Microsoft 365 Overholdelsescenter. Denne rolle er som standard føjet til flere rollegrupper. Du kan finde en liste over disse rollegrupper i afsnittet "Roller i sikkerheds- og overholdelsescenter" i Tilladelser i [& Compliance Center](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternativt kan en administrator i organisationen oprette en brugerdefineret rollegruppe, tildele rollen Dataforbindelsesadministrator og derefter tilføje de relevante brugere som medlemmer. Du kan finde en vejledning i afsnittet "Opret en brugerdefineret rollegruppe" under [Tilladelser i Microsoft 365 Overholdelsescenter](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Du skal have logonoplysninger (mailadresse eller telefonnummer og adgangskode) til en LinkedIn-brugerkonto, som er administrator for den LinkedIn-firmaside, du vil arkivere. Du bruger disse legitimationsoplysninger til at logge på LinkedIn, når du konfigurerer forbindelsen.

- LinkedIn-forbindelsen kan importere i alt 200.000 elementer på en enkelt dag. Hvis der er mere end 200.000 LinkedIn-elementer på en dag, importeres ingen af disse elementer til Microsoft 365.

## <a name="create-a-linkedin-connector"></a>Opret en LinkedIn-forbindelse

1. Gå til og <https://compliance.microsoft.com> klik derefter **på sider med** **DataforbindelserLinkedIn** >  Company.

2. Klik på **Tilføj forbindelse på produktsiden** for LinkedIn-firmasiderne.

3. På siden **Servicebetingelser skal** du vælge **Acceptér**.

4. På siden **Log på med LinkedIn** skal du klikke **på Log på med LinkedIn**.

   LinkedIn-logonsiden vises.

   ![LinkedIn-logonsiden.](../media/LinkedInSigninPage.png)

5. På LinkedIn-logonsiden skal du angive mailadressen (eller telefonnummeret) og adgangskoden til den LinkedIn-konto, der er knyttet til den firmaside, du vil arkivere, og derefter klikke på **Log på**.

   En side i guiden vises med en liste over alle LinkedIn-firmasider, der er knyttet til den konto, du er logget på. En forbindelse kan kun konfigureres til én firmaside. Hvis din organisation har flere LinkedIn-firmasider, skal du oprette en forbindelse for hver enkelt.

   ![Der vises en side med en liste over LinkedIn-firmasider.](../media/LinkedInSelectCompanyPage.png)

6. Vælg den firmaside, du vil arkivere elementer fra, og klik derefter på **Næste**.

7. På siden **Vælg lagerplacering** skal du klikke i feltet, vælge mailadressen til en Microsoft 365-postkasse, som LinkedIn-elementerne importeres til, og derefter klikke på **Næste**. Elementer importeres til indbakkemappen i denne postkasse.

8. Klik **på Næste** for at gennemgå forbindelsesindstillingerne, og klik derefter **på Udfør** for at fuldføre konfigurationen af forbindelsen.

Når du har oprettet forbindelsen, kan du gå tilbage til siden **Dataforbindelser** for at se status for importprocessen for den nye forbindelse (vælg Opdater, hvis  det er nødvendigt for at opdatere listen over forbindelser). Værdien i kolonnen **Status** er Venter **på at starte**. Det tager op til 24 timer, før den indledende importproces er startet. Efter den første gang forbindelsen kører og importerer LinkedIn-elementerne, kører forbindelsen én gang i døgnet og importerer alle nye elementer, der er oprettet på LinkedIn-firmasiden i de seneste 24 timer.

Hvis du vil have vist flere detaljer, skal du markere forbindelsen på listen **på siden Dataforbindelser** for at få vist pop op-siden. Under **Status** angiver det datointerval, der vises, det aldersfilter, der blev valgt, da forbindelsen blev oprettet.

## <a name="more-information"></a>Flere oplysninger

LinkedIn-elementer importeres til LinkedIn-undermappen i indbakken for lagerpostkassen Microsoft 365. De vises som mails.