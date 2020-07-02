---
title: Anwendungs Ressourcen-, Inhalts-und Datendateien
description: Informieren Sie sich über die besondere Unterstützung für die Konfiguration, Identifizierung und Verwendung von Anwendungs Datendateien in Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
ms.openlocfilehash: 324b3eb922f0fd1d1d9ad00105a06a7fbdb8effd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622860"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="733a1-103">WPF-Anwendungsressource, Inhalts- und Datendateien</span><span class="sxs-lookup"><span data-stu-id="733a1-103">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="733a1-104">Microsoft Windows-Anwendungen sind häufig von Dateien abhängig, die nicht ausführbare Daten enthalten, z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . b. Bilder, Videos und Audiodaten.</span><span class="sxs-lookup"><span data-stu-id="733a1-104">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="733a1-105">Windows Presentation Foundation (WPF) bietet spezielle Unterstützung für das konfigurieren, identifizieren und Verwenden dieser Daten Dateitypen, die als Anwendungs Datendateien bezeichnet werden.</span><span class="sxs-lookup"><span data-stu-id="733a1-105">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="733a1-106">Diese Unterstützung bezieht sich auf einen bestimmten Satz von Anwendungsdatendateitypen, einschließlich:</span><span class="sxs-lookup"><span data-stu-id="733a1-106">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="733a1-107">**Ressourcen Dateien**: Datendateien, die entweder in eine ausführbare Datei oder in eine WPF-Bibliotheks Assembly kompiliert werden.</span><span class="sxs-lookup"><span data-stu-id="733a1-107">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="733a1-108">**Inhalts Dateien**: eigenständige Datendateien, die über eine explizite Zuordnung zu einer ausführbaren WPF-Assembly verfügen.</span><span class="sxs-lookup"><span data-stu-id="733a1-108">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="733a1-109">**Dateien der Ursprungs Site**: eigenständige Datendateien, die keiner ausführbaren WPF-Assembly zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="733a1-109">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="733a1-110">Ein wichtiger Unterschied zwischen diesen drei Dateitypen besteht darin, dass die Ressourcen- und Inhaltsdateien zur Buildzeit bekannt sind. Sie sind einer Assembly explizit bekannt.</span><span class="sxs-lookup"><span data-stu-id="733a1-110">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="733a1-111">Für Dateien der Ursprungs Site ist eine Assembly jedoch möglicherweise überhaupt nicht bekannt oder implizites Wissen durch einen URI-Verweis (Uniform Resource Identifier) des Pakets. bei letzterem gibt es keine Garantie dafür, dass die referenzierte Site der Ursprungs Datei tatsächlich vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="733a1-111">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="733a1-112">Um auf Anwendungs Datendateien zu verweisen, verwendet Windows Presentation Foundation (WPF) das Paket-URI-Schema (Uniform Resource Identifier), das unter [Paket-URIs in WPF](pack-uris-in-wpf.md)ausführlich beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="733a1-112">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="733a1-113">In diesem Thema wird beschrieben, wie Sie Anwendungsdatendateien konfigurieren und verwenden.</span><span class="sxs-lookup"><span data-stu-id="733a1-113">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>
## <a name="resource-files"></a><span data-ttu-id="733a1-114">Ressourcendateien</span><span class="sxs-lookup"><span data-stu-id="733a1-114">Resource Files</span></span>  
 <span data-ttu-id="733a1-115">Wenn eine Anwendungsdatendatei einer Anwendung stets zur Verfügung stehen muss, kann die Verfügbarkeit nur dadurch gewährleistet werden, dass die Datei in eine der ausführbaren Hauptassemblys einer Anwendung oder in eine der Assemblys kompiliert wird, auf die verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="733a1-115">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="733a1-116">Diese Art von Anwendungs Datendatei wird als *Ressourcen Datei*bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="733a1-116">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="733a1-117">Verwenden Sie die Ressourcendateien in folgenden Fällen:</span><span class="sxs-lookup"><span data-stu-id="733a1-117">You should use resource files when:</span></span>  
  
