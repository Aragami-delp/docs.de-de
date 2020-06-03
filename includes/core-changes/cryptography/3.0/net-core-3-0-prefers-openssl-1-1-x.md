---
ms.openlocfilehash: 877f9d99b660c4af843e4d8d525219c1df6c99a9
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721119"
---
### <a name="net-core-30-prefers-openssl-11x-to-openssl-10x"></a><span data-ttu-id="abad6-101">.NET Core 3.0 zieht OpenSSL 1.1.x OpenSSL 1.0.x vor</span><span class="sxs-lookup"><span data-stu-id="abad6-101">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>

<span data-ttu-id="abad6-102">.NET Core für Linux, das über mehrere Linux-Distributionen hinweg funktioniert, kann sowohl OpenSSL 1.0.x als auch OpenSSL 1.1.x unterstützen.</span><span class="sxs-lookup"><span data-stu-id="abad6-102">.NET Core for Linux, which works across multiple Linux distributions, can support both OpenSSL 1.0.x and OpenSSL 1.1.x.</span></span>  <span data-ttu-id="abad6-103">.NET Core 2.1 und .NET Core 2.2 suchen zuerst nach 1.0.x und dann nach 1.1.x. .NET Core 3.0 sucht zuerst nach 1.1.x.</span><span class="sxs-lookup"><span data-stu-id="abad6-103">.NET Core 2.1 and .NET Core 2.2 look for 1.0.x first, then fall back to 1.1.x; .NET Core 3.0 looks for 1.1.x first.</span></span> <span data-ttu-id="abad6-104">Diese Änderung wurde vorgenommen, um Unterstützung für neue Kryptografiestandards hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="abad6-104">This change was made to add support for new cryptographic standards.</span></span>

<span data-ttu-id="abad6-105">Diese Änderung kann sich auf Bibliotheken oder Anwendungen auswirken, die plattformübergreifendes Interop mit den OpenSSL-spezifischen Interoptypen in .NET Core durchführen.</span><span class="sxs-lookup"><span data-stu-id="abad6-105">This change may impact libraries or applications that do platform interop with the OpenSSL-specific interop types in .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="abad6-106">Änderungsbeschreibung</span><span class="sxs-lookup"><span data-stu-id="abad6-106">Change description</span></span>

<span data-ttu-id="abad6-107">In .NET Core 2.2 und früheren Versionen zieht die Runtime das Laden von OpenSSL 1.0.x dem Laden von 1.1.x vor.</span><span class="sxs-lookup"><span data-stu-id="abad6-107">In .NET Core 2.2 and earlier versions, the runtime prefers loading OpenSSL 1.0.x over 1.1.x.</span></span> <span data-ttu-id="abad6-108">Dies bedeutet, dass der <xref:System.IntPtr>- und <xref:System.Runtime.InteropServices.SafeHandle>-Typ für Interop mit OpenSSL mit libcrypto.so.1.0.0/libcrypto.so.1.0/libcrypto.so.10 bevorzugt verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="abad6-108">This means that the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.0.0 / libcrypto.so.1.0 / libcrypto.so.10 by preference.</span></span>

<span data-ttu-id="abad6-109">Ab .NET Core 3.0 bevorzugt die Runtime das Laden von OpenSSL 1.1.x gegenüber OpenSSL 1.0.x, sodass die Typen <xref:System.IntPtr> und <xref:System.Runtime.InteropServices.SafeHandle> für Interop mit OpenSSL mit libcrypto.so.1.1/libcrypto.so.11/libcrypto.so.1.1.0/libcrypto.so.1.1.1 verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="abad6-109">Starting with .NET Core 3.0, the runtime prefers loading OpenSSL 1.1.x over OpenSSL 1.0.x, so the <xref:System.IntPtr> and <xref:System.Runtime.InteropServices.SafeHandle> types for interop with OpenSSL are used with libcrypto.so.1.1 / libcrypto.so.11 / libcrypto.so.1.1.0 / libcrypto.so.1.1.1 by preference.</span></span> <span data-ttu-id="abad6-110">Infolgedessen können Bibliotheken und Anwendungen, die direkt mit OpenSSL interagieren, beim Upgrade von .NET Core 2.1 oder .NET Core 2.2 inkompatible Zeiger mit den von .NET Core bereitgestellten Werten aufweisen.</span><span class="sxs-lookup"><span data-stu-id="abad6-110">As a result, libraries and applications that interoperate with OpenSSL directly may have incompatible pointers with the .NET Core-exposed values when upgrading from .NET Core 2.1 or .NET Core 2.2.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="abad6-111">Eingeführt in Version</span><span class="sxs-lookup"><span data-stu-id="abad6-111">Version introduced</span></span>

<span data-ttu-id="abad6-112">3.0</span><span class="sxs-lookup"><span data-stu-id="abad6-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="abad6-113">Empfohlene Aktion</span><span class="sxs-lookup"><span data-stu-id="abad6-113">Recommended action</span></span>

<span data-ttu-id="abad6-114">Bibliotheken und Anwendungen, die direkte Vorgänge mit OpenSSL ausführen, müssen darauf achten, dass sichergestellt wird, dass sie die gleiche OpenSSL-Version wie die .NET Core-Runtime verwenden.</span><span class="sxs-lookup"><span data-stu-id="abad6-114">Libraries and applications that do direct operations with OpenSSL need to be careful to ensure they are using the same version of OpenSSL as the .NET Core runtime.</span></span>

<span data-ttu-id="abad6-115">Alle Bibliotheken oder Anwendungen, die <xref:System.IntPtr>- oder <xref:System.Runtime.InteropServices.SafeHandle>-Werte aus den kryptographischen .NET Core-Typen direkt mit OpenSSL verwenden, sollten die Version der von ihnen verwendeten Bibliothek mit der neuen <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType>-Eigenschaft vergleichen, um sicherzustellen, dass die Zeiger kompatibel sind.</span><span class="sxs-lookup"><span data-stu-id="abad6-115">All libraries or applications that use <xref:System.IntPtr> or <xref:System.Runtime.InteropServices.SafeHandle> values from the .NET Core cryptographic types directly with OpenSSL should compare the version of the library they use with the new <xref:System.Security.Cryptography.SafeEvpPKeyHandle.OpenSslVersion?displayProperty=nameWithType> property to ensure the pointers are compatible.</span></span>

#### <a name="category"></a><span data-ttu-id="abad6-116">Kategorie</span><span class="sxs-lookup"><span data-stu-id="abad6-116">Category</span></span>

<span data-ttu-id="abad6-117">Kryptografie</span><span class="sxs-lookup"><span data-stu-id="abad6-117">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="abad6-118">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="abad6-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.SafeEvpPKeyHandle.%23ctor%2A>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.RSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.DSAOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.IntPtr)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.%23ctor(System.Security.Cryptography.SafeEvpPKeyHandle)>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Handle?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Security.Cryptography.SafeEvpPKeyHandle.#ctor`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.RSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.RSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.DSAOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.DSAOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.#ctor(System.Security.CryptographySafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDsaOpenSsl.DuplicateKeyHandle`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.IntPtr)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.#ctor(System.Security.Cryptography.SafeEvpPKeyHandle)`
- `M:System.Security.Cryptography.ECDiffieHellmanOpenSsl.DuplicateKeyHandle`
- `P:System.Security.Cryptography.X509Certificates.X509Certificate.Handle`

-->
