---
title: '.NET Core: Einführung und Übersicht'
description: .NET Core ist eine modulare, hochleistungsfähige Implementierung von .NET, mit der Sie Windows-, Linux- und macOS-Apps erstellen können. Erfahren Sie mehr über .NET Core, und legen Sie los.
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: f99b446bbd38b2b814c13afa13ab34cd5c9aa086
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645521"
---
# <a name="introduction-to-net-core"></a>Einführung in .NET Core

[.NET Core](about.md) ist eine universelle [Open Source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)-Entwicklungsplattform. Sie können .NET Core-Apps für Windows, macOS und Linux für x64-, x86-, ARM32- und ARM64-Prozessoren erstellen und dabei verschiedene Programmiersprachen verwenden. Es werden Frameworks und APIs für die [Cloud](/aspnet/core/), für [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), für [Clientbenutzeroberflächen](../desktop-wpf/overview/index.md) und für [Machine Learning](/dotnet/machine-learning/) bereitgestellt.

[Laden Sie das .NET Core SDK herunter](https://dotnet.microsoft.com/download), um .NET Core auf Ihrem Computer zu testen. [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/) ist die neueste Version.

## <a name="download-net-core"></a>Herunterladen von .NET Core

Zum Abrufen von .NET Core stehen die folgenden Möglichkeiten zur Verfügung:

* [Installationsprogramme für Windows und macOS](https://dotnet.microsoft.com/download)
* [Linux-Pakete](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [Docker-Container](https://hub.docker.com/_/microsoft-dotnet-core/)
* [ZIP-Dateien und Tarballs](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [Installationsskripts](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [Versionshinweise](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a>Erstellen Ihrer ersten Anwendung

Öffnen Sie nach der Installation von .NET Core SDK eine Eingabeaufforderung. Verwenden Sie die folgenden Befehle, um eine Anwendung zu erstellen und auszuführen:

```dotnetcli
dotnet new console
dotnet run
```

Die folgende Ausgabe wird angezeigt:

```output
Hello World!
```

## <a name="contribute"></a>Mitwirken

.NET Core ist eine offene Plattform. Alle Benutzer dürfen gerne daran mitwirken.

* Bei Produktproblemen und -fragen hilft die [Entwicklercommunity](https://developercommunity.visualstudio.com/spaces/61/index.html).
* Beiträge müssen über eins der Projektrepositorys eingereicht werden, z. B. [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn) oder [aspnetcore](https://github.com/dotnet/aspnetcore). Weitere Informationen finden Sie unter [.NET Core-Repositorys](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).

## <a name="support"></a>Support

.NET Core wird von Microsoft unter Windows, macOS und Linux sowie von Red Hat unter Red Hat Enterprise Linux unterstützt.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [.NET Core-Tutorials](tutorials/index.md)

> [!div class="nextstepaction"]
> [.NET Core im Browser testen](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
