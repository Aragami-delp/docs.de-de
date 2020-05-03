---
title: 'Vorgehensweise: Entfernen einer Assembly aus dem globalen Assemblycache'
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- global assembly cache, removing assemblies
- strong-named assemblies, global assembly cache
- removing assemblies from global assembly cache
- deleting assemblies in global assembly cache
- Global Assembly Cache tool
- GAC (global assembly cache), removing assemblies
ms.assetid: acdcc588-b458-436d-876c-726de68244c1
ms.openlocfilehash: c7d85222f35a61154e3eec70d8c9dad2ca6a32f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119857"
---
# <a name="how-to-remove-an-assembly-from-the-global-assembly-cache"></a>Vorgehensweise: Entfernen einer Assembly aus dem globalen Assemblycache

Es gibt zwei Möglichkeiten, eine Assembly aus dem globalen Assemblycache (GAC) zu entfernen:

- Durch Verwenden des [Global Assembly Cache-Tools (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md). Diese Option können Sie zum Deinstallieren von Assemblys verwenden, die Sie beim Entwickeln und Testen im GAC platziert haben.

- Mithilfe von [Windows Installer](/windows/desktop/Msi/windows-installer-portal). Diese Option für das Deinstallieren von Assemblys sollten Sie für Produktionssysteme und dann verwenden, wenn Sie Installationspakete testen.

## <a name="removing-an-assembly-with-gacutilexe"></a>Entfernen einer Assembly mit "Gacutil.exe"

Geben Sie an der Eingabeaufforderung folgenden Befehl ein:

**gacutil -u** \<*Assemblyname*>

In diesem Befehl ist *Assemblyname* der Name der Assembly, die aus dem globalen Assemblycache entfernt werden soll.

> [!WARNING]
> Sie sollten "Gacutil.exe" nicht verwenden, um Assemblys auf Produktionssystemen zu entfernen, denn es besteht die Möglichkeit, dass die Assembly für einige Anwendungen weiterhin erforderlich ist. Stattdessen sollten Sie den Windows Installer verwenden, der einen Verweiszähler für jede Assembly verwaltet, die er im GAC installiert.

Im folgenden Beispiel wird die Assembly `hello.dll` aus dem globalen Assemblycache entfernt:

```console
gacutil -u hello
```

## <a name="removing-an-assembly-with-windows-installer"></a>Entfernen einer Assembly mit Windows Installer

Wählen Sie in der **Systemsteuerung** in **Programme und Funktionen** die Anwendung aus, die Sie deinstallieren möchten. Wenn das Installationspaket Assemblys im GAC platziert hat, werden diese von Windows Installer entfernt, sofern sie nicht von einer anderen Anwendung verwendet werden.

> [!NOTE]
> Windows Installer verwaltet einen Verweiszähler für Assemblys, die im GAC installiert sind. Eine Assembly wird nur dann aus dem GAC entfernt, wenn ihr Verweiszähler gleich null wird, wodurch angegeben ist, dass sie von keiner der Anwendungen verwendet wird, die über ein Windows Installer-Paket installiert wurden.

## <a name="see-also"></a>Siehe auch

- [Arbeiten mit Assemblys und dem globalen Assemblychache](working-with-assemblies-and-the-gac.md)
- [How to: Installieren einer Assembly im globalen Assemblycache](install-assembly-into-gac.md)
- [Gacutil.exe (Global Assembly Cache-Tool)](../tools/gacutil-exe-gac-tool.md)
