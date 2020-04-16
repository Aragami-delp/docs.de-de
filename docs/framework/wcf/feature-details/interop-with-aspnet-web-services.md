---
title: Interoperabilität mit ASP.NET-Webdiensten
ms.date: 03/30/2017
ms.assetid: 622422f8-6651-442f-b8be-e654a4aabcac
ms.openlocfilehash: 41810d8044e4b7ff3193950a914edbf1e61cffb1
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464093"
---
# <a name="interoperability-with-aspnet-web-services"></a><span data-ttu-id="988dc-102">Interoperabilität mit ASP.NET-Webdiensten</span><span class="sxs-lookup"><span data-stu-id="988dc-102">Interoperability with ASP.NET Web Services</span></span>
<span data-ttu-id="988dc-103">Die Interoperabilität zwischen ASP.NET Webdiensten und WCF-Webdiensten (Windows Communication Foundation) kann erreicht werden, indem sichergestellt wird, dass Dienste, die mit beiden Technologien implementiert werden, der WS-I Basic Profile 1.1-Spezifikation entsprechen.</span><span class="sxs-lookup"><span data-stu-id="988dc-103">Interoperability between ASP.NET Web services and Windows Communication Foundation (WCF) Web services can be achieved by ensuring that services implemented using both technologies conform to the WS-I Basic Profile 1.1 specification.</span></span> <span data-ttu-id="988dc-104">ASP.NET Webdienste, die WS-I Basic Profile 1.1 entsprechen, mit WCF-Clients mithilfe <xref:System.ServiceModel.BasicHttpBinding>der vom WCF bereitgestellten Bindung interoperabel sind.</span><span class="sxs-lookup"><span data-stu-id="988dc-104">ASP.NET Web services that conform to WS-I Basic Profile 1.1 are interoperable with WCF clients by using WCF system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
 <span data-ttu-id="988dc-105">Verwenden Sie ASP.NET 2.0-Option, um die <xref:System.Web.Services.WebService> und-Attribute <xref:System.Web.Services.WebMethodAttribute> zu einer Schnittstelle anstatt zu einer Klasse hinzuzufügen und eine Klasse zum Implementieren der Schnittstelle zu schreiben, wie im folgenden Beispielcode gezeigt.</span><span class="sxs-lookup"><span data-stu-id="988dc-105">Use ASP.NET 2.0 option of adding the <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> attributes to an interface rather than to a class, and writing a class to implement the interface, as shown in the following sample code.</span></span>  
  
