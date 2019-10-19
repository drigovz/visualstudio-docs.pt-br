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
ms.openlocfilehash: d90b6b923f631c7785428a1b3879528e97c1bfd6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572871"
---
# <a name="enumerator-object-expected"></a>Objeto enumerador esperado
Você tentou invocar o método **enumerador. prototype. atEnd, Enumerator. prototype. Item, enumerador. prototype. MoveFirst** ou **enumerador. prototype. MoveNext** em um objeto de um tipo diferente de `Enumerator`. O objeto desse tipo de invocação deve ser do tipo `Enumerator`. Aqui está um exemplo de código que interrompe esta regra:  
  
```JavaScript  
var o = new Object;  
o.f = Enumerator.prototype.atEnd;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Invoque somente os métodos **Enumerator. prototype. atEnd**, **enumerador. prototype. Item**, **enumerador. prototype. MoveFirst**ou **enumerador. prototype. MoveNext** em objetos do tipo `Enumerator`. Para descobrir se o objeto é um `Enumerator` objeto, use:  
  
    ```js
    if(x instanceof Enumerator)  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Enumerator](../../javascript/reference/enumerator-object-javascript.md)