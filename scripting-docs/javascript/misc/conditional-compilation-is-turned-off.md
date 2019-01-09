---
title: Compilação condicional está desativada | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bcbf844ced2bb74ddfea9bd62d68877b7a3c969c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092879"
---
# <a name="conditional-compilation-is-turned-off"></a>Compilação condicional está desativada
Você tentou usar uma variável de compilação condicional sem primeiro compilação condicional de ativação no. Ativar a compilação condicional informa o [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] compilador a interpretar os identificadores que começam com como variáveis de compilação condicional. Você pode fazer isso, a partir de seu código condicional com a instrução:  
  
```js
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicione a seguinte instrução para o início do seu código condicional:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Compilação condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variáveis de compilação condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Instrução](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Instrução](../../javascript/reference/at-if-statement-javascript.md)   
 [Instrução @set](../../javascript/reference/at-set-statement-javascript.md)