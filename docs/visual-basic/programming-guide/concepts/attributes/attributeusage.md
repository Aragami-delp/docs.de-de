---
title: AttributeUsage
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: 677d49aba38801f2adf42cc745983af30b3eddc5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400731"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="92d7f-102">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92d7f-102">AttributeUsage (Visual Basic)</span></span>

<span data-ttu-id="92d7f-103">Bestimmt, wie eine benutzerdefinierte Attributklasse verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="92d7f-103">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="92d7f-104">`AttributeUsage` ist ein Attribut, dass auf benutzerdefinierte Attributdefinitionen zur Steuerung der Anwendung neuer Attribute angewendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="92d7f-104">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="92d7f-105">Die Standardeinstellungen sehen wie folgt aus, wenn Sie explizit angewendet werden:</span><span class="sxs-lookup"><span data-stu-id="92d7f-105">The default settings look like this when applied explicitly:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="92d7f-106">In diesem Beispiel kann die Klasse `NewAttribute` auf jede attributfähige Codeentität angewendet werden; allerdings nur einmal pro Entität.</span><span class="sxs-lookup"><span data-stu-id="92d7f-106">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="92d7f-107">Wenn sie auf eine Basisklasse angewendet wird, wird sie an eine abgeleitete Klasse vererbt.</span><span class="sxs-lookup"><span data-stu-id="92d7f-107">It is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="92d7f-108">Die Argumente `AllowMultiple` und `Inherited` sind optional, sodass dieser Code die gleiche Wirkung hat:</span><span class="sxs-lookup"><span data-stu-id="92d7f-108">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="92d7f-109">Das erste `AttributeUsage`-Argument muss mindestens ein Element der <xref:System.AttributeTargets>-Enumeration sein.</span><span class="sxs-lookup"><span data-stu-id="92d7f-109">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="92d7f-110">Mehrere Zieltypen können mithilfe des OR-Operator wie folgt verknüpft werden:</span><span class="sxs-lookup"><span data-stu-id="92d7f-110">Multiple target types can be linked together with the OR operator, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

<span data-ttu-id="92d7f-111">Wenn das `AllowMultiple`-Argument auf `true` festgelegt ist, kann das daraus entstehende Attribut wie folgt mehr als einmal auf eine einzelne Entität angewendet werden:</span><span class="sxs-lookup"><span data-stu-id="92d7f-111">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

<span data-ttu-id="92d7f-112">In diesem Fall kann `MultiUseAttr` wiederholt angewendet werden, da `AllowMultiple` auf `true` festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="92d7f-112">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="92d7f-113">Beide gezeigten Formate für das Anwenden von mehreren Attributen sind gültig.</span><span class="sxs-lookup"><span data-stu-id="92d7f-113">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="92d7f-114">Wenn `Inherited` auf `false` festgelegt ist, wird das Attribut nicht an die von der attribuierten Klasse abgeleiteten Klassen vererbt.</span><span class="sxs-lookup"><span data-stu-id="92d7f-114">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="92d7f-115">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="92d7f-115">For example:</span></span>

```vb
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>
Class Attr1
    Inherits Attribute
End Class

<Attr1()>
Class BClass

End Class

Class DClass
    Inherits BClass
End Class
```

<span data-ttu-id="92d7f-116">In diesem Fall wird `Attr1` nicht durch Vererbung auf `DClass` angewendet.</span><span class="sxs-lookup"><span data-stu-id="92d7f-116">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="92d7f-117">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="92d7f-117">Remarks</span></span>

<span data-ttu-id="92d7f-118">Das `AttributeUsage`-Attribut ist für die einmalige Nutzung bestimmt; es kann nicht mehr als einmal auf dieselbe Klasse angewendet werden.</span><span class="sxs-lookup"><span data-stu-id="92d7f-118">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="92d7f-119">`AttributeUsage` ist ein Alias für <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="92d7f-119">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="92d7f-120">Weitere Informationen finden Sie unter [Zugreifen auf Attribute mithilfe der Reflektion (Visual Basic)](accessing-attributes-by-using-reflection.md).</span><span class="sxs-lookup"><span data-stu-id="92d7f-120">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="92d7f-121">Beispiel</span><span class="sxs-lookup"><span data-stu-id="92d7f-121">Example</span></span>

<span data-ttu-id="92d7f-122">In folgendem Beispiel wird die Wirkung der Argumente `Inherited` und `AllowMultiple` auf das Attribut `AttributeUsage` und die Enumeration benutzerdefinierter Attribute veranschaulicht, die auf eine Klasse angewendet wurden.</span><span class="sxs-lookup"><span data-stu-id="92d7f-122">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

```vb
' Create some custom attributes:
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>
Class A1
    Inherits System.Attribute
End Class

<AttributeUsage(System.AttributeTargets.Class)>
Class A2
    Inherits System.Attribute
End Class

<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>
Class A3
    Inherits System.Attribute
End Class

' Apply custom attributes to classes:
<A1(), A2()>
Class BaseClass

End Class

<A3(), A3()>
Class DerivedClass
    Inherits BaseClass
End Class

Public Class TestAttributeUsage
    Sub Main()
        Dim b As New BaseClass
        Dim d As New DerivedClass
        ' Display custom attributes for each class.
        Console.WriteLine("Attributes on Base Class:")
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)

        For Each attr In attrs
            Console.WriteLine(attr)
        Next

        Console.WriteLine("Attributes on Derived Class:")
        attrs = d.GetType().GetCustomAttributes(True)
        For Each attr In attrs
            Console.WriteLine(attr)
        Next
    End Sub
End Class
```

## <a name="sample-output"></a><span data-ttu-id="92d7f-123">Beispielausgabe</span><span class="sxs-lookup"><span data-stu-id="92d7f-123">Sample Output</span></span>

```console
Attributes on Base Class:
A1
A2
Attributes on Derived Class:
A3
A3
A2
```

## <a name="see-also"></a><span data-ttu-id="92d7f-124">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="92d7f-124">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="92d7f-125">Visual Basic-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="92d7f-125">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="92d7f-126">Attribute</span><span class="sxs-lookup"><span data-stu-id="92d7f-126">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="92d7f-127">Reflektion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92d7f-127">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="92d7f-128">Attribute (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92d7f-128">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- <span data-ttu-id="92d7f-129">[Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md) (Erstellen benutzerdefinierter Attribute (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="92d7f-129">[Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md)</span></span>
- <span data-ttu-id="92d7f-130">[Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md) (Zugreifen auf Attribute mithilfe der Reflektion (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="92d7f-130">[Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md)</span></span>
