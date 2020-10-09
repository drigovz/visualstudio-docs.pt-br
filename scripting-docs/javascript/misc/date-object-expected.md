---
title: Objeto Date esperado | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 28531c1ac1dc73ca2bf309d412b08d23dd17bfb8
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862648"
---
# <a name="date-object-expected"></a>Objeto de data esperado
Você tentou invocar o método **Date. prototype. ToString** ou **Date. prototype. valueOf** em um objeto de um tipo diferente de `Date` . O objeto deste tipo de invocação deve ser do tipo `Date` . Por exemplo:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Invocar apenas os métodos **Date. prototype. ToString** ou **Date. prototype. valueOf** em objetos do tipo `Date` .  
  
## <a name="see-also"></a>Confira também  
 [Objeto Date](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date)   
 [Método getDate (Date)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Date/getdate)   
 [Objetos intrínsecos](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)