---
title: Übersicht über Formen und grundlegende Zeichnungen
description: Verbessern Sie Ihre Benutzeroberfläche mit sofort einsatzbereiten Formen und mehreren Ebenen der Renderingdienste in Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: 41d8f2b87232740c8945bd6a6099aa86dbe77bc6
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853688"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Übersicht über Formen und die grundlegenden Funktionen zum Zeichnen in WPF
Dieses Thema enthält eine Übersicht über das Zeichnen mit- <xref:System.Windows.Shapes.Shape> Objekten. Ein <xref:System.Windows.Shapes.Shape> ist ein Typ von <xref:System.Windows.UIElement> , mit dem Sie eine Form auf dem Bildschirm zeichnen können. Da es sich um Benutzeroberflächen Elemente handelt, <xref:System.Windows.Shapes.Shape> können-Objekte innerhalb von <xref:System.Windows.Controls.Panel> Elementen und den meisten Steuerelementen verwendet werden.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] bietet mehrere Ebenen für den Zugriff auf Grafiken und Renderingdienste. Auf der obersten Ebene <xref:System.Windows.Shapes.Shape> sind-Objekte einfach zu verwenden und bieten zahlreiche nützliche Features, wie z. b. das Layout und die Teilnahme am [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Ereignis System.  

<a name="shapes"></a>
## <a name="shape-objects"></a>Shape-Objekte  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]stellt eine Reihe von gebrauchsfertigen <xref:System.Windows.Shapes.Shape> Objekten bereit.  Alle Shape-Objekte erben von der- <xref:System.Windows.Shapes.Shape> Klasse. Zu den verfügbaren Shape-Objekten zählen <xref:System.Windows.Shapes.Ellipse> , <xref:System.Windows.Shapes.Line> , <xref:System.Windows.Shapes.Path> , <xref:System.Windows.Shapes.Polygon> , <xref:System.Windows.Shapes.Polyline> und <xref:System.Windows.Shapes.Rectangle> . <xref:System.Windows.Shapes.Shape>-Objekte haben die folgenden allgemeinen Eigenschaften gemeinsam.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: Beschreibt, wie der Umriss der Form gezeichnet wird.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Beschreibt die Stärke der Kontur der Form.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: Beschreibt, wie das Innere der Form gezeichnet wird.  
  
- Dateneigenschaften zum Angeben von Koordinaten und Eckpunkten, gemessen in geräteunabhängigen Pixeln.  
  
 Da Sie von abgeleitet <xref:System.Windows.UIElement> sind, können Shape-Objekte in Bereichen und den meisten Steuerelementen verwendet werden. Das <xref:System.Windows.Controls.Canvas> Panel ist eine besonders gute Wahl zum Erstellen komplexer Zeichnungen, da es die absolute Positionierung der untergeordneten Objekte unterstützt.  
  
 Mit der- <xref:System.Windows.Shapes.Line> Klasse können Sie eine Linie zwischen zwei Punkten zeichnen. Das folgende Beispiel zeigt verschiedene Arten, wie Zeilenkoordinaten und Stricheigenschaften angegeben werden können.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Die folgende Abbildung zeigt die gerenderte <xref:System.Windows.Shapes.Line> .  
  
 ![Liniendarstellung](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Obwohl die- <xref:System.Windows.Shapes.Line> Klasse eine-Eigenschaft bereitstellt, wirkt sich <xref:System.Windows.Shapes.Shape.Fill%2A> Diese Einstellung nicht aus, da ein <xref:System.Windows.Shapes.Line> keinen Bereich aufweist.  
  
 Eine andere gängige Form ist die <xref:System.Windows.Shapes.Ellipse> .  Erstellen Sie ein, <xref:System.Windows.Shapes.Ellipse> indem Sie die <xref:System.Windows.FrameworkElement.Width%2A> Eigenschaften und der Form definieren <xref:System.Windows.FrameworkElement.Height%2A> . Zum Zeichnen eines Kreises geben Sie einen an, <xref:System.Windows.Shapes.Ellipse> dessen <xref:System.Windows.FrameworkElement.Width%2A> -Wert und- <xref:System.Windows.FrameworkElement.Height%2A> Wert gleich sind.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Die folgende Abbildung zeigt ein Beispiel für eine gerenderte <xref:System.Windows.Shapes.Ellipse> .  
  
 ![Ellipsendarstellung](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>Verwenden von Pfaden und Geometrien  
 Die <xref:System.Windows.Shapes.Path> -Klasse ermöglicht es Ihnen, Kurven und komplexe Formen zu zeichnen. Diese Kurven und Formen werden mithilfe von <xref:System.Windows.Media.Geometry> Objekten beschrieben. Um einen zu verwenden <xref:System.Windows.Shapes.Path> , erstellen Sie eine <xref:System.Windows.Media.Geometry> und verwenden Sie, um die <xref:System.Windows.Shapes.Path> -Eigenschaft des-Objekts festzulegen <xref:System.Windows.Shapes.Path.Data%2A> .  
  
 Es gibt eine Vielzahl von <xref:System.Windows.Media.Geometry> Objekten, aus denen Sie auswählen können. Die <xref:System.Windows.Media.LineGeometry> <xref:System.Windows.Media.RectangleGeometry> Klassen, und <xref:System.Windows.Media.EllipseGeometry> beschreiben relativ einfache Formen. Um komplexere Formen zu erstellen oder Kurven zu erstellen, verwenden Sie eine <xref:System.Windows.Media.PathGeometry> .  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry und PathSegments  
 <xref:System.Windows.Media.PathGeometry>Objekte bestehen aus einem oder mehreren <xref:System.Windows.Media.PathFigure> Objekten; jede <xref:System.Windows.Media.PathFigure> stellt eine andere "Abbildung" oder Form dar. Jede Komponente besteht aus <xref:System.Windows.Media.PathFigure> einem oder mehreren- <xref:System.Windows.Media.PathSegment> Objekten, die jeweils einen verbundenen Teil der Abbildung oder Form darstellen. Zu den Segment Typen zählen die folgenden: <xref:System.Windows.Media.LineSegment> , <xref:System.Windows.Media.BezierSegment> und <xref:System.Windows.Media.ArcSegment> .  
  
 Im folgenden Beispiel <xref:System.Windows.Shapes.Path> wird ein verwendet, um eine quadratische Bezier-Kurve zu zeichnen.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Die folgende Abbildung zeigt die gerenderte Form.  
  
 ![Pfaddarstellung](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Weitere Informationen zu <xref:System.Windows.Media.PathGeometry> und den anderen <xref:System.Windows.Media.Geometry> Klassen finden Sie in der [Übersicht](geometry-overview.md)über die Geometrie.  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>Abgekürzte Syntax in XAML  
 In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] können Sie auch eine spezielle abgekürzte Syntax verwenden, um eine zu beschreiben <xref:System.Windows.Shapes.Path> . Im folgenden Beispiel wird abgekürzte Syntax verwendet, um eine komplexe Form zu zeichnen.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Die folgende Abbildung zeigt ein gerendertes <xref:System.Windows.Shapes.Path> .  
  
 ![Pfaddarstellung](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 Die <xref:System.Windows.Shapes.Path.Data%2A> Attribut Zeichenfolge beginnt mit dem Befehl "muveto", der durch M angegeben wird. Dadurch wird ein Startpunkt für den Pfad im Koordinatensystem von festgelegt <xref:System.Windows.Controls.Canvas> . <xref:System.Windows.Shapes.Path>bei Daten Parametern wird die Groß-/Kleinschreibung beachtet. Das Kapital M gibt eine absolute Position für den neuen aktuellen Punkt an. Ein kleingeschriebenes m würde relative Koordinaten angeben. Das erste Segment ist eine kubische Bezier-Kurve, beginnend bei (100.200) und endet bei (400.175), gezeichnet mithilfe der beiden Kontrollpunkte (100, 25) und (400.350). Dieses Segment wird durch den C-Befehl in der <xref:System.Windows.Shapes.Path.Data%2A> Attribut Zeichenfolge angegeben. Ein großes C gibt erneut einen absoluten Pfad an. Ein kleingeschriebenes c würde einen relativen Pfad angeben.  
  
 Das zweite Segment beginnt mit einem absoluten horizontalen „Lineto“-Befehl H, der eine Linie vom vorherigen untergeordneten Endpunkt (400,175) zu einem neuen Endpunkt (280,175) zeichnet. Da es sich um einen horizontalen "LineTo"-Befehl handelt, ist der angegebene Wert eine *x*-Koordinate.  
  
 Die gesamte Pfad Syntax finden Sie in der <xref:System.Windows.Shapes.Path.Data%2A> Referenz und unter [Erstellen einer Form mithilfe von PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>Zeichnen von Formen  
 <xref:System.Windows.Media.Brush>-Objekte werden zum Zeichnen von und verwendet <xref:System.Windows.Shapes.Shape.Stroke%2A> <xref:System.Windows.Shapes.Shape.Fill%2A> . Im folgenden Beispiel werden der Strich und die Füllung eines <xref:System.Windows.Shapes.Ellipse> angegeben. Beachten Sie, dass Pinseleigenschaften entweder ein Schlüsselwort oder einen hexadezimalen Farbwert werden können. Weitere Informationen zu verfügbaren Farb Schlüsselwörtern finden Sie unter Eigenschaften der- <xref:System.Windows.Media.Colors> Klasse im- <xref:System.Windows.Media> Namespace.  
  
```xaml
<Canvas Background="LightGray">
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 Die folgende Abbildung zeigt die gerenderte <xref:System.Windows.Shapes.Ellipse> .  
  
 ![Eine Ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternativ können Sie die Eigenschafts Element Syntax verwenden, um explizit ein- <xref:System.Windows.Media.SolidColorBrush> Objekt zu erstellen, um die Form mit einer voll Tonfarbe zu zeichnen.  
  
```xaml
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 Die folgende Abbildung zeigt die gerenderte Form.  
  
 ![SolidColorBrush-Darstellung](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Sie können die Kontur oder Fläche einer Form auch mit Farbverläufen, Bildern, Mustern und mehr zeichnen. Weitere Informationen finden Sie unter [Übersicht über das Zeichnen mit voll Tonfarben und Farbverläufen](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a>Gestreckte Formen  
 Die <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path> Klassen,, <xref:System.Windows.Shapes.Polygon> , <xref:System.Windows.Shapes.Polyline> und <xref:System.Windows.Shapes.Rectangle> verfügen alle über eine- <xref:System.Windows.Shapes.Shape.Stretch%2A> Eigenschaft. Diese Eigenschaft bestimmt, wie der Inhalt eines- <xref:System.Windows.Shapes.Shape> Objekts (die Form, die gezeichnet werden soll) gestreckt wird, um den <xref:System.Windows.Shapes.Shape> Layoutbereich des Objekts zu füllen. Der <xref:System.Windows.Shapes.Shape> Layoutbereich eines-Objekts ist die Menge des Speicherplatzes <xref:System.Windows.Shapes.Shape> , der vom Layoutsystem aufgrund einer expliziten <xref:System.Windows.FrameworkElement.Width%2A> und- <xref:System.Windows.FrameworkElement.Height%2A> Einstellung oder aufgrund der <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> -und- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> Einstellungen zugeordnet wird. Weitere Informationen zum Layout in Windows Presentation Foundation finden Sie unter Übersicht über [das Layout.](../advanced/layout.md)  
  
 Die Stretch-Eigenschaft nimmt einen der folgenden Werte an:  
  
- <xref:System.Windows.Media.Stretch.None>: Der <xref:System.Windows.Shapes.Shape> Inhalt des Objekts wird nicht gestreckt.  
  
- <xref:System.Windows.Media.Stretch.Fill>: Der <xref:System.Windows.Shapes.Shape> Inhalt des Objekts wird gestreckt, um den Layoutbereich auszufüllen.  Das Seitenverhältnis wird nicht beibehalten.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: Der <xref:System.Windows.Shapes.Shape> Inhalt des Objekts wird so weit wie möglich gestreckt, um den Layoutbereich auszufüllen, während das ursprüngliche Seitenverhältnis beibehalten wird.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: Der <xref:System.Windows.Shapes.Shape> Inhalt des Objekts wird gestreckt, um seinen Layoutbereich vollständig auszufüllen, während das ursprüngliche Seitenverhältnis beibehalten wird.  
  
 Beachten Sie, dass <xref:System.Windows.Shapes.Shape> die <xref:System.Windows.Shapes.Shape> Kontur des Objekts nach der Streckung gezeichnet wird, wenn der Inhalt eines-Objekts gestreckt wird.  
  
 Im folgenden Beispiel <xref:System.Windows.Shapes.Polygon> wird eine zum Zeichnen eines sehr kleinen Dreiecks von (0,0) bis (0,0) bis (1, 1) verwendet. Der <xref:System.Windows.Shapes.Polygon> und die-Eigenschaft des-Objekts <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> werden auf 100 festgelegt, und die Stretch-Eigenschaft ist auf Fill festgelegt. Folglich wird der Inhalt des <xref:System.Windows.Shapes.Polygon> Objekts (das Dreieck) gestreckt, um den größeren Bereich auszufüllen.  
  
```xaml
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
```

```csharp
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
```

<a name="transforms"></a>
## <a name="transforming-shapes"></a>Transformieren von Formen  
 Die- <xref:System.Windows.Media.Transform> Klasse stellt die Mittel zum Transformieren von Formen in einer zweidimensionalen Ebene bereit.  Zu den verschiedenen Transformations Typen zählen Drehung ( <xref:System.Windows.Media.RotateTransform> ), Skalierung ( <xref:System.Windows.Media.ScaleTransform> ), Schiefe ( <xref:System.Windows.Media.SkewTransform> ) und Übersetzung ( <xref:System.Windows.Media.TranslateTransform> ).  
  
 Eine allgemeine Transformation einer Form ist die Drehung.  Um eine Form zu drehen, erstellen Sie eine <xref:System.Windows.Media.RotateTransform> und geben deren an <xref:System.Windows.Media.RotateTransform.Angle%2A> . Ein <xref:System.Windows.Media.RotateTransform.Angle%2A> von 45 dreht das Element um 45 Grad im Uhrzeigersinn, ein Winkel von 90 dreht das Element um 90 Grad im Uhrzeigersinn und so weiter. Legen Sie die-Eigenschaft und die-Eigenschaft fest <xref:System.Windows.Media.RotateTransform.CenterX%2A> <xref:System.Windows.Media.RotateTransform.CenterY%2A> , wenn Sie den Punkt steuern möchten, an dem das Element gedreht wird. Diese Eigenschaftswerte werden im Koordinatenraum des transformierten Elements ausgedrückt. <xref:System.Windows.Media.RotateTransform.CenterX%2A>und <xref:System.Windows.Media.RotateTransform.CenterY%2A> haben die Standardwerte 0 (null). Wenden <xref:System.Windows.Media.RotateTransform> Sie schließlich auf das-Element an. Wenn Sie nicht möchten, dass sich die Transformation auf das Layout auswirkt, legen Sie die-Eigenschaft der Form fest <xref:System.Windows.UIElement.RenderTransform%2A> .  
  
 Im folgenden Beispiel wird ein-Wert <xref:System.Windows.Media.RotateTransform> verwendet, um eine Form 45 Grad um die linke obere Ecke (0,0) zu drehen.  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 Im nächsten Beispiel eine andere Form um 45 Grad gedreht wird, aber dieses Mal wird sie über den Punkt (25,50) gedreht.  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 In der folgenden Abbildung werden die Ergebnisse der Anwendung der zwei Transformationen dargestellt.  
  
 ![45-Grad-Drehungen mit unterschiedlichen Mittelpunkten](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 In den vorherigen Beispielen wurde eine einzelne Transformation auf jedes Shape-Objekt angewendet. Verwenden Sie zum Anwenden mehrerer Transformationen auf eine Form (oder ein beliebiges anderes UI-Element) <xref:System.Windows.Media.TransformGroup> .  
  
## <a name="see-also"></a>Siehe auch

- [2D-Grafiken und Bildverarbeitung](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Übersicht über das Zeichnen mit Volltonfarben und Farbverläufen](painting-with-solid-colors-and-gradients-overview.md)
- [Übersicht über die Geometrie](geometry-overview.md)
- [Exemplarische Vorgehensweise: Walkthrough: My first WPF desktop application (Exemplarische Vorgehensweise: Meine erste WPF-Desktopanwendung)](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Übersicht über Animationen](animation-overview.md)
