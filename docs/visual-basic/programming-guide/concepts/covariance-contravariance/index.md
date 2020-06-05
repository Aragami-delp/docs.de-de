---
title: Kovarianz und Kontravarianz
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 11dd71a8cfde12b7af1de79e3f5a095f79d8aa6e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400629"
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="e007f-102">Kovarianz und Kontravarianz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e007f-102">Covariance and Contravariance (Visual Basic)</span></span>

<span data-ttu-id="e007f-103">Kovarianz und Kontravarianz in Visual Basic ermöglichen die implizite Referenzkonvertierung für Arraytypen, Delegattypen und generische Typargumente.</span><span class="sxs-lookup"><span data-stu-id="e007f-103">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="e007f-104">Die Kovarianz behält die Zuweisungskompatibilität bei und die Kontravarianz kehrt sie um.</span><span class="sxs-lookup"><span data-stu-id="e007f-104">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>

<span data-ttu-id="e007f-105">Der folgende Code veranschaulicht den Unterschied zwischen Zuweisungskompatibilität, Kovarianz und Kontravarianz.</span><span class="sxs-lookup"><span data-stu-id="e007f-105">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>

```vb
' Assignment compatibility.
Dim str As String = "test"
' An object of a more derived type is assigned to an object of a less derived type.
Dim obj As Object = str

' Covariance.
Dim strings As IEnumerable(Of String) = New List(Of String)()
' An object that is instantiated with a more derived type argument
' is assigned to an object instantiated with a less derived type argument.
' Assignment compatibility is preserved.
Dim objects As IEnumerable(Of Object) = strings

' Contravariance.
' Assume that there is the following method in the class:
' Shared Sub SetObject(ByVal o As Object)
' End Sub
Dim actObject As Action(Of Object) = AddressOf SetObject

' An object that is instantiated with a less derived type argument
' is assigned to an object instantiated with a more derived type argument.
' Assignment compatibility is reversed.
Dim actString As Action(Of String) = actObject
```

<span data-ttu-id="e007f-106">Die Kovarianz für Arrays ermöglicht die implizite Konvertierung eines Arrays mit einem stärker abgeleiteten Typ zu einem Array mit einem schwächer abgeleiteten Typ.</span><span class="sxs-lookup"><span data-stu-id="e007f-106">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="e007f-107">Dieser Vorgang ist jedoch nicht typsicher, wie im folgenden Codebeispiel gezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="e007f-107">But this operation is not type safe, as shown in the following code example.</span></span>

```vb
Dim array() As Object = New String(10) {}
' The following statement produces a run-time exception.
' array(0) = 10
```

