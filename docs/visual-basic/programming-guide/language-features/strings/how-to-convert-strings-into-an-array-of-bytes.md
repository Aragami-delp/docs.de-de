---
title: 'Vorgehensweise: Konvertieren von Zeichenfolgen in ein Bytearray'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 3ee1d5e1e31054f23f4510c7a112d8e3473bcdd7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410605"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a><span data-ttu-id="96012-102">Gewusst wie: Konvertieren von Zeichenfolgen in ein Bytearray in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="96012-102">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>
<span data-ttu-id="96012-103">In diesem Thema wird gezeigt, wie eine Zeichenfolge in ein Bytearray konvertiert wird.</span><span class="sxs-lookup"><span data-stu-id="96012-103">This topic shows how to convert a string into an array of bytes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96012-104">Beispiel</span><span class="sxs-lookup"><span data-stu-id="96012-104">Example</span></span>  
 <span data-ttu-id="96012-105">In diesem Beispiel wird die- <xref:System.Text.Encoding.GetBytes%2A> Methode der <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> Encoding-Klasse verwendet, um eine Zeichenfolge in ein Bytearray zu konvertieren.</span><span class="sxs-lookup"><span data-stu-id="96012-105">This example uses the <xref:System.Text.Encoding.GetBytes%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert a string into an array of bytes.</span></span>  
  
 [!code-vb[VbVbalrStrings#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#74)]  
  
 <span data-ttu-id="96012-106">Sie können zwischen mehreren Codierungsoptionen wählen, um eine Zeichenfolge in ein Bytearray zu konvertieren:</span><span class="sxs-lookup"><span data-stu-id="96012-106">You can choose from several encoding options to convert a string into a byte array:</span></span>  
  
- <span data-ttu-id="96012-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Ruft eine Codierung für den ASCII-Zeichensatz (7-Bit) ab.</span><span class="sxs-lookup"><span data-stu-id="96012-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
- <span data-ttu-id="96012-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Ruft eine Codierung für das UTF-16-Format mit der Big-Endian-Byte Reihenfolge ab.</span><span class="sxs-lookup"><span data-stu-id="96012-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
- <span data-ttu-id="96012-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Ruft eine Codierung für die aktuelle ANSI-Codepage des Systems ab.</span><span class="sxs-lookup"><span data-stu-id="96012-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
- <span data-ttu-id="96012-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Ruft eine Codierung für das UTF-16-Format mit der Little-Endian-Byte Reihenfolge ab.</span><span class="sxs-lookup"><span data-stu-id="96012-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="96012-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Ruft eine Codierung für das UTF-32-Format unter Verwendung der Little-Endian-Byte Reihenfolge ab.</span><span class="sxs-lookup"><span data-stu-id="96012-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="96012-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Ruft eine Codierung für das UTF-7-Format ab.</span><span class="sxs-lookup"><span data-stu-id="96012-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
- <span data-ttu-id="96012-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Ruft eine Codierung für das UTF-8-Format ab.</span><span class="sxs-lookup"><span data-stu-id="96012-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96012-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="96012-114">See also</span></span>

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [<span data-ttu-id="96012-115">Gewusst wie: Konvertieren eines Bytearrays in eine Zeichenfolge in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="96012-115">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>](how-to-convert-an-array-of-bytes-into-a-string.md)
