---
title: Konfigurer din begivenhedshub
description: Få mere at vide om, hvordan du konfigurerer din begivenhedshub
keywords: begivenhedshub, konfigurer, indsigt
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
ms.openlocfilehash: a842f9161aa823203354917326653b583e5fddb9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754294"
---
# <a name="configure-your-event-hub"></a>Konfigurer din begivenhedshub

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Gælder for:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Få mere at vide om, hvordan du konfigurerer din Begivenhedshub, så den kan indtrænge begivenheder Microsoft 365 Defender.

## <a name="set-up-the-required-resource-provider-in-the-event-hub-subscription"></a>Konfigurere den påkrævede ressourceudbyder i abonnementet Hændelseshub

1. Log på portalen[Azure](https://portal.azure.com).
1. Vælg **Abonnementer** > **{ Vælg det abonnement, som begivenhedshubs installeres til }** > **Ressourceudbydere**.
1. Kontrollér, at **Microsoft.Insights** Udbyderen er registreret. Ellers skal du registrere den.

:::image type="content" source="../../media/f893db7a7b1f7aa520e8b9257cc72562.png" alt-text="Siden med liste over tjenesteudbydere i Microsoft Azure portal" lightbox="../../media/f893db7a7b1f7aa520e8b9257cc72562.png":::

## <a name="set-up-azure-active-directory-app-registration"></a>Konfigurer Azure Active Directory appregistrering

> ! [BEMÆRK] Du skal have administratorrolle eller Azure Active Directory (AAD) skal være indstillet til at tillade ikke-administratorer at registrere apps. Du skal også have en Ejer- eller Brugeradgangsadministrator-rolle for at tildele tjenesteinspektøren en rolle. Få mere at vide under [Opret en Azure AD-&-tjenesteinspektør på portalen – Microsoft-identitetsplatform \| Microsoft Docs](/azure/active-directory/develop/howto-create-service-principal-portal).

1. Opret en ny registrering (som indbygget opretter en tjenesteinspektør) i **Azure Active Directory** \> **Appregistreringer** \> **Ny registrering.**

1. Udfyld formularen kun med navnet (der kræves ingen Redirect URI).

    :::image type="content" source="../../media/336bc84e6be23900c43232b4ef0c253c.png" alt-text="Sektionen med programnavnet, der vises i Microsoft Azure portal" lightbox="../../media/336bc84e6be23900c43232b4ef0c253c.png":::


    :::image type="content" source="../../media/06ac04c4ff713c2065cec2ef2f99a294.png" alt-text="Afsnittet Oversigtsoplysninger i Microsoft Azure portal" lightbox="../../media/06ac04c4ff713c2065cec2ef2f99a294.png":::

1. Opret en hemmelighed ved at klikke **på Certifikater og & Ny** **klienthemmelighed**\>:

    :::image type="content" source="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png" alt-text="Sektionen Klienthemmelighed i Microsoft Azure portal" lightbox="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png":::
    

> [!WARNING]
> **Du vil ikke kunne få adgang til klienthemmelighederne igen, så sørg for at gemme den**.

## <a name="set-up-event-hub-namespace"></a>Konfigurere navneområde for hændelseshub

1. Opret et navneområde for begivenhedshub:

    Gå **til Begivenhedshub \>** Tilføj, og vælg prisniveau, overførselshastighedsenheder og automatisk opsnævning (kræver standardpriser og under funktioner), der er relevante for den belastning, du forventer. Få mere at vide under [Priser – Event Hub \| Microsoft Azure](https://azure.microsoft.com/pricing/details/event-hubs/)

    > [!NOTE]
    > Du kan bruge en eksisterende begivenhedshub, men overførselshastigheden og skaleringen er angivet på navneområdeniveau, så det anbefales at placere en begivenhedshub i sit eget navneområde.

   :::image type="content" source="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png" alt-text="Sektionen begivenhedshubs i Microsoft Azure portal" lightbox="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png":::

1. Du skal også bruge ressource-id'et for dette hændelseshubnavnområde. Gå til Azure Event Hub-navneområdesiden \> Egenskaber. Kopiér teksten under Ressource-id, og registrer den til brug Microsoft 365 sektionen Konfiguration nedenfor.

    :::image type="content" source="../../media/759498162a4e93cbf17c4130d704d164.png" alt-text="Sektionen med egenskaber for hændelseshubs i Microsoft Azure portal" lightbox="../../media/759498162a4e93cbf17c4130d704d164.png":::


1. Når Navneområde for hændelseshub er oprettet, skal du tilføje appregistreringstjenestens hovedstol som Læser, Azure Event Hub-datamodtager og den bruger, der logger på Microsoft 365 Defender som bidragyder (du kan også gøre dette på ressourcegruppe- eller abonnementsniveau).

    Du skal udføre dette trin **i Access Control** \> til Hændelseshub-navneområde **(IAM)** \> **Tilføj** og bekræft under **Rolletildelinger**:

    :::image type="content" source="../../media/9c9c29137b90d5858920202d87680d16.png" alt-text="Hovedsektionen for en programregistreringstjeneste på Microsoft Azure portal" lightbox="../../media/9c9c29137b90d5858920202d87680d16.png":::

## <a name="set-up-event-hub"></a>Konfigurer begivenhedshub

**Mulighed 1:**

Du kan oprette en Begivenhedshub i dit navneområde, og alle de hændelsestyper (tabeller), du vælger at eksportere, vil blive skrevet i denne **ene Begivenhedshub**.

**Mulighed 2:**

I stedet for at eksportere alle hændelsestyper (tabeller) til én hændelseshub kan du eksportere hver tabel til forskellige hændelseshub i begivenhedshubområdet (én hændelseshub pr. hændelsestype).

Med denne indstilling Microsoft 365 Defender Begivenhedshub for dig.

> [!NOTE]
> Hvis du bruger et Event Hub-navneområde, der  ikke er en del af en begivenhedshubklynge, kan du kun vælge op til 10 hændelsestyper (tabeller), der skal eksporteres, i hver eksport Indstillinger du definerer på grund af en Azure-begrænsning på 10 Hændelseshub pr. Event Hub-navneområde.

Eksempel:

:::image type="content" source="../../media/005c1f6c10c34420d387f594987f9ffe.png" alt-text="En begivenhedshubsektion i Microsoft Azure portal" lightbox="../../media/005c1f6c10c34420d387f594987f9ffe.png":::

Hvis du vælger denne indstilling, kan du gå til afsnittet [Konfigurer Microsoft 365 Defender at sende mailtabeller](#configure-microsoft-365-defender-to-send-email-tables).

Opret Begivenhedshub i dit navneområde ved at vælge **Hændelseshub** \> **+ Begivenhedshub**.

Partition Count giver mulighed for mere overførselshastighed via parallelitet, så det anbefales at øge dette tal baseret på den belastning, du forventer. Standardværdierne for Meddelelsesopbevaring og Registrer på 1 og Fra anbefales.

:::image type="content" source="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png" alt-text="En sektion til oprettelse af begivenhedshubs på Microsoft Azure portal" lightbox="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png":::
 

For disse Hændelseshub (ikke navneområde) skal du konfigurere en delt adgangspolitik med Send, Lyt krav. Klik på politikkerne **for Delt adgang** \> **i** \> begivenhedshubben **+** Tilføj, og giv den derefter et Politiknavn (bruges ikke et andet sted), og **markér Send** og **lyt**.

:::image type="content" source="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png" alt-text="Siden Politikker for delt adgang i Microsoft Azure portal" lightbox="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png":::

## <a name="configure-microsoft-365-defender-to-send-email-tables"></a>Konfigurere Microsoft 365 Defender til at sende mailtabeller

### <a name="set-up-microsoft-365-defender-send-email-tables-to-splunk-via-event-hub"></a>Konfigurere Microsoft 365 Defender sende mailtabeller til Splunk via Event Hub

1. Log <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">på Microsoft 365 Defender med</a> en konto, der opfylder alle følgende rollekrav:

    - Bidragyderrolle på Event *Hub-navneområderessourceniveau* eller højere for den hændelseshub, du skal eksportere til. Uden denne tilladelse får du en eksportfejl, når du forsøger at gemme indstillingerne.

    - Global administrator- eller sikkerhedsadministratorrolle på lejeren, der er bundet Microsoft 365 Defender og Azure.

      :::image type="content" source="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png" alt-text="Siden Indstillinger i Microsoft 365 Defender portalen" lightbox="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png":::

1. Klik på **Rå dataeksport \> + Tilføj**.

    Du skal nu bruge de data, du har registreret ovenfor.

    **Navn**: Denne værdi er lokal og bør være den, der fungerer i dit miljø.

    **Videresende begivenheder til begivenhedshub**: Markér dette afkrydsningsfelt.

    **Ressource-id for hændelseshub**: Denne værdi er det Hændelseshub-ressource-id, du registrerede, da du konfigurerede Hændelseshub.

    **Navn på begivenhedshub**: Hvis du har oprettet en begivenhedshub i begivenhedshubnavnet, skal du indsætte navnet på begivenhedshubben, du har registreret ovenfor.

    Hvis du vælger at lade en Microsoft 365 Defender oprette Begivenhedshub pr. hændelsestyper (tabeller) for dig, skal du lade dette felt være tomt.

    **Hændelsestyper**: Vælg tabellerne Avanceret jagt, som du vil videresende til Event Hub og derefter videre til din brugerdefinerede app. Påmindelsestabeller kommer Microsoft 365 Defender, enhederne er fra Microsoft Defender til slutpunkt (Slutpunktsregistrering og -svar), og mailtabeller er fra Microsoft Defender Office 365. Mailhændelser registrerer alle mailtransaktioner. URL-adressen (Pengeskab Links), vedhæftede filer (Pengeskab vedhæftede filer) og efter leveringshændelser (ZAP) optages også og kan sammenkædes med mailhændelser i feltet NetworkMessageId.

    :::image type="content" source="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png" alt-text="Siden med indstillinger for Streaming API i Microsoft Azure-portalen" lightbox="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png":::

1. Sørg for at klikke på **Send**.

### <a name="verify-that-the-events-are-being-exported-to-the-event-hub"></a>Kontrollér, at hændelserne eksporteres til hændelseshubben

Du kan kontrollere, at begivenheder sendes til Hændelseshub ved at køre en grundlæggende avanceret forespørgsel om en forespørgsel med avanceret forespørgsel. Vælg **På jagt** \> **efter avanceret** \> **forespørgsel** , og angiv følgende forespørgsel:

```console
EmailEvents
|joinkind=fullouterEmailAttachmentInfoonNetworkMessageId
|joinkind=fullouterEmailUrlInfoonNetworkMessageId
|joinkind=fullouterEmailPostDeliveryEventsonNetworkMessageId
|whereTimestamp\>ago(1h)
|count
```

Dette viser, hvor mange mails der blev modtaget i den sidste time sammenføjet på tværs af alle de andre tabeller. Den viser dig også, hvis du får vist hændelser, der kan eksporteres til begivenhedshubs. Hvis dette antal viser 0, vil du ikke se nogen data, der går ud til Hændelseshub.

:::image type="content" source="../../media/c305e57dc6f72fa9eb035943f244738e.png" alt-text="Den avancerede jagtside i Microsoft Azure portal" lightbox="../../media/c305e57dc6f72fa9eb035943f244738e.png":::

Når du har bekræftet, at der er data, der skal eksporteres, kan du få vist siden Hændelseshub for at bekræfte, at meddelelserne er indgående. Det kan tage op til en time.

1. I Azure skal du gå til **Hændelseshub** \> Klik på **navneområdets hændelseshub** \>  \> Klik på **Begivenhedshub**.
1. **Rul** ned i grafen Meddelelser under Oversigt, og se Indgående meddelelser. Hvis du ikke kan se nogen resultater, vil der ikke være nogen meddelelser om, at din brugerdefinerede app skal modtages.

:::image type="content" source="../../media/e88060e315d76e74269a3fc866df047f.png" alt-text="Siden Oversigt i Microsoft 365 Azure-portalen" lightbox="../../media/e88060e315d76e74269a3fc866df047f.png":::
