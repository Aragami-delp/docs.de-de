---
ms.openlocfilehash: 19ccdb634d4e53ea66c032502f2adb70423ab121
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416250"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="17084-101">Azure: Azure-Integrationspakete mit Präfix „Microsoft“ entfernt</span><span class="sxs-lookup"><span data-stu-id="17084-101">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="17084-102">Die folgenden `Microsoft.*`-Pakete zur Integration von ASP.NET Core und Azure SDKs sind in ASP.NET Core 5.0 nicht enthalten:</span><span class="sxs-lookup"><span data-stu-id="17084-102">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="17084-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/) für die Integration von [Azure Key Vault](/azure/key-vault/) in das [Konfigurationssystem](/aspnet/core/fundamentals/configuration/).</span><span class="sxs-lookup"><span data-stu-id="17084-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="17084-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/) zur Integration von Azure Key Vault in das [ASP.NET Core Data Protection-System](/aspnet/core/security/data-protection/introduction).</span><span class="sxs-lookup"><span data-stu-id="17084-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="17084-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/) zur Integration von [Azure Blob Storage](/azure/storage/blobs/) in das ASP.NET Core-Datenschutzsystem.</span><span class="sxs-lookup"><span data-stu-id="17084-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="17084-106">Dieses Problem wird unter [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570) behandelt.</span><span class="sxs-lookup"><span data-stu-id="17084-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="17084-107">Eingeführt in Version</span><span class="sxs-lookup"><span data-stu-id="17084-107">Version introduced</span></span>

<span data-ttu-id="17084-108">5.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="17084-108">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="17084-109">Altes Verhalten</span><span class="sxs-lookup"><span data-stu-id="17084-109">Old behavior</span></span>

<span data-ttu-id="17084-110">Die `Microsoft.*`-Pakete integrierten Azure-Dienste in die APIs für Konfiguration und Datenschutz.</span><span class="sxs-lookup"><span data-stu-id="17084-110">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="17084-111">Neues Verhalten</span><span class="sxs-lookup"><span data-stu-id="17084-111">New behavior</span></span>

<span data-ttu-id="17084-112">Neue `Azure.*`-Pakete integrierten Azure-Dienste in die APIs für Konfiguration und Datenschutz.</span><span class="sxs-lookup"><span data-stu-id="17084-112">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="17084-113">Grund für die Änderung</span><span class="sxs-lookup"><span data-stu-id="17084-113">Reason for change</span></span>

<span data-ttu-id="17084-114">Die Änderungen wurden aufgrund der folgenden Eigenschaften der `Microsoft.*`-Pakete vorgenommen:</span><span class="sxs-lookup"><span data-stu-id="17084-114">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="17084-115">Es wurden veraltete Versionen des Azure SDK verwendet.</span><span class="sxs-lookup"><span data-stu-id="17084-115">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="17084-116">Einfache Updates waren nicht möglich, weil die neuen Azure SDK-Versionen Änderungen mit Auswirkung auf die Lauffähigkeit umfassten.</span><span class="sxs-lookup"><span data-stu-id="17084-116">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="17084-117">Sie waren an den .NET Core-Releasezeitplan gebunden.</span><span class="sxs-lookup"><span data-stu-id="17084-117">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="17084-118">Eine Übertragung des Paketbesitzes an das Azure SDK-Team ermöglicht Paketupdates im Rahmen von Azure SDK-Aktualisierungen.</span><span class="sxs-lookup"><span data-stu-id="17084-118">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="17084-119">Empfohlene Aktion</span><span class="sxs-lookup"><span data-stu-id="17084-119">Recommended action</span></span>

<span data-ttu-id="17084-120">Ersetzen Sie in Projekten mit ASP.NET Core 2.1 oder höher die alten `Microsoft.*`- durch die neuen `Azure.*`-Pakete.</span><span class="sxs-lookup"><span data-stu-id="17084-120">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="17084-121">Alt</span><span class="sxs-lookup"><span data-stu-id="17084-121">Old</span></span> | <span data-ttu-id="17084-122">Neu</span><span class="sxs-lookup"><span data-stu-id="17084-122">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="17084-123">Azure.Extensions.AspNetCore.DataProtection.Keys</span><span class="sxs-lookup"><span data-stu-id="17084-123">Azure.Extensions.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="17084-124">Azure.Extensions.AspNetCore.DataProtection.Blobs</span><span class="sxs-lookup"><span data-stu-id="17084-124">Azure.Extensions.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="17084-125">Azure.Extensions.AspNetCore.Configuration.Secrets</span><span class="sxs-lookup"><span data-stu-id="17084-125">Azure.Extensions.AspNetCore.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

<span data-ttu-id="17084-126">Die neuen Pakete verwenden eine neue Azure SDK-Version, die Breaking Changes umfasst.</span><span class="sxs-lookup"><span data-stu-id="17084-126">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="17084-127">Die allgemeinen Nutzungsmuster haben sich nicht verändert.</span><span class="sxs-lookup"><span data-stu-id="17084-127">The general usage patterns are unchanged.</span></span> <span data-ttu-id="17084-128">Einige Überladungen und Optionen können abweichen, um sich an Änderungen in den zugrunde liegenden Azure SDK-APIs anzupassen.</span><span class="sxs-lookup"><span data-stu-id="17084-128">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="17084-129">Für die alten Pakete gilt:</span><span class="sxs-lookup"><span data-stu-id="17084-129">The old packages will:</span></span>

* <span data-ttu-id="17084-130">Sie werden für die gesamte Lebensdauer von .NET Core 2.1 und 3.1 vom ASP.NET Core-Team unterstützt.</span><span class="sxs-lookup"><span data-stu-id="17084-130">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="17084-131">Die Pakete sind nicht in .NET 5 enthalten.</span><span class="sxs-lookup"><span data-stu-id="17084-131">Not be included in .NET 5.</span></span>

<span data-ttu-id="17084-132">Stellen Sie beim Upgrade Ihres Projekts auf .NET 5 auf die `Azure.*`-Pakete um, um eine weitere Unterstützung zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="17084-132">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

#### <a name="category"></a><span data-ttu-id="17084-133">Kategorie</span><span class="sxs-lookup"><span data-stu-id="17084-133">Category</span></span>

<span data-ttu-id="17084-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="17084-134">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="17084-135">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="17084-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
