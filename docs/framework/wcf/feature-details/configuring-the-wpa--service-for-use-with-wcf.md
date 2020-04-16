---
title: Konfigurieren des Windows-Prozessaktivierungsdiensts zur Verwendung mit Windows Communication Foundation
ms.date: 03/30/2017
ms.assetid: 1d50712e-53cd-4773-b8bc-a1e1aad66b78
ms.openlocfilehash: 86e50b80d84479ca32b3d4d1fe3f205983640c76
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464169"
---
# <a name="configuring-the-windows-process-activation-service-for-use-with-windows-communication-foundation"></a>Konfigurieren des Windows-Prozessaktivierungsdiensts zur Verwendung mit Windows Communication Foundation
In diesem Thema werden die Schritte beschrieben, die zum Einrichten des Windows-Prozessaktivierungsdienstes (auch als WAS bezeichnet) in Windows Vista erforderlich sind, um Windows Communication Foundation (WCF)-Dienste zu hosten, die nicht über HTTP-Netzwerkprotokolle kommunizieren. In den folgenden Abschnitten werden die für diese Konfiguration erforderlichen Schritte kurz beschrieben:  
  
- Installieren (oder bestätigen Sie die Installation) der erforderlichen WCF-Aktivierungskomponenten.  
  
- Erstellen Sie eine WAS-Site mit den Netzwerkprotokollbindungen, die Sie verwenden möchten, oder fügen Sie einer vorhandenen Site eine neue Protokollbindung hinzu.  
  
- Erstellen Sie eine Anwendung, die als Host der Dienste fungieren soll, und bereiten Sie diese Anwendung auf die Verwendung der erforderlichen Netzwerkprotokolle vor.  
  
- Erstellen Sie einen WCF-Dienst, der einen Nicht-HTTP-Endpunkt verfügbar macht.  
  
## <a name="configuring-a-site-with-non-http-bindings"></a>Konfigurieren einer Site mit Nicht-HTTP-Bindungen  
 Damit eine Nicht-HTTP-Bindung in WAS verwendet werden kann, muss die Sitebindung der WAS-Konfiguration hinzugefügt werden. Die WAS-Konfiguration wird in der Datei applicationHost.config im Verzeichnis %windir%\system32\inetsrv\config gespeichert. Diese Konfigurationsdatei wird sowohl für WAS als auch für IIS&#160;7.0 genutzt.  
  
 Bei der Datei applicationHost.config handelt es sich um eine XML-Textdatei, die mit jedem Standardtexteditor (wie Editor) geöffnet werden kann. Das IIS 7.0-Befehlszeilenkonfigurationstool (appcmd.exe) ist jedoch die bevorzugte Methode zum Hinzufügen von Nicht-HTTP-Standortbindungen.  
  
 Mit dem folgenden Befehl wird mit appcmd.exe eine net.tcp-Sitebindung der Standardwebsite hinzugefügt (der gesamte Befehl wird in eine Zeile eingegeben).  
  
```console  
appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
```  
  
 Mit dem folgenden Befehl wird die neue net.tcp-Sitebindung der Standardwebsite hinzugefügt, indem die unten dargestellte Zeile in die Datei „applicationHost.config“ eingefügt wird.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
        <bindings>  
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            //The following line is added by the command.  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
        </bindings>  
    </site>  
