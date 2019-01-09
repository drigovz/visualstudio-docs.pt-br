---
title: Não é possível atribuir a um resultado de função | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5003
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ee8ffb3a-1451-4cb3-99bf-5e9cf8b77d79
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a29c3f20392dc216c0306137c0dec6b22aaa58a
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093854"
---
# <a name="cannot-assign-to-a-function-result"></a>Não é possível designar a um resultado de função
Você tentou atribuir um valor a um resultado de função. O resultado de uma função pode ser atribuído a uma variável, mas ele não pode ser usado como uma variável. Se você deseja atribuir um novo valor para a função em si, omita os parênteses (o operador de chamada de função). O exemplo a seguir demonstra uma situação em que esse erro é gerado.  
  
```js
myFunction() = 42;  // Attempting to assign the value 42 to the result of the function call.  
```  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Não use o valor de um resultado de chamada de função como algo que você pode *atribuir a*. Você pode atribuir o resultado da chamada de função *a uma variável* embora.  
  
    ```JavaScript  
    myVar = myFunction(42);  
    ```  
  
-   Como alternativa, você pode atribuir a função em si (e não seu valor de retorno) a uma variável.  
  
    ```JavaScript  
    myFunction = new Function("return 42;");  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Objeto de função](../../javascript/reference/function-object-javascript.md)   
 [Escrevendo código JavaScript](../../javascript/writing-javascript-code.md)   
 [Funções](../../javascript/functions-javascript.md)