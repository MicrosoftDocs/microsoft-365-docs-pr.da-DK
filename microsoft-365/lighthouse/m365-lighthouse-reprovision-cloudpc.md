---
title: Klargør en Windows 365 Cloud-pc i Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: katmartin
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: For MSP'er (Managed Service Providers) ved hjælp af Microsoft 365 Lighthouse kan du få mere at vide om, hvordan du klargør en Windows 365 Cloud-pc i Microsoft 365 Lighthouse.
ms.openlocfilehash: 9ce402d1db83b07653c3e93a5e1e1c25406ae3e9
ms.sourcegitcommit: 5e5c2c1f7c321b5eb1c5b932c03bdd510005de13
ms.translationtype: MT
ms.contentlocale: da-DK
ms.lasthandoff: 07/15/2022
ms.locfileid: "66859102"
---
# <a name="reprovision-a-windows-365-cloud-pc-in-microsoft-365-lighthouse"></a>Klargør en Windows 365 Cloud-pc i Microsoft 365 Lighthouse

Microsoft 365 Lighthouse understøtter klargøring af cloud-pc'er, der har en klargøringspolitik. Du skal muligvis klargøre en enhed igen for en ny bruger, eller hvis enheden ikke fungerer korrekt. Når en klargøring udløses, slettes cloud-pc'en og oprettes igen som en ny Cloud-pc. Alle brugerdata, -programmer og -tilpasninger slettes.

## <a name="before-you-begin"></a>Før du begynder

Du skal være cloud-pc-administrator i partnerlejer.

## <a name="reprovision-a-windows-365-cloud-pc"></a>Klargør en Windows 365 Cloud-pc igen

1. Vælg **Enheder** >  i venstre navigationsrude i Lighthouse **Windows 365**.

2. Vælg fanen **Alle cloud-pc'er** .

3. Vælg licenstype på rullelisten **Filtre** .

4. Vælg en enhed på den filtrerede liste.

5. Vælg **Klargør igen** i ruden med enhedsoplysninger.

6. Vælg **Klargør igen** i bekræftelsesdialogboksen.

> [!NOTE]
> Den aktuelle bruger af Cloud-pc'en er straks logget af, og alle brugerdata fjernes.

## <a name="check-the-device-action-status"></a>Kontrollér status for enhedens handling

1. Vælg **Enheder** >  i venstre navigationsrude i Lighthouse **Windows 365**.

2. Vælg fanen **Alle cloud-pc'er** .

3. Vælg en enhed på listen over enheder.

4. Vælg fanen **Status for enhedshandling** i ruden med enhedsoplysninger.

Fanen viser alle aktuelle handlinger, der er sat i kø for denne enhed, herunder handlingstype, status og tidsstempel.

## <a name="related-content"></a>Relateret indhold

[Oversigt over klargøring](/windows-365/enterprise/provisioning) (artikel)\
[Rediger klargøringspolitikker](/windows-365/enterprise/edit-provisioning-policy) (artikel)
