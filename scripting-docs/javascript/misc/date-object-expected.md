---
title: Objeto de data esperado | Microsoft Docs
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
ms.openlocfilehash: 2767ffc16b637c6b1e7bdf51cb0815d71f58edac
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050486"
---
# <a name="date-object-expected"></a>Objeto de data esperado
Você tentou invocar o **Date.prototype.toString** ou **Date.prototype.valueOf** método em um objeto de um tipo diferente de `Date`. O objeto desse tipo de invocação deve ser do tipo `Date`. Por exemplo:  
  
```JavaScript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Invoque apenas o **Date.prototype.toString** ou **Date.prototype.valueOf** métodos em objetos do tipo `Date`.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Date](../../javascript/reference/date-object-javascript.md)   
 [Método getDate (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Objetos intrínsecos](../../javascript/intrinsic-objects-javascript.md)