---
title: LINQ to Objects (C#)
ms.date: 07/20/2015
ms.assetid: c5c2c178-3529-4f6c-b3df-2d5267af7f22
ms.openlocfilehash: f4ca6e57ffff026cb73121ecaf443ae54b25262c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990018"
---
# <a name="linq-to-objects-c"></a><span data-ttu-id="a74af-102">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="a74af-102">LINQ to Objects (C#)</span></span>

<span data-ttu-id="a74af-103">Die Bezeichnung „LINQ to Objects“ bezieht sich auf die direkte Verwendung von LINQ-Abfragen mit einer beliebigen <xref:System.Collections.IEnumerable>- oder <xref:System.Collections.Generic.IEnumerable%601>-Auflistung, ohne einen LINQ-Zwischenanbieter oder eine API wie [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) oder [LINQ to XML](./linq-to-xml-overview.md) zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="a74af-103">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](./linq-to-xml-overview.md).</span></span> <span data-ttu-id="a74af-104">Sie können LINQ zur Abfrage beliebiger aufzählbarer Auflistungen wie <xref:System.Collections.Generic.List%601>, <xref:System.Array> oder <xref:System.Collections.Generic.Dictionary%602> verwenden.</span><span class="sxs-lookup"><span data-stu-id="a74af-104">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="a74af-105">Die Sammlung kann benutzerdefiniert sein oder von einer .NET-API zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a74af-105">The collection may be user-defined or may be returned by a .NET API.</span></span>  
  
 <span data-ttu-id="a74af-106">Im Grunde stellt LINQ to Objects einen neuen Ansatz für Auflistungen dar.</span><span class="sxs-lookup"><span data-stu-id="a74af-106">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="a74af-107">Bisher mussten Sie komplexe `foreach`-Schleifen erstellen, die angegeben haben, wie Daten aus einer Auflistung abgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="a74af-107">In the old way, you had to write complex `foreach` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="a74af-108">Im LINQ-Ansatz verfassen Sie einen deklarativen Code, in dem beschrieben wird, was Sie abrufen möchten.</span><span class="sxs-lookup"><span data-stu-id="a74af-108">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="a74af-109">Zudem bieten LINQ-Abfragen drei wesentliche Vorteile gegenüber herkömmlichen `foreach`-Schleifen:</span><span class="sxs-lookup"><span data-stu-id="a74af-109">In addition, LINQ queries offer three main advantages over traditional `foreach` loops:</span></span>  
  
- <span data-ttu-id="a74af-110">Sie sind präziser und lesbarer, insbesondere beim Filtern mehrerer Bedingungen.</span><span class="sxs-lookup"><span data-stu-id="a74af-110">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
- <span data-ttu-id="a74af-111">Sie bieten mit minimalem Anwendungscode leistungsstarke Filter-, Sortier- und Gruppierungsfunktionen.</span><span class="sxs-lookup"><span data-stu-id="a74af-111">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
- <span data-ttu-id="a74af-112">Sie können mit geringfügigen oder ohne Änderungen zu anderen Datenquellen portiert werden.</span><span class="sxs-lookup"><span data-stu-id="a74af-112">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="a74af-113">Je komplexer der für die Daten durchzuführende Vorgang, desto größer ist im Allgemeinen der Vorteil, den Sie durch die Verwendung von LINQ anstelle der herkömmlichen Iterationsverfahren haben.</span><span class="sxs-lookup"><span data-stu-id="a74af-113">In general, the more complex the operation you want to perform on the data, the more benefit you'll realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="a74af-114">Der Zweck dieses Abschnitts ist es, den LINQ-Ansatz anhand einiger Beispiele zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="a74af-114">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="a74af-115">Er ist nicht als vollständig zu betrachten.</span><span class="sxs-lookup"><span data-stu-id="a74af-115">It's not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a74af-116">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="a74af-116">In This Section</span></span>  
 [<span data-ttu-id="a74af-117">LINQ and Strings (C#) (LINQ und Zeichenfolgen (C#))</span><span class="sxs-lookup"><span data-stu-id="a74af-117">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)  
 <span data-ttu-id="a74af-118">Erläutert, wie LINQ zum Abfragen und Transformieren von Zeichenfolgen und Auflistungen von Zeichenfolgen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="a74af-118">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="a74af-119">Dieser Abschnitt umfasst auch Links zu Artikeln, die diese Prinzipien veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="a74af-119">Also includes links to articles that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="a74af-120">LINQ and Reflection (C#) (LINQ und Reflektion (C#))</span><span class="sxs-lookup"><span data-stu-id="a74af-120">LINQ and Reflection (C#)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 <span data-ttu-id="a74af-121">Verweist auf ein Beispiel, das darstellt, wie LINQ die Reflektion verwendet.</span><span class="sxs-lookup"><span data-stu-id="a74af-121">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="a74af-122">LINQ and File Directories (C#) (LINQ und Dateiverzeichnisse (C#))</span><span class="sxs-lookup"><span data-stu-id="a74af-122">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)  
 <span data-ttu-id="a74af-123">Erläutert, wie LINQ für die Interaktion mit Dateisystemen verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="a74af-123">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="a74af-124">Dieser Abschnitt umfasst auch Links zu Artikeln, die diese Konzepte veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="a74af-124">Also includes links to articles that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="a74af-125">Vorgehensweise: Abfragen von ArrayList mit LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="a74af-125">How to query an ArrayList with LINQ (C#)</span></span>](./how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="a74af-126">Veranschaulicht die Abfrage einer ArrayList in Visual Basic und C#.</span><span class="sxs-lookup"><span data-stu-id="a74af-126">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="a74af-127">Vorgehensweise: Hinzufügen von benutzerdefinierten Methoden zu LINQ-Abfragen (C#)</span><span class="sxs-lookup"><span data-stu-id="a74af-127">How to add custom methods for LINQ queries (C#)</span></span>](./how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="a74af-128">Erläutert die Erweiterung des Methodensatzes, den Sie durch Hinzufügen von Erweiterungsmethoden zur <xref:System.Collections.Generic.IEnumerable%601>-Schnittstelle verwenden können.</span><span class="sxs-lookup"><span data-stu-id="a74af-128">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="a74af-129">Language Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="a74af-129">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)  
 <span data-ttu-id="a74af-130">In diesem Artikel werden Links zu Artikeln bereitgestellt, die LINQ erläutern und Codebeispiele enthalten, die Abfragen durchführen.</span><span class="sxs-lookup"><span data-stu-id="a74af-130">Provides links to articles that explain LINQ and provide examples of code that perform queries.</span></span>
