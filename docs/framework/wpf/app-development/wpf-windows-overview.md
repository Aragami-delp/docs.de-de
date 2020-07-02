---
title: Übersicht über Windows
description: Machen Sie sich mit den Grundlagen der Erstellung und Verwaltung von Windows für eigenständige Anwendungen in Windows Presentation Foundation (WPF) vertraut.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XAML [WPF], displaying content via
- XAML pages [WPF], displaying
- content [WPF], displaying via XAML
- window objects [WPF]
- hosting [WPF], applications
- managing windows [WPF]
- dialog boxes [WPF]
- Page object [WPF]
- NavigationWindow objects [WPF]
- applications [WPF], hosting
- content [WPF], displaying
- events [WPF]
- content [WPF], displaying via procedural code
- modal windows [WPF]
- procedural code [WPF], displaying content via
- displaying content via procedural code [WPF]
- window management [WPF]
- displaying content [WPF]
- window events [WPF]
- windows [WPF]
- modal dialog boxes [WPF]
- displaying XAML pages [WPF]
ms.assetid: 737d04ec-8861-46c3-8d44-fa11d3528d23
ms.openlocfilehash: e1ad3c118fbaea8f1e23d012721f0cf3c2c50015
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622886"
---
# <a name="wpf-windows-overview"></a>Übersicht über WPF-Fenster
Benutzer interagieren über Windows Windows Presentation Foundation mit eigenständigen WPF-Anwendungen (WPF). Die Hauptaufgabe eines Fensters besteht darin, Inhalt zu hosten, der Daten visuell darstellen kann und Benutzern die Interaktion mit Daten ermöglicht. Eigenständige WPF-Anwendungen stellen mithilfe der-Klasse ihre eigenen Fenster bereit <xref:System.Windows.Window> . In diesem Thema wird erläutert, <xref:System.Windows.Window> bevor die Grundlagen der Erstellung und Verwaltung von Fenstern in eigenständigen Anwendungen behandelt werden.  
  
> [!NOTE]
> Im Browser gehostete WPF-Anwendungen, einschließlich XAML-Browser Anwendungen (XBAPs) und losen [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] Seiten, stellen keine eigenen Fenster bereit. Stattdessen werden Sie in Windows von Windows Internet Explorer bereitgestellt. Siehe [Übersicht über WPF-XAML-Browser Anwendungen](wpf-xaml-browser-applications-overview.md).  

<a name="TheWindowClass"></a>
## <a name="the-window-class"></a>Die Fensterklasse  
 In der folgenden Abbildung werden die Bestandteile eines Fensters veranschaulicht:  
  
 ![Screenshot, der Fensterelemente zeigt.](./media/wpf-windows-overview/window-constituent-elements.png)  
  
 Ein Fenster wird in zwei Bereiche geteilt: der Nicht-Clientbereich und der Clientbereich.  
  
 Der *nicht-Client Bereich* eines Fensters wird von WPF implementiert und umfasst die Teile eines Fensters, die für die meisten Fenster gelten, einschließlich der folgenden:  
  
- Rahmen  
  
- Titelleiste  
  
- Symbol  
  
- Schaltflächen zum Minimieren, Maximieren und Wiederherstellen  
  
- Schaltfläche Schließen  
  
- Ein Systemmenü mit Menüelementen, mit denen Benutzer ein Fenster minimieren, maximieren, wiederherstellen, verschieben, schließen und dessen Größe ändern können.  
  
 Der *Client Bereich* eines Fensters ist der Bereich im nicht-Client Bereich eines Fensters und wird von Entwicklern verwendet, um anwendungsspezifische Inhalte wie Menüleisten, Symbolleisten und Steuerelemente hinzuzufügen.  
  
 In WPF wird ein Fenster von der-Klasse gekapselt, die <xref:System.Windows.Window> Sie für folgende Aufgaben verwenden:  
  
- Anzeigen eines Fensters  
  
- Konfigurieren der Größe, Position und Darstellung eines Fensters  
  
- Hosten von anwendungsspezifischem Inhalt  
  
- Verwalten der Lebensdauer eines Fensters  
  
