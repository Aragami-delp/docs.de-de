---
ms.openlocfilehash: 7723892a33bf7dd8e475b2f696db5d9ab287e182
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602753"
---

Die Pakete, die dem Paket-Manager-Feed hinzugefügt werden, werden in einem Format benannt, das gehackt werden kann: `{product}-{type}-{version}`.

- **Produkt**\
Der Typ des zu installierenden .NET-Produkts. Folgende Optionen sind gültig:

  - dotnet
  - aspnetcore

- **Typ**\
Wählt das SDK oder die Runtime aus. Folgende Optionen sind gültig:

  - SDK
  - Laufzeit

- **Version**\
Die Version des zu installierenden SDK oder der zu installierenden Runtime. In diesem Artikel erhalten Sie stets die Anweisungen für die neueste unterstützte Version. Gültige Optionen sind alle veröffentlichte Versionen, wie z. B.:

  - 3.1
  - 3.0
  - 2.1

  Es ist möglich, dass das SDK bzw. die Runtime, das/die Sie herunterladen möchten, für Ihre Linux-Distribution nicht verfügbar ist. Eine Liste der unterstützten Distributionen finden Sie unter [.NET Core-Abhängigkeiten und -Anforderungen](../linux.md).

### <a name="examples"></a>Beispiele

- Installieren der ASP.NET Core 3.1-Runtime: `aspnetcore-runtime-3.1`
- Installieren der .NET Core 2.1-Runtime: `dotnet-runtime-2.1`
- Installieren des .NET Core 3.1 SDK: `dotnet-sdk-3.1`

### <a name="package-missing"></a>Fehlendes Paket

Wenn die Kombination aus Paket und Version nicht funktioniert, ist sie nicht verfügbar. Beispielsweise gibt es keine ASP.NET Core SDK, die SDK-Komponenten sind in der .NET Core SDK enthalten. Der Wert `aspnetcore-sdk-2.2` ist falsch und sollte `dotnet-sdk-2.2` lauten. Eine Liste der von .NET Core unterstützten Linux-Distributionen finden Sie unter [.NET Core-Abhängigkeiten und -Anforderungen](../linux.md).