</sites>  
```  
  
## <a name="enabling-an-application-to-use-non-http-protocols"></a>Aktivieren der Verwendung von Nicht-HTTP-Protokollen auf Anwendungsebene  
 Sie können einzelne Netzwerkprotokolle auf Anwendungsebene aktivieren oder deaktivieren. Der folgende Befehl veranschaulicht, wie die Protokolle HTTP und net.tcp für eine Anwendung aktiviert werden, die auf der `Default Web Site` ausgeführt wird.  
  
```console  
appcmd.exe set app "Default Web Site/appOne" /enabledProtocols:net.tcp  
```  
  
 Die Liste der aktivierten Protokolle \<kann auch in der anwendungDefaults>-Element der XML-Konfiguration der Site festgelegt werden, die in ApplicationHost.config gespeichert ist.  
  
 Der folgende XML-Code aus applicationHost.config veranschaulicht eine Site, die sowohl an HTTP als auch an Nicht-HTTP-Protokolle gebunden ist. Die zusätzliche Konfiguration, die zur Unterstützung von Nicht-HTTP-Protokollen erforderlich ist, wird durch Kommentare hervorgehoben.  
  
```xml  
<sites>  
    <site name="Default Web Site" id="1">  
      <application path="/">  
        <virtualDirectory path="/" physicalPath="D:\inetpub\wwwroot" />  
      </application>  
      <bindings>  
            <!-- The following two lines are added by the command. -->
            <binding protocol="HTTP" bindingInformation="*:80:" />  
            <binding protocol="net.tcp" bindingInformation="808:*" />  
       </bindings>  
    </site>  
    <siteDefaults>  
        <logFile
        customLogPluginClsid="{FF160663-DE82-11CF-BC0A-00AA006111E0}"  
          directory="D:\inetpub\logs\LogFiles" />  
        <traceFailedRequestsLogging
          directory="D:\inetpub\logs\FailedReqLogFiles" />  
    </siteDefaults>  
    <applicationDefaults
      applicationPool="DefaultAppPool"
      <!-- The following line is inserted by the command. -->
      enabledProtocols="http, net.tcp" />  
    <virtualDirectoryDefaults allowSubDirConfig="true" />  
</sites>  
```  
  
 Wenn Sie versuchen, einen Dienst mithilfe von WAS zur Aktivierung von Nicht-HTTP-Protokollen zu aktivieren, und WAS nicht installiert und konfiguriert ist, erhalten Sie möglicherweise folgende Fehlermeldung:  
  
```output  
[InvalidOperationException: The protocol 'net.tcp' does not have an implementation of HostedTransportConfiguration type registered.]   System.ServiceModel.AsyncResult.End(IAsyncResult result) +15778592   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.End(IAsyncResult result) +15698937   System.ServiceModel.Activation.HostedHttpRequestAsyncResult.ExecuteSynchronous(HttpApplication context, Boolean flowContext) +265   System.ServiceModel.Activation.HttpModule.ProcessRequest(Object sender, EventArgs e) +227   System.Web.SyncEventExecutionStep.System.Web.HttpApplication.IExecutionStep.Execute() +80   System.Web.HttpApplication.ExecuteStep(IExecutionStep step, Boolean& completedSynchronously) +171  
```  
  
 Wenn dieser Fehler angezeigt wird, stellen Sie sicher, dass WAS zur Aktivierung von Nicht-HTTP-Protokollen installiert und ordnungsgemäß konfiguriert ist. Weitere Informationen finden Sie unter [Gewusst wie: Installieren und Konfigurieren von WCF-Aktivierungskomponenten](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md).  
  
## <a name="building-a-wcf-service-that-uses-was-for-non-http-activation"></a>Erstellen eines WCF-Diensts, der WAS zur Aktivierung von Nicht-HTTP-Protokollen verwendet  
 Nachdem Sie die Schritte zum Installieren und Konfigurieren von WAS ausgeführt haben (siehe [Gewusst wie: Installieren und Konfigurieren von WCF-Aktivierungskomponenten](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)), ähnelt die Konfiguration eines Dienstes, der in IIS gehostet wird, mit der Verwendung von WAS für die Aktivierung.  
  
 Ausführliche Anweisungen zum Erstellen eines WAS-aktivierten WCF-Dienstes finden Sie unter [Gewusst wie: Hosten eines WCF-Dienstes in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
## <a name="see-also"></a>Weitere Informationen

- [Hosten in WAS (Windows Process Activation Service)](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)
- [Windows Server AppFabric-Hostingfunktionen](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
