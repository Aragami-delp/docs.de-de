---
title: 'Vorgehensweise: Aufrufen einer Windows-Funktion, die vorzeichenlose Typen akzeptiert'
ms.date: 07/20/2015
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
ms.openlocfilehash: f30b78a2f0c38f233796e18006c889438dce4c58
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396829"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="d82bb-102">Gewusst wie: Aufrufen einer Windows-Funktion, die vorzeichenlose Typen akzeptiert (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d82bb-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>

<span data-ttu-id="d82bb-103">Wenn Sie eine Klasse, ein Modul oder eine Struktur mit Membern von ganzzahligen Typen ohne Vorzeichen verwenden, können Sie mit Visual Basic auf diese Member zugreifen.</span><span class="sxs-lookup"><span data-stu-id="d82bb-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="d82bb-104">So wird eine Windows-Funktion aufgerufen, die einen nicht signierten Typ annimmt</span><span class="sxs-lookup"><span data-stu-id="d82bb-104">To call a Windows function that takes an unsigned type</span></span>

1. <span data-ttu-id="d82bb-105">Verwenden Sie eine [Declare-Anweisung](../../language-reference/statements/declare-statement.md) , um zu ermitteln, Visual Basic welche Bibliothek die Funktion enthält, wie sich Ihr Name in dieser Bibliothek befindet, welche Aufruf Sequenz Sie enthält und wie Zeichen folgen beim Aufrufen konvertiert werden.</span><span class="sxs-lookup"><span data-stu-id="d82bb-105">Use a [Declare Statement](../../language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>

2. <span data-ttu-id="d82bb-106">Verwenden Sie in der- `Declare` Anweisung `UInteger` , `ULong` , `UShort` oder `Byte` nach Bedarf für jeden Parameter mit einem unsignierten Typ.</span><span class="sxs-lookup"><span data-stu-id="d82bb-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>

3. <span data-ttu-id="d82bb-107">In der Dokumentation für die Windows-Funktion, die Sie aufrufen, finden Sie die Namen und Werte der Konstanten, die Sie verwendet.</span><span class="sxs-lookup"><span data-stu-id="d82bb-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="d82bb-108">Viele davon sind in der Datei "Winuser. h" definiert.</span><span class="sxs-lookup"><span data-stu-id="d82bb-108">Many of these are defined in the WinUser.h file.</span></span>

4. <span data-ttu-id="d82bb-109">Deklarieren Sie die erforderlichen Konstanten in Ihrem Code.</span><span class="sxs-lookup"><span data-stu-id="d82bb-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="d82bb-110">Viele Windows-Konstanten sind 32-Bit-Werte ohne Vorzeichen, und Sie sollten diese deklarieren `As UInteger` .</span><span class="sxs-lookup"><span data-stu-id="d82bb-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>

5. <span data-ttu-id="d82bb-111">Die-Funktion wird auf die übliche Weise aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="d82bb-111">Call the function in the normal way.</span></span> <span data-ttu-id="d82bb-112">Im folgenden Beispiel wird die Windows-Funktion aufgerufen `MessageBox` , die ein ganzzahliges Argument ohne Vorzeichen annimmt.</span><span class="sxs-lookup"><span data-stu-id="d82bb-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>

    ```vb
    Public Class windowsMessage
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (
            ByVal hWnd As Integer,
            ByVal lpText As String,
            ByVal lpCaption As String,
            ByVal uType As UInteger) As Integer
        Private Const MB_OK As UInteger = 0
        Private Const MB_ICONEXCLAMATION As UInteger = &H30
        Private Const IDOK As UInteger = 1
        Private Const IDCLOSE As UInteger = 8
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION
        Public Function messageThroughWindows() As String
            Dim r As Integer = mb(0, "Click OK if you see this!",
                "Windows API call", c)
            Dim s As String = "Windows API MessageBox returned " &
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"
            Return s
        End Function
    End Class
    ```

     <span data-ttu-id="d82bb-113">Sie können die Funktion `messageThroughWindows` mit dem folgenden Code testen.</span><span class="sxs-lookup"><span data-stu-id="d82bb-113">You can test the function `messageThroughWindows` with the following code.</span></span>

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > <span data-ttu-id="d82bb-114">Die `UInteger` `ULong` `UShort` Datentypen,, und `SByte` sind nicht Teil der [Sprachunabhängigkeit und sprachunabhängigen Komponenten](../../../standard/language-independence-and-language-independent-components.md) (CLS). Daher kann CLS-kompatibler Code keine Komponente verwenden, die Sie verwendet.</span><span class="sxs-lookup"><span data-stu-id="d82bb-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d82bb-115">Wenn Sie nicht verwalteten Code, wie z. b. die Windows-API (Application Programming Interface), anrufen, wird der Code für potenzielle Sicherheitsrisiken verfügbar gemacht.</span><span class="sxs-lookup"><span data-stu-id="d82bb-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d82bb-116">Der Aufruf der Windows-API erfordert die Berechtigung "nicht verwalteter Code", die sich in teilweise vertrauenswürdigen Situationen auf die Ausführung auswirken kann.</span><span class="sxs-lookup"><span data-stu-id="d82bb-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="d82bb-117">Weitere Informationen finden Sie unter <xref:System.Security.Permissions.SecurityPermission> und [Code Zugriffsberechtigungen](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d82bb-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="d82bb-118">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d82bb-118">See also</span></span>

- [<span data-ttu-id="d82bb-119">Datentypen</span><span class="sxs-lookup"><span data-stu-id="d82bb-119">Data Types</span></span>](../../language-reference/data-types/index.md)
- [<span data-ttu-id="d82bb-120">Integer-Datentyp</span><span class="sxs-lookup"><span data-stu-id="d82bb-120">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="d82bb-121">UInteger-Datentyp</span><span class="sxs-lookup"><span data-stu-id="d82bb-121">UInteger Data Type</span></span>](../../language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="d82bb-122">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="d82bb-122">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)
- [<span data-ttu-id="d82bb-123">Exemplarische Vorgehensweise: Aufrufen von Windows-APIs</span><span class="sxs-lookup"><span data-stu-id="d82bb-123">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
