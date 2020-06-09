---
title: 'Vorgehensweise: Installieren und Konfigurieren von WCF-Aktivierungskomponenten'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: f7a846b076691394cb855e4978e890cdcac76eb2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597032"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="9e5fc-102">Vorgehensweise: Installieren und Konfigurieren von WCF-Aktivierungskomponenten</span><span class="sxs-lookup"><span data-stu-id="9e5fc-102">How to: Install and Configure WCF Activation Components</span></span>

<span data-ttu-id="9e5fc-103">In diesem Thema werden die Schritte beschrieben, die zum Einrichten von Windows Process Activation Service (auch bekannt als was) unter Windows Vista erforderlich sind, um Windows Communication Foundation (WCF)-Dienste zu hosten, die nicht über HTTP-Netzwerkprotokolle kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on Windows Vista to host Windows Communication Foundation (WCF) services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="9e5fc-104">In den folgenden Abschnitten werden die für diese Konfiguration erforderlichen Schritte kurz beschrieben:</span><span class="sxs-lookup"><span data-stu-id="9e5fc-104">The following sections outline the steps for this configuration:</span></span>

- <span data-ttu-id="9e5fc-105">Installieren (oder bestätigen Sie die Installation von) der WCF-Aktivierungs Komponenten.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-105">Install (or confirm the installation of) the WCF activation components.</span></span>

- <span data-ttu-id="9e5fc-106">Konfigurieren Sie WAS, sodass Nicht-HTTP-Protokolle unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="9e5fc-107">Mit dem folgenden Verfahren wird Windows Vista für die TCP-Aktivierung konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-107">The following procedure configures Windows Vista for TCP activation.</span></span>

<span data-ttu-id="9e5fc-108">Nach der Installation und Konfiguration von was finden Sie unter Gewusst [wie: Hosten eines WCF-Diensts in was](how-to-host-a-wcf-service-in-was.md) die Verfahren zum Erstellen eines WCF-Diensts, der einen nicht-HTTP-Endpunkt bereitstellt, der was verwendet.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](how-to-host-a-wcf-service-in-was.md) for the procedures to create a WCF service that exposes an non-HTTP endpoint that employs WAS.</span></span>

## <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="9e5fc-109">So installieren Sie die WCF-Aktivierungskomponenten für andere Protokolle als HTTP</span><span class="sxs-lookup"><span data-stu-id="9e5fc-109">To install the WCF non-HTTP activation components</span></span>

1. <span data-ttu-id="9e5fc-110">Klicken Sie auf die Schaltfläche **Start** und dann auf **Systemsteuerung**.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-110">Click the **Start** button, and then click **Control Panel**.</span></span>

2. <span data-ttu-id="9e5fc-111">Klicken Sie auf **Programme** und dann auf **Programme und Funktionen**.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-111">Click **Programs**, and then click **Programs and Features**.</span></span>

3. <span data-ttu-id="9e5fc-112">Klicken Sie im Menü **Aufgaben** auf **Windows-Funktionen ein-oder ausschalten**.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>

4. <span data-ttu-id="9e5fc-113">Suchen Sie den Knoten WinFX, wählen Sie ihn aus, und erweitern Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-113">Find the WinFX node, select and then expand it.</span></span>

5. <span data-ttu-id="9e5fc-114">Aktivieren Sie das Kontrollkästchen **WCF-nicht-http-Aktivierungs Komponenten** , und speichern Sie die Einstellung.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>

## <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="9e5fc-115">So konfigurieren Sie den WAS, sodass die TCP-Aktivierung unterstützt wird</span><span class="sxs-lookup"><span data-stu-id="9e5fc-115">To configure the WAS to support TCP activation</span></span>

1. <span data-ttu-id="9e5fc-116">Zur Unterstützung der net.tcp-Aktivierung muss die Standardwebsite zuerst an einen net.tcp-Port gebunden werden.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="9e5fc-117">Hierfür können Sie Appcmd. exe verwenden, das mit dem IIS 7,0-Verwaltungs Toolset installiert wird.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-117">You can do this by using Appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="9e5fc-118">Führen Sie in einem Eingabeaufforderungsfenster auf Administratorebene den folgenden Befehl aus.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-118">In an administrator-level Command Prompt window, run the following command.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="9e5fc-119">Dieser Befehl ist eine einzelne Textzeile.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-119">This command is a single line of text.</span></span> <span data-ttu-id="9e5fc-120">Mit dem Befehl wird eine neue net.tcp-Sitebindung der Standardwebsite hinzugefügt, die TCP-Anschluss 808 mit jedem beliebigen Hostnamen überwacht.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>

