---
title: Objeto enumerador esperado | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5015
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: dc6e32c1-a6e6-4e12-ac99-e3f65f91c8d7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 06005f635e5173e903cfba6a952750d64181d0bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946336"
---
# <a name="enumerator-object-expected"></a>Objeto enumerador esperado
Você tentou invocar o **Enumerator.prototype.atEnd, Enumerator.prototype.item, Enumerator.prototype.moveFirst,** ou **Enumerator.prototype.moveNext** método em um objeto de um tipo que `Enumerator`. O objeto desse tipo de invocação deve ser do tipo `Enumerator`. Aqui está um exemplo de código que violam essa regra:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Invoque apenas o **Enumerator.prototype.atEnd**, **Enumerator.prototype.item**, **Enumerator.prototype.moveFirst**, ou  **Enumerator.prototype.moveNext** métodos em objetos do tipo `Enumerator`. Para descobrir se o objeto é um `Enumerator` de objeto, use:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Enumerator](../../javascript/reference/enumerator-object-javascript.md)