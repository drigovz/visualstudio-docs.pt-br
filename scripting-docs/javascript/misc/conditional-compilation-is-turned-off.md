---
title: Compilação condicional está desativada | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8317121b840d82ab12d4a9e1ca50f6680eb1e21d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946570"
---
# <a name="conditional-compilation-is-turned-off"></a>Compilação condicional está desativada
Você tentou usar uma variável de compilação condicional sem primeiro compilação condicional de ativação no. Ativar a compilação condicional informa o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] compilador a interpretar os identificadores que começam com como variáveis de compilação condicional. Você pode fazer isso, a partir de seu código condicional com a instrução:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Adicione a seguinte instrução para o início do seu código condicional:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Compilação condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variáveis de compilação condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Statement](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Statement](../../javascript/reference/at-if-statement-javascript.md)   
 [Instrução @set](../../javascript/reference/at-set-statement-javascript.md)