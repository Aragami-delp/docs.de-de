---
title: 'Vorgehensweise: Signieren einer Assembly mit einem starken Namen'
description: In diesem Artikel erfahren Sie, wie Sie eine .NET-Assembly mit einem starken Namen signieren, indem Sie die Registerkarte „Signierung“, den Assemblylinker, Assemblyattribute oder Compileroptionen verwenden.
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: d4888a12ac0494ca34eac3553a5374c3517fee38
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378619"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a><span data-ttu-id="faaf1-103">Vorgehensweise: Signieren einer Assembly mit einem starken Namen</span><span class="sxs-lookup"><span data-stu-id="faaf1-103">How to: Sign an assembly with a strong name</span></span>

> [!NOTE]
> <span data-ttu-id="faaf1-104">.NET Core unterstützt Assemblys mit starkem Namen, und alle Assemblys in der .NET Core-Bibliothek sind signiert. Für die meisten Assemblys von Drittanbietern sind jedoch keine starken Namen erforderlich.</span><span class="sxs-lookup"><span data-stu-id="faaf1-104">Although .NET Core supports strong-named assemblies, and all assemblies in the .NET Core library are signed, the majority of third-party assemblies do not need strong names.</span></span> <span data-ttu-id="faaf1-105">Weitere Informationen finden Sie unter [Strong Name Signing (Signieren von Assemblys mit starkem Namen)](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) auf GitHub.</span><span class="sxs-lookup"><span data-stu-id="faaf1-105">For more information, see [Strong Name Signing](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md) on GitHub.</span></span>

<span data-ttu-id="faaf1-106">Es gibt mehrere Möglichkeiten, eine Assembly mit einem starken Namen zu signieren:</span><span class="sxs-lookup"><span data-stu-id="faaf1-106">There are a number of ways to sign an assembly with a strong name:</span></span>  
  
- <span data-ttu-id="faaf1-107">Mithilfe der Registerkarte **Signierung** im Dialogfeld **Eigenschaften** eines Projekts in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="faaf1-107">By using the **Signing** tab in a project's **Properties** dialog box in Visual Studio.</span></span> <span data-ttu-id="faaf1-108">Dies ist die einfachste und bequemste Methode, eine Assembly mit einem starken Namen zu signieren.</span><span class="sxs-lookup"><span data-stu-id="faaf1-108">This is the easiest and most convenient way to sign an assembly with a strong name.</span></span>  
  
- <span data-ttu-id="faaf1-109">Mit dem [Assemblylinker-Tool (Al.exe)](../../framework/tools/al-exe-assembly-linker.md), um ein .NET Framework-Codemodul (eine *.netmodule*-Datei) mit einer Schlüsseldatei zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="faaf1-109">By using the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) to link a .NET Framework code module (a *.netmodule* file) with a key file.</span></span>  
  
- <span data-ttu-id="faaf1-110">Mithilfe von Assemblyattributen, um die Informationen zum starken Namen in den Code einzufügen.</span><span class="sxs-lookup"><span data-stu-id="faaf1-110">By using assembly attributes to insert the strong name information into your code.</span></span> <span data-ttu-id="faaf1-111">Abhängig von dem Ort, an dem sich die zu verwendende Schlüsseldatei befindet, können Sie entweder das <xref:System.Reflection.AssemblyKeyFileAttribute> -Attribut oder das <xref:System.Reflection.AssemblyKeyNameAttribute> -Attribut verwenden.</span><span class="sxs-lookup"><span data-stu-id="faaf1-111">You can use either the <xref:System.Reflection.AssemblyKeyFileAttribute> or the <xref:System.Reflection.AssemblyKeyNameAttribute> attribute, depending on where the key file to be used is located.</span></span>  
  
