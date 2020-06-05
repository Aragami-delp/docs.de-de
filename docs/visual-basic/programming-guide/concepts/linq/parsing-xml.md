---
title: Parsen von XML
ms.date: 07/20/2015
ms.assetid: 5bcbd7e2-d9f1-4c8f-80d6-39915fe17bd1
ms.openlocfilehash: 3517a0925e886dcd3d2d7860be606c4e44127cd6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406858"
---
# <a name="parsing-xml-visual-basic"></a><span data-ttu-id="b8778-102">XML-Datei (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8778-102">Parsing XML (Visual Basic)</span></span>
<span data-ttu-id="b8778-103">In den Themen in diesem Abschnitt wird das Analysieren von XML-Dokumenten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="b8778-103">The topics in this section describe how to parse XML documents.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8778-104">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="b8778-104">In This Section</span></span>  
  
|<span data-ttu-id="b8778-105">Thema</span><span class="sxs-lookup"><span data-stu-id="b8778-105">Topic</span></span>|<span data-ttu-id="b8778-106">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="b8778-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b8778-107">Vorgehensweise: Analysieren einer Zeichenfolge (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8778-107">How to: Parse a String (Visual Basic)</span></span>](how-to-parse-a-string.md)|<span data-ttu-id="b8778-108">Zeigt, wie eine Zeichenfolge zum Erstellen einer XML-Struktur analysiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="b8778-108">Shows how to parse a string to create an XML tree.</span></span>|  
|[<span data-ttu-id="b8778-109">Gewusst wie: Laden von XML aus einer Datei (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8778-109">How to: Load XML from a File (Visual Basic)</span></span>](how-to-load-xml-from-a-file.md)|<span data-ttu-id="b8778-110">Zeigt, wie mit der <xref:System.Xml.Linq.XElement.Load%2A>-Methode XML-Code aus einem URI geladen werden kann.</span><span class="sxs-lookup"><span data-stu-id="b8778-110">Shows how to load XML from a URI using the <xref:System.Xml.Linq.XElement.Load%2A> method.</span></span>|  
|[<span data-ttu-id="b8778-111">Beibehalten von Leerzeichen beim Laden oder Parsen von XML</span><span class="sxs-lookup"><span data-stu-id="b8778-111">Preserving White Space while Loading or Parsing XML</span></span>](preserving-white-space-while-loading-or-parsing-xml.md)|<span data-ttu-id="b8778-112">Beschreibt, wie das Leerraumverhalten von [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] beim Laden von XML-Strukturen gesteuert werden kann.</span><span class="sxs-lookup"><span data-stu-id="b8778-112">Describes how to control the white space behavior of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] while loading XML trees.</span></span>|  
|[<span data-ttu-id="b8778-113">Gewusst wie: Auffangen von Parsing-Fehlern (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8778-113">How to: Catch Parsing Errors (Visual Basic)</span></span>](how-to-catch-parsing-errors.md)|<span data-ttu-id="b8778-114">Zeigt, wie nicht wohlgeformtes oder ungültiges XML erkannt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b8778-114">Shows how to detect badly formed or invalid XML.</span></span>|  
|[<span data-ttu-id="b8778-115">Vorgehensweise: Erstellen einer Struktur aus einem XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8778-115">How to: Create a Tree from an XmlReader (Visual Basic)</span></span>](how-to-create-a-tree-from-an-xmlreader.md)|<span data-ttu-id="b8778-116">Zeigt, wie direkt aus einem <xref:System.Xml.XmlReader> eine XML-Struktur erstellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b8778-116">Shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span>|  
|[<span data-ttu-id="b8778-117">Gewusst wie: Streamen von XML-Fragmenten aus einem XmlReader-Objekt (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8778-117">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>](how-to-stream-xml-fragments-from-an-xmlreader.md)|<span data-ttu-id="b8778-118">Zeigt, wie XML-Fragmente mit einem <xref:System.Xml.XmlReader> gestreamt werden können.</span><span class="sxs-lookup"><span data-stu-id="b8778-118">Shows how to stream XML fragments by using an <xref:System.Xml.XmlReader>.</span></span><br /><br /> <span data-ttu-id="b8778-119">Wenn Sie willkürlich große XML-Dateien verarbeiten müssen, kann u. U. nicht die gesamte XML-Struktur in den Arbeitsspeicher geladen werden.</span><span class="sxs-lookup"><span data-stu-id="b8778-119">When you have to process arbitrarily large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="b8778-120">Stattdessen können Sie XML-Fragmente streamen.</span><span class="sxs-lookup"><span data-stu-id="b8778-120">Instead, you can stream XML fragments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8778-121">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b8778-121">See also</span></span>

- [<span data-ttu-id="b8778-122">Erstellen von XML-Strukturen (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8778-122">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
