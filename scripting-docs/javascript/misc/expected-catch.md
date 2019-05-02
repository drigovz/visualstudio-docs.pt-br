---
title: "'Catch' esperado | Microsoft Docs"
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 941d49a530b14e2af64ddcb599dd775feb347de0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935393"
---
# <a name="expected-catch"></a>'catch' esperado
Você usou a manipulação de exceção **tente** bloquear, mas não escreveu associado **catch** instrução. A mecanismo de tratamento de exceção requer que o código que pode falhar, juntamente com o código que não deve ser executada se ocorrer uma exceção, ser encapsulados dentro de um **tente** bloco. As exceções são geradas de dentro de **tente** bloquear usando o **lançar** instrução e capturada fora o **tente** bloco com um ou mais **catch**as instruções.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Adicionar associado **catch** bloco.  
  
- Tente usar um **finalmente** bloquear em vez de uma **catch** bloco.  
  
## <a name="see-also"></a>Consulte também  
 [Try...... finally instrução catch](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Objeto Error](../../javascript/reference/error-object-javascript.md)