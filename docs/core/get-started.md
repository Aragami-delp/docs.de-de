---
title: Erste Schritte mit .NET Core
description: Lernen Sie verschiedene Ressourcen kennen, um zu erfahren, wie Sie .NET Core-Anwendungen unter Windows, Linux und macOS erstellen können.
author: adegeo
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ddbee0764897b511cac0c4142354ba995d94a2b6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416061"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="57fbb-103">Erste Schritte mit .NET Core</span><span class="sxs-lookup"><span data-stu-id="57fbb-103">Get started with .NET Core</span></span>

<span data-ttu-id="57fbb-104">Dieser Artikel enthält Informationen zu den ersten Schritten mit .NET Core.</span><span class="sxs-lookup"><span data-stu-id="57fbb-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="57fbb-105">.NET Core kann unter Windows, Linux und macOS installiert werden.</span><span class="sxs-lookup"><span data-stu-id="57fbb-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="57fbb-106">Außerdem können Sie in Ihrem bevorzugten Text-Editor programmieren und plattformübergreifende Bibliotheken und Anwendungen erstellen.</span><span class="sxs-lookup"><span data-stu-id="57fbb-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="57fbb-107">Wenn Sie nicht sicher sind, was .NET Core ist oder in welcher Beziehung es zu anderen .NET-Technologien steht, sollten Sie mit [What is .NET (Was ist .NET)](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) beginnen.</span><span class="sxs-lookup"><span data-stu-id="57fbb-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="57fbb-108">Einfach ausgedrückt, ist .NET Core eine plattformübergreifende Open-Source-Implementierung von .NET.</span><span class="sxs-lookup"><span data-stu-id="57fbb-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="57fbb-109">Erstellen einer Anwendung</span><span class="sxs-lookup"><span data-stu-id="57fbb-109">Create an application</span></span>

