---
title: SKIP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 75140384823588b8f6785de00b0ab3cd17314a3f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319338"
---
# <a name="skip-entity-sql"></a>SKIP (Entity SQL)

Physisches Paging kann mithilfe der SKIP-Unterklausel in der ORDER BY-Klausel durchgeführt werden. SKIP kann nicht ohne die ORDER BY-Klausel verwendet werden.

## <a name="syntax"></a>Syntax

```sql
[ SKIP n ]
```

## <a name="arguments"></a>Argumente

`n` \
Die Anzahl zu überspringender Elemente.

## <a name="remarks"></a>Hinweise

Wenn eine ORDER BY-Klausel den Ausdruck SKIP als Unterklausel enthält, werden die Ergebnisse den Sortierangaben entsprechend sortiert, und das Resultset enthält die Zeilen, die auf den SKIP-Ausdruck folgen. Mit SKIP 5 werden beispielsweise die ersten fünf Zeilen übersprungen und nur die Zeilen ab der sechsten Zeile zurückgegeben.

> [!NOTE]
> Eine [!INCLUDE[esql](../../../../../../includes/esql-md.md)] -Abfrage ist ungültig, wenn im selben Abfrageausdruck sowohl ein TOP-Modifizierer als auch eine SKIP-Unterklausel vorhanden sind. In der Abfrage sollte der TOP-Ausdruck in einen LIMIT-Ausdruck geändert werden.

> [!NOTE]
> In SQL Server 2000 werden bei Verwendung von Skip mit Order by für nicht Schlüssel Spalten möglicherweise falsche Ergebnisse zurückgegeben. Es kann vorkommen, dass mehr als die angegebene Anzahl von Zeilen übersprungen wird, wenn die Nichtschlüsselspalte Daten doppelt enthält. Dies liegt daran, wie Skip für SQL Server 2000 übersetzt wird. Im folgenden Code können beispielsweise mehr als fünf Zeilen übersprungen werden, wenn `E.NonKeyColumn` Werte doppelt enthält:
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

Die [!INCLUDE[esql](../../../../../../includes/esql-md.md)]-Abfrage in Gewusst [wie: seitenweise durch Abfrageergebnisse](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) verwendet den Order by-Operator mit Skip, um die Sortierreihenfolge für Objekte anzugeben, die in einer SELECT-Anweisung zurückgegeben werden.

## <a name="see-also"></a>Siehe auch

- [ORDER BY](order-by-entity-sql.md)
- [Gewusst wie: seitenweise durch Abfrageergebnisse](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))
- [Paging](paging-entity-sql.md)
- [TOP](top-entity-sql.md)