- <span data-ttu-id="faaf1-112">Mithilfe von Compileroptionen.</span><span class="sxs-lookup"><span data-stu-id="faaf1-112">By using compiler options.</span></span>  
  
 <span data-ttu-id="faaf1-113">Sie benötigen ein kryptografisches Schlüsselpaar, um eine Assembly mit einem starken Namen zu signieren.</span><span class="sxs-lookup"><span data-stu-id="faaf1-113">You must have a cryptographic key pair to sign an assembly with a strong name.</span></span> <span data-ttu-id="faaf1-114">Weitere Informationen zum Erstellen eines Schlüsselpaars finden Sie unter [Vorgehensweise: Erstellen eines öffentlichen/privaten Schlüsselpaars](create-public-private-key-pair.md).</span><span class="sxs-lookup"><span data-stu-id="faaf1-114">For more information about creating a key pair, see [How to: Create a public-private key pair](create-public-private-key-pair.md).</span></span>  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a><span data-ttu-id="faaf1-115">Erstellen und Signieren einer Assembly mit einem starken Namen mit Visual Studio</span><span class="sxs-lookup"><span data-stu-id="faaf1-115">Create and sign an assembly with a strong name by using Visual Studio</span></span>  
  
1. <span data-ttu-id="faaf1-116">Öffnen Sie im **Projektmappen-Explorer**das Kontextmenü für das Projekt, und wählen Sie **Eigenschaften**aus.</span><span class="sxs-lookup"><span data-stu-id="faaf1-116">In **Solution Explorer**, open the shortcut menu for the project, and then choose **Properties**.</span></span>  
  
2. <span data-ttu-id="faaf1-117">Wählen Sie die Registerkarte **Signierung** aus.</span><span class="sxs-lookup"><span data-stu-id="faaf1-117">Choose the **Signing** tab.</span></span>  
  
3. <span data-ttu-id="faaf1-118">Wählen Sie das Feld **Assembly signieren** aus.</span><span class="sxs-lookup"><span data-stu-id="faaf1-118">Select the **Sign the assembly** box.</span></span>  
  