- <span data-ttu-id="733a1-118">Sie müssen den Inhalt der Ressourcendatei nicht aktualisieren, nachdem sie in eine Assembly kompiliert wurde.</span><span class="sxs-lookup"><span data-stu-id="733a1-118">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="733a1-119">Sie möchten die Komplexität der Anwendungsverteilung vereinfachen, indem Sie die Anzahl von Dateiabhängigkeiten verringern.</span><span class="sxs-lookup"><span data-stu-id="733a1-119">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="733a1-120">Die Anwendungs Datendatei muss lokalisiert werden können (Weitere Informationen finden Sie unter [Übersicht über WPF-Globalisierung und-Lokalisierung](../advanced/wpf-globalization-and-localization-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="733a1-120">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="733a1-121">Die in diesem Abschnitt beschriebenen Ressourcen Dateien unterscheiden sich von den in [XAML-Ressourcen](../../../desktop-wpf/fundamentals/xaml-resources-define.md) beschriebenen Ressourcen Dateien und unterscheiden sich von den in [Verwalten von Anwendungs Ressourcen (.net)](/visualstudio/ide/managing-application-resources-dotnet)beschriebenen eingebetteten oder verknüpften Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="733a1-121">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="733a1-122">Konfigurieren von Ressourcendateien</span><span class="sxs-lookup"><span data-stu-id="733a1-122">Configuring Resource Files</span></span>  
 <span data-ttu-id="733a1-123">In WPF ist eine Ressourcen Datei eine Datei, die in einem Microsoft Build Engine (MSBuild)-Projekt als-Element enthalten ist `Resource` .</span><span class="sxs-lookup"><span data-stu-id="733a1-123">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="733a1-124">In Visual Studio erstellen Sie eine Ressourcen Datei, indem Sie einem Projekt eine Datei hinzufügen und `Build Action` auf festlegen `Resource` .</span><span class="sxs-lookup"><span data-stu-id="733a1-124">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="733a1-125">Wenn das Projekt erstellt wird, kompiliert MSBuild die Ressource in die Assembly.</span><span class="sxs-lookup"><span data-stu-id="733a1-125">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="733a1-126">Verwenden von Ressourcendateien</span><span class="sxs-lookup"><span data-stu-id="733a1-126">Using Resource Files</span></span>  
 <span data-ttu-id="733a1-127">Wenn Sie eine Ressourcen Datei laden möchten, können Sie die- <xref:System.Windows.Application.GetResourceStream%2A> Methode der-Klasse aufzurufen <xref:System.Windows.Application> , indem Sie einen Paket-URI übergeben, der die gewünschte Ressourcen Datei identifiziert.</span><span class="sxs-lookup"><span data-stu-id="733a1-127">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="733a1-128"><xref:System.Windows.Application.GetResourceStream%2A>Gibt ein <xref:System.Windows.Resources.StreamResourceInfo> -Objekt zurück, das die Ressourcen Datei als verfügbar macht <xref:System.IO.Stream> und den Inhaltstyp beschreibt.</span><span class="sxs-lookup"><span data-stu-id="733a1-128"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="733a1-129">Der folgende Code zeigt beispielsweise, wie <xref:System.Windows.Application.GetResourceStream%2A> Sie mit eine <xref:System.Windows.Controls.Page> Ressourcen Datei laden und als Inhalt einer <xref:System.Windows.Controls.Frame> () festlegen `pageFrame` :</span><span class="sxs-lookup"><span data-stu-id="733a1-129">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="733a1-130">Beim Aufrufen <xref:System.Windows.Application.GetResourceStream%2A> von haben Sie Zugriff auf das- <xref:System.IO.Stream> Objekt, das Sie zum Festlegen der Eigenschaft in den Typ der Eigenschaft, mit der Sie ihn festlegen, benötigen.</span><span class="sxs-lookup"><span data-stu-id="733a1-130">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="733a1-131">Stattdessen können Sie das Öffnen und wandeln von WPF durchführen, <xref:System.IO.Stream> indem Sie eine Ressourcen Datei direkt in die-Eigenschaft eines Typs mithilfe von Code laden.</span><span class="sxs-lookup"><span data-stu-id="733a1-131">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="733a1-132">Im folgenden Beispiel wird gezeigt, wie ein <xref:System.Windows.Controls.Page> direkt in ein <xref:System.Windows.Controls.Frame> ( `pageFrame` ) mithilfe von Code geladen wird.</span><span class="sxs-lookup"><span data-stu-id="733a1-132">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="733a1-133">Das folgende Beispiel entspricht dem Markup des vorangehenden Beispiels.</span><span class="sxs-lookup"><span data-stu-id="733a1-133">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="733a1-134">Anwendungscodedateien als Ressourcendateien</span><span class="sxs-lookup"><span data-stu-id="733a1-134">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="733a1-135">Ein spezieller Satz von WPF-Anwendungscode Dateien kann mithilfe von Paket-URIs referenziert werden, einschließlich Fenstern, Seiten, Fluss Dokumenten und Ressourcen Wörterbüchern.</span><span class="sxs-lookup"><span data-stu-id="733a1-135">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="733a1-136">Beispielsweise können Sie die- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> Eigenschaft mit einem Paket-URI festlegen, der auf das Fenster oder die Seite verweist, das Sie beim Starten einer Anwendung laden möchten.</span><span class="sxs-lookup"><span data-stu-id="733a1-136">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="733a1-137">Dies ist möglich, wenn eine XAML-Datei in einem MSBuild-Projekt als- `Page` Element enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="733a1-137">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="733a1-138">In Visual Studio fügen Sie einem Projekt ein neues-,-,-oder-Element hinzu <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationWindow> , das-Element <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.ResourceDictionary> `Build Action` für die Markup Datei wird standardmäßig auf eingestellt `Page` .</span><span class="sxs-lookup"><span data-stu-id="733a1-138">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="733a1-139">Wenn ein Projekt mit `Page` Elementen kompiliert wird, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] werden die Elemente in das Binärformat konvertiert und in die zugehörige Assembly kompiliert.</span><span class="sxs-lookup"><span data-stu-id="733a1-139">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="733a1-140">Folglich können diese Dateien auf die gleiche Weise verwendet werden wie typische Ressourcendateien.</span><span class="sxs-lookup"><span data-stu-id="733a1-140">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="733a1-141">Wenn eine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Datei als `Resource` -Element konfiguriert ist und keine Code-Behind-Datei enthält, wird die Rohdaten [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] in eine Assembly anstatt in eine binäre Version der RAW-Datei kompiliert [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="733a1-141">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>
## <a name="content-files"></a><span data-ttu-id="733a1-142">Inhaltsdateien</span><span class="sxs-lookup"><span data-stu-id="733a1-142">Content Files</span></span>  
 <span data-ttu-id="733a1-143">Eine *Inhalts Datei* wird neben einer ausführbaren Assembly als lose Datei verteilt.</span><span class="sxs-lookup"><span data-stu-id="733a1-143">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="733a1-144">Obwohl Assemblys nicht in eine Assembly kompiliert werden, werden sie mit Metadaten kompiliert, die eine Zuordnung mit den einzelnen Inhaltsdateien herstellen.</span><span class="sxs-lookup"><span data-stu-id="733a1-144">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="733a1-145">Verwenden Sie Inhaltsdateien, wenn die Anwendung einen speziellen Satz von Anwendungsdatendateien erfordert, die aktualisierbar sein soll, ohne dass die Assembly, die sie verwendet, neu kompiliert werden muss.</span><span class="sxs-lookup"><span data-stu-id="733a1-145">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="733a1-146">Konfigurieren von Inhaltsdateien</span><span class="sxs-lookup"><span data-stu-id="733a1-146">Configuring Content Files</span></span>  
 <span data-ttu-id="733a1-147">Wenn Sie einem Projekt eine Inhalts Datei hinzufügen möchten, muss eine Anwendungs Datendatei als Element eingeschlossen werden `Content` .</span><span class="sxs-lookup"><span data-stu-id="733a1-147">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="733a1-148">Da eine Inhalts Datei nicht direkt in die Assembly kompiliert wird, müssen Sie außerdem das MSBuild- `CopyToOutputDirectory` Metadatenelement festlegen, um anzugeben, dass die Inhalts Datei an einen Speicherort kopiert wird, der relativ zur erstellten Assembly ist.</span><span class="sxs-lookup"><span data-stu-id="733a1-148">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="733a1-149">Wenn Sie möchten, dass die Ressource bei jedem Erstellen eines Projekts in den Buildausgabeordner kopiert wird, legen Sie das `CopyToOutputDirectory` Metadatenelement mit dem `Always` Wert fest.</span><span class="sxs-lookup"><span data-stu-id="733a1-149">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="733a1-150">Andernfalls können Sie mithilfe des-Werts sicherstellen, dass nur die neueste Version der Ressource in den Buildausgabeordner kopiert wird `PreserveNewest` .</span><span class="sxs-lookup"><span data-stu-id="733a1-150">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="733a1-151">Im Folgenden wird eine Datei gezeigt, die als Inhaltsdatei konfiguriert ist und nur dann in den Buildausgabeordner kopiert wird, wenn dem Projekt eine neue Version der Ressource hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="733a1-151">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="733a1-152">In Visual Studio erstellen Sie eine Inhalts Datei, indem Sie einem Projekt eine Datei hinzufügen und `Build Action` auf festlegen `Content` , und legen Sie `Copy to Output Directory` auf fest `Copy always` (identisch mit `Always` ) und `Copy if newer` (identisch mit `PreserveNewest` ).</span><span class="sxs-lookup"><span data-stu-id="733a1-152">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="733a1-153">Wenn das Projekt erstellt wird, <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> wird ein Attribut in die Metadaten der Assembly für jede Inhalts Datei kompiliert.</span><span class="sxs-lookup"><span data-stu-id="733a1-153">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="733a1-154">Der Wert der <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> impliziert den Pfad zur Inhalts Datei relativ zur Position im Projekt.</span><span class="sxs-lookup"><span data-stu-id="733a1-154">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="733a1-155">Wenn sich eine Inhalts Datei z. b. in einem Unterordner des Projekts befindet, werden die zusätzlichen Pfadinformationen in den <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Wert eingefügt.</span><span class="sxs-lookup"><span data-stu-id="733a1-155">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="733a1-156">Der <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> Wert ist auch der Wert des Pfads zur Inhalts Datei im Buildausgabeordner.</span><span class="sxs-lookup"><span data-stu-id="733a1-156">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="733a1-157">Verwenden von Inhaltsdateien</span><span class="sxs-lookup"><span data-stu-id="733a1-157">Using Content Files</span></span>  
 <span data-ttu-id="733a1-158">Wenn Sie eine Inhalts Datei laden möchten, können Sie die- <xref:System.Windows.Application.GetContentStream%2A> Methode der-Klasse aufzurufen <xref:System.Windows.Application> , indem Sie einen Paket-URI übergeben, der die gewünschte Inhalts Datei identifiziert.</span><span class="sxs-lookup"><span data-stu-id="733a1-158">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="733a1-159"><xref:System.Windows.Application.GetContentStream%2A>Gibt ein <xref:System.Windows.Resources.StreamResourceInfo> -Objekt zurück, das die Inhalts Datei als verfügbar macht <xref:System.IO.Stream> und den Inhaltstyp beschreibt.</span><span class="sxs-lookup"><span data-stu-id="733a1-159"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="733a1-160">Im folgenden Codebeispiel wird gezeigt, wie verwendet wird, <xref:System.Windows.Application.GetContentStream%2A> um eine <xref:System.Windows.Controls.Page> Inhalts Datei zu laden und als Inhalt einer <xref:System.Windows.Controls.Frame> () festzulegen `pageFrame` .</span><span class="sxs-lookup"><span data-stu-id="733a1-160">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="733a1-161">Beim Aufrufen <xref:System.Windows.Application.GetContentStream%2A> von haben Sie Zugriff auf das- <xref:System.IO.Stream> Objekt, das Sie zum Festlegen der Eigenschaft in den Typ der Eigenschaft, mit der Sie ihn festlegen, benötigen.</span><span class="sxs-lookup"><span data-stu-id="733a1-161">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="733a1-162">Stattdessen können Sie das Öffnen und wandeln von WPF durchführen, <xref:System.IO.Stream> indem Sie eine Ressourcen Datei direkt in die-Eigenschaft eines Typs mithilfe von Code laden.</span><span class="sxs-lookup"><span data-stu-id="733a1-162">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="733a1-163">Im folgenden Beispiel wird gezeigt, wie ein <xref:System.Windows.Controls.Page> direkt in ein <xref:System.Windows.Controls.Frame> ( `pageFrame` ) mithilfe von Code geladen wird.</span><span class="sxs-lookup"><span data-stu-id="733a1-163">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="733a1-164">Das folgende Beispiel entspricht dem Markup des vorangehenden Beispiels.</span><span class="sxs-lookup"><span data-stu-id="733a1-164">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a><span data-ttu-id="733a1-165">Dateien der Ursprungssite</span><span class="sxs-lookup"><span data-stu-id="733a1-165">Site of Origin Files</span></span>  
 <span data-ttu-id="733a1-166">Ressourcen Dateien haben eine explizite Beziehung zu den Assemblys, die Sie zusammen mit den von definierten Assemblys verteilen <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> .</span><span class="sxs-lookup"><span data-stu-id="733a1-166">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="733a1-167">Es kann jedoch vorkommen, dass Sie eine implizite oder nicht vorhandene Beziehung zwischen einer Assembly und einer Anwendungsdatendatei herstellen, u. a. in folgenden Fällen:</span><span class="sxs-lookup"><span data-stu-id="733a1-167">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="733a1-168">Zum Zeitpunkt der Kompilierung ist keine Datei vorhanden.</span><span class="sxs-lookup"><span data-stu-id="733a1-168">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="733a1-169">Sie wissen bis zur Laufzeit nicht, welche Dateien von der Assembly benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="733a1-169">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="733a1-170">Sie möchten in der Lage sein, Dateien ohne Neukompilierung der Assembly, der sie zugeordnet sind, zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="733a1-170">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="733a1-171">Die Anwendung verwendet große Datendateien, z. B. Audio und Video. Diese sollen von Benutzern nur heruntergeladen werden, wenn sie dies wünschen.</span><span class="sxs-lookup"><span data-stu-id="733a1-171">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="733a1-172">Es ist möglich, diese Dateitypen mithilfe herkömmlicher URI-Schemas (z. b `file:///` . die Schemas und) zu laden `http://` .</span><span class="sxs-lookup"><span data-stu-id="733a1-172">It is possible to load these types of files by using traditional URI schemes, such as the `file:///` and `http://` schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="733a1-173">Die `file:///` -und- `http://` Schemas erfordern jedoch, dass Ihre Anwendung über volle Vertrauenswürdigkeit verfügt.</span><span class="sxs-lookup"><span data-stu-id="733a1-173">However, the `file:///` and `http://` schemes require your application to have full trust.</span></span> <span data-ttu-id="733a1-174">Wenn es sich bei Ihrer Anwendung um eine XAML-Browser Anwendung (XBAP) handelt, die über das Internet oder Intranet gestartet wurde, und nur den Berechtigungs Satz anfordert, der für Anwendungen zulässig ist, die von diesen Speicherorten aus gestartet werden, können lose Dateien nur aus der Ursprungs Site der Anwendung (Start Speicherort) geladen werden.</span><span class="sxs-lookup"><span data-stu-id="733a1-174">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="733a1-175">Solche Dateien werden als Dateien *der Ursprungs Site* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="733a1-175">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="733a1-176">Dateien der Ursprungssite stellen für teilweise vertrauenswürdige Anwendungen die einzige Option dar, obwohl sie nicht auf letztere beschränkt sind.</span><span class="sxs-lookup"><span data-stu-id="733a1-176">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="733a1-177">Anwendungen mit voller Vertrauenswürdigkeit müssen ggf. Anwendungsdatendateien laden, die sie zur Buildzeit nicht kennen. Obwohl Anwendungen mit voller Vertrauenswürdigkeit „file:///“ verwenden könnten, ist anzunehmen, dass die Anwendungsdatendateien im selben Ordner oder in einem Unterordner der Anwendungsassembly installiert werden.</span><span class="sxs-lookup"><span data-stu-id="733a1-177">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="733a1-178">In einem solchen Fall gestaltet sich die Verwendung des Verweises auf die Ursprungssite einfacher als die Verwendung von „file:///“, da die Verwendung von „file:///“ von Ihnen erfordert, den vollständigen Pfad zur Datei auszuarbeiten.</span><span class="sxs-lookup"><span data-stu-id="733a1-178">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="733a1-179">Dateien der Ursprungs Site werden nicht mit einer XAML-Browser Anwendung (XBAP) auf einem Client Computer zwischengespeichert, während Inhalts Dateien gleich sind.</span><span class="sxs-lookup"><span data-stu-id="733a1-179">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="733a1-180">Folglich werden sie nur heruntergeladen, wenn sie ausdrücklich angefordert werden.</span><span class="sxs-lookup"><span data-stu-id="733a1-180">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="733a1-181">Wenn eine XBAP-Anwendung (XAML-Browser Anwendung) große Mediendateien enthält und diese als Dateien der Ursprungs Site konfiguriert werden, ist der erste Anwendungsstart wesentlich schneller, und die Dateien werden nur bei Bedarf heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="733a1-181">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="733a1-182">Konfigurieren der Dateien der Ursprungssite</span><span class="sxs-lookup"><span data-stu-id="733a1-182">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="733a1-183">Wenn die Dateien der Ursprungs Site zum Zeitpunkt der Kompilierung nicht vorhanden oder unbekannt sind, müssen Sie herkömmliche Bereitstellungs Mechanismen verwenden, um sicherzustellen, dass die erforderlichen Dateien zur Laufzeit verfügbar sind, einschließlich der Verwendung des `XCopy` Befehlszeilen Programms oder des Microsoft Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="733a1-183">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="733a1-184">Wenn Sie zum Zeitpunkt der Kompilierung wissen, dass Sie sich auf der Ursprungs Site befinden möchten, aber trotzdem eine explizite Abhängigkeit vermeiden möchten, können Sie diese Dateien einem MSBuild-Projekt als Element hinzufügen `None` .</span><span class="sxs-lookup"><span data-stu-id="733a1-184">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="733a1-185">Wie bei Inhalts Dateien müssen Sie das MSBuild-Attribut festlegen, `CopyToOutputDirectory` um anzugeben, dass die Ursprungs Site Datei an einen Speicherort kopiert wird, der relativ zur erstellten Assembly ist, indem Sie entweder den `Always` Wert oder den `PreserveNewest` Wert angeben.</span><span class="sxs-lookup"><span data-stu-id="733a1-185">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
> <span data-ttu-id="733a1-186">In Visual Studio erstellen Sie eine Website der Ursprungs Datei, indem Sie einem Projekt eine Datei hinzufügen und `Build Action` auf festlegen `None` .</span><span class="sxs-lookup"><span data-stu-id="733a1-186">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="733a1-187">Wenn das Projekt erstellt wird, kopiert MSBuild die angegebenen Dateien in den Buildausgabeordner.</span><span class="sxs-lookup"><span data-stu-id="733a1-187">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="733a1-188">Verwenden der Dateien der Ursprungssite</span><span class="sxs-lookup"><span data-stu-id="733a1-188">Using Site of Origin Files</span></span>  
 <span data-ttu-id="733a1-189">Zum Laden einer Ursprungs Site Datei können Sie die- <xref:System.Windows.Application.GetRemoteStream%2A> Methode der-Klasse aufzurufen <xref:System.Windows.Application> , indem Sie einen Paket-URI übergeben, der die gewünschte Ursprungs Site Datei identifiziert.</span><span class="sxs-lookup"><span data-stu-id="733a1-189">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="733a1-190"><xref:System.Windows.Application.GetRemoteStream%2A>Gibt ein <xref:System.Windows.Resources.StreamResourceInfo> -Objekt zurück, das die Datei der Ursprungs Site als bereitstellt <xref:System.IO.Stream> und den Inhaltstyp beschreibt.</span><span class="sxs-lookup"><span data-stu-id="733a1-190"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="733a1-191">Der folgende Code zeigt beispielsweise, wie verwendet wird, <xref:System.Windows.Application.GetRemoteStream%2A> um eine <xref:System.Windows.Controls.Page> Datei der Ursprungs Site zu laden und als Inhalt eines <xref:System.Windows.Controls.Frame> () festzulegen `pageFrame` .</span><span class="sxs-lookup"><span data-stu-id="733a1-191">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="733a1-192">Beim Aufrufen <xref:System.Windows.Application.GetRemoteStream%2A> von haben Sie Zugriff auf das- <xref:System.IO.Stream> Objekt, das Sie zum Festlegen der Eigenschaft in den Typ der Eigenschaft, mit der Sie ihn festlegen, benötigen.</span><span class="sxs-lookup"><span data-stu-id="733a1-192">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="733a1-193">Stattdessen können Sie das Öffnen und wandeln von WPF durchführen, <xref:System.IO.Stream> indem Sie eine Ressourcen Datei direkt in die-Eigenschaft eines Typs mithilfe von Code laden.</span><span class="sxs-lookup"><span data-stu-id="733a1-193">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="733a1-194">Im folgenden Beispiel wird gezeigt, wie ein <xref:System.Windows.Controls.Page> direkt in ein <xref:System.Windows.Controls.Frame> ( `pageFrame` ) mithilfe von Code geladen wird.</span><span class="sxs-lookup"><span data-stu-id="733a1-194">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="733a1-195">Das folgende Beispiel entspricht dem Markup des vorangehenden Beispiels.</span><span class="sxs-lookup"><span data-stu-id="733a1-195">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="733a1-196">Neuerstellung nach Ändern des Buildtyps</span><span class="sxs-lookup"><span data-stu-id="733a1-196">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="733a1-197">Nachdem Sie den Buildtyp einer Anwendungsdatendatei geändert haben, müssen Sie die gesamte Anwendung neu erstellen, um zu gewährleisten, dass diese Änderungen übernommen werden.</span><span class="sxs-lookup"><span data-stu-id="733a1-197">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="733a1-198">Wenn Sie nur die Anwendung erstellen, werden die Änderungen nicht übernommen.</span><span class="sxs-lookup"><span data-stu-id="733a1-198">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733a1-199">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="733a1-199">See also</span></span>

- [<span data-ttu-id="733a1-200">Paket-URI in WPF</span><span class="sxs-lookup"><span data-stu-id="733a1-200">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
