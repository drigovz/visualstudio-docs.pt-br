---
title: Argumento substituto inválido | Microsoft Docs
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
ms.openlocfilehash: 0f144e733bf115cc98bf61b23a2ed3e4e3cda1e0
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346209"
---
# <a name="invalid-replacer-argument"></a>Argumento substituto inválido
Foi feita uma tentativa para invocar `JSON.stringify` com um argumento que não é válido. O `replacer` argumento deve ser uma função ou uma matriz.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Alterar o `replacer` argumento para uma função ou uma matriz.  
  
## <a name="example"></a>Exemplo  
 O código neste exemplo causa um erro de tempo de execução porque `memberfilter` é um objeto, em vez de uma função ou uma matriz.  
  
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
 [Objeto JSON](../../javascript/reference/json-object-javascript.md)   
 [Função JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Erros de tempo de execução JavaScript](../../javascript/reference/javascript-run-time-errors.md)