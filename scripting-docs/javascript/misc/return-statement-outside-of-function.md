---
title: instrução ' return' fora função | Microsoft Docs
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
ms.openlocfilehash: 01ef96385d5fe3dccf14a7491e67983d39913280
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63006400"
---
# <a name="return-statement-outside-of-function"></a>Instrução 'return' fora de função
Você usou um `return` instrução no escopo global do seu código. O `return` instrução deve aparecer apenas dentro do corpo de uma função.  
  
 Invocação de uma função com o `()` operador é uma expressão. Todas as expressões têm valores; o `return` instrução é usada para especificar o valor retornado por uma função. O formato geral é:  
  
```js
  
return [ expression ];  
```  
  
 Quando o `return` instrução é executada, *expressão* é avaliado e retornado como o valor da função. Se não houver nenhuma expressão **indefinido** é retornado.  
  
 A execução da função é interrompido quando o `return` instrução é executada, mesmo se houver outras instruções ainda resta no corpo da função. A exceção a essa regra é se o **retornar** instrução ocorre dentro de uma **tente** bloco, e há um correspondente **finalmente** bloco, o código no  **Por fim** bloco serão executadas antes da função retorna.  
  
 Se uma função retornar porque ela atinge o final do corpo da função sem executar uma `return` instrução, o valor retornado é o **indefinido** valor (Isso significa que o resultado da função não pode ser usado como parte de uma expressão maior ).  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remover o `return` instrução do corpo principal do seu código (o escopo global).  
  
## <a name="see-also"></a>Consulte também  
 [Instrução return](../../javascript/reference/return-statement-javascript.md)   
 [Objeto de função](../../javascript/reference/function-object-javascript.md)   
 [Propriedade caller (Function)](../../javascript/reference/caller-property-function-javascript.md)