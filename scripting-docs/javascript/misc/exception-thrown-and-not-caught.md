---
title: Exceção lançada, mas não capturada | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: bae4ed0a335a9c12d16cb46208f77c4b66f12547
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946323"
---
# <a name="exception-thrown-and-not-caught"></a>Exceção lançada, mas não capturada
Você incluído um `throw` instrução em seu código, mas não foi incluída dentro uma **tente** bloco, ou houve não associado **catch** bloco para interceptar o erro. As exceções são geradas de dentro a **tente** bloquear usando o **throw** instrução e capturada fora o **tente** bloco com um **catch** instrução.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Coloque o código que pode lançar uma exceção em um **tente** bloquear e verifique se há um correspondente **catch** bloco.  
  
- Certifique-se de sua instrução catch espera que a forma correta de exceção.  
  
- Se a exceção será gerada novamente, verifique se que há outra instrução catch correspondente.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto Error](../../javascript/reference/error-object-javascript.md)   
 [Instrução throw](../../javascript/reference/throw-statement-javascript.md)   
 [Instrução try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)