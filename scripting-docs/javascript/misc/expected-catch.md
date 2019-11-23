---
title: "' Catch ' esperado | Microsoft Docs"
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
ms.openlocfilehash: 8cad981e4ba469f67645aca601e6b58c18e1fab6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573434"
---
# <a name="expected-catch"></a>'catch' esperado
Você usou o bloco **try** de tratamento de exceção, mas não gravou a instrução **Catch** associada. O mecanismo de tratamento de exceção requer que o código que pode falhar, juntamente com o código que não deve ser executado se ocorrer uma exceção, seja encapsulado dentro de um bloco **try** . As exceções são geradas de dentro do bloco **try** usando a instrução **throw** e capturadas fora do bloco **try** com uma ou mais instruções **Catch** .  
  
### <a name="to-correct-this-error"></a>Para corrigir esse erro  
  
- Adicione o bloco **Catch** associado.  
  
- Tente usar um bloco **finally** em vez de um bloco **Catch** .  
  
## <a name="see-also"></a>Consulte também  
 [tentar... capturar... Instrução Finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Objeto Error](../../javascript/reference/error-object-javascript.md)