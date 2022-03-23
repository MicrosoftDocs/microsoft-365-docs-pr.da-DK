---
title: Brugersupport
description: Beskriver indstillingerne for kundeledet og partnerbaseret support.
keywords: Microsoft-administreret skrivebord, Microsoft 365, tjeneste, dokumentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 43b1addbf1b1d5e0d0134f80e4a90c420a4d6789
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 02/15/2022
ms.locfileid: "63592478"
---
# <a name="user-support"></a>Brugersupport

Dine Microsoft-administrerede skrivebordsbrugere kan få support enten fra din organisation ("kundestyret" support) eller fra en udvalgt partner ("partnerbaseret" support).

Vi bestræber os på at give brugerne en ensartet oplevelse, mens vi holder enheder sikre med begge supportmuligheder. Uanset hvilken valgmulighed du vælger, gælder de samme principper:

- Fleksibel integration af Microsoft Managed Desktop-enheder med dine eksisterende supportprocesser.
- Ryd roller og ansvarsområder mellem supportudbyderen, it-administratorer og Microsoft Managed Desktop.
- [Definerede eskaleringsstier](#workflow-for-support-providers).
- Dokumentation leveret af Microsoft Managed Desktop sammen med en portal, hvor du kan anmode om administratoradgang og eskalering til vores supportmedarbejdere, hvis det er nødvendigt.
- Overvågning og afhjælpning af trusler leveret af Microsoft Managed Desktop hele dagen.

## <a name="roles-and-responsibilities"></a>Roller og ansvarsområder

For at sikre kvaliteten af tjenesten uden at forringe sikkerheden har supportudbyderen, it-administratorer og Microsoft Managed Desktop forskellige roller og ansvarsområder.

| Rolle | Ansvarsområder |
| ------ | ------ |
| Supportudbyder | Den person, der yder support (enten dig for kundeledet support eller en partner med partner), er ansvarlig for disse varer: <ul><li>Giv al brugersupport og teknisk hjælp fra første kontakt til løsning for brugeren.</li><li>Opfylder alle serviceaftaler for brugersupport, der er oprettet af din organisation, eller i partnerskab med din valgte supportudbyder.</li><li>Udfør bestemte fejlfindingshandlinger, f.eks. anmodning om administratorrettigheder for enheder som beskrevet i [Få hjælp til brugere](../working-with-managed-desktop/end-user-support.md).</li><li>Fejlfinding og løsning af brugerproblemer, herunder: <ul><li>Operativsystem (Windows)</li><li>Microsoft Apps til virksomheder</li><li>Browserfunktioner</li><li>Enhedsproblemer</li><li>Problemer med infrastruktur, f.eks. printere, drivere og VPN</li><li>Line of business-programmer</li></ul></ul> |
| IT-administrator | Din it-administrator er ansvarlig for disse elementer: <ul><li>Arbejde sammen med supportudbyderen om at definere og administrere serviceaftaler for brugersupport</li><li>Administrer administratorrettigheder for godkendt supportpersonale. Få mere at vide under [Aktivér brugersupportfunktioner](../get-started/enable-support.md).</li><li>Hvis der er enhedsproblemer, der påvirker brugere, skal du eskalere problemerne ved hjælp af Microsoft Managed Desktop-administratorsupportprocessen. Du kan få mere at vide [under Administratorsupport til Microsoft Managed Desktop](../working-with-managed-desktop/admin-support.md).</li><li>Distribuere hardwarerelaterede problemer til den relevante leverandør eller leverandør.</li><li>Vedligehold og beskyt indstillinger for sikkerhedspolitik for enheder på Microsoft-administrerede skrivebordsenheder. Du må ikke ændre de politikker, vi har angivet. </li></ul> |
| Microsoft-administreret skrivebord |Som den serviceudbyder, er vi ansvarlige for disse varer: <ul><li>Angive metoder til administratoradgang og eskalering af problemer, herunder dokumentation.</li><li>Sørg for, at disse oplysninger om roller og ansvarsområder er aktuelle.</li><li>Svar på anmodninger om administratorsupport i overensstemmelse med definitionerne af alvorsgrad.</li><li>Giv mulighed for overvågning af trusler og afhjælpning for alle enheder, der er tilmeldt hele dagen, hver dag.</li></ul> |

## <a name="workflow-for-support-providers"></a>Arbejdsproces for supportudbydere

Uanset om support er kunde- eller partnerledet, følger aktivitetsstrømmen for en brugersupportanmodning denne sti:

:::image type="content" source="../../media/mmd-support-flow.png" alt-text="Når en bruger kontakter support, vil de arbejde gennem dit niveauerede personalesystem, som du har designet. Det er vigtigt at udpege en gruppe af supportmedarbejdere, der kan udvides og eskaleres, hvilket kaldes supporteskaleringsteamet. Ved bestemte problemer med Microsoft-administreret skrivebord kan de eskalere til vores driftsteam. Eller ved andre Microsoft-problemer kan de dirigere til din eksisterende supportkanal, Unified eller Premier. Hardwareproblemer skal altid distribueres til din etablerede udbyder eller leverandør":::

Integrering af dine eksisterende processer med denne arbejdsproces for Microsoft Managed Desktop-enheder er fleksibelt, så detaljerne kan være forskellige. Supportudbyderen følger typisk en eksisterende metode, der er baseret på niveau eller aflevering. Supportudbyderen udpeger bestemte brugere, der har mulighed for at administratorrettigheder eller eskalere problemer til Microsoft-administrerede computerhandlinger. Det er bedst at holde denne gruppe mindre end det bredere supportteam.

Hvis et problem skal eskaleres til Microsoft Managed Desktop, er det nyttigt at identificere, hvilket team problemet skal dirigeres til. Vi kan overføre sager korrekt, men det sparer tid at dirigere dem til det rigtige sted fra starten.

| Problem | Kontakt dette team |
| ------ | ------ |
| Problemer, der er specifikke for Microsoft Managed Desktop | Eksempelvis en politik eller indstilling, der installeres af selve tjenesten. Eskaler direkte til operationsteamet ved at oprette en ny supportanmodning. Du kan finde flere oplysninger [under Få hjælp til brugere](../working-with-managed-desktop/end-user-support.md).
| Hardwareproblemer | Direkte til din hardwareleverandør eller leverandør.
| Andre problemer| Eskaler gennem eksisterende supportkanaler, uanset om det er et samlet eller Premier-abonnement.

## <a name="provided-support-framework"></a>Understøttet struktur

### <a name="elevation-portal"></a>Udvidelsesportal

Da Microsoft-administrerede skrivebordsenheder kører på standardbruger som standard, kræver nogle opgaver udvidelse af rettigheder. Du kan finde flere oplysninger om kontrol af brugerkonti [under Kontrol af brugerkonti](/windows/security/identity-protection/user-account-control/user-account-control-overview). For at supportpersonale kan udføre opgaver under fejlfinding [](../working-with-managed-desktop/end-user-support.md#elevation-requests) af problemer for brugerne, giver vi "just-in-time" adgang til en administratorkonto. Denne adgangskode tilgås sikkert af kun de brugere, du angiver, og roterer med et par timer.  

Du kan finde en vejledning til, hvordan du konfigurerer brugere til at få adgang til denne portal, [under Aktivere brugersupportfunktioner](../get-started/enable-support.md).

Du kan finde trin til indsendelse af en udvidelsesanmodning under [Anmodninger om udvidelse](../working-with-managed-desktop/end-user-support.md#elevation-requests).

### <a name="escalation-portal"></a>Eskaleringsportal

Hvis et problem kræver eskalering til Microsoft Managed Desktop Operations-teamet, kan en udpeget supportmedarbejder muligvis komme til at ligne en supportanmodning fra en it-administrator.  

> [!NOTE]
> Kun sev C-supportanmodninger kan arkiveres på denne måde. Hvis du har et problem, der matcher beskrivelsen af andre alvorsgrader, anbefales det at kontakte den relevante it-administrator for at arkivere. Du kan finde flere oplysninger i [Supportanmodninger om alvorlighedsdefinitioner](../working-with-managed-desktop/admin-support.md#support-request-severity-definitions).

Du kan finde en vejledning til, hvordan du konfigurerer brugere til at få adgang til denne portal, [under Aktivere brugersupportfunktioner](../get-started/enable-support.md).

Du kan finde trin til at sende en eskaleringsanmodning under [Eskaleringsanmodninger](../working-with-managed-desktop/end-user-support.md#escalation-requests).