<span data-ttu-id="e007f-108">Die Unterstützung von Kovarianz und Kontravarianz für Methodengruppen ermöglicht es, Methodensignaturen mit Delegattypen abzugleichen.</span><span class="sxs-lookup"><span data-stu-id="e007f-108">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="e007f-109">Das bedeutet, dass Sie Delegaten nicht nur Methoden mit übereinstimmenden Signaturen zuweisen können, sondern auch Methoden, die mehrere abgeleitete Typen zurückgeben (Kovarianz) oder die Parameter akzeptieren, die über weniger abgeleitete Typen verfügen, als durch den Delegattyp angegeben wurde (Kontravarianz).</span><span class="sxs-lookup"><span data-stu-id="e007f-109">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="e007f-110">Weitere Informationen finden Sie unter [Variance in Delegates (Visual Basic) (Varianz in Delegaten (Visual Basic))](variance-in-delegates.md) und [Using Variance in Delegates (Visual Basic) (Verwenden von Varianz in Delegaten (Visual Basic))](using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="e007f-110">For more information, see [Variance in Delegates (Visual Basic)](variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](using-variance-in-delegates.md).</span></span>

<span data-ttu-id="e007f-111">Im folgenden Codebeispiel wird die Unterstützung von Methodengruppen durch Kovarianz und Kontravarianz veranschaulicht.</span><span class="sxs-lookup"><span data-stu-id="e007f-111">The following code example shows covariance and contravariance support for method groups.</span></span>

```vb
Shared Function GetObject() As Object
    Return Nothing
End Function

Shared Sub SetObject(ByVal obj As Object)
End Sub

Shared Function GetString() As String
    Return ""
End Function

Shared Sub SetString(ByVal str As String)

End Sub

Shared Sub Test()
    ' Covariance. A delegate specifies a return type as object,
    ' but you can assign a method that returns a string.
    Dim del As Func(Of Object) = AddressOf GetString

    ' Contravariance. A delegate specifies a parameter type as string,
    ' but you can assign a method that takes an object.
    Dim del2 As Action(Of String) = AddressOf SetObject
End Sub
```

<span data-ttu-id="e007f-112">In .NET Framework 4 oder höher unterstützt Visual Basic Kovarianz und Kontra Varianz in generischen Schnittstellen und Delegaten und ermöglicht die implizite Konvertierung generischer Typparameter.</span><span class="sxs-lookup"><span data-stu-id="e007f-112">In .NET Framework 4 or later, Visual Basic supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="e007f-113">Weitere Informationen finden Sie unter [Variance in Generic Interfaces (Visual Basic) (Varianz in generischen Schnittstellen (Visual Basic))](variance-in-generic-interfaces.md) und [Variance in Delegates (Visual Basic) (Varianz in Delegaten (Visual Basic))](variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="e007f-113">For more information, see [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

<span data-ttu-id="e007f-114">Das folgende Codebeispiel zeigt die implizite Verweiskonvertierung bei generischen Schnittstellen.</span><span class="sxs-lookup"><span data-stu-id="e007f-114">The following code example shows implicit reference conversion for generic interfaces.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="e007f-115">Generische Schnittstellen oder Delegate werden als *variant* bezeichnet, wenn deren generische Parameter als kovariant oder kontravariant deklariert sind.</span><span class="sxs-lookup"><span data-stu-id="e007f-115">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="e007f-116">Visual Basic ermöglicht es Ihnen, eigene variante Schnittstellen oder Delegate zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="e007f-116">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="e007f-117">Weitere Informationen finden Sie unter [Creating Variant Generic Interfaces (Visual Basic) (Erstellen von varianten generischen Schnittstellen (Visual Basic))](creating-variant-generic-interfaces.md) und [Variance in Delegates (Visual Basic) (Varianz in Delegaten (Visual Basic))](variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="e007f-117">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="e007f-118">Verwandte Themen</span><span class="sxs-lookup"><span data-stu-id="e007f-118">Related Topics</span></span>

|<span data-ttu-id="e007f-119">Titel</span><span class="sxs-lookup"><span data-stu-id="e007f-119">Title</span></span>|<span data-ttu-id="e007f-120">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="e007f-120">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="e007f-121">Variance in Generic Interfaces (Visual Basic) (Varianz in generischen Schnittstellen (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="e007f-121">Variance in Generic Interfaces (Visual Basic)</span></span>](variance-in-generic-interfaces.md)|<span data-ttu-id="e007f-122">Erläutert Ko- und Kontravarianz in generischen Schnittstellen und enthält eine Liste der Varianten generischen Schnittstellen in .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e007f-122">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|
|[<span data-ttu-id="e007f-123">Creating Variant Generic Interfaces (Visual Basic) (Erstellen varianter generischer Schnittstellen (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="e007f-123">Creating Variant Generic Interfaces (Visual Basic)</span></span>](creating-variant-generic-interfaces.md)|<span data-ttu-id="e007f-124">Zeigt, wie benutzerdefinierte variante Schnittstellen erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="e007f-124">Shows how to create custom variant interfaces.</span></span>|
|[<span data-ttu-id="e007f-125">Using Variance in Interfaces for Generic Collections (Visual Basic) (Verwenden von Varianz in Schnittstellen für generische Auflistungen (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="e007f-125">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="e007f-126">Zeigt, wie die Unterstützung durch Kovarianz und Kontravarianz bei <xref:System.Collections.Generic.IEnumerable%601>- und <xref:System.IComparable%601>-Schnittstellen bei der Wiederverwendung Ihres Codes helfen kann.</span><span class="sxs-lookup"><span data-stu-id="e007f-126">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|
|[<span data-ttu-id="e007f-127">Variance in Delegates (Visual Basic) (Varianz in Delegaten (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="e007f-127">Variance in Delegates (Visual Basic)</span></span>](variance-in-delegates.md)|<span data-ttu-id="e007f-128">Erläutert Ko- und Kontravarianz in generischen und nicht generischen Delegaten und stellt eine Liste von varianten generischen Delegaten im .NET Framework bereit.</span><span class="sxs-lookup"><span data-stu-id="e007f-128">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|
|[<span data-ttu-id="e007f-129">Using Variance in Delegates (Visual Basic) (Verwenden von Varianz in Delegaten (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="e007f-129">Using Variance in Delegates (Visual Basic)</span></span>](using-variance-in-delegates.md)|<span data-ttu-id="e007f-130">Zeigt, wie die Unterstützung durch Kovarianz und Kontravarianz in nicht generischen Delegaten verwendet werden kann, um Methodensignaturen mit Delegattypen abzugleichen.</span><span class="sxs-lookup"><span data-stu-id="e007f-130">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|
|[<span data-ttu-id="e007f-131">Using Variance for Func and Action Generic Delegates (Visual Basic) (Verwenden von Varianz für die generischen Delegaten Func und Action (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="e007f-131">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="e007f-132">Zeigt, wie die Unterstützung durch Kovarianz und Kontravarianz bei `Func`- und `Action`-Delegaten bei der Wiederverwendung Ihres Codes helfen kann.</span><span class="sxs-lookup"><span data-stu-id="e007f-132">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
