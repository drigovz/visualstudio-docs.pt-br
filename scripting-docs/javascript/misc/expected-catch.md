---
title: "'Catch' esperado | Microsoft Docs"
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 244635605abafc5c0bd22c5203b105aa6e7dc669
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344103"
---
# <a name="expected-catch"></a>'catch' esperado
Você usou a manipulação de exceção **tente** bloquear, mas não escreveu associado **catch** instrução. A mecanismo de tratamento de exceção requer que o código que pode falhar, juntamente com o código que não deve ser executada se ocorrer uma exceção, ser encapsulados dentro de um **tente** bloco. As exceções são geradas de dentro de **tente** bloquear usando o **lançar** instrução e capturada fora o **tente** bloco com um ou mais **catch**as instruções.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Adicionar associado **catch** bloco.  
  
-   Tente usar um **finalmente** bloquear em vez de uma **catch** bloco.  
  
## <a name="see-also"></a>Consulte também  
 [Try...... finally instrução catch](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Objeto Error](../../javascript/reference/error-object-javascript.md)