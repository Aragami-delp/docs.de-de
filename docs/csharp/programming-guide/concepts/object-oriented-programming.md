---
title: Objektorientiertes Programmieren (C#)
ms.date: 05/13/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 541d1a2581a3241f35fc8478040c007b6581e3b2
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396689"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="921cd-102">Objektorientiertes Programmieren (C#)</span><span class="sxs-lookup"><span data-stu-id="921cd-102">Object-Oriented programming (C#)</span></span>

<span data-ttu-id="921cd-103">C# bietet vollständige Unterstützung für objektorientierte Programmierung, einschließlich Kapselung, Vererbung und Polymorphie.</span><span class="sxs-lookup"><span data-stu-id="921cd-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

- <span data-ttu-id="921cd-104">*Kapselung* bedeutet, dass eine Gruppe verwandter Eigenschaften, Methoden sowie anderer Member als eine Einheit bzw. ein Objekt behandelt wird.</span><span class="sxs-lookup"><span data-stu-id="921cd-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>
- <span data-ttu-id="921cd-105">*Vererbung* beschreibt die Fähigkeit, neue Klassen basierend auf einer vorhandenen Klasse zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="921cd-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>
- <span data-ttu-id="921cd-106">*Polymorphismus* bedeutet, dass Sie mehrere Klassen untereinander austauschen können, obwohl jede Klasse dieselben Eigenschaften oder Methoden auf unterschiedliche Art und Weise implementiert.</span><span class="sxs-lookup"><span data-stu-id="921cd-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

## <a name="classes-and-objects"></a><span data-ttu-id="921cd-107">Klassen und Objekte</span><span class="sxs-lookup"><span data-stu-id="921cd-107">Classes and objects</span></span>

<span data-ttu-id="921cd-108">Die Begriffe *Klasse* und *Objekt* beschreiben jeweils den *Typ* von Objekten und die *Instanzen* von Klassen.</span><span class="sxs-lookup"><span data-stu-id="921cd-108">The terms *class* and *object* describe the *type* of objects, and the *instances* of classes, respectively.</span></span> <span data-ttu-id="921cd-109">Das Erstellen eines Objekts wird daher als *Instanziierung* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="921cd-109">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="921cd-110">Um auf den Vergleich mit Bauplänen zurückzukommen: Eine Klasse ist ein Bauplan, und ein Objekt ist ein anhand dieses Bauplans errichtetes Gebäude.</span><span class="sxs-lookup"><span data-stu-id="921cd-110">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="921cd-111">So definieren Sie eine Klasse</span><span class="sxs-lookup"><span data-stu-id="921cd-111">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="921cd-112">C# stellt auch Typen namens *Strukturen* bereit, die nützlich sind, wenn Sie keine Unterstützung für Vererbungen oder Polymorphie benötigen.</span><span class="sxs-lookup"><span data-stu-id="921cd-112">C# also provides types called *structures* that are useful when you don't need support for inheritance or polymorphism.</span></span>

<span data-ttu-id="921cd-113">So definieren Sie eine Struktur</span><span class="sxs-lookup"><span data-stu-id="921cd-113">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="921cd-114">Weitere Informationen finden Sie in den Artikeln zu den Schlüsselwörtern [Klasse](../../language-reference/keywords/class.md) und [Struktur](../../language-reference/builtin-types/struct.md).</span><span class="sxs-lookup"><span data-stu-id="921cd-114">For more information, see the articles on the [class](../../language-reference/keywords/class.md) and [struct](../../language-reference/builtin-types/struct.md) keywords.</span></span>

### <a name="class-members"></a><span data-ttu-id="921cd-115">Klassenmember</span><span class="sxs-lookup"><span data-stu-id="921cd-115">Class members</span></span>

<span data-ttu-id="921cd-116">Jede Klasse kann über andere *Klassenmember* verfügen. Diese enthalten Eigenschaften, die Klassendaten beschreiben, Methoden, die Klassenverhalten definieren sowie Ereignisse, die die Kommunikation zwischen verschiedenen Klassen und Objekten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="921cd-116">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="921cd-117">Eigenschaften und Felder</span><span class="sxs-lookup"><span data-stu-id="921cd-117">Properties and fields</span></span>

<span data-ttu-id="921cd-118">Felder und Eigenschaften stellen die in einem Objekt enthaltenen Informationen dar.</span><span class="sxs-lookup"><span data-stu-id="921cd-118">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="921cd-119">Felder sind wie Variablen, sie können direkt gelesen oder festgelegt werden und unterliegen anwendbaren Zugriffsmodifizierern.</span><span class="sxs-lookup"><span data-stu-id="921cd-119">Fields are like variables because they can be read or set directly, subject to applicable access modifiers.</span></span>

<span data-ttu-id="921cd-120">So definieren Sie ein Feld, auf das innerhalb von Instanzen der Klasse zugegriffen werden kann:</span><span class="sxs-lookup"><span data-stu-id="921cd-120">To define a field that can be accessed from within instances of the class:</span></span>

```csharp
public class SampleClass
{
    string sampleField;
}
```

<span data-ttu-id="921cd-121">Eigenschaften verfügen über `get`- und `set`-Zugriffsmethoden, die eine bessere Kontrolle über das Festlegen oder Abrufen von Werten ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="921cd-121">Properties have `get` and `set` accessors, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="921cd-122">Mit C# können Sie ein privates Feld erstellen, um den Eigenschaftswert zu speichern, oder Sie können automatisch implementierte Eigenschaften verwenden, die dieses Feld automatisch im Hintergrund erstellen und die grundlegende Logik für die Eigenschaftenprozeduren bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="921cd-122">C# allows you either to create a private field for storing the property value or use auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="921cd-123">So definieren Sie eine automatisch implementierte Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="921cd-123">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="921cd-124">Verwenden Sie den folgenden Code, wenn Sie zusätzliche Lese- und Schreibvorgänge für den Eigenschaftswert ausführen müssen, um ein Feld zum Speichern des Eigenschaftswerts zu definieren und die grundlegende Logik zum Speichern und Abrufen bereitzustellen:</span><span class="sxs-lookup"><span data-stu-id="921cd-124">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

<span data-ttu-id="921cd-125">Die meisten Eigenschaften verfügen über Methoden oder Prozeduren zum Festlegen und Abrufen des Eigenschaftswerts.</span><span class="sxs-lookup"><span data-stu-id="921cd-125">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="921cd-126">Sie können jedoch schreib- oder lesegeschützte Eigenschaften erstellen, um zu verhindern, dass die Eigenschaften gelesen oder geändert werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-126">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="921cd-127">In C# muss die `get`-Eigenschaftenmethode oder die `set`-Eigenschaftenmethode nicht angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-127">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="921cd-128">Automatisch implementierte Eigenschaften können jedoch nicht lesegeschützt sein.</span><span class="sxs-lookup"><span data-stu-id="921cd-128">However, auto-implemented properties cannot be write-only.</span></span> <span data-ttu-id="921cd-129">Schreibgeschützte automatisch implementierte Eigenschaften können in Konstruktoren der enthaltenden Klasse festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-129">Read-only auto-implemented properties can be set in constructors of the containing class.</span></span>

<span data-ttu-id="921cd-130">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="921cd-130">For more information, see:</span></span>

- [<span data-ttu-id="921cd-131">get</span><span class="sxs-lookup"><span data-stu-id="921cd-131">get</span></span>](../../language-reference/keywords/get.md)
- [<span data-ttu-id="921cd-132">set</span><span class="sxs-lookup"><span data-stu-id="921cd-132">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="methods"></a><span data-ttu-id="921cd-133">Methoden</span><span class="sxs-lookup"><span data-stu-id="921cd-133">Methods</span></span>

<span data-ttu-id="921cd-134">Eine *Methode* ist eine Aktion, die von einem Objekt ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="921cd-134">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="921cd-135">So definieren Sie eine Methode einer Klasse:</span><span class="sxs-lookup"><span data-stu-id="921cd-135">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int SampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="921cd-136">Eine Klasse kann über mehrere Implementierungen oder *Überladungen* der gleichen Methode verfügen, die sich in der Anzahl der Parameter oder Parametertypen unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="921cd-136">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="921cd-137">So überladen Sie eine Methode</span><span class="sxs-lookup"><span data-stu-id="921cd-137">To overload a method:</span></span>

```csharp
public int SampleMethod(string sampleParam) { }
public int SampleMethod(int sampleParam) { }
```

<span data-ttu-id="921cd-138">In den meisten Fällen deklarieren Sie eine Methode innerhalb einer Klassendefinition.</span><span class="sxs-lookup"><span data-stu-id="921cd-138">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="921cd-139">Auch C# unterstützt jedoch *Erweiterungsmethoden*, mit denen Sie einer vorhandenen Klasse außerhalb der eigentlichen Klassendefinition Methoden hinzuzufügen können.</span><span class="sxs-lookup"><span data-stu-id="921cd-139">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="921cd-140">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="921cd-140">For more information, see:</span></span>

- [<span data-ttu-id="921cd-141">Methoden</span><span class="sxs-lookup"><span data-stu-id="921cd-141">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="921cd-142">Erweiterungsmethoden</span><span class="sxs-lookup"><span data-stu-id="921cd-142">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="921cd-143">Konstruktoren</span><span class="sxs-lookup"><span data-stu-id="921cd-143">Constructors</span></span>

<span data-ttu-id="921cd-144">Konstruktoren sind Klassenmethoden, die automatisch ausgeführt werden, wenn ein Objekt eines bestimmten Typs erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="921cd-144">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="921cd-145">Konstruktoren initialisieren normalerweise die Datenmember des neuen Objekts.</span><span class="sxs-lookup"><span data-stu-id="921cd-145">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="921cd-146">Konstruktoren können nur einmal während der Erstellung der Klasse ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-146">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="921cd-147">Weiterhin wird der Code im Konstruktor immer vor jedem anderen Code in einer Klasse ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="921cd-147">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="921cd-148">Sie können jedoch mehrere Konstruktorüberladungen auf die gleiche Weise wie für jede andere Methode erstellen.</span><span class="sxs-lookup"><span data-stu-id="921cd-148">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="921cd-149">So definieren Sie einen Konstruktor für eine Klasse:</span><span class="sxs-lookup"><span data-stu-id="921cd-149">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="921cd-150">Weitere Informationen finden Sie unter [Konstruktoren](../classes-and-structs/constructors.md).</span><span class="sxs-lookup"><span data-stu-id="921cd-150">For more information, see [Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="finalizers"></a><span data-ttu-id="921cd-151">Finalizer</span><span class="sxs-lookup"><span data-stu-id="921cd-151">Finalizers</span></span>

<span data-ttu-id="921cd-152">Ein Finalizer wird zur Zerstörung von Klasseninstanzen verwendet.</span><span class="sxs-lookup"><span data-stu-id="921cd-152">A finalizer is used to destruct instances of classes.</span></span> <span data-ttu-id="921cd-153">In .NET Framework verwaltet die Garbage Collection die Speicherbelegung automatisch und gibt Arbeitsspeicher für die verwalteten Objekte in der Anwendung frei.</span><span class="sxs-lookup"><span data-stu-id="921cd-153">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="921cd-154">Möglicherweise sind jedoch noch Finalizer erforderlich, um alle nicht verwalteten Ressourcen zu bereinigen, die von der Anwendung erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-154">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="921cd-155">Es kann nur einen Finalizer pro Klasse geben.</span><span class="sxs-lookup"><span data-stu-id="921cd-155">There can be only one finalizer for a class.</span></span>

<span data-ttu-id="921cd-156">Weitere Informationen zu Finalizern und der Garbage Collection in .NET Framework finden Sie unter [Garbage Collection](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="921cd-156">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="921cd-157">Ereignisse</span><span class="sxs-lookup"><span data-stu-id="921cd-157">Events</span></span>

<span data-ttu-id="921cd-158">Ereignisse aktivieren eine Klasse oder ein Objekt, um Informationen über Aktionen von Interesse an andere Klassen oder Objekte zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="921cd-158">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="921cd-159">Die Klasse, die das Ereignis sendet (oder auslöst), wird als *Herausgeber* bezeichnet, und die Klassen, die das Ereignis empfangen (oder verarbeiten), werden als *Abonnenten* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="921cd-159">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="921cd-160">Weitere Informationen zu Ereignissen sowie zu ihrer Auslösung und Behandlung finden Sie unter [Ereignisse](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="921cd-160">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="921cd-161">Verwenden Sie das Schlüsselwort [event](../../language-reference/keywords/event.md), um ein Ereignis in einer Klasse zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="921cd-161">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>
- <span data-ttu-id="921cd-162">Um ein Ereignis auszulösen, rufen Sie den Ereignisdelegaten auf.</span><span class="sxs-lookup"><span data-stu-id="921cd-162">To raise an event, invoke the event delegate.</span></span>
- <span data-ttu-id="921cd-163">Verwenden Sie den `+=`-Operator, um ein Ereignis zu abonnieren, und verwenden Sie den `-=`-Operator, um das Abonnement eines Ereignisses zu kündigen.</span><span class="sxs-lookup"><span data-stu-id="921cd-163">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="921cd-164">Geschachtelte Klassen</span><span class="sxs-lookup"><span data-stu-id="921cd-164">Nested classes</span></span>

<span data-ttu-id="921cd-165">Eine Klasse, die in einer anderen Klasse definiert wird, wird als *geschachtelt* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="921cd-165">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="921cd-166">Standardmäßig ist die geschachtelte Klasse privat.</span><span class="sxs-lookup"><span data-stu-id="921cd-166">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="921cd-167">Um eine Instanz der geschachtelten Klasse zu erstellen, verwenden Sie den Namen der Containerklasse und geben einen Punkt sowie anschließend den Namen der geschachtelten Klasse ein:</span><span class="sxs-lookup"><span data-stu-id="921cd-167">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="921cd-168">Zugriffsmodifizierer und Zugriffsebenen</span><span class="sxs-lookup"><span data-stu-id="921cd-168">Access modifiers and access levels</span></span>

<span data-ttu-id="921cd-169">Alle Klassen und Klassenmember können mit *Zugriffsmodifizierern* angeben, welche Zugriffsebene sie für andere Klassen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="921cd-169">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="921cd-170">Die folgenden Zugriffsmodifizierer sind verfügbar:</span><span class="sxs-lookup"><span data-stu-id="921cd-170">The following access modifiers are available:</span></span>

| <span data-ttu-id="921cd-171">C#-Modifizierer</span><span class="sxs-lookup"><span data-stu-id="921cd-171">C# Modifier</span></span> | <span data-ttu-id="921cd-172">Definition</span><span class="sxs-lookup"><span data-stu-id="921cd-172">Definition</span></span> |
|--|--|
| [<span data-ttu-id="921cd-173">public</span><span class="sxs-lookup"><span data-stu-id="921cd-173">public</span></span>](../../language-reference/keywords/public.md) | <span data-ttu-id="921cd-174">Auf den Typ oder Member kann von jedem Code in der gleichen Assembly oder einer anderen Assembly, die darauf verweist, zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-174">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span> |
| [<span data-ttu-id="921cd-175">private</span><span class="sxs-lookup"><span data-stu-id="921cd-175">private</span></span>](../../language-reference/keywords/private.md) | <span data-ttu-id="921cd-176">Auf den Typ oder Member kann nur von Code in der gleichen Klasse zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-176">The type or member can only be accessed by code in the same class.</span></span> |
| [<span data-ttu-id="921cd-177">protected</span><span class="sxs-lookup"><span data-stu-id="921cd-177">protected</span></span>](../../language-reference/keywords/protected.md) | <span data-ttu-id="921cd-178">Auf den Typ oder Member kann nur von Code in der gleichen Klasse oder in einer abgeleiteten Klasse zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-178">The type or member can only be accessed by code in the same class or in a derived class.</span></span> |
| [<span data-ttu-id="921cd-179">internal</span><span class="sxs-lookup"><span data-stu-id="921cd-179">internal</span></span>](../../language-reference/keywords/internal.md) | <span data-ttu-id="921cd-180">Auf den Typ oder Member kann von jedem Code in der gleichen Assembly zugegriffen werden, jedoch nicht von Code in einer anderen Assembly.</span><span class="sxs-lookup"><span data-stu-id="921cd-180">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span> |
| [<span data-ttu-id="921cd-181">protected internal</span><span class="sxs-lookup"><span data-stu-id="921cd-181">protected internal</span></span>](../../language-reference/keywords/protected-internal.md) | <span data-ttu-id="921cd-182">Auf den Typ oder Member kann von jedem Code in der gleichen Assembly oder von jeder abgeleiteten Klasse in einer anderen Assembly zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-182">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span> |
| [<span data-ttu-id="921cd-183">private protected</span><span class="sxs-lookup"><span data-stu-id="921cd-183">private protected</span></span>](../../language-reference/keywords/private-protected.md) | <span data-ttu-id="921cd-184">Auf den Typ oder Member kann nur über Code in der gleichen Klasse, in einer abgeleiteten Klasse oder innerhalb der Basisklassenassembly zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-184">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span> |

<span data-ttu-id="921cd-185">Weitere Informationen finden Sie unter [Zugriffsmodifizierer](../classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="921cd-185">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="921cd-186">Instanziieren von Klassen</span><span class="sxs-lookup"><span data-stu-id="921cd-186">Instantiating classes</span></span>

<span data-ttu-id="921cd-187">Um ein Objekt zu erstellen, müssen Sie eine Klasse instanziieren oder eine Klasseninstanz erstellen.</span><span class="sxs-lookup"><span data-stu-id="921cd-187">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="921cd-188">Nachdem Sie eine Klasse instanziiert haben, können Sie den Eigenschaften und Feldern der Instanz Werte zuweisen und Klassenmethoden aufrufen.</span><span class="sxs-lookup"><span data-stu-id="921cd-188">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.SampleMethod();
```

<span data-ttu-id="921cd-189">Verwenden Sie Objektinitialisierer, um Eigenschaften im Rahmen des Klasseninstanziierungsprozesses Werte zuzuweisen:</span><span class="sxs-lookup"><span data-stu-id="921cd-189">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
var sampleObject = new SampleClass
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="921cd-190">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="921cd-190">For more information, see:</span></span>

- [<span data-ttu-id="921cd-191">new-Operator</span><span class="sxs-lookup"><span data-stu-id="921cd-191">new Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="921cd-192">Objekt- und Auflistungsinitialisierer</span><span class="sxs-lookup"><span data-stu-id="921cd-192">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a><span data-ttu-id="921cd-193">Statische Klassen und Member</span><span class="sxs-lookup"><span data-stu-id="921cd-193">Static Classes and Members</span></span>

<span data-ttu-id="921cd-194">Ein statischer Member der Klasse ist eine Eigenschaft, eine Prozedur oder ein Feld, die von allen Instanzen einer Klasse gemeinsam verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-194">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="921cd-195">So definieren Sie einen statischen Member:</span><span class="sxs-lookup"><span data-stu-id="921cd-195">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="921cd-196">Verwenden Sie den Namen der Klasse, ohne ein Objekt dieser Klasse zu erstellen, um auf den statischen Member zuzugreifen:</span><span class="sxs-lookup"><span data-stu-id="921cd-196">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="921cd-197">Statische Klassen in C# haben nur statische Member und können nicht instanziiert werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-197">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="921cd-198">Statische Member können auch nicht auf nicht statische Eigenschaften, Felder oder Methoden zugreifen.</span><span class="sxs-lookup"><span data-stu-id="921cd-198">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="921cd-199">Weitere Informationen finden Sie unter [static](../../language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="921cd-199">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="anonymous-types"></a><span data-ttu-id="921cd-200">Anonyme Typen</span><span class="sxs-lookup"><span data-stu-id="921cd-200">Anonymous types</span></span>

<span data-ttu-id="921cd-201">Mit anonymen Typen können Objekte erstellt werden, ohne eine Klassendefinition für den Datentyp zu schreiben.</span><span class="sxs-lookup"><span data-stu-id="921cd-201">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="921cd-202">Stattdessen erzeugt der Compiler eine Klasse.</span><span class="sxs-lookup"><span data-stu-id="921cd-202">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="921cd-203">Die Klasse hat keinen verwendbaren Namen und enthält die von Ihnen in der Deklaration des Objekts angegebenen Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="921cd-203">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="921cd-204">So erstellen Sie eine Instanz eines anonymen Typs</span><span class="sxs-lookup"><span data-stu-id="921cd-204">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject = new
{
    FirstProperty = "A",
    SecondProperty = "B"
};
```

<span data-ttu-id="921cd-205">Weitere Informationen finden Sie unter: [Anonyme Typen](../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="921cd-205">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="921cd-206">Vererbung</span><span class="sxs-lookup"><span data-stu-id="921cd-206">Inheritance</span></span>

<span data-ttu-id="921cd-207">Vererbung ermöglicht die Erstellung neuer Klassen, die in anderen Klassen definiertes Verhalten wieder verwenden, erweitern und ändern.</span><span class="sxs-lookup"><span data-stu-id="921cd-207">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="921cd-208">Die Klasse, deren Member vererbt werden, wird *Basisklasse* genannt, und die Klasse, die diese Member erbt, wird *abgeleitete Klasse* genannt.</span><span class="sxs-lookup"><span data-stu-id="921cd-208">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="921cd-209">Alle Klassen in C# erben jedoch implizit von der Klasse <xref:System.Object>, die die .NET-Klassenhierarchie unterstützt und einfache Dienste für alle Klassen bereitstellt.</span><span class="sxs-lookup"><span data-stu-id="921cd-209">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="921cd-210">C# unterstützt keine mehrfache Vererbung.</span><span class="sxs-lookup"><span data-stu-id="921cd-210">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="921cd-211">Sie können also nur eine Basisklasse für eine abgeleitete Klasse angeben.</span><span class="sxs-lookup"><span data-stu-id="921cd-211">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="921cd-212">So erben Sie von einer Basisklasse</span><span class="sxs-lookup"><span data-stu-id="921cd-212">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass { }
```

<span data-ttu-id="921cd-213">Standardmäßig können alle Klassen geerbt werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-213">By default all classes can be inherited.</span></span> <span data-ttu-id="921cd-214">Sie können jedoch angeben, dass eine Klasse nicht als Basisklasse verwendet werden darf, oder eine Klasse erstellen, die nur als Basisklasse verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="921cd-214">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="921cd-215">So geben Sie an, dass eine Klasse nicht als Basisklasse verwendet werden kann</span><span class="sxs-lookup"><span data-stu-id="921cd-215">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="921cd-216">So geben Sie an, dass eine Klasse nur als Basisklasse verwendet und nicht instanziiert werden kann:</span><span class="sxs-lookup"><span data-stu-id="921cd-216">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="921cd-217">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="921cd-217">For more information, see:</span></span>

- [<span data-ttu-id="921cd-218">sealed</span><span class="sxs-lookup"><span data-stu-id="921cd-218">sealed</span></span>](../../language-reference/keywords/sealed.md)
- [<span data-ttu-id="921cd-219">abstract</span><span class="sxs-lookup"><span data-stu-id="921cd-219">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a><span data-ttu-id="921cd-220">Überschreiben von Membern</span><span class="sxs-lookup"><span data-stu-id="921cd-220">Overriding Members</span></span>

<span data-ttu-id="921cd-221">Standardmäßig erbt eine abgeleitete Klasse alle Member von ihrer Basisklasse.</span><span class="sxs-lookup"><span data-stu-id="921cd-221">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="921cd-222">Wenn Sie das Verhalten des geerbten Members ändern möchten, müssen Sie diesen überschreiben.</span><span class="sxs-lookup"><span data-stu-id="921cd-222">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="921cd-223">Das heißt, Sie können eine neue Implementierung der Methode, der Eigenschaft oder des Ereignisses in der abgeleiteten Klasse definieren.</span><span class="sxs-lookup"><span data-stu-id="921cd-223">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="921cd-224">Mit folgenden Modifizierern steuern Sie das Überschreiben von Eigenschaften und Methoden:</span><span class="sxs-lookup"><span data-stu-id="921cd-224">The following modifiers are used to control how properties and methods are overridden:</span></span>

| <span data-ttu-id="921cd-225">C#-Modifizierer</span><span class="sxs-lookup"><span data-stu-id="921cd-225">C# Modifier</span></span> | <span data-ttu-id="921cd-226">Definition</span><span class="sxs-lookup"><span data-stu-id="921cd-226">Definition</span></span> |
|--|--|
| [<span data-ttu-id="921cd-227">virtual</span><span class="sxs-lookup"><span data-stu-id="921cd-227">virtual</span></span>](../../language-reference/keywords/virtual.md) | <span data-ttu-id="921cd-228">Ermöglicht das Überschreiben eines Klassenmembers in einer abgeleiteten Klasse.</span><span class="sxs-lookup"><span data-stu-id="921cd-228">Allows a class member to be overridden in a derived class.</span></span> |
| [<span data-ttu-id="921cd-229">override</span><span class="sxs-lookup"><span data-stu-id="921cd-229">override</span></span>](../../language-reference/keywords/override.md) | <span data-ttu-id="921cd-230">Überschreibt einen virtuellen (überschreibbaren) Member, der in der Basisklasse definiert wurde.</span><span class="sxs-lookup"><span data-stu-id="921cd-230">Overrides a virtual (overridable) member defined in the base class.</span></span> |
| [<span data-ttu-id="921cd-231">abstract</span><span class="sxs-lookup"><span data-stu-id="921cd-231">abstract</span></span>](../../language-reference/keywords/abstract.md) | <span data-ttu-id="921cd-232">Erfordert das Überschreiben eines Klassenmembers in der abgeleiteten Klasse.</span><span class="sxs-lookup"><span data-stu-id="921cd-232">Requires that a class member to be overridden in the derived class.</span></span> |
| [<span data-ttu-id="921cd-233">new-Modifizierer</span><span class="sxs-lookup"><span data-stu-id="921cd-233">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md) | <span data-ttu-id="921cd-234">Blendet einen von einer Basisklasse geerbten Member aus.</span><span class="sxs-lookup"><span data-stu-id="921cd-234">Hides a member inherited from a base class</span></span> |

## <a name="interfaces"></a><span data-ttu-id="921cd-235">Schnittstellen</span><span class="sxs-lookup"><span data-stu-id="921cd-235">Interfaces</span></span>

<span data-ttu-id="921cd-236">Schnittstellen definieren (wie Klassen) einen Satz von Eigenschaften, Methoden und Ereignissen.</span><span class="sxs-lookup"><span data-stu-id="921cd-236">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="921cd-237">Im Gegensatz zu Klassen jedoch bieten Schnittstellen keine Implementierung.</span><span class="sxs-lookup"><span data-stu-id="921cd-237">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="921cd-238">Sie werden durch Klassen implementiert und als von Klassen unabhängige Entitäten definiert.</span><span class="sxs-lookup"><span data-stu-id="921cd-238">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="921cd-239">Eine Schnittstelle stellt insofern einen Vertrag dar, dass eine Klasse, die eine Schnittstelle implementiert, jeden Aspekt dieser Schnittstelle gemäß seiner Definition implementieren muss.</span><span class="sxs-lookup"><span data-stu-id="921cd-239">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="921cd-240">So definieren Sie eine Schnittstelle</span><span class="sxs-lookup"><span data-stu-id="921cd-240">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void DoSomething();
}
```

<span data-ttu-id="921cd-241">So implementieren Sie eine Schnittstelle in einer Klasse</span><span class="sxs-lookup"><span data-stu-id="921cd-241">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.DoSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="921cd-242">Weitere Informationen finden Sie im Programmierleitfaden zu [Schnittstellen](../interfaces/index.md) und der Sprachreferenz zum Schlüsselwort [Schnittstelle](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="921cd-242">For more information, see the programming guide article on [Interfaces](../interfaces/index.md) and the language reference article on the [interface](../../language-reference/keywords/interface.md) keyword.</span></span>

## <a name="generics"></a><span data-ttu-id="921cd-243">Generics</span><span class="sxs-lookup"><span data-stu-id="921cd-243">Generics</span></span>

<span data-ttu-id="921cd-244">Klassen, Strukturen, Schnittstellen und Methoden in .NET Framework können *Typparameter* enthalten, die Objekttypen definieren, die sie speichern oder verwenden können.</span><span class="sxs-lookup"><span data-stu-id="921cd-244">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="921cd-245">Das einfachste Beispiel für Generics ist eine Auflistung, in der Sie den Typ von Objekten angeben können, die in einer Auflistung gespeichert werden sollen.</span><span class="sxs-lookup"><span data-stu-id="921cd-245">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="921cd-246">So definieren Sie eine generische Klasse</span><span class="sxs-lookup"><span data-stu-id="921cd-246">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="921cd-247">So erstellen Sie eine Instanz einer generischen Klasse</span><span class="sxs-lookup"><span data-stu-id="921cd-247">To create an instance of a generic class:</span></span>

```csharp
var sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="921cd-248">Weitere Informationen finden Sie unter:</span><span class="sxs-lookup"><span data-stu-id="921cd-248">For more information, see:</span></span>

- [<span data-ttu-id="921cd-249">Generics in .NET</span><span class="sxs-lookup"><span data-stu-id="921cd-249">Generics in .NET</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="921cd-250">Generics (C#-Programmierhandbuch)</span><span class="sxs-lookup"><span data-stu-id="921cd-250">Generics - C# Programming Guide</span></span>](../generics/index.md)

## <a name="delegates"></a><span data-ttu-id="921cd-251">Delegaten</span><span class="sxs-lookup"><span data-stu-id="921cd-251">Delegates</span></span>

<span data-ttu-id="921cd-252">Ein *Delegat* ist ein Typ, der eine Methodensignatur definiert. Er kann einen Verweis auf jede Methode bereitstellen, die über eine kompatible Signatur verfügt.</span><span class="sxs-lookup"><span data-stu-id="921cd-252">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="921cd-253">Sie können die Methode über den Delegaten aufrufen.</span><span class="sxs-lookup"><span data-stu-id="921cd-253">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="921cd-254">Delegaten werden verwendet, um Methoden als Argumente an anderen Methoden zu übergeben.</span><span class="sxs-lookup"><span data-stu-id="921cd-254">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="921cd-255">Ereignishandler sind nichts weiter als Methoden, die durch Delegaten aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="921cd-255">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="921cd-256">Weitere Informationen zur Ereignisbehandlung mit Delegaten finden Sie unter [Ereignisse](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="921cd-256">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="921cd-257">So erstellen Sie einen Delegaten</span><span class="sxs-lookup"><span data-stu-id="921cd-257">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="921cd-258">So erstellen Sie einen Verweis auf eine Methode, die der vom Delegaten angegebenen Signatur entspricht:</span><span class="sxs-lookup"><span data-stu-id="921cd-258">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void SampleMethod(string message)
    {
        // Add code here.
    }

    // Method that instantiates the delegate.
    void SampleDelegate()
    {
        SampleDelegate sd = sampleMethod;
        sd("Sample string");
    }
}
```

<span data-ttu-id="921cd-259">Weitere Informationen finden Sie im Programmierleitfaden zu [Delegaten](../delegates/index.md) und der Sprachreferenz zum Schlüsselwort [Delegat](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="921cd-259">For more information, see the programming guide article on [Delegates](../delegates/index.md) and the language reference article on the [delegate](../../language-reference/builtin-types/reference-types.md) keyword.</span></span>

## <a name="see-also"></a><span data-ttu-id="921cd-260">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="921cd-260">See also</span></span>

- [<span data-ttu-id="921cd-261">C#-Programmierhandbuch</span><span class="sxs-lookup"><span data-stu-id="921cd-261">C# Programming Guide</span></span>](../index.md)
