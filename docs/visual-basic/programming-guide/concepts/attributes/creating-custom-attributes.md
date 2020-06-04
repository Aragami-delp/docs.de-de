---
title: Erstellen benutzerdefinierter Attribute
ms.date: 07/20/2015
ms.assetid: 5c9ef584-6c7c-496b-92a9-6e42f8d9ca28
ms.openlocfilehash: 84b400c2fa1b2d4019eec32092f954d680e64978
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400693"
---
# <a name="creating-custom-attributes-visual-basic"></a><span data-ttu-id="04e95-102">Creating Custom Attributes (Visual Basic) (Erstellen benutzerdefinierter Attribute (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="04e95-102">Creating Custom Attributes (Visual Basic)</span></span>

<span data-ttu-id="04e95-103">Sie können eigene benutzerdefinierte Attribute erstellen, indem Sie eine Attributklasse definieren. Dies ist eine Klasse, die direkt oder indirekt von <xref:System.Attribute> abgeleitet wird, was es einfach macht, schnell Attributdefinitionen in Metadaten zu identifizieren.</span><span class="sxs-lookup"><span data-stu-id="04e95-103">You can create your own custom attributes by defining an attribute class, a class that derives directly or indirectly from <xref:System.Attribute>, which makes identifying attribute definitions in metadata fast and easy.</span></span> <span data-ttu-id="04e95-104">Angenommen, Sie möchten Typen mit dem Namen des Programmierers markieren, der den Typ geschrieben hat.</span><span class="sxs-lookup"><span data-stu-id="04e95-104">Suppose you want to tag types with the name of the programmer who wrote the type.</span></span> <span data-ttu-id="04e95-105">Sie definieren möglicherweise eine benutzerdefinierte `Author`-Attributklasse:</span><span class="sxs-lookup"><span data-stu-id="04e95-105">You might define a custom `Author` attribute class:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName
        version = 1.0
    End Sub
End Class
```

<span data-ttu-id="04e95-106">Der Klassenname ist der Attributname, `Author`.</span><span class="sxs-lookup"><span data-stu-id="04e95-106">The class name is the attribute's name, `Author`.</span></span> <span data-ttu-id="04e95-107">Er ist von `System.Attribute` abgeleitet, ist also eine benutzerdefinierte Attributklasse.</span><span class="sxs-lookup"><span data-stu-id="04e95-107">It is derived from `System.Attribute`, so it is a custom attribute class.</span></span> <span data-ttu-id="04e95-108">Die Parameter des Konstruktors sind die Positionsparameter des benutzerdefinierten Attributs.</span><span class="sxs-lookup"><span data-stu-id="04e95-108">The constructor's parameters are the custom attribute's positional parameters.</span></span> <span data-ttu-id="04e95-109">In diesem Beispiel ist `name` ein Positionsparameter.</span><span class="sxs-lookup"><span data-stu-id="04e95-109">In this example, `name` is a positional parameter.</span></span> <span data-ttu-id="04e95-110">Alle öffentlichen Lese-/Schreibfelder oder -Eigenschaften werden Parameter genannt.</span><span class="sxs-lookup"><span data-stu-id="04e95-110">Any public read-write fields or properties are named parameters.</span></span> <span data-ttu-id="04e95-111">In diesem Fall ist `version` der einzige Parameter mit Namen.</span><span class="sxs-lookup"><span data-stu-id="04e95-111">In this case, `version` is the only named parameter.</span></span> <span data-ttu-id="04e95-112">Beachten Sie die Verwendung des `AttributeUsage`-Attributs, um das `Author`-Attribut ausschließlich für Klassen- und `Structure`-Deklarationen gültig zu machen.</span><span class="sxs-lookup"><span data-stu-id="04e95-112">Note the use of the `AttributeUsage` attribute to make the `Author` attribute valid only on class and `Structure` declarations.</span></span>

<span data-ttu-id="04e95-113">Sie könnten dieses neue Attribut wie folgt verwenden:</span><span class="sxs-lookup"><span data-stu-id="04e95-113">You could use this new attribute as follows:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

<span data-ttu-id="04e95-114">`AttributeUsage` verfügt über einen Parameter, `AllowMultiple`, mit dem Sie ein benutzerdefiniertes Attribut zur einmaligen oder mehrfachen Nutzung erstellen können.</span><span class="sxs-lookup"><span data-stu-id="04e95-114">`AttributeUsage` has a named parameter, `AllowMultiple`, with which you can make a custom attribute single-use or multiuse.</span></span> <span data-ttu-id="04e95-115">Im folgenden Codebeispiel wird ein mehrfach verwendbares Attribut erstellt.</span><span class="sxs-lookup"><span data-stu-id="04e95-115">In the following code example, a multiuse attribute is created.</span></span>

```vb
' multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
```

<span data-ttu-id="04e95-116">Im folgenden Codebeispiel werden mehrere Attribute desselben Typs auf eine Klasse angewendet.</span><span class="sxs-lookup"><span data-stu-id="04e95-116">In the following code example, multiple attributes of the same type are applied to a class.</span></span>

```vb
<Author("P. Ackerman", Version:=1.1),
Author("R. Koch", Version:=1.2)>
Class SampleClass
    ' P. Ackerman's code goes here...
    ' R. Koch's code goes here...
End Class
```

> [!NOTE]
> <span data-ttu-id="04e95-117">Wenn die Attributklasse eine Eigenschaft enthält, muss die Eigenschaft Lese- und Schreibberechtigung aufweisen.</span><span class="sxs-lookup"><span data-stu-id="04e95-117">If your attribute class contains a property, that property must be read-write.</span></span>

## <a name="see-also"></a><span data-ttu-id="04e95-118">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="04e95-118">See also</span></span>

- <xref:System.Reflection>
- [<span data-ttu-id="04e95-119">Visual Basic-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="04e95-119">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="04e95-120">Verfassen von benutzerdefinierten Attributen</span><span class="sxs-lookup"><span data-stu-id="04e95-120">Writing Custom Attributes</span></span>](../../../../standard/attributes/writing-custom-attributes.md)
- [<span data-ttu-id="04e95-121">Reflektion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04e95-121">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="04e95-122">Attribute (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04e95-122">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- <span data-ttu-id="04e95-123">[Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md) (Zugreifen auf Attribute mithilfe der Reflektion (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="04e95-123">[Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md)</span></span>
- [<span data-ttu-id="04e95-124">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04e95-124">AttributeUsage (Visual Basic)</span></span>](attributeusage.md)
