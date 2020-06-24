---
title: Erstellen eines WCF Data Service in Visual Studio
description: Erfahren Sie, wie Sie einen Beispiel Datendienst erstellen, der WCF Data Services verwendet, um einen odata-Feed auf der Grundlage einer Beispieldatenbank verfügbar zu machen.
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: 739cb6971209792724a2e939ca4f4821d5879c8c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247790"
---
# <a name="create-the-data-service"></a><span data-ttu-id="560ad-103">Erstellen des Datendiensts</span><span class="sxs-lookup"><span data-stu-id="560ad-103">Create the data service</span></span>

<span data-ttu-id="560ad-104">In diesem Thema erstellen Sie einen Beispiel Datendienst, der WCF Data Services verwendet, um einen Open Data Protocol-Feed (odata) verfügbar zu machen, der auf der Beispieldatenbank Northwind basiert.</span><span class="sxs-lookup"><span data-stu-id="560ad-104">In this topic, you create a sample data service that uses WCF Data Services to expose an Open Data Protocol (OData) feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="560ad-105">Die Aufgabe umfasst die folgenden grundlegenden Schritte:</span><span class="sxs-lookup"><span data-stu-id="560ad-105">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="560ad-106">Erstellen Sie eine ASP.NET-Webanwendung.</span><span class="sxs-lookup"><span data-stu-id="560ad-106">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="560ad-107">Definieren Sie das Datenmodell mit den Entity Data Model-Tools.</span><span class="sxs-lookup"><span data-stu-id="560ad-107">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="560ad-108">Fügen Sie den Datendienst der Webanwendung hinzu.</span><span class="sxs-lookup"><span data-stu-id="560ad-108">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="560ad-109">Aktivieren Sie den Zugriff auf den Datendienst.</span><span class="sxs-lookup"><span data-stu-id="560ad-109">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="560ad-110">Erstellen der ASP.net-Web-App</span><span class="sxs-lookup"><span data-stu-id="560ad-110">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="560ad-111">Wählen Sie in Visual Studio im Menü **Datei** die Optionen **Neu** > **Projekt** aus.</span><span class="sxs-lookup"><span data-stu-id="560ad-111">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="560ad-112">Wählen Sie im Dialogfeld **Neues Projekt** unter entweder Visual Basic oder Visual c# die Kategorie **Web** aus, und wählen Sie dann **ASP.NET Webanwendung**aus.</span><span class="sxs-lookup"><span data-stu-id="560ad-112">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="560ad-113">Geben Sie `NorthwindService` als Namen für das Projekt ein, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="560ad-113">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="560ad-114">Wählen Sie im Dialogfeld **neue ASP.NET Webanwendung** die Option **leer** aus, und klicken Sie dann auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="560ad-114">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="560ad-115">(Optional) Geben Sie eine bestimmte Portnummer für die Webanwendung an.</span><span class="sxs-lookup"><span data-stu-id="560ad-115">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="560ad-116">Hinweis: die Portnummer `12345` wird in dieser Reihe von Schnellstart Themen verwendet.</span><span class="sxs-lookup"><span data-stu-id="560ad-116">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="560ad-117">Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das ASP.net-Projekt, das Sie gerade erstellt haben, und wählen Sie dann **Eigenschaften**aus.</span><span class="sxs-lookup"><span data-stu-id="560ad-117">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="560ad-118">Wählen Sie die Registerkarte **Web** aus, und legen Sie den Wert für das Textfeld **bestimmter Port** auf fest `12345` .</span><span class="sxs-lookup"><span data-stu-id="560ad-118">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="560ad-119">Definieren des Datenmodells</span><span class="sxs-lookup"><span data-stu-id="560ad-119">Define the data model</span></span>

