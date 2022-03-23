---
title: Oversigt over kryptering med dobbelt nøgle og ofte stillede spørgsmål
description: Ofte stillede spørgsmål om kryptering af dobbelt nøgle til Microsoft 365.
author: kccross
ms.author: krowley
manager: laurawi
ms.date: 02/28/2022
ms.topic: conceptual
ms.service: information-protection
audience: Admin
ms.reviewer: esaggese
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.openlocfilehash: 269937e78ffee6956df5a4dc8dc978fa30043912
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 03/08/2022
ms.locfileid: "63589824"
---
# <a name="double-key-encryption-frequently-asked-questions"></a>Ofte stillede spørgsmål om kryptering af dobbelt nøgle

Har du spørgsmål om, hvordan kryptering med dobbelt nøgle fungerer? Se efter et svar her.

## <a name="what-is-double-key-encryption-for-microsoft-365-dke"></a>Hvad er Dobbelt nøglekryptering til Microsoft 365 (DKE)?

Kryptering med dobbelt nøgle til Microsoft 365 kunderne mulighed for at beskytte deres meget følsomme data, så de opfylder særlige krav. Det hjælper kunder med at bevare fuld kontrol over deres krypteringsnøgler. Den bruger to taster til at beskytte data. én nøgle i din kontrol og en anden nøgle, der er gemt sikkert Microsoft Azure. Visning af data, der er beskyttet med kryptering med dobbelt nøgle, kræver adgang til begge nøgler. Da Microsoft kun kan få adgang til én af disse nøgler, vil beskyttede data ikke være tilgængelige for Microsoft og sikre, at du har fuld kontrol over dine datas beskyttelse af personlige oplysninger og sikkerhed.  

Du kan hoste dobbelt nøglekrypteringstjenesten, der bruges til at anmode om din nøgle, på et sted efter eget valg (nøgleadministrationsserver i det lokale miljø eller i skyen). Du vedligeholder tjenesten, som du ville gøre med ethvert andet program. Dobbelt nøglekryptering giver dig mulighed for at kontrollere adgangen til tjenesten Dobbelt nøglekryptering. Du kan gemme dine meget følsomme data lokalt eller flytte dem til skyen. Du kan være sikker på at forhindre tredjepartsadgang, fordi du har fuld kontrol over din nøgle. Dobbelt nøglekryptering gør det muligt at gemme dine data og nøgler på samme placering.

DKE hjælper dig med at opfylde lovmæssige krav på tværs af flere bestemmelser og standarder som f.eks. General Data Protection Regulation (GDPR), HEALTH Insurance Portability and Accountability Act (HIPAA), Gramm-Leach-Bliley Act (GLBA), Ruslands lovgivning om lokalisering af data – Federal Law No. 242-FZ, Australiens Federal Privacy Act 1988 og New Zealand's Privacy Act 1993.

## <a name="can-i-use-double-key-encryption-with-microsoft-office-built-in-sensitivity-labeling"></a>Kan jeg bruge dobbelt nøglekryptering Microsoft Office Indbygget følsomhedsmærkater?

Du skal bruge Den samlede Azure Information Protection-etiketklient til at beskytte dokumenter med dobbelt nøglekryptering. I øjeblikket kan du ikke bruge Microsoft Office indbyggede følsomhedsmærkater.

## <a name="what-microsoft-365-apps-can-i-use-with-dke"></a>Hvilke Microsoft 365 Apps kan jeg bruge med DKE?

Du kan bruge DKE-etiketter til at beskytte dokumenter ved hjælp af skrivebordsversionerne af Word, Excel og PowerPoint på Windows. Sørg for, at du bruger *.12711 eller nyere (skrivebordsversioner af Word, PowerPoint og Excel) på Windows.

## <a name="how-is-double-key-encryption-different-from-the-existing-hold-your-own-key-hyok-solution"></a>Hvordan er kryptering med dobbelt nøgle anderledes end den eksisterende løsning hold din egen nøgle (HYOK)?

