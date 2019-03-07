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
ms.openlocfilehash: e1e34be9f8eab5171af0e2553d5777b0958bf3c2
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840864"
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