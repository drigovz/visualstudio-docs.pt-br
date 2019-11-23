---
title: Objeto Date esperado | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5006
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 10af48c4804df3b5513df71578b948abe73ff8c2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572893"
---
# <a name="date-object-expected"></a>Objeto de data esperado
Você tentou invocar o método **Date. prototype. ToString** ou **Date. prototype. valueOf** em um objeto de um tipo diferente de `Date`. O objeto desse tipo de invocação deve ser do tipo `Date`. Por exemplo:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir esse erro  
  
- Invocar apenas os métodos **Date. prototype. ToString** ou **Date. prototype. valueOf** em objetos do tipo `Date`.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Date](../../javascript/reference/date-object-javascript.md)   
 [método GETDATE (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Objetos intrínsecos](../../javascript/intrinsic-objects-javascript.md)