---
title: 'lock-Anweisung: C#-Referenz'
description: Verwenden Sie die lock-Anweisung von C#, um den Threadzugriff auf eine freigegebene Ressource zu synchronisieren.
ms.date: 04/02/2020
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6e9a6975977588ba7692c925d7940cd2ec26671f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406689"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="d2ade-103">lock-Anweisung (C#-Referenz)</span><span class="sxs-lookup"><span data-stu-id="d2ade-103">lock statement (C# reference)</span></span>

<span data-ttu-id="d2ade-104">Die `lock`-Anweisung ruft die Sperre für gegenseitigen Ausschluss für ein bestimmtes Objekt ab, führt einen Anweisungsblock aus und hebt die Sperre anschließend auf.</span><span class="sxs-lookup"><span data-stu-id="d2ade-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="d2ade-105">Während eine Sperre aufrechterhalten wird, kann der Thread, der die Sperre aufrechterhält, die Sperre abrufen und aufheben.</span><span class="sxs-lookup"><span data-stu-id="d2ade-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="d2ade-106">Für jeden anderen Thread wird das Abrufen der Sperre blockiert, und die Sperre wartet auf die Aufhebung.</span><span class="sxs-lookup"><span data-stu-id="d2ade-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="d2ade-107">Die `lock`-Anweisung weist folgendes Format auf:</span><span class="sxs-lookup"><span data-stu-id="d2ade-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="d2ade-108">`x` entspricht einem Ausdruck eines [Verweistyps](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="d2ade-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="d2ade-109">Dieser entspricht exakt Folgendem:</span><span class="sxs-lookup"><span data-stu-id="d2ade-109">It's precisely equivalent to</span></span>

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

<span data-ttu-id="d2ade-110">Da ein [try...finally](try-finally.md)-Block in diesem Code verwendet wird, wird die Sperre aufgehoben, wenn eine Ausnahme innerhalb des Texts einer `lock`-Anweisung ausgelöst wird.</span><span class="sxs-lookup"><span data-stu-id="d2ade-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="d2ade-111">Sie können den Operator [await](../operators/await.md) nicht im Text einer `lock`-Anweisung verwenden.</span><span class="sxs-lookup"><span data-stu-id="d2ade-111">You can't use the [await operator](../operators/await.md) in the body of a `lock` statement.</span></span>

## <a name="guidelines"></a><span data-ttu-id="d2ade-112">Richtlinien</span><span class="sxs-lookup"><span data-stu-id="d2ade-112">Guidelines</span></span>

<span data-ttu-id="d2ade-113">Wenn Sie den Threadzugriff auf eine freigegebene Ressource synchronisieren, sperren Sie eine dedizierte Objektinstanz (z.B. `private readonly object balanceLock = new object();`) oder eine andere Instanz, die wahrscheinlich nicht von anderen Teilen des Codes als lock-Objekt verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d2ade-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="d2ade-114">Vermeiden Sie, die gleiche lock-Objektinstanz für verschiedene freigegebene Ressourcen zu verwenden, da dies zu einem Deadlock oder Sperrkonflikt führen kann.</span><span class="sxs-lookup"><span data-stu-id="d2ade-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="d2ade-115">Vermeiden Sie insbesondere die Verwendung der folgenden Objekte als Sperre:</span><span class="sxs-lookup"><span data-stu-id="d2ade-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="d2ade-116">`this` – kann von den Aufrufern als Sperre verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d2ade-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="d2ade-117"><xref:System.Type>-Instanzen – können vom [typeof](../operators/type-testing-and-cast.md#typeof-operator)-Operator oder der Reflektion abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="d2ade-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="d2ade-118">Zeichenfolgeninstanzen, einschließlich Zeichenfolgenliteralen – können [internalisiert](/dotnet/api/system.string.intern#remarks) sein.</span><span class="sxs-lookup"><span data-stu-id="d2ade-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

<span data-ttu-id="d2ade-119">Die Dauer von Sperren sollte so kurz wie möglich sein, um Sperrungskonflikte zu vermindern.</span><span class="sxs-lookup"><span data-stu-id="d2ade-119">Hold a lock for as short time as possible to reduce lock contention.</span></span>

## <a name="example"></a><span data-ttu-id="d2ade-120">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d2ade-120">Example</span></span>

<span data-ttu-id="d2ade-121">Im folgenden Beispiel wird eine `Account`-Klasse definiert, die den Zugriff auf das private `balance`-Feld synchronisiert, indem eine dedizierte `balanceLock`-Instanz gesperrt wird.</span><span class="sxs-lookup"><span data-stu-id="d2ade-121">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="d2ade-122">Durch Verwendung der gleichen Instanz für die Sperre wird sichergestellt, dass das `balance`-Feld nicht von zwei Threads gleichzeitig aktualisiert werden kann, die zur gleichen Zeit versuchen, die Methoden `Debit` oder `Credit` aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="d2ade-122">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](snippets/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="d2ade-123">C#-Sprachspezifikation</span><span class="sxs-lookup"><span data-stu-id="d2ade-123">C# language specification</span></span>

<span data-ttu-id="d2ade-124">Weitere Informationen finden Sie im Abschnitt [Die lock-Anweisung](~/_csharplang/spec/statements.md#the-lock-statement) der [C#-Sprachspezifikation](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d2ade-124">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d2ade-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d2ade-125">See also</span></span>

- [<span data-ttu-id="d2ade-126">C#-Referenz</span><span class="sxs-lookup"><span data-stu-id="d2ade-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d2ade-127">C#-Schlüsselwörter</span><span class="sxs-lookup"><span data-stu-id="d2ade-127">C# keywords</span></span>](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="d2ade-128">Übersicht über Synchronisierungsprimitiven</span><span class="sxs-lookup"><span data-stu-id="d2ade-128">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
