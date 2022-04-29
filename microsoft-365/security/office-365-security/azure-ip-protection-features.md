---
title: Beskyttelsesfunktioner i Azure Information Protection udrulning til eksisterende lejere
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 7ad6f58e-65d7-4c82-8e65-0b773666634d
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: I denne artikel forklares de ændringer, der udrulles til beskyttelsesfunktionerne i Azure Information Protection
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dbfc21b879745567c9273c79356ff60e498d95ff
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130818"
---
# <a name="protection-features-in-azure-information-protection-rolling-out-to-existing-tenants"></a>Beskyttelsesfunktioner i Azure Information Protection udrulning til eksisterende lejere

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender for Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Fra og med juli 2018 vil alle berettigede Lejere i Azure Information Protection have beskyttelsesfunktionerne i Azure Information Protection aktiveret som standard for at hjælpe med det første trin til beskyttelse af dine oplysninger. Beskyttelsesfunktionerne i Azure Information Protection var tidligere kendt i Office 365 som Rights Management eller Azure RMS. Hvis din organisation har en Office E3-serviceplan eller en højere serviceplan, kan du nu komme i gang med at beskytte oplysninger via Azure Information Protection, når vi udruller disse funktioner.

## <a name="changes-beginning-july-1-2018"></a>Ændringer fra og med den 1. juli 2018

Fra og med den 1. juli 2018 aktiverer Microsoft beskyttelsesfunktionerne i Azure Information Protection for alle organisationer med en af følgende abonnementsplaner:

- Office 365 Meddelelseskryptering tilbydes som en del af Office 365 E3 og E5, Microsoft E3 og E5, Office 365 A1, A3 og A5 og Office 365 G3 og G5. Du behøver ikke yderligere licenser for at modtage de nye beskyttelsesfunktioner, der leveres af Azure Information Protection.

- Du kan også føje Azure Information Protection Plan 1 til følgende planer for at modtage de nye funktioner til Office 365 meddelelsekryptering: Exchange Online Plan 1, Exchange Online Plan 2, Office 365 F1, Microsoft 365 Business Basic, Microsoft 365 Business Standard eller Office 365 Enterprise E1.

- Hver bruger, der drager fordel af Office 365 Meddelelseskryptering, skal have licens for at være omfattet af funktionen.

- Du kan se den komplette liste i [Exchange Online tjenestebeskrivelser](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) for Office 365 Meddelelsekryptering.

Lejeradministratorer kan kontrollere beskyttelsesstatussen på Office 365-administratorportalen.

:::image type="content" source="../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png" alt-text="Rettighedsadministrationen i Office 365, der er aktiveret" lightbox="../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png":::

## <a name="why-are-we-making-this-change"></a>Hvorfor foretager vi denne ændring?

Office 365 Message Encryption udnytter beskyttelsesfunktionerne i Azure Information Protection. I hjertet af de seneste forbedringer af Office 365 Meddelelseskryptering og vores bredere investeringer i information beskyttelse i Microsoft 365 gør vi det nemmere for organisationer at aktivere og bruge vores beskyttelsesfunktioner, da krypteringsteknologier historisk set har været vanskelige at konfigurere. Når du aktiverer beskyttelsesfunktionerne i Azure Information Protection som standard, kan du hurtigt komme i gang med at beskytte dine følsomme data.

## <a name="does-this-impact-me"></a>Påvirker det mig?

Hvis din organisation har købt en berettiget Office 365 licens, påvirkes din lejer af denne ændring.

> [!IMPORTANT]
> Hvis du bruger Active Directory Rights Management-tjenester (AD RMS) i dit lokale miljø, skal du enten framelde dig ændringen med det samme eller migrere til Azure Information Protection før vi udruller ændringen inden for de næste 30 dage. Du kan få oplysninger om, hvordan du fravælger, under "Jeg bruger AD RMS, hvordan fravælger jeg?" senere i denne artikel. Hvis du foretrækker at overføre, skal du se [Overførsel fra AD RMS til Azure Information Protection.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms).

## <a name="can-i-use-azure-information-protection-with-active-directory-rights-management-services-ad-rms"></a>Kan jeg bruge Azure Information Protection med Active Directory Rights Management-tjenester (AD RMS)?

Nej. Dette er ikke et understøttet installationsscenarie. Uden at tage de ekstra fravalgstrin kan nogle computere muligvis begynde at bruge Azure Rights Management-tjenesten automatisk og også oprette forbindelse til AD RMS-klyngen. Dette scenarie understøttes ikke og har upålidelige resultater, så det er vigtigt, at du fravælger denne ændring inden for de næste 30 dage, før vi udruller disse nye funktioner. Du kan få oplysninger om, hvordan du fravælger, under "Jeg bruger AD RMS, hvordan fravælger jeg?" senere i denne artikel. Hvis du foretrækker at overføre, skal du se [Overførsel fra AD RMS til Azure Information Protection.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="how-do-i-know-if-im-using-ad-rms"></a>Hvordan gør jeg vide, om jeg bruger AD RMS?

Brug disse instruktioner fra [Forberedelse af miljøet til Azure Rights Management, når du også har Active Directory Rights Management-tjenester (AD RMS)](/azure/information-protection/deploy-use/prepare-environment-adrms) for at kontrollere, om du har installeret AD RMS:

1. Selvom det er valgfrit, publicerer de fleste AD RMS-installationer tjenesteforbindelsespunktet (SCP) til Active Directory, så domænecomputere kan finde AD RMS-klyngen.

   Brug ADSI Edit til at se, om du har udgivet et SCP i Active Directory: CN=Configuration [servernavn], CN=Services, CN=RightsManagementServices, CN=SCP

2. Hvis du ikke bruger et SCP, skal Windows computere, der opretter forbindelse til en AD RMS-klynge, konfigureres til registrering af tjenester på klientsiden eller licensomdirigering ved hjælp af Windows registreringsdatabasen: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation`.

Du kan finde flere oplysninger om disse konfigurationer i registreringsdatabasen under [Aktivering af registrering af tjenester på klientsiden ved hjælp af Windows registreringsdatabasen](/azure/information-protection/rms-client/client-deployment-notes#enabling-client-side-service-discovery-by-using-the-windows-registry) og [servertrafik til omdirigering af licenser](/azure/information-protection/rms-client/client-deployment-notes#redirecting-licensing-server-traffic).

## <a name="i-use-ad-rms-how-do-i-opt-out"></a>Jeg bruger AD RMS, hvordan fravælger jeg?

Hvis du vil fravælge den kommende ændring, skal du udføre disse trin:

1. Hvis du bruger en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, skal du starte en Windows PowerShell session og oprette forbindelse til Exchange Online. Du kan finde instruktioner [under Forbind til at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør Set-IRMConfiguration-cmdlet'en ved hjælp af følgende syntaks:

  ```powershell
  Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false
  ```

## <a name="what-can-i-expect-after-this-change-has-been-made"></a>Hvad kan jeg forvente, når denne ændring er foretaget?

Når dette er aktiveret, kan du begynde at bruge den nye version af Office 365 Meddelelseskryptering, som blev annonceret på [Microsoft Ignite 2017](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801), og udnytte krypterings- og beskyttelsesfunktionerne i Azure Information Protection.

:::image type="content" source="../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png" alt-text="En OME-beskyttet meddelelse i Outlook på internettet" lightbox="../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png":::

Du kan få flere oplysninger om de nye forbedringer [under Office 365 Meddelelsekryptering](../../compliance/ome.md).
