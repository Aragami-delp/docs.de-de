---
title: Installieren von .NET Core auf SLES 12 mit einem Paket-Manager (.NET Core)
description: Verwenden Sie einen Paket-Manager, um das .NET Core SDK und die -Runtime auf SLES 12 zu installieren.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 314688d60fb77e1b569dd037fb1d78c3f1f94dbc
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645649"
---
# <a name="sles-12-package-manager---install-net-core"></a>SLES 12-Paket-Manager: Installieren von .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

In diesem Artikel wird beschrieben, wie Sie mit einem Paket-Manager .NET Core auf SLES 12 installieren.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a>Hinzufügen des Microsoft-Repositoryschlüssels und -Feeds

Vor der Installation von .NET müssen Sie folgende Schritte ausführen:

- Fügen Sie der Liste der vertrauenswürdigen Schlüssel den Microsoft-Paketsignaturschlüssel hinzu.
- Fügen Sie das Repository dem Paket-Manager hinzu.
- Installieren Sie erforderliche Abhängigkeiten.

Dies muss nur einmal pro Computer ausgeführt werden.

Öffnen Sie ein Terminal, und führen Sie den folgenden Befehl aus.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>Installieren des .NET Core SDK

Aktualisieren Sie die zur Installation verfügbaren Produkte, und installieren Sie dann das .NET Core SDK. Führen Sie in Ihrem Terminal den folgenden Befehl aus.

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Installieren der ASP.NET Core-Runtime

Aktualisieren Sie die zur Installation verfügbaren Produkte, und installieren Sie dann die ASP.NET-Runtime. Führen Sie in Ihrem Terminal den folgenden Befehl aus.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Installieren der .NET Core-Runtime

Aktualisieren Sie die zur Installation verfügbaren Produkte, und installieren Sie dann die .NET Core-Runtime. Führen Sie in Ihrem Terminal den folgenden Befehl aus.

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Installieren anderer Versionen

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Problembehandlung des Paket-Managers

Dieser Abschnitt enthält Informationen zu häufigen Fehlern, die bei der Verwendung des Paket-Managers zur Installation von .NET Core auftreten können.

### <a name="failed-to-fetch"></a>Fehler beim Abrufen

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
