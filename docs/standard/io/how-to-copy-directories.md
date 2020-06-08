---
title: 'Vorgehensweise: Kopieren von Verzeichnissen'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directory copying
- I/O [.NET Framework], copying directories
- subdirectory copying
- copying directories
- directories [.NET Framework], copying
ms.assetid: 5a969765-e5f8-4b4e-977e-90e2b0a1fe3c
ms.openlocfilehash: f71f428037f33fdbc692ca2f02a4c767998d684e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288575"
---
# <a name="how-to-copy-directories"></a><span data-ttu-id="15da0-102">Vorgehensweise: Kopieren von Verzeichnissen</span><span class="sxs-lookup"><span data-stu-id="15da0-102">How to: Copy directories</span></span>
<span data-ttu-id="15da0-103">In diesem Thema wird gezeigt, wie E/A-Klassen zum synchronen Kopieren der Inhalte eines Verzeichnisses an einen anderen Speicherort verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="15da0-103">This topic demonstrates how to use I/O classes to synchronously copy the contents of a directory to another location.</span></span>

<span data-ttu-id="15da0-104">Ein Beispiel für das asynchrone Kopieren von Dateien finden Sie unter [Asynchrone Datei-E/A](asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="15da0-104">For an example of asynchronous file copy, see [Asynchronous file I/O](asynchronous-file-i-o.md).</span></span>

<span data-ttu-id="15da0-105">In diesem Beispiel werden Unterverzeichnisse kopiert, indem `copySubDirs` der `DirectoryCopy`-Methode auf `true` festgelegt wird.</span><span class="sxs-lookup"><span data-stu-id="15da0-105">This example copies subdirectories by setting the `copySubDirs` of the `DirectoryCopy` method to `true`.</span></span> <span data-ttu-id="15da0-106">Die `DirectoryCopy`-Methode kopiert Unterverzeichnisse rekursiv, indem sie sich selbst so lange für jedes weitere Unterverzeichnis aufruft, bis alle kopiert wurden.</span><span class="sxs-lookup"><span data-stu-id="15da0-106">The `DirectoryCopy` method recursively copies subdirectories by calling itself on each subdirectory until there are no more to copy.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15da0-107">Beispiel</span><span class="sxs-lookup"><span data-stu-id="15da0-107">Example</span></span>  
 [!code-csharp[System.IO.Directory_Copy#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.Directory_Copy/cs/program.cs#1)]
 [!code-vb[System.IO.Directory_Copy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.Directory_Copy/vb/Program.vb#1)]  
  
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="see-also"></a><span data-ttu-id="15da0-108">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="15da0-108">See also</span></span>

- <xref:System.IO.FileInfo>
- <xref:System.IO.DirectoryInfo>
- <xref:System.IO.FileStream>
- [<span data-ttu-id="15da0-109">Datei- und Stream-E/A</span><span class="sxs-lookup"><span data-stu-id="15da0-109">File and stream I/O</span></span>](index.md)
- [<span data-ttu-id="15da0-110">Allgemeine E/A-Aufgaben</span><span class="sxs-lookup"><span data-stu-id="15da0-110">Common I/O tasks</span></span>](common-i-o-tasks.md)
- [<span data-ttu-id="15da0-111">Asynchrone Datei-E/A</span><span class="sxs-lookup"><span data-stu-id="15da0-111">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)
