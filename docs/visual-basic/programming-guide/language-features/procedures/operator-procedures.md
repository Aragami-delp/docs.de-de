---
title: Operatorprozeduren
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: a1dd183570c8aa50efff85bdaebef90bd3b0120f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364317"
---
# <a name="operator-procedures-visual-basic"></a>Operatorprozeduren (Visual Basic)

Eine Operator Prozedur ist eine Reihe von Visual Basic-Anweisungen, die das Verhalten eines Standard Operators (z. b. `*` , `<>` oder `And` ) für eine von Ihnen definierte Klasse oder Struktur definieren. Dies wird auch als *Operator Überladung*bezeichnet.

## <a name="when-to-define-operator-procedures"></a>Definieren von Operator Prozeduren

Wenn Sie eine Klasse oder Struktur definiert haben, können Sie Variablen so deklarieren, dass Sie vom Typ dieser Klasse oder Struktur sind. Manchmal muss eine solche Variable an einem Vorgang als Teil eines Ausdrucks teilnehmen. Zu diesem Zweck muss Sie ein Operand eines Operators sein.

Visual Basic definiert Operatoren nur für die grundlegenden Datentypen. Sie können das Verhalten eines Operators definieren, wenn einer oder beide Operanden vom Typ der Klasse oder Struktur sind.

Weitere Informationen finden Sie unter [Operator Statement](../../../language-reference/statements/operator-statement.md).

## <a name="types-of-operator-procedure"></a>Typen von Operator Prozeduren

Eine Operator Prozedur kann einen der folgenden Typen aufweisen:

- Eine Definition eines unären Operators, bei dem das Argument vom Typ der Klasse oder Struktur ist.

- Eine Definition eines binären Operators, bei der mindestens eines der Argumente vom Typ der Klasse oder Struktur ist.

- Eine Definition eines Konvertierungs Operators, bei der das Argument vom Typ der Klasse oder Struktur ist.

- Eine Definition eines Konvertierungs Operators, der den Typ der Klasse oder Struktur zurückgibt.

 Konvertierungs Operatoren sind immer Unär, und Sie verwenden immer `CType` als Operator, den Sie definieren.

## <a name="declaration-syntax"></a>Deklarationssyntax

Die Syntax zum Deklarieren einer Operator Prozedur lautet wie folgt:

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

Sie verwenden das `Widening` `Narrowing` Schlüsselwort oder nur für einen Typkonvertierungs Operator. Das Operator Symbol ist immer [CType-Funktion](../../../language-reference/functions/ctype-function.md) für einen Typkonvertierungs Operator.

Sie deklarieren zwei Operanden, um einen binären Operator zu definieren, und Sie deklarieren einen Operanden, um einen unären Operator, einschließlich eines Typkonvertierungs Operators, zu definieren. Alle Operanden müssen deklariert werden `ByVal` .

Sie deklarieren jeden Operanden auf dieselbe Weise, wie Sie Parameter für [unter Prozeduren](./sub-procedures.md)deklarieren.

### <a name="data-type"></a>Datentyp

Da Sie einen Operator in einer Klasse oder Struktur definieren, die Sie definiert haben, muss mindestens einer der Operanden vom Datentyp dieser Klasse oder Struktur sein. Für einen Typkonvertierungs Operator muss entweder der Operand oder der Rückgabetyp vom Datentyp der Klasse oder Struktur sein.

Weitere Informationen finden Sie unter [Operator Statement](../../../language-reference/statements/operator-statement.md).

## <a name="calling-syntax"></a>Aufruf Syntax

Sie rufen eine Operator Prozedur implizit mithilfe des-Operator Symbols in einem Ausdruck auf. Sie stellen die Operanden auf die gleiche Weise wie für vordefinierte Operatoren bereit.

Die Syntax für einen impliziten aufrufsvorgang für eine Operator Prozedur lautet wie folgt:

`Dim testStruct As`  *structurename*

`Dim testNewStruct As`  *structurename* `= testStruct` *Operatorsymbol*      `10`

### <a name="illustration-of-declaration-and-call"></a>Abbildung der Deklaration und des Aufruf

In der folgenden Struktur wird ein ganzzahliger 128-Bit-ganzzahliger Wert als die einzelnen Teile der Reihenfolge und der unteren Reihenfolge gespeichert. Er definiert den `+` Operator, um zwei `veryLong` Werte hinzuzufügen und einen resultierenden Wert zu generieren `veryLong` .

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

Das folgende Beispiel zeigt einen typischen aufrufsoperator, der für `+` definiert ist `veryLong` .

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a>Weitere Informationen

- [Vorgehensweisen](./index.md)
- [Sub-Prozeduren](./sub-procedures.md)
- [Function-Prozeduren](./function-procedures.md)
- [Eigenschaftenprozeduren](./property-procedures.md)
- [Parameter und Argumente von Prozeduren](./procedure-parameters-and-arguments.md)
- [Operator Statement](../../../language-reference/statements/operator-statement.md)
- [Vorgehensweise: Definieren eines Operators](./how-to-define-an-operator.md)
- [Vorgehensweise: Definieren eines Konvertierungsoperators](./how-to-define-a-conversion-operator.md)
- [Vorgehensweise: Aufrufen einer Operatorprozedur](./how-to-call-an-operator-procedure.md)
- [Vorgehensweise: Verwenden einer Klasse, die Operatoren definiert](./how-to-use-a-class-that-defines-operators.md)
