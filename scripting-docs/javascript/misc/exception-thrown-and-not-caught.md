---
title: Exceção lançada e não detectada | Microsoft Docs
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
ms.openlocfilehash: 05a9e4f51d5daf7a9e1b1153acbbe8b76b539b72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572862"
---
# <a name="exception-thrown-and-not-caught"></a>Exceção lançada, mas não capturada
Você incluiu uma instrução `throw` em seu código, mas ela não estava dentro de um bloco **try** ou não havia nenhum bloco **Catch** associado para interceptar o erro. As exceções são geradas de dentro do bloco **try** usando a instrução **throw** e detectadas fora do bloco **try** com uma instrução **Catch** .  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Coloque o código que pode gerar uma exceção em um bloco **try** e garantir que haja um bloco **Catch** correspondente.  
  
- Verifique se sua instrução Catch espera a forma correta de exceção.  
  
- Se a exceção for relançada, verifique se há outra instrução Catch correspondente.  
  
## <a name="see-also"></a>Consulte também  
 @No__t_1 de [objeto de erro](../../javascript/reference/error-object-javascript.md)  
 [instrução throw](../../javascript/reference/throw-statement-javascript.md)    
 [Instrução try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)