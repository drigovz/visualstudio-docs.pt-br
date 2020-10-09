---
title: Função esperada | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2028d8923c2f81d1d99fec752d7ac0ce2fb32f65
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862174"
---
# <a name="function-expected"></a>Função esperada
Você tentou invocar um dos métodos de **protótipo de função** em um objeto que não era um `Function` objeto ou usou um objeto em um contexto de chamada de função. Por exemplo, o código a seguir produz esse erro porque o **exemplo** não é uma função.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Só chame métodos de **protótipo de função** em `Function` objetos.  
  
- Certifique-se de usar o operador de chamada de função `()` para chamar apenas funções.  
  
## <a name="see-also"></a>Confira também  
 [Objeto de função](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Propriedade prototype (Object)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)