```csharp
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="988dc-106">Die Verwendung dieser Option wird empfohlen, da die Schnittstelle mit dem <xref:System.Web.Services.WebService>-Attribut einen Vertrag für die vom Dienst ausgeführten Vorgänge darstellt. Dieser Vertrag kann wiederholt für verschiedene Klassen verwendet werden, die den gleichen Vertrag möglicherweise auf unterschiedliche Art und Weise implementieren.</span><span class="sxs-lookup"><span data-stu-id="988dc-106">Using this option is preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="988dc-107">Verwenden Sie das <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute>-Attribut nicht, um Nachrichten basierend auf dem voll qualifizierten Namen des Textelements der SOAP-Nachricht anstatt des `SOAPAction`-HTTP-Headers an Methoden weiterzuleiten.</span><span class="sxs-lookup"><span data-stu-id="988dc-107">Avoid using the <xref:System.Web.Services.Protocols.SoapDocumentServiceAttribute> attribute to have messages routed to methods based on the fully-qualified name of the body element of the SOAP message rather than the `SOAPAction` HTTP header.</span></span> <span data-ttu-id="988dc-108">WCF verwendet `SOAPAction` den HTTP-Header zum Weiterleiten von Nachrichten.</span><span class="sxs-lookup"><span data-stu-id="988dc-108">WCF uses the `SOAPAction` HTTP header for routing messages.</span></span>  
  
 <span data-ttu-id="988dc-109">Die XML, in die <xref:System.Xml.Serialization.XmlSerializer> standardmäßig einen Typ serialisiert, ist semantisch identisch mit der XML, in die <xref:System.Runtime.Serialization.DataContractSerializer> einen Typ serialisiert, vorausgesetzt, der Namespace ist für die XML explizit definiert.</span><span class="sxs-lookup"><span data-stu-id="988dc-109">The XML into which <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="988dc-110">Gehen Sie beim Definieren eines Datentyps für die Verwendung mit ASP.NETWeb-Diensten im Vorgriff auf die Einführung von WCF wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="988dc-110">When defining a data type for use with ASP.NETWeb services in anticipation of adopting WCF, do the following:</span></span>  
  
- <span data-ttu-id="988dc-111">Definieren Sie den Typ mit .NET Framework-Klassen und nicht mit dem XML-Schema.</span><span class="sxs-lookup"><span data-stu-id="988dc-111">Define the type using .NET Framework classes rather than XML Schema.</span></span>  
  
- <span data-ttu-id="988dc-112">Fügen Sie der Klasse lediglich <xref:System.SerializableAttribute> und <xref:System.Xml.Serialization.XmlRootAttribute> hinzu, wobei Sie mit dem zweiten Attribut den Namespace für den Typ explizit definieren.</span><span class="sxs-lookup"><span data-stu-id="988dc-112">Add only the <xref:System.SerializableAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the class, using the latter to explicitly define the namespace for the type.</span></span> <span data-ttu-id="988dc-113">Fügen Sie keine zusätzlichen Attribute aus dem <xref:System.Xml.Serialization>-Namespace hinzu, um die Übersetzung der .NET Framework-Klasse in XML zu steuern.</span><span class="sxs-lookup"><span data-stu-id="988dc-113">Do not add additional attributes from the <xref:System.Xml.Serialization> namespace to control how the .NET Framework class is to be translated into XML.</span></span>  
  
- <span data-ttu-id="988dc-114">Wenn Sie diese Vorgehensweise wählen, sollte es später kein Problem darstellen, die .NET-Klassen in Datenverträge umzuwandeln, indem Sie <xref:System.Runtime.Serialization.DataContractAttribute> und <xref:System.Runtime.Serialization.DataMemberAttribute> hinzufügen, ohne die XML erheblich zu ändern, in die die Klassen für die Übertragung serialisiert werden.</span><span class="sxs-lookup"><span data-stu-id="988dc-114">By adopting this approach, you should be able to later make the .NET classes into data contracts with the addition of the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> without significantly altering the XML into which the classes are serialized for transmission.</span></span> <span data-ttu-id="988dc-115">Die typen, die in Nachrichten von ASP.NET Webdiensten verwendet werden, können von WCF-Anwendungen als Datenverträge verarbeitet werden, was unter anderem zu einer besseren Leistung in WCF-Anwendungen führt.</span><span class="sxs-lookup"><span data-stu-id="988dc-115">The types used in messages by ASP.NET Web services can be processed as data contracts by WCF applications, yielding, among other benefits, better performance in WCF applications.</span></span>  
  
 <span data-ttu-id="988dc-116">Vermeiden Sie die Verwendung der von den Internetinformationsdiensten (IIS) bereitgestellten Authentifizierungsoptionen.</span><span class="sxs-lookup"><span data-stu-id="988dc-116">Avoid using the authentication options provided by Internet Information Services (IIS).</span></span> <span data-ttu-id="988dc-117">WCF-Clients unterstützen sie nicht.</span><span class="sxs-lookup"><span data-stu-id="988dc-117">WCF clients do not support them.</span></span> <span data-ttu-id="988dc-118">Wenn ein Dienst gesichert werden muss, verwenden Sie die von WCF bereitgestellten Optionen, da diese Optionen robust sind und auf Standardprotokollen basieren.</span><span class="sxs-lookup"><span data-stu-id="988dc-118">If a service must be secured, use the options provided by WCF, because these options are robust and are based on standard protocols.</span></span>  
  
## <a name="performance-impact-caused-by-loading-the-servicemodel-httpmodule"></a><span data-ttu-id="988dc-119">Durch das Laden von ServiceModel HttpModule verursachte Leistungsbeeinträchtigungen</span><span class="sxs-lookup"><span data-stu-id="988dc-119">Performance impact caused by loading the ServiceModel HttpModule</span></span>  
 <span data-ttu-id="988dc-120">In .NET Framework&#160;3.0 wurde das WCF-`HttpModule`-Element in der Stammdatei Web.config installiert, sodass jede ASP.NET-Anwendung WCF unterstützte.</span><span class="sxs-lookup"><span data-stu-id="988dc-120">In the .NET Framework 3.0, the WCF `HttpModule` was installed in the root Web.config file such that every ASP.NET application was WCF enabled.</span></span> <span data-ttu-id="988dc-121">Dies kann die Leistung beeinträchtigen. Sie können daher `ServiceModel` für die Datei Web.config entfernen, wie im folgenden Bespiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="988dc-121">This might affect performance, so you can remove `ServiceModel` for the Web.config file as shown in the following example.</span></span>  
  
```xml  
<httpModules>  
    <remove name="ServiceModel" />  
</httpModules>
```  
  
## <a name="see-also"></a><span data-ttu-id="988dc-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="988dc-122">See also</span></span>

- [<span data-ttu-id="988dc-123">Vorgehensweise: Konfigurieren eines WCF-Diensts für die Zusammenarbeit mit ASP.NET-Webdienstclients</span><span class="sxs-lookup"><span data-stu-id="988dc-123">How to: Configure WCF Service to Interoperate with ASP.NET Web Service Clients</span></span>](../../../../docs/framework/wcf/feature-details/config-wcf-service-with-aspnet-web-service.md)
