---
title: Skabeloner til insiderrisikostyringsmeddelelse
description: Få mere at vide om skabeloner til administration af insiderrisikostyring i Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, insiderrisiko, risikostyring, overholdelse af angivne standarder
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
ms.openlocfilehash: 7af1152d1393aaaf9eeb242c78b280cf0e9d80e6
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639792"
---
# <a name="insider-risk-management-notice-templates"></a>Skabeloner til insiderrisikostyringsmeddelelse

Skabeloner til insiderrisikostyring giver dig mulighed for automatisk at sende mails til brugerne, når der oprettes en sag for aktiviteter, der har genereret et politikmatch og en bekræftet besked. For de fleste beskeder, der genererer sager, er brugerhandlinger resultatet af fejl eller utilsigtede aktiviteter uden dårlig hensigt. Meddelelser fungerer som enkle påmindelser til brugerne om at være mere forsigtige, til at angive links til oplysninger til oplæring i opdatering eller til virksomhedens politikressourcer. Meddelelser kan være en vigtig del af dit interne oplæringsprogram til overholdelse af angivne standarder og kan hjælpe med at oprette et dokumenteret revisionsspor for brugere med tilbagevendende risikoaktiviteter.

Opret meddelelsesskabeloner, hvis du vil sende brugerne en påmindelse via mail for politikforekomster som en del af sagsløsningsprocessen. Meddelelser kan kun sendes til den brugermailadresse, der er knyttet til den specifikke sag, der gennemses. Når du vælger en meddelelsesskabelon, der skal anvendes på et politikmatch, kan du vælge at acceptere de feltværdier, der er defineret i skabelonen, eller overskrive felterne efter behov.

## <a name="notice-templates-dashboard"></a>Bemærk dashboard med skabeloner

**Dashboardet Meddelelsesskabeloner** viser en liste over konfigurerede meddelelsesskabeloner og giver dig mulighed for at oprette nye meddelelsesskabeloner. Meddelelsesskabelonerne vises i omvendt datorækkefølge, hvor den seneste meddelelsesskabelon er angivet først.

![Skabelondashboard til styring af insiderrisiko.](../media/insider-risk-notices-dashboard.png)

## <a name="html-for-notices"></a>HTML til meddelelser

Hvis du vil oprette mere end en simpel tekstbaseret mail til meddelelser, kan du oprette en mere detaljeret meddelelse ved hjælp af HTML i meddelelsesbrødtekstfeltet i en meddelelsesskabelon. I følgende eksempel vises meddelelsesbrødtekstformatet for en grundlæggende SKABELON til HTML-baseret mailmeddelelse:

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
> Implementeringen af HTML href-attributten i meddelelsesskabelonerne til styring af insiderrisiko understøtter i øjeblikket kun enkelte anførselstegn i stedet for dobbelte anførselstegn for URL-referencer.

## <a name="create-a-new-notice-template"></a>Opret en ny meddelelsesskabelon

Hvis du vil oprette en ny skabelon til insiderrisikostyring, skal du bruge meddelelsesoprettelsesværktøjet i **Insider-løsningen til styring af risici** i Microsoft Purview-compliance-portal.

Fuldfør følgende trin for at oprette en ny skabelon til styring af insiderrisiko:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Meddelelsesskabeloner**.
2. Vælg **Opret meddelelsesskabelon** for at åbne værktøjet til oprettelse af meddelelser.
3. Udfyld følgende felter på siden **Opret en ny meddelelsesskabelon** :
    - **Skabelonnavn**: Angiv et brugervenligt navn til meddelelsen. Dette navn vises på listen over meddelelser på meddelelsesdashboardet og på listen over valg af meddelelser, når der sendes meddelelser fra en sag.
    - **Send fra**: Angiv afsenderens mailadresse for meddelelsen. Denne adresse vises i feltet **Fra:** i alle meddelelser, der sendes til brugere, medmindre den ændres, når der sendes en meddelelse fra en sag.
    - **Felterne Cc og Bcc** : Valgfrie brugere eller grupper, der skal have besked om politikmatch, som er valgt i Active Directory for dit abonnement.
    - **Emne**: Oplysninger, der vises i meddelelsens emnelinje, understøtter teksttegn.
    - **Meddelelsesbrødtekst**: Oplysninger, der vises i meddelelsens brødtekst, understøtter tekst eller HTML-værdier.
4. Vælg **Opret** for at oprette og gemme meddelelsesskabelonen, eller vælg **Annuller** for at lukke uden at gemme meddelelsesskabelonen.

## <a name="update-a-notice-template"></a>Opdater en meddelelsesskabelon

Hvis du vil opdatere en eksisterende skabelon til insiderrisikostyring, skal du udføre følgende trin:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Meddelelsesskabeloner**.
2. Vælg den meddelelsesskabelon, du vil administrere, på meddelelsesdashboardet.
3. På siden med meddelelsesoplysninger skal du vælge **Rediger**
4. På siden **Rediger** kan du redigere følgende felter:
    - **Skabelonnavn**: Angiv et nyt brugervenligt navn til meddelelsen. Dette navn vises på listen over meddelelser på meddelelsesdashboardet og på listen over valg af meddelelser, når der sendes meddelelser fra en sag.
    - **Send fra**: Opdater afsenderens mailadresse for meddelelsen. Denne adresse vises i feltet **Fra:** i alle meddelelser, der sendes til brugere, medmindre den ændres, når der sendes en meddelelse fra en sag.
    - **Felterne Cc og Bcc** : Opdater valgfrie brugere eller grupper for at få besked om politikmatch, der er valgt i Active Directory for dit abonnement.
    - **Emne**: Opdater oplysninger, der vises i meddelelsens emnelinje, understøtter teksttegn.
    - **Meddelelsesbrødtekst**: Opdater oplysninger, der vises i meddelelsens brødtekst, understøtter tekst eller HTML-værdier.
5. Vælg **Gem** for at opdatere og gemme meddelelsen, eller vælg **Annuller** for at lukke uden at gemme meddelelsesskabelonen.

## <a name="delete-a-notice-template"></a>Slet en meddelelsesskabelon

Hvis du vil slette en eksisterende skabelon til insiderrisikostyring, skal du udføre følgende trin:

1. I [Microsoft Purview-compliance-portal](https://compliance.microsoft.com) skal du gå til **Styring af insiderrisiko** og vælge fanen **Meddelelsesskabeloner**.
2. Vælg den meddelelsesskabelon, du vil slette, på meddelelsesdashboardet.
3. Vælg ikonet **Slet** på værktøjslinjen.
4. Hvis du vil slette meddelelsesskabelonen, skal du vælge **Ja** i dialogboksen Slet. Hvis du vil annullere sletningen, skal du vælge **Annuller**.
