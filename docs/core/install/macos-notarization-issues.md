---
title: Verwenden der macOS Catalina-Notarisierung
description: In diesem Artikel erfahren Sie, wie Sie Probleme mit der Notarisierung und mit Zertifikaten unter macOS behandeln, wenn Sie die .NET Core-Runtime, das SDK und mit .NET Core erstellte Apps installieren.
author: thraka
ms.author: adegeo
ms.date: 02/14/2020
ms.openlocfilehash: be39c1ea56699f84736a2b37bc958507b16e826b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146748"
---
# <a name="macos-catalina-notarization-and-the-impact-on-net-core-downloads-and-projects"></a><span data-ttu-id="75cc2-103">macOS Catalina-Notarisierung und die Auswirkungen auf .NET Core-Downloads und -Projekte</span><span class="sxs-lookup"><span data-stu-id="75cc2-103">macOS Catalina Notarization and the impact on .NET Core downloads and projects</span></span>

<span data-ttu-id="75cc2-104">Ab macOS Catalina (Version 10.15) muss jegliche Software notarisiert werden, die nach dem 1. Juni 2019 erstellt wurde und mit einer Entwickler-ID verteilt wird.</span><span class="sxs-lookup"><span data-stu-id="75cc2-104">Beginning with macOS Catalina (version 10.15), all software built after June 1, 2019, and distributed with Developer ID, must be notarized.</span></span> <span data-ttu-id="75cc2-105">Diese Voraussetzung gilt für die .NET Core-Runtime, das .NET Core SDK und jegliche Software, die mit .NET Core erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="75cc2-105">This requirement applies to the .NET Core runtime, .NET Core SDK, and software created with .NET Core.</span></span> <span data-ttu-id="75cc2-106">In diesem Artikel werden gängige Szenarios beschrieben, die bei .NET Core und der macOS-Notarisierung auftreten können.</span><span class="sxs-lookup"><span data-stu-id="75cc2-106">This article describes the common scenarios you may face with .NET Core and macOS notarization.</span></span>

## <a name="installing-net-core"></a><span data-ttu-id="75cc2-107">Installieren von .NET Core</span><span class="sxs-lookup"><span data-stu-id="75cc2-107">Installing .NET Core</span></span>

<span data-ttu-id="75cc2-108">Die Installationsprogramme für die Versionen 3.1, 3.0 und 2.1 von .NET Core (sowohl für die Runtime als auch das SDK) wurden seit dem 18. Februar 2020 notarisiert.</span><span class="sxs-lookup"><span data-stu-id="75cc2-108">The installers for .NET Core (both runtime and SDK) versions 3.1, 3.0, and 2.1, have been notarized since February 18, 2020.</span></span> <span data-ttu-id="75cc2-109">Vorherige Versionen wurden nicht notarisiert.</span><span class="sxs-lookup"><span data-stu-id="75cc2-109">Prior released versions aren't notarized.</span></span> <span data-ttu-id="75cc2-110">Sie können eine nicht notarisierte Version von .NET Core manuell installieren, indem Sie zunächst das Installationsprogramm herunterladen und dann den Befehl `sudo installer` ausführen.</span><span class="sxs-lookup"><span data-stu-id="75cc2-110">You can manually install a non-notarized version of .NET Core by first downloading the installer, and then using the `sudo installer` command.</span></span> <span data-ttu-id="75cc2-111">Weitere Informationen finden Sie unter [Herunterladen und manuelles Installieren für macOS](sdk.md?pivots=os-macos#download-and-manually-install).</span><span class="sxs-lookup"><span data-stu-id="75cc2-111">For more information, see [Download and manually install for macOS](sdk.md?pivots=os-macos#download-and-manually-install).</span></span>

<span data-ttu-id="75cc2-112">Ab den folgenden Versionen sind die .NET Core-Installationsprogramme notarisiert:</span><span class="sxs-lookup"><span data-stu-id="75cc2-112">Beginning with the following versions, the .NET Core installers are notarized:</span></span>

- <span data-ttu-id="75cc2-113">.NET Core Runtime</span><span class="sxs-lookup"><span data-stu-id="75cc2-113">.NET Core Runtime</span></span>
  - <span data-ttu-id="75cc2-114">2.1.16</span><span class="sxs-lookup"><span data-stu-id="75cc2-114">2.1.16</span></span>
  - <span data-ttu-id="75cc2-115">3.0.3</span><span class="sxs-lookup"><span data-stu-id="75cc2-115">3.0.3</span></span>
  - <span data-ttu-id="75cc2-116">3.1.2</span><span class="sxs-lookup"><span data-stu-id="75cc2-116">3.1.2</span></span>

