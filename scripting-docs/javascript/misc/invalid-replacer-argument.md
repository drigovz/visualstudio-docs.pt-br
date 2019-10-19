---
title: Argumento de realocador inválido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ba76a2121dfb3853e38bacbdf49c985103c2a35
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573803"
---
# <a name="invalid-replacer-argument"></a>Argumento substituto inválido
Foi feita uma tentativa de invocar `JSON.stringify` com um argumento que não é válido. O argumento `replacer` deve ser uma função ou uma matriz.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Altere o argumento `replacer` para uma função ou uma matriz.  
  
## <a name="example"></a>Exemplo  
 O código neste exemplo causa um erro de tempo de execução porque `memberfilter` é um objeto em vez de uma função ou matriz.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [objeto JSON](../../javascript/reference/json-object-javascript.md)  
 [Função JSON. parse](../../javascript/reference/json-parse-function-javascript.md)    
 [Erros de tempo de execução JavaScript](../../javascript/reference/javascript-run-time-errors.md)