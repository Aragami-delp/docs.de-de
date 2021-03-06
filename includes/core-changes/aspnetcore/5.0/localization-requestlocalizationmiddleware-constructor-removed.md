---
ms.openlocfilehash: db941229e02064ee856829417d6762aa17b0b926
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2020
ms.locfileid: "86309147"
---
### <a name="localization-obsolete-constructor-removed-in-request-localization-middleware"></a>Lokalisierung: Ein veralteter Konstruktor wurde in der Middleware für Anforderungslokalisierung entfernt

Der <xref:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware>-Konstruktor, dem ein <xref:Microsoft.Extensions.Logging.ILoggerFactory>-Parameter fehlt, wurde [in diesem Commit](https://github.com/dotnet/aspnetcore/commit/ba8c6ccf6fd3eeb7fc42a159d362b15eae4fb3a0) als veraltet gekennzeichnet. In ASP.NET Core 5.0 wurde der veraltete Konstruktor entfernt. Weitere Informationen finden Sie unter [dotnet/aspnetcore#23785](https://github.com/dotnet/aspnetcore/issues/23785).

#### <a name="version-introduced"></a>Eingeführt in Version

5.0 Preview 8

#### <a name="old-behavior"></a>Altes Verhalten

Der veraltete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)`-Konstruktor ist vorhanden.

#### <a name="new-behavior"></a>Neues Verhalten

Der veraltete `RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions<RequestLocalizationOptions>)`-Konstruktor ist nicht vorhanden.

#### <a name="reason-for-change"></a>Grund für die Änderung

Diese Änderung sorgt dafür, dass die Middleware für die Anforderungslokalisierung immer Zugriff auf die Protokollierung hat.

#### <a name="recommended-action"></a>Empfohlene Aktion

Wenn eine `RequestLocalizationMiddleware`-Instanz manuell erstellt wird, übergeben Sie eine `ILoggerFactory`-Instanz im Konstruktor. Wenn in diesem Kontext keine gültige `ILoggerFactory`-Instanz verfügbar ist, sollten Sie den Middlewarekonstruktor eine <xref:Microsoft.Extensions.Logging.Abstractions.NullLoggerFactory>-Instanz übergeben.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Betroffene APIs

[RequestLocalizationMiddleware.ctor(RequestDelegate, IOptions\<RequestLocalizationOptions>)](/dotnet/api/microsoft.aspnetcore.localization.requestlocalizationmiddleware.-ctor?view=aspnetcore-3.1#Microsoft_AspNetCore_Localization_RequestLocalizationMiddleware__ctor_Microsoft_AspNetCore_Http_RequestDelegate_Microsoft_Extensions_Options_IOptions_Microsoft_AspNetCore_Builder_RequestLocalizationOptions__)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Localization.RequestLocalizationMiddleware.#ctor(Microsoft.AspNetCore.Http.RequestDelegate,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Builder.RequestLocalizationOptions})`

-->
