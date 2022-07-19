---
title: Brug administratorloggen til dataconnectors til at få vist status for import af data
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: Få mere at vide om, hvordan du får adgang til og får vist administratorlogge for dataconnectors for at få statusoplysninger for de data, der importeres af connectoren.
ms.openlocfilehash: de8b1de56b5e44ad199db942c3d385dcc05e1160
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 05/11/2022
ms.locfileid: "66858510"
---
# <a name="view-admin-logs-for-data-connectors"></a>Få vist administratorlogge for dataconnectorer

Når du har oprettet en dataconnector til at importere ikke-Microsoft-data til Microsoft Purview, kan du overvåge den daglige importstatus for connectoren ved at downloade administratorlogfilerne for dataconnectoren.

> [!IMPORTANT]
> Overvågningslogføring skal være aktiveret, for at din organisation kan få vist administratorloggen. Den er som standard aktiveret for Microsoft 365 og Office 365 organisationer, men vi anbefaler på det kraftigste, at du bekræfter overvågningsstatus for din organisation. Klik her for at få en vejledning i at kontrollere overvågningsstatus. Klik her for at få en vejledning i, hvordan du slår overvågning til manuelt. Når overvågning er slået til, kan det tage op til 48 timer at logføre importhændelser. Det anbefales på det kraftigste, at du aktiverer overvågning, før en connector konfigureres. Når en connector er konfigureret, kan det tage op til 72 timer at generere logge, der indeholder en oversigt over importstatus.

## <a name="before-you-view-admin-logs"></a>Før du får vist administratorlogge

- Overvågning skal være aktiveret, for at din organisation kan oprette og få vist administratorlog for din organisation. Overvågning er som standard aktiveret i Microsoft Purview. Vi anbefaler dog, at du bekræfter overvågningsstatussen for din organisation. Du kan finde instruktioner under [Kontrollér overvågningsstatus for din organisation](turn-audit-log-search-on-or-off.md#verify-the-auditing-status-for-your-organization). Hvis du har brug for at aktivere overvågning for din organisation, skal du se [Slå overvågning](turn-audit-log-search-on-or-off.md#turn-on-auditing) til.

- Når overvågning er slået til, kan det tage op til 48 timer at generere administratorlogge for dataconnectors. Vi anbefaler, at du aktiverer overvågning, før du opretter dataconnectors.

- Når en dataconnector er oprettet, kan det tage op til 72 timer at generere administratorlogge, der indeholder en oversigt over importstatus.

- Administration logge er tilgængelige for de seneste syv dage.

## <a name="download-admin-logs-for-data-connectors"></a>Download administratorlogge for dataconnectors

1. Gå til , <https://compliance.microsoft.com/> og klik derefter på **Dataconnectors**.

2. Klik på fanen **Mine forbindelser,** og vælg derefter en dataconnector for at få vist siden Fly out, som indeholder oplysninger og egenskaber om dataconnectoren.

3. Under **Administration logge** skal du klikke på linket **Downloadlog** for at åbne en administratorlog.

   ![Administratorlogge, der vises på dataconnectorens pop op-side.](..\media\Data-connector-admin-logs1.png)

4. Få vist følgende importstatusoplysninger i administratorloggen:

    - **Importfuldførelsestid**: Tidsstempel (i UTC), når connectoren fuldfører import fra datakilde, og alle nedenstående hændelser beregnes/opdateres i forhold til importen.
    - **Tilgængelige elementer fra kilde**: Antal elementer, der blev downloadet af Connector fra datakilde.
    - **Elementer, der er tilgængelige for import**: antal elementer, der var tilgængelige til import af Connector efter fanout. Fanout repræsenterer den handling at skrive en meddelelse til alle tilknyttede deltagere (afsender, modtager osv.).
    - **Elementer blev importeret**: Antallet af elementer, der blev importeret korrekt af Connector i brugerpostkasser efter fanout.
    - **Elementer, der er delvist importeret**: Antallet af elementer, der blev importeret korrekt af Connector i brugerpostkasser efter fanout, men hvor vedhæftede filer blev droppet.
    - **Elementer blev sprunget over**: Antallet af elementer, der blev sprunget over, fra at blive importeret til brugerpostkasser efter fanout, fordi det var dubletelementer.
    - **Elementer mislykkedes**: Antallet af elementer, der ikke kunne importeres i brugerpostkasser efter fanout pga. fejl (f.eks. brugertilknytning, elementstørrelse er overskredet osv.). Hændelsen logføres én gang pr. bruger for brugertilknytningsfejl.

    > [!NOTE]
    > Elementer, der er tilgængelige for import, skal være en sum af elementer, der er importeret korrekt, delvist importeret, sprunget over og mislykkedes.

    - Oversigt over oplysninger om mislykket element:
      - **Element-id** – entydigt id for elementet
      - **Kildebruger-id** – bruger-id i kildeprogrammet
      - **M365-bruger-id** – brugerens hovednavn i M365
      - **Fejlårsag** – angiver årsagen til, hvorfor connectoren ikke kunne importere elementet

      Hvis der ikke er nogen elementer, der indtages på en bestemt dag, vises meddelelsen nedenfor i logfilen:

      Der er ingen elementer, der er blevet indtaget på datoen i *mm/dd/åååå*.

> [!NOTE]
> Hvis der ikke importeres nogen elementer på en bestemt dag, indeholder administratorloggen følgende meddelelse: `No items ingested on mm/dd/yyyy.`