<span data-ttu-id="57fbb-110">Laden Sie das [.NET Core SDK](https://dotnet.microsoft.com/download) auf Ihrem Computer herunter, und installieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="57fbb-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="57fbb-111">Als Nächstes öffnen Sie ein Terminal, z.B. **PowerShell**, die **Eingabeaufforderung** oder die **Bash**.</span><span class="sxs-lookup"><span data-stu-id="57fbb-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="57fbb-112">Geben Sie die folgenden `dotnet`-Befehle ein, um eine C#-Anwendung zu erstellen und zu veröffentlichen:</span><span class="sxs-lookup"><span data-stu-id="57fbb-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="57fbb-113">Die folgende Ausgabe wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="57fbb-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="57fbb-114">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="57fbb-114">Congratulations!</span></span> <span data-ttu-id="57fbb-115">Sie haben eine einfache .NET Core-Anwendung erstellt.</span><span class="sxs-lookup"><span data-stu-id="57fbb-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="57fbb-116">Sie können auch [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (nur Windows) oder [Visual Studio für Mac](./tutorials/using-on-mac-vs.md) (nur macOS) verwenden, um eine .NET Core-Anwendung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="57fbb-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](./tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="57fbb-117">Tutorials</span><span class="sxs-lookup"><span data-stu-id="57fbb-117">Tutorials</span></span>

<span data-ttu-id="57fbb-118">Steigen Sie in die Entwicklung von .NET Core-Anwendungen ein, indem Sie diese schrittweisen Tutorials durcharbeiten:</span><span class="sxs-lookup"><span data-stu-id="57fbb-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="57fbb-119">Windows</span><span class="sxs-lookup"><span data-stu-id="57fbb-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="57fbb-120">Erstellen Ihrer ersten .NET Core-Konsolenanwendung in Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="57fbb-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="57fbb-121">Erstellen einer Klassenbibliothek mit .NET Standard in Visual Studio</span><span class="sxs-lookup"><span data-stu-id="57fbb-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="57fbb-122">Erste Schritte mit .NET Core unter Verwendung der .NET Core-CLI</span><span class="sxs-lookup"><span data-stu-id="57fbb-122">Get started with .NET Core using the .NET Core CLI</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="57fbb-123">![Symbol für Filmkamera für das Video](./media/video-icon.png "Video ansehen")</span><span class="sxs-lookup"><span data-stu-id="57fbb-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="57fbb-124">Sehen Sie sich das Video [Vorgehensweise: Installieren und Verwenden von Visual Studio Code und .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) auf Channel 9 an.</span><span class="sxs-lookup"><span data-stu-id="57fbb-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="57fbb-125">![Symbol für Filmkamera für das Video](./media/video-icon.png "Video ansehen")</span><span class="sxs-lookup"><span data-stu-id="57fbb-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="57fbb-126">Sehen Sie sich das Video [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) auf YouTube an.</span><span class="sxs-lookup"><span data-stu-id="57fbb-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="57fbb-127">Eine Liste der unterstützten Windows-Versionen finden Sie im Artikel [.NET Core-Abhängigkeiten und -Anforderungen](install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="57fbb-127">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linux"></a>[<span data-ttu-id="57fbb-128">Linux</span><span class="sxs-lookup"><span data-stu-id="57fbb-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="57fbb-129">Steigen Sie in die Entwicklung von .NET Core-Anwendungen ein, indem Sie diese schrittweisen Tutorials durcharbeiten:</span><span class="sxs-lookup"><span data-stu-id="57fbb-129">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="57fbb-130">Erste Schritte mit .NET Core unter Verwendung der Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="57fbb-130">Get started with .NET Core using the command line</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="57fbb-131">![Symbol für Filmkamera für das Video](./media/video-icon.png "Video ansehen")</span><span class="sxs-lookup"><span data-stu-id="57fbb-131">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="57fbb-132">Sehen Sie sich ein Video zu den [ersten Schritte mit Visual Studio Code mit C# und .NET Core unter Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu) an.</span><span class="sxs-lookup"><span data-stu-id="57fbb-132">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="57fbb-133">Eine Liste der unterstützten Linux-Distributionen und -Versionen finden Sie im Artikel [.NET Core-Abhängigkeiten und -Anforderungen](install/dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="57fbb-133">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macos"></a>[<span data-ttu-id="57fbb-134">macOS</span><span class="sxs-lookup"><span data-stu-id="57fbb-134">macOS</span></span>](#tab/macos)

<span data-ttu-id="57fbb-135">Steigen Sie in die Entwicklung von .NET Core-Anwendungen ein, indem Sie diese schrittweisen Tutorials durcharbeiten:</span><span class="sxs-lookup"><span data-stu-id="57fbb-135">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="57fbb-136">Erste Schritte mit .NET Core unter macOS mithilfe von Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="57fbb-136">Get started with .NET Core on macOS using Visual Studio Code</span></span>](./tutorials/using-on-macos.md)
- [<span data-ttu-id="57fbb-137">Erste Schritte mit .NET Core unter Verwendung der Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="57fbb-137">Get started with .NET Core using the command-line</span></span>](./tutorials/cli-create-console-app.md)
- [<span data-ttu-id="57fbb-138">Erste Schritte mit .NET Core unter macOS mit Visual Studio für Mac</span><span class="sxs-lookup"><span data-stu-id="57fbb-138">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="57fbb-139">Tutorial: Erstellen einer .NET-Standard-Bibliothek in Visual Studio für Mac</span><span class="sxs-lookup"><span data-stu-id="57fbb-139">Build a .NET Standard library on macOS using Visual Studio for Mac</span></span>](tutorials/library-with-visual-studio-mac.md)

|   |   |
|---|---|
| <span data-ttu-id="57fbb-140">![Symbol für Filmkamera für das Video](media/video-icon.png "Video ansehen")</span><span class="sxs-lookup"><span data-stu-id="57fbb-140">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="57fbb-141">Sehen Sie sich ein Video zu den [ersten Schritte mit Visual Studio Code mit C# und .NET Core unter macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac) an.</span><span class="sxs-lookup"><span data-stu-id="57fbb-141">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="57fbb-142">Eine Liste der unterstützten OS X-/macOS-Versionen finden Sie im Artikel [.NET Core-Abhängigkeiten und -Anforderungen](install/dependencies.md?pivots=os-macos).</span><span class="sxs-lookup"><span data-stu-id="57fbb-142">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
