---
title: Typografische und Codekonventionen
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: 0e36d9d61b0dd2701210ce614d15fd38f08f5401
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401354"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>Typografische und Codekonventionen (Visual Basic)

In Visual Basic Dokumentation werden die folgenden typografischen und Code Konventionen verwendet.  
  
## <a name="typographic-conventions"></a>Typografische Konventionen  
  
|Beispiel|BESCHREIBUNG|  
|-------------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|Sprachspezifische Schlüsselwörter und Lauf Zeit Elemente verfügen über anfängliche Großbuchstaben und werden wie in diesem Beispiel gezeigt formatiert.|  
|**Smallproject**, **buttoncollection**|Die Wörter und Ausdrücke, die Sie eingeben, werden wie in diesem Beispiel gezeigt formatiert.|  
|[Module-Anweisung](statements/module-statement.md)|Links, auf die Sie klicken können, um zu einer anderen Hilfeseite zu wechseln, werden wie in diesem Beispiel gezeigt formatiert|  
|*Object*, *VariableName*,`argumentList`|Platzhalter für Informationen, die Sie angeben, werden wie in diesem Beispiel dargestellt formatiert.|  
|[Shadows], [ *expressionlist* ]|In der-Syntax werden optionale Elemente in eckige Klammern eingeschlossen.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|Wenn Sie in der Syntax eine Auswahl zwischen zwei oder mehr Elementen treffen müssen, werden die Elemente in geschweifte Klammern eingeschlossen und durch vertikale Balken voneinander getrennt.<br /><br /> Sie müssen nur eine der Elemente auswählen.|  
|[ `Protected` &#124; `Friend` ]|Wenn Sie in der-Syntax zwischen zwei oder mehr Elementen auswählen können, werden die Elemente in eckige Klammern eingeschlossen und durch vertikale Balken voneinander getrennt.<br /><br /> Sie können eine beliebige Kombination der Elemente oder kein Element auswählen.|  
|[{ `ByVal` &#124; `ByRef` }]|Wenn Sie in der Syntax nicht mehr als ein Element auswählen, aber die Elemente auch vollständig weglassen können, werden die Elemente in eckige Klammern eingeschlossen, die von geschweiften Klammern umgeben sind und durch vertikale Balken voneinander getrennt sind.|  
|*Mitgliedsname*1, *Mitgliedsname*2, *Mitgliedsname*3|Mehrere Instanzen desselben Platzhalters unterscheiden sich durch abonniert, wie im Beispiel gezeigt.|  
|*memberName1*<br /><br /> ...<br /><br /> *Mitgliednamen*|In der-Syntax wird ein Auslassungs Zeichen (...) verwendet, um eine unbegrenzte Anzahl von Elementen der Art anzugeben, die unmittelbar vor den Auslassungs Zeichen stehen.<br /><br /> Im Code steht Ellipsen für Code, der aus Gründen der Übersichtlichkeit weggelassen wird.|  
|ESC, EINGABETASTE|Schlüsselnamen und schlüsselsequenzen auf der Tastatur werden in Großbuchstaben angezeigt.|  
|ALT+F1|Wenn zwischen den Schlüsselnamen Pluszeichen (+) angezeigt wird, müssen Sie beim Drücken der anderen einen Schlüssel gedrückt halten. Alt + F1 bedeutet beispielsweise, dass die Alt-Taste gedrückt gehalten wird, während die F1-Taste gedrückt wird.|  
  
## <a name="code-conventions"></a>Code Konventionen  
  
|Beispiel|BESCHREIBUNG|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Code Beispiele werden in einer Schriftart mit fester Größe angezeigt und wie in diesem Beispiel gezeigt formatiert.|  
|Die vorherige Anweisung legt den Wert von `sampleString` auf "Hello, World!" fest.|Code Elemente in erklärendem Text werden in einer Schriftart mit fester Größe angezeigt, wie in diesem Beispiel gezeigt.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Code Kommentare werden von einem Apostroph (') oder dem REM-Schlüsselwort eingeführt.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|Ein Leerzeichen, gefolgt von einem Unterstrich (_) am Ende einer Zeile, gibt an, dass die Anweisung in der folgenden Zeile fortgesetzt wird.|  
  
## <a name="see-also"></a>Weitere Informationen

- [Sprachreferenz zu Visual Basic](index.md)
- [Schlüsselwörter](keywords/index.md)
- [Member der Visual Basic-Laufzeitbibliothek](runtime-library-members.md)
- [Benennungskonventionen in Visual Basic](../programming-guide/program-structure/naming-conventions.md)
- [Vorgehensweise: Umbrechen und Zusammenfassen von Anweisungen in Code](../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Kommentare in Code](../programming-guide/program-structure/comments-in-code.md)
