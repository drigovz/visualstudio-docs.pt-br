---
title: Não há suporte para referência circular em argumento de valor | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 542fca58778a7b85b3044ce984b6ea049db12509
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572341"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Referência circular no argumento de valor não é compatível
Foi feita uma tentativa de invocar `JSON.stringify` com um valor que não é válido. O argumento `value`, uma matriz ou um objeto, contém uma referência circular.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Remova a referência circular do argumento.  
  
## <a name="example"></a>Exemplo  
 O código neste exemplo causa um erro em tempo de execução porque `john` tem uma referência a `mary` e `mary` tem uma referência a `john`. para remover a referência circular, remova ou desmarque a propriedade `brother` do objeto `mary` ou da propriedade `sister` do objeto `john`.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [objeto JSON](../../javascript/reference/json-object-javascript.md)  
 [Função JSON. parse](../../javascript/reference/json-parse-function-javascript.md)    
 [Erros de tempo de execução JavaScript](../../javascript/reference/javascript-run-time-errors.md)