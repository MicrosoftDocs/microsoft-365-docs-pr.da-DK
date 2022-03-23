---
title: Insider-skabeloner til risikostyringsmeddelelse
description: Få mere at vide om insider-meddelelser om risikostyring i Microsoft 365
keywords: Microsoft 365, insider-risikostyring, risikostyring, overholdelse af regler og standarder
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: cfa9628861e592b1e8cf235fe5c68e538be354ba
ms.sourcegitcommit: efb333ce0772265da91632110acba39acfbe0bde
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 12/01/2021
ms.locfileid: "63588764"
---
# <a name="insider-risk-management-notice-templates"></a>Insider-skabeloner til risikostyringsmeddelelse

Insider-skabeloner til risikostyringsmeddelelser giver dig mulighed for automatisk at sende mails til brugere, når der oprettes en sag for aktiviteter, der har genereret et politikmatch og bekræftet advarsel. For de fleste beskeder, der genererer tilfælde, er brugerhandlinger resultatet af fejl eller utilsigtede aktiviteter uden dårlige hensigter. Meddelelser fungerer som enkle påmindelser til brugerne om at være mere forsigtige, til at vise links til oplysninger om oplæring i opdatering eller til virksomhedens politikressourcer. Meddelelser kan være en vigtig del af dit interne kursusprogram til overholdelse af regler og standarder og kan hjælpe med at oprette en dokumenteret revisionslog til brugere med tilbagevendende risikoaktiviteter.

Opret meddelelsesskabeloner, hvis du vil sende brugere en påmindelse via mail for politik matches som en del af sagsløsningsprocessen. Meddelelser kan kun sendes til den brugermailadresse, der er knyttet til den specifikke sag, der gennemgås. Når du vælger en meddelelsesskabelon, der skal anvendes på et politik match, kan du vælge at acceptere feltværdierne, der er defineret i skabelonen, eller overskrive felterne efter behov

## <a name="notice-templates-dashboard"></a>Meddelelsesskabeloner til dashboard

**Dashboardet i meddelelsesskabeloner** viser en liste over konfigurerede meddelelsesskabeloner og giver dig mulighed for at oprette nye meddelelsesskabeloner. Meddelelsesskabelonerne er angivet i omvendt datorækkefølge med den seneste meddelelsesskabelon angivet først.

![Insider-skabelon til risikostyringsmeddelelses-dashboard.](../media/insider-risk-notices-dashboard.png)

## <a name="html-for-notices"></a>HTML til meddelelser

Hvis du vil oprette mere end en enkel tekstbaseret mail til meddelelser, kan du oprette en mere detaljeret meddelelse ved hjælp af HTML i meddelelsesfeltet i en meddelelsesskabelon. Følgende eksempel indeholder brødtekstformatet til en grundlæggende HTML-baseret mailmeddelelsesskabelon:

```HTML
<!DOCTYPE html>
<html>
<body>
<h2>Action Required: Contoso User Code of Conduct Policy Training</h2>
<p>A recent activity you've performed has generated a risk alert prohibited by the Contoso User <a href='https://www.contoso.com'>Code of Conduct Policy</a>.</p>
<p>You are required to attend the Contoso User Code of Conduct <a href='https://www.contoso.com'>training</a> within the next 14 days. Please contact <a href='mailto:hr@contoso.com'>Human Resources</a> with any questions about this training request.</p>
<p>Thank you,</p>
<p><em>Human Resources</em></p>
</body>
</html>
```

> [!NOTE]
> Implementering af HTML-attributten href i skabelonerne til insider-risikostyringsmeddelelsen understøtter i øjeblikket kun enkelte anførselstegn i stedet for dobbelte anførselstegn for URL-referencer.

## <a name="create-a-new-notice-template"></a>Opret en ny meddelelsesskabelon

Hvis du vil oprette en ny skabelon til meddelelser om insider-risikostyring, skal du bruge værktøjet til  oprettelse af meddelelser i Insider-risikostyringsløsningen Microsoft 365 Overholdelsescenter.

Udfør følgende trin for at oprette en ny skabelon til en meddelelse om insider-risikostyring:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring og** vælge fanen **Meddelelsesskabeloner**.
2. Vælg **Opret meddelelsesskabelon for** at åbne værktøjet til oprettelse af meddelelser.
3. På siden **Opret en ny meddelelsesskabelon** skal du udfylde følgende felter:
    - **Skabelonnavn**: Angiv et brugervenligt navn til meddelelsen. Dette navn vises på listen over meddelelser på dashboardet til meddelelser og på listen over valg af meddelelser, når der sendes meddelelser fra en sag.
    - **Send fra**: Angiv afsendermailadressen for meddelelsen. Denne adresse vises i feltet Fra **: i alle** meddelelser, der sendes til brugere, medmindre det ændres, når der sendes en meddelelse fra en sag.
    - **Felterne Cc og Bcc** : Valgfrie brugere eller grupper, der skal underrettes om matchet af politikker, som vælges i Active Directory til dit abonnement.
    - **Emne**: Oplysninger, der vises i meddelelsens emnelinje, understøtter teksttegn.
    - **Meddelelsestekst**: Oplysninger, der vises i brødteksten, understøtter tekst- eller HTML-værdier.
4. Vælg **Opret for** at oprette og gemme meddelelsesskabelonen, eller vælg **Annuller** for at lukke uden at gemme meddelelsesskabelonen.

## <a name="update-a-notice-template"></a>Opdatere en meddelelsesskabelon

Hvis du vil opdatere en eksisterende skabelon for insider-risikostyring, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring og** vælge fanen **Meddelelsesskabeloner**.
2. På dashboardet til meddelelser skal du vælge den meddelelsesskabelon, du vil administrere.
3. På siden med meddelelsesoplysninger skal du vælge **Rediger**
4. På **siden Rediger** kan du redigere følgende felter:
    - **Skabelonnavn**: Angiv et nyt brugervenligt navn til meddelelsen. Dette navn vises på listen over meddelelser på dashboardet til meddelelser og på listen over valg af meddelelser, når der sendes meddelelser fra en sag.
    - **Send fra**: Opdater afsenderens mailadresse til meddelelsen. Denne adresse vises i feltet Fra **: i alle** meddelelser, der sendes til brugere, medmindre det ændres, når der sendes en meddelelse fra en sag.
    - **Felterne Cc og Bcc** : Opdater valgfrie brugere eller grupper, der skal underrettes om matchet af politikker, som vælges i Active Directory for dit abonnement.
    - **Emne**: Opdater de oplysninger, der vises i meddelelsens emnelinje, understøtter teksttegn.
    - **Meddelelsestekst**: Opdateringsoplysninger, der vises i brødteksten, understøtter tekst- eller HTML-værdier.
5. Vælg **Gem for** at opdatere og gemme meddelelsen, eller vælg **Annuller** for at lukke uden at gemme meddelelsesskabelonen.

## <a name="delete-a-notice-template"></a>Slet en meddelelsesskabelon

Hvis du vil slette en eksisterende skabelon til insider-risikostyring, skal du udføre følgende trin:

1. I [Microsoft 365 Overholdelsescenter du](https://compliance.microsoft.com) gå til **Insider-risikostyring og** vælge fanen **Meddelelsesskabeloner**.
2. Vælg den meddelelsesskabelon, du vil slette, på dashboardet for meddelelser.
3. Vælg **ikonet** Slet på værktøjslinjen.
4. Hvis du vil slette meddelelsesskabelonen, **skal du** vælge Ja i dialogboksen Slet. Hvis du vil annullere sletningen, skal du vælge **Annuller**.
