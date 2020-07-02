---
title: 'Gewusst wie: Erstellen und Binden an ObservableCollection'
description: Erfahren Sie, wie Sie eine Sammlung erstellen und binden, die von der ObservableCollection-Klasse in Windows Presentation Foundation abgeleitet ist.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], ObservableCollection class
- notifications [WPF]
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
ms.openlocfilehash: 36e3d2d84aff0ab96c9b2914da28d4c968c32bac
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617868"
---
# <a name="how-to-create-and-bind-to-an-observablecollection"></a>Gewusst wie: Erstellen und Binden an ObservableCollection
Dieses Beispiel zeigt, wie Sie eine Auflistung erstellen und binden, die von der-Klasse abgeleitet wird. dabei handelt es sich um eine Auflistungs <xref:System.Collections.ObjectModel.ObservableCollection%601> Klasse, die beim Hinzufügen oder Entfernen von Elementen Benachrichtigungen bereitstellt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Codebeispiel wird die Implementierung einer `NameList`-Auflistung veranschaulicht:  
  
```csharp  
public class NameList : ObservableCollection<PersonName>  
{  
    public NameList() : base()  
    {  
        Add(new PersonName("Willa", "Cather"));  
        Add(new PersonName("Isak", "Dinesen"));  
        Add(new PersonName("Victor", "Hugo"));  
        Add(new PersonName("Jules", "Verne"));  
    }  
  }  
  
  public class PersonName  
  {  
      private string firstName;  
      private string lastName;  
  
      public PersonName(string first, string last)  
      {  
          this.firstName = first;  
          this.lastName = last;  
      }  
  
      public string FirstName  
      {  
          get { return firstName; }  
          set { firstName = value; }  
      }  
  
      public string LastName  
      {  
          get { return lastName; }  
          set { lastName = value; }  
      }  
  }  
```  
  
```vb  
Public Class NameList  
    Inherits ObservableCollection(Of PersonName)  
  
    ' Methods  
    Public Sub New()  
        MyBase.Add(New PersonName("Willa", "Cather"))  
        MyBase.Add(New PersonName("Isak", "Dinesen"))  
        MyBase.Add(New PersonName("Victor", "Hugo"))  
        MyBase.Add(New PersonName("Jules", "Verne"))  
    End Sub  
  
End Class  
  
Public Class PersonName  
    ' Methods  
    Public Sub New(ByVal first As String, ByVal last As String)  
        Me._firstName = first  
        Me._lastName = last  
    End Sub  
  
    ' Properties  
    Public Property FirstName() As String  
        Get  
            Return Me._firstName  
        End Get  
        Set(ByVal value As String)  
            Me._firstName = value  
        End Set  
    End Property  
  
    Public Property LastName() As String  
        Get  
            Return Me._lastName  
        End Get  
        Set(ByVal value As String)  
            Me._lastName = value  
        End Set  
    End Property  
  
    ' Fields  
    Private _firstName As String  
    Private _lastName As String  
End Class  
```  
  
 Sie können die Auflistung für die Bindung auf die gleiche Weise wie andere Common Language Runtime (CLR)-Objekte zur Verfügung stellen, wie unter [Bereitstellen von Daten für die Bindung in XAML](how-to-make-data-available-for-binding-in-xaml.md)beschrieben. Sie können beispielsweise die Auflistung in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] instanziieren und sie als Ressource, wie hier dargestellt, angeben:  
  
```xaml  
<Window  
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
  xmlns:c="clr-namespace:SDKSample"  
  x:Class="SDKSample.Window1"  
  Width="400"  
  Height="280"  
  Title="MultiBinding Sample">  
  
  <Window.Resources>  
    <c:NameList x:Key="NameListData"/>  
  
...  
  
</Window.Resources>  
```  
  
 Danach können Sie eine Bindung an die Auflistung erstellen:  
  
```xaml  
<ListBox Width="200"  
         ItemsSource="{Binding Source={StaticResource NameListData}}"  
         ItemTemplate="{StaticResource NameItemTemplate}"  
         IsSynchronizedWithCurrentItem="True"/>  
```  
  
 Die Definition von `NameItemTemplate` wird hier nicht gezeigt.  
  
> [!NOTE]
> Die Objekte in der Auflistung müssen die unter [Übersicht über Bindungsquellen](binding-sources-overview.md) beschriebenen Anforderungen erfüllen. Insbesondere wenn Sie oder verwenden (z. b. Wenn <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> Sie möchten, dass sich [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] die Quell Eigenschaften dynamisch ändern), müssen Sie einen geeigneten Benachrichtigungs Mechanismus für geänderte Eigenschaften wie die- <xref:System.ComponentModel.INotifyPropertyChanged> Schnittstelle implementieren.  
  
 Weitere Informationen finden Sie in der [Übersicht über die Datenbindung](../../../desktop-wpf/data/data-binding-overview.md) unter „Binden an Auflistungen“.  
  
## <a name="see-also"></a>Weitere Informationen

- [Sortieren von Daten in einer Ansicht](how-to-sort-data-in-a-view.md)
- [Filtern von Daten in einer Ansicht](how-to-filter-data-in-a-view.md)
- [Sortieren und Gruppieren von Daten mit einer Ansicht in XAML](how-to-sort-and-group-data-using-a-view-in-xaml.md)
- [Übersicht über die Datenbindung](../../../desktop-wpf/data/data-binding-overview.md)
- [Artikel zu Vorgehensweisen](data-binding-how-to-topics.md)
