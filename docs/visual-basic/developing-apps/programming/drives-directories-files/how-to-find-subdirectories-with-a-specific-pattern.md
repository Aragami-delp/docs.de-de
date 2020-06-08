---
title: 'Gewusst wie: Suchen nach Unterverzeichnissen mit einem bestimmten Muster'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 5b57914a518b568732955e5c73bb2031824c84dd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401627"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>Gewusst wie: Suchen nach Unterverzeichnissen mit einem bestimmten Muster in Visual Basic

Die <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>-Methode gibt eine schreibgeschützte Auflistung von Zeichenfolgen zurück, die die Pfadnamen für die Unterverzeichnisse in einem Verzeichnis darstellen. Sie können den `wildCards` -Parameter verwenden, um ein bestimmtes Muster anzugeben. Wenn Sie den Inhalt der Unterverzeichnisse in Ihre Suche mit einbeziehen möchten, legen Sie den `searchType`-Parameter auf `SearchOption.SearchAllSubDirectories` fest.

Es wird eine leere Auflistung zurückgegeben, wenn keine Dateien dem angegebenen Muster entsprechen.

## <a name="to-find-subdirectories-with-a-specific-pattern"></a>Suchen nach Unterverzeichnissen mit einem bestimmten Muster

Verwenden Sie die `GetDirectories`-Methode, die den Namen und Pfad des zu durchsuchenden Verzeichnisses bereitstellt. Im folgenden Beispiel werden alle Verzeichnisse in der Verzeichnisstruktur zurückgegeben, in deren Namen sich das Wort „Logs“ befindet. Außerdem werden Sie in `ListBox1` eingefügt.

[!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]

## <a name="robust-programming"></a>Stabile Programmierung

Die folgenden Bedingungen können einen Ausnahmefehler verursachen:

- Der Pfad ist aus einem der folgenden Gründe ungültig: Er ist eine Zeichenfolge der Länge 0, er enthält nur Leerzeichen, er enthält ungültige Zeichen, oder er ist ein Gerätepfad (beginnt mit \\\\.\\) (<xref:System.ArgumentException>).

- Der Pfad ist ungültig, da er `Nothing` ist (<xref:System.ArgumentNullException>).

- Mindestens eins der angegebenen Platzhalterzeichen ist `Nothing`, eine leere Zeichenfolge oder enthält nur Leerzeichen (<xref:System.ArgumentNullException>).

- `directory` ist nicht vorhanden (<xref:System.IO.DirectoryNotFoundException>).

- `directory` verweist auf eine vorhandene Datei (<xref:System.IO.IOException>).

- Der Pfad überschreitet die im System definierte maximale Länge (<xref:System.IO.PathTooLongException>).

- Der Pfad eines Datei- oder Ordnernamens enthält einen Doppelpunkt (:) oder weist ein ungültiges Format auf (<xref:System.NotSupportedException>).

- Dem Benutzer fehlen die erforderlichen Berechtigungen zum Anzeigen des Pfades (<xref:System.Security.SecurityException>).

- Der Benutzer verfügt nicht über die erforderlichen Berechtigungen (<xref:System.UnauthorizedAccessException>).

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [Gewusst wie: Suchen nach Dateien mit einem bestimmten Muster](how-to-find-files-with-a-specific-pattern.md)