<a name="DefiningAWindow"></a>
## <a name="implementing-a-window"></a>Implementieren eines Fensters  
 Die Implementierung eines typischen Fensters umfasst Darstellung und Verhalten, wobei Darstellung definiert, wie ein Fenster für Benutzer und *Verhalten* aussieht, wie ein Fenster funktioniert *, wenn Benutzer* damit interagieren. In WPF können Sie die Darstellung und das Verhalten eines Fensters mithilfe von Code oder Markup implementieren [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .  
  
 Im Allgemeinen wird jedoch das Aussehen eines Fensters mithilfe von [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Markup implementiert, und das Verhalten wird mithilfe von Code Behind implementiert, wie im folgenden Beispiel gezeigt.  
  
 [!code-xaml[WindowsOverviewSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
 Damit eine [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Markup Datei und eine Code-Behind-Datei zusammenarbeiten können, ist Folgendes erforderlich:  
  
- Im Markup muss das- `Window` Element das- `x:Class` Attribut enthalten. Wenn die Anwendung erstellt wird, bewirkt das vorhanden sein von `x:Class` in der Markup Datei, dass Microsoft Build Engine (MSBuild) eine Klasse erstellt, die `partial` von abgeleitet <xref:System.Windows.Window> wird und den Namen hat, der vom-Attribut angegeben wird `x:Class` . Dies erfordert das Hinzufügen einer XML-Namespace Deklaration für das [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Schema ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` ). Die generierte- `partial` Klasse implementiert die- `InitializeComponent` Methode, die aufgerufen wird, um die Ereignisse zu registrieren und die Eigenschaften festzulegen, die im Markup implementiert werden.  
  
- Bei Code-Behind muss die Klasse eine `partial` Klasse mit dem gleichen Namen sein, der im Markup durch das `x:Class` -Attribut angegeben ist, und Sie muss von abgeleitet werden <xref:System.Windows.Window> . Dadurch kann die Code-Behind-Datei mit der-Klasse verknüpft werden `partial` , die beim Erstellen der Anwendung für die Markup Datei generiert wird (siehe [Erstellen einer WPF-Anwendung](building-a-wpf-application-wpf.md)).  
  
- Im Code-Behind muss die <xref:System.Windows.Window> Klasse einen Konstruktor implementieren, der die- `InitializeComponent` Methode aufruft. `InitializeComponent`wird durch die generierte-Klasse der Markup Datei implementiert `partial` , um Ereignisse zu registrieren und im Markup definierte Eigenschaften festzulegen.  
  
> [!NOTE]
> Wenn Sie <xref:System.Windows.Window> Ihrem Projekt mithilfe von Visual Studio eine neue hinzufügen, <xref:System.Windows.Window> wird der mit Markup und Code Behind implementiert und umfasst die erforderliche Konfiguration zum Erstellen der Zuordnung zwischen dem Markup und den Code-Behind-Dateien, wie hier beschrieben.  
  
 Wenn diese Konfiguration vorhanden ist, können Sie sich darauf konzentrieren, das Aussehen des Fensters im [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Markup zu definieren und dessen Verhalten in Code Behind zu implementieren. Das folgende Beispiel zeigt ein Fenster mit einer Schaltfläche, die im Markup implementiert ist, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] und einen Ereignishandler für das-Ereignis der Schaltfläche <xref:System.Windows.Controls.Primitives.ButtonBase.Click> , die in Code Behind implementiert ist.  
  
 [!code-xaml[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml#markupandcodebehindwindowmarkup)]  
  
 [!code-csharp[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/CSharp/MarkupAndCodeBehindWindow.xaml.cs#markupandcodebehindwindowcodebehind)]
 [!code-vb[WindowsOverviewWindowWithButtonSnippets#MarkupAndCodeBehindWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewWindowWithButtonSnippets/VisualBasic/MarkupAndCodeBehindWindow.xaml.vb#markupandcodebehindwindowcodebehind)]  
  
<a name="ConfiguringWindowForMSBuild"></a>
## <a name="configuring-a-window-definition-for-msbuild"></a>Konfigurieren einer Fensterdefinition für MSBuild  
 Wie Sie Ihr Fenster implementieren, legt fest, wie es für MSBuild konfiguriert ist. Für ein Fenster, das sowohl mit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Markup als auch mit Code-Behind definiert wird:  
  
- XAML-Markup Dateien werden als MSBuild- `Page` Elemente konfiguriert.  
  
- Code Behind-Dateien werden als MSBuild- `Compile` Elemente konfiguriert.  
  
 Dies wird in der folgenden MSBuild-Projektdatei gezeigt.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
    ...  
    <Page Include="MarkupAndCodeBehindWindow.xaml" />  
    <Compile Include=" MarkupAndCodeBehindWindow.xaml.cs" />  
    ...  
</Project>  
```  
  
 Weitere Informationen zum Entwickeln von WPF-Anwendungen finden Sie unter [aufbauen einer WPF-Anwendung](building-a-wpf-application-wpf.md).  
  
<a name="WindowLifetime"></a>
## <a name="window-lifetime"></a>Fensterlebensdauer  
 Wie alle Klassen hat auch ein Fenster eine Lebensdauer, die mit dem erstmaligen Instanziieren beginnt. Anschließend wird es geöffnet, aktiviert, deaktiviert und schließlich geschlossen.  

<a name="Opening_a_Window"></a>
### <a name="opening-a-window"></a>Öffnen eines Fensters  
 Wenn Sie ein Fenster öffnen möchten, müssen Sie zuerst eine Instanz davon erstellen. Dies wird im folgenden Beispiel veranschaulicht.  
  
 [!code-xaml[WindowsOverviewStartupEventSnippets#AppMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml#appmarkup)]  
  
 [!code-csharp[WindowsOverviewStartupEventSnippets#AppCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewStartupEventSnippets/CSharp/App.xaml.cs#appcodebehind)]  
  
 In diesem Beispiel wird das `MarkupAndCodeBehindWindow` instanziiert, wenn die Anwendung gestartet wird. Dies tritt ein, wenn das- <xref:System.Windows.Application.Startup> Ereignis ausgelöst wird.  
  
 Wenn ein Fenster instanziiert wird, wird automatisch ein Verweis darauf zu einer Liste von Fenstern hinzugefügt, die vom-Objekt verwaltet wird <xref:System.Windows.Application> (siehe <xref:System.Windows.Application.Windows%2A?displayProperty=nameWithType> ). Außerdem wird das erste zu instanziierte Fenster standardmäßig <xref:System.Windows.Application> als Hauptanwendungsfenster festgelegt (siehe <xref:System.Windows.Application.MainWindow%2A?displayProperty=nameWithType> ).  
  
 Das Fenster wird schließlich durch Aufrufen der- <xref:System.Windows.Window.Show%2A> Methode geöffnet. das Ergebnis wird in der folgenden Abbildung dargestellt.  
  
 ![Ein durch Aufrufen von Window. Show geöffnetes Fenster](./media/wpf-windows-overview//window-opened-show-method.png)  
  
 Ein Fenster, das durch Aufrufen von geöffnet wird <xref:System.Windows.Window.Show%2A> , ist ein nicht modalem Fenster, was bedeutet, dass die Anwendung in einem Modus ausgeführt wird, der es Benutzern ermöglicht, andere Fenster in derselben Anwendung zu aktivieren.  
  
> [!NOTE]
> <xref:System.Windows.Window.ShowDialog%2A>wird aufgerufen, um Fenster (z. b. Dialogfelder Modal) zu öffnen. Weitere Informationen finden Sie unter [Übersicht über Dialog Felder](dialog-boxes-overview.md) .  
  
 Wenn <xref:System.Windows.Window.Show%2A> aufgerufen wird, führt ein Fenster Initialisierungs Aufgaben aus, bevor es angezeigt wird, um die Infrastruktur zu erstellen, die es ermöglicht, Benutzereingaben zu empfangen. Wenn das Fenster initialisiert wird, <xref:System.Windows.Window.SourceInitialized> wird das-Ereignis ausgelöst, und das Fenster wird angezeigt.  
  
 Als Verknüpfung <xref:System.Windows.Application.StartupUri%2A> kann festgelegt werden, um das erste Fenster anzugeben, das beim Start einer Anwendung automatisch geöffnet wird.  
  
 [!code-xaml[WindowsOverviewSnippets#ApplicationStartupUriMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/App.xaml#applicationstartupurimarkup)]  
  
 Wenn die Anwendung gestartet wird, wird das Fenster, das durch den Wert von angegeben <xref:System.Windows.Application.StartupUri%2A> wird, modelblily geöffnet. intern wird das Fenster durch Aufrufen der zugehörigen- <xref:System.Windows.Window.Show%2A> Methode geöffnet.  
  
<a name="Ownership"></a>
#### <a name="window-ownership"></a>Besitz von Fenstern  
 Ein Fenster, das mit der-Methode geöffnet wird, <xref:System.Windows.Window.Show%2A> verfügt nicht über eine implizite Beziehung zu dem Fenster, das es erstellt hat. Benutzer können mit einem der beiden Fenster interagieren, was bedeutet, dass beide Fenster folgende Aktionen ausführen können:  
  
- Deckt die andere ab (es sei denn, für eines der Fenster ist die- <xref:System.Windows.Window.Topmost%2A> Eigenschaft auf festgelegt `true` ).  
  
- Es wird minimiert, maximiert und wiederhergestellt, ohne das andere zu beeinflussen.  
  
 Bei einigen Fenstern ist eine Beziehung zu dem Fenster erforderlich, durch das es geöffnet wird. Beispielsweise kann eine integrierte Entwicklungsumgebung (IDE) Eigenschaften Fenster und Tool Fenster öffnen, deren typisches Verhalten darin besteht, das Fenster abzudecken, in dem Sie erstellt werden. Darüber hinaus sollten solche Fenster stets mit den Fenstern geschlossen, minimiert, maximiert und wiederhergestellt werden, durch die sie erstellt wurden. Eine solche Beziehung kann hergestellt werden, indem *ein Fenster in einem anderen* Fenster erstellt wird. Dies wird erreicht, indem die- <xref:System.Windows.Window.Owner%2A> Eigenschaft des *Fensters im Besitz* mit einem Verweis auf das *Besitzer Fenster*festgelegt wird. Dies wird im folgenden Beispiel gezeigt.  
  
 [!code-csharp[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/CSharp/MainWindow.xaml.cs#setwindowownercode)]
 [!code-vb[WindowOwnerOwnedWindowsSnippets#SetWindowOwnerCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowOwnerOwnedWindowsSnippets/visualbasic/mainwindow.xaml.vb#setwindowownercode)]  
  
 Nach Einrichten des Besitzes:  
  
- Das im Besitz befindliche Fenster kann auf das Besitzer Fenster verweisen, indem der Wert der zugehörigen-Eigenschaft überprüft wird <xref:System.Windows.Window.Owner%2A> .  
  
- Das Besitzer Fenster kann alle Windows-Besitzer ermitteln, indem er den Wert seiner- <xref:System.Windows.Window.OwnedWindows%2A> Eigenschaft prüft.  
  
<a name="Preventing"></a>
#### <a name="preventing-window-activation"></a>Verhindern der Fensteraktivierung  
 Es gibt Szenarien, in denen Windows nicht aktiviert werden soll, wenn es angezeigt wird, z. b. Konversationsfenster einer Internet Messenger-Anwendung oder Benachrichtigungsfenster einer e-Mail-Anwendung.  
  
 Wenn die Anwendung über ein Fenster verfügt, das nicht aktiviert werden soll, wenn Sie angezeigt wird, können Sie die- <xref:System.Windows.Window.ShowActivated%2A> Eigenschaft auf festlegen, `false` bevor Sie die- <xref:System.Windows.Window.Show%2A> Methode zum ersten Mal aufrufen. Daraus folgt:  
  
- Das Fenster wird nicht aktiviert.  
  
- Das-Ereignis des Fensters <xref:System.Windows.Window.Activated> wird nicht ausgelöst.  
  
- Das momentan aktivierte Fenster bleibt aktiviert.  
  
 Das Fenster wird jedoch aktiviert, sobald der Benutzer es durch Klicken auf den Client- oder Nicht-Clientbereich aktiviert. In diesem Fall:  
  
- Das Fenster wird aktiviert.  
  
- Das-Ereignis des Fensters <xref:System.Windows.Window.Activated> wird ausgelöst.  
  
- Das zuvor aktivierte Fenster wird deaktiviert.  
  
- Die-und-Ereignisse des Fensters <xref:System.Windows.Window.Deactivated> <xref:System.Windows.Window.Activated> werden dann wie erwartet als Reaktion auf Benutzeraktionen ausgelöst.  
  
<a name="Window_Activation"></a>
### <a name="window-activation"></a>Aktivieren von Fenstern  
 Wenn ein Fenster zum ersten Mal geöffnet wird, wird es zum aktiven Fenster (es sei denn, es wird angezeigt, wenn <xref:System.Windows.Window.ShowActivated%2A> auf festgelegt ist `false` ). Das *aktive Fenster* ist das Fenster, das zurzeit Benutzereingaben erfasst, z. b. Tastenanschläge und Mausklicks. Wenn ein Fenster aktiv wird, löst es das- <xref:System.Windows.Window.Activated> Ereignis aus.  
  
> [!NOTE]
> Wenn ein Fenster zum ersten Mal geöffnet wird, <xref:System.Windows.FrameworkElement.Loaded> werden das-Ereignis und das- <xref:System.Windows.Window.ContentRendered> Ereignis erst ausgelöst, nachdem das- <xref:System.Windows.Window.Activated> Ereignis ausgelöst wurde. Vor diesem Hintergrund kann ein Fenster als geöffnet angesehen werden, wenn <xref:System.Windows.Window.ContentRendered> ausgelöst wird.  
  
 Nachdem ein Fenster aktiv geworden ist, kann ein Benutzer ein weiteres Fenster in derselben Anwendung oder eine andere Anwendung aktivieren. Wenn dies der Fall ist, wird das derzeit aktive Fenster deaktiviert und löst das- <xref:System.Windows.Window.Deactivated> Ereignis aus. Ebenso wird, wenn der Benutzer ein momentan deaktiviertes Fenster auswählt, das Fenster erneut aktiviert und <xref:System.Windows.Window.Activated> ausgelöst.  
  
 Ein häufiger Grund für die Handhabung von <xref:System.Windows.Window.Activated> und <xref:System.Windows.Window.Deactivated> ist das Aktivieren und Deaktivieren von Funktionen, die nur ausgeführt werden können, wenn ein Fenster aktiv ist. In einigen Fenstern wird beispielsweise interaktiver Inhalt angezeigt, der andauernde Benutzereingaben oder Aufmerksamkeit erfordert, wie beispielsweise Spiele und Videoplayer. Das folgende Beispiel ist ein vereinfachter Video Player, der veranschaulicht, wie <xref:System.Windows.Window.Activated> und <xref:System.Windows.Window.Deactivated> dieses Verhalten implementiert werden.  
  
 [!code-xaml[WindowsOverviewSnippets#ActivationDeactivationMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml#activationdeactivationmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/CustomMediaPlayerWindow.xaml.cs#activationdeactivationcodebehind)]
 [!code-vb[WindowsOverviewSnippets#ActivationDeactivationCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/CustomMediaPlayerWindow.xaml.vb#activationdeactivationcodebehind)]  
  
 Andere Anwendungstypen führen im Hintergrund möglicherweise weiterhin Code aus, nachdem ein Fenster deaktiviert wurde. Ein E-Mail-Client kann z. B. weiterhin den E-Mail-Server abrufen, während der Benutzer andere Anwendungen verwendet. Während das Hauptfenster deaktiviert ist, stellen derartige Anwendungen häufig zusätzliches oder anderes Verhalten zur Verfügung. Im Hinblick auf das E-Mail-Programm kann das sowohl das Hinzufügen des neuen E-Mail-Elements zum Posteingang als auch eines Benachrichtigungssymbol in die Taskleiste bedeuten. Ein Benachrichtigungssymbol muss nur angezeigt werden, wenn das Mail Fenster nicht aktiv ist. Dies kann durch Überprüfen der-Eigenschaft bestimmt werden <xref:System.Windows.Window.IsActive%2A> .  
  
 Wenn eine Hintergrundaufgabe abgeschlossen ist, kann es sein, dass ein Fenster den Benutzer durch Aufrufen der-Methode dringender benachrichtigen soll <xref:System.Windows.Window.Activate%2A> . Wenn der Benutzer mit einer anderen Anwendung interagiert, die beim Aufrufen von aktiviert ist <xref:System.Windows.Window.Activate%2A> , blinkt die Task leisten Schaltfläche des Fensters. Wenn ein Benutzer mit der aktuellen Anwendung interagiert, <xref:System.Windows.Window.Activate%2A> wird durch den Aufruf von das Fenster in den Vordergrund gebracht.  
  
> [!NOTE]
> Sie können die Aktivierung des Anwendungsbereichs mithilfe der <xref:System.Windows.Application.Activated?displayProperty=nameWithType> Ereignisse und behandeln <xref:System.Windows.Application.Deactivated?displayProperty=nameWithType> .  
  
<a name="Closing_a_Window"></a>
### <a name="closing-a-window"></a>Schließen eines Fensters  
 Die Lebensdauer eines Fensters endet, wenn der Benutzer das Fenster schließt. Ein Fenster kann mithilfe der Elemente im Nicht-Clientbereich geschlossen werden, z. B. mit den folgenden:  
  
- Das Schließ **Ende** Element im **System** Menü.  
  
- Drücken von ALT+F4.  
  
- Drücken der Schaltfläche **Schließen** .  
  
 Zum Schließen eines Fensters können Sie dem Clientbereich weitere Mechanismen hinzufügen. Zu den gebräuchlichsten zählen:  
  
- Ein **Exit** Beendigungs Element im Menü **Datei** (in der Regel für Hauptanwendungsfenster).  
  
- Ein Schließ **Ende** Element im Menü **Datei** , in der Regel in einem sekundären Anwendungsfenster.  
  
- Eine Schaltfläche **Abbrechen** (in der Regel in einem modalen Dialogfeld).  
  
- Eine Schaltfläche **Schließen** (in der Regel in einem nicht modalem Dialogfeld).  
  
 Um ein Fenster als Reaktion auf einen dieser benutzerdefinierten Mechanismen zu schließen, müssen Sie die- <xref:System.Windows.Window.Close%2A> Methode aufzurufen. Im folgenden Beispiel wird die Fähigkeit zum Schließen eines Fensters implementiert, indem im Menü **Datei** die Option **Beenden** ausgewählt wird.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowWithFileExitMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml#windowwithfileexitmarkup)]  
  
 [!code-csharp[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowWithFileExit.xaml.cs#windowwithfileexitcodebehind)]
 [!code-vb[WindowsOverviewSnippets#WindowWithFileExitCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowsOverviewSnippets/VisualBasic/WindowWithFileExit.xaml.vb#windowwithfileexitcodebehind)]  
  
 Wenn ein Fenster geschlossen wird, werden zwei Ereignisse ausgelöst: <xref:System.Windows.Window.Closing> und <xref:System.Windows.Window.Closed> .  
  
 <xref:System.Windows.Window.Closing>wird ausgelöst, bevor das Fenster geschlossen wird, und stellt einen Mechanismus bereit, mit dem die Fenster Schließung verhindert werden kann. Der häufigste Grund, um das Schließen eines Fensters zu verhindern, liegt darin, dass Fensterinhalt geänderte Daten enthält. In dieser Situation kann das <xref:System.Windows.Window.Closing> Ereignis behandelt werden, um zu bestimmen, ob Daten geändert werden, und wenn dies der Fall ist, um den Benutzer zu Fragen, ob das Schließen des Fensters fortgesetzt werden soll, ohne die Daten zu speichern oder die Fenster Schließung abzubrechen. Das folgende Beispiel zeigt die wichtigsten Aspekte der Behandlung von <xref:System.Windows.Window.Closing> .  
  
 [!code-csharp[WindowClosingSnippets](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowClosingSnippets/CSharp/DataWindow.xaml.cs)]
 [!code-vb[WindowClosingSnippets](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WindowClosingSnippets/visualbasic/datawindow.xaml.vb)]  

 <xref:System.Windows.Window.Closing>An den Ereignishandler wird ein <xref:System.ComponentModel.CancelEventArgs> übermittelt, der die Eigenschaft implementiert, die `Boolean` <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Sie auf festlegen, `true` um zu verhindern, dass ein Fenster geschlossen wird.  
  
 Wenn <xref:System.Windows.Window.Closing> nicht behandelt wird oder wenn es behandelt, aber nicht abgebrochen wird, wird das Fenster geschlossen. Unmittelbar bevor ein Fenster geschlossen wird, <xref:System.Windows.Window.Closed> wird ausgelöst. An dieser Stelle kann das Schließen des Fensters nicht verhindert werden.  
  
> [!NOTE]
> Eine Anwendung kann so konfiguriert werden, dass Sie automatisch heruntergefahren wird, wenn das Hauptanwendungsfenster geschlossen wird (siehe <xref:System.Windows.Application.MainWindow%2A> ) oder das letzte Fenster geschlossen wird. Einzelheiten dazu finden Sie unter <xref:System.Windows.Application.ShutdownMode%2A>.  
  
 Während ein Fenster durch Mechanismen, die in den nicht-Client-und Client Bereichen bereitgestellt werden, explizit geschlossen werden kann, kann ein Fenster aufgrund des Verhaltens in anderen Teilen der Anwendung oder von Fenstern implizit geschlossen werden, einschließlich der folgenden:  
  
- Ein Benutzer meldet sich ab oder fährt Windows herunter.  
  
- Der Besitzer eines Fensters wird geschlossen (Weitere Informationen finden Sie unter <xref:System.Windows.Window.Owner%2A> ).  
  
- Das Hauptanwendungsfenster ist geschlossen, und <xref:System.Windows.Application.ShutdownMode%2A> ist <xref:System.Windows.ShutdownMode.OnMainWindowClose> .  
  
- <xref:System.Windows.Application.Shutdown%2A> wird aufgerufen.  
  
> [!NOTE]
> Ein Fenster kann nicht erneut geöffnet werden, nachdem es geschlossen wurde.  
  
<a name="Window_Lifetime_Events"></a>
### <a name="window-lifetime-events"></a>Ereignisse in der Lebensdauer eines Fensters  
 Die folgende Abbildung zeigt die Reihenfolge der Prinzipal Ereignisse in der Lebensdauer eines Fensters:  
  
 ![Diagramm, in dem Ereignisse in der Lebensdauer eines Fensters angezeigt werden.](./media/wpf-windows-overview/window-lifetime-events.png)  
  
 Die folgende Abbildung zeigt die Reihenfolge der Prinzipal Ereignisse in der Lebensdauer eines Fensters, das ohne Aktivierung angezeigt wird ( <xref:System.Windows.Window.ShowActivated%2A> wird auf festgelegt, `false` bevor das Fenster angezeigt wird):  
  
 ![Diagramm, in dem Ereignisse in der Lebensdauer eines Fensters ohne Aktivierung angezeigt werden.](./media/wpf-windows-overview/window-lifetime-no-activation.png)  
  
<a name="WindowLocation"></a>
## <a name="window-location"></a>Fensterposition  
 Solange ein Fenster geöffnet ist, befindet sich dessen Position in der x- und y-Dimension relativ zum Desktop. Dieser Speicherort kann ermittelt werden, indem die <xref:System.Windows.Window.Left%2A> -Eigenschaft bzw. die-Eigenschaft überprüft wird <xref:System.Windows.Window.Top%2A> . Sie können diese Eigenschaften festlegen, um die Position des Fensters zu ändern.  
  
 Sie können auch den ursprünglichen Speicherort eines angeben, <xref:System.Windows.Window> Wenn er zum ersten Mal angezeigt wird, indem Sie die- <xref:System.Windows.Window.WindowStartupLocation%2A> Eigenschaft mit einem der folgenden <xref:System.Windows.WindowStartupLocation> Enumerationswerte festlegen:  
  
- <xref:System.Windows.WindowStartupLocation.CenterOwner> (Standardwert)  
  
- <xref:System.Windows.WindowStartupLocation.CenterScreen>  
  
- <xref:System.Windows.WindowStartupLocation.Manual>  
  
 Wenn der Start Speicherort als angegeben wird <xref:System.Windows.WindowStartupLocation.Manual> und die <xref:System.Windows.Window.Left%2A> -Eigenschaft und die-Eigenschaft <xref:System.Windows.Window.Top%2A> nicht festgelegt wurden, <xref:System.Windows.Window> fragt Windows nach einem Speicherort, der in angezeigt wird.  
  
<a name="Topmost_Windows_and_Z_Order"></a>
### <a name="topmost-windows-and-z-order"></a>Oberstes Fenster und Z-Reihenfolge  
 Neben der X- und Y-Position verfügt das Fenster auch über eine Position in der Z-Dimension, die dessen vertikale Position im Verhältnis zu anderen Fenstern bestimmt. Dies wird als Z-Reihenfolge des Fensters bezeichnet. Davon gibt es zwei Typen: die normale Z-Reihenfolge und die oberste Z-Reihenfolge. Die Position eines Fensters in der *normalen z-Reihenfolge* hängt davon ab, ob es zurzeit aktiv ist oder nicht. Standardmäßig befindet sich ein Fenster in der normalen Z-Reihenfolge. Der Speicherort eines Fensters in der *obersten z-Reihenfolge* hängt auch davon ab, ob er derzeit aktiv ist oder nicht. Darüber hinaus befinden sich Fenster in der obersten Z-Reihenfolge stets über den Fenstern in der normalen Z-Reihenfolge. Ein Fenster befindet sich in der obersten z-Reihenfolge, indem die zugehörige-Eigenschaft auf festgelegt wird <xref:System.Windows.Window.Topmost%2A> `true` .  
  
 [!code-xaml[WindowsOverviewSnippets#TopmostWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TopmostWindow.xaml#topmostwindowmarkup1)]  
  
 Innerhalb jeder Z-Reihenfolge wird das aktuell aktive Fenster über allen anderen Fenstern derselben Z-Reihenfolge angezeigt.  
  
<a name="WindowSize"></a>
## <a name="window-size"></a>Fenstergröße  
 Neben einem Desktop Speicherort hat ein Fenster eine Größe, die von mehreren Eigenschaften bestimmt wird, einschließlich der verschiedenen Eigenschaften für Breite und Höhe und <xref:System.Windows.Window.SizeToContent%2A> .  
  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Width%2A> und <xref:System.Windows.FrameworkElement.MaxWidth%2A> werden verwendet, um den breiten Bereich zu verwalten, den ein Fenster während seiner Lebensdauer aufweisen kann, und wie im folgenden Beispiel gezeigt.  
  
 [!code-xaml[WindowsOverviewSnippets#WidthWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WidthWindow.xaml#widthwindowmarkup1)]  
  
 Die Fensterhöhe wird von <xref:System.Windows.FrameworkElement.MinHeight%2A> , <xref:System.Windows.FrameworkElement.Height%2A> und verwaltet <xref:System.Windows.FrameworkElement.MaxHeight%2A> und wie im folgenden Beispiel gezeigt konfiguriert.  
  
 [!code-xaml[WindowsOverviewSnippets#HeightWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/HeightWindow.xaml#heightwindowmarkup1)]  
  
 Da die verschiedenen Werte für die Breite und für die Höhe jeweils einen Bereich angeben, kann die Breite und Höhe eines in der Größe veränderbaren Fensters irgendwo innerhalb des angegebenen Bereichs für die entsprechende Dimension liegen. Um die aktuelle Breite und Höhe zu ermitteln, überprüfen Sie <xref:System.Windows.FrameworkElement.ActualWidth%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> bzw..  
  
 Wenn Sie möchten, dass die Breite und Höhe des Fensters auf die Größe des Fenster Inhalts zugeschnitten ist, können Sie die- <xref:System.Windows.Window.SizeToContent%2A> Eigenschaft mit den folgenden Werten verwenden:  
  
- <xref:System.Windows.SizeToContent.Manual>. Keine Auswirkung (Standard).  
  
- <xref:System.Windows.SizeToContent.Width>. An Inhalts Breite anpassen, was die gleiche Wirkung hat wie das Festlegen <xref:System.Windows.FrameworkElement.MinWidth%2A> von sowohl als auch <xref:System.Windows.FrameworkElement.MaxWidth%2A> der Breite des Inhalts.  
  
- <xref:System.Windows.SizeToContent.Height>. An die Höhe des Inhalts anpassen. Dies hat die gleiche Wirkung wie das Festlegen <xref:System.Windows.FrameworkElement.MinHeight%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> von und auf die Höhe des Inhalts.  
  
- <xref:System.Windows.SizeToContent.WidthAndHeight>. An Inhalts Breite und-Höhe anpassen, was die gleiche Wirkung hat wie das <xref:System.Windows.FrameworkElement.MinHeight%2A> festlegen <xref:System.Windows.FrameworkElement.MaxHeight%2A> von und auf die Höhe des Inhalts und das Festlegen <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement.MaxWidth%2A> von und auf die Breite des Inhalts.  
  
 Im folgenden Beispiel wird ein Fenster dass die Größe automatisch an seinen Inhalt vertikal und horizontal an, wenn es zuerst angezeigt wird.  
  
 [!code-xaml[WindowsOverviewSnippets#SizeToContentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/SizeToContentWindow.xaml#sizetocontentwindowmarkup1)]  
  
 Im folgenden Beispiel wird gezeigt, wie die- <xref:System.Windows.Window.SizeToContent%2A> Eigenschaft im Code festgelegt wird, um anzugeben, wie die Größe eines Fensters an seinen Inhalt angepasst wird.
  
 [!code-csharp[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#setwindowsizetocontentpropertycode)]
 [!code-vb[HOWTOWindowManagementSnippets#SetWindowSizeToContentPropertyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#setwindowsizetocontentpropertycode)]  
  
<a name="OrderOfPrecedence"></a>
## <a name="order-of-precedence-for-sizing-properties"></a>Rangfolge der Größeneigenschaften  
 Im Wesentlichen werden die verschiedenen Größeneigenschaften eines Fensters kombiniert, um den Bereich der Breite und der Höhe für ein in der Größe veränderbares Fenster zu definieren. Um sicherzustellen, dass ein gültiger Bereich beibehalten wird, <xref:System.Windows.Window> wertet die Werte der Size-Eigenschaften anhand der folgenden Rangfolge aus.  
  
 **Für Höheneigenschaften:**  
  
1. <xref:System.Windows.FrameworkElement.MinHeight%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxHeight%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Height?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Height%2A?displayProperty=nameWithType>  
  
 **Für Breiteneigenschaften:**  
  
1. <xref:System.Windows.FrameworkElement.MinWidth%2A?displayProperty=nameWithType>
  
2. <xref:System.Windows.FrameworkElement.MaxWidth%2A?displayProperty=nameWithType>
  
3. <xref:System.Windows.SizeToContent.Width?displayProperty=nameWithType>/<xref:System.Windows.SizeToContent.WidthAndHeight?displayProperty=nameWithType>
  
4. <xref:System.Windows.FrameworkElement.Width%2A?displayProperty=nameWithType>  
  
 Die Rangfolge kann auch die Größe eines Fensters bestimmen, wenn es maximiert ist, das mit der-Eigenschaft verwaltet wird <xref:System.Windows.Window.WindowState%2A> .  
  
<a name="WindowState"></a>
## <a name="window-state"></a>Fensterzustand  
 Während der Lebensdauer eines in der Größe veränderbaren Fenster kann dieses über drei Zustände verfügen: normal, minimiert und maximiert. Ein Fenster mit einem *normalen* Zustand ist der Standardzustand eines Fensters. Ein Benutzer kann ein Fenster mit diesem Zustand verschieben und dessen Größe ändern, indem er den Ziehpunkt zur Größenänderung oder den Rahmen verwendet, sofern er in der Größe veränderbar ist.  
  
 Ein Fenster mit einem *minimierten* Zustand wird auf die Task leisten Schaltfläche reduziert, wenn <xref:System.Windows.Window.ShowInTaskbar%2A> auf festgelegt ist `true` . andernfalls wird es auf die kleinste mögliche Größe reduziert, und es kann sich in der linken unteren Ecke des Desktops wiederholen. Keiner der minimierten Fenstertypen kann mithilfe des Ziehpunkts zur Größenreduzierung oder mit dem Rahmen in der Größe verändert werden. Allerdings kann ein minimiertes Fenster, das nicht in der Taskleiste angezeigt wird, auf dem Desktop hin und her verschoben werden.  
  
 Ein Fenster mit einem *maximierten* Zustand wird auf die maximal zulässige Größe erweitert. Dies ist nur so groß wie die <xref:System.Windows.FrameworkElement.MaxWidth%2A> <xref:System.Windows.FrameworkElement.MaxHeight%2A> Eigenschaften, und <xref:System.Windows.Window.SizeToContent%2A> . Wie ein minimiertes Fenster kann auch ein maximiertes Fenster nicht mithilfe des Ziehpunkts zur Größenänderung oder durch Ziehen des Rahmens in seiner Größe verändert werden.  
  
> [!NOTE]
> Die Werte der <xref:System.Windows.Window.Top%2A> Eigenschaften, <xref:System.Windows.Window.Left%2A> , <xref:System.Windows.FrameworkElement.Width%2A> und <xref:System.Windows.FrameworkElement.Height%2A> eines Fensters stellen immer die Werte für den normalen Zustand dar, auch wenn das Fenster derzeit maximiert oder minimiert ist.  
  
 Der Zustand eines Fensters kann durch Festlegen der-Eigenschaft konfiguriert werden <xref:System.Windows.Window.WindowState%2A> , die einen der folgenden <xref:System.Windows.WindowState> Enumerationswerte aufweisen kann:  
  
- <xref:System.Windows.WindowState.Normal> (Standardwert)  
  
- <xref:System.Windows.WindowState.Maximized>  
  
- <xref:System.Windows.WindowState.Minimized>  
  
 Im folgenden Beispiel wird veranschaulicht, wie Sie ein Fenster erstellen, das beim Öffnen als maximiert angezeigt wird.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStateWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStateWindow.xaml#windowstatewindowmarkup1)]  
  
 Im Allgemeinen sollten Sie festlegen, <xref:System.Windows.Window.WindowState%2A> um den ursprünglichen Zustand eines Fensters zu konfigurieren. Wenn ein in der Größe veränderbares Fenster angezeigt wird, können die Benutzer die Schaltflächen zum Minimieren, Maximieren oder Wiederherstellen auf der Titelleiste des Fensters aktivieren, um den Fensterzustand zu ändern.  
  
<a name="WindowAppearance"></a>
## <a name="window-appearance"></a>Fensterdarstellung  
 Sie ändern die Darstellung des Clientbereichs eines Fensters, indem Sie fensterspezifischen Inhalt hinzufügen, z. B. Schaltflächen, Bezeichnungen und Textfelder. Um den nicht-Client Bereich zu konfigurieren, <xref:System.Windows.Window> stellt verschiedene Eigenschaften bereit <xref:System.Windows.Window.Icon%2A> . dazu gehören das Festlegen des Symbol eines Fensters und das <xref:System.Windows.Window.Title%2A> Festlegen seines Titels.  
  
 Außerdem können Sie die Darstellung und das Verhalten des Rahmens im Nicht-Clientbereich ändern, indem Sie den Größenänderungsmodus, den Fensterstil und die Tatsache konfigurieren, ob es als Schaltfläche in der Desktoptaskleiste angezeigt wird.  

<a name="Resize_Mode"></a>
### <a name="resize-mode"></a>Größenänderungsmodus  
 Abhängig von der <xref:System.Windows.Window.WindowStyle%2A> Eigenschaft können Sie steuern, wie (und ob) Benutzer die Größe des Fensters ändern können. Die Auswahl des Fenster Stils wirkt sich darauf aus, ob ein Benutzer die Größe des Fensters ändern kann, indem er den Rahmen mit der Maus zieht, unabhängig davon, ob die Schaltflächen **minimieren**, **maximieren**und **Größe ändern** im nicht-Client Bereich angezeigt werden, und wenn Sie angezeigt werden, ob Sie aktiviert sind.  
  
 Sie können konfigurieren, wie die Größe eines Fensters geändert wird, indem Sie die zugehörige- <xref:System.Windows.Window.ResizeMode%2A> Eigenschaft festlegen, die einen der folgenden <xref:System.Windows.ResizeMode> Enumerationswerte aufweisen kann:  
  
- <xref:System.Windows.ResizeMode.NoResize>  
  
- <xref:System.Windows.ResizeMode.CanMinimize>  
  
- <xref:System.Windows.ResizeMode.CanResize> (Standardwert)  
  
- <xref:System.Windows.ResizeMode.CanResizeWithGrip>  
  
 Wie bei <xref:System.Windows.Window.WindowStyle%2A> ist es unwahrscheinlich, dass sich der Größen Änderungs Modus eines Fensters während seiner Lebensdauer ändert. Dies bedeutet, dass Sie ihn wahrscheinlich von [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Markup festlegen.  
  
 [!code-xaml[WindowsOverviewSnippets#ResizeModeWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ResizeModeWindow.xaml#resizemodewindowmarkup1)]  
  
 Beachten Sie, dass Sie erkennen können, ob ein Fenster maximiert, minimiert oder wieder hergestellt wird, indem Sie die-Eigenschaft überprüfen <xref:System.Windows.Window.WindowState%2A> .  
  
<a name="Window_Style"></a>
### <a name="window-style"></a>Fensterstil  
 Der Rahmen, der vom Nicht-Clientbereich eines Fensters verfügbar gemacht wird, eignet sich für die meisten Anwendungen. Unter bestimmten Umständen werden je nach Fenstertyp dennoch andere Rahmentypen oder überhaupt keine Rahmen benötigt.  
  
 Um zu steuern, welche Art von Rahmen ein Fenster erhält, legen Sie dessen- <xref:System.Windows.Window.WindowStyle%2A> Eigenschaft mit einem der folgenden Werte der- <xref:System.Windows.WindowStyle> Enumeration fest:  
  
- <xref:System.Windows.WindowStyle.None>  
  
- <xref:System.Windows.WindowStyle.SingleBorderWindow> (Standardwert)  
  
- <xref:System.Windows.WindowStyle.ThreeDBorderWindow>  
  
- <xref:System.Windows.WindowStyle.ToolWindow>  
  
 Die Auswirkungen dieser Fenster Stile sind in der folgenden Abbildung dargestellt:  
  
 ![Abbildung der Fensterrahmen Stile.](./media/wpf-windows-overview/window-border-styles.png)  
  
 Sie können <xref:System.Windows.Window.WindowStyle%2A> entweder mithilfe von [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Markup oder Code festlegen, da es unwahrscheinlich ist, dass es sich während der Lebensdauer eines Fensters ändert, wird es wahrscheinlich mit [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] Markup konfiguriert.  
  
 [!code-xaml[WindowsOverviewSnippets#WindowStyleWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/WindowStyleWindow.xaml#windowstylewindowmarkup1)]  
  
#### <a name="non-rectangular-window-style"></a>Nicht rechteckiger Fensterstil  
 Es gibt auch Situationen, in denen die Rahmen Stile, die <xref:System.Windows.Window.WindowStyle%2A> Ihnen die Möglichkeit bieten, nicht ausreichen. Beispielsweise können Sie eine Anwendung mit einem nicht rechteckigen Rahmen erstellen, wie z. b. Microsoft Windows Media Player verwendet.  
  
 Sehen Sie sich beispielsweise das in der folgenden Abbildung gezeigte Sprechblasen Fenster an:  
  
 ![Ein Sprechblasen Fenster mit dem Text Drag Me.](./media/wpf-windows-overview/non-rectangular-window-figure.png)  
  
 Diese Art von Fenster kann erstellt werden, indem die <xref:System.Windows.Window.WindowStyle%2A> -Eigenschaft auf festgelegt wird <xref:System.Windows.WindowStyle.None> , und mit spezieller Unterstützung <xref:System.Windows.Window> für Transparenz.  
  
 [!code-xaml[WindowsOverviewSnippets#TransparentWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/TransparentWindow.xaml#transparentwindowmarkup1)]  
  
 Durch diese Kombination von Werten wird das Fenster angewiesen, ein vollkommen transparentes Rendering zu übernehmen. In diesem Zustand können die Zusatzelemente des Nicht-Clientbereichs des Fensters (das Menü „Schließen“, die Schaltflächen „Minimieren“, „Maximieren“ und „Wiederherstellen“ usw.) nicht verwendet werden. Folglich müssen Sie Ihre eigenen bereitstellen.  
  
<a name="Task_Bar_Presence"></a>
### <a name="task-bar-presence"></a>Vorhandensein der Taskleiste  

Die Standarddarstellung eines Fensters umfasst eine Task leisten Schaltfläche, wie in der folgenden Abbildung dargestellt:

 ![Screenshot, der ein Fenster mit einer Task leisten Schaltfläche anzeigt.](./media/wpf-windows-overview/window-taskbar-button.png)  
  
 Einige Windows-Typen verfügen nicht über eine Task leisten Schaltfläche, z. b. Meldungs Felder und Dialogfelder (siehe [Übersicht über Dialogfelder](dialog-boxes-overview.md)). Sie können steuern, ob die Task leisten Schaltfläche für ein Fenster angezeigt wird, indem Sie die- <xref:System.Windows.Window.ShowInTaskbar%2A> Eigenschaft festlegen ( `true` standardmäßig).  
  
 [!code-xaml[WindowsOverviewSnippets#ShowInTaskbarWindowMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/WindowsOverviewSnippets/CSharp/ShowInTaskbarWindow.xaml#showintaskbarwindowmarkup1)]  
  
<a name="SecurityConsiderations"></a>
## <a name="security-considerations"></a>Überlegungen zur Sicherheit  
 <xref:System.Windows.Window>erfordert `UnmanagedCode` die-Sicherheits Berechtigung, um instanziiert zu werden. Bei Anwendungen, die auf dem lokalen Computer installiert und gestartet werden, wird dies durch die Berechtigungen abgedeckt, die der Anwendung gewährt werden.  
  
 Dies liegt jedoch außerhalb der Berechtigungs Sätze, die Anwendungen gewährt werden, die über die Internet-oder lokale Intranetzone mithilfe von ClickOnce gestartet werden. Folglich erhalten Benutzer eine ClickOnce-Sicherheitswarnung und müssen den Berechtigungs Satz für die Anwendung auf Full Trust erhöhen.  
  
 Außerdem können in XBAPs standardmäßig keine Fenster oder Dialogfelder angezeigt werden. Eine Erläuterung zu den Sicherheitsüberlegungen für eigenständige Anwendungen finden Sie unter [WPF-Sicherheitsstrategie-Plattformsicherheit](../wpf-security-strategy-platform-security.md).  
  
<a name="Other_Types_of_Windows"></a>
## <a name="other-types-of-windows"></a>Andere Fenstertypen  
 <xref:System.Windows.Navigation.NavigationWindow>ist ein Fenster, das zum Hosten von Navigier barem Inhalt entworfen wurde. Weitere Informationen finden Sie unter [Übersicht über die Navigation](navigation-overview.md).  
  
 Dialogfelder sind Fenster, die häufig zum Erfassen von Benutzerinformationen verwendet werden, um eine Funktion ausführen. Wenn ein Benutzer beispielsweise eine Datei öffnen möchte, wird das Dialogfeld **Datei öffnen** normalerweise von einer Anwendung angezeigt, um den Dateinamen vom Benutzer zu erhalten. Weitere Informationen finden Sie unter [Übersicht über Dialogfelder](dialog-boxes-overview.md).  
  
## <a name="see-also"></a>Weitere Informationen

- <xref:System.Windows.Window>
- <xref:System.Windows.MessageBox>
- <xref:System.Windows.Navigation.NavigationWindow>
- <xref:System.Windows.Application>
- [Übersicht über Dialogfelder](dialog-boxes-overview.md)
- [Erstellen einer WPF-Anwendung](building-a-wpf-application-wpf.md)
