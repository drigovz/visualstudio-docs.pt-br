---
title: Função esperada | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 988ca00613d3dec4c55309fd77bc43705a6038ae
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576590"
---
# <a name="function-expected"></a>Função esperada
Você tentou invocar um dos métodos de **protótipo de função** em um objeto que não era um objeto `Function` ou usou um objeto em um contexto de chamada de função. Por exemplo, o código a seguir produz esse erro porque o **exemplo** não é uma função.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Só chame métodos de **protótipo de função** em objetos `Function`.  
  
- Certifique-se de usar o operador de chamada de função `()` para chamar apenas funções.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [objeto de função](../../javascript/reference/function-object-javascript.md)  
 [Propriedade prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)