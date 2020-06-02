---
title: 'Vorgehensweise: Signieren von XML-Dokumenten mit digitalen Signaturen'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signatures, XML signing
- System.Security.Cryptography.SignedXml class
- digital signatures, XML signing
- System.Security.Cryptography.RSACryptoServiceProvider class
- XML digital signatures
- XML signing
- signing XML
ms.assetid: 99692ac1-d8c9-42d7-b1bf-2737b01037e4
ms.openlocfilehash: 81fa5e4c503f26dc13758090f845fd8387287084
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277179"
---
# <a name="how-to-sign-xml-documents-with-digital-signatures"></a><span data-ttu-id="f3797-102">Vorgehensweise: Signieren von XML-Dokumenten mit digitalen Signaturen</span><span class="sxs-lookup"><span data-stu-id="f3797-102">How to: Sign XML Documents with Digital Signatures</span></span>
<span data-ttu-id="f3797-103">Um ein XML-Dokument teilweise oder vollständig mit einer digitalen Signatur zu versehen, können Sie die Klassen im <xref:System.Security.Cryptography.Xml>-Namespace verwenden.</span><span class="sxs-lookup"><span data-stu-id="f3797-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to sign an XML document or part of an XML document with a digital signature.</span></span>  <span data-ttu-id="f3797-104">Über digitale XML-Signaturen (XMLDSIG) können Sie sich vergewissern, dass Daten nicht mehr geändert wurden, nachdem sie signiert wurden.</span><span class="sxs-lookup"><span data-stu-id="f3797-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="f3797-105">Weitere Informationen zum XMLDSIG-Standard finden Sie unter World Wide Web Consortium (W3C) Empfehlungs [Syntax für XML-Signaturen und Verarbeitung](https://www.w3.org/TR/xmldsig-core/).</span><span class="sxs-lookup"><span data-stu-id="f3797-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) recommendation [XML Signature Syntax and Processing](https://www.w3.org/TR/xmldsig-core/).</span></span>  
  
 <span data-ttu-id="f3797-106">Das Codebeispiel in dieser Prozedur veranschaulicht, wie ein gesamtes XML-Dokument digital signiert und die Signatur an das Dokument in einem <>-Element angefügt wird `Signature` .</span><span class="sxs-lookup"><span data-stu-id="f3797-106">The code example in this procedure demonstrates how to digitally sign an entire XML document and attach the signature to the document in a <`Signature`> element.</span></span>  <span data-ttu-id="f3797-107">Im Beispiel wird ein RSA-Signaturschlüssel erstellt, wird der Schlüssel einem sicheren Schlüsselcontainer hinzugefügt und wird der Schlüssel dann verwendet, um ein XML-Dokument digital zu signieren.</span><span class="sxs-lookup"><span data-stu-id="f3797-107">The example creates an RSA signing key, adds the key to a secure key container, and then uses the key to digitally sign an XML document.</span></span>  <span data-ttu-id="f3797-108">Der Schlüssel kann danach abgerufen werden, um die digitale Signatur des XML-Dokuments zu überprüfen oder ein anderes XML-Dokument zu signieren.</span><span class="sxs-lookup"><span data-stu-id="f3797-108">The key can then be retrieved to verify the XML digital signature, or can be used to sign another XML document.</span></span>  
  
 <span data-ttu-id="f3797-109">Informationen zum Überprüfen einer digitalen XML-Signatur, die mit diesem Verfahren erstellt wurde, finden Sie unter Gewusst [wie: Überprüfen der digitalen Signaturen von XML-Dokumenten](how-to-verify-the-digital-signatures-of-xml-documents.md).</span><span class="sxs-lookup"><span data-stu-id="f3797-109">For information about how to verify an XML digital signature that was created using this procedure, see [How to: Verify the Digital Signatures of XML Documents](how-to-verify-the-digital-signatures-of-xml-documents.md).</span></span>  
  
### <a name="to-digitally-sign-an-xml-document"></a><span data-ttu-id="f3797-110">So signieren Sie ein XML-Dokument digital</span><span class="sxs-lookup"><span data-stu-id="f3797-110">To digitally sign an XML document</span></span>  
  
1. <span data-ttu-id="f3797-111">Erstellen Sie ein <xref:System.Security.Cryptography.CspParameters>-Objekt, und geben Sie den Namen des Schlüsselcontainers an.</span><span class="sxs-lookup"><span data-stu-id="f3797-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToSignXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#2)]  
  
2. <span data-ttu-id="f3797-112">Generieren Sie mit der <xref:System.Security.Cryptography.RSACryptoServiceProvider>-Klasse einen asymmetrischen Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="f3797-112">Generate an asymmetric key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="f3797-113">Der Schlüssel wird automatisch im Schlüsselcontainer gespeichert, wenn Sie das <xref:System.Security.Cryptography.CspParameters>-Objekt an den Konstruktor der <xref:System.Security.Cryptography.RSACryptoServiceProvider>-Klasse übergeben.</span><span class="sxs-lookup"><span data-stu-id="f3797-113">The key is automatically saved to the key container when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="f3797-114">Dieser Schlüssel wird zum Signieren des XML-Dokuments verwendet.</span><span class="sxs-lookup"><span data-stu-id="f3797-114">This key will be used to sign the XML document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToSignXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#3)]  
  
3. <span data-ttu-id="f3797-115">Erstellen Sie ein <xref:System.Xml.XmlDocument>-Objekt, indem Sie eine XML-Datei von einem Datenträger laden.</span><span class="sxs-lookup"><span data-stu-id="f3797-115">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="f3797-116">Das <xref:System.Xml.XmlDocument>-Objekt enthält das zu verschlüsselnde XML-Element.</span><span class="sxs-lookup"><span data-stu-id="f3797-116">The <xref:System.Xml.XmlDocument> object contains the XML element to encrypt.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToSignXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#4)]  
  
4. <span data-ttu-id="f3797-117">Erstellen Sie ein neues <xref:System.Security.Cryptography.Xml.SignedXml>-Objekt, und übergeben Sie diesem das <xref:System.Xml.XmlDocument>-Objekt.</span><span class="sxs-lookup"><span data-stu-id="f3797-117">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToSignXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#5)]  
  
5. <span data-ttu-id="f3797-118">Fügen Sie den RSA-Signaturschlüssel dem <xref:System.Security.Cryptography.Xml.SignedXml>-Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="f3797-118">Add the signing RSA key to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToSignXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#6)]  
  
6. <span data-ttu-id="f3797-119">Erstellen Sie ein <xref:System.Security.Cryptography.Xml.Reference>-Objekt, das beschreibt, was signiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="f3797-119">Create a <xref:System.Security.Cryptography.Xml.Reference> object that describes what to sign.</span></span>  <span data-ttu-id="f3797-120">Um das gesamte Dokument zu signieren, legen Sie die <xref:System.Security.Cryptography.Xml.Reference.Uri%2A>-Eigenschaft auf `""` fest.</span><span class="sxs-lookup"><span data-stu-id="f3797-120">To sign the entire document, set the <xref:System.Security.Cryptography.Xml.Reference.Uri%2A> property to `""`.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToSignXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#7)]  
  
7. <span data-ttu-id="f3797-121">Fügen Sie dem <xref:System.Security.Cryptography.Xml.Reference>-Objekt ein <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform>-Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="f3797-121">Add an <xref:System.Security.Cryptography.Xml.XmlDsigEnvelopedSignatureTransform> object to the <xref:System.Security.Cryptography.Xml.Reference> object.</span></span>  <span data-ttu-id="f3797-122">Eine Transformation ermöglicht es dem Prüfer, die XML-Daten auf genau die Weise darzustellen, die der Signaturgeber verwendet hat.</span><span class="sxs-lookup"><span data-stu-id="f3797-122">A transformation allows the verifier to represent the XML data in the identical manner that the signer used.</span></span>  <span data-ttu-id="f3797-123">XML-Daten können auf unterschiedliche Weise dargestellt werden, weshalb dieser Schritt für die Überprüfung unverzichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="f3797-123">XML data can be represented in different ways, so this step is vital to verification.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToSignXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#8)]  
  
8. <span data-ttu-id="f3797-124">Fügen Sie dem <xref:System.Security.Cryptography.Xml.SignedXml>-Objekt das <xref:System.Security.Cryptography.Xml.Reference>-Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="f3797-124">Add the <xref:System.Security.Cryptography.Xml.Reference> object to the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#9)]
     [!code-vb[HowToSignXMLDocumentRSA#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#9)]  
  
9. <span data-ttu-id="f3797-125">Berechnen Sie die Signatur, indem Sie die <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A>-Methode aufrufen.</span><span class="sxs-lookup"><span data-stu-id="f3797-125">Compute the signature by calling the <xref:System.Security.Cryptography.Xml.SignedXml.ComputeSignature%2A> method.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#10)]
     [!code-vb[HowToSignXMLDocumentRSA#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#10)]  
  
10. <span data-ttu-id="f3797-126">Rufen Sie die XML-Darstellung der Signatur (ein <`Signature`>-Element) ab, und speichern Sie Sie in einem neuen- <xref:System.Xml.XmlElement> Objekt.</span><span class="sxs-lookup"><span data-stu-id="f3797-126">Retrieve the XML representation of the signature (a <`Signature`> element) and save it to a new <xref:System.Xml.XmlElement> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#11)]
     [!code-vb[HowToSignXMLDocumentRSA#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#11)]  
  
11. <span data-ttu-id="f3797-127">Fügen Sie das Element an das <xref:System.Xml.XmlDocument>-Objekt an.</span><span class="sxs-lookup"><span data-stu-id="f3797-127">Append the element to the <xref:System.Xml.XmlDocument> object.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#12)]
     [!code-vb[HowToSignXMLDocumentRSA#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#12)]  
  
12. <span data-ttu-id="f3797-128">Speichern Sie das Dokument.</span><span class="sxs-lookup"><span data-stu-id="f3797-128">Save the document.</span></span>  
  
     [!code-csharp[HowToSignXMLDocumentRSA#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#13)]
     [!code-vb[HowToSignXMLDocumentRSA#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#13)]  
  
## <a name="example"></a><span data-ttu-id="f3797-129">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f3797-129">Example</span></span>  
 <span data-ttu-id="f3797-130">Für dieses Beispiel wird angenommen, dass eine Datei namens `test.xml` im selben Verzeichnis wie das kompilierte Programm vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="f3797-130">This example assumes that a file named `test.xml` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="f3797-131">Sie können den folgenden XML-Code in eine Datei namens `test.xml` einfügen und mit diesem Beispiel verwenden.</span><span class="sxs-lookup"><span data-stu-id="f3797-131">You can place the following XML into a file called `test.xml` and use it with this example.</span></span>  
  
```xml  
<root>  
    <creditcard>  
        <number>19834209</number>  
        <expiry>02/02/2002</expiry>  
    </creditcard>  
</root>  
```  
  
 [!code-csharp[HowToSignXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToSignXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToSignXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToSignXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f3797-132">Kompilieren des Codes</span><span class="sxs-lookup"><span data-stu-id="f3797-132">Compiling the Code</span></span>  
  
- <span data-ttu-id="f3797-133">Um dieses Beispiel zu kompilieren, müssen Sie einen Verweis auf `System.Security.dll` einfügen.</span><span class="sxs-lookup"><span data-stu-id="f3797-133">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
- <span data-ttu-id="f3797-134">Fügen Sie die folgenden Namespaces hinzu: <xref:System.Xml>, <xref:System.Security.Cryptography> und <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="f3797-134">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f3797-135">.NET Framework-Sicherheit</span><span class="sxs-lookup"><span data-stu-id="f3797-135">.NET Framework Security</span></span>  
 <span data-ttu-id="f3797-136">Sie sollten den privaten Schlüssel eines asymmetrischen Schlüsselpaars niemals in Klartext speichern oder übertragen.</span><span class="sxs-lookup"><span data-stu-id="f3797-136">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="f3797-137">Weitere Informationen zu symmetrischen und asymmetrischen Kryptografieschlüsseln finden Sie unter [Erstellen von Schlüsseln für die Verschlüsselung und Entschlüsselung](generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="f3797-137">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="f3797-138">Sie sollten einen privaten Schlüssel niemals direkt in Ihren Quellcode einbetten.</span><span class="sxs-lookup"><span data-stu-id="f3797-138">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="f3797-139">Eingebettete Schlüssel können problemlos aus einer Assembly gelesen werden, indem [Ildasm. exe (IL-Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) verwendet wird, oder indem die Assembly in einem Texteditor wie dem Editor geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="f3797-139">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3797-140">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f3797-140">See also</span></span>

- <xref:System.Security.Cryptography.Xml>
- [<span data-ttu-id="f3797-141">Vorgehensweise: Überprüfen der digitalen Signaturen von XML-Dokumenten</span><span class="sxs-lookup"><span data-stu-id="f3797-141">How to: Verify the Digital Signatures of XML Documents</span></span>](how-to-verify-the-digital-signatures-of-xml-documents.md)
