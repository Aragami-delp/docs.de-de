---
title: "\"<interfacename>.<membername>\" wird bereits durch die <baseclassname>-Basisklssse implementiert. Die erneute Implementierung von <type> wird angenommen."
ms.date: 07/20/2015
f1_keywords:
- vbc42015
- bc42015
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
ms.openlocfilehash: 6525ae08b90cc530a8f6a469d35d9ab8c27fb5e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402823"
---
# <a name="interfacenamemembername-is-already-implemented-by-the-base-class-baseclassname-re-implementation-of-type-assumed"></a>"\<interfacename>.\<membername>" wird bereits durch die \<baseclassname>-Basisklssse implementiert. Die erneute Implementierung von \<type> wird angenommen.
Eine Eigenschaft, Prozedur oder ein Ereignis in einer abgeleiteten Klasse verwendet eine- `Implements` Klausel, die einen Schnittstellenmember angibt, der bereits in der Basisklasse implementiert ist.  
  
 Ein Schnittstellenmember, der von seiner Basisklasse implementiert wird, kann von einer abgeleiteten Klasse erneut implementiert werden. Dieser Vorgang ist nicht identisch mit dem Überschreiben der Basisklassenimplementierung. Weitere Informationen finden Sie unter [Implements](../statements/implements-clause.md).  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Fehler-ID:** BC42015  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Wenn Sie beabsichtigen, den Schnittstellenmember erneut zu implementieren, müssen Sie keine Maßnahme ergreifen. Der Code in der abgeleiteten Klasse greift auf den neu implementierten Member zu, sofern Sie nicht das- `MyBase` Schlüsselwort verwenden, um auf die Basisklassen Implementierung zuzugreifen.  
  
- Wenn Sie keine erneute Implementierung des Schnittstellenmembers beabsichtigen, entfernen Sie die `Implements` -Klausel aus der Deklaration der Eigenschaft, Prozedur oder des Ereignisses.  
  
## <a name="see-also"></a>Weitere Informationen

- [Schnittstellen](../../programming-guide/language-features/interfaces/index.md)
