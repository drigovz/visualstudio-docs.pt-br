---
title: Exceção lançada e não detectada | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a0e3eb6d1275e5598ad44ea553e22f0b53eeb45
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862755"
---
# <a name="exception-thrown-and-not-caught"></a>Exceção lançada, mas não capturada
Você incluiu uma `throw` instrução em seu código, mas ela não estava colocada dentro de um bloco **try** ou não havia nenhum bloco **Catch** associado para interceptar o erro. As exceções são geradas de dentro do bloco **try** usando a instrução **throw** e detectadas fora do bloco **try** com uma instrução **Catch** .  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Coloque o código que pode gerar uma exceção em um bloco **try** e garantir que haja um bloco **Catch** correspondente.  
  
- Verifique se sua instrução Catch espera a forma correta de exceção.  
  
- Se a exceção for relançada, verifique se há outra instrução Catch correspondente.  
  
## <a name="see-also"></a>Confira também  
 [Objeto de erro](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [Instrução Throw](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [tentar... capturar... Instrução Finally](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)