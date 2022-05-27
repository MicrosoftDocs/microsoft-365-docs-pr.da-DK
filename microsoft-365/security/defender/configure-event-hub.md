---
title: Konfigurer dine Event Hubs
description: Få mere at vide om, hvordan du konfigurerer dine Event Hubs
keywords: hændelseshub, konfigurere, indsigt
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
MS.technology: mde
ms.openlocfilehash: 569f51eda2f2ee61286c661548fe73e793928294
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754836"
---
# <a name="configure-your-event-hubs"></a>Konfigurer dine Event Hubs

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Få mere at vide om, hvordan du konfigurerer dine Event Hubs, så den kan overføre hændelser fra Microsoft 365 Defender.

## <a name="set-up-the-required-resource-provider-in-the-event-hubs-subscription"></a>Konfigurer den påkrævede ressourceudbyder i Event Hubs-abonnementet

1. Log på portalen[Azure](https://portal.azure.com).
1. Vælg **Abonnementer** > **{ Vælg det abonnement, som hændelseshubben udrulles til }** > **Ressourceudbydere**.
1. Kontrollér, om **Microsoft.Insights** Provideren er registreret. Ellers skal du registrere den.

:::image type="content" source="../../media/f893db7a7b1f7aa520e8b9257cc72562.png" alt-text="Listen over tjenesteudbydere på Microsoft Azure-portalen" lightbox="../../media/f893db7a7b1f7aa520e8b9257cc72562.png":::

## <a name="set-up-azure-active-directory-app-registration"></a>Konfigurer Azure Active Directory appregistrering

> [!NOTE]
> Du skal have administratorrollen, eller Azure Active Directory (AAD) skal være angivet, for at ikke-administratorer kan registrere apps. Du skal også have rollen Ejer eller Administrator af brugeradgang for at tildele tjenesteprincipalen en rolle. Du kan få flere oplysninger under [Opret en Azure AD app & tjenesteprincipal på portalen – Microsoft-identitetsplatform \| Microsoft Docs](/azure/active-directory/develop/howto-create-service-principal-portal).

1. Opret en ny registrering (som i sagens natur opretter en tjenesteprincipal) i **Azure Active Directory** \> **Appregistreringer** \> **Ny registrering.**

1. Udfyld formularen med navnet (der kræves ingen omdirigerings-URI).

    :::image type="content" source="../../media/336bc84e6be23900c43232b4ef0c253c.png" alt-text="Den viste sektion for programnavn på Microsoft Azure-portalen" lightbox="../../media/336bc84e6be23900c43232b4ef0c253c.png":::


    :::image type="content" source="../../media/06ac04c4ff713c2065cec2ef2f99a294.png" alt-text="Afsnittet Oversigtsoplysninger på portalen Microsoft Azure" lightbox="../../media/06ac04c4ff713c2065cec2ef2f99a294.png":::

1. Opret en hemmelighed ved at klikke på **Certifikater & hemmeligheder** \> **Ny klienthemmelighed**:

    :::image type="content" source="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png" alt-text="Sektionen Klienthemmelighed på Microsoft Azure-portalen" lightbox="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png":::

Denne værdi for klienthemmelighed bruges af Microsoft Graph API'er til at godkende det program, der registreres.

> [!WARNING]
> **Du kan ikke få adgang til klienthemmeligheden igen, så sørg for at gemme den**.

## <a name="set-up-event-hubs-namespace"></a>Konfigurer Event Hubs-navneområdet

1. Opret et Event Hubs-navneområde:

    Gå **til Event Hub \> Tilføj** , og vælg prisniveauet, gennemløbsenhederne og Automatisk oppumpning (kræver standardpriser og under funktioner), der passer til den belastning, du forventer. Du kan finde flere oplysninger under [Prisfastsættelse – Event Hubs \| Microsoft Azure](https://azure.microsoft.com/pricing/details/event-hubs/).

    > [!NOTE]
    > Du kan bruge en eksisterende hændelseshub, men dataoverførselshastigheden og skaleringen er angivet på navneområdeniveau, så det anbefales at placere en hændelseshub i sit eget navneområde.

   :::image type="content" source="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png" alt-text="Sektionen hændelseshubber på Microsoft Azure-portalen" lightbox="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png":::

1. Du skal også bruge ressource-id'et for dette Event Hubs-navneområde. Gå til siden \> Egenskaber for azure Event Hubs-navneområde. Kopiér teksten under Ressource-id, og registrer den til brug i afsnittet konfiguration af Microsoft 365 nedenfor.

    :::image type="content" source="../../media/759498162a4e93cbf17c4130d704d164.png" alt-text="Afsnittet med egenskaber for hændelseshubber på Microsoft Azure-portalen" lightbox="../../media/759498162a4e93cbf17c4130d704d164.png":::

### <a name="add-permissions"></a>Tilføj tilladelser

Du skal føje tilladelser til følgende roller til enheder, der er involveret i Event Hubs-dataadministration:

- **Bidragyder**: De tilladelser, der er relateret til denne rolle, føjes til det objekt, der logger på Microsoft 365 Defender portalen.
- **Læser**- og **Azure Event Hub-datamodtager**: De tilladelser, der er relateret til disse roller, tildeles til den enhed, der allerede har fået tildelt rollen som **tjenesteprincipal**, og logger på Azure Active Directory-programmet.

Udfør følgende trin for at sikre, at disse roller er blevet tilføjet:

Gå til **Event Hub Namespace** \> **Access Control (IAM)** \> **Tilføj** og bekræft under **Rolletildelinger**.

:::image type="content" source="../../media/9c9c29137b90d5858920202d87680d16.png" alt-text="Et afsnit med tjenesteprincipalen til programregistrering på Microsoft Azure-portalen" lightbox="../../media/9c9c29137b90d5858920202d87680d16.png":::

## <a name="set-up-event-hubs"></a>Konfigurer Event Hubs

**Mulighed 1:**

Du kan oprette en Event Hubs i dit navneområde, og **alle** de hændelsestyper (tabeller), du vælger at eksportere, skrives til denne **hændelseshub** .

**Mulighed 2:**

I stedet for at eksportere alle hændelsestyper (tabeller) til én Event Hub kan du eksportere hver tabel til forskellige Event Hubs i dit Event Hubs Namespace (én Event Hub pr. Hændelsestype).

I denne indstilling opretter Microsoft 365 Defender Event Hubs for dig.

> [!NOTE]
> Hvis du bruger et Event Hub Namespace, der **ikke** er en del af en Event Hub Cluster, kan du kun vælge op til 10 hændelsestyper (tabeller) til eksport i hvert Eksportér Indstillinger, du definerer, på grund af en Azure-begrænsning på 10 Event Hub pr. Event Hub Namespace.

Eksempel:

:::image type="content" source="../../media/005c1f6c10c34420d387f594987f9ffe.png" alt-text="Et afsnit med hændelseshubber på Microsoft Azure-portalen" lightbox="../../media/005c1f6c10c34420d387f594987f9ffe.png":::

Hvis du vælger denne indstilling, kan du springe til afsnittet [Konfigurer Microsoft 365 Defender til at sende mailtabeller](#configure-microsoft-365-defender-to-send-email-tables).

Opret Event Hubs i dit navneområde ved at vælge **Event Hub** \> **+ Event Hub**.

Partitionsantallet giver mulighed for flere dataoverførselshastigheder via parallelitet, så det anbefales at øge dette tal baseret på den belastning, du forventer. Standardværdier for opbevaring og hentning af meddelelser på 1 og Fra anbefales.

:::image type="content" source="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png" alt-text="Et afsnit til oprettelse af hændelseshubber på Microsoft Azure-portalen" lightbox="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png":::

For disse Event Hubs (ikke navneområde) skal du konfigurere en delt adgangspolitik med Send, Lyttekrav. Klik på dine **politikker for delt adgang til** \> **Event Hub** \> **+ Tilføj**, og giv den derefter et politiknavn (bruges ikke et andet sted), og markér **Send** og **lyt**.

:::image type="content" source="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png" alt-text="Siden Politikker for delt adgang på portalen Microsoft Azure" lightbox="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png":::

## <a name="configure-microsoft-365-defender-to-send-email-tables"></a>Konfigurer Microsoft 365 Defender til at sende mailtabeller

### <a name="set-up-microsoft-365-defender-send-email-tables-to-splunk-via-event-hubs"></a>Konfigurer Microsoft 365 Defender sende mailtabeller til Splunk via Event Hubs

1. Log på for at <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> med en konto, der opfylder alle følgende rollekrav:

    - Rolle som bidragyder på Ressourceniveau for Event Hubs *Namespace* eller højere for de Event Hubs, du eksporterer til. Uden denne tilladelse får du vist en eksportfejl, når du forsøger at gemme indstillingerne.

    - Global Administration- eller sikkerhedsrolle Administration rolle i den lejer, der er knyttet til Microsoft 365 Defender og Azure.

      :::image type="content" source="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png" alt-text="Indstillinger-siden på Microsoft 365 Defender-portalen" lightbox="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png":::

1. Klik på **Rå dataeksport \> +Tilføj**.

    Du skal nu bruge de data, du har optaget ovenfor.

    **Navn**: Denne værdi er lokal og bør være, hvad der fungerer i dit miljø.

    **Videresend hændelser til hændelseshub**: Markér dette afkrydsningsfelt.

    **Event-Hub-ressource-id**: Denne værdi er det Event Hubs Namespace-ressource-id, du registrerede, da du konfigurerede Event Hubs.

    **Event-Hub-navn**: Hvis du har oprettet en Event Hubs i dit Event Hubs-navneområde, skal du indsætte det Event Hubs-navn, du har registreret ovenfor.

    Hvis du vælger at lade Microsoft 365 Defender oprette Event Hubs pr. hændelsestyper (tabeller) for dig, skal du lade feltet være tomt.

    **Hændelsestyper**: Vælg de avancerede jagttabeller, du vil videresende til Event Hubs og derefter videre til din brugerdefinerede app. Beskedtabeller er fra Microsoft 365 Defender, enhedstabeller er fra Microsoft Defender for Endpoint (Slutpunktsregistrering og -svar), og mailtabeller er fra Microsoft Defender for Office 365. Mailhændelser registrerer alle mailtransaktioner. URL-adressen (Pengeskab Links), Vedhæftet fil (Pengeskab vedhæftede filer) og ZAP (Post Delivery Events) registreres også og kan føjes til mailhændelser i feltet NetworkMessageId.

    :::image type="content" source="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png" alt-text="Siden med indstillinger for streaming-API'en på Microsoft Azure-portalen" lightbox="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png":::

1. Sørg for at klikke på **Send**.

### <a name="verify-that-the-events-are-being-exported-to-the-event-hubs"></a>Kontrollér, at hændelserne eksporteres til Event Hubs

Du kan bekræfte, at hændelser sendes til Event Hubs ved at køre en grundlæggende avanceret jagtforespørgsel. Vælg **Avanceret** \> **jagtforespørgsel,** \> og angiv følgende forespørgsel:

```console
EmailEvents
|joinkind=fullouterEmailAttachmentInfoonNetworkMessageId
|joinkind=fullouterEmailUrlInfoonNetworkMessageId
|joinkind=fullouterEmailPostDeliveryEventsonNetworkMessageId
|whereTimestamp\>ago(1h)
|count
```

Denne forespørgsel viser dig, hvor mange mails der blev modtaget i løbet af den sidste time, der blev joinforbundet på tværs af alle de andre tabeller. Du får også vist, hvis du får vist hændelser, der kan eksporteres til hændelseshubben. Hvis dette antal viser 0, kan du ikke se nogen data, der går ud til Event Hubs.

:::image type="content" source="../../media/c305e57dc6f72fa9eb035943f244738e.png" alt-text="Den avancerede jagtside på Microsoft Azure-portalen" lightbox="../../media/c305e57dc6f72fa9eb035943f244738e.png":::

Når du har bekræftet, at der er data at eksportere, kan du få vist siden Event Hubs for at bekræfte, at meddelelser er indgående. Denne proces kan tage op til én time.

1. I Azure skal du gå til **Event Hub** \> Klik på **navneområdet** \> **Event Hub** \> Klik på **Event Hub**.
1. Under **Oversigt** skal du rulle ned og i grafen Meddelelser kan du se Indgående meddelelser. Hvis du ikke kan se nogen resultater, er der ingen meddelelser til din brugerdefinerede app til indfødning.

:::image type="content" source="../../media/e88060e315d76e74269a3fc866df047f.png" alt-text="Siden Oversigt i Microsoft 365 Azure Portal" lightbox="../../media/e88060e315d76e74269a3fc866df047f.png":::