2. <span data-ttu-id="9e5fc-121">Alle Anwendungen innerhalb einer Site nutzen zwar eine gemeinsame net.tcp-Bindung, aber jede Anwendung kann die net.tcp-Unterstützung unabhängig von den anderen Anwendungen aktivieren.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="9e5fc-122">Um net.tcp für die Anwendung zu aktivieren, führen Sie den folgenden Befehl in einem Eingabeaufforderungsfenster auf Administratorebene aus.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > <span data-ttu-id="9e5fc-123">Dieser Befehl ist eine einzelne Textzeile.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-123">This command is a single line of text.</span></span> <span data-ttu-id="9e5fc-124">Dieser Befehl ermöglicht den Zugriff auf die/- \<*WCF Application*> Anwendung mithilfe von `http://localhost/<WCF Application>` und `net.tcp://localhost/<WCF Application>` .</span><span class="sxs-lookup"><span data-stu-id="9e5fc-124">This command enables the /\<*WCF Application*> application to be accessed using both `http://localhost/<WCF Application>` and `net.tcp://localhost/<WCF Application>`.</span></span>

     <span data-ttu-id="9e5fc-125">Entfernen Sie die net.tcp-Sitebindung, die für dieses Beispiel hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-125">Remove the net.tcp site binding you added for this sample.</span></span>

     <span data-ttu-id="9e5fc-126">Zur Vereinfachung sind die folgenden beiden Schritte in einer Batchdatei namens RemoveNetTcpSiteBinding.cmd implementiert, die sich im Beispielverzeichnis befindet.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="9e5fc-127">Entfernen Sie net.tcp aus der Liste aktivierter Protokolle, indem Sie den folgenden Befehl in einem Eingabeaufforderungsfenster auf Administratorebene ausführen.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="9e5fc-128">Dieser Befehl ist eine einzelne Textzeile.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-128">This command is a single line of text.</span></span>

    2. <span data-ttu-id="9e5fc-129">Entfernen Sie die net.tcp-Sitebindung, indem Sie den folgenden Befehl in einem Eingabeaufforderungsfenster auf Administratorebene ausführen:</span><span class="sxs-lookup"><span data-stu-id="9e5fc-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="9e5fc-130">Dieser Befehl ist eine einzelne Textzeile.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-130">This command is a single line of text.</span></span>

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="9e5fc-131">So entfernen Sie net.tcp aus der Liste aktivierter Protokolle</span><span class="sxs-lookup"><span data-stu-id="9e5fc-131">To remove net.tcp from the list of enabled protocols</span></span>

1. <span data-ttu-id="9e5fc-132">Um net.tcp aus der Liste aktivierter Protokolle zu entfernen, führen Sie den folgenden Befehl in einem Eingabeaufforderungsfenster auf Administratorebene aus.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > <span data-ttu-id="9e5fc-133">Dieser Befehl ist eine einzelne Textzeile.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-133">This command is a single line of text.</span></span>

## <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="9e5fc-134">So entfernen Sie die net.tcp-Bindung</span><span class="sxs-lookup"><span data-stu-id="9e5fc-134">To remove the net.tcp site binding</span></span>

1. <span data-ttu-id="9e5fc-135">Um die net.tcp-Sitebindung zu entfernen, führen Sie den folgenden Befehl in einem Eingabeaufforderungsfenster auf Administratorebene aus.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > <span data-ttu-id="9e5fc-136">Dieser Befehl ist eine einzelne Textzeile.</span><span class="sxs-lookup"><span data-stu-id="9e5fc-136">This command is a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e5fc-137">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="9e5fc-137">See also</span></span>

- [<span data-ttu-id="9e5fc-138">TCP-Aktivierung</span><span class="sxs-lookup"><span data-stu-id="9e5fc-138">TCP Activation</span></span>](../samples/tcp-activation.md)
- [<span data-ttu-id="9e5fc-139">MSMQ-Aktivierung</span><span class="sxs-lookup"><span data-stu-id="9e5fc-139">MSMQ Activation</span></span>](../samples/msmq-activation.md)
- [<span data-ttu-id="9e5fc-140">NamedPipe-Aktivierung</span><span class="sxs-lookup"><span data-stu-id="9e5fc-140">NamedPipe Activation</span></span>](../samples/namedpipe-activation.md)
- <span data-ttu-id="9e5fc-141">[Windows Server AppFabric-Hostingfunktionen](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9e5fc-141">[Windows Server App Fabric Hosting Features](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
