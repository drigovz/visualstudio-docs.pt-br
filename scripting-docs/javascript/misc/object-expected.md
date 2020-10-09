---
title: Objeto esperado | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5007
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d88c93d-e5b5-4b11-9bb5-bf1a5e41ccc3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a3b8510c92e15a5b1bf5e15bb774ba031f7181f
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862106"
---
# <a name="object-expected"></a>Objeto esperado
Você tentou invocar um método ou propriedade em um objeto de um tipo diferente de `Object`, ou passou um argumento de um tipo diferente de `Object` quando um `Object` era necessário.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Invoque apenas o método ou propriedade em objetos do tipo `Object`.  
  
- Se o erro ocorrer para um argumento não objeto, passe um objeto do tipo `Object`.  
  
- Verifique se uma referência indefinida ou nula está sendo invocada em vez de um objeto do tipo `Object`.  
  
     Por exemplo, se você receber esse erro em myVar no código a seguir:  
  
    ```JavaScript  
    var str = myVar.toString();  
    ```  
  
     você pode usar esse código:  
  
    ```JavaScript  
    if (myVar) {  
        var str = myVar.toString();  
    }  
    ```  
  
## <a name="see-also"></a>Confira também  
 [Objeto Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)   
 [Objetos e matrizes](https://developer.mozilla.org/docs/Learn/JavaScript/Objects)