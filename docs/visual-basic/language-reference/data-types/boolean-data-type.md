---
title: Boolean-Datentyp
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: 851c524a83c5f24b77a151634a96798249c5905e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374420"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="1d34e-102">Boolean-Datentyp (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d34e-102">Boolean Data Type (Visual Basic)</span></span>

<span data-ttu-id="1d34e-103">Enthält Werte, die nur oder aufweisen können `True` `False` .</span><span class="sxs-lookup"><span data-stu-id="1d34e-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="1d34e-104">Die Schlüsselwörter `True` und `False` entsprechen den beiden Zuständen der `Boolean` Variablen.</span><span class="sxs-lookup"><span data-stu-id="1d34e-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d34e-105">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="1d34e-105">Remarks</span></span>  

 <span data-ttu-id="1d34e-106">Verwenden Sie den [booleschen Datentyp (Visual Basic)](boolean-data-type.md) , um zwei Zustands Werte wie "true", "false", "Ja/Nein" oder "ein/aus" zu enthalten.</span><span class="sxs-lookup"><span data-stu-id="1d34e-106">Use the [Boolean Data Type (Visual Basic)](boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="1d34e-107">Der Standardwert von `Boolean` ist `False`.</span><span class="sxs-lookup"><span data-stu-id="1d34e-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="1d34e-108">`Boolean`Werte werden nicht als Zahlen gespeichert, und die gespeicherten Werte sind nicht als äquivalent zu zahlen vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="1d34e-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="1d34e-109">Sie sollten niemals Code schreiben, der auf äquivalenten numerischen Werten für `True` und basiert `False` .</span><span class="sxs-lookup"><span data-stu-id="1d34e-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="1d34e-110">Wenn möglich, sollten Sie die Verwendung von `Boolean` Variablen auf die logischen Werte beschränken, für die Sie entworfen wurden.</span><span class="sxs-lookup"><span data-stu-id="1d34e-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="1d34e-111">Typkonvertierungen</span><span class="sxs-lookup"><span data-stu-id="1d34e-111">Type Conversions</span></span>  

 <span data-ttu-id="1d34e-112">Wenn Visual Basic numerische Datentyp Werte in konvertiert `Boolean` , wird 0 zu, `False` und alle anderen Werte werden `True` .</span><span class="sxs-lookup"><span data-stu-id="1d34e-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="1d34e-113">Wenn Visual Basic `Boolean` Werte in numerische Typen konvertiert, `False` wird 0 und `True` wird zu-1.</span><span class="sxs-lookup"><span data-stu-id="1d34e-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="1d34e-114">Wenn Sie zwischen `Boolean` Werten und numerischen Datentypen konvertieren, beachten Sie, dass die .NET Framework-Konvertierungs Methoden nicht immer die gleichen Ergebnisse wie die Visual Basic Konvertierungs Schlüsselwörter erzielen.</span><span class="sxs-lookup"><span data-stu-id="1d34e-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="1d34e-115">Dies liegt daran, dass die Visual Basic Konvertierung das Verhalten beibehält, das mit früheren Versionen kompatibel ist</span><span class="sxs-lookup"><span data-stu-id="1d34e-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="1d34e-116">Weitere Informationen finden Sie in der Problembehandlung bei [Datentypen](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)unter "boolescher Typ wird nicht in numerischen Typ konvertiert".</span><span class="sxs-lookup"><span data-stu-id="1d34e-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="1d34e-117">Programmiertipps</span><span class="sxs-lookup"><span data-stu-id="1d34e-117">Programming Tips</span></span>  
  
- <span data-ttu-id="1d34e-118">**Negative Zahlen.**</span><span class="sxs-lookup"><span data-stu-id="1d34e-118">**Negative Numbers.**</span></span> <span data-ttu-id="1d34e-119">`Boolean`ist kein numerischer Typ und kann keinen negativen Wert darstellen.</span><span class="sxs-lookup"><span data-stu-id="1d34e-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="1d34e-120">In jedem Fall sollten Sie nicht verwenden `Boolean` , um numerische Werte zu speichern.</span><span class="sxs-lookup"><span data-stu-id="1d34e-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
- <span data-ttu-id="1d34e-121">**Geben Sie Zeichen ein.**</span><span class="sxs-lookup"><span data-stu-id="1d34e-121">**Type Characters.**</span></span> <span data-ttu-id="1d34e-122">`Boolean`weist kein Literaltyp Zeichen oder Bezeichnertyp Zeichen auf.</span><span class="sxs-lookup"><span data-stu-id="1d34e-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="1d34e-123">**Framework-Typ.**</span><span class="sxs-lookup"><span data-stu-id="1d34e-123">**Framework Type.**</span></span> <span data-ttu-id="1d34e-124">Der entsprechende Typ in .NET Framework ist die <xref:System.Boolean?displayProperty=nameWithType>-Struktur.</span><span class="sxs-lookup"><span data-stu-id="1d34e-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d34e-125">Beispiel</span><span class="sxs-lookup"><span data-stu-id="1d34e-125">Example</span></span>  

 <span data-ttu-id="1d34e-126">Im folgenden Beispiel `runningVB` ist eine `Boolean` Variable, in der eine einfache Ja/Nein-Einstellung gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="1d34e-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d34e-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1d34e-127">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="1d34e-128">Datentypen</span><span class="sxs-lookup"><span data-stu-id="1d34e-128">Data Types</span></span>](index.md)
- [<span data-ttu-id="1d34e-129">Type Conversion Functions</span><span class="sxs-lookup"><span data-stu-id="1d34e-129">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="1d34e-130">Konvertierung: Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="1d34e-130">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="1d34e-131">Effiziente Verwendung von Datentypen</span><span class="sxs-lookup"><span data-stu-id="1d34e-131">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="1d34e-132">Problembehandlung bei Datentypen</span><span class="sxs-lookup"><span data-stu-id="1d34e-132">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="1d34e-133">CType Function</span><span class="sxs-lookup"><span data-stu-id="1d34e-133">CType Function</span></span>](../functions/ctype-function.md)
