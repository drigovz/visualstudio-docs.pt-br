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
ms.openlocfilehash: 4a25f72fccfd072243d6d0fdfd1d311c1a3bb6f4
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841437"
---
# <a name="expected-catch"></a>'catch' esperado
Você usou a manipulação de exceção **tente** bloquear, mas não escreveu associado **catch** instrução. A mecanismo de tratamento de exceção requer que o código que pode falhar, juntamente com o código que não deve ser executada se ocorrer uma exceção, ser encapsulados dentro de um **tente** bloco. As exceções são geradas de dentro de **tente** bloquear usando o **lançar** instrução e capturada fora o **tente** bloco com um ou mais **catch**as instruções.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicionar associado **catch** bloco.  
  
-   Tente usar um **finalmente** bloquear em vez de uma **catch** bloco.  
  
## <a name="see-also"></a>Consulte também  
 [Try...... finally instrução catch](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Objeto Error](../../javascript/reference/error-object-javascript.md)