---
title: 'Vorgehensweise: Analysieren von Zeichenfolgen mithilfe von „String.Split“ (C#-Anleitung)'
description: „String.Split“ gibt einen Array mit Zeichenfolgen an, die von mehreren Trennzeichen getrennt werden. So können Sie auf einfache Weise Zeichenfolgen analysieren.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: fb11ff59705188f9425beedfbbbf3c244d21f587
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121510"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Vorgehensweise: Analysieren von Zeichenfolgen mithilfe von „String.Split“ (C#-Anleitung)

Die <xref:System.String.Split%2A?displayProperty=nameWithType>-Methode erstellt ein Array mit Teilzeichenfolgen, indem die Eingabezeichenfolge von mindestens einem Trennzeichen geteilt wird. Dies stellt in der Regel die einfachste Methode dar, eine Zeichenfolge an Wortgrenzen zu teilen. Sie wird außerdem verwendet, um Zeichenfolgen nach anderen bestimmten Zeichen und Zeichenfolgen zu trennen.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Mithilfe des folgenden Codes wird ein häufig verwendeter Ausdruck in ein Array mit Zeichenfolgen für jedes Wort unterteilt.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Jede Instanz eines Trennzeichens gibt einen Wert in dem zurückgegebenen Array zurück. Aufeinander folgende Trennzeichen geben eine leere Zeichenfolge als Wert in einem zurückgegebenen Array zurück.  Dies wird im folgenden Beispiel dargestellt, in dem Leerräume als Trennlinien verwendet werden:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Dieses Verhalten vereinfacht den Vorgang für Dateien mit Formaten wie CSV (Comma Separated Values = durch Trennzeichen getrennte Werte), die Tabellendaten darstellen. Aufeinander folgende Kommas stellen eine leere Spalte dar.

Sie können einen optionalen <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType>-Parameter übergeben, um jegliche leeren Zeichenfolgen aus dem zurückgegebenen Array auszuschließen. Für kompliziertere Prozesse der zurückgegebenen Auflistung können Sie [LINQ](../programming-guide/concepts/linq/index.md) verwenden, um die Ergebnissequenz zu manipulieren.

<xref:System.String.Split%2A?displayProperty=nameWithType> kann mehrere Trennzeichen verwenden.
In diesem Beispiel werden Leerräume, Kommas, Punkte, Doppelpunkte und Tabstopps verwendet, die alle in einem Array, das diese Trennzeichen enthält, an <xref:System.String.Split%2A>übergeben werden.
Die Schleife am Ende des Codes zeigt sämtliche Wörter im zurückgegeben Array an.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Aufeinander folgende Instanzen einer beliebigen Trennlinie geben die leere Zeichenfolge im Ausgabearray zurück:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType> kann ein Array mit Zeichenfolgen aufnehmen (Zeichenfolgen, die als Trennzeichen für die Analyse der Zielzeichenfolge fungieren, statt einzelne Zeichen).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Sie können diese Beispiele ausprobieren, indem Sie sich den Code in unserem [GitHub-Repository](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings) ansehen. Alternativ dazu können Sie die Beispiele [als ZIP-Datei](../../../samples/snippets/csharp/how-to/strings.zip) herunterladen.

## <a name="see-also"></a>Weitere Informationen

- [C#-Programmierhandbuch](../programming-guide/index.md)
- [Zeichenfolgen](../programming-guide/strings/index.md)
- [Reguläre Ausdrücke von .NET](../../standard/base-types/regular-expressions.md)
