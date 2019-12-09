---
title: instrução ' Return ' fora da função | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a90af6de8e2c238e3660111b19d13c1eaf628c9e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573694"
---
# <a name="return-statement-outside-of-function"></a>Instrução 'return' fora de função
Você usou uma instrução `return` no escopo global do seu código. A instrução `return` deve aparecer apenas dentro do corpo de uma função.  
  
 Invocar uma função com o operador `()` é uma expressão. Todas as expressões têm valores; a instrução `return` é usada para especificar o valor retornado por uma função. A forma geral é:  
  
```js
  
return [ expression ];  
```  
  
 Quando a instrução de `return` é executada, a *expressão* é avaliada e retornada como o valor da função. Se não houver nenhuma expressão, **indefinido** será retornado.  
  
 A execução da função é interrompida quando a instrução `return` é executada, mesmo se houver outras instruções ainda restantes no corpo da função. A exceção a essa regra é se a instrução **Return** ocorrer dentro de um bloco **try** e houver um bloco **finally** correspondente, o código no bloco **finally** será executado antes da função retornar.  
  
 Se uma função retornar, pois atingirá o final do corpo da função sem executar uma instrução `return`, o valor retornado será o valor **indefinido** (isso significa que o resultado da função não poderá ser usado como parte de uma expressão maior).  
  
### <a name="to-correct-this-error"></a>Para corrigir esse erro  
  
- Remova a instrução `return` do corpo principal do seu código (o escopo global).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução return](../../javascript/reference/return-statement-javascript.md)   
   de [objeto de função](../../javascript/reference/function-object-javascript.md)  
 [Propriedade caller (Function)](../../javascript/reference/caller-property-function-javascript.md)