- <span data-ttu-id="75cc2-117">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="75cc2-117">.NET Core SDK</span></span>
  - <span data-ttu-id="75cc2-118">2.1.512</span><span class="sxs-lookup"><span data-stu-id="75cc2-118">2.1.512</span></span>
  - <span data-ttu-id="75cc2-119">3.0.103</span><span class="sxs-lookup"><span data-stu-id="75cc2-119">3.0.103</span></span>
  - <span data-ttu-id="75cc2-120">3.1.102</span><span class="sxs-lookup"><span data-stu-id="75cc2-120">3.1.102</span></span>

## <a name="apphost-is-disabled-by-default"></a><span data-ttu-id="75cc2-121">appHost ist standardmäßig deaktiviert</span><span class="sxs-lookup"><span data-stu-id="75cc2-121">appHost is disabled by default</span></span>

<span data-ttu-id="75cc2-122">Nicht notarisierte Versionen von .NET Core SDK 3.0 und höher erstellen eine native ausführbare Mach-O-Datei (als **appHost** bekannt), sobald ihr Projekt kompiliert, veröffentlicht oder ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="75cc2-122">By default, non-notarized versions of the .NET Core SDK 3.0 and above produce a native Mach-O executable (known as the **appHost**) when your project compiles, publishes, or is run.</span></span> <span data-ttu-id="75cc2-123">Diese ausführbare Datei ist eine praktische Methode zum Ausführen Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="75cc2-123">This executable is a convenient way to run your app.</span></span> <span data-ttu-id="75cc2-124">Andernfalls muss Ihre App durch Ausführen von `dotnet <filename.dll>` gestartet werden.</span><span class="sxs-lookup"><span data-stu-id="75cc2-124">Otherwise, your app must be started by running `dotnet <filename.dll>`.</span></span> <span data-ttu-id="75cc2-125">Wenn die appHost-Datei aktiviert ist, wird der `dotnet run`-Befehl im Kontext der appHost-Datei aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="75cc2-125">When the appHost is enabled, the `dotnet run` command is invoked in the context of the appHost.</span></span> <span data-ttu-id="75cc2-126">Weitere Informationen finden Sie im Abschnitt [Kontext der appHost-Datei](#context-of-the-apphost).</span><span class="sxs-lookup"><span data-stu-id="75cc2-126">For more information, see [Context of the appHost](#context-of-the-apphost).</span></span>

<span data-ttu-id="75cc2-127">Beginnend mit den notarisierten Versionen des .NET Core SDK 3.0 wird die ausführbare appHost-Datei nicht standardmäßig generiert.</span><span class="sxs-lookup"><span data-stu-id="75cc2-127">Starting with the notarized versions of the .NET Core SDK 3.0 and above, the appHost executable isn't generated by default.</span></span> <span data-ttu-id="75cc2-128">Sie können die Generation der appHost-Datei mit der booleschen Einstellung [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) in der Projektdatei aktivieren.</span><span class="sxs-lookup"><span data-stu-id="75cc2-128">You can turn on appHost generation with the [`UseAppHost`](../project-sdk/msbuild-props.md#useapphost) boolean setting in the project file.</span></span> <span data-ttu-id="75cc2-129">Sie können die appHost-Datei auch mit dem `-p:UseAppHost`-Parameter für den spezifischen `dotnet`-Befehl aktivieren, den Sie über die Befehlszeile ausführen:</span><span class="sxs-lookup"><span data-stu-id="75cc2-129">You can also toggle the appHost with the `-p:UseAppHost` parameter on the command line for the specific `dotnet` command you run:</span></span>

- <span data-ttu-id="75cc2-130">Projektdatei</span><span class="sxs-lookup"><span data-stu-id="75cc2-130">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="75cc2-131">Befehlszeilenparameter</span><span class="sxs-lookup"><span data-stu-id="75cc2-131">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="75cc2-132">Es wird immer eine appHost-Datei erstellt, wenn Sie Ihre App [eigenständig](../deploying/index.md#publish-self-contained) veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="75cc2-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="75cc2-133">Weitere Informationen über die `UseAppHost`-Einstellung finden Sie unter [MSBuild-Eigenschaften für Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="75cc2-133">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

### <a name="context-of-the-apphost"></a><span data-ttu-id="75cc2-134">Kontext der appHost-Datei</span><span class="sxs-lookup"><span data-stu-id="75cc2-134">Context of the appHost</span></span>

<span data-ttu-id="75cc2-135">Wenn die appHost-Datei in Ihrem Projekt aktiviert ist, und Sie den `dotnet run`-Befehl zum Ausführen Ihrer App verwenden, wird die App im Kontext der appHost-Datei und nicht im Kontext des Standardhosts aufgerufen (der Standardhost entspricht dem `dotnet`-Befehl).</span><span class="sxs-lookup"><span data-stu-id="75cc2-135">When the appHost is enabled in your project, and you use the `dotnet run` command to run your app, the app is invoked in the context of the appHost and not the default host (the default host is the `dotnet` command).</span></span> <span data-ttu-id="75cc2-136">Wenn die appHost-Datei in Ihrem Projekt deaktiviert ist, führt der `dotnet run`-Befehl Ihre App im Kontext des Standardhosts aus.</span><span class="sxs-lookup"><span data-stu-id="75cc2-136">If the appHost is disabled in your project, the `dotnet run` command runs your app in the context of the default host.</span></span> <span data-ttu-id="75cc2-137">Selbst wenn die appHost-Datei deaktiviert ist, wird eine ausführbare appHost-Datei beim Veröffentlichen Ihrer App als eigenständig generiert. Benutzer verwenden diese ausführbare Datei zum Ausführen Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="75cc2-137">Even if the appHost is disabled, publishing your app as self-contained generates an appHost executable, and users use that executable to run your app.</span></span> <span data-ttu-id="75cc2-138">Wenn Sie Ihre App mit `dotnet <filename.dll>` ausführen, wird die App mit dem Standardhost aufgerufen, der Shared Runtime.</span><span class="sxs-lookup"><span data-stu-id="75cc2-138">Running your app with `dotnet <filename.dll>` invokes the app with the default host, the shared runtime.</span></span>

<span data-ttu-id="75cc2-139">Wenn eine App aufgerufen wird, die die appHost-Datei verwendet, unterscheidet sich der Zugriff auf die App vom notarisierten Standardhost.</span><span class="sxs-lookup"><span data-stu-id="75cc2-139">When an app using the appHost is invoked, the certificate partition accessed by the app is different from the notarized default host.</span></span> <span data-ttu-id="75cc2-140">Wenn Ihre App auf Zertifikate zugreifen muss, die über den Standardhost installiert wurden, verwenden Sie den `dotnet run`-Befehl zum Ausführen Ihrer App über die Projektdatei, oder verwenden Sie den `dotnet <filename.dll>`-Befehl, um die App direkt auszuführen.</span><span class="sxs-lookup"><span data-stu-id="75cc2-140">If your app must access the certificates installed through the default host, use the `dotnet run` command to run your app from its project file, or use the `dotnet <filename.dll>` command to start the app directly.</span></span>

<span data-ttu-id="75cc2-141">Weitere Informationen über dieses Szenario finden Sie im Abschnitt [ASP.NET Core, macOS und Zertifikate](#aspnet-core-and-macos-and-certificates).</span><span class="sxs-lookup"><span data-stu-id="75cc2-141">More information about this scenario is provided in the [ASP.NET Core and macOS and certificates](#aspnet-core-and-macos-and-certificates) section.</span></span>

## <a name="aspnet-core-and-macos-and-certificates"></a><span data-ttu-id="75cc2-142">ASP.NET Core, macOS und Zertifikate</span><span class="sxs-lookup"><span data-stu-id="75cc2-142">ASP.NET Core and macOS and certificates</span></span>

<span data-ttu-id="75cc2-143">.NET Core bietet die Möglichkeit, Zertifikate in der macOS-Keychain mit der <xref:System.Security.Cryptography.X509Certificates>-Klasse zu verwalten.</span><span class="sxs-lookup"><span data-stu-id="75cc2-143">.NET Core provides the ability to manage certificates in the macOS Keychain with the <xref:System.Security.Cryptography.X509Certificates> class.</span></span> <span data-ttu-id="75cc2-144">Der Zugriff auf die macOS-Keychain verwendet bei der Entscheidung, welche Partition berücksichtigt werden soll, die Identität der Anwendung als Primärschlüssel.</span><span class="sxs-lookup"><span data-stu-id="75cc2-144">Access to the macOS Keychain uses the applications identity as the primary key when deciding which partition to consider.</span></span> <span data-ttu-id="75cc2-145">Beispielsweise speichern nicht signierte Anwendungen Geheimnisse in der nicht signierten Partition. Signierte Anwendungen speichern ihre Geheimnisse jedoch in Partitionen, auf die nur sie zugreifen können.</span><span class="sxs-lookup"><span data-stu-id="75cc2-145">For example, unsigned applications store secrets in the unsigned partition, but signed applications store their secrets in partitions only they can access.</span></span> <span data-ttu-id="75cc2-146">Die Ausführungsquelle, die Ihre App aufruft, entscheidet, welche Partition verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="75cc2-146">The source of execution that invokes your app decides which partition to use.</span></span>

<span data-ttu-id="75cc2-147">.NET Core bietet drei Ausführungsquellen: [appHost](#apphost-is-disabled-by-default), Standardhost (der `dotnet`-Befehl) und einen benutzerdefinierten Host.</span><span class="sxs-lookup"><span data-stu-id="75cc2-147">.NET Core provides three sources of execution: [appHost](#apphost-is-disabled-by-default), default host (the `dotnet` command), and a custom host.</span></span> <span data-ttu-id="75cc2-148">Alle Ausführungsmodelle können verschiedene signierte oder nicht signierte Identitäten aufweisen und verfügen über Zugriff auf verschiedene Partitionen in der Keychain.</span><span class="sxs-lookup"><span data-stu-id="75cc2-148">Each execution model may have different identities, either signed or unsigned, and has access to different partitions within the Keychain.</span></span> <span data-ttu-id="75cc2-149">Auf Zertifikate, die von einem Modus importiert werden, kann möglicherweise nicht über einen anderen Modus zugegriffen werden.</span><span class="sxs-lookup"><span data-stu-id="75cc2-149">Certificates imported by one mode may not be accessible from another.</span></span> <span data-ttu-id="75cc2-150">Beispielsweise verfügen die notarisierten Versionen von .NET Core über einen Standardhost, der signiert ist.</span><span class="sxs-lookup"><span data-stu-id="75cc2-150">For example, the notarized versions of .NET Core have a default host that is signed.</span></span> <span data-ttu-id="75cc2-151">Zertifikate werden basierend auf ihrer Identität in eine sichere Partition importiert.</span><span class="sxs-lookup"><span data-stu-id="75cc2-151">Certificates are imported into a secure partition based on its identity.</span></span> <span data-ttu-id="75cc2-152">Der Zugriff auf diese Zertifikate ist nicht über eine generierte appHost-Datei möglich, da diese nicht signiert ist.</span><span class="sxs-lookup"><span data-stu-id="75cc2-152">These certificates aren't accessible from a generated appHost, as the appHost is unsigned.</span></span>

<span data-ttu-id="75cc2-153">Ein weiteres Beispiel besteht darin, dass ASP.NET Core standardmäßig ein Standard-SSL-Zertifikat über den Standardhost importiert.</span><span class="sxs-lookup"><span data-stu-id="75cc2-153">Another example, by default, ASP.NET Core imports a default SSL certificate through the default host.</span></span> <span data-ttu-id="75cc2-154">ASP.NET Core-Anwendungen, die eine appHost-Datei verwenden, verfügen über keinen Zugriff auf dieses Zertifikat. Wenn .NET Core ein nicht zugängliches Zertifikat ermittelt, wird ein Fehler ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="75cc2-154">ASP.NET Core applications that use an appHost won't have access to this certificate and will receive an error when .NET Core detects the certificate isn't accessible.</span></span> <span data-ttu-id="75cc2-155">Die Fehlermeldung bietet Anweisungen zum Beheben des Problems.</span><span class="sxs-lookup"><span data-stu-id="75cc2-155">The error message provides instructions on how to fix this problem.</span></span>

<span data-ttu-id="75cc2-156">Wenn die Zertifikatfreigabe erforderlich ist, bietet macOS Konfigurationsoptionen über das Hilfsprogramm `security`.</span><span class="sxs-lookup"><span data-stu-id="75cc2-156">If certificate sharing is required, macOS provides configuration options with the `security` utility.</span></span>

<span data-ttu-id="75cc2-157">Weitere Informationen zur Behandlung von ASP.NET Core-Zertifikatproblemen finden Sie unter [Erzwingen von HTTPS in ASP.NET Core](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems).</span><span class="sxs-lookup"><span data-stu-id="75cc2-157">For more information on how to troubleshoot ASP.NET Core certificate issues, see [Enforce HTTPS in ASP.NET Core](/aspnet/core/security/enforcing-ssl?view=aspnetcore-3.1&tabs=visual-studio#troubleshoot-certificate-problems).</span></span>

## <a name="default-entitlements"></a><span data-ttu-id="75cc2-158">Standardberechtigungen</span><span class="sxs-lookup"><span data-stu-id="75cc2-158">Default entitlements</span></span>

<span data-ttu-id="75cc2-159">Der Standardhost von .NET Core (`dotnet`-Befehl) verfügt über einige Standardberechtigungen.</span><span class="sxs-lookup"><span data-stu-id="75cc2-159">.NET Core’s default host (the `dotnet` command) has a set of default entitlements.</span></span> <span data-ttu-id="75cc2-160">Diese Berechtigungen sind für den ordnungsgemäßen Betrieb von .NET Core erforderlich.</span><span class="sxs-lookup"><span data-stu-id="75cc2-160">These entitlements are required for proper operation of .NET Core.</span></span> <span data-ttu-id="75cc2-161">Manchmal erfordert Ihre Anwendung zusätzliche Berechtigungen. In diesem Fall müssen Sie eine [appHost-Datei](#apphost-is-disabled-by-default) generieren und verwenden und anschließend die erforderlichen Berechtigungen lokal hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="75cc2-161">It's possible that your application may need additional entitlements, in which case you'll need to generate and use an [appHost](#apphost-is-disabled-by-default) and then add the necessary entitlements locally.</span></span>

<span data-ttu-id="75cc2-162">Standardberechtigungen für .NET Core:</span><span class="sxs-lookup"><span data-stu-id="75cc2-162">Default set of entitlements for .NET Core:</span></span>

- `com.apple.security.cs.allow-jit`
- `com.apple.security.cs.allow-unsigned-executable-memory`
- `com.apple.security.cs.allow-dyld-environment-variables`
- `com.apple.security.cs.disable-library-validation`

## <a name="notarize-a-net-core-app"></a><span data-ttu-id="75cc2-163">Notarisieren einer .NET Core-App</span><span class="sxs-lookup"><span data-stu-id="75cc2-163">Notarize a .NET Core app</span></span>

<span data-ttu-id="75cc2-164">Wenn Sie Ihre Anwendung unter macOS Catalina (Version 10.15) oder höher ausführen möchten, müssen Sie Ihre App notarisieren.</span><span class="sxs-lookup"><span data-stu-id="75cc2-164">If you want your application to run on macOS Catalina (version 10.15) or higher, you'll want to notarize your app.</span></span> <span data-ttu-id="75cc2-165">Die appHost-Datei, die Sie mit Ihrer Anwendung zur Notarisierung einreichen, sollte mindestens über die [Standardberechtigungen](#default-entitlements) für .NET Core verfügen.</span><span class="sxs-lookup"><span data-stu-id="75cc2-165">The appHost you submit with your application for notarization should be used with at least the same [default entitlements](#default-entitlements) for .NET Core.</span></span>

## <a name="next-steps"></a><span data-ttu-id="75cc2-166">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="75cc2-166">Next steps</span></span>

- <span data-ttu-id="75cc2-167">[.NET Core-Abhängigkeiten und -Anforderungen](dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="75cc2-167">[.NET Core dependencies and requirements](dependencies.md).</span></span>
- <span data-ttu-id="75cc2-168">[Installieren des .NET Core SDK](sdk.md)</span><span class="sxs-lookup"><span data-stu-id="75cc2-168">[Install the .NET Core SDK](sdk.md).</span></span>
- [<span data-ttu-id="75cc2-169">Installieren der .NET Core-Runtime</span><span class="sxs-lookup"><span data-stu-id="75cc2-169">Install the .NET Core Runtime</span></span>](runtime.md)