Dobbelt nøglekryptering krypterer dine data med to nøgler. Din krypteringsnøgle er i din kontrol, og den anden nøgle gemmes i Microsoft Azure, så du kan flytte dine krypterede data til skyen. HYOK beskytter dit indhold med kun én nøgle, og nøglen er altid lokalt.  

## <a name="can-double-key-encrypted-documents-be-shared-externally"></a>Kan krypterede dokumenter med dobbelt nøgle deles eksternt?

Du kan dele krypterede dokumenter med dobbeltnøgler med brugere på en separat lejer, så længe disse brugere:

- Have den nødvendige tilladelse til at få adgang til din nøgle i tjenesten Kryptering af dobbeltnøgler.

- Have den nødvendige tilladelse til at få adgang til din nøgle Microsoft Azure.

## <a name="what-happens-to-documents-that-are-protected-with-hyok"></a>Hvad sker der med dokumenter, der er beskyttet med HYOK?

Installation af Kryptering med dobbelt nøgle påvirker ikke din eksisterende HYOK-konfiguration. Vi anbefaler dog, at du begynder at bruge dobbelt nøglekryptering parallelt med HYOK.

## <a name="can-i-run-double-key-encryption-in-my-non-microsoft-air-gapped-environment"></a>Kan jeg køre Dobbelt nøglekryptering i mit ikke-Microsoft-miljø, hvor der ikke er mellemrum?

DKE understøtter ikke disse miljøer, fordi tjenesten kræver adgang for at kunne Microsoft Azure.

## <a name="where-can-i-store-double-key-encrypted-documents"></a>Hvor kan jeg gemme krypterede dokumenter med dobbeltnøgler?

Du kan gemme krypterede dokumenter med dobbelt nøgle lokalt eller i skyen. I skyen kan du flytte krypteret indhold til SharePoint Online og OneDrive for Business. Da Microsoft ikke har adgang til din private nøgle, forbliver de krypterede data ugennemsigtige for Microsoft. Det betyder også, at du ikke kan få vist de krypterede dokumenter online Office webapps.

## <a name="what-regions-and-languages-is-double-key-encryption-available-in-is-double-key-encryption-available-worldwide"></a>Hvilke områder og sprog findes kryptering med dobbelt nøgle i? Findes kryptering med dobbelt nøgle i hele verden?

DKE-etiketter er oversatte til de samme sprog som andre følsomhedsmærkater i Microsoft Information Protection. Kryptering med dobbelt nøgle er tilgængelig i hele verden.

## <a name="can-i-convert-a-non-dke-label-to-a-dke-label"></a>Kan jeg konvertere et ikke-DKE-navn til en DKE-etiket?

Nej. Du kan ikke føje DKE til en etiket, når du har oprettet den. I stedet skal du vælge **Brug dobbelt nøglekryptering** og angive URL-adressen til din dobbeltnøglekrypteringstjeneste, når du opretter etiketten.

## <a name="how-do-i-roll-my-dke-keys"></a>Hvordan ruller jeg mine DKE-nøgler?

Du kan finde en vejledning til, hvordan du ruller (også kaldet rotation eller nøglering) den nøgle, du gemmer i Azure, under [Handlinger for din Azure Information Protection-lejernøgle](/azure/information-protection/operations-customer-managed-tenant-key).

Se [Lejer- og nøgleindstillinger](double-key-encryption.md#tenant-and-key-settings) for at få oplysninger om oprettelse af en ny nøgle til DKE-tjenesten.

Når du opretter en nøgle, konfigurerer du et navn og et GUID. Hvis du derefter roterer en nøgle, beholder du den gamle post med navnet og GUID, men tilføjer en ny post med det samme navn, men forskelligt GUID. Den nye nøgle indstilles som aktiv, så den offentlige nøgle-API begynder at returnere den til ny kryptering. Begge nøgler kan dekrypteres, så nyt indhold og gammelt indhold kan dekrypteres.