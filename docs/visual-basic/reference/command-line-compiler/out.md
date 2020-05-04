---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 67366e13e4dceea4772d0730222413cb25b4e8b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352384"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="ef306-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef306-102">-out (Visual Basic)</span></span>
<span data-ttu-id="ef306-103">Gibt den Namen der Ausgabedatei an.</span><span class="sxs-lookup"><span data-stu-id="ef306-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef306-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef306-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="ef306-105">Argumente</span><span class="sxs-lookup"><span data-stu-id="ef306-105">Arguments</span></span>  
  
|<span data-ttu-id="ef306-106">Begriff</span><span class="sxs-lookup"><span data-stu-id="ef306-106">Term</span></span>|<span data-ttu-id="ef306-107">Definition</span><span class="sxs-lookup"><span data-stu-id="ef306-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="ef306-108">Erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ef306-108">Required.</span></span> <span data-ttu-id="ef306-109">Der Name der Ausgabedatei, die vom Compiler erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="ef306-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="ef306-110">Wenn der Dateiname ein Leerzeichen enthält, müssen Sie diesen in Anführungszeichen (" ") einschließen.</span><span class="sxs-lookup"><span data-stu-id="ef306-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef306-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ef306-111">Remarks</span></span>  
 <span data-ttu-id="ef306-112">Geben Sie den vollständigen Namen und die Erweiterung der Datei an, die erstellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ef306-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="ef306-113">Wenn Sie das nicht tun, wird der Name der EXE-Datei aus der Quellcodedatei mit der `Sub Main`-Prozedur und der Name der DLL-Datei aus der ersten Quellcodedatei abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="ef306-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="ef306-114">Wenn Sie einen Dateinamen ohne EXE- oder DLL-Erweiterung angeben, fügt der Compiler die Erweiterung automatisch hinzu. Dabei ist entscheidend, welcher Wert für die `-target`-Compileroption angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="ef306-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="ef306-115">So legen Sie -out in der Visual Studio-IDE fest</span><span class="sxs-lookup"><span data-stu-id="ef306-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="ef306-116">1.  Ein Projekt auswählen in **Projektmappen-Explorer**.</span><span class="sxs-lookup"><span data-stu-id="ef306-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="ef306-117">Klicken Sie im Menü **Projekt** auf **Eigenschaften**.</span><span class="sxs-lookup"><span data-stu-id="ef306-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="ef306-118">2.  Klicken Sie auf die Registerkarte **Anwendung** .</span><span class="sxs-lookup"><span data-stu-id="ef306-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="ef306-119">3.  Ändern Sie den Wert im Feld **Assemblyname**.</span><span class="sxs-lookup"><span data-stu-id="ef306-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ef306-120">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ef306-120">Example</span></span>  
 <span data-ttu-id="ef306-121">Der folgende Code kompiliert `T2.vb` und erstellt die Ausgabedatei `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="ef306-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef306-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ef306-122">See also</span></span>

- [<span data-ttu-id="ef306-123">Visual Basic-Befehlszeilencompiler</span><span class="sxs-lookup"><span data-stu-id="ef306-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="ef306-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ef306-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="ef306-125">Beispiele für Kompilierungsbefehlszeilen</span><span class="sxs-lookup"><span data-stu-id="ef306-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
