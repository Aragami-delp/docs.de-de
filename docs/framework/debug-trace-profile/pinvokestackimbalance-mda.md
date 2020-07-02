---
title: pInvokeStackImbalance-MDA
description: Überprüfen Sie den pinvokestackungleichmumda, der während einer Zugriffsverletzung oder einer Beschädigung des Arbeitsspeichers aktiviert werden kann, wenn ein Platt Form Aufruf aufgerufen oder darauf folgt.
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
ms.openlocfilehash: 89afd3fce3f2a8bffe88d45991ceeb59fc5e5b76
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803663"
---
# <a name="pinvokestackimbalance-mda"></a>PInvokeStackImbalance-MDA

Der `PInvokeStackImbalance` Assistent für verwaltetes Debuggen (MDA) wird aktiviert, wenn die CLR erkennt, dass die Stapel Tiefe nach einem Platt Form Aufruf nicht mit der erwarteten Stapel Tiefe übereinstimmt, wenn die im-Attribut angegebene Aufruf Konvention <xref:System.Runtime.InteropServices.DllImportAttribute> und die Deklaration der Parameter in der verwalteten Signatur angegeben ist.

Der `PInvokeStackImbalance`-MDA wird nur für 32-Bit-x86-Plattformen implementiert.

> [!NOTE]
> Der `PInvokeStackImbalance` MDA ist standardmäßig deaktiviert. In Visual Studio 2017 und höheren Versionen wird der `PInvokeStackImbalance` MDA in der Liste der **Assistenten für verwaltetes Debuggen** im Dialogfeld **Ausnahme Einstellungen** angezeigt, das angezeigt wird, wenn Sie Windows- **Debug**  >  **Windows**  >  **Ausnahme Einstellungen**Debuggen auswählen. Durch Aktivieren oder Deaktivieren des Kontrollkästchens "unter **brechen bei** auslösen" wird jedoch der MDA nicht aktiviert bzw. deaktiviert. Es steuert nur, ob Visual Studio eine Ausnahme auslöst, wenn der MDA aktiviert wird.

## <a name="symptoms"></a>Symptome

Während eines Plattformaufrufs in einer Anwendung oder danach kommt es zu einer Zugriffsverletzung oder Speicherbeschädigung.

## <a name="cause"></a>Ursache

Die verwaltete Signatur des Plattformaufrufs stimmt möglicherweise nicht mit der nicht verwalteten Signatur der aufgerufenen Methode überein.  Dazu kann es kommen, wenn für die verwaltete Methode nicht die korrekte Anzahl der Parameter bzw. eine falsche Parametergröße deklariert wurde.  Der MDA wird auch aktiviert, wenn die ggf. durch das <xref:System.Runtime.InteropServices.DllImportAttribute>-Attribut festgelegte Aufrufkonvention nicht mit der nicht verwalteten Aufrufkonvention übereinstimmt.

## <a name="resolution"></a>Lösung

Überprüfen Sie die Signatur des verwalteten Plattformaufrufs sowie die Aufrufkonvention, um sich zu vergewissern, dass diese mit der Signatur und Aufrufkonvention des systemeigenen Ziels übereinstimmen.  Versuchen Sie, die Aufrufkonvention sowohl auf der verwalteten als auch auf der nicht verwalteten Seite explizit anzugeben. Es ist ebenfalls möglich (wenn auch weniger wahrscheinlich), dass die nicht verwaltete Funktion aus einem anderen Grund einen nicht ausgeglichenen Stapel verursacht hat, beispielsweise durch einen Programmfehler im nicht verwalteten Compiler.

## <a name="effect-on-the-runtime"></a>Auswirkungen auf die Laufzeit

Erzwingt für alle Plattformaufrufe die Verwendung des nicht optimierten Pfads in die CLR.

## <a name="output"></a>Output

Die MDA-Meldung enthält den Namen der Plattformaufrufmethode, die das Stapelungleichgewicht verursacht hat. Beispielmeldung eines Plattformaufrufs der `SampleMethod`-Methode: 

**Ein Ping-Befehl für die PInvoke-Funktion "SampleMethod" hat den Stapel nicht ausgeglichen. Dies liegt wahrscheinlich daran, dass die verwaltete PInvoke-Signatur nicht mit der nicht verwalteten Ziel Signatur identisch ist. Überprüfen Sie, ob die Aufruf Konvention und die Parameter der PInvoke-Signatur mit der nicht verwalteten Ziel Signatur übereinstimmen.**

## <a name="configuration"></a>Konfiguration

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Weitere Informationen

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnostizieren von Fehlern mit Assistenten für verwaltetes Debuggen](diagnosing-errors-with-managed-debugging-assistants.md)
- [Interop Marshaling (Interop-Marshalling)](../interop/interop-marshaling.md)
