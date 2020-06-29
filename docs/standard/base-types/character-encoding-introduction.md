---
title: Einführung in die Zeichencodierung in .NET
description: Erfahren Sie mehr über die Zeichencodierung und -decodierung in .NET.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 85349e1e1c4eca4dd3ef7980f48350a4145fca24
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599866"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="7be82-103">Zeichencodierung in .NET</span><span class="sxs-lookup"><span data-stu-id="7be82-103">Character encoding in .NET</span></span>

<span data-ttu-id="7be82-104">Dieser Artikel bietet eine Einführung in die von .NET verwendeten Zeichencodierungssysteme.</span><span class="sxs-lookup"><span data-stu-id="7be82-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="7be82-105">Es wird erläutert, wie die Typen <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune> und <xref:System.Globalization.StringInfo> mit Unicode, UTF-16 und UTF-8 funktionieren.</span><span class="sxs-lookup"><span data-stu-id="7be82-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="7be82-106">Der Begriff *Zeichen* wird hier im allgemeinen Sinn für ein Zeichen verwendet, das *vom Leser als einzelnes Anzeigeelement wahrgenommen wird*.</span><span class="sxs-lookup"><span data-stu-id="7be82-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="7be82-107">Gängige Beispiele sind der Buchstabe „a“, das Symbol „@“ und das Emoji 🐂.</span><span class="sxs-lookup"><span data-stu-id="7be82-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="7be82-108">Mitunter setzt sich ein als ein Zeichen wahrgenommenes Zeichen tatsächlich aus mehreren unabhängigen Anzeigeelementen zusammen, dies wird im Abschnitt zu [Graphemhaufen](#grapheme-clusters) erläutert.</span><span class="sxs-lookup"><span data-stu-id="7be82-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-string-and-char-types"></a><span data-ttu-id="7be82-109">Die string- und char-Typen.</span><span class="sxs-lookup"><span data-stu-id="7be82-109">The string and char types</span></span>

<span data-ttu-id="7be82-110">Eine Instanz der [string](xref:System.String)-Klasse stellt Text dar.</span><span class="sxs-lookup"><span data-stu-id="7be82-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="7be82-111">Ein `string` ist logisch gesehen eine Abfolge von 16-Bit-Werten, von denen jeder eine Instanz der [char](xref:System.Char)-Struktur ist.</span><span class="sxs-lookup"><span data-stu-id="7be82-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="7be82-112">Die [string.Length](xref:System.String.Length)-Eigenschaft gibt die Anzahl von `char`-Instanzen in der `string`-Instanz zurück.</span><span class="sxs-lookup"><span data-stu-id="7be82-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="7be82-113">Die folgende Beispielfunktion gibt die Werte aller `char`-Instanzen in einem `string` in Hexadezimalnotation zurück:</span><span class="sxs-lookup"><span data-stu-id="7be82-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

<span data-ttu-id="7be82-114">Wenn Sie an diese Funktion die string „Hello“ übergeben, erhalten Sie die folgende Ausgabe:</span><span class="sxs-lookup"><span data-stu-id="7be82-114">Pass the string "Hello" to this function, and you get the following output:</span></span>

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

<span data-ttu-id="7be82-115">Jedes Zeichen wird durch einen einzelnen `char`-Wert repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="7be82-115">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="7be82-116">Dieses Muster gilt für die meisten Sprachen der Welt.</span><span class="sxs-lookup"><span data-stu-id="7be82-116">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="7be82-117">Beispielsweise sehen Sie nachfolgend die Ausgabe für zwei chinesische Zeichen, die ausgesprochen wie *nǐ hǎo* klingen und *Hallo* bedeuten:</span><span class="sxs-lookup"><span data-stu-id="7be82-117">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="7be82-118">Für einige Sprachen und für einige Symbole und Emojis werden jedoch zwei `char`-Instanzen benötigt, um ein einzelnes Zeichen darzustellen.</span><span class="sxs-lookup"><span data-stu-id="7be82-118">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="7be82-119">Vergleichen Sie beispielsweise die Zeichen und `char`-Instanzen in dem Wort, das in der Osage-Sprache *Osage* bedeutet:</span><span class="sxs-lookup"><span data-stu-id="7be82-119">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

<span data-ttu-id="7be82-120">Im vorherigen Beispiel wird jedes Zeichen mit Ausnahme des Leerzeichens durch zwei `char`-Instanzen repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="7be82-120">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="7be82-121">Ein einzelnes Unicode-Emoji wird ebenfalls durch zwei `char`s dargestellt, wie im folgenden Beispiel eines Emojis für einen Ochsen:</span><span class="sxs-lookup"><span data-stu-id="7be82-121">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="7be82-122">Diese Beispiele zeigen, dass der Wert von `string.Length`, der die Anzahl von `char`-Instanzen angibt, nicht notwendigerweise der Anzahl angezeigter Zeichen entsprechen muss.</span><span class="sxs-lookup"><span data-stu-id="7be82-122">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="7be82-123">Eine einzelne `char`-Instanz repräsentiert für sich genommen nicht zwingend ein Zeichen.</span><span class="sxs-lookup"><span data-stu-id="7be82-123">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="7be82-124">Die `char`-Paare, die einem einzelnen Zeichen zugeordnet sind, werden als *Ersatzzeichenpaare* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="7be82-124">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="7be82-125">Um deren Funktionsweise zu verstehen, müssen wir die Unicode- und die UTF-16-Codierung verstehen.</span><span class="sxs-lookup"><span data-stu-id="7be82-125">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="7be82-126">Unicode-Codepunkte</span><span class="sxs-lookup"><span data-stu-id="7be82-126">Unicode code points</span></span>

<span data-ttu-id="7be82-127">Unicode ist ein internationaler Codierungsstandard, der in zahlreichen Plattformen und mit verschiedenen Sprachen und Skripts eingesetzt wird.</span><span class="sxs-lookup"><span data-stu-id="7be82-127">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="7be82-128">Der Unicode-Standard definiert über 1,1 Millionen [Codepunkte](https://www.unicode.org/glossary/#code_point).</span><span class="sxs-lookup"><span data-stu-id="7be82-128">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="7be82-129">Ein Codepunkt ist ein ganzzahliger Wert, der zwischen 0 und `U+10FFFF` liegen kann (in Dezimalschreibweise: 1.114.111).</span><span class="sxs-lookup"><span data-stu-id="7be82-129">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="7be82-130">Einige Codepunkte sind Buchstaben, Symbolen oder Emojis zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="7be82-130">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="7be82-131">Andere sind Aktionen zugeordnet, die steuern, wie Textelemente oder Zeichen angezeigt werden – beispielsweise ein Zeilenvorschub.</span><span class="sxs-lookup"><span data-stu-id="7be82-131">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="7be82-132">Viele Codepunkte sind noch nicht zugewiesen.</span><span class="sxs-lookup"><span data-stu-id="7be82-132">Many code points are not yet assigned.</span></span>

<span data-ttu-id="7be82-133">Nachfolgend werden einige Beispiele für Codepunktzuweisungen aufgelistet, mit Links zu Unicode-Diagrammen, in denen sie angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="7be82-133">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="7be82-134">Decimal</span><span class="sxs-lookup"><span data-stu-id="7be82-134">Decimal</span></span>|<span data-ttu-id="7be82-135">Hex</span><span class="sxs-lookup"><span data-stu-id="7be82-135">Hex</span></span>       |<span data-ttu-id="7be82-136">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7be82-136">Example</span></span>|<span data-ttu-id="7be82-137">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7be82-137">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="7be82-138">10</span><span class="sxs-lookup"><span data-stu-id="7be82-138">10</span></span>     | `U+000A` |<span data-ttu-id="7be82-139">Nicht zutreffend</span><span class="sxs-lookup"><span data-stu-id="7be82-139">N/A</span></span>| [<span data-ttu-id="7be82-140">ZEILENVORSCHUB</span><span class="sxs-lookup"><span data-stu-id="7be82-140">LINE FEED</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="7be82-141">65</span><span class="sxs-lookup"><span data-stu-id="7be82-141">65</span></span>     | `U+0061` | <span data-ttu-id="7be82-142">eine</span><span class="sxs-lookup"><span data-stu-id="7be82-142">a</span></span> | [<span data-ttu-id="7be82-143">LATEINISCHER KLEINBUCHSTABE A</span><span class="sxs-lookup"><span data-stu-id="7be82-143">LATIN SMALL LETTER A</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="7be82-144">562</span><span class="sxs-lookup"><span data-stu-id="7be82-144">562</span></span>    | `U+0232` | <span data-ttu-id="7be82-145">Ȳ</span><span class="sxs-lookup"><span data-stu-id="7be82-145">Ȳ</span></span> | [<span data-ttu-id="7be82-146">LATEINISCHER GROSSBUCHSTABE MIT MAKRON</span><span class="sxs-lookup"><span data-stu-id="7be82-146">LATIN CAPITAL LETTER Y WITH MACRON</span></span>](https://www.unicode.org/charts/PDF/U0180.pdf) |
|<span data-ttu-id="7be82-147">68.675</span><span class="sxs-lookup"><span data-stu-id="7be82-147">68,675</span></span> | `U+10C43`| <span data-ttu-id="7be82-148">𐱃</span><span class="sxs-lookup"><span data-stu-id="7be82-148">𐱃</span></span> | [<span data-ttu-id="7be82-149">ALTTÜRKISCHES ORCHON-SCHRIFTZEICHEN AT</span><span class="sxs-lookup"><span data-stu-id="7be82-149">OLD TURKIC LETTER ORKHON AT</span></span>](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|<span data-ttu-id="7be82-150">127.801</span><span class="sxs-lookup"><span data-stu-id="7be82-150">127,801</span></span>| `U+1F339`| <span data-ttu-id="7be82-151">🌹</span><span class="sxs-lookup"><span data-stu-id="7be82-151">🌹</span></span> | [<span data-ttu-id="7be82-152">Rosen-Emoji</span><span class="sxs-lookup"><span data-stu-id="7be82-152">ROSE emoji</span></span>](https://www.unicode.org/charts/PDF/U1F300.pdf) |

<span data-ttu-id="7be82-153">Auf Codepunkte wird hauptsächlich durch Verwendung der Syntax `U+xxxx` verwiesen, wobei es sich bei `xxxx` um den ganzzahligen Wert in Hexadezimalcodierung handelt.</span><span class="sxs-lookup"><span data-stu-id="7be82-153">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="7be82-154">Der vollständige Bereich der Codepunkte enthält zwei Unterbereiche:</span><span class="sxs-lookup"><span data-stu-id="7be82-154">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="7be82-155">Die **Basic Multilingual Plane (BMP)** im Bereich `U+0000..U+FFFF`.</span><span class="sxs-lookup"><span data-stu-id="7be82-155">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="7be82-156">Dieser 16-Bit-Bereich umfasst 65.536 Codepunkte und reicht zur Abdeckung der meisten Schriftsysteme der Welt aus.</span><span class="sxs-lookup"><span data-stu-id="7be82-156">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="7be82-157">**Ergänzende Codepunkte** im Bereich `U+10000..U+10FFFF`.</span><span class="sxs-lookup"><span data-stu-id="7be82-157">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="7be82-158">Dieser 21-Bit-Bereich umfasst mehr als eine Million zusätzlicher Codepunkte, die für weniger bekannte Sprachen und zu anderen Zwecken genutzt werden können, wie beispielsweise Emojis.</span><span class="sxs-lookup"><span data-stu-id="7be82-158">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="7be82-159">Das folgende Diagramm veranschaulicht die Beziehung zwischen der BMP und den ergänzenden Codepunkten.</span><span class="sxs-lookup"><span data-stu-id="7be82-159">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP und ergänzende Codepunkte":::

## <a name="utf-16-code-units"></a><span data-ttu-id="7be82-161">UTF-16-Codeeinheiten</span><span class="sxs-lookup"><span data-stu-id="7be82-161">UTF-16 code units</span></span>

<span data-ttu-id="7be82-162">16-Bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) ist ein Zeichencodierungssystem, das 16-Bit-*Codeeinheiten* zur Darstellung von Unicode-Codepunkten verwendet.</span><span class="sxs-lookup"><span data-stu-id="7be82-162">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="7be82-163">.NET verwendet UTF-16 zum Codieren von Text in einem `string`.</span><span class="sxs-lookup"><span data-stu-id="7be82-163">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="7be82-164">Eine `char`-Instanz repräsentiert eine 16-Bit-Codeeinheit.</span><span class="sxs-lookup"><span data-stu-id="7be82-164">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="7be82-165">Eine einzelne 16-Bit-Codeeinheit kann jeden Codepunkt im 16-Bit-Bereich der Basic Multilingual Plane (BMP) repräsentieren.</span><span class="sxs-lookup"><span data-stu-id="7be82-165">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="7be82-166">Aber für einen Codepunkt im ergänzenden Bereich werden zwei `char`-Instanzen benötigt.</span><span class="sxs-lookup"><span data-stu-id="7be82-166">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="7be82-167">Ersatzzeichenpaare</span><span class="sxs-lookup"><span data-stu-id="7be82-167">Surrogate pairs</span></span>

<span data-ttu-id="7be82-168">Die Übersetzung von zwei 16-Bit-Werten in einen einzelnen 21-Bit-Wert wird durch einen speziellen Bereich ermöglicht, der die sogenannten *Ersatzcodepunkte* von `U+D800` bis `U+DFFF` einschließlich (in Dezimalschreibweise: 55.296 bis 57.343) umfasst.</span><span class="sxs-lookup"><span data-stu-id="7be82-168">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="7be82-169">Das folgende Diagramm veranschaulicht die Beziehung zwischen der BMP und den Ersatzcodepunkten.</span><span class="sxs-lookup"><span data-stu-id="7be82-169">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP und Ersatzcodepunkte":::

<span data-ttu-id="7be82-171">Wenn auf einen *hohen* Ersatzcodepunkt (`U+D800..U+DBFF`) unmittelbar ein *niedriger* Ersatzcodepunkt (`U+DC00..U+DFFF`) folgt, wird das Paar anhand der folgenden Formel als ergänzender Codepunkt interpretiert:</span><span class="sxs-lookup"><span data-stu-id="7be82-171">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="7be82-172">Nachstehend sehen Sie die gleiche Formel unter Verwendung der Dezimalschreibweise:</span><span class="sxs-lookup"><span data-stu-id="7be82-172">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="7be82-173">Ein *hoher* Ersatzcodepunkt weist keinen höheren Zahlenwert auf als ein *niedriger* Ersatzcodepunkt.</span><span class="sxs-lookup"><span data-stu-id="7be82-173">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="7be82-174">Der hohe Ersatzcodepunkt wird so bezeichnet, weil er zum Berechnen der hohen 11 Bits des vollständigen 21-Bit-Codepunktbereichs verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7be82-174">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="7be82-175">Der niedrige Ersatzcodepunkt wird zum Berechnen der unteren 10 Bits verwendet.</span><span class="sxs-lookup"><span data-stu-id="7be82-175">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="7be82-176">Beispielsweise wird der tatsächliche Codepunkt, der dem Ersatzzeichenpaar `0xD83C` und `0xDF39` entspricht, folgendermaßen berechnet:</span><span class="sxs-lookup"><span data-stu-id="7be82-176">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="7be82-177">Hier dieselbe Berechnung in Dezimalschreibweise:</span><span class="sxs-lookup"><span data-stu-id="7be82-177">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="7be82-178">Das vorstehende Beispiel zeigt, dass es sich bei `"\ud83c\udf39"` um die UTF-16-Codierung des zuvor erwähnten Codepunkts `U+1F339 ROSE ('🌹')` handelt.</span><span class="sxs-lookup"><span data-stu-id="7be82-178">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="7be82-179">Unicode-Skalarwerte</span><span class="sxs-lookup"><span data-stu-id="7be82-179">Unicode scalar values</span></span>

<span data-ttu-id="7be82-180">Der Begriff [Unicode-Skalarwert](https://www.unicode.org/glossary/#unicode_scalar_value) bezieht sich auf alle Codepunkte mit Ausnahme der Ersatzcodepunkte.</span><span class="sxs-lookup"><span data-stu-id="7be82-180">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="7be82-181">Anders ausgedrückt: Ein Skalarwert ist ein beliebiger Codepunkt, der einem Zeichen zugewiesen ist oder in Zukunft einem Zeichen zugewiesen werden kann.</span><span class="sxs-lookup"><span data-stu-id="7be82-181">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="7be82-182">„Zeichen“ bezieht sich hierbei auf ein beliebiges Element, das einem Codepunkt zugewiesen werden kann, darunter z. B. Aktionen zum Steuern der Anzeige von Text oder Zeichen.</span><span class="sxs-lookup"><span data-stu-id="7be82-182">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="7be82-183">Das nachstehende Diagramm veranschaulicht die Skalarwert-Codepunkte.</span><span class="sxs-lookup"><span data-stu-id="7be82-183">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Skalarwerte":::

### <a name="the-rune-type-as-a-scalar-value"></a><span data-ttu-id="7be82-185">Der Rune-Typ als Skalarwert</span><span class="sxs-lookup"><span data-stu-id="7be82-185">The Rune type as a scalar value</span></span>

<span data-ttu-id="7be82-186">Ab .NET Core 3.0 repräsentiert der <xref:System.Text.Rune?displayProperty=fullName>-Typ einen Unicode-Skalarwert.</span><span class="sxs-lookup"><span data-stu-id="7be82-186">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="7be82-187">**`Rune` ist in .NET Core 2. oder .NET Framework 4.x nicht verfügbar.**</span><span class="sxs-lookup"><span data-stu-id="7be82-187">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="7be82-188">Der `Rune`-Konstruktor überprüft, ob die Ergebnisinstanz ein gültiger Unicode-Skalarwert ist, anderenfalls wird eine Ausnahme ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="7be82-188">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="7be82-189">Das folgende Codebeispiel zeigt eine erfolgreiche Instanziierung von `Rune`-Instanzen, weil es sich bei der Eingabe um gültige Skalarwerte handelt:</span><span class="sxs-lookup"><span data-stu-id="7be82-189">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

<span data-ttu-id="7be82-190">Das folgende Beispiel führt zu einer Ausnahme, weil der Codepunkt sich im Ersatzbereich befindet und nicht Teil eines Ersatzzeichenpaars ist:</span><span class="sxs-lookup"><span data-stu-id="7be82-190">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

<span data-ttu-id="7be82-191">Das nachstehende Beispiel führt zu einer Ausnahme, weil der Codepunkt nicht im ergänzenden Bereich liegt:</span><span class="sxs-lookup"><span data-stu-id="7be82-191">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="rune-usage-example-changing-letter-case"></a><span data-ttu-id="7be82-192">Beispiel für die Verwendung von Rune: Änderung der Groß-/Kleinschreibung</span><span class="sxs-lookup"><span data-stu-id="7be82-192">Rune usage example: changing letter case</span></span>

<span data-ttu-id="7be82-193">Eine API, die einen `char`-Wert verwendet und annimmt, dass sie mit einem Codepunkt arbeitet, bei dem es sich um einen Skalarwert handelt, funktioniert nicht ordnungsgemäß, wenn der `char`-Wert aus einem Ersatzzeichenpaar stammt.</span><span class="sxs-lookup"><span data-stu-id="7be82-193">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="7be82-194">Betrachten Sie beispielsweise die folgende Methode, die <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> für jeden char in einem string aufruft:</span><span class="sxs-lookup"><span data-stu-id="7be82-194">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

<span data-ttu-id="7be82-195">Wenn die Eingabezeichenfolge (`input` string) den Deseret-Buchstaben `er` in Kleinschreibung (`𐑉`) enthält, wird mit diesem Code keine Konvertierung in einen Großbuchstaben (`𐐡`) durchgeführt.</span><span class="sxs-lookup"><span data-stu-id="7be82-195">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="7be82-196">Der Code ruft `char.ToUpperInvariant` separat für jeden Ersatzcodepunkt auf, `U+D801` und `U+DC49`.</span><span class="sxs-lookup"><span data-stu-id="7be82-196">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="7be82-197">Aber `U+D801` selbst weist nicht genügend Informationen für die Identifizierung als Kleinbuchstabe auf und wird daher von `char.ToUpperInvariant` nicht verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="7be82-197">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="7be82-198">`U+DC49` wird in gleicher Weise behandelt.</span><span class="sxs-lookup"><span data-stu-id="7be82-198">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="7be82-199">Als Ergebnis wird der Kleinbuchstabe „𐑉“ in der Eingabezeichenfolge (`input` string) nicht in den Großbuchstaben „𐐡“ konvertiert wird.</span><span class="sxs-lookup"><span data-stu-id="7be82-199">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="7be82-200">Hier sind zwei Optionen für die korrekte Konvertierung von string in Großbuchstaben:</span><span class="sxs-lookup"><span data-stu-id="7be82-200">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="7be82-201">Rufen Sie <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> für den Eingabe-string auf, statt `char` für `char` zu durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="7be82-201">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="7be82-202">Die `string.ToUpperInvariant`-Methode hat Zugriff auf beide Teile des Ersatzzeichenpaars, deshalb können alle Unicode-Codepunkte ordnungsgemäß verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="7be82-202">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="7be82-203">Durchlaufen Sie die Unicode-Skalarwerte nicht als `char`-Instanzen, sondern als `Rune`-Instanzen, wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="7be82-203">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="7be82-204">Eine `Rune`-Instanz ist ein gültiger Unicode-Skalarwert, deshalb kann sie an APIs übergeben werden, die einen Skalarwert für die Verarbeitung erwarten.</span><span class="sxs-lookup"><span data-stu-id="7be82-204">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="7be82-205">Beispielsweise liefert der Aufruf von <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> wie im folgenden Beispiel richtige Ergebnisse:</span><span class="sxs-lookup"><span data-stu-id="7be82-205">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-rune-apis"></a><span data-ttu-id="7be82-206">Andere Rune-APIs</span><span class="sxs-lookup"><span data-stu-id="7be82-206">Other Rune APIs</span></span>

<span data-ttu-id="7be82-207">Der `Rune`-Typ macht Entsprechungen vieler der `char`-APIs verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7be82-207">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="7be82-208">Beispielsweise spiegeln die folgenden Methoden statische APIs für den `char`-Typ:</span><span class="sxs-lookup"><span data-stu-id="7be82-208">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="7be82-209">Um den Rohskalarwert aus einer `Rune`-Instanz abzurufen, verwenden Sie die <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType>-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="7be82-209">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="7be82-210">Um eine `Rune`-Instanz wieder ein eine `char`-Sequenz zu konvertieren, verwenden Sie <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> oder die <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType>-Methode.</span><span class="sxs-lookup"><span data-stu-id="7be82-210">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7be82-211">Da jeder Unicode-Skalarwert durch einen einzelnen `char` oder durch ein Ersatzzeichenpaar dargestellt wird, kann jede `Rune`-Instanz durch höchstens 2 `char`-Instanzen dargestellt werden.</span><span class="sxs-lookup"><span data-stu-id="7be82-211">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="7be82-212">Verwenden Sie <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType>, um anzuzeigen, wie viele `char`-Instanzen zur Darstellung einer `Rune`-Instanz benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="7be82-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="7be82-213">Weitere Informationen zum .NET-Typ `Rune` finden Sie in der [`Rune`API-Referenz](xref:System.Text.Rune).</span><span class="sxs-lookup"><span data-stu-id="7be82-213">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="7be82-214">Graphemhaufen</span><span class="sxs-lookup"><span data-stu-id="7be82-214">Grapheme clusters</span></span>

<span data-ttu-id="7be82-215">Was wie ein einziges Zeichen aussieht, kann tatsächlich eine Kombination mehrerer Codepunkte sein, deshalb wird zur Beschreibung anstelle des Begriffs „Zeichen“ häufig der Begriff [Graphemhaufen](https://www.unicode.org/glossary/#grapheme_cluster) verwendet.</span><span class="sxs-lookup"><span data-stu-id="7be82-215">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="7be82-216">Der äquivalente Begriff in .NET lautet [Textelement](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span><span class="sxs-lookup"><span data-stu-id="7be82-216">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="7be82-217">Betrachten Sie die `string`-Instanzen „a“, „á“,</span><span class="sxs-lookup"><span data-stu-id="7be82-217">Consider the `string` instances "a", "á".</span></span> <span data-ttu-id="7be82-218">„á“ und `👩🏽‍🚒`.</span><span class="sxs-lookup"><span data-stu-id="7be82-218">"á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="7be82-219">Wenn Ihr Betriebssystem diese gemäß Spezifikation im Unicode-Standard verarbeitet, wird jede dieser `string`-Instanzen als ein einzelnes Textelement bzw. als Graphemhaufen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7be82-219">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="7be82-220">Aber die letzten beiden werden durch mehr als einen Skalarwert-Codepunkt repräsentiert.</span><span class="sxs-lookup"><span data-stu-id="7be82-220">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="7be82-221">Die string-Instanz „a“ wird durch einen Skalarwert repräsentiert und enthält eine `char`-Instanz.</span><span class="sxs-lookup"><span data-stu-id="7be82-221">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="7be82-222">Die string-Instanz „á“ wird durch einen Skalarwert repräsentiert und enthält eine `char`-Instanz.</span><span class="sxs-lookup"><span data-stu-id="7be82-222">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* <span data-ttu-id="7be82-223">Die string-Instanz „á“ sieht aus wie „á“, wird jedoch durch zwei Skalarwerte repräsentiert und enthält zwei `char`-Instanzen.</span><span class="sxs-lookup"><span data-stu-id="7be82-223">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="7be82-224">Die string-Instanz `👩🏽‍🚒` schließlich wird durch vier Skalarwerte repräsentiert und enthält sieben `char`-Instanzen.</span><span class="sxs-lookup"><span data-stu-id="7be82-224">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="7be82-225">`U+1F469 WOMAN` (ergänzender Bereich, erfordert ein Ersatzzeichenpaar)</span><span class="sxs-lookup"><span data-stu-id="7be82-225">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="7be82-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (ergänzender Bereich, erfordert ein Ersatzzeichenpaar)</span><span class="sxs-lookup"><span data-stu-id="7be82-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="7be82-227">`U+1F692 FIRE ENGINE` (ergänzender Bereich, erfordert ein Ersatzzeichenpaar)</span><span class="sxs-lookup"><span data-stu-id="7be82-227">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="7be82-228">In einigen der vorhergehenden Beispiele – beispielsweise dem kombinierten Akzentmodifizierer oder dem Modifizierer für den Hautton – wird der Codepunkt nicht als eigenständiges Element auf dem Bildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7be82-228">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="7be82-229">Stattdessen dient er zum Ändern des Aussehens eines vorangegangenen Textelements.</span><span class="sxs-lookup"><span data-stu-id="7be82-229">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="7be82-230">Diese Beispiele zeigen, dass möglicherweise mehrere Skalarwerte erforderlich sind, um ein einzelnes „Zeichen“ oder einen „Graphemhaufen“ zu erzeugen.</span><span class="sxs-lookup"><span data-stu-id="7be82-230">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="7be82-231">Um die Graphemhaufen für einen `string` aufzulisten, verwenden Sie die <xref:System.Globalization.StringInfo>-Klasse wie im folgenden Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="7be82-231">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="7be82-232">Wenn Sie mit Swift vertraut sind: Der .NET-Typ `StringInfo` ähnelt vom Konzept her dem [`character`-Typ in Swift](https://developer.apple.com/documentation/swift/character).</span><span class="sxs-lookup"><span data-stu-id="7be82-232">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-char-rune-and-text-element-instances"></a><span data-ttu-id="7be82-233">Beispiel: Zählen von char-, Rune- und Textelementinstanzen</span><span class="sxs-lookup"><span data-stu-id="7be82-233">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="7be82-234">In den .NET-APIs wird ein Graphemhaufen als *Textelement* bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="7be82-234">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="7be82-235">Die folgenden Methoden veranschaulichen die Unterschiede zwischen `char`-, `Rune`- und Textelementinstanzen in einem `string`:</span><span class="sxs-lookup"><span data-stu-id="7be82-235">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

<span data-ttu-id="7be82-236">Wenn Sie diesen Code in .NET Framework oder .NET Code 3.1 oder früher ausführen, wird die Textelementanzahl für das Emoji als `4` angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7be82-236">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="7be82-237">Dies liegt an einem Fehler in der `StringInfo`-Klasse, der in .NET 5 behoben wurde.</span><span class="sxs-lookup"><span data-stu-id="7be82-237">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-string-instances"></a><span data-ttu-id="7be82-238">Beispiel: Aufteilen von string-Instanzen</span><span class="sxs-lookup"><span data-stu-id="7be82-238">Example: splitting string instances</span></span>

<span data-ttu-id="7be82-239">Vermeiden Sie beim Aufteilen von `string`-Instanzen das Teilen von Ersatzzeichenpaaren und Graphemhaufen.</span><span class="sxs-lookup"><span data-stu-id="7be82-239">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="7be82-240">Sehen Sie sich das folgende fehlerhafte Codebeispiel an, bei dem nach jeweils 10 Zeichen in einem string ein Zeilenumbruch eingefügt werden soll:</span><span class="sxs-lookup"><span data-stu-id="7be82-240">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

<span data-ttu-id="7be82-241">Dieser Code zählt `char`-Instanzen auf, deshalb wird ein Ersatzzeichenpaar, dass sich über eine 10-`char`-Grenze erstreckt, aufgeteilt und dazwischen ein Zeilenumbruch eingefügt.</span><span class="sxs-lookup"><span data-stu-id="7be82-241">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="7be82-242">Diese Einfügung führt zu einer Datenbeschädigung, weil Ersatzcodepunkte nur als Paar eine Bedeutung tragen.</span><span class="sxs-lookup"><span data-stu-id="7be82-242">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="7be82-243">Die Möglichkeit einer Datenbeschädigung ist nicht ausgeschlossen, wenn Sie anstelle von `char`-Instanzen `Rune`-Instanzen (Skalarwerte) aufzählen.</span><span class="sxs-lookup"><span data-stu-id="7be82-243">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="7be82-244">Ein Satz aus `Rune`-Instanzen kann einen Graphemhaufen bilden, der sich über eine 10-`char`-Grenze erstreckt.</span><span class="sxs-lookup"><span data-stu-id="7be82-244">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="7be82-245">Wenn der Graphemhaufen geteilt wird, kann er nicht ordnungsgemäß interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="7be82-245">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="7be82-246">Ein besserer Ansatz besteht darin, den string durch Zählen der Graphemhaufen oder Textelemente zu teilen, wie im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="7be82-246">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

<span data-ttu-id="7be82-247">Wie bereits erwähnt, kann die `StringInfo`-Klasse in .NET-Implementierungen (im Gegensatz zu .NET 5) einige Graphemhaufen jedoch falsch verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="7be82-247">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="7be82-248">UTF-8 und UTF-32</span><span class="sxs-lookup"><span data-stu-id="7be82-248">UTF-8 and UTF-32</span></span>

<span data-ttu-id="7be82-249">Die vorangegangenen Abschnitte konzentrierten sich auf UTF-16, weil .NET UTF-16 zur Codierung von `string`-Instanzen verwendet.</span><span class="sxs-lookup"><span data-stu-id="7be82-249">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="7be82-250">Für Unicode sind einige weitere Codierungssysteme vorhanden – [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) und [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span><span class="sxs-lookup"><span data-stu-id="7be82-250">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="7be82-251">Diese Codierungen verwenden 8-Bit-Codeeinheiten bzw. 32-Bit-Codeeinheiten.</span><span class="sxs-lookup"><span data-stu-id="7be82-251">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="7be82-252">Wie UTF-16 werden in UTF-8 mehrere Codeeinheiten benötigt, um einige Unicode-Skalarwerte darzustellen.</span><span class="sxs-lookup"><span data-stu-id="7be82-252">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="7be82-253">UTF-32 kann jeden beliebigen Skalarwert in einer einzelnen 32-Bit-Codeeinheit darstellen.</span><span class="sxs-lookup"><span data-stu-id="7be82-253">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="7be82-254">Hier sind einige Beispiele, die zeigen, wie derselbe Unicode-Codepunkt in jedem dieser drei Unicode-Codierungssysteme dargestellt wird:</span><span class="sxs-lookup"><span data-stu-id="7be82-254">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

<span data-ttu-id="7be82-255">Wie bereits erwähnt, ist eine einzelne UTF-16-Codeeinheit aus einem [Einzelzeichenpaar](#surrogate-pairs) für sich genommen bedeutungslos.</span><span class="sxs-lookup"><span data-stu-id="7be82-255">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="7be82-256">Ebenso ist eine einzelne UTF-8-Codeeinheit für sich genommen bedeutungslos, wenn sie in einer Sequenz von zwei, drei oder vier Einheiten zur Berechnung eines Skalarwerts verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7be82-256">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="7be82-257">Endianness</span><span class="sxs-lookup"><span data-stu-id="7be82-257">Endianness</span></span>

<span data-ttu-id="7be82-258">In .NET werden die UTF-16-Codeeinheiten für einen string in zusammenhängenden Speicherbereichen als Sequenz aus 16-Bit-Ganzzahlen (`char`-Instanzen) gespeichert.</span><span class="sxs-lookup"><span data-stu-id="7be82-258">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="7be82-259">Die Bits der einzelnen Codeeinheiten werden gemäß [Endianwert](https://en.wikipedia.org/wiki/Endianness) der aktuellen Architektur angeordnet.</span><span class="sxs-lookup"><span data-stu-id="7be82-259">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="7be82-260">In einer Little-Endian-Architektur wird der aus UTF-16-Codeeinheiten `[ D801 DCCC ]` bestehende string im Arbeitsspeicher in Form der Bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]` angeordnet.</span><span class="sxs-lookup"><span data-stu-id="7be82-260">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="7be82-261">In einer Big-Endian-Architektur würde derselbe string im Arbeitsspeicher in Form der Bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]` angeordnet werden.</span><span class="sxs-lookup"><span data-stu-id="7be82-261">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="7be82-262">Computersysteme, die miteinander kommunizieren, müssen sich auf die Darstellung von Daten einigen, die übertragen werden.</span><span class="sxs-lookup"><span data-stu-id="7be82-262">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="7be82-263">Die meisten Netzwerkprotokolle verwenden UTF-8 als Standard für die Textübertragung – unter anderem, um Probleme zu vermeiden, die durch die Kommunikation eines Big-Endian-Computers mit einem Little-Endian-Computer entstehen könnten.</span><span class="sxs-lookup"><span data-stu-id="7be82-263">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="7be82-264">Der aus den UTF-8-Codepunkten `[ F0 90 93 8C ]` bestehende string wird immer in Form der Bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` dargestellt, unabhängig vom Endianwert.</span><span class="sxs-lookup"><span data-stu-id="7be82-264">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="7be82-265">Um UTF-8 für die Übertragung von Text zu verwenden, nutzen .NET-Anwendungen häufig Code wie im folgenden Beispiel:</span><span class="sxs-lookup"><span data-stu-id="7be82-265">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="7be82-266">Im vorstehenden Beispiel decodiert die Methode [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) den UTF-16-`string` zurück in eine Reihe von Unicode-Skalarwerten. Anschließend werden diese Skalarwerte wieder in UTF-8 codiert, und die Ergebnissequenz wird in einem `byte`-Array platziert.</span><span class="sxs-lookup"><span data-stu-id="7be82-266">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="7be82-267">Die Methode [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) führt die umgekehrte Transformation durch, sie konvertiert einen UTF-8-`byte`-Array in einen UTF-16-`string`.</span><span class="sxs-lookup"><span data-stu-id="7be82-267">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="7be82-268">Weil UTF-8 im Internet so weit verbreitet ist, kann es verlockend sein, Rohbytes aus der Verbindung zu lesen und die Daten so zu behandeln, als handele es sich um UTF-8.</span><span class="sxs-lookup"><span data-stu-id="7be82-268">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="7be82-269">Sie müssen jedoch sicherstellen, dass die Daten tatsächlich wohlgeformt sind.</span><span class="sxs-lookup"><span data-stu-id="7be82-269">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="7be82-270">Ein schädlicher Client überträgt möglicherweise nicht wohlgeformte UTF-8-Daten an Ihren Dienst.</span><span class="sxs-lookup"><span data-stu-id="7be82-270">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="7be82-271">Wenn Sie mit diesen Daten arbeiten, als seien es wohlgeformte Daten, kann dies zu Fehlern oder Sicherheitslücken in Ihrer Anwendung führen.</span><span class="sxs-lookup"><span data-stu-id="7be82-271">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="7be82-272">Um UTF-8-Daten zu validieren, können Sie eine Methode wie `Encoding.UTF8.GetString` verwenden, die während der Konvertierung der eingehenden Daten in einen `string` eine Überprüfung durchführt.</span><span class="sxs-lookup"><span data-stu-id="7be82-272">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="7be82-273">Wohlgeformte Codierung</span><span class="sxs-lookup"><span data-stu-id="7be82-273">Well-formed encoding</span></span>

<span data-ttu-id="7be82-274">Eine wohlgeformte Unicode-Codierung ist ein string aus Codeeinheiten, die eindeutig decodiert und ohne Fehler in eine Sequenz von Unicode-Skalarwerten konvertiert werden können.</span><span class="sxs-lookup"><span data-stu-id="7be82-274">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="7be82-275">Wohlgeformte Daten können ohne Einschränkung zwischen UTF-8, UTF-16 und UTF-32 hin- und her transcodiert werden.</span><span class="sxs-lookup"><span data-stu-id="7be82-275">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="7be82-276">Die Frage, ob eine Codierungssequenz wohlgeformt ist oder nicht, hat nichts mit dem Endianwert einer Computerarchitektur zu tun.</span><span class="sxs-lookup"><span data-stu-id="7be82-276">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="7be82-277">Eine nicht wohlgeformte UTF-8-Sequenz ist sowohl für einen Big-Endian- als auch für einen Little-Endian-Computer nicht wohlgeformt.</span><span class="sxs-lookup"><span data-stu-id="7be82-277">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="7be82-278">Hier sehen Sie einige Beispiele für nicht wohlgeformte Codierungen:</span><span class="sxs-lookup"><span data-stu-id="7be82-278">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="7be82-279">In UTF-8 ist die Sequenz `[ 6C C2 61 ]` nicht wohlgeformt, weil auf `C2` nicht `61` folgen darf.</span><span class="sxs-lookup"><span data-stu-id="7be82-279">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="7be82-280">In UTF-16 ist die Sequenz `[ DC00 DD00 ]` nicht wohlgeformt (oder in C# der string `"\udc00\udd00"`), weil auf das niedrige Ersatzzeichen `DC00` nicht ein weiteres niedriges Ersatzzeichen `DD00` folgen kann.</span><span class="sxs-lookup"><span data-stu-id="7be82-280">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="7be82-281">In UTF-32 ist die Sequenz `[ 0011ABCD ]` nicht wohlgeformt, weil `0011ABCD` außerhalb des Bereichs für Unicode-Skalarwerte liegt.</span><span class="sxs-lookup"><span data-stu-id="7be82-281">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="7be82-282">In .NET enthalten `string`-Instanzen fast immer wohlgeformte UTF-16-Daten, aber dies ist nicht garantiert.</span><span class="sxs-lookup"><span data-stu-id="7be82-282">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="7be82-283">Die folgenden Beispiele zeigen gültigen C#-Code, der nicht wohlgeformte UTF-16-Daten in `string`-Instanzen erzeugt.</span><span class="sxs-lookup"><span data-stu-id="7be82-283">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="7be82-284">Ein nicht wohlgeformtes Literal:</span><span class="sxs-lookup"><span data-stu-id="7be82-284">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="7be82-285">Eine Teilzeichenfolge, die ein Ersatzzeichenpaar aufteilt:</span><span class="sxs-lookup"><span data-stu-id="7be82-285">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="7be82-286">APIs wie [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) geben keine nicht wohlgeformten `string`-Instanzen zurück.</span><span class="sxs-lookup"><span data-stu-id="7be82-286">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="7be82-287">Die Methoden `Encoding.GetString` und `Encoding.GetBytes` erkennen nicht wohlgeformte Sequenzen in der Eingabe und führen beim Generieren der Ausgabe Zeichenersetzungen durch.</span><span class="sxs-lookup"><span data-stu-id="7be82-287">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="7be82-288">Wenn [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) beispielsweise ein Nicht-ASCII-Byte (außerhalb des Bereichs U+0000..U+007F) in der Eingabe erkennt, wird ein ? in die zurückgegebene `string`-Instanz eingefügt.</span><span class="sxs-lookup"><span data-stu-id="7be82-288">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="7be82-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) ersetzt nicht wohlgeformte UTF-8-Sequenzen in der zurückgegebenen `string`-Instanz durch `U+FFFD REPLACEMENT CHARACTER ('�')`.</span><span class="sxs-lookup"><span data-stu-id="7be82-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="7be82-290">Weitere Informationen finden Sie unter [Unicode-Standard](https://www.unicode.org/versions/latest/) in den Abschnitten 5.22 und 3.9.</span><span class="sxs-lookup"><span data-stu-id="7be82-290">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="7be82-291">Die integrierten `Encoding`-Klassen können auch so konfiguriert werden, dass sie anstelle einer Zeichenersetzung eine Ausnahme auslösen, wenn falsch formatierte Sequenzen erkannt werden.</span><span class="sxs-lookup"><span data-stu-id="7be82-291">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="7be82-292">Dieser Ansatz findet häufig in Anwendungen mit hohen Sicherheitsanforderungen Anwendung, bei denen eine Zeichenersetzung möglicherweise nicht akzeptabel ist.</span><span class="sxs-lookup"><span data-stu-id="7be82-292">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="7be82-293">Informationen zur Verwendung der integrierten `Encoding`-Klassen finden Sie unter [Verwenden von Zeichencodierungsklassen in .NET](character-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="7be82-293">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7be82-294">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7be82-294">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="7be82-295">Globalisierung und Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="7be82-295">Globalization and Localization</span></span>](../globalization-localization/index.md)
