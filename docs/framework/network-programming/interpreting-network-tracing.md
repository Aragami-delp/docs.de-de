---
title: Interpretieren von Netzwerkablaufverfolgung
description: Informationen zur Verwendung der Ablaufverfolgung, um die Aufrufe zu erfassen, die Ihre Anwendung an verschiedene Member der System.Net-Klasse im .NET Framework sendet
ms.date: 03/30/2017
helpviewer_keywords:
- TraceMode attribute
- hexidecimal data, network tracing output
- network tracing, analyzing
- protocolonly
- text, network tracing output
- includehex
ms.assetid: ad22b4b8-00af-4778-9cca-cb609ce1f8ff
ms.openlocfilehash: 7a17e4ba14d8c5fe136667c4eb5bc5b2fd7a8242
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502365"
---
# <a name="interpreting-network-tracing"></a><span data-ttu-id="8266f-103">Interpretieren von Netzwerkablaufverfolgung</span><span class="sxs-lookup"><span data-stu-id="8266f-103">Interpreting Network Tracing</span></span>
<span data-ttu-id="8266f-104">Wenn die Netzwerkablaufverfolgung aktiviert ist, können Sie die Ablaufverfolgung zum Erfassen von Aufrufen durch Ihre Anwendung an verschiedene <xref:System.Net>-Klassenmember verwenden.</span><span class="sxs-lookup"><span data-stu-id="8266f-104">When network tracing is enabled, you can use tracing to capture calls your application makes to various <xref:System.Net> class members.</span></span> <span data-ttu-id="8266f-105">Die Ausgabe dieser Aufrufe ähnelt möglicherweise den folgenden Beispielen.</span><span class="sxs-lookup"><span data-stu-id="8266f-105">The output from these calls may be similar to the following examples.</span></span>  
  
```output
[588]   (4357)   Entering Socket#33574638::Send()  
[588]   (4387)   Exiting Socket#33574638::Send()-> 61#61
```  
  
 <span data-ttu-id="8266f-106">Im vorhergehenden Beispiel ist [588] der eindeutige Bezeichner des aktuellen Threads.</span><span class="sxs-lookup"><span data-stu-id="8266f-106">In the preceding example, [588] is the current thread's unique identifier.</span></span> <span data-ttu-id="8266f-107">(4357) und (4387) sind Zeitstempel, die die Anzahl der Millisekunden seit dem Anwendungsstart angeben.</span><span class="sxs-lookup"><span data-stu-id="8266f-107">(4357) and (4387) are timestamps denoting the number of milliseconds that have elapsed since the application started.</span></span> <span data-ttu-id="8266f-108">Die Daten nach dem Zeitstempel geben an, dass die Methode **Socket.Send** von der Anwendung betreten und beendet wird.</span><span class="sxs-lookup"><span data-stu-id="8266f-108">The data following the timestamp shows the application entering and exiting the method **Socket.Send**.</span></span> <span data-ttu-id="8266f-109">Das Objekt, das die Methode **Send** ausführt, besitzt „33574638“ als eindeutigen Bezeichner.</span><span class="sxs-lookup"><span data-stu-id="8266f-109">The object executing the **Send** method has 33574638 as its unique identifier.</span></span> <span data-ttu-id="8266f-110">Die Ablaufverfolgung zum Beenden der Methode enthält den Rückgabewert (im vorherigen Beispiel 61).</span><span class="sxs-lookup"><span data-stu-id="8266f-110">The method exit trace includes the return value (61 in the preceding example).</span></span>  
  
 <span data-ttu-id="8266f-111">Netzwerkablaufverfolgungen können Netzwerkdatenverkehr erfassen, der mithilfe von Protokollen auf Anwendungsebene, wie z.B. HTTP (Hypertext Transfer Protocol), von der Anwendung gesendet oder empfangen wird.</span><span class="sxs-lookup"><span data-stu-id="8266f-111">Network traces can capture network traffic that is sent from or received by your application using application-level protocols such as Hypertext Transfer Protocol (HTTP).</span></span> <span data-ttu-id="8266f-112">Diese Daten können als Text und optional als hexadezimale Daten erfasst werden.</span><span class="sxs-lookup"><span data-stu-id="8266f-112">This data can be captured as text and, optionally, hexadecimal data.</span></span> <span data-ttu-id="8266f-113">Hexadezimale Daten sind verfügbar, wenn **includehex** als Wert des Attributs **tracemode** angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="8266f-113">Hexadecimal data is available when you specify **includehex** as the value of the **tracemode** attribute.</span></span> <span data-ttu-id="8266f-114">(Ausführliche Informationen zu diesem Attribut finden Sie unter [Vorgehensweise: Konfigurieren der Netzwerkablaufverfolgung](how-to-configure-network-tracing.md).) Das folgende Beispiel für eine Ablaufverfolgung wurde mit **includehex** generiert.</span><span class="sxs-lookup"><span data-stu-id="8266f-114">(For detailed information about this attribute, see [How to: Configure Network Tracing](how-to-configure-network-tracing.md).) The following example trace was generated using **includehex**.</span></span>  
  
 `[1692]   (1142)   00000000 : 47 45 54 20 2F 77 70 61-64 2E 64 61 74 20 48 54 : GET /wpad.dat HT`  
  
 `[1692]   (1142)   00000010 : 54 50 2F 31 2E 31 0D 0A-48 6F 73 74 3A 20 69 74 : TP/1.1..Host: it`  
  
 `[1692]   (1142)   00000020 : 67 70 72 6F 78 79 0D 0A-43 6F 6E 6E 65 63 74 69 : gproxy..Connecti`  
  
 `[1692]   (1142)   00000030 : 6F 6E 3A 20 43 6C 6F 73-65 0D 0A 0D 0A     : on: Close....`  
  
 <span data-ttu-id="8266f-115">Geben Sie **protocolonly** als Wert des Attributs **tracemode** an, um die hexadezimalen Daten auszulassen.</span><span class="sxs-lookup"><span data-stu-id="8266f-115">To omit hexadecimal data, specify **protocolonly** as the value for the **tracemode** attribute.</span></span> <span data-ttu-id="8266f-116">Das folgende Beispiel zeigt die Ablaufverfolgung für **protocolonly**.</span><span class="sxs-lookup"><span data-stu-id="8266f-116">The following example shows the trace when **protocolonly** is specified.</span></span>  
  
 `[2444]   (594)   Data from ConnectStream#33574638::WriteHeaders<<GET /wpad.dat HTTP/1.1`  
  
 `Host: itgproxy`  
  
 `Connection: Close`  
  
## <a name="see-also"></a><span data-ttu-id="8266f-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8266f-117">See also</span></span>

- [<span data-ttu-id="8266f-118">Aktivieren der Netzwerkablaufverfolgung</span><span class="sxs-lookup"><span data-stu-id="8266f-118">Enabling Network Tracing</span></span>](enabling-network-tracing.md)
- [<span data-ttu-id="8266f-119">How to: Konfigurieren der Netzwerkablaufverfolgung</span><span class="sxs-lookup"><span data-stu-id="8266f-119">How to: Configure Network Tracing</span></span>](how-to-configure-network-tracing.md)
- [<span data-ttu-id="8266f-120">Netzwerkablaufverfolgung in .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8266f-120">Network Tracing in the .NET Framework</span></span>](network-tracing.md)
