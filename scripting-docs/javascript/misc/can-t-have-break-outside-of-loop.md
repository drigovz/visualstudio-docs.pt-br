---
title: Não é possível ter 'break' fora do loop | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a02848230187eb465d56ed73e44380e4b043b117
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084421"
---
# <a name="cant-have-break-outside-of-loop"></a>Não é possível ter 'break' fora do loop
Você tentou usar o **quebra** palavra-chave fora de um loop. O **quebra** palavra-chave é usada para encerrar um loop ou `switch` instrução. Ele deve ser inserido no corpo de um loop ou `switch` instrução. No entanto, uma **rótulo** pode seguir a palavra-chave break.  
  
```js
break labelname;  
```  
  
 Você só precisa rotulada forma do **quebra** loops aninhados de palavra-chave quando você estiver usando ou `switch` instruções e a necessidade de interromper um loop não é o mais interno.  
  
### <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Verifique se o **quebra** palavra-chave aparece dentro de uma instrução de loop ou opção de circunscrição.  
  
## <a name="see-also"></a>Consulte também  
 [Instrução break](../../javascript/reference/break-statement-javascript.md)   
 [Controlando o fluxo de programa](../../javascript/controlling-program-flow-javascript.md)   
 [Solucionar problemas com scripts](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)