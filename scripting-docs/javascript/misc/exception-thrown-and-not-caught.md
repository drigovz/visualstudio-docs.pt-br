---
title: Exceção lançada, mas não capturada | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349030"
---
# <a name="exception-thrown-and-not-caught"></a>Exceção lançada, mas não capturada
Você incluído um `throw` instrução em seu código, mas não foi incluída dentro uma **tente** bloco, ou houve não associado **catch** bloco para interceptar o erro. As exceções são geradas de dentro a **tente** bloquear usando o **throw** instrução e capturada fora o **tente** bloco com um **catch** instrução.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Coloque o código que pode lançar uma exceção em um **tente** bloquear e verifique se há um correspondente **catch** bloco.  
  
-   Certifique-se de sua instrução catch espera que a forma correta de exceção.  
  
-   Se a exceção será gerada novamente, verifique se que há outra instrução catch correspondente.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Error](../../javascript/reference/error-object-javascript.md)   
 [Instrução throw](../../javascript/reference/throw-statement-javascript.md)   
 [Instrução try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)