1. <span data-ttu-id="560ad-120">Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf den Namen des ASP.NET-Projekts, und klicken Sie dann auf **Add**  >  **Neues Element**hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="560ad-120">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="560ad-121">Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Kategorie **Daten** aus, und wählen Sie dann **ADO.NET Entity Data Model**aus.</span><span class="sxs-lookup"><span data-stu-id="560ad-121">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="560ad-122">Geben Sie als Name des Datenmodells ein `Northwind.edmx` .</span><span class="sxs-lookup"><span data-stu-id="560ad-122">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="560ad-123">Wählen Sie im **Entity Data Model-Assistenten**die Option EF- **Designer aus Datenbank aus**, und klicken Sie dann auf **weiter**.</span><span class="sxs-lookup"><span data-stu-id="560ad-123">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="560ad-124">Verbinden Sie das Datenmodell mit der Datenbank, indem Sie einen der folgenden Schritte ausführen, und klicken Sie dann auf **weiter**:</span><span class="sxs-lookup"><span data-stu-id="560ad-124">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="560ad-125">Wenn Sie noch keine Datenbankverbindung konfiguriert haben, klicken Sie auf **neue Verbindung** , und erstellen Sie eine neue Verbindung.</span><span class="sxs-lookup"><span data-stu-id="560ad-125">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="560ad-126">Weitere Informationen finden Sie unter [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="560ad-126">For more information, see [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="560ad-127">Dieser SQL Server-Instanz muss die Northwind-Beispieldatenbank angefügt sein.</span><span class="sxs-lookup"><span data-stu-id="560ad-127">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="560ad-128">\- oder -</span><span class="sxs-lookup"><span data-stu-id="560ad-128">\- or -</span></span>

    - <span data-ttu-id="560ad-129">Wenn bereits eine Datenbankverbindung für die Northwind-Datenbank konfiguriert wurde, wählen Sie diese Verbindung in der Liste der Verbindungen aus.</span><span class="sxs-lookup"><span data-stu-id="560ad-129">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="560ad-130">Aktivieren Sie auf der letzten Seite des Assistenten die Kontrollkästchen für alle Tabellen in der Datenbank, und deaktivieren Sie die Kontrollkästchen für Sichten und gespeicherte Prozeduren.</span><span class="sxs-lookup"><span data-stu-id="560ad-130">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="560ad-131">Klicken Sie auf **Fertig stellen**, und beenden Sie den Assistenten.</span><span class="sxs-lookup"><span data-stu-id="560ad-131">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="560ad-132">Erstellen des WCF-Daten Dienstanbieter</span><span class="sxs-lookup"><span data-stu-id="560ad-132">Create the WCF data service</span></span>

1. <span data-ttu-id="560ad-133">Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Projekt ASP.net, und wählen Sie dann **Add**  >  **Neues Element**hinzufügen aus.</span><span class="sxs-lookup"><span data-stu-id="560ad-133">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="560ad-134">Wählen Sie im Dialogfeld **Neues Element hinzufügen** die Element Vorlage **WCF-Datendienst** aus der Kategorie **Web** aus.</span><span class="sxs-lookup"><span data-stu-id="560ad-134">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![WCF Data Service-Element Vorlage in Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="560ad-136">Die **WCF Data Service** -Vorlage ist in Visual Studio 2015 verfügbar, aber nicht in Visual Studio 2017 oder höher.</span><span class="sxs-lookup"><span data-stu-id="560ad-136">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="560ad-137">Geben Sie als Namen für den Dienst ein `Northwind` .</span><span class="sxs-lookup"><span data-stu-id="560ad-137">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="560ad-138">Visual Studio erstellt das XML-Markup und die Codedateien für den neuen Dienst.</span><span class="sxs-lookup"><span data-stu-id="560ad-138">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="560ad-139">In der Standardeinstellung wird das Fenster des Code-Editors geöffnet.</span><span class="sxs-lookup"><span data-stu-id="560ad-139">By default, the code-editor window opens.</span></span> <span data-ttu-id="560ad-140">In **Projektmappen-Explorer**hat der Dienst den Namen "Northwind" mit der Erweiterung " *. svc.cs* " oder " *. svc. vb*".</span><span class="sxs-lookup"><span data-stu-id="560ad-140">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="560ad-141">Ersetzen Sie im Code für den Datendienst in der Definition der Klasse, die den Datendienst definiert, den Kommentar `/* TODO: put your data source class name here */` durch den Typ des Entitätscontainers des Datenmodells, in diesem Fall `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="560ad-141">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="560ad-142">Die Klassendefinition sollte wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="560ad-142">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="560ad-143">Aktivieren des Zugriffs auf Datendienst Ressourcen</span><span class="sxs-lookup"><span data-stu-id="560ad-143">Enable access to data service resources</span></span>

1. <span data-ttu-id="560ad-144">Ersetzen Sie im Code für den Datendienst den Platzhaltercode in der `InitializeService`-Funktion durch Folgendes:</span><span class="sxs-lookup"><span data-stu-id="560ad-144">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="560ad-145">So können autorisierte Clients, Lese- und Schreibzugriff auf Ressourcen für die angegebenen Entitätenmengen erhalten.</span><span class="sxs-lookup"><span data-stu-id="560ad-145">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="560ad-146">Jeder Client, der auf die ASP.NET-Anwendung zugreifen kann, kann auch auf die vom Datendienst verfügbar gemachten Ressourcen zugreifen.</span><span class="sxs-lookup"><span data-stu-id="560ad-146">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="560ad-147">Sie sollten in einem Produktionsdatendienst auch die Anwendung selbst sichern, um nicht autorisierten Zugriff auf Ressourcen zu verhindern.</span><span class="sxs-lookup"><span data-stu-id="560ad-147">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="560ad-148">Weitere Informationen finden Sie unter [Securing WCF Data Services](securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="560ad-148">For more information, see [Securing WCF Data Services](securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="560ad-149">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="560ad-149">Next steps</span></span>

<span data-ttu-id="560ad-150">Sie haben erfolgreich einen neuen Datendienst erstellt, der einen auf der Northwind-Beispieldatenbank basierenden odata-Feed verfügbar macht. Sie haben den Zugriff auf den Feed für Clients aktiviert, die über Berechtigungen für die ASP.NET-Webanwendung verfügen.</span><span class="sxs-lookup"><span data-stu-id="560ad-150">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="560ad-151">Als nächstes starten Sie den Datendienst aus Visual Studio und greifen auf den odata-Feed zu, indem Sie HTTP GET-Anforderungen über einen Webbrowser senden:</span><span class="sxs-lookup"><span data-stu-id="560ad-151">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="560ad-152">Zugreifen auf den Dienst über einen Webbrowser</span><span class="sxs-lookup"><span data-stu-id="560ad-152">Access the service from a web browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="560ad-153">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="560ad-153">See also</span></span>

- <span data-ttu-id="560ad-154">[ADO.NET-Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="560ad-154">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
