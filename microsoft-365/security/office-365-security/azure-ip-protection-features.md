---
title: Beskyttelsesfunktioner i Azure Information Protection udrulles til eksisterende lejere
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
description: I denne artikel beskrives de ændringer, der rulles ud til beskyttelsesfunktionerne i Azure Information Protection
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a11821e6c2165c79e286612b89d42f7e19b1593d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 10/06/2021
ms.locfileid: "63589142"
---
# <a name="protection-features-in-azure-information-protection-rolling-out-to-existing-tenants"></a>Beskyttelsesfunktioner i Azure Information Protection udrulles til eksisterende lejere

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Gælder for**
- [Microsoft Defender til Office 365 plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Som en hjælp til det første trin til beskyttelse af dine oplysninger vil alle berettigede Azure Information Protection-lejere fra juli 2018 have beskyttelsesfunktionerne i Azure Information Protection slået til som standard. Beskyttelsesfunktionerne i Azure Information Protection blev tidligere kendt i Office 365 som Rights Management eller Azure RMS. Hvis din organisation har en Office E3-serviceplan eller en højere serviceplan, får du nu et forspring ved at beskytte oplysninger via Azure Information Protection, når vi udruller disse funktioner.

## <a name="changes-beginning-july-1-2018"></a>Ændringer fra d. 1. juli 2018

Fra og med d. 1. juli 2018 aktiverer Microsoft beskyttelsesfunktionaliteten i Azure Information Protection for alle organisationer med et af følgende abonnementsplaner:

- Office 365-meddelelseskryptering tilbydes som en del af Office 365 E3 og E5, Microsoft E3 og E5, Office 365 A1, A3 og A5 og Office 365 G3 og G5. Du behøver ikke yderligere licenser for at modtage de nye beskyttelsesfunktioner, der leveres af Azure Information Protection.

- Du kan også føje Azure Information Protection Plan 1 til følgende planer for at modtage de nye Office 365-meddelelseskryptering-funktioner: Exchange Online Plan 1, Exchange Online Plan 2, Office 365 F1, Microsoft 365 Business Basic, Microsoft 365 Business Standard eller Office 365 Enterprise E1.

- Hver enkelt bruger, der Office 365-meddelelseskryptering adgang til en bruger, skal have licens for at være omfattet af funktionen.

- Du kan se den komplette liste [i Exchange Online tjenestebeskrivelser](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description) for Office 365-meddelelseskryptering.

Lejeradministratorer kan kontrollere beskyttelsesstatus på Office 365 administratorportalen.

![Skærmbillede, der viser, at rettighedsstyring i Office 365 er aktiveret.](../../media/303453c8-e4a5-4875-b49f-e80c3eb7b91e.png)

## <a name="why-are-we-making-this-change"></a>Hvorfor foretager vi denne ændring?

Office 365-meddelelseskryptering udnytter beskyttelsesfunktionerne i Azure Information Protection. Kernen i de seneste forbedringer af Office 365-meddelelseskryptering og vores bredere investeringer i informationsbeskyttelse i Microsoft 365 gør vi det nemmere for organisationer at aktivere og bruge vores beskyttelsesfunktioner, da krypteringsteknologier historisk har været svære at konfigurere. Ved at slå beskyttelsesfunktionerne i Azure Information Protection til som standard kan du hurtigt komme i gang med at beskytte dine følsomme data.

## <a name="does-this-impact-me"></a>Påvirker det mig?

Hvis din organisation har købt en berettiget Office 365-licens, vil din lejer blive påvirket af denne ændring.

> [!IMPORTANT]
> Hvis du bruger Active Directory Rights Management-tjenester (AD RMS) i dit lokale miljø, skal du enten fravælge denne ændring med det samme eller overføre til Azure Information Protection, før vi udruller denne ændring inden for de næste 30 dage. Du kan finde oplysninger om, hvordan du fravælger, under "Jeg bruger AD RMS, hvordan fravælger jeg?" senere i denne artikel. Hvis du foretrækker at overføre, skal [du se Overførsel fra AD RMS til Azure Information Protection](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms).

## <a name="can-i-use-azure-information-protection-with-active-directory-rights-management-services-ad-rms"></a>Kan jeg bruge Azure Information Protection med Active Directory Rights Management-tjenester (AD RMS)?

Nej. Dette er ikke et understøttet installationsscenarie. Uden at udføre de ekstra fravalgstrin vil nogle computere muligvis automatisk begynde at bruge Azure Rights Management-tjenesten og også oprette forbindelse til din AD RMS-klynge. Dette scenarie understøttes ikke og har upålidelige resultater, så det er vigtigt, at du fravælger denne ændring inden for de næste 30 dage, før vi udruller disse nye funktioner. Du kan finde oplysninger om, hvordan du fravælger, under "Jeg bruger AD RMS, hvordan fravælger jeg?" senere i denne artikel. Hvis du foretrækker at overføre, skal [du se Overførsel fra AD RMS til Azure Information Protection.](/azure/information-protection/plan-design/migrate-from-ad-rms-to-azure-rms)

## <a name="how-do-i-know-if-im-using-ad-rms"></a>Hvordan ved jeg, om jeg bruger AD RMS?

Følg disse instruktioner fra Forberedelse af miljøet [til Azure Rights Management, når du også har Active Directory Rights Management-tjenester (AD RMS) for](/azure/information-protection/deploy-use/prepare-environment-adrms) at kontrollere, om du har installeret AD RMS:

1. Selvom det er valgfrit, publicerer de fleste AD RMS-installationer tjenesteforbindelsespunktet (SCP) til Active Directory, så domænecomputere kan finde AD RMS-klyngen.

   Brug ADSI Edit for at se, om du har et SCP publiceret i Active Directory: CN=Configuration [servernavn], CN=Services, CN=RightsManagementServices, CN=SCP

2. Hvis du ikke bruger et SCP, skal Windows-computere, der opretter forbindelse til en AD RMS-klynge, konfigureres til tjenesteregistrering på klientsiden eller omdirigering af licenser ved hjælp af Windows registreringsdatabase: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation or HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\ServiceLocation`.

Du kan finde flere oplysninger om disse konfigurationer i registreringsdatabasen i Aktivering af tjenesteregistrering på klientsiden ved hjælp [af registreringsdatabasen Windows](/azure/information-protection/rms-client/client-deployment-notes#enabling-client-side-service-discovery-by-using-the-windows-registry) [Redirecting licensing server traffic](/azure/information-protection/rms-client/client-deployment-notes#redirecting-licensing-server-traffic).

## <a name="i-use-ad-rms-how-do-i-opt-out"></a>Jeg bruger AD RMS, hvordan fravælger jeg?

Hvis du vil fravælge den kommende ændring, skal du udføre disse trin:

1. Du kan bruge en arbejds- eller skolekonto, der har globale administratortilladelser i din organisation, til at starte en Windows PowerShell-session og oprette forbindelse til Exchange Online. Du kan finde en [vejledning Forbind at Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Kør cmdletten Set-IRMConfiguration ved hjælp af følgende syntaks:

  ```powershell
  Set-IRMConfiguration -AutomaticServiceUpdateEnabled $false
  ```

## <a name="what-can-i-expect-after-this-change-has-been-made"></a>Hvad kan jeg forvente, når denne ændring er foretaget?

Når denne funktion er aktiveret, og du ikke har fravalgt den, kan du begynde at bruge den nye version af Office 365-meddelelseskryptering, som blev offentliggjort på [Microsoft Ignite 2017](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801), og benytte krypterings- og beskyttelsesfunktionerne fra Azure Information Protection.

![Skærmbillede, der viser en OME-beskyttet meddelelse Outlook på internettet.](../../media/599ca9e7-c05a-429e-ae8d-359f1291a3d8.png)

Du kan finde flere oplysninger om de nye forbedringer [under Office 365-meddelelseskryptering](../../compliance/ome.md).