4. <span data-ttu-id="faaf1-119">Klicken Sie im Feld **Schlüsseldatei mit starkem Namen auswählen** auf **Durchsuchen**, und navigieren Sie dann zur Schlüsseldatei.</span><span class="sxs-lookup"><span data-stu-id="faaf1-119">In the **Choose a strong name key file** box, choose **Browse**, and then navigate to the key file.</span></span> <span data-ttu-id="faaf1-120">Klicken Sie zum Erstellen einer neuen Schlüsseldatei auf **Neu**, und geben Sie ihren Namen in das Dialogfeld **Schlüssel für einen starken Namen erstellen** ein.</span><span class="sxs-lookup"><span data-stu-id="faaf1-120">To create a new key file, choose **New** and enter its name in the **Create Strong Name Key** dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="faaf1-121">Wählen Sie eine Datei mit öffentlichem Schlüssel aus, um [die Signierung einer Assembly zu verzögern](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="faaf1-121">In order to [delay sign an assembly](delay-sign.md), choose a public key file.</span></span>  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a><span data-ttu-id="faaf1-122">Erstellen und Signieren einer Assembly mit einem starken Name mithilfe des Assemblylinkers</span><span class="sxs-lookup"><span data-stu-id="faaf1-122">Create and sign an assembly with a strong name by using the Assembly Linker</span></span>  
  
<span data-ttu-id="faaf1-123">Geben Sie in der [Developer-Eingabeaufforderung für Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md) den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="faaf1-123">At the [Developer Command Prompt for Visual Studio](../../framework/tools/developer-command-prompt-for-vs.md), enter the following command:</span></span>  

<span data-ttu-id="faaf1-124">**al** **/out:** \<*assemblyName*>  *\<moduleName>* **/keyfile:** \<*keyfileName*></span><span class="sxs-lookup"><span data-stu-id="faaf1-124">**al** **/out:**\<*assemblyName*> *\<moduleName>* **/keyfile:**\<*keyfileName*></span></span>  

<span data-ttu-id="faaf1-125">Ort:</span><span class="sxs-lookup"><span data-stu-id="faaf1-125">Where:</span></span>  

- <span data-ttu-id="faaf1-126">*assemblyName* ist der Name der stark signierten Assembly (eine *DLL*- oder *EXE*-Datei), die der Assemblylinker ausgibt.</span><span class="sxs-lookup"><span data-stu-id="faaf1-126">*assemblyName* is the name of the strongly signed assembly (a *.dll* or *.exe* file) that Assembly Linker will emit.</span></span>  
  
- <span data-ttu-id="faaf1-127">*moduleName* ist der Name eines .NET Framework-Codemoduls (eine *NETMODULE*-Datei), das mindestens einen Typ enthält.</span><span class="sxs-lookup"><span data-stu-id="faaf1-127">*moduleName* is the name of a .NET Framework code module (a *.netmodule* file) that includes one or more types.</span></span> <span data-ttu-id="faaf1-128">Sie können eine *NETMODULE*-Datei erstellen, indem Sie Ihren Code mit der `/target:module`-Option in C# oder Visual Basic kompilieren.</span><span class="sxs-lookup"><span data-stu-id="faaf1-128">You can create a *.netmodule* file by compiling your code with the `/target:module` switch in C# or Visual Basic.</span></span>
  
- <span data-ttu-id="faaf1-129">*keyfileName* ist der Name des Containers oder der Datei, der bzw. die das Schlüsselpaar enthält.</span><span class="sxs-lookup"><span data-stu-id="faaf1-129">*keyfileName* is the name of the container or file that contains the key pair.</span></span> <span data-ttu-id="faaf1-130">Der Assemblylinker interpretiert einen relativen Pfad im Zusammenhang mit dem aktuellen Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="faaf1-130">Assembly Linker interprets a relative path in relation to the current directory.</span></span>  

<span data-ttu-id="faaf1-131">Im folgenden Beispiel wird die Assembly *MyAssembly.dll* unter Verwendung der Schlüsseldatei *sgKey.snk* mit einem starken Namen signiert.</span><span class="sxs-lookup"><span data-stu-id="faaf1-131">The following example signs the assembly *MyAssembly.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
<span data-ttu-id="faaf1-132">Weitere Informationen über die Verwendung dieses Tools finden Sie unter [Assemblylinker](../../framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="faaf1-132">For more information about this tool, see [Assembly Linker](../../framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a><span data-ttu-id="faaf1-133">Signieren einer Assembly mit einem starken Namen mithilfe von Attributen</span><span class="sxs-lookup"><span data-stu-id="faaf1-133">Sign an assembly with a strong name by using attributes</span></span>  
  
1. <span data-ttu-id="faaf1-134">Fügen Sie in Ihrer Codemoduldatei das <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> -Attribut oder das <xref:System.Reflection.AssemblyKeyNameAttribute> -Attribut hinzu, und geben Sie den Namen der Datei oder des Containers an, die bzw. der das zum Signieren der Assembly mit einem starken Namen zu verwendende Schlüsselpaar enthält.</span><span class="sxs-lookup"><span data-stu-id="faaf1-134">Add the <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute to your source code file, and specify the name of the file or container that contains the key pair to use when signing the assembly with a strong name.</span></span>  

2. <span data-ttu-id="faaf1-135">Kompilieren Sie die Quellcodedatei normal.</span><span class="sxs-lookup"><span data-stu-id="faaf1-135">Compile the source code file normally.</span></span>  

   > [!NOTE]
   > <span data-ttu-id="faaf1-136">Die C#- und Visual Basic-Compiler geben Compilerwarnungen aus (CS1699 bzw. BC41008), wenn das <xref:System.Reflection.AssemblyKeyFileAttribute> -Attribut oder das <xref:System.Reflection.AssemblyKeyNameAttribute> -Attribut im Quellcode auftreten.</span><span class="sxs-lookup"><span data-stu-id="faaf1-136">The C# and Visual Basic compilers issue compiler warnings (CS1699 and BC41008, respectively) when they encounter the <xref:System.Reflection.AssemblyKeyFileAttribute> or <xref:System.Reflection.AssemblyKeyNameAttribute> attribute in source code.</span></span> <span data-ttu-id="faaf1-137">Sie können die Warnungen ignorieren.</span><span class="sxs-lookup"><span data-stu-id="faaf1-137">You can ignore the warnings.</span></span>  

<span data-ttu-id="faaf1-138">Im folgenden Beispiel wird das <xref:System.Reflection.AssemblyKeyFileAttribute>-Attribut mit der Schlüsseldatei *keyfile.snk* verwendet, die sich in dem Verzeichnis befindet, in dem die Assembly kompiliert wird.</span><span class="sxs-lookup"><span data-stu-id="faaf1-138">The following example uses the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute with a key file called *keyfile.snk*, which is located in the directory where the assembly is compiled.</span></span>  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

<span data-ttu-id="faaf1-139">Sie können auch während des Kompiliervorgangs der Quelldatei eine Assembly verzögert signieren.</span><span class="sxs-lookup"><span data-stu-id="faaf1-139">You can also delay sign an assembly when compiling your source file.</span></span> <span data-ttu-id="faaf1-140">Weitere Informationen finden Sie unter [Verzögertes Signieren einer Assembly](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="faaf1-140">For more information, see [Delay-sign an assembly](delay-sign.md).</span></span>  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a><span data-ttu-id="faaf1-141">Signieren einer Assembly mit einem starken Namen mithilfe des Compilers</span><span class="sxs-lookup"><span data-stu-id="faaf1-141">Sign an assembly with a strong name by using the compiler</span></span>  

<span data-ttu-id="faaf1-142">Kompilieren Sie Ihre Quellcodedateien mit der Compileroption `/keyfile` oder `/delaysign` in C# und Visual Basic bzw. mit der Linkeroption `/KEYFILE` oder `/DELAYSIGN` in C++.</span><span class="sxs-lookup"><span data-stu-id="faaf1-142">Compile your source code file or files with the `/keyfile` or `/delaysign` compiler option in C# and Visual Basic, or the `/KEYFILE` or `/DELAYSIGN` linker option in C++.</span></span> <span data-ttu-id="faaf1-143">Fügen Sie nach dem Optionsnamen einen Doppelpunkt und den Namen der Schlüsseldatei hinzu.</span><span class="sxs-lookup"><span data-stu-id="faaf1-143">After the option name, add a colon and the name of the key file.</span></span> <span data-ttu-id="faaf1-144">Wenn Sie einen Befehlszeilencompiler verwenden, können Sie die Schlüsseldatei in das Verzeichnis kopieren, das die Quellcodedateien enthält.</span><span class="sxs-lookup"><span data-stu-id="faaf1-144">When using command-line compilers, you can copy the key file to the directory that contains your source code files.</span></span>  

<span data-ttu-id="faaf1-145">Weitere Informationen zum verzögerten Signieren finden Sie unter [Verzögertes Signieren einer Assembly](delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="faaf1-145">For information on delay signing, see [Delay-sign an assembly](delay-sign.md).</span></span>  

<span data-ttu-id="faaf1-146">Im folgenden Beispiel wird der C#-Compiler verwendet und die Assembly *UtilityLibrary.dll* mithilfe der Schlüsseldatei *sgKey.snk* mit einem starken Namen signiert.</span><span class="sxs-lookup"><span data-stu-id="faaf1-146">The following example uses the C# compiler and signs the assembly *UtilityLibrary.dll* with a strong name by using the key file *sgKey.snk*.</span></span>  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a><span data-ttu-id="faaf1-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="faaf1-147">See also</span></span>

- [<span data-ttu-id="faaf1-148">Erstellen und Verwenden von Assemblys mit starkem Namen</span><span class="sxs-lookup"><span data-stu-id="faaf1-148">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="faaf1-149">How to: Erstellen eines öffentlichen/privaten Schlüsselpaars</span><span class="sxs-lookup"><span data-stu-id="faaf1-149">How to: Create a public-private key pair</span></span>](create-public-private-key-pair.md)
- [<span data-ttu-id="faaf1-150">Al.exe (Assembly Linker-Tool)</span><span class="sxs-lookup"><span data-stu-id="faaf1-150">Al.exe (Assembly Linker)</span></span>](../../framework/tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="faaf1-151">Verzögertes Signieren einer Assembly</span><span class="sxs-lookup"><span data-stu-id="faaf1-151">Delay-sign an assembly</span></span>](delay-sign.md)
- [<span data-ttu-id="faaf1-152">Verwalten der Signierung von Assemblys und Manifesten</span><span class="sxs-lookup"><span data-stu-id="faaf1-152">Manage assembly and manifest signing</span></span>](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [<span data-ttu-id="faaf1-153">Seite „Signierung“, Projekt-Designer</span><span class="sxs-lookup"><span data-stu-id="faaf1-153">Signing page, Project Designer</span></span>](/visualstudio/ide/reference/signing-page-project